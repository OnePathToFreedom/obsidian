---
tags: [networking, coursera, network-layer, ip-addressing, bilingual, flashcards, review]
course: "Computer Networking (Google/Coursera)"
created: 2026-09-21
---

# Классы IP-адресов · IP Address Classes

Связано: [[IP Addresses Basics]] · [[IP Datagram Structure]] · [[TCP-IP Model]]

---

## Network ID и Host ID
#network-id #host-id

RU: IP-адрес делится на две части: **Network ID** (идентификатор сети) и **Host ID** (идентификатор узла).
EN: An IP address splits into two sections: the **Network ID** and the **Host ID**.

> [!example] Пример / Example
> RU: IBM владеет всеми адресами с первым октетом = 9 (см. [[IP Addresses Basics]]). Для адреса `9.100.100.100`: Network ID = `9` (первый октет), Host ID = `100.100.100` (три оставшихся октета).
> EN: IBM owns all addresses with 9 as the first octet (see [[IP Addresses Basics]]). For `9.100.100.100`: Network ID = `9` (first octet), Host ID = `100.100.100` (remaining three octets).

---

## Система адресных классов · The address class system
#address-classes

RU: Способ деления глобального адресного пространства IP. Три основных класса — **A, B, C**, плюс два специальных — **D, E**.
EN: A way of splitting up the global IP address space. Three primary classes — **A, B, C** — plus two special ones — **D, E**.

| Класс / Class | Октеты под Network ID / Network ID octets | Октеты под Host ID / Host ID octets | Первые биты / Leading bits | Диапазон 1-го октета / 1st octet range |
|---|---|---|---|---|
| A | 1 | 3 | `0` | 0–127 |
| B | 2 | 2 | `10` | 128–191 |
| C | 3 | 1 | `110` | 192–223 |
| D (multicast) | — | — | `1110` | 224–239 |
| E (тест / test) | — | — | остальное / remainder | 240–255 |

---

## Class A / B / C — размер сети · Network size

RU: Чем больше октетов под Host ID — тем **больше** возможных адресов в сети (больше устройств может быть в одной сети).
EN: The more octets given to the Host ID — the **more** possible addresses the network has (more devices can fit in one network).

> [!example] Расчёт количества адресов / Calculating address count
> RU: **Class A**: 24 бита под Host ID → 2²⁴ = **16 777 216** адресов.
> EN: **Class A**: 24 bits of Host ID → 2²⁴ = **16,777,216** addresses.
>
> RU: **Class C**: 8 бит под Host ID → 2⁸ = **256** адресов.
> EN: **Class C**: 8 bits of Host ID → 2⁸ = **256** addresses.

---

## Как определить класс по битам / по десятичной записи · Identifying the class

RU: Класс адреса можно определить прямо по первым битам:
EN: You can identify an address's class right from its leading bits:

- RU: Первый бит = `0` → **Class A**
  EN: First bit = `0` → **Class A**
- RU: Первые биты = `10` → **Class B**
  EN: First bits = `10` → **Class B**
- RU: Первые биты = `110` → **Class C**
  EN: First bits = `110` → **Class C**
- RU: Первые биты = `1110` → **Class D** (multicast)
  EN: First bits = `1110` → **Class D** (multicast)

> [!note] В десятичной записи (dotted decimal) / In dotted decimal
> RU: Поскольку октет = 8 бит = значение 0-255, ограничение по первому биту переводится в диапазон значений первого октета:
> EN: Since an octet is 8 bits = value 0-255, the leading-bit restriction translates into a range for the first octet's value:
>
> - Class A: **0–127**
> - Class B: **128–191**
> - Class C: **192–223**
> - Class D: **224–239** (multicast)
> - Class E: **240–255** (не назначено, только для тестов / unassigned, testing only)

---

## Class D и Class E
#class-d #class-e

RU: **Class D** — всегда начинается с битов `1110` (десятично: 224–239). Используется для **multicasting** — способа отправить одну IP-датаграмму сразу целой группе получателей.
EN: **Class D** — always begins with bits `1110` (decimal: 224–239). Used for **multicasting** — a way to send a single IP datagram to an entire group at once.

RU: **Class E** — оставшиеся адреса (240–255). Не назначены, используются только для тестирования.
EN: **Class E** — the remaining addresses (240–255). Unassigned, used only for testing purposes.

---

## Актуальность сегодня · Relevance today
#cidr

RU: На практике система классов в основном заменена системой **CIDR (Classless Inter-Domain Routing)**. Но сама классовая система всё ещё применяется местами и важна для понимания основ сетей.
EN: In practical terms, the class system has mostly been replaced by **CIDR (Classless Inter-Domain Routing)**. But the class system is still in place in many ways and matters for a well-rounded networking foundation.

### Почему появился CIDR · Why CIDR was introduced

RU: Классовая система создавала две конкретные проблемы:
EN: The class system created two specific problems:

1. RU: **Расточительность адресов.** Компании с 500 узлами не хватало Class C (256 адресов), приходилось брать целый Class B (65 536 адресов) — десятки тысяч адресов пропадали неиспользованными.
   EN: **Address waste.** A company with 500 hosts couldn't fit in a Class C (256 addresses) and had to take a whole Class B (65,536 addresses) — tens of thousands of addresses went unused.
2. RU: **Раздутие таблиц маршрутизации.** Каждая отдельно выданная сеть — отдельная запись в таблице core-роутеров интернета. Рост числа сетей делал эти таблицы слишком большими.
   EN: **Routing table bloat.** Each individually issued network is a separate entry in internet core routers' tables. As the number of networks grew, these tables became too large.

