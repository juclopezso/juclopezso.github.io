---
layout: post
title: "Algoritmo Scanline"
date: 2017-08-20
---


# Algoritmo Scanline
--------------------

También llamado como "scan conversion algorithm", es un tipo de renderizado hecho para aplicaciones 3D, el cual determina la forma en que los objetos de una escena van siendo proyectados.
Es uno de los sistemas más utilizados para las aplicaciones 3D.


## ¿Que es el renderizado?

La renderización es el proceso final de creación de una imagen foto realista desde un modelo 3D. En términos de visualización la renderización es un proceso de cálculo desarrollado por un equipo de computo destinado a generar una imagen 2D a partir de una escena 3D.
Se han desarrollado distintos métodos de representación que van desde wireframe no realistas a tráves de representaciones basadas en polígonos, hasta técnicas avanzadas como: **scanline**, radiosity o ray tracing.


## ¿En que consiste?

El algoritmo de Scanline consiste en detectar la intersección de los **scanlines** del dispositivos con los bordes de la primitiva. Por cada **scanline** rellena el espacio de píxeles que este entre cada par de intersrcciones.
Cuando el polígono es convexo y la figura es primitiva solo hay dos intersecciones por **scanline**.

![scanline1](https://image.ibb.co/nzqLr5/scanline_1.png "scanline_1")

En la imagen podemos ver ejemplos de los **scanlines** de las figuras primitivas y los puntos de intersección de cada **scanline** en las figuras.


## ¿Como funciona?

Primero se debe encontrar las intersecciones de los scanlines con con el polígono.
Ya encontradas las intersecciones se deben almacenar estos puntos en una estructura de datos, de forma ordenada ascendentemente en y y en x.
Después de esto se rellenan los spans o espacios usando la estructura.

![scanline2](https://image.ibb.co/kQhByk/scanline_2.png "scanline_2")

Se debe usar un criterio de **paridad** para saber cuando un intervalo debe ser rellenado, por ejemplo el intervado (x2, x3) debe ser rellenado, pero el intervalo (x3, x4) no, ya que sale de los bordes de la imagen.

![scanline3](https://image.ibb.co/d7CByk/scanline3.png "scanline_3")

Pero el método anterior tiene un fallo y es cuando calcula los **scanlines** en un vértice de la figura, lo que genera problemas de paridad en el algoritmo. 
Para solucionar este problema se aplica la siguiente regla.
Se cuenta el vértice Ymin de una arista en el cálculo de paridad pero no en el vértice Ymax, entonces un vértice Ymax se dibuja solo si equivale al vértice Ymin de la arista adyacente.

![scanline4](https://image.ibb.co/cEyjJk/scanline4.png "scanline_4")

Con esta misma regla para el caso de aristas horizontales, solo se quiere que se trace la linea de abajo de una figura, esto ocurrirá de forma automática con la regla propuesta.


## Ventajas y desventajas

- No es necesario traducir las coordenadas de los vértices de la memoria principal en la memoria de trabajo, sólo los vértices que definen los bordes del scanline necesitan estar en la memoria activa y cada vertice es leído solo una vez.
- Los pixeles visibles se procesan sólo una vez siendo benefiio para los casos de alta resolución.
- Este método funciona para polígonos convexos y cóncavos pero no funciona si el polígono se intersecta a si mismo.

## Media

Un video muy interesante donde se explica el algoritmo Scanline:

[![scanline_video](https://image.ibb.co/fzPAPQ/scanline.png)](https://www.youtube.com/watch?v=rrHVPrbsQYY&t=)

## Bibliografía

1. http://ccg.ciens.ucv.ve/~esmitt/cgI/II-2010/RellenoPoligonos.pdf
2. http://www.3dcadportal.com/rendering.html
4. https://es.slideshare.net/jdtorrespal/exposicin-scanline
5. https://en.wikipedia.org/wiki/Scan_line