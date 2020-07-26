---
layout: archive
classes: wide
category: entry
title:  "CTF SombreroBlanco/Q4 - [Crypto] Juguemos"
excerpt: "Mi solución para el challenge Juguemos del CTF realizado hace poco gracias a la gente de Sombrero Blanco y Q4"
author: p4ncontomat3
---
Mi solución para el challenge Juguemos del CTF realizado hace poco gracias a la gente de Sombrero Blanco y Q4

Para resolver este desafío creado por [n3v1l](https://twitter.com/n3v1l1) había que usar el texto entregado en la descripción del desafío.

![](https://uroven4.github.io/assets/images/content/Q4SB/juguemos/desc_juguemos.jpg)

```
IBLEWQ3LFNLXIMZUIVRDALJBIJVTWMDNIROWS2ZJIYQSYIRNIYVCSLBWIZBUENJVIBZEO3
LMIFXGEYLAIBYWM2ZBIFKEWSJSIA6CIRRIFNCCGVRZL5VUCMTQIZLWEWCEIFJWYLRCGNNHC
OKWHNQVAZ3GINUEORZPGFHFEWDQIQUHAJB4GFUVESLLIREWESKYIREWER2M
```

Bien resumido, el texto inicial estaba en base32 y la salida de ello estaba en base85, asique usando [cyberchef](https://gchq.github.io/CyberChef/) la solución salía rapidito sin tener que hacer mucho más.

![](https://uroven4.github.io/assets/images/content/Q4SB/juguemos/sol_juguemos.jpg)

`Q4SB{4lg0_3st4m0s_4pr3nd13nd0}`




[p4n](https://www.hackthebox.eu/home/users/profile/140674)