## Write-up-crackmes.one-parkourk.exe1crack

# (AVISO) En este write-up no voy a dedicarle a explicaciones técnicas.
# (NOTICE) In this write-up I am not going to devote to technical explanations.


Para visualizar lo que tenemos vamos a ver la gráfica y ya podemos ver la FLAG pero vamos a llegar a ella y demas un bypass para que valga cualquier contraseña que introduzcamos.
To visualize what we have we are going to see the graph and we can already see the FLAG but we are going to get to it and bypass it so that any password we enter will be valid.

# "flag{th3_cr3d3n14ls_4r3_s4f3}"
![graficoparkour](https://user-images.githubusercontent.com/107126653/198892117-d6ce5f0c-5e19-4b51-8983-7856acb59342.png)

Vemos que aqui tenemos al empezar el programa en el x64 lo veremos como ENTRY POINT , y la visualización del programa nos poner first stage con un stop debug , podemos deducir que tiene un anti-debug. llamado IsdebuggerPresent , en cuál lo introduciremos en el LOG para ver en que dirección de memoria se encuentra y así anularlo.
We see that here we have to start the program in the x64 we will see it as ENTRY POINT, and the visualization of the program put us first stage with a stop debug, we can deduce that it has an anti-debug. called IsdebuggerPresent, in which we will introduce it in the LOG to see in which memory address it is and thus to annul it.

![first stage](https://user-images.githubusercontent.com/107126653/198892118-ccea343e-cf76-4272-8ddb-e9da09bb5c33.png)

Previamente modificamos RAX Poniendole un 0 en vez de dejarlo en 1 ¿porqué? por que sino lo hacemos lo va interpretar como que lo estamos depurando(anti-debug) despues de hacer esto cambiamos el jne por el jmp para que nos salte al SECOND STAGE.
Previously we modify RAX putting a 0 instead of leaving it in 1 why? because if we don't do it it will interpret it as that we are debugging (anti-debug) after doing this we change the jne by the jmp so that it jumps us to the SECOND STAGE.

![rax0yjmp](https://user-images.githubusercontent.com/107126653/198892126-c805d674-5467-4b88-b990-03e375614e52.png)

Podemos ver la órdenes que estan en rojo que son las MODIFICADAS. para llegar a los niveles.
We can see the orders that are in red which are the MODIFIED ones. to reach the levels.

![level2level3](https://user-images.githubusercontent.com/107126653/198894068-a7171f82-ab59-4682-b15a-16520635c0d6.png)


Para enteder esa comparación nos iremos a RBP a la derecha y le daremos a click derecho A follow in dump  y nos fijamos en que esta comp-41 cogemos la dirección de memoria de RBP 00000000006FFE50 - 41 en calculadora de programación dando como resultado : 6FFEOF pues nos vamos a buscar esa direccion de memoria en el volcado/dump  y ahí empezaremos a contar cada dos dígitos es un byte POR EJEMPLO 00 (1) empezaremosa contar hasta llegar a 41 y llegaremos a la coomparación que si es igual pues nos saltará A dnde no queremos ir por lo que vamos a romper esa compraración introduciendo en lugar de 0 pues un 1
-----------------------------------------------------------------------------------------------------------------------
To understand this comparison we will go to RBP to the right and we will give right click A follow in dump and we notice that this comp-41 we take the memory address of RBP 00000000006FFE50 - 41 in programming calculator giving as a result : 6FFEOF then we are going to look for that memory address in the dump and there we will begin to count every two digits is a byte FOR EXAMPLE 00 (1) we will begin to count until we reach 41 and we will arrive at the comparison that if it is equal then we will jump to where we do not want to go so we will break that comparison entering instead of 0 then a 1.

![2at3rbp](https://user-images.githubusercontent.com/107126653/198991389-f1c5e6d8-33f9-4931-b875-35703b09c42b.png)

 # La forma sencilla de esto es click sobre la direccion de memoria ensamblar(espacio) y modificar
 # The simple way to do this is to click on the assembly memory address(space) and modify

![s](https://user-images.githubusercontent.com/107126653/198994516-b4398ee9-93de-40f5-bb7e-66615f6479ba.png)

# En este momento parcheamos el programa para guardar el progreso.
# At this point we patch the program to save the progress.

Llegamos al Third stage junto a la flag!
We arrived at the Third stage next to the flag!

![flag](https://user-images.githubusercontent.com/107126653/198892133-323fac5f-c3a4-4afa-b893-4f38b02c0717.png)

Tenemos varias maneras un trabajo mal hecho pero rápido, es cambiar ese jne por un jmp pero un trabajo un poco mas limpio sería : push rax, pop rax que es lo mismo que los nops. push empuja rax al stack y luego lo popeamos . no tiene efecto sobre los registros.
We have several ways a bad but quick job, is to change that jne for a jmp but a little cleaner job would be : push rax, pop rax which is the same as the nops. push push pushes rax to the stack and then we pop it . it has no effect on the registers.

![ultimo paso](https://user-images.githubusercontent.com/107126653/198996393-a4faf149-651a-41e6-9c8b-369fb5a33cb4.png)


Como veís ya podemos usar cualquier contraseña para acceder al programa . Sin utilizar flags
Para hacer esto debemos de darle click derecho y parchear y guardar el programa como por ejemplo parkourALL.exe
As you can see we can use any password to access the program. Without using flags
To do this we must right click and patch and save the program as for example parkourALL.exe

![parkourall](https://user-images.githubusercontent.com/107126653/198892150-cb231cfd-34bb-4d9a-988f-48a3c3835ae4.png)


Página de la actividad.
Activity page.


<https://www.crackmes.one/>


