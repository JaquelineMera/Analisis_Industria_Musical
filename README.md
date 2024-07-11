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
+ Identificar valores nulos a través COUNTIF e IS NULL.
+ Identificar duplicados a través de COUNT, GROUP BY, HAVING.
+ Manejar variables que no son útiles en el análisis a través de EXCEPT.
+ Identificar datos discrepantes en variables categóricas con REGEXP_REPLACE.
+ Identificar datos discrepantes en variables numéricas con MAX, MIN y AVG.
+ Comprobar y modificar tipos de datos con SAFE_CAST y CAST.
+ Crear nuevas variables utilizando CONCAT, SUM y DATE. 
+ Construir tablas auxiliares utilizando WITH.
+ Unir las tablas utilizando LEFT JOIN.

## Análisis exploratorio
+ Agrupar datos según variables categóricas a través de tablas
+ Visualizar las variables categóricas a través de gráficos de barras y líneas 
+ Aplicar medidas de tendencia central en BPM, Playlists y Streams
+ Aplicar medidas de dispersión BPM, Playlists y Streams
+ Visualizar distribución a través de Hitogramas BPM, Playlists y Streams
  
## Validación de hipótesis
La validación de hipótesis se llevó a cabo en BigQuery y Google Colab
+ Análisis de correlación entre métricas (Coeficiente de Pearson)
+ Test estadísticos Test T y Test Mann–Whitney U (Wilcoxon)
  + Calcular cuartiles en características técnicas
  + Segmentación de características técnicas en grupos "alto" y "bajo"
  + Visualizar distribución de las características técnicas (histogramas y gráficos de densidad)
  + Aplicación de Test estadísticos a partir de la distribución
    +  Se aplico el Test Mann–Whitney U (Wilcoxon), los datos no siguen una distribución normal
+ Regresión Lineal Simple
  + Error Cuadrático Medio (MSE)
  + Coeficiente de Determinación (R²)
  + Precisión del modelo

## Resultados
### Validación de hipótesis
  + H1: Las canciones con un mayor BPM (Beats Por Minuto) tienen más éxito en términos de cantidad de streams en Spotify.
    + **Conclusión**: No hay relación lineal significativa entre los BPM de una canción y su popularidad  en términos de streams.
      + *Coeficiente de Pearson* (-0.0023): Hay una correlación negativa extremadamente débil (casi nula).
      + *Test Mann-Whitney U - Valor P* (0.4395): No hay una diferencia significativa entre las categorías 'alto' y 'bajo‘.
      + *Regresión lineal simple*: Modelo Inadecuado, no hay una relación lineal significativa entre BPM y Streams; Coeficiente de determinación R² (-0.0013).
  + H2: Las canciones más populares en el ranking de Spotify también tienen un comportamiento similar en otras plataformas como Deezer.
    + **Conclusión**: Las canciones que son populares en los ranking de Spotify también tienden a ser populares en otras plataformas como Deezer, Apple y Shazam. Sin embargo, el modelo de regresión lineal no puede usarse como modelo predictivo pues solo explica el 30% de esta variabilidad en Deezer y el 14% en Apple y Shazam.
      +  *Coeficiente de Pearson* (Dezzer 0.6051; Apple 0.5518; Shazam 0.6056): Existe una correlación positiva moderada entre el ranking de las canciones en Spotify y otras plataformas.
      +  *Regresión lineal simple*: Relación moderada entre la presencia en los charts de Spotify y otras plataformas. Sin embargo, un R² 0.303 indica en Deezer que el 30.3% de la variabilidad en "In Spotify Charts" puede explicarse por "In Deezer Charts“. Para Apple el R² es de 0.1403 y para Shazam de 0.1407
  + H3: La presencia de una canción en un mayor número de playlists se relaciona con un mayor número de streams.
  + H4: Los artistas con un mayor número de canciones en Spotify tienen más streams.
  + H5: Las características de la música influyen en el éxito en términos de cantidad de streams en Spotify.
  + H6: Las canciones con más apariciones en playlist de Spotify tienen un comportamiento similar en otras plataformas como Deezer o Apple.
## Conclusiones
A partir de los resultados, se pueden extraer las siguientes conclusiones...

## Recomendaciones


~~~
