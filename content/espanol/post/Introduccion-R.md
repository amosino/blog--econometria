---
title: "Introducción a R"
author: "Alejandro Mosiño"
<<<<<<< HEAD
date: '2023-08-01'
slug: Introduccion R
summary: 'R es un conjunto integrado de programas para manipulación de datos, cálculo y gráficos. En este post daremos una breve introducción a R: tipos de variables, operaciones numéricas, clases de datos, entre otros.'
=======
date: '2020-07-20'
slug: Introduccion R
summary: 'R es un conjunto integrado de programas para manipulación de datos, cálculo y gráficos. En este post daremos una muy breve introducción a R: tipos de variables, operaciones numéricas, clases de datos, entre otros.'
>>>>>>> 214c0ae948ee9931e30630b2e07f646e37896ca4
tags:
- Data Management
- Econometrics
- Programming
- R
categories:
- Data Managment
- Econometrics
- Programming
weight: 1
math: true
---

<script src="/rmarkdown-libs/htmlwidgets/htmlwidgets.js"></script>
<script src="/rmarkdown-libs/jquery/jquery.min.js"></script>
<link href="/rmarkdown-libs/leaflet/leaflet.css" rel="stylesheet" />
<script src="/rmarkdown-libs/leaflet/leaflet.js"></script>
<link href="/rmarkdown-libs/leafletfix/leafletfix.css" rel="stylesheet" />
<script src="/rmarkdown-libs/proj4/proj4.min.js"></script>
<script src="/rmarkdown-libs/Proj4Leaflet/proj4leaflet.js"></script>
<link href="/rmarkdown-libs/rstudio_leaflet/rstudio_leaflet.css" rel="stylesheet" />
<script src="/rmarkdown-libs/leaflet-binding/leaflet.js"></script>

<<<<<<< HEAD
R es un conjunto integrado de programas para la manipulación de datos, cálculo y gráficos. Entre otras características, dispone de: 1) almacenamiento y manipulación efectiva de datos, 2) operadores para cálculo sobre variables indexadas, en particular matrices, 3) una amplia, coherente e integrada colección de herramientas para el análisis de datos, 4) posibilidades gráficas para el análisis de datos que funcionan directamente en pantalla o impresora, y 5) un lenguaje de programación bien desarrollado, simple y efectivo, que incluye condicionales, ciclos, funciones recursivas y posibilidad de entradas y salidas.
=======
R es un conjunto integrado de programas para manipulación de datos, cálculo y gráficos. Entre otras características dispone de: 1) almacenamiento y manipulación efectiva de datos, 2) operadores para cálculo sobre variables indexadas, en particular matrices, 3) una amplia, coherente e integrada colección de herramientas para análisis de datos, 4) posibilidades gráficas para análisis de datos que funcionan directamente sobre pantalla o impresora, y 5) un lenguaje de programación bien desarrollado, simple y efectivo, que incluye condicionales, ciclos, funciones recursivas y posibilidad de entradas y salidas.
>>>>>>> 214c0ae948ee9931e30630b2e07f646e37896ca4

## Variables, operaciones, operadores lógicos y clases de datos

### Tipos de variables


Primero asignemos un valor a una variable `\(x\)`. Este valor puede ser un número, pero también puede ser un conjunto de caracteres, variables categóricas (o factores), booleanas (lógicas: verdadero o falso) y fechas. Esto se puede ver en los siguientes ejemplos:

``` r
# Números
x <- 10
print(x)
```

    ## [1] 10

``` r
# Caracteres
x <- "Economia"
print(x)
```

    ## [1] "Economia"

``` r
# Categóricas
x <- factor(c(10,11))
print(x)
```

    ## [1] 10 11
    ## Levels: 10 11

``` r
# Booleanas
x <- FALSE
print(x)
```

    ## [1] FALSE

``` r
# Fechas
x <- as.Date("08/08/2018", "%m/%d/%Y")
print(x)
```

    ## [1] "2018-08-08"

Nota que la asignación de valores se expresa mediante el símbolo `<-`, aunque el signo `=` también funciona. Nota, además, que hemos usado el comando `print(x)` para ver si el código funciona correctamente.

Las variales en R también pueden tener más de un valor. Por ejemplo, construimos un vector llamado `votantes` que consiste en una secuencia de números *del mismo tipo*:

``` r
votantes <- c(134, 542, 324, 102, 402, 383, 853)
print(votantes)
```

    ## [1] 134 542 324 102 402 383 853


Supongamos que cada elemento del vector `votantes` representa el número de votantes en una casilla electoral. Deseamos, por ejemplo: 1) calcular el número total de votantes en la elección, 2) el número de casillas electorales y 3) imprimir un mensaje que resuma la información obtenida. Esto se puede lograr con las funciones: `sum()`, `length()` y `paste()`, respectivamente.

