---
layout: archive
classes: wide
category: entry
title:  "CTF SombreroBlanco/Q4 - [Crypto] El Espejo"
excerpt: "Mi solución para el challenge 'El Espejo' del CTF realizado hace poco gracias a la gente de Sombrero Blanco y Q4"
author: p4ncontomat3
---
Mi solución para el challenge 'El Espejo' del CTF realizado hace poco gracias a la gente de Sombrero Blanco y Q4

Para resolver este desafío creado por [n3v1l](https://twitter.com/n3v1l1) había que usar el texto entregado en la descripción del desafío.

![](https://uroven4.github.io/assets/images/content/Q4SB/espejo/desc_espejo.jpg)

`
HV EVRZ NZH HRNKOV VHGV XRUIZWLI KLI OL GZMGL GV TZMZHGV OZ UOZT JFV WVYV RI ZWVMGIL VHGVXRUIZWLIVHSVYIVL
`

Ya que el nombre del desafío es `espejo` empecé a cachar tipos de encoding o ciphers que tuvieran que ver con `mirror`, asi fue como llegue una vez más a usar la vieja confiable y su [Atbash mirror cipher](https://www.dcode.fr/atbash-cipher) 

![](https://uroven4.github.io/assets/images/content/Q4SB/espejo/atbash_espejo.jpg)

Obteniendo un texto como respuesta de este desafío

![](https://uroven4.github.io/assets/images/content/Q4SB/espejo/sol_espejo.jpg)

`Q4SB{ESTECIFRADORESHEBREO}`




[p4n](https://www.hackthebox.eu/home/users/profile/140674)