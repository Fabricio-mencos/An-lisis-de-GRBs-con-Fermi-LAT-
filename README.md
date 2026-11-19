# Aprendizaje de herramientas de Fermi-LAT para el estudio de GRBs

Este repositorio tiene el informe final de mis prácticas en la Escuela de Ciencias Físicas y Matemáticas de
la USAC, supervisadas por el Dr. Rodrigo Sacahuí, junto con los cuadernos de Jupyter que usé para el análisis.

Durante las prácticas aprendí a usar Fermitools y XSPEC para analizar datos del LAT de Fermi. Primero
reproduje el análisis del GRB 080916C, que es el ejemplo del tutorial oficial y uno de los GRB más brillantes
que ha visto el LAT, para asegurarme de que todo funcionaba bien. Después analicé el GRB 251118A, que llegó
al LAT con muy pocos fotones (35 en la región, de los cuales unos 8 son del GRB), así que buena parte del
trabajo fue decidir cómo tratar el fondo. Al final mis resultados para este GRB salieron muy parecidos a los
de la circular GCN 42752, con un índice de −1.80 ± 0.30 y un flujo de (2.22 ± 1.03)×10⁻⁶ ph cm⁻² s⁻¹ por
encima de 100 MeV.

## Qué hay en cada carpeta

En `cuadernos/` están los dos análisis, uno por GRB. Cada cuaderno va paso a paso, desde los datos crudos
hasta el ajuste final, y explica para qué sirve cada herramienta.

En `informe/` está el informe en PDF y sus fuentes en LaTeX, por si alguien quiere compilarlo (pdflatex,
bibtex y dos veces más pdflatex).

En `correcciones/` está la versión del informe que revisó mi asesor, con sus anotaciones a mano, y una
transcripción de esas correcciones en Markdown que usé para ir aplicándolas.

## Para correr los cuadernos

Necesitas Fermitools instalado con conda (yo le puse `fermi` al entorno), XSPEC y Python con astropy,
numpy y matplotlib. Todas las gráficas las hice con Python, menos las de XSPEC.

Los archivos de datos no están en el repositorio porque pesan mucho. Se bajan del
[LAT Data Server](https://fermi.gsfc.nasa.gov/cgi-bin/ssc/LAT/LATDataQuery.cgi) y se guardan en una carpeta
`data/` al lado de cada cuaderno, como `FT1.fits` y `FT2.fits`. Yo usé estas consultas, ambas entre 100 MeV
y 300 GeV:

- GRB 080916C, centrado en RA 121.8°, Dec −61.3°, con radio de 40° y unos 2500 s alrededor del disparo
  (T0 = 243216766.614 s MET).
- GRB 251118A, centrado en RA 160.08°, Dec −34.58°, con radio de 30°, de 785189695 a 785194395 s MET.

Con esos dos archivos, cada cuaderno genera todo lo demás.
