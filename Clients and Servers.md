---
tags: [networking, coursera, client-server, bilingual]
course: "Computer Networking (Google/Coursera)"
created: 2026-09-16
---

# Клиенты и серверы · Clients and Servers

Связано: [[Network Devices - Hub and Switch]] · [[Network Devices - Router]] · [[TCP-IP Model]]

Все сетевые устройства нужны для того, чтобы узлы (nodes) могли общаться друг с другом.
*All network devices exist so that nodes can communicate with each other.*

---

## Сервер и клиент · Server and client
#server #client

**Сервер / Server** — RU: то, что предоставляет данные по запросу. EN: something that provides data to something requesting it.
**Клиент / Client** — RU: то, что запрашивает и получает эти данные. EN: something that requests and receives that data.

> [!note] Почему "something" / Why "something," not "device"
> RU: Серверами и клиентами могут быть не только узлы сети, но и отдельные программы на одном узле по отношению друг к другу.
> EN: Servers and clients can be individual programs on the *same* node, not just whole devices.

---

## Узлы редко бывают "чистыми" · Nodes are rarely purely one or the other
#node

RU: Большинство узлов — и сервер, и клиент одновременно, в зависимости от момента.
EN: Most nodes are both a server and a client at different points in time.

> [!example] Пример / Example
> RU: Email-сервер — сервер для клиентов, но сам является клиентом DNS-сервера.
> EN: An email server is a server to its clients, but it's itself a client of a DNS server.
>
> RU: Обычный компьютер иногда тоже "отдаёт" данные другим машинам, но это не его основная роль.
> EN: A regular desktop sometimes provides data to another machine too, but that's not its primary purpose.

---

## Итог · Takeaway

RU: Термины "сервер"/"клиент" используются в двух смыслах:
EN: The terms "server"/"client" are used in two senses:

1. RU: Буквально — в конкретный момент, кто отдаёт, кто получает данные.
   EN: Literally — in a given moment, who provides vs. who receives data.
2. RU: По основной роли узла — "email-сервер" называют сервером за его основное предназначение, а не потому что он никогда не бывает клиентом.
   EN: By primary role — an "email server" is called a server because serving clients is its **primary purpose**, not because it's never a client.

> [!warning] Частые ошибки / Common mistakes
> - RU: Сервер/клиент — не всегда целое устройство, может быть программа · EN: Server/client can be individual **programs**, not just whole devices
> - RU: Один узел может быть и сервером, и клиентом одновременно · EN: A single node can be both a server and a client at the same time (in different roles)
> - RU: "Сервер X" называют так по основной функции · EN: A node is called "server X" based on its **primary function**, not exclusivity
