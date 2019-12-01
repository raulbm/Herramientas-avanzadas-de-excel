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
Cuando escribimos nuestra primera expresión con DAX, hay varias opciones de menú para crear columnas calculadas y además, como en el caso de las medidas, aparece la barra de fórmulas y la sintaxis DAX para escribir medidas y columnas calculadas es la misma, la sintaxis es la misma, lo que es diferente es lo que el motor espera evaluar en una medida y en una columna calculada. Lo iremos viendo.

Para crear columnas calculadas mi recomendación es situarse en la ficha Datos, en este caso, mostrando la tabla Ventas, y seleccionar Nueva Columna

nueva columna

Desde la barra de fórmulas estamos listos para escribir la expresión que va a ser evaluada por cada una de las filas de la nueva columna calculada, para la que como vemos en la imagen ya se ha reservado un sitio en la tabla.

Es posible crear tantas columnas calculadas como se desee; pero cuidado… muchísimo cuidado con las columnas calculadas… poder, se puede trabajar con ellas; pero pueden ser muy dañinas para el Modelo tabular. Las columnas calculadas no están recomendadas. Voy a insistir una y otra vez y veremos ejemplos que lo demuestran, uno de los casos, hoy mismo.

nueva columna 2

En la Barra de fórmulas, vamos a contar con la inestimable ayuda de IntelliSense, igual que en el caso de las medidas. Escribir la expresión Importe Ventas = Cantidad * Precio, es tan sencillo como seleccionar las columnas con el Intellisense.

Int1

En la medida que vamos tecleando Intellisense es más útil



Al crear las columnas, y es válido también para las medidas, podemos y debemos asignar el formato adecuado. Esta asignación a nivel de modelo de datos permite que ya aparezca con formato cuando se utilice en los gráficos, tarjetas y otras visualizaciones de Power BI. No olvidéis dar formato a nivel de modelo a cada columna y medida que vayáis a utilizar.

formato

De esta forma, definimos la expresión DAX para Importe Ventas.

ImpV

Definimos la expresión DAX para Beneficios.

Benef

Y por último, definimos la expresión DAX para % Beneficio.

porcbenef

En este caso, voy a hacer un paréntesis aclarando algunos aspectos relacionados con esta expresión

El nombre de la columna, % Beneficio, es correcto. En el modelo tabular las columnas siempre, siempre van entre corchetes, por lo que admiten todo tipo de espacios y caracteres que se quiera definir
Para trabajar con cálculos que implican división nos enfrentamos al dilema de la división por cero, tendríamos que utilizar una función que comprobara antes de hacer la división. Las funciones de control de errores en DAX son lentas, no favorecen el óptimo rendimiento del motor. Hay que evitarlas a toda costa. Para ello, siempre hay que definir bien el tipo de datos y en este caso, utilizar la función DIVIDE(), que ya está optimizada y se encarga de comprobar que no ocurra la División por cero.
divide

Por otra parte, al tratarse de un % hay que indicar también el formato adecuado
formstopor

En la tabla Ventas, podemos ver las tres columnas que han sido calculadas. Si nos detemenos fila a fila, vemos que el resultado es correcto, las expresiones se han evaluado de forma adecuada, todo parece ir bien.

porcbenef2

Una vez creadas las columnas, el siguiente paso es utilizarlas en una visualización, en nuestro caso será una sencilla tabla. Vamos a analizar el resultado de estas tres expresiones según sea la categoría de los productos vendidos.

Empezamos por las dos primeras columnas calculadas: Importe Ventas y Beneficios.



Mostramos luego, la columna calculada % de Beneficios.

ColCalMal

Los valores devueltos por las columnas Importe Ventas y Beneficios tienen buen aspecto, parecen razonablemente bien, de hecho son correctos. Pero la columna % de Beneficios devuelve valores completamente irreales e incorrectos. No tenemos ningún mensaje de error; pero no cabe duda de la incoherencia de los datos.

¿Te haces una idea de lo que ha ocurrido? Pues lo que ha ocurrido es que la columna calculada, a efectos de uso en un informe, se comporta como una columna nativa y al añadirla al informe crea una medida implícita, agregando los valores, sumándolos, como mismo vismos al analizar Medidas implícitas vs Explícitas. Está sumando los Porcientos de Beneficios obtenidos fila a fila en lugar de devolver el Porciento que representan los Beneficios sobre las Ventas.

Podríamos intentar mostrar el Porciento de contribución al padre, reutilizando la columna Beneficios y la funcionalidad Mostrar como porciento del total general, de Power BI Desktop, que es por cierto, la misma que en Excel.

MostrarComo

El valor devuelto es correcto; pero no es lo que necesitamos. Al menos, es correcto.



## Medidas

Hay que tener en cuenta que:

Como la medida no pertenece a ninguna tabla en concreto, no puede acceder, por sí misma a las filas de las columnas de ninguna de las tablas.
No existe, de forma natural, el contexto de fila, como en las columnas calculadas.
La buena noticia es que DAX dispone de funciones, que son iteradores, que recorren una tabla o expresión DAX que devuelva tabla y se pase a la función como primer parámetro, y fila a fila de esa tabla evalúa la expresión que se pase como segundo parámetro.
Como siempre, veamos la teoría a través de ejemplos.

Para calcular Importe Ventas con una medida DAX, lo que en realidad necesitamos es recorrer la tabla Ventas y poder calcular, fila a fila la expresión Ventas[CantidadETL] * Ventas[Precio]. Luego, hay que sumar estos valores para obtener el resultado agregado.

Medidas en Modelos tabulares
Una de las opciones es seleccionar la tabla _Cálculos, el contenedor para medidas que creamos en la entrada anterior, DAX: Crear contenedor para medidas DAX en Modelos tabulares con Power BI,  y en los tres puntos que aparecen a la derecha desplegar las opciones y seleccionar Nueva Medida. Para que se note la diferencia en el informe, las tres medidas que voy a crear van a empezar con la palabra Total.



En la barra de fórmulas, escribimos el nombre y vemos que, al intentar sumar la expresión, no podemos. La función SUM sólo permite trabajar con una columna.

SumNoVale

Afortunadamente, disponemos de SUMX, ese es el iterador del que hablaba yo antes, recibe dos parámetros, Ventas, que es la tabla a recorrer y la expresión a evaluar es: Ventas[CantidadETL] * Ventas[Precio].

Regresamos a las medidas. De igual forma que antes creamos la medidas para Total Beneficios, con el mismo iterador SUMX y la expresión que corresponde.

Por último, definimos la medida para el Total % Beneficios. En este caso, lo más interesante es que podemos reutilizar las medidas que hemos creado anteriormente, lo que resulta muy cómodo, limpio y efectivo.

        

Resumiendo, las expresiones de las tres medidas creadas son:

Total Importe = SUMX(Ventas;Ventas[CantidadETL]*Ventas[Precio])
Total Beneficios = SUMX(Ventas;Ventas[CantidadETL] * (Ventas[Precio] – Ventas[Coste]))
Total % Beneficios = DIVIDE([Total Beneficios];[Total Importe])

Vamos a comparar entonces, el resultado que se obtiene al trabajar con las medidas