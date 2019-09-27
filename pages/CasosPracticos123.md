##### [Volver](/Curso-de-Herramientas-analiticas-para-auditoria-I/pages/Indice_curso.html)
<script src="https://kit.fontawesome.com/065728df02.js" crossorigin="anonymous"></script>
# Indice del curso


## Caso 1 - Analisis inventario y pedidos
El objetivo es auditar diariamente la cantidad de pedidos ingresado a la empresa y cruzarlo con el inventarios disponibles para determinar el nivel de respuesta, es decir, si con este inventario se suple o no la demanda requerida.

Tenemos dos tablas, una de los inventarios disponibles, y la otra tabla es la transaccional de pedidos, donde a diario se registran los pedidos de la compañía.

La meta es cruzar los inventarios y consolidar los pedidos por referencia y determinar si dicho inventario cubre la cantidad de pedidos.

Fichero de trabajo 1 <a href="/Curso-de-Herramientas-analiticas-para-auditoria-I/downloads/17.1.Caso_1.xlsx"><i class="fas fa-file-excel"></i> </a>

*  [Solución Caso 1](/Curso-de-Herramientas-analiticas-para-auditoria-I/downloads/17.1.Solucion_ Caso_1.xlsx)


## Caso 2 - Análisis de ventas

La parte comercial en una compañía es un área muy determinante para su operación, es la primera cadena que juega un papel importante para la toma de decisiones. En este caso queremos saber cuál es el mejor cliente de cada vendedor y que porcentaje contribuye a las ventas.

el objetivo es determinar mes a mes cual es cliente que mayor tiene de cada vendedor y su porcentaje de participación.

Fichero de trabajo  2 <a href="/Curso-de-Herramientas-analiticas-para-auditoria-I/downloads/17.2.Caso_2.xlsx"><i class="fas fa-file-excel"></i> </a> 

1. Agrupamos por MES y VENDEDOR con nuevas columnas Total (Suma) y Detalle (Todas las filas)
2. Expandir
3. Agregar columna personalizada -> Ingresar esta fórmula -> `Table. Max([DETALLE],"VENTAS")`
4. Eliminamos la columna DETALLE -> Cambiar nombre de columna VENTAS “VENTA MAX” -> Tipo de dato -> Número entero.

Por último solo nos queda calcular el porcentaje de venta de cada cliente sobre el total por vendedor y mes.

* Seleccionamos la columna VENTA MAX y TOTAL, en este mismo orden.
* Agregar columna -> Estándar -> Dividir


*  [Solución Caso 2](/Curso-de-Herramientas-analiticas-para-auditoria-I/downloads/17.2.Solucion_Caso_2.xlsx)


## Caso 3 - Consolidar información contable

Uno de los mayores esfuerzos que realiza un contable a diario es tratar de organizar y consolidar los datos para la presentación de informes, les toma mucho tiempo cada semana o cada mes tener todo al día. Veamos varios trucos y funciones con Power Query, que son de utilidad para ese trabajo diario.


La información de partida es un balance de comprobación exportado desde el sistema contable, el objetivo es consolidar los datos por grupos o cuentas principales para realizar los respectivos informes.

Tenemos varios inconvenientes:
▪ La columna cuenta en cada registro tiene espacios al final, por tal razón no está en tipo número.
▪ La cuenta tiene un nivel mínimo de 2 dígitos, para los informes los necesitamos a partir del grupo o cuenta mayor, 1 dígito.
▪ Se debe consolidar la información.

Fichero de trabajo 3 <a href="/Curso-de-Herramientas-analiticas-para-auditoria-I/downloads/17.3.Caso_3.xlsx"><i class="fas fa-file-excel"></i> </a>

*  [Solución Caso 3](/Curso-de-Herramientas-analiticas-para-auditoria-I/downloads/17.3.Solucion_Caso_3.xlsx)
