---
tags: [networking, coursera, network-layer, subnetting, bilingual]
course: "Computer Networking (Google/Coursera)"
created: 2026-09-21
---

# Маски подсети · Subnet Masks

Связано: [[Subnetting Basics]] · [[IP Address Classes]] · [[IP Addresses Basics]]

---

## Третий ID: Subnet ID · The third ID: Subnet ID
#subnet-id

RU: Раньше мы знали два ID: **Network ID** (идентифицирует сеть) и **Host ID** (идентифицирует узел). Сабнеттинг добавляет третий — **Subnet ID**.
EN: Previously we knew two IDs: **Network ID** (identifies the network) and **Host ID** (identifies the host). Subnetting adds a third — **Subnet ID**.

RU: IP-адрес — 32-битное число (см. [[IP Addresses Basics]]). Без сабнеттинга часть битов — Network ID, остальные — Host ID. С сабнеттингом **часть битов, которые раньше принадлежали бы Host ID, теперь отдаются под Subnet ID**.
EN: An IP address is a 32-bit number (see [[IP Addresses Basics]]). Without subnetting, some bits are Network ID and the rest are Host ID. With subnetting, **some bits that would normally be part of the Host ID are used for the Subnet ID instead**.

> [!example] Путь доставки пакета / Packet delivery path
> RU: **Core-роутеры** интернета смотрят только на **Network ID**, отправляя датаграмму к нужному gateway router.
> EN: Internet **core routers** only care about the **Network ID**, forwarding the datagram to the right gateway router.
>
> RU: **Gateway router** использует дополнительную информацию (Subnet ID), чтобы направить датаграмму дальше — к целевой машине или следующему роутеру.
> EN: The **gateway router** uses additional info (the Subnet ID) to forward the datagram further — to the destination machine or the next router.
>
> RU: **Host ID** используется последним роутером на пути, чтобы доставить датаграмму конкретному получателю.
> EN: The **Host ID** is used by the final router on the path to deliver the datagram to the intended recipient machine.

---

## Что такое маска подсети · What a subnet mask is
#subnet-mask

RU: **Subnet ID** вычисляется через **subnet mask (маску подсети)**. Как и IP-адрес, маска — 32-битное число, обычно записывается как 4 десятичных октета.
EN: The **Subnet ID** is calculated via a **subnet mask**. Like an IP address, it's a 32-bit number, usually written as 4 decimal octets.

RU: Маска состоит из двух частей в двоичном виде: сначала идёт строка **единиц**, затем — строка **нулей**.
EN: In binary, a mask has two sections: a string of **ones** first, then a string of **zeros**.

- RU: **Единицы** — показывают, что нужно **игнорировать** при вычислении Host ID (это область Network ID + Subnet ID).
  EN: The **ones** — show what to **ignore** when computing the Host ID (this covers Network ID + Subnet ID).
- RU: **Нули** — показывают, что нужно **оставить** (это область Host ID).
  EN: The **zeros** — show what to **keep** (this is the Host ID area).

---

## Пример: 9.100.100.100 в двоичном виде · Binary example
#binary-example

RU: Каждый октет — 8 бит. Число `9` в двоичном виде: `1001`, дополняется нулями слева до 8 бит: **`00001001`**.
EN: Each octet is 8 bits. The number `9` in binary is `1001`, padded with leading zeros to 8 bits: **`00001001`**.

RU: Число `100` в двоичном виде: **`01100100`**.
EN: The number `100` in binary is: **`01100100`**.

---

## Как найти Subnet ID и Host ID · Finding the Subnet ID and Host ID
#calculation

> [!example] Маска 255.255.255.0 / Mask 255.255.255.0
> RU: В двоичном виде это **24 единицы, затем 8 нулей**.
> EN: In binary, this is **24 ones followed by 8 zeros**.
>
> RU: Для `9.100.100.100` (Class A) мы уже знаем Network ID — это первый октет (`9`, см. [[IP Address Classes]]). Остаются последние три октета.
> EN: For `9.100.100.100` (Class A), we already know the Network ID — the first octet (`9`, see [[IP Address Classes]]). That leaves the last three octets.
>
> RU: Сопоставляем оставшиеся октеты с маской побитово: биты, где в маске стоит **1** — это **Subnet ID**. Биты, где в маске стоит **0** — это **Host ID**.
> EN: Line up the remaining octets against the mask bit by bit: bits where the mask has a **1** are the **Subnet ID**. Bits where the mask has a **0** are the **Host ID**.

