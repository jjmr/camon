Taller impartido por **Ana Belén García Parra**

# Introducción #
Protovis es una librería gráfica javascript orientada a la realización de visualizaciones, que proporciona al desarrollador un gran conjunto de componentes y herramientas y otorga al mismo la posibilidad de personalizar sus visualizaciones con un **control detallado**, permitiéndole abstraerse de las tareas básicas de creación de gráficas.


# Visualización #
A continuación se presentan los distintos ejemplos realizados con Protovis. Para poder visualizar los ejemplos únicamente es necesario descargar el código a partir del enlace proporcionado en cada ejemplo y abrirlo con un navegador web (Firefox,...).

La fuente de datos indicada en cada uno de los ejemplos será de utilidad para comprobar el formato de los mismos. Sin embargo, modificaciones en dichos datos no redundarán en modificaciones en las visualizaciones, ya que los ejemplos tienen una adaptación de dichos datos incluidos en el código fuente. Esto es debido a que Protovis no proporciona ningún método de interacción con Google Spreadsheets

## Tree Map ##
Al igual que el <em>treemap</em> del <strong>Google API</strong>, esta visualización muestra las menciones que ha tenido cada jugador de cada país, pero con otra interactividad. En la parte superior derecha aparece la siguiente información numérica asociada a la visualización: Nº de jugadores, nº de menciones y porcentaje de los datos mostrados.

<strong>Interactividad</strong>: En la parte inferior izquierda permite realizar búsquedas, tanto por países como por jugadores tecleando el nombre. Conforme se escribe se van adaptando los colores del <em>treemap</em> para resaltar el dato buscado a la vez que se actualiza la información numérica de la parte superior derecha.

**Fuente de datos**
  * Hoja con los datos de los jugadores del mundial [turkey\_2010\_players](https://spreadsheets.google.com/ccc?key=0AvqG-02OdbLbdGNad1JfV1ZiOTdudndXcWVveWZjREE&hl=en#gid=0). Tabla players\_pais.

**Codigo del ejemplo**:  [treemap.html](https://camon.googlecode.com/svn/trunk/visualizacion_protovis/treemap-full.html)

**Resultado**

&lt;wiki:gadget url="http://barriblog.com/taller/javascript/protovis/treemap-full.xml" width="900" height="600" border="0" /&gt;

## Bubble Chart ##

Con el mismo código de color por país que el anterior <em>treemap</em> se muestran las menciones de todos los jugadores a la vez con una colocación aleatoria, representadas por una burbuja cuyo tamaño es proporcional al número de veces en que fueron citados.
<strong>Interactividad</strong>: Pasando el ratón por cada burbuja indica el nombre del jugador, el país al que pertenece y el número de menciones que ha obtenido.

**Fuente de datos**

  * Hoja con los datos de los jugadores del mundial [turkey\_2010\_players](https://spreadsheets.google.com/ccc?key=0AvqG-02OdbLbdGNad1JfV1ZiOTdudndXcWVveWZjREE&hl=en#gid=0). Tabla players\_pais.

**Código del ejemplo**: [bubblechart.html](https://camon.googlecode.com/svn/trunk/visualizacion_protovis/bubble-chart.html)

Resultado:


&lt;wiki:gadget url="http://barriblog.com/taller/javascript/protovis/bubble\_chart.xml" width="625" height="475" border="0" /&gt;

## Stream Graph ##

Se muestran las menciones de todos las palabras clave con las que se han seleccionado los tweets.

<strong>Interactividad</strong>: No tiene

**Fuente de datos^**
  * Hoja con los datos de las menciones por hora [turkey\_2010\_hour\_count](https://spreadsheets.google.com/ccc?key=0AvqG-02OdbLbdGVqSmVMWThBc2lNUVRyV1l2V3lkNUE&hl=en#gid=4). Tabla keywords\_hour\_count.

**Código del ejemplo**: [streamgraph.html](https://camon.googlecode.com/svn/trunk/visualizacion_protovis/streamgraph-full.html)

Resultado:


&lt;wiki:gadget url="http://barriblog.com/taller/javascript/protovis/streamgraph.xml" width="625" height="475" border="0" /&gt;