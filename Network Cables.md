---
tags: [networking, coursera, cables, bilingual]
course: "Computer Networking (Google/Coursera)"
created: 2026-09-16
---

# Сетевые кабели: медь и оптика · Network Cables: Copper and Fiber

Связано: [[TCP-IP Model]] · [[Cat 5e vs Cat 6]] · [[Fiber optic]]

Кабели соединяют устройства и передают данные между ними. Два основных типа:
*Cables connect devices and carry data between them. Two main types:*

1. [[#Медные кабели · Copper cable]]
2. [[#Оптоволоконные кабели · Fiber optic]]

---

## Медные кабели · Copper cable
#copper-cable

Самый распространённый тип. Состоят из нескольких пар скрученных медных проводов в пластиковой изоляции.
*The most common type. Made up of several twisted pairs of copper wires inside plastic insulation.*

Передающее устройство кодирует биты, меняя напряжение; принимающее устройство считывает эти перепады и переводит их в данные.
*The sender encodes bits by varying voltage; the receiver reads these voltage changes and translates them into data.*

### Категории (Cat 5 / Cat 5e / Cat 6) · Categories
#twisted-pair

Внешне почти неотличимы, но разное количество витков пар влияет на:
*Look almost identical, but the number of twists per pair affects:*
- максимальную длину / maximum length
- скорость передачи / transfer speed
- устойчивость к помехам / resistance to interference

> [!note] Cat 5 → Cat 5e
> RU: Cat 5 устарел, вытеснен Cat 5e — меньше подвержен crosstalk (наводкам между проводами). Меньше ошибок → меньше повторных передач → в среднем больше данных за то же время.
> EN: Cat 5 is outdated, replaced by Cat 5e — less prone to **crosstalk** (interference between wires). Fewer errors → fewer retransmissions → more data transferred on average in the same time.

> [!note] Cat 6
> RU: Ещё более строгая спецификация против crosstalk → быстрее и надёжнее Cat 5e, но дороже и **короче** макс. дистанция при высоких скоростях.
> EN: An even stricter anti-crosstalk spec → faster and more reliable than Cat 5e, but more expensive and has a **shorter** max distance at high speeds.

---

## Оптоволоконные кабели · Fiber optic
#fiber-optic

Тонкие стеклянные трубки, по которым передаются световые импульсы вместо электрического напряжения.
*Thin glass tubes carrying pulses of light instead of electrical voltage.*

**Плюсы / Pros:**
- быстрее меди / faster than copper
- работает на больших дистанциях без потери данных / works over much longer distances without data loss
- не подвержен электромагнитным помехам / not affected by electromagnetic interference

**Минусы / Cons:**
- дороже / more expensive
- более хрупкий / more fragile

> [!tip] Где встречается / Where it's used
> RU: В офисах и дома — почти никогда. В основном — в дата-центрах.
> EN: Rarely in offices or homes. Mostly used in **data centers**.

---

## Итоговая таблица · Summary table

| | Copper (Cat 5/5e/6) | Fiber |
|---|---|---|
| Signal carrier / Носитель | Voltage / Напряжение | Light / Свет |
| Speed / Скорость | Lower / Ниже | Higher / Выше |
| Distance / Дистанция | Shorter / Короче | Much longer / Значительно больше |
| Interference resistance | Lower (crosstalk) | High |
| Cost / Стоимость | Cheaper / Дешевле | More expensive / Дороже |
| Fragility / Хрупкость | Sturdier / Прочнее | More fragile / Хрупкий |
| Common location / Где встречается | Office, home | Data centers |

> [!warning] Частые ошибки / Common mistakes
> - RU: Crosstalk — наводка между проводами внутри кабеля, не внешняя помеха · EN: Crosstalk is interference **between wires inside the cable**, not external interference
> - RU: Cat 6 быстрее Cat 5e, но короче макс. дистанция · EN: Cat 6 is faster than Cat 5e but has a **shorter** max distance at high speed
> - RU: Оптика быстрее/дальнобойнее меди, но дороже и хрупче · EN: Fiber is faster/longer-range than copper, but more expensive and fragile
> - RU: Fiber — про свет, не про напряжение · EN: Fiber is about **light**, not voltage
