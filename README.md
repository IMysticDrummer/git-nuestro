# git-nuestro
Práctica de GIT usando modificaciones sobre el "git-nuestro"

**Nota:** la rama principal del repositorio es *main*. Por tanto, toda referencia del ejercicio a la rama *master*, en repositorio es *main*.

## Ejercicio 1

**Paso 11**
> Utilizado el comando `git reset --hard HEAD~1`. Esto nos lleva al commit anterior, sustituyendo todo el contenido del working copy

**Paso 12**
> Primero utilizamos `git reflog` para ver el histórico de movimientos.
> Localizado el commit en el que hemos estilizado el archivo, copiamos el identificador (en mi caso c8f2124).
> Una vez con el identificador, hacemos un `git reset --hard c8f2124`.
> > En mi caso he optado por --hard para recuperar todo el trabajo realizado.
> Con esto hemos re-accedido al commit con el trabajo que habíamos *"perdido"*.

**Paso 13**
> No se producen conflictos. De hecho, git nos devuelve *Already up to date*. Es lógico, ya que en el grafo, la rama **styled** ya tiene en su histórico el puntero a **main**.

**Paso 19**
> Se produce un conflicto.
> Esto es lógico puesto que hemos modificado *git-nuestro.md* en una rama diferente de **styled**, y por tanto *git* nos deja a nosotros el trabajo de decidir qué cambios deben quedarse.

**Paso 21**
> No se producen conflictos.
> **main** está apuntando a un commit *antepasado* de **styled**.
> Si dibujamos el grafo, vemos que los commits entre el puntero **main** y **styled** forman una *lista*.
> Por ello *git* sólo necesita hacer un merge de tipo *fast-foward*, sin ningún tipo de conflicto, para unir las dos ramas en la principal **main**.

**Paso 25**
> Para dibujar el diagrama he utilizado `git log --graph --decorate`.
> En mi caso concreto he configurado un alias llamado *graph*, para llamar al comando anterior de “un solo golpe de teclado”.
>> `git config --global alias.graph "log --graph --decorate”`.
> Podría haber utilizado también la info en una línea con `--pretty=oneline`, pero la verdad es que no me molesta tener más información.

**Paso 26**
> Sí, podría hacerse un merge fast-forward.
> Hemos creado una rama **title**, dónde hemos modificado *git-nuestro.md*. Pero en la rama **main** el archivo no ha sido modificado, por lo que **title** en realidad está situado un “punto” del grafo por encima de **main**. Podemos hacer un merge *fast-forward*, sin conflictos, y evitamos generar un commit de unión a mayores.

**Paso 27**
> Utilizo `git reset HEAD^1` para volver al punto anterior del grafo, por la rama **title**.

**Paso 28**
> Utilizo `git restore git-nuestro.md` para descartar los cambios del *staying área*.

**Paso 29**
> Para eliminar la rama **title**, primero me aseguro que no estoy en ella:
>> `git branch`.
> Me dice que estoy en **main**. Desde ahí elimino la rama **title**:
>> `git branch -D title`.

**Paso 30**
> Primero utilizo `git reflog` para localizar el identificador del commit en el que hicimos el merge entre **main** y **title**. En mi caso es 4fa6292.
> Luego utilizo `git reset 4fa6292` para volver al punto en el que teníamos hecho el merge.
> Restauro el archivo *git-nuestro.md* con los cambios del título utilizando restore:
>>`git restore git-nuestro.md`.
>*Esto se podía haber hecho también con un `git reset --hard`. Lo decidí hacer así, para asegurar los pasos y cambios*.

**Paso 32**
> Utilizo `git log` para localizar el primer commit (inicial). En mi caso 81b74115285dd37881f5dfc21b80d67baa177ee1.
> Utilizo `git reset 81b74115285dd37881f5dfc21b80d67baa177ee1` ya que nos están pidiendo volver al commit inicial.

**Paso 33**
> Utilizo `git reflog` para localizar el commit final. En mi caso 4fa6292.
> Utilizo `git reset 4fa6292` para volver a colocarnos en el commit final.
