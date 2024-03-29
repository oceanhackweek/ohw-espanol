# Introducción a R
**Autores**:Hector Villalobos y Marian Peña

R es un poderoso y flexible lenguaje de programacion para el analisis de datos y
la elaboracion de gráficas con calidad de publicacion.
Este curso introductorio tiene por objeto mostrar el uso basico de R desde un enfoque practico



## Obtener e Instalar R y Rstudio

La version mas reciente de R puede obtenerse del sitio web
oficial: [The R Project for Statistical Computing](http://www.r-project.org/), el cual contiene las ligas hacia diferentes servidores "espejo" distribuidos en todo el mundo. En estos servidores se puede descargar el codigo fuente de R o una version precompilada para la plataforma de nuestro interes (Linux, Mac OS X, Windows).
En este documento comentaremos la instalacion y el uso de R bajo Windows 10

* Select setup language: Se recomienda seleccionar "English". La razon de esto es
  que aunque el menu de R y algunos mensajes están traducidos en varios idiomas (entre ellos el español el sistema de ayuda y muchos recursos en Internet solo estan disponibles en ingles, por lo que una busqueda en este idioma producir mas resultados que en español o cualquier otro idioma.

* Welcome screen: "Next" para continuar

* License: "Next" para continuar

* Select Destination Location: Se recomienda instalar en el directorio por defecto.
![cdf3c335d5b3e0235da06be727746d85.png](imagenes/cdf3c335d5b3e0235da06be727746d85.png)
* Select Components: "Next" para continuar.

* Startup options: Seleccionar "No (accept defaults)". Si se elige "Yes (customized
  startup)" el programa de instalacion pregunta si se desea utilizar el programa en
  modo MDI (ver Figura 1) o SDI (ver Figura 2); si se prefiere la ayuda en modo de
  texto o html y el tipo de acceso a Internet (estandar o Internet2).

* Select Start Menu Folder : "Next" para continuar

* Select Additional Tasks: "Next" para continuar

Una manera de facilitar la creacion y manipulacion de scripts en R es por medio de
un editor que resalte la sintaxis con diferentes colores, y al mismo tiempo que pueda interactuar con R enviando codigo a la consola para su ejecucion. Existen diferentes opciones como EMACS, JGR, R Commander, Sciviews y Tinn-R. La pagina web: http://www.sciviews.org/_rgui/ contiene ligas para estos y otros editores. Sin embargo dada la facilidad de instalacion, de uso y sus caracteristicas, se recomienda el uso de RStudio el cual puede descargarse desde la siguiente pagina: http://www.rstudio.org. RStudio es lo que se conoce como un Ambiente de Desarrollo Integrado (IDE, por sus siglas en ingles) que bajo una misma ventana agrupa el editor de scripts, la consola de R, el workspace con los objetos creados, el historico de los comandos utilizados, la ayuda, las gráficas, paquetes instalados y archivos en el directorio de trabajo.

* Welcome to the RStudio Setup Wizard: Pantalla de bienvenida del instalador, seleccionar "Next" para continuar
* Choose Install Location: Seleccionar carpeta de instalacion, puede aceptarse la propuesta por el programa o elegir otra. "Next" para continuar
* Choose Start Menu Folder : Carpeta para crear atajo para ejecutar el programa, la opcion por defecto esta bien. Pulsar "Install" para iniciar la instalacion.
* Completing the RStudio Setup Wizard: Seleccionar "Finish"

## Instalación de paquetes adicionales

La instalación de packages es bastante simple, se puede hacer a partir del menú o
de la consola. Los paquetes se encuentran en un servidor de Internet denominado Comprehensive R Archive Network (CRAN) y sus espejos distribuidos en diferentes paises. Usualmente, cuando se cuenta con una conexión a Internet adecuada, es preferible instalar desde estos servidores. Es importante se~nalar que los usuarios de Windows Vista y Windows 7 deben abrir una sesion de R como administrador, lo cual se logra haciendo click con el botón derecho del mouse sobre el icono del programa y después seleccionando "Ejecutar como administrador" en el menú desplegado.
Una vez dentro de R, desde el menú seleccionamos la opción: Packages/Install pac-
kage(s). . . Después será necesario elegir un servidor o\espejo"y a continuación el package de nuestro interés en la lista desplegada. Desde la consola podemos usar los comandos: chooseCRANmirror(), que nos permite seleccionar el servidor, e install.packages() indicando el o los packages deseados.
Pongamos un ejemplo:
```r
> chooseCRANmirror()
> install.packages("TeachingDemos", dependencies = TRUE)
```
El argumento dependencies = TRUE instruye a R a descargar e instalar otros paquetes requeridos para el funciónamiento del paquete TeachingDemos. Como puede apreciarse, durante el proceso la consola de R despliega una serie de mensajes, en particular el nombre y tamaño de los archivos descargados, que están en forma de archivos comprimidos (en formato"*.zip" para la versión de Windows) y que son automáticamente desempacados por R.
En la memoria USB proporcionada se incluyen algunos de los paquetes disponibles a la fecha en el directorio Software/R/contrib_packages. Estos corresponden a las versiones binarias para Windows y se instalan de manera similar al caso anterior. Desde el menú, la opcion corresponde a Packages/Install package(s) from local zip files. . . , mientras que desde la consola la instrucción completa requiere indicar la ruta en donde se ubican los archivos *.zip. La ventaja de usar la consola en lugar del menú radica en que las dependencias también son tomadas en cuenta. Supongamos por ejemplo que \G" es la letra asignada por Windows a nuestra memoria, entonces la sintaxis sería:
> install.packages("TeachingDemos", repos = NULL,
+ contriburl = "file:///G:/Software/R/contrib_packages",
+ dependencies = TRUE)
Una vez instalado un paquete es necesario cargarlo en la sesion para que esté disponible para usarlo, en el caso de nuestro ejemplo:
> library(TeachingDemos)
Podemos ahora ver la ayuda de este paquete y ensayar los ejemplos de alguna función, por ejemplo my.symbols():
> ?TeachingDemos
> example(my.symbols)
Cuando ya no necesitamos el package podemos desactivarlo usando el comando:
> detach("package:TeachingDemos")
En el sitio de R se puede consultar la lista de packages disponibles con una breve
descripción de los mismos. Por lo general, se recomienda buscar el package útil para
resolver un problema específico, en lugar de intentar instalar y explorar todos los paquetes
disponibles.


## Operaciones simples

Con R podemos realizar cualquier operación aritmética usando los operadores habituales:

```r
    > 3+6
     [1] 9
    > 8*9
     [1] 72
    > 10-8
     [1] 2
    > 5/2
     [1] 2.5
    > 4^2
     [1] 16
    > log(100)
     [1] 4.60517
    > log10(100)
     [1] 2
    > exp(2)
     [1] 7.389056
    > sqrt(16)
     [1] 4
    > w <- 1:6
```
<details>
<summary>Ejercicio: calcula el seno y coseno de 90. Dale click para ver la solución</summary>
 ```r
 > sin(90)
 [1] 0.8939967
> cos(90)
 [1] -0.4480736
```
</details>

Para verificar el contenido de w simplemente escribimos su nombre:

```r
  > w
   [1] 1 2 3 4 5 6
  > seq(1, 6, 0.5)
   [1] 1.0 1.5 2.0 2.5 3.0 3.5 4.0 4.5 5.0 5.5 6.0
  > x <- c("a", "a", "a", "b", "b", "b")
  > x
   [1] "a" "a" "a" "b" "b" "b"
```

En este ejemplo, usamos la instruccion combine c() para combinar las letras en un
solo objeto. De manera similar, el vector de nuestro primer ejemplo puede crearse tambien usando la instrucción: w <- c(1, 2, 3, 4, 5, 6). En el caso de la creacion del vector x usamos comillas para indicar que se trata de texto y no de objetos ya existentes. Imaginemos que en algun momento de la sesión se hicieron las asignaciones a <- 2.5 y b <- 3.6 y después lo olvidamos. Si en un momento posterior de la misma sesion deseáramos crear el vector de caracteres del ejemplo anterior pero olvidasemos usar las comillas, el resultado sera totalmente diferente:

```r
  > xx <- c(a, a, a, b, b, b)
  > xx
  [1] 2.5 2.5 2.5 3.6 3.6 3.6
```

Ademas de los vectores numericos y de caracteres que acabamos de ejemplicar, tambien hay vectores logicos que resultan de la evaluación de expresiones:

```r
  > ww <- w > 4
  > ww
  [1] FALSE FALSE FALSE FALSE TRUE TRUE
```

Este ultimo tipo de vector es muy útil para indexar otros vectores, pues nos permite, por ejemplo, extraer elementos específicos que cumplen con cierta condición (en este caso, aquellos que son mayores que 4):

```r
  > w[ww]
  [1] 5 6
```

Matrices
El siguiente tipo de objeto que nos interesa es la matriz:

```r
  > y <- matrix(1:20, ncol = 4)
  > y
   [,1] [,2] [,3] [,4]
   [1,] 1 6 11 16
   [2,] 2 7 12 17
   [3,] 3 8 13 18
   [4,] 4 9 14 19
   [5,] 5 10 15 20
```

Notese como hemos indicado el número de columnas que querríamos con el argumento ncol. Tambien podemos precisar como queremos que los datos sean ordenados en la matriz al incluir el argumento byrow, que instruye a la función matrix() a llenar primero los renglones:

```r
  > matrix(1:20, byrow = TRUE, ncol = 4)
   [,1] [,2] [,3] [,4]
   [1,] 1 2 3 4
   [2,] 5 6 7 8
   [3,] 9 10 11 12
   [4,] 13 14 15 16
   [5,] 17 18 19 20
```

Incluso podemos asignar nombres a las columnas y renglones de la matriz, para lo cual añadimos el argumento dimnames:

```r
  > y <- matrix(1:20, byrow = TRUE, ncol = 4, dimnames = list(paste("r", 1:5, sep = ""), paste("c", 1:4, sep = ".")))

  > y
  > c.1 c.2 c.3 c.4
  > r1 1 2 3 4
  > r2 5 6 7 8
  > r3 9 10 11 12
  > r4 13 14 15 16
  > r5 17 18 19 20    
```

El valor de dimnames en la función anterior utiliza otras funciónes (list() y paste()) con sus respectivos argumentos. Para comprender su propósito podemos evaluarlas de  manera independiente.  Data frames  Una característica que comparten los vectores y las matrices es que pueden contener un solo tipo de valores (numéricos, caracteres o lógicos). En muchas ocasiones, nuestros datos contienen una mezcla de variables numericas y factoriales. Esta información puede manejarse por medio de un data frame, muy similar a la matriz pero que puede contener mas de un tipo de datos:

```r
  > z <- data.frame(x, w)
  > z
   x w
   1 a 1
   2 a 2
   3 a 3
   4 b 4
   5 b 5
   6 b 6
```

Es importante mencionar que R es sensible al uso de mayúsculas/minúsculas, de tal
forma que nuestros objetos z y Z son diferentes.

### Indexar objetos

Podemos tener acceso a elementos particulares de un objeto usando índices. Por ejemplo, si nos interesan los primeros tres elementos del vector x:

```r
  > x[1:3]
   [1] "a" "a" "a"
```

En el caso de matrices y data frames debemos indicar tambien la columna, por ejemplo, para extraer de la matriz y los elementos correspondientes a los renglones 4{5 y a las columnas 3 a 4 escribimos:

```r
  > y[4:5, 3:4]
   c.3 c.4
   r4 15 16
   r5 19 20
```
<details>
<summary>Ejercicio: selecciona la columna 2 de y completa. Dale click para ver la solución</summary>
 ```r
 > y[, 2]
   r1 r2 r3 r4 r5
   2 6 10 14 18
```
</details>


 en el caso de un data frame ademas podemos acceder a las columnas mediante el nombre del data frame seguido del símbolo "$" y del nombre de la columna:

```r
  > z$x
   [1] a a a b b b
   Levels: a b
  > z$w
   [1] 1 2 3 4 5 6
```

por último, en el caso de las listas procedemos de manera similar:

```r
  > Z$M.y
   c.1 c.2 c.3 c.4
   r1 0.000000 0.6931472 1.098612 1.386294
   r2 1.609438 1.7917595 1.945910 2.079442
   r3 2.197225 2.3025851 2.397895 2.484907
   r4 2.564949 2.6390573 2.708050 2.772589
   r5 2.833213 2.8903718 2.944439 2.995732
```

para extraer solo los renglones tercero y cuarto de la segunda columna de la matriz
 anterior:

```r
  > Z$M.y[3:4, 2]
   r3 r4
   2.302585 2.639057
```

o de manera alternativa:

```r
  > Z[[3]][3:4, 2]
   r3 r4
   2.302585 2.639057
```

Atributos de los objetos 
Una vez que los objetos han sido creados podemos saber a que clase pertenecen inspeccionándolos o de manera mas precisa usando la función class(). Veamos lo reportado por esta función para los objetos creados hasta este momento:

```r
  > class(w); class(x); class(ww); class(y); class(z); class(Z)
   [1] "integer"
   [1] "character"
   [1] "logical"
   [1] "matrix"
   [1] "data.frame"
   [1] "list"
```

Los objetos en R tienen atributos, por ejemplo el modo en que estan almacenados
(mode(), "numeric", "character", "logical", . . . ) y su longitud (length()), que corresponde al número total de elementos de un vector o matriz, mientras que en el caso de un data frame es el número de columnas, y en una lista el número de elementos de esta. Otros atributos de un objeto corresponden a sus dimensiones y nombres de las columnas y renglones (o de los elementos de la lista). La función attributes() puede ser útil para conocer algunos de estos atributos, aunque str() nos proporciona mayores detalles sobre la estructura del objeto.

```r
  > attributes(w); str(w)
   NULL
   int [1:6] 1 2 3 4 5 6
   attributes(Z); str(Z)
   $names
   [1] "V.w" "V.x" "M.y"
   List of 3
   $ V.w: num [1:6] 2 4 6 8 10 12
   $ V.x: chr [1:6] "a" "a" "a" "b" ...
   $ M.y: num [1:5, 1:4] 0 1.61 2.2 2.56 2.83 ...
   ..- attr(*, "dimnames")=List of 2
   .. ..$ : chr [1:5] "r1" "r2" "r3" "r4" ...
   .. ..$ : chr [1:4] "c.1" "c.2" "c.3" "c.4"
```

Ahora utilicemos algunos de los objetos creados previamente para ilustrar algunas
operaciones sencillas. Por ejemplo, si queremos calcular la raiz cuadrada de los elementos del vector w usamos la función sqrt():

```r
  > sqrt(w)
  [1] 1.000000 1.414214 1.732051 2.000000 2.236068 2.449490
```

La sintaxis en el caso de una matriz es idéntica:

```r
  > sqrt(y)
   c.1 c.2 c.3 c.4
   r1 1.000000 1.414214 1.732051 2.000000
   r2 2.236068 2.449490 2.645751 2.828427
   r3 3.000000 3.162278 3.316625 3.464102
   r4 3.605551 3.741657 3.872983 4.000000
   r5 4.123106 4.242641 4.358899 4.472136
```

La diferencia con una hoja de calculo, donde la formula se tiene que aplicar a cada elemento {ya sea escribiéndola o copiándola, es evidente. También podemos aplicar una operación de este tipo a una sola columna de una matriz o de un data frame:

```r
  sqrt(z$w)
  > [1] 1.000000 1.414214 1.732051 2.000000 2.236068 2.449490
```

En este caso especificamos que nos interesa la columna w del data frame z. Alternativamente, podemos emplear la notación: sqrt(z[ , 2]). Para las operaciones con vectores y matrices, es importante la notación empleada para obtener el resultado deseado:

```r
  > A <- matrix(c(1,2,3,4), ncol=2)
  > b <- c(2,3)
```

La operación A * b ejecuta la multiplicación elemento por elemento, y es equivalente

```r
  > a b * A:

  A * b
  [,1] [,2] [1] [,1] [,2]
  [1,] 1 3 2 = [1,] 1*2 3*2
  [2,] 2 4 3 [2,] 2*3 4*3

  > A * b
   [,1] [,2]
   [1,] 2 6
   [2,] 6 12
```

> En cambio, el producto matricial

```r
  > A %*% b
   [,1] [,2] [1] [,1]
   [1,] 1 3 2 = [1,] 1*2 + 3*3
   [2,] 2 4 3 [2,] 2*2 + 4*3
```

se obtiene mediante:

```r
  > A %*% b
   [,1]
   [1,] 11
   [2,] 16
```

La transposición de una matriz se obtiene mediante:

```r
  > t(A)
   [,1] [,2]
   [1,] 1 2
   [2,] 3 4
```

Y la inversa

```r
  > solve(A)
   [,1][,2]
   [1,] -2 1.5
   [2,] 1 -0.5
```

## Gráficas simples

Para mostrar la creación de gráficos sencillos vamos a crear un \data frame" con dos
columnas, la primera que denominaremos \grupo", y la segunda \var1". Este ejemplo
ilustra también el uso de la función rnorm(), que produce números aleatorios distribuidos
normalmente.

```r
> z <- data.frame("grupo" = sort(rep(c("a", "b"), 8)), "var1" = rnorm(16))
 z
 grupo var1
 1 a -0.62645381
 2 a 0.18364332
 3 a -0.83562861
 4 a 1.59528080
 5 a 0.32950777
 6 a -0.82046838
 7 a 0.48742905
 8 a 0.73832471
 9 b 0.57578135
 10 b -0.30538839
 11 b 1.51178117
 12 b 0.38984324
 13 b -0.62124058
 14 b -2.21469989
 15 b 1.12493092
 16 b -0.04493361
```

 La función plot() produce una gráfica de dispersion:

```r
 > plot(z$var1)
```
![](imagenes/dcb5962226ac6bfe278bc95860218862.png)

Si queremos un histograma usamos la función hist():

```r
> hist(z$var1)
```

![](imagenes/e0d1208638b1f9f96feb5262e2b9bc4a.png)

Ahora intentemos hacer una gráfica de cajas y bigotes de var1 con respecto al grupo,
añadiendo titulo y etiquetas a los ejes x y y:

 ```r
> boxplot(var1 ~ grupo, data=z, main="boxplot de prueba", xlab = "grupo",
+ ylab = "variable 1")
```

![](imagenes/641086fe14fa3533d3fe6f4ef035ee57.png)

Para explorar otras opciones gráficas, añadiremos una segunda columna a z, y despues ordenaremos el data frame con respecto a var1. A continuación vamos a crear en una sola ventana cuatro graficas de las mismas variables usando diferentes opciones (solo puntos, solo líneas y ambos):

 ```r
> z$var2 <- (z$var1)^2
> z <- z[order(z$var1), ]
> par(mfrow=c(2,2))
> plot(z$var1, z$var2, type="p", main="solo puntos")
> plot(z$var1, z$var2, type="l", main="solo líneas")
> plot(z$var1, z$var2, type="b", main="puntos y líneas")
> plot(z$var1, z$var2, type="o", main="puntos y líneas\n sobrepuestos")
 ```
![](imagenes/14f2f27bfeff629633e861b5546e3cac.png)

Se recomienda familiarizarse con la función par(), que explica los parámetros graficos que pueden ser modificados por el usuario, por ejemplo el tamaño de la fuente, símbolos, colores, etc.

Para saber que objetos tenemos disponibles, podemos enlistarlos usando los comandos:


```r
o bien:
> ls()
[1] "a" "A" "b" "w" "ww" "x" "xx" "y" "z" "Z"
```

Si ahora queremos eliminar permanentemente algún objeto en particular, digamos la
matriz y usamos:
```r
> rm(y)
> ls()
```
explicar. Para ejemplificar esto, creemos un objeto al que
llamaremos .invisible:
```r
> .invisible <- rnorm(20)
```
ahora ejecutemos los comandos siguientes:
```r
> ls()
character(0)
```
Como se aprecia, la función ls() no despliega los objetos ocultos. Para deplegarlos
requerimos a~nadir el argumento all = TRUE a dicha función:
```r
> ls(all=TRUE)
[1] ".invisible" ".Random.seed"
```
el objeto .Random.seed fue creado por la función rnorm() usada previamente. Veamos
ahora lo que sucede al intentar borrar a todos los objetos como se hizo anteriormente:
```r
> rm(list=ls())
> ls(all=TRUE)
[1] ".invisible" ".Random.seed"
```
Como podemos ver, los dos objetos ocultos siguen ahí. La notación correcta para
borrarlos sera la siguiente:
```r
> rm(list=ls(all=TRUE))
> ls(all=TRUE)
character(0)
```


## Ayuda de funciónes y paquetes

Podemos acceder al sistema de ayuda de R mediante \?" seguido del nombre de la
función que nos interesa o con el comando help(). Probemos esto con algunas de las
funciónes que hemos utilizado hasta el momento:
```r
> ?ls
> help("rnorm")
> help(par)
> help.search("linear models")
```

<details>
<summary>Ejercicio: busca ayuda sobre la función 'hist'. Dale click para ver la solución</summary>
 ```r
> help("hist")
```
</details>

A partir del menu Help tambien podemos acceder a la ayuda compilada en html, a
los diferentes manuales de R en formato pdf que se crearon durante la instalación, a los archivos en línea de la lista de correo de ayuda de R, etc.

## Importar datos externos
En los primeros ejemplos vimos la manera de introducir datos y crear objetos a partir
del teclado, pero lo mas usual es que tengamos nuestra informacion en alguna hoja de calculo o base de datos. Desde el portapapeles Cuando la cantidad de datos es peque~na y su fomato sencillo, podemos pasarlos directamente del archivo a la consola de R por medio del portapapeles. Para ello primero copiamos los datos al portapapeles y despues escribimos en la consola la instruccion:
```r
> read.delim("clipboard")
```
Mediante read.table()
Cuando el tamaño de los datos es importante, es preferible usar otro metodo para
leerlos en R. Los archivos de Excel y de Access pueden ser importados mediante funciónes especiales, sin embargo lo mas sencillo es exportar nuestros datos en formato ascii, puesto que todas las hojas de calculo y manejadores de bases de datos tienen esta capacidad. Se sugiere salvar los datos en un archivo de texto, con nombres de columnas que empiecen por una letra y sin espacios (si se desean nombres compuestos se puede usar un guion bajo) y usando tabuladores como separadores de columnas (aunque R puede importar datos sin nombres de columnas y separados por espacios, comas, etc.). Uno de los comandos de importacion de datos externos que mas utilizaremos es read.table() y su sintaxis es la siguiente:
```r
> x <- read.table("ruta/archivo", header, sep)
```
Del lado izquierdo del assignment, x corresponde al objeto que contendra los datos
del archivo importado. Del lado derecho, ruta se refiere a un directorio, por ejemplo
"G:/datos" y archivo al nombre {incluyendo la extension (\.txt", \.dat"){ del archivo
externo que contiene los datos. Los argumentos header y sep indican si el archivo incluye (TRUE) o no (FALSE) nombres de columnas y el separador de las mismas. Este ultimo puede ser un tabulador ("\t"), un espacio (" "), una coma (",") o punto y coma (";"). Como primer ejemplo importaremos los datos contenidos en archivo_00.txt, localizado en el directorio /Datos/importar de la memoria USB. Una rapida inspeccion de este archivo de texto nos permite ver que se trata de dos columnas numericas cuyos nombres son tmin y tmax. Con una observacion cuidadosa del archivo ademas podemos descubrir que las columnas estan separadas por tabuladores y no por espacios. 
```r
> a00 <- read.table("G:/Datos/importar/archivo_00.txt", header=TRUE, sep="\t")
```
Una vez los datos importados, estaran disponibles para ser analizados dentro de R.
Es importante se~nalar que el archivo original permanece sin cambios y que los datos solo estan disponibles mientras la sesion actual de R se mantenga abierta. Si en una sesion posterior deseamos usar los mismos datos debemos importarlos nuevamente, a menos que hayamos guardado el workspace y se haya restaurado en la nueva sesion. Una sesion formal de R requiere que denamos nuestro directorio de trabajo (\working directory", wd). Eso simplificará mucho la importacion y exportacion de datos y figuras, ademas de que nos ayudara a mantener organizado nuestro trabajo. Para conocer el directorio de trabajo actual usamos el comando getwd(), mientras que definimos uno diferente mediante setwd(), por ejemplo:
```r
> setwd('G:/Datos')
```
De esta manera, la sintaxis del ejemplo anterior se puede simplificar:
```r
> a00 <- read.table("./importar/archivo_00.txt", header=TRUE, sep="\t")
```
El "." antes de la diagonal inicial sirve para indicar que importar es un subdirectorio
de Datos. 

**Desde archivos de Excel y Access **

Para importar archivos creados con estas aplicaciones, es necesario el uso de paquetes adicionales. Uno de los mas sencillos de instalar y uilizar es RODBC. La secuencia completa de pasos para importar un archivo de Excel, requiere (1) cargar el paquete, (2) establecer una\conexion"al archivo, (3) leer los nombres de las hojas del archivo Excel y (4) importar la hoja que nos interesa. La sintaxis es la siguiente:
```r
> library(RODBC)
> con <- odbcConnectExcel("./importar/archivo_04.xls")
> sqlTables(con)
> a04pA <- sqlFetch(con, "A_1962")
```
En este ejemplo, con es unicamente la conexion al archivo archivo_04.xls y es a
traves de ella que consultamos los nombres de las hojas Excel (sqlTables(con)) e importamos aquella que nos interesa (sqlFetch(con, "A_1962")). Adicionalmente, si ya no se van a importar mas datos se cierra la conexion y se quita el paquete de la memoria:
```r
> closeAllConnections()
> detach("package:RODBC")
```
Otro de los paquetes que permiten leer archivos de Excel es gdata, que contiene una
función llamada read.xls() que es capaz de leer archivos de la version 2010 (*.xlsx).
Este paquete utiliza scripts escritos en Perl, por lo que ademas de instalar el paquete en R es necesario instalar una version de Perl en la computadora.
El procedimiento para importar datos de un archivo Access mediante el paquete RODBC es equivalente, solamente se requiere sustituir la función que establece la conexion al archivo correspondiente (odbcConnectAccess()). Mas detalles acerca de la importacion de estos y otros tipos de archivos se pueden consultar en el manual R Data Import/Export (R-data.pdf) que se encuentra bajo la carpeta doc/manual de la instalacion de R.

## Exportar tablas y figuras
Si deseamos exportar algunos de nuestros resultados podemos usar el comando:
```r
> write.table(taire, file = "temp_aire.txt", quote = FALSE, sep = "\t",
+ dec = ".", row.names = TRUE, col.names = TRUE)
```
Las figuras pueden salvarse en diversos formatos a partir del menú File/Save As de
la ventana grafica, o bien dentro de nuestro script podemos especificarlo:
```r
> savePlot(filename="Figura_1", type="png")
```
En ambos casos, tanto las figuras como las tablas serán guardadas en el directorio de trabajo especificado previamente.

<details>
<summary>Ejercicio: salva los datos de la variable 'taire' en un fichero de texto llamado 'taire_datos' separado por punto y coma indicando la coma como separador decimal. Dale click para ver la solución</summary>
 ```r
> write.table(taire, file = "taire_datos", quote = FALSE, sep = ";",
+ dec = ".", row.names = TRUE, col.names = TRUE)
```
</details>

## Algunos análisis estadísticos

    1. Analisis de datos temporales
    
Vamos ahora a desarrollar un ejemplo mas completo de importacion y analisis de datos utilizando el archivo cibmeteo.txt. Estos datos corresponden a lecturas de la temperatura del aire, la humedad relativa, la velocidad y direccion del viento registradas cada media hora de junio de 2006 a mayo de 2007 en la estacion meteorologica del CIBNOR en el Comitán, B.C.S. Veamos las
dimensiones de este archivo y las variables que contiene:
```r
> cibmeteo <- read.table("cibmeteo.txt", header=TRUE, sep="\t")
> dim(cibmeteo)
[1] 17364 8
> names(cibmeteo)
[1] "year" "month" "day" "hour"
[5] "temperature" "rel_hum" "wind_spd" "wind_dir"
```
Para tener una primera impresion de los datos, la función summary() produce una
serie de estadísticas descriptivas:
```r
> summary(cibmeteo)
year month day hour
Min. :2006 Min. : 1.000 Min. : 1.00 00:00 : 362
1st Qu.:2006 1st Qu.: 4.000 1st Qu.: 8.00 00:30 : 362
Median :2006 Median : 7.000 Median :16.00 01:00 : 362
Mean :2006 Mean : 6.555 Mean :15.67 01:30 : 362
3rd Qu.:2007 3rd Qu.:10.000 3rd Qu.:23.00 02:00 : 362
Max. :2007 Max. :12.000 Max. :31.00 02:30 : 362
(Other):15192
temperature rel_hum wind_spd wind_dir
Min. : 4.497 Min. : 3.681 Min. :0.000 Min. : 0.00
1st Qu.:18.668 1st Qu.: 45.568 1st Qu.:0.395 1st Qu.: 26.09
Median :24.410 Median : 64.430 Median :1.121 Median :159.60
Mean :24.132 Mean : 62.923 Mean :1.092 Mean :146.49
3rd Qu.:29.250 3rd Qu.: 82.100 3rd Qu.:1.663 3rd Qu.:226.00
Max. :39.790 Max. :100.500 Max. :6.525 Max. :360.00
```
Analicemos la temperatura del aire, haciendo un primer grafico de líneas:
```r
> plot(cibmeteo$temperature, type="l", col = "grey")
```
![](imagenes/c182a662b387e70288d8bdf76407088e.png)

Dada la frecuencia de las lecturas de temperatura, esta figura resulta poco util. Procedamos a resumir la informacion de alguna manera. Calculemos por ejemplo los extremos (mínimo y maximo) y el promedio diario de la temperatura a partir de las 48 lecturas de cada dìa. Para ello necesitamos crear un índice que identifique de manera unica a cada día, pues en el archivo el a~no, el mes y el día se encuentran en columnas separadas.
```r
> attach(cibmeteo)
> fecha <- paste(year, month, day, sep="-")
> fecha <- strptime(fecha, "%Y-%m-%d")
> fecha_txt <- as.character(fecha)
> taire <- as.data.frame(
+ cbind(tapply(temperature, list(fecha_txt), min),
+ tapply(temperature, list(fecha_txt), max),
+ tapply(temperature, list(fecha_txt), mean)))
> detach(cibmeteo)
```
La función attach() nos permite acceder a las variables contenidas en un data frame
directamente. En nuestro ejemplo, no fue necesario especificar cibmeteo$temperature para acceder a la variable temperature dentro del data frame cibmeteo. Otra función muy util en este ejemplo es tapply(), que nos permite aplicar una función (min, max, mean) a cada celda de una matriz definida por una combinacion unica de uno a varios factores (fecha_txt en nuestro ejemplo).
Bien, ahora asignemos nombres significativos a las columnas de nuestro nuevo data
frame:

```r
> colnames(taire) <- c('tmin', 'tmax', 'tavg')
```
Cuando se usa mas de un factor, la función tapply() genera por defecto una tabla.
Supongamos por ejemplo que nos interesa el promedio mensual de temperatura, el codigo sería el siguiente:
```r
> tapply(temperature, list(month, year), mean)
2006 2007
1 NA 17.05386
2 NA 18.63466
3 NA 21.39798
4 NA 21.73464
5 NA 24.13266
6 27.56828 NA
7 30.23218 NA
8 30.21151 NA
9 28.60434 NA
10 27.16089 NA
11 22.68055 NA
12 19.44399 NA
```
Una manera alternativa de obtener estos valores pero organizados de manera diferente (e.g. en un vector) sería usando la función aggregate():
```r
> aggregate(temperature, by=list(mes=month, a~no=year), mean)
mes año x
1 6 2006 27.56828
2 7 2006 30.23218
3 8 2006 30.21151
4 9 2006 28.60434
5 10 2006 27.16089
6 11 2006 22.68055
7 12 2006 19.44399
8 1 2007 17.05386
9 2 2007 18.63466
10 3 2007 21.39798
11 4 2007 21.73464
12 5 2007 24.13266
> detach(cibmeteo)
```
Regresando a los promedios diarios calculados antes, vamos a suavizar los datos con un metodo que es comunmente utilizado con este proposito: los promedios moviles. Este metodo consiste en definir una ventana de cierta longitud, por ejemplo 3 (denominado orden=3), y obtener el promedio de los valores primero al tercero, segundo al cuarto, tercero al quinto y por ultimo del valor n-2 al n. Supongase que tenemos el vector Z con 8 valores:
```r
> Z <- c(4, 8, 9, 7, 8, 9, 4, 5)
```
y deseamos calcular el promedio movil de orden 3. Los calculos a realizar serán: (4+8+9)/3; (8+9+7)/3; (9+7+8)/3; (7+8+9)/3; (8+9+4)/3; (9+4+5)/3; lo que resultaría en el vector:

```r
> Z.pmov <- c(7, 8, 8, 8, 7, 6)
```
cuya longitud (6) es menor que la del vector original (8). Entonces, si deseamos comparar graficamente ambos vectores, lo mejor es que ambos tengan la misma longitud. En este ejemplo se puede hacer agregando NA al inicio y al final de Z.pmov para centrar la serie suavizada con respecto a la serie original:
```r
> Z.pmov <- c(NA, Z.pmov, NA)
> Z.pmov
[1] NA 7 8 8 8 7 6 NA
```
Para vectores de mayor longitud estos calculos manuales resultan tediosos, por lo que vamos a crear nuestra primera función, a la que denominaremos "pmov" y que usaremos para calcular el promedio movil de las temperaturas de manera mas rapida y sencilla:
```r
> pmov <- function(x, k) {
+ n <- length(x)
+ y <- rep(NA, n)
+ for (i in k:n)
+ y[i-floor(k/2)] <- mean( x[(1+i-k):i] )
+ y
+ }
```
En esta función x es el vector a suavizar y k es el orden. "pmov" calcula primero la longitud del vector, despues genera un vector vacío (y) de la misma longitud de x y por ultimo calcula los promedios correspondientes. Apliquemos esta función a la temperatura diaria promedio con un orden igual a 15 días 

```r
> tmean.pmov <- pmov(taire$tavg, 15)
``` 

Ahora procedamos a graficar la temperatura diaria promedio sobreponiendo los promedios moviles que hemos calculado:

```r
> plot(taire$tavg, type = "o",ylab = "temperatura (°C)",xlab="día",
+ main = "Temp. diaria promedio en La Paz \n (junio 2006 a mayo 2007)",
+ lty = 3, col="grey50", lwd = 1)
> lines(tmean.pmov, lwd = 2, col = "blue")
```


![](imagenes/0990b3da0f17f7b760c74501ed05f704.png) 

Tambien podemos presentar esta información como anomalías:
```r
> anomalia <- tmean.pmov-mean(tmean.pmov, na.rm=TRUE)
> anomalia[is.na(anomalia)] <- 0
```

Para la figura correspondiente, pero esta vez usando etiquetas adecuadas para los meses en el eje 'x' y dibujando un polígono que es como se suele representar este tipo de informacion, necesitamos obtener el numero de días de cada mes. Primero extraemos los valores unicos de las primeras tres columnas de cibmeteo con la función unique() y a continuacion contamos los días por mes y por a~no con ayuda de la función aggregate()

```r
> dias <- unique(cibmeteo[, 1:3])
> ndmes <- aggregate(dias$day, by = list(dias$month, dias$year), length)
> ndmes
Group.1 Group.2 x
1 6 2006 30
2 7 2006 31
3 8 2006 31
4 9 2006 30
5 10 2006 31
6 11 2006 30
7 12 2006 31
8 1 2007 31
9 2 2007 28
10 3 2007 31
11 4 2007 30
12 5 2007 30
```

usaremos el vector ndmes$x para dibujar un grid vertical y poner las etiquetas en la grafica:


```r
> plot(anomalia, type="n", ylab = "anomalía de temperatura", xlab = "",
+ xaxt = "n" )
> polygon(c(1:364, 364:1), c(anomalia, rep(0, 364)), col="green")
> abline(h=0, v=c(0, cumsum(ndmes$x)), col="black", lty=3)
> axis(1, at=cumsum(ndmes$x)-ndmes$x/2, labels = c("jun","jul","ago",
+ "sep","oct","nov","dic","ene","feb","mar","abr","may"))
```


![](imagenes/f43223736bddbe8e99e66036acc80209.png)





    2. Analisis de regresion lineal
    
    Para este ejemplo vamos a generar un par de variables ficticias. La variable independiente consistiría en una serie de valores del 1 al 100, y la variable dependiente será calculada usando un valor de 2.5 para la pendiente y de 31 para la ordenada al origen,añadiendo un termino de error aleatorio a la ecuación de la recta:
    ```r
> x <- 1:100
> y <- 2.5*x + 31 + (rnorm(100) * 9)
```
Creemos la grafica de dispersion de nuestras variables ficticias:

```r
> plot(x, y)
```
![](imagenes/14e14b035f9948bf6b2bd71c2efc5722.png)

Y ahora procedamos a efectuar la regresion usando la función lm(), para lo cual debemos especificar el modelo en notacion de formula: $$y ~ x$$
Esta formula es equivalente a: Y = aX + b dado que por defecto, la función lm() calcula el intercepto. Si se desea forzar el intercepto a cero, el modelo debe escribirse de la siguiente forma: 
$$y ~ x + 0$$
Apliquemos pues la función lm() guardando el resultado en un objeto denominado xy.lm:
```r
 > xy.lm <- lm(y ~ x)
```
Para ver el resultado de la regresion utilizamos la función 

```r
summary():
> summary(xy.lm)
Call:
lm(formula = y ~ x)
Residuals:
Min 1Q Median 3Q Max
-26.2903 -6.4543 0.3368 7.1698 18.3609
Coefficients:
Estimate Std. Error t value Pr(>|t|)
(Intercept) 31.54835 1.79969 17.53 <2e-16 ***
x 2.47684 0.03094 80.05 <2e-16 ***
---
Signif. codes: 0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
Residual standard error: 8.931 on 98 degrees of freedom
Multiple R-squared: 0.9849, Adjusted R-squared: 0.9848
F-statistic: 6409 on 1 and 98 DF, p-value: < 2.2e-16
```
Otros detalles del objeto xy.lm pueden verse con la función attributes():

```r
> attributes(xy.lm)
$names
[1] "coefficients" "residuals" "effects" "rank"
[5] "fitted.values" "assign" "qr" "df.residual"
[9] "xlevels" "call" "terms" "model"
$class
[1] "lm"
```
Para extraer los coeficientes de la regresion:

```r
> coef(xy.lm)
(Intercept) x
31.548351 2.476842
```
A continuacion podemos a~nadir el modelo ajustado a la figura anterior:

```r
> abline(xy.lm)
```
![](imagenes/7bfb7a483a4b17cda398da623b06c50b.png)

Por ultimo, podemos explorar los residuales

```r
> par(mfrow=c(2,2))
> plot(xy.lm)
```

![](imagenes/5ba37f60f70b193e948a5eabf13b021c.png)

    3. Estimacion no lineal 
Como en el ejemplo anterior generamos dos variables ficticias X y Y. En el caso de Y utilizamos un modelo potencial sin olvidar agregar un término de error aleatorio.

```r
> X <- seq(1, 20, length=100)
> Y <- 2.5 *( X+runif(100)*3 )^2.5
```

<details>
<summary>Ejercicio: crea la grafica para explorar visualmente la relación entre las dos variables. Dale click para ver la solución</summary>
 ```r
> plot(X, Y)
```
</details>
    

![](imagenes/c3365ad981119acf3bd7560ae79af5f9.png)

Ahora usemos la función de estimacion no lineal nls(). En este caso, ademas de especificar el modelo a ajustar (Y ~ a*X^b) debemos especificar valores iniciales de los parametros de la función. El algoritmo por defecto es el de Gauss-Newton (ver la ayuda de la función nls() para mayores detalles).

```r
> modelo.potencial <- nls(Y ~ a * X^b, start = list(a=1, b=1), trace=TRUE,
+ algorithm="default", model = TRUE)
567164091 : 1 1
565769406 : 0.5182804 1.3203834
562881757 : 0.2159211 1.7617258
549027633 : 0.1885474 2.1288339
529353452 : 0.2916764 2.1929388
495480860 : 0.5002174 2.2127316
435586440 : 0.9047526 2.2174604
334992197 : 1.663137 2.218141
191548384 : 2.990254 2.218180
53250684 : 4.980923 2.218178
7151008 : 6.971593 2.218179
```
Para ver los parametros ajustados usamos coef(), y la función summary() nos muestra resultados adicionales:   

```r
> coef(modelo.potencial)
a b
6.971593 2.218179
> summary(modelo.potencial)
Formula: Y ~ a * X^b
Parameters:
Estimate Std. Error t value Pr(>|t|)
a 6.97159 1.21540 5.736 1.08e-07 ***
b 2.21818 0.06177 35.913 < 2e-16 ***
---
Signif. codes: 0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
Residual standard error: 270.1 on 98 degrees of freedom
Number of iterations to convergence: 10
Achieved convergence tolerance: 1.611e-06
```
Por ultimo, añadimos este modelo final a la grafica:

```r
> lines(X, predict(modelo.potencial), col="red", lwd=2)
```

![](imagenes/a5c35df2e754af9b42f5de3c16c6543b.png)

La estimacion no lineal es sensible a los valores iniciales utilizados, por lo que en ocasiones puede no tener exito. En esos casos se puede efectuar una estimacion previa de los parametros usando la función optim(). En esta, se requiere un criterio a minimizar, generalmente la suma de los residuales al cuadrado:
                   $\sum X (Y_{obs} - Y_{calc})^2$
y ademas se deben especificar valores semilla para los parametros, con la ventaja de que la función de optimizacion es menos exigente respecto a los valores iniciales utilizados.

    4. Analisis de variancia 
Para ilustrar este ultimo caso, utilizaremos un ejemplo de Daniel4 (1993, p. 286). En un estudio del efecto de la glucosa sobre la liberacion de insulina, se trataron muestras de tejido pancreático de animales de laboratorio con 5 estimulantes distintos. Posteriormente se determinó la cantidad de insulina liberada. Los datos se encuentran en el archivo "exaov.txt" proporcionado 

```r
> exaov <- read.table("exaov.txt" ,header=TRUE, sep=";")
```
Una vez importados los datos procedemos a examinar el tama~no de la matriz, los nombres de las variables y las estadísticas descriptivas.

```r
> dim(exaov)
[1] 32 2
> names(exaov)
[1] "estimulante" "insulina"
> summary(exaov)
estimulante insulina
Min. :1.000 Min. :1.450
1st Qu.:2.000 1st Qu.:3.507
Median :3.000 Median :5.395
Mean :3.219 Mean :5.098
3rd Qu.:4.250 3rd Qu.:6.643
Max. :5.000 Max. :9.030
```
Nos interesa probar el efecto del estimulante sobre la cantidad de insulina liberada. La función a utilizar es aov() en la que especificamos los argumentos en notacion de formula:

```r
> insul.anova <- aov(insulina ~ as.factor(estimulante), data=exaov)
```
Los resultados del analisis los podemos ver invocando el objeto recién creado y con la función summary() usada anteriormente:

```r
> insul.anova
Call:
aov(formula = insulina ~ as.factor(estimulante), data = exaov)
Terms:
as.factor(estimulante) Residuals
Sum of Squares 121.18543 41.35739
Deg. of Freedom 4 27
Residual standard error: 1.237641
Estimated effects may be unbalanced
> summary(insul.anova)
Df Sum Sq Mean Sq F value Pr(>F)
as.factor(estimulante) 4 121.19 30.296 19.78 1.05e-07 ***
Residuals 27 41.36 1.532
---
Signif. codes: 0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```

## Lecturas Recomendadas
1. Everitt, B. y Hothorn, T. 2006. A Handbook of Statistical Analyses Using R Chapman& Hall/CRC, 275 pp.
2. Murrell, P. 2005. R Graphics. Chapman & Hall/CRC. 301 pp.
3. Paradis, E. 2005. R For Beginners. 72 pp. Disponible en Internet: http://cran.
r-project.org/doc/contrib/Paradis-rdebuts_en.pdf
4. R Core Team. 2012. R Language Definition. Version 2.15.2 (2012-10-26) DRAFT.
ISBN 3-900051-13-5. 55 pp.
5. Venables, W. N.y Ripley, B. D. 2002. Modern Applied Statistics with S. 4a Edicion.Springer. 495 pp.
6. Venables, W. N., D.M. Smith y R Development Core Team. 2009. An Introduction
to R. Notes on R: A Programming Environment for Data Analysis and Graphics.
Version 2.9.1 (2009-06-26). ISBN 3-900051-12-7. 94 pp.