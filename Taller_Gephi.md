#Taller de visualizacin en Gephi

# Introducción #

**[Gephi](http://gephi.org/)** es una plataforma Open Source para el análisis y visualización de redes. Actualmente es un [Consorcio](http://consortium.gephi.org/) para garantizar el desarrollo de la plataforma.

> Funciona sobre Java y por tanto es multiplataforma

> Vídeo de la versión =0.7


<a href='http://www.youtube.com/watch?feature=player_embedded&v=bXCBh6QH5W0' target='_blank'><img src='http://img.youtube.com/vi/bXCBh6QH5W0/0.jpg' width='425' height=344 /></a>

# Características #
  * Interfaz intuitiva
  * Admite  [Múltiples formatos de entrada](http://gephi.org/users/supported-graph-formats/), el suyo propio GEXF, los hererdados NET y DOT , CSV y otros más
  * Customizable por plugins
  * [Muy buena documentación](http://gephi.org/users/)
  * En evolución constante, actualmente en la versión 0.7
  * Tiene detrás una comunidad

# Funcionalidades #
  * **Interactividad**: Permite interactuar con el grafo, creando grupos de nodos, comprimiéndolos y expandiéndolos, ver la conectividad de cada nodo de forma visual.
  * **layout** :Tiene algoritmos de layout de force based y Multi level
  * **Color**: El color del los nodos se puede aplicar por paticiones o por ranking
  * **Tamaño nodos/enlaces**: El tamaño de los nodos y los enlaces se puede representar según su importancia
  * Tiene un conjunto de atributos configurables como el font, el color de y tamaño del font, etc..
  * Es posible generar grafos dinámicos en función del tiempos del enlace (requiere formato GDF).

# Data Set #

Desde [los Tweets obtenidos](http://code.google.com/p/camon/wiki/Datset) del pasado mundial de Baloncesto se han creado un conjunto de relaciones basadas en la mención, es decir los nombres de usuarios Twitter que aparecen en el texto del tweet. Dado que el tamaño de la red podría ser demasiado grande para la práctica se han seleccionado los nodos que han tenido más de **5 menciones**. En este data set hay tres grupos de usuarios: Los **más mencionados**, los **más activos** y los **usuarios normales**.


# Visualización #

## Datos de entrada ##

Para evitar complicaciones en la conversión a otro formato propuse que en el taller la entrada fuera en formato CSV, un formato ampliamente usado en otras herramientas, [los nodos](http://barriblog.com/taller/redes/turkey2010_mentions_most_nodes.csv) y [los enlaces](http://barriblog.com/taller/redes/turkey2010_mentions_most_arcs.csv). Al hacer la práctica  de las particiones, no funcionó bien porque el programa no entendía los atributos del nodo, por ejemplo el grupo al que pertenecía el nodo( Top\_mentions: grupo de los 50 usuarios más mencionados, Top\_twitters grupo de los más activos y normales, el resto de usuarios). Consulté el foro de Gephi vi que los  CSV no
[sirven cuando se quiere importar las propieddaes del nodo](http://forum.gephi.org/viewtopic.php?f=29&t=577)
Para dejar la práctica funcionando al 100% los datos de entrada estarán en formato GDF, que es un formato muy sencillo, casi como el CSV. Por tanto el fichero de entrada será:
Turkey2010\_most\_mentions.gdf




## Layouts ##

  * **Base forced** Con fuerzas de atracción y repulsión que se pueden ajustar
  * **Multilevel**




## Formatos Salida ##
  * SVG
  * PDF



# Práctica #

## Bajar los ficheros entrada y abrir programa ##

  * Bajar los ficheros en formato GDF:  [turkey2010\_mentions\_most\_nodes.gdf](http://barriblog.com/taller/redes/turkey2010_mentions_most_nodes.gdf)
  * Abrir el programa gephi
  * Abrir un nuevo proyecto **File > Open** En la esquina inferior derecha pondrá workspace  0 (puede haber más de un workspace). Aparecerá una ventana como esta:
![http://www.barriblog.com/taller/redes/turkey2010_gephi_read.jpg](http://www.barriblog.com/taller/redes/turkey2010_gephi_read.jpg)


  * Si no aparece abierta la ventana **Graph**, abrirla con  **Window > Graph**.

```
*nota*: El zoom del grafo se hace con la rueda del ratón y se mueve pulsando el botón derecho a la vez que se mueve el ratón. 
        La ventana Graph es interactiva y cualquier cambio que se aplique al grafo queda reflejado. 
        Se puede actuar sobre los nodos directamente con el ratón.
```

> Debe salir algo así:

![http://www.barriblog.com/taller/redes/turkey2010_gephi_sin_layaout.jpg](http://www.barriblog.com/taller/redes/turkey2010_gephi_sin_layaout.jpg)


  * Para dale forma al grafo, abrir la ventana de layout **Window > Layout** y  elegir un layout. En este caso se ha elegido **Force Atlas**.

> Tendrá este aspecto:

![http://www.barriblog.com/taller/redes/turkey2010_gephi_force_atlas_bn.jpg](http://www.barriblog.com/taller/redes/turkey2010_gephi_force_atlas_bn.jpg)

  * Para darle color y tamaños a los nodos según la importancia, abrir la ventana  **Window > Ranking**
    * **Tamaño**: En la pestaña de **Nodes**, pulsar el **diamante**, elegir en el desplegable **Degree** (Número de enlaces del nodo) y establecer el tamaño entre 5 y 20. Pulsar **Apply**. Observar cómo cambian de tamaño los nodos (usar zoom si no se aprecia bien en la vista del grafo).

> Así se verá el tamaño:
![http://www.barriblog.com/taller/redes/turkey2010_gephi_force_atlas_tamanio.jpg](http://www.barriblog.com/taller/redes/turkey2010_gephi_force_atlas_tamanio.jpg)
    * **Color**: En la misma pestaña, pulsar en color, elegir la gama de color y pulsar **Apply**.

> Así se verá el color:

![http://www.barriblog.com/taller/redes/turkey2010_gephi_force_atlas_color.jpg](http://www.barriblog.com/taller/redes/turkey2010_gephi_force_atlas_color.jpg)

  * Para ver cual será el aspecto final, abrir las ventanas de previsualización **Window > Preview** y **Window > Preview settings**.

`   *Nota*: La ventana de preview no es interactiva.`

> Pulsar en **Refresh** y Tendrá este aspecto:


![http://www.barriblog.com/taller/redes/turkey2010_gephi_force_atlas_color_preview.jpg](http://www.barriblog.com/taller/redes/turkey2010_gephi_force_atlas_color_preview.jpg)

  * Para darle color a los nodos según una agrupación, abrir la ventana  **Window > Partition**. Aparecen los distintos grupos (Si no aparece ninguno pulsar en el icono de refrescar). Elegir **Group** Pulsar **Apply** y se verá como ahora los nodos están coloreados según los grupos por estos colores:
    * **Rojo** Los más mencionados
    * **Azul** los más activos (que más han twiteado)
    * **verde** El resto

> Esta es la previsualización resultante:
![http://www.barriblog.com/taller/redes/turkey2010_gephi_force_atlas_group.jpg](http://www.barriblog.com/taller/redes/turkey2010_gephi_force_atlas_group.jpg)

> ¿Pero que es esa mancha grande de la izquierda?

> Es una celebrity (Justin Bieber) que ha tenido muchísimas menciones de un fan.

> Este sería el zoom:

![http://www.barriblog.com/taller/redes/turkey2010_gephi_force_atlas_justin_bieber.jpg](http://www.barriblog.com/taller/redes/turkey2010_gephi_force_atlas_justin_bieber.jpg)

  * Para filtrar nodos del grafo, abrir la ventana de filtros **Window > Filters**. En la ventana de **Filters** aparecen todas las opciones de filtrado de nodos. Vamos a ver dos casos:
    * **Filtrado por enlaces**: Seleccionar  **Library >Topology > Degree Range** y moviendo la barra inferior para ajustar el rango de enlaces del nodo y pulsando **Filter** se verá como va cambiando el grafo conforme movemos la barra inferior.  Este es el grafo resultante de filtrar 7 - 132:
![http://www.barriblog.com/taller/redes/turkey2010_gephi_force_atlas_filter.jpg](http://www.barriblog.com/taller/redes/turkey2010_gephi_force_atlas_filter.jpg)

  * **Filtrado por grupos**: Seleccionar **Attributes > Partition > Grupos**. Si se selecciona **Mentions** y **Twitter**  y se le hacen algunos ajustes en los setting de previsualización:
  * Backgroud negro
  * Hacer visibles las etiquetas de los nodos
  * Poner las etiquetas en color blanco
  * Poner tamaño de letra de las etiquetas en 24

> Puede quedar algo asi:


![http://www.barriblog.com/taller/redes/turkey2010_gephi_force_atlas_filter_group.jpg](http://www.barriblog.com/taller/redes/turkey2010_gephi_force_atlas_filter_group.jpg)
  1. Finalmente, mirar las estadísticas **Windows > Statistics**




## Exportar ##
  1. Exportar el gráfico File > Export


## Guardar el trabajo realizado ##
  * Salvar el proyecto File > Save