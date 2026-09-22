---
tags: [networking, coursera, data-link-layer, ethernet, bilingual]
course: "Computer Networking (Google/Coursera)"
created: 2026-09-21
---

# Ethernet и MAC-адреса · Ethernet and MAC Addresses

Связано: [[TCP-IP Model]] · [[Network Devices - Hub and Switch]] · [[Physical Layer - Bits and Modulation]]

RU: Ethernet — протокол канального уровня, отвечающий за передачу данных по отдельным линиям связи.
EN: Ethernet is the data link layer protocol responsible for sending data across individual links.

> [!note] Зачем канальный уровень абстрагирует физический / Why the data link layer abstracts the physical layer
> RU: Одна из главных задач этого уровня — скрыть от вышестоящих уровней (сеть, транспорт, приложение) детали физического подключения. Поэтому браузеру не важно, подключено устройство по витой паре или по Wi-Fi.
> EN: One of this layer's main jobs is hiding the physical connection details from higher layers (network, transport, application). That's why a browser doesn't care whether the device connects via twisted pair or wireless.

---

## Немного истории · A bit of history
#history

RU: Ethernet появился в 1980 году, первая полная стандартизация — 1983 год. С тех пор менялась в основном пропускная способность, а базовый принцип остался прежним.
EN: Ethernet was invented in 1980, first fully standardized in 1983. Since then it's mostly bandwidth that's changed — the core standard is largely the same.

RU: В 1983 году свича (switch) ещё не существовало — многие/все устройства в сети делили **один общий collision domain**.
EN: In 1983 the switch hadn't been invented yet — many/all devices on a network often shared **a single collision domain**.

---

## CSMA/CD
#csma-cd

RU: **Carrier Sense Multiple Access with Collision Detection** — техника, которую Ethernet использует, чтобы решить проблему коллизий в общем collision domain.
EN: **Carrier Sense Multiple Access with Collision Detection** — the technique Ethernet uses to solve the collision problem in a shared collision domain.

**Как работает / How it works:**
1. RU: Если канал свободен — узел передаёт данные. EN: If the channel is free — a node transmits.
2. RU: Если два устройства передают одновременно — происходит коллизия, оба останавливают передачу. EN: If two devices transmit at once — collision detected, both stop transmitting.
3. RU: Каждое устройство ждёт **случайный** интервал времени перед повторной попыткой (чтобы избежать повторной коллизии). EN: Each device waits a **random** interval before retrying (to avoid colliding again).

---

## MAC-адрес · MAC address
#mac-address

RU: **Media Access Control address** — глобально уникальный идентификатор, присвоенный сетевому интерфейсу.
EN: **Media Access Control address** — a globally unique identifier assigned to an individual network interface.

**Формат / Format:**
- RU: 48-битное число · EN: a 48-bit number
- RU: Обычно записывается как 6 групп по 2 шестнадцатеричных цифры (hex) · EN: usually written as 6 groups of 2 hexadecimal digits
- RU: Шестнадцатеричная система — 16 цифр (0-9, затем A-F для 10-15) · EN: hexadecimal uses 16 digits (0-9, then A-F for 10-15)
- RU: Каждая группа = **октет** (число, представимое 8 битами; 2 hex-цифры = 8 бит) · EN: each group = an **octet** (a number representable by 8 bits; 2 hex digits = 8 bits)

> [!example] Масштаб уникальности / Scale of uniqueness
> RU: Возможных MAC-адресов: 2⁴⁸ = 281 474 976 710 656 (≈281 триллион). Поэтому адреса могут быть глобально уникальными.
> EN: Total possible MAC addresses: 2⁴⁸ = 281,474,976,710,656 (~281 trillion). That's why addresses can be globally unique.

### Структура MAC-адреса · MAC address structure

| Часть / Part | Октеты / Octets | Кто назначает / Assigned by |
|---|---|---|
| **OUI** (Organizationally Unique Identifier) | Первые 3 / First 3 | IEEE → производителю оборудования / manufacturer |
| Вторая часть / Second part | Последние 3 / Last 3 | Сам производитель (уникально в рамках OUI) / manufacturer itself (unique within its OUI) |

RU: По OUI (первым трём октетам) всегда можно определить производителя сетевого интерфейса.
EN: The OUI (first three octets) always lets you identify the manufacturer of a network interface.

