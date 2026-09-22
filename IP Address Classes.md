---
tags: [networking, coursera, network-layer, ip-addressing, bilingual]
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

---

> [!warning] Частые ошибки / Common mistakes
> - RU: Class A — **1** октет под Network ID (не 3!), Class C — **3** октета под Network ID (не 1!) — легко перепутать · EN: Class A uses **1** octet for Network ID (not 3!), Class C uses **3** octets for Network ID (not 1!) — easy to mix up
> - RU: Class A имеет **больше всего** адресов (2²⁴), Class C — **меньше всего** из основных классов (2⁸) · EN: Class A has the **most** addresses (2²⁴), Class C the **fewest** among the main classes (2⁸)
> - RU: Диапазоны первого октета: A=0-127, B=128-191, C=192-223, D=224-239, E=240-255 · EN: First-octet ranges: A=0-127, B=128-191, C=192-223, D=224-239, E=240-255
> - RU: Class D — не "ещё один диапазон сетей", а специально для **multicast** · EN: Class D isn't "just another network range" — it's specifically for **multicast**
> - RU: Class E не назначается устройствам, только для тестов · EN: Class E is not assigned to devices, only used for testing
> - RU: Классовая система сегодня в основном вытеснена **CIDR** · EN: The class system has mostly been replaced today by **CIDR**
