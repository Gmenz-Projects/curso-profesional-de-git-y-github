<div align="center">
  <h1>Curso Profesional de Git y GitHub</h1>
</div>


# Introducción al documento

El contenido de este documento esta basado en el curso del mismo nombre dictado por [Freddy Vega](https://github.com/freddier) en [Platzi](https://platzi.com/fergimenezzz/).

# Tabla de contenido
- [Comandos básicos en Git](#Comandos-básicos-en-Git)
  - [¿Qué es el staging y los repositorios? Ciclo básico de trabajo en Git](#¿Qué-es-el-staging-y-los-repositorios?-Ciclo-básico-de-trabajo-en-Git)
  - [¿Qué es un Branch y cómo funciona un Merge en Git?](#¿Qué-es-un-Branch-y-cómo-funciona-un-Merge-en-Git?)


  
  - [Crea un repositorio de Git y haz tu primer commit](#Crea-un-repositorio-de-Git-y-haz-tu-primer-commit)
  - [Analizar cambios en los archivos de tu proyecto con Git](#Analizar-cambios-en-los-archivos-de-tu-proyecto-con-Git)
  - [Git reset vs. Git rm](#Git-reset-vs.-Git-rm)
  - [Volver en el tiempo en nuestro repositorio utilizando reset y checkout](#Volver-en-el-tiempo-en-nuestro-repositorio-utilizando-reset-y-checkout)
  
- [Flujo de trabajo básico en Git](#Flujo-de-trabajo-básico-en-Git)
  - [Flujo de trabajo básico con un repositorio remoto](#Flujo-de-trabajo-básico-con-un-repositorio-remoto)
  - [Introducción a las ramas o branches de Git](#Introducción-a-las-ramas-o-branches-de-Git)
  - [Fusión de ramas con Git merge](#Fusión-de-ramas-con-Git-merge)
  - [Resolución de conflictos al hacer un merge](#Resolución-de-conflictos-al-hacer-un-merge)
  
- [Trabajando con repositorios remotos en GitHub](#Trabajando-con-repositorios-remotos-en-GitHub)
  - [Uso de GitHub](#Uso-de-GitHub)
  - [Cómo funcionan las llaves públicas y privadas](#Cómo-funcionan-las-llaves-públicas-y-privadas)
  - [Configura tus llaves SSH en local](#Configura-tus-llaves-SSH-en-local)
  - [Conexión a GitHub con SSH](#Conexión-a-GitHub-con-SSH)
  - [Tags y versiones en Git y GitHub](#Tags-y-versiones-en-Git-y-GitHub)
  - [Manejo de ramas en GitHub](#Manejo-de-ramas-en-GitHub)
  - [Configurar múltiples colaboradores en un repositorio de GitHub](#Configurar-múltiples-colaboradores-en-un-repositorio-de-GitHub)
  
- [Flujos de trabajo profesionales](#Flujos-de-trabajo-profesionales)
  - [Flujo de trabajo profesional.Haciendo merge de ramas de desarrollo a master](#Flujo-de-trabajo-profesional.Haciendo-merge-de-ramas-de-desarrollo-a-master)
  - [Flujo de trabajo profesional con Pull requests](#Flujo-de-trabajo-profesional-con-Pull-requests)
  - [Utilizando Pull Requests en GitHub](#Utilizando-Pull-Requests-en-GitHub)
  - [Creando un Fork, contribuyendo a un repositorio](#Creando-un-Fork,-contribuyendo-a-un-repositorio)
  - [Haciendo deployment a un servidor](#Haciendo-deployment-a-un-servidor)
  - [Hazme un pull request](#Hazme-un-pull-request)
  - [Ignorar archivos en el repositorio con .gitignore](#Ignorar-archivos-en-el-repositorio-con-.gitignore)
  - [Readme.md es una excelente práctica](#Readme.md-es-una-excelente-práctica)
  - [Tu sitio web público con GitHub Pages](#Tu-sitio-web-público-con-GitHub-Pages)
  
- [Multiples entornos de trabajo en Git](#Multiples-entornos-de-trabajo-en-Git)
  - [Git Rebase: reorganizando el trabajo realizado](#Git-Rebase:-reorganizando-el-trabajo-realizado)
  - [Git Stash: Guardar cambios en memoria y recuperarlos después ESTO ES IMPORTANTE LO VAMOS A USAR](#Git-Stash:-Guardar-cambios-en-memoria-y-recuperar-los-después-ESTO-ES-IMPORTANTE-LO-VAMOS-A-USAR)
  - [Git Clean: limpiar tu proyecto de archivos no deseados](#Git-Clean:-limpiar-tu-proyecto-de-archivos-no-deseados)
  - [Git cherry-pick: traer commits viejos al head de un branch](#Git-cherry-pick:-traer-commits-viejos-al-head-de-un-branch)
- [Comandos de Git para casos de emergencia](#Comandos-de-Git-para-casos-de-emergencia)
  - [Reconstruir commits en Git con amend](#Reconstruir-commits-en-Git-con-amend)
  - [Git Reset y Reflog: úsese en caso de emergencia](#Git-Reset-y-Reflog:-úsese-en-caso-de-emergencia)
  - [Buscar en archivos y commits de Git con Grep y log](#Buscar-en-archivos-y-commits-de-Git-con-Grep-y-log)
- [Comandos y recursos colaborativos en Git y GitHub](#Comandos-y-recursos-colaborativos-en-Git-y-GitHub)

# Comandos básicos en Git
## ¿Qué es el staging y los repositorios? Ciclo básico de trabajo en Git
Para iniciar un repositorio, o sea, activar el sistema de control de versiones de Git en tu proyecto, solo debes ejecutar el comando
`git init`. 

Este comando se encargará de dos cosas: primero, crear una carpeta .git, donde se guardará toda la base de datos con cambios atómicos de nuestro proyecto; y segundo, crear un área que conocemos como Staging, que guardará temporalmente nuestros archivos (cuando ejecutemos un comando especial para eso) y nos permitirá, más adelante, guardar estos cambios en el repositorio (también con un comando especial). 

Staging: Es donde se guardan las modificaciones del archivo antes de enviar la versión final al repositorio (staging es como tener la milanesa empanizada pero no freída). 

 
Repositorio: Es la carpeta < /.git/ > donde se guardan las versiones finales de los archivos, todos los que trabajen en el mismo proyecto tienen acceso a esta carpeta y pueden ver qué se ha modificado de un archivo y quién lo realizó. 

 

Ciclo de vida o estados de los archivos en Git: 

Cuando trabajamos con Git nuestros archivos pueden vivir y moverse entre 4 diferentes estados (cuando trabajamos con repositorios remotos pueden ser más estados, pero lo estudiaremos más adelante): 

Archivos Tracked: son los archivos que viven dentro de Git, no tienen cambios pendientes y sus últimas actualizaciones han sido guardadas en el repositorio gracias a los comandos git add y git commit. 

Archivos Staged: son archivos en Staging. Viven dentro de Git y hay registro de ellos porque han sido afectados por el comando git add, aunque no sus últimos cambios. Git ya sabe de la existencia de estos últimos cambios, pero todavía no han sido guardados definitivamente en el repositorio porque falta ejecutar el comando git commit. 

Archivos Unstaged: entiéndelos como archivos “Tracked pero Unstaged”. Son archivos que viven dentro de Git pero no han sido afectados por el comando git add ni mucho menos por git commit. Git tiene un registro de estos archivos, pero está desactualizado, sus últimas versiones solo están guardadas en el disco duro. 

Archivos Untracked: son archivos que NO viven dentro de Git, solo en el disco duro. Nunca han sido afectados por git add, así que Git no tiene registros de su existencia. 
Recuerda que hay un caso muy raro donde los archivos tienen dos estados al mismo tiempo: staged y untracked. Esto pasa cuando guardas los cambios de un archivo en el área de Staging (con el comando git add), pero antes de hacer commit para guardar los cambios en el repositorio haces nuevos cambios que todavía no han sido guardados en el área de Staging (en realidad, todo sigue funcionando igual pero es un poco divertido). 

 

Comandos para mover archivos entre los estados de Git: 

`git status`: Nos permite ver el estado de todos nuestros archivos y carpetas. 

`git add`: Nos ayuda a mover archivos del Untracked o Unstaged al estado Staged. Podemos usar git nombre-del-archivo-o-carpeta para añadir archivos y carpetas individuales o git add -A para mover todos los archivos de nuestro proyecto (tanto Untrackeds como unstageds). 

`git reset HEAD`Nos ayuda a sacar archivos del estado Staged para devolverlos a su estado anterior. Si los archivos venían de Unstaged, vuelven allí. Y lo mismo se venían de Untracked. 

 

`git mkdir` Crea un directorio. 

`git touch`Crea un archivo. 

`git init` Define la carpeta del proyecto, crea el staging y el repositorio. 

`git add <nombre_del_archivo>` Guarda la versión del archivo en staging(en la memoria RAM 

`git commit -m" <mensaje>”`Se escribe un comentario sobre las modificaciones para hacer que tus compañeros y tu comprendan posteriormente cuáles fueron los cambios).

-version1 

-version 2 


`git rm`Este comando necesita alguno de los siguientes argumentos para poder ejecutarse correctamente:  
`git rm --cached` Cambia el estado de los archivos a untracked. 
`git rm --force` Elimina los archivos tanto en el disco duro como en el flujo de Git, aunque queda registro de ese archivo por si se necesita recuperarlo 

`git checkout` En caso de tener una versión desactualizada de un archivo que está en el repositorio, este comando trae los cambios necesarios al disco duro.(tramos todos los cambios o los que queremos) 


##  ¿Qué es un Branch y cómo funciona un Merge en Git?
Las ramas es romper en pedacitos en diferentes lineas de tiempo nuestro código para que varias personas puedan trabajar en el, para luego volver a unirlas al final  

Git es una base de datos muy precisa con todos los cambios y crecimiento que ha tenido nuestro proyecto. Los commits son la única forma de tener un registro de los cambios. Pero las ramas amplifican mucho más el potencial de Git. 

Todos los commits se aplican sobre una rama. Por defecto, siempre empezamos en la rama master (pero puedes cambiarle el nombre si no te gusta) y creamos nuevas ramas, a partir de esta, para crear flujos de trabajo independientes. 

Crear una nueva rama se trata de copiar un commit (de cualquier rama), pasarlo a otro lado (a otra rama) y continuar el trabajo de una parte específica de nuestro proyecto sin afectar el flujo de trabajo principal (que continúa en la rama master o la rama principal). 

Los equipos de desarrollo tienen un estándar: Todo lo que esté en la rama master va a producción, las nuevas features, características y experimentos van en una rama “development” (para unirse a master cuando estén definitivamente listas) y los issues o errores se solucionan en una rama “hotfix” para unirse a master tan pronto como sea posible. 

Crear una nueva rama lo conocemos como Checkout. Unir dos ramas lo conocemos como Merge. 

Podemos crear todas las ramas y commits que queramos. De hecho, podemos aprovechar el registro de cambios de Git para crear ramas, traer versiones viejas del código, arreglarlas y combinarlas de nuevo para mejorar el proyecto. 

Solo ten en cuenta que combinar estas ramas (sí, hacer “merge”) puede generar conflictos. Algunos archivos pueden ser diferentes en ambas ramas. Git es muy inteligente y puede intentar unir estos cambios automáticamente, pero no siempre funciona. En algunos casos, somos nosotros los que debemos resolver estos conflictos “a mano”. 

 

Es muy importante tener un manejo ordenado de nuestro repositorio y para esto existe algo que se llama GitFlow. 

GitFlow es una una guía que nos da cierto estándares para manejar la ramificación de nuestros proyectos, es decir, que ramas debemos tener, cuándo y de dónde debemos crear nuevas ramas, cómo debemos nombrar dichas ramas y muchos otros conceptos que nos ayudaran a manejar mucho mejor nuestro repositorio; siendo esto muy importante cuando trabajamos en conjunto con varios desarrolladores. 

El flujo de Gitflow es así: 

En la rama master tendremos solo lo que se ha liberado. 

1.- Se crea la rama develop, es la rama en la que estamos trabajando (lo que vamos a liberar). 

2.- Liberar a producción con tu equipo de trabajo se crea una release desde develop. 

No se pasa directo de develop a master, Git Flow crea la nueva rama de release. 

3.- Por cada petición o tarea se genera una rama llamada feature a partir de develop. 

4.- Por ejemplo una pantalla nueva, se crea y está completa el feature de pantalla se cierra y se afusiona con develop. 

5.- Cuando tienes la rama release terminada, fusionas con develop y master. 

6.- Si hay problema en master se crea hotfix que son los cambios sobre algo que está en producción. 

7.- Se crea una nueva rama se trabaja y se reintegra. Una vez que hotfix se completa, se fusiona a ambos develop y master. 

   FOTOOOO
   
   V4 encontramos un bug,hacemos un hotfix. Y luego enviamos h2(hicimos un Merge,unir los cambios de una rama con otra) 

Fn es la version final(HEAD) donde estan todos los cambios. 

Cuanto tenemos una rama de experimentos(development) y la queremos unir al HEAD final ese proceso tambien se lo conoce como un merge. 

## Crea un repositorio de Git y haz tu primer commit
Si quieres ver los archivos ocultos de una carpeta puedes habilitar la opción de Vista > Mostrar u ocultar > Elementos ocultos (en Windows) o ejecutar el comando `ls -a`. 

Le indicaremos a Git que queremos crear un nuevo repositorio para utilizar su sistema de control de versiones. Solo debemos posicionarnos en la carpeta raíz de nuestro proyecto y ejecutar el comando `git init```. 

Recuerda que al ejecutar este comando (y de aquí en adelante) vamos a tener una nueva carpeta oculta llamada .git con toda la base de datos con cambios atómicos en nuestro proyecto. 

Recuerda que Git está optimizado para trabajar en equipo, por lo tanto, debemos darle un poco de información sobre nosotros. No debemos hacerlo todas las veces que ejecutamos un comando, basta con ejecutar solo una sola vez los siguientes comandos con tu información: 

 

`git config --global user.email "tu@email.com"` 

`git config --global user.name "Tu Nombre"` `

 

Existen muchas otras configuraciones de Git que puedes encontrar ejecutando el comando git config --list (o solo git config para ver una explicación más detallada). 

comandos de git aprendidos en esta clase: 

`git init`(se crean las carpetas ocultas donde vamos a trabajar)lo usamos para determinar la carpeta en la que vamos a trabajar. 

`git status`lo usamos para saber si tenemos un archivo añadido o borrado en nuestro proyecto, para saber en la rama en la que estamos y si tenemos commits. 

`git add <nombre del archivo>`es para añadir un archivo a nuestra rama seguidamente ponemos entre comillas el nombre de nuestro archivo o poner un punto para añadir todos los archios de nuestra carpeta. 

`git rm <nombre del archivo>`lo usamos para borrar un archivo que hayamos añadido, para eliminarlo por completo de nuestra rama usamos : 

`git rm --cached <nombre del archivo>`  (--cached significa que todavia esta en memoria RAM,todavia o guardado en la base de datos).Basicamente es quitarle el “git add”.Esto es por si nos equivocamos. 

`git commit --m"Este es el primer commit del archivo"` se usa para añadir un commit a nuestra rama, también podemos no ponerle un -m seguidamente ponemos entre comillas nuestro mensaje pero es un MALA practica 

Cuando modificamos nuestro archivo y queremos hacerle denuevo un commit no nos va a dejar nos va a decir que primero tenemos que usar
`git add <nombre del archivo>` 

Si tenemos que hacerle add a muchos archivos solamente usamos
` git add .  ` (ese punto representa la carpeta en la que estamos) 

Commit “43253223523623623235325” el numero largo representa el “tag” donde estamos,osea el nombre de la modificacion.HEAD->master es la ultima modificacion 

`git config`muestra configuraciones de git también podemos usar –list para mostrar la configuración por defecto de nuestro git y si añadimos --show-origin inhales nos muestra las configuraciones guardadas y su ubicación. 

`git config --global user.name"<nombre>”`: cambia de manera global el nombre del usuario, seguidamente ponemos entre comillas nuestro nombre.(cuando nosotros usamos –l –m usamos un solo guion porque es una letra,cuando queremos poner una palabra usamos – doble guion 

`git config --global user.email”<mail>”`: cambia de manera global el email del usuario, seguidamente ponemos entre comillas nuestro nombre. 

`git log <nombre_del_archivo>`: se usa para ver la historia de nuestros archivos, los commits, el usuario que lo cambió, cuando se realizaron los cambios etc. seguidamente ponemos el nombre de nuestro archivo. 

`code <nombre_del_archivo>` nos abre el archivo en el visual studio code 
 
 
 FOTOOOOOO
 
 
##  Analizar cambios en los archivos de tu proyecto con Git 
El comando `git show` nos muestra los cambios que han existido sobre un archivo y es muy útil para detectar cuándo se produjeron ciertos cambios, qué se rompió y cómo lo podemos solucionar. Pero podemos ser más detallados. 

Si queremos ver la diferencia entre una versión y otra, no necesariamente todos los cambios desde la creación del archivo, podemos usar el comando
`git diff <IDcommit1 IDcommit2> `

Recuerda que puedes obtener el ID de tus commits con el comando git log. 

 

 `git init` //inicializar el repositorio 
 `git add <nombre_de_archivo.extencion>` //Agregar el archivo al repositorio 
 `git commit -m “<Mensaje>`// Agregamos los cambios para el repositorio 
 `git add .`// Agregar los cambios de la carpeta en la que nos encontramos agregar todo 
 `git status` // visualizar cambios 

 `git show <nombre del archivo>` //nos va a mostrar los cambios.promero nos muestra el ultimo commit  ,que estoy en la cabezera de la rama master,lla version mas reciente 

Cuando NOS OLVIDAMOS de poner un titulo al cambio cuando hacemos el commit.Podemos agregarlo en la cabezera arriba de todo del mensaje que nos avisa.Para salir del modo ese que entra apretamos Esc + shift + zz. Y asi volvemos a nuestra consola principal. 

Si seguimos agregando cambios nos va a volver a abri esa misma interface.Esta es un editor de codigo basado en linea de comandos VIN.Es un editor de texto.Lo que esta en # celeste.son comentarios.Para escribir apretamos Esc + i 

Le damos `Esc + shift + zz `fuerza el envio del  commit.Esta es la forma de guardar en VIN 

 
`git log <nombre_de_archivos.extencion>` //historico de cambios en los commits 

`git diff <copiamos el numero 242535323632 del commit del arhivo que queremos comparar con otro seguido del otro numero 42532523423>` //esto va a comparar los cambios hechos entre los dos archivos.Segun el orden en el que los coloquemos los nombre de los archivos, el color verde o rojo van a ser los cambios mostrados 

 

## Volver en el tiempo en nuestro repositorio utilizando reset y checkout Volver en el tiempo en nuestro repositorio utilizando reset y checkout 

El comando `git checkout <ID>` del commit nos permite viajar en el tiempo. Podemos volver a cualquier versión anterior de un archivo específico o incluso del proyecto entero. Esta también es la forma de crear ramas y movernos entre ellas. 

También hay una forma de hacerlo un poco más “ruda”: usando el comando git reset. En este caso, no solo “volvemos en el tiempo”, sino que borramos los cambios que hicimos después de este commit. 

Hay dos formas de usar git reset: con el argumento --hard, borrando toda la información que tengamos en el área de staging (y perdiendo todo para siempre). O, un poco más seguro, con el argumento --soft, que mantiene allí los archivos del área de staging para que podamos aplicar nuestros últimos cambios pero desde un commit anterior. 

`git reset 42353326235343235 –hard `

`git reset 34234234234 –soft `

Cuando creamos carpetas,y modificamos archivos y lo vemos en status.con  

`git diff` solamente podemos ver la que esta en la memoria ram vs lo que esta en el disco duro.Puedo ver las diferencias entre mi directorio actual y el stagging. 

Para agregar todo hacemos `git add .` 

`git log –stat` // vemos los cambios especificos que se hicieron en los archivos a partir del commit.Los bits que se cambiaron.Con la letra  q salimos de esa visualización. 

Digamos que queremos ver la primera version de un archivo,verlo en su primera version.Para Hacer eso usamos el checkout 

`git checkout <id del archivo(34235325236235)> <nombre del archivo.ext> `

Con esto volvemos al staggin pero en log vemos que no pasa nada,si ponemos 

`git checkout master <nombre del archivo>` volvemos a la ultima version que teniamos 
## Git reset vs. Git rm 
`git reset` y `git rm` son comandos con utilidades muy diferentes, pero aún así se confunden muy fácilmente. 

`git rm` 

Este comando nos ayuda a eliminar archivos de Git sin eliminar su historial del sistema de versiones. Esto quiere decir que si necesitamos recuperar el archivo solo debemos “viajar en el tiempo” y recuperar el último commit antes de borrar el archivo en cuestión. 

Recuerda que git rm no puede usarse así nomás. Debemos usar uno de los flags para indicarle a Git cómo eliminar los archivos que ya no necesitamos en la última versión del proyecto: 

`git rm --cached`: Elimina los archivos del área de Staging y del próximo commit pero los mantiene en nuestro disco duro. 

`git rm --force`: Elimina los archivos de Git y del disco duro. Git siempre guarda todo, por lo que podemos acceder al registro de la existencia de los archivos, de modo que podremos recuperarlos si es necesario (pero debemos usar comandos más avanzados). 

`git reset `

Este comando nos ayuda a volver en el tiempo. Pero no como git checkout que nos deja ir, mirar, pasear y volver. Con git reset volvemos al pasado sin la posibilidad de volver al futuro. Borramos la historia y la debemos sobreescribir. No hay vuelta atrás. 

Este comando es muy peligroso y debemos usarlo solo en caso de emergencia. Recuerda que debemos usar alguna de estas dos opciones: 

Hay dos formas de usar git reset: con el argumento --hard, borrando toda la información que tengamos en el área de staging (y perdiendo todo para siempre). O, un poco más seguro, con el argumento --soft, que mantiene allí los archivos del área de staging para que podamos aplicar nuestros últimos cambios pero desde un commit anterior. 

`git reset --soft`: Borramos todo el historial y los registros de Git pero guardamos los cambios que tengamos en Staging, así podemos aplicar las últimas actualizaciones a un nuevo commit. 

`git reset --hard`: Borra todo. Todo todito, absolutamente todo. Toda la información de los commits y del área de staging se borra del historial. 

¡Pero todavía falta algo! 

`git reset HEAD`: Este es el comando para sacar archivos del área de Staging. No para borrarlos ni nada de eso, solo para que los últimos cambios de estos archivos no se envíen al último commit, a menos que cambiemos de opinión y los incluyamos de nuevo en staging con git add, por supuesto. 

¿Por qué esto es importante? 

Imagina el siguiente caso: 

Hacemos cambios en los archivos de un proyecto para una nueva actualización. Todos los archivos con cambios se mueven al área de staging con el comando git add. Pero te das cuenta de que uno de esos archivos no está listo todavía. Actualizaste el archivo pero ese cambio no debe ir en el próximo commit por ahora. 

¿Qué podemos hacer? 

Bueno, todos los cambios están en el área de Staging, incluido el archivo con los cambios que no están listos. Esto significa que debemos sacar ese archivo de Staging para poder hacer commit de todos los demás. 

¡Al usar `git rm` lo que haremos será eliminar este archivo completamente de git! Todavía tendremos el historial de cambios de este archivo, con la eliminación del archivo como su última actualización. Recuerda que en este caso no buscábamos eliminar un archivo, solo dejarlo como estaba y actualizarlo después, no en este commit. 

En cambio, si usamos `git reset HEAD`, lo único que haremos será mover estos cambios de Staging a Unstaged. Seguiremos teniendo los últimos cambios del archivo, el repositorio mantendrá el archivo (no con sus últimos cambios pero sí con los últimos en los que hicimos commit) y no habremos perdido nada. 

Conclusión: Lo mejor que puedes hacer para salvar tu puesto y evitar un incendio en tu trabajo es conocer muy bien la diferencia y los riesgos de todos los comandos de Git. 
# Flujo de trabajo básico en Git
## Flujo de trabajo básico con un repositorio remoto
Por ahora, nuestro proyecto vive únicamente en nuestra computadora. Esto significa que no hay forma de que otros miembros del equipo trabajen en él. 

Para solucionar esto están los servidores remotos: un nuevo estado que deben seguir nuestros archivos para conectarse y trabajar con equipos de cualquier parte del mundo. 

Estos servidores remotos pueden estar alojados en GitHub, GitLab, BitBucket, entre otros. Lo que van a hacer es guardar el mismo repositorio que tienes en tu computadora y darnos una URL con la que todos podremos acceder a los archivos del proyecto para descargarlos, hacer cambios y volverlos a enviar al servidor remoto para que otras personas vean los cambios, comparen sus versiones y creen nuevas propuestas para el proyecto. 

Esto significa que debes aprender algunos nuevos comandos: 

`git clone <url_del_servidor_remoto>`Nos permite descargar los archivos de la última versión de la rama principal y todo el historial de cambios en la carpeta .git. 

`git push` Luego de hacer git add y git commit debemos ejecutar este comando para mandar los cambios al servidor remoto. 

`git fetch` Lo usamos para traer actualizaciones del servidor remoto y guardarlas en nuestro repositorio local (en caso de que hayan, por supuesto). 

`git merge`También usamos el comando git merge con servidores remotos. Lo necesitamos para combinar los últimos cambios del servidor remoto y nuestro directorio de trabajo. 

`git pull`Básicamente, git fetch y git merge al mismo tiempo. 

 

 

Algunos comandos que pueden ayudar cuando colaboren con proyectos muy grandes de github: 

`git log --oneline` - Te muestra el id commit y el título del commit. 

`git log --decorate`- Te muestra donde se encuentra el head point en el log. 

`git log --stat `- Explica el número de líneas que se cambiaron brevemente. 

`git log -p`- Explica el número de líneas que se cambiaron y te muestra que se cambió en el contenido. 

`git shortlog` - Indica que commits ha realizado un usuario, mostrando el usuario y el titulo de sus commits. 

`git log --graph --oneline --decorate ` Muestra mensajes personalizados de los commits. 

`git log --pretty=format:"%cn hizo un commit %h el dia %cd" `- Muestra mensajes personalizados de los commits. 

`git log -3 `- Limitamos el número de commits. 
`


    git log --after=“2018-1-2” ,
    
    git log --after=“today” 
    
    git log --after=“2018-1-2” --before=“today”
	
	- Commits para localizar por fechas. 

`git log --author=“Name Author”` - Commits realizados por autor que cumplan exactamente con el nombre. 

`git log --grep=“INVIE”` - Busca los commits que cumplan tal cual está escrito entre las comillas. 

`git log --grep=“INVIE” –i`- Busca los commits que cumplan sin importar mayúsculas o minúsculas. 

`git log – index.html`- Busca los commits en un archivo en específico. 

`git log -S “Por contenido”`- Buscar los commits con el contenido dentro del archivo. 

`git log > log.txt `- guardar los logs en un archivo txt 

## Introducción a las ramas o branches de Git
Las ramas son la forma de hacer cambios en nuestro proyecto sin afectar el flujo de trabajo de la rama principal. Esto porque queremos trabajar una parte muy específica de la aplicación o simplemente experimentar. 

La cabecera o HEAD representan la rama y el commit de esa rama donde estamos trabajando. Por defecto, esta cabecera aparecerá en el último commit de nuestra rama principal. Pero podemos cambiarlo al crear una rama (git branch rama, git checkout -b rama) o movernos en el tiempo a cualquier otro commit de cualquier otra rama con los comandos (git reset id-commit, git checkout rama-o-id-commit) 

 

Cuando estamos trabajando con archivos que ya les hicimos add simplemente podemos mandarlos al repositorio con git commit –am, no hace falta agregar el add denuevo,el add es para un archivo nuevo. 

La rama se va a crear desde el lugar en donde estoy, asi que le damos a git status, vemos que dice estamos en la rama(brench en ingles) master, ningún commit para hacer, trabajando en un árbol limpio, en una cabecera que apunta al master(en celeste).  

Tambien puedo darle a git show y vemos el ultimo cambio que hicimos y significa que desde aquí vamos a hacer los cambios.Con git show se donde esta   el HEAD->.Osea la carpeta en la que estamos trabajando.Salimos del git show con q 

Limpiamos la pantalla.Y ponemos  

`git branch <nombre de la rama>`en este caso git branch cabecera.Si le damos a git show denuevo vemos que ahora apuntar a master y tambien a <cabecera>.Es decir el ultimo commit esta pegado a dos ramas distintas 

¿Cómo me muevo hacia la otra rama?Lo hago con  

`git checkout <nombre de la rama>` Vemos que cambia de branch(rama).Ponemos git status y vemos que cambio a la rama cabecera.Hacemos nuestros cambios a los archivos,les damos git add,git commit. Vemos nuestros cambios con git status,git log. 

Si nos volvemos a cambiar de rama con git checkout a master .Nuestro archivo vuelve a ser el anterior,no el que modificamos en la rama nueva.Es decir que podemos trabajar en nuestra rama sin alterar la otra.En donde definimos nuestro branch ahi tenemos una misma copia del otro archivo y de ahí parte nuestras modificaciones. 

 

RECORDAR QUE LOS CAMBIOS QUE HAGAMOS EN LA OTRA RAMA CABECERA HAY QUE HACERLES `git commit –am `porque si volvemos a cambiar de rama sin hacer esto podemos perder nuestros archivos 

 

Recuerda que al ejecutar el comando git checkout para cambiar de rama o commit puedes perder el trabajo que no hayas guardado. Guarda tus cambios antes de hacer git checkout.(ESTO va para cualquier rama donde estemos trabajando,si nos cambiamos de rama sin hacer el commit vamos a perder nuestros archivos) 

## Fusión de ramas con Git merge 
El comando `git merge `nos permite crear un nuevo commit con la combinación de dos ramas (la rama donde nos encontramos cuando ejecutamos el comando y la rama que indiquemos después del comando). 



Crear un nuevo commit en la rama cabecera combinando los cambios de cualquier otra rama:
`git checkout cabecera`

`git merge cualquier-otra-rama `

Asombroso, ¿verdad? Es como si Git tuviera super poderes para saber qué cambios queremos conservar de una rama y qué otros de la otra. El problema es que no siempre puede adivinar, sobretodo en algunos casos donde dos ramas tienen actualizaciones diferentes en ciertas líneas en los archivos. Esto lo conocemos como un conflicto y aprenderemos a solucionarlos en la siguiente clase. 

Recuerda que al ejecutar el comando git checkout para cambiar de rama o commit puedes perder el trabajo que no hayas guardado. Guarda tus cambios antes de hacer git checkout.(ESTO va para cualquier rama donde estemos trabajando,si nos cambiamos de rama sin hacer el commit vamos a perder nuestros archivos) 

 

Si queremos unir los archivos de cabecera(la rama segunda ) a nuestra rama principal master ,el merge hay que hacerlo desde master llamando a la rama. 

`git checkout master `

`git merge  <nombre de la rama> `

Si no sabemos el nombre de la rama usamos  

`git branch` y nos dice el nombre de la rama  

Un merge es un commit ,asi que nos van a pedir un mensaje. 

Si hacemos un `git log` vemos que todos los commit que tenia la branch ahora los vemos tambien en el master. 

## Resolución de conflictos al hacer un merge 
Git nunca borra nada a menos que nosotros se lo indiquemos. Cuando usamos los comandos `git merge` o `git checkout` estamos cambiando de rama o creando un nuevo commit, no borrando ramas ni commits (recuerda que puedes borrar commits con `git reset` y ramas con `git branch -d`). 

Git es muy inteligente y puede resolver algunos conflictos automáticamente: cambios, nuevas líneas, entre otros. Pero algunas veces no sabe cómo resolver estas diferencias, por ejemplo, cuando dos ramas diferentes hacen cambios distintos a una misma línea. 

Esto lo conocemos como conflicto y lo podemos resolver manualmente, solo debemos hacer el merge, ir a nuestro editor de código y elegir si queremos quedarnos con alguna de estas dos versiones o algo diferente. Algunos editores de código como VSCode nos ayudan a resolver estos conflictos sin necesidad de borrar o escribir líneas de texto, basta con hundir un botón y guardar el archivo. 

Recuerda que siempre debemos crear un nuevo commit para aplicar los cambios del merge. Si Git puede resolver el conflicto hará commit automáticamente. Pero, en caso de no pueda  , debemos solucionarlo y hacer el commit. 

Los archivos con conflictos por el comando git merge entran en un nuevo estado que conocemos como Unmerged. Funcionan muy parecido a los archivos en estado Unstaged, algo así como un estado intermedio entre Untracked y Unstaged, solo debemos ejecutar git add para pasarlos al área de staging y git commit para aplicar los cambios en el repositorio. 

## Uso de GitHub 
GitHub es una plataforma que nos permite guardar repositorios de Git que podemos usar como servidores remotos y ejecutar algunos comandos de forma visual e interactiva (sin necesidad de la consola de comandos). 

Luego de crear nuestra cuenta, podemos crear o importar repositorios, crear organizaciones y proyectos de trabajo, descubrir repositorios de otras personas, contribuir a esos proyectos, dar estrellas y muchas otras cosas. 

El README.md es el archivo que veremos por defecto al entrar a un repositorio. Es una muy buena práctica configurarlo para describir el proyecto, los requerimientos y las instrucciones que debemos seguir para contribuir correctamente. 

Para clonar un repositorio desde GitHub (o cualquier otro servidor remoto) debemos copiar la URL (por ahora, usando HTTPS) y ejecutar el comando `git clone <+ la URL>` que acabamos de copiar. Esto descargara la versión de nuestro proyecto que se encuentra en GitHub. 

Sin embargo, esto solo funciona para las personas que quieren empezar a contribuir en el proyecto. Si queremos conectar el repositorio de GitHub con nuestro repositorio local, el que creamos con git init, debemos ejecutar las siguientes instrucciones: 

 Primero: Guardar la URL del repositorio de GitHub 

`git remote add origin <URL que nos da la pagina> `
 Segundo: Verificar que la URL se haya guardado correctamente: 

`git remote` 

`git remote -v `

Nos va a mostrar  la url (fetch)traer cosas y (push)enviar cosas 

Hacemos `git push(enviele) origin(al origen,la url de la pagina q nos dieron) master(la rama master) `

Va a salir una pantallita que nos pide el mail y la contraseña de git,la colocamos 

Nos va a salir un error,porque ahora el readme de github es nuestro master 

 Tercero: Traer la versión del repositorio remoto y hacer merge para crear un commit con los archivos de ambas partes. Podemos usar `git fetch` y
 `git merge `o solo`git pull origin master --allow-unrelated-histories`(esto significa fusionar lo otro con la rama que tengo en local.

 Por último, ahora sí podemos hacer `git push` para guardar los cambios de nuestro repositorio local en GitHub: 
`git push origin master` (del master local al master de hithub) 



    Resumen comandos
    
    git clone url //para traer el repositorio desde el servidor remoto| 
    git fetch //para traer los archivos del servidor al repositorio local | 
    git merge //para actualizar y fucionar el directorio de trabajo| 
    git pull //union de fetch y merge| 
    git push //sirve para subir todos los archivos a tu repositorio remoto| 
    git remote add origin url //esto sirve para agregar algo a github| 
    git pull origin master //para bajar los archivos a tu pc| 
    git push origin master //para subir las cosas a github| 
    git pull origin master --allow-unrelated-histories //para hacer el merge fusionado lo de tu pc con lo de github| 

## Cómo funcionan las llaves públicas y privadas 
Las llaves públicas y privadas nos ayudan a cifrar y descifrar nuestros archivos de forma que los podamos compartir sin correr el riesgo de que sean interceptados por personas con malas intenciones. 

La forma de hacerlo es la siguiente: 

1.Ambas personas deben crear su llave pública y privada. 

2.Ambas personas pueden compartir su llave pública a las otras partes (recuerda que esta llave es pública, no hay problema si la “interceptan”).

 3.La persona que quiere compartir un mensaje puede usar la llave pública de la otra persona para cifrar los archivos y asegurarse que solo puedan ser descifrados con la llave privada de la persona con la que queremos compartir el mensaje. 

4.El mensaje está cifrado y puede ser enviado a la otra persona sin problemas en caso de que los archivos sean interceptados.

 5.La persona a la que enviamos el mensaje cifrado puede usar su llave privada para descifrar el mensaje y ver los archivos.

Puedes compartir tu llave pública pero nunca tu llave privada.

En la siguiente clase vamos a crear nuestras llaves para compartir archivos con GitHub sin correr el riesgo de que sean interceptados.



Llaves públicas y privadas o Cifrado asimétrico de un sólo camino 

Sirve para mandar mensajes privados entre varios nodos con la lógica de que firmas tu mensaje con una llave pública vinculada con una llave privada que puede leer el mensaje. 

El flujo es: 

Creas una llave pública y una llave privada (ambas están vinculadas) 

Cifras el mensaje con la llave pública (puede ser llave de otra persona) 

Envías el mensaje 

El receptor, al tener la llave privada puede descifrar el mensaje. 

Este algoritmo es completamente seguro, así es cómo se mandan las comunicaciones en bancos, la comunicación entre servidores o las firmas electrónicas 

## Configura tus llaves SSH en local 
Para cambiar el email de git denuevo usamos: 

`git config –global user.email”<email>”`  

Vemos que cambio con : 
`git config -l `


Nadie se sabe de memoria como crear la llave simplemente lo googleamos 

Primer paso: Generar tus llaves SSH. Recuerda que es muy buena idea proteger tu llave privada con una contraseña. 

`ssh-keygen -t rsa -b 4096 -C "<tu@email.com> " `

Segundo paso: Terminar de configurar nuestro sistema. 

Nos dice que elijamos la carpeta,le damos enter porque esta carpeta esta bien.el .blabla significa que va a estar escondida la carpeta. 

Luego nos va a pedir un passphrase(esto significa una contraseña con espacios)si queremos le ponemos sino no,es recomendable que si. 

Vamos a la carpeta home donde creamos la llave y vamos a ver que se creo una carpeta llamada .ssh:ahí adentro vamos a ver dos archivos,una es nuestra llave privada y la otra es una llave publica.La publica la abrimos con visual studio code  la copiamos y la llevamos a GitHub   

  

En Windows y Linux: 
 Encender el "servidor" de llaves SSH de tu computadora: 

`eval $(ssh-agent -s)   ` .Esto nos va abrir un agent pid 45454 numero distinto,este agent significa que el servidor de ssh esta corriendoSiguiente paso 

Recordar donde creamos la llave 

Simplemente con `cd ~ ` para no poner toda la ruta 

Podemos ir donde esta la llave con `cd ~/.shh/ `


 Añadir tu llave SSH a este "servidor": 

`ssh-add <ruta-donde-guardaste-tu-llave-privada> `  LA LLAVE PRIVADA 


 ` UseKeychain yes `

  `IdentityFile ~/.ssh/id_rsa `

Agrega tu llave 

`ssh-add -K ~/.ssh/id_rsa `

## Conexión a GitHub con SSH
Las llaves estan creadas en el home de tu carpeta no en nuestro proyecto.Aclaracion debe haber tantas llaves como usuarios,computadoras haya conectadas con el repositorio. 

Luego de crear nuestras llaves SSH podemos entregarle la llave pública a GitHub para comunicarnos de forma segura y sin necesidad de escribir nuestro usuario y contraseña todo el tiempo. 

Para esto debes entrar a la Configuración de Llaves SSH en GitHub, (SSH and GPG keys,add new)(titulo ejemplo:laptop de educacion de platzi),crear una nueva llave con el nombre que le quieras dar y el contenido de la llave pública de tu computadora. 

Ahora podemos actualizar la URL que guardamos en nuestro repositorio remoto, solo que, en vez de guardar la URL con HTTPS, vamos a usar la URL con SSH:(en la parte del repositorio que dice Clone or download) cambiamos a SSH,copiamos esa direccion que aparece y vamos a nuestro entorno local,nos metemos en nuestra carpeta de proyecto1 ahí le damos a : 

$git remote –v esto nos va a mostrar cual es la URL de nuestros repositorios.Lo que vamos a hacer es cambiar ese URL: 

`git remote set-url origin <url-ssh-del-repositorio-en-github>` ( lo que copiamos para pegar)origin es un estandar que se usa pero puede ser cualquier otra palabra 

Vemos que cambio con` git remote –v `y listo podemos hacer cambios en nuestros archivos a ver que tal 

Lo primero que hay que hacer un commit debemos traernos la ultima version del servidor¿Como se trae? 

`git pull  `nos pregunta algo y le damos a yes or no 

Nos da un error porque tenemos que aclarar con que rama nos queremos conectar,etc 

Nos traemos del origen por eso(origin) osea el nombre de nuestro repositorio.Y lo vamos a fusionar con nuestra rama actual que es:(master) 

`git pull origin master`  y nos dice que listo que todo esta actualizado 

`git status `

`git diff `

`gitt commit –am ”una version del hiperblog”` .Ahora como envio el cambio?Antes de enviar el cambio deberia hacer git push 

`git push origin master `

 
Listo ahora vamos a GitHub vamos a repositorios,vemos la actualizados hace unos segundos y vemos el cambio,en history agora podemos ver quien hizo los cambios 
## Tags y versiones en Git y GitHub 
`git log` vemos el historial de commits 

`git log –all` VEMOS TODO los cambios 

`git log –all --graph` nos muestra como unas rayitas de como han funcionados las ramas 

`git log –all  –graph –decorate –oneline `Nuestra muestra todo mas resumido pero bien organizado. 

Como el comando es tan  largo y no lo vamos a recordar le podemos cambiar el nombre poniendolo algun alias como en linux : 

`alias <nombre_del_alias>=” git log –all  –graph –decorate –oneline” `

`<nombre_del_alias> nos muestra el comando largo `

Esto lo podemos hacer con todas las funciones ,osea estamos creando no alias sino TAGS 

Como podemos crear TAGS de nuestros commits?: 

Los tags o etiquetas nos permiten asignar versiones a los commits con cambios más importantes o significativos de nuestro proyecto. 

Comandos para trabajar con etiquetas: 

Crear un nuevo tag y asignarlo a un commit: 
`git tag -a <nombre del tag> -m <mensaje del commit”<ID del commit>   (la convension para nombres del tag es v0.1  v0.2) `
`
 

Borrar un tag en el repositorio local: `git tag -d nombre-del-tag. `

Listar los tags de nuestro repositorio local: `git tag` o `git show-ref --tags. 

Los tags son utiles en la pagina web para que los usuarios del codigo abierto o otras  puedan ver que versiones ocurrieron,rara ves son utiles adentro del proyecto  por eso vamos a enviarlos a internet: 

Antes de hacer cualquier cambio acordarse de hacer un 

`git pull origin master` (Para traernos todo lo que esta en internet) 

Ahora si enviamos el tag 

Publicar un tag en el repositorio remoto: `git push origin --tags. `

Vamos a ver la pagina en la parte de branch, se agrego Tag v0.1 y vemos los archivos 

Borrar (lo podemos hacer desde la pagina pero debemos saber hacerlo desde la consola)borrar un tag del repositorio remoto:  

 `  git tag -d <nombre-del-tag>  `

 `  git push origin :refs/tags/<nombre del tag que queremos borrar> `
 
 
 
 
##  Manejo de ramas en GitHub 
Puedes trabajar con ramas que nunca envías a GitHub, así como pueden haber ramas importantes en GitHub que nunca usas en el repositorio local. Lo importante es que aprendas a manejarlas para trabajar profesionalmente. 

Recordatorio de comando importanes en ramas. 

`git checkout <nombre de la rama>` es lo que me permite cambiar de rama 

`git branch` me muestra todas las ramas que existen 

`git show-branch` muestra las ramas y sus historias 

`git show-branch –al `nos va a mostrar lo mismo pero con un poco mas de datos 

 
Crear una rama en el repositorio local: `git branch <nombre-de-la-rama></nombre-de-la-rama>` o` git checkout -b <nombre-de-la-rama.> `

`git pull origin master `

Publicar una rama local al repositorio remoto: `git push origin <nombre-de-la-rama.>
`
Recuerda que podemos ver gráficamente nuestro entorno y flujo de trabajo local con Git usando el comando  

`gitk. `

 

Creemos nuestras ramas headery footer,lo mejor es desde nuestra rama mas reciente osea el master 

`git checkout master `

`git branch header `

`git branch footer `

`git branch` // vemos las ramas creadas 

Las enviamos a  GitHub 

##  Configurar múltiples colaboradores en un repositorio de GitHub 
Por defecto, cualquier persona puede clonar o descargar tu proyecto desde GitHub, pero no pueden crear commits, ni ramas, ni nada. 

Existen varias formas de solucionar esto para poder aceptar contribuciones. Una de ellas es añadir a cada persona de nuestro equipo como colaborador de nuestro repositorio. 

Solo debemos entrar a la configuración de colaboradores de nuestro proyecto (Repositorio > Settings > Collaborators) y añadir el email o username de los nuevos colaboradores. 

## Flujo de trabajo profesional: Haciendo merge de ramas de desarrollo a master 
Queremos poner una imagen al header del hyperp blog 

Las mejores practicas dicen que no se deberian enviar archivos binarios al repositorio,deberian estar aparte 

Vamos a hacer un chekout la rama header porque a master solo vamos a enviar lo que esta listo para produccion.Esto es una buena practica 

`git add imágenes/dragon.png `

`git pull origin header `

`git push origin header `

Los cambios que realizamos en nuestras imagen pueden tardar en aparecer en github.si queremos forzar la actualizacion ponemos  ctrol shif r ,o control f5 

Hacemos los cambios  

`git commit –am `

Nosotros como desarrolladores generalmente tenemos cque trabajarar en las ramas y no en el ,master por eso nos dice que trabajemos en el footer,para ello nos traemos de internet la rama footer 

`git pull origin footer 
`
Nos vamos a la rama 

`git checkout footer `

`git branch `

`git ls –al 
`
El Jefe va a ser el que haga el merge de las ramas.Recordar de ir a la rama maestra y desde ahi hacer el merge 

 

 

 

 

Basicamente el flujo de trabajo seria como: 

Crear ramas 

Asignar una rama a cada programador 

El programador baja el repositorio con git pull origin master 

El programador cambia de rama 

El programador trabaja en esa rama y hace commits 

El programador sube su trabajo con git push origin #nombre_rama 

El jefe,cto, baja y unifica todos los cambios 

 

-Simular dos ambientes es agotador para el profesor y su equipo de producción. También lo es para el estudiante. 
-El verdadero poder de Github se desata en cuanto se ordena el trabajo colaborativo mediante ramas. 
-El manejo adecuado de este poder es más sencillo para quienes ya tienen experiencia (alias, muy malas experiencias, sí es mi caso) en programación en grupo (sí, te miro a tí Team Fundation). 
-Observen que el instructor pone mucho cuidado cuando ejecuta el “pull/push”, no sólo que lo ejecuta en ese orden, sino que respeta el emparejamiento de ramas, es decir, sí localmente está situado en header, hace un pull/push de la rama remota header. 
-Bueno IO me equivoqué, aunque no la lie tan parda, pude hacer un “git merge --abort” y luego una muy corta sesión de solución de conflictos y revisión del código. Aún así esto me dejo la mejor experiencia. 
-Esta es la última y nos vamos, EQUIVOQUENSE!!! Por Dios, mejor aquí entre las criaturas del Señor, que en un puesto corporativo jugándose su cuello flaco. 

## Flujo de trabajo profesional con Pull requests 
En un entorno profesional normalmente se bloquea la rama master, y para enviar código a dicha rama pasa por un code review y luego de su aprobación se unen códigos con los llamados merge request. 

Para realizar pruebas enviamos el código a servidores que normalmente los llamamos staging develop (servidores de pruebas,que son iguales al master,siempre tienen que estar actualizadoc con el principal) luego de que se realizan las pruebas pertinentes tanto de código como de la aplicación estos pasan a el servidor de producción con el ya antes mencionado merge request. Los PR(pre merge) son la base de la colaboración a proyectos Open Source, si tienen pensando colaborar en alguno es muy importante entender esto y ver cómo se hace en las próximas clases. Por lo general es forkear el proyecto, implementar el cambio en una nueva rama, hacer el PR y esperar que los administradores del proyecto hagan el merge o pidan algún cambio en el código o commits que hiciste. 

## Utilizando Pull Requests en GitHub 

Supongamos que tenemos que corregir unos error de tipografia de nuestra rama master 

Podemos Crear una nueva rama para arreglar estos error y luego fusionarla a la master. 

`git pull origin master` //nos traemos la ultima version 

`git branch fix-type ` //creamos una nueva rama 

`git branch` //comprobamos  

`git checkout fix-type` // nos vemos a esa rama 

Hacemos los cambios pertinentes dentro de esa rama 

`git status` // vemos las modificaciones 

`git diff` // lo mismo 

`git push origin fix-type (osea a GitHub)` //hacemos un push hacia nuestra rama fix 

¿Cómo la fusionamos con el otro lado? Desde github en nuestra rama fyx-type hacemos un “New pull request 

ponemos que compare desde master a fix type 

Ya que hicimos los cambios voy a hacer un git status desde la consola 

Recordar que todos las cambios que hagamos hay que hacerle commit o no se van a ver en el repositorio.Recordar que estamos en la rama fix-type en la consla 

`git commit –a “mensaje,blabla arreglados” `

g`it push origin fix-type( lo envie en github) `

Si yo soy el dueño del trabajo.Y en la rama master voy a pull request.comparamos las ramas y nos va a decir si se mpuede hacer merge o no(esto nos permite agregarles detalles)me toma el nombre del commit como el nombre del pull request 

Podemos perdirle a otras personas que revisen este pull request en la pestaañ derecha (REWIEVS) 

Asiggnes ,le puede hasignar este pull a alguien 

Le puedo asignar etiquetas, esto se vuelve util  en el proceso de DevsOps.el proceso de crear un sistema en el cual nuestros programaodes puedan trabajar mejor 

Milestone signifa que logramos un objetivo que teniamos y este pull request lo representa 

Project,formas de agrupar repositorios dentro de github 

Esto entra en formas de trabajos (devops) 

El pull request no ejecuta el merge de porsi solo nos describe lo q esta pasando y alguien puede revisasrlo,lo importane es enviarlo al equipo 

Lo que hago a darla pull request se los envio asi lo ven  

Los demos pueden comentarlo,aprobarlo,o hacerle solicitarle cambios 

 

Los pull request del lado de git no existen,solo existen los merge.en git hub es como una pausa para analizar el cambio. 

 

 
Pull request: 

Es una funcionalidad de github (en gitlab llamada merge request y en bitbucket push request), en la que un colaborador pide que revisen sus cambios antes de hacer merge a una rama, normalmente master. 

Al hacer un pull request se genera una conversación que pueden seguir los demás usuarios del repositorio, así como autorizar y rechazar los cambios. 

El flujo del pull request es el siguiente 

Se trabaja en una rama paralela los cambios que se desean (git checkout -b <rama>) 

Se hace un commit a la rama (git commit -am '<Comentario>') 

Se suben al remoto los cambios (git push origin <rama>) 

En GitHub se hace el pull request comparando la rama master con la rama del fix. 

Uno, o varios colaboradores revisan que el código sea correcto y dan feedback (en el chat del pull request) 

El colaborador hace los cambios que desea en la rama y lo vuelve a subir al remoto (automáticamente jala la historia de los cambios que se hagan en la rama, en remoto) 

Se aceptan los cambios en GitHub 

Se hace merge a master desde GitHub 

Importante: Cuando se modifica una rama, también se modifica el pull request. 

La persona encargada de coordinar todo lo que sucede con el proyecto es comúnmente denominada DevOps, un administrador del entorno de desarrollo que hace más fácil la vida del programador y crea el ambiente para que los equipos de trabajo hagan su labor de manera más efectiva. 

## Creando un Fork, contribuyendo a un repositorio 
 

Forks o Bifurcaciones 

Es una característica única de GitHub en la que se crea una copia exacta del estado actual de un repositorio directamente en GitHub, éste repositorio podrá servir como otro origen y se podrá clonar (como cualquier otro repositorio), en pocas palabras, lo podremos utilizar como un git cualquiera 
. 
Un fork es como una bifurcación del repositorio completo, tiene una historia en común, pero de repente se bifurca y pueden variar los cambios, ya que ambos proyectos podrán ser modificados en paralelo y para estar al día un colaborador tendrá que estar actualizando su fork con la información del original. 
. 
Al hacer un fork de un poryecto en GitHub, te conviertes en dueñ@ del repositorio fork, puedes trabajar en éste con todos los permisos, pero es un repositorio completamente diferente que el original, teniendo alguna historia en común. 
. 
Los forks son importantes porque es la manera en la que funciona el open source, ya que, una persona puede no ser colaborador de un proyecto, pero puede contribuír al mismo, haciendo mejor software que pueda ser utilizado por cualquiera. 
. 
Al hacer un fork, GitHub sabe que se hizo el fork del proyecto, por lo que se le permite al colaborador hacer pull request desde su repositorio propio. 

Trabajando con más de 1 repositorio remoto 

Cuando trabajas en un proyecto que existe en diferentes repositorios remotos (normalmente a causa de un fork) es muy probable que desees poder trabajar con ambos repositorios, para ésto puedes crear un remoto adicional desde consola. 

`git remote add <nombre_del_remoto> <url_del_remoto> `

`git remote upstream  `

https://github.com/freddier/hyperblog 

Al crear un remoto adicional podremos, hacer pull desde el nuevo origen (en caso de tener permisos podremos hacer fetch y push) 

`git pull <remoto> <rama> `

`git pull upstream master `

Éste pull nos traerá los cambios del remoto, por lo que se estará al día en el proyecto, el flujo de trabajo cambia, en adelante se estará trabajando haciendo pull desde el upstream y push al origin para pasar a hacer pull request. 

`git pull upstream master `
` git push origin master `

## Haciendo deployment a un servidor 
En esta clase veremos como hacer deploy de nuestra aplicación utilizando un servidor. 

No te preocupes si no has comprado un servidor, no es necesario, puedes instalar un servidor local en tu computadora para realizar pruebas y testear tu aplicación. 

En Platzi tenemos una carrera de servidores que te va a ayudar a automatizar mucho más estas tareas: platzi.com/servidores 

 

 

Son impresionantes las ventajas que tiene el utilizar o implementar DevOps en el flujo de trabajo, ahora veamos cómo encaja DevOps dentro de este flujo: 

Desarrollo: nuevas características, mejoras, corrección de errores. 
Se crea el Pull Request. 
Se compila o construye lo que sea necesario y se ejecutan las pruebas: automatización de procesos con GitHub y herramientas como Jenkins, Travis, CircleCI, entre otras. 
Se aprueba el Pull Request. 
Se hace merge con Master. 
Se compila o construye lo que sea necesario para un entorno de staging o producción y se ejecutan las pruebas 
Deploy: lo ejecuta automáticamente Jenkins, o la herramienta utilizada, una vez las pruebas pasan. 

Por qué es importante DevOps? 
Primero, vamos a definir ¿qué es DevOps? no es un cargo o una persona, es una cultura que agrupa una serie de prácticas y principios para mejorar y automatizar los procesos entre los equipos de desarrollo e infraestructura (IT) para hacer el lanzamiento de software de una manera rápida, eficiente y segura. 

Un concepto importante y uno de los pilares fundamentales en DevOps es la automatización de procesos, que incluye los procesos de construcción, pruebas y lanzamiento del software con herramientas como Git, Jenkins, Circle CI, Travis, Terraform, entre otras. 

Estas herramientas hacen pruebas a nuestra aplicación, antes de salir a producción, para identificar errores y solucionarlos, con esto los usuarios no se verán afectados. 

##  Hazme un pull request 
¡Muchas gracias por tu participación en este reto! Hasta agosto de 2020 hemos procesado 1.269 pull requests en el repositorio del curso. Ahora hemos decidido cerrar este experimento, por lo que no seguiremos aprobando nuevos PRs. ¡Pero no te desanimes! Aún así te animamos a completar y enviar tu solución a este desafío para poner en práctica todo lo que has aprendido. 

 
 

Queremos que uses las habilidades ya aprendidas para aplicarlas en esta clase. Haz un fork de el repositorio de GitHub y realiza las tareas que te indicaremos en esta clase. Ojo, debes seguir las reglas e instrucciones que se dieron en el video. 

 

Vamos al link del hyperblog de fredy 

Le hacemos un fork,osea copiarle el repositorio y pegarlo en nuestro perfil en el que vamos a trabajar 

Una ves que lo tenemos en nuestro repositorio vamos a la consola 

Usamos git clone y pegamos  la url de nuestro repositorio 

Abrimos el archivo blogspot.html con code para editarlo,agregamos nuestro nombre 

Hacemos `git add `. 

`git commit –am" “ `

`git push origin master `

Ya quedaron hechos los cambios en GitHub 

Vamos al repositorio y hacemos un pull request,como el archivo ya esta vinculado,envia la solicitud 

 
 

Regla a seguir: 

Dentro del ID “post” luego de “suscribete y dale like” agrega otra línea o párrafo con tu nombre o tu nombre de usuario en Platzi. 

¡Suerte! Y #NuncaParesDeAprender 

 

HazmeUnPullRequest 

hacer FORK de hyperblog 

en blogpost.html 
Dentro del ID “post” luego de “suscribete y dale like” agrega otra línea o párrafo con tu nombre o tu nombre de usuario en Platzi. 

hacer add, commit, push 

hacer un pull request 

Esperar :v 

NuncaParesDeAprender 

##  Ignorar archivos en el repositorio con .gitignore 
 No todos los archivos que agregas a un proyecto deberían ir a un repositorio, por ejemplo cuando tienes un archivo donde están tus contraseñas que comúnmente tienen la extensión .env o cuando te estás conectando a una base de datos; son archivos que nadie debe ver. 
 Ignorar archivos para no subirlos al repositorio (.gitignore) 

Por diversas razones, no todos los archivos que agregas a un proyecto deberían guardarse en un repositorio, ésto porque hay archivos que no todo el mundo debería de ver, y hay archivos que al estar en el repositorio alentan el proceso de desarrollo (por ejemplo los binary large objects, blob, que se tardan en descargarse). 
. 
Para que no se suban estos archivos no deseados se puede crear un archivo con el nombre .gitignore en la raíz del repositorio con las reglas para los archivos que no se deberían subir (ver [sintaxis de los .gitignore(https://git-scm.com/docs/gitignore)). 
. 
Las razones principales para tomar la decisión de no agregar un archivo a un repositorio son: 
. 

Es un archivo con contraseñas (normalmente con la extensión .env) 

Es un blob (binary large object, objeto binario grande), mismos que son difíciles de gestionar en git. 

Son archivos que se generan corriendo comandos, por ejemplo la carpeta node_modules que genera npm al correr el comando npm install 

## Readme.md es una excelente práctica 
README.md es una excelente práctica en tus proyectos, md significa Markdown, que es una especie de código que te permite cambiar la manera en que se ve un archivo de texto. 

Lo interesante de Markdown es que funciona en muchas páginas, por ejemplo la edición en Wikipedia; es un lenguaje intermedio que no es HTML, no es texto plano, es una manera de crear excelentes texto formateados. 

 

 

Abrimos el archivo README con Visual studio code. 

Abrimos el editor de markcdown (TAMBIEN SE PUEDE HACER DESDE VC LEER MAS ABAJO EL APORTE)hacemos nuestro proyecto,lo copiamos y lo insertamos en VIsual studio code 

Hacemos git pull origin master 

Git commit –a 

Git push origin master y VUala 

 

Readme.md y markdown 

README.md es el lugar dónde se explica de qué trata el proyecto, cómo utilizarlo y demás información que se considere que se deba conocer antes de utilizar un proyecto. 
. 
Los archivos README son escritos en un lenguaje llamado markdown, por eso la extensión .md, mismo que es un estándar de escritura en diversos sitios (como platzi, como wikipedia y obvio GitHub), ver reglas de markdown. 
. 
Los README.md pueden estar en todas las carpetas, pero el más importante es el que se encuentra en la raíz y ayudan a que los colaboradores sepan información importante del proyecto, módulo o sección, puedes crear cualquier cualquier archivo con la extensión .md pero sólo losn README.md los mostrará por defecto GitHub. 
. 
Un ejemplo de archivo Readme.md son mis apuntes de este curso. 

 
si quieren crear el README.md desde el mismo editor. 
VSCODE nos da una opción para poder visualizarlo. 

para visualizarlo 
1) abrimos el archivo README.md 
2) damos click en la parte superior derecha en el siguiente icono 

##  Tu sitio web público con GitHub Pages 
GitHub tiene un servicio de hosting gratis llamado GitHub Pages, tu puedes tener un repositorio donde el contenido del repositorio se vaya a GitHub y se vea online. 

Publica tu página en GitHub Pages y compártelo con la comunidad en el área de discusiones de la clase, ¡te esperamos! 

 

 

Abrir pages.github.com 

Crear un repositorio con el mismo nombre de usuario en github 

tiene que ser publico 

Voy al home desde mi consola 

$git clone copiar y pegar la url de ese repositorio 

Aparece un nuevo archivo con el nombre mio 

$vim index.html   creamos el archivo que nos dicen y le ponemos lo que queremos adentro 

Hacemos git pull 

Hacemos git commit 

$git pull origin master 

Fatal:couldnt fin remotre ref master 

$git remote –v 

$git push origin master 

Revisamos nuestro repositorio y ahí aparecio 

Vamos al repositorio de git hub en setting ,vamos a la parte de git pages 

En source le damos master branch 

Puedo tener un dominio personalizado ahi vemos las opciones 

Para cambiar el nombre del repositorio y nos apareezca soble el nombre 

En setting cambiamos el REpository name a  <nombre>.github.io 

 

Voy a freddier.github.io y esta es la url especial de la pagina 

 

 

Aquí dejo mi página de Stranger Things hecho con React :3 

https://juanvf.github.io/stranger-things-imdb/ 

https://lrangelc.github.io/ 

https://diazgio.github.io/My_Cv_web/index.html 

 

 

Crear un GitHub Pages: https://pages.github.com/ 

 

 

 

1. Crear un nuevo repositorio dentro de la pagina pages.github.com 

2. Clonar repositorio a carpeta de usuario "SSH o HTTPS" 

3. Entrar en el directorio nuevo 

4. Crear un archivo de index.html 

5. Hacer el commit del archivo index.html 

6. Hacer Git push  

7. Ingresamos a las opciones del repositorio creado en GitHub y señalamos la opcion de Github Pages y activamos la master/main 

8. cambiamos el nombre del usuario a usuario.github.io 

9. Listo 

 

https://platzi.com/clases/1557-git-github/19976-tu-sitio-web-publico-con-github-pages/ 


## Git Rebase: reorganizando el trabajo realizado
El comando rebase es una mala práctica, nunca se debe usar, pero para efectos del curso te lo vamos a enseñar para que hagas tus propios experimentos. Con rebase puedes recoger todos los cambios confirmados en una rama y ponerlos sobre otra. 

# Cambiamos a la rama que queremos traer los cambios  

git checkout experiment  

# Aplicamos rebase para traer los cambios de la rama que queremos 

 $git rebase master desde la rama experimento.Primero hacer el rebase en la rama trayendo el master y luego hacer el rebase en el master trayendo a la rama 

$git rebase experimento desde el master 

 
Rebase 
Es el proceso de mover o combinar una secuencia de confirmaciones en una nueva confirmación base. La reorganización es muy útil y se visualiza fácilmente en el contexto de un flujo de trabajo de ramas de funciones. El proceso general se puede visualizar de la siguiente manera. 
Para hacer un rebase en la rama feature de la rama master, correrías los siguientes comandos: 

git checkout featuregit rebase master 

Esto trasplanta la rama feature desde su locación actual hacia la punta de la rama master

Ahora, falta fusionar la rama feature con la rama master 

git checkout mastergit rebase feature 

 No reorganices el historial público 

Nunca debes reorganizar las confirmaciones una vez que se hayan enviado a un repositorio público. La reorganización sustituiría las confirmaciones antiguas por las nuevas y parecería que esa parte del historial de tu proyecto se hubiera desvanecido de repente. 

## Git Stash: Guardar cambios en memoria y recuperarlos después ESTO ES IMPORTANTE LO VAMOS A USAR 
Recordamos nuestra funcion  

 $gitk que nos muestra todo el historal 

Cuando necesitamos regresar en el tiempo porque borramos alguna línea de código pero no queremos pasarnos a otra rama porque nos daría un error ya que debemos pasar ese “mal cambio” que hicimos a stage, podemos usar git stash para regresar el cambio anterior que hicimos. 

git stash es típico cuando estamos cambios que no merecen una rama o no merecen un rebase si no simplemente estamos probando algo y luego quieres volver rápidamente a tu versión anterior la cual es la correcta. 

 

Stashed: 

El stashed nos sirve para guardar cambios para después, Es una lista de estados que nos guarda algunos cambios que hicimos en Staging para poder cambiar de rama sin perder el trabajo que todavía no guardamos en un commit 

Ésto es especialmente útil porque hay veces que no se permite cambiar de rama, ésto porque porque tenemos cambios sin guardar, no siempre es un cambio lo suficientemente bueno como para hacer un commit, pero no queremos perder ese código en el que estuvimos trabajando. 

El stashed nos permite cambiar de ramas, hacer cambios, trabajar en otras cosas y, más adelante, retomar el trabajo con los archivos que teníamos en Staging pero que podemos recuperar ya que los guardamos en el Stash. 

git stash 

El comando git stash guarda el trabajo actual del Staging en una lista diseñada para ser temporal llamada Stash, para que pueda ser recuperado en el futuro. 

Para agregar los cambios al stash se utiliza el comando: 

git stash 

Podemos poner un mensaje en el stash, para asi diferenciarlos en git stash list por si tenemos varios elementos en el stash. Ésto con: 

git stash save "mensaje identificador del elemento del stashed" 

Obtener elelmentos del stash 

El stashed se comporta como una Stack de datos comportándose de manera tipo LIFO (del inglés Last In, First Out, «último en entrar, primero en salir»), así podemos acceder al método pop. 

El método pop recuperará y sacará de la lista el último estado del stashed y lo insertará en el staging area, por lo que es importante saber en qué branch te encuentras para poder recuperarlo, ya que el stash será agnóstico a la rama o estado en el que te encuentres, siempre recuperará los cambios que hiciste en el lugar que lo llamas. 

Para recuperar los últimos cambios desde el stash a tu staging area utiliza el comando: 

git stash pop 

Para aplicar los cambios de un stash específico y eliminarlo del stash: 

git stash pop stash@{<num_stash>} 

Para retomar los cambios de una posición específica del Stash puedes utilizar el comando: 

git stash apply stash@{<num_stash>} 

Donde el <num_stash> lo obtienes desden el git stash list 

Listado de elementos en el stash 

Para ver la lista de cambios guardados en Stash y así poder recuperarlos o hacer algo con ellos podemos utilizar el comando: 

git stash list 

Retomar los cambios de una posición específica del Stash || Aplica los cambios de un stash específico 

Crear una rama con el stash 

Para crear una rama y aplicar el stash mas reciente podemos utilizar el comando 

git stash branch <nombre_de_la_rama> 

Si deseas crear una rama y aplicar un stash específico (obtenido desde git stash list) puedes utilizar el comando: 

git stash branch nombre_de_rama stash@{<num_stash>} 

Al utilizar estos comandos crearás una rama con el nombre <nombre_de_la_rama>, te pasarás a ella y tendrás el stash especificado en tu staging area. 

Eliminar elementos del stash 

Para eliminar los cambios más recientes dentro del stash (el elemento 0), podemos utilizar el comando: 

git stash drop 

Pero si en cambio conoces el índice del stash que quieres borrar (mediante git stash list) puedes utilizar el comando: 

git stash drop stash@{<num_stash>} 

Donde el <num_stash> es el índice del cambio guardado. 

Si en cambio deseas eliminar todos los elementos del stash, puedes utilizar: 

git stash clear 

Consideraciones: 

El cambio más reciente (al crear un stash) SIEMPRE recibe el valor 0 y los que estaban antes aumentan su valor. 

Al crear un stash tomará los archivos que han sido modificados y eliminados. Para que tome un archivo creado es necesario agregarlo al Staging Area con git add [nombre_archivo] con la intención de que git tenga un seguimiento de ese archivo, o también utilizando el comando git stash -u (que guardará en el stash los archivos que no estén en el staging). 

Al aplicar un stash este no se elimina, es buena práctica eliminarlo. 

##  Git Clean: limpiar tu proyecto de archivos no deseados 
A veces creamos archivos cuando estamos realizando nuestro proyecto que realmente no forman parte de nuestro directorio de trabajo, que no se deberían agregar y lo sabemos. 

Para saber qué archivos vamos a borrar tecleamos git clean --dry-run 

Para borrar todos los archivos listados (que no son carpetas) tecleamos git clean -f 

 

El parametro -d ayuda con el borrado de carpetas untracked. Por ejemplo: git clean -df hubiera borrado la carpeta “css - copia” 

 

Quiero dejar bien en claro ¿cuando funciona git clean? 
Git clean solo detecta archivos nuevos, no es necesario que se trate de una copia de otro archivo, suficiente con que sea un archivo nuevo que ustedes hayan creado. 

**git clean --dry-run ** 
Simula la eliminación de archivos, ¿tienes dudas de que archivos eliminará?, ejecuta git clean --dry-run, y cuando estes seguro de que desea eliminarlos, ejecutas git clean -f 

Archivos que se hayan modificado o editados git clean no interviene aquí. 

## Git cherry-pick: traer commits viejos al head de un branch 
 Existe un mundo alternativo en el cual vamos avanzando en una rama pero necesitamos en master uno de esos avances de la rama, para eso utilizamos el comando git cherry-pick IDCommit. 

cherry-pick es una mala práctica porque significa que estamos reconstruyendo la historia, usa cherry-pick con sabiduría. Si no sabes lo que estás haciendo ten mucho cuidado. 

 

Resumen de la clase: 

Crear una nueva rama y pasarse para esa rama. 

Realizar los cambios en el código y realizar todos los commits necesarios. 

Antes de ejecutar el comando git cherry-pick, se debe anotar el id del commit que queremos traer al master. 

Para ello vamos a la rama donde esta el commit requerido (git checkout nombre_rama), ejecutamos el comando git log --oneline, 
copiamos el id del commit y nos regresamos a la rama master (git 
checkout master). 

En la rama master, ejecutamos: git cherry-pick id_commit. 

Git agregará al master el código requerido del commit indicado. 

Después, de ser necesario, se ejecutan los comandos git pull 
origin master y git push origin master para subir los cambios al 
repositorio de github en la nube. 

Si se necesitan traer todos los cambios de la rama de donde tomé el commit, se ejecuta desde master, git merge nombre_rama. 

De haber conflictos al hacer merge, se resuelven dejando las líneas de código necesarias o utilizando las opciones de Vscode. 

## Reconstruir commits en Git con amend Reconstruir commits en Git con amend 

A veces hacemos un commit, pero resulta que no queríamos mandarlo porque faltaba algo más. Utilizamos git commit --amend, amend en inglés es remendar y lo que hará es que los cambios que hicimos nos los agregará al commit anterior

el commit --amend es muy util, pero hay que tener cuidado en algunos casos, como en el caso de que el commit que quieras enmendar lo hayas pusheado al repositorio remoto, entonces quieras enmendar un commit que esta en remoto. 

Así como en el caso de cherry-pick y rebase, hay que usarlo con cuidado porque modificará la historia de tu repositorio. 

Digamos que haces un cambio al archivo a.txt y haces un commit. 

Luego subes ese commit al repositorio haciendo push. 

Pero se te olvido agregar cambios a ese commit y quieres enmendarlo. 

Haces un git --amend y en la historia de tu repositorio local, pareciera que no ha pasado nada: enmendaste tu commit. 

Pero resulta que en el repositorio remoto eso no ha ocurrido, ese git --amend no tuvo lugar en el repositorio remoto, y al hacer git status te mostrará un error así: 

Your branch and 'origin/master' have diverged,and have 1 and 1 different commits each, respectively.  (use "git pull" to merge the remote branch into yours) 

y al momento de hacer push para sobreescribirlo, te aparecerá este error: 

! [rejected]        master -> master (non-fast-forward)error: failed to push some refs to 'git@github.com:luisxxor/hyperblog-1.git'hint: Updates were rejected because the tip of your current branch is behindhint: its remote counterpart. Integrate the remote changes (e.g.hint: 'git pull ...') before pushing again.hint: See the 'Note about fast-forwards' in 'git push --help' for details. 

Y tendrás que hacer git pull para mergear los cambios de tu repositorio remoto y finalmente hacer push. Es decir, se puede hacer, pero sería contraproducente, porque la idea del amend era enmendar un sólo commit y no generar commits adicionales, pero el resultado de continuar haciendolo en éste caso es que tienes: 

El primer commit 

El commit enmendado 

Y el commit del merge 

tl:dr 

Es una mala práctica enmendar un commit que ya ha sido pusheado al repositorio remoto. 


## Git Reset y Reflog: úsese en caso de emergencia 
Git branch –D <nombre de la rama> BORRA LA RAMA 

 

¿Qué pasa cuando todo se rompe y no sabemos qué está pasando? Con 

$ git reset <HashDelHEAD>(osea el nombre del head,el que esta en amarillo que vemos  con git reflog) nos devolveremos al estado en que el proyecto funcionaba. 

 

git reset --soft HashDelHEAD te mantiene lo que tengas en staging ahí. 

git reset --hard HashDelHEAD resetea absolutamente todo incluyendo lo que tengas en staging. 

git reset es una mala práctica, no deberías usarlo en ningún momento; debe ser nuestro último recurso. 

 

 

 

Git nunca olvida,  

$git reflog 

Git guarda todos los cambios aunque decidas borrarlos, al borrar un cambio lo que estás haciendo sólo es actualizar la punta del branch, para gestionar éstas puntas existe un mecanismo llamado registros de referencia o reflogs. 
. 
La gestión de estos cambios es mediante los hash’es de referencia (o ref) que son apuntadores a los commits. 
. 
Los recoges registran cuándo se actualizaron las referencias de Git en el repositorio local (sólo en el local), por lo que si deseas ver cómo has modificado la historia puedes utilizar el comando: 

git reflog 

Muchos comandos de Git aceptan un parámetro para especificar una referencia o “ref”, que es un puntero a una confirmación sobre todo los comandos: 

git checkout Puedes moverte sin realizar ningún cambio al commit exacto de la ref 

git checkout eff544f 

git reset: Hará que el último commit sea el pasado por la ref, usar este comando sólo si sabes exactamente qué estás haciendo 

git reset --hard eff544f  

 Perderá todo lo que se encuentra en staging y en el Working directory y se moverá el head al commit eff544f 

git reset --soft eff544f  

Te recuperará todos los cambios que tengas diferentes al commit eff544f, los agregará al staging area y moverá el head al commit eff544f 

git merge: Puedes hacer merge de un commit en específico, funciona igual que con una branch, pero te hace el merge del estado específico del commit mandado 

git checkout master 

git merge eff544f # Fusionará en un nuevo commit la historia de master con el momento específico en el que vive eff544f 

##  Buscar en archivos y commits de Git con Grep y log 

A medida que nuestro proyecto se hace grande vamos a querer buscar ciertas cosas. 

Por ejemplo: ¿cuántas veces en nuestro proyecto utilizamos la palabra color? 

Grep para los archivos 

Log para los commits 

 

Para buscar utilizamos el comando git grep color y nos buscará en todo el proyecto los archivos en donde está la palabra color. 

Con `git grep -n color` nos saldrá un output el cual nos dirá en qué línea está lo que estamos buscando. 

Con `git grep -c color` nos saldrá un output el cual nos dirá cuántas veces se repite esa palabra y en qué archivo. 

Si queremos buscar cuántas veces utilizamos un atributo de HTML lo hacemos con` git grep -c "<p>". `


`git grep color` use la palabra color 
`git grep la` donde use la palabra la 
`git grep -n color` en que lineas use la palabra color 
`git grep -n platzi`  en que lineas use la palabra platzi 
`git grep -c la`  cuantas veces use la palabra la 
`git grep -c paltzi`  cuantas veces use la palabra platzi
`git grep -c “<p>”` cuantas veces use la etiqueta <p>
`git log-S “cabecera”` cuantas veces use la palabra cabecera en 
todos los commits. 

`grep` para los archivos 
`log`  para los commits. 

##  Comandos y recursos colaborativos en Git y GitHub 
 

NOTAS CLASE: 

`git shortlog` Ver cuantos commits a hecho los miembros del equipo 

`git shortlog -sn` Las personas que han hecho ciertos commits 

`git shortlog -sn --all` Todos los commits (también los borrados) 

`git shortlog -sn --all --no-merges` muestra las estadisticas de los comigs del repositorio donde estoy 

`git config --global alias.stats “shortlog -sn --all --no-merges”`configura el comando “shortlog -sn --all --no-merges” en un Alias en las configuraciones globales de git del pc 

`git blame -c blogpost.html` Muestra quien ha hecho cambios en dicho archivo identado 

`git blame --help` Muestra en el navegador el uso del comando 

`git blame archivo -L 35, 60 -c`: Muestra quien escribio el codigo con informacion de la linea 35 a la 60, EJ: git blame css/estilos.css -L 35, 60 -c 

`git branch -r` Muestra las Ramas remotas de GitHub 

`git branch -a` Muestra todas las Ramas del repo y remotas de GitHub 

 

EN GITHUB tenemos un panel llamado insight que nos muestra muchas estadisticas 

