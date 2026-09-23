---
tags: [networking, coursera, network-layer, ip-addressing, bilingual, flashcards, review]
course: "Computer Networking (Google/Coursera)"
created: 2026-09-21
---

# Структура IP-датаграммы · IP Datagram Structure

Связано: [[IP Addresses Basics]] · [[Ethernet Frame Structure]] · [[TCP-IP Model]]

RU: Так же, как пакеты на Ethernet-уровне называются **Ethernet-фреймами**, пакеты на уровне IP называются **IP datagram (IP-датаграмма)**.
EN: Just like packets at the Ethernet layer are called **Ethernet frames**, packets under the IP protocol are called **IP datagrams**.

RU: Как и Ethernet-фрейм, IP-датаграмма — строго структурированный набор полей. Две главные секции: **header (заголовок)** и **payload (полезная нагрузка)**.
EN: Like an Ethernet frame, an IP datagram is a highly structured series of strictly defined fields. The two primary sections: **header** and **payload**.

> [!note]
> RU: Заголовок IP-датаграммы содержит намного больше данных, чем заголовок Ethernet-фрейма.
> EN: An IP datagram header contains a lot more data than an Ethernet frame header.

---

## Поля заголовка IP-датаграммы (IPv4) · IPv4 header fields

| Поле / Field | Размер / Size | Описание / Description |
|---|---|---|
| Version | 4 bit | RU: Версия IP (обычно IPv4) · EN: IP version in use (usually IPv4) |
| Header Length (IHL) | 4 bit | RU: Длина заголовка, обычно 20 байт (минимум) · EN: Header length, usually 20 bytes (the minimum) |
| Service Type (ToS) | 8 bit | RU: Детали QoS (Quality of Service) · EN: Quality of Service (QoS) details |
| Total Length | 16 bit | RU: Общая длина всей датаграммы · EN: Total length of the datagram |
| Identification | 16 bit | RU: Группирует части одной передачи · EN: Groups fragments of the same transmission |
| Flags | — | RU: Разрешена ли фрагментация / уже фрагментирован ли пакет · EN: Whether fragmentation is allowed / already fragmented |
| Fragmentation Offset | — | RU: Порядок сборки фрагментов · EN: Order for reassembling fragments |
| Time to Live (TTL) | 8 bit | RU: Сколько router hops осталось · EN: How many router hops remain |
| Protocol | 8 bit | RU: Протокол транспортного уровня (TCP/UDP) · EN: Transport-layer protocol (TCP/UDP) |
| Header Checksum | — | RU: Контрольная сумма заголовка · EN: Checksum of the header |
| Source IP Address | 32 bit | RU: IP-адрес отправителя · EN: Sender's IP address |
| Destination IP Address | 32 bit | RU: IP-адрес получателя · EN: Recipient's IP address |
| IP Options | — | RU: Опционально, для тестирования · EN: Optional, mostly for testing |
| Padding | — | RU: Нули, чтобы выровнять размер заголовка · EN: Zeros, to pad the header to correct size |

---

## Version и Header Length
#version #ihl

RU: **Version** — 4 бита, указывает версию IP. Самая распространённая — **IPv4**, но **IPv6** активно набирает популярность.
EN: **Version** — 4 bits, indicates the IP version in use. The most common is **IPv4**, but **IPv6** is seeing rapid adoption.

RU: **Header Length** — тоже 4 бита, указывает длину всего заголовка. Для IPv4 почти всегда **20 байт** — это одновременно и минимальная длина заголовка (меньше физически невозможно уместить нужные данные).
EN: **Header Length** — also 4 bits, declares the length of the entire header. For IPv4 it's almost always **20 bytes** — also the minimum possible header length.

---

## Service Type (QoS)
#qos

RU: 8 бит, задают детали **Quality of Service (QoS)** — технологий, позволяющих роутерам определять, какая датаграмма важнее других.
EN: 8 bits used to specify **Quality of Service (QoS)** details — technologies letting routers decide which datagram may be more important than others.

---

## Total Length, Identification, Fragmentation
#fragmentation

RU: **Total Length** — 16 бит, общая длина датаграммы.
EN: **Total Length** — 16 bits, the total length of the datagram.

> [!example] Максимальный размер датаграммы / Max datagram size
> RU: Поле Total Length — 16 бит → максимум = 2¹⁶ − 1 = **65 535 байт**. Больше в одну датаграмму не помещается.
> EN: The Total Length field is 16 bits → max = 2¹⁶ − 1 = **65,535 bytes**. That's the largest a single datagram can be.

