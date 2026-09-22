---
tags: [networking, coursera, network-devices, bilingual]
course: "Computer Networking (Google/Coursera)"
created: 2026-09-16
---

# Сетевые устройства: хаб и свич · Network Devices: Hub and Switch

Связано: [[Network Cables]] · [[TCP-IP Model]] · [[Collision Domain]]

Кабели дают только point-to-point соединение (одно устройство на каждом конце). Для сети из многих компьютеров нужны:
*Cables only give point-to-point connections (one device on each end). To network many computers, you need:*

1. [[#Хаб (Hub)]]
2. [[#Свич (Switch)]]

---

## Хаб (Hub)
#hub #layer-1

Самое простое устройство для объединения компьютеров. Работает на **физическом уровне (Layer 1)**.
*The simplest device for connecting computers together. Operates at the **physical layer (Layer 1)**.*

**Как работает / How it works:** все устройства "слышат" все данные одновременно; каждое само решает — ему ли эти данные.
*All connected devices "hear" all data at once; each device decides for itself whether the data is meant for it.*

> [!warning] Collision Domain
> RU: Сегмент сети, где только одно устройство может передавать данные одновременно. Одновременная передача = помехи → нужно ждать "тишины" и повторять передачу. Много "шума", сеть замедляется.
> EN: A network segment where only one device can transmit at a time. Simultaneous transmission = interference → devices must wait for a quiet period and retry. Creates noise and slows the network down.

**Итог / Bottom line:** RU: хабы устарели, встречаются как исторический артефакт. EN: hubs are largely obsolete, mostly a historical artifact today.

---

## Свич (Switch)
#switch #layer-2

Более продвинутое устройство. Работает на **канальном уровне (Layer 2)**, а не на физическом.
*A more advanced device. Operates at the **data link layer (Layer 2)**, not physical.*

Свич может заглянуть внутрь Ethernet-данных, определить адресата и отправить данные **только** ему.
*A switch can inspect the Ethernet data, determine the intended recipient, and send data **only** to that device.*

**Результат / Result:**
- домены коллизий уменьшаются/исчезают / collision domains shrink or disappear
- меньше повторных передач / fewer retransmissions
- выше пропускная способность / higher overall throughput

> [!note] Исторический факт / Fun fact
> RU: Свич изначально назывался switching hub.
> EN: The switch was originally called a "switching hub."

---

## Итоговая таблица · Summary table

| | Hub / Хаб | Switch / Свич |
|---|---|---|
| Layer / Уровень | 1 (physical) | 2 (data link) |
| Sends data to / Отправляет | All devices / Всем | Only recipient / Только адресату |
| Collision domain | Large / Большой | Small/none / Маленький |
| Retransmissions | Frequent / Часто | Rare / Редко |
| Relevance today | Obsolete / Устарел | Standard |

> [!warning] Частые ошибки / Common mistakes
> - RU: Хаб — Layer 1, свич — Layer 2 · EN: Hub = Layer 1, Switch = Layer 2
> - RU: Именно хаб создаёт большой collision domain · EN: It's the **hub**, not the switch, that creates a large collision domain
> - RU: Свич "видит" Ethernet-кадр, хаб — нет · EN: A switch inspects the Ethernet frame's contents; a hub cannot
