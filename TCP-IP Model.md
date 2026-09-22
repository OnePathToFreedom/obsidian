---
tags: [networking, coursera, bilingual]
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
