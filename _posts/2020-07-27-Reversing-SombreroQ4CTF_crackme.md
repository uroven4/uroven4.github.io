---
layout: archive
classes: wide
category: entry
title:  "CTF SombreroBlanco/Q4 - [Rev] crackme"
excerpt: "Mi solución para el challenge 'crackme' del CTF realizado hace poco gracias a la gente de Sombrero Blanco y Q4"
author: p4ncontomat3
---
Mi solución para el challenge 'crackme' del CTF realizado hace poco gracias a la gente de Sombrero Blanco y Q4

Para resolver este desafío creado por [dplastico](https://dplastico.me/) había que analizar el binario entregado, para lo que usé ghidra.

Aqui tenemos las decompilaciones de las funciones mas importantes del binario:

#### main:

![](https://uroven4.github.io/assets/images/content/Q4SB/crackme/main.png)

Podemos ver que se llama con dos argumentos, `param_1` es la cantidad de argumentos y `param_2` es el argumento con el que corremos el binario. Vemos que, en la linea 15, hace un check para ver que la cantidad de argumentos sea 2, es decir, que estemos corriendo el binario con un argumento. A esto se debe el error que vemos al correrlo sin argumentos: "Need exactly one argument".

Luego de hacer el check de argumentos se definen un par de variables. Poco despues (linea 24) vemos un printf de una string que parece tener el formato de flag del CTF: "Q4SB{}". Tiene un format specifier que se junta con otro pedazo de string, y solo se llega a ejecutar si los if de la linea 21 y 23 son True. Podemos tomar como objetivo entonces pasar estos if.

El primero es sumamente sencillo: sVar2 tiene que ser 9. sVar2 esta definido como `strlen(*(char **)(param_2 + 8));`, basicamente la length de la string `param_2`, que es el argumento con el que corremos el binario. Con esto sabemos entonces que nuestro argumento tiene que tener una longitud de 9.

Pasamos al siguiente if. Este simplemente checkea que `uVar1 != 0`. `uVar1` esta definida como `check_pw(*(long *)(param_2 + 8),(long)&local_24,(long)&local_1a);` y aqui es donde entra en el juego la segunda funcion importante del binario: `check_pw`. Dejo aqui su decompilación:

#### check_pw:

![](https://uroven4.github.io/assets/images/content/Q4SB/crackme/check_pw.png)

Volviendo al if que queriamos pasar - necesitamos que lo que check_pw retorne no sea igual a 0. Podemos ver que hay solo dos posibilidades, 0 y 1, por lo que el objetivo es hacer que se ejecute el `return 1;`.

El `return 0;` se ejecuta en una condicion dentro de un while loop, por lo que vamos a tener que hacer que esa condicion sea falsa durante todas las iteraciones del while loop, para luego salir de este y ejecutar el `return 1;`. En la condicion se usan `param_1`, `param_2` y `param_3`. Podemos volver a la call a `check_pw` desde la funcion `main` para ver que valores toman estos parametros.

Vemos entonces que `param_1 = param_2`, `param_2 = (long)&local_24 = * 0x63617243616c7064` y `param_3 = (long)&local_1a = * 0x102010503020302`.

`param_1` pasa a ser el argumento con el que corremos el binario. Tenemos que hacer que sea igual a `(char)(*(char *)(param_3 + local_c) + *(char *)(param_2 + local_c))` para no llegar al `return 0;` y al llegar a la newline salir del while loop. Esta parte de la funcion compara byte por byte los parametros de una manera que es mas facil entender mirando la desensamblacion de la funcion. Para esto se puede usar cualquier disassembler, voy a usar el de ghidra ya que lo tengo abierto :P

![](https://uroven4.github.io/assets/images/content/Q4SB/crackme/disasm.png)

Esa es la parte que nos importa. Vemos que termina con un `cmp`, que podemos asumir es el if que tenemos que pasar. Si seguimos un poco el flujo del codigo, podemos notar que el ultimo valor que se carga al `RAX` es el byte en cuestion del argumento con el que estamos corriendo el binario. Cada byte del argumento va a ser `al` en este `cmp`, y va a ser comparado con el byte respectivo de la string del binario.

Personalmente no soy muy experimentado en reversing en general (tengo mas experiencia en pwn) por lo que me manejo mejor con un debugger, entonces para esta parte voy a usar GDB.

Seteo un breakpoint en main y luego corro el binario con un argumento cualquiera de longitud 9 (Ej: "YYYYYYYYY"). Hago un `disas check_pw` para checkear la direccion de la instruccion del `cmp` y seteo un breakpoint ahi tambien. Lo que voy a hacer ahora es setear un hook para que cada vez que haga `continue` gdb me muestre el valor que este tomando parte en la comparacion, que como podemos ver en el disassembly es `[rbp-5]`. El plan es, por cada byte que hagamos el `cmp` seteemos a `al` manualmente al valor que necesitamos, que esta almacenado en `[rbp-5]`. Luego seteamos `rax` al valor que nos muestra el hook y seguimos con la ejecucion hasta completar la string, salir del while loop, y finalmente hacer que `check_pw` retorne 1. Dejo aqui los comandos de gdb usados:

```
# Break en main
b main
# Correr el binario con argumento
r YYYYYYYY
# Ver la direccion de la instruccion cmp en check_pw
disas check
# Break ahi
b *0x000055555555478c
# Setear el hook
define hook-stop
> x/xb $rbp-5
> end

# Ahora hacemos un continue para saltar al cmp. Hacemos esto varias veces (9), seteando rax al valor mostrado por el hook, para pasar el cmp
c
set $rax=[hook-value]
# (hay que introducir hook-value manualmente)
```

Haciendo eso deberiamos pasar todos los `cmp`, finalmente logrando el `return 1;`, y el binario deberia correr el printf que esta en main, que en teoria nos daria la flag.
Pero ojo! Hacemos esto y no nos da la flag, sino "Q4SB{YYYYYYYYYyeyeah!}"! Nos printeo el argumento que le dimos al binario. Volviendo a la dcompilacion en ghidra, tiene sentido. Pero como hacemos que nos de la flag verdadera? Pasandole el argumento correcto. El argumento correcto esta formado por los valores que nos mostraba el hook que seteamos, y que posteriormente manualmente le pusimos al `rax`. Podemos entonces tomar cada uno de estos valores y crear una string a partir de ellos, para despues correr el binario. 

Agregamos lo siguiente al hook para que nos muestre tambien la string a la que corresponde el valor del byte en cuestion:

```
define hook-stop
> x/xb $rbp-5
> x/s $rbp-5
> end
```

y nos hacemos nuestra string manualmente con cada uno de estos valores. Tenemos que seguir seteando rax manualmente para poder ver todos los valores. Finalmente quedamos con "fsndHscdm", y si simplemente corremos el binario con ese argumento llegamos a la call a printf que nos da la flag real.

`Q4SB{fsndHscdmyeyeah!}`

[p4n](https://www.hackthebox.eu/home/users/profile/140674)
