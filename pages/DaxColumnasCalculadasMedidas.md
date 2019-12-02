##### [Volver](/Curso-de-Herramientas-analiticas-para-auditoria-I/pages/Indice_curso.html)
<script src="https://kit.fontawesome.com/065728df02.js" crossorigin="anonymous"></script>


# ¿Qué es DAX?
DAX es una recopilación de funciones, operadores y constantes que se pueden usar en una fórmula o expresión para calcular y devolver uno o varios valores. Dicho más fácilmente, DAX ayuda a crear información de datos nueva que ya está en un modelo.

La sintaxis de DAX es sencilla y se puede resumir así:
* Las fórmulas comienzan con un "=" seguido de una expresión DAX 
* Las expresiones contienen funciones, operadores, constantes y referencias a columnas
* Los nombres de las columnas siempre se escriben entre corchetes y pueden estar compuestas por nombre de tabla + nombre de columna o sólo nombre de columna.

En este [enlace](https://support.office.com/es-es/article/tutorial-rápido-aprenda-los-fundamentos-de-dax-en-30-minutos-51744643-c2a5-436a-bdf6-c895762bec1a) podemos encontrar una introducción rápida a DAX


# Columnas calculadas y medidas
 
## Columnas calculadas
Cuando escribimos nuestra primera expresión con DAX, disponemos de varias opciones de menú para crear columnas calculadas y/o medidas. Disponemos además de una barra de fórmulas y la sintaxis DAX para escribir medidas y columnas calculadas es la misma.

Para crear columnas calculadas en power pivot podemos situarnos en la ficha Diseñar y seleccionar Agregar, también situarnos sobre una columna y con el botón derecho escoger y también situandonos en la última columna denominada 'Agregar columna' y modificando su nombre. 
![DAX_columna](/Curso-de-Herramientas-analiticas-para-auditoria-I/images/DAX_Columna.png)

Una vez creada la columna, hemos de introducir el calculo o fórmula de dicha columna y para ello desde la barra de fórmulas podemos escribir la expresión que va a ser evaluada por cada una de las filas de la nueva columna calculada. En la Barra de fórmulas, vamos a contar con la ayuda de IntelliSense. 
![DAX_intellisense](/Curso-de-Herramientas-analiticas-para-auditoria-I/images/DAX_intellisence.png)

En el modelo tabular las columnas siempre van entre corchetes, por lo que admiten todo tipo de espacios y caracteres que se quiera definir. Opcionalmente pueden ir precedidas con el nombre de la tabla a la que pertenecen, siendo recomendable.

Muy importante: La expresión debe comenzar con el signo  =

Es posible crear tantas columnas calculadas como se desee, pero lo recomendable es no crear demasiadas ya que su número será inversamente proporcional al rendimiento de power pivot. Por tanto, cuidado… 

Al crear las columnas, y es válido también para las medidas, es muy recomendable asignar el formato adecuado. Esta asignación hecha en el modelo de datos permite que ya aparezca con formato cuando se utilice en los gráficos y tablas dinámicas. Recomendación: No olvidar dar formato en el modelo a cada columna y medida que se vaya a utilizar.
![DAX_formato](/Curso-de-Herramientas-analiticas-para-auditoria-I/images/DAX_formato.png)

De esta forma, definimos en una nueva columna calculada
![DAX_columna_calculada](/Curso-de-Herramientas-analiticas-para-auditoria-I/images/DAX_calculo_columna.png)


## Medidas

Para crear una medida desde power pivot no situaremos en el área de medidas y luego en la barra de fórmulas escribiremos un nombre descriptivo y a continuación :=  y por último la formula o expresión en DAX a calcular.


![DAX_medida](/Curso-de-Herramientas-analiticas-para-auditoria-I/images/DAX_medida.png)

