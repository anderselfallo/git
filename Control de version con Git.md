Un sistema de control de versiones como Git nos ayuda a guardar el historial de cambios y crecimiento de los archivos de nuestro proyecto.

En realidad, los cambios y diferencias entre las versiones de nuestros proyectos pueden tener similitudes, algunas veces los cambios pueden ser solo una palabra o una parte específica de un archivo específico. Git está optimizado para guardar todos estos cambios de forma atómica e incremental, o sea, aplicando cambios sobre los últimos cambios, estos sobre los cambios anteriores y así hasta el inicio de nuestro proyecto.


## Las tres secciones principales de un proyecto de Git

--> El directorio de Git (Git Directory, Repository)
    
--> El directorio de trabajo (Working Directory)
    
--> El área de preparación (Staging Area)
    


>  - El comando para iniciar nuestro repositorio, o sea, indicarle a Git que queremos usar su sistema de control de versiones en nuestro proyecto, es `git init`.
>  - Se crea una carpeta .git. El cual es el repositorio local donde Git almacena los metadatos y la base de datos de objetos para el proyecto. Es la parte más importante de Git, y es lo que se copia cuando clonas un repositorio desde otro ordenador.
>  - Se crea un archivo sencillo que define el staging area, generalmente está contenido en el directorio de Git, que almacena información acerca de lo que va a ir en tu próxima confirmación.

> El comando para que nuestro repositorio sepa de la existencia de un archivo o sus últimos cambios es `git add`. Este comando no almacena las actualizaciones de forma definitiva, solo las guarda en algo que conocemos como “Staging Area”.

> El comando para almacenar definitivamente todos los cambios que por ahora viven en el staging area es `git commit`. También podemos guardar un mensaje para recordar muy bien qué cambios hicimos en este commit con el argumento `-m "Mensaje del commit"`.

![[Pasted image 20211123212502.png]]

> Por último, si queremos mandar nuestros commits a un servidor remoto, un lugar donde todos podamos conectar nuestros proyectos, usamos el comando `git push`.


