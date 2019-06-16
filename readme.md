- ¿Qué comando utilizaste en el paso 11? ¿Por qué?
He utilizado el siguiente comando:
git reset --hard HEAD~1

Se puede hacer de varias formas, por ejemplo con reflog y capturando el hash, pero esta es mas sencilla en este caso ya que sabemos que solo queremos volver atrás 1 commit, por eso ponemos la virgulilla 1 (~1). En el comando git reset hay que usar –hard para que perdamos los cambios en el working copy, si no lo ponemos únicamente retrocedemos el commit pero sin perder cambios. En ambos casos el staging se queda vacio.

- ¿Qué comando o comandos utilizaste en el paso 12? ¿Por qué?

Hay que hacer un comando:  git reflog para buscar el hash que nos interesa.
Despues capturamos el hash inmediatamente anterior al ultimo commit (el que deshacía los cambios en el working copy anterior), en mi caso  este hash: f0bcdd6
Por ultimo hacer un  git reset --hard f0bcdd6 (con el git reset normal no veriamos el working copy correctamente, tan solo nos moveríamos pero no veriamos los cambios tal y como estaban antes de deshacer el commit)
Este comando nos posiciona en el commit que queremos antes de perder los cambios realizados, y por lo tanto rehaciendo el ultimo commit al completo.


- El merge del paso 13, ¿Causó algún conflicto? ¿Por qué? 

No causa conflicto por que el primer commit si que se encuentra en la rama styled ya que se hizo en el paso 4. Aparte de eso también al haber rehecho el ultimo commit, volvimos a dejarlo todo como estaba en el paso 10.

- El merge del paso 19, ¿Causó algún conflicto? ¿Por qué? 
Si causa conflicto.
Es causado ya que se han modificado mismas líneas en 2 ramas diferentes. Al intentar merge salta el aviso para que selecciones que líneas quieres quedarte puesto que hay difenrencias entre ambas.

- El merge del paso 21, ¿Causó algún conflicto? ¿Por qué? 
No causa conflicto ya que realmente no hay cambios puesto que en el merge anterior nos quedábamos con el contenido de Styled, rama que además había absorbido el contenido de máster en el merge del paso 13.


- ¿Qué comando o comandos utilizaste en el paso 25?
git log --graph –decorate
Tambien podia haber usado este: git log --graph --decorate --oneline
Para que muestre todo en una línea. 
- El merge del paso 26, ¿Podría ser fast forward? ¿Por qué?
Si podía ser un merge fast forward sin problema, ya que entre medias en la rama master no se ha realizado ningún cambio (no se han realizado otros commits). En el merge únicamente pretendemos que la rama master tenga el titulo que hemos puesto en la rama title.

 - ¿Qué comando o comandos utilizaste en el paso 27? 
Se puede hacer de varias formas. Yo he usado git reflog y he sacado el hash para después aplicar “git reset” seguido del hash.
git reset 56d9551

- ¿Qué comando o comandos utilizaste en el paso 28? 
Para descartar los cambios también se usa el checkout (aparte de para cambiar de rama). Git checkout seguido de -- y el nombre del fichero, hace que se descarten.
git checkout -- git-nuestro.md
- ¿Qué comando o comandos utilizaste en el paso 29?
git branch -D title
*Ojo por que si ponemos la D en minúscula, te pide que la pongas en mayúscula para confirmar realmente. Es una forma de evitar errores…
 - ¿Qué comando o comandos utilizaste en el paso 30? 
Lo primero de todo es sacar el hash con git reflog.
Hay que buscar y copiar el hash del merge y después hacer un reset -- hard para poder rehacer el merge y por lo tanto que los cambios del titulo sigan aplicados.
git reflog
git reset --hard 92b583c

- ¿Qué comando o comandos usaste en el paso 32? 
Buscando el hash con git reflog he copiado el hash del primer commit  y he usado
git reset 313b0dd

- ¿Qué comando o comandos usaste en el punto 33? 
Buscando el hash con git reflog he copiado el hash del commit del merge que en el que master absorvia a title. (en ese merge tenia titulo el poema).
git reset 92b583c
