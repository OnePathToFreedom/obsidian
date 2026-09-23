---
tags: [networking, coursera, cables, twisted-pair, bilingual, flashcards, review]
course: "Computer Networking (Google/Coursera)"
created: 2026-09-21
---

# Кроссовер-кабели · Crossover Cables

Связано: [[Twisted Pair Cabling and Duplex]] · [[Network Devices - Hub and Switch]] · [[Network Devices - Router]]

RU: Кроссовер-кабели ещё встречаются в старых корпоративных сетях.
EN: Crossover cables may still be found in older enterprise network environments.

> [!note] Auto-MDI/MDIX
> RU: Большинство новых устройств умеют сами определять тип Ethernet-подключения и выбирать нужные провода для передачи/приёма — технология Auto-MDI/MDIX. Она заменяет собой функцию кроссовер-кабеля.
> EN: Most new enterprise devices can auto-detect the connection type and pick the right send/receive wires — **Auto-MDI/MDIX**. This replaces the need for a crossover cable.

---

## Назначение · Purpose
#crossover-cable

RU: Кроссовер-кабель соединяет два вычислительных устройства **напрямую друг с другом**.
EN: A crossover cable connects two computing devices **directly to each other**.

> [!example] Типичный сценарий / Typical use case
> RU: IT-специалист подключает короткий кроссовер-кабель между своим ноутбуком и management-портом enterprise-устройства (сервер, свич, роутер, хаб) — для обновления, ремонта, администрирования.
> EN: An IT specialist uses a short crossover cable to connect an admin laptop directly to an enterprise machine's (server, switch, router, hub) management port — for updates, repairs, and admin tasks.

RU: Также кроссовер-кабелем можно соединить: два свича, два хаба, свич-хаб, два роутера, два ПК, роутер-ПК.
EN: Crossover cables can also connect: two switches, two hubs, a switch to a hub, two routers, two PCs, or a router to a PC.

---

## Как отличить от straight-through · How to identify
#wiring

RU: Как и у straight-through, оба конца кабеля сравнивают между собой — но у кроссовера порядок цветов пар **разный** на концах.
EN: Like straight-through cables, you compare both ends — but on a crossover cable, the color order of the pairs is **different** at each end.

RU: Смысл перекрёстной разводки — соединить два устройства, которые передают и принимают данные по **одним и тем же** проводам.
EN: The crossover wiring exists to connect two devices that transmit and receive on the **same** wires.

> [!note] T-568-A vs T-568-B
> RU: Straight-through кабели используют схему **T568B** на обоих концах. Кроссовер-кабели используют **обе** схемы — T568A на одном конце, T568B на другом.
> EN: Straight-through cables use the **T568B** scheme on both ends. Crossover cables use **both** schemes — T568A on one end, T568B on the other.
>
> RU: Синий и коричневый провода в этой разводке **не** перекрещиваются.
> EN: The blue and brown wires do **not** cross over in this setup.

---

## Crossover cable key (T-568-A ↔ T-568-B)

| Endpoint / Конец | Pins 1 & 2 (send / передача) | Pins 3 & 6 (receive / приём) |
|---|---|---|
| **Endpoint 1** | Green / Зелёные | Orange / Оранжевые |
| **Endpoint 2** | Orange / Оранжевые | Green / Зелёные |

RU: То есть зелёные провода в позициях 1-2 на одном конце переходят в позиции 3-6 на другом; оранжевые — наоборот.
EN: Green wires at pins 1-2 on one end move to pins 3-6 on the other; orange wires do the reverse.

---

> [!warning] Частые ошибки / Common mistakes
> - RU: Auto-MDI/MDIX делает кроссовер-кабель необязательным на новом оборудовании, но не отменяет его существование · EN: Auto-MDI/MDIX makes crossover cables unnecessary on new hardware, but doesn't eliminate them entirely
> - RU: Straight-through = T568B на обоих концах; crossover = T568A + T568B · EN: Straight-through = T568B both ends; crossover = T568A + T568B
> - RU: Синий/коричневый провода в crossover **не** перекрещиваются · EN: Blue/brown wires do **not** cross over in a crossover cable
> - RU: Кроссовер нужен, когда оба устройства используют одни и те же провода для send/receive (напрямую, без свича) · EN: Crossover is needed when both devices use the same wires for send/receive (direct connection, no switch)

---

## Флеш-карточки · Flashcards
#flashcards

Для чего нужен кроссовер-кабель? Приведи пример сценария. / What is a crossover cable for? Give an example scenario.::RU: **Кроссовер-кабель (Crossover cable)** соединяет два вычислительных устройства **напрямую** друг с другом (без свича/хаба между ними) — например, два свича, два ПК, роутер с ПК. Типичный сценарий: IT-специалист подключает короткий кроссовер-кабель между своим ноутбуком и management-портом enterprise-устройства для администрирования. EN: A **crossover cable** connects two computing devices **directly** to each other (no switch/hub between them) — e.g. two switches, two PCs, a router to a PC. Typical use: an IT specialist connects a laptop directly to an enterprise device's management port for admin tasks.
Какая технология делает кроссовер-кабель необязательным на новом оборудовании, и как она работает? / What technology makes crossover cables unnecessary on new hardware, and how does it work?::RU: **Auto-MDI/MDIX** — большинство новых устройств умеют сами определять тип Ethernet-подключения и автоматически выбирать нужные провода для передачи/приёма, заменяя тем самым функцию кроссовер-кабеля. Но сами кроссовер-кабели по-прежнему встречаются в старых сетях. EN: **Auto-MDI/MDIX** — most new devices can auto-detect the connection type and automatically pick the right send/receive wires, replacing the need for a crossover cable. Crossover cables still turn up in older networks, though.
Какие схемы разводки использует кроссовер-кабель на двух концах, и чем это отличается от straight-through? / Which wiring schemes does a crossover cable use at its two ends, and how does that differ from straight-through?::RU: Straight-through кабели используют схему **T568B на обоих концах**. Кроссовер-кабели используют **обе** схемы — **T568A на одном конце, T568B на другом** — именно эта разница создаёт "перекрёстную" разводку, нужную для соединения двух устройств, использующих одни и те же провода для send/receive. EN: Straight-through cables use **T568B on both ends**. Crossover cables use **both** schemes — **T568A on one end, T568B on the other** — this difference is what creates the "crossed" wiring needed to connect two devices that transmit/receive on the same wires.
Перекрещиваются ли синий/коричневый провода в crossover-кабеле? / Do the blue/brown wires cross over in a crossover cable?::RU: Нет — синий и коричневый провода в T568A/T568B разводке **не** перекрещиваются; перекрещиваются только зелёная и оранжевая пары (позиции 1-2 ↔ 3-6). EN: No — the blue and brown wires in the T568A/T568B wiring do **not** cross over; only the green and orange pairs swap (pins 1-2 ↔ 3-6).
