---
tags: [networking, coursera, glossary, bilingual]
course: "Computer Networking (Google/Coursera)"
created: 2026-09-21
---

# Глоссарий · Course 2, Module 1 Glossary

Связано: [[TCP-IP Model]] · [[Network Cables]] · [[Network Devices - Hub and Switch]] · [[Network Devices - Router]] · [[Clients and Servers]] · [[Physical Layer - Bits and Modulation]] · [[Twisted Pair Cabling and Duplex]] · [[Crossover Cables]] · [[Ethernet and MAC Addresses]] · [[Ethernet Frame Structure]]

RU: Официальный глоссарий терминов курса (Module 1) — алфавитный порядок, как в оригинале.
EN: The course's official term glossary (Module 1) — alphabetical order, as in the original.

---

**Bit** — Бит
RU: Наименьшая единица данных, понятная компьютеру.
EN: The smallest representation of data that a computer can understand.

**Border Gateway Protocol (BGP)** — Протокол граничного шлюза
RU: Протокол, по которому роутеры обмениваются данными друг с другом.
EN: A protocol by which routers share data with each other.

**Broadcast** — Широковещательная передача
RU: Тип Ethernet-передачи, отправляемый абсолютно всем устройствам в LAN.
EN: A type of Ethernet transmission, sent to every single device on a LAN.

**Broadcast address** — Broadcast-адрес
RU: Специальный адрес назначения для Ethernet broadcast — состоит из всех F.
EN: A special destination used by an Ethernet broadcast composed of all F's.

**Cable categories** — Категории кабелей
RU: Группы кабелей, сделанные из одного материала. Большинство сетевых кабелей делятся на две категории — медь и оптика.
EN: Groups of cables made with the same material. Most network cables split into two categories: copper and fiber.

**Cables** — Кабели
RU: Изолированные провода, соединяющие устройства между собой и позволяющие передавать по ним данные.
EN: Insulated wires that connect devices to each other, allowing data to be transmitted over them.

**Carrier-Sense Multiple Access with Collision Detection (CSMA/CD)** — Множественный доступ с контролем несущей и обнаружением коллизий
RU: Используется, чтобы определить, когда канал связи свободен и устройство может передавать данные.
EN: Used to determine when the communications channel is clear and a device is free to transmit data.

**Client** — Клиент
RU: Устройство, получающее данные от сервера.
EN: A device that receives data from a server.

**Collision domain** — Домен коллизий
RU: Сегмент сети, где в момент времени может общаться только одно устройство.
EN: A network segment where only one device can communicate at a time.

**Computer networking** — Компьютерные сети
RU: Вся область знаний о том, как компьютеры общаются друг с другом.
EN: The full scope of how computers communicate with each other.

**Copper cable categories** — Категории медных кабелей
RU: Категории (Cat 5, 5e, 6 и т.д.) с разными физическими характеристиками — количеством витков пар проводов, влияющим на скорость и устойчивость к помехам.
EN: Categories (Cat 5, 5e, 6, etc.) with different physical characteristics — the number of twists per pair, affecting speed and interference resistance.

**Crosstalk** — Перекрёстная наводка
RU: Ситуация, когда электрический импульс в одном проводе случайно детектируется в соседнем.
EN: When an electrical pulse on one wire is accidentally detected on another wire.

**Cyclical Redundancy Check (CRC)** — Циклическая избыточная проверка
RU: Математическое преобразование через полиномиальное деление, сжимающее большой набор данных в одно число. Важна для целостности данных, применяется не только в сетях.
EN: A mathematical transformation using polynomial division to represent a larger set of data as one number. Important for data integrity, used throughout computing.

**Data packet** — Пакет данных
RU: Общий термин для любого набора бинарных данных, передаваемых по сети.
EN: An all-encompassing term for any single set of binary data sent across a network link.

**Data link layer** — Канальный уровень
RU: Уровень, где впервые появляются протоколы. Отвечает за общий способ интерпретации сигналов, чтобы устройства могли общаться.
EN: The layer where the first protocols are introduced. Responsible for defining a common way of interpreting signals so devices can communicate.

**Destination MAC address** — MAC-адрес получателя
RU: Аппаратный адрес получателя, идёт сразу после start frame delimiter.
EN: The hardware address of the intended recipient, immediately following the start frame delimiter.

**Duplex communication** — Дуплексная связь
RU: Форма связи, где данные могут идти в обе стороны по кабелю.
EN: A form of communication where information can flow in both directions across a cable.

