---
layout: archive
classes: wide
category: misc
title:  "CTF SobreroBlanco/Q4 - [Misc] Viaje Mistico"
excerpt: "Mi solución para el challenge de Stego 'Viaje Mistico' del CTF realizado por Sombrero Blanco y Q4"
author: p4ncontomat3
---
Mi solución para el challenge de Stego 'Viaje Mistico' creado por [n3v1l](https://twitter.com/n3v1l1) 

![](https://uroven4.github.io/assets/images/content/Q4SB/viaje/desc_viaje.jpg)

La descripción del desafío incluía un texto con muchos `pika pika pikachu pika pi pika pi` 

![](https://uroven4.github.io/assets/images/content/Q4SB/viaje/text_viaje.jpg)

![](https://media.giphy.com/media/QZB0rrcGLljpu/giphy.gif)

bueno, el texto estaba en un lenguaje esterico llamado [pikalang](https://github.com/groteworld/pikalang) y para poder saber que decía me ayudé de la vieja confiable

![](https://uroven4.github.io/assets/images/content/Q4SB/viaje/viejaconfiable.png)

Usando el interprete de pikalang de [dcode.fr](https://www.dcode.fr/pikalang-language) pude saber que cosa decían los `pika pika pikachu pika pi pika pi` 

![](https://uroven4.github.io/assets/images/content/Q4SB/viaje/pikalang_viaje.jpg)

pero, resulta que ahí no terminaba la cosa, porque me esperaba un lindo mensaje que decía:

```
Excelente! Ahora viene lo weno: D'`$q]]~}5Y{iyU5AQQrrppK]ml)ii3Vf0/.b>O_)]rZp6nVl2jinmfe+Lbgf_^]#a`Y^WVzZSXWPt7SRQJONMLEiIHG)?cCB$@9>=<54X87w/43,P*/('K+*j(!E%|{A!~wv<tsxwpo5srqSi/mOkdcb(`H^]\"`_XW\UyxwWVU7SLp]
```

El cual estaba en oootro lenguaje esoterico [malbolge](http://malbolge.doleczek.pl/) y así al fin obtuve la preciada flag

![](https://uroven4.github.io/assets/images/content/Q4SB/viaje/malbolge_viaje.jpg)

`Q4SB{l4_m3d14_v0l4!!!}`


[p4n](https://www.hackthebox.eu/home/users/profile/140674)