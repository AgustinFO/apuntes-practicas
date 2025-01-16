# GIT

## Indice

1. [Qué es git?](#qué-es-git)
2. [Qué es github?](#qué-es-github)
3. [Conceptos básicos](#conceptos-basicos)

## Qué es Git? 

Es un dVCS que nos permite rastrear los cambios que hemos hecho en un conjunto de archivos.

Merge: Fusión de ramas para actualizar los cambios que realizamos en la rama principal.

## Qué es Github?

Servicio de hosting que nos permite almacenar proyectos de desarrollo de SW y de VCS usando git.

## Conceptos básicos

- **VCS**: Sistema que administra cambios que se realizan en distintos archivos.

- **Repositorio**: Colección de archivos de distintas versiones de un proyecto. 
    - Puede ser local o remoto.

- **Commit**: Componentes basicos de la línea del tiempo de un proyecto de git. Son como un registro o "foto" del estado de un proyecto en un momento específico.

- **Git Bash**: Herramienta que te permite ejecutar comandos de Git. Es una linea de comandos.

## Comandos en Git

### cd

- Permite cambiar el directorio en el cual nos encontramos.
- Si el nombre del directorio al cual nos queremos dirigir tiene espacios debemos ponerlo entre " ".

    `cd "Curso de Github"`

- El comando `cd ..` nos permite volver a subir en el sistema de archivos.
- Si solo se ejecuta el comando `cd` se vuelve al directorio base o principal.

### mkdir

- Crea una carpeta nueva dentro de la dirección en la que nos encontramos.

### ls

- Permite ver todo el contenido de un directorio.
- Las carpetas terminan con /.

### rmdir

- Permite eliminar un directorio.

    `rmdir <dir>`

### clear

- Limpia la consola.

### git init

- Inicia un nuevo repositorio en el directorio actual.

### git status

- Chequea el estado de los commit.

### git add

- Agrega el archivo al area de stage.
- Para agregar un archivo específico se usa `git add <file>`
- Si queremos agregar todos los cambios que se indican podemos usar `git add .`

### git rm --cached

- Remueve el archivo del area de stage.

### git commit

- Realiza el commit de los archivos presentes en el area de stage.
- Se puede usar `git commit -m "descripción"` para incluirlo en la misma linea de prompt.
- Para agregar la descripción del commit en un editor de texto usar `git commit`, esto abrirá el editor de texto que utiliza Git por defecto.
- Para modificar el mensaje del commit se puede usar `git commit --amend`.
    - ***En caso de usarlo, se debe usar en el repositorio local, no realizar en el remoto.***

### git log

- Muestra el historial de commits realizados.
- Se puede utilizar el comando `git log --oneline` para visualizarlo en una sola linea.
- Tambien se puede utilizar el comando `git log -p` para visualizar las modificaciones realizadas.

### git reset

- Deshace los cambios realizados en los commit.
- Por ejemplo, tenemos `git reset --soft HEAD~1`
    - `--soft`nos indica que los archivos no van a ser eliminados del working directory. Caso contrario se usa `--hard`.
    - `HEAD~1`indica que queremos revertir los cambios realizados en el último commit.

### git branch

- Muestra las branchs que tenemos creadas.
- Para crear una nueva branch se usa `git branch <name>`
- Para modificar el nombre de una rama se puede utilizar:
    - `git branch -m <name>` si nos encontramos en la rama a modificar.
    - `git branch -m <actual-name> <new-name>` si no nos encontramos en la rama a modificar.
- Para eliminar una branch se utiliza `git branch -d <name>`.
    - Esto aplica a branches locales.
    - No se debe estar en la rama que se elimina al momento de ejecutar el comando.

### git checkout

- Switchea a la branch que deseemos utilizando `git checkout <name>`
- Se puede crear y switchear a una branch utilizando `git checkout -b <name>`

### git merge

- Realiza un merge de 2 branches.
- Utilizamos `git merge <branch-name>`.
- Se debe estar situado en la branch que recibirá la fusión.



## Crear un nombre de usuario y email en git.

- Es el nombre de usuario y email que aparecerá cuando se realicen los commit.
- Para ello utilizamos los comandos `git config --global user.name "nombre"`y   
 `git config --global user.email "email"`.

## Crear un repositorio
~~~
agustin@Agustin-PC:~$ cd Documents
agustin@Agustin-PC:~/Documents$ cd Git
agustin@Agustin-PC:~/Documents/Git$ mkdir curso-git
agustin@Agustin-PC:~/Documents/Git$ cd curso-git
agustin@Agustin-PC:~/Documents/Git/curso-git$ git init
Initialized empty Git repository in /home/agustin/Documents/Git/curso-git/.git/

~~~

## Borrar un repositorio

- Simplemente hay que eliminar la carpeta .git

## Areas de Git

### Directorio de trabajo (Working Directory)

- La carpeta del proyecto que contiene los archivos y el directorio .git del repositorio.
- Cuando una versión se encuentra en el directorio de trabajo, decimos que esa versión se encuentra **modificada** (modified).

### Area de preparación (Staging area)

- Conjunto de archivos y cambios que serán incluidos en el próximo commit.
- Cuando una versión se encuentra en el área de preparación, decimos que esa versión se encuentra **preparada** (staged).

### Repositorio (Directorio .git)

- Directorio que contiene los metadatos y las versiones de un proyecto.
- Es la parte del repositorio que se copia cuando clonas un repositorio a tu computadora.
- Es la parte mas importante de Git.
- Cuando una versión se encuentra en el repositorio decimos que esa versión se encuentra **confirmada** (commited).

## Estado de los archivos

- Modificada: Si la versión del archivo contiene cambios que no son parte del repositorio y no se ha añadido al área de preparación.

- Preparada: Si la versión del archivo contiene cambios que no son parte del repositorio pero fue añadida al área de preparación.

- Confirmada: Si la versión ya se encuentra en el directorio de Git.

## Commit

- Todos los [commit](#conceptos-básicos) deben incluir un mensaje descriptivo, en el cual se indican los cambios realizados.

    ~~~
    agustin@Agustin-PC:~/Documents/Git/curso-git$ git commit -m "Agregar archivo de texto"
    [main (root-commit) 462e965] Agregar archivo de texto
    1 file changed, 1 insertion(+)
    create mode 100644 mi-archivo.txt
    ~~~


### SHA o Hash

- Cada commit tiene un identificador unico, con una referencia, que es el SHA (Secure Hash Algorithm), lo que nos permite trackear dicho commit.
- SHA identifica:
    - Los cambios realizados.
    - Fecha en que se realizaron los cambios.
    - Dónde se realizaron los cambios.
    - Quién realizó los cambios.


### log

- El log nos va a indiciar la lista de commits realizados, con toda la información que incluye el mismo.

    ~~~
    agustin@Agustin-PC:~/Documents/Git/curso-git$ git log
    commit 462e965c0b870df3345dc5435f6439c1cb762167 (HEAD -> main)
    Author: AgustinFO <AgustinFO@users.noreply.github.com>
    Date:   Tue Jan 14 16:56:18 2025 -0300

        Agregar archivo de texto
    ~~~

### Modificar texto de un commit

- Para esto se utiliza --amend, tal cual se detalla en [comandos commit](#git-commit).

### Deshacer el último commit

- para esto se utiliza git rest, tal cual se detalla en [comandos commit](#git-reset).


## Branches en Git

- Un branch es una línea independiente de desarrollo en el repositorio.
- Esto nos permite trabajar sobre otras versiones de un proyecto, sin afectar al repositorio main (que está live).
- Aplicar los cambios a futuro requiere una coordinación del equipo de desarrollo, ya que estos deben ser compatibles.

### Crear una branch

- Se utiliza el comando [git branch](#git-branch).

### Cambiar el nombre de una branch

- Se utiliza el comando [git branch](#git-branch).

### Eliminar una rama

- Se utiliza el comando [git branch](#git-branch).

### Crear un commit en una branch alternativa

- Cambiamos a la branch en la que queremos trabajar.
- Añadimos el archivo al staged area.
- Creamos el commit.

### Git log para branches

- Se utiliza el comando [git log](#git-log).


### Fusionar branches

- Es un proceso que permite combinar varias lineas independientes de desarrollo en una sola rama.
- Para fusionar dos ramas debes estar en la rama que recibirá la fusión.
- Se utiliza el comando [git merge](#git-merge).

- Por ejemplo:

    ~~~
    agustin@Agustin-PC:~/Documents/Git/curso-git$ git branch
    * main
    texto-expandido
    version-js
    agustin@Agustin-PC:~/Documents/Git/curso-git$ git merge texto-expandido
    Updating 08693d2..7f61a1e
    Fast-forward
    mi-archivo.txt | 3 ++-
    1 file changed, 2 insertions(+), 1 deletion(-)
    ~~~

### Conflictos al fusionar branches

- Ocurren cuando tratas de combinar archivos que están en conflicto. Cambios que Git considera como incompatibles.
