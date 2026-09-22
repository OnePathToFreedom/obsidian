---
tags: [networking, coursera, cables, twisted-pair, bilingual]
course: "Computer Networking (Google/Coursera)"
created: 2026-09-16
---

# Витая пара: дуплекс, типы кабелей, разводка · Twisted Pair: Duplex, Cable Types, Wiring

Связано: [[Network Cables]] · [[Physical Layer - Bits and Modulation]] · [[Straight-through Cable]]

Самый распространённый тип кабеля — twisted pair (витая пара).
*The most common cable type is twisted pair.*

---

## Почему "витая" · Why "twisted"
#twisted-pair

RU: Пары медных проводов скручены между собой — это защищает от EMI, RFI и crosstalk.
EN: Pairs of copper wires are twisted together — this protects against EMI, RFI, and crosstalk.

RU: Ранние кабели использовали параллельные (не скрученные) провода и страдали от помех. Скручивание было одним из первых решений этой проблемы.
EN: Early cables used parallel (untwisted) wires and suffered from interference. Twisting the pairs was one of the first engineering fixes.

Стандартный Cat 6 = 8 проводов = 4 скрученные пары. *Standard Cat 6 = 8 wires = 4 twisted pairs.*

---

## Duplex: full vs half
#duplex

**Duplex-связь / Duplex communication** — RU: данные идут в обе стороны. EN: information can flow in both directions.

- **Simplex** — RU: однонаправленная передача. EN: unidirectional.
- **Full duplex** — RU: оба устройства передают одновременно (разные пары под каждое направление). EN: both devices transmit at the same time (separate pairs reserved per direction).
- **Half duplex** — RU: связь возможна в обе стороны, но только одно устройство передаёт в момент времени. EN: communication possible both ways, but only one device transmits at a time.

> [!warning]
> RU: Деградация до half-duplex обычно признак проблемы с линией.
> EN: A link degrading to half-duplex is usually a sign of a connection problem.

---

## Ethernet over twisted pair — общая схема · General setup

```
ISP → coax/fiber → gateway modem → twisted pair Ethernet → router → internal LAN wiring
```

RU: Роутер раздаёт проводные соединения внутри здания через twisted pair (CAT-кабели), может раздавать и Wi-Fi.
EN: The router distributes wired connections inside the building via twisted pair (CAT cables), and may also provide Wi-Fi.

RU: Ethernet over twisted pair умеет передавать не только данные, но и телефонию/ТВ.
EN: Ethernet over twisted pair can also carry telephone and television services.

**Почему twisted pair популярен для LAN / Why it's popular for LANs:**
- защита от EMI/RFI/crosstalk / protection against EMI, RFI, crosstalk
- дешевизна / low cost
- лёгкие и гибкие кабели / thin, lightweight, easy to install
- подходящая дальность для зданий / suitable range for buildings/homes
- частоты подходят и для данных, и для голоса / frequency range fits both data and voice

---

## Типы кабелей: UTP / STP / FTP · Cable types

| Type / Тип | Full name / Расшифровка | Protection / Защита | Note / Особенность |
|---|---|---|---|
| **UTP** | Unshielded Twisted Pair | Basic / Базовая | Cheapest, most common / Самый дешёвый |
| **STP** | Shielded Twisted Pair | High / Высокая | Braided shield / Оплётка |
| **FTP** | Foiled Twisted Pair | High / Высокая | Foil shield / Фольга |

> [!note]
> RU: STP и FTP часто взаимозаменяемы. Экранирование может быть и вокруг каждой пары отдельно (сильнее против crosstalk, но дороже всего).
> EN: STP and FTP are often used interchangeably. Shielding can wrap each pair individually (stronger anti-crosstalk, but most expensive).
>
> RU: **SF/FTP** — самый защищённый вариант, для промышленных сред с высоким EMI/RFI.
> EN: **SF/FTP** is the most protected option, used in industrial settings with high EMI/RFI.

---

## Straight-through cable (патч-кабель)
#straight-through-cable

RU: Основной тип Ethernet-кабеля. Соединяет компьютеры/роутеры → хабы/свичи, серверы → свичи.
EN: The primary type of Ethernet cable. Connects computers/routers → hubs/switches, servers → switches.

**Как определить / How to identify:** RU: цвет и порядок пар одинаковы на обоих концах кабеля. EN: color and stripe order of the pairs match on both ends of the cable.

> [!note] 100Base-T
> RU: Стандарт для домашних сетей — не использует синий и коричневый провода. В gigabit Ethernet эти провода могут применяться для PoE.
> EN: Home-network standard — doesn't use the blue and brown wires. Gigabit Ethernet can use them for **PoE** (Power over Ethernet).

### Разводка · Wiring key

| Device / Устройство | Send / Передача | Receive / Приём |
|---|---|---|
| Computers/routers / Компьютеры/роутеры | Pins 1-2, orange / оранжевые | Pins 3-6, green / зелёные |
| Hubs/switches / Хабы/свичи | Pins 1-2, green / зелёные | Pins 3-6, orange / оранжевые |

---

> [!warning] Частые ошибки / Common mistakes
> - RU: Скручивание защищает от EMI/RFI/crosstalk, не увеличивает скорость напрямую · EN: Twisting protects against EMI/RFI/crosstalk, doesn't directly boost speed
> - RU: Full duplex = одновременно; half duplex = по очереди · EN: Full duplex = simultaneous; half duplex = one at a time
> - RU: UTP — без активной защиты; STP/FTP — с экраном · EN: UTP has no active shielding; STP/FTP are shielded
> - RU: Straight-through = одинаковый порядок пар на обоих концах · EN: Straight-through = matching pair order on both ends
> - RU: PoE использует синий/коричневый — актуально для gigabit, не 100Base-T · EN: PoE uses blue/brown wires — relevant for gigabit, not 100Base-T
