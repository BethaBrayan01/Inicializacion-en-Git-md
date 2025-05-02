# GUIA RAPIDO Y SENCILLA PARA USAR GIT


---
---

## Introducción

Para empezar hay que saber que es GIT?
GIT es un sistema distribuido de sistema de control de versiones(es la herramienta que nos permite a nosotros tener un historial completo de todo el codigo que hemos desarrollando sobre nuestra aplicacion).

GIT trabaja de manera descentralizada, que cada desarrollador tiene copia completa del codigo que se esta trabajando, y que los desarrolladores tienen la opcion sobre estos archivos luego poder subirlos a un servidor central y de esta manera sincronizar los cambios entre todos los desarrolladores.

---

## Configuracion y Comandos

La aplicacion de estas configuraciones se haran en Debian 12 (algunas cosas pueden variar segun en la ISO/distribucion que tengas).

Empecemos por la configuracion:

* git config --global user.name "nombre del usuario"
* git config --global user.email correo_electronico
     - estas 2 configuraciones se asociarán con tus commits de Git en todos tus repositorios. Esto es útil para identificar quién realizó un cambio en el proyecto. 
* git config --global core.editor "code --wait"
    - esta configuracion es para que VSC sea nuestro editor por defecto y la terminal se quede esperando hasta que cerremos nuestro editor (en este caso VSC). 
* git config -- global e
    - esta configuracion nos mostrarà (si todo esta bien) nuestro archivo de configuracion global se abrirà dentro de VSC, tomaremos el control de la terminal cuando cerremos VSC.
    
## Comandos de bash
 
ejecutamos: 

* ls (listado de carpetas).
* cd nombre_de_la_carpeta o directorio donde nos queremos mover.
* (una vez dentro de la carpeta o directorio) ejecutamos ls 
* ahora si queremos retroceder, ejecutamos (dentro de la carpeta que estamos) cd .. esto lo que hara es salirme del directorio y mandarme 1 mas atras en la jerquia, para verificar ejecutamos pwd y nos mostrarà en donde estamos.
* ahora dentro de la carpeta podemos crearnos otra carpeta para almacenar nuestro proyecto, lo creamos con el siguiente comando mkdir nombre_carpeta, ejm: mkdir proyectogit, volvemos a ejecutar ls y nos mostrarà la carpeta creada, ejm: home/usuario/proyectos/git/proyectogit.
ahora accedemos a èl (proyectogit) con el comando cd proyectogit 
* ahora para inicializar un proyecto dentro de nuestra carpeta, ejecutamos el comando git init y no mostrarà que ha inicialidao un repositorio vacio en git home/usuario/proyectos/git/proyectogit/.git (el . (punto) significa que ese directorio se encuentra oculto.)
    - ejecutamos ls -a nos mostrara todos los archivos/directorios ocultos.
    - veremos el directorio .git y lo abrimos con cd .git
    - dentro de .git ejecutamos ls -a y nos mostrarà todos los archivos que se utlizan en git para gestionar nuestros proyectos, a esto se llama Detalle de Implementacion aqui es donde se van almacenar las distintas versiones de nuestro codigo, las distintas ramas, los commist, etc.
    - ahora para regresar a nuestro carpeta donde trabajaremos, ejecutasmos cd .. 
    
## Agregando Cambios a la Etapa stage

ejecutamos:

* (dentro de nuestra carpeta donde trabajaremos) code . (el . (punto) quiere decir que habras la carpeta en la cual yo me encuentro) nos mostrara el nombre de nuestra carpeta.
* una vez dentro de VSC en la seccion de nuestra carpeta creamos un archivo, depende que tipo de proyecto quisieramos trabajar nombre_del_archivo.extension
* realizamos lo que tengamos hacer dentro de ese archivo, luego guardamos (ctrl + s).
* ejecutamos el comando git status nos mostrarà el estado actual de nuestro repositorio. nos dira que no existe ningun commit y untracked files (que git no esta haciendo seguimiento) y nos mostrarà el nombre de nuestro archivo en color rojo, por defecto git no sigue todos los archivos.
* para  que git haga el seguimiento tenemos que ejecutar git add nombre_del_archivo.extension con esto pasaremos a la estapa stage
* luego ejecutamos git status para ver el estado de nuestro trabajo, nos mostrara que estamos en la breach master (rama principal), no tenemos ningun commit (comprometer) y que hay cambios listos para comprometer (pasar el archivo a commit) junto con el combre new file:  nombre_archivo.extension en color verde significa que esta encuentra en una etapa stage

## Estado commit

ejecutamos:

* git commit -m "colocar mensaje se entienda", ejm: git commit -m "commit incial".
* luego nos mostrarà un mensaje de que nuestros cambios han sido comprometidos
* luego ejecutamos git status y nos mostrar que estamos en la breach master y que no hay archivos que comprometer.

## Ignorando archivos y Directorios

