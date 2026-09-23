---
tags: [networking, coursera, network-layer, arp, bilingual, flashcards, review]
course: "Computer Networking (Google/Coursera)"
created: 2026-09-21
---

# ARP — Address Resolution Protocol

Связано: [[Ethernet and MAC Addresses]] · [[IP Addresses Basics]] · [[IP Datagram Structure]]

RU: **ARP** — протокол, связывающий MAC-адреса (канальный уровень) и IP-адреса (сетевой уровень): он находит аппаратный (MAC) адрес узла по его IP-адресу.
EN: **ARP** is the protocol linking MAC addresses (data link layer) and IP addresses (network layer): it discovers the hardware (MAC) address of a node with a given IP address.

---

## Зачем нужен ARP · Why ARP is needed
#why-arp

RU: Когда IP-датаграмма полностью сформирована, её нужно инкапсулировать в Ethernet-фрейм (см. [[IP Datagram Structure]]). Для этого передающему устройству нужен **MAC-адрес получателя**, чтобы заполнить заголовок Ethernet-фрейма.
EN: Once an IP datagram is fully formed, it needs to be encapsulated inside an Ethernet frame (see [[IP Datagram Structure]]). For that, the sending device needs the **destination MAC address** to complete the Ethernet frame header.

RU: Устройство знает IP-адрес получателя, но не знает его MAC-адрес — вот тут и нужен ARP.
EN: The device knows the recipient's IP address but not its MAC address — that's where ARP comes in.

---

## ARP-таблица · ARP table
#arp-table

RU: Почти каждое сетевое устройство хранит локальную **ARP-таблицу** — список соответствий IP-адресов и MAC-адресов.
EN: Almost every network-connected device keeps a local **ARP table** — a list of IP addresses and their associated MAC addresses.

> [!note] Срок жизни записей / Entry lifetime
> RU: Записи в ARP-таблице обычно **истекают** через непродолжительное время — это нужно, чтобы учитывать изменения в сети.
> EN: ARP table entries generally **expire** after a short time — this ensures changes in the network are accounted for.

---

## Как работает ARP · How ARP works
#arp-process

> [!example] Пошаговый процесс / Step-by-step
> RU: Допустим, нужно отправить данные на IP `10.20.30.40`, но записи для этого адреса нет в ARP-таблице.
> EN: Say we want to send data to IP `10.20.30.40`, but there's no entry for it in the ARP table.
>
> 1. RU: Отправитель рассылает **ARP-broadcast** сообщение на MAC-broadcast адрес (`FF:FF:FF:FF:FF:FF`).
>    EN: The sender broadcasts an **ARP request** to the MAC broadcast address (`FF:FF:FF:FF:FF:FF`).
> 2. RU: Это сообщение доставляется **всем** компьютерам локальной сети.
>    EN: This broadcast is delivered to **every** computer on the local network.
> 3. RU: Устройство с IP `10.20.30.40` получает broadcast и отправляет обратно **ARP response** (ARP-ответ) со своим MAC-адресом.
>    EN: The device with IP `10.20.30.40` receives the broadcast and sends back an **ARP response** containing its MAC address.
> 4. RU: Отправитель теперь знает, какой MAC-адрес вписать в поле destination hardware address заголовка Ethernet-фрейма — фрейм готов к отправке.
>    EN: The sender now knows which MAC address to put in the Ethernet frame's destination hardware address field — the frame is ready for delivery.
> 5. RU: Полученная пара IP↔MAC обычно сохраняется в локальной ARP-таблице — чтобы не рассылать broadcast заново при следующей отправке на этот же IP.
>    EN: The resulting IP↔MAC pair is usually saved to the local ARP table — so a broadcast isn't needed again next time this IP is contacted.

---

## Итоговая схема · Summary diagram

```
Есть IP получателя, нет MAC → проверка ARP-таблицы
   └── если нет записи → ARP request (broadcast, FF:FF:FF:FF:FF:FF)
         └── устройство с нужным IP отвечает → ARP response (свой MAC)
               └── MAC записывается в заголовок Ethernet-фрейма + кэшируется в ARP-таблице
```

---

> [!warning] Частые ошибки / Common mistakes
> - RU: ARP решает задачу IP → MAC, а не наоборот · EN: ARP resolves IP → MAC, not the other way around
> - RU: ARP request рассылается именно на **MAC broadcast** адрес (все F), не на IP broadcast · EN: The ARP request goes to the **MAC broadcast** address (all F's), not an IP broadcast
> - RU: ARP-ответ (response) — это **unicast**, отправленный конкретно запросившему устройству, а не всем · EN: The ARP response is **unicast**, sent specifically to the requesting device, not to everyone
> - RU: Записи ARP-таблицы истекают — это не постоянное хранилище · EN: ARP table entries expire — it's not permanent storage
> - RU: ARP нужен именно потому, что для отправки Ethernet-фрейма обязателен MAC-адрес получателя в заголовке · EN: ARP is needed because an Ethernet frame's header requires the recipient's MAC address to be sent at all

---

## Флеш-карточки · Flashcards
#flashcards

Что делает ARP, и зачем он вообще нужен? / What does ARP do, and why is it needed at all?::RU: **ARP (Address Resolution Protocol)** связывает MAC-адреса (канальный уровень) и IP-адреса (сетевой уровень): находит аппаратный (MAC) адрес узла по его IP-адресу. Он нужен, потому что для инкапсуляции IP-датаграммы в Ethernet-фрейм обязательно требуется **MAC-адрес получателя** в заголовке фрейма, а устройство изначально знает только IP-адрес. EN: **ARP** links MAC addresses (data link layer) and IP addresses (network layer): it discovers a node's MAC address given its IP. It's needed because encapsulating an IP datagram into an Ethernet frame requires the **destination MAC address** in the frame header, and a device initially only knows the IP address.
На какой MAC-адрес отправляется ARP-запрос, и кто его получает? / What MAC address does an ARP request go to, and who receives it?::RU: ARP-запрос (**ARP request**) рассылается как **ARP-broadcast** на MAC-адрес **`FF:FF:FF:FF:FF:FF`** и доставляется **всем** компьютерам локальной сети — только устройство с искомым IP отвечает. EN: An **ARP request** is broadcast to MAC address **`FF:FF:FF:FF:FF:FF`** and delivered to **every** computer on the local network — only the device with the matching IP responds.
ARP-ответ — unicast или broadcast, и что в нём содержится? / Is an ARP response unicast or broadcast, and what does it contain?::RU: **ARP response** — это **unicast**, отправленный конкретно запросившему устройству (а не всем), и содержит MAC-адрес устройства, у которого искомый IP. Отправитель затем вписывает этот MAC в заголовок Ethernet-фрейма. EN: An **ARP response** is **unicast**, sent specifically to the requesting device (not broadcast), and contains the MAC address of the device owning the queried IP. The sender then puts that MAC into the Ethernet frame header.
Что происходит с записями ARP-таблицы со временем, и почему? / What happens to ARP table entries over time, and why?::RU: Записи **ARP-таблицы** обычно **истекают (expire)** через непродолжительное время — это не постоянное хранилище. Нужно это, чтобы учитывать изменения в сети (например, если у устройства сменился сетевой интерфейс или IP). EN: **ARP table** entries generally **expire** after a short time — it's not permanent storage. This ensures changes in the network are accounted for (e.g. a device getting a new network interface or IP).
