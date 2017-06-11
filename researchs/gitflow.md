# Flujo de trabajo con git-flow

## Metodología
La forma en la que vamos a trabajar se va a basar en la metodología git-flow. Para esta metodología, vamos a disponer permanentemente de dos ramas:

- master: rama donde vamos a tener las versiones estables del producto, que serán las que liberemos. Siempre se va a aconsejar el uso de la última versión de esta rama a los usuarios. Esta rama tendrá su tag para indicar el número de versión al que corresponda.

- develop: rama donde se van a hacer o mergear los desarrollos, así como donde se van a corregir los bugs que vayan saliendo en el producto.

Además de estas dos ramas, también tendremos ramas temporales para el desarrollo de las features así como la solución de hotfix que se tengan que liberar antes de sacar una versión oficial.

- feature/nombre_rama_feature: se va a crear una rama por cada feature que se lleve a cabo. Esta saldrá de la rama develop y, cuando se termine el desarrollo, se va a mergear con la rama develop también.

- hotfix/nombre_rama_hotfix: se crea a partir de la rama master. Se va a solucionar el bug que se encuentre en la rama estable (master) y que es necesario que salga ya en la versión estable del producto. Una vez hecho el arreglo se va a mergear a la rama master y a la rama develop, para tenerlo en futuras versiones.

- issue_numeroIssue: su funcionamiento será el mismo que el de la rama hotfix salvo que el desarrollo se realiza debido a algún issue que se haya abierto en el repositorio contra la versión master y es necesario liberar en master sin esperar a la siguiente versión.

Realmente, la única diferencia que habrá entre estas ramas es el origen de las mismas. Para los desarrollos de las features se sacará la rama desde develop mientras que para los bugs e issues que sean necesarios liberar antes de generar una nueva versión se sacará de la rama master.

Cada vez que se quiera liberar una nueva versión estable del producto se hará un merge a master desde la rama develop, para tener los nuevos desarrollos disponibles. Además, se creará el tag que corresponda. Con estos dos pasos ya tendríamos una versión estable en master lista para que los usuarios la puedan usar.

## Ejemplo de uso
Ahora, se va a explicar cual podría ser el flujo de trabajo para la siguiente situación: tenemos una versión estable en master (v_1.0). A su vez, tenemos que llevar a cabo dos desarrollos independientes. Además, nos vamos a dar cuenta que tenemos un bug reconocido (bug1), y nos han abierto una issue (issue_1). En el caso de la issue, será necesario que salga en la versión liberada en cuanto esté solucionado.

1. Desde la rama develop vamos a crear dos ramas de feature (feature/f1 y feature/f2).
2. En cada una de las ramas de feature se van a desarrollar las funcionalidades solicitadas.
3. Cuando nos damos cuenta de que tenemos el bug1 en producción, pero este bug no es necesario liberarlo en la versión estable, lo que hacemos es solucionar el bug en la rama develop. En caso de que el bug sea lo suficientemente complejo como para tener que desarrollarlo a parte de la rama develop, nos vamos a poder crear una rama feature/solucion_bug1 donde se solucionaría el bug y, posteriormente, se hará un merge a la rama develop.
4. En el momento en el que nos abren la issue_1 lo que haremos será sacar una rama de issue desde master (issue_1). Tras solucionar este problema haremos un merge de la solución tanto en máster como en develop, para así tener la solución tanto en la rama estable como en la rama de develop. Crearemos un tag en máster con la nueva versión de la herramienta.
5. A medida que vayamos terminando de desarrollar cada feature iremos haciendo un merge a la rama develop con todos los cambios.
6. Una vez que ya se han terminado todas las features y se han hecho todos los merges a develop vamos a proceder a hacer el merge a la rama master y crear el tag de version, para así tener disponible nuestra nueva versión estable de la herramienta liberada.

## Descarga de git-flow
Para poder tener acceso a git flow desde la consola de comandos de windows será necesario realizar los siguientes pasos:
1. Descargar los binarios de: [http://gnuwin32.sourceforge.net/packages/util-linux-ng.htm](http://gnuwin32.sourceforge.net/packages/util-linux-ng.htm)
2. Descomprimir el fichero descargado.
3. Copiar getopt.exe en la ruta "C:\Program Files (x86)\Git\bin"
4. Clonar el repositorio de git-flow donde quieras: git clone –recursive https://github.com/nvie/gitflow.git
5. Ir al repositorio clonado y en "cd contrib/" ejecutar: 
    "msysgit-install.cmd "C:\Program Files (x86)\Git"
6. Ya está instalado. Si ejecutas "git flow" en una consola ya te lo reconoce.

_Fuente:_ [http://aprendegit.com/instalacion-de-git-flow/](http://aprendegit.com/instalacion-de-git-flow/)

## Comandos de creación y finalización de features y hotfixes
Algunos comandos para la creación y finalización de features y hotfixes:
- Features:
    - git flow feature start nombre_de_feature: Al iniciar una funcionalidad. Nos crear la rama y nos pone en ella.
    - git flow feature finish nombre_de_feature: Ya hemos hecho todos los commit en la feature y hemos terminado el desarrollo. Con este comando nos fusiona la rama con develop, borra la rama y cambiamos a develop.
    - git flow feature checkout nombre_de_feature: Volver a la rama de una feature para seguir desarrollando en ella.
- HotFix:
    - git flow hotfix start nombre_hotfix: Se crea la rama a partir de master para comenzar a desarrollar el hotfix.
    - git flow hotfix finish nombre_hotfix: Se ha terminado de solucionar el error. Esto fusiona los cambios tanto a develop como a master.

