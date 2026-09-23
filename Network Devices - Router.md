---
tags: [networking, coursera, network-devices, bilingual, flashcards, review]
course: "Computer Networking (Google/Coursera)"
created: 2026-09-16
---

# Сетевые устройства: роутер · Network Devices: Router

Связано: [[Network Devices - Hub and Switch]] · [[TCP-IP Model]] · [[BGP]]

Хаб и свич объединяют компьютеры внутри одной сети (LAN). Для обмена данными с другими сетями нужен роутер.
*Hubs and switches connect computers within a single network (LAN). To exchange data with other networks, you need a router.*

---

## Роутер (Router)
#router #layer-3

Устройство, пересылающее данные между независимыми сетями. Работает на **сетевом уровне (Layer 3)**.
*A device that forwards data between independent networks. Operates at the **network layer (Layer 3)**.*

| Device / Устройство | Layer / Уровень |
|---|---|
| Hub / Хаб | 1 (physical) |
| Switch / Свич | 2 (data link) |
| Router / Роутер | 3 (network) |

Так же, как свич заглядывает в Ethernet-данные, роутер заглядывает в **IP-данные**, чтобы решить, куда слать трафик.
*Just as a switch inspects Ethernet data, a router inspects **IP data** to decide where to send traffic.*

**Хранит / Stores:** routing tables — RU: информацию о маршрутах до множества сетей мира. EN: information on how to route traffic to networks all over the world.

---

## Домашний / офисный роутер · Home/office router
#home-router

Самый распространённый тип. Таблицы маршрутизации простые.
*The most common type. Routing tables are fairly simple.*

**Главная задача / Main job:** RU: забирать трафик из LAN и пересылать его к ISP. EN: forward traffic originating inside the home/office LAN to the ISP.

---

## Core-роутеры (магистральные) · Core routers
#core-router #isp

Как только трафик доходит до ISP — за дело берутся более сложные устройства.
*Once traffic reaches the ISP, much more sophisticated devices take over.*

- формируют backbone интернета / form the backbone of the Internet
- обрабатывают намного больше трафика / handle far more traffic
- принимают более сложные решения о маршрутизации / make far more complex routing decisions
- обычно много подключений к другим роутерам / usually have many connections to other routers

### BGP (Border Gateway Protocol)
#bgp

RU: Протокол, через который роутеры обмениваются информацией об оптимальных путях для трафика.
EN: The protocol routers use to share information about optimal paths for forwarding traffic.

> [!example] Как это работает на практике / In practice
> RU: Трафик от браузера до веб-сервера может пройти через десятки разных роутеров.
> EN: Traffic from a browser to a web server may travel over dozens of different routers.

---

## Итоговая таблица · Summary table

| | Home/office router | Core (ISP) router |
|---|---|---|
| Routing tables | Simple / Простые | Complex, detailed / Сложные |
| Main job | LAN → ISP | Global routing |
| Traffic volume | Small / Небольшой | Huge / Огромный |
| Connections to other routers | Few / Мало | Many / Много |

> [!warning] Частые ошибки / Common mistakes
> - RU: Роутер = Layer 3, не Layer 2 · EN: Router = **Layer 3**, not Layer 2
> - RU: Роутер смотрит на IP-данные, свич — на Ethernet · EN: Router inspects **IP data**; switch inspects Ethernet data
> - RU: BGP — обмен маршрутной инфой между роутерами · EN: BGP is how routers **exchange routing information**
> - RU: Домашний роутер ≠ core-роутер по сложности · EN: A home router and a core router differ greatly in complexity

---

## Флеш-карточки · Flashcards
#flashcards

На каком уровне работает роутер и чем он занимается? / What layer does a router operate at, and what does it do?::RU: **Роутер (Router)** — устройство **сетевого уровня (Layer 3)**, пересылающее данные между **независимыми сетями** (в отличие от свича, который работает внутри одной LAN). EN: A **router** is a **network layer (Layer 3)** device that forwards data between **independent networks** (unlike a switch, which works within a single LAN).
Во что "заглядывает" роутер, чтобы принять решение о маршрутизации? / What does a router inspect to make routing decisions?::RU: Роутер заглядывает в **IP-данные** пакета (так же, как свич заглядывает в Ethernet-данные), чтобы решить, куда переслать трафик дальше. EN: A router inspects the packet's **IP data** (the way a switch inspects Ethernet data) to decide where to forward traffic next.
Что хранит роутер для маршрутизации? / What does a router store for routing?::RU: Роутер хранит **routing tables (таблицы маршрутизации)** — информацию о том, как добраться до множества сетей по всему миру. У домашнего роутера таблица простая, у core-роутера ISP — намного сложнее. EN: A router stores **routing tables** — information on how to reach networks all over the world. A home router's table is simple; an ISP core router's is far more complex.
Что такое BGP и зачем он нужен? / What is BGP and why is it needed?::RU: **BGP (Border Gateway Protocol)** — протокол, через который роутеры обмениваются информацией об оптимальных путях для пересылки трафика. Именно BGP позволяет core-роутерам интернета согласовывать маршруты между собой. EN: **BGP (Border Gateway Protocol)** is the protocol routers use to share information about optimal paths for forwarding traffic. It's what lets internet core routers coordinate routes with each other.
<!--SR:!2026-09-24,1,230-->
Чем отличается домашний/офисный роутер от core-роутера ISP? / How does a home/office router differ from an ISP core router?::RU: **Домашний роутер** — простые таблицы маршрутизации, главная задача — забирать трафик из LAN и пересылать его к ISP. **Core-роутер** — формирует backbone интернета, обрабатывает намного больше трафика, принимает более сложные решения о маршрутизации и имеет много подключений к другим роутерам. EN: A **home router** has simple routing tables; its main job is forwarding LAN traffic to the ISP. A **core router** forms the internet's backbone, handles far more traffic, makes more complex routing decisions, and has many connections to other routers.
