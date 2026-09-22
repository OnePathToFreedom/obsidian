---
tags: [networking, coursera, physical-layer, bilingual]
course: "Computer Networking (Google/Coursera)"
created: 2026-09-16
---

# Физический уровень: биты и модуляция · Physical Layer: Bits and Modulation

Связано: [[TCP-IP Model]] · [[Network Cables]]

Задача физического уровня — двигать биты от одного конца линии к другому.
*The physical layer's job is to move bits from one end of a link to the other.*

---

## Бит · Bit
#bit

RU: Наименьшая единица данных, понятная компьютеру. Либо 0, либо 1.
EN: The smallest unit of data a computer understands. Either a 0 or a 1.

> [!note] Важная мысль / Key idea
> RU: Стриминг музыки, письмо в почте, банкомат — на физическом уровне это всё одно и то же: передача битов.
> EN: Streaming music, sending an email, using an ATM — at the physical layer it's all the same thing: sending bits.

RU: Эти биты в итоге складываются во фреймы и пакеты на более высоких уровнях.
EN: These bits ultimately make up the frames and packets used at higher layers.

---

## Модуляция и линейное кодирование · Modulation and line coding
#modulation #line-coding

RU: Медный кабель несёт постоянный электрический заряд. Модуляция — способ менять напряжение этого заряда, чтобы передавать биты.
EN: A copper cable carries a constant electrical charge. Modulation is a way of varying that voltage to transmit bits.

RU: В сетях такая модуляция называется линейным кодированием (line coding) — устройства договариваются, какое напряжение = 0, а какое = 1.
EN: In networking, this modulation is specifically called **line coding** — devices agree on which voltage state means 0 and which means 1.

> [!example] Масштаб / Scale
> RU: Современные сети передают до 10 миллиардов бит в секунду по одному кабелю.
> EN: Modern networks can move up to 10 billion bits per second across a single cable.

---

## Итог · Summary

| Term / Термин | Meaning / Значение |
|---|---|
| Bit / Бит | Smallest unit of data (0 or 1) / Наименьшая единица данных |
| Modulation / Модуляция | Varying voltage to encode bits / Изменение напряжения для кодирования бит |
| Line coding | Modulation specific to networks / Модуляция применительно к сетям |

> [!warning] Частые ошибки / Common mistakes
> - RU: Line coding — разновидность модуляции для сетей · EN: Line coding is modulation **specifically for networks**
> - RU: Передаётся напряжение, не сила тока · EN: It's **voltage**, not current, that's varied
> - RU: Всё сводится к передаче бит на физическом уровне · EN: Everything reduces to bit transmission at the physical layer
