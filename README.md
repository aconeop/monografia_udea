
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
-   [Como Usar](#como-usar)
    -   [How-to chapters](#how-to-chapters)
        -   [Word output](#word-output)
-   [Customisations and extensions](#customisations-and-extensions)
-   [Limitationes](#limitaciones)
    -   [Gotchas](#gotchas)

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
     - 
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
   - Los hallazgos relevantes se informan en documentos científicos, accesibles a través de los enlaces relacionados en #Referencias.

**Referencias:**
   - [Ref 1](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6176866/)
   - [Ref 2](https://pubmed.ncbi.nlm.nih.gov/29663411/)
   - [Ref 3](https://pubmed.ncbi.nlm.nih.gov/30033447/)
   - [Ref 4](https://pubmed.ncbi.nlm.nih.gov/29427210/)
   - [Ref 5](https://pubmed.ncbi.nlm.nih.gov/30328048/)
   - [Ref 6](https://pubmed.ncbi.nlm.nih.gov/30672045/)

Esta base de datos integral proporciona un recurso rico para investigar las características del cáncer de mama y los resultados del tratamiento mediante un análisis avanzado de resonancia magnética.

## Requirements

> _Para replicar los pasos que describire seguidamente, es necesario tener en cuenta que requiere algunas herramientas las cuales son:_

1. Cuenta en [Goggle Colab](https://colab.research.google.com/) activa y algunas librerias que describo a continuacion:

2. Las librerias que se requieren tener instaladas son `pydicom` `scikit-fuzzy`, se importan librerias comunes tambien como import os
import `pandas`, `pydicom`, `matplotlib.pyplot`, `seaborn`, from skimage import `segmentation`, from io import `BytesIO`, from PIL import `Image`, `numpy`, `requests`, `skfuzzy`, en caso de que le falte instalar una, instalela usando `!pip install -U [nombre-del-paquete]`

3. 
~a LaTeX installation

    -   Option 1: Use [TinyTeX](https://yihui.name/tinytex/) (a minimal LaTeX installation intended for use with R Markdown)

        -   the development version of TinyTex is [currently required](https://github.com/ulyngs/oxforddown/issues/4). Install from R with

        ``` r
        remotes::install_github('yihui/tinytex')
        tinytex::install_tinytex()
        ```

        -   Then install the LaTeX packages used by `oxforddown` (diskspace taken up by TinyTex with the required packages installed is about 280 Mb)

        ``` r
        missing_packages <- c(
          "appendix", "babel-english", "babel-greek", "babel-latin",
          "biber", "biblatex", "caption", "cbfonts-fd", "colortbl", "csquotes",
          "enumitem", "environ", "eso-pic", "fancyhdr", "greek-fontenc",
          "grfext", "hyphen-greek", "hyphen-latin", "lineno", "logreq",
          "makecell", "microtype", "minitoc", "multirow", "notoccite",
          "oberdiek", "pdflscape", "pdfpages", "quotchap", "soul", "tabu",
          "threeparttable", "threeparttablex", "titlesec", "tocbibind",
          "trimspaces", "ulem", "units", "utopia", "varwidth", "wrapfig",
          "fvextra", "xurl"
          )
        tinytex::tlmgr_install(missing_packages)
        ```

    -   Option 2: Use an ordinary LaTeX distribution

        -   Mac: download and install MacTeX from [tug.org/mactex/](http://www.tug.org/mactex/) (\~4 gigs)
        -   Windows: download and install MikTex from [miktex.org](https://miktex.org)

-   *If on Mac*

    -   Command line developer tools. If you haven't got these installed already, your mac will probably automatically prompt you to install them. Otherwise, you can install them by opening a terminal and typing `xcode-select --install`

-   xploit1.csv: Muestra del Data set Original, obtenido de "the cancer wiki". La muestra esta representada por X numero de pacientes, contiene Tal y tal datos.

-   xploit2.ipynb: Archivo de Jupyter Notebook que contiene codigo de ejecucion de scritp para replicar este ejercicio, utilizando directamente el data set anterior desde el repositorio.


## How to use

-   download the **ulyngs/oxforddown** repo as a zip
-   open **oxforddown.Rproj** in RStudio

### How-to chapters
Read the ['How to use' chapter](https://ulyngs.github.io/oxforddown/how-to-use.html) to understand the structure of `oxforddown` and how to do the basic things like building your thesis.

For how to use R Markdown syntax in general and in `oxforddown` in particular, read the dedicated chapters on this ([R Markdown basics](https://ulyngs.github.io/oxforddown/rmd-basics.html), [Citations, cross-references, and collaboration](https://ulyngs.github.io/oxforddown/cites-and-refs.html), and [Tables](https://ulyngs.github.io/oxforddown/tables.html)).

See also the general, official R Markdown resources [*R Markdown: The Definitive Guide*](https://bookdown.org/yihui/rmarkdown/) and the [*R Markdown Cookbook*](https://bookdown.org/yihui/rmarkdown-cookbook/).

### Video tutorials

I am in the process of updating the tutorial videos to v3 - I've noted below which have yet to be updated, but are still informative, and struck out those that no longer apply:

- [Part 1: Building the entire thesis](https://youtu.be/LBHxcuCMjnk)
- [Part 2: Building a single chapter](https://youtu.be/8vcO252Us6g)
- [(*old but informative*) Part 3: Understanding the file structure](https://www.youtube.com/watch?v=jafgJobOgpc)
- [(*old but informative*) Part 4: A walk-through example of creating your thesis](https://www.youtube.com/watch?v=uWpinaVSZ6Q)
- [~~Part 5: The content included in index.Rmd (or: why the introduction chapter is special)~~](https://www.youtube.com/watch?v=FPlwCj5ZH8M)
- [(*old but informative*) Part 6: Adjusting the order of chapters](https://www.youtube.com/watch?v=-0M3TuDnu7Y)
- [(*old but informative*) Part 7: \_bookdown.yml: Adjusting build settings](https://www.youtube.com/watch?v=jXYfC8RXTvg)
- [~~Part 8: Makefile: Adjusting build settings~~](https://www.youtube.com/watch?v=L6mV8z32RfE)
- [(*old but informative*) Part 9: The LaTeX templates](https://www.youtube.com/watch?v=o2fd_O1On7g)


### Writing your thesis

-   update the YAML header (the stuff at the top between '---') in **index.Rmd** with your name, college, etc.
-   write the individual chapters as **.Rmd** files in the root folder
-   write the front matter (abstract, acknowledgements, abbreviations) and back matter (appendices) by adjusting the **.Rmd** files in the **front-and-back-matter/** folder

**.Rmd** files you don't want included in the body text must be given file names that begin with an underscore (e.g. **front-and-back-matter/\_abstract.Rmd** and **front-and-back-matter/\_acknowledgements.Rmd**).
(Alternatively, specify manually in **\_bookdown.yml** which files should be merged into the body text.)

### Building your entire thesis

-   Build the entire thesis by opening **index.Rmd** and clicking the 'knit' button.
-   The generated thesis files are saved in the **docs/** folder
-   To choose output formats, go to the top of **index.Rmd**'s YAML header and edit the line `thesis_formats <- "pdf";` to the format(s) you want (options are "pdf", "bs4", "gitbook", and "word")
-   You can build to multiple formats simultaneously with, e.g., `thesis_formats <- c("pdf", "bs4", "word")`
-   If you want to customise the build function, edit **scripts_and_filters/knit-functions.R**

#### PDF output

``` yaml
knit: (function(input, ...) {
    thesis_formats <- "pdf";
    ...
```



When you build the entire thesis to PDF, Latex generates a whole bunch of auxillary files - these are automatically removed after the build process end by the custom knit function that is used when you knit **index.Rmd**.

To change how this removal is done, edit **scripts_and_filters/knit-functions.R**.
The line `file.remove(list.files(pattern = "*\\.(log|mtc\\d*|maf|aux|bcf|lof|lot|out|toc)$"))` within `if ("pdf" %in% output_format){` is the one that removes files after PDF output is generated.

#### BS4 book output (HTML)

``` yaml
knit: (function(input, ...) {
    thesis_formats <- "bs4";
    ...
```

-   NOTE: the [bs4 book output](https://pkgs.rstudio.com/bookdown/reference/bs4_book.html) requires the `downlit` and `bslib` R packages (install them with `install.packages`)
-   Note also that to deploy a BS4 book on GitHub Pages, there must be a **.nojekyll** file in the **docs/** folder, otherwise GitHub does some voodoo that causes some filepaths not to work. This file is generated automatically by `oxforddown`'s knitting function.

#### Gitbook output (HTML)

``` yaml
knit: (function(input, ...) {
    thesis_formats <- "gitbook";
    ...
```

-   Note that to deploy a gitbook on GitHub Pages, there must be a **.nojekyll** file in the **docs/** folder, otherwise GitHub does some voodoo that causes some filepaths not to work. This file is generated automatically by `oxforddown`'s knitting function.

#### Word output

``` yaml
knit: (function(input, ...) {
    thesis_formats <- "word";
    ...
```

-   Note that the Word output has no templates behind it, and many things do not work (e.g. image rotation, highlighting corrections). **I encourage pull requests that optimise the Word output, e.g. by using tools from the [`officer`](https://github.com/davidgohel/officer) package.**

### Building a single chapter

To knit an individual chapter without compiling the entire thesis:

1.  open the **.Rmd** file of a chapter
2.  add a YAML header specifying the output format(s) (e.g. `bookdown::word_document2` for a word document you might want to upload to Google Docs for feedback from collaborators)
3.  click the `knit` button (the output file is then saved in the root folder)

As shown in the sample chapters' YAML headers, to output a single chapter to PDF, use e.g.:

``` yaml
output:
  bookdown::pdf_document2:
    template: templates/brief_template.tex
    citation_package: biblatex
documentclass: book
bibliography: references.bib
```

The file **templates/brief_template.tex** formats the chapter in the OxThesis style but without including the front matter (table of contents, abstract, etc).

**NOTE:** The bibliography path in your individual chapters' YAML headers needs to be identical to the one in **index.Rmd** - otherwise your individual chapters' bibliography path may override the path in **index.Rmd** and cause trouble when you knit the entire thesis.

## Customisations and extensions

-   for common things you might want to do in your thesis, read through the sample content
-   the ['Customisations and extensions' chapter](https://ulyngs.github.io/oxforddown/customisations-and-extensions.html) (thanks \@bmvandoren!) has tips on how to include PDF pages from a published typeset article in your thesis, and much more!

## Limitations

### Gotchas

-   don't use underscores (\_) in your YAML front matter or code chunk labels!
    (underscores have special meaning in LaTeX, so therefore you are likely to get an error, cf. <https://yihui.org/en/2018/03/space-pain/>)

    -   bad YAML: `bibliography: bib_final.bib`
    -   good YAML: `bibliography: bib-final.bib`
    -   bad chunk label: `{r my_plot}`
    -   good chunk label: `{r my-plot}`

### Output formats

-   at the moment only PDF and HTML output have been properly implemented; I may improve on the Word output further down the line

Enjoy!
