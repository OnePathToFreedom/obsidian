---
tags: [networking, coursera, client-server, bilingual, flashcards, review]
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

---

## Флеш-карточки · Flashcards
#flashcards

Что такое сервер и что важно понимать про это понятие? / What is a server, and what's important to understand about the term?::RU: **Сервер (Server)** — это то, что предоставляет данные по запросу. Важно: сервером может быть не только целое устройство, но и отдельная программа на узле по отношению к другой программе на том же узле. EN: A **server** is something that provides data to something requesting it. Importantly, a server can be an individual **program**, not just a whole device — even two programs on the same machine can be in a server/client relationship.
Что такое клиент? / What is a client?::RU: **Клиент (Client)** — это то, что запрашивает и получает данные у сервера. Как и сервер, клиентом может быть целое устройство или отдельная программа. EN: A **client** is something that requests and receives data from a server. Like a server, a client can be a whole device or an individual program.
Может ли один узел быть и сервером, и клиентом одновременно? Приведи пример. / Can one node be both a server and a client at the same time? Give an example.::RU: Да — большинство узлов являются и сервером, и клиентом в разные моменты. Пример: email-сервер — сервер для своих клиентов, но сам является клиентом DNS-сервера, когда ему нужно разрешить доменное имя. EN: Yes — most nodes are both a server and a client at different times. Example: an email server serves its clients, but it's itself a client of a DNS server when it needs to resolve a domain name.
Почему email-сервер называют "сервером", хотя он иногда бывает и клиентом (например, DNS)? / Why is an email server called a "server" even though it's sometimes a client (e.g. of DNS)?::RU: Термин "сервер"/"клиент" используется в двух смыслах: (1) буквально — в конкретный момент, кто отдаёт, а кто получает данные; (2) по основной роли узла — "email-сервер" называют так за его **основное предназначение** (обслуживать email-клиентов), а не потому что он никогда не бывает клиентом. EN: "Server"/"client" is used in two senses: (1) literally — at a given moment, who's providing vs receiving data; (2) by primary role — an "email server" is named for its **primary purpose** (serving email clients), not because it's never a client.
