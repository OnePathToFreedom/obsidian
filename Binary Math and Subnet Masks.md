---
tags: [networking, coursera, binary, subnetting, bilingual, flashcards, review]
course: "Computer Networking (Google/Coursera)"
created: 2026-09-21
---

# Бинарная математика и маски подсети · Binary Math and Subnet Masks

Связано: [[Subnet Masks]] · [[Subnetting Basics]] · [[IP Addresses Basics]]

---

## Счёт в двоичной системе · Counting in binary
#binary-counting

RU: Числа — универсальны, различаются только **системы счисления** (нотации) для их записи. Десятичная система (**base 10**) использует 10 цифр (0-9) — вероятно, потому что у людей 10 пальцев.
EN: Numbers are universal — only the **notations** for referencing them differ. Decimal (**base 10**) uses 10 numerals (0-9) — likely because most people have 10 fingers.

RU: Компьютерам проще работать только с 0 и 1 (из-за устройства логических элементов процессора) — это **двоичная система (binary, base 2)**.
EN: Computers find it easier to work only with 0 and 1 (due to how logic gates work) — this is **binary (base 2)**.

RU: Принцип счёта одинаковый что в десятичной, что в двоичной системе: когда цифры в столбце заканчиваются — добавляется новый столбец слева. Просто в binary цифр всего две.
EN: The counting principle is the same in decimal and binary: when you run out of digits in a column, you add a new column to the left. Binary just has only two digits to work with.

> [!example] Счёт от 0 до 7 / Counting 0 to 7
> | Decimal | Binary |
> |---|---|
> | 0 | 0 |
> | 1 | 1 |
> | 2 | 10 |
> | 3 | 11 |
> | 4 | 100 |
> | 5 | 101 |
> | 6 | 110 |
> | 7 | 111 |

---

## Сколько чисел представляет N бит · How many numbers N bits can represent
#bit-math

RU: Формула: **2ⁿ**, где n — количество бит.
EN: Formula: **2ⁿ**, where n is the number of bits.

- RU: 8 бит → 2⁸ = **256** чисел (0-255)
  EN: 8 bits → 2⁸ = **256** numbers (0-255)
- RU: 4 бита → 2⁴ = **16** чисел
  EN: 4 bits → 2⁴ = **16** numbers
- RU: 16 бит → 2¹⁶ = **65 536** чисел
  EN: 16 bits → 2¹⁶ = **65,536** numbers

> [!note] Это работает для любой системы счисления / This works for any base
> RU: Формула на самом деле общая: **(основание)^(число разрядов)**. Например, 2 разряда в десятичной системе: 10² = 100 чисел (0-99). 3 разряда: 10³ = 1000 чисел (0-999).
> EN: The formula generalizes: **base^(number of digits)**. E.g. 2 decimal digits: 10² = 100 numbers (0-99). 3 digits: 10³ = 1000 numbers (0-999).

---

## Двоичное сложение · Binary addition
#binary-addition

RU: Всего 4 возможных случая (проще, чем в десятичной системе!):
EN: Only 4 possible cases (simpler than decimal!):

```
0 + 0 = 0
0 + 1 = 1
1 + 0 = 1
1 + 1 = 10   (перенос в следующий разряд / carry to next column)
```

RU: Перенос в binary происходит при достижении **2** (не 10, как в десятичной).
EN: The carry in binary happens upon reaching **2** (not 10, as in decimal).

---

## Логические операторы OR и AND · Logical operators OR and AND
#or #and

RU: В компьютерной логике: `1` = true (истина), `0` = false (ложь).
EN: In computer logic: `1` = true, `0` = false.

### OR
RU: Результат = true, если **хотя бы одно** из значений true.
EN: Result = true if **at least one** value is true.

```
1 OR 0 = 1
0 OR 0 = 0
1 OR 1 = 1
```

### AND
RU: Результат = true, только если **оба** значения true.
EN: Result = true only if **both** values are true.

```
1 AND 1 = 1
1 AND 0 = 0
0 AND 0 = 0
```

---

## Как это связано с маской подсети · How this relates to subnet masks
#and-subnet-mask

RU: Маска подсети — это способ для компьютера использовать оператор **AND**, чтобы определить, находится ли IP-адрес **в той же сети**.
EN: A subnet mask is a way for a computer to use the **AND** operator to determine whether an IP address is **on the same network**.

RU: Если сложить (AND) IP-адрес и маску побитово — результат покажет **Network ID + Subnet ID**. Всё, что "выпало" (не совпало) — это Host ID.
EN: ANDing the IP address and the mask bit-by-bit gives the **Network ID + Subnet ID**. Whatever's left out is the Host ID.