**Ethernet**
RU: Наиболее широко используемый протокол для передачи данных по отдельным линиям связи.
EN: The protocol most widely used to send data across individual links.

**Ethernet frame** — Ethernet-фрейм
RU: Строго структурированный набор информации в определённом порядке.
EN: A highly structured collection of information presented in a specific order.

**EtherType field** — Поле EtherType
RU: Идёт после Source MAC Address, длина 16 бит, описывает протокол содержимого фрейма.
EN: Follows the Source MAC Address in a data frame. 16 bits long, describes the protocol of the frame's contents.

**Fiber cable** — Оптоволоконный кабель
RU: Содержит тонкие стеклянные трубки (толщиной с волос), передающие световые импульсы вместо электрического напряжения.
EN: Contains individual optical fibers, tiny glass tubes about the width of a human hair, using light pulses instead of electrical voltage.

**Five layer model** — Пятиуровневая модель
RU: Модель, объясняющая коммуникацию сетевых устройств: физический, канальный, сетевой, транспортный, прикладной уровни.
EN: A model explaining how network devices communicate, with five layers: Physical, Data Link, Network, Transport, and Application.

**Frame check sequence (FCS)** — Последовательность проверки кадра
RU: 4-байтное (32-битное) число — контрольная сумма всего фрейма.
EN: A 4-byte or 32-bit number representing a checksum value for the entire frame.

**Full duplex**
RU: Возможность устройств на обоих концах линии общаться одновременно.
EN: The capacity of devices on either side of a link to communicate at the exact same time.

**Half-duplex**
RU: Связь возможна в обе стороны, но только одно устройство может передавать в конкретный момент.
EN: Communication is possible in each direction, but only one device can communicate at a time.

**Hexadecimal** — Шестнадцатеричная система
RU: Способ представления чисел с основанием 16.
EN: A way to represent numbers using a numerical base of 16.

**Hub** — Хаб
RU: Устройство физического уровня, рассылающее данные всем подключённым компьютерам.
EN: A physical layer device that broadcasts data to every computer connected to it.

**Internet Protocol (IP)**
RU: Самый распространённый протокол сетевого уровня.
EN: The most common protocol used at the network layer.

**Internet Service Provider (ISP)** — Интернет-провайдер
RU: Компания, предоставляющая потребителю подключение к интернету.
EN: A company that provides a consumer an internet connection.

**Internetwork** — Интернетворк
RU: Совокупность сетей, соединённых через роутеры — самая известная из них — Интернет.
EN: A collection of networks connected together through routers — the most famous being the Internet.

**Line coding** — Линейное кодирование
RU: Модуляция, используемая в компьютерных сетях.
EN: Modulation used for computer networks.

**Local Area Network (LAN)** — Локальная сеть
RU: Единая сеть, в которой соединены несколько устройств.
EN: A single network in which multiple devices are connected.

**MAC (Media Access Control) address** — MAC-адрес
RU: Глобально уникальный идентификатор сетевого интерфейса. 48-битное число, 6 групп по 2 hex-цифры.
EN: A globally unique identifier attached to an individual network interface. A 48-bit number, normally 6 groupings of 2 hexadecimal digits.

**Modulation** — Модуляция
RU: Способ изменения напряжения постоянного электрического заряда в стандартном медном сетевом кабеле.
EN: A way of varying the voltage of a constant electrical charge moving across a standard copper network cable.

**Multicast frame** — Multicast-фрейм
RU: Если младший бит первого октета адреса назначения = 1 — это multicast-фрейм. Рассылается всем устройствам сегмента, но принимается/отбрасывается по критерию, отличному от собственного MAC-адреса.
EN: If the least significant bit in the first octet of a destination address is set to 1 — it's a multicast frame. Sent to all devices on the segment, accepted/discarded based on criteria other than the device's own MAC address.

**Network layer** — Сетевой уровень
RU: Уровень, позволяющий разным сетям общаться друг с другом через роутеры. Отвечает за доставку данных через совокупность сетей.
EN: The layer that lets different networks communicate through routers. Responsible for getting data delivered across a collection of networks.

**Network port** — Сетевой порт
RU: Физический разъём для подключения устройства к сети. Может быть на самом устройстве, на стене или на патч-панели.
EN: The physical connector to connect a device to the network — on the device itself, a wall, or a patch panel.

