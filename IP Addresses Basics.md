---
tags: [networking, coursera, network-layer, ip-addressing, bilingual]
course: "Computer Networking (Google/Coursera)"
created: 2026-09-21
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