---

## Размер подсети зависит от маски · Subnet size depends on the mask
#subnet-size

RU: Размер подсети полностью определяется маской. С маской `255.255.255.0` только **последний октет** доступен под Host ID (8 бит = 256 значений: 0-255) — независимо от того, как распределены остальные биты между сетью и subnet ID.
EN: Subnet size is entirely defined by the mask. With mask `255.255.255.0`, only the **last octet** is available for host IDs (8 bits = 256 values: 0-255) — regardless of how the rest is split between network and subnet ID.

> [!warning] Формула доступных адресов узлов / Available host address formula
> RU: Общее число адресов = 2ⁿ (n = количество нулевых бит). Но из них обычно **вычитают 2**:
> EN: Total addresses = 2ⁿ (n = number of zero bits). But **2 are usually subtracted**:
>
> - RU: **0** (все нули в host-части) обычно не используется.
>   EN: **0** (all-zeros host part) is generally not used.
> - RU: **255** (все единицы в host-части, для маски /24) зарезервировано как **broadcast-адрес** подсети.
>   EN: **255** (all-ones host part, for a /24 mask) is reserved as the subnet's **broadcast address**.
>
> RU: Для маски `255.255.255.0`: диапазон 0-255, но реально узлам можно назначить только **1-254**.
> EN: For mask `255.255.255.0`: range is 0-255, but only **1-254** can actually be assigned to hosts.

> [!note] Как это принято называть / How this is conventionally described
> RU: Несмотря на правило "минус 2", при описании размера подсети всё равно говорят про **полное** число адресов (например, "8 бит host ID = 256 адресов", а не 254) — потому что остальные IP всё ещё существуют как адреса, просто не назначаются напрямую узлу.
> EN: Despite the "minus 2" rule, subnet size is still described using the **full** address count (e.g. "8 bits of host ID = 256 addresses", not 254) — because those other IPs still exist as addresses, they're just not directly assigned to a node.

---

## Маски, не выровненные по октету · Masks not aligned to an octet
#non-octet-mask

> [!example] Маска 255.255.255.224 / Mask 255.255.255.224
> RU: В двоичном виде: **27 единиц, затем 5 нулей**.
> EN: In binary: **27 ones, followed by 5 zeros**.
>
> RU: 5 бит под Host ID → 2⁵ = **32 адреса** в подсети.
> EN: 5 bits of Host ID → 2⁵ = **32 addresses** in the subnet.

---

## CIDR-нотация (сокращённая запись маски) · CIDR notation
#cidr-notation

RU: Вместо записи полной маски можно использовать **сокращённую нотацию** — число единиц в маске после слэша.
EN: Instead of writing out the full mask, you can use **shorthand notation** — the number of ones in the mask, after a slash.

> [!example]
> RU: Маска `255.255.255.224` = 27 единиц → записывается как **`/27`**.
> EN: Mask `255.255.255.224` = 27 ones → written as **`/27`**.
>
> RU: Вместе с IP: `9.100.100.100/27`.
> EN: Combined with the IP: `9.100.100.100/27`.

> [!note]
> RU: Обе формы записи (полная маска и `/N`) одинаково распространены — важно понимать обе.
> EN: Neither notation is more common than the other — it's important to understand both.

---

> [!warning] Частые ошибки / Common mistakes
> - RU: В маске единицы = "игнорировать" (Network+Subnet ID), нули = "оставить" (Host ID) — легко перепутать местами · EN: In a mask, ones = "ignore" (Network+Subnet ID), zeros = "keep" (Host ID) — easy to mix up
> - RU: Количество адресов в подсети = 2 в степени количества **нулевых** бит маски, не единичных · EN: Number of addresses in a subnet = 2 to the power of the number of **zero** bits in the mask, not the ones
> - RU: Из общего числа адресов обычно вычитают 2 (network address + broadcast), но размер подсети всё равно называют полным числом · EN: 2 addresses are typically subtracted (network address + broadcast), but subnet size is still stated as the full number
> - RU: `/N` в CIDR-нотации — это количество **единиц** в маске (длина префикса), а не нулей · EN: The `/N` in CIDR notation is the number of **ones** in the mask (prefix length), not zeros
> - RU: Маска не обязана совпадать с границами октетов (например, `/27` режет внутри последнего октета) · EN: A mask doesn't have to align with octet boundaries (e.g. `/27` cuts inside the last octet)