``` r
no_votantes <- sum(votantes)
no_casillas <- length(votantes)
texto1 <- "El número total de votantes es:"
texto2 <- "en un total de:"
texto3 <- "casillas electorales"
mensaje <- paste(texto1, no_votantes, texto2, no_casillas, texto3)
print(mensaje)
```

    ## [1] "El número total de votantes es: 2740 en un total de: 7 casillas electorales"

### Operaciones con números


R se puede utilizar como calculadora. Es decir, los valores numéricos se pueden modificar o manipular mediante los operadores aritméticos clásicos: suma (`+`), resta (`-`), multiplicación (`*`), división (`/`), potencia (`**`) y módulo (`%%`).

``` r
x <- 10

# Suma
x <- x+5
print(x)
```

    ## [1] 15

``` r
# Resta
x <- x-8
print(x)
```

    ## [1] 7

``` r
# Multiplicación
x <- x*4
print(x)
```

    ## [1] 28

``` r
# División
x <- x/14
print(x)
```

    ## [1] 2

``` r
# Potencia
x <- x**2
print(x)
```

    ## [1] 4

``` r
# Módulo
mod1 <- 10%%10
mod2 <- 20%%10
mod3 <- 10%%20
mod4 <- 2%%8
print(c(mod1,mod2, mod3, mod4))
```

    ## [1]  0  0 10  2


Estas operaciones también se aplican a los vectores. Por ejemplo, si multiplicamos por 2 el vector `votantes`, cada elemento de este vector se multiplicará por 2.

``` r
# Multiplicación
votantes_doble <- votantes*2
print(votantes_doble)
```

    ## [1]  268 1084  648  204  804  766 1706

``` r
# División
votantes_mitad <- votantes/2
print(votantes_mitad)
```

    ## [1]  67.0 271.0 162.0  51.0 201.0 191.5 426.5

### Operadores lógicos


Los valores lógicos son particularmente útiles para clasificar datos de acuerdo a valores o umbrales específicos. El resultado de una operación lógica es un valor booleano. Las operaciones también pueden aplicarse a vectores.

``` r
x <- 10
y <- 2

# Desigualdad estricta
resultado <- x > y
print(resultado)
```

    ## [1] TRUE

``` r
# Desigualdad
resultado <- x >= y
print(resultado)
```

    ## [1] TRUE

``` r
# Igualdad
resultado <- x == y
print(resultado)
```

    ## [1] FALSE

``` r
# Negación
resultado <- x != y
print(resultado)
```

    ## [1] TRUE

``` r
casillas_200 <- votantes>200
table(casillas_200)
```

    ## casillas_200
    ## FALSE  TRUE 
    ##     2     5


Nota que en la última operación hemos utilizado el comando `table()` para obtener el número de registros verdaderos y el número de falsos. Este comando sirve para dar el número de registros diferentes en un vector o matriz de datos.

### Clases de datos

Los vectores que hemos visto antes son solo una de las clases de datos que admite R. Pero existen otras clases. Las más importantes son, aparte de los vectores, las matrices, las listas y los *data frames*.

Las matrices pueden construirse a partir de vectores. Recuerda que los vectores son secuencias de números del mismo tipo. Considera el siguiente ejemplo, en el que un vector contiene caracteres y dos contienen números. La matriz en la última línea se construye utilizando el comando `cbind()`.

``` r
cities <- c("Guadalajara","León","Aguascalientes","San Luis Potosí","Irapuato", "San Miguel de Allende")
pop <- c(1600940, 1278087, 723043, 730950, 463103, 139297)
area <- c(187.9, 1219.67, 385, 385, 845.2, 1559)
mat <- cbind(cities, pop, area)
print(mat)
```

    ##      cities                  pop       area     
    ## [1,] "Guadalajara"           "1600940" "187.9"  
    ## [2,] "León"                  "1278087" "1219.67"
    ## [3,] "Aguascalientes"        "723043"  "385"    
    ## [4,] "San Luis Potosí"       "730950"  "385"    
    ## [5,] "Irapuato"              "463103"  "845.2"  
    ## [6,] "San Miguel de Allende" "139297"  "1559"


Todos los vectores y matrices están indizados, por lo que podemos buscar elementos dentro de ellos. Algunos ejemplos son los siguientes:

``` r
# Primer elemento del vector cities
cities1 <- cities[1]
print(cities1)
```

    ## [1] "Guadalajara"

``` r
# Elementos 1 y 4 del vector cities
cities2 <- cities[c(1,4)]
print(cities2)
```

    ## [1] "Guadalajara"     "San Luis Potosí"