> [!example] Пример: 9.100.100.100 AND 255.255.255.0 / Example
> RU: Побитовый AND между двоичным IP и двоичной маской:
> EN: Bitwise AND between the binary IP and the binary mask:
>
> ```
>   IP:    9.100.100.100
>   Mask:  255.255.255.0
>   -------------------------
>   AND:   9.100.100.0
> ```
>
> RU: Результат AND-операции — `9.100.100.0` — это Network ID + Subnet ID этого адреса.
> EN: The AND result — `9.100.100.0` — is this address's Network ID + Subnet ID.
>
> RU: Компьютер сравнивает этот результат со своим собственным network ID, чтобы понять: адрес в той же сети или в другой.
> EN: The computer compares this result with its own network ID to determine whether the address is on the same network or a different one.

---

> [!warning] Частые ошибки / Common mistakes
> - RU: Перенос разряда в binary происходит при достижении **2** (не 10) · EN: Binary carries at **2** (not 10)
> - RU: Формула количества чисел — 2ⁿ, где n = **число бит**, а не значение числа · EN: The count formula is 2ⁿ, where n = **number of bits**, not the number's value
> - RU: OR — истина, если хотя бы один true; AND — истина, только если **оба** true · EN: OR is true if at least one is true; AND is true only if **both** are true
> - RU: Маска подсети применяется через **AND**, а не OR · EN: The subnet mask is applied via **AND**, not OR
> - RU: Результат AND(IP, маска) = Network ID + Subnet ID, а не просто Network ID · EN: AND(IP, mask) result = Network ID + Subnet ID, not just Network ID

---

## Флеш-карточки · Flashcards
#flashcards

При каком значении происходит перенос разряда в двоичном сложении, и чем это отличается от десятичной системы? / At what value does binary addition carry to the next column, and how does that differ from decimal?::RU: В **двоичной системе (binary)** перенос в следующий разряд происходит при достижении **2** (`1 + 1 = 10`), тогда как в десятичной — при достижении **10**. Принцип счёта одинаков в обеих системах: когда цифры в столбце заканчиваются, добавляется новый столбец слева — просто в binary всего две цифры (0 и 1). EN: In **binary**, the carry happens at **2** (`1 + 1 = 10`), whereas in decimal it happens at **10**. The counting principle is the same in both: when a column runs out of digits, a new column is added on the left — binary just has only two digits (0 and 1).
Какая формула определяет, сколько чисел можно представить N битами? / What formula determines how many numbers N bits can represent?::RU: Формула — **2ⁿ**, где n = количество бит. Например, 8 бит → 2⁸ = 256 чисел (0-255); 4 бита → 2⁴ = 16 чисел. Эта формула на самом деле общая для любой системы счисления: **(основание)^(число разрядов)**. EN: The formula is **2ⁿ**, where n = number of bits. E.g. 8 bits → 2⁸ = 256 numbers (0-255); 4 bits → 2⁴ = 16 numbers. The formula generalizes to any base: **base^(number of digits)**.
Когда логический оператор OR даёт результат true? / When does the logical OR operator give a true result?::RU: **OR** даёт **true**, если **хотя бы одно** из значений true (`1 OR 0 = 1`, `0 OR 0 = 0`, `1 OR 1 = 1`). В компьютерной логике `1` = true, `0` = false. EN: **OR** gives **true** if **at least one** of the values is true (`1 OR 0 = 1`, `0 OR 0 = 0`, `1 OR 1 = 1`). In computer logic, `1` = true, `0` = false.
Когда логический оператор AND даёт результат true? / When does the logical AND operator give a true result?::RU: **AND** даёт **true**, только если **оба** значения true (`1 AND 1 = 1`, остальные комбинации = 0). Именно этот оператор используется для применения маски подсети к IP-адресу. EN: **AND** gives **true** only if **both** values are true (`1 AND 1 = 1`, every other combination = 0). This is exactly the operator used to apply a subnet mask to an IP address.
Каким логическим оператором маска подсети применяется к IP-адресу, и что даёт результат? / Which logical operator is used to apply a subnet mask to an IP address, and what does the result give you?::RU: Маска применяется через оператор **AND** (не OR). Если побитово сложить (AND) IP-адрес и маску, результат покажет **Network ID + Subnet ID** этого адреса; всё, что "выпало" — это Host ID. Например: `9.100.100.100 AND 255.255.255.0 = 9.100.100.0`. EN: The mask is applied via **AND** (not OR). Bitwise-ANDing the IP address and mask gives the address's **Network ID + Subnet ID**; whatever's left out is the Host ID. E.g.: `9.100.100.100 AND 255.255.255.0 = 9.100.100.0`.
