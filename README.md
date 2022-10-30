# Write-up-crackmes.one-parkourk.exe1crack

Para visualizar lo que tenemos vamos a ver la grafica y ya podemos ver la FLAG pero vamos a llegar a ella y demas un bypass para que valga cualquier contraseña que introduzcamos.

![graficoparkour](https://user-images.githubusercontent.com/107126653/198892117-d6ce5f0c-5e19-4b51-8983-7856acb59342.png)

vemos que aqui tenemos al empezar el programa en el x64 lo veremos como ENTRY POINT , y la visualizacion del programa nos poner first stage con un stop debug , podemos deducir que tiene un anti-debug.
![first stage](https://user-images.githubusercontent.com/107126653/198892118-ccea343e-cf76-4272-8ddb-e9da09bb5c33.png)

previamnete modificamos RAX  ------------- cambiamos el jne por el jmp para que nos salte al SECOND STAGE.
![rax0yjmp](https://user-images.githubusercontent.com/107126653/198892126-c805d674-5467-4b88-b990-03e375614e52.png)


Modificamos esos NOPS ya que si no llenamos esas dos ordenes nos llevaran al donde no queremos.. asi que vamos derechos al THIRD STAGE
![3stage](https://user-images.githubusercontent.com/107126653/198892131-a25472a4-add1-4eae-a92c-96e894caef46.png)



Llegamos al Third stage junto a la flag!
![flag](https://user-images.githubusercontent.com/107126653/198892133-323fac5f-c3a4-4afa-b893-4f38b02c0717.png)




Como veis ya podemos usar cualquier contraseña para acceder al programa.Sin utilizar flags

![parkourall](https://user-images.githubusercontent.com/107126653/198892150-cb231cfd-34bb-4d9a-988f-48a3c3835ae4.png)