**Network switch** — Сетевой свич
RU: Устройство канального (2) уровня, подключающее много устройств. Заглядывает в содержимое Ethernet-данных и отправляет их только адресату.
EN: A Layer 2 (data link) device that connects many devices, inspects the Ethernet data's contents, and sends it only to the intended recipient.

**Node** — Узел
RU: Любое устройство, подключённое к сети. Обычно выступает сервером или клиентом.
EN: Any device connected to a network. Typically acts as a server or a client.

**Octet** — Октет
RU: Любое число, представимое 8 битами.
EN: Any number that can be represented by 8 bits.

**Organizationally Unique Identifier (OUI)** — Организационно уникальный идентификатор
RU: Первые три октета MAC-адреса.
EN: The first three octets of a MAC address.

**OSI model** — Модель OSI
RU: Модель коммуникации сетевых устройств из семи уровней: физический, канальный, сетевой, транспортный, сеансовый, представления и прикладной.
EN: A model defining how network devices communicate, with seven layers: Physical, Data Link, Network, Transport, Session, Presentation, and Application.

**Patch panel** — Патч-панель
RU: Устройство с множеством физических сетевых портов.
EN: A device containing many physical network ports.

**Payload** — Полезная нагрузка
RU: Реальные передаваемые данные — всё, что не является заголовком.
EN: The actual data being transported — everything that isn't a header.

**Physical layer** — Физический уровень
RU: Представляет физические устройства, соединяющие компьютеры.
EN: Represents the physical devices that interconnect computers.

**Preamble** — Преамбула
RU: Первая часть Ethernet-фрейма, 8 байт (64 бита), делится на две секции.
EN: The first part of an Ethernet frame, 8 bytes (64 bits) long, itself split into two sections.

**Protocol** — Протокол
RU: Определённый набор стандартов, которым должны следовать компьютеры для правильного общения.
EN: A defined set of standards that computers must follow in order to communicate properly.

**Router** — Роутер
RU: Устройство, умеющее пересылать данные между независимыми сетями.
EN: A device that knows how to forward data between independent networks.

**Server** — Сервер
RU: Устройство, предоставляющее данные другому устройству (клиенту), запросившему их.
EN: A device that provides data to another device (a client) that is requesting it.

**Simplex communication** — Симплексная связь
RU: Форма передачи данных только в одном направлении по кабелю.
EN: A form of data communication that only goes in one direction across a cable.

**Source MAC address** — MAC-адрес отправителя
RU: Аппаратный адрес устройства, отправившего Ethernet-фрейм; в пакете идёт после MAC-адреса получателя.
EN: The hardware address of the device that sent the frame; in the packet, it follows the destination MAC address.

**Start Frame Delimiter (SFD)**
RU: Последний байт преамбулы, сигнализирует принимающему устройству, что преамбула закончилась и дальше идёт само содержимое фрейма.
EN: The last byte in the preamble, signaling to the receiving device that the preamble is over and actual frame contents follow.

**Transmission Control Protocol (TCP)**
RU: Протокол передачи данных, наиболее часто используемый на 4-м уровне. Требует установленного соединения между клиентом и сервером.
EN: The data transfer protocol most commonly used at the fourth layer. Requires an established connection between client and server.

**Transport layer** — Транспортный уровень
RU: Уровень, определяющий, какие клиентские и серверные программы должны получить данные.
EN: The layer that sorts out which client and server programs are supposed to get the data.

**Twisted pair cable** — Кабель "витая пара"
RU: Самый распространённый тип кабеля для подключения устройств. Пары медных проводов, скрученные вместе.
EN: The most common type of cabling for connecting computing devices. Features pairs of copper wires twisted together.

**Unicast transmission** — Unicast-передача
RU: Передача, всегда предназначенная только одному получателю.
EN: A unicast transmission is always meant for just one receiving address.

**User Datagram Protocol (UDP)**
RU: Протокол передачи без установления соединения. Не поддерживает подтверждения доставки — просто указывается порт назначения и отправляется пакет.
EN: A transfer protocol that doesn't rely on connections. Doesn't support acknowledgements — you set a destination port and send the packet.

**Virtual LAN (VLAN)** — Виртуальная LAN
RU: Техника, позволяющая иметь несколько логических LAN на одном физическом оборудовании.
EN: A technique that lets you have multiple logical LANs operating on the same physical equipment.

**VLAN header**
RU: Данные, указывающие тип фрейма. В пакете идут перед полем EtherType.
EN: A piece of data indicating what the frame is. In a data packet, followed by the EtherType field.