RU: **CIDR** решает обе проблемы: маску можно резать **в любом месте** (не только по границам октета — см. пример `/27` в [[Subnet Masks]]), выделяя блок ровно под нужный размер. Это также называют **VLSM (Variable Length Subnet Masking)** — подсети внутри одной организации могут быть **разного размера**.
EN: **CIDR** solves both: the mask can be cut **anywhere** (not just at octet boundaries — see the `/27` example in [[Subnet Masks]]), allocating a block sized exactly to need. This is also called **VLSM (Variable Length Subnet Masking)** — subnets within one organization can be **different sizes**.

> [!example] Route aggregation (супернеттинг) / Route aggregation
> RU: Если провайдер владеет 256 смежными блоками `/24`, он может анонсировать их core-роутерам **одной записью** `/16` вместо 256 отдельных строк — резко сокращая размер таблицы маршрутизации.
> EN: If a provider owns 256 contiguous `/24` blocks, it can advertise them to core routers as **one** `/16` entry instead of 256 separate rows — drastically shrinking the routing table.

---

> [!warning] Частые ошибки / Common mistakes
> - RU: Class A — **1** октет под Network ID (не 3!), Class C — **3** октета под Network ID (не 1!) — легко перепутать · EN: Class A uses **1** octet for Network ID (not 3!), Class C uses **3** octets for Network ID (not 1!) — easy to mix up
> - RU: Class A имеет **больше всего** адресов (2²⁴), Class C — **меньше всего** из основных классов (2⁸) · EN: Class A has the **most** addresses (2²⁴), Class C the **fewest** among the main classes (2⁸)
> - RU: Диапазоны первого октета: A=0-127, B=128-191, C=192-223, D=224-239, E=240-255 · EN: First-octet ranges: A=0-127, B=128-191, C=192-223, D=224-239, E=240-255
> - RU: Class D — не "ещё один диапазон сетей", а специально для **multicast** · EN: Class D isn't "just another network range" — it's specifically for **multicast**
> - RU: Class E не назначается устройствам, только для тестов · EN: Class E is not assigned to devices, only used for testing
> - RU: Классовая система сегодня в основном вытеснена **CIDR** · EN: The class system has mostly been replaced today by **CIDR**

---

## Флеш-карточки · Flashcards
#flashcards

Сколько октетов под Network ID у Class A, и сколько адресов это даёт? / How many octets does Class A use for the Network ID, and how many addresses does that give?::RU: **Class A** отдаёт под Network ID всего **1 октет** (первый бит адреса = `0`, диапазон первого октета 0–127), а оставшиеся **3 октета** (24 бита) — под Host ID → 2²⁴ = **16 777 216** адресов на сеть. EN: **Class A** uses just **1 octet** for the Network ID (leading bit `0`, first-octet range 0–127), leaving **3 octets** (24 bits) for the Host ID → 2²⁴ = **16,777,216** addresses per network.
Сколько октетов под Network ID у Class C, и сколько адресов это даёт? / How many octets does Class C use for the Network ID, and how many addresses does that give?::RU: **Class C**, наоборот, отдаёт под Network ID **3 октета** (первые биты `110`, диапазон 192–223), оставляя всего **1 октет** (8 бит) под Host ID → 2⁸ = **256** адресов на сеть — самое маленькое число среди основных классов. EN: **Class C** uses **3 octets** for the Network ID (leading bits `110`, range 192–223), leaving just **1 octet** (8 bits) for the Host ID → 2⁸ = **256** addresses per network — the smallest among the main classes.
Какой диапазон первого октета у Class B, и как это связано с ведущими битами? / What's Class B's first-octet range, and how does that relate to its leading bits?::RU: **Class B** — первые биты адреса `10`, диапазон первого октета **128–191**; под Network ID отводится 2 октета, под Host ID — тоже 2 октета (65 534 доступных адреса). EN: **Class B** — leading bits `10`, first-octet range **128–191**; 2 octets go to Network ID, 2 octets to Host ID (65,534 usable addresses).
Для чего используется Class D, и как его узнать? / What is Class D used for, and how do you recognize it?::RU: **Class D** (диапазон 224–239, ведущие биты `1110`) используется для **multicast** — способа отправить одну IP-датаграмму сразу целой группе получателей. Это не "ещё один диапазон сетей", а специальное назначение. EN: **Class D** (range 224–239, leading bits `1110`) is used for **multicast** — sending a single IP datagram to an entire group of recipients at once. It's not "just another network range" — it's a special-purpose class.
Чем CIDR отличается от классовой системы (A/B/C/D/E)? / How does CIDR differ from the class-based system (A/B/C/D/E)?::RU: Классовая система жёстко привязывает размер сети к границам октетов. **CIDR (Classless Inter-Domain Routing)** позволяет резать маску **в любом месте** (например `/27` — внутри последнего октета), выделяя блок ровно под нужный размер сети — отсюда и "classless" (безклассовый). EN: The class system rigidly ties network size to octet boundaries. **CIDR** lets you cut the mask **anywhere** (e.g. `/27` inside the last octet), allocating a block sized exactly to need — hence "classless."
Что такое route aggregation (супернеттинг) в контексте CIDR? / What is route aggregation (supernetting) in the context of CIDR?::RU: **Route aggregation** — объединение множества смежных сетевых блоков в **одну** запись маршрутизации. Например, 256 смежных блоков `/24` можно анонсировать core-роутерам одной записью `/16`, резко сокращая размер таблицы маршрутизации. EN: **Route aggregation** combines many contiguous network blocks into a **single** routing table entry. E.g. 256 contiguous `/24` blocks can be advertised to core routers as one `/16` entry, drastically shrinking the routing table.
