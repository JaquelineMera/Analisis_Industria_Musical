# p2_validacion_hipotesis_spotify

# Laboratoria
Este proyecto tiene como objetivo confirmar o refutar hipótesis para identificar los factores que pueden llevar al éxito a un artista o a una canción. Mediante el análisis de datos y el uso de pruebas estadísticas, se pretende comprender las variables que influyen en el desempeño en plataformas de streaming y otros indicadores de popularidad musical.

# Temas

- [Introducción](#introducción)
- [Equipo](#equipo)
- [Herramientas](#herramientas)
- [Lenguajes](#lenguajes)
- [Procesamiento y análisis](#procesamiento-y-análisis)
  - [Procesamiento de los datos](#procesamiento-de-los-datos)
  - [Análisis exploratorio](#análisis-exploratorio)
  - [Validación de hipótesis](#validación-de-hipótesis)
- [Resultados](#resultados)
- [Conclusiones](#conclusiones)
- [Recomendaciones](#recomendaciones)

## Introducción
En el competitivo mundo de la industria musical, la capacidad de tomar decisiones basadas en datos se ha convertido en un activo invaluable. En este contexto, una discográfica se enfrenta al emocionante desafío de lanzar un nuevo artista en el escenario musical global, y cuenta con una poderosa herramienta: un extenso dataset de Spotify con información sobre las canciones más escuchadas en 2023.
La discográfica ha formulado una serie de hipótesis para entender qué hace que una canción sea más popular.

 + Las canciones con un mayor BPM (Beats Por Minuto) tienen más éxito en términos de cantidad de streams en Spotify.
 + Las canciones más populares en el ranking de Spotify también tienen un comportamiento similar en otras plataformas como Deezer.
 + La presencia de una canción en un mayor número de playlists se relaciona con un mayor número de streams.
 + Los artistas con un mayor número de canciones en Spotify tienen más streams.
 + Las características de la música influyen en el éxito en términos de cantidad de streams en Spotify.
 + Las canciones con más cantidad de veces en playlist de Spotify tienen un comportamiento similar en otras plataformas como Deezer o Apple.

La tarea de este proyecto es validar estas hipótesis mediante el análisis de datos y proporcionar recomendaciones estratégicas basadas en los hallazgos, con el objetivo final de aumentar las posibilidades de éxito del nuevo artista.
## Equipo
Jaqueline Mera y Ximena Castillo
## Herramientas
+ BigQuery 
+ Google Colab 
+ Power BI
## Lenguajes
+ SQL
+ Python
## Procesamiento y análisis
El flujo de trabajo incluyó varias etapas, el procesamiento de los datos, el análisis exploratorio y la validación de hipótesis.

## Procesamiento de los datos
El procesamiento de los datos, se llevó a cabo en BigQuery a partir de comandos SQL, se siguieron los siguientes pasos:
+ Identificar valores nulos a través COUNT, WHERE y IS NULL.
+ Identificar duplicados a través de comandos SQL COUNT, GROUP BY, HAVING.
Manejar variables que no son útiles para el análisis a través de comandos SQL SELECT EXCEPT.
Identificar datos discrepantes en variables categóricas utilizando comandos de manejo de string, como REGEXP.
Identificar datos discrepantes en variables numéricas utilizando comandos como MAX, MIN y AVG.
Comprobar y modificar tipos de datos, cuando es necesario, utilizando CAST.
Crear nuevas variables utilizando CONCAT y SUM.
Construir tablas auxiliares utilizando WITH.
Unir las tablas utilizando LEFT JOIN.
+ 
+ 
+

## Análisis exploratorio

## Validación de hipótesis
Se plantearon las siguientes hipótesis...

## Resultados
Los resultados obtenidos...

## Conclusiones
A partir de los resultados, se pueden extraer las siguientes conclusiones...

## Recomendaciones


~~~
