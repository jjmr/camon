Taller impartido por **Ana Belén García Parra**

# Introducción #
Google Visualization API es una librería de visualización open source que permite embeber atractivas visualizaciones en una página web de forma sencilla utilizando el lenguaje Javascript. Esta librería abstrae al desarrollador de los detalles de bajo nivel ofreciendo componentes completos de visualización y herramientas para el manejo de datos. Posee una amplia [documentación](http://code.google.com/intl/es-ES/apis/visualization/interactive_charts.html) y está en continuo desarrollo (última versión: Agosto de 2010) En [su galería](http://code.google.com/intl/es-ES/apis/visualization/documentation/gallery.html) podemos encontrar una amplia selección de componentes disponibles para ser reutilizados.
# Visualización #
## Motion Chart ##
Para confeccionar la muestra de datos se han  escogido a España y a los cuatro países que llegaron a semifinales.  Para cada partido jugado en un mismo día se representa en un eje de coordenadas la relación entre los resultados y las menciones obtenidas por cada equipo mediante un círculo. Sobre el eje  <strong>x</strong> se epresenta el número de menciones contabilizadas de cada país y sobre el eje <strong>y</strong> el número de puntos anotados por ese país en cada partido.

<strong>Interactividad</strong>: Se puede elegir el color y el tamaño de los círculos, seleccionar o deseleccionar países, dejar rastro o no de la trayectoria y avanzar/retroceder en el tiempo. Pasando el ratón por cada círculo aparece el país al que corresponde.

**Fuente de datos**:
  * [Turkey2010\_day\_list](https://spreadsheets.google.com/ccc?key=0AvqG-02OdbLbdE9XRmE5UnFZLU5qQ3M4MXp1aEVFNXc&hl=en#gid=5). Tabla _main\_countries\_day\_list_. Tabla de datos que registra el número de menciones obtenidas cada día del mundial de los países que llegaron a semifinales (Serbia, Lituania, EEUU y Turquía) y España. Se accede a esta tabla automáticamente desde la visualización [invocándolo como fuente de datos externa](http://code.google.com/intl/es-ES/apis/visualization/documentation/queries.html).
  * Tabla creada _inline_ en el código de la visualización con los siguientes datos: país, fecha del partido, puntos obtenidos y victoria de dicho país o no

**Código**:[motionChart.html](https://camon.googlecode.com/svn/trunk/visualizacion_google/motionChart.html)

**Resultado**:

&lt;wiki:gadget url="http://barriblog.com/taller/javascript/googleAPI/motionchart.xml" height="400" width="800" border="0" /&gt;


## Annotated Time Line ##

Este gráfico muestra el número de menciones de cada país en el tiempo. La unidad adoptada para expresar la granularidad del dato es de una hora (La referencia horaria es GMT)


<strong>Interactividad</strong>: Se puede modificar la escala temporal para ver la información con más detalle y avanzar o retroceder en el tiempo con la ayuda de la barra inferior.


**Fuente de datos**:
  * [Turkey2010\_hour\_count](https://spreadsheets.google.com/ccc?key=0AvqG-02OdbLbdGVqSmVMWThBc2lNUVRyV1l2V3lkNUE&hl=en#gid=0). Tabla _country\_hour\_count_. Tabla de datos que registra el número de menciones por hora y día de los países que recibieron más de 500 menciones en total durante el tiempo que duró el mundial.

**Código**:[annotatedTimeline.html](https://camon.googlecode.com/svn/trunk/visualizacion_google/annotatedTimeline.html)


**Resultado**:

&lt;wiki:gadget url="http://barriblog.com/taller/javascript/googleAPI/annotatedTimeLine.xml" height="950" width="1500" border="0" /&gt;



## Treemap ##

Esta visualización muestra las menciones que ha tenido cada uno de los jugadores de cada país. Se consigue una comparativa sobre el número de menciones a cada jugador teniendo en cuenta diversos criterios: su edad, altura, liga local, equipo local, país... Implícitamente también se puede sacar conclusiones sobre los países participantes en el mundial siguiendo los criterios anteriores.


<strong>Interactividad</strong>: Pulsando con el botón izquierdo del ratón en el primer nivel de clasificación aparece un nuevo <em>treemap</em> con el detalle de las menciones de sus jugadores. Para volver a la visualización inicial se debe hacer click en el botón derecho del ratón.

**Fuente de datos**:
  * [Turkey2010\_players](https://spreadsheets.google.com/ccc?key=0AvqG-02OdbLbdGNad1JfV1ZiOTdudndXcWVveWZjREE&hl=en#gid=0) Tabla _players\_pais_. Esta tabla registra la siguiente información sobre cada jugador: País, número de dorsal, nombre completo, nombre de pila, número de menciones, porcentaje del total que representa este número de menciones, edad, altura, posición en la que juega y el Club y la liga en los que juega normalmente.


**Código**:[treemap.html](http://barriblog.com/taller/javascript/googleAPI/treemap.html)

**Resultado**:


&lt;wiki:gadget url="https://camon.googlecode.com/svn/trunk/visualizacion\_google/gadgets/treemap.xml" height="2000" width="1000" border="0" /&gt;