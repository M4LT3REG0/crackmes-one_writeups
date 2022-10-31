# Write-up-crackmes.one-parkourk.exe1crack

Para visualizar lo que tenemos vamos a ver la grafica y ya podemos ver la FLAG pero vamos a llegar a ella y demas un bypass para que valga cualquier contraseña que introduzcamos.

# "flag{th3_cr3d3n14ls_4r3_s4f3}"
![graficoparkour](https://user-images.githubusercontent.com/107126653/198892117-d6ce5f0c-5e19-4b51-8983-7856acb59342.png)

vemos que aqui tenemos al empezar el programa en el x64 lo veremos como ENTRY POINT , y la visualizacion del programa nos poner first stage con un stop debug , podemos deducir que tiene un anti-debug. llamado IsdebuggerPresent , en cual lo introduciremos en el LOG para ver en que direccion de memoria se encuentra y asi anularlo.
![first stage](https://user-images.githubusercontent.com/107126653/198892118-ccea343e-cf76-4272-8ddb-e9da09bb5c33.png)

previamente modificamos RAX  ------------- cambiamos el jne por el jmp para que nos salte al SECOND STAGE.
![rax0yjmp](https://user-images.githubusercontent.com/107126653/198892126-c805d674-5467-4b88-b990-03e375614e52.png)

Podemos ver la ordenes que estan en rojo que son las MODIFICADAS. para llegar a los niveles.
![level2level3](https://user-images.githubusercontent.com/107126653/198894068-a7171f82-ab59-4682-b15a-16520635c0d6.png)


para enteder esa comparacion no iremos a RBP a la derecha y le daremos a click derecho A follow in dump  y nos fijamos en que esta comp-41 cogemos la direccion de memoria de RBP 00000000006FFE50 - 41 en calculadora de programacion dando como resultado : 6FFEOF pues nos vamos a buscar esa direccion de memoria en el volcado/dump  y ahi empezaremos a contar cada dos digitos es un byte POR EJEMPLO 00 (1) empezaremosa contar hasta llegar a 41 y llegaremos a la coomparacion que si es igual pues no saltará A dnde no queremos ir asique vamos a romper esa compraracion introduciendo en lugar de 0 pues un 1
![2at3rbp](https://user-images.githubusercontent.com/107126653/198991389-f1c5e6d8-33f9-4931-b875-35703b09c42b.png)

 # La forma sencilla de esto es click sobre la direccion de memoria ensamblar(espacio) y modificar
![s](https://user-images.githubusercontent.com/107126653/198994516-b4398ee9-93de-40f5-bb7e-66615f6479ba.png)

# En este momento parcheamos el programa para guardar el progreso.
Llegamos al Third stage junto a la flag!
![flag](https://user-images.githubusercontent.com/107126653/198892133-323fac5f-c3a4-4afa-b893-4f38b02c0717.png)

Tenemos varias maneras un trabajo mal hecho pe pro rapido, es cambiar ese jne por un jmp pero un trabajo un poco mas limpio sería : push rax, pop rax que es lo mismo que los nops. push empuja rax al stack y luego lo popeamos . no tiene efecto sobre los registros.
![ultimo paso](https://user-images.githubusercontent.com/107126653/198996393-a4faf149-651a-41e6-9c8b-369fb5a33cb4.png)


Como veis ya podemos usar cualquier contraseña para acceder al programa.Sin utilizar flags
Para hacer esto debemos de darle click derecho y parchear y guardar el programa como por ejemplo parkourALL.exe

![parkourall](https://user-images.githubusercontent.com/107126653/198892150-cb231cfd-34bb-4d9a-988f-48a3c3835ae4.png)



