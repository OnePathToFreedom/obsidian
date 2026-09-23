---
tags: [networking, coursera, data-link-layer, ethernet, bilingual, flashcards, review]
course: "Computer Networking (Google/Coursera)"
created: 2026-09-21
---

# Структура Ethernet-фрейма · Dissecting an Ethernet Frame

Связано: [[Ethernet and MAC Addresses]] · [[TCP-IP Model]]

---

## Data packet vs Ethernet frame
#terminology

RU: **Data packet (пакет данных)** — общий термин, обозначающий любой набор бинарных данных, передаваемых по сети. Не привязан к конкретному уровню или технологии.
EN: A **data packet** is a general term for any set of binary data sent across a network link. It isn't tied to a specific layer or technology.

RU: На уровне Ethernet такие пакеты называются **Ethernet-фреймами (frames)**.
EN: At the Ethernet level, these packets are called **Ethernet frames**.

RU: Фрейм — строго структурированный набор информации в фиксированном порядке. Это позволяет сетевым интерфейсам на физическом уровне превращать поток бит в осмысленные данные (и обратно).
EN: A frame is a highly structured collection of information in a specific order. This lets physical-layer network interfaces convert a stream of bits into meaningful data (and back).

> [!note]
> RU: Почти все секции фрейма обязательны, у большинства — фиксированный размер.
> EN: Almost all sections of a frame are mandatory, and most have a fixed size.

---

## Структура Ethernet-фрейма · Frame structure

| Поле / Field | Размер / Size | Описание / Description |
|---|---|---|
| Preamble | 8 bytes (64 bit) | RU: Синхронизация + сигнал начала фрейма · EN: Sync + start-of-frame signal |
| Destination MAC | 6 bytes (48 bit) | RU: Адрес получателя · EN: Recipient's address |
| Source MAC | 6 bytes (48 bit) | RU: Адрес отправителя · EN: Sender's address |
| EtherType (или VLAN header) | 16 bit | RU: Протокол содержимого · EN: Protocol of the contents |
| Data payload | 46–1500 bytes | RU: Полезные данные (IP, транспорт, приложение) · EN: Actual data (IP, transport, application layers) |
| Frame Check Sequence (FCS) | 4 bytes (32 bit) | RU: Контрольная сумма (CRC) · EN: Checksum (CRC) |

---

## Preamble
#preamble

RU: 8 байт (64 бита), делится на две части:
EN: 8 bytes (64 bits), split into two parts:

1. RU: Первые **7 байт** — чередующиеся единицы и нули. Служат буфером между фреймами и помогают сетевым интерфейсам синхронизировать внутренние часы (скорость передачи данных).
   EN: The first **7 bytes** — alternating ones and zeros. Act as a buffer between frames and help network interfaces sync their internal clocks (data transmission speed).
2. RU: Последний байт — **SFD (Start Frame Delimiter)**. Сигнализирует принимающему устройству, что преамбула закончилась и дальше идёт само содержимое фрейма.
   EN: The last byte — **SFD (Start Frame Delimiter)**. Signals to the receiving device that the preamble is over and actual frame content follows.

---

## MAC-адреса в фрейме · MAC addresses in the frame
#mac-addresses

RU: Сразу после SFD идёт **destination MAC** (адрес получателя), затем **source MAC** (адрес отправителя, откуда пришёл фрейм).
EN: Right after the SFD comes the **destination MAC** address, followed by the **source MAC** address (where the frame originated).

RU: Каждый MAC-адрес — 48 бит = 6 байт (см. [[Ethernet and MAC Addresses]]).
EN: Each MAC address is 48 bits = 6 bytes (see [[Ethernet and MAC Addresses]]).

---

## EtherType и VLAN
#ethertype #vlan

RU: **EtherType** — поле длиной 16 бит, описывает протокол содержимого фрейма (какой протокол используется в данных).
EN: **EtherType** — a 16-bit field describing the protocol of the frame's contents.

> [!note] VLAN header
> RU: Вместо EtherType может стоять **VLAN header** — он означает, что это **VLAN-фрейм**. Если VLAN header присутствует, поле EtherType идёт следом за ним.
> EN: Instead of EtherType, you may find a **VLAN header** — indicating this is a **VLAN frame**. If present, the EtherType field follows the VLAN header.
>
> RU: **VLAN (Virtual LAN)** — техника, позволяющая иметь несколько логических LAN на одном физическом оборудовании. Фрейм с VLAN-тегом будет отправлен только через интерфейсы свича, настроенные на этот конкретный тег.
> EN: **VLAN (Virtual LAN)** — a technique for running multiple logical LANs on the same physical equipment. A frame with a VLAN tag is only forwarded out of switch interfaces configured for that specific tag.
>
> RU: Используется для разделения разных видов трафика — например, IP-телефоны на одном VLAN, десктопы — на другом.
> EN: Used to segregate different types of traffic — e.g. a company's IP phones on one VLAN, desktops on another.

---

## Data payload
#payload

RU: **Payload** — сами передаваемые данные, всё, что не является заголовком (header).
EN: **Payload** — the actual data being transported, everything that isn't a header.

RU: Размер: от **46 до 1500 байт**. Содержит данные с более высоких уровней (IP, транспортный, прикладной).
EN: Size: **46 to 1500 bytes**. Contains data from higher layers (IP, transport, application).

---

## Frame Check Sequence (FCS) и CRC
#fcs #crc

RU: **FCS** — 4 байта (32 бита), контрольная сумма (checksum) всего фрейма.
EN: **FCS** — 4 bytes (32 bits), a checksum value for the entire frame.

