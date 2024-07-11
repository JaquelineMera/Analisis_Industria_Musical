# p2_validacion_hipotesis_spotify

# Laboratoria: Validación de Hipótesis
Este proyecto tiene como objetivo confirmar o refutar hipótesis para identificar los factores que pueden llevar al éxito a un artista o a una canción. Mediante el análisis de datos y el uso de pruebas estadísticas, se pretende comprender las variables que influyen en el desempeño en plataformas de streaming y otros indicadores de popularidad musical.

![Caratula](caratula_spotify.jpeg)

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
- [Pasos a seguir](#pasos-a-seguir)
- [Enlaces](#enlaces)

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
  + **H1**: Las canciones con un mayor BPM (Beats Por Minuto) tienen más éxito en términos de cantidad de streams en Spotify.
    + **Conclusión**: No hay relación lineal significativa entre los BPM de una canción y su popularidad  en términos de streams.
      + *Coeficiente de Pearson* (-0.0023): Hay una correlación negativa extremadamente débil (casi nula).
      + *Test Mann-Whitney U - Valor P* (0.4395): No hay una diferencia significativa entre las categorías 'alto' y 'bajo‘.
      + *Regresión lineal simple*: Modelo Inadecuado, no hay una relación lineal significativa entre BPM y Streams; Coeficiente de determinación R² (-0.0013).
![Hipótesis 1](/images/Diapositiva1.PNG)
  + **H2**: Las canciones más populares en el ranking de Spotify también tienen un comportamiento similar en otras plataformas como Deezer.
    + **Conclusión**: Las canciones que son populares en los ranking de Spotify también tienden a ser populares en otras plataformas como Deezer, Apple y Shazam. Sin embargo, el modelo de regresión lineal no puede usarse como modelo predictivo pues solo explica el 30% de esta variabilidad en Deezer y el 14% en Apple y Shazam.
      +  *Coeficiente de Pearson* (Dezzer 0.6051; Apple 0.5518; Shazam 0.6056): Existe una correlación positiva moderada entre el ranking de las canciones en Spotify y otras plataformas.
      +  *Regresión lineal simple*: Relación moderada entre la presencia en los charts de Spotify y otras plataformas. Sin embargo, un R² 0.303 indica en Deezer que el 30.3% de la variabilidad en "In Spotify Charts" puede explicarse por "In Deezer Charts“. Para Apple el R² es de 0.1403 y para Shazam de 0.1407
![Hipótesis 2](/images/Diapositiva2.PNG)
  + **H3**: La presencia de una canción en un mayor número de playlists se relaciona con un mayor número de streams.
    + **Conclusión**: La inclusión en playlists es un factor importante que impulsa el número de streams de una canción. El modelo de regresión lineal puede usarse como modelo predictivo, nos explica el 67% de los casos.
      + *Coeficiente de Pearson* (0.7833): Existe una fuerte correlación positiva entre el número de streams y la cantidad de veces que una canción aparece en playlists. 
      + *Regresión lineal simple*: Relación fuerte entre el número de "Total playlist" y "Streams". Un R² de aproximadamente 0.670 indica que el 67% de la variabilidaden "Streams" puede explicarse por "Total playlist".
![Hipótesis 3](/images/Diapositiva3.PNG)
  + **H4**: Los artistas con un mayor número de canciones en Spotify tienen más streams.
    + **Conclusión**: A medida que el número de canciones de un artista aumenta, el total de streams también tiende a aumentar . Sin embargo, el modelo de regresión lineal no es adecuado para predecir el total de streams basándose en el total de canciones, puesto que existen muchos casos de canciones únicas con alta cantidad de streams.
      + *Coeficiente de Pearson*(-0.0536): Existe una correlación positiva fuerte entre el total de streams y el total de canciones.
      + *Regresión lineal simple*: El modelo no es adecuado para predecir "Total streams" basándose en "Total canciones". Coeficiente de determinación R² (-0.0536)
![Hipótesis 4](/images/Diapositiva4.PNG)
  + **H5**: Las características de la música influyen en el éxito en términos de cantidad de streams en Spotify. Aplicable en “Danceability y Speechiness”
    + **Conclusión**: La bailabilidad y número de elementos hablados en una canción tiene muy poco en la popularidad medida por streams. A valores bajos de estas características, ligeramente hay más streams.
      + *Coeficiente de Pearson* (Danceability -0.1055; Speechiness -0.1128): Hay una correlación negativa débil entre el número de streams, la bailabilidad y el número de elementos hablados en una canción.
      + *Test Mann-Whitney U - Valor P* (Danceability 0.0554; Speechiness 0.0092) : Existe una diferencia significativa entre las categorías 'alto' y 'bajo‘.
      + *Regresión lineal simple*: Relación muy débil, modelo inadecuado.
![Hipótesis 5](/images/Diapositiva5.PNG)
  + **H6 (Extra)**: Las canciones con más apariciones en playlist de Spotify tienen un comportamiento similar en otras plataformas como Deezer o Apple.
    + **Conclusión**: Las canciones que son populares en las playlists de una plataforma tienden a ser populares en las playlists de la otra. El modelo de regresión lineal tiene una buena capacidad explicativa, del 72% al 67% de los casos.
    + *Coeficiente de Pearson* (0.8265): Existe una fuerte correlación positiva entre la cantidad de veces que una canción aparece en playlists de Spotify y Deezer.
    + *Regresión lineal simple*: Relación fuerte y significativa entre el número de veces que una canción aparece en playlists de Deezer y Spotify. Un R² de 0.7284 indica que el 72.84% de la variabilidad en "In Spotify Playlist" puede explicarse por "In Deezer Playlist“, mientras que un R² de 0.6758 indica que el 67.58% de la variabilidad en "In Spotify Playlist" puede explicarse por "In Apple Playlist“. 
![Hipótesis 6](/images/Diapositiva6.PNG)
## Conclusiones
El éxito de una canción y/o artista depende de:
+ **Factores de Distribución y Promoción**: La popularidad de una canción en términos de streams se debe, a factores de distribución y promoción, como su inclusión en playlists y rankings, así como la presencia en múltiples plataformas.
+ **Consistencia entre Plataformas**: Hay una tendencia moderada a fuerte en la popularidad de canciones entre diferentes plataformas de streaming, aunque no sea una relación perfecta.
+ **Cantidad de Contenido**: El número total de canciones de un artista está fuertemente relacionado con su éxito en streams, sugiriendo que más contenido puede atraer más streams.

## Recomendaciones
A partir de las conclusiones se sugiere:
+ **Distribución y Promoción**: Incluir los lanzamientos en al menos 5 mil playlists y estar presente en las múltiples plataformas de streaming en el siguiente orden: Spotify, Deezer y Apple.
+ **Cantidad de Contenido**: Considerar al menos 3 lanzamientos por artista nuevo. Se recomiendan los meses de mayo (inicio de verano) y enero (inicio de año), en los primeros 5 días del mes.
+ **Tomar en cuenta características de la canción**: Aunque la relación del éxito y las características musicales es muy baja, se recomiendan los valores de los segmentos con más éxito, por tanto se recomienda el lanzamiento de canciones con un BPM de 110 a 160, con un promedio de 120. Con Danceability del 60% al 65% y Speechiness del 5% al 10%. Los géneros recomendados de acuerdo al análisis de la data son Pop, Hip Hop, Electrónica y Música Latina.

## Pasos a seguir
Como pasos a seguir se sugieren los siguientes análisis:
+ Análisis por género musical.
+ Análisis de canciones como contenido de audio en redes sociales (Tik Tok, Instagram y Facebook).
+ Evaluar otras métricas clave como likes y shares y su influencia en el número de streams. 
+ Medir el impacto de colaboraciones (feat.) en el éxito de canciones y artistas. 

## Enlaces
### [Presentación](https://drive.google.com/file/d/1E_k514FKv_UPGcI7mYX1VyMI5XJDF48j/view?usp=sharing)
### [Dashboard](https://drive.google.com/file/d/10Xgsw3iV5z_9617aBMpS1iasr12VRz4k/view?usp=sharing)
### [Video Loom](https://www.loom.com/share/c0a2aa6a67694dd686945d81a6c7ec0d?sid=a0dade66-db6b-41d8-bc8f-0af9896b59df)
