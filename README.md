# Ejercicio Guiado

### Creo y accedo al directorio prueba_git

```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~
$ mkdir prueba_git

ivanc@DESKTOP-NCBURPK MINGW64 ~
$ cd prueba_git
```

### Mediante un editor de texto creo dos archivos dentro del directorio
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git
$ nano texto.txt
uno dos tres

ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git
$ nano script.sh

echo Listado completo
ls -l

```

## Inicializacion(init y status)
### Lo añado como nuevo repositorio local
```bash
$ git init
Initialized empty Git repository in C:/Users/ivanc/prueba_git/.git/
```

### Ver repositorio git con dos archivos untracked
```bash
$ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        script.sh
        texto.txt

nothing added to commit but untracked files present (use "git add" to track)

```

### Cambiar rama master a main
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git branch -m main

ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (main)
```

### Restaurarlo a master de nuevo
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (main)
$ git branch -m master

ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$
```

## Añadir archivos (add y commit)
### Ejecuto comando para añadirlo a archivos de rastreado
```bash
$ git add script.sh
warning: in the working copy of 'script.sh', LF will be replaced by CRLF the nex
t time Git touches it

ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   script.sh

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        texto.txt

```
### Hacemos un commit para establecer una version sicronizada del archivo
```bash
$ git commit -m "Confirmacion inicial"
[master (root-commit) ce330a1] Confirmacion inicial
 1 file changed, 3 insertions(+)
 create mode 100644 script.sh

ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        texto.txt

nothing added to commit but untracked files present (use "git add" to track)
```

### Ver lo que hay en alguno de los hash

#### Lo hice listando objetos y haciendolo con uno de ellos.
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)

$ ls .git/objects
33/  bd/  ce/  info/  pack/

ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)

$ ls .git/objects/33
420d4bf62d2ac847c49d70234274ac12a83d8f

ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)

$ git cat-file -t 33420d4bf62d2ac847c49d70234274ac12a83d8f 
tree

```

### Añado texto.txt
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git add texto.txt

warning: in the working copy of 'texto.txt', LF will be replaced by CRLF the nex
t time Git touches it

ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git commit -m "Añadido archivo texto.txt"

[master 8b251bb] Añadido archivo texto.txt
 1 file changed, 2 insertions(+)
 create mode 100644 texto.txt

ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git status

On branch master
nothing to commit, working tree clean
```
## Modifico archivos
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ nano texto.txt
uno dos tres cuatro

ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)

$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   texto.txt

no changes added to commit (use "git add" and/or "git commit -a")
```
### Preparo para el siguiente commit
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git add texto.txt
warning: in the working copy of 'texto.txt', LF will be replaced by CRLF the nex
t time Git touches it

ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   texto.txt

ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ nano texto.txt
uno dos tres cuatro cinco
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   texto.txt

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   texto.txt

```
### Hacemos el commit y confirma la version que esta en verde
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git add texto.txt

warning: in the working copy of 'texto.txt', LF will be replaced by CRLF the nex
t time Git touches it

ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git commit -m "Ampliada la explicacion del texto"

[master 8fd99cb] Ampliada la explicacion del texto
 1 file changed, 2 insertions(+)

ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git status

On branch master
nothing to commit, working tree clean
```

## Informacion (git show y git log)
### Realizar en un unico comando el add y el commit
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git commit -a -m "Nueva version"

On branch master
nothing to commit, working tree clean
```
### Ver informacion sobre la ultima version confirmada
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git show

commit 8fd99cb607db83501f77b3529c6e32bc5c055576 (HEAD -> master)
Author: jcvb23 <globexsolutions.es@gmail.com>
Date:   Wed Oct 29 22:02:00 2025 +0100

    Ampliada la explicacion del texto

diff --git a/texto.txt b/texto.txt
index c6bb304..61a8d96 100644
--- a/texto.txt
+++ b/texto.txt
@@ -1,2 +1,4 @@
 uno dos tres
+cuatro
+cinco
```
### Ver cambios realizados en forma de historico
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git log
commit 8fd99cb607db83501f77b3529c6e32bc5c055576 (HEAD -> master)
Author: jcvb23 <globexsolutions.es@gmail.com>
Date:   Wed Oct 29 22:02:00 2025 +0100

    Ampliada la explicacion del texto

commit 8b251bbf9bfb50b10b2793a605ed38c11d25afb6
Author: jcvb23 <globexsolutions.es@gmail.com>
Date:   Wed Oct 29 21:51:11 2025 +0100

    Añadido archivo texto.txt

commit ce330a10501bdc46b0511f77c90488ff27b9d526
Author: jcvb23 <globexsolutions.es@gmail.com>
Date:   Wed Oct 29 21:30:30 2025 +0100

    Confirmacion inicial

```

### Mostrar solo objetos commit indicando el hash
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git cat-file -p 33420d4bf62d2ac847c49d70234274ac12a83d8f
100644 blob bdeae59061459eb794360f01a5f316d79ba743ce    script.sh
```
## Diferencias (git diff)
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ nano texto.txt

