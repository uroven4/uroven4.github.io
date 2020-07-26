---
layout: archive
classes: wide
category: stego
title:  "CTF SombreroBlanco/Q4 - [Stego] sartaarap"
excerpt: "Mi solución para el challenge de Stego 'sartaarap' del CTF realizado por Sombrero Blanco y Q4"
author: p4ncontomat3
---
Mi solución para el challenge de Stego 'sartaarap' creado por [dplastico](https://dplastico.me) 

![](https://uroven4.github.io/assets/images/content/Q4SB/sartaarap/desc_sartaarap.jpg)

La imagen del desafío era la "caratula" del Floral Shoppe de Macintosh Plus, en caso de que quieras cachar que onda el veiporweib puedes escuchar el album [aqui](https://vektroid.bandcamp.com/album/floral-shoppe)

![](https://uroven4.github.io/assets/images/content/Q4SB/sartaarap/image_sartaarap.jpg)

`Aesthetics`

Al tirarle un binwalk al jpg me di cuenta que tenia un zip dentro

![](https://uroven4.github.io/assets/images/content/Q4SB/sartaarap/binwalk_sartaarap.jpg)

Luego, de descomprimir usando `binwalk -e mac.jpg` usé john para obtener la contraseña y descomprimir el zip oculto de la imagen

![](https://uroven4.github.io/assets/images/content/Q4SB/sartaarap/extract_sartaarap.jpg)

Obteniendo un archivo de texto y un mp3, el archivo de texto (cai en la trampa e intente usarlo como flag), en realidad no aportaba mucho asique segui con el mp3.

![](https://uroven4.github.io/assets/images/content/Q4SB/sartaarap/files_sartaarap.jpg)

Básicamente el mp3, en más o menos el minuto 1:45, podía escucharse la voz de alguien deletreando algo que no se entendia bien, asique solo fue necesario usar revert para escuchar el audio de atrás para adelante y sorprendernos con que un amable sujeto nos daba clarito la flag y solo había que escribirla luego de la cuenta de 3, uno dos tres 

![](https://uroven4.github.io/assets/images/content/Q4SB/sartaarap/audio_sartaarap.jpg)

`Q4SB{dificilescantarlaflag}`


[p4n](https://www.hackthebox.eu/home/users/profile/140674)