``` r
# Elementos del 1 al 3 del vector cities
cities3 <- cities[1:3]
print(cities3)
```

    ## [1] "Guadalajara"    "León"           "Aguascalientes"

``` r
# Elemento (2,1) de la matriz mat
mat1 <- mat[2,1]
print(mat1)
```

    ## cities 
    ## "León"

``` r
# 2 y 3 filas y 1 y 3 columnas de la matriz mat
mat2 <- mat[2:3, c(1,3)]
print(mat2)
```

    ##      cities           area     
    ## [1,] "León"           "1219.67"
    ## [2,] "Aguascalientes" "385"

``` r
# Primera columna de la matriz mat
mat3 <- mat[,1]
print(mat3)
```

    ## [1] "Guadalajara"           "León"                  "Aguascalientes"       
    ## [4] "San Luis Potosí"       "Irapuato"              "San Miguel de Allende"

``` r
# Tercera fila de la matriz mat
mat4 <- mat[3,]
print(mat4)
```

    ##           cities              pop             area 
    ## "Aguascalientes"         "723043"            "385"


Los vectores (y matrices) se pueden transformar en *data frames*. Estos resultan muy útiles dado que permiten fijar y modificar los nombres de las variables que los conforman. Esta característica no está disponible para las matrices. Por ejemplo, el *data frame* a continuación se crea a partir de los vectores `cities`, `pop` y `area`, a la vez que modificamos los nombres de las variables:

``` r
df <- data.frame(city=cities, population = pop, area=area)
print(df)
```

    ##                    city population    area
    ## 1           Guadalajara    1600940  187.90
    ## 2                  León    1278087 1219.67
    ## 3        Aguascalientes     723043  385.00
    ## 4       San Luis Potosí     730950  385.00
    ## 5              Irapuato     463103  845.20
    ## 6 San Miguel de Allende     139297 1559.00

Si deseamos modificar nuevamente los nombres de las variables, no es necesario volver a crear el *data frame* `df`. Podemos obtener el nombre de las variables mediante el comando `colnames()`. Dado que los nombres no son más que elementos de un vector, basta con modificar el valor de sus elementos. Por ejemplo:

``` r
colnames(df) <- c("Ciudad", "Poblacion", "Área")
print(df)
```

    ##                  Ciudad Poblacion    Área
    ## 1           Guadalajara   1600940  187.90
    ## 2                  León   1278087 1219.67
    ## 3        Aguascalientes    723043  385.00
    ## 4       San Luis Potosí    730950  385.00
    ## 5              Irapuato    463103  845.20
    ## 6 San Miguel de Allende    139297 1559.00

Con los *data frames*, es posible obtener las columnas utilizando el operador `$`. Por ejemplo, la columna correspondiente a las ciudades se obtiene:

``` r
df$Ciudad
```

    ## [1] "Guadalajara"           "León"                  "Aguascalientes"       
    ## [4] "San Luis Potosí"       "Irapuato"              "San Miguel de Allende"

El operador `$` también nos permite agregar columnas al *data frame*. Por ejemplo, deseamos construir una nueva variable booleana que indique cuáles son las ciudades con una población mayor a 2500000. Esta nueva variable, que llamaremos `CiudadGrande` será agregada al *data_frame* \`df:

``` r
df$CiudadGrande <- df$Poblacion > 1000000
print(df)
```

    ##                  Ciudad Poblacion    Área CiudadGrande
    ## 1           Guadalajara   1600940  187.90         TRUE
    ## 2                  León   1278087 1219.67         TRUE
    ## 3        Aguascalientes    723043  385.00        FALSE
    ## 4       San Luis Potosí    730950  385.00        FALSE
    ## 5              Irapuato    463103  845.20        FALSE
    ## 6 San Miguel de Allende    139297 1559.00        FALSE

## Librerías


R viene precargado con varios paquetes que nos permiten realizar varias funciones relativamente simples como las descritas arriba. Sin embargo, existen muchos más paquetes que pueden ser descargados y utilizados para aumentar la potencia y simplificar muchas tareas. Estos paquetes se pueden instalar usando el comando `install.packages()`. Una vez instalados los paquetes (lo cual se hace solo una vez y para siempre), tenemos que indicarle a R que deseamos usarlos durante la sesión activa. Para esto utilizamos el comando `library()`.

Para hacer una demostración de lo anterior, aquí instalaremos y utilizaremos los paquetes `stargazer`, `ggplot2` y `leaflet`. El primero es una librería que nos permite hacer tablas en diferentes formatos: texto, HTML y LaTeX. El segundo nos permite aumentar las capacidades gráficas de R. El tercero nos permite hacer mapas interactivos. Utilizaremos la base de datos anterior sobre las ciudades de México, pero agregaremos información sobre sus coordenadas geográficas.

``` r
# install.packages("stargazer")
# install.packages("ggplot2")
# install.packages("leaflet")
library(stargazer)
```

    ## 
    ## Please cite as:

    ##  Hlavac, Marek (2022). stargazer: Well-Formatted Regression and Summary Statistics Tables.

    ##  R package version 5.2.3. https://CRAN.R-project.org/package=stargazer

``` r
library(ggplot2)
library(leaflet)

