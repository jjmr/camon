#Taller de visualizacin de TouchGraph

# Introducción #

**[Touchgraph](http://www.touchgraph.com/navigator.html)** es un programa comercial para visualizar relaciones.

Funciona sobre Java y por tanto es multiplataforma

# Características #
  * Interfaz intuitiva
  * Admite  [Múltiples formatos de entrada](http://gephi.org/users/supported-graph-formats/), entre ellos excel con varias pestañas
  * Es muy sencillo de utilizar
  * Sirve para grandes grafos y es capaz de identificar comunidades
  * Se pueden asociar imágenes a los nodos y  representa las propiedades mediante un halo semitransparente


# Funcionalidades #
  * **Interactividad**: Permite interactuar con el grafo ver la conectividad de cada nodo de forma visual.
  * **layout**:Tiene algoritmos de layout de force based, se le puede ajustar los parámetros
  * **Color**: El color del los nodos se puede aplicar por atributos
  * **Tamaño nodos/enlaces**: El tamaño de los nodos y los enlaces se puede representar según su importancia mediante halos


# Data Set #

Desde [los Tweets obtenidos](http://code.google.com/p/camon/wiki/Datset) del pasado mundial de Baloncesto se han creado un conjunto de relaciones basadas en la mención, es decir los nombres de usuarios Twitter que aparecen en el texto del tweet. Dado que el tamaño de la red podría ser demasiado grande para la práctica se han seleccionado los nodos que han tenido más de **5 menciones**. En este data set hay tres grupos de usuarios: Los **más mencionados**, los **más activos** y los **usuarios normales**.


# Visualización #

## Datos de entrada ##

Los datos de entrada están en formato xls, [los nodos y enlaces](http://barriblog.com/taller/redes/turkey2010_mentions.xls)



## Layouts ##

  * **Base forced** Con fuerzas de atracción y repulsión que se pueden ajustar

## Formatos Salida ##
  * png
  * jpg



# Práctica #

## Bajar los ficheros entrada y abrir programa ##

  * Bajar los ficheros en formato xls:  [los nodos y enlaces](http://barriblog.com/taller/redes/turkey2010_mentions.xls)
  * Abrir el programa touchgraph
  * Seleccionar File > Open Wizard que nos ayuda a cargar los datos
    * Formulario select Input: subir fichero turkey2010\_mentions.xls en la casilla de file xls y pulsar **Configure**, aparecerá esta ventana:

> ![http://www.barriblog.com/taller/redes/touchgraph_input.jpg](http://www.barriblog.com/taller/redes/touchgraph_input.jpg)
    * En el Menú del Loading Wizard seleccionar Entities & Relations
    * Añadimos las entidades (nodos) seleccionando en la hoja de cálculo la tabla **Most\_mentions\_nodes**.  Marcamos la primera columna de la tabla(Id) como **Ent Id**  y el resto de columnas como **Atrib**

> ![http://www.barriblog.com/taller/redes/touchgraph_input_nodes.jpg](http://www.barriblog.com/taller/redes/touchgraph_input_nodes.jpg)
    * Añadimos las relaciones (Enlaces)  seleccionando en la hoja de cálculo la tabla **Most\_mentions\_arcs**.  **MUY IMPORTANTE** marcamos cuales son las entidades de la relación rellenando las casillas: **Src Entity** y **Dest entity** y **Direction** como directed. Marcamos la primera columna  (Source) de la tabla como **Src Id**  y la segunda (Target) como **Dest Id**, el resto lo marcamos como  **Atrib** damos OK

> ![http://www.barriblog.com/taller/redes/touchgraph_input_links.jpg](http://www.barriblog.com/taller/redes/touchgraph_input_links.jpg)

  * Salvamos el proyecto y pulsamos **Load**, Aparecerá el grafo sin expandir:

> ![http://www.barriblog.com/taller/redes/touchgraph_load.jpg](http://www.barriblog.com/taller/redes/touchgraph_load.jpg)

  * Expandir el grafo al máximo, connected components **All** y le dejamos que se aplique el layout.

> ![http://www.barriblog.com/taller/redes/touchgraph_all.jpg](http://www.barriblog.com/taller/redes/touchgraph_all.jpg)

  * Darle color a los nodos. Seleccionar **Settings > Node Apparence > Color** , seleccionar color por grupo:
    * Usuarios normales **gris**
    * Más mencionados **rojo**
    * Más activos **verdes**.


![http://www.barriblog.com/taller/redes/touchgraph_al_colorsl.jpg](http://www.barriblog.com/taller/redes/touchgraph_al_colorsl.jpg)

> Probar con otros atributos


  * Apariencia de los enlaces: Seleccionar **Settings > Edge apparence**. Poner los enlaces según su peso
  * Tamaño y forma del nodo: Seleccionar **Settings > Halo Size/Shape**. Probar con varios atributos, por ejemplo con el número de enlaces y halo redondo:

> ![http://www.barriblog.com/taller/redes/touchgraph_al_color_halol.jpg](http://www.barriblog.com/taller/redes/touchgraph_al_color_halol.jpg)

  * Ajustar el layout: **Seleccionar Settings > Graph layout** y ajustar la fuerza de repulsión del nodo y de tensión de las relaciones.
  * Probar los Halos con los distintos atributos



## Exportar ##
  1. Exportar el gráfico **File > Export > Image**


## Guardar el trabajo realizado ##
  * Salvar el proyecto **File > Save**