RU: **Identification** — 16-битное число, группирующее сообщения вместе. Если данных больше, чем помещается в одну датаграмму, IP-уровень разбивает их на несколько пакетов — и все пакеты с одинаковым значением Identification принадлежат одной передаче.
EN: **Identification** — a 16-bit number used to group messages together. If data is too large for one datagram, the IP layer splits it into several packets — packets sharing the same Identification value belong to the same transmission.

RU: **Fragmentation** — процесс разбиения одной IP-датаграммы на несколько меньших. Происходит, когда датаграмма переходит из сети с большим допустимым размером в сеть с меньшим.
EN: **Fragmentation** — the process of splitting one IP datagram into several smaller ones. Happens when a datagram crosses from a network allowing larger datagrams into one allowing smaller ones.

- RU: **Flags field** — указывает, разрешена ли фрагментация датаграммы, или что она уже была фрагментирована.
  EN: **Flags field** — indicates whether fragmentation is allowed, or that the datagram has already been fragmented.
- RU: **Fragmentation Offset field** — содержит значения, по которым принимающая сторона собирает фрагменты в правильном порядке.
  EN: **Fragmentation Offset field** — contains values the receiving end uses to reassemble fragments in the correct order.

---

## Time to Live (TTL)
#ttl

RU: 8-битное поле, указывающее, сколько **router hops** (переходов через роутеры) датаграмма может пройти, прежде чем будет отброшена.
EN: An 8-bit field indicating how many **router hops** a datagram can traverse before being discarded.

RU: Каждый роутер, через который проходит датаграмма, **уменьшает TTL на 1**. Когда значение достигает нуля — роутер больше не пересылает датаграмму дальше.
EN: Every router the datagram passes through **decrements TTL by 1**. Once it reaches zero, the router stops forwarding the datagram.

> [!note] Зачем нужен TTL / Why TTL exists
> RU: Основная цель — предотвратить бесконечное блуждание датаграммы при ошибке маршрутизации (например, петля: роутер A думает, что следующий хоп — B, а B думает, что следующий хоп — A).
> EN: Its main purpose is to prevent a datagram from looping forever due to a routing misconfiguration (e.g. router A thinks B is the next hop, and B thinks A is the next hop).

---

## Protocol и Header Checksum
#protocol-field #checksum

RU: **Protocol** — 8 бит, указывает, какой протокол **транспортного уровня** используется (чаще всего TCP или UDP).
EN: **Protocol** — 8 bits, indicates which **transport-layer** protocol is in use (most commonly TCP or UDP).

RU: **Header Checksum** — контрольная сумма всего заголовка датаграммы. Работает похоже на checksum-поле Ethernet-фрейма ([[Ethernet Frame Structure]]).
EN: **Header Checksum** — a checksum of the entire datagram header. Works similarly to the Ethernet frame's checksum field ([[Ethernet Frame Structure]]).

> [!note]
> RU: Поскольку TTL пересчитывается на **каждом** роутере, checksum тоже приходится пересчитывать заново на каждом хопе.
> EN: Since TTL is recomputed at every router, the checksum necessarily changes at every hop too.

---

## Source / Destination IP + IP Options + Padding
#addresses

RU: **Source IP** и **Destination IP** — по 32 бита каждый (напомним: IP-адрес = 32-битное число, см. [[IP Addresses Basics]]).
EN: **Source IP** and **Destination IP** — 32 bits each (recall: an IP address is a 32-bit number, see [[IP Addresses Basics]]).

RU: **IP Options** — опциональное поле, задаёт особые характеристики датаграммы, в основном для тестирования.
EN: **IP Options** — an optional field, used to set special datagram characteristics, mostly for testing purposes.

RU: **Padding** — поле из нулей, дополняющее заголовок до нужного размера (нужно, т.к. IP Options опционально и переменной длины).
EN: **Padding** — a field of zeros, padding the header to the correct total size (needed because IP Options is optional and variable-length).

---

## Инкапсуляция · Encapsulation
#encapsulation

RU: Вся IP-датаграмма целиком становится **payload (полезной нагрузкой)** Ethernet-фрейма — этот процесс называется **инкапсуляцией**.
EN: The entire IP datagram becomes the **payload** of an Ethernet frame — this process is called **encapsulation**.

RU: У самой IP-датаграммы тоже есть payload — и его содержимое, в свою очередь, это целиком **TCP- или UDP-пакет**.
EN: The IP datagram also has its own payload — and its contents are, in turn, an entire **TCP or UDP packet**.