df$Latitud <- c(20.6736, 21.1236, 21.8818, 22.2021, 20.6833, 20.9)
df$Longitud <- c(-103.34420,-101.6821, -102.291, -101.0542, -101.35,-101.4833)
print(df)
```

    ##                  Ciudad Poblacion    Área CiudadGrande Latitud  Longitud
    ## 1           Guadalajara   1600940  187.90         TRUE 20.6736 -103.3442
    ## 2                  León   1278087 1219.67         TRUE 21.1236 -101.6821
    ## 3        Aguascalientes    723043  385.00        FALSE 21.8818 -102.2910
    ## 4       San Luis Potosí    730950  385.00        FALSE 22.2021 -101.0542
    ## 5              Irapuato    463103  845.20        FALSE 20.6833 -101.3500
    ## 6 San Miguel de Allende    139297 1559.00        FALSE 20.9000 -101.4833


Ahora haremos una tabla que muestre un resumen de la información. El formato de salida será de texto para efectos de este ejemplo, pero recuerda que podemos elegir otros formatos. Intenta, por tu cuenta, cambiar la opción *text* por la opción *latex*.

``` r
stargazer(df, type="text")
```

    ## 
    ## =========================================================
    ## Statistic    N    Mean      St. Dev.     Min       Max   
    ## ---------------------------------------------------------
    ## Poblacion    6 822,570.000 534,365.800 139,297  1,600,940
    ## Área         6   763.628     541.373   187.900  1,559.000
    ## CiudadGrande 6    0.333       0.516       0         1    
    ## Latitud      6   21.244       0.648     20.674   22.202  
    ## Longitud     6  -101.867      0.833    -103.344 -101.054 
    ## ---------------------------------------------------------

Ahora crearemos un mapa interactivo que nos mostrará la posición geográfica de las ciudades que hemos elegido. La posición será indicada con un círculo, cuyo tamaño dependerá del número de habitantes. Dado que este no es un curso de `ggplot2` ni de `leaflet`, no debes preocuparte si no comprendes todo el código.

``` r
leaflet(df) %>%
  addTiles() %>%
  addCircles(lng=~Longitud, lat=~Latitud, weight=1,
             radius =~sqrt(Poblacion)*30, popup=~Ciudad)
```

<div class="leaflet html-widget html-fill-item-overflow-hidden html-fill-item" id="htmlwidget-1" style="width:672px;height:480px;"></div>
<script type="application/json" data-for="htmlwidget-1">{"x":{"options":{"crs":{"crsClass":"L.CRS.EPSG3857","code":null,"proj4def":null,"projectedBounds":null,"options":{}}},"calls":[{"method":"addTiles","args":["https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png",null,null,{"minZoom":0,"maxZoom":18,"tileSize":256,"subdomains":"abc","errorTileUrl":"","tms":false,"noWrap":false,"zoomOffset":0,"zoomReverse":false,"opacity":1,"zIndex":1,"detectRetina":false,"attribution":"&copy; <a href=\"https://openstreetmap.org\">OpenStreetMap<\/a> contributors, <a href=\"https://creativecommons.org/licenses/by-sa/2.0/\">CC-BY-SA<\/a>"}]},{"method":"addCircles","args":[[20.6736,21.1236,21.8818,22.2021,20.6833,20.9],[-103.3442,-101.6821,-102.291,-101.0542,-101.35,-101.4833],[37958.4773140336,33915.7529770459,25509.5805531961,25648.684176776,20415.5014633489,11196.7539939038],null,null,{"interactive":true,"className":"","stroke":true,"color":"#03F","weight":1,"opacity":0.5,"fill":true,"fillColor":"#03F","fillOpacity":0.2},["Guadalajara","León","Aguascalientes","San Luis Potosí","Irapuato","San Miguel de Allende"],null,null,{"interactive":false,"permanent":false,"direction":"auto","opacity":1,"offset":[0,0],"textsize":"10px","textOnly":false,"className":"","sticky":true},null,null]}],"limits":{"lat":[20.6736,22.2021],"lng":[-103.3442,-101.0542]}},"evals":[],"jsHooks":[]}</script>


Dado que este mapa es interactivo, puedes acercar o alejar el mapa con tu mouse. ¡Inténtalo!

*Última actualización: 09-08-2023.*