![](https://static.platzi.com/media/user_upload/GIT%20GITHUB-21de2769-fd6c-4835-b078-04128276f16f.jpg)

- **Historial del archivo en una sola linea por commit**
	```shell
	$ git log --oneline <File name> ## No es necesario agregar el nombre del archivo
	```
- **Grafico de las ramas **
	```shell
	$ git log --graph --oneline
	```
- **Eliminar un archivo de *stare area***
	```shell
	$ git rm --cached <File name>
	```
	
- **Git-Commit no puede abrir vim**

	```shell
	$ git config --global core.editor vim
	```
	
- **Configuraciones de Git**
	```shell
	$ git config --global -e
	```

- **Ver las configuraciones que tiene Git**

	```shell
	$ git config --list
	```
	
	- **Ver donde estan guardadas las configuraciones**
	
		```shell
		$ git config --list --show-origin
		```
		


![](https://static.platzi.com/media/user_upload/Analizar%20cambios%20en%20los%20archivos%20de%20tu%20proyecto%20con%20Git-f6f2fe08-e2e9-46ef-86fa-6180354bc151.jpg)

__________________________________
# Ciclo de trabajo en Git	
___________________________________________

![[Pasted image 20211124020404.png]]

![](https://static.platzi.com/media/user_upload/CicloBasico-c7cf1961-2813-4a23-ab2a-14c315dbf819.jpg)

- **Mueve el archivo al esta Untracked**
	
	```shell
	$ git rm --cached <File Name>
	```
- **Elimina el Archivo Git y disco duro**
	> Git guarda el registro de la existencia de los archivos, por lo que podremos recuperarlos si es necesario (pero debemos usar comandos más avanzados).
	```shell
	$ git rm --force <File Name>
	```
	
	![](https://static.platzi.com/media/user_upload/gitworkflow-b47db71b-3714-4358-a462-a35d2c4242af.jpg)
- **Del estado "Staged" para devolverlos a su estado anterior**
	
	> Si los archivos venían de Unstaged, vuelven allí. Y lo mismo se venían de Untracked. *Recupera el estado anterior del archivo*
			
	```shell
	$ git restore <File Name>
	```
		
	![](https://static.platzi.com/media/user_upload/estados-git-0acb84f7-5080-4098-99d9-59012a3b8e86.jpg)
	
	
	----
	# BRANCH
	----
	Git es una base de datos muy precisa con todos los cambios y crecimiento que ha tenido nuestro proyecto. Los commits son la única forma de tener un registro de los cambios. Pero las ramas amplifican mucho más el potencial de Git.

**Todos los commits se aplican sobre una rama**. Por defecto, siempre empezamos en la rama master (pero puedes cambiarle el nombre si no te gusta) y creamos nuevas ramas, a partir de esta, para crear flujos de trabajo independientes.

Crear una nueva rama se trata de copiar un commit (de cualquier rama), pasarlo a otro lado (a otra rama) y continuar el trabajo de una parte específica de nuestro proyecto sin afectar el flujo de trabajo principal (que continúa en la rama master o la rama principal).

Los equipos de desarrollo tienen un estándar: Todo lo que esté en la rama master va a producción, las nuevas features, características y experimentos van en una rama “development” (para unirse a master cuando estén definitivamente listas) y los issues o errores se solucionan en una rama “hotfix” para unirse a master tan pronto como sea posible.

> Crear una nueva rama lo conocemos como **Checkout**. Unir dos ramas lo conocemos como **Merge**.

Podemos crear todas las ramas y commits que queramos. De hecho, podemos aprovechar el registro de cambios de Git para crear ramas, traer versiones viejas del código, arreglarlas y combinarlas de nuevo para mejorar el proyecto.

Solo ten en cuenta que combinar estas ramas (sí, hacer “merge”) puede generar conflictos. Algunos archivos pueden ser diferentes en ambas ramas. Git es muy inteligente y puede intentar unir estos cambios automáticamente, pero no siempre funciona. En algunos casos, somos nosotros los que debemos resolver estos conflictos “a mano”.
	
![](https://static.platzi.com/media/user_upload/Branch%20y%20Checkout-9d05b5e2-887f-4fcb-9065-18079bb3c8a9.jpg)
![](https://static.platzi.com/media/user_upload/07.Branch_rama-44cd5ab0-fea6-4687-8256-16338098d94f.jpg)

### Volver en el tiempo de los *"git commit"*
>```shell
>$ git checkout <COMMIT ID> 
>```
> Podemos volver a cualquier versión anterior de un archivo específico o incluso del proyecto entero. Esta también es la forma de crear ramas y movernos entre ellas.
	
> **Elimina todo los *Commit* desde el `COMMIT ID` asignado en adelante. Todo los cambio de los commit pasan al estado *Untracked* o Working Directory en espera de un nuevo *Commit***.
>```shell
>$ git reset <COMMIT ID>
>```
>>`git reset`-->no solo “volvemos en el tiempo”, sino que borramos los cambios que hicimos después de este commit.
>>```shell
>>$ git reset <COMMIT ID> --hard
>>```
	>>>Con el argumento `--hard`, borrando toda la información que tengamos en el área de staging (y perdiendo todo para siempre)
>>
>>```shell
>>$ git reset <COMMIT ID> --soft
>>```
	>>>Con el argumento `--soft`, que mantiene allí los archivos del área de staging para que podamos aplicar nuestros últimos cambios pero desde un commit anterior.

	
![](https://static.platzi.com/media/user_upload/Volver%20en%20el%20tiempo%20en%20nuestro%20repositorio%20utilizando%20reset%20y%20checkout-78a042b3-a254-4fc9-bd8e-91734caa02b4.jpg)


**Regresar a la rama master**
```shell
$ git checkout master
```