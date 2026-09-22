---
tags: [networking, coursera, network-layer, subnetting, bilingual]
course: "Computer Networking (Google/Coursera)"
created: 2026-09-21
---

# Основы сабнеттинга · Subnetting Basics

Связано: [[IP Address Classes]] · [[IP Addresses Basics]] · [[Network Devices - Router]] · [[ARP - Address Resolution Protocol]]

RU: **Subnetting (сабнеттинг)** — процесс разбиения большой сети на множество маленьких подсетей (subnets).
EN: **Subnetting** is the process of taking a large network and splitting it into many smaller subnetworks (subnets).

---

## Как маршрутизируется пакет без сабнеттинга · Routing without subnetting
#gateway-router

RU: Адресные классы (см. [[IP Address Classes]]) делят глобальное IP-пространство на дискретные сети.
EN: Address classes (see [[IP Address Classes]]) split the global IP space into discrete networks.

> [!example] Путь пакета до 9.100.100.100 / Path of a packet to 9.100.100.100
> RU: Core-роутеры интернета знают, что этот IP принадлежит **Class A сети 9.0.0.0** (см. [[Network Devices - Router]]). Они направляют сообщение к **gateway router**, отвечающему за эту сеть, — глядя на **Network ID**.
> EN: Internet core routers know this IP belongs to the **Class A network 9.0.0.0**. They route the message to the **gateway router** responsible for that network — by looking at the **Network ID**.
>
> RU: Дальше, уже внутри сети, gateway router доставляет пакет нужному устройству, глядя на **Host ID**.
> EN: From there, inside the network, the gateway router delivers the packet to the correct system by looking at the **Host ID**.

---

## Gateway router vs core router
#gateway-router #core-router

RU: **Gateway router** — служит точкой входа и выхода (ingress/egress) для конкретной сети.
EN: A **gateway router** — serves as the entry and exit path for a specific network.

RU: В отличие от него, **core-роутеры** интернета могут общаться только с другими core-роутерами.
EN: In contrast, internet **core routers** might only talk to other core routers.

---

## Проблема: слишком большая сеть · The problem: networks too large
#the-problem

> [!warning] Масштаб проблемы / Scale of the problem
> RU: Один Class A network содержит **16 777 216** отдельных IP-адресов (см. [[IP Address Classes]]). Это слишком много устройств, чтобы подключить их всех к одному роутеру.
> EN: A single Class A network contains **16,777,216** individual IPs (see [[IP Address Classes]]). That's far too many devices to connect to one router.

---

## Решение: сабнеттинг · The solution: subnetting
#solution

RU: С помощью сабнеттинга большую сеть можно разбить на много **меньших подсетей**. У каждой такой подсети — **свой собственный gateway router**, служащий точкой входа/выхода именно для неё.
EN: With subnetting, a large network can be split into many **smaller subnets**. Each individual subnet gets **its own gateway router**, serving as the ingress/egress point for that subnet.

---

> [!warning] Частые ошибки / Common mistakes
> - RU: Gateway router определяет сеть по **Network ID**, а устройство внутри сети — по **Host ID** · EN: A gateway router uses the **Network ID** to find the network, and the **Host ID** to find the device within it
> - RU: Core-роутеры общаются только с другими core-роутерами, не с конечными устройствами напрямую · EN: Core routers only talk to other core routers, not directly to end devices
> - RU: Проблема сабнеттинга — не в нехватке адресов, а в том, что **слишком много** устройств нельзя разумно подключить к одному роутеру · EN: The subnetting problem isn't a shortage of addresses — it's that **too many** devices can't reasonably connect to a single router
> - RU: У каждой подсети — собственный gateway router, а не общий на всю исходную сеть · EN: Each subnet gets its own gateway router, not a shared one for the whole original network