RU: Вычисляется через **CRC (Cyclical Redundancy Check)** — циклическую избыточную проверку. Это математическое преобразование (полиномиальное деление), которое сжимает больший набор данных в одно число.
EN: Calculated via **CRC (Cyclical Redundancy Check)** — a mathematical transformation (polynomial division) that compresses a larger dataset into one number.

> [!example] Как это работает / How it works
> RU: **Отправитель**: собирает все поля фрейма (MAC-адреса, payload и т.д.) → вычисляет CRC → прикладывает результат как FCS в конец фрейма.
> EN: **Sender**: gathers all frame fields (MAC addresses, payload, etc.) → computes CRC → attaches the result as the FCS at the end of the frame.
>
> RU: **Получатель**: заново вычисляет CRC по полученным данным → сравнивает со значением в FCS.
> EN: **Receiver**: recomputes CRC over the received data → compares it to the value in the FCS.
>
> RU: Если суммы **не совпадают** → данные повреждены/потеряны при передаче → фрейм отбрасывается.
> EN: If the checksums **don't match** → data was corrupted/lost in transit → the frame is discarded.

> [!warning] Важно / Important
> RU: Ethernet только **обнаруживает** проблему целостности данных — он **не занимается** восстановлением данных. Решение о повторной отправке — задача протокола более высокого уровня.
> EN: Ethernet only **reports** on data integrity — it does **not** perform data recovery. Retransmission decisions are up to a higher-layer protocol.

---

> [!warning] Частые ошибки / Common mistakes
> - RU: Preamble = 8 байт (7 байт синхронизации + 1 байт SFD) · EN: Preamble = 8 bytes (7 sync bytes + 1 SFD byte)
> - RU: Payload — от 46 до 1500 байт, не любой размер · EN: Payload ranges from 46 to 1500 bytes, not arbitrary
> - RU: FCS = 4 байта / 32 бита, вычисляется через CRC · EN: FCS = 4 bytes / 32 bits, computed via CRC
> - RU: EtherType — 16 бит, показывает протокол содержимого, а не сам протокол данных · EN: EtherType is 16 bits and identifies the protocol of the contents
> - RU: VLAN header, если есть, идёт **перед** EtherType · EN: The VLAN header, when present, comes **before** EtherType
> - RU: Ethernet обнаруживает повреждение данных, но НЕ восстанавливает их · EN: Ethernet detects corruption but does NOT recover the data

---

## Флеш-карточки · Flashcards
#flashcards

Из скольки байт состоит preamble, и из каких частей? / How many bytes is the preamble, and what parts does it have?::RU: **Preamble (преамбула)** — 8 байт (64 бита), первая часть Ethernet-фрейма. Делится на: первые **7 байт** — чередующиеся единицы и нули, помогающие устройствам синхронизировать внутренние часы; последний байт — **SFD (Start Frame Delimiter)**, сигнализирующий об окончании преамбулы. EN: The **preamble** is 8 bytes (64 bits), the frame's first part. Split into: the first **7 bytes** — alternating 1s and 0s that help devices sync their clocks; the last byte — the **SFD**, signaling the preamble is over.
Какой диапазон размера payload у Ethernet-фрейма? / What's the payload size range of an Ethernet frame?::RU: **Payload (полезная нагрузка)** Ethernet-фрейма — от **46 до 1500 байт**; содержит данные с более высоких уровней (IP, транспортный, прикладной). EN: An Ethernet frame's **payload** ranges from **46 to 1500 bytes**; it contains data from higher layers (IP, transport, application).
Из скольки байт состоит FCS, и как он вычисляется? / How many bytes is the FCS, and how is it computed?::RU: **FCS (Frame Check Sequence)** — 4 байта (32 бита), контрольная сумма всего фрейма. Вычисляется через **CRC (Cyclical Redundancy Check)** — математическое преобразование (полиномиальное деление), сжимающее данные фрейма в одно число. EN: The **FCS (Frame Check Sequence)** is 4 bytes (32 bits), a checksum of the whole frame. It's computed via **CRC (Cyclical Redundancy Check)** — a mathematical transform (polynomial division) compressing the frame's data into one number.
Что делает Ethernet, если CRC на приёмнике не совпал с полученным FCS? / What does Ethernet do if the receiver's recomputed CRC doesn't match the received FCS?::RU: Если контрольные суммы **не совпадают**, значит данные были повреждены или потеряны при передаче — Ethernet **отбрасывает** такой фрейм. Важно: Ethernet только **обнаруживает** проблему целостности, но сам **не восстанавливает** данные — это задача протокола более высокого уровня. EN: If the checksums **don't match**, the data was corrupted or lost in transit — Ethernet **discards** the frame. Importantly, Ethernet only **detects** the integrity problem; it does **not** recover the data itself — that's a higher-layer protocol's job.
Где расположен VLAN header относительно EtherType, и зачем он вообще нужен? / Where is the VLAN header located relative to EtherType, and why does it exist?::RU: Если VLAN header присутствует, он идёт **перед** полем EtherType (которое следует сразу за ним). **VLAN (Virtual LAN)** — техника, позволяющая иметь несколько логических LAN на одном физическом оборудовании; фрейм с VLAN-тегом пересылается только через интерфейсы свича, настроенные на этот тег. EN: When present, the VLAN header comes **before** the EtherType field (which follows right after it). **VLAN** is a technique for running multiple logical LANs on the same physical equipment; a VLAN-tagged frame is only forwarded out of switch interfaces configured for that tag.
