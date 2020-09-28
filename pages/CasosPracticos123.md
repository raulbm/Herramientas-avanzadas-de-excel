##### [Volver](/Herramientas-avanzadas-de-excel/pages/Indice_curso.html)
<script src="https://kit.fontawesome.com/065728df02.js" crossorigin="anonymous"></script>
# Indice del curso


## Caso 1 - Analisis inventario y pedidos
El objetivo es auditar diariamente la cantidad de pedidos ingresados en la empresa y cruzarlo con los inventarios disponibles para determinar el nivel de respuesta, es decir, si con este inventario es suficiente para suplir o no la demanda requerida.

Tenemos dos tablas, una de los inventarios disponibles, y la otra tabla es la transaccional de pedidos, donde a diario se registran los pedidos de la compañía.

La meta es cruzar los inventarios y consolidar los pedidos por referencia y determinar si dicho inventario cubre la cantidad de pedidos.

Fichero de trabajo 1 <a href="/Herramientas-avanzadas-de-excel/downloads/17.1.Caso_1.xlsx"><i class="fas fa-file-excel"></i> </a>

*  [Solución Caso 1](/Herramientas-avanzadas-de-excel/downloads/17.1.Solucion_ Caso_1.xlsx)


## Caso 2 - Análisis de ventas

La parte comercial en una compañía es un área muy determinante para sus operaciones y juega un papel importante en la toma de decisiones. En este caso queremos saber cuál es el mejor cliente de cada vendedor y en que porcentaje contribuye a las ventas.

El objetivo es determinar mes a mes cual es el mayor cliente que tiene cada vendedor y su porcentaje de participación.

Fichero de trabajo  2 <a href="/Herramientas-avanzadas-de-excel/downloads/17.2.Caso_2.xlsx"><i class="fas fa-file-excel"></i> </a> 

1. Agrupamos por MES y VENDEDOR con nuevas columnas Total (Suma) y Detalle (Todas las filas)
2. Agregar columna personalizada -> Ingresar esta fórmula -> `Table. Max([DETALLE],"VENTAS")`
3. Expandir
4. Eliminamos la columna DETALLE -> Cambiar nombre de columna VENTAS “VENTA MAX” -> Tipo de dato -> Número entero.

Por último, sólo nos queda calcular el porcentaje de venta de cada cliente sobre el total por vendedor y mes.

* Seleccionamos la columna VENTA MAX y TOTAL, en este mismo orden.
* Agregar columna -> Estándar -> Dividir


*  [Solución Caso 2](/Herramientas-avanzadas-de-excel/downloads/17.2.Solucion_Caso_2.xlsx)