Supongamos que tenemos mas de un archivo en nuestra carpeta de trabajo y para que no sean inlcuidos en nuestro repositorio de git, creamos un archivo sin nombre solo con extension .gitignore
     
* dentro del archivo .gitignore especificamos cuales son los archivos o directorios, ejm: tenemos un archivo2.txt y queremos ignorarlo, dentro de .gitignore lo mencionamos nombre_del_archivo.extension y tambien se puede ignorar carpetas.
* ejecutamos git status y veremos que el archivo2.txt ya no se encuentra pero si se encontrarà .gitignore (en color rojo)
* ahora agregaremos nuestro archivo .gitignore con el comando git add .gitignore y lo comprometemos inmediatamente git commit -m "agregando archivo gitignore" 
* luego ejecutamos git status y nos mostrarà que estamos en la breach master y que no hay nada que comitear
     
## Revisar Historial

![image alt] (https://github.com/BethaBrayan01/Inicializacion-en-Git-md/blob/fa70279aa805133bd17173b0b3fce56ee5e286cb/historial.png)

El siguiente comando nos motrarà el nombre la persona que hizo algun cambio, su correo y un mensaje de commit:

* git log

Pero al ser muy detallado nos puede confundir, asi que podemos ejecutar el siguiente comando :

* git log --oneline nos mostrarà un pequeño historial con un pequeño hash que sirve como identificador de ese commit seguido de mensajes que ponemos en cad commit, por eso es importante que los nombres como mensajes dentro de los commit sean algo que tengan sentido
    
En la parte (HEAD - master) mostrando status corto, nos dice donde estas, te dice "estas aqui", para salir de ese cuadro presionas la tecla q (hay casos en el que ejecutas el git log --oneline y te muestra el historial y no hay necesidad de presionar la tecla q)

## Ramas o Branches

![image alt](https://github.com/BethaBrayan01/Inicializacion-en-Git-md/blob/master/branches.png)

En la parte que dice "your work / someone else's work es una rama independiente cuando varios programadores trabajando en un mismo proyecto y cuando uno (yo) quiere trabajar independientemente y hacemos el trabajo necesario y cuando hayamos terminado podemos solicitar realizar un merge a la rama de master y podemos continuar con el desarrollo del programa.

Ahora ejecutamos un git status y nos mostrarà: 

* modificados : archivo.txt (en color verde)
y luego restauramos el archivo:

* git restore --staged archivo.txt
y ejecutamos git status y nos mostrarà:

* modificados: archcivo.txt (en rojo)
y descartamos esos cambios con el siguiente comando:

* git restore archivo.txt
ejecutamos el comando git status y nos mostrarà que no hay nada para hacer commit, el arbol de trabajo esta limpio.
Ahora antes de crear una rama, veremos en que rama NOSOTROS estamos, ejecutamos el siguiente comando:

* git branch

Nos mostrarà que estamos en la rama master que es la principal, ahora si queremos crear una rama, ejecutamos el comando:

* git checkout -b nombre_de_la_rama (ejemplo que la rama se llame ramab), nos mostrarà que nos hemos cambiado a una rama "ramab" y volvemos a ejecutar:

* git branch y nos mostrara las ramas que hay y a la que cambiamos (ramab):

- master
- ramab (en color verde)

Luego regresamos a VSC y realizamos los cambios necesaior en nuestro archivo.txt, guardamos y ejecutamos el comando git status y nos mostrarà:

* modificado: archivo.txt (en rojo)

ahora lo agregamos con:

* git add archivo.txt

Y luego hacemos un commit:

* git commit -m "actualizado archvio"

Y nos mostrarà por pantalla:

actulizado archivo 
"nro" file changed, "nro" insertios (+), "nro" deletions (-)

--> "nro" quiere decir la cantidad.

Una vez ejecutado el archivo, podemos ver el historial en el cual nos encontramos trabajando ejecutando el comando:

* git log --oneline

Nos mostarà el historial de todo lo que estuvimos haciendo hasta ahora comiteando, en la parte (HEAD - ramab) actualizado archivo nos indica que estamos en la cabeza, pero quiere decir que es la ultima actualizacion que se hizo en esa rama.

Ahora para cambiar a la rama principal (master) ejecutamos el siguiente comando:

* git checkout master

Para poder trabajar luego ejecutamos los siguientes pasos:

* abrimos nuetsro trabajo en VSC.
* hacemos los respectivos cambios en nuestro proyecto.
* guardamos. 

y desde la terminal ejecutamos:

* git add nombre_archivo
* git commit -m "mensaje claro y descriptivo de lo que se hizo"
* git push simepre y cuando tengamos una cuenta en github, en caso de que lo tengas aùn puedes guardar el trabajo y lo puedes subir cuando tengas una cuenta en github.


Hasta aca esta guia ràpida y sencilla de git, espero que te haya sido util.


---

## Conclusiones

Reflexiones finales, resultados o propuestas.

---

## Bibliografía

- Fuente 1
- Fuente 2