> [!example] Матрёшка уровней / Layered "nesting doll"
> ```
> Ethernet Frame
> └── payload = IP Datagram
>     └── payload = TCP/UDP Packet
>         └── payload = application data
> ```
> RU: Именно поэтому мы говорим о сетях **уровнями** — каждый уровень нужен тому, что находится над ним.
> EN: This is exactly why networking is discussed in terms of **layers** — each layer is needed for the one above it.

---

> [!warning] Частые ошибки / Common mistakes
> - RU: Минимальная длина заголовка IPv4 — **20 байт**, не меньше · EN: The minimum IPv4 header length is **20 bytes**, not less
> - RU: Максимальный размер одной датаграммы — **65 535 байт** (16-битное поле Total Length) · EN: Max size of a single datagram is **65,535 bytes** (16-bit Total Length field)
> - RU: TTL уменьшается на 1 на **каждом** роутере, а не только один раз · EN: TTL decrements by 1 at **every** router, not just once
> - RU: Checksum пересчитывается на каждом хопе, т.к. TTL меняется · EN: The checksum is recomputed at every hop because TTL changes
> - RU: Protocol field указывает транспортный протокол (TCP/UDP), Version field — версию IP · EN: The Protocol field identifies the transport protocol (TCP/UDP); the Version field identifies the IP version — don't mix them up
> - RU: Инкапсуляция: Ethernet-фрейм ⊃ IP-датаграмма ⊃ TCP/UDP-пакет · EN: Encapsulation nesting: Ethernet frame ⊃ IP datagram ⊃ TCP/UDP packet

---

## Флеш-карточки · Flashcards
#flashcards

Какая минимальная длина заголовка IPv4, и какое поле её задаёт? / What's the minimum IPv4 header length, and which field declares it?::RU: Поле **Header Length (IHL)**, 4 бита, указывает длину заголовка — для IPv4 почти всегда **20 байт**. Это одновременно и минимальная длина: меньше физически невозможно уместить обязательные поля. EN: The **Header Length (IHL)** field, 4 bits, declares the header's length — for IPv4 almost always **20 bytes**. This is also the minimum: fewer bytes can't physically hold the required fields.
Какой максимальный размер одной IP-датаграммы, и откуда берётся это число? / What's the max size of a single IP datagram, and where does that number come from?::RU: Максимум — **65 535 байт**. Он определяется полем **Total Length**, которое занимает 16 бит: 2¹⁶ − 1 = 65 535. Больше в одну датаграмму физически не помещается. EN: The max is **65,535 bytes**, set by the **Total Length** field, which is 16 bits: 2¹⁶ − 1 = 65,535. A single datagram can't be larger.
Что делает поле TTL, и что происходит, когда оно достигает 0? / What does the TTL field do, and what happens when it reaches 0?::RU: **TTL (Time to Live)**, 8 бит, задаёт, сколько **router hops** (переходов через роутеры) датаграмма может пройти. Каждый роутер уменьшает TTL на 1; при достижении **0** роутер прекращает пересылку. Цель — предотвратить бесконечное блуждание датаграммы при ошибке маршрутизации (например, при петле). EN: **TTL (Time to Live)**, 8 bits, sets how many **router hops** a datagram may traverse. Each router decrements it by 1; at **0** the router stops forwarding. Its purpose is preventing an infinite loop from a routing misconfiguration.
Почему checksum IP-датаграммы пересчитывается на каждом роутере? / Why is the IP datagram's header checksum recomputed at every router?::RU: Потому что поле **TTL** уменьшается на каждом хопе, а **Header Checksum** — это контрольная сумма всего заголовка, включая TTL. Раз TTL меняется — checksum обязательно нужно пересчитать заново. EN: Because the **TTL** field is decremented at every hop, and the **Header Checksum** covers the entire header, including TTL. Since TTL changes, the checksum has to be recomputed each time.
Опиши порядок инкапсуляции от Ethernet-фрейма до данных приложения. / Describe the encapsulation order from the Ethernet frame down to application data.::RU: Это "матрёшка" уровней: **Ethernet Frame ⊃ IP Datagram ⊃ TCP/UDP Packet ⊃ Application data** — то есть вся IP-датаграмма становится payload Ethernet-фрейма, а внутри самой датаграммы её payload — это целиком TCP- или UDP-пакет, и так далее. EN: It's a layered "nesting doll": **Ethernet Frame ⊃ IP Datagram ⊃ TCP/UDP Packet ⊃ Application data** — the entire IP datagram becomes the Ethernet frame's payload, and the datagram's own payload is, in turn, an entire TCP or UDP packet, and so on.
