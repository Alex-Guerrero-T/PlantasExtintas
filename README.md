Trabajo con plantas extintas
================

# Introducción

Queremos saber ahora para probar solamentela app queremos ir probando si
es que efectivamente podemos ocupar github con rstudio
[*IUCN*](https://www.iucnredlist.org/)

## Subtítulo

Vamos a partir por cargar los pauetes necesarios para trabajar

``` r
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.1 ──

    ## ✓ ggplot2 3.3.3     ✓ purrr   0.3.4
    ## ✓ tibble  3.1.2     ✓ dplyr   1.0.6
    ## ✓ tidyr   1.1.3     ✓ stringr 1.4.0
    ## ✓ readr   1.4.0     ✓ forcats 0.5.1

    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

``` r
library(dplyr)
```

Ahora voy a leer los datos con los que voy a trabajar:

``` r
plants <- read_csv("https://raw.githubusercontent.com/rfordatascience/tidytuesday/master/data/2020/2020-08-18/plants.csv")
```

    ## 
    ## ── Column specification ────────────────────────────────────────────────────────
    ## cols(
    ##   .default = col_double(),
    ##   binomial_name = col_character(),
    ##   country = col_character(),
    ##   continent = col_character(),
    ##   group = col_character(),
    ##   year_last_seen = col_character(),
    ##   red_list_category = col_character()
    ## )
    ## ℹ Use `spec()` for the full column specifications.

## Filtrando los datos para resolver el ejemplo 1

El código que voy a ejecutar ahora es para resolver el problema en el
siguiente
[slide](https://derek-corcoran-barrios.github.io/CursoProgrPres/Clase2/Clase2InvestigacionReproducible.html#29),
para poner dentro de la base de datos, sólo los datos de Chile y sólo
usar las columnas para País (*country*), la especie (*binomial\_name*) y
la categoria de IUCN (*red\_list\_category*).

``` r
Chile <- plants %>% 
  filter(country == "Chile") %>% 
  select(binomial_name, country, red_list_category)
Chile
```

    ## # A tibble: 2 x 3
    ##   binomial_name           country red_list_category  
    ##   <chr>                   <chr>   <chr>              
    ## 1 Santalum fernandezianum Chile   Extinct            
    ## 2 Sophora toromiro        Chile   Extinct in the Wild
