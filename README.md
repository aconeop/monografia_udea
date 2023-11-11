
<p><img alt="Udea logo" width="450px" height="112px" src="https://www.udea.edu.co/wps/wcm/connect/udea/2288a382-341c-41ee-9633-702a83d5ad2b/logosimbolo-horizontal-png.png?MOD=AJPERES&CVID=ljeSAX9" align="center" hspace="10px" vspace="0px"></p>

# **Cáncer de mama: Un abordaje diagnóstico desde la IA**
<p style="line-height: 0; margin-bottom: 0;"> 
    por Andrés M. Coneo Pretelt. </p> 

<!-- ### **Análisis de Incidentes de Robo en Medellín (2004-2020)** --> 

# **Descripción General**

_Este repositorio se crea como parte de la entrega ME03 de Seminario de Investigación en el programa de [Especialización en Analítica y Ciencia de Datos](https://www.udea.edu.co/wps/portal/udea/web/inicio/unidades-academicas/ingenieria/estudiar-facultad/posgrados/especializacion-analitica-ciencia-datos)  de la Universidad de Antioquia (Medellín, Colombia). Dentro de los objetivos de este proyecto es aplicar técnicas de Deep Learning para optimizar la detección temprana del cáncer de mama. Este proyecto es una exploración amplia de la relación entre la imagen médica y la biología del cáncer de mama. Se basa en estudios recientes que han demostrado que los fenotipos de imagen pueden proporcionar información valiosa sobre las características moleculares y genómicas de los tumores de forma temprana. Este proyecto se centra en un análisis amplio y multidisciplinario de esta relación, basado en un conjunto de [datos](https://wiki.cancerimagingarchive.net/pages/viewpage.action?pageId=70226903#70226903c579742f614844eabac2c3c1651ec8b4) de resonancia magnética de mama y anotaciones medicas de cada caso, tomados desde el 1 de enero de 2000 hasta el 23 de marzo de 2014, que contiene 922 pacientes con cáncer de mama invasivo y resonancia magnética preoperatoria reunidas en el Hospital Duke (Durham, NC, USA)_

_Siguiendo la línea de investigación de este estudio, se utilizará una muestra del conjunto de datos de resonancias magnéticas para entrenar modelos de Machine Learning, con el objetivo de mejorar la precisión en la identificación de tumores de mama y, al mismo tiempo, comprender mejor las relaciones entre los fenotipos de imagen y las características moleculares y genómicas de los tumores conocidas de segun los casos. A través de la aplicación de algoritmos de aprendizaje profundo, este proyecto busca contribuir al avance de la detección temprana del cáncer de mama y al entendimiento de sus implicaciones moleculares._

_Para garantizar que nuestra muestra de datos sea representativa y que nuestros modelos de Machine Learning sean efectivos, se utilizará el estadístico Z para calcular el tamaño de muestra necesario. El estadístico Z nos permitirá determinar el tamaño óptimo de la muestra, teniendo en cuenta la población de 922 pacientes en nuestro conjunto de datos de resonancias magnéticas. Al configurar el nivel de confianza y el margen de error deseado, podremos determinar cuántas observaciones son necesarias para obtener resultados sólidos en nuestro análisis._

Tienes razón, para calcular el tamaño de muestra necesario, necesitas conocer el tamaño total de la población de la cual deseas tomar una muestra representativa. En tu caso, tienes una población de 922 pacientes. El cálculo del tamaño de muestra se basa en una fracción del tamaño total de la población y depende de la precisión deseada, el nivel de confianza y otros parámetros.

Para calcular el tamaño de muestra necesario conociendo el tamaño total de la población, puedes utilizar una fórmula que ajusta el cálculo en consecuencia. Una fórmula común para el cálculo del tamaño de muestra en una población finita es la siguiente:

$$
n = \frac{N \cdot Z^2 \cdot p(1-p)}{E^2(N-1) + Z^2 \cdot p(1-p)}
$$

Donde:  

- $n$ = $(?)$ numero de imagenes para la muestra.  
- $N$ = $(773888)$ total de imagenes.  
- $Z$ = $1.96$ valor de la distribución normal estándar correspondiente a un nivel de confianza del $95$%. 
- $p$ = $0.5$ asumiendo que la proporción es igualmente probable de ser alta o baja dentro de la población.  
- $E$ = $0.05$ es el margen de error que deseas permitir en tu estimación.  

Obtuve entonces un $n$ muestral asi:  

$$
n = \frac{773888 \cdot 1.96^2 \cdot 0.5(1-0.5)}{0.05^2(773888-1) + 1.96^2 \cdot 0.5(1-0.5)} = 384
$$



# Contenido

-   [Datos](#datos)
-   [Requerimientos](#requerimientos)
-   [Guía de Uso](#guia-de-uso)
-   [Limitationes](#limitaciones)

## Datos
**Descripción de la Fuente de Datos para el Conjunto de Datos de Resonancia Magnética de Mama**

1. **Visión General del Conjunto de Datos:**
   - **Modalidades:** Imágenes por Resonancia Magnética (MR), Segmentación (SEG).
   - **Número de Participantes:** 922.
   - **Número de Estudios:** 922.
   - **Número de Series:** 5,161.
   - **Número de Imágenes:** 773,888.
   - **Tamaño de Imágenes (GB):** 368.4.

2. **Población:**
   - El conjunto de datos incluye 922 pacientes diagnosticadas con cáncer de mama invasivo.
   - Datos recopilados en el Hospital Duke desde el 1 de enero de 2000 hasta el 23 de marzo de 2014.
   - Los pacientes deben haber tenido una resonancia magnética preoperatoria en el Hospital Duke.

3. **Procedimiento de Anotación Radiologica:**
   - La anotación se llevó a cabo en dos fases:
     - Fase 1: 271 pacientes anotadas por un panel de 6 radiólogos.
     - Fase 2: 651 pacientes anotadas por un panel de 4 radiólogos.
     - Las anotaciones fueron realizadas por 8 radiólogos utilizando una interfaz gráfica en MATLAB.
     - La anotación incluyó tres secuencias de resonancia magnética: pre-contraste, primer post-contraste y sustracción.

4. **Datos Demográficos, Clínicos, Patológicos, Genómicos, Tratamiento, Resultados y Otros:**
   - Los datos clínicos detallados están disponibles [aquí](https://doi.org/10.7937/TCIA.e3sv-re93) bajo "Acceso a Datos" usando el elemento "Tipo de Datos" "Características Clínicas y Otros" en su version original, al igual que anidados en la carpeta [data](https://github.com/aconeop/monografia_udea/blob/1bd3c63fb22608bc159b0008784794703a35b78a/data/Clinical_and_Other_Features.xlsx).
   - Los datos incluyen información demográfica, características del tumor, hallazgos de la resonancia magnética, detalles de la cirugía, terapia de radiación, respuesta del tumor, recurrencia y seguimiento.

5. **Información Técnica de Resonancia Magnética (MRI):**
   - Los detalles técnicos están disponibles [aquí](https://doi.org/10.7937/TCIA.e3sv-re93) bajo "Acceso a Datos" usando el elemento "Tipo de Datos" "Características de Imágenes" en su version original, al igual que anidados en la carpeta [data](https://github.com/aconeop/monografia_udea/blob/6f1fae8a166cb30f56725faea74908b5ad101bc7/data/Imaging_Features.xlsx).
   - La información incluye desde el diagnóstico hasta la fecha de la MRI, detalles del fabricante, opciones de escaneo, intensidad del campo y más.

6. **Características de Imágenes:**
   - Las características se extrajeron previamente de tumores y tejido fibroglandular (FGT) utilizando secuencias T1.
   - Las características se categorizan en varios grupos, incluyendo volumen, tamaño, morfología, realce y heterogeneidad.

7. **Características para Analizar:**
   - Se tienen una serie de características que se pueden evaluar:
     - Evaluación de la variabilidad de las características debido a cambios en el protocolo de resonancia magnética.
     - Evaluación de la estabilidad entre lectores con un subconjunto de 50 pacientes.
     - Validación para predecir subtipo tumoral, estado de receptor y estado de Ki-67.
     - Validación para predecir niveles de puntuación de recurrencia de Oncotype DX.
     - Validación para predecir respuesta completa a la terapia neoadyuvante (pCR).
     - Validación de características asociadas con la supervivencia libre de recurrencia a distancia.

8. **Publicaciones existentes basadas en el dataset:**
   - Los hallazgos relevantes se informan en documentos científicos, accesibles a través de los enlaces relacionados en **Referencias**.

**Referencias:**
   - [Ref 1](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6176866/)
   - [Ref 2](https://pubmed.ncbi.nlm.nih.gov/29663411/)
   - [Ref 3](https://pubmed.ncbi.nlm.nih.gov/30033447/)
   - [Ref 4](https://pubmed.ncbi.nlm.nih.gov/29427210/)
   - [Ref 5](https://pubmed.ncbi.nlm.nih.gov/30328048/)
   - [Ref 6](https://pubmed.ncbi.nlm.nih.gov/30672045/)

Esta base de datos integral proporciona un recurso rico para investigar las características del cáncer de mama y los resultados del tratamiento mediante un análisis avanzado de resonancia magnética.

## Requirimientos

> _Para replicar los pasos que describire seguidamente, es necesario tener en cuenta que requiere algunas herramientas las cuales son:_

1. Cuenta en [Goggle Colab](https://colab.research.google.com/) activa y algunas librerias que describo a continuacion:

2. Las librerias que se requieren tener instaladas son `pydicom` `scikit-fuzzy`, se importan librerias comunes tambien como import os
import `pandas`, `pydicom`, `matplotlib.pyplot`, `seaborn`, `segmentation` from skimage,`BytesIO` from io, `Image` from PIL, `numpy`, `requests`, `skfuzzy`, en caso de que le falte instalar una, instalela usando `!pip install -U [nombre-del-paquete]`.

## Guía de Uso

Para utilizar eficazmente este repositorio y replicar el estudio en otro entorno, se proporciona la siguiente guía:

1. **Clonación del Repositorio:**
   - Clone este repositorio en su entorno local utilizando el comando:
     ```
     git clone <URL_del_Repositorio>
     ```
   - Esto asegurará que tenga acceso a todos los archivos y datos necesarios.

2. **Entorno de Trabajo en Colab:**
   - Para replicar el estudio en un entorno de Google Colab, abra el cuaderno Colab suministrado ("Pre-procesamientoME03.ipynb") desde el repositorio clonado.

3. **Configuración del Entorno:**
   - Asegúrese de tener acceso a todas las bibliotecas y dependencias necesarias. Esto puede requerir la instalación de bibliotecas específicas utilizando los comandos `pip install` en las celdas del cuaderno.

4. **Acceso a los Datos:**
   - Utilice los enlaces proporcionados en el cuaderno para acceder a los conjuntos de datos requeridos. Esto incluye datos clínicos, imágenes de resonancia magnética y características de imágenes. Profesor David V. tenga en cuenta que en esta ocasion me enfoque en los datos clinicos y caracteristicas de las imagenes, y no en si en las imagenes, por que el procesamiento de las mismas me tocaria mucho mas tiempo para la entrega ME03.

5. **Ejecución del Código:**
   - Siga las celdas del cuaderno secuencialmente para ejecutar el código. Asegúrese de seguir cualquier instrucción específica proporcionada en los comentarios del código.

## Limitaciones del Análisis Preliminar de Datos

El análisis preliminar de datos realizado presenta limitaciones importantes que requieren consideración. La imputación de valores nulos mediante la mediana puede introducir sesgos, especialmente en casos de distribuciones significativas de datos faltantes. Además, las decisiones sobre la imputación de columnas pueden influir en la integridad del conjunto de datos resultante. Estas limitaciones subrayan la importancia de completar el trabajo y buscar diversas alternativas para poder evaluar y validar las hipotesis del trabajpo, seria ideal ampliar la idea y lograr correlacionar de manera efectiva y acertada todas las variables disponibles.

Gracias!