---

## Зачем нужны MAC-адреса на практике · Why MAC addresses matter in practice
#practical-use

RU: Даже в общем collision domain каждый пакет Ethernet несёт MAC-адрес отправителя **и** получателя — поэтому каждый узел понимает, предназначены ли ему данные.
EN: Even within a shared collision domain, every Ethernet frame carries **both** the sender's and the recipient's MAC address — so every node can tell whether the data is meant for it.

---

## Unicast, Multicast, Broadcast
#unicast #multicast #broadcast

RU: Три типа Ethernet-передачи различаются тем, **кому предназначен** кадр — определяется через специальный бит в MAC-адресе получателя.
EN: The three types of Ethernet transmission differ in **who the frame is meant for** — determined by a special bit in the destination MAC address.

> [!note] I/G bit (least significant bit первого октета / least significant bit of the first octet)
> RU: `0` → unicast (одному адресату). `1` → multicast (группе адресатов).
> EN: `0` → unicast (single recipient). `1` → multicast (group of recipients).

### Unicast
#unicast

RU: Передача, предназначенная **только одному** получателю.
EN: A transmission meant for **just one** receiving address.

RU: Бит I/G = 0. Физически кадр всё равно расходится по всем устройствам collision domain (т.к. это общая среда), но **обрабатывает** его только устройство с совпадающим MAC-адресом — остальные отбрасывают.
EN: I/G bit = 0. The frame is still physically sent to every device on the collision domain (shared medium), but only the device whose MAC address matches will **receive and process** it — others discard it.

### Multicast
#multicast

RU: Тоже физически рассылается всем устройствам сегмента, но принимается/отбрасывается по **другому критерию**, не по собственному MAC-адресу устройства.
EN: Also physically sent to every device on the segment, but accepted/discarded based on a **different criterion**, not the device's own MAC address.

RU: Бит I/G = 1. Сетевые интерфейсы можно настроить на приём списка конкретных multicast-адресов — устройство "подписывается" на группу.
EN: I/G bit = 1. Network interfaces can be configured to accept a list of specific multicast addresses — the device "subscribes" to a group.

### Broadcast
#broadcast

RU: Отправляется **абсолютно всем** устройствам в LAN.
EN: Sent to **every single device** on a LAN.

RU: Используется специальный broadcast-адрес — **все биты единицы** (`FF:FF:FF:FF:FF:FF`).
EN: Uses a special broadcast address — **all F's** (`FF:FF:FF:FF:FF:FF`), i.e. all bits set to 1.

RU: Применяется, чтобы устройства могли "узнавать" друг о друге в сети.
EN: Used so devices can learn about each other on the network.

> [!example] Сводная таблица / Summary table
> | Тип / Type | Получатели / Recipients | I/G bit | Адрес / Address |
> |---|---|---|---|
> | Unicast | Один узел / One node | 0 | Конкретный MAC / Specific MAC |
> | Multicast | Группа по подписке / Subscribed group | 1 | Multicast-адрес / Multicast address |
> | Broadcast | Все узлы LAN / Every node on the LAN | 1 | `FF:FF:FF:FF:FF:FF` |

---

> [!warning] Частые ошибки / Common mistakes
> - RU: MAC-адрес — 48 бит, не 32 и не 64 · EN: A MAC address is **48 bits**, not 32 or 64
> - RU: OUI — это первые **3** октета (не последние) · EN: The OUI is the **first** 3 octets (not the last)
> - RU: CSMA/CD — про обнаружение и разрешение коллизий, а не их предотвращение целиком · EN: CSMA/CD **detects and handles** collisions, it doesn't fully prevent them
> - RU: Один октет = 8 бит = 2 hex-цифры · EN: One octet = 8 bits = 2 hex digits
> - RU: Свича в 1983 году ещё не было — отсюда общий collision domain · EN: The switch didn't exist in 1983 — hence the shared collision domain
> - RU: Даже unicast физически доходит до всех в collision domain — просто обрабатывается только адресатом · EN: Even unicast physically reaches everyone in the collision domain — only the addressee processes it
> - RU: Broadcast-адрес — все биты **единицы**, не нули · EN: The broadcast address is all bits set to **one**, not zero
