#Taller de Pajek

# Introducción #

**[Pajek](http://pajek.imfm.si/doku.php)**  (_Pajek_ significa araña en esloveno) es un programa para **visualizar** y **analizar**  grandes redes. Fue desarrollado por [Vladimir Batagelj](http://vlado.fmf.uni-lj.si/vlado/vlado.htm) (matématico) y [Andrej Mrvar](http://mrvar.fdv.uni-lj.si/) (sociólogo).  Se empezó a desarrollar en noviembre 1996 y se implementó en Delphi (Pascal).

Tiene una [documentación](http://vlado.fmf.uni-lj.si/pub/networks/pajek/doc/pajekman.pdf)  extensa y un libro titulado [Exploratory Social Network Analysis with Pajek (Structural Analysis in the Social Sciences](http://www.amazon.com/gp/product/0521602629/104-4818949-5145535?v=glance&n=283155)

Funciona sobre plataformas Windows y es muy usado dentro del entorno de análisis de redes sociales. Se puede descargar el en su página de [downloads](http://pajek.imfm.si/doku.php?id=download)

# Características #
  * Permite seleccionar la forma y tamaño del nodo
  * El color se utiliza en [función del formato de exportación del gráfico](http://vlado.fmf.uni-lj.si/pub/networks/pajek/doc/epsdef.htm)
  * Tiene un conjunto de atributos configurables como el font, el color de y tamaño del font, etc.. La información se encuentra en el [manual de pajek](http://vlado.fmf.uni-lj.si/pub/networks/pajek/doc/pajekman.pdf) en punto _5.3 Exporting pictures to EPS/SVG – defining parameters in input file (page 72)_.
  * Es posible generar grafos en el tiempo.

# Data Set #

Desde [los Tweets obtenidos](http://code.google.com/p/camon/wiki/Datset) del pasado mundial de Baloncesto se han creado un conjunto de relaciones basadas en la mención, es decir los nombres de usuarios Twitter que aparecen en el texto del tweet. Dado que el tamaño de la red podría ser demasiado grande para la práctica se han seleccionado los nodos más mencionados y los nodos más activos. De estos dos conjuntos solo hay un elemento que está en ambos y que es @turkey2010, el community manager de la  [web del campeonato](http://www.fiba.com/pages/eng/fe/10/fwcm/p/index.html)


# Visualización #

## Datos de entrada ##

Los datos de entrada están en formato [aquí](https://docs.google.com/leaf?id=0B_qG-02OdbLbZDBmYjQ2ODAtOGM0MS00ZGUxLTk2MGQtMDE1ZjFhZTk0ZGE2&hl=en&authkey=CN_i8p0O)

Se han generado automáticamente desde los tweets seleccionados del Turkey2010 de la manera más sencilla posible. Se ha tratado de aplicar los atributos más necesarios para mejorar la visualización de la red.

Se ha adoptado un **convenio de color**, tamaño de los nodos, tamaño de las fechas y _timestamp_:
  * Los nodos **rojos** son los más mencionados y los **verdes** los más activos twiteando.
  * El tamaño de los nodos depende del número de enlaces entrantes y salientes.
  * El tamaño de los arcos depende del número de menciones entre los dos nodos.
  * A cada nodo se le asocia el _timestamp_ de su primera aparición en la red
  * Al conjunto de menciones entre cada par de nodos se le asocia el _timestamp_ de su primera aparición.
  * Se han eliminado los nodos que no tenían ninguna mención

## Layouts ##

  * **Circular** Estructura circular de los nodos con enlaces entre ellos.
  * **Energy Kamada-Kawai** es un layout _spring model_ que busca la mínima energía entre nodos.
  * **Energy Fruchterman-Reingold** es un layout _spring nodel_ que utiliza springs solo en los nodos conectados con un flecha y fuerzas repulsivas con el resto de los nodos.

## Formatos Salida ##

No exporta a los clásicos formatos de imágenes como jpg, png y gif, solo al formato bmp.

  * Exportación en 2D:
    * EPS/PS
    * SVG (las imágenes SVG pueden ser abiertas con el programa [InkScape](http://inkscape.org/?lang=es) para mejorar su presentación)
    * bmp
  * Exportación en 3D:
    * 3XD
    * VRML

# Práctica #

## Bajar el fichero .NET y arrancar programa ##
  1. Bajar el fichero NET: [turkey2010\_top\_mentions.net](https://docs.google.com/leaf?id=0B_qG-02OdbLbZDBmYjQ2ODAtOGM0MS00ZGUxLTk2MGQtMDE1ZjFhZTk0ZGE2&hl=en&authkey=CN_i8p0O)
  1. Abrir el programa pajek.exe
  1. Leer la red (**File >Network > Read**  > Abrir fichero turkey2010\_mentions.net )
  1. Seleccionar opción de menú **Draw > Draw**
  1. Ajustar Opciones de Visualización
    * Seleccionar **Options > Size > Of Vertices Defined in Input File**
    * Seleccionar **Options > Color > Vertices > As Defined in Input File**
  1. En la ventana de **Draw** seleccionar **Layout > circular > original**  (se verán muchos nodos que no tienen conexión, aunque no estaban en el fichero de entrada)
![http://www.barriblog.com/taller/redes/turkey2010_pajek_circular_todos.jpg](http://www.barriblog.com/taller/redes/turkey2010_pajek_circular_todos.jpg)

## Seleccionar solo los nodos que tiene conexión ##

Los nodos que no tienen relaciones con otros no son relevantes. Para eliminar las entidades que pudieran estar aisladas y mejorar los resultados del análisis, se ejecutan los comandos:
  * **Net > Partitions > Degree > All**
  * **Operations > Extract from Network > Partition > 1-`*`**
  * Seleccionar opción de menú **Draw > Draw**
  * En la ventana de **Draw** seleccionar **Layout > circular > original** (Se verán solo los nodos que tienen conexión).
![http://www.barriblog.com/taller/redes/turkey2010_pajek_circular.jpg](http://www.barriblog.com/taller/redes/turkey2010_pajek_circular.jpg)

## Visualizar los distintos layouts ##

En la ventana de Draw, seleccionar los distintos layouts y observar las diferencias entre las visualizaciones.

  * **Energy Kamada-Kawai**
![http://www.barriblog.com/taller/redes/turkey2010_pajek_kk.jpg](http://www.barriblog.com/taller/redes/turkey2010_pajek_kk.jpg)
  * **Energy Fruchterman-Reingold**
![http://www.barriblog.com/taller/redes/turkey2010_pajek_fd.jpg](http://www.barriblog.com/taller/redes/turkey2010_pajek_fd.jpg)

## Visualizar en 3D ##

Visualización realizada por **[Victor Caballero](http://www.vectart.com/)**, asistente al curso. El detalle de esta visualización los podéis encontrar en **[su blog](http://blog.vectart.com/2010/11/01/visualizando-conversaciones-con-pajek)**.

También ha realizado una interesantísima visualización de las líneas del **metro de Madrid** que explica con **[todo detalle](http://blog.vectart.com/2010/10/29/una-nueva-forma-de-ver-el-metro-de-madrid/)**


<a href='http://www.youtube.com/watch?feature=player_embedded&v=WPIngSvJAAI' target='_blank'><img src='http://img.youtube.com/vi/WPIngSvJAAI/0.jpg' width='425' height=344 /></a>
## Visualizar en el tiempo ##

Volver a la ventana principal y ejecutar el comando

  * Net > Transform > Generate in Time > all
    * Primer timestamp: 1
    * Ultimo timestamp: 17
    * pasos: 1
  * Seleccionar la red de **time 1**  (desplegable de networks)
  * Ir a la ventana de Draw y observar como la red va creciendo con el tiempo con la opción de **next**


## Exportar ##
Exportar a los distintos formatos de salida desde la ventana de **Draw**

  * Exportar a SVG la la serie temporal del grafo
    * Situarse en a red de tiempo 1
    * Seleccionar layout circular
    * Activar la opción  **Export  > 2D  > SVG > Current and All subsequent**
    * Exportar a SVG **Export > 2D > SVG >  General**

Debe generar un conjunto de páginas html que llevarán incrustado la imagen SVG, en la que se podrá navegar hacia adelante y hacia atrás, **[como en esta página](http://www.barriblog.com/taller/redes/turkey2010_pajek001.htm)**


## Guardar el trabajo realizado ##
  * **File  Pajek Project File > Save**