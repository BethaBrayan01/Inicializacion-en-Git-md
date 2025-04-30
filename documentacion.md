# GUIA RAPIDO Y SENCILLA PARA USAR GIT


---

![Mi imagen](imagenes/git.png)


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
    - esta configuracion es para que la terminal se quede eseperando hasta que cerremos nuestro editor (en este caso VSC). 
* git config -- global e
    - esta configuracion nos mostrarà (si todo esta bien) nuestro archivo de configuracion global se abrirà dentro de VSC
    

---

## Conclusiones

Reflexiones finales, resultados o propuestas.

---

## Bibliografía

- Fuente 1
- Fuente 2
