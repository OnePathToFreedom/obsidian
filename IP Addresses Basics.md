---
tags:
  - networking
  - coursera
  - network-layer
  - ip-addressing
  - bilingual
  - flashcards
  - review
course: Computer Networking (Google/Coursera)
created: 2026-09-21
sr-due: 2026-09-24
sr-interval: 1
sr-ease: 230
---

# Основы IP-адресов · IP Addresses Basics

Связано: [[TCP-IP Model]] · [[Ethernet and MAC Addresses]] · [[Network Devices - Router]]

---

## Формат IP-адреса · IP address format
#ip-format

RU: IP-адрес — 32-битное число, состоящее из **4 октетов**. Каждый октет обычно записывается в десятичной форме.
EN: An IP address is a **32-bit** number made up of **4 octets**. Each octet is normally written in decimal.

RU: 8 бит (1 октет) могут представить все десятичные числа **от 0 до 255**.
EN: 8 bits (1 octet) can represent all decimal numbers **from 0 to 255**.

> [!example] Dotted decimal notation
> RU: `12.34.56.78` — валидный IP-адрес. `123.456.789.100` — **невалидный**, потому что числа больше 255 (8 бит их представить не может). Такой формат записи называется **dotted decimal notation**.
> EN: `12.34.56.78` is a valid IP address. `123.456.789.100` is **not valid** — the numbers exceed 255 (can't be represented by 8 bits). This format is called **dotted decimal notation**.

---

## IP-адреса принадлежат сетям, не устройствам · IP addresses belong to networks, not devices
#ownership

RU: IP-адреса выдаются крупными блоками организациям и компаниям — **не** производителями оборудования (в отличие от MAC-адресов). Это делает их более иерархичными и удобными для хранения информации о маршрутах.
EN: IP addresses are distributed in large blocks to organizations and companies — **not** assigned by hardware vendors (unlike MAC addresses). This makes them more hierarchical and easier to store routing data about.

> [!example] Пример / Example
> RU: IBM владеет всеми IP-адресами, у которых первый октет = 9. Если роутеру нужно доставить пакет на `90.0.0.1`, ему достаточно знать, как добраться до **одного** из роутеров IBM — дальше маршрутизацию внутри своей сети берёт на себя IBM.
> EN: IBM owns every IP address with 9 as the first octet. If a router needs to deliver a packet to `90.0.0.1`, it only needs to know how to reach **one** of IBM's routers — IBM handles the rest internally.

> [!warning] Важное отличие от MAC-адресов / Key difference from MAC addresses
> RU: **IP-адрес принадлежит сети**, а не устройству. Твой ноутбук всегда имеет один и тот же MAC-адрес, но в интернет-кафе и дома у него будут **разные** IP-адреса — их выдаёт LAN, к которой ты подключаешься в конкретный момент.
> EN: **An IP address belongs to the network**, not the device. Your laptop always has the same MAC address, but it gets a **different** IP address at an internet café than at home — each LAN is responsible for handing one out.

---

## Dynamic vs Static IP
#dynamic-ip #static-ip

RU: **Dynamic IP address** — назначается автоматически при подключении устройства к сети, через технологию **DHCP (Dynamic Host Configuration Protocol)**.
EN: A **dynamic IP address** — automatically assigned when a device connects to a network, via **DHCP (Dynamic Host Configuration Protocol)**.

RU: **Static IP address** — настраивается на узле **вручную**.
EN: A **static IP address** — must be configured on a node **manually**.

> [!note] Кто обычно что использует / Typical usage
> RU: Static IP чаще всего используют серверы и сетевые устройства. Dynamic IP — обычные клиенты. Но бывают исключения.
> EN: Static IPs are typically reserved for servers and network devices. Dynamic IPs are typically for clients. But there are exceptions.

---

> [!warning] Частые ошибки / Common mistakes
> - RU: IP-адрес — 32 бита / 4 октета, не 48 бит (это MAC) · EN: An IP address is **32 bits / 4 octets**, not 48 bits (that's MAC)
> - RU: Максимум для одного октета — **255**, не 256 (диапазон 0-255) · EN: The max value per octet is **255**, not 256 (range is 0-255)
> - RU: IP-адреса раздаются организациям блоками — не производителями оборудования (в отличие от MAC/OUI) · EN: IP addresses are handed out to organizations in blocks — not assigned by hardware vendors (unlike MAC/OUI)
> - RU: IP-адрес принадлежит **сети**, MAC-адрес принадлежит **устройству** · EN: The IP address belongs to the **network**; the MAC address belongs to the **device**
> - RU: Dynamic IP выдаётся через DHCP автоматически; static — настраивается вручную · EN: Dynamic IP is assigned automatically via DHCP; static is configured manually

---

## Флеш-карточки · Flashcards
#flashcards

Сколько бит в IP-адресе, и как он обычно записывается? / How many bits are in an IP address, and how is it normally written?::RU: IP-адрес — **32-битное** число из **4 октетов**, каждый обычно записывается в десятичной форме (**dotted decimal notation**), например `12.34.56.78`. EN: An IP address is a **32-bit** number made of **4 octets**, each normally written in decimal (**dotted decimal notation**), e.g. `12.34.56.78`.
Какое максимальное значение может быть у одного октета, и почему? / What's the max value a single octet can have, and why?::RU: Максимум — **255** (диапазон 0-255), потому что октет = 8 бит, а 8 бит могут представить ровно 256 разных значений (0-255). Поэтому `123.456.789.100` — невалидный IP: 456 и 789 не помещаются в 8 бит. EN: The max is **255** (range 0-255), because an octet is 8 bits, and 8 bits can represent exactly 256 values (0-255). That's why `123.456.789.100` is invalid — 456 and 789 don't fit in 8 bits.
Кому принадлежит IP-адрес — устройству или сети, и чем это отличается от MAC-адреса? / Does an IP address belong to the device or the network, and how does that differ from a MAC address?::RU: IP-адрес принадлежит **сети**, а не устройству — например, твой ноутбук имеет один и тот же MAC-адрес везде, но дома и в интернет-кафе получит **разные** IP-адреса (их выдаёт конкретная LAN). IP-адреса раздаются крупными блоками организациям, а не производителями оборудования, как MAC/OUI. EN: An IP address belongs to the **network**, not the device — e.g. your laptop keeps the same MAC address everywhere, but gets a **different** IP address at home vs. an internet café (each LAN hands one out). IP addresses are distributed in large blocks to organizations, not assigned by hardware vendors like MAC/OUI.
Как назначается dynamic IP, и чем он отличается от static IP? / How is a dynamic IP assigned, and how does it differ from a static IP?::RU: **Dynamic IP** назначается **автоматически** при подключении устройства к сети через **DHCP (Dynamic Host Configuration Protocol)** — обычно так получают адрес клиенты. **Static IP** настраивается на узле **вручную** — обычно используется серверами и сетевыми устройствами. EN: A **dynamic IP** is assigned **automatically** when a device connects, via **DHCP** — typically how clients get their address. A **static IP** is configured **manually** — typically used by servers and network devices.
