---
tags: [networking, coursera, bilingual, flashcards, review]
course: "Computer Networking (Google/Coursera)"
created: 2026-09-16
---

# Пятиуровневая модель TCP/IP · The Five-Layer TCP/IP Model

Связано: [[Ethernet]] · [[IP протокол]] · [[TCP vs UDP]]

Модель описывает, как устройства в сети общаются друг с другом. 5 уровней, снизу вверх:
*The model describes how networked devices communicate. 5 layers, bottom to top:*

1. [[#Физический уровень · Physical layer]]
2. [[#Канальный уровень · Data Link layer]]
3. [[#Сетевой уровень · Network layer]]
4. [[#Транспортный уровень · Transport layer]]
5. [[#Прикладной уровень · Application layer]]

---

## Физический уровень · Physical layer
#physical-layer

Кабели, разъёмы, передача сигнала. Самый нижний уровень — «железо».
*Cables, connectors, signal transmission. The bottom-most layer — the hardware.*

> [!example] Аналогия / Analogy
> RU: Грузовик и дороги, по которым он едет.
> EN: The delivery truck and the roads it drives on.

---

## Канальный уровень · Data Link layer
#data-link-layer

Определяет, как интерпретировать сигналы физического уровня, чтобы устройства могли общаться в пределах **одной** сети/линии.
*Defines how to interpret physical-layer signals so devices can communicate within a **single** network/link.*

Главный протокол: [[Ethernet]] (+ беспроводные технологии).
*Main protocol: Ethernet (+ wireless technologies).*

> [!example] Аналогия / Analogy
> RU: Как грузовик едет от одного перекрёстка к другому.
> EN: How the truck moves from one intersection to the next.

---

## Сетевой уровень · Network layer
#network-layer

Связь **между разными** сетями через роутеры. Совокупность сетей = интернетворк (например, Интернет).
*Communication **between different** networks via routers. A collection of networks = an internetwork (e.g. the Internet).*

Главный протокол: [[IP протокол]] · Main protocol: **IP**.

> [!example] Аналогия / Analogy
> RU: Определение маршрута — по каким дорогам ехать из точки A в точку B.
> EN: Figuring out which roads to take from address A to address B.

---

## Транспортный уровень · Transport layer
#transport-layer

Разносит данные по нужным приложениям на устройстве (а не просто доставляет на сам узел).
*Sorts data to the right application on a device (rather than just delivering it to the node).*

Протоколы: [[TCP vs UDP]] · Protocols: **TCP** (reliable) / **UDP** (not reliable, faster).

> [!example] Аналогия / Analogy
> RU: Курьер, который знает, в какую именно дверь постучать.
> EN: The courier who knows exactly which door to knock on.

---

## Прикладной уровень · Application layer
#application-layer

Протоколы конкретных приложений — браузер, почта и т.д.
*Application-specific protocols — browser, email, etc.*

> [!example] Аналогия / Analogy
> RU: Содержимое посылки.
> EN: The contents of the package.

---

## Итоговая таблица · Summary table

| Layer / Уровень | Purpose / Что делает | Example / Пример |
|---|---|---|
| 5. Application / Прикладной | App-specific comms / Работа приложений | Browser, email |
| 4. Transport / Транспортный | Delivers to right app / Доставка приложению | TCP, UDP |
| 3. Network / Сетевой | Between networks / Между сетями | IP, router |
| 2. Data Link / Канальный | Within one network / В пределах сети | Ethernet, MAC |
| 1. Physical / Физический | Cables, signal / Кабели, сигнал | Cable, connector |

> [!warning] Частые ошибки / Common mistakes
> - RU: Кабели/коннекторы → физический, не транспортный · EN: Cabling/connectors → **physical** layer, not transport
> - RU: Роутер → сетевой уровень · EN: Routers operate at the **network** layer
> - RU: IP → сетевой; TCP/UDP → транспортный · EN: IP is **network**-layer; TCP/UDP are **transport**-layer
> - RU: Ethernet → канальный уровень · EN: Ethernet → **data link** layer

---

## Флеш-карточки · Flashcards
#flashcards

Сколько уровней в модели TCP/IP и как они называются (снизу вверх)? / How many layers does the TCP/IP model have, bottom to top?::RU: Модель TCP/IP состоит из **5 уровней**: Physical (физический), Data Link (канальный), Network (сетевой), Transport (транспортный), Application (прикладной). Каждый уровень решает свою задачу и абстрагирует уровень под собой от вышестоящих. EN: The TCP/IP model has **5 layers**: Physical, Data Link, Network, Transport, Application. Each layer handles its own job and hides the layer below it from the ones above.
На каком уровне работает Ethernet и что он делает? / Which layer does Ethernet operate at, and what does it do?::RU: **Ethernet** — главный протокол **канального уровня (Data Link layer, уровень 2)**. Он определяет, как интерпретировать сигналы физического уровня, чтобы устройства могли общаться в пределах **одной** сети/линии. EN: **Ethernet** is the main **Data Link layer (layer 2)** protocol. It defines how to interpret physical-layer signals so devices can communicate within a **single** network/link.
На каком уровне работает IP и что он делает? / Which layer does IP operate at, and what does it do?::RU: **IP (Internet Protocol)** — главный протокол **сетевого уровня (Network layer, уровень 3)**. Он обеспечивает связь **между разными** сетями через роутеры; совокупность таких сетей называется **интернетворк**. EN: **IP** is the main **Network layer (layer 3)** protocol. It handles communication **between different** networks via routers; a collection of such networks is called an **internetwork**.
Что делает транспортный уровень и какие у него протоколы? / What does the transport layer do, and what protocols does it use?::RU: **Транспортный уровень (Transport layer, уровень 4)** разносит данные по нужным приложениям на устройстве, а не просто доставляет их на сам узел. Протоколы: **TCP** (надёжный, с установлением соединения) и **UDP** (быстрее, но без гарантий доставки). EN: The **Transport layer (layer 4)** sorts data to the right application on a device, rather than just delivering it to the node. Protocols: **TCP** (reliable, connection-based) and **UDP** (faster, no delivery guarantee).
Какой уровень отвечает за кабели и передачу сигнала? / Which layer handles cabling and signal transmission?::RU: **Физический уровень (Physical layer, уровень 1)** — самый нижний уровень модели, отвечает за кабели, разъёмы и саму передачу сигнала («железо»). EN: The **Physical layer (layer 1)** is the model's bottom-most layer, responsible for cables, connectors, and the actual signal transmission (the "hardware").
