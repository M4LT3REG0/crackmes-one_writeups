# Write-up-crackmes.one-parkourk.exe1crack

Para visualizar lo que tenemos vamos a ver la gráfica y ya podemos ver la FLAG pero vamos a llegar a ella y demas un bypass para que valga cualquier contraseña que introduzcamos.

# "flag{th3_cr3d3n14ls_4r3_s4f3}"
![graficoparkour](https://user-images.githubusercontent.com/107126653/198892117-d6ce5f0c-5e19-4b51-8983-7856acb59342.png)

Vemos que aqui tenemos al empezar el programa en el x64 lo veremos como ENTRY POINT , y la visualización del programa nos poner first stage con un stop debug , podemos deducir que tiene un anti-debug. llamado IsdebuggerPresent , en cuál lo introduciremos en el LOG para ver en que dirección de memoria se encuentra y así anularlo.
![first stage](https://user-images.githubusercontent.com/107126653/198892118-ccea343e-cf76-4272-8ddb-e9da09bb5c33.png)

Previamente modificamos RAX Poniendole un 0 en vez de dejarlo en 1 ¿porqué? por que sino lo hacemos lo va interpretar como que lo estamos depurando(anti-debug) despues de hacer esto cambiamos el jne por el jmp para que nos salte al SECOND STAGE.
![rax0yjmp](https://user-images.githubusercontent.com/107126653/198892126-c805d674-5467-4b88-b990-03e375614e52.png)

Podemos ver la órdenes que estan en rojo que son las MODIFICADAS. para llegar a los niveles.
![level2level3](https://user-images.githubusercontent.com/107126653/198894068-a7171f82-ab59-4682-b15a-16520635c0d6.png)


Para enteder esa comparación nos iremos a RBP a la derecha y le daremos a click derecho A follow in dump  y nos fijamos en que esta comp-41 cogemos la dirección de memoria de RBP 00000000006FFE50 - 41 en calculadora de programación dando como resultado : 6FFEOF pues nos vamos a buscar esa direccion de memoria en el volcado/dump  y ahí empezaremos a contar cada dos dígitos es un byte POR EJEMPLO 00 (1) empezaremosa contar hasta llegar a 41 y llegaremos a la coomparación que si es igual pues nos saltará A dnde no queremos ir por lo que vamos a romper esa compraración introduciendo en lugar de 0 pues un 1
![2at3rbp](https://user-images.githubusercontent.com/107126653/198991389-f1c5e6d8-33f9-4931-b875-35703b09c42b.png)

 # La forma sencilla de esto es click sobre la direccion de memoria ensamblar(espacio) y modificar
![s](https://user-images.githubusercontent.com/107126653/198994516-b4398ee9-93de-40f5-bb7e-66615f6479ba.png)

# En este momento parcheamos el programa para guardar el progreso.
Llegamos al Third stage junto a la flag!
![flag](https://user-images.githubusercontent.com/107126653/198892133-323fac5f-c3a4-4afa-b893-4f38b02c0717.png)

Tenemos varias maneras un trabajo mal hecho pero rápido, es cambiar ese jne por un jmp pero un trabajo un poco mas limpio sería : push rax, pop rax que es lo mismo que los nops. push empuja rax al stack y luego lo popeamos . no tiene efecto sobre los registros.
![ultimo paso](https://user-images.githubusercontent.com/107126653/198996393-a4faf149-651a-41e6-9c8b-369fb5a33cb4.png)


Como veís ya podemos usar cualquier contraseña para acceder al programa . Sin utilizar flags
Para hacer esto debemos de darle click derecho y parchear y guardar el programa como por ejemplo parkourALL.exe

![parkourall](https://user-images.githubusercontent.com/107126653/198892150-cb231cfd-34bb-4d9a-988f-48a3c3835ae4.png)


Página de la actividad.

<https://www.crackmes.one/>


