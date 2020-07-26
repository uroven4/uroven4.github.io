---
layout: archive
classes: wide
category: entry
title:  "CTF SobreroBlanco/Q4 - [Entry] 10%"
excerpt: "Mi solución para el challenge '10%' del CTF realizado por Sombrero Blanco y Q4"
author: p4ncontomat3
---
Mi solución para el challenge '10%' del CTF realizado por Sombrero Blanco y Q4

![](https://uroven4.github.io/assets/images/content/Q4SB/10/desc_10.jpg)

Para resolver este desafío que la verdad no cacho cual de los organizadores lo hizo, pero si me di cuenta que el sitio de esta pulenta AFP fue hecha por `El medio más serio de Chile`, [LaLegal](https://lalegal.news/)

![](https://uroven4.github.io/assets/images/content/Q4SB/10/site_10.jpg)

La verdad es que me reí caleta haciendo este desafío, por lo que debo decir que, fué mi favorito de este evento. Asique por lo mismo estoy cachando en tomar el plan rancagua de [Afpvidalife](https://afpvidalife.com/)

Bueno, volviendo a la solucion del challenge, haciendo un poquito de enumeración básica al sitio [Afpvidalife](https://afpvidalife.com/), me di cuenta de cierta info 'interesante' que había en `robots.txt`

![](https://uroven4.github.io/assets/images/content/Q4SB/10/enum_10.jpg)



Le di una miradita a ese directorio, y había algo que evidentemente era importante para poder resolverlo ya que la imágen era un claro énfasis al CTF en curso.

![](https://uroven4.github.io/assets/images/content/Q4SB/10/image_10.jpg)

Después de batallar un buen rato con la imagen (asumiendo que era un stego), dieron un `hint gratis` subiendo otra versión de la imagen, ya que al parecer la que estaba en el sitio no era la que correspondía.

![](https://uroven4.github.io/assets/images/content/Q4SB/10/descupdate_10.jpg)

Teniendo eso en cuenta, segui con la resolución del stego haciendo un pequeño guessing, ya que la imagen estaba en el directorio `chileelmejorpaisdeshile` y considerando que evidentemente Chile es el mejor país de todo $hile, le pegué un pequeño corte a rockyou buscando solo las coincidencias con `chile`, para luego usar ese mini diccionario con stegcracker obteniendo un archivo de texto de salida con la codiciada flag.

![](https://uroven4.github.io/assets/images/content/Q4SB/10/sol_10.jpg)

`Q4SB{Ch1l3_3l_m3j0r_p4is_d3_ch1l1t0!!!}`


[p4n](https://www.hackthebox.eu/home/users/profile/140674)