![[Pasted image 20211201210634.png]]

-----
## Repositorio local
**Ver en que rama nos encotramos**
```shell
 $ git branch
 ```
**Crear la rama y cambiarnos de rama**
 ```shell
 $ git checkout -b <BRANCH NAME>
 ```
 or 
 ```shell
 $ git checkout --branch <BRANCH NAME>
 ```
 
 **Ir a una rama ya creada**
  ```shell
 $ git checkout <BRANCH NAME>
 ```
-----
## Repositorio Remoto
**Creacion de la ramas *master* o *main* en el repositorio**
```shell
$ git push -u origin <master or main>
```
*Verificar el comando anterior*
```shell
$ git remote -v
```

>```shell
>$ git push -u origin <NOMBRE DE RAMAS LOCAL>:<NOMBRE DE RAMA EN EL REPOSITORIO>
>```
>> *NOMBRE DE LA RAMA LOCAL:*
>> Puede ser `master` o `nombre que creaste y deseas subir`
>
>>*NOMBRE DE LA RAMA EN EL REPOSITORIO*
>> Es el nombre de la rama que se le asignara en el repositorio. Puede ser distinto los nombre de la *Ramas local* con la *Rama del repositorio*
>
>> Si deseas que la rama *Ramas local* con la *Rama del repositorio* tenge el mismo nombre:
>>>```shell
>>>$ git push -u origin <BRANCH NAME> ## Nombre de la rama local que se le asignara el mismo nombre a la rama en el repositorio
>>>```

 *Después de ejecutar esto solo se necesita lo siguiente para seguir subiendo*
 ```shell
 $ git push
 ```
 
