---
layout: archive
classes: wide
category: entry
title:  "CTF SombreroBlanco/Q4 - [Crypto] Terrible de shoro"
excerpt: "Mi solución para el challenge 'Terrible de shoro' del CTF realizado hace poco gracias a la gente de Sombrero Blanco y Q4"
author: p4ncontomat3
---
Mi solución para el challenge 'Terrible de shoro' del CTF realizado hace poco gracias a la gente de Sombrero Blanco y Q4

Para resolver este desafío creado por [n3v1l](https://twitter.com/n3v1l1) había que usar el texto entregado en la descripción del desafío.

![](https://uroven4.github.io/assets/images/content/Q4SB/shoro/desc_shoro.jpg)

`
5Q%QR25QR2-U#U/%R3U8Q2U#PU%R9Q3
`

Debo decir que me costó mucho, pero después de varios intentos de muchas cosas y blabla, de la nada salió la idea de

```
shoro, shoro, shoro, 
que puede ser?
shoro?
ah xd fijo es XOR
```

y así fue, asique corriendo a [cyberchef](https://gchq.github.io/CyberChef/) y usando `XOR bruteforce`, salió la flag clarita jojo

![](https://uroven4.github.io/assets/images/content/Q4SB/shoro/sol_shoro.jpg)

`Q4SB{T0D03ST03SL4B4ND3R4Y0S4B14D3X0Rkk}`



[p4n](https://www.hackthebox.eu/home/users/profile/140674)