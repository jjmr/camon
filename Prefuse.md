# Introducción #
Prefuse es un framework para la realización de visualizaciones en java. Tiene licencia Open Source y proporciona un gran conjunto de componentes extensibles al desarrollador.

En esta sección presentaremos los ejemplos utilizados en el taller de visualización.

# Ejemplos #
A continuación se exponen los distintos ejemplos utilizados a lo largo del curso. Para probar su funcionamiento hay dos alternativas:
  1. Acceder a la sección de descargas:
    * Descargar el fichero prefuse-camon\_v1.zip
    * Crear un proyecto Eclipse a partir del proyecto descargado
    * Acceder al directorio demos/prefuse/demos/curso y seleccionar la opción "Run as Java application" sobre el ejemplo seleccionado.
  1. Añadir el ejemplo a partir de la url especificada en cada ejemplo a un proyecto ya existente de prefuse.

## Tree Map ##
  * Fuente de datos: Hoja de datos por jugador [turkey2010\_players](https://spreadsheets.google.com/ccc?key=0AvqG-02OdbLbdGNad1JfV1ZiOTdudndXcWVveWZjREE&hl=en#gid=0), tabla Players\_pais.
  * [Datos adaptados al ejemplo](https://camon.googlecode.com/svn/trunk/visualizacion_java/data/turkey2010_players.csv)
  * [Código del ejemplo](https://camon.googlecode.com/svn/trunk/visualizacion_java/code/TreeMap.java)


## Stacked Chart ##
  * Fuente de datos: Hoja de datos totales por día [turkey2010\_day\_count](https://spreadsheets.google.com/ccc?key=0AvqG-02OdbLbdE41c2RTWkRDdkx5M3NiZHB2WVhELVE&authkey=CPHt-pcF&hl=en#gid=4), tabla keywords\_day\_count.
  * [Datos adaptados al ejemplo](https://camon.googlecode.com/svn/trunk/visualizacion_java/data/turkey2010_day_count.csv)
  * [Código del ejemplo](https://camon.googlecode.com/svn/trunk/visualizacion_java/code/StackedChart.java)


## Graph View ##
  * Fuente de datos: Hoja de datos de menciones a autores [turkey2010\_mentions](https://spreadsheets.google.com/ccc?key=0AvqG-02OdbLbdGFoeHcxNm9qczBRWl9LWFFIamFILUE&hl=en&authkey=CIHiuYgI#gid=1), tabla most\_mentions.
  * Datos adaptados al ejemplo: [nodos](https://camon.googlecode.com/svn/trunk/visualizacion_java/data/turkey2010_most_mentions_nodes.csv) y [arcos](https://camon.googlecode.com/svn/trunk/visualizacion_java/data/turkey2010_most_mentions_arcs.csv)
  * [Código del ejemplo](https://camon.googlecode.com/svn/trunk/visualizacion_java/code/GraphViewAll.java)


## Graph View (top menciones) ##
  * Fuente de datos: Hoja de datos de menciones a autores [turkey2010\_mentions](https://spreadsheets.google.com/ccc?key=0AvqG-02OdbLbdGFoeHcxNm9qczBRWl9LWFFIamFILUE&hl=en&authkey=CIHiuYgI#gid=1), tabla top\_mentions.
  * Datos adaptados al ejemplo: [nodos](https://camon.googlecode.com/svn/trunk/visualizacion_java/data/turkey2010_top_mentions_nodes.csv) y [arcos](https://camon.googlecode.com/svn/trunk/visualizacion_java/data/turkey2010_top_mentions_arcs.csv)
  * [Código del ejemplo](https://camon.googlecode.com/svn/trunk/visualizacion_java/code/GraphViewTOP.java)

## Radial Graph View ##
  * Fuente de datos: Hoja de datos de menciones a autores [turkey2010\_mentions](https://spreadsheets.google.com/ccc?key=0AvqG-02OdbLbdGFoeHcxNm9qczBRWl9LWFFIamFILUE&hl=en&authkey=CIHiuYgI#gid=1), tabla top\_mentions.
  * Datos adaptados al ejemplo: [nodos](https://camon.googlecode.com/svn/trunk/visualizacion_java/data/turkey2010_top_mentions_nodes.csv) y [arcos](https://camon.googlecode.com/svn/trunk/visualizacion_java/data/turkey2010_top_mentions_arcs.csv)
  * [Código del ejemplo](https://camon.googlecode.com/svn/trunk/visualizacion_java/code/GraphViewTOP.java)