uno
dos
cuatro
cinco
seis

$ git diff
warning: in the working copy of 'texto.txt', LF will be replaced by CRLF the nex
t time Git touches it
diff --git a/texto.txt b/texto.txt
index 61a8d96..2fe7a26 100644
--- a/texto.txt
+++ b/texto.txt
@@ -1,4 +1,6 @@
-uno dos tres
+uno
+dos
 cuatro
 cinco
+seis

```
### Informacion sobre lo añadido y eliminado
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git commit -a -m "Probando diff"
warning: in the working copy of 'texto.txt', LF will be replaced by CRLF the nex
t time Git touches it
[master 6c49160] Probando diff
 1 file changed, 3 insertions(+), 1 deletion(-)
```
### Añado linea 7 y lo ejecuto
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ nano texto.txt
uno
dos
cuatro
cinco
seis
siete
$ git diff

warning: in the working copy of 'texto.txt', LF will be replaced by CRLF the nex
t time Git touches it
diff --git a/texto.txt b/texto.txt
index 2fe7a26..26d22aa 100644
--- a/texto.txt
+++ b/texto.txt
@@ -3,4 +3,5 @@ dos
 cuatro
 cinco
 seis
+siete
```
## Ignorar archivos
### Creo el archivo .gitignore
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ nano .gitignor
*.class
*~
```
### Creo hola.java y le meto codigo
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ nano Hola.java
class Hola {
    public static void main(String[] args) {
        System.out.println("Welcome to the Java World");
    }
}
```
### Listo los archivos
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ ls -a
./  ../  .git/  .gitignore  Hola.java  script.sh  texto.txt
```
### Compilo Hola.java
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ javac Hola.java

$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   texto.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .gitignore
        Hola.java

no changes added to commit (use "git add" and/or "git commit -a")
```
### Cambiar gitignore
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ mv .gitignore .gitignore.bak

ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   texto.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .gitignore.bak
        Hola.class
        Hola.java

no changes added to commit (use "git add" and/or "git commit -a")
```
### Pongo .gitignore como antes y metemos todo lo que este pendiente y confirmamos
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git add .

warning: in the working copy of 'texto.txt', LF will be replaced by CRLF the nex
t time Git touches it
warning: in the working copy of '.gitignore', LF will be replaced by CRLF the ne
xt time Git touches it
warning: in the working copy of 'Hola.java', LF will be replaced by CRLF the nex
t time Git touches it

ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git commit -m "Añadidos fuentes en java y archivos importantes"

[master ce04c18] Añadidos fuentes en java y archivos importantes
 3 files changed, 8 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 Hola.java
```
### Ver archivos tras el ultimo commit
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git ls-tree --name-only -r HEAD
.gitignore
Hola.java
script.sh
texto.txt
```

## Tags y gestion de versiones (git tag y checkout)
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git show 8b251bbf9bfb50b10b2793a605ed38c11d25afb6
commit 8b251bbf9bfb50b10b2793a605ed38c11d25afb6
Author: jcvb23 <globexsolutions.es@gmail.com>
Date:   Wed Oct 29 21:51:11 2025 +0100

    Añadido archivo texto.txt

diff --git a/texto.txt b/texto.txt
new file mode 100644
index 0000000..c6bb304
--- /dev/null
+++ b/texto.txt
@@ -0,0 +1,2 @@
+uno dos tres
+
```
### Añadir un tag
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git tag v0.7
```
### Añadir un tag a una version anterior mostrar versiones
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git tag v0.3 8b251bbf9bfb50b10b2793a605ed38c11d25afb6

