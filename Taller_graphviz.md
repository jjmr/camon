#Información para el taller de graphviz

# Introductión #

**[Graphviz](http://www.graphviz.org/)** es una aplicación y un conjunto de librerías **open source**  para dibujar gráficos. Está desarrollada por [investigadores de AT&T](http://www.graphviz.org/Credits.php) con algunas colaboraciones externas.

Los datos de entrada están en formato [DOT](http://en.wikipedia.org/wiki/DOT_language), permite realizar diferentes layouts y obtener la salida en diferentes formatos. Muestra  una [galería](http://www.graphviz.org/Gallery.php) de visualizaciones y los datos de entrada necesarios para realizarla.

Tiene una buena [documentación](http://www.graphviz.org/Documentation.php) y una interesante [FAQ](http://www.graphviz.org/doc/FAQ.html)

Funciona para plataformas unix/windows/mac y tiene disponible el código fuente. Tanto ejecutables como fuentes se se pueden descargar desde su página de [downloads](http://www.graphviz.org/Download..php)

# Caracteristicas #

  * Permite selecionar [la forma](http://www.graphviz.org/doc/info/shapes.html)
  * Utiliza _[The X11 color scheme](http://www.graphviz.org/doc/info/colors.html)_
  * Tiene un conjunto de [atributos configurables](http://www.graphviz.org/doc/info/attrs.html) como el font, el color de y tamaño del font, etc..
  * Es posible controlar, hasta cierto grado el tamaño de los grafos



# Data Set #

Desde [los tweets obtenidos](http://code.google.com/p/camon/wiki/Datset) del pasado mundial de Baloncesto se han creado un conjunto de relaciones basadas en la **mención**, es decir los nombres de usuarios twitter que aparecen en el texto del tweet. Dado que el tamaño de la red podría ser demasiado grande para la práctica se han seleccionado los nodos **más mencionados** y los nodos **más activos**. De estos dos conjuntos solo hay un elemento que está en ambos y que es **@turkey2010**, el community manager de la [web del campeonato](http://www.fiba.com/pages/eng/fe/10/fwcm/p/index.html)

# Filtros #

Si tenemos los datos en formato CSV separados por ; podríamos aplicar un par de filtros [awk](http://es.wikipedia.org/wiki/AWK) para convertirlo en formato dot.

Filtro 1: aplicado a la tabla de nodos:

```
# Datos de entrada: un fichero de texto con los datos de los nodos separados por tabulaciones 
#    posición de los datos
#    1:Id 2:Label 3:Group 4:Num Links 5:Links_in 6:links_out 7:Timestamp
# Solo se van a utilizar los  datos de las tres primeras comumnas
# Datos de salida: primera parte del fichero en formato dot 

BEGIN {
# Tratamiento inicial del filtro: se genera la cabecera del fichero dot
printf "digraph turkey2010 {\n"
printf "node [shape=plaintext];\n"
printf "edge [color=Grey];\n"
# limitación del tamaño del gráfico
printf "ranksep=\"1.0 equally\"\n"
printf "nodesep=\"1.0 equally\"\n"
flag_head="True"
}
{
# tratamiento para cada una de las filas del fichero

  if (flag_head=="False")
  {
    Id=$1
    Label= $2
    Group= $3

    printf "%s [label=\"%s\"];\n", Id,Label
    if (Group =="top_mentions")
      printf "%s [fontcolor=Red];\n",Id
    if (Group =="top_twitters")
      printf "%s [fontcolor=darkgreen];\n",Id
   }
   flag_head="False"
 
}
END {
# tratamiento final del fichero, no hay que hacer nada

}

```


Filtro 2: aplicado a la tabla de arcos:

```
# Datos de entrada: un fichero de texto con los datos de los arcos separados por tabulaciones 
#    posición de los datos
#    1:Source 2:Target 3:Weight 4:Timestamp
# Solo se van a utilizar los  datos de las dos primeras columnas
# Datos de salida: segunda parte del fichero en formato dot 

#tratamiento inicial
BEGIN {
flag_head="True"
}
{
# tratamiento para cada una de las filas del fichero
  if (flag_head == "False")
  {
    Source=$1
    Target= $2

    printf "\"%s\" ->\"%s\";\n", Source,Target
  }
  flag_head="False"
}   

END {
# tratamiento final del fichero, se inserta token de cierre
printf "}\n"

}


```

Cómo invocarlos:

```

awk -F";" -f node_tab2dot.awk  turkey2010_mentions_top_nodes.csv > turkey2010_top_mentions.dot
awk -F";" -f arc_tab2dot.awk  turkey2010_mentions_top_arcs.csv >> turkey2010_top_mentions.dot
```
# Visualización #

## Datos de entrada ##

Los datos de entrada están en formato DOT, y son acesibles [aquí](https://docs.google.com/document/d/12-obAlTglu7Gq_ZtKgOUqFOVdNPIwrgmSLu9afXzSuY/edit?hl=en&authkey=CNSKk9AB)

Se han generado automáticamente desde los tweets seleccionados del Turkey2010 de la manera más sencilla posible. Se ha evitado aplicar muchos atributos como font, fontsize, etc.. para que tome los valores por defecto.

Se ha adoptado un **convenio de color**: Los nodos **rojos** son los más mencionados y los **verdes** los más activos twiteando.

Se han eliminado los nodos que no tenían ninguna mención.

## Layouts ##

  * **dot** Estructura jerárquica, se dibuja de evitando que los arcos se crucen y pasen por encima de los nodos. No es eficiente en el espacio ocupado. Se puede ajustar el tamaño mínimo poniendo los parametros  "_ranksep="0.2 equally" y nodesep="0.2 equally_". (_ranksep_ es la distancia en vertical entre nodos y _nodesep_ es la distancia horizontal entre nodos, en pulgadas)
  * **neato** es un layout _spring model_ que busca la mínima energía entre nodos, basado en el algoritmo **Kamada-Kawai** (no se puede ajustar las distancia entre nodos con los parámetros _ranksep_ y _nodesep_)
  * **fdp** es un layout _spring nodel_ que utiliza springs solo en los nodos conectados con un flecha y fuerzas respulsivas con el resto de los nodos. Implementa el heurístico **Fruchterman-Reingold** (no se puede ajustar las distancia entre nodos con los parámetros _ranksep_ y _nodesep_).
  * **twopi** Dibuja un layout radial disponiendo los nodos concentricos a un nodo central en función de su distancia. En este caso _ranksep_ y _nodesep_ es la distancia radial
  * **circo** Dispone los nodos de forma circular (no se puede ajustar las distancia entre nodos con los parámetros _ranksep_ y _nodesep_).

## Formatos Salida ##

Permite los clasicos formatos de imágenes como jpg, png y gif así como Postscript (ps),o formatos estandarizados por el W3C como sgv, vml

# Prática #
  1. Bajar el fichero DOT: [turkey2010\_top\_mentions.dot](https://docs.google.com/document/edit?id=12-obAlTglu7Gq_ZtKgOUqFOVdNPIwrgmSLu9afXzSuY&hl=en&authkey=CNSKk9AB#) como texto
  1. Abrir el programa graphviz (GVedit.exe)
  1. Abrir fichero turkey2010\_top\_mentions.dot (en local)
  1. Seleccionar settings (Graphviz/settings) desde este formulario se pueden seleccionar el layout, el directorio de salida y el formato de salida. Por defecto toma como directorio de salida el mismo del que se encuentra el fichero de entarda .dot
  1. Seleccionar layout **dot**: y ejecutar. Se verá que el grafo es **muy grande**. Para ajustar tamaño poner los parámetros: **ranksep="0.2 equally" nodesep="0.2 equally**" debe quedar así:
![http://www.barriblog.com/taller/redes/turkey2010_mentions_dot.jpg](http://www.barriblog.com/taller/redes/turkey2010_mentions_dot.jpg)
  1. Seleccionar layout **neato** Como se ve, este layout no es muy adecuado a esta red y no podemos ajustar la distancia de los nodos.
![http://www.barriblog.com/taller/redes/turkey2010_mentions_neato.jpg](http://www.barriblog.com/taller/redes/turkey2010_mentions_neato.jpg)
  1. Seleccionar layout **fdp**. El gráfico debe quedar así:
![http://www.barriblog.com/taller/redes/turkey2010_mentions_fdp.jpg](http://www.barriblog.com/taller/redes/turkey2010_mentions_fdp.jpg)
  1. Seleccionar layout **twopi**. Para ajustar tamaño poner los parámetros: **ranksep="1.0 equally" nodesep="1.0 equally**". El resultado debe quedar así:
![http://www.barriblog.com/taller/redes/turkey2010_mentions_twopi.jpg](http://www.barriblog.com/taller/redes/turkey2010_mentions_twopi.jpg)
  1. Seleccionat layout **circo**. El layaout resultante no es muy adecuado para esta red y no se puede ajustar la distancia entre los nodos:

**Hacer scroll hacia abajo que la imagen que sale es enorme**
![http://www.barriblog.com/taller/redes/turkey2010_mentions_circo.jpg](http://www.barriblog.com/taller/redes/turkey2010_mentions_circo.jpg)


