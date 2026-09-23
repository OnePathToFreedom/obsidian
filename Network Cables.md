---
tags: [networking, coursera, cables, bilingual, flashcards, review]
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

---

## Флеш-карточки · Flashcards
#flashcards

Два основных типа сетевых кабелей? / Two main types of network cables?::RU: **Медные кабели (copper)** — пары скрученных медных проводов, передающие данные через изменение напряжения; и **оптоволоконные кабели (fiber optic)** — тонкие стеклянные трубки, передающие световые импульсы. EN: **Copper cables** — twisted pairs of copper wire transmitting data via voltage changes; and **fiber optic cables** — thin glass tubes carrying light pulses.
Что такое crosstalk? / What is crosstalk?::RU: **Crosstalk (перекрёстная наводка)** — ситуация, когда электрический импульс в одном проводе кабеля случайно детектируется в соседнем проводе. Это внутренняя помеха между проводами **внутри** кабеля, а не внешний источник шума. EN: **Crosstalk** is when an electrical pulse on one wire is accidentally picked up by a neighboring wire. It's interference **between wires inside the cable**, not an external noise source.
Чем Cat 6 отличается от Cat 5e? / How does Cat 6 differ from Cat 5e?::RU: **Cat 6** использует более строгую спецификацию защиты от crosstalk, чем **Cat 5e** — за счёт этого быстрее и надёжнее, но дороже, и его максимальная дистанция передачи на высоких скоростях **короче**. EN: **Cat 6** uses a stricter anti-crosstalk spec than **Cat 5e** — faster and more reliable, but more expensive, with a **shorter** max distance at high speeds.
Что передаёт данные в оптоволокне вместо напряжения? / What carries data in fiber optic instead of voltage?::RU: **Свет** — оптоволоконный кабель передаёт данные световыми импульсами по тонким стеклянным трубкам, вместо изменения электрического напряжения, как в меди. EN: **Light** — a fiber optic cable transmits data as light pulses through thin glass tubes, instead of varying electrical voltage like copper does.
Где чаще всего используется оптоволокно и почему? / Where is fiber optic mostly used, and why?::RU: В основном в **дата-центрах** — оптика быстрее, работает на больших дистанциях без потери данных и не подвержена электромагнитным помехам, но дороже и более хрупкая, чем медь, поэтому редко встречается в офисах/домах. EN: Mostly in **data centers** — fiber is faster, works over longer distances without data loss, and resists electromagnetic interference, but it's more expensive and fragile than copper, so it's rare in offices/homes.
