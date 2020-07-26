---
layout: archive
classes: wide
category: entry
title:  "CTF SombreroBlanco/Q4 - [Entry] Roma"
excerpt: "Mi solución para uno de los desafíos de la categoría 'Entry' del CTF realizado hace poco gracias a la gente de Sombrero Blanco y Q4"
author: p4ncontomat3
---
Mi solución para uno de los desafíos de la categoría 'Entry' del CTF realizado hace poco gracias a la gente de Sombrero Blanco y Q4

Para resolver este desafío creado por [n3v1l](https://twitter.com/n3v1l1) básicamente hay que prestar atención a los detalles entregados en la descripción.

![](https://uroven4.github.io/assets/images/content/Q4SB/roma/desc_roma.jpg)

De acuerdo al nombre del challenge `Roma` tiene sentido entonces suponer que el texto está en `Caesar Cipher`

`
Rfgn uvfgbevn rf znf ivrwn dhr ry uvyb arteb. Rfgn uvfgbevn cebivrar qr yn rcbpn qry Rzcrenqbe Prfne Nhthfgb. Qror fre hab qr ybf pevsnqbf znf nagvthbf qry zhaqb. Ybf npragbf ab chrqra fre hfnqbf ndhv gnzcbpb ybf fvtabf. Yn onaqren rf NyPrfneYbDhrRfqryPrfne
`

Por lo que usando la clásica herramienta [Cyberchef](https://gchq.github.io/CyberChef/) se aplica `Rot13` al texto obteniendo una respuesta legible.

![](https://uroven4.github.io/assets/images/content/Q4SB/roma/sol_roma.jpg)

`Q4SB{AlCesarLoQueEsdelCesar}`




[p4n](https://www.hackthebox.eu/home/users/profile/140674)