$ git log --oneline
ce04c18 (HEAD -> master, tag: v0.7) Añadidos fuentes en java y archivos importan
tes
6c49160 Probando diff
8fd99cb Ampliada la explicacion del texto
8b251bb (tag: v0.3) Añadido archivo texto.txt
ce330a1 Confirmacion inicial
```
### Ver version determinada
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git show v0.3
commit 8b251bbf9bfb50b10b2793a605ed38c11d25afb6 (tag: v0.3)
Author: jcvb23 <globexsolutions.es@gmail.com>
Date:   Wed Oct 29 21:51:11 2025 +0100

    Añadido archivo texto.txt

diff --git a/texto.txt b/texto.txt
new file mode 100644
index 0000000..c6bb304
--- /dev/null
+++ b/texto.txt
@@ -0,0 +1,2 @@
+uno dos tres
+
```
### Ver una version antigua
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git checkout v0.3
Note: switching to 'v0.3'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 8b251bb Añadido archivo texto.txt
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git ((v0.3))
```
### Volver a la version mas reciente
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git ((v0.3))
$ git checkout master
Previous HEAD position was 8b251bb Añadido archivo texto.txt
Switched to branch 'master'

ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$
```
## Ramas
### Crear una rama con el nombre Prueba
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git branch Prueba

ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git log --oneline
ce04c18 (HEAD -> master, tag: v0.7, Prueba) Añadidos fuentes en java y archivos
importantes
6c49160 Probando diff
8fd99cb Ampliada la explicacion del texto
8b251bb (tag: v0.3) Añadido archivo texto.txt
ce330a1 Confirmacion inicial
```
### Listado de ramas
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git branch
  Prueba
* master
```
### Cambiar a la rama de prueba
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git switch Prueba
Switched to branch 'Prueba'
```
### Mostrar otra vez el listado de ramas
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (Prueba)
$ git branch
* Prueba
  master

ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (Prueba)
$ git log --oneline
ce04c18 (HEAD -> Prueba, tag: v0.7, master) Añadidos fuentes en java y archivos
importantes
6c49160 Probando diff
8fd99cb Ampliada la explicacion del texto
8b251bb (tag: v0.3) Añadido archivo texto.txt
ce330a1 Confirmacion inicial
```
### Ver archivo .git/HEAD
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (Prueba)
$ git commit -a -m "Rama para pruebas de codigo"
On branch Prueba
nothing to commit, working tree clean

ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (Prueba)
$ git log --oneline
ce04c18 (HEAD -> Prueba, tag: v0.7, master) Añadidos fuentes en java y archivos
importantes
6c49160 Probando diff
8fd99cb Ampliada la explicacion del texto
8b251bb (tag: v0.3) Añadido archivo texto.txt
ce330a1 Confirmacion inicial
```
### Meto una linea de codigo a Hola.java y el commit que le corresponde
```bash
class Hola {
    public static void main(String[] args){
       System.out.println("Welcome to the Java World");
       System.out.println("I have no more branches to commit, said the Ent");
    }
}
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (Prueba)
$ git commit -a -m "Llegan los Ents a Java"
[Prueba 34b5589] Llegan los Ents a Java
 1 file changed, 2 insertions(+), 1 deletion(-)

ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (Prueba)
$ git tag v0.7-Ent-Release
```
### Hago el log para mostrar y ver
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (Prueba)
$ git log
commit 34b558921829fc29153c1942c2c20c99f25d26d5 (HEAD -> Prueba, tag: v0.7-Ent-R
elease)
Author: jcvb23 <globexsolutions.es@gmail.com>
Date:   Thu Oct 30 00:31:58 2025 +0100

    Llegan los Ents a Java

commit ce04c18db82a56e46008dcf526384f83c73073c9 (tag: v0.7, master)
Author: jcvb23 <globexsolutions.es@gmail.com>
Date:   Wed Oct 29 22:44:53 2025 +0100

    Añadidos fuentes en java y archivos importantes

commit 6c491600596d7caa7d79b4893c8a3212deb912f0
Author: jcvb23 <globexsolutions.es@gmail.com>
Date:   Wed Oct 29 22:26:07 2025 +0100

    Probando diff

commit 8fd99cb607db83501f77b3529c6e32bc5c055576
Author: jcvb23 <globexsolutions.es@gmail.com>
Date:   Wed Oct 29 22:02:00 2025 +0100
:
```
### Vuevlo a la rama principal y mostramos que no cambia el Hola.java por que lo hicimos en la rama
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (Prueba)
$ git switch master
Switched to branch 'master'

ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ cat Hola.java
class Hola {
    public static void main(String[] args){
        System.out.println("Welcome to the Java World");
    }
}
```
### Juntar con la rama principal
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git merge Prueba
Updating ce04c18..34b5589
Fast-forward
 Hola.java | 3 ++-
 1 file changed, 2 insertions(+), 1 deletion(-)

```
## Eliminar y quitar de seguimiento
###   Eliminar archivo 
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git rm -f borrar.txt
rm 'borrar.txt'

ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git commit -m "Eliminado borrar.txt"
On branch master
nothing to commit, working tree clean
```
### Quitar archivos de seguimiento
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git reset HEAD *.class
```
## Repositorios remotos
### Clonar un proyecto
```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git clone https://github.com/Ivxn15/prueba_git.git
Cloning into 'prueba_git'...
warning: You appear to have cloned an empty repository.

ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git clone https://github.com/Ivxn15/MiPrueba
Cloning into 'MiPrueba'...
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 4 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Receiving objects: 100% (4/4), done.

```
### Mandar cambios al repositorio remoto

```bash
ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git remote add origin https://github.com/Ivxn15/MiPrueba.git

ivanc@DESKTOP-NCBURPK MINGW64 ~/prueba_git (master)
$ git push -u origin master
info: please complete authentication in your browser...
Enumerating objects: 20, done.
Counting objects: 100% (20/20), done.
Delta compression using up to 6 threads
Compressing objects: 100% (13/13), done.
Writing objects: 100% (20/20), 1.85 KiB | 630.00 KiB/s, done.
Total 20 (delta 2), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (2/2), done.
remote:
remote: Create a pull request for 'master' on GitHub by visiting:
remote:      https://github.com/Ivxn15/MiPrueba/pull/new/master
remote:
To https://github.com/Ivxn15/MiPrueba.git
 * [new branch]      master -> master
branch 'master' set up to track 'origin/master'.


```

