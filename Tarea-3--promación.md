TAREA N°3
================
Grupo 12
13/1/2022

# 9. Ejercicios: tidyverse

``` r
library(dplyr)
```

    ## Warning: package 'dplyr' was built under R version 4.1.2

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

``` r
library(nycflights13)
```

    ## Warning: package 'nycflights13' was built under R version 4.1.2

``` r
nycflights13::flights
```

    ## # A tibble: 336,776 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     1      517            515         2      830            819
    ##  2  2013     1     1      533            529         4      850            830
    ##  3  2013     1     1      542            540         2      923            850
    ##  4  2013     1     1      544            545        -1     1004           1022
    ##  5  2013     1     1      554            600        -6      812            837
    ##  6  2013     1     1      554            558        -4      740            728
    ##  7  2013     1     1      555            600        -5      913            854
    ##  8  2013     1     1      557            600        -3      709            723
    ##  9  2013     1     1      557            600        -3      838            846
    ## 10  2013     1     1      558            600        -2      753            745
    ## # ... with 336,766 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

``` r
flights
```

    ## # A tibble: 336,776 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     1      517            515         2      830            819
    ##  2  2013     1     1      533            529         4      850            830
    ##  3  2013     1     1      542            540         2      923            850
    ##  4  2013     1     1      544            545        -1     1004           1022
    ##  5  2013     1     1      554            600        -6      812            837
    ##  6  2013     1     1      554            558        -4      740            728
    ##  7  2013     1     1      555            600        -5      913            854
    ##  8  2013     1     1      557            600        -3      709            723
    ##  9  2013     1     1      557            600        -3      838            846
    ## 10  2013     1     1      558            600        -2      753            745
    ## # ... with 336,766 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

## 9.1 Parte 1: Dplyr - filter

### 1.Encuentra todos los vuelos que:

#### a.Tuvieron un retraso de llegada de dos o más horas

``` r
respa=dplyr::filter(flights, arr_delay >= 120)
respa
```

    ## # A tibble: 10,200 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     1      811            630       101     1047            830
    ##  2  2013     1     1      848           1835       853     1001           1950
    ##  3  2013     1     1      957            733       144     1056            853
    ##  4  2013     1     1     1114            900       134     1447           1222
    ##  5  2013     1     1     1505           1310       115     1638           1431
    ##  6  2013     1     1     1525           1340       105     1831           1626
    ##  7  2013     1     1     1549           1445        64     1912           1656
    ##  8  2013     1     1     1558           1359       119     1718           1515
    ##  9  2013     1     1     1732           1630        62     2028           1825
    ## 10  2013     1     1     1803           1620       103     2008           1750
    ## # ... with 10,190 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

#### b. Volaron a Houston (IAH oHOU)

``` r
respb=dplyr::filter(flights, dest=="IAH"|dest=="HOU")
respb
```

    ## # A tibble: 9,313 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     1      517            515         2      830            819
    ##  2  2013     1     1      533            529         4      850            830
    ##  3  2013     1     1      623            627        -4      933            932
    ##  4  2013     1     1      728            732        -4     1041           1038
    ##  5  2013     1     1      739            739         0     1104           1038
    ##  6  2013     1     1      908            908         0     1228           1219
    ##  7  2013     1     1     1028           1026         2     1350           1339
    ##  8  2013     1     1     1044           1045        -1     1352           1351
    ##  9  2013     1     1     1114            900       134     1447           1222
    ## 10  2013     1     1     1205           1200         5     1503           1505
    ## # ... with 9,303 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

#### c. Fueron operados por United, American o Delta

``` r
filter(flights, carrier=="UU"|carrier=="AA"|carrier=="DL")
```

    ## # A tibble: 80,839 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     1      542            540         2      923            850
    ##  2  2013     1     1      554            600        -6      812            837
    ##  3  2013     1     1      558            600        -2      753            745
    ##  4  2013     1     1      559            600        -1      941            910
    ##  5  2013     1     1      602            610        -8      812            820
    ##  6  2013     1     1      606            610        -4      858            910
    ##  7  2013     1     1      606            610        -4      837            845
    ##  8  2013     1     1      615            615         0      833            842
    ##  9  2013     1     1      623            610        13      920            915
    ## 10  2013     1     1      628            630        -2     1137           1140
    ## # ... with 80,829 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

#### d. Partieron en invierno del hemisferio sur (julio, agosto y septiembre)

``` r
filter(flights, month=="7"|month=="8"|month=="9")
```

    ## # A tibble: 86,326 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     7     1        1           2029       212      236           2359
    ##  2  2013     7     1        2           2359         3      344            344
    ##  3  2013     7     1       29           2245       104      151              1
    ##  4  2013     7     1       43           2130       193      322             14
    ##  5  2013     7     1       44           2150       174      300            100
    ##  6  2013     7     1       46           2051       235      304           2358
    ##  7  2013     7     1       48           2001       287      308           2305
    ##  8  2013     7     1       58           2155       183      335             43
    ##  9  2013     7     1      100           2146       194      327             30
    ## 10  2013     7     1      100           2245       135      337            135
    ## # ... with 86,316 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

#### e. Llegaron más de dos horas tarde, pero no salieron tarde

``` r
filter(flights, dep_delay <= 0 & arr_delay > 120)
```

    ## # A tibble: 29 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1    27     1419           1420        -1     1754           1550
    ##  2  2013    10     7     1350           1350         0     1736           1526
    ##  3  2013    10     7     1357           1359        -2     1858           1654
    ##  4  2013    10    16      657            700        -3     1258           1056
    ##  5  2013    11     1      658            700        -2     1329           1015
    ##  6  2013     3    18     1844           1847        -3       39           2219
    ##  7  2013     4    17     1635           1640        -5     2049           1845
    ##  8  2013     4    18      558            600        -2     1149            850
    ##  9  2013     4    18      655            700        -5     1213            950
    ## 10  2013     5    22     1827           1830        -3     2217           2010
    ## # ... with 19 more rows, and 11 more variables: arr_delay <dbl>, carrier <chr>,
    ## #   flight <int>, tailnum <chr>, origin <chr>, dest <chr>, air_time <dbl>,
    ## #   distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

#### f. Se retrasaron por lo menos una hora, pero repusieron más de 30 minutos en vuelo

``` r
filter(flights, dep_delay >= 60 & dep_delay - arr_delay > 30)
```

    ## # A tibble: 1,844 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     1     2205           1720       285       46           2040
    ##  2  2013     1     1     2326           2130       116      131             18
    ##  3  2013     1     3     1503           1221       162     1803           1555
    ##  4  2013     1     3     1839           1700        99     2056           1950
    ##  5  2013     1     3     1850           1745        65     2148           2120
    ##  6  2013     1     3     1941           1759       102     2246           2139
    ##  7  2013     1     3     1950           1845        65     2228           2227
    ##  8  2013     1     3     2015           1915        60     2135           2111
    ##  9  2013     1     3     2257           2000       177       45           2224
    ## 10  2013     1     4     1917           1700       137     2135           1950
    ## # ... with 1,834 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

#### g. Partieron entre la medianoche y las 6 a.m. (incluyente)

``` r
filter(flights, dep_time %in% c(1:600) | dep_time == 2400 )
```

    ## # A tibble: 9,373 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     1      517            515         2      830            819
    ##  2  2013     1     1      533            529         4      850            830
    ##  3  2013     1     1      542            540         2      923            850
    ##  4  2013     1     1      544            545        -1     1004           1022
    ##  5  2013     1     1      554            600        -6      812            837
    ##  6  2013     1     1      554            558        -4      740            728
    ##  7  2013     1     1      555            600        -5      913            854
    ##  8  2013     1     1      557            600        -3      709            723
    ##  9  2013     1     1      557            600        -3      838            846
    ## 10  2013     1     1      558            600        -2      753            745
    ## # ... with 9,363 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

### 2. Otra función de dplyr que es útil para usar filtros es between(). ¿Qué hace?¿Puedes usarla para simplificar el código necesario para responder a los desafíos anteriores?

#### Es una función que puede evaluar cada elemento de un vector se encuentra entre dos valores que se escriben en su sintaxis. Devuelve un vector lógico, por lo que se puede usar dentro de filter para filtrar datos de una tabla más fácilmente.

``` r
# 1ra forma
flights%>%
  filter(between(flights$month,7,9))
```

    ## # A tibble: 86,326 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     7     1        1           2029       212      236           2359
    ##  2  2013     7     1        2           2359         3      344            344
    ##  3  2013     7     1       29           2245       104      151              1
    ##  4  2013     7     1       43           2130       193      322             14
    ##  5  2013     7     1       44           2150       174      300            100
    ##  6  2013     7     1       46           2051       235      304           2358
    ##  7  2013     7     1       48           2001       287      308           2305
    ##  8  2013     7     1       58           2155       183      335             43
    ##  9  2013     7     1      100           2146       194      327             30
    ## 10  2013     7     1      100           2245       135      337            135
    ## # ... with 86,316 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

``` r
# 2da forma
filter(flights, between(month, 7, 9))
```

    ## # A tibble: 86,326 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     7     1        1           2029       212      236           2359
    ##  2  2013     7     1        2           2359         3      344            344
    ##  3  2013     7     1       29           2245       104      151              1
    ##  4  2013     7     1       43           2130       193      322             14
    ##  5  2013     7     1       44           2150       174      300            100
    ##  6  2013     7     1       46           2051       235      304           2358
    ##  7  2013     7     1       48           2001       287      308           2305
    ##  8  2013     7     1       58           2155       183      335             43
    ##  9  2013     7     1      100           2146       194      327             30
    ## 10  2013     7     1      100           2245       135      337            135
    ## # ... with 86,316 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

### 3. ¿Cuántos vuelos tienen datos faltantes en horario_salida? ¿Qué otras variables tienen valores faltantes? ¿Qué representan estas filas?

``` r
flights %>% 
  summarise_all(funs(sum(is.na(.))))
```

    ## Warning: `funs()` was deprecated in dplyr 0.8.0.
    ## Please use a list of either functions or lambdas: 
    ## 
    ##   # Simple named list: 
    ##   list(mean = mean, median = median)
    ## 
    ##   # Auto named with `tibble::lst()`: 
    ##   tibble::lst(mean, median)
    ## 
    ##   # Using lambdas
    ##   list(~ mean(., trim = .2), ~ median(., na.rm = TRUE))
    ## This warning is displayed once every 8 hours.
    ## Call `lifecycle::last_lifecycle_warnings()` to see where this warning was generated.

    ## # A tibble: 1 x 19
    ##    year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##   <int> <int> <int>    <int>          <int>     <int>    <int>          <int>
    ## 1     0     0     0     8255              0      8255     8713              0
    ## # ... with 11 more variables: arr_delay <int>, carrier <int>, flight <int>,
    ## #   tailnum <int>, origin <int>, dest <int>, air_time <int>, distance <int>,
    ## #   hour <int>, minute <int>, time_hour <int>

#### Tenemos el caso del horario de salida (dep_time) el valor NA nos dice que estos vuelos no llegaron a salir, por lo que tampoco existe un retraso en la salida (dep_delay) aunque estos ya tenían un horario programado (sched_dep_time).

### 4. ¿Por qué NA^0 no es faltante? ¿Por qué NA \| TRUE no es faltante? ¿Por qué FALSE & NA no es faltante? ¿Puedes descubrir la regla general? (¡NA \* 0 es un contraejemplo complicado!)

``` r
vect= c(NA)
is.na(vect)
```

    ## [1] TRUE

#### ¿Por qué NA^0 no es faltante?

``` r
#### Como NA puede tomar cualquier valor, cualquier número elevado a la 0 es igual a 
```

#### ¿Por qué NA \| TRUE no es faltante?

``` r
#### Es igual a TRUE pues el NA se entiende como un valor lógico (T o F) y por lógica proposicional `TRUE` | `TRUE`  y  `FALSE` | `TRUE` es siempre igual a `TRUE`. 
```

#### ¿Por qué FALSE & NA no es faltante?

``` r
#### Porque es igual a “TRUE” ya que por lógica “TRUE”&”FALSE” y “FALSE” & “FALSE” es siempre “FALSE”
```

#### ¿Puedes descubrir la regla general?

``` r
# “NA” al poder ser cualquier valor, cuando este es de mayor valor y se multiplica por 0, nos  brinda una indeterminación que se define como “Not a Number”. Sin embargo, cuando es de menor valor, entonces “NA” multiplicado por 0 es igual a 0.  En todo caso, usaremos una variable “x” ya que desconocemos si el valor es mayor o menor.
```

## 9.2 Parte 2: Dplyr - arrange

### 1. ¿Cómo podrías usar arrange() para ordenar todos los valores faltantes al comienzo? (Sugerencia: usa is.na()).

``` r
arrange(flights,desc(is.na(air_time)))
```

    ## # A tibble: 336,776 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     1     1525           1530        -5     1934           1805
    ##  2  2013     1     1     1528           1459        29     2002           1647
    ##  3  2013     1     1     1740           1745        -5     2158           2020
    ##  4  2013     1     1     1807           1738        29     2251           2103
    ##  5  2013     1     1     1939           1840        59       29           2151
    ##  6  2013     1     1     1952           1930        22     2358           2207
    ##  7  2013     1     1     2016           1930        46       NA           2220
    ##  8  2013     1     1       NA           1630        NA       NA           1815
    ##  9  2013     1     1       NA           1935        NA       NA           2240
    ## 10  2013     1     1       NA           1500        NA       NA           1825
    ## # ... with 336,766 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

### 2.Ordena vuelos para encontrar los vuelos más retrasados. Encuentra los vuelos que salieron más temprano.

``` r
# Vuelos más retrasados
arrange(flights,desc(dep_delay))
```

    ## # A tibble: 336,776 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     9      641            900      1301     1242           1530
    ##  2  2013     6    15     1432           1935      1137     1607           2120
    ##  3  2013     1    10     1121           1635      1126     1239           1810
    ##  4  2013     9    20     1139           1845      1014     1457           2210
    ##  5  2013     7    22      845           1600      1005     1044           1815
    ##  6  2013     4    10     1100           1900       960     1342           2211
    ##  7  2013     3    17     2321            810       911      135           1020
    ##  8  2013     6    27      959           1900       899     1236           2226
    ##  9  2013     7    22     2257            759       898      121           1026
    ## 10  2013    12     5      756           1700       896     1058           2020
    ## # ... with 336,766 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

``` r
# Vuelos más tempranos
arrange(flights,dep_delay)
```

    ## # A tibble: 336,776 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013    12     7     2040           2123       -43       40           2352
    ##  2  2013     2     3     2022           2055       -33     2240           2338
    ##  3  2013    11    10     1408           1440       -32     1549           1559
    ##  4  2013     1    11     1900           1930       -30     2233           2243
    ##  5  2013     1    29     1703           1730       -27     1947           1957
    ##  6  2013     8     9      729            755       -26     1002            955
    ##  7  2013    10    23     1907           1932       -25     2143           2143
    ##  8  2013     3    30     2030           2055       -25     2213           2250
    ##  9  2013     3     2     1431           1455       -24     1601           1631
    ## 10  2013     5     5      934            958       -24     1225           1309
    ## # ... with 336,766 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

### 3.Ordena vuelos para encontrar los vuelos más rápidos (que viajaron a mayor velocidad).

``` r
arrange(flights,desc(distance/air_time))
```

    ## # A tibble: 336,776 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     5    25     1709           1700         9     1923           1937
    ##  2  2013     7     2     1558           1513        45     1745           1719
    ##  3  2013     5    13     2040           2025        15     2225           2226
    ##  4  2013     3    23     1914           1910         4     2045           2043
    ##  5  2013     1    12     1559           1600        -1     1849           1917
    ##  6  2013    11    17      650            655        -5     1059           1150
    ##  7  2013     2    21     2355           2358        -3      412            438
    ##  8  2013    11    17      759            800        -1     1212           1255
    ##  9  2013    11    16     2003           1925        38       17             36
    ## 10  2013    11    16     2349           2359       -10      402            440
    ## # ... with 336,766 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

### 4.¿Cuáles vuelos viajaron más lejos? ¿Cuál viajó más cerca?

#### ¿Cuáles vuelos viajaron más lejos?

``` r
arrange(flights,desc(distance)) 
```

    ## # A tibble: 336,776 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     1      857            900        -3     1516           1530
    ##  2  2013     1     2      909            900         9     1525           1530
    ##  3  2013     1     3      914            900        14     1504           1530
    ##  4  2013     1     4      900            900         0     1516           1530
    ##  5  2013     1     5      858            900        -2     1519           1530
    ##  6  2013     1     6     1019            900        79     1558           1530
    ##  7  2013     1     7     1042            900       102     1620           1530
    ##  8  2013     1     8      901            900         1     1504           1530
    ##  9  2013     1     9      641            900      1301     1242           1530
    ## 10  2013     1    10      859            900        -1     1449           1530
    ## # ... with 336,766 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

#### ¿Cuál viajó más cerca?

``` r
arrange(flights,distance)
```

    ## # A tibble: 336,776 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     7    27       NA            106        NA       NA            245
    ##  2  2013     1     3     2127           2129        -2     2222           2224
    ##  3  2013     1     4     1240           1200        40     1333           1306
    ##  4  2013     1     4     1829           1615       134     1937           1721
    ##  5  2013     1     4     2128           2129        -1     2218           2224
    ##  6  2013     1     5     1155           1200        -5     1241           1306
    ##  7  2013     1     6     2125           2129        -4     2224           2224
    ##  8  2013     1     7     2124           2129        -5     2212           2224
    ##  9  2013     1     8     2127           2130        -3     2304           2225
    ## 10  2013     1     9     2126           2129        -3     2217           2224
    ## # ... with 336,766 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

## 9.3 Parte 3: Dplyr - select

### 1.Haz una lluvia de ideas sobre tantas maneras como sea posible para seleccionar dep_time, dep_delay, arr_time, and arr_delay de flights.

``` r
#### 1ra manera
select(flights,dep_time, dep_delay, arr_time, arr_delay)
```

    ## # A tibble: 336,776 x 4
    ##    dep_time dep_delay arr_time arr_delay
    ##       <int>     <dbl>    <int>     <dbl>
    ##  1      517         2      830        11
    ##  2      533         4      850        20
    ##  3      542         2      923        33
    ##  4      544        -1     1004       -18
    ##  5      554        -6      812       -25
    ##  6      554        -4      740        12
    ##  7      555        -5      913        19
    ##  8      557        -3      709       -14
    ##  9      557        -3      838        -8
    ## 10      558        -2      753         8
    ## # ... with 336,766 more rows

``` r
#### 2da manera
select(flights, starts_with("dep"), starts_with("arr"))
```

    ## # A tibble: 336,776 x 4
    ##    dep_time dep_delay arr_time arr_delay
    ##       <int>     <dbl>    <int>     <dbl>
    ##  1      517         2      830        11
    ##  2      533         4      850        20
    ##  3      542         2      923        33
    ##  4      544        -1     1004       -18
    ##  5      554        -6      812       -25
    ##  6      554        -4      740        12
    ##  7      555        -5      913        19
    ##  8      557        -3      709       -14
    ##  9      557        -3      838        -8
    ## 10      558        -2      753         8
    ## # ... with 336,766 more rows

``` r
#### 3ra manera
select(flights, ends_with("time"),ends_with("delay"))
```

    ## # A tibble: 336,776 x 7
    ##    dep_time sched_dep_time arr_time sched_arr_time air_time dep_delay arr_delay
    ##       <int>          <int>    <int>          <int>    <dbl>     <dbl>     <dbl>
    ##  1      517            515      830            819      227         2        11
    ##  2      533            529      850            830      227         4        20
    ##  3      542            540      923            850      160         2        33
    ##  4      544            545     1004           1022      183        -1       -18
    ##  5      554            600      812            837      116        -6       -25
    ##  6      554            558      740            728      150        -4        12
    ##  7      555            600      913            854      158        -5        19
    ##  8      557            600      709            723       53        -3       -14
    ##  9      557            600      838            846      140        -3        -8
    ## 10      558            600      753            745      138        -2         8
    ## # ... with 336,766 more rows

``` r
#### 4ta manera 
select(flights, contains("dep"), contains("arr"))
```

    ## # A tibble: 336,776 x 7
    ##    dep_time sched_dep_time dep_delay arr_time sched_arr_time arr_delay carrier
    ##       <int>          <int>     <dbl>    <int>          <int>     <dbl> <chr>  
    ##  1      517            515         2      830            819        11 UA     
    ##  2      533            529         4      850            830        20 UA     
    ##  3      542            540         2      923            850        33 AA     
    ##  4      544            545        -1     1004           1022       -18 B6     
    ##  5      554            600        -6      812            837       -25 DL     
    ##  6      554            558        -4      740            728        12 UA     
    ##  7      555            600        -5      913            854        19 B6     
    ##  8      557            600        -3      709            723       -14 EV     
    ##  9      557            600        -3      838            846        -8 B6     
    ## 10      558            600        -2      753            745         8 AA     
    ## # ... with 336,766 more rows

### 2.¿Qué sucede si incluyes el nombre de una variable varias veces en una llamada a select()?

``` r
#### Con Origin
select(flights,origin, origin, origin)
```

    ## # A tibble: 336,776 x 1
    ##    origin
    ##    <chr> 
    ##  1 EWR   
    ##  2 LGA   
    ##  3 JFK   
    ##  4 JFK   
    ##  5 LGA   
    ##  6 EWR   
    ##  7 EWR   
    ##  8 LGA   
    ##  9 JFK   
    ## 10 LGA   
    ## # ... with 336,766 more rows

``` r
#### Con Tailnum
select(flights,tailnum, tailnum, tailnum)
```

    ## # A tibble: 336,776 x 1
    ##    tailnum
    ##    <chr>  
    ##  1 N14228 
    ##  2 N24211 
    ##  3 N619AA 
    ##  4 N804JB 
    ##  5 N668DN 
    ##  6 N39463 
    ##  7 N516JB 
    ##  8 N829AS 
    ##  9 N593JB 
    ## 10 N3ALAA 
    ## # ... with 336,766 more rows

``` r
#### Con Dest
select(flights, dest, dest, dest)
```

    ## # A tibble: 336,776 x 1
    ##    dest 
    ##    <chr>
    ##  1 IAH  
    ##  2 IAH  
    ##  3 MIA  
    ##  4 BQN  
    ##  5 ATL  
    ##  6 ORD  
    ##  7 FLL  
    ##  8 IAD  
    ##  9 MCO  
    ## 10 ORD  
    ## # ... with 336,766 more rows

### 3.¿Qué hace la función any_of()? ¡¿Por qué podría ser útil en conjunto con este vector?

``` r
#### La función "any_of()" es aquella que indica las variables que queremos seleccionar con el nombre de un vector que contiene dichas variables.
#### Ejemplo:
#### Tenemos al vectorx que va tener 6 variables: "year", "month", "day","distance", "origin", "carrier"
variables <- c( "year", "month", "day","distance", "origin", "carrier")
#### Usamos "any_of()" de dos maneras distintas
select(flights, any_of(variables))
```

    ## # A tibble: 336,776 x 6
    ##     year month   day distance origin carrier
    ##    <int> <int> <int>    <dbl> <chr>  <chr>  
    ##  1  2013     1     1     1400 EWR    UA     
    ##  2  2013     1     1     1416 LGA    UA     
    ##  3  2013     1     1     1089 JFK    AA     
    ##  4  2013     1     1     1576 JFK    B6     
    ##  5  2013     1     1      762 LGA    DL     
    ##  6  2013     1     1      719 EWR    UA     
    ##  7  2013     1     1     1065 EWR    B6     
    ##  8  2013     1     1      229 LGA    EV     
    ##  9  2013     1     1      944 JFK    B6     
    ## 10  2013     1     1      733 LGA    AA     
    ## # ... with 336,766 more rows

``` r
select(flights, variables)
```

    ## Note: Using an external vector in selections is ambiguous.
    ## i Use `all_of(variables)` instead of `variables` to silence this message.
    ## i See <https://tidyselect.r-lib.org/reference/faq-external-vector.html>.
    ## This message is displayed once per session.

    ## # A tibble: 336,776 x 6
    ##     year month   day distance origin carrier
    ##    <int> <int> <int>    <dbl> <chr>  <chr>  
    ##  1  2013     1     1     1400 EWR    UA     
    ##  2  2013     1     1     1416 LGA    UA     
    ##  3  2013     1     1     1089 JFK    AA     
    ##  4  2013     1     1     1576 JFK    B6     
    ##  5  2013     1     1      762 LGA    DL     
    ##  6  2013     1     1      719 EWR    UA     
    ##  7  2013     1     1     1065 EWR    B6     
    ##  8  2013     1     1      229 LGA    EV     
    ##  9  2013     1     1      944 JFK    B6     
    ## 10  2013     1     1      733 LGA    AA     
    ## # ... with 336,766 more rows

## 9.4 Parte 4: Dplyr - mutate

### 1.Las variables horario_salida y salida_programada tienen un formato conveniente para leer, pero es difícil realizar cualquier cálculo con ellas porque no son realmente números continuos. Transfórmalas hacia un formato más conveniente como número de minutos desde la medianoche.

``` r
mutate(flights, sched_dep_time = (dep_time %/% 100 * 60 + dep_time %% 100) %% 1440)
```

    ## # A tibble: 336,776 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <dbl>     <dbl>    <int>          <int>
    ##  1  2013     1     1      517            317         2      830            819
    ##  2  2013     1     1      533            333         4      850            830
    ##  3  2013     1     1      542            342         2      923            850
    ##  4  2013     1     1      544            344        -1     1004           1022
    ##  5  2013     1     1      554            354        -6      812            837
    ##  6  2013     1     1      554            354        -4      740            728
    ##  7  2013     1     1      555            355        -5      913            854
    ##  8  2013     1     1      557            357        -3      709            723
    ##  9  2013     1     1      557            357        -3      838            846
    ## 10  2013     1     1      558            358        -2      753            745
    ## # ... with 336,766 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

### 2.Compara tiempo_vuelo con horario_llegada - horario_salida. ¿Qué esperas ver? ¿Qué ves? ¿Qué necesitas hacer para arreglarlo?

``` r
flights %>%
filter(sched_arr_time - sched_dep_time == air_time)
```

    ## # A tibble: 902 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     2     1555           1445        70     1845           1656
    ##  2  2013     1     2     1605           1607        -2     2010           1947
    ##  3  2013     1     2     1940           1932         8     2228           2253
    ##  4  2013     1     3      557            601        -4      724            725
    ##  5  2013     1     3      855            900        -5     1157           1227
    ##  6  2013     1     3     1124           1130        -6     1407           1450
    ##  7  2013     1     4      702            659         3      901            942
    ##  8  2013     1     4     1457           1500        -3     1824           1837
    ##  9  2013     1     4     1711           1715        -4     2003           2040
    ## 10  2013     1     5      900            900         0     1118           1130
    ## # ... with 892 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

``` r
# Como la diferencia entre el horario de llegada y el horario de salida no es igual al tiempo de vuelo. se usará mutate:
flights %>%
mutate(air_time, air_time = sched_arr_time - sched_dep_time)
```

    ## # A tibble: 336,776 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     1      517            515         2      830            819
    ##  2  2013     1     1      533            529         4      850            830
    ##  3  2013     1     1      542            540         2      923            850
    ##  4  2013     1     1      544            545        -1     1004           1022
    ##  5  2013     1     1      554            600        -6      812            837
    ##  6  2013     1     1      554            558        -4      740            728
    ##  7  2013     1     1      555            600        -5      913            854
    ##  8  2013     1     1      557            600        -3      709            723
    ##  9  2013     1     1      557            600        -3      838            846
    ## 10  2013     1     1      558            600        -2      753            745
    ## # ... with 336,766 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <int>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

### 3.Compara horario_salida, salida_programada, y atraso_salida. ¿Cómo esperarías que esos tres números estén relacionados?

``` r
# Se espera que el horario salida sea igual a la salida programada (ambos en minutos después de medianoche) sumada con el dep_delay.
flights %>%
mutate(dep_time, dep_time=dep_time%%100+(dep_time-dep_time%%100)/100*60) %>%
mutate(sched_dep_time, sched_dep_time=sched_dep_time%%100+(sched_dep_time-sched_dep_time%%100)/100*60) %>%
select(dep_time, sched_dep_time, dep_delay) %>%
filter(sched_dep_time + dep_delay != dep_time)
```

    ## # A tibble: 1,207 x 3
    ##    dep_time sched_dep_time dep_delay
    ##       <dbl>          <dbl>     <dbl>
    ##  1      528           1115       853
    ##  2       42           1439        43
    ##  3       86           1370       156
    ##  4       32           1439        33
    ##  5       50           1305       185
    ##  6      155           1439       156
    ##  7       25           1439        26
    ##  8       66           1365       141
    ##  9       14           1439        15
    ## 10       37           1350       127
    ## # ... with 1,197 more rows

### 4.Encuentra los 10 vuelos más retrasados utilizando una función de ordenamiento. ¿Cómo quieres manejar los empates? Lee atentamente la documentación de min_rank().

``` r
# La función min_rank() es aquella que devuelve los valores de un vector de manera de ranking pero, como este establece un “min”, a los empates se les designa el rango más bajo posible.
v_retrasados<-head(arrange(flights,desc(arr_delay)),10)
v_retrasados
```

    ## # A tibble: 10 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     9      641            900      1301     1242           1530
    ##  2  2013     6    15     1432           1935      1137     1607           2120
    ##  3  2013     1    10     1121           1635      1126     1239           1810
    ##  4  2013     9    20     1139           1845      1014     1457           2210
    ##  5  2013     7    22      845           1600      1005     1044           1815
    ##  6  2013     4    10     1100           1900       960     1342           2211
    ##  7  2013     3    17     2321            810       911      135           1020
    ##  8  2013     7    22     2257            759       898      121           1026
    ##  9  2013    12     5      756           1700       896     1058           2020
    ## 10  2013     5     3     1133           2055       878     1250           2215
    ## # ... with 11 more variables: arr_delay <dbl>, carrier <chr>, flight <int>,
    ## #   tailnum <chr>, origin <chr>, dest <chr>, air_time <dbl>, distance <dbl>,
    ## #   hour <dbl>, minute <dbl>, time_hour <dttm>

``` r
v_R<-v_retrasados$arr_delay
v_R
```

    ##  [1] 1272 1127 1109 1007  989  931  915  895  878  875

``` r
min_rank(v_R)
```

    ##  [1] 10  9  8  7  6  5  4  3  2  1

### 5.¿Qué devuelve 1:3 + 1:10? ¿Por qué?

``` r
1:3+1:10
```

    ## Warning in 1:3 + 1:10: longitud de objeto mayor no es múltiplo de la longitud de
    ## uno menor

    ##  [1]  2  4  6  5  7  9  8 10 12 11

``` r
#### Manda un mensaje en la que indica que los objetos al no tener la misma longitud, R va repetir el primer vector hasat que alcance la longitud deseada.
#Ejem: rpta de 1:3+1:10
```

### 6.¿Qué funciones trigonométricas proporciona R?

``` r
###Posee a seno, coseno y tangente y para tener a contagente, secante y cosecantes seinverte las primeras tres. Asimismo, podemos hallar las inversas de las 6 razones trigonométricas.
 
#### Valores
x=pi/8
y=pi/6
 
#### Razones trigonométricas
sin(x)
```

    ## [1] 0.3826834

``` r
cos(x)
```

    ## [1] 0.9238795

``` r
tan(x)
```

    ## [1] 0.4142136

``` r
1/sin(x)
```

    ## [1] 2.613126

``` r
1/cos(x)
```

    ## [1] 1.082392

``` r
1/tan(x)
```

    ## [1] 2.414214

``` r
#### Inversa
asin(y)
```

    ## [1] 0.5510696

``` r
acos(y)
```

    ## [1] 1.019727

``` r
atan(y)
```

    ## [1] 0.4823479

``` r
asin(1/y)
```

    ## Warning in asin(1/y): Se han producido NaNs

    ## [1] NaN

``` r
acos(1/y)
```

    ## Warning in acos(1/y): Se han producido NaNs

    ## [1] NaN

``` r
atan(1/y)
```

    ## [1] 1.088448

## 9.5 Parte 5: Dplyr - group by & summarize

### 1. Haz una lluvia de ideas de al menos 5 formas diferentes de evaluar las características de un retraso típico de un grupo de vuelos. Considera los siguientes escenarios:

#### a.Un vuelo llega 15 minutos antes 50% del tiempo, y 15 minutos tarde 50% del tiempo.

``` r
filter(flights, arr_delay < 15)%>%
group_by(year, month, day,flight)%>%  
summarise(v_15mina=quantile(arr_delay, 0.5, na.rm=TRUE))
```

    ## `summarise()` has grouped output by 'year', 'month', 'day'. You can override using the `.groups` argument.

    ## # A tibble: 227,640 x 5
    ## # Groups:   year, month, day [365]
    ##     year month   day flight v_15mina
    ##    <int> <int> <int>  <int>    <dbl>
    ##  1  2013     1     1      1      6  
    ##  2  2013     1     1      3      9.5
    ##  3  2013     1     1      4    -14.5
    ##  4  2013     1     1      6    -19  
    ##  5  2013     1     1      7    -19  
    ##  6  2013     1     1      9      4  
    ##  7  2013     1     1     11    -18  
    ##  8  2013     1     1     15     -8  
    ##  9  2013     1     1     16     -6  
    ## 10  2013     1     1     19     11  
    ## # ... with 227,630 more rows

``` r
filter(flights, arr_delay > 15)%>%
group_by(year, month, day,flight)%>%  
summarise(v_15mint=quantile(arr_delay, 0.5, na.rm=TRUE))
```

    ## `summarise()` has grouped output by 'year', 'month', 'day'. You can override using the `.groups` argument.

    ## # A tibble: 75,402 x 5
    ## # Groups:   year, month, day [365]
    ##     year month   day flight v_15mint
    ##    <int> <int> <int>  <int>    <dbl>
    ##  1  2013     1     1      1       29
    ##  2  2013     1     1      8       27
    ##  3  2013     1     1     11       49
    ##  4  2013     1     1     12       20
    ##  5  2013     1     1     15       21
    ##  6  2013     1     1     17       42
    ##  7  2013     1     1     21       49
    ##  8  2013     1     1     22       33
    ##  9  2013     1     1     30       23
    ## 10  2013     1     1     32       60
    ## # ... with 75,392 more rows

#### b.Un vuelo llega siempre 10 minutos tarde.

``` r
filter(flights, arr_delay == 10)%>%
group_by(year, month, day,flight)
```

    ## # A tibble: 3,373 x 19
    ## # Groups:   year, month, day, flight [3,370]
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     1      624            630        -6      840            830
    ##  2  2013     1     1      717            720        -3      850            840
    ##  3  2013     1     1      745            745         0     1135           1125
    ##  4  2013     1     1      805            805         0     1015           1005
    ##  5  2013     1     1      811            815        -4     1026           1016
    ##  6  2013     1     1      921            900        21     1237           1227
    ##  7  2013     1     1     1158           1205        -7     1530           1520
    ##  8  2013     1     1     1211           1215        -4     1423           1413
    ##  9  2013     1     1     1455           1459        -4     1655           1645
    ## 10  2013     1     1     1554           1600        -6     1830           1820
    ## # ... with 3,363 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

#### c.Un vuelo llega 30 minutos antes 50% del tiempo, y 30 minutos tarde 50% del tiempo.

``` r
filter(flights, arr_delay < 30)%>%
group_by(year, month, day,flight)%>%  
summarise(v_30minta=quantile(arr_delay, 0.5, na.rm=TRUE))
```

    ## `summarise()` has grouped output by 'year', 'month', 'day'. You can override using the `.groups` argument.

    ## # A tibble: 250,967 x 5
    ## # Groups:   year, month, day [365]
    ##     year month   day flight v_30minta
    ##    <int> <int> <int>  <int>     <dbl>
    ##  1  2013     1     1      1      17.5
    ##  2  2013     1     1      3       9.5
    ##  3  2013     1     1      4     -14.5
    ##  4  2013     1     1      6     -19  
    ##  5  2013     1     1      7     -19  
    ##  6  2013     1     1      8      27  
    ##  7  2013     1     1      9       4  
    ##  8  2013     1     1     11     -18  
    ##  9  2013     1     1     12      20  
    ## 10  2013     1     1     15       6.5
    ## # ... with 250,957 more rows

``` r
filter(flights, arr_delay >30)%>%
group_by(year, month, day,,flight)%>%  
summarise(v_30mint=quantile(arr_delay, 0.5, na.rm=TRUE))
```

    ## `summarise()` has grouped output by 'year', 'month', 'day'. You can override using the `.groups` argument.

    ## # A tibble: 50,419 x 5
    ## # Groups:   year, month, day [365]
    ##     year month   day flight v_30mint
    ##    <int> <int> <int>  <int>    <dbl>
    ##  1  2013     1     1     11       49
    ##  2  2013     1     1     17       42
    ##  3  2013     1     1     21       73
    ##  4  2013     1     1     22       33
    ##  5  2013     1     1     32       60
    ##  6  2013     1     1     39       50
    ##  7  2013     1     1     63       80
    ##  8  2013     1     1     66       36
    ##  9  2013     1     1     95       34
    ## 10  2013     1     1    128       35
    ## # ... with 50,409 more rows

#### d.Un vuelo llega a tiempo en el 99% de los casos. 1% de las veces llega 2 horas tarde.

``` r
filter(flights, arr_delay == 0)%>%
group_by(year, month, day,flight)%>%  
summarise(v_0min=quantile(arr_delay, 0.99, na.rm=TRUE))
```

    ## `summarise()` has grouped output by 'year', 'month', 'day'. You can override using the `.groups` argument.

    ## # A tibble: 5,397 x 5
    ## # Groups:   year, month, day [365]
    ##     year month   day flight v_0min
    ##    <int> <int> <int>  <int>  <dbl>
    ##  1  2013     1     1     27      0
    ##  2  2013     1     1    269      0
    ##  3  2013     1     1    537      0
    ##  4  2013     1     1    615      0
    ##  5  2013     1     1    951      0
    ##  6  2013     1     1   1075      0
    ##  7  2013     1     1   1171      0
    ##  8  2013     1     1   1280      0
    ##  9  2013     1     1   1351      0
    ## 10  2013     1     1   1757      0
    ## # ... with 5,387 more rows

``` r
filter(flights, arr_delay > 120)%>%
group_by(year, month, day,flight)%>%  
summarise(v_120mint=quantile(arr_delay,0.01 , na.rm=TRUE))
```

    ## `summarise()` has grouped output by 'year', 'month', 'day'. You can override using the `.groups` argument.

    ## # A tibble: 9,951 x 5
    ## # Groups:   year, month, day [364]
    ##     year month   day flight v_120mint
    ##    <int> <int> <int>  <int>     <dbl>
    ##  1  2013     1     1    181       127
    ##  2  2013     1     1    525       125
    ##  3  2013     1     1    856       123
    ##  4  2013     1     1   1086       145
    ##  5  2013     1     1   1999       246
    ##  6  2013     1     1   3347       250
    ##  7  2013     1     1   3944       851
    ##  8  2013     1     1   4092       123
    ##  9  2013     1     1   4181       136
    ## 10  2013     1     1   4255       151
    ## # ... with 9,941 more rows

#### e.¿Qué es más importante: retraso de la llegada o demora de salida?

``` r
##### Es más importante la demora en la salida, ya que esto también repercute en la hora de llegada lo cual significa un atraso a los planes que tendríamos en nuestro destino.
```

### 2.Sugiere un nuevo enfoque que te dé el mismo output que no_cancelados %>% count(destino) y no_cancelado %>% count(codigo_cola, wt = distancia) (sin usar count()).

``` r
nocancel <-filter(flights, !is.na(dep_delay), !is.na(arr_delay))
nocancel %>% 
  count(dest)
```

    ## # A tibble: 104 x 2
    ##    dest      n
    ##    <chr> <int>
    ##  1 ABQ     254
    ##  2 ACK     264
    ##  3 ALB     418
    ##  4 ANC       8
    ##  5 ATL   16837
    ##  6 AUS    2411
    ##  7 AVL     261
    ##  8 BDL     412
    ##  9 BGR     358
    ## 10 BHM     269
    ## # ... with 94 more rows

``` r
nocancel %>% 
  group_by(dest) %>%
  summarise(length(dest))
```

    ## # A tibble: 104 x 2
    ##    dest  `length(dest)`
    ##    <chr>          <int>
    ##  1 ABQ              254
    ##  2 ACK              264
    ##  3 ALB              418
    ##  4 ANC                8
    ##  5 ATL            16837
    ##  6 AUS             2411
    ##  7 AVL              261
    ##  8 BDL              412
    ##  9 BGR              358
    ## 10 BHM              269
    ## # ... with 94 more rows

### 3.Nuestra definición de vuelos cancelados (is.na(atraso_salida) \| is.na (atraso_llegada)) es un poco subóptima. ¿Por qué? ¿Cuál es la columna más importante?

``` r
# La columna más importante es la primera por que el segundo no afecta en la función pues ya se usa "is.na(atraso_salida)"
```

### 4.Mira la cantidad de vuelos cancelados por día. ¿Hay un patrón? ¿La proporción de vuelos cancelados está relacionada con el retraso promedio?

``` r
# Esta función ve la cantidad de vuelos cancelados por dia:
 
Cancelados_dia <- group_by(flights, year, month, day)
 
Cancelados_dia %>% 
  summarise_all(funs(sum(is.na(.))))
```

    ## # A tibble: 365 x 19
    ## # Groups:   year, month [12]
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <int>    <int>          <int>
    ##  1  2013     1     1        4              0         4        5              0
    ##  2  2013     1     2        8              0         8       10              0
    ##  3  2013     1     3       10              0        10       10              0
    ##  4  2013     1     4        6              0         6        6              0
    ##  5  2013     1     5        3              0         3        3              0
    ##  6  2013     1     6        1              0         1        1              0
    ##  7  2013     1     7        3              0         3        3              0
    ##  8  2013     1     8        4              0         4        4              0
    ##  9  2013     1     9        5              0         5        7              0
    ## 10  2013     1    10        3              0         3        3              0
    ## # ... with 355 more rows, and 11 more variables: arr_delay <int>,
    ## #   carrier <int>, flight <int>, tailnum <int>, origin <int>, dest <int>,
    ## #   air_time <int>, distance <int>, hour <int>, minute <int>, time_hour <int>

### 5.¿Qué compañía tiene los peores retrasos? Desafío: ¿puedes desenredar el efecto de malos aeropuertos vs. el efecto de malas aerolíneas? ¿Por qué o por qué no? (Sugerencia: piensa en vuelos %>% group_by(aerolinea, destino)

``` r
arrange(flights, arr_delay) %>%
group_by(arr_delay, carrier, dest) %>%
summarise()
```

    ## `summarise()` has grouped output by 'arr_delay', 'carrier'. You can override using the `.groups` argument.

    ## # A tibble: 39,730 x 3
    ## # Groups:   arr_delay, carrier [4,683]
    ##    arr_delay carrier dest 
    ##        <dbl> <chr>   <chr>
    ##  1       -86 VX      SFO  
    ##  2       -79 VX      SFO  
    ##  3       -75 AA      SEA  
    ##  4       -75 UA      LAX  
    ##  5       -74 AS      SEA  
    ##  6       -73 UA      SFO  
    ##  7       -71 B6      LAX  
    ##  8       -71 DL      PDX  
    ##  9       -71 UA      SFO  
    ## 10       -70 B6      LGB  
    ## # ... with 39,720 more rows

### 6.¿Qué hace el argumento sort a count(). ¿Cuándo podrías usarlo?

``` r
# Sort en count nos muestra de forma descendente la cantidad de datos con su respectivo valor.
# Ejm, de uso: Para hallar en qué día del mes salieron más vuelos
flights %>%
  count(day, sort=TRUE)
```

    ## # A tibble: 31 x 2
    ##      day     n
    ##    <int> <int>
    ##  1    18 11399
    ##  2    11 11359
    ##  3    22 11345
    ##  4    15 11317
    ##  5     8 11271
    ##  6    10 11227
    ##  7    17 11222
    ##  8     3 11211
    ##  9    21 11141
    ## 10    20 11111
    ## # ... with 21 more rows

## 9.6 Parte 6: Dplyr - transformaciones agrupadas

### 1.Remítase a las listas de funciones útiles de mutación y filtrado. Describe cómo cambia cada operación cuando las combinas con la agrupación.

### a.Selecciona datos basándose en los valores.

filter() ### b.Crea nuevas variables respecto a los datos filtrados.
mutate()

### 2.¿Qué avión (codigo_cola) tiene el peor registro de tiempo?

``` r
nocancelados<-flights %>% 
filter(!is.na(dep_delay),!is.na(arr_delay))
 
peor_reg<-nocancelados %>%
  count(tailnum,wt=air_time)
arrange(peor_reg,n)
```

    ## # A tibble: 4,037 x 2
    ##    tailnum     n
    ##    <chr>   <dbl>
    ##  1 N505SW     43
    ##  2 N746SK     50
    ##  3 N824AS     53
    ##  4 N881AS     57
    ##  5 N766SK     60
    ##  6 N701SK     64
    ##  7 N760SK     64
    ##  8 N795SK     66
    ##  9 N726SK     67
    ## 10 N772SK     67
    ## # ... with 4,027 more rows

### 3.¿A qué hora del día deberías volar si quieres evitar lo más posible los retrasos?

``` r
f_hm <-select(flights,hour, minute, dep_delay, arr_delay)

no_cancelados<-f_hm %>% 
  filter(!is.na(dep_delay),!is.na(arr_delay))

sin_ret<-no_cancelados%>%
  filter((arr_delay<0) & (dep_delay<0))%>%
  select(hour,minute,dep_delay,arr_delay)
arrange(sin_ret,hour,minute)
```

    ## # A tibble: 144,346 x 4
    ##     hour minute dep_delay arr_delay
    ##    <dbl>  <dbl>     <dbl>     <dbl>
    ##  1     5      0        -4       -19
    ##  2     5      0        -2       -10
    ##  3     5      0        -6       -11
    ##  4     5      0        -6       -23
    ##  5     5      0        -3        -1
    ##  6     5      0       -10       -14
    ##  7     5      0        -7        -5
    ##  8     5      0        -7        -8
    ##  9     5      0        -7        -3
    ## 10     5      0        -7       -12
    ## # ... with 144,336 more rows

### 4.Para cada destino, calcula los minutos totales de demora. Para cada vuelo, calcula la proporción de la demora total para su destino.

``` r
demora_total <- group_by(flights, dest)
summarise(demora_total, demora_min <- sum(arr_delay, na.rm = TRUE))
```

    ## # A tibble: 105 x 2
    ##    dest  `demora_min <- sum(arr_delay, na.rm = TRUE)`
    ##    <chr>                                        <dbl>
    ##  1 ABQ                                           1113
    ##  2 ACK                                           1281
    ##  3 ALB                                           6018
    ##  4 ANC                                            -20
    ##  5 ATL                                         190260
    ##  6 AUS                                          14514
    ##  7 AVL                                           2089
    ##  8 BDL                                           2904
    ##  9 BGR                                           2874
    ## 10 BHM                                           4540
    ## # ... with 95 more rows

``` r
proporcion <- group_by(flights, dest)
summarise(proporcion, demora_min <- mean(arr_delay, na.rm = TRUE))
```

    ## # A tibble: 105 x 2
    ##    dest  `demora_min <- mean(arr_delay, na.rm = TRUE)`
    ##    <chr>                                         <dbl>
    ##  1 ABQ                                            4.38
    ##  2 ACK                                            4.85
    ##  3 ALB                                           14.4 
    ##  4 ANC                                           -2.5 
    ##  5 ATL                                           11.3 
    ##  6 AUS                                            6.02
    ##  7 AVL                                            8.00
    ##  8 BDL                                            7.05
    ##  9 BGR                                            8.03
    ## 10 BHM                                           16.9 
    ## # ... with 95 more rows

### 5.Los retrasos suelen estar temporalmente correlacionados: incluso una vez que el problema que causó el retraso inicial se ha resuelto, los vuelos posteriores se retrasan para permitir que salgan los vuelos anteriores. Usando lag(), explora cómo el retraso de un vuelo está relacionado con el retraso del vuelo inmediatamente anterior.

``` r
lag(flights$arr_time, n = 1L, default = NA, order_by = NULL)
```

    ##     [1]   NA  830  850  923 1004  812  740  913  709  838  753  849  853  924
    ##    [15]  923  941  702  854  851  837  844  812  821  858  837  858  807  945
    ##    [29]  925 1039  833 1017  920  933  909  840 1018 1137 1016  824  721  824
    ##    [43]  740 1028  930  739  922  837  931  815  910 1023  936  932  936 1021
    ##    [57] 1037 1002  854  949 1007  948  959  944 1027 1008 1008  907  959 1123
    ##    [71] 1058  852 1151 1023  911  850 1017 1013 1111 1020 1052  959 1041 1049
    ##    [85]  857 1041 1011  854 1047  918 1104 1038 1107 1043 1059 1135 1119  939
    ##    [99] 1041 1025  955 1056 1039 1103 1053 1057 1022  949  900  903 1132 1103
    ##   [113] 1015 1118 1006 1043 1043 1048 1100 1006 1047 1026 1040 1103 1047 1005
    ##   [127] 1254  940 1249 1153  932 1014 1019 1151 1027 1058 1136 1145 1027 1150
    ##   [141] 1152 1117 1018 1052 1021 1006 1134 1210 1027 1311 1053 1138 1001 1155
    ##   [155] 1032 1102 1215 1046 1147 1143 1226 1222 1140 1516 1107 1124 1157 1102
    ##   [169] 1140 1223 1211 1048 1045 1207 1309 1134 1020 1004 1228 1331 1241 1219
    ##   [183] 1346 1244 1058 1313 1206 1052 1039 1152 1237 1026 1404 1221 1233 1231
    ##   [197] 1028 1220 1218 1237 1121 1219 1057 1252 1120 1235 1257 1238 1127 1119
    ##   [211] 1226 1300 1146 1053 1155 1141 1320 1336 1241 1056 1313 1151 1255 1408
    ##   [225] 1239 1147 1219 1204 1225 1133 1246 1254 1140 1204 1356 1258 1351 1350
    ##   [239] 1427 1229 1353 1323 1305 1130 1221 1223 1325 1231 1352 1339 1359 1401
    ##   [253] 1302 1402 1326 1203 1407 1210 1201 1210 1342 1345 1410 1428 1305 1402
    ##   [267] 1222 1440 1318 1447 1331 1330 1410 1435 1445 1325 1303 1504 1421 1422
    ##   [281] 1301 1345 1324 1440 1448 1429 1445 1512 1422 1335 1302 1350 1454 1450
    ##   [295] 1253 1452 1517 1507 1441 1312 1310 1342 1452 1530 1256 1338 1408 1318
    ##   [309] 1645 1501 1519 1500 1503 1325 1540 1423 1414 1525 1415 1451 1403 1512
    ##   [323] 1520 1631 1440 1449 1523 1340 1410 1451 1554 1415 1342 1616 1722 1424
    ##   [337] 1607 1611 1624 1524 1541 1540 1451 1501 1401 1601 1454 1532 1459 1633
    ##   [351] 1518 1629 1402 1553 1518 1430 1523 1622 1622 1559 1507 1413 1412 1454
    ##   [365] 1358 1602 1625 1651 1606 1638 1624 1613 1608 1508 1649 1642 1654 1709
    ##   [379] 1617 1658 2005 1736 1504 1456 1446 1549 1556 1452 1538 1646 1537 1612
    ##   [393] 1538 1537 1659 1742 1645 1634 1650 1646 1717 1603 1726 1557 1517 1735
    ##   [407] 1724 1613 1748 1535 1701 1659 1803 1718 1735 1727 1627 1636 1840 1558
    ##   [421] 1658 1728 1600 1635 1729 1803 1651 1651 1634 1637 1753 1707 1601 1554
    ##   [435] 1635 1815 1731 1655 1753 1649 1830 1758 1652 1658 1651 1750 1809 1802
    ##   [449] 1638 1654 1838 1723 1651 1748 1813 1811 1753 1657 1805 1714 1705 1834
    ##   [463] 1837 1835 1643 1817 1830 1731 1858 1831 1828 1831 1934 1714 1841 1655
    ##   [477] 1836 1854 2002 1731 1720 1733 1650 1637 1745 1809 1755 1709 1827 1904
    ##   [491] 1853 1854 2020 1852 1933 1731 1753 1823 1751 1912 1851 1844 1732 1826
    ##   [505] 1749 1933 1701 1857 1830 1737 1910 1746 1808 1718 1910 1844 1712 1750
    ##   [519] 1834 1720 1751 1839 1818 1912 1817 1804 1735 1711 2002 1953 1847 1913
    ##   [533] 1827 1852 2010 1748 1912 1945 1904 2002 2054 2007 1855 1925 1940 1740
    ##   [547] 1907 1902 1913 1740 1956 1935 1903 1824 1913 1830 1747 1858 1815 1859
    ##   [561] 1746 1944 1832 1937 2009 2000 2030 2005 1752 2020 1804 1953 2027 2025
    ##   [575] 1941 1921 1948 1808 2026 1856 2044 2054 1924 1928 2006 2037 1820 1918
    ##   [589] 2005 1939 2042 2006 1915 1947 2140 1902 1920 2154 1908 2121 1929 2045
    ##   [603] 2054 2042 2043 2004 2052 2013 2126 2039 2028 2047 2030 1956 2051 2102
    ##   [617] 2158 2028 1925 2043 2052 2055 1925 1943 2109 2044 2015 2058 2036 1904
    ##   [631] 2027 1905 2105 2020 1957 1945 1951 1930 2125 2011 2008 2021 2117 2002
    ##   [645] 2251 2111 2117 2132 2051 2122 2120 1928 2013 2101 2008 2216 2036 2203
    ##   [659] 2056 2046 2132 2154 2105 2023 2131 1948 2059 2144 2027 2014 2107 2022
    ##   [673] 2055 2223 1958 2144 2052 1955 2339 2147 2336 2238 2131 2007 2142 2249
    ##   [687] 2004 2055 2140 2203 2212 2133 2142 2034 2012 2151 2212 2139 2157 2311
    ##   [701] 2211 2239 2212 2126 2126 2118 2050 2200 2242 2238 2242 2053 2125 2315
    ##   [715] 2139 2239 2037 2259 2258 2117    3 2233 2126 2223 2250 2109   29 2238
    ##   [729] 2033 2231 2124 2247 2148 2237 2358 2314 2257 2145 2100 2307 2321 2331
    ##   [743] 2310 2255 2054 2306 2302 2230 2132 2223 2206 2145 2154 2120 2149   NA
    ##   [757] 2215 2223 2318 2314 2148 2351 2240 2328 2334 2358 2157 2319 2205 2132
    ##   [771] 2150 2354 2308 2344 2134 2337 2224 2317 2144 2328 2229 2349 2357 2254
    ##   [785] 2350 2156 2210 2337 2240 2237 2342 2235    8 2307 2156  146 2345 2354
    ##   [799]   25 2351 2340 2240 2330 2202 2358   16    6 2312   26 2243 2342   20
    ##   [813]   25  210   43 2254   46   58 2400 2339  249  140 2331 2324  149 2340
    ##   [827] 2352 2342   28   32   24   21   22  131   32  314  425  418  425   NA
    ##   [841]   NA   NA   NA  518  233  703  809  831  840  959  845  841  909  931
    ##   [855]  856  750  724  837  832  838  916  809  906  814  751  819  846  737
    ##   [869]  748  747  646  733  912  851  846  825  859  909  826  854  756  901
    ##   [883] 1053 1001  837  912  820  908  833  935  954  850  935  730  746  844
    ##   [897] 1010  948  948  727  812  941  806 1012 1005  832 1012  821  732  926
    ##   [911]  926 1013  804  930  854  849  738  903  951  934  946 1003  955  929
    ##   [925] 1031 1005 1015 1013 1014  806  959  917  851 1017 1001 1054  947  908
    ##   [939] 1142 1209  827 1022 1006  945  844 1026 1013 1047 1027  905  949  846
    ##   [953] 1039 1024 1001  846 1047 1011 1206 1105  914 1047  902 1043 1045  844
    ##   [967] 1042  926 1116 1033 1025  932 1005  858 1017 1112 1118 1051 1048  942
    ##   [981]  956  912 1055  900 1055 1100 1048 1037 1058 1018 1052  901 1102 1136
    ##   [995]  951 1039 1300 1133 1049 1020  950 1008 1100 1126  944 1109 1008  933
    ##  [1009] 1107 1015  931 1044 1130 1127 1117 1259 1206 1142 1053  952 1141 1012
    ##  [1023] 1034 1103 1120 1315 1059  947  952 1021  938 1151 1154 1018 1039 1226
    ##  [1037] 1059 1114 1403 1027 1205  955 1134 1017 1103 1157 1114 1102 1052 1154
    ##  [1051] 1157 1112 1146 1225 1022 1050 1130 1041 1230 1128 1135 1204 1246 1035
    ##  [1065] 1205 1054 1204 1203 1146 1016 1218 1026 1313 1231 1525 1114 1114 1041
    ##  [1079] 1252 1133 1353 1029 1135 1240 1248 1051 1431 1124 1233 1209 1212 1331
    ##  [1093] 1233 1203 1255 1223 1252 1157 1235 1305 1104 1110 1055 1242 1257 1051
    ##  [1107] 1054 1113 1219 1157 1104 1117 1108 1115 1336 1211 1240 1312 1319 1307
    ##  [1121] 1259 1105 1251 1235 1220 1228 1128 1215 1250 1242 1343 1251 1330 1253
    ##  [1135] 1118 1223 1219 1328 1255 1345 1140 1135 1235 1328 1400 1309 1347 1257
    ##  [1149] 1336 1259 1156 1344 1242 1347 1321 1413 1356 1347 1147 1349 1341 1207
    ##  [1163] 1334 1202 1421 1343 1406 1408 1201 1430 1220 1312 1313 1231 1437 1248
    ##  [1177] 1407 1434 1315 1340 1309 1445 1416 1451 1333 1431 1420 1600 1436 1449
    ##  [1191] 1442 1436 1411 1435 1353 1343 1318 1452 1313 1520 1437 1517 1509 1427
    ##  [1205] 1254 1247 1441 1342 1512 1408 1418 1513 1504 1340 1511 1316 1349 1311
    ##  [1219] 1457 1523 1451 1421 1520 1334 1513 1521 1329 1354 1430 1505 1423 1408
    ##  [1233] 1354 1614 1446 1403 1417 1429 1328 1538 1556 1521 1453 1431 1718 1555
    ##  [1247] 1535 1349 1552 1505 1545 1501 1600 1526 1409 1356 1529 1613 1537 1448
    ##  [1261] 1557 1437 1601 1358 1442 1535 1518 1456 1626 1634 1633 1513 1620 1552
    ##  [1275] 1650 1433 1621 1441 1804 1616 1419 1503 1414 1631 1617 1611 1643 1651
    ##  [1289] 1603 1548 1648 1627 1650 1702 1940 1642 1548 1702 1509 1509 1635 1715
    ##  [1303] 1648 1509 1516 1550 1611 1504 1634 1723 1520 1710 1736 1624 1515 1604
    ##  [1317] 1609 1715 1654 1730 1542 1754 1821 1745 1618 1742 1651 1733 1800 1640
    ##  [1331] 1612 1639 1607 1724 1637 1707 1755 1715 1749 1733 1821 1750 1755 1715
    ##  [1345] 1826 1558 1824 1607 1628 1741 1643 1647 1743 1651 1822 1653 1811 1741
    ##  [1359] 1608 1807 1607 1824 1804 1732 1642 1814 1827 1616 1724 1650 1653 1713
    ##  [1373] 1852 1700 1833 1814 1745 1658 1803 1723 1652 1832 1823 1729 1650 1736
    ##  [1387] 1726 1755 1853 1709 1752 1859 1910 1844 1846 1738 1824 1713 1803 1850
    ##  [1401] 2047 1856 1805 1920 1830 1819 1743 1853 1710 1922 1824 1905 1926 1838
    ##  [1415] 1727 1853 1919 1845 1921 1935 1906 1935 1916 1853 1846 1923 1746 1800
    ##  [1429] 1809 1704 1803 1809 1843 1826 1800 1817 1735 1937 1851 2010 1730 2003
    ##  [1443] 1710 2105 1924 1736 1835 1922 1808 1846 1839 1820 1913 1931 1836 1839
    ##  [1457] 1939 1744 1935 1927 1859 1805 1853 1950 1905 1905 1838 1950 1854 1958
    ##  [1471] 1952 2017 1757 1814 1931 1915 1810 1843 2039 1759 2026 1911 1955 2022
    ##  [1485] 1920 1857 2031 2008 1908 2026 1845 1958 2006 1909 2015 2035 1857 1927
    ##  [1499] 2007 1947 1837 2007 1916 2053 2033 1921 1857 1959 2022 2003 2026 2116
    ##  [1513] 2031 2042 1920 1829 1843 1952 2054 2012 2040 2039 1850 2004 2044 2035
    ##  [1527] 1947 1908 2028 2028 1950 2035 2026 2123 2035 1938 2053 1835 2043 1927
    ##  [1541] 1938 1904 1904 1904 1915 1934 2041 2052 1936 1929 2111 2123 2057 1902
    ##  [1555] 1941 2055 1932 2146 2005 1951 2050 1946 2005 2008 2140 2110 1955 1948
    ##  [1569] 2132 2145 2146 1923 2051 2149 2131 1945 2000 2033 2115 2022 2035 2029
    ##  [1583] 2107 2153 1940 2104 2103 2130 2104 1926 2132 1951 2147 2045 2133 2321
    ##  [1597] 2145 1942 2156 1953 2138 2050 2236 2137 2112 2333 2208 2235 2038 2229
    ##  [1611] 2030 2119 2351 2128 1959 2024 2126 2250 2021 2148 2352 2054 2038 2021
    ##  [1625] 2203 2201 2228 2213 2053 2216 2037 2137 2227 2116 2218 2220 2219 2225
    ##  [1639] 2139 2255 2200 2315 2055 2143 2110 2225 2224 2041 2220 2255 2218 2359
    ##  [1653] 2232 2236 2227 2107 2302 2138 2301 2034 2242 2226 2052 2156 2228 2240
    ##  [1667] 2048 2225 2215 2143 2253 2236 2227 2241 2128 2151 2249 2303 2153 2330
    ##  [1681] 2256 2152 2102 2309 2308 2126 2326 2121 2146 2256 2147 2132 2203 2314
    ##  [1695] 2305 2216 2329 2206 2336 2309 2202 2330   13    8 2353 2314 2220 2325
    ##  [1709] 2137 2351 2134  110 2151 2210 2318   NA 2251 2229 2302 2329 2239 2220
    ##  [1723] 2229 2256 2331 2343 2349 2224 2347   36 2258 2240    7 2359   13 2218
    ##  [1737] 2211 2346 2345 2322    5 2257 2242 2342 2227  153 2221   37   43    1
    ##  [1751] 2340   36  208 2301   32  111   54   NA 2234 2255 2333  142 2331  231
    ##  [1765]  300 2339 2350 2358 2340  122   26    5   20   33  222   58  427  413
    ##  [1779]   NA   NA   NA   NA   NA   NA   NA   NA  504  203  700  650  830  851
    ##  [1793]  835 1009  843  759  721  858  819  727  735  903  900  852  756  700
    ##  [1807]  724  846  909  802  726  843  736  753  730  709  852  917  915  953
    ##  [1821]  756  853  912  751  816  829  913 1044 1128  928  954  923  914  835
    ##  [1835]  945  947  905  948  853  826  724  843  801 1024  752 1032 1000  950
    ##  [1849]  920  945  827  733  802  917  800  911  948  847  952 1018 1005  859
    ##  [1863]  941 1023  815  959  949 1011 1005  932 1004  938  851  903  937  946
    ##  [1877]  906 1014  954  959 1036  946 1013 1204  901 1042 1043  848  951 1016
    ##  [1891]  917 1050 1036  910 1004 1012 1059 1035 1038  905 1000 1014 1046  853
    ##  [1905] 1042 1106 1024 1034 1049 1038 1056  905  946  959  941 1031  958 1057
    ##  [1919] 1236 1109 1008 1114 1107 1019 1102 1137 1146 1024 1038  940 1025 1127
    ##  [1933] 1043  904  907 1301 1126 1128  953 1137 1053 1110 1011 1022  949 1048
    ##  [1947]  912 1010  934 1035 1050 1040 1020 1120 1007 1155 1153 1311 1138 1134
    ##  [1961] 1046 1028 1116 1022 1102  957 1007  938  938 1113 1114 1150  939 1154
    ##  [1975] 1040 1319 1115 1147 1149 1126 1126 1007 1206 1049 1120 1136 1100 1057
    ##  [1989] 1135 1144 1157 1123 1107 1137 1223 1111 1155 1124 1011 1200 1235 1216
    ##  [2003] 1230 1014 1031 1111 1039 1108 1244 1252 1103 1214 1421 1024 1242 1255
    ##  [2017] 1258 1011 1106 1504 1235 1128 1108 1210 1238 1207 1421 1157 1140 1140
    ##  [2031] 1036 1048 1100 1446 1221 1246 1153 1307 1112 1300 1106 1245 1107 1232
    ##  [2045] 1051 1142 1111 1130 1246 1120 1320 1312 1219 1317 1254 1258 1320 1215
    ##  [2059] 1213 1237 1150 1114 1139 1212 1337 1152 1144 1340 1207 1144 1334 1303
    ##  [2073] 1207 1312 1210 1521 1312 1323 1257 1229 1342 1154 1259 1243 1358 1200
    ##  [2087] 1223 1418 1350 1253 1343 1348 1157 1346 1206 1344 1407 1208 1352 1158
    ##  [2101] 1307 1425 1420 1355 1348 1325 1603 1407 1422 1431 1330 1330 1357 1500
    ##  [2115] 1316 1314 1323 1328 1502 1455 1448 1251 1506 1353 1251 1412 1446 1327
    ##  [2129] 1446 1248 1429 1442 1317 1441 1502 1505 1522 1328 1531 1354 1355 1510
    ##  [2143] 1400 1350 1527 1319 1439 1347 1451 1534 1353 1647 1332 1351 1421 1503
    ##  [2157] 1416 1534 1327 1550 1604 1347 1343 1437 1550 1600 1554 1504 1346 1455
    ##  [2171] 1510 1423 1553 1413 1347 1527 1602 1502 1430 1513 1601 1536 1617 1425
    ##  [2185] 1511 1358 1502 1407 1615 1633 1547 1502 1511 1612 1539 1556 1358 1510
    ##  [2199] 1533 1450 1543 1609 1557 1648 1650 1645 1637 1600 1641 1443 1652 1705
    ##  [2213] 1706 1821 1631 1506 1450 1505 1704 1838 1550 1718 1456 1640 1659 1641
    ##  [2227] 1522 1715 1648 1540 1551 1546 1727 1634 1516 2006 1611 1638 1711 1724
    ##  [2241] 1613 1539 1741 1735 1650 1754 1623 1731 1627 1632 1727 1741 1704 1542
    ##  [2255] 1726 1636 1642 1626 1558 1631 1550 1542 1558 1553 1803 1702 1636 1754
    ##  [2269] 1754 1616 1759 1656 1836 1712 1811 1801 1603 1621 1706 1648 1614 1730
    ##  [2283] 1757 1701 1832 1711 1827 1803 1726 1846 1742 1653 1630 1826 1813 1736
    ##  [2297] 1649 1623 1847 1839 1722 1724 1710 1855 1640 1821 1658 1850 1725 1801
    ##  [2311] 1802 1728 1736 1734 1857 1657 1846 1834 1902 1713 1859 1845 1706 1716
    ##  [2325] 1820 1748 1851 1716 1658 1845 2035 1804 1725 1710 1828 1837 1659 1817
    ##  [2339] 1856 1915 1934 1759 1653 1824 1820 1739 1824 1719 1823 1829 1800 1917
    ##  [2353] 1855 1904 1816 1926 1809 1824 1735 1915 1733 1925 1913 2001 1738 1926
    ##  [2367] 1837 1900 1851 1811 1739 1853 1922 1824 2004 1756 2005 1920 1908 1817
    ##  [2381] 1832 1809 1829 1825 1859 1806 1958 2001 1953 1746 1812 1947 1833 1924
    ##  [2395] 2016 1843 1917 1805 1857 1923 1952 1933 1830 1817 2019 1849 1954 1827
    ##  [2409] 1923 2141 1947 2028 2015 1904 2138 2041 1825 1805 2017 1805 1914 2028
    ##  [2423] 1959 1854 2017 1951 1803 2024 2037 2004 2017 2019 2013 1914 2030 2024
    ##  [2437] 1855 1836 1900 2003 1912 2010 2024 2036 1847 1837 2043 1955 1902 1936
    ##  [2451] 1953 2038 1950 1856 2034 1958 1858 1908 2043 2045 2014 2056 2110 1913
    ##  [2465] 2034 2108 1911 2240 2116 1934 1937 2023 2006 2004 2113 1935 1926 2102
    ##  [2479] 2036 1911 2108 1937 2027 1932 1959 2015 2127 2108 2027 1940 2121 2108
    ##  [2493] 1942 2052 2056 1951 2131 2112 2024 2048 2045 2033 1941 2121 2141 2152
    ##  [2507] 2019 2040 2052 2056 2013 2135 2102 2143 2149 2023 2035 2334 2130 2102
    ##  [2521] 2008 2204 2037 2148 2208 2121 2014 2002 2057 1959 2149 2131 2009 2200
    ##  [2535] 2154 2233 2109 2027 2327 2048 2223 2139 2125 2145 2021 2208 2207 2212
    ##  [2549] 2030 2104 2232 2050 2219 2158 2221 2103 2248 2036 2208 2228 2148   19
    ##  [2563] 2220 2050 2131 2207 2100 2238 2136 2121 2039 2200 2246   33 2249 2300
    ##  [2577] 2314 2241 2228 2135 2256 2125 2234 2252 2304 2232 2229 2302 2126 2203
    ##  [2591] 2215 2107 2101 2120 2302 2116 2308 2155 2258 2339 2129 2314 2116 2250
    ##  [2605] 2135 2116 2206 2303 2247 2158 2209 2308 2231 2333 2303 2120 2131 2139
    ##  [2619] 2235 2328 2133 2345 2311 2351 2226 2255 2339 2355 2337 2205 2152 2325
    ##  [2633] 2340 2340 2204 2249 2344 2207 2239 2353   48 2202 2236 2230 2209 2327
    ##  [2647] 2323 2225 2355 2240 2249   28 2238    4   27 2240   49 2225 2239 2222
    ##  [2661]  204   20 2326 2233 2232   29 2358   31   41  230 2346   50 2303   52
    ##  [2675] 2306 2259 2327 2346  103  302 2345 2350   26   45    9 2359   30   31
    ##  [2689]   18  434   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA  505  201
    ##  [2703]  631  813  841  851  833  730  846  824  848  745  851  706  849  816
    ##  [2717]  645  711  846  902  651  752  821  732  718  716  915  703  733  805
    ##  [2731]  904  916  729  759  846  915 1039  856  717  737 1051  838  904  807
    ##  [2745]  851  806  911  825  825 1004  818  835 1124  947  842  814  852  717
    ##  [2759]  805  751  934  929  940  927  930  911  754  859  916  854  854  748
    ##  [2773]  929  800  842  801  932  933 1013  807  919  926  955  857 1006  812
    ##  [2787]  941  956  934  859  901  844  937 1033  956  957  841 1035  914 1009
    ##  [2801] 1022 1021  905 1007 1013 1043  855 1102 1001 1030 1201 1029 1015 1031
    ##  [2815]  951 1025 1024  946  854  901 1030 1030 1051 1033  904 1044 1057  907
    ##  [2829] 1008 1109 1106  940  944 1219  918  900 1058 1030  956 1057 1109 1048
    ##  [2843] 1007  909 1112 1120  902 1055 1000 1002 1126 1027  952 1019 1016 1122
    ##  [2857] 1105 1110 1122  951 1029 1116 1004  956  925 1013 1335 1023 1000 1111
    ##  [2871]  938 1008 1042 1103 1305 1004 1119  946 1020 1034  954 1412 1128 1113
    ##  [2885] 1029 1034 1012 1115 1130  948 1059 1134 1107 1102  939 1001 1044  942
    ##  [2899] 1153 1343 1032 1109 1037 1001 1000 1108 1036 1040 1022 1143 1022 1122
    ##  [2913] 1150 1119 1123 1215 1217 1151 1210 1240 1215 1108 1157 1516 1224 1102
    ##  [2927] 1200 1120 1116 1021 1047 1027 1227 1234 1214 1231 1400 1228 1200 1032
    ##  [2941] 1110 1221 1250 1114 1156 1025 1039 1227 1406 1228 1134 1106 1233 1052
    ##  [2955] 1150 1145 1056 1053 1115 1107 1144 1233 1240 1114 1102 1114 1321 1141
    ##  [2969] 1219 1259 1238 1254 1216 1205 1259 1229 1232 1159 1139 1318 1211 1121
    ##  [2983] 1234 1159 1207 1320 1119 1212 1335 1155 1252 1305 1240 1342 1133 1343
    ##  [2997] 1324 1238 1327 1155 1154 1237 1150 1333 1349 1216 1341 1257 1402 1349
    ##  [3011] 1354 1350 1203 1201 1414 1208 1346 1322 1343 1328 1349 1301 1414 1229
    ##  [3025] 1211 1258 1307 1310 1215 1332 1350 1550 1256 1436 1415 1316 1304 1323
    ##  [3039] 1329 1427 1413 1416 1423 1559 1255 1434 1429 1444 1404 1312 1254 1316
    ##  [3053] 1342 1249 1302 1319 1436 1451 1346 1323 1446 1447 1431 1523 1332 1504
    ##  [3067] 1500 1435 1538 1334 1405 1454 1457 1528 1332 1533 1353 1524 1337 1526
    ##  [3081] 1325 1507 1338 1351 1333 1546 1542 1443 1432 1407 1544 1434 1511 1545
    ##  [3095] 1511 1528 1417 1410 1357 1527 1356 1556 1448 1535 1531 1442 1450 1452
    ##  [3109] 1423 1546 1522 1410 1500 1518 1604 1423 1442 1556 1453 1621 1504 1449
    ##  [3123] 1629 1550 1527 1606 1621 1645 1615 1632 1617 1438 1633 1536 1932 1641
    ##  [3137] 1650 1525 1530 1458 1552 1644 1501 1701 1657 1621 1653 1629 1507 1542
    ##  [3151] 1631 1712 1845 1655 1722 1617 1532 1613 1535 1732 1640 1629 1536 1726
    ##  [3165] 1721 1717 1546 1628 1530 1757 1731 1745 1537 1647 1652 1703 1657 1613
    ##  [3179] 1616 1607 1807 1746 1635 1636 1656 1637 1809 1814 1619 1746 1626 1553
    ##  [3193] 1611 1548 1814 1745 1554 1635 1824 1651 1646 1612 1755 1633 1722 1819
    ##  [3207] 1806 1713 1650 1731 1629 1722 1629 1827 1637 1828 1656 1656 1715 1820
    ##  [3221] 1600 1824 1700 1645 1805 1804 1816 1712 1814 1650 1740 1820 1648 1915
    ##  [3235] 1640 1745 1759 1641 1834 1849 1732 1745 1846 1644 1855 1850 1736 1828
    ##  [3249] 1802 1909 1822 1836 1840 1736 1719 1652 1903 1752 1751 1755 1711 1743
    ##  [3263] 1757 1756 2100 1859 1851 1858 1831 1741 1709 1914 1838 1731 1715 1924
    ##  [3277] 1816 1740 1919 1814 1825 1830 1916 1813 1755 1853 1714 1809 1759 1820
    ##  [3291] 1830 1853 1937 1925 1902 1815 1907 1918 1900 1736 1937 1844 1811 1940
    ##  [3305] 1933 1954 1831 1946 1840 1836 1942 1926 1857 1929 1809 1748 1923 1749
    ##  [3319] 1938 1751 1908 1857 2019 1833 1925 2127 1801 2111 1921 2004 1817 1952
    ##  [3333] 1955 1959 1800 1912 1823 2001 1948 1904 2007 2003 1836 2017 1945 2003
    ##  [3347] 2010 1849 1913 2153 2010 1853 1849 1820 2016 2202 1841 1926 2013 1948
    ##  [3361] 2014 2016 1835 1923 1905 1905 2000 1837 1835 1839 2027 2037 1924 1935
    ##  [3375] 2032 2025 1930 2050 2031 2045 2030 2054 1904 2044 1914 1856 2117 2102
    ##  [3389] 2127 2037 1910 2036 2016 2018 2057 1920 1947 1929 2013 2114 1915 2101
    ##  [3403] 2103 2042 1936 1939 2016 2140 2126 1937 2148 2057 1938 1943 2123 2019
    ##  [3417] 2053 2111 1949 2113 1954 1952 2026 1952 2058 1925 2119 1937 2148 2129
    ##  [3431] 2129 2029 2210 2103 1940 2136 2004 2011 2000 2013 2024 2140 2136 2052
    ##  [3445] 2012 2039 2157 2351 2133 2029 2035 2021 2139 2010 2129 2126 2216 2105
    ##  [3459] 2200 2018 2147 2212 2211 2022 2051 2025 2108 2128 2204 2015 2033 2124
    ##  [3473] 2146 2228 2127 2043 2358 2135 2224 2211 2219 2052 2112 2051 2213 2046
    ##  [3487] 2234 2059 2227 2135 2128 2225 2230 2146 2158 2208 2126 2255 2203 2227
    ##  [3501] 2120 2054 2249 2151 2059 2226 2237 2242 2250 2114 2150 2148 2231 2111
    ##  [3515] 2128 2118 2120 2228 2205 2211 2314 2320 2311 2212 2147 2250 2116 2257
    ##  [3529] 2139 2129 2317 2254 2346 2237 2153 2154 2152 2248 2313 2316 2131 2318
    ##  [3543] 2149 2151 2134 2329 2326 2334 2146 2326 2240 2359 2342 2346 2305 2332
    ##  [3557] 2206 2258 2237 2217   20 2334    2 2349 2224 2154 2215 2304 2157    4
    ##  [3571] 2228 2221 2231   11 2218 2332 2312 2244 2337 2218   10    5 2346  206
    ##  [3585] 2241 2314   31   28  209 2312 2247   32   46 2314 2314 2309    7 2311
    ##  [3599]   32  116  257    9 2357   12    9   17   56  429  436   NA   NA   NA
    ##  [3613]   NA   NA   NA  503  341  640  821  829  831  903  739  824  818  904
    ##  [3627]  845  858  846  840  840  900  843  644 1035  909  728  724  857  917
    ##  [3641]  857  854  703  714  902  828  823  720  909  717  737  809 1054  835
    ##  [3655]  801  819 1127  916  945  815  946 1003  750  757  738 1009  803  829
    ##  [3669]  955  949  904 1015  918 1010 1002 1056  942  934  821  841 1002 1014
    ##  [3683]  913 1013  931 1003  841 1024  941 1017  900 1028 1200 1201  835 1000
    ##  [3697]  824 1011 1110  930  941 1127 1110  856 1019 1101 1037 1122 1046 1039
    ##  [3711] 1220  902 1141 1030 1101  932 1101  903  943 1048 1101  944 1039 1106
    ##  [3725]  944  857 1012 1119 1036  915 1025  919 1106  957  914 1037 1249 1039
    ##  [3739] 1005  949  956  927 1114 1101 1139  958 1037  953  956 1106  916 1114
    ##  [3753]  929 1019  948 1030 1132 1317  949 1047  946 1139 1005  956 1050 1009
    ##  [3767]  939 1057 1031 1200 1104 1012 1156  959 1322 1150 1144 1012 1135 1100
    ##  [3781] 1126 1110 1132 1206 1248 1043 1108 1125 1124 1133 1225 1225 1519 1208
    ##  [3795] 1253 1101 1122 1144 1118 1050 1205 1035 1218 1345 1449 1105 1056 1032
    ##  [3809] 1030 1301 1054 1210 1213 1022 1229 1137 1100 1420 1043 1105 1229 1250
    ##  [3823] 1255 1116 1243 1057 1245 1225 1135 1318 1242 1320 1254 1126 1108 1246
    ##  [3837] 1216 1135 1112 1327 1308 1200 1500 1252 1336 1153 1351 1250 1118 1129
    ##  [3851] 1107 1356 1150 1356 1131 1341 1329 1316 1341 1149 1416 1359 1443 1226
    ##  [3865] 1405 1157 1404 1342 1214 1326 1411 1400 1258 1444 1410 1410 1321 1222
    ##  [3879] 1434 1407 1436 1315 1320 1452 1426 1325 1454 1340 1448 1329 1249 1442
    ##  [3893] 1427 1455 1401 1441 1307 1417 1456 1319 1628 1339 1241 1443 1250 1300
    ##  [3907] 1314 1329 1517 1519 1517 1320 1355 1329 1533 1540 1530 1333 1338 1402
    ##  [3921] 1447 1357 1447 1520 1405 1444 1430 1339 1549 1537 1402 1540 1401 1404
    ##  [3935] 1440 1551 1545 1524 1739 1605 1404 1426 1415 1523 1452 1502 1621 1610
    ##  [3949] 1606 1439 1450 1645 1509 1640 1358 1801 1613 1640 1421 1623 1429 1420
    ##  [3963] 1634 1618 1850 1554 1640 1644 1704 1645 1635 1707 1655 1530 1646 1617
    ##  [3977] 1704 1649 1707 1658 1616 1449 1707 1657 1623 1715 1650 1619 1623 1732
    ##  [3991] 1552 1541 1648 1524 1629 1605 1747 1738 1727 1730 1637 1536 1623 1548
    ##  [4005] 1636 1649 1624 1642 1548 1751 1639 1737 1637 1649 1630 1630 1613 1747
    ##  [4019] 1729 1636 1639 1809 1634 1818 1717 1823 1803 1817 1627 1815 1642 1759
    ##  [4033] 1636 1822 1831 1623 1637 1739 1758 1646 1850 1642 1703 1730 1814 1737
    ##  [4047] 1858 1713 1759 1837 1643 1833 1819 1854 1647 1706 1644 1731 1908 1854
    ##  [4061] 1820 1850 1632 1909 1916 1705 1713 1733 1654 2039 1758 1805 1908 1743
    ##  [4075] 1833 1822 1751 1911 1912 1853 1727 1918 1921 1825 1913 1755 2047 1912
    ##  [4089] 1900 1853 1913 1656 1744 1902 1743 1800 1916 1806 1929 1723 1742 1923
    ##  [4103] 1831 1920 1729 1714 1940 1749 2010 1832 1823 1758 1908 1819 1928 1816
    ##  [4117] 1949 1846 1815 1937 1828 1813 1811 1937 1954 2004 2002 1835 1946 1837
    ##  [4131] 2016 1759 1950 1938 1932 2010 1749 1935 2127 2028 1933 1805 1855 2050
    ##  [4145] 2019 1959 1933 1904 2010 2017 1816 2139 2019 2013 1844 2022 1852 2040
    ##  [4159] 2028 1912 1947 2002 1839 1948 2015 1934 2020 1817 2017 2036 2024 2103
    ##  [4173] 2045 2037 2041 1842 2044 2050 1921 2037 2041 2050 1859 1943 2028 2101
    ##  [4187] 1908 2053 2117 1942 1911 2114 2118 2021 1916 1933 2100 2152 2119 2151
    ##  [4201] 1916 1949 2001 1914 2012 1930 2154 2026 1937 2001 2126 2128 2000 2129
    ##  [4215] 2019 2141 1952 1941 2147 2159 2046 2153 2044 2059 2150 2135 2032 2125
    ##  [4229] 2233 2218 2205 2144 2158 2253 2100 2212 2221 2149 2107 2228 2227 2036
    ##  [4243] 2205 2105 2348 2051 2035 2217 2038 2249 2206 2139 2142 2232 2159 2154
    ##  [4257] 2207 2246 2304 2046 2118 2216 2245 2059 2158 2227 2056 2109 2133 2322
    ##  [4271] 2253 2257 2303 2237 2138 2330 2116 2310   50 2311 2308 2108 2309 2329
    ##  [4285] 2122 2144 2359 2302 2317 2332 2349 2339 2146 2245 2342    4 2319 2252
    ##  [4299] 2308  114 2347 2220   56 2356 2400    4 2242 2225 2225   16 2354  207
    ##  [4313] 2245 2259   41 2257  100 2253 2333 2343  128  113 2345 2339  352    9
    ##  [4327]   30   19  202  106  425  432   NA   NA   NA  451  718  827  855  930
    ##  [4341]  830  855  905  849  910  845  906  944  911  733  837  916  908  839
    ##  [4355]  846  816 1053  807  826  810  936  941  806 1154  947  818  909  926
    ##  [4369] 1002 1156  820  936  940  836  933  810 1025  947  957 1025  940 1012
    ##  [4383]  900 1001  958 1018  836  816  936 1001 1001  906 1057 1013 1018  959
    ##  [4397] 1037  858 1207 1023  852 1024  832 1042 1040 1023 1053 1053  856 1056
    ##  [4411] 1101 1039  927 1119  930 1224 1141 1057 1113  850  937 1007  949 1119
    ##  [4425] 1102 1033 1116 1110 1108 1105 1119  946 1028 1136 1023 1256  914 1110
    ##  [4439] 1015  923 1044 1109 1053  947 1021  951 1102 1038 1015  917 1140 1110
    ##  [4453] 1040  940 1123  921 1128  935  929  946 1000 1320 1058 1314 1135 1122
    ##  [4467] 1133 1055 1040 1003 1101  953 1009 1159  956 1151 1005 1053 1147 1013
    ##  [4481] 1041 1034 1044 1159 1047 1402 1209 1144 1133 1210 1227 1058 1102 1133
    ##  [4495] 1116 1228 1234 1236 1313 1141 1031 1411 1109 1225 1056 1218 1053 1217
    ##  [4509] 1041 1241 1128 1100 1240 1133 1237 1105 1032 1311 1118 1235 1230 1300
    ##  [4523] 1102 1238 1227 1102 1052 1122 1259 1233 1308 1331 1250 1143 1215 1244
    ##  [4537] 1320 1318 1325 1322 1111 1118 1117 1301 1132 1222 1208 1236 1321 1341
    ##  [4551] 1148 1201 1558 1330 1328 1205 1252 1218 1335 1330 1154 1354 1443 1221
    ##  [4565] 1327 1240 1309 1145 1406 1229 1356 1353 1212 1353 1404 1345 1543 1229
    ##  [4579] 1203 1359 1255 1439 1234 1301 1310 1253 1224 1254 1445 1427 1330 1331
    ##  [4593] 1600 1255 1421 1253 1338 1435 1336 1438 1302 1440 1331 1449 1253 1244
    ##  [4607] 1510 1436 1327 1454 1516 1439 1327 1507 1500 1316 1643 1307 1503 1502
    ##  [4621] 1309 1503 1502 1437 1514 1515 1508 1430 1308 1310 1518 1331 1545 1331
    ##  [4635] 1409 1322 1449 1406 1506 1511 1409 1527 1342 1422 1427 1530 1334 1530
    ##  [4649] 1548 1527 1444 1551 1537 1556 1440 1541 1503 1336 1345 1605 1508 1610
    ##  [4663] 1349 1537 1426 1422 1505 1356 1609 1536 1510 1439 1452 1636 1513 1507
    ##  [4677] 1600 1414 1436 1432 1501 1628 1605 1616 1634 1620 1634 1444 1651 1453
    ##  [4691] 1433 1655 1506 1816 1704 1700 1654 1608 1647 1539 1504 1636 1502 1729
    ##  [4705] 1723 1604 1927 1705 1505 1633 1536 1707 1641 1648 1733 1557 1701 1625
    ##  [4719] 1538 1718 1733 1727 1539 1726 1624 1750 1651 1734 1555 1632 1619 1629
    ##  [4733] 1552 1756 1608 1655 1710 1802 1755 1646 1734 1703 1552 1641 1627 1647
    ##  [4747] 1750 1637 1648 1703 1853 1645 1713 1551 1633 1749 1606 1555 1637 1623
    ##  [4761] 1617 1655 1829 1807 1821 1620 1834 1648 1632 1729 1825 1709 1833 1825
    ##  [4775] 1708 1809 1644 1644 1814 1628 1722 1811 1700 1827 1645 1811 1804 1848
    ##  [4789] 1718 1629 1836 1701 1727 1656 1653 1730 1937 1825 1802 1844 1726 1900
    ##  [4803] 1839 1718 1848 1911 1805 1711 1911 1814 1846 1917 1851 1842 1637 1903
    ##  [4817] 1654 2048 1805 2047 1722 1815 1849 1733 1859 1814 1736 1836 1907 1836
    ##  [4831] 1918 1714 1914 1759 1805 1927 1946 1929 1719 1745 1736 1916 1828 1717
    ##  [4845] 1906 1813 1757 1930 1936 1906 1749 1756 1746 1726 1949 1722 1823 1720
    ##  [4859] 1958 1936 1747 1930 1947 1903 1807 1846 1901 1754 1846 1927 1945 1828
    ##  [4873] 1954 1935 1952 1859 1850 2000 1823 1950 1744 1845 1959 1737 1955 2021
    ##  [4887] 1923 1814 2134 1812 2010 2025 1953 2019 1943 1928 1811 1942 1807 2001
    ##  [4901] 1835 2010 1803 1908 1947 1912 2017 1902 1953 2013 2022 1906 2041 2036
    ##  [4915] 2037 1912 1901 2018 1946 1912 2029 1847 1835 2005 1938 2037 2020 2055
    ##  [4929] 2039 1905 2211 2100 2049 1957 1926 1928 1923 2002 2031 2116 2041 1937
    ##  [4943] 2125 2053 2054 2031 1919 2115 1911 1913 2113 1858 2131 2038 2048 2101
    ##  [4957] 1936 1906 1945 2017 1923 2121 1955 2048 2128 2019 1945 2034 2112 1947
    ##  [4971] 1928 2118 2128 2045 2143 2146 2124 2121 2015 2028 2117 2019 2128 2013
    ##  [4985] 1955 2210 2045 2201 2055 2030 2141 2210 2040 1942 2008 2011 2219 2154
    ##  [4999] 2100 2115 2017 2118 1953 2147 2205 2040 2036 2019 2144 2204 2059 2205
    ##  [5013] 2023   22 2126 2223 2207 2014 2020 2056 2219 2154 2015 2203 2133 2220
    ##  [5027] 2013 2111 2128 2116 2205 2046 2204 2014 2046 2202 2105 2033 2153 2237
    ##  [5041] 2054 2218 2221 2139 2231 2115 2233 2243 2241 2204 2249 2206 2210 2159
    ##  [5055] 2318 2243   34 2233 2244 2052 2237 2044 2247 2159 2252 2057 2121 2058
    ##  [5069] 2126 2228 2305 2200 2208 2306 2109 2234 2229 2247 2119 2203 2143 2131
    ##  [5083] 2243 2115 2224 2113 2140 2325 2206 2315 2309 2158 2244 2243 2310 2331
    ##  [5097] 2324 2111 2323 2307 2253 2330 2131 2335 2151 2322 2258 2144 2150 2337
    ##  [5111] 2358 2241 2339 2142 2329 2200 2229 2206 2241   18  143 2203 2204 2243
    ##  [5125]    2    6 2254 2212 2208 2232 2241 2224 2234 2342 2301   22 2311 2325
    ##  [5139] 2237  214    4   46 2237   50 2246 2254 2245  104 2302 2250  104 2256
    ##  [5153]  114   54  130  304  107 2352   12   10  125   14   12   25  441  433
    ##  [5167]   NA  531  637  758  827 1020  822  646  843  708  741  800  850  827
    ##  [5181]  808  746  819  711  908  700  710  752  704  913  712  711  854  718
    ##  [5195]  757  809  908  718  741 1047  658  820  735  812  748  727  828  815
    ##  [5209]  908  902  920  828  707  855  809  802  844  811  908  757  928  831
    ##  [5223]  854  743 1125  936  931  918  925  753  919  845  758  936  923  833
    ##  [5237]  752  913  749  945 1021  934  859  915  754 1017  926  955  901  854
    ##  [5251]  947  945  815 1011  758  912  959  816 1007  951  936  944  956  845
    ##  [5265] 1006  854  920 1156  846 1048  933 1038  959  845  851 1025  912 1017
    ##  [5279] 1021  835 1016  959 1033 1008 1010  854 1100 1039 1029 1057 1017 1017
    ##  [5293]  923 1041  910  921 1230 1101 1049 1034  849  951  849 1041  907  907
    ##  [5307] 1119 1014 1018 1033 1047 1055 1039 1100 1014 1315 1003 1057 1016  939
    ##  [5321]  946 1029  926 1118  909  955  942 1112 1037  915  907 1104 1126 1045
    ##  [5335]  954  955  924  937 1000 1102 1014  954 1138  954  956 1109 1007 1000
    ##  [5349] 1006 1107 1057  931 1011 1029 1110 1315  940 1116  935 1125  936 1024
    ##  [5363] 1143 1145 1110 1155  932 1028  955  946 1035 1347 1141 1027 1041 1016
    ##  [5377] 1130 1002 1052 1058 1150 1105 1209 1144 1156 1105 1204 1026 1102 1159
    ##  [5391] 1118 1115 1219 1038 1029 1047 1206 1203 1105 1127 1209 1128 1128 1407
    ##  [5405] 1146 1239 1051 1047 1121 1019 1031 1108 1200 1047 1140 1043 1238 1149
    ##  [5419] 1222 1213 1158 1211 1235 1103 1042 1046 1153 1106 1211 1106 1054 1053
    ##  [5433] 1249 1202 1313 1103 1302 1107 1303 1225 1201 1221 1206 1444 1158 1242
    ##  [5447] 1251 1119 1119 1254 1457 1331 1308 1325 1123 1202 1131 1315 1231 1311
    ##  [5461] 1146 1209 1210 1206 1224 1335 1234 1248 1240 1329 1200 1324 1312 1234
    ##  [5475] 1620 1155 1213 1345 1350 1404 1347 1323 1226 1415 1225 1340 1219 1232
    ##  [5489] 1206 1257 1215 1210 1237 1251 1400 1433 1304 1339 1332 1355 1304 1426
    ##  [5503] 1237 1330 1341 1258 1357 1359 1405 1339 1405 1248 1437 1611 1341 1257
    ##  [5517] 1347 1426 1423 1313 1617 1423 1459 1532 1302 1457 1356 1255 1421 1245
    ##  [5531] 1341 1402 1259 1425 1303 1449 1458 1437 1436 1450 1352 1508 1316 1337
    ##  [5545] 1314 1301 1315 1332 1315 1407 1509 1352 1519 1403 1527 1406 1531 1330
    ##  [5559] 1418 1531 1533 1553 1444 1553 1433 1538 1536 1338 1548 1447 1535 1440
    ##  [5573] 1525 1447 1405 1418 1503 1339 1410 1400 1538 1540 1537 1355 1553 1414
    ##  [5587] 1609 1553 1401 1520 1345 1531 1447 1454 1518 1600 1446 1502 1608 1621
    ##  [5601] 1446 1805 1604 1631 1441 1520 1419 1610 1622 1543 1622 1658 1634 1438
    ##  [5615] 1704 1925 1648 1629 1638 1625 1539 1702 1521 1538 1517 1651 1625 1503
    ##  [5629] 1619 1501 1628 1513 1654 1544 1614 1505 1614 1517 1627 1530 1711 1626
    ##  [5643] 1733 1749 1541 1525 1700 1734 1634 1630 1620 1645 1631 1656 1737 1742
    ##  [5657] 1542 1619 1643 1553 1740 1744 1659 1620 1732 1714 1650 1548 1640 1839
    ##  [5671] 1640 1631 1718 1651 1600 1811 1823 1548 1739 1822 1751 1637 1623 1616
    ##  [5685] 1649 1757 1714 1621 1752 1703 1610 1629 1814 1747 1634 1715 1734 1807
    ##  [5699] 1813 1702 1749 1622 1802 1656 1808 1700 1645 1757 1839 1720 1714 1643
    ##  [5713] 1710 1719 1813 1640 1948 1857 1730 1835 1825 1850 1645 1756 1721 1748
    ##  [5727] 1714 1724 1925 1737 1758 1757 1821 1830 1847 1657 1859 1828 1720 1734
    ##  [5741] 1801 1646 1803 1730 1706 1823 1854 1833 1726 2040 1938 1932 1854 1721
    ##  [5755] 1757 1750 1908 1849 1857 1842 1909 1721 1753 1852 1737 1752 1832 1818
    ##  [5769] 1729 1858 1807 1729 1850 1937 1825 1728 1933 1828 1755 1716 1914 1714
    ##  [5783] 1759 1900 1729 1934 1941 1844 1751 1842 1851 1725 1912 1753 2159 2011
    ##  [5797] 1937 1948 1838 1810 1952 1838 1840 1846 1932 1937 1811 1916 1940 1942
    ##  [5811] 1829 1926 1815 1926 1841 1944 1914 1839 1935 1839 2003 2213 1821 2005
    ##  [5825] 2000 2017 1838 1826 1949 1816 1948 1948 1845 2014 1804 1800 1956 2012
    ##  [5839] 1859 1903 2019 2027 2004 1836 1907 1921 1944 2028 2052 1840 2054 1912
    ##  [5853] 1905 1852 1849 2012 2042 1859 2000 2019 2021 2029 2042 2056 2033 1936
    ##  [5867] 2056 2038 1838 2117 1843 1900 1900 2026 2009 1917 2020 1945 2118 2109
    ##  [5881] 2036 2057 2107 1908 1906 1900 2108 2057 2039 1957 2037 2046 2033 2137
    ##  [5895] 2116 1933 1938 1953 1943 1951 2056 2035 2111 1918 1911 1921 2034 1948
    ##  [5909] 2025 2032 1938 1945 2035 2010 1958 1949 2007 2024 2136 2130 1944 2042
    ##  [5923] 2138 2143 2139 2117 2036 2045 2124 2155 2154 2006 1944 1936 2018 2134
    ##  [5937] 2049 2028 2216 2007 2045 2141 1957 2002 2018 2029 2035 2026 2123 2214
    ##  [5951] 2008 2130 2219 2025 2107 2133 2035 2217 2059 2033 2048 2209 2203    7
    ##  [5965] 2158 2130 2042 2052 2222 2121 2216 2212 2041 2247 2223 2235 2222 2155
    ##  [5979] 2229 2302 2039 2201 2125 2114 2216 2219 2227 2152 2045 2108 2203 2146
    ##  [5993] 2223 2112 2041 2159 2050 2037 2223 2045 2144 2241 2308 2118 2109 2100
    ##  [6007] 2231 2300 2220 2106 2111 2256 2104 2129 2205 2123 2239 2310 2117 2306
    ##  [6021] 2300 2304 2150 2119 2246 2153 2332 2250 2304 2106 2209 2238 2314 2230
    ##  [6035] 2351 2124 2134 2200 2203  134 2352 2334 2138    7 2247 2215 2332 2142
    ##  [6049] 2341 2204 2233 2335 2237 2226 2205 2226 2242 2215 2201 2204 2350 2323
    ##  [6063] 2352 2301 2359 2219 2220 2229 2212   19 2231  201 2229 2338   27   19
    ##  [6077] 2253   36 2249 2308 2256   33 2247   18   59    4  308 2333 2342 2344
    ##  [6091]    6    2  155    3   13    3  506   NA   NA   NA  625  837  826 1025
    ##  [6105]  853  850  824  650  819  844  703  804  741  850  701  728  846  732
    ##  [6119]  713  905  729  850  850  932  801  741  725  728  723  835  903 1047
    ##  [6133]  852  733  801  901 1040  859  821  850  933  759  844  911  824  740
    ##  [6147]  836  842  912  840  747  810  819  912  932  730  857 1128  936  947
    ##  [6161]  800  931  855 1000  818  807  958  923  912  939  905  955 1021  831
    ##  [6175]  929  921  757  933  815  949 1022 1008  806 1011  948  929  954  935
    ##  [6189]  810  836 1003 1017  946  932  946 1027  847 1028  837  844 1007 1018
    ##  [6203] 1029 1045  916  844 1005 1101  929 1037 1052 1031 1027 1026  841 1036
    ##  [6217] 1034 1004 1056 1048  921  912 1213  920  914  905 1058 1033 1229  943
    ##  [6231] 1102  901 1049  852 1029  858  954  858 1021 1105  917 1112 1107 1116
    ##  [6245] 1043  938  911  956 1026 1029 1029 1118  958 1252  909  949 1055 1102
    ##  [6259] 1127 1103 1041 1025  930  957 1049 1253 1157 1007  926  932  922  939
    ##  [6273] 1031 1003  952 1112 1020 1007 1010 1058  940 1008 1141 1048 1047 1127
    ##  [6287] 1119 1141 1116  956 1318 1009 1141  941 1032 1205 1153 1120 1027  950
    ##  [6301] 1004 1401 1051 1042 1116 1023 1137 1222 1154 1006 1209 1215 1119 1042
    ##  [6315] 1144 1214 1006 1134 1022 1059 1000 1132 1113 1245 1110 1155 1113 1033
    ##  [6329] 1223 1504 1006 1143 1206 1315 1148 1432 1037 1049 1215 1212 1306 1125
    ##  [6343] 1043 1233 1046 1433 1222 1038 1026 1201 1204 1214 1241 1122 1159 1109
    ##  [6357] 1230 1105 1213 1237 1110 1118 1100 1226 1244 1229 1311 1251 1308 1312
    ##  [6371] 1231 1117 1235 1230 1110 1157 1124 1213 1215 1158 1326 1148 1244 1337
    ##  [6385] 1302 1339 1340 1124 1153 1144 1213 1337 1228 1344 1252 1343 1324 1147
    ##  [6399] 1141 1347 1235 1233 1210 1357 1352 1351 1153 1158 1155 1408 1359 1340
    ##  [6413] 1416 1522 1234 1332 1254 1201 1225 1205 1412 1353 1233 1251 1253 1521
    ##  [6427] 1309 1417 1247 1415 1431 1424 1315 1414 1307 1411 1340 1437 1607 1432
    ##  [6441] 1449 1435 1415 1314 1435 1353 1306 1304 1428 1402 1312 1449 1426 1351
    ##  [6455] 1419 1321 1259 1258 1301 1301 1451 1259 1308 1348 1338 1424 1451 1522
    ##  [6469] 1529 1458 1315 1305 1337 1533 1516 1422 1343 1359 1523 1531 1343 1335
    ##  [6483] 1521 1421 1353 1538 1558 1430 1601 1544 1525 1533 1353 1607 1432 1347
    ##  [6497] 1401 1421 1540 1354 1410 1459 1513 1359 1518 1607 1400 1426 1544 1505
    ##  [6511] 1352 1428 1418 1510 1622 1519 1425 1500 1512 1633 1635 1617 1600 1624
    ##  [6525] 1614 1640 1635 1652 1559 1525 1654 1641 1951 1653 1526 1701 1639 1531
    ##  [6539] 1651 1503 1650 1508 1556 1621 1637 1707 1754 1651 1513 1529 1629 1630
    ##  [6553] 1717 1510 1523 1608 1620 1531 1518 1628 1701 1518 1653 1728 1802 1753
    ##  [6567] 1701 1726 1537 1530 1717 1633 1554 1752 1608 1656 1625 1738 1705 1609
    ##  [6581] 1651 1738 1626 1541 1747 1550 1744 1800 1720 1931 1625 1646 1730 1643
    ##  [6595] 1819 1612 1643 1612 1827 1828 1618 1814 1741 1627 1607 1807 1741 1646
    ##  [6609] 1703 1642 1733 1757 1750 1758 1827 1652 1700 1819 1645 1822 1720 1811
    ##  [6623] 1706 1707 1843 1645 1712 1820 1644 1722 1711 1739 1916 1724 1830 1808
    ##  [6637] 1838 1719 1704 1652 1707 1753 1815 1755 1851 1953 1659 1653 1842 1812
    ##  [6651] 1846 1826 1759 1718 1656 1724 2029 1924 1820 1755 1723 2029 1744 1848
    ##  [6665] 1854 1906 1727 1709 1728 1834 1923 1718 1807 1934 1847 1858 1732 1927
    ##  [6679] 1914 1753 1742 1856 1722 1841 1924 2025 1745 1844 1744 1848 1708 1729
    ##  [6693] 1904 1718 1858 1849 1920 1729 1804 1859 2000 1859 1750 1951 2000 1941
    ##  [6707] 1854 1944 1914 1854 1842 1757 1826 1938 1847 1848 1840 1941 1749 1854
    ##  [6721] 1755 1805 2001 1916 1851 1805 1930 1801 2000 1959 2021 1756 1825 1821
    ##  [6735] 1942 2038 2140 1931 1956 2009 1859 1947 2036 1910 1949 2018 1808 2050
    ##  [6749] 2020 1929 1838 2047 1902 2024 2005 1818 2018 1919 1900 1830 2023 2041
    ##  [6763] 2043 2034 1856 2032 2008 2006 2050 2053 1843 1845 1900 2031 1915 2017
    ##  [6777] 2042 2020 2051 2108 1853 2034 2105 1951 1942 2110 1911 2054 2105 1909
    ##  [6791] 2117 2051 2048 2033 2107 1913 2053 2037 1911 1917 1948 1917 1947 1925
    ##  [6805] 2126 1913 2117 2139 1949 1936 2040 1930 1915 2021 1929 2038 2100 1946
    ##  [6819] 1948 1936 1945 2039 2126 2121 2058 2110 2137 1924 1958 2207 2046 2040
    ##  [6833] 2201 2149 1941 2139 2039 2226 2026 2017 2056 1950 2046 2058 2005 2142
    ##  [6847] 1940 2159 2203 2117 1954 2044 2326 2117 1957 2228 2001 2029 2047 2132
    ##  [6861] 2145 2223 2036 2158 2026 2301 2206 2119 2027 2045 2056 2240 2221 2058
    ##  [6875] 2244 2158 2218 2036 2026 2300 2120 2155 2203 2243 2206 2022 2121 2111
    ##  [6889] 2239 2057 2238 2241 2224 2244 2219 2059 2240 2100 2121 2140 2052 2229
    ##  [6903] 2045 2246 2105 2050 2327 2131 2104 2200 2148 2249 2105 2121 2117 2226
    ##  [6917] 2218 2236 2203 2252 2154 2140 2306 2114 2248 2301 2224 2337 2157 2056
    ##  [6931] 2237 2334 2323 2112 2153 2324 2258 2256 2338 2333 2202 2224 2127 2202
    ##  [6945] 2345 2131 2324 2131  109 2203 2342 2244 2338 2311 2142 2156 2317 2343
    ##  [6959] 2239 2204 2206 2235 2153 2225 2313 2200 2227   29 2239 2218 2229 2231
    ##  [6973]  154 2304  114 2355 2244   10 2231   13   44 2241 2303 2243 2309  246
    ##  [6987] 2336 2344 2349 2339  157   22   43  414  417   NA   NA   NA   NA  432
    ##  [7001]  432  647  837  818  823 1007  815  648  822  758  752  905  642  855
    ##  [7015]  950  828  756  739  652  814  728  704  725  806  722  906  812  851
    ##  [7029]  857  708  910  926  742 1040  741  720  911  804  838  832   NA  743
    ##  [7043]  937  826  718  848  758  816 1123  828  810  920  854  834  930  836
    ##  [7057]  847  728  827  811  924  936  911  922 1011  909  936  908  947 1004
    ##  [7071]  750 1032  755 1242  916  926  910  837  757  801 1031  950  905 1052
    ##  [7085]  938  919 1010  949  949  944 1022  834 1014  927 1005 1040  831  953
    ##  [7099]  955 1003 1011 1022 1043  859  853 1002 1027 1111  919 1026 1154  812
    ##  [7113] 1041 1031 1000 1046 1015 1105 1123  834 1031 1105 1025 1102  933  932
    ##  [7127] 1119 1217  852  903 1034  952 1056  848  922  944  926 1102 1047  925
    ##  [7141]  849 1014 1049 1117 1027 1032 1108 1134 1153 1008 1108 1049 1013 1154
    ##  [7155]  944  914  910 1045 1110  959  943 1104 1015 1311 1011 1014  939 1103
    ##  [7169]  951  939 1003  944 1004  957 1124 1123 1014 1120 1119 1258 1144 1059
    ##  [7183] 1302 1116 1016 1223 1034 1132 1206 1101  942 1020 1154 1034 1019  939
    ##  [7197] 1003 1016  950 1031 1331 1131 1120 1105 1049 1125 1107 1136 1126 1004
    ##  [7211] 1101 1056 1037 1208 1211 1239 1125 1144 1015 1016 1047 1048 1150 1114
    ##  [7225] 1202 1206 1001 1126 1230 1210 1211 1207 1202 1152 1405 1221 1114 1041
    ##  [7239] 1203 1226 1149 1232 1124 1212 1033 1019 1034 1233 1205 1241 1119 1103
    ##  [7253] 1407 1213 1231 1224 1207 1205 1123 1119 1052 1241 1116 1212 1240 1121
    ##  [7267] 1103 1140 1252 1230 1303 1200 1248 1315 1246 1052 1244 1242 1328 1227
    ##  [7281] 1120 1134 1126 1212 1314 1154 1149 1115 1323 1323 1249 1202 1211 1119
    ##  [7295] 1235 1216 1247 1411 1404 1420 1251 1232 1135 1353 1156 1345 1219 1409
    ##  [7309] 1200 1334 1155 1207 1420 1333 1210 1409 1333 1258 1511 1427 1207 1237
    ##  [7323] 1301 1235 1300 1356 1340 1244 1401 1351 1420 1530 1558 1312 1408 1414
    ##  [7337] 1255 1335 1506 1421 1325 1432 1309 1328 1434 1447 1440 1424 1242 1425
    ##  [7351] 1413 1430 1326 1446 1251 1355 1305 1316 1420 1414 1550 1252 1304 1250
    ##  [7365] 1432 1302 1257 1337 1346 1510 1504 1510 1300 1519 1336 1310 1451 1405
    ##  [7379] 1343 1400 1330 1450 1350 1521 1408 1438 1339 1531 1344 1432 1519 1602
    ##  [7393] 1342 1520 1548 1423 1539 1356 1346 1449 1348 1548 1542 1447 1456 1417
    ##  [7407] 1559 1431 1651 1507 1357 1615 1535 1358 1422 1458 1416 1512 1454 1435
    ##  [7421] 1627 1649 1618 1610 1528 1616 1708 1549 1656 1828 1645 2019 1701 1636
    ##  [7435] 1600 1746 1630 1534 1609 1702 1556 1457 1646 1506 1648 1509 1627 1541
    ##  [7449] 1451 1552 1655 1528 1542 1705 1737 1631 1623 1708 1608 1514 1544 1627
    ##  [7463] 1803 1705 1628 1727 1801 1836 1634 1630 1528 1700 1719 1543 1739 1731
    ##  [7477] 1724 1724 1710 1552 1621 1635 1638 1727 1646 1730 1636 1624 1819 1650
    ##  [7491] 1629 1557 1741 1735 1644 1604 1613 1740 1753 1600 1756 1647 1721 1655
    ##  [7505] 1741 1835 1701 1633 1611 1907 1626 1817 1633 1637 1727 1638 1703 1652
    ##  [7519] 1746 1739 1618 1649 1652 1842 1806 1653 1720 1617 1638 1929 1647 1803
    ##  [7533] 1824 1718 1823 1816 1740 1917 1724 1702 1751 1658 1812 1639 1838 1729
    ##  [7547] 1855 1822 1704 1917 1736 1816 1812 1819 2039 2028 1816 1817 1714 1848
    ##  [7561] 1906 1938 1836 1709 1750 1718 1830 1731 1649 1811 1855 1853 1825 1907
    ##  [7575] 1844 1822 1739 1751 1931 1751 1928 1936 1911 1757 1747 1932 1847 1746
    ##  [7589] 1721 1842 1739 1919 1808 1853 1706 1727 1858 1939 1946 1757 1929 1954
    ##  [7603] 1728 2017 1936 1927 1935 1727 1825 1837 1815 1936 1827 1838 1810 1843
    ##  [7617] 2009 1741 1810 1943 1849 1917 1833 1852 1759 1925 1831 1959 1939 1920
    ##  [7631] 1810 2038 1834 1804 1956 2001 2035 1804 1759 2105 1911 1809 1816 2133
    ##  [7645] 1958 2034 1821 2007 2013 2036 2053 2005 2007 2018 2007 2001 2003 1900
    ##  [7659] 2039 1908 1846 1924 2010 1858 1920 2048 1847 2017 2056 1921 2034 1959
    ##  [7673] 1830 1908 1947 2026 2036 1928 1943 2122 2008 1916 2053 1952 1959 2114
    ##  [7687] 2131 1902 2037 1843 1855 1913 1921 2128 2044 1903 2054 2102 1936 2040
    ##  [7701] 2037 2100 2042 1858 1900 1850 1952 1945 1951 2005 1955 2123 2114 2017
    ##  [7715] 2104 2041 1941 1927 2035 2147 1952 2139 2108 2139 2152 2038 2055 2111
    ##  [7729] 1946 2048 1949 2210 2159 2045 2230 2011 2021 2238 1946 1931 2032 2143
    ##  [7743] 2016 2241 2124 2010   24 2034 2132 2127 2133 2115 2024 2115 2047 2009
    ##  [7757] 2214 1952 2139 2143 2230 2055 2128 2021 2025 2248 2151 2220 2050 2105
    ##  [7771] 2036 2009 2038 2038 2214 2153 2246 2220 2220 2144 2306 2209 2044 2233
    ##  [7785] 2326 2205 2228 2217 2221 2211 2245 2110 2121 2137 2128 2224 2049 2225
    ##  [7799] 2120 2239 2302 2124 2224 2055 2159 2105 2245 2146 2130 2255 2340 2059
    ##  [7813] 2137 2150 2109 2045 2312 2103 2251 2126 2120 2232 2129 2251 2119 2232
    ##  [7827] 2251 2249 2114 2231 2206 2111 2158 2148 2245   53 2344 2159 2304 2329
    ##  [7841] 2106 2301 2228 2307 2200 2250 2136 2147 2222 2204 2319 2220   NA 2209
    ##  [7855] 2234 2323 2337 2217 2153 2211 2318 2149 2312 2234 2204   31 2254 2206
    ##  [7869] 2211 2228 2225 2231  150 2212 2217 2358   15   30  207  100 2244 2251
    ##  [7883] 2305 2301   18 2322 2259   43  111  101  258 2340 2357   21   28   12
    ##  [7897]   NA   NA   NA   NA   NA  426  447  634  813  824  832 1015  645  652
    ##  [7911]  649  711  837  834  733  733  746  701  903  716  823  818  855  933
    ##  [7925]  741  759  844  721  821  653  734  808  808  726  711  851  858  740
    ##  [7939]  932  811  844 1028  800  840  846  726  814  837  708  855  902  823
    ##  [7953]  950  840  920  753  818  802  900  836  951  727  920  748  810  800
    ##  [7967]  943 1008 1142  907  927  856  859  759  754  841 1009  946  756  942
    ##  [7981]  949  834  940  802  938 1025 1003  911  758 1013 1006  837 1007  831
    ##  [7995] 1020 1035 1006  842  943  912 1005 1158 1037  842 1014  940 1051 1022
    ##  [8009]  914  911 1003 1011  833 1006 1024 1020 1020 1003 1023 1026  954 1101
    ##  [8023] 1003 1031 1033 1011  902  925 1113 1214  901  915  925  936  907  945
    ##  [8037] 1015  855 1055 1024 1121 1002  851  858  917 1022 1007 1101  908  916
    ##  [8051] 1018 1051  947 1036  900 1101 1056 1131 1144  937  958 1016 1044 1044
    ##  [8065] 1004  955 1116 1247  948  913 1006  947 1041 1101 1043 1046  955  924
    ##  [8079] 1037  943 1251  943  929  951 1056 1041 1010 1027 1001  953 1128 1122
    ##  [8093] 1113  950 1103 1058 1200 1258 1130 1122  947  936 1124  944 1118 1023
    ##  [8107] 1013  940 1135 1036 1316 1111 1120 1051 1134 1200 1004 1004 1127 1234
    ##  [8121] 1056 1206 1213 1034 1159 1130 1040 1137 1142 1133 1153 1449 1155 1118
    ##  [8135] 1058 1205 1219 1115 1216 1053 1219 1403 1019 1018 1113 1219 1216 1221
    ##  [8149] 1035 1237 1010 1144 1425 1200 1050 1202 1125 1040 1132 1240 1225 1228
    ##  [8163] 1052 1105 1259 1208 1102 1119 1236 1101 1217 1119 1125 1051 1239 1128
    ##  [8177] 1046 1205 1203 1241 1254 1314 1245 1202 1243 1104 1304 1319 1239 1127
    ##  [8191] 1328 1323 1321 1121 1228 1218 1319 1259 1329 1236 1159 1135 1330 1358
    ##  [8205] 1358 1208 1217 1306 1158 1231 1318 1428 1212 1338 1344 1323 1206 1146
    ##  [8219] 1354 1332 1153 1155 1409 1154 1210 1223 1215 1357 1407 1316 1252 1434
    ##  [8233] 1234 1251 1258 1347 1341 1240 1248 1320 1239 1555 1350 1336 1430 1400
    ##  [8247] 1305 1439 1315 1339 1409 1448 1244 1350 1452 1430 1449 1427 1423 1356
    ##  [8261] 1446 1252 1322 1346 1440 1407 1254 1426 1345 1244 1531 1434 1350 1300
    ##  [8275] 1441 1313 1303 1507 1329 1441 1422 1317 1256 1323 1321 1408 1325 1523
    ##  [8289] 1341 1413 1528 1357 1356 1456 1426 1614 1515 1549 1514 1525 1336 1455
    ##  [8303] 1542 1340 1350 1552 1346 1537 1522 1529 1344 1542 1538 1430 1403 1417
    ##  [8317] 1443 1416 1557 1453 1445 1408 1414 1524 1412 1400 1602 1449 1503 1538
    ##  [8331] 1447 1457 1646 1427 1628 1613 1457 1436 1604 1540 1611 1430 1455 1630
    ##  [8345] 1623 1430 1609 1649 1814 1610 1708 1935 1617 1510 1533 1605 1607 1703
    ##  [8359] 1632 1659 1503 1545 1509 1628 1702 1458 1516 1630 1645 1629 1551 1703
    ##  [8373] 1540 1511 1512 1621 1511 1618 1633 1640 1548 1705 1659 1632 1716 1812
    ##  [8387] 1546 1729 1533 1656 1600 1738 1634 1538 1747 1639 1659 1711 1551 1628
    ##  [8401] 1801 1637 1614 1753 1655 1608 1740 1804 1559 1608 1610 1602 1726 1605
    ##  [8415] 1642 1645 1815 1739 1805 1740 1729 1755 1830 1636 1629 1806 1659 1624
    ##  [8429] 1648 1629 1654 1810 1753 1712 1821 1744 1647 1737 1758 1649 1625 1736
    ##  [8443] 1641 1704 1826 1744 1624 1633 1831 1707 1729 1644 1727 1641 1757 1856
    ##  [8457] 1800 1851 1713 1908 1711 1845 1652 1703 1704 1851 1729 1839 1835 1906
    ##  [8471] 1846 1817 1901 1828 2030 1805 1855 1750 1732 1657 1848 1658 1706 1715
    ##  [8485] 1744 1844 2037 1858 1841 1836 1714 1914 1805 1751 1715 1717 1844 1905
    ##  [8499] 1834 1848 1856 1853 1731 1927 1841 1813 1748 1835 1745 1843 1754 1926
    ##  [8513] 1901 1748 1831 1804 1817 1930 1928 1729 1827 1828 1949 1825 1911 1858
    ##  [8527] 1931 1941 1926 1815 1932 1849 1937 1847 1814 1829 1817 1939 1919 1837
    ##  [8541] 2000 1752 1928 1733 1958 1811 2007 1757 1934 1814 1948 2125 1810 1924
    ##  [8555] 1925 1831 2007 2030 1800 1950 1808 1802 2020 1913 2003 1823 1944 2034
    ##  [8569] 1858 1913 2013 1926 2010 1807 1902 1852 2014 1910 1851 2017 1836 2035
    ##  [8583] 1950 2058 2023 1925 2002 1848 2029 1901 2005 1911 1840 2001 1844 2050
    ##  [8597] 2010 2014 1901 2038 2033 1939 1957 1915 1944 2033 2035 2103 2049 2104
    ##  [8611] 2115 2100 2033 1905 2051 2137 1925 1854 2030 1916 2040 1911 1946 1929
    ##  [8625] 2005 2115 1923 1943 2100 2132 2122 2139 2027 2017 2109 2158 2041 1927
    ##  [8639] 1921 2149 2111 2058 2105 2100 2012 1945 1955 2037 2031 2157 1946 1941
    ##  [8653] 1957 2014 2144 2031 1940 2104 1932 2102 2133 2216 2025 1951 2123 2004
    ##  [8667] 1959 1949 2034 2144 2058 2018 2118 2137 2052 2128 2125 2034 2220 2038
    ##  [8681] 2131 2124 2016 2002 2033 2027 2201 2029 2152 2003 2152 2226 2208 2239
    ##  [8695] 2059 2012 2027 2135 2029 2230 2200 2052 2130 2147 2219 2129 2200 2228
    ##  [8709] 2037 2047 2217 2242 2207 2223 2203 2133 2042 2230 2150 2058 2127 2041
    ##  [8723] 2251 2052 2242 2215 2219 2134 2047 2223 2044 2130 2224 2050 2059 2231
    ##  [8737] 2205   18 2258 2134 2248 2149 2106 2242 2240 2146 2124 2304 2239 2055
    ##  [8751] 2311 2152 2111 2144 2130 2246 2114 2251 2223 2131 2128 2147 2300 2213
    ##  [8765] 2258 2304 2259 2327 2219 2347 2200 2215 2307  112 2138 2328 2318 2139
    ##  [8779] 2140 2217 2351 2308 2245 2212 2151 2345 2316 2209 2202 2216 2236 2229
    ##  [8793] 2256 2201 2321   37 2318 2337 2219 2230 2206 2220 2234 2334 2214  148
    ##  [8807]    2    6 2223   22 2251   17 2320   37   45   34 2256 2250 2302 2247
    ##  [8821] 2303 2345  254 2349   18 2346 2357 2355    6   16   NA   NA   NA  436
    ##  [8835]  439  643  735  817  812  956  642  750  653  652  824  647  837  701
    ##  [8849]  753  849  849  826  743  839  740  740  923  838  719  859  936  857
    ##  [8863]  702  729  909  745  722  805  726  810  725  854  828  840  721 1039
    ##  [8877]  857  856  825  718  812  839  919  758 1153  836  914  818  800  736
    ##  [8891]  922  846  801 1026  934  834  914  918  942  810  934  756  858 1002
    ##  [8905]  919  827  923  831  906  749  856  955 1025  750  907  816  758 1001
    ##  [8919]  822  845 1014  929 1025 1004  945  949  938  754  903 1026 1021  844
    ##  [8933] 1000 1031  947  933  952  824 1044  954 1006 1024 1019 1208  949  854
    ##  [8947] 1004  919 1010  938  845 1028 1053 1022  954 1058 1006 1034 1057 1031
    ##  [8961] 1021  854 1021  925  854 1110 1223 1115  959  940 1052  848  912 1032
    ##  [8975] 1038 1038  951  938 1028 1100  851  923 1011  906  909 1028  911 1116
    ##  [8989] 1103  958  950  949 1026  959 1152 1114 1053 1100  907 1024  953 1056
    ##  [9003]  911 1018 1114 1123 1252  936  933  935 1257  952  951 1205 1108 1133
    ##  [9017] 1054 1003 1006 1008 1018  941 1021 1106  949 1105 1201 1123 1016 1015
    ##  [9031] 1140 1056 1017  954 1331 1103 1010  934  952 1137 1203 1006 1224 1138
    ##  [9045] 1056 1020 1123 1157 1101 1137 1053  957 1002 1021 1350 1142 1147 1023
    ##  [9059] 1157 1102 1143 1442 1213 1054 1023 1152 1158 1132 1223 1112 1354 1034
    ##  [9073] 1242 1156 1015 1231 1110 1108 1221 1136 1215 1121 1216 1019 1211 1241
    ##  [9087] 1044 1228 1216 1039 1125 1405 1219 1225 1217 1040 1151 1239 1219 1203
    ##  [9101] 1122 1100 1054 1136 1056 1055 1054 1112 1210 1110 1246 1052 1250 1222
    ##  [9115] 1236 1222 1247 1319 1400 1321 1156 1207 1125 1242 1130 1236 1348 1310
    ##  [9129] 1244 1137 1223 1214 1133 1154 1308 1311 1217 1225 1331 1114 1339 1342
    ##  [9143] 1241 1202 1136 1153 1317 1358 1153 1225 1333 1226 1323 1214 1335 1356
    ##  [9157] 1341 1142 1153 1350 1413 1203 1355 1240 1411 1223 1348 1241 1403 1250
    ##  [9171] 1206 1326 1249 1356 1352 1328 1358 1239 1427 1436 1559 1413 1319 1359
    ##  [9185] 1432 1304 1331 1300 1426 1410 1432 1449 1313 1313 1245 1417 1400 1433
    ##  [9199] 1338 1241 1313 1247 1345 1434 1516 1327 1318 1302 1414 1431 1414 1449
    ##  [9213] 1313 1422 1259 1303 1313 1301 1308 1523 1551 1434 1359 1530 1349 1404
    ##  [9227] 1339 1606 1521 1434 1526 1418 1535 1332 1535 1612 1531 1458 1459 1556
    ##  [9241] 1519 1438 1543 1349 1403 1422 1459 1454 1348 1417 1406 1357 1533 1401
    ##  [9255] 1518 1549 1548 1527 1558 1507 1414 1411 1438 1505 1356 1602 1647 1429
    ##  [9269] 1639 1523 1559 1445 1425 1617 1754 1545 1605 1600 1710 1457 1634 1657
    ##  [9283] 1451 1521 1617   NA 1558 1540 1635 1718 1540 1644 1443 1643 1506 1631
    ##  [9297] 1655 1627 1511 1619 1520 1658 1459 1548 1642 1502 1629 1529 1602 1524
    ##  [9311] 1538 1639 1629 1952 1707 1702 1630 1646 1726 1844 1650 1758 1558 1711
    ##  [9325] 1648 1532 1724 1729 1607 1716 1725 1645 1708 1743 1622 1655 1730 1734
    ##  [9339] 1651 1618 1648 1829 1615 1557 1620 1801 1721 1827 1553 1646 1723 1648
    ##  [9353] 1753 1604 1649 1631 1727 1819 1616 1724 1702 1703 1627 1750 1635 1705
    ##  [9367] 1847 1618 1751 1730 1753 1823 1634 1657 1657 1637 1747 1730 1821 1724
    ##  [9381] 1651 1711 1709 1657 1848 1732 1824 1634 1837 1847 1910 1716 1833 1848
    ##  [9395] 1724 1746 1712 1700 1714 1801 1835 1916 1754 1807 1637 1811 1908 1744
    ##  [9409] 1837 1815 1805 1723 1737 1707 1906 1821 1802 1849 1708 1853 1718 1837
    ##  [9423] 1720 1717 1746 1848 1834 1917 1842 1816 1720 1857 1717 2030 1859 2049
    ##  [9437] 1805 1718 1852 1753 1845 1803 1918 1951 2012 1737 1847 2003 1748 1826
    ##  [9451] 1716 1750 1955 1739 1724 1925 1955 1843 1758 1801 2011 1913 1923 1925
    ##  [9465] 1851 1859 1930 1811 1903 1912 1835 1849 1842 1831 1754 1939 1952 1937
    ##  [9479] 1803 2016 2009 2019 1817 1822 2133 1825 1859 1940 2009 2018 1943 2018
    ##  [9493] 2001 1928 2020 1918 1801 2012 1817 2003 1943 1847 2013 1923 1839 1832
    ##  [9507] 2042 2003 1826 1828 2035 1854 2005 2011 2026 1854 1852 2037 1927 1918
    ##  [9521] 1955 2049 2038 2035 1842 1853 1933 2016 2010 2052 2017 1933 1916 2037
    ##  [9535] 2040 1918 2021 2031 1942 2031 2123 2034 1908 1911 2052 2022 2029 1914
    ##  [9549] 1910 2024 2115 1941 1918 1954 1911 2059 1923 1924 2021 2117 1940 2050
    ##  [9563] 2012 1934 2114 2030 2145 2116 2109 2117 2025 2135 2138 2146 2115 2014
    ##  [9577] 2003 1941 2028 2153 2102 2142 2040 2145 2006 2017 2016 2020 2143 2022
    ##  [9591] 2049 2124 2152 2009 1958 1959 2117 2139 2006 2128 2021 2218 2128 2123
    ##  [9605] 2005 2117 2007 2103 2241 2146 2024 2134 2236 2248 2133 2125 2222 2139
    ##  [9619] 2038 2033 2233 2234 2231 2201 2217 2144 2141 2222 2240 2047 2059 2223
    ##  [9633] 2223 2306 2218 2247 2214 2052 2157 2107 2254 2259 2125 2216 2218 2043
    ##  [9647] 2207 2227 2226 2146 2057 2239 2053 2140 2059 2209 2321 2105 2118 2308
    ##  [9661] 2123 2119 2059 2242 2321 2122 2237 2153 2236 2234 2117 2236 2240 2119
    ##  [9675] 2206 2152 2206 2141 2118 2206 2235 2319 2255 2332 2145 2259 2140 2136
    ##  [9689] 2216 2205 2244 2200 2143 2333 2147 2148 2318 2211 2215 2355 2248 2335
    ##  [9703]  114 2255 2328 2212 2220 2224 2226 2252 2218 2321 2218   22 2204 2348
    ##  [9717] 2309  150 2226 2346 2219 2218 2255 2233  159   12    7   51   14 2358
    ##  [9731] 2235 2233 2245   20 2319 2248 2300 2330   31    7    1   49   53 2318
    ##  [9745]  301 2343 2349    3 2353    9    1    9   NA   NA   NA   NA   NA   NA
    ##  [9759]   NA   NA   NA   NA   NA  506  646  755  808  821 1005  653  832  818
    ##  [9773]  915  720  658  847  836  708  836  752  833  705  853  731  842  847
    ##  [9787]  728  852  715  811  906  837 1029  802  749  828  816  839  721  855
    ##  [9801]  756  830  816  948  857  828  929  741  910 1114  905  957  837  808
    ##  [9815]  748  841  907  803  914  901  859 1029 1014  948  927  811  827  955
    ##  [9829]  807  952  923  903 1018 1003  848 1013 1146  952 1017 1002  905  840
    ##  [9843] 1144 1028 1008  956  959 1021 1050 1056 1034  933 1036  901 1032 1057
    ##  [9857] 1111 1218 1036  934 1033  910 1038 1020  923 1035 1051  935 1022  903
    ##  [9871] 1016 1044 1029 1147  948 1033  937  918 1020 1043 1008 1042  929 1245
    ##  [9885] 1001 1027  954 1052  923 1056 1033 1006 1246  929  932 1119 1018  923
    ##  [9899]  959 1115 1300  927 1112  929 1112  953  933 1121 1024  947 1152 1116
    ##  [9913] 1042 1109 1012 1049 1146 1120 1149 1007 1147  936 1030 1334 1112  957
    ##  [9927] 1031 1048  956 1008 1050 1148 1111 1113 1000 1219 1104 1109 1138 1146
    ##  [9941] 1128 1156 1043 1012 1215 1035 1146 1037 1452 1145 1215 1028 1347 1403
    ##  [9955] 1237 1219 1357 1052 1044 1208 1239 1149 1409 1039 1210 1037 1104 1056
    ##  [9969] 1212 1213 1223 1109 1236 1052 1118 1235 1215 1108 1052 1218 1107 1225
    ##  [9983] 1159 1106 1328 1234 1234 1122 1112 1322 1152 1328 1253 1120 1240 1206
    ##  [9997] 1335 1358 1320 1308 1122 1344 1341 1306 1341 1339 1336 1342 1346 1408
    ## [10011] 1337 1324 1415 1200 1201 1235 1211 1259 1337 1251 1350 1421 1403 1423
    ## [10025] 1401 1423 1344 1254 1258 1320 1328 1438 1312 1408 1307 1238 1443 1307
    ## [10039] 1300 1438 1248 1409 1247 1450 1344 1259 1322 1501 1344 1414 1258 1508
    ## [10053] 1426 1438 1320 1327 1606 1336 1305 1330 1534 1532 1525 1441 1529 1417
    ## [10067] 1356 1513 1535 1518 1359 1541 1514 1505 1412 1400 1427 1556 1404 1454
    ## [10081] 1407 1516 1535 1543 1419 1623 1402 1411 1411 1547 1531 1415 1733 1420
    ## [10095] 1546 1511 1602 1616 1447 1625 1444 1357 1421 1554 1554 1544 1748 1636
    ## [10109] 1609 1605 1629 1913 1637 1659 1553 1554 1719 1454 1500 1535 1644 1606
    ## [10123] 1608 1449 1606 1720 1637 1628 1555 1511 1615 1601 1621 1700 1538 1734
    ## [10137] 1744 1652 1626 1746 1555 1602 1624 1723 1631 1714 1553 1534 1605 1606
    ## [10151] 1721 1648 1731 1733 1642 1742 1551 1627 1644 1634 1755 1738 1725 1633
    ## [10165] 1627 1758 1622 1840 1614 1621 1637 1602 1718 1752 1723 1637 1757 2010
    ## [10179] 1738 1649 1746 1632 1640 1744 1638 1638 1834 1705 1639 1649 1709 1702
    ## [10193] 1838 1807 1845 1639 1704 1732 1722 1737 1647 1849 1904 1742 1802 1841
    ## [10207] 1816 1708 1707 1901 1816 1740 1803 2038 1802 1754 1838 1845 1850 1824
    ## [10221] 1814 1733 1856 1811 1849 1730 2059 1837 1903 1729 1726 1733 1841 1717
    ## [10235] 1817 2021 1708 1917 1744 1858 2004 1801 1718 1924 1742 2008 1731 1749
    ## [10249] 1945 1825 1821 1908 1909 1820 1820 1757 1825 1801 1920 1845 2002 1827
    ## [10263] 1838 1924 1804 1953 1952 1955 2001 2023 1739 1740 1935 2015 1829 1932
    ## [10277] 2120 1816 1849 1913 1757 1941 1924 1941 1935 2014 1949 1947 1842 1817
    ## [10291] 2009 2003 1805 2015 1822 1922 1835 2017 1820 2030 2020 1908 2006 1957
    ## [10305] 2044 2013 2109 2001 2025 1903 1912 2014 2055 2057 1907 2025 1953 2115
    ## [10319] 1854 1946 2035 2040 1909 2059 2134 2046 2036 1920 2104 1918 2016 2035
    ## [10333] 1951 2049 1937 2047 1929 2104 2049 2131 1947 2123 1922 2106 1936 1915
    ## [10347] 1932 2038 2125 2017 2042 2108 1943 2001 2109 2002 2157 2039 2100 2208
    ## [10361] 2147 2349 2108 2105 2218 2130 2138 2210 2142 2040 2050 2147 2134 2203
    ## [10375] 2250 2141 2153 2023 2049 2031 2047 2305 2042 2119 2216 2151 2213 2249
    ## [10389] 2157 2113 2226 2115 2225 2257 2159 2109 2130 2154 2122 2113 2104 2247
    ## [10403] 2049 2243 2156 2109 2131 2122 2202 2348 2126 2141 2107 2336 2318 2249
    ## [10417]  110 2141 2230 2310 2354 2243 2300 2337 2246 2354   13 2234   51 2224
    ## [10431]   16    4 2233  210 2307 2246 2249 2242   29 2336 2352   15 2355    9
    ## [10445] 2357  347  429   NA   NA   NA   NA   NA   NA  108  502  340  305  505
    ## [10459]  203  223  222  409  806 1027  826  930  851  902  815  817  853  842
    ## [10473]  843  839  801  827  753  853  910  952  900  920  825  911  746  849
    ## [10487]  754  753  903  915 1009 1134  814  939  826  910  934  933  845  956
    ## [10501] 1006  804  928  946  800  957  959  953  918  930  838  955  955 1001
    ## [10515]  946 1022  924  958 1150  904 1007 1020 1040 1025  835 1027 1155 1022
    ## [10529] 1025 1010 1058 1027  915 1057 1053 1045 1029 1056  900  945  925 1228
    ## [10543] 1103 1046 1021  914 1026 1018 1050 1016  939  906  944 1038 1049 1144
    ## [10557] 1022 1023 1006 1043  907  950  913  937 1006  952 1002  925 1038 1141
    ## [10571]  939  915 1038  941 1116 1114 1256 1000  952 1034  954 1149 1026 1049
    ## [10585] 1101  942 1113 1042 1123 1136 1156 1005  958 1030 1002 1100 1144 1142
    ## [10599] 1001 1009 1154 1335 1013 1150 1121 1104 1136 1050 1225 1031 1129 1019
    ## [10613] 1041 1142 1523 1044 1220 1205 1232 1203 1243 1024 1126 1121 1040 1237
    ## [10627] 1352 1134 1031 1046 1104 1102 1231 1233 1225 1139 1230 1040 1142 1059
    ## [10641] 1217 1426 1054 1214 1213 1232 1226 1116 1052 1112 1104 1227 1220 1210
    ## [10655] 1130 1324 1224 1354 1254 1221 1122 1300 1206 1247 1148 1154 1133 1214
    ## [10669] 1111 1202 1330 1136 1159 1333 1320 1321 1337 1347 1128 1250 1202 1335
    ## [10683] 1342 1317 1315 1211 1317 1234 1407 1331 1325 1238 1158 1209 1407 1236
    ## [10697] 1359 1359 1319 1212 1207 1416 1215 1256 1349 1346 1258 1407 1233 1644
    ## [10711] 1359 1248 1556 1412 1256 1301 1439 1415 1255 1347 1233 1442 1419 1423
    ## [10725] 1434 1335 1337 1309 1316 1335 1338 1251 1446 1344 1302 1512 1420 1519
    ## [10739] 1415 1308 1310 1505 1429 1336 1328 1336 1312 1358 1329 1515 1558 1525
    ## [10753] 1346 1338 1400 1516 1410 1348 1531 1527 1502 1537 1557 1434 1547 1336
    ## [10767] 1343 1513 1548 1529 1541 1459 1503 1418 1417 1335 1506 1558 1449 1604
    ## [10781] 1442 1530 1455 1408 1537 1412 1458 1411 1449 1620 1503 1609 1450 1550
    ## [10795] 1636 1912 1454 1628 1600 1434 1554 1526 1815 1500 1449 1656 1629 1908
    ## [10809] 1533 1456 1630 1617 1521 1615 1454 1636 1541 1628 1654 1633 1658 1730
    ## [10823] 1505 1502 1506 1631 1711 1643 1649 1536 1750 1649 1637 1633 1514 1551
    ## [10837] 1648 1605 1659 1732 1711 1739 1615 1652 1632 1543 1715 1602 1625 1631
    ## [10851] 1704 1747 1759 1612 1706 1743 1746 1630 1638 1613 1649 1558 1752 1747
    ## [10865] 1601 1622 1745 1604 1732 1736 1733 1627 1638 1736 1706 1740 1830 1733
    ## [10879] 1635 1621 1654 1648 1722 1649 1803 1745 1717 1841 1824 1629 1625 1741
    ## [10893] 1703 1823 1716 1658 1653 1706 1837 1659 1650 1843 1843 1809 1822 1638
    ## [10907] 1708 1846 1728 1823 1857 1742 1836 1712 1659 1648 1806 1820 1830 1758
    ## [10921] 1704 1852 1757 2043 1836 1841 1759 1804 1919 1655 1843 1818 1820 1743
    ## [10935] 1759 1742 1844 1733 1711 1922 1928 1704 1946 1722 1915 1759 1800 1918
    ## [10949] 1846 1734 1910 1919 1736 1842 1846 1914 1844 1742 1933 1843 2102 1853
    ## [10963] 1852 2001 1836 1825 1756 1946 1937 1812 1727 2000 1806 1924 1836 1901
    ## [10977] 1950 1903 1757 1930 1820 2003 1803 1909 1946 1959 2015 2138 2014 1852
    ## [10991] 1959 1805 1928 1819 2008 1902 2012 1949 1829 2056 2015 1900 2023 1856
    ## [11005] 1824 1826 2025 1954 1839 2021 2047 2019 2020 2027 2025 1821 2035 1838
    ## [11019] 2004 1920 2041 2027 1856 1850 2025 1951 1920 2013 2025 1901 2038 1927
    ## [11033] 1907 2018 2013 2106 2039 2028 2115 2043 2040 1922 1940 2031 1939 1853
    ## [11047] 2101 2025 1848 2057 1941 1951 2016 2045 1923 2003 2134 2034 2111 1942
    ## [11061] 1933 1952 2201 2035 2054 2036 2004 2057 1945 1941 1917 2156 2230 1944
    ## [11075] 1937 1927 2223 2007 2108 2015 2145 1956 1956 2202 2014 2037 2018 2104
    ## [11089] 2146 2209 2029 2008 2021 2150 2027 2123 2131 2024 2034 2132 2224 2226
    ## [11103] 2038 2045 2214 2204 2241 2135 2055 2209 2122 2021 2254 2059 2003 2117
    ## [11117] 2146 2257 2038 2021 2042 2150 2315   11 2126 2210 2208 2049 2245   NA
    ## [11131] 2229 2259 2116 2314 2300 2354 2257 2126 2224 2052 2245 2052 2243 2214
    ## [11145] 2202 2232 2131 2252 2241 2105 2301 2159 2150 2131 2218 2325 2206 2303
    ## [11159] 2117 2302 2246 2127 2144 2209 2231 2303 2155 2133 2314 2221 2319 2259
    ## [11173] 2309 2342 2203 2328 2355 2202 2202 2200 2246 2330    4 2345 2233 2227
    ## [11187] 2152 2157    5 2302   58 2320    2 2334 2304 2254 2235   14 2235 2237
    ## [11201] 2221 2226   23    7 2253 2323 2251 2257 2243 2241 2320 2318 2336 2243
    ## [11215]   21 2322   35 2256 2236   17  115   22   20   56    4   42 2316   45
    ## [11229] 2300 2344  116  218  100   12  230 2302  101   58   32  127  116 2346
    ## [11243]    5  115  111  143   NA  152   43  317 2400   25  142 2350  119  121
    ## [11257]  357  125  121   40   35  100  100  233  435   NA   NA   NA   NA   NA
    ## [11271]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA  640  831  859
    ## [11285] 1007  830  837  833  813  921  751  646  818  652  651  701 1014  908
    ## [11299]  827  740  849  808  911  657  732  717  900  810  744  906  745  732
    ## [11313]  708 1034  805  839  752  856  820  910  921  909  839  737  934  813
    ## [11327]  935  802 1004  828 1010  911  904 1130  852  943  842  829  731  831
    ## [11341] 1005  929 1027  810  847  939  946  858  958  758  939  932  916  950
    ## [11355] 1012 1029  942  912  927 1008  840 1020 1028 1001 1021  852  959  855
    ## [11369] 1000  952 1103  953 1031  950 1020  809 1004 1033  852 1038  948  854
    ## [11383] 1019  837 1044  904 1029 1204  907 1021 1109 1013 1003  927  836  920
    ## [11397] 1056  849 1104 1100 1039 1004 1112  922 1111 1036  937 1133 1218 1054
    ## [11411] 1122 1044  916  951  940 1107 1020 1100  953  908  933  905 1108 1219
    ## [11425] 1112 1124  905 1013  909 1255 1009 1056 1031  955 1046 1039 1123 1105
    ## [11439]  913 1110 1005 1016  934 1053 1107 1030 1120 1056 1100 1024  957 1037
    ## [11453] 1127 1022 1000 1011 1049  937  957 1015 1302 1009 1132 1008 1305 1113
    ## [11467]  941 1001 1003 1013 1208 1117 1138 1206 1158 1210  953 1001  942 1403
    ## [11481] 1151 1113 1037 1015 1101 1040 1027 1226 1102 1151 1154 1015 1126 1154
    ## [11495] 1105 1146 1227 1210 1148 1050 1046 1210 1456 1149 1213 1018 1027 1216
    ## [11509] 1010 1339 1248 1228 1150 1143 1121 1129 1107 1040 1104 1124 1245 1113
    ## [11523] 1248 1102 1241 1259 1149 1220 1103 1306 1426 1042 1213 1238 1231 1137
    ## [11537] 1236 1104 1109 1222 1310 1112 1135 1153 1213 1130 1120 1239 1100 1151
    ## [11551] 1313 1100 1246 1057 1139 1250 1258 1248 1240 1355 1120 1244 1209 1139
    ## [11565] 1308 1125 1215 1209 1354 1312 1119 1338 1302 1251 1215 1206 1250 1334
    ## [11579] 1346 1218 1147 1253 1409 1358 1339 1253 1334 1404 1300 1325 1214 1236
    ## [11593] 1226 1205 1149 1206 1412 1201 1404 1338 1405 1316 1354 1413 1420 1343
    ## [11607] 1317 1423 1252 1202 1323 1426 1226 1248 1320 1346 1542 1420 1431 1310
    ## [11621] 1322 1443 1406 1240 1408 1316 1255 1350 1438 1343 1358 1620 1449 1427
    ## [11635] 1254 1427 1321 1450 1455 1447 1410 1243 1435 1244 1419 1248 1307 1304
    ## [11649] 1435 1505 1419 1448 1313 1543 1324 1410 1458 1533 1321 1514 1301 1354
    ## [11663] 1416 1632 1529 1444 1423 1406 1342 1453 1406 1330 1552 1537 1551 1440
    ## [11677] 1537 1524 1616 1346 1506 1616 1345 1346 1545 1503 1544 1419 1538 1400
    ## [11691] 1400 1459 1454 1541 1518 1610 1354 1406 1618 1557 1425 1402 1424 1504
    ## [11705] 1351 1552 1526 1503 1419 1558 1636 1633 1512 1634 1431 1605 1605 1506
    ## [11719] 1746 1638 1728 1603 1620 1648 1443 1514 1703 1651 1618 1920 1625 1634
    ## [11733] 1542 1527 1724 1536 1620 1700 1542 1635 1603 1504 1522 1454 1630 1455
    ## [11747] 1657 1523 1707 1650 1546 1647 1515 1614 1617 1509 1559 1711 1716 1745
    ## [11761] 1722 1635 1721 1706 1742 1606 1600 1712 1727 1621 1827 1629 1730 1724
    ## [11775] 1627 1654 1742 1734 1816 1636 1647 1755 1550 1644 1652 1721 1555 1558
    ## [11789] 1658 1803 1638 1813 1638 1806 1740 1654 1606 1623 1557 1831 1656 1804
    ## [11803] 1623 1733 1807 1643 1655 1724 1635 1657 1806 1653 1727 1755 1707 1748
    ## [11817] 1840 1649 1811 1849 1642 1707 1831 1823 1736 1819 1910 1736 1749 1712
    ## [11831] 1657 1707 1904 1720 1722 1914 1806 1749 1833 1740 1723 1854 1848 1739
    ## [11845] 1801 1854 1645 1810 1820 1918 1724 1646 1834 1905 1847 1908 1815 1731
    ## [11859] 1707 1726 1905 1918 2038 1844 1830 1909 1839 1834 1826 1807 1808 1744
    ## [11873] 1822 1715 1828 1843 1745 1928 1730 1925 1723 1744 1845 1955 1758 1709
    ## [11887] 1901 1910 1850 1722 1857 1816 1846 1939 2052 1906 1720 1802 1938 1809
    ## [11901] 1908 1726 2014 1832 1954 1748 2017 2055 1817 1832 1933 1854 1839 1859
    ## [11915] 1836 1900 1951 1951 1915 1751 1824 2014 1835 1955 1813 2008 1955 1938
    ## [11929] 1802 1806 2003 1812 1815 1844 2013 1944 1824 2150 2124 1934 2037 1810
    ## [11943] 1815 2051 1938 1905 1818 1813 2027 2034 1907 2023 2003 2011 2014 1901
    ## [11957] 1933 2026 1928 1935 2013 2012 2044 2039 1932 1849 2041 2026 2043 1931
    ## [11971] 2008 1933 2031 1910 2028 2044 2027 2027 1835 2047 2025 2036 2032 1913
    ## [11985] 1915 1946 2114 2024 1941 2055 2107 1932 1858 2035 2039 2057 2031 1857
    ## [11999] 1921 2124 1850 2059 1918 1946 2103 2046 2131 1856 1959 1941 1949 2127
    ## [12013] 2201 2002 1949 2112 2204 2043 2005 2027 2056 2101 2018 2107 2209 2111
    ## [12027] 1928 1928 1928 2111 1944 2132 2138 2137 2020 2132 2136 1926 2130 2109
    ## [12041] 2015 2118 2039 2019 2106 2004 2116 2117 2038 2156 2026 2157 2047 2119
    ## [12055] 2114 2145 1947 2059 2040 2019 2128 2010 2212 2017 2135 2033 2152 2033
    ## [12069] 2216 2015 2341 2054 2102 2102 2010 2300 2053 2233 2202 2142 2219 2100
    ## [12083] 2215 2250 2148 2103 2157 2248 2240 2316 2218 2241 2139 2210 2059 2235
    ## [12097] 2120 2118 2051 2232 2237 2252 2222 2225 2121 2330 2256 2247 2100 2142
    ## [12111] 2049 2120 2223 2318 2251 2126 2210 2058 2240 2248 2246 2106 2104 2139
    ## [12125] 2211 2140 2108 2245 2255 2338 2303 2134 2224 2223 2211 2149 2119 2209
    ## [12139] 2305 2320 2115 2354 2156 2302 2241 2311 2127 2226 2353  100 2137 2135
    ## [12153] 2334 2157 2145 2301 2348 2249 2342 2152 2202 2209 2329 2232 2354 2320
    ## [12167]   18 2249 2152 2218   10 2242 2238 2200 2314   15 2252    1    6 2256
    ## [12181]    4 2215   38   28   16   29 2231  157 2223 2239 2306   32 2249 2255
    ## [12195] 2304 2313  157 2335 2347 2344 2341    1    9   47  212  427  429   NA
    ## [12209]   NA  645  825  839  829 1014  710  637  934  658  851  841  850  914
    ## [12223]  751  647  730  845  920  905  704  659  812  719  733  845  747  804
    ## [12237]  825  858  748  852 1036  706  920  906  748  820  818  927  916  719
    ## [12251]  828  915  903  945  843  847 1057  833  923  740  727  852  813  928
    ## [12265]  833  804  852  907  940  925  908  811  957 1013  755  911  746  927
    ## [12279]  943  923 1014 1006 1008  836  912 1030  948  803  803  948  831  958
    ## [12293]  838 1020 1012  949  929 1005  900 1027  752 1015 1026  843 1013  946
    ## [12307] 1205  931 1013 1031 1024  903 1027 1039  920  910 1033 1028 1006 1046
    ## [12321] 1053 1046  848 1050 1003 1037 1042  946 1104 1026 1216  917  936  922
    ## [12335]  958  947  854  856 1058 1038  923  857 1028 1121  852  938 1041 1201
    ## [12349] 1015 1108 1130 1307 1059  902  949  907  944 1003 1045 1043 1008 1050
    ## [12363] 1017 1034 1112 1040 1115 1055 1114 1025 1032  911  949 1003  941  938
    ## [12377] 1252 1043 1037 1011 1043 1118  928 1123 1053 1143  955 1018 1355 1017
    ## [12391] 1123 1029 1112 1004 1025 1122 1133  958 1023 1201 1148 1117  932 1047
    ## [12405]  957 1144 1029 1321  936 1033 1053 1054 1203 1044 1214 1144 1122 1146
    ## [12419] 1221 1152 1148 1137  957  950 1010 1055 1136 1439 1056 1130 1035 1117
    ## [12433] 1221 1013 1151 1226 1213 1231 1348 1152 1052 1208 1223 1042 1125 1028
    ## [12447] 1203 1226 1128 1047 1227 1401 1045 1222 1218 1244 1042 1221 1223 1210
    ## [12461] 1234 1055 1236 1120 1242 1207 1218 1140 1047 1224 1132 1042 1206 1204
    ## [12475] 1226 1053 1233 1123 1134 1249 1134 1340 1239 1311 1248 1249 1316 1141
    ## [12489] 1239 1234 1128 1346 1230 1328 1304 1216 1341 1220 1325 1300 1340 1425
    ## [12503] 1140 1220 1158 1355 1323 1251 1217 1234 1216 1358 1356 1352 1151 1145
    ## [12517] 1342 1359 1401 1210 1306 1204 1429 1410 1205 1241 1231 1304 1411 1313
    ## [12531] 1411 1344 1403 1355 1352 1555 1405 1427 1311 1424 1358 1331 1344 1429
    ## [12545] 1322 1446 1310 1306 1419 1424 1235 1446 1440 1322 1411 1408 1448 1238
    ## [12559] 1432 1457 1434 1246 1504 1311 1250 1424 1309 1358 1334 1326 1402 1446
    ## [12573] 1509 1307 1317 1413 1606 1354 1530 1334 1532 1335 1456 1402 1407 1522
    ## [12587] 1431 1606 1505 1550 1336 1651 1536 1459 1613 1604 1436 1535 1337 1532
    ## [12601] 1557 1408 1418 1608 1441 1505 1341 1454 1552 1605 1548 1438 1407 1515
    ## [12615] 1606 1415 1517 1425 1632 1635 1515 1427 1501 1507 1710 1606 1605 1749
    ## [12629] 1403 1419 1424 1606 1707 1658 1623 1634 1710 1612 1540 1714 1615 1641
    ## [12643] 1705 1503 1535 1524 1700 1654 1721 1602 1453 1702 1948 1552 1712 1615
    ## [12657] 1551 1553 1511 1645 1640 1740 1713 1732 1541 1752 1720 1534 1747 1617
    ## [12671] 1726 1748 1718 1531 1736 1642 1653 1602 1632 1720 1738 1718 1558 1717
    ## [12685] 1811 1657 1601 1623 1800 1743 1616 1720 1635 1734 1700 1602 1625 1658
    ## [12699] 1800 1636 1819 1657 1832 1706 1656 1815 1744 1802 1709 1813 1641 1704
    ## [12713] 1649 1613 1728 1733 1756 1750 1750 1739 1611 1837 1843 1743 1658 1713
    ## [12727] 1852 1729 1647 1650 1723 1714 1637 1835 1744 1837 1850 1826 1854 1750
    ## [12741] 1840 1859 1811 1755 1656 1836 1744 1853 1737 1709 1908 1915 1754 1823
    ## [12755] 1648 2022 1813 1820 1717 1810 1750 1733 1704 1844 1926 1842 1857 1726
    ## [12769] 1705 1805 1913 1835 1842 1804 1906 1918 1936 1837 1957 1744 1734 1808
    ## [12783] 1903 1836 1752 1834 1854 1748 1814 1709 1815 1804 1901 1925 1803 1713
    ## [12797] 1830 1717 1919 1957 1929 1810 1913 1941 1849 1850 1811 1833 2004 1938
    ## [12811] 1846 2015 1937 1819 1841 1851 2001 1908 1856 1755 1944 1909 1927 2126
    ## [12825] 1935 1959 1816 1953 1854 2122 1802 1956 1801 1816 2003 1955 2005 1827
    ## [12839] 2008 1942 2018 2033 1905 1821 2026 1946 1902 1821 2017 1834 2007 1941
    ## [12853] 2019 2028 1845 1905 1920 1956 2042 1912 1928 2046 2036 1846 1924 2023
    ## [12867] 1948 2016 2030 1928 1843 1943 1918 2006 2029 1838 2108 2053 1930 2030
    ## [12881] 2028 1927 1919 1957 1948 2129 2105 2047 2119 2054 1905 2040 2106 1942
    ## [12895] 2053 1917 1959 1913 2109 2117 2035 2106 1919 2006 2005 1849 2003 1948
    ## [12909] 2108 1941 2010 2037 2114 2129 2133 2028 2130 2120 2142 2126 2112 1930
    ## [12923] 1930 2104 1954 2122 2014 1941 2157 2039 2135 1931 2211 2127 2023 2157
    ## [12937] 2016 2033 2043 2045 2009 2146 2030 2131 2133 2055 2211 2134 2128 2126
    ## [12951] 2327 1957 2028 2213 2103 2047 2012 2149 2043 2104 2225 2150 2014 2038
    ## [12965] 2029 2126 2227 2227 2146 2235 2045 2231 2135 2158 2149 2241 2155 2142
    ## [12979] 2206 2101 2048 2209 2222 2231 2234 2246 2113 2123 2107 2242 2230 2113
    ## [12993] 2126 2241 2232 2240 2105 2239 2234 2127 2109 2217 2124 2128 2245 2241
    ## [13007] 2129 2310 2122 2038 2108 2121 2103 2124 2138 2221 2247 2249 2313 2250
    ## [13021]   15 2249 2100 2246 2213 2214 2150 2132 2211 2243 2218 2127 2157 2119
    ## [13035] 2307 2213 2343 2118 2329 2221 2317 2305 2213 2126 2213 2123 2352 2239
    ## [13049] 2309 2305 2201 2330 2213  126 2216 2150 2256 2323 2148    4 2225 2218
    ## [13063] 2235 2256 2255 2202 2359 2251 2211 2207 2230   23   21 2225 2252 2243
    ## [13077] 2249  102  112 2302 2313 2332 2340    8  146   10    5    1  416  439
    ## [13091]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA  119
    ## [13105]  212  730 1027  908  920 1048  859  920  917  920  711  720  900  754
    ## [13119]  952  936  942  734  802 1002 1103  915  818  905  807  928  842  958
    ## [13133]  922  849  812  825  905  821  919  842 1026  823  926  836 1136  916
    ## [13147]  908 1000  942 1047  951  829  811  931  945  940  835 1038 1004 1029
    ## [13161]  914  858 1056  946 1023 1047  848  952 1023 1114 1010  904 1042 1014
    ## [13175] 1042  934 1101  920 1054  916  949 1106  923 1056 1207 1113  943 1027
    ## [13189] 1029 1032 1008 1037 1045 1009 1039 1055  918 1121 1037  853 1028 1053
    ## [13203] 1028  859 1055 1040 1021 1120 1121 1119 1103 1137 1107  937 1037 1052
    ## [13217] 1131  931 1042  937 1027 1055  938 1309 1153 1040 1107 1154 1112 1224
    ## [13231] 1026 1128 1052  950 1118 1006 1157 1138 1028  922 1127  955 1001  952
    ## [13245] 1109 1313  959 1228  924  927 1139 1111 1055 1100  935 1043 1037 1136
    ## [13259] 1143 1041 1049 1048 1144 1335 1208 1008  959 1152 1208   NA 1048 1053
    ## [13273] 1145 1358 1033  953 1213 1054 1126 1223 1138 1221 1015 1212 1120 1124
    ## [13287] 1216 1208 1510 1010 1215 1124 1021 1114 1010 1207 1117 1211 1250 1224
    ## [13301] 1252 1110 1146 1221 1149 1131 1143 1236 1127 1125 1306 1032 1302 1238
    ## [13315] 1126 1043 1237 1116 1049 1105 1243 1321 1243 1245 1242 1210 1254 1113
    ## [13329] 1236 1510 1239 1300 1058 1231 1118 1308 1116 1108 1144 1211 1141 1238
    ## [13343] 1311 1445 1255 1131 1148 1219 1315 1319 1154 1300 1156 1247 1326 1110
    ## [13357] 1301 1201 1222 1235 1549 1134 1230 1317 1348 1412 1347 1355 1312 1259
    ## [13371] 1252 1308 1120 1309 1344 1315 1416 1316 1417 1330 1437 1323 1222 1255
    ## [13385] 1310 1256 1304 1401 1412 1233 1430 1415 1302 1204 1215 1424 1211 1251
    ## [13399] 1324 1310 1259 1445 1411 1403 1501 1405 1454 1501 1438 1429 1311 1426
    ## [13413] 1607 1442 1312 1428 1416 1352 1342 1425 1447 1304 1525 1406 1512 1411
    ## [13427] 1512 1348 1403 1311 1509 1449 1515 1408 1503 1429 1529 1306 1339 1532
    ## [13441] 1514 1310 1308 1333 1446 1537 1327 1502 1345 1356 1346 1342 1445 1513
    ## [13455] 1427 1355 1539 1324 1600 1418 1404 1528 1558 1559 1450 1558 1424 1546
    ## [13469] 1431 1553 1613 1435 1649 1620 1557 1557 1600 1512 1502 1542 1455 1513
    ## [13483] 1455 1351 1352 1551 1433 1547 1620 1414 1359 1517 1603 1609 1450 1441
    ## [13497] 1525 1534 1441 1637 1639 1603 1803 1559 1658 1523 1437 1650 1534 1615
    ## [13511] 1451 1658 1645 1703 1609 1710 1620 1732 1701 1626 1631 1722 1542 1508
    ## [13525] 1533 1442 1649 1649 1708 1505 1725 2017 1453 1613 1518 1502 1719 1636
    ## [13539] 1721 1738 1710 1559 1623 1712 1740 1739 1728 1734 1635 1720 1803 1734
    ## [13553] 1740 1613 1656 1653 1641 1737 1811 1725 1648 1731 1716 1643 1745 1652
    ## [13567] 1649 1755 1758 1807 1622 1832 1602 1811 1738 1604 1706 1721 1620 1743
    ## [13581] 1705 1712 1726 1817 1840 1641 1824 1722 1703 1804 1644 1729 1835 1730
    ## [13595] 1635 1836 1808 1637 1705 1642 1836 1704 1921 1745 1636 1632 1732 1750
    ## [13609] 1820 1907 1815 1733 1909 1835 1815 1825 1854 1732 1758 1905 2044 1909
    ## [13623] 1847 1835 1953 1911 1828 1919 1751 1850 1913 1724 1754 1845 2055 1749
    ## [13637] 1918 1919 1817 1746 1958 1800 1928 1848 1913 1837 1753 1931 1830 1911
    ## [13651] 1734 1952 1839 1956 1852 1911 1745 1918 1939 1841 1939 1857 2002 1956
    ## [13665] 1746 1903 2006 1813 1959 2013 1939 1808 1849 1957 1908 1902 1950 1829
    ## [13679] 1858 2026 1955 2010 1900 1958 2115 2023 1818 1752 2038 1842 2018 1845
    ## [13693] 2013 2022 1825 1832 1932 1913 2057 1958 1827 2023 2155 2024 1956 1902
    ## [13707] 1928 1910 1822 1908 2013 2000 2023 2117 1855 2018 2051 1906 2026 1951
    ## [13721] 2005 1825 2107 1928 2031 1841 2048 2033 2034 2114 1948 1914 1933 2118
    ## [13735] 2152 2140 2103 1937 1938 1855 1924 2113 1900 2056 1953 2043 2116 2106
    ## [13749] 2057 2047 2115 2053 2023 2000 2140 1953 2151 2023 2015 1910 2036 2105
    ## [13763] 2037 1937 2041 2133 2129 2011 1935 2159 2139 2012 1943 2029 2157 2117
    ## [13777] 1922 2133 1955 2128 2242 2138 2116 2107 2042 2205 2052 2114 2217 2114
    ## [13791] 2150 2003 2001 2220 2210 2134 2024 2150 2255 2140 2019 2151 2004 2309
    ## [13805] 2210 2232 2203 2218 2227 2044 2021 2116 2158 2123 2226 2029 2133 2101
    ## [13819] 2146 2253 2225 2012 2020 2222 2231 2049 2226 2236 2231 2120 2300 2103
    ## [13833] 2041 2240 2131 2113 2136 2237 2330   33 2255 2110 2247 2215 2216 2257
    ## [13847] 2252 2229 2332 2140 2135 2106 2229 2147 2058 2318 2256 2110 2140 2340
    ## [13861] 2153 2136   54 2225 2224 2254 2234 2132 2318 2101 2136 2251 2147    1
    ## [13875] 2230 2253 2342 2301 2342  107 2336 2331 2152 2304 2349 2348 2201 2245
    ## [13889] 2305 2347 2225 2332 2251 2157   13   41 2219 2252 2220 2229 2333 2325
    ## [13903] 2314   12 2257 2227   15 2232 2222 2247 2356 2214 2257 2324 2258   16
    ## [13917] 2311    3   41 2400   51   35 2238 2317 2251 2355 2349 2300 2303 2306
    ## [13931] 2343   38  110 2319   47 2326    5 2354   15   10 2342   56   30 2351
    ## [13945] 2346   26   24  100  103   19    1   19   14   40   17  217  453  502
    ## [13959]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [13973]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [13987]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [14001]   NA   NA   NA   NA  636  815  828 1023  845  724  643  653  818  904
    ## [14015]  851  649  742  708  832  825  805  853  756  730  945  657  928  926
    ## [14029]  659  733 1055  821  740  819  904  847  750  858  906  827  734  738
    ## [14043]  718  849  818  829  849  836  726  903  846  814  923  923 1012 1131
    ## [14057]  807 1001  930  947  939  903  937  942  937  805  828  804  906 1014
    ## [14071]  957  916  901 1014  924  750 1029  943  756  832  951  954 1027  905
    ## [14085] 1017 1004  947  804  851 1008  853 1004 1043  931  934  851 1016  955
    ## [14099]  954  940  931 1213  952  838 1018 1023 1011  921 1102 1110 1017  934
    ## [14113]  845 1020 1049  954 1050 1031 1040 1042  919 1042  924  925 1228 1033
    ## [14127] 1002 1135 1104 1000 1020 1008  900 1100  911 1139  858  856  927 1101
    ## [14141] 1043  949 1131 1016 1002 1110  952 1056 1028 1017 1100 1028  917 1310
    ## [14155] 1029 1058 1031  952 1112 1056 1019 1048 1132  922 1039 1157 1007  947
    ## [14169] 1319  955 1113 1050 1019 1036  938 1053  936  935 1029 1125  921 1113
    ## [14183] 1136 1022 1027 1112 1044 1128 1034 1329 1134 1146 1145 1001 1119 1039
    ## [14197] 1137  948 1200 1158 1338 1042 1107 1105 1151 1044 1118 1115 1201 1104
    ## [14211] 1157 1014 1014 1035 1209 1217  957 1123 1139 1128 1219 1058 1057 1211
    ## [14225] 1156 1011 1210 1513 1205 1225 1206 1106 1209 1216 1051 1019 1233 1152
    ## [14239] 1013 1128 1445 1203 1201 1057 1207 1220 1113 1131 1246 1242 1040 1017
    ## [14253] 1036 1042 1436 1030 1159 1215 1238 1207 1245 1214 1254 1136 1234 1127
    ## [14267] 1041 1211 1042 1153 1246 1130 1144 1228 1146 1106 1113 1120 1239 1257
    ## [14281] 1315 1141 1237 1228 1127 1224 1332 1314 1259 1315 1127 1342 1230 1312
    ## [14295] 1302 1214 1339 1347 1139 1149 1302 1232 1353 1302 1312 1343 1228 1351
    ## [14309] 1236 1337 1246 1240 1248 1349 1217 1355 1337 1158 1148 1415 1206 1331
    ## [14323] 1343 1355 1336 1245 1424 1213 1251 1414 1316 1203 1229 1406 1323 1257
    ## [14337] 1259 1416 1356 1417 1345 1323 1419 1434 1425 1417 1309 1418 1403 1436
    ## [14351] 1403 1321 1452 1347 1631 1310 1454 1443 1357 1456 1255 1416 1407 1248
    ## [14365] 1443 1242 1250 1446 1308 1322 1501 1313 1402 1311 1405 1321 1420 1434
    ## [14379] 1320 1447 1453 1331 1437 1451 1257 1334 1422 1521 1348 1527 1332 1402
    ## [14393] 1541 1521 1530 1533 1440 1526 1435 1540 1543 1351 1447 1347 1405 1408
    ## [14407] 1447 1404 1434 1515 1607 1534 1519 1419 1542 1600 1427 1555 1456 1532
    ## [14421] 1608 1552 1513 1611 1523 1459 1438 1819 1643 1621 1645 1613 1513 1636
    ## [14435] 1600 1625 1430 1451 1631 1632 1659 1530 1614 1649 1541 1431 1659 1444
    ## [14449] 1612 1530 1657 1705 1524 1622 1631 1655 1632 1446 1504 1713 1519 2008
    ## [14463] 1520 1718 1639 1645 1641 1719 1549 1544 1545 1724 1620 1651 1619 1523
    ## [14477] 1625 1634 1735 1537 1640 1748 1758 1653 1738 1744 1732 1545 1519 1710
    ## [14491] 1534 1748 1631 1652 1630 1745 1751 1541 1704 1726 1641 1546 1711 1739
    ## [14505] 1742 1702 1649 1624 1622 1720 1613 1607 1808 1800 1601 1613 1807 1740
    ## [14519] 1717 1748 1808 1637 1652 1641 1811 1554 1655 1639 1737 1642 1711 1820
    ## [14533] 1637 1726 1709 1823 1847 1837 1707 1635 1830 1757 1721 1808 1725 1646
    ## [14547] 1723 1802 1800 1911 1912 1848 1707 1840 1753 1726 1702 1910 1859 1820
    ## [14561] 1903 1843 1758 1706 1731 1649 1834 1914 1758 1928 1850 1916 1907 1925
    ## [14575] 2055 1840 1710 1835 1710 1921 1802 1712 1726 1759 1810 1903 1813 1840
    ## [14589] 1841 1823 1850 1838 2059 1852 1739 1735 1801 1821 1817 1750 1935 1950
    ## [14603] 1937 1911 1918 1925 1859 1940 1939 1852 1952 1840 1854 1729 1750 1933
    ## [14617] 1949 1810 1825 1728 1808 1934 1834 1855 1820 1944 1750 1924 1823 1953
    ## [14631] 1946 1939 1807 1956 1901 1936 1950 1813 1840 2151 1753 2009 1757 1946
    ## [14645] 2004 2010 2019 1835 1957 1935 1908 1947 1810 2011 1810 1832 1813 2017
    ## [14659] 1828 2010 2016 2015 1916 1916 1912 2024 2052 2339 1953 1919 1858 1830
    ## [14673] 1955 2023 1940 2034 2001 2045 2008 2035 1915 2020 2044 1838 2033 1908
    ## [14687] 2206 1921 2054 2052 2002 1952 1909 2108 2114 1904 2043 1859 2013 2057
    ## [14701] 2105 1902 2012 1922 2042 1927 2114 1946 1941 1901 2111 2049 2122 1901
    ## [14715] 1949 1939 1944 2102 1935 2143 2123 2123 2003 2118 1909 2029 2120 2022
    ## [14729] 1951 2105 2004 2124 2131 2048 2008 2016 2006 2038 2127 2039 2004 2041
    ## [14743] 2002 2108 2231 2233 1935 2116 2045 2212 2157 1941 2127 2018 2053 1947
    ## [14757] 2149 2037 2050 2021 2034 2200 2150 2120 2025 2037 2237 2200 2152 2124
    ## [14771] 2037 1950 2028 2206 2035 2020 2017 2223 2202 2126 2200 2218 2118 2028
    ## [14785] 2232   10 2130 2238 2113 2230 2215 2154 2133 2104 2223 2248 2056 2238
    ## [14799] 2125 2119 2223 2318 2249 2155 2246 2215 2255 2256 2115 2127 2128 2139
    ## [14813] 2059 2223 2241 2115 2059 2048 2251 2210 2253 2306 2307 2058 2305 2224
    ## [14827] 2248 2321 2125 2203 2116 2302 2212 2307 2115 2224 2240 2139 2227 2312
    ## [14841] 2259 2224 2201 2125 2135 2107 2259 2247 2155 2314 2323 2335  132 2156
    ## [14855] 2239 2129 2333 2245 2203 2152 2343 2335 2206 2150 2224 2247 2258 2147
    ## [14869] 2203 2306 2302 2152 2146    8 2205 2217 2248 2356 2213 2222 2234 2320
    ## [14883] 2322 2155   43 2211   11 2334 2241 2225 2226 2242   33   40 2340 2355
    ## [14897] 2350 2346   32 2301   31 2235 2354   41 2309 2252 2259   38 2305  126
    ## [14911] 2339 2330 2335 2345   27    3 2348 2400    5 2358  445  448   NA   NA
    ## [14925]   NA   NA   NA   NA   NA   NA   NA  636  800  818 1016  841  639  800
    ## [14939]  911  815  658  707  721  659  743  848  649  807  732  715  910  749
    ## [14953]  720  821  923  745  735  718  903  824  908 1122  829  823  743  731
    ## [14967]  912  900  925  910  926  717  804  907  850  835  829  935  839  901
    ## [14981]  847  723  807  758  844  925  953  853 1128  847  758  937  946  930
    ## [14995]  943  901  923  854  758  927  904  907  742  945  902  831  811  951
    ## [15009]  942 1026  952  950 1020 1008  951 1016  816  957  808  835 1020 1009
    ## [15023]  916  923  803  841 1008 1002  926 1010  848  949 1012  845 1035 1231
    ## [15037]  923 1025 1048  853 1035 1046 1003  826 1037 1044 1023  947 1047  918
    ## [15051] 1026  841 1004 1036 1030  959 1031  919  856 1031  924 1100 1053 1014
    ## [15065] 1232 1108  908 1043  934  845  907 1110 1058 1020 1019 1006  905 1123
    ## [15079] 1106 1003 1113 1049 1125 1037 1053  908  934 1101 1023 1024 1003  911
    ## [15093]  903 1034 1119  955  958  944  911 1107 1258 1052 1049  954  949 1007
    ## [15107]  929 1040 1007 1128  929  942 1122 1012 1011 1104 1007 1114  951 1132
    ## [15121] 1343 1204 1034 1043  956 1111 1122 1026 1143 1102 1143 1007  947  947
    ## [15135] 1332 1010 1037 1103 1020 1156 1159 1203 1115  954 1005 1016 1107 1051
    ## [15149] 1149 1208 1116 1213 1130 1116 1159 1217 1007 1228 1202 1133 1218 1057
    ## [15163] 1140 1418 1234 1214 1038 1051 1057 1127 1219 1214 1225 1014 1238 1153
    ## [15177] 1129 1038 1120 1232 1424 1050 1048 1121 1232 1203 1219 1239 1207 1110
    ## [15191] 1231 1107 1054 1118 1123 1218 1308 1224 1429 1108 1135 1103 1058 1243
    ## [15205] 1126 1126 1222 1327 1236 1238 1116 1311 1120 1123 1334 1314 1429 1325
    ## [15219] 1217 1319 1326 1208 1257 1324 1332 1140 1215 1321 1251 1354 1300 1318
    ## [15233] 1354 1408 1231 1334 1200 1240 1240 1352 1401 1243 1201 1404 1216 1349
    ## [15247] 1148 1343 1306 1239 1417 1419 1209 1635 1229 1217 1306 1307 1343 1417
    ## [15261] 1425 1403 1305 1309 1318 1418 1416 1432 1315 1254 1419 1429 1617 1347
    ## [15275] 1339 1449 1450 1351 1300 1307 1358 1435 1444 1308 1404 1447 1342 1245
    ## [15289] 1439 1440 1251 1322 1308 1255 1454 1414 1244 1447 1353 1334 1344 1439
    ## [15303] 1311 1308 1331 1518 1313 1306 1331 1537 1352 1518 1449 1506 1402 1356
    ## [15317] 1553 1539 1527 1435 1454 1347 1333 1512 1606 1553 1340 1459 1545 1509
    ## [15331] 1542 1558 1357 1443 1454 1351 1409 1539 1527 1415 1451 1547 1431 1556
    ## [15345] 1433 1427 1520 1422 1606 1549 1402 1449 1612 1635 1439 1607 1459 1614
    ## [15359] 1453 1623 1620 1809 1512 1627 1629 1639 1640 1658 1444 1630 1701 1932
    ## [15373] 1709 1538 1514 1714 1718 1547 1621 1642 1500 1506 1748 1521 1641 1517
    ## [15387] 1708 1632 1503 1601 1510 1708 1629 1621 1555 1644 1709 1604 1710 1646
    ## [15401] 1740 1608 1645 1542 1600 1730 1742 1529 1702 1650 1758 1637 1737 1734
    ## [15415] 1657 1614 1732 1740 1633 1745 1550 1819 1646 1755 1611 1817 1716 1627
    ## [15429] 1643 1636 1653 1606 1601 1808 1628 1616 1742 1632 1810 1729 1817 1743
    ## [15443] 1830 1626 1656 1640 1715 1937 1818 1643 1734 1836 1801 1730 1648 1806
    ## [15457] 1738 1825 1843 1721 1757 1650 1713 1758 1713 1731 1654 1740 1858 1841
    ## [15471] 1739 1714 1847 1858 1907 1726 1856 1755 1658 1800 1841 1754 1916 1709
    ## [15485] 1833 1835 1905 1805 1734 1731 1757 1806 2048 1726 1741 1755 1808 1937
    ## [15499] 1656 1918 1721 1845 1740 1712 1759 1913 1832 2124 1718 1929 1831 1813
    ## [15513] 1752 1934 1838 1704 1746 1706 1731 1805 1925 1904 1923 1807 1844 1812
    ## [15527] 1846 1819 1914 1810 1930 1930 1931 2001 1959 1910 1747 1955 1957 1834
    ## [15541] 1942 1922 1917 1848 1825 1855 2004 1934 1930 2002 1855 1801 1953 2007
    ## [15555] 1918 1954 1747 1906 1820 1817 1827 1918 1936 1932 1831 2007 1933 1900
    ## [15569] 1828 2032 2203 2035 1833 2011 1941 1811 1958 2023 2009 1949 1838 1827
    ## [15583] 2005 2019 1844 2023 1924 1823 2036 2021 2035 2010 2021 2047 1922 2001
    ## [15597] 1938 1852 2051 2024 1912 2155 1911 2018 2023 2059 2055 1834 2018 2058
    ## [15611] 2034 1919 1957 1943 1922 1919 1853 1932 1919 1906 2102 2054 1934 2051
    ## [15625] 2052 2208 2055 2046 1934 2119 1919 2003 1859 1957 2113 1907 1955 1944
    ## [15639] 2050 1940 2106 1952 2014 2128 1924 2117 1957 1928 1952 1916 2100 1909
    ## [15653] 2031 2031 2149 2155 2114 2126 2046 2100 2134 2138 1935 2022 1939 1941
    ## [15667] 1952 2152 1957 2121 1956 2018 2214 2007 2011 2030 2226 2200 2010 2157
    ## [15681] 2105 2056 2200 2156 2152 2136 2153 2201 2103 1956 2118 2122 2051 2027
    ## [15695] 2146 2340 2157 2208 2011 2016 2059 2157 2235 2219 2029 2111 2226 2052
    ## [15709] 2052 2038 2142 2201 2152 2224 2036 2102 2218 2048 2233 2138 2033 2147
    ## [15723] 2225 2237 2221 2236 2237 2157 2108 2217 2123 2133 2159 2042 2248 2144
    ## [15737] 2102 2209 2055 2236 2134 2108 2131 2241 2132 2141 2220 2235 2132 2043
    ## [15751] 2058 2131 2255 2322 2301 2123 2158 2258 2100 2115 2124 2105 2154 2218
    ## [15765] 2250 2058 2307 2258 2254 2118 2128 2223 2122 2147 2142 2306 2156 2327
    ## [15779] 2251 2117 2312 2329  113   18 2136 2204 2149 2323 2234 2143 2325 2212
    ## [15793] 2311 2141 2307 2201 2230 2146 2233 2200 2204 2339 2148 2252 2220 2233
    ## [15807] 2205 2315 2306 2243 2342    4 2324 2344 2204 2241 2234   16 2232 2339
    ## [15821]   22 2237   15 2255 2247   27 2243 2302   21 2255 2250   51 2254 2320
    ## [15835]  127 2355 2343 2351 2348 2355    5  100  103  432  439   NA   NA   NA
    ## [15849]   NA   NA   NA   NA   NA   NA   NA  634  859 1009  842  824  819  903
    ## [15863]  749  749  904  649  858  846  723  854  915  711  743  859  902  737
    ## [15877]  713  705  807  921  740  913  857 1050  818  835  857  828  910  715
    ## [15891]  902  857  832  819  758 1131  924  757  915  726  941  949  919  931
    ## [15905]  815  753  808  944  756  858  942  808 1015  952 1014  906  955  826
    ## [15919] 1002  914  835  950  956 1007 1005  835 1147 1019 1018 1026  959  928
    ## [15933]  928 1032 1017  935  837 1212 1045  939 1004 1016 1042 1025 1018 1101
    ## [15947] 1050  921 1226  853  925 1050 1101 1030 1035  855 1114  952 1051 1132
    ## [15961]  904 1003  903 1028 1007 1028 1031 1058 1103  910 1014  938 1250  958
    ## [15975] 1046 1107  951  941 1114 1040  950 1259 1016  926  927 1134  957 1044
    ## [15989] 1006 1136  947  954 1136 1313 1100 1109 1119 1135  943 1057 1121 1008
    ## [16003] 1011 1102 1207  947 1214  945 1028  950 1038 1139 1630 1123 1140 1026
    ## [16017] 1027 1044 1158 1158 1055 1116 1458 1152 1039 1113 1110 1128 1207 1023
    ## [16031] 1119 1001 1209 1016 1207 1216 1215 1013 1129 1059 1138 1118 1028 1212
    ## [16045] 1411 1415 1215 1057 1200 1034 1106 1203 1145 1053 1047 1221 1132 1420
    ## [16059] 1216 1100 1229 1232 1103 1237 1241 1039 1117 1046 1042 1102 1245 1123
    ## [16073] 1232 1205 1222 1135 1313 1242 1106 1335 1315 1301 1244 1318 1131 1334
    ## [16087] 1333 1335 1320 1131 1318 1337 1221 1153 1236 1320 1337 1228 1357 1332
    ## [16101] 1401 1158 1400 1323 1206 1405 1402 1207 1252 1405 1250 1403 1336 1257
    ## [16115] 1409 1346 1303 1423 1325 1237 1416 1422 1324 1443 1419 1459 1243 1313
    ## [16129] 1331 1453 1250 1443 1355 1326 1257 1333 1413 1446 1333 1511 1259 1420
    ## [16143] 1450 1329 1309 1435 1315 1307 1332 1505 1330 1515 1526 1549 1446 1446
    ## [16157] 1419 1601 1348 1335 1527 1536 1342 1502 1540 1544 1536 1407 1412 1434
    ## [16171] 1403 1604 1606 1436 1549 1357 1543 1523 1540 1420 1744 1558 1412 1503
    ## [16185] 1534 1417 1617 1500 1444 1620 1615 1546 1421 1815 1612 1614 1632 1629
    ## [16199] 1622 1850 1618 1621 1419 1634 1605 1650 1528 1458 1619 1650 1701 1645
    ## [16213] 1510 1611 1545 1631 1656 1500 1618 1512 1536 1743 1646 1716 1630 1755
    ## [16227] 1547 1756 1621 1734 1552 1615 1642 1735 1639 1603 1630 1736 1634 1653
    ## [16241] 1629 1617 1732 1743 1738 1627 1738 1626 1727 1722 1624 1622 1713 1608
    ## [16255] 1805 1754 1744 1616 1741 1809 1710 1636 1650 1616 1813 1740 1628 1631
    ## [16269] 1754 1625 1620 1826 1650 1706 1620 1635 1638 1657 1629 1633 1751 1655
    ## [16283] 1811 1711 1840 1656 1744 1837 1856 1653 1734 1658 1741 1847 1806 1649
    ## [16297] 1905 1812 1821 1751 1752 1854 1811 1750 1730 1847 1850 1837 1856 1842
    ## [16311] 1900 1725 1850 1822 1913 1741 1900 1704 1735 2104 1933 1907 2059 1731
    ## [16325] 1835 1714 1806 1757 1750 1722 1936 1937 1902 1756 1746 1918 1852 1733
    ## [16339] 1808 1800 1920 1922 1923 1939 1913 1755 1850 1809 1813 1933 1939 2002
    ## [16353] 1833 1816 1944 1749 1758 1749 1946 1935 1958 2000 1918 1750 1849 1939
    ## [16367] 1806 1949 1958 1937 1759 1942 1802 1934 1920 1955 1852 2020 1902 1956
    ## [16381] 1924 2150 2008 1839 1952 1948 1834 2005 2013 2020 2048 1845 2005 1942
    ## [16395] 1857 2015 2039 2025 2030 2102 2102 1852 2003 2041 1847 2115 1903 1942
    ## [16409] 2038 2038 1901 1915 1925 2048 2057 2116 2101 2112 2035 1933 2007 2057
    ## [16423] 1941 2119 2116 1916 1926 2026 2044 1941 2202 2013 2033 2210 2101 2128
    ## [16437] 2143 1950 2052 2023 2005 2205 2148 2029 2154 2104 2120 2224 2218 2049
    ## [16451] 2030 2200 2218 2022 2007 2157 2026 2231 2155 2206 2226 2222 2031 2207
    ## [16465] 2138 2113   23 2229 2205 2226 2144 2226 2233 2056 2222 2211 2137 2310
    ## [16479] 2107 2259 2142    2 2044 2250 2132 2202 2253 2136 2102 2114 2150 2136
    ## [16493] 2202 2128 2122 2125 2324  113 2224 2324 2145 2306 2225 2243 2343    1
    ## [16507] 2231 2220 2214   17 2234 2240 2231   31   16   36 2254   39 2250 2343
    ## [16521] 2358 2352    9   15 2350 2348  456  437   NA  832  850  911  700  931
    ## [16535]  818  913  816  910  908  917 1048  857  900  925 1052  841  912 1203
    ## [16549]  807  903  821  811  924  955  829  801  924 1124  928  932  821 1006
    ## [16563]  935  824  835  811  931  914 1022 1021 1043 1013  959  930  954  949
    ## [16577]  943  835  829  832 1019  948 1025 1017 1149 1027 1013 1005 1008 1014
    ## [16591] 1022 1034 1036 1059 1047  827  833 1033 1034  857 1033 1223 1124  901
    ## [16605] 1111 1103  907 1037  951  944 1050 1028 1020 1031 1130 1127 1107  859
    ## [16619] 1125  918 1325  956 1020 1103  940 1025 1025  902  935  935 1052  952
    ## [16633] 1041 1110  916 1002 1006 1003 1305 1012 1123  957 1140 1100  954 1119
    ## [16647]  942 1128  944 1047 1329 1123  944  955 1039 1157 1000 1106  938 1153
    ## [16661] 1128 1326 1216 1039 1018 1056 1208 1159 1055 1156 1113 1059 1148 1047
    ## [16675] 1202 1025 1157 1227 1119 1152 1218 1135 1452 1230 1106 1011 1213 1402
    ## [16689] 1040 1057 1049 1217 1018 1211 1020 1211 1158 1410 1216 1040 1040 1214
    ## [16703] 1228 1234 1218 1224 1112 1233 1059 1043 1053 1326 1245 1117 1100 1210
    ## [16717] 1238 1151 1222 1302 1105 1224 1248 1332 1321 1251 1118 1256 1112 1205
    ## [16731] 1315 1125 1235 1314 1327 1146 1329 1319 1315 1143 1338 1239 1252 1136
    ## [16745] 1414 1358 1321 1335 1207 1343 1400 1341 1214 1211 1426 1354 1355 1316
    ## [16759] 1153 1418 1242 1444 1204 1331 1409 1258 1411 1249 1356 1338 1253 1610
    ## [16773] 1248 1442 1252 1444 1317 1327 1415 1318 1332 1422 1354 1425 1421 1438
    ## [16787] 1437 1304 1243 1438 1439 1307 1408 1441 1600 1424 1252 1323 1440 1423
    ## [16801] 1249 1306 1401 1354 1451 1524 1300 1457 1317 1302 1330 1421 1306 1311
    ## [16815] 1336 1409 1534 1336 1414 1416 1452 1520 1520 1541 1527 1615 1526 1334
    ## [16829] 1421 1527 1551 1336 1533 1409 1406 1535 1458 1444 1438 1438 1559 1546
    ## [16843] 1625 1510 1601 1407 1556 1452 1522 1358 1420 1504 1452 1513 1425 1623
    ## [16857] 1425 1636 1454 1631 1424 1809 1543 1452 1620 1621 1620 1705 1622 1643
    ## [16871] 1546 1442 1646 1558 1705 1618 1442 1554 1445 1703 1511 1616 1453 1725
    ## [16885] 1649 1538 1659 1609 1456 1544 1714 1628 1556 1623 1643 1552 1639 1759
    ## [16899] 2043 1559 1731 1729 1816 1545 1724 1600 1544 1645 1704 1728 1745 1742
    ## [16913] 1536 1747 1642 1751 1802 1645 1644 1607 1645 1644 1759 1634 1805 1722
    ## [16927] 1642 1640 1907 1726 1754 1555 1649 1643 1724 1802 1833 1601 1801 1813
    ## [16941] 1749 1626 1637 1824 1700 1802 1635 1639 1753 1824 1712 1649 1750 1756
    ## [16955] 1655 1630 1845 1653 1723 1733 1847 1829 1654 1850 1700 1831 1830 1828
    ## [16969] 1707 1733 1721 1733 1806 1641 1804 1805 1710 1815 1841 1648 2037 1640
    ## [16983] 1839 1740 1752 1920 1752 1921 1804 1855 1855 1830 1859 1743 1707 1825
    ## [16997] 1910 2044 1852 1749 1915 1850 1859 1753 1923 1734 1731 1849 1756 1927
    ## [17011] 1916 1819 1838 1912 1741 1750 1738 1917 1831 1851 1720 1955 1855 1914
    ## [17025] 1729 2005 1945 1856 1756 1914 1947 1938 1838 1812 2004 1809 1930 1935
    ## [17039] 1846 1844 1847 1947 1839 1946 1836 1955 2019 1814 1939 1742 2002 1749
    ## [17053] 1822 2015 2021 1848 2022 1913 2022 2018 2013 1808 1957 2018 2141 2009
    ## [17067] 2026 1812 1914 1905 2019 1958 2019 2016 2001 1959 1859 1833 2021 2053
    ## [17081] 2000 2024 1905 2016 2042 1918 1921 1908 2043 2007 1945 1855 1837 1859
    ## [17095] 1958 2118 1904 2015 1913 1926 1922 2114 2110 2044 2118 1914 1918 2029
    ## [17109] 2032 2108 2118 1909 2024 2055 2004 1924 1908 1853 2143 1929 1942 2011
    ## [17123] 2015 2143 1858 2029 1946 2203 1948 2039 2110 2021 1935 2030 1925 2129
    ## [17137] 1929 2016 2103 2109 2029 1957 2202 2222 2207 2205 2106 2210 2007 1955
    ## [17151] 2007 2118 2151 2047 2106 2027 2156 2027 2242 2240 2050 2046 2106 2025
    ## [17165] 2135 2208 2113   18 2155 2242 2247 2051 2029 2101 2144 2324 2012 2022
    ## [17179] 2206 2044 2231 2252 2203 2043 2214 2038 2103 2111 2230 2214 2307 2327
    ## [17193] 2235 2119 2221 2234 2049 2217 2140 2041 2118 2241 2321 2111 2156 2234
    ## [17207] 2230 2213 2114 2057 2156 2250 2144 2048 2225 2337 2244 2057 2303 2142
    ## [17221] 2310 2341 2257 2117 2221 2229 2140 2341 2204 2301 2144 2156 2247 2305
    ## [17235] 2305 2201 2302 2209 2157 2226 2324 2248 2320 2246 2125 2126 2346 2159
    ## [17249] 2339 2157 2158 2349 2220  141 2218    5 2334 2150 2157 2305 2235 2242
    ## [17263] 2211 2211 2307 2223   14 2147 2339 2229 2336 2301 2231 2249 2208   23
    ## [17277]   45    9 2303   33   21   27 2229 2234 2238   33 2348 2255 2302 2331
    ## [17291]   46   55   14 2316 2338  118 2336 2347    4    4 2351  118    6   26
    ## [17305]   18  428  230  426   53  238  223   NA   NA   NA   NA  646  806  832
    ## [17319]  845  751  636  853 1020  852  755  721  909  851  641  842  855  659
    ## [17333]  734  822  920  718  713  737  807  739  911  654  825  805  901  744
    ## [17347]  808  732 1041  834  734  843  736  930  856  716  846  811  831  923
    ## [17361]  905  942  824  932  759  805  849  805  720 1123  938  819  933  905
    ## [17375]  927  918  933 1007 1005  814  844  947  937  908  915  753  951  853
    ## [17389]  933 1015 1003  946  928 1025 1008  833  944  747  944  954 1012  754
    ## [17403]  951 1024  840  846  956 1022 1026  849 1029 1019  942  847 1018 1144
    ## [17417] 1028 1023 1043 1036 1025 1028  858 1010  944  833 1043 1026 1108 1043
    ## [17431]  932 1044 1042 1036 1105  916 1049 1038 1042 1225  959 1100  910  938
    ## [17445] 1021 1106 1051  911  857 1111 1108 1045  947  903 1051 1147 1051  957
    ## [17459] 1234  853 1004 1055 1102 1008  949 1034  907  940 1113 1015  941 1059
    ## [17473] 1039 1034 1033 1006  953  912 1247 1010 1025  924 1038  959 1008 1052
    ## [17487] 1016 1134 1120 1127 1017  929  923 1101  949 1310 1009 1109 1141 1134
    ## [17501] 1127 1134 1021 1144 1130  944 1020  942 1028  932 1204 1017 1318  948
    ## [17515] 1012  938 1155 1145 1045 1459 1041 1155 1107 1151 1202 1101 1122 1019
    ## [17529] 1053 1128 1245 1138 1009 1158 1159 1221 1203 1208 1049 1125 1239 1201
    ## [17543] 1222 1226 1009 1353 1132 1051 1245 1148 1214 1228 1220 1348 1008 1040
    ## [17557] 1145 1117 1200 1048 1223 1034 1210 1037 1225 1151 1244 1248 1121 1121
    ## [17571] 1157 1105 1147 1128 1310 1109 1258 1238 1044 1146 1220 1321 1303 1225
    ## [17585] 1058 1224 1107 1303 1224 1128 1238 1129 1248 1112 1311 1326 1220 1322
    ## [17599] 1332 1345 1214 1252 1329 1206 1134 1345 1220 1339 1332 1240 1300 1208
    ## [17613] 1348 1247 1341 1354 1356 1230 1145 1345 1146 1155 1341 1401 1358 1326
    ## [17627] 1245 1416 1251 1212 1307 1222 1236 1202 1406 1309 1236 1339 1403 1423
    ## [17641] 1314 1318 1401 1427 1548 1306 1423 1425 1327 1412 1328 1258 1350 1446
    ## [17655] 1445 1247 1430 1440 1239 1449 1403 1343 1338 1248 1245 1517 1448 1335
    ## [17669] 1315 1259 1425 1301 1517 1510 1350 1451 1337 1338 1534 1340 1514 1347
    ## [17683] 1520 1352 1343 1323 1337 1402 1528 1342 1443 1429 1535 1436 1612 1342
    ## [17697] 1450 1604 1603 1436 1338 1544 1507 1443 1551 1429 1547 1351 1415 1401
    ## [17711] 1431 1404 1543 1533 1559 1520 1419 1425 1628 1612 1544 1538 1551 1414
    ## [17725] 1403 1653 1525 1424 1622 1630 1630 1515 1624 1600 1513 1645 1655 1557
    ## [17739] 1412 1644 1651 1943 1654 1631 1657 1603 1543 1636 1618 1502 1720 1724
    ## [17753] 1619 1526 1642 1646 1833 1510 1646 1727 1716 1716 1500 1729 1641 1727
    ## [17767] 1647 1552 1507 1715 1649 1613 1519 1532 1609 1546 1745 1743 1743 1622
    ## [17781] 1813 1745 1621 1531 1536 1649 1643 1809 1710 1635 1813 1723 1636 1606
    ## [17795] 1622 1543 1608 1637 1759 1648 1804 1815 1620 1757 1750 1628 1603 1810
    ## [17809] 1827 1751 1714 1602 1712 1704 1730 1632 1813 1645 1837 1758 1611 1646
    ## [17823] 1739 1610 1728 1638 1705 1848 1641 1805 1830 1808 1840 1804 1657 1749
    ## [17837] 1628 1830 1712 1742 1754 1905 1718 1833 1736 1843 1705 1851 1922 1809
    ## [17851] 1859 1755 1726 1815 1837 1642 2017 1920 1751 1942 1811 1721 2048 1745
    ## [17865] 1724 1827 1905 1831 1714 1825 1919 1748 1939 1917 1715 1906 1712 1723
    ## [17879] 1918 1839 1921 1837 1840 1820 1728 1839 1757 1902 1814 1834 1755 1820
    ## [17893] 1705 1801 1737 2009 1859 1930 1726 1808 1906 1825 1854 1816 1816 1725
    ## [17907] 2031 1933 1732 1944 1801 1839 1809 1828 2005 1757 1838 1952 1938 1950
    ## [17921] 1932 1826 1951 1907 1937 1856 2012 1915 1851 1923 1934 1818 1859 2004
    ## [17935] 1939 1831 1758 1831 2005 2028 1945 1756 1813 1930 2028 2124 1805 1923
    ## [17949] 2004 1959 2127 2025 2023 2011 1831 1820 1831 1956 2048 2033 1907 2032
    ## [17963] 1811 1814 2025 1838 2040 2007 2009 1854 2009 2033 1857 1930 2054 1923
    ## [17977] 1835 2058 1856 2010 2015 1954 2024 1912 2035 1928 2034 2032 2052 2000
    ## [17991] 2040 1852 1939 1842 1920 1908 1933 1847 1838 2047 2022 2006 2111 1903
    ## [18005] 2113 2109 2044 2052 1850 1859 1903 2015 2057 2108 1902 2059 2108 1930
    ## [18019] 2018 1945 2121 1956 2058 2038 2051 2124 2055 2008 2018 1955 2123 2122
    ## [18033] 1926 1957 2046 2133 2059 1920 1953 2206 2028 2142 2031 1928 2138 2038
    ## [18047] 2153 2212 2031 2010 2153 2020 2144 2131 1943 2143 2148 2026 2030 2154
    ## [18061] 2216 1958 2126 2324 2034 2038 2107 2058 2026 2010 2046 2240 2029 2014
    ## [18075] 2207 2212 2221 2211 2132 2015 2101 2114 2026 2023 2058 2218 2222 2222
    ## [18089] 2156 2049 2216 2140 2202 2050 2330 2215 2238 2240 2035 2146 2226 2231
    ## [18103] 2242 2258 2032 2217 2212 2105 2247 2042 2230 2251 2301 2123 2122 2052
    ## [18117] 2050 2303 2249 2118 2241 2051 2118 2200 2323 2131 2224 2137 2209 2237
    ## [18131] 2345 2234 2256 2230 2234 2304 2200 2143 2307 2344 2311 2224 2328   17
    ## [18145] 2349 2340  101 2210 2326 2215 2205    8 2139 2143 2221 2230   17 2330
    ## [18159] 2313 2334 2234   17   16 2302 2239 2231 2310 2203   19 2211 2204 2238
    ## [18173] 2155   40    4 2244 2227 2301   10 2305 2227 2257   10   12 2215   16
    ## [18187] 2303 2217 2216  107   17 2339  103 2307 2232 2302   54 2330   42 2308
    ## [18201]  112 2311   49 2249   46 2313 2338 2321 2338  140 2343    6 2348   13
    ## [18215]   36   46   45  423  433   NA   NA   NA   NA   NA   NA   NA   NA  452
    ## [18229]  646  811  827  829 1013  651  645  905  911  649  915  745  717  923
    ## [18243]  714  716  646  729  846  836  917  808  910  912  759  911  736  800
    ## [18257]  715 1047  911  831  844  857  735  735  939  732  718  845  829  922
    ## [18271]  849  815  928  951  932  757  843  805 1127  926  846  742  901  903
    ## [18285]  813  809  733  835  852  956  944  945  808  942  901  745  859  939
    ## [18299] 1011  821 1023 1001  829  950  755  801  934  958 1024  809  951 1010
    ## [18313]  933 1001  957 1031 1028 1003  836 1021 1013  952 1037  847 1029 1033
    ## [18327]  942 1154 1031 1044  906  848 1047 1018 1025 1034 1031  950  918 1042
    ## [18341] 1040 1025 1105  957  844 1053 1054 1039  926  927  909 1102 1230  943
    ## [18355] 1043 1055  959  902  921 1052 1139 1010  921 1048  900 1007  902 1052
    ## [18369]  909 1004 1142 1147 1105  956 1042 1028 1119  948 1055 1132 1028 1053
    ## [18383] 1013  914 1014 1148 1017 1017 1126 1134 1319  941  941 1004 1003  921
    ## [18397] 1107 1335 1156 1120 1036 1021 1029 1046 1145 1156  950 1202 1111 1022
    ## [18411] 1011 1131  950 1039 1118 1005 1221  943 1020 1158 1139  946 1352 1059
    ## [18425] 1153 1223 1118 1148 1047 1222 1055 1131 1114 1144 1506 1208 1015 1020
    ## [18439] 1149 1033 1217 1225 1217 1155 1212 1123 1048 1133 1230 1024 1207 1125
    ## [18453] 1134 1239 1101 1215 1034 1235 1413 1113 1229 1125 1242 1140 1127 1223
    ## [18467] 1237 1221 1135 1132 1022 1439 1202 1131 1040 1102 1054 1301 1059 1236
    ## [18481] 1428 1249 1204 1312 1131 1054 1221 1107 1235 1123 1130 1105 1304 1221
    ## [18495] 1134 1256 1311 1239 1237 1338 1238 1129 1130 1221 1234 1123 1226 1348
    ## [18509] 1329 1342 1221 1340 1259 1323 1351 1344 1156 1158 1307 1333 1253 1415
    ## [18523] 1226 1321 1242 1405 1232 1418 1151 1351 1418 1206 1252 1202 1414 1413
    ## [18537] 1421 1212 1241 1304 1416 1259 1246 1347 1322 1557 1420 1346 1353 1323
    ## [18551] 1427 1424 1448 1426 1328 1253 1333 1428 1319 1444 1432 1506 1411 1320
    ## [18565] 1440 1447 1406 1449 1336 1247 1339 1455 1429 1419 1513 1451 1359 1359
    ## [18579] 1255 1313 1435 1345 1351 1517 1331 1441 1322 1330 1301 1322 1530 1333
    ## [18593] 1419 1308 1528 1413 1334 1542 1529 1349 1341 1419 1544 1527 1556 1426
    ## [18607] 1428 1530 1356 1515 1547 1501 1523 1553 1410 1543 1348 1625 1346 1351
    ## [18621] 1416 1557 1537 1603 1442 1539 1500 1530 1404 1354 1602 1425 1434 1459
    ## [18635] 1602 1501 1500 1423 1420 1404 1358 1413 1625 1625 1603 1552 1641 1433
    ## [18649] 1429 1517 1653 1620 1653 1530 1655 1643 1724 1608 1620 1653 1453 1445
    ## [18663] 1657 1835 1510 1453 1628 1657 1708 1536 1714 1551 1712 1559 1724 1609
    ## [18677] 1527 1534 1618 1544 1647 1736 1753 1714 1620 1532 2013 1739 1650 1539
    ## [18691] 1642 1540 1634 1757 1830 1703 1629 1726 1754 1537 1732 1827 1538 1558
    ## [18705] 1715 1636 1640 1705 1722 1619 1627 1808 1749 1615 1708 1620 1547 1630
    ## [18719] 1622 1819 1803 1812 1723 1711 1620 1704 1708 1822 1634 1758 1843 1655
    ## [18733] 1744 1747 1834 1758 1749 1816 1649 1702 1830 1847 1653 1741 1807 1716
    ## [18747] 1822 1652 1852 1850 1754 1831 1818 1715 1850 1719 1702 1649 1706 1830
    ## [18761] 1727 1919 1715 1739 1854 2030 1806 1820 1825 1902 1807 1648 1801 1820
    ## [18775] 1931 1825 1729 1752 1849 1814 1849 1720 1929 2001 1807 2046 1937 1907
    ## [18789] 1736 1924 1840 1812 1757 1722 1957 1814 1821 1733 1807 1801 1925 1904
    ## [18803] 1836 1947 1916 1845 1918 1951 1930 1820 1905 1805 1950 1937 1841 1742
    ## [18817] 1806 1804 1917 1840 1811 1832 1844 1729 1932 1946 2001 1818 1937 1842
    ## [18831] 1830 1926 1748 1910 2013 1907 2140 1940 2007 1810 2037 1827 1753 2020
    ## [18845] 2007 2016 1754 2021 1821 1936 2037 1821 2027 1943 1959 2003 1915 1829
    ## [18859] 1912 1818 1910 2009 2015 1930 2023 2028 1858 1928 1916 2016 1952 2046
    ## [18873] 2040 2037 2105 2032 2036 1837 1925 2019 2051 1924 2039 2034 2110 2021
    ## [18887] 1917 1910 2027 2110 2043 2003 2130 2039 1941 2107 2047 2128 2113 2009
    ## [18901] 1905 2050 2120 1934 2005 1919 1858 2056 1924 1914 1859 2049 2029 1928
    ## [18915] 1948 2021 1938 1925 2138 1948 2229 2115 1919 1945 2134 2055 2018 1954
    ## [18929] 2057 2139 2200 2211 2136 2105 1936 2118 2240 2000 1954 2051 2138 2047
    ## [18943] 2022 2012 2024 2219 2016 2152 2208 2139 2037 2020 2057 2023 2102 2158
    ## [18957] 2001 2122    6 2116 2010 2141 2207 2034 2205 2036 2245 2214 2157 2019
    ## [18971] 2215 2026 2154 2226 2228 2113 2101 2300 2234 2053 2132 2147 2142 2120
    ## [18985] 2240 2114 2126 2158 2252 2241 2213 2240 2124 2127 2223 2111 2303 2303
    ## [18999] 2306 2102 2118 2057 2140 2315 2240 2137 2216 2229 2057 2312 2217 2317
    ## [19013] 2249 2306 2129 2110 2136 2212 2301 2311 2200 2206 2113 2211 2112 2220
    ## [19027] 2214 2327 2252 2203 2123 2208 2256 2329 2120 2216 2315 2245 2300 2126
    ## [19041] 2310  117 2150 2140 2342 2329 2208 2144 2228 2337 2227 2247 2303 2221
    ## [19055] 2250 2148 2158 2205 2216 2208 2359 2156 2352 2217 2206 2247 2230 2229
    ## [19069] 2249   23 2223 2339 2217 2338   51 2309 2221 2312 2304   38 2239 2354
    ## [19083]   13 2244 2302    7   46 2326 2330 2317 2323 2335 2400 2344   38   50
    ## [19097]  133 2348  156   17   11    1 2344 2400 2352    7    1  141  218   25
    ## [19111]  432  142   NA   NA   NA   NA   NA  253  636  757  810 1019  857  948
    ## [19125]  817  810  645  650  902  652  723  707  717  749  848  752  914  755
    ## [19139]  706  917  815  850  705  735  829  913  735 1047  826  842  837  738
    ## [19153]  827  822  812 1121  825  837  744  917  917  808  943  849 1003  930
    ## [19167]  809 1004  923  931  830  934  915  730  836  909  753  918  902  855
    ## [19181]  919  922  804  833 1037 1007 1013  822  823  958  938 1026  837 1057
    ## [19195]  800 1029  834 1005  805  938  918  951 1023  941 1018 1022  923  924
    ## [19209] 1011 1033 1053 1023 1027  959 1033  919  854 1046  950 1102  945 1049
    ## [19223] 1018 1009  840 1126 1044 1218 1059 1024  920  901  945  942 1108  955
    ## [19237] 1043 1024  852 1055  928  957 1230  904  901  900  921 1038 1038 1019
    ## [19251] 1038 1042 1132 1143 1024  959  900  909 1032 1105 1108 1004 1025  921
    ## [19265]  945 1409  946  947 1117  936 1005 1054 1003  930  954 1026 1023  936
    ## [19279] 1018 1015 1107  944 1007 1007 1137 1134 1059 1003 1117 1052 1021 1140
    ## [19293] 1023 1126 1205 1116 1042 1020 1049 1001 1135 1146 1105  958 1338 1322
    ## [19307] 1001 1139 1153 1155 1141 1055 1111 1136 1105 1017 1121  957 1202 1033
    ## [19321] 1214 1104 1049 1119 1152 1201 1010 1014 1149 1159 1048 1208 1044 1134
    ## [19335] 1235 1045 1148 1154 1412 1218 1209 1217 1011 1050 1135 1227 1146 1226
    ## [19349] 1201 1046 1144 1241 1210 1415 1047 1045 1229 1241 1247 1113 1235 1144
    ## [19363] 1214 1227 1133 1235 1119 1042 1235 1105 1118 1219 1241 1119 1136 1256
    ## [19377] 1206 1059 1109 1124 1248 1231 1213 1226 1114 1305 1149 1314 1309 1238
    ## [19391] 1325 1156 1308 1209 1141 1325 1115 1215 1234 1259 1404 1359 1233 1322
    ## [19405] 1413 1337 1231 1527 1230 1253 1652 1229 1313 1324 1354 1349 1329 1143
    ## [19419] 1353 1424 1200 1353 1204 1316 1247 1210 1427 1217 1344 1231 1218 1251
    ## [19433] 1211 1400 1435 1321 1600 1246 1257 1348 1251 1320 1359 1421 1441 1426
    ## [19447] 1410 1400 1305 1302 1329 1323 1448 1353 1410 1412 1436 1250 1348 1334
    ## [19461] 1428 1421 1324 1239 1401 1248 1506 1308 1503 1323 1305 1505 1459 1313
    ## [19475] 1443 1456 1524 1444 1426 1403 1358 1527 1258 1444 1317 1352 1331 1418
    ## [19489] 1600 1412 1527 1404 1352 1521 1447 1334 1423 1600 1408 1459 1545 1547
    ## [19503] 1436 1559 1531 1358 1447 1546 1630 1526 1508 1413 1400 1433 1546 1524
    ## [19517] 1538 1524 1453 1554 1400 1537 1427 1606 1627 1459 1616 1617 1444 1640
    ## [19531] 1437 1422 1515 1555 1557 1613 1541 1812 1657 1547 1631 1938 1646 1709
    ## [19545] 1604 1605 1705 1716 1734 1615 1553 1637 1452 1651 1449 1627 1530 1531
    ## [19559] 1605 1557 1651 1528 1618 1638 1628 1603 1709 1555 1521 1710 1650 1649
    ## [19573] 1643 1726 1703 1533 1704 1749 1633 1835 1734 1549 1603 1652 1529 1703
    ## [19587] 1641 1625 1541 1703 1640 1626 1754 1819 1741 1554 1550 1722 1635 1752
    ## [19601] 1707 1550 1658 1624 1710 1717 1802 1822 1653 1633 1807 1806 1629 1822
    ## [19615] 1840 1649 1649 1720 1644 1710 1614 1735 1656 1747 1743 1837 1640 1650
    ## [19629] 1653 1748 1838 1807 1811 1637 1840 1734 1809 1636 1653 1705 1834 1839
    ## [19643] 1740 1729 1644 1724 1821 1820 1641 1752 1711 1846 1825 1733 1730 1838
    ## [19657] 1812 1806 2027 1845 1719 1832 1744 1732 1950 1757 1727 1857 1709 1843
    ## [19671] 1812 1824 1943 2037 1819 1758 1843 1853 1907 1725 1727 1822 1849 1831
    ## [19685] 1859 1911 1845 1919 1747 1738 1920 1727 1757 1858 1714 1755 1714 1752
    ## [19699] 1856 1823 1757 1820 1850 2002 1852 2011 1832 1934 1754 1928 1753 1754
    ## [19713] 1828 1933 1853 1914 1959 1900 1851 1845 1922 1925 1820 1840 1839 1940
    ## [19727] 1933 1944 1947 2050 1907 2002 1759 2013 1756 2137 1921 1751 1934 2023
    ## [19741] 2013 1836 1751 1954 1828 1949 1837 1757 2036 1939 1953 1954 1819 1959
    ## [19755] 2004 1815 2013 1941 2024 2002 1842 1801 1803 1951 2011 2101 1905 2044
    ## [19769] 1936 1900 2017 1920 1845 1957 1906 2003 1938 2028 1958 1922 1827 2058
    ## [19783] 1900 2119 2020 1926 1836 1904 2137 2034 1952 2053 2130 2029 2046 1927
    ## [19797] 2100 1954 2132 2045 2119 2108 1915 2027 2049 1900 2043 2039 1928 1957
    ## [19811] 1900 2011 1949 1950 1939 1914 2106 1926 1937 2137 2035 2015 2125 1946
    ## [19825] 2112 1943 2135 2149 2046 2152 1915 2026 2021 2118 2147 2033 2222 1938
    ## [19839] 2021 2119 1935 2044 2042 2025 2242 2053 2150 2045 2011 2140 2139 2133
    ## [19853] 2035 1948 1954 2136 2011 2128 2027 2125 2359 2104 2204 2214 2125 2100
    ## [19867] 2307 2252 2041 2058 2247 2206 2044 2045 2051 2141 2247 2154 2150 2151
    ## [19881] 2216 2145 2231 2017 2050 2230 2302 2213 2052 2212 2108 2054 2156 2051
    ## [19895] 2219 2042 2213 2048 2045 2150 2221 2144 2050 2144 2121 2137 2225 2144
    ## [19909] 2233 2209 2245 2310 2247 2132 2359 2226 2254 2046 2303 2250 2120 2226
    ## [19923] 2223 2146 2305 2101 2238 2152 2248 2311 2140 2215 2250 2235 2149 2221
    ## [19937] 2132 2204 2316 2202 2357 2126 2253 2230 2141 2327 2229 2307 2137 2203
    ## [19951] 2138 2127  122 2338 2332    1 2146 2139 2322 2325 2303 2145 2249 2319
    ## [19965] 2203 2156 2249 2225   25 2217 2248 2218 2203 2320 2326 2303 2208 2306
    ## [19979] 2335 2236 2231 2235 2253   10 2221 2307   16  100 2328 2237 2255 2345
    ## [19993] 2245 2258   21 2340 2355    5    5 2352   10  439   44  437   57   NA
    ## [20007]   NA   NA   NA   NA   NA   NA   NA   NA  236  147  644  749  807  820
    ## [20021] 1016  650  844  816  846  707  941  716  653  843  841  752  815  750
    ## [20035]  925  833  728  818  659  732  849  841  817  742  752 1049  734  855
    ## [20049]  907  756  837  903  803  857  903  712  818  725  916  804  828  911
    ## [20063]  734  909  834  810  909 1015 1121  826  909 1005  918  923  759  919
    ## [20077]  814  925  755  912 1624  842  923  854 1034  922  841  801  926 1007
    ## [20091] 1031  931  927  818 1052 1000 1000  808  952  940  950 1010 1022  830
    ## [20105]  838  956  858  948 1147 1101 1021  850 1056  916 1022 1044 1011  839
    ## [20119] 1008 1004 1006  850 1115 1000  935  856 1029  845 1026  840  855 1055
    ## [20133]  925 1019 1025 1030  914 1132 1128 1005 1112 1107  925 1008  912  846
    ## [20147] 1035 1104 1039  954 1048 1006 1009 1103 1018 1157 1037  905 1041 1022
    ## [20161] 1052 1057  905  931 1056 1306  936 1024 1053 1124 1031 1002  921  953
    ## [20175]  951 1030 1307  945  946 1020  950 1014 1148  952 1107 1155 1118 1121
    ## [20189] 1633 1331 1051 1009  957 1202  939 1028 1334 1107  942 1144 1131 1119
    ## [20203] 1151 1039 1102  949 1004 1157 1041 1049 1342 1133 1111 1137 1021 1026
    ## [20217] 1116 1155 1008 1118 1143 1520 1156 1222 1037 1107 1256 1126 1228 1203
    ## [20231] 1142 1018 1100 1106 1417 1105 1040 1217 1034 1228 1440 1103 1207 1217
    ## [20245] 1011 1109 1058 1118 1027 1224 1215 1123 1045 1242 1031 1218 1046 1050
    ## [20259] 1234 1437 1234 1109 1144 1238 1219 1243 1205 1152 1211 1122 1117 1056
    ## [20273] 1050 1139 1233 1303 1241 1132 1339 1252 1223 1237 1226 1257 1331 1257
    ## [20287] 1234 1354 1112 1250 1122 1225 1205 1311 1147 1132 1331 1226 1206 1159
    ## [20301] 1242 1220 1231 1215 1225 1319 1145 1217 1315 1406 1211 1412 1437 1351
    ## [20315] 1157 1317 1413 1318 1353 1343 1352 1146 1250 1455 1219 1428 1405 1815
    ## [20329] 1250 1250 1259 1223 1259 1334 1413 1423 1401 1252 1317 1348 1347 1226
    ## [20343] 1340 1607 1438 1300 1418 1302 1316 1441 1352 1309 1249 1339 1251 1403
    ## [20357] 1417 1438 1440 1320 1402 1302 1243 1511 1436 1414 1532 1421 1259 1440
    ## [20371] 1336 1449 1349 1311 1305 1308 1256 1325 1320 1532 1348 1545 1457 1355
    ## [20385] 1518 1416 1446 1339 1339 1444 1417 1401 1346 1358 1521 1433 1544 1519
    ## [20399] 1547 1352 1541 1433 1402 1532 1358 1531 1533 1505 1440 1525 1506 1410
    ## [20413] 1532 1412 1512 1350 1451 1439 1537 1459 1412 1640 1429 1529 1502 1558
    ## [20427] 1408 1513 1607 1710 1442 1656 1619 1525 1515 1605 1542 1545 1613 1420
    ## [20441] 1719 1625 2000 1740 1502 1823 1453 1627 1507 1644 1456 1454 1647 1611
    ## [20455] 1652 1536 1732 1629 1644 1645 1509 1533 1510 1620 1536 1532 1632 1629
    ## [20469] 1504 1600 1521 1615 1658 1816 1554 1635 1712 1616 1727 1634 1708 1729
    ## [20483] 1700 1615 1548 1628 1604 1717 1648 1738 1657 1634 1724 1815 1620 1559
    ## [20497] 1555 1707 1621 1654 1720 1650 1648 1820 1835 1648 1659 1644 1653 1627
    ## [20511] 1747 1722 1738 1640 1733 1823 1659 1757 1656 1722 1802 1647 1710 1741
    ## [20525] 1825 1759 1647 1634 1835 1641 1815 1900 1649 1801 1930 1635 1834 1727
    ## [20539] 1814 1707 1855 1717 1826 1825 1744 1750 1841 1940 1721 1807 1652 1719
    ## [20553] 1758 1652 1655 1940 1725 1917 1852 1805 1822 1736 1711 1905 1656 1710
    ## [20567] 1829 1844 1832 1807 1836 1857 1735 1812 1812 1744 1749 1728 1826 1747
    ## [20581] 1827 1713 1919 2116 1835 1732 1725 1739 1907 1903 1917 1739 1841 1902
    ## [20595] 1939 2112 1759 1954 1847 1903 1751 1816 2013 1743 1949 1904 1859 2047
    ## [20609] 1840 1928 1941 1815 1940 1738 1742 1916 1844 1927 1759 1833 1833 1809
    ## [20623] 1932 2116 1854 2019 2100 2013 2040 1827 2146 2032 1937 1819 1826 2016
    ## [20637] 1817 1816 1826 1951 1805 1824 1831 1957 1943 2013 2003 1840 2036 2048
    ## [20651] 1848 2032 2037 1948 1925 1956 1957 2035 1848 1913 2021 1909 2023 1832
    ## [20665] 1955 2040 1922 1922 1955 2149 2046 2042 2004 1910 1933 2038 1848 2034
    ## [20679] 1906 1919 2027 1837 1923 1927 2029 2034 2144 1904 1954 1932 2029 2152
    ## [20693] 2104 1921 2037 1913 1947 1900 1942 2055 1915 2031 2036 2111 2015 1939
    ## [20707] 1935 2044 2044 2028 2149 2110 1947 1933 1950 2006 2149 1938 2106 1954
    ## [20721] 2058 2008 2003 2151 2058 2046 1934 2132 2049 2113 2222 2024 2103 2015
    ## [20735] 2211 1944 2001 2230 1954 2032 2041 2018 2202 1955 2020 2048 2010 2024
    ## [20749] 2203 2157 2300 2042 2150 2029 2156 2126 2213 2049 2014 2011 2221 1951
    ## [20763] 2309 2131 2025    9 2121 2054 2318 2120 2307 2256 2313 2129 2052 2102
    ## [20777] 2125 2033 2156 2135 2126 2113 2036 2249 2200 2200 2246 2358 2040 2112
    ## [20791] 2052 2328 2329 2327 2343 2153 2120 2150 2151 2048 2202 2226 2248 2216
    ## [20805] 2131 2147 2238 2251 2245 2102 2138 2345 2129 2227 2234 2058 2120 2239
    ## [20819] 2150 2129 2132 2140 2241   16 2211 2217 2120   23 2206 2302 2312 2254
    ## [20833] 2236 2342 2212 2152 2204   37 2359 2210 2236 2243 2143 2334 2327 2220
    ## [20847] 2226 2302 2146 2157   30   34 2322 2233 2343  121 2243 2253 2205 2220
    ## [20861] 2158 2307 2242   39 2339 2211   37 2327 2302 2212 2224 2317 2231 2258
    ## [20875] 2324 2237 2319 2252 2225 2355 2245 2255   21   10    6 2238   14   49
    ## [20889] 2244   15 2242 2324 2305   58 2254 2317   23 2322   49 2324   35   36
    ## [20903]    7 2321   50 2348   30 2340 2340 2350    1 2354 2359 2352    7 2353
    ## [20917]  132   21    1  149   22   28  419  418  229   NA   NA   NA   NA   NA
    ## [20931]   NA   NA   NA   NA   NA   NA   NA   NA   NA  208  119  225  229  215
    ## [20945]  632  804  820  826 1006  724  707  644  903  743  655  739  838  745
    ## [20959]  841  857  754  817  839  754  758  932  837  708  653  835  850  746
    ## [20973]  809 1001 1041  846  844  749  900  732  712  853  833  901  834  901
    ## [20987]  850  801  808  903  848  811  739 1120  918 1003  900  955  730  914
    ## [21001]  836  835  909  900 1002  911  935  926  809 1047 1046 1039  807  957
    ## [21015]  904  946  753 1000 1001  836  802 1014 1033  941  944 1046 1035 1039
    ## [21029]  953  959 1006 1005 1110  956  809 1031  927 1159  925  849 1028  913
    ## [21043]  903 1048 1026 1012 1000 1041  848 1129  853 1029  933 1030 1006  923
    ## [21057] 1111 1107 1010 1129  943 1120 1033 1003 1221 1042  931 1036  945  958
    ## [21071]  854  900  900  900 1053 1008  942 1204 1115  933 1034 1108  942 1032
    ## [21085]  955 1015 1047 1035 1112  859 1027 1101 1136 1038 1059  930 1250  939
    ## [21099]  914 1056 1009  907 1045 1110 1005  922  955 1259 1013 1003  930 1143
    ## [21113] 1040 1009 1035 1121 1055 1002 1154 1311  925 1021 1108 1143 1113 1041
    ## [21127] 1008 1144 1117 1202 1223 1028 1021 1121  949 1026 1214 1048 1348 1013
    ## [21141]  942 1015 1054 1135 1148 1214  947 1106 1146 1137 1011 1203 1138 1027
    ## [21155] 1215 1012 1012 1149 1243 1233 1102 1010 1150 1150 1218 1136 1249 1234
    ## [21169] 1402 1052 1202 1119 1208 1124 1047 1127 1059 1109 1211 1142 1210 1226
    ## [21183] 1222 1123 1539 1341 1026 1302 1049 1215 1046 1107 1405 1027 1239 1206
    ## [21197] 1239 1226 1208 1119 1049 1158 1052 1046 1247 1237 1154 1317 1244 1131
    ## [21211] 1131 1058 1129 1120 1312 1156 1232 1303 1257 1218 1112 1150 1358 1238
    ## [21225] 1116 1323 1139 1219 1121 1307 1257 1233 1311 1340 1206 1225 1359 1254
    ## [21239] 1337 1157 1330 1343 1252 1401 1415 1338 1200 1151 1336 1327 1250 1358
    ## [21253] 1241 1136 1220 1219 1345 1211 1408 1334 1431 1214 1408 1240 1424 1207
    ## [21267] 1239 1302 1231 1420 1409 1305 1341 1344 1321 1403 1447 1546 1416 1315
    ## [21281] 1301 1452 1316 1443 1322 1426 1414 1304 1247 1300 1405 1426 1242 1432
    ## [21295] 1342 1444 1442 1239 1249 1303 1345 1507 1301 1428 1517 1445 1428 1358
    ## [21309] 1536 1309 1440 1302 1516 1347 1313 1346 1313 1556 1604 1541 1423 1310
    ## [21323] 1336 1558 1532 1417 1328 1553 1427 1531 1552 1604 1333 1547 1552 1511
    ## [21337] 1409 1529 1536 1406 1523 1511 1428 1434 1350 1553 1550 1539 1531 1600
    ## [21351] 1455 1559 1547 1516 1422 1423 1659 1451 1511 1645 1549 1508 1823 1704
    ## [21365] 1549 1618 1631 1416 1614 1647 1600 1445 1505 1711 1655 1439 1602 1520
    ## [21379] 1653 1652 1641 1444 1455 1655 1557 1647 1629 1752 1610 1652 1523 1608
    ## [21393] 1710 1539 1707 1609 1552 1535 1541 1651 1604 1745 1733 1801 1639 1600
    ## [21407] 1716 1630 1658 1721 1737 1558 1537 1606 1702 1614 1732 1744 1540 1830
    ## [21421] 2049 1639 1750 1735 1827 1753   NA 1748 1636 1702 1619 1748 1709 1649
    ## [21435] 1617 1554   NA 1745 1757 1731 1557 1759 1853 1824 1634 1728 1616 1736
    ## [21449] 1743 1703 1812 1757 1749 1801 1752 1815 1851 1639 1826 1713 1646 1724
    ## [21463] 1703 1642 1818 1840 1829 1708 1714 1706 1727 1833 1748 1832 1700 1905
    ## [21477] 1708 1834 1800 1745 1910 1903 1747 1806 1820 1808 1759 1850 1711 1909
    ## [21491] 1652 1835 1852 1820 1737 1705 1911 1738 2039 1815 1719 1900 1710 1835
    ## [21505] 1900 1902 1821 1853 1754 1817 1718 1738 1906 1909 1736 1826 1849 1801
    ## [21519] 1831 1930 2109 1953 1705 1745 1914 1826 1857 2011 1808 1824 2006 1723
    ## [21533] 1903 1911 1923 1839 1928 1951 1920 1933 1836 1826 1821 1839 1931 2001
    ## [21547] 1810 1915 1938 1850 1825 2024 1801 1813 2048 1745 2030 1941 2011 2011
    ## [21561] 1954 2011 2048 2017 1833 2009 2140 1923 1802 1818 2047 1954 1857 2103
    ## [21575] 1812 1952 1919 1911 2056 1900 2043 2057 1946 1848 1959 2024 1937 2057
    ## [21589] 2051 1942 1943 2111 2257 2123 2140 1831 1904 2021 2005 2038 2122 1930
    ## [21603] 2141 2139 1923 1955 2108 2046 2056 2157 2100 2130 2051 2120 1935 2003
    ## [21617] 2037 2103 1916 2127 2053   34 2056 1917 2000 2141 2032 2111 2103 2152
    ## [21631] 2205 2021 2145 2009 2253 2101 2215 2153 2001 2130 2231 1946 2020 2204
    ## [21645] 2116 2112 2125 1952 2123 2229 2257 2054 2033 2101 2026 2025 2225 2039
    ## [21659] 2024 2232 2252 2102 2057 2232 2127 2225 2149 2059 2252 2151 2058 2252
    ## [21673] 2035 2230 2044 2223 2105 2055 2334 2114 2257 2250 2306 2203 2328 2136
    ## [21687] 2207 2104 2312 2254 2103 2228 2242 2136 2338 2214 2342   48 2346 2335
    ## [21701] 2201 2139 2153 2308 2218 2305 2209 2131 2356 2319 2149   42 2346 2128
    ## [21715] 2248 2325 2348   NA 2219 2144 2238 2302   31 2139 2359   16   21 2306
    ## [21729] 2304   21 2335 2332 2159  107   14 2344 2245 2257 2317 2238  135 2234
    ## [21743] 2215   26 2232   18    8   13   55   50  134 2400 2229 2302 2234 2311
    ## [21757] 2249 2254 2357 2305   23   42  310   20  125 2354 2331    2 2340   30
    ## [21771] 2342   45 2353    4   37 2332  105 2313   10 2318   57    6   18   49
    ## [21785] 2337 2326  124  100   47 2335 2347   34   36   25  124  114  130  158
    ## [21799]   51   17 2356  130  153  223   26  126 2346    7   31  114   19   20
    ## [21813]  323    8 2357  214  154   48  119   54   38   46  144  104  438  500
    ## [21827]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [21841]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [21855]   NA   NA   NA   NA   NA   NA   NA  229  655  756  808 1046  926  808
    ## [21869]  709  845  931  836  902  859  741  823  905  805  750 1039  715  749
    ## [21883]  855  726  841 1019  837  909  831  901  721  946  923  835 1030  922
    ## [21897]  748  936  831  810  937  806  841  802  904  958  842  943  943  913
    ## [21911] 1030  928 1051  944  757  954  813 1002 1039 1009  910  934 1018  840
    ## [21925] 1058 1028 1205 1014 1012 1011 1009  928  914  954 1035  845 1225 1049
    ## [21939]  958  944 1016 1030  846 1032 1100  946 1028 1101 1049 1040 1045  859
    ## [21953] 1104 1154  853 1124 1154 1026 1020 1053 1024  923 1028  921 1037  934
    ## [21967] 1257 1024  906 1105 1056 1022  944 1141 1101 1034  908 1013 1119 1003
    ## [21981] 1100 1020 1105 1102  929 1134 1025 1004 1339  941 1000 1119 1051 1039
    ## [21995] 1216 1328 1220 1101 1114 1045 1114 1142 1044 1147 1031 1138 1110 1022
    ## [22009] 1044 1242  956 1332 1029 1351 1343 1022 1037 1144 1137 1101 1115 1000
    ## [22023] 1016 1205 1008 1221 1156 1214 1202 1156 1058 1536 1221 1145 1212 1126
    ## [22037] 1218 1146 1017 1408 1254 1107 1051 1151 1228 1110 1414 1033 1114 1201
    ## [22051] 1042 1231 1146 1021 1142 1219 1112 1345 1220 1218 1038 1040 1230 1050
    ## [22065] 1217 1157 1050 1236 1111 1120 1045 1105 1259 1116 1244 1154 1237 1309
    ## [22079] 1109 1258 1124 1122 1343 1238 1327 1305 1227 1405 1123 1147 1355 1142
    ## [22093] 1334 1329 1401 1323 1336 1336 1215 1422 1355 1428 1439 1318 1417 1536
    ## [22107] 1307 1403 1421 1332 1225 1353 1246 1309 1249 1321 1308 1444 1410 1418
    ## [22121] 1339 1309 1432 1443 1422 1316 1446 1445 1445 1344 1246 1403 1251 1311
    ## [22135] 1253 1410 1251 1313 1459 1242 1525 1433 1448 1431 1348 1503 1503 1355
    ## [22149] 1312 1301 1334 1530 1549 1341 1521 1445 1426 1440 1334 1558 1540 1504
    ## [22163] 1536 1351 1355 1356 1528 1411 1409 1619 1409 1420 1452 1558 1522 1545
    ## [22177] 1519 1740 1408 1454 1605 1612 1507 1634 1503 1447 1411 1535 1614 1609
    ## [22191] 1804 1616 1445 1606 1635 1653 1717 1941 1639 1705 1525 1626 1716 1457
    ## [22205] 1553 1632 1636 1532 1645 1606 1455 1700 1603 1627 1618 1523 1528 1629
    ## [22219] 1506 1532 1520 1559 1710 1614 1828 1720 1631 1824 1728 1609 1733 1603
    ## [22233] 1529 1728 1621 1633 1735 1647 1608 1635 1606 1641 1750 1746 1748 1722
    ## [22247] 1646 1640 1722 1657 1614 1544 1746 1742 1744 1814 1741 1707 1613 1747
    ## [22261] 1831 1556 1755 1804 1650 1640 1819 1808 1631 1627 1639 1644 1647 1829
    ## [22275] 1743 1738 1824 1750 1652 1700 1644 1659 1721 1627 1703 1905 1846 1810
    ## [22289] 1843 1931 1649 1700 1641 1821 1840 1707 1808 1740 1756 1910 1840 1758
    ## [22303] 1802 1724 2034 1736 1724 1848 1803 1830 1844 1859 1755 1806 1740 1805
    ## [22317] 1849 1905 1916 2036 1729 1734 1848 1907 1906 1751 1750 1909 1805 1706
    ## [22331] 1914 1741 1949 2021 2007 1705 1823 1716 1826 1738 1735 1827 1804 1946
    ## [22345] 1759 1805 1914 1923 1943 1923 2001 1745 1943 2000 2004 1742 1946 1958
    ## [22359] 1945 1900 1938 2140 2031 1925 1944 1935 1957 1921 1845 1808 1931 1922
    ## [22373] 1857 1822 1953 1809 1950 2021 1859 1816 1831 1851 2103 1847 2045 2032
    ## [22387] 2043 2036 2050 2006 2053 2034 2031 1939 1822 1848 1957 1921 2014 1906
    ## [22401] 2019 1930 2058 1905 2007 2021 2123 2111 1945 2020 1907 2058 2116 2109
    ## [22415] 1915 2109 1908 2006 2007 2022 2101 1931 2115 2044 1949 1922 2120 2133
    ## [22429] 2151 2014 2142 2122 2011 1913 2038 2134 2209 2103 2207 2058 2000 1957
    ## [22443] 2126 1942 2000 1953 2121 2154 2034 2028 2141 2051 2129 2237 2218 2347
    ## [22457] 2107 2118 2200 2041 2104 2208 2248 2210 2238 2140 2241 2204 2151 2258
    ## [22471] 2210 2107 2058 2105 2115 2133 2134 2247 2141 2058 2138 2218 2226 2148
    ## [22485] 2145 2300 2353 2253 2046 2125 2113 2257 2305 2124 2116 2257 2218 2130
    ## [22499] 2147 2125 2229 2316 2356  114 2245 2226 2148 2148 2317 2209 2326 2343
    ## [22513] 2212 2245   32 2242 2254 2228   20   22 2305 2301   30 2348 2341 2346
    ## [22527]    9   31   22   40  429  423   NA   NA   NA   NA   NA   NA   NA   NA
    ## [22541]   NA  749  824 1103  840  848  828  806  851  813  933  812  843 1038
    ## [22555]  748  927  846  843  811  831  852  755  841  910  953  912  746  754
    ## [22569]  905  916 1115  804 1009  920  912  819  807  916  858 1015  925 1030
    ## [22583]  930  953 1014  816  956  948 1003  930  815  902 1004 1016 1025 1001
    ## [22597]  934  956  944  903 1046 1009 1039  816 1013 1101 1016 1047 1202  911
    ## [22611] 1010 1101 1018 1133 1201 1056  857  954 1024 1029 1038 1022  853  939
    ## [22625] 1034 1115 1015 1027 1136  857  946 1019 1041  932  942 1024 1029 1048
    ## [22639] 1118  912 1016  931 1100 1249  949  946 1036  947 1127 1020  958  952
    ## [22653]  959 1040  915 1058 1046  955  950 1051 1303 1044 1105 1306  953 1112
    ## [22667] 1007 1111 1158 1121 1205 1025 1157 1019  946 1006 1017 1148 1102 1035
    ## [22681] 1144 1129 1201  952 1100 1154 1210 1047 1136 1224 1138 1158 1504 1157
    ## [22695] 1040 1104 1148 1348 1145 1110 1135 1029 1010 1348 1100 1057 1153 1016
    ## [22709] 1037 1211 1139 1140 1036 1442 1215 1207 1218 1148 1214 1103 1037 1222
    ## [22723] 1215 1256 1122 1118 1103 1039 1144 1134 1215 1323 1310 1108 1257 1107
    ## [22737] 1234 1224 1239 1106 1300 1136 1338 1138 1226 1116 1258 1332 1302 1201
    ## [22751] 1307 1310 1305 1215 1132 1158 1314 1342 1241 1311 1402 1321 1221 1435
    ## [22765] 1420 1216 1229 1317 1323 1236 1339 1154 1427 1235 1423 1342 1329 1218
    ## [22779] 1211 1504 1158 1400 1302 1300 1407 1534 1312 1435 1239 1235 1406 1313
    ## [22793] 1432 1306 1359 1408 1430 1428 1419 1316 1303 1433 1419 1315 1405 1255
    ## [22807] 1426 1251 1252 1251 1253 1452 1423 1512 1458 1408 1532 1259 1551 1441
    ## [22821] 1343 1335 1324 1429 1458 1341 1458 1330 1315 1541 1536 1435 1415 1519
    ## [22835] 1454 1414 1430 1426 1353 1515 1400 1441 1530 1344 1432 1526 1346 1358
    ## [22849] 1518 1528 1510 1516 1537 1457 1440 1441 1348 1450 1418 1547 1601 1554
    ## [22863] 1508 1557 1451 1639 1409 1450 1603 1602 1606 1424 1613 1652 1649 1532
    ## [22877] 1540 1421 1459 1447 1701 1614 1642 1634 1441 1806 1505 1535 1632 1606
    ## [22891] 1521 1634 1501 1628 1611 1637 1458 1545 1650 1556 1625 1702 1557 1629
    ## [22905] 1624 1540 1656 1725 1636 1529 1528 1659 1754 1742 1709 1721 1544 1635
    ## [22919] 1806 1533 1737 1537 1656 1741 1659 1627 1754 1627 1614 1745 1724 1723
    ## [22933] 1727 1739 1710 1652 1614 1725 1622 1821 1639 1548 1819 1618 1643 1646
    ## [22947] 1802 1746 1715 1843 1613 1711 1712 1610 1650 1749 1713 1820 1720 1742
    ## [22961] 1616 1741 1739 1658 1823 1702 1808 1826 1710 1615 1652 1807 1801 1634
    ## [22975] 1734 1809 1727 2128 1630 1717 1855 1717 1841 1853 1846 1737 1827 1655
    ## [22989] 1904 1703 1720 1852 1906 1814 1743 1930 1802 1750 1802 1743 1840 1751
    ## [23003] 1745 1809 1901 1837 1823 1700 1717 1839 1844 1904 1830 1852 1713 1905
    ## [23017] 1824 1802 1841 1923 1802 1743 2031 1808 2043 1855 1716 1833 1753 1735
    ## [23031] 1744 1728 1952 1854 1748 1945 1920 1814 1921 1849 1824 1934 1810 1720
    ## [23045] 2003 1833 1930 1927 1910 1841 1857 2004 1806 1757 1925 1909 1837 1836
    ## [23059] 1859 1851 1948 1926 1847 1737 1819 1739 1750 1751 1814 1945 2004 1850
    ## [23073] 1948 1940 2015 1754 2022 1920 2125 2013 2035 1808 1804 1932 2021 1808
    ## [23087] 1814 1958 2016 1940 1808 1945 2010 2000 1944 2005 2011 1823 1939 1903
    ## [23101] 1811 1830 1922 1845 1824 2030 1955 2044 2007 1846 2013 2010 2157 2005
    ## [23115] 1919 1912 2022 1910 1906 2033 2046 1954 1845 1934 2010 2100 2024 2117
    ## [23129] 2122 2033 1934 1855 2019 1915 2111 1850 2043 1903 1948 2017 2050 1936
    ## [23143] 1944 1948 1857 2049 2052 2127 2057 1931 1919 1906 1950 2049 1944 2158
    ## [23157] 2100 2040 2136 1947 2037 2102 2150 1956 2108 1954 2206 2151 1921 2143
    ## [23171] 2136 2014 1952 2200 1948 2025 2054 2205 2052 2006 2114 2109 2038 1951
    ## [23185] 2010 2114 2123 2029 2110 2126 2340 2125 2214 2042 2017 2210 2111 2220
    ## [23199] 2229 2146 2022 2036 1954 2249 2003 2027 2056 2031 2143 2010 2245 2149
    ## [23213] 2200 2043 2201 2310 2201 2152 2202 2250 2228 2052 2101 2343 2048 2214
    ## [23227] 2221 2158 2217 2038 2308 2026 2136 2156 2223 2226 2034 2107 2111 2214
    ## [23241] 2124 2032 2225 2225 2134 2059 2154 2222 2236 2217 2330 2150 2310 2141
    ## [23255] 2235 2132 2059 2315 2124 2255 2218 2102 2251 2211 2229 2233 2207 2103
    ## [23269] 2234 2059 2137 2305 2159 2201 2127 2214 2235 2316 2248 2153 2144 2150
    ## [23283] 2220 2203 2120 2327 2217 2304 2132 2138  108 2338 2223 2141 2258 2140
    ## [23297] 2153 2300 2340 2217 2343 2257 2248 2236   19 2322 2157 2222 2158 2210
    ## [23311] 2201 2234   33 2341 2329    6 2211 2357 2251 2208 2228 2223 2311 2236
    ## [23325] 2213   16   33 2253    7 2256 2339 2247 2356 2254   47 2242   38 2305
    ## [23339] 2359 2343 2359 2351 2356   13    4   12  424  424   NA   NA   NA   NA
    ## [23353]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA  454  635
    ## [23367]  803  809  956  836  808  649  828  854  845  842  706  816  911  651
    ## [23381]  755  902  640  757  659  705  718  745  822 1030  852  739  855  805
    ## [23395]  721  746  915  728  856  837  734  717  856  809 1127  817  847  825
    ## [23409]  752  741  912  815  822  807  921  909  904  724  901  812  917 1000
    ## [23423]  816 1013  936  908  931  806  843  926 1019 1045  901  744  939 1033
    ## [23437]  958  942  945  754  800 1017  959 1016  943  931 1030  835  952  959
    ## [23451] 1034  924  834 1002 1027  846 1136  943  909 1016  847 1021 1046 1037
    ## [23465] 1047  842 1030  934  929 1044 1009 1027 1001 1045  908 1032  951 1103
    ## [23479]  944 1040 1034 1035  848  940  936 1118 1204  922 1112 1002 1000  948
    ## [23493]  952 1033 1001 1045 1033  847  853 1101 1045 1142 1112 1025 1032  954
    ## [23507] 1055 1053  904 1003 1019 1108 1048 1257  910 1041 1055 1012  924  911
    ## [23521]  947  952 1117 1034 1015 1105 1038 1032 1233  925  919  932 1014 1006
    ## [23535] 1128 1000 1047  958 1011 1008  948 1057 1002 1115 1119  950 1009 1126
    ## [23549] 1007 1159  948 1008  957 1309 1109  948 1129  944 1336 1103 1149 1036
    ## [23563] 1107 1058 1133 1057 1135 1143 1156 1123 1008 1153  948 1209 1130 1137
    ## [23577] 1203 1045 1513 1004 1136 1102 1139 1149 1004 1211 1203 1134 1158 1120
    ## [23591] 1332 1221 1125 1201 1143 1033 1100 1050 1052 1208 1118 1045 1138 1039
    ## [23605] 1213 1204 1259 1410 1059 1227 1418 1221 1220 1215 1206 1108 1219 1027
    ## [23619] 1250 1236 1106 1128 1112 1122 1316 1227 1210 1340 1122 1210 1231 1149
    ## [23633] 1303 1301 1243 1120 1347 1259 1240 1205 1312 1131 1325 1204 1150 1400
    ## [23647] 1320 1158 1150 1329 1154 1335 1252 1309 1357 1231 1341 1242 1218 1349
    ## [23661] 1158 1405 1332 1254 1335 1214 1322 1219 1304 1346 1204 1353 1340 1151
    ## [23675] 1158 1334 1419 1421 1306 1221 1454 1219 1440 1259 1425 1356 1603 1321
    ## [23689] 1422 1301 1417 1416 1445 1433 1325 1413 1410 1441 1403 1416 1431 1446
    ## [23703] 1256 1301 1326 1452 1435 1325 1446 1422 1330 1533 1442 1433 1310 1448
    ## [23717] 1454 1437 1436 1428 1322 1457 1334 1351 1419 1338 1608 1345 1403 1407
    ## [23731] 1336 1534 1637 1502 1509 1601 1356 1359 1442 1420 1537 1601 1357 1417
    ## [23745] 1503 1509 1409 1528 1506 1434 1443 1538 1551 1601 1443 1426 1433 1550
    ## [23759] 1530 1448 1540 1528 1417 1605 1553 1513 1614 1455 1441 1433 1615 1621
    ## [23773] 1547 1822 1617 1649 1650 1517 1550 1522 1551 1538 1622 1700 1607 1556
    ## [23787] 1453 1634 1633 1629 1653 1643 1445 1706 1626 1556 1726 1520 1506 1518
    ## [23801] 1726 1650 1542 1620 1702 1546 1649 1541 1758 1647 1655 1809 1747 1616
    ## [23815] 1806 1642 1604 1722 1731 1718 1540 1614 1717 1723 1731 1730 1623 1701
    ## [23829] 1735 1628 1746 1632 1730 1646 1753 1643 1814 1638 1643 1624 1713 1554
    ## [23843] 1754 1647 1625 2113 1640 1748 1639 1658 1644 1809 1625 1637 1758 1821
    ## [23857] 1630 1720 1725 1749 1653 1717 1820 1701 1738 1759 1654 1842 1903 1647
    ## [23871] 1658 1712 1840 1813 1749 1845 1731 1821 1655 1750 1907 1855 1818 1921
    ## [23885] 1826 1812 1708 1835 1822 1933 1835 1757 1855 1937 1806 1840 1657 1721
    ## [23899] 1726 1708 1826 2050 1835 1847 1910 1836 1924 1730 1851 1833 1849 1951
    ## [23913] 1741 1906 1925 1711 1800 1736 1841 1809 1807 1852 1922 1838 1916 1815
    ## [23927] 1859 1956 1829 1906 1856 1828 1806 1740 1822 1913 1801 2112 1834 1807
    ## [23941] 1904 1804 1948 1951 1816 1818 1923 1936 2007 2014 2017 2124 1949 1837
    ## [23955] 1957 2016 1813 1959 2026 1827 2012 2016 1920 1948 1851 2016 1821 1830
    ## [23969] 1822 2014 1955 2008 2017 2027 2106 1949 1931 1952 1924 1852 1917 2008
    ## [23983] 1956 2006 1921 1839 2016 2037 2002 2022 2046 1833 1910 2054 1900 1845
    ## [23997] 1912 2036 2000 1837 2029 2018 2034 2103 2020 1916 2133 2100 2106 2052
    ## [24011] 1912 2047 1913 2109 1906 2031 2029 2029 1954 1859 2029 1917 1917 2035
    ## [24025] 1928 2029 2010 1946 2117 2135 1936 2103 2141 2253 2124 1933 2108 2031
    ## [24039] 2104 1946 1920 1921 1940 2113 2112 2047 2105 2157 2039 1949 2009 2124
    ## [24053] 1934 1949 2005 2157 2159 2147 2147 1954 2131 2028 1955 2042 2009 2002
    ## [24067] 1950 2038 2216 2137 2005 2211 2202 2130 2108 2001 2132 1954 2127 2216
    ## [24081] 2115 2358 2214 2136 2030 2134 2143 2136 2211 2140 2015 2134 2251 2034
    ## [24095] 2048 2101 2040 2034 2146 2118 2217 2148 2029 2225 2235 2232 2044 2055
    ## [24109] 2244 2210 2216 2058 2256 2207 2211 2156 2139 2241 2132 2316 2052 2215
    ## [24123] 2110 2225 2117 2250 2239 2216 2305 2103 2215 2240 2121 2205 2116 2200
    ## [24137] 2148 2128 2256 2157 2159 2148 2250 2340 2141 2148 2201 2249 2147 2135
    ## [24151] 2258 2130 2306 2257 2313 2215 2148 2138 2244  109 2315 2208 2145 2205
    ## [24165] 2142 2137 2351 2206 2219 2150 2359 2158   11 2227 2329 2158 2233 2207
    ## [24179] 2341 2313   12 2231   18 2335 2215 2220 2230 2205   18 2344 2342 2229
    ## [24193] 2228   52 2245   57   32 2306 2245   35 2301   27 2308   39   37 2312
    ## [24207] 2259    3 2353 2354 2340   43  121 2343   55    3   15   40 2400  145
    ## [24221]   35   41  430   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [24235]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [24249]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [24263]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [24277]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA  635  753  815
    ## [24291] 1004  816  825  806  840  658  854  820  654  657  646  751  812  738
    ## [24305]  707  834  854  648  727  916  804  748  936  901  815  850  740  838
    ## [24319] 1029  751  836  839  711  838  808  727  719  851  804  914  840  817
    ## [24333]  917  959 1054  856  902  835  835  835  917  740  943  935  809  822
    ## [24347]  910 1003  856  739  924  757  934  803  931  854  957 1013 1038  916
    ## [24361]  932  944  748 1026  914  945  748  753  849  844  804  902  830 1026
    ## [24375]  824  946  858  931 1020 1020  917  931 1006 1051 1010 1029 1009  906
    ## [24389] 1012  916  926  837 1148  958 1053 1027 1004 1024 1052 1010  942 1050
    ## [24403]  926 1019 1004  915  933 1102  843 1213 1046 1007  953  943  859  936
    ## [24417] 1045 1035 1018  945  903 1038 1031  856 1022  845 1103 1012 1014 1022
    ## [24431] 1129 1133  924 1225 1017  904 1049 1035  958  939 1051 1049  946 1014
    ## [24445] 1109  911 1036  954  930  939 1227 1105 1040  938  936 1058 1031 1104
    ## [24459]  930 1246 1120 1110 1000 1015 1118 1134 1052 1145 1106  957 1200 1053
    ## [24473] 1000 1005 1141  932  933 1040 1146 1029 1334  953 1001 1002 1028 1112
    ## [24487] 1142 1031 1105 1052 1154  947 1129 1111 1202 1140 1159 1154 1011 1010
    ## [24501] 1101 1111 1035 1504 1049 1103 1122 1143 1158 1011 1206 1133 1153 1011
    ## [24515] 1142 1148 1046 1231 1048 1117 1350 1024 1152 1243 1210 1015 1151 1113
    ## [24529] 1353 1033 1205 1159 1211 1051 1213 1134 1220 1201 1103 1118 1048 1056
    ## [24543] 1106 1101 1202 1103 1051 1109 1240 1045 1058 1221 1208 1232 1228 1257
    ## [24557] 1134 1321 1308 1208 1243 1129 1316 1219 1313 1117 1322 1327 1233 1317
    ## [24571] 1148 1201 1314 1157 1201 1348 1345 1221 1239 1158 1321 1308 1232 1350
    ## [24585] 1214 1209 1322 1242 1344 1147 1151 1159 1413 1321 1402 1315 1249 1417
    ## [24599] 1341 1232 1212 1201 1212 1254 1316 1213 1411 1337 1257 1415 1535 1356
    ## [24613] 1340 1419 1356 1257 1347 1436 1305 1310 1433 1403 1408 1423 1417 1420
    ## [24627] 1421 1248 1314 1402 1240 1353 1414 1252 1323 1336 1303 1522 1439 1448
    ## [24641] 1304 1305 1305 1422 1813 1415 1429 1348 1342 1302 1313 1401 1550 1340
    ## [24655] 1526 1347 1351 1352 1448 1429 1855 1330 1523 1354 1440 1907 1454 1522
    ## [24669] 1548 1513 1541 1345 1801 1552 1518 1517 1352 1534 1401 1416 1443 1348
    ## [24683] 1449 1428 1444 1538 1425 1534 1554 1416 1448 1534 1508 1406 1417 1616
    ## [24697] 1453 1609 1402 1630 1553 1549 1553 1429 1727 1747 1559 1701 1621 1522
    ## [24711] 1646 1925 1550 1600 1530 1646 1620 1521 1652 1535 1703 1641 1647 1455
    ## [24725] 1451 1455 1628 1524 1635 1458 1641 1629 1641 1557 1546 1503 1641 1551
    ## [24739] 1605 1708 1728 1619 1630 2058 1701 1757 1625 1725 1717 1649 1738 1536
    ## [24753] 1619 1724 1730 1556 1726 1638 1721 1708 1627 1651 1716 1559 1614 1718
    ## [24767] 1615 1628 1750 1625 1908 1556 1812 1632 1624 1807 1612 1559 1800 1640
    ## [24781] 1633 1611 1736 1751 1831 1644 1717 1612 1611 1641 1814 1709 1712 1642
    ## [24795] 1732 1746 1742 1744 1805 1811 1811 1936 1619 1654 1631 1810 1625 1700
    ## [24809] 1640 1722 1628 1735 1813 1713 1727 1710 1813 1901 1836 1737 1841 1655
    ## [24823] 1756 1647 1744 1758 1705 1651 1856 1842 1726 1647 1808 1936 1840 1757
    ## [24837] 1859 1904 1700 1837 1825 1835 1838 1827 1818 1912 1716 1811 1723 1947
    ## [24851] 1714 1900 1910 1830 1846   NA 1826 1736 1725 2033 1907 1746 1753 1843
    ## [24865] 1706 1823 1800 1753 1753 1956 1847 1909 1902 1917 1837 1724 1807 1819
    ## [24879] 1725 1922 1926 1855 1902 1812 1808 1919 1931 1833 1750 1843 1834 1816
    ## [24893] 1945 2001 1923 2104 1931 2037 1940 1808 2001 1947 1948 2010 1758 1913
    ## [24907] 1807 1755 1815 1934 1815 1950 2028 2138 1946 1849 1947 1950 1825 2004
    ## [24921] 1807 2045 1940 1854 2037 2044 1855 1859 2008 1957 1940 2020 1846 2035
    ## [24935] 2052 1937 1955 2009 2040 1856 2002 1849 1907 1856 2011 2007 1904 1836
    ## [24949] 1847 2045 1906 2050 2000 2055 2113 1938 2137 2016 2016 2021 2058 1857
    ## [24963] 2047 2045 1901 1921 2027 1902 1946 1947 1853 1932 1931 2036 2137 2032
    ## [24977] 1935 1929 2015 1945 2151 2045 2031 1932 2136 1929 2128 2008 2047 2108
    ## [24991] 2116 2145 2143 1951 2101 2110 2204 2035 1934 2146 2014 2017 2148 2035
    ## [25005] 2041 2008 2145 2015 2132 2142 2049 2206 2140 2329 2206 2120 1956 2103
    ## [25019] 2013 2248 2127 2046 2158 2130 2009 2033 2013 2039 2036 2210 2045 2056
    ## [25033] 2121 2223 2010 2052 2214 2055 2250 2150 2244 2218 2040 2222 2239 2116
    ## [25047] 2220 2103 2208 2054 2100 2302 2310 2110 2149 2254 2037 2036 2200 2127
    ## [25061] 2222 2033 2059 2220 2228 2214 2111 2040 2316 2239 2246 2314 2248 2136
    ## [25075] 2149 2252 2138 2258 2149 2150 2245 2100 2111 2128 2225 2142 2249 2233
    ## [25089] 2131 2148 2113 2108 2140 2126 2200 2335 2207 2121 2215 2212 2139 2306
    ## [25103] 2241 2107 2315 2157 2319 2335 2150 2333 2307 2126 2229    5 2341 2249
    ## [25117] 2337 2134 2230 2141 2143 2146 2155 2148 2316 2307  112 2201 2217 2208
    ## [25131] 2223   15 2238 2203 2216 2242 2156 2212 2331 2300 2233 2207    4 2227
    ## [25145] 2225    8 2221 2236   36 2307 2249 2259 2300  101 2313   35 2335 2341
    ## [25159] 2346 2352 2346    2  414  419   NA   NA   NA   NA   NA   NA   NA   NA
    ## [25173]   NA   NA   NA   NA   NA  100  643  825  833  833 1006  900  724  907
    ## [25187]  917  822  745  900  852  650  823  923  733  711  751  716  709  711
    ## [25201]  938  739  657  728  833  905  846  744  809  858 1046  728  854  808
    ## [25215]  830  838  844  953  916  802  822  718  832  952  853  922  854  742
    ## [25229]  807 1107  825  938  931  740 1001  813  958  756  832 1008  859  854
    ## [25243]  857  955  802  818 1002 1013  945  804 1026  945 1002 1003  959  813
    ## [25257]  936  934  825 1016  933 1002  957 1005 1023  854  818 1143 1003  856
    ## [25271] 1012 1008 1000 1022 1052  959  901 1032 1004  849 1038 1017 1105  915
    ## [25285] 1036 1048 1037 1012  847 1051 1028 1040 1026 1037  936 1059 1214 1111
    ## [25299]  934 1010  856 1005 1046 1104  906  907 1033  948  932 1113 1110 1113
    ## [25313] 1129 1054 1234  904 1005 1049  934 1105 1100 1118 1013 1007 1009 1030
    ## [25327] 1044 1045  926 1132 1121  935  950 1008 1003 1251  957 1031 1127 1030
    ## [25341] 1130 1008 1020 1021 1030 1056 1312 1058 1031  951 1134 1102 1137 1158
    ## [25355] 1023 1142  946 1137 1046 1321 1029 1239 1018 1238 1043 1008 1221 1017
    ## [25369] 1059 1149 1110 1224 1157 1051 1441 1106 1202 1215 1209 1109 1212 1247
    ## [25383] 1241 1208 1116 1041 1203 1013 1208 1139 1134 1257 1444 1207 1225 1056
    ## [25397] 1022 1233 1217 1310 1031 1225 1315 1221 1439 1220 1045 1218 1214 1057
    ## [25411] 1128 1045 1202 1051 1226 1231 1222 1202 1209 1304 1248 1058 1316 1216
    ## [25425] 1324 1301 1344 1231 1213 1231 1204 1131 1321 1207 1327 1349 1155 1327
    ## [25439] 1234 1319 1120 1232 1324 1343   NA 1251 1135 1333 1224 1342 1203 1350
    ## [25453] 1327 1341 1317 1201 1221 1248 1209 1213 1411 1352 1342 1218 1227 1426
    ## [25467] 1354 1254 1411 1228 1222 1202 1246 1217 1253 1404 1304 1430 1319 1411
    ## [25481] 1250 1358 1232 1335 1450 1549 1442 1420 1319 1422 1428 1448 1245 1259
    ## [25495] 1257 1426 1332 1409 1310 1245 1441 1339 1514 1536 1510 1448 1339 1311
    ## [25509] 1512 1524 1445 1329 1450 1305 1428 1311 1317 1345 1529 1511 1512 1345
    ## [25523] 1425 1342 1513 1421 1402 1406 1517 1336 1830 1540 1400 1422 1338 1528
    ## [25537] 1349 1549 1343 2042 1553 1608 1523 1606 1534 1500 1419 1600 1434 1553
    ## [25551] 1428 1613 1527 1430 1507 1818 1555 1444 1506 1421 1512 1458 1426 1622
    ## [25565] 1509 1622 1635 1628 1502 1448 1623 1618 1532 1820 1445 1646 1647 1546
    ## [25579] 1627 1615 1640 1918 1818 1513 1652 1459 1656 1548 1505 1510 1530 1715
    ## [25593] 1614 1744 1628 1709 1620 1729 1801 1640 1734 1607 1736 1549 1559 1544
    ## [25607] 1725 1612 1544 1758 1750 1550 1629 1647 1659 1635 1613 1738 1757 1813
    ## [25621] 1806 1613 1811 1816 1646 1759 1651 1706 1619 1649 1706 1824 1617 1737
    ## [25635] 1648 1606 1708 1818 1812 1803 1702 1648 1806 1710 1643 1621 1840 1827
    ## [25649] 1754 1800 1842 1659 1703 1746 1743 1736 1821 1903 1847 1635 1837 1803
    ## [25663] 1748 1910 1735 2036 1701 1853 1852 1904 1921 1751 1823 1819 1845 1816
    ## [25677] 1710 1758 1707 1802 1851 1841 1854 1729 1914 1826 1905 1750 1921 1929
    ## [25691] 1911 1804 1715 1725 1911 1921 1917 1816 1935 2009 1942 1924 1801 1830
    ## [25705] 1945 1800 1940 1828 1828 1758 1937 2006 1845 2110 1844 1947 2006 1817
    ## [25719] 1852 1939 1934 1942 2015 2019 2029 1958 2145 2055 1853 1847 2031 1841
    ## [25733] 2015 2031 2023 1905 2037 2012 1921 1858 1925 2027 2020 2015 2057 2012
    ## [25747] 1856 2027 1845 1948 1832 2027 2048 1854 2022 2108 2005 1902 2041 2038
    ## [25761] 2042 2037 1907 2014 2033 1921 2059 2040 2104 2103 1958 2104 2106 2118
    ## [25775] 2054 2115 2105 2012 1936 2002 1940 2136 2006 1923 2037 2056 2125 2132
    ## [25789] 2155 1914 1933 2134 2020 2056 2128 2043 2119 2151 1936 2038 2136 2214
    ## [25803] 2113 1955 2145 1934 2121 2159 2116 1956 2130 1953 2027 2005 2035 2129
    ## [25817] 1956 2150 1950 2041 2205 2031 2056 2153 2152 2218 2201 2250 2229 2057
    ## [25831] 2241 2056  127 2017 2215 2036 2227 2024 2042 2216 2049 2103 2037 2030
    ## [25845] 2133 2233 2207 2227 2102 2048 2230 2035 2216 2241 2113 2107   10 2301
    ## [25859] 2228 2239 2112 2122 2223 2150 2240 2103 2233 2239 2103 2251 2144 2249
    ## [25873] 2324 2311  107 2317 2252 2313 2259 2247 2306 2159 2246 2208 2204 2058
    ## [25887] 2154 2143 2127 2335 2247 2332 2111 2201 2312 2137 2128 2154 2142 2313
    ## [25901] 2256 2333 2324 2325 2342 2139 2133  110 2203 2336 2340 2227 2339 2202
    ## [25915]    1 2313 2305 2152   14   15 2210 2250 2209 2316 2207 2216 2343 2228
    ## [25929] 2326 2335    2 2353 2224 2318 2253    2 2227 2351 2327 2310 2243 2313
    ## [25943] 2253 2326   23 2352 2335 2250 2315 2400 2347   24   58 2314  127  132
    ## [25957]  107   50 2316  110    9    6 2343 2341 2338  149    9 2345   23   41
    ## [25971]  227   33   16  124  129   45   51  435  429   NA   NA   NA   NA   NA
    ## [25985]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [25999]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [26013]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [26027]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [26041]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [26055]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [26069]   NA   NA   NA   NA   NA   NA   NA   NA   NA  124  455  453  132  328
    ## [26083]  135  132  152  651  820  832 1019  851  641  828  900  726  743  848
    ## [26097]  913  909  840  720  919  725  707  921  708  908  911  712  926  805
    ## [26111]  812  752  748  924 1052  804  910  726  719  848  905  850  922  750
    ## [26125]  843  740  800  935  952  848  932  818  842  739 1011 1147 1004  909
    ## [26139]  953  806  957  906  807  813 1003 1045 1011  839 1028 1014 1042 1038
    ## [26153] 1033  829  922 1051 1027  946 1059 1007 1026 1032 1005  814 1035  933
    ## [26167] 1031 1004 1028 1012 1012  947  901  825  859  843 1049  928 1101 1001
    ## [26181] 1041 1051 1021 1118 1008 1000  857 1055 1125 1048  952 1233 1116 1028
    ## [26195] 1107 1059 1041  923 1047 1115  929 1241  946 1127  903 1056 1123  924
    ## [26209] 1042  920 1014 1107 1131 1021  919  955 1131 1000 1023 1052 1253  914
    ## [26223] 1026 1141 1041 1054 1022  955  945 1056 1133 1010  913 1022 1012 1113
    ## [26237] 1007 1150  955 1041 1047  936  956 1136 1140  930 1033 1151  945 1314
    ## [26251] 1055 1025 1117 1042 1306  943 1206  958 1211 1155 1141 1053 1210 1151
    ## [26265] 1350 1051 1002 1102 1234 1150 1108 1111 1227 1224 1208 1014 1235 1226
    ## [26279] 1220 1111 1222 1118 1138 1435 1230 1036 1040 1127 1117 1127 1229 1132
    ## [26293] 1219 1106 1134 1305 1112 1235 1120 1411 1210 1046 1241 1255 1242 1111
    ## [26307] 1040 1053 1147 1147 1308 1231 1112 1133 1306 1451 1227 1302 1214 1105
    ## [26321] 1140 1050 1051 1242 1256 1118 1217 1330 1315 1252 1303 1107 1234 1133
    ## [26335] 1319 1138 1241 1247 1251 1243 1341 1316 1202 1320 1236 1216 1401 1324
    ## [26349] 1355 1218 1314 1343 1305 1253 1343 1156 1351 1419 1148 1253 1234 1324
    ## [26363] 1359 1305 1224 1345 1148 1334 1331 1419 1233 1332 1338 1411 1401 1356
    ## [26377] 1202 1419 1214 1413 1210 1229 1213 1310 1311 1419 1230 1421 1600 1443
    ## [26391] 1245 1430 1315 1313 1314 1454 1413 1442 1315 1340 1433 1257 1252 1455
    ## [26405] 1318 1451 1453 1307 1334 1509 1455 1248 1356 1310 1258 1319 1300 1315
    ## [26419] 1305 1503 1329 1340 1344 1526 1519 1313 1352 1546 1536 1539 1340 1436
    ## [26433] 1520 1320 1427 1553 1543 1508 1546 1543 1503 1402 1620 1552 1456 1442
    ## [26447] 1515 1625 1525 1405 1414 1420 1407 1417 1416 1404 1538 1633 1634 1556
    ## [26461] 1446 1630 1416 1526 1554 1630 1808 1618 1613 1636 1439 1559 1705 1633
    ## [26475] 1514 1553 1915 1705 1657 1527 1714 1516 1703 1551 1657 1650 1717 1649
    ## [26489] 1545 1609 1726 1644 1642 1529 1532 1627 1553 1529 1735 1557 1752 1530
    ## [26503] 1808 1735 1733 1729 1658 1750 1536 1756 1610 1540 1800 1710 1800 1805
    ## [26517] 1803 1650 1645 1650 1811 1540 1635   NA 1804 1753 1623 1833 1802 1749
    ## [26531] 1813 1705 1607 1623 1637 1731 1630 1813 1719 1816 1709 1741 1830 1847
    ## [26545] 1820 1640 1611 1654 1745 1649 1850 1735 1845 1847 1833 1919 1715 1843
    ## [26559] 1655 1729 1742 1900 1812 1835 1859 1646 1903 1828 1643 2034 1735 1758
    ## [26573] 1905 1743 1914 1811 1714 1826 1751 1911 1832 1824 1937 1809 1930 1813
    ## [26587] 2035 1912 1902 1733 1922 1835 1919 1759 1736 1747 1958 1927 1922 1901
    ## [26601] 1848 1901 1937 1845 1827 1821 1946 1749 1808 1740 1744 1937 1823 1921
    ## [26615] 1937 1745 2010 1740 1750 1817 1830 2013 2003 1806 1925 1922 1902 1809
    ## [26629] 1843 1748 1956 1916 2019 2011 1820 1937 1818 2029 2044 1810 2020 2021
    ## [26643] 2025 2012 1805 2020 1949 2024 1815 2238 1935 1834 1827 2149 2014 1957
    ## [26657] 1947 2123 1958 1838 2009 2112 2045 2033 1908 2015 1902 1904 1859 1947
    ## [26671] 2050 1844 1903 1928 2030 1921 1916 2122 1834 2037 2049 2134 2047 2046
    ## [26685] 2057 2112 2125 1951 1945 2116 2141 2134 2121 2057 2137 2006 1922 2150
    ## [26699] 2110 2138 2204 2022 1912 2023 2022 2220 2016 2134 2006 2124 1923 2006
    ## [26713] 2203 2002 2043 2222 2154 2138 2144 2034 2151 2156 2126 2103 2038 2113
    ## [26727] 2116 2156 2034 2111 2034 2023 2152 2214 2031 2159 2241 2016 2036 2123
    ## [26741] 2131 2009 2223 2041 2221 2028 2229 2149 2004 2259 2224    5 2047 2143
    ## [26755] 2114 2250 2229 2308 2121 2101 2301 2232 2032 2218 2332 2120 2305 2228
    ## [26769] 2243 2157 2252 2154 2235 2244 2135 2121 2248 2311 2249 2053 2246 2311
    ## [26783] 2303 2333 2126 2233 2313 2104 2055 2229 2120 2327 2158 2235 2304 2142
    ## [26797] 2222 2312 2117 2127 2153 2318 2324 2332 2312 2205 2349 2330 2304 2355
    ## [26811] 2336 2134 2341 2211 2220 2342 2208 2343 2335 2306 2213    4 2328 2254
    ## [26825] 2313 2154  124 2145 2225 2252 2151 2210 2331 2348 2215 2304 2302 2332
    ## [26839] 2321 2143 2248 2344   17 2235 2217 2219 2241 2217 2317 2229 2331 2223
    ## [26853]   11 2229    5   13 2151 2319 2250 2242 2205 2223 2239 2228   16    8
    ## [26867] 2219 2357 2227   30   49   27   22 2258 2233 2234 2227 2235 2245 2228
    ## [26881] 2258 2325  109   38    5   58   53 2400 2328 2311   20 2355 2310 2323
    ## [26895] 2320 2253 2338 2345 2349 2346    2 2343   14   26  110   41  123   29
    ## [26909] 2337 2335  157   13  102  206    2   27    8   32   32  144   NA   NA
    ## [26923]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [26937]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [26951]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [26965]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [26979]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [26993]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA  614
    ## [27007]  735  809  801  917  912  653  648  649  727  710  655  834  829  811
    ## [27021]  757  831  810  810  737  851  726  650  757  743  831  719  706  735
    ## [27035]  751  722  744  719  843  738  808  837  800  719  720  713  808  735
    ## [27049]  851  854  822  721  843  757  857  913  749  829  818  756  917  809
    ## [27063]  820  807  825  742  856  743  846  758  903  827  738  839  804  903
    ## [27077]  744  925  847  758  929  849  921  821  853  900  755  848  912  930
    ## [27091]  937  928  939  946  826  941  947  808  855 1007  813  841 1044  935
    ## [27105]  827  948  937  934  844  949 1021 1051  942  956  814  904  931  950
    ## [27119] 1118 1005  914  918 1049  957 1018  857  925  852  933 1028 1032  949
    ## [27133]  931  923  932 1012 1038  945 1133  913 1015 1008  938  859  900  930
    ## [27147] 1014 1014  947  849  924 1047  859  938  913  950  920 1022 1046  928
    ## [27161]  945  954  928  909 1052 1032 1054  940  956 1040 1016 1102  913 1105
    ## [27175]  938  921 1026 1037  934 1030 1043 1012 1025 1050 1038 1108 1058 1151
    ## [27189] 1202  955 1110 1029  934 1008 1111  932 1007 1100 1109  947  949 1030
    ## [27203] 1030  946  948 1031  930  931 1022  930 1018 1105 1118  935 1057  958
    ## [27217] 1017 1021 1001 1003 1125  924 1115 1117 1017  942 1052 1101 1012 1008
    ## [27231] 1045 1122  954 1131 1030 1000 1007 1138 1019 1009 1217 1003 1149 1116
    ## [27245] 1226 1152 1058 1134 1211 1104 1136 1020 1109 1123 1147 1035 1012 1143
    ## [27259] 1110 1147 1142 1116 1152 1155 1016 1204 1046 1135 1159 1104 1117 1152
    ## [27273] 1115 1146 1025 1032 1204 1156 1022 1202 1048 1102 1111 1129 1113 1106
    ## [27287] 1203 1059 1136 1107 1116 1054 1058 1106 1123 1158 1052 1139 1156 1115
    ## [27301] 1300 1153 1201 1204 1155 1122 1145 1235 1128 1258 1124 1242 1236 1242
    ## [27315] 1137 1257 1135 1318 1207 1220 1215 1111 1157 1204 1121 1317 1222 1225
    ## [27329] 1300 1137 1219 1307 1320 1245 1231 1341 1300 1330 1155 1336 1256 1225
    ## [27343] 1338 1236 1218 1303 1213 1235 1308 1214 1201 1152 1333 1158 1205 1319
    ## [27357] 1338 1205 1344 1313 1406 1215 1311 1346 1353 1244 1258 1310 1219 1333
    ## [27371] 1320 1342 1352 1332 1403 1409 1332 1247 1245 1353 1311 1351 1256 1350
    ## [27385] 1418 1300 1345 1421 1436 1429 1320 1444 1426 1344 1302 1306 1317 1444
    ## [27399] 1407 1307 1419 1416 1441 1321 1355 1440 1326 1339 1320 1402 1350 1325
    ## [27413] 1345 1424 1427 1435 1358 1508 1358 1459 1334 1356 1423 1355 1349 1530
    ## [27427] 1430 1506 1413 1343 1400 1538 1359 1456 1532 1358 1443 1424 1445 1454
    ## [27441] 1437 1541 1522 1548 1423 1420 1529 1437 1448 1549 1444 1430 1514 1539
    ## [27455] 1600 1550 1553 1521 1600 1504 1551 1418 1443 1550 1519 1543 1512 1453
    ## [27469] 1608 1444 1446 1456 1820 1622 1458 1633 1627 1513 1457 1432 1532 1531
    ## [27483] 1559 1554 1444 1532 1455 1512 1458 1648 1559 1614 1545 1558 1637 1613
    ## [27497] 1559 1629 1505 1617 1543 1531 1615 1623 1713 1653 1541 1657 1523 1540
    ## [27511] 1634 1652 1525 1717 1535 1703 1553 1615 1534 1702 1642 1809 1621 1547
    ## [27525] 1619 1716 1543 1601 1650 1707 1725 1555 1705 1724 1635 1617 1640 1610
    ## [27539] 1717 1726 1719 1733 1751 1721 1612 1732 1649 1818 1602 1600 1612 1635
    ## [27553] 1617 1611 1724 1618 1751 1704 1643 1633 1630 1630 1701 1601 1749 1627
    ## [27567] 1817 1724 1737 1656 1616 1652 1856 1716 1736 1623 1709 1715 1701 1746
    ## [27581] 1709 1808 1709 1634 1741 1744 1821 1803 1820 1647 1630 1727 1628 1845
    ## [27595] 1832 1730 1817 1701 1755 1825 1637 1740 1820 1936 1708 1835 1844 1702
    ## [27609] 1815 1740 1819 1711 1845 1741 1705 1901 1659 1715 1706 1748 1801 1832
    ## [27623] 1830 1829 1721 1713 1707 1824 1903 1814 1743 1728 1833 1741 1756 1718
    ## [27637] 1809 1732 1715 1746 1805 1923 1915 1827 1806 1812 1845 1903 1755 1814
    ## [27651] 1724 1847 1751 1904 1808 1727 1741 1736 1836 1826 1834 1906 1835 1732
    ## [27665] 1908 1806 1926 1902 1935 1836 1929 1747 1842 1847 1912 1823 1933 1809
    ## [27679] 1814 1851 1831 1808 1930 1748 1757 1910 1815 1919 1922 1908 1911 1825
    ## [27693] 1841 1756 1824 1907 1939 2002 1917 1938 1952 1813 1926 1802 1926 1839
    ## [27707] 1838 1847 1810 1932 1818 1950 1943 1837 1938 1817 1933 1817 1830 1942
    ## [27721] 2000 1942 1828 1828 2016 1958 1912 1834 1914 2010 2029 1838 1953 1851
    ## [27735] 1901 1910 1943 1920 1919 1925 1921 1924 2025 1944 1946 2018 1909 2020
    ## [27749] 2011 1859 1915 1923 2007 1945 1936 1846 2102 1857 2007 2024 1958 2047
    ## [27763] 1946 1851 1904 1919 2007 1930 2040 2042 2007 1919 2050 2056 2101 1925
    ## [27777] 1958 2008 2047 1950 1948 2101 1922 1917 1955 2118 2033 2035 2110 2159
    ## [27791] 2015 2138 2142 2056 1958 2109 1946 2005 1936 1958 2104 2045 2140 2058
    ## [27805] 2032 2013 2130 2149 2115 2148 2009 2040 2012 2117 2030 1950 2030 2025
    ## [27819] 2007 1959 2110 2029 2114 2126 2149 2044 2118 2149 2054 2013 2127 2039
    ## [27833] 2122 2034 2128 2054 2128 2016 2056 2140 2203 2026 2123 2209 2114 2150
    ## [27847] 2205 2104 2157 2039 2227 2046 2136 2115 2124 2049 2101 2115 2129 2227
    ## [27861] 2145 2117 2113 2143 2226 2224 2113 2052 2216 2232 2209 2244 2124 2031
    ## [27875] 2058 2058 2153 2202 2111 2233 2144 2208 2213 2222 2241 2109 2216 2145
    ## [27889] 2142 2107 2112 2106 2202 2110 2139 2144 2236 2112 2145 2301 2221 2249
    ## [27903] 2136 2125 2222 2138 2227 2202 2319 2156 2130 2258 2220 2136 2150 2218
    ## [27917] 2306 2308 2127 2141 2142 2400 2234 2140 2221 2305 2143 2322 2219 2202
    ## [27931] 2344 2142 2215 2304 2215 2348 2324 2322 2159 2254 2218 2244 2310 2251
    ## [27945]    5 2318 2230 2232 2356 2217 2229    5  126 2244 2247 2254 2246 2348
    ## [27959] 2400 2352 2351 2359   15   17  335   NA   NA   NA   NA   NA  620  736
    ## [27973]  916  807  813  918  700  700  642  702  656  828  716  648  817  835
    ## [27987]  718  721  840  749  802  808  739  728  849  734  905  744  757  721
    ## [28001]  742  833  745  806  737  755  755  716  739  752  817  853  818  926
    ## [28015]  837  819  733  845  900  800  812  823  809  743  906  744  842  920
    ## [28029]  915  917  750  800  856  829  756  756  831  850  842  852  812  829
    ## [28043]  758  752  838  934  807  810  851  927 1024  826  939  801 1034  927
    ## [28057]  921  909  957  943 1000  748  954  950  932  928  852  940  940  831
    ## [28071]  951  827  943  953  924  914 1008  956  950  952 1016  858 1014  930
    ## [28085] 1101  829  852 1010  850 1034 1026 1012  921 1017  935  928  945  955
    ## [28099] 1112 1048 1021 1020  907 1042  909 1028  943 1033  919  852  847 1010
    ## [28113] 1020 1030  914  959 1021 1043  852 1032  916 1001  908 1012  907  943
    ## [28127]  946  945  957 1038  950 1007 1045 1006  926  911  918 1042 1111 1048
    ## [28141] 1016 1103  940 1045 1055  941 1036 1053 1120  948 1100 1100 1220 1138
    ## [28155] 1204 1031 1042  950 1006 1114 1115  946 1004 1028  942 1006  938 1022
    ## [28169] 1123 1026  936  948 1031 1040  928 1010 1021  952 1132 1003 1031 1035
    ## [28183] 1042 1049 1015  936 1136 1001 1134  957 1046 1006 1008 1000  956  955
    ## [28197] 1039 1157 1032 1146  950 1152 1246 1147 1114 1011 1121 1036 1024 1157
    ## [28211] 1113 1140 1207 1212 1211 1141 1046 1026 1021 1134 1056 1202 1027 1213
    ## [28225] 1100 1213 1104 1026 1115 1124 1148 1210 1128 1039 1215 1204 1130 1028
    ## [28239] 1034 1206 1206 1105 1214 1101 1046 1214 1218 1127 1147 1201 1143 1150
    ## [28253] 1149 1108 1056 1123 1150 1110 1056 1115 1438 1114 1210 1107 1143 1252
    ## [28267] 1215 1055 1108 1155 1131 1127 1214 1150 1200 1128 1129 1129 1300 1311
    ## [28281] 1335 1201 1302 1222 1141 1255 1206 1224 1312 1325 1224 1259 1322 1333
    ## [28295] 1229 1308 1228 1311 1331 1242 1211 1149 1218 1331 1200 1151 1200 1217
    ## [28309] 1224 1348 1323 1232 1323 1321 1156 1234 1600 1211 1401 1347 1217 1434
    ## [28323] 1236 1300 1315 1220 1353 1352 1344 1228 1323 1236 1340 1244 1325 1300
    ## [28337] 1315 1327 1336 1253 1316 1339 1412 1408 1420 1257 1427 1252 1345 1458
    ## [28351] 1319 1441 1250 1322 1433 1259 1442 1354 1314 1415 1305 1310 1445 1312
    ## [28365] 1452 1344 1258 1433 1346 1400 1354 1325 1335 1421 1321 1447 1329 1337
    ## [28379] 1341 1503 1444 1347 1412 1515 1541 1403 1531 1523 1419 1348 1506 1433
    ## [28393] 1344 1426 1449 1349 1516 1446 1501 1354 1522 1532 1454 1411 1450 1354
    ## [28407] 1413 1355 1432 1539 1544 1432 1513 1434 1358 1537 1548 1537 1450 1458
    ## [28421] 1508 1534 1606 1434 1459 1453 1424 1518 1515 1450 1444 1610 1534 1748
    ## [28435] 1600 1528 1520 1455 1600 1618 1626 1621 1558 1501 1455 1529 1643 1650
    ## [28449] 1620 1648 1549 1620 1511 1615 1554 1501 1652 1544 1556 1500 1456 1458
    ## [28463] 1604 1543 1459 1453 1555 1503 1550 1524 1611 1630 1524 1622 1642 1533
    ## [28477] 1639 1720 1532 1634 1732 1707 1709 1711 1611 1552 1538 1603 1550 1611
    ## [28491] 1613 1810 1621 1542 1720 1549 1730 1724 1605 1602 1656 1628 1707 1723
    ## [28505] 1731 1542 1654 1625 1735 1740 1728 1620 1602 1640 1713 1609 1654 1737
    ## [28519] 1716 1743 1642 1630 1557 1728 1826 1645 1718 1616 1801 1749 1755 1745
    ## [28533] 1658 1717 1758 1612 1652 1852 1752 1608 1833 1628 1710 1754 1755 1705
    ## [28547] 1621 1641 1723 1814 1731 1758 1650 1830 1834 1750 1642 1723 1724 1841
    ## [28561] 1742 1855 1652 1851 1709 1643 1841 1841 1828 1931 1701 1708 1743 1646
    ## [28575] 1740 1832 1653 1703 1732 1851 1843 1711 1856 1749 1720 1758 1830 1817
    ## [28589] 1738 1810 1703 1757 1833 1708 1905 1838 1850 1833 1702 1836 1729 1725
    ## [28603] 1711 1753 1828 1903 1728 1734 1734 1808 1816 1818 1945 1821 1738 1739
    ## [28617] 1728 1816 1734 1930 1726 1749 1829 1858 1900 1931 1830 1927 1904 1803
    ## [28631] 1745 1908 1905 1835 1936 1746 1822 1837 1925 1849 1831 1901 1843 1819
    ## [28645] 1836 1808 2006 1841 1834 1936 1805 1839 1825 1803 1931 2013 1800 1947
    ## [28659] 1823 1942 1919 1953 1808 1949 1919 1950 1935 1937 1916 1809 1842 1825
    ## [28673] 1813 1824 1853 1939 1815 1920 1810 1830 2006 1815 2008 2008 1940 2003
    ## [28687] 1953 2002 1839 1833 1912 1915 2009 1924 1910 2031 1837 1909 1917 2039
    ## [28701] 1845 1900 2036 2028 2001 1928 1908 2021 2048 1935 1910 1926 2026 1926
    ## [28715] 1958 2051 2020 2007 1904 2043 2028 1934 2120 1917 1942 2043 1927 1927
    ## [28729] 2058 2035 2054 2053 2022 1931 1957 1951 2013 2023 2124 2026 2023 1914
    ## [28743] 2123 2100 2122 2006 2112 1956 2006 1918 1956 2129 1943 2015 1934 2111
    ## [28757] 2009 2020 2040 2029 2032 2112 1950 2147 2127 2127 2054 2102 2048 1945
    ## [28771] 2128 2040 1951 2009 2145 2144 2038 2143 2113 2127 2028 2023 2106 2012
    ## [28785] 2202 2110 2045 1954 2058 2116 2138 2128 2152 2036 2120 2043 2121 2053
    ## [28799] 2159 2157 2030 2234 2106 2110 2013 2149 2058 2058 2051 2157 2113 2135
    ## [28813] 2224 2055 2103 2127 2048 2154 2152 2151 2207 2137 2224 2218 2217 2302
    ## [28827] 2117 2111 2237 2127 2236 2213 2227 2120 2040 2106 2254 2238 2207 2122
    ## [28841] 2109 2140 2243 2223 2122 2148 2157 2146 2231 2125 2236 2137 2059 2212
    ## [28855] 2240 2100 2159 2133 2157 2113 2154 2141 2137 2047 2109 2130 2242 2122
    ## [28869] 2230 2113 2215 2259 2132 2135 2239 2227 2121 2138 2222 2305 2322 2307
    ## [28883] 2146 2221 2322 2128 2141 2232 2138 2224 2259 2255 2153 2145 2335 2351
    ## [28897] 2219 2250 2227 2357 2325 2221 2233 2254 2250 2153 2219 2359   57 2341
    ## [28911] 2332 2204 2318 2218 2313    5 2305 2358 2311 2228   18 2301 2232 2329
    ## [28925] 2306 2300 2346   23  118 2240 2259 2345 2306 2257 2248 2319 2329 2346
    ## [28939] 2345 2359 2344 2400  157  324   NA  636  739  826  920  822  917  646
    ## [28953]  844  651  656  714  726  739  655  816  807  704  913  842  833  712
    ## [28967]  747  701  848  713  820  728  717  750  710  834  754  753  754  819
    ## [28981]  731  852  755  842  817  855  825  900  841  935  724  741  812  741
    ## [28995]  847  921  812  757  945  818  915  748  748  809  856  840  735  911
    ## [29009]  827  928  918  841  858  830  745  749  911  944  801 1035  903  809
    ## [29023]  806 1014  903  953  912 1011 1008 1031  931  816  951  802  950  956
    ## [29037] 1002 1002 1021 1000  954  937  945 1001  852 1020 1002  836  949 1021
    ## [29051]  951  958  940  958  925 1104  820 1013 1032  924  855 1042  859 1045
    ## [29065]  927  906  927  921 1020 1101  958 1111 1044 1042 1018 1032 1104  839
    ## [29079] 1133  914 1009  911  926  901 1002 1116 1017  937  907 1043  914 1028
    ## [29093] 1032 1020  929  949 1011  913 1006 1051  909  939 1118  941 1323 1137
    ## [29107] 1048  925 1105 1103 1009  937 1057 1058  930 1103 1052 1121 1053 1041
    ## [29121] 1006 1042 1100 1018 1205 1007 1100 1002 1212 1014 1015  930 1025 1110
    ## [29135] 1135  937  938  957  929 1126  931 1032 1036 1128 1047 1138  940 1020
    ## [29149] 1051 1002 1013 1002  931  959 1202 1043 1036 1043 1029 1003 1116 1129
    ## [29163]  945  959 1002 1138 1005  950  953 1125 1216 1152 1203 1056 1145 1000
    ## [29177] 1020 1150 1226 1010 1233 1010 1017 1206 1125 1127 1145 1032 1144 1200
    ## [29191] 1134 1022 1103 1156 1211 1131 1223 1126 1217 1027 1215 1210 1129 1030
    ## [29205] 1120 1149 1237 1225 1201 1059 1159 1031 1211 1121 1240 1216 1228 1220
    ## [29219] 1254 1130 1121 1109 1115 1249 1109 1140 1125 1152 1100 1136 1227 1056
    ## [29233] 1227 1219 1049 1132 1122 1133 1239 1110 1249 1200 1149 1136 1244 1336
    ## [29247] 1156 1142 1113 1203 1302 1314 1258 1132 1158 1253 1429 1354 1301 1237
    ## [29261] 1131 1251 1300 1309 1312 1353 1254 1323 1341 1310 1356 1334 1308 1158
    ## [29275] 1330 1344 1241 1234 1205 1208 1340 1243 1354 1250 1257 1323 1435 1217
    ## [29289] 1200 1337 1410 1357 1240 1229 1402 1414 1336 1220 1401 1420 1310 1357
    ## [29303] 1307 1408 1327 1406 1412 1237 1410 1432 1439 1346 1442 1449 1249 1404
    ## [29317] 1444 1345 1453 1504 1420 1328 1515 1259 1434 1446 1407 1338 1316 1305
    ## [29331] 1402 1443 1316 1439 1359 1522 1347 1346 1334 1332 1421 1433 1336 1423
    ## [29345] 1333 1341 1437 1501 1342 1418 1331 1440 1526 1417 1340 1335 1436 1419
    ## [29359] 1440 1425 1408 1348 1521 1530 1429 1516 1404 1533 1517 1343 1418 1624
    ## [29373] 1531 1354 1531 1442 1409 1439 1502 1601 1402 1505 1547 1351 1558 1544
    ## [29387] 1542 1604 1452 1556 1415 1415 1541   NA 1420 1531 1503 1444 1609 1453
    ## [29401] 1612 1544 1613 1453 1434 1547 1546 1556 1606 1600 1534 1633 1629 1502
    ## [29415] 1645 1608 1627 1630 1803 1457 1519 1636 1527 1624 1533 1508 1501 1447
    ## [29429] 1504 1557 1532 1509 1455 1630 1559 1648 1618 1718 1543 1544 1605 1613
    ## [29443] 1624 1709 1527 1642 1614 1514 1651 1726 1618 1615 1612 1713 1541 1645
    ## [29457] 1621 1646 1655 1741 1757 1620 1816 1614 1600 1550 1648 1720 1558 1822
    ## [29471] 1720 1730 1633 1757 1702 1753 1543 1702 1632 1738 1650 1620 1627 1758
    ## [29485] 1556 1639 1702 1611 1640 1741 1750 1739 1624 1744 1646 1736 1755 1757
    ## [29499] 1708 1716 1701 1723 1726 1651 1824 1556 1813 1623 1757 1806 1728 1757
    ## [29513] 1701 1754 1657 1856 1752 1655 1745 1636 1625 1753 1724 1826 1625 1838
    ## [29527] 1802 1813 1819 1731 1707 1716 1702 1747 1857 1650 1845 1838 1700 1716
    ## [29541] 1736 1731 1841 1753 1729 1838 1725 1709 1835 1802 1856 1817 1823 1821
    ## [29555] 1921 1748 1655 1804 1832 1657 1907 1921 1734 1737 1913 1817 1710 1759
    ## [29569] 1835 1848 1756 1906 1814 1737 1852 1800 1727 1844 1832 1846 1752 1851
    ## [29583] 1853 1726 1858 1846 1747 1940 1727 1911 1808 1915 1838 1748 1755 1847
    ## [29597] 1804 1935 1953 1918 1951 1753 1823 1910 1932 1815 1912 1937 1824 1940
    ## [29611] 1856 1826 1836 1922 1859 1844 1843 1836 1909 1939 2010 1823 1854 1838
    ## [29625] 1833 1925 1818 1903 2001 1808 1935 2002 1956 1943 1900 1835 2009 1939
    ## [29639] 1811 1947 1831 2019 1808 2032 1952 1901 2020 1950 1943 1953 2018 1919
    ## [29653] 1833 1922 1827 1849 1957 1812 1922 1825 1835 2006 1949 1848 1830 2012
    ## [29667] 1907 1829 2001 2030 1840 2012 2039 1931 2002 1915 2044 1929 2045 1930
    ## [29681] 2000 2018 1946 1858 2027 1929 1923 2014 1933 1852 2044 1955 1937 1906
    ## [29695] 2017 2034 1934 2021 1913 1902 2003 2046 2052 2036 2026 2056 2013 2112
    ## [29709] 2003 2000 1930 2026 1950 2007 2056 2047 2110 2138 1925 1926 2013 2019
    ## [29723] 2022 2111 2100 2136 2124 2136 2008 2032 1925 1958 2001 2132 2009 2039
    ## [29737] 2124 1951 2130 2053 2031 2126 2026 2114 2009 2144 2016 2006 2036 1955
    ## [29751] 2015 2217 2046 2043 2037 2214 2155 2104 2152 2053 2104 2035 2006 2205
    ## [29765] 2043 2040 2128 2051 2002 2118 2118 2115 2105 2137 2213 2019 2031 2043
    ## [29779] 2027 2219 2032 2227 2153 2133 2134 2056 2202 2029 2152 2136 2220 2140
    ## [29793] 2122 2155 2244 2145 2221 2045 2206 2158 2042 2107 2213 2116 2143 2054
    ## [29807] 2216 2124 2203 2210 2059 2134 2136 2227 2104 2244 2105 2054 2240 2138
    ## [29821] 2224 2234 2107 2037 2206 2147 2236 2138 2248 2149 2321 2232 2120 2105
    ## [29835] 2231 2312 2206 2230 2231 2129 2300 2236 2139 2153 2102 2122 2201 2122
    ## [29849] 2120 2108 2227 2130 2136 2207 2114 2142 2356 2307 2156 2209 2333 2344
    ## [29863] 2330 2134 2136 2248 2317 2330 2224 2319 2248 2147 2335 2149 2220 2206
    ## [29877] 2209 2338 2307 2151    8 2240 2245 2323 2330 2358    5 2212 2212 2313
    ## [29891] 2302   44 2243 2308 2328 2317 2238 2344 2257 2353 2252   10 2235 2258
    ## [29905] 2247 2357 2327   50 2315 2358   58 2305 2255  132 2252 2348 2312 2315
    ## [29919] 2326 2400 2332 2331 2317 2338 2339 2335 2343   27 2355 2352 2348    5
    ## [29933]    8    9  152  118  331   NA   NA   NA  350  628  913  830  810  703
    ## [29947]  932  651  903  655  703  840  801  740  829  745  814  847  727  810
    ## [29961]  845  706  710  715  738  717  846  723  736  749  724  808  742  756
    ## [29975]  808  821  825  815  903  830  858  815  750  853  823  730  917  758
    ## [29989]  751  843  820  854  738  850  827  904  745  752  902  945  822  855
    ## [30003]  910  908  750  918  854  752  853  917  905 1008 1042 1022  945  759
    ## [30017]  852  923  820  756  940  911  929 1021  820  858  948  803  941 1005
    ## [30031]  931  812  828 1024  942  832  949  952 1013  910  842 1000 1008 1015
    ## [30045]  946  936  918 1024  813  956  909  842 1008  943 1059 1002  915  921
    ## [30059] 1016 1009  903 1046 1016  954 1005 1025  936 1022  914 1126  931 1014
    ## [30073] 1008  902  912 1023 1005  852 1102 1034  916  855  913  905  927 1029
    ## [30087] 1003  943 1052 1026 1046  859 1006 1050  932  916 1036 1005  904 1052
    ## [30101] 1040  909 1107 1102 1023 1051 1116 1100 1050 1045 1039 1039 1057 1118
    ## [30115]  953  959 1015  950 1015 1003 1009  949  942 1023 1005 1053 1044 1143
    ## [30129]  951  939 1229 1141 1136 1017 1205 1051 1127  939 1133  938  933 1046
    ## [30143] 1000  950  932  949 1022 1041 1123 1030  944  940 1013 1030 1002 1138
    ## [30157] 1051 1012  956 1021 1108 1143 1018  952 1030 1008 1121 1015 1223 1200
    ## [30171] 1041 1231 1207 1000  958 1148 1141 1211 1125 1104 1157 1032 1110 1024
    ## [30185] 1200 1018 1210 1054 1021 1155 1209 1041 1130 1148 1106 1205 1210 1230
    ## [30199] 1137 1239 1031 1109 1116 1142 1200 1213 1121 1211 1202 1248 1201 1044
    ## [30213] 1220 1058 1107 1243 1121 1129 1148 1246 1119 1102 1105 1124 1149 1159
    ## [30227] 1133 1123 1105 1200 1438 1048 1135 1216 1124 1300 1104 1130 1205 1311
    ## [30241] 1201 1145 1125 1225 1300 1221 1151 1201 1123 1245 1248 1247 1138 1128
    ## [30255] 1235 1330 1214 1247 1313 1336 1306 1311 1224 1251 1136 1347 1157 1207
    ## [30269] 1253 1343 1312 1224 1323 1315 1227 1157 1204 1339 1332 1217 1202 1348
    ## [30283] 1205 1209 1240 1354 1334 1337 1154 1315 1224 1352 1343 1237 1417 1315
    ## [30297] 1229 1231 1255 1414 1257 1346 1401 1217 1313 1400 1325 1429 1349 1346
    ## [30311] 1315 1405 1404 1426 1421 1407 1515 1353 1256 1258 1501 1332 1255 1441
    ## [30325] 1428 1436 1347 1316 1327 1316 1513 1429 1451 1453 1310 1309 1354 1321
    ## [30339] 1305 1433 1455 1334 1441 1428 1430 1322 1513 1319 1403 1406 1433 1343
    ## [30353] 1355 1440 1344 1411 1421 1513 1517 1456 1416 1504 1357 1459 1352 1514
    ## [30367] 1432 1438 1533 1355 1418 1532 1610 1530 1454 1554 1600 1359 1441 1407
    ## [30381] 1553 1415 1527 1507 1449 1549 1416 1531 1624 1358 1524 1411 1415 1414
    ## [30395] 1432 1518 1458 1451 1450 1500 1507 1608 1454 1516 1420 1549 1556 1515
    ## [30409] 1546 1545 1615 1622 1547 1551 1452 1554 1552 1445 1615 1500 1756 1651
    ## [30423] 1538 1450 1633 1637 1609 1535 1506 1536 1441 1614 1526 1527 1512 1521
    ## [30437] 1603 1709 1606 1508 1459 1630 1616 1547 1537 1517 1615 1629 1631 1623
    ## [30451] 1540 1729 1646 1632 1541 1543 1518 1730 1526 1648 1533 1538 1552 1718
    ## [30465] 1712 1616 1809 1758 1636 1709 1712 1611 1724 1734 1551 1637 1613 1621
    ## [30479] 1724 1644 1645 1639 1633 1710 1734 1619 1734 1605 1626 1744 1720 1606
    ## [30493] 1717 1614 1611 1734 1706 1637 1747 1606 1644 1549 1642 1614 1743 1713
    ## [30507] 1741 1742 1756 1604 1721 1704 1624 1751 1743 1733 1859 1645 1726 1710
    ## [30521] 1802 1757 1825 1830 1720 1758 1804 1715 1657 1821 1647 1812 1635 1847
    ## [30535] 1734 1744 1638 1833 1842 1818 1652 1716 1649 1833 1710 1735 1708 1935
    ## [30549] 1755 1711 1752 1840 1651 1721 1846 1837 1658 1812 1738 1822 1657 1702
    ## [30563] 1836 1827 1821 1731 1706 1823 1837 1710 1724 1828 1827 1906 1726 1759
    ## [30577] 1755 1729 1727 1911 1727 1734 1723 1823 1902 1916 1814 1732 1836 1721
    ## [30591] 1925 1828 1850 1818 1843 1857 1919 1827 1753 1858 1833 1757 1913 1806
    ## [30605] 1938 2009 1835 1829 1806 1756 1908 1839 1901 1824 1901 1829 1820 2016
    ## [30619] 1834 1757 1842 1835 2009 1859 1816 1935 1907 1954 1928 1810 1959 1938
    ## [30633] 2005 1821 1837 2017 2016 1828 2014 1934 1914 1856 1828 2029 1928 1828
    ## [30647] 1826 1941 1923 1827 1821 2030 1858 1958 1936 2016 1957 1837 1913 1908
    ## [30661] 1851 2103 2013 2006 2008 1921 1850 1829 1841 2028 1915 1942 1951 2100
    ## [30675] 1837 1850 2055 2017 2107 2022 1905 1951 2047 1948 2030 1915 1934 2021
    ## [30689] 1946 2000 1914 2016 2058 1859 1859 2022 2045 2056 2055 1934 1959 2044
    ## [30703] 1945 2012 2054 1922 2040 1945 1944 2103 2026 2007 2017 2051 2106 2121
    ## [30717] 2101 2129 2009 2100 2016 2109 1921 2002 2049 1949 2011 2143 2028 2046
    ## [30731] 2114 1913 2136 2111 2026 2059 2010 2018 2045 1944 2104 2015 2035 2217
    ## [30745] 2111 2051 2147 2144 2204 1951 2045 2024 2056 2129 2010 2017 2213 2002
    ## [30759] 2201 2212 2016 2048 2130 2000 2008 2000 2233 2114 2058 2238 2057 2054
    ## [30773] 2051 2100 2126 2147 2248 2142 2240 2132 2158 2119 2047 2115 2129 2051
    ## [30787] 2205 2153 2101 2122 2143 2251 2249 2151 2211 2205 2104 2121 2105 2203
    ## [30801] 2213 2210 2125 2216 2212 2120 2159 2246 2109 2206 2202 2145 2216 2108
    ## [30815] 2249 2221 2156 2039 2154 2210 2342 2103 2311 2235 2111 2254 2107 2127
    ## [30829] 2123 2318 2143 2109 2235 2136 2319 2210 2241 2307 2223 2130 2156 2251
    ## [30843] 2256 2134 2110 2133 2157 2202 2145 2304 2337 2156 2213 2138 2237 2246
    ## [30857] 2312 2314 2251 2239 2354 2128 2146 2241 2309 2332 2201 2309 2202 2205
    ## [30871] 2159 2156 2204 2207 2149 2326 2325    2 2259 2345 2204 2317 2307 2334
    ## [30885] 2254   11   40 2228 2231 2321 2355 2257 2250 2248   10 2237 2237 2225
    ## [30899] 2338   32 2242 2306    6 2356 2341 2251 2241 2359 2324    9   40 2252
    ## [30913] 2327  128 2303    4 2308 2307 2339 2342 2356 2346  115 2351   10 2359
    ## [30927]  111   10  121   NA   NA   NA   NA   NA   NA  624  747  827  813  920
    ## [30941]  826  712  832  924  703  845  832  651  810  847  813  901  720  744
    ## [30955]  750  712  912  823  759  806  816  821  737  819  808  902  910  804
    ## [30969]  755  837  903  818  857  757  903  913  855  744  906  908 1018  951
    ## [30983]  918  823  844  935  950  904 1036  856  914  932 1010  959  819  826
    ## [30997]  948 1009  929 1009  809  929 1005  943 1014  949 1002  949  953  826
    ## [31011]  910 1015 1101 1016  840  814 1011  858 1021 1025 1001  900 1023  958
    ## [31025]  930 1022 1017 1141  937  946 1035  918 1022  918 1038  903  939 1021
    ## [31039] 1033  922  902  905  940  923  916 1101  857  959 1049 1049 1031 1051
    ## [31053]  956 1041  916 1151  927  930  939 1012 1049 1033 1100 1038  949 1051
    ## [31067]  951 1109 1033 1002 1054  958 1000 1213 1105 1017  941 1108 1026 1112
    ## [31081] 1202 1019 1043 1035 1115 1101 1009  945  937 1104  947 1128  928  935
    ## [31095] 1025 1003  959  942 1130 1004 1009  953 1050 1219 1152 1109 1017 1109
    ## [31109] 1152 1108 1135 1141 1041 1151 1140 1149 1212 1041 1002 1015 1056 1137
    ## [31123] 1155 1202 1008 1142 1029 1154 1159 1216 1040 1116 1207 1201 1239 1155
    ## [31137] 1050 1220 1132 1113 1347 1229 1102 1059 1141 1240 1057 1133 1206 1128
    ## [31151] 1103 1255 1100 1102 1321 1203 1220 1200 1418 1220 1302 1155 1144 1241
    ## [31165] 1122 1253 1235 1219 1317 1310 1204 1141 1124 1312 1227 1243 1151 1249
    ## [31179] 1146 1319 1132 1303 1248 1330 1236 1249 1329 1203 1157 1300 1327 1217
    ## [31193] 1154 1220 1321 1330 1245 1241 1314 1202 1302 1319 1336 1401 1315 1244
    ## [31207] 1408 1408 1228 1351 1224 1334 1224 1347 1239 1340 1247 1324 1310 1332
    ## [31221] 1219 1415 1259 1245 1335 1427 1354 1431 1359 1431 1309 1339 1426 1249
    ## [31235] 1413 1254 1435 1502 1448 1323 1430 1338 1444 1301 1349 1445 1447 1511
    ## [31249] 1349 1323 1504 1341 1416 1505 1324 1424 1435 1354 1527 1516 1433 1441
    ## [31263] 1413 1421 1443 1529 1349 1449 1408 1359 1433 1536 1352 1530 1506 1404
    ## [31277] 1451 1522 1553 1525 1415 1527 1507 1438 1430 1519 1449 1430 1547 1416
    ## [31291] 1618 1606 1609 1621 1525 1550 1747 1549 1524 1606 1615 1609 1442 1610
    ## [31305] 1639 1559 1626 1528 1533 1542 1620 1636 1625 1604 1623 1452 1509 1550
    ## [31319] 1528 1507 1705 1612 1538 1545 1535 1634 1524 1658 1716 1525 1633 1629
    ## [31333] 1718 1654 1816 1601 1546 1645 1640 1725 1631 1740 1604 1636 1640 1719
    ## [31347] 1739 1639 1558 1554 1559 1719 1621 1753 1735 1727 1727 1646 1703 1635
    ## [31361] 1639 1750 1641 1654 1730 1658 1723 1712 1634 1745 1735 1715 1734 1947
    ## [31375] 1622 1624 1701 1721 1710 1907 1640 1655 1643 1705 1816 1830 1633 1809
    ## [31389] 1802 1848 1827 1831 1820 1745 1821 1822 1653 1929 1649 1825 1841 1753
    ## [31403] 1832 1733 1726 1747 1819 1824 1719 1841 1704 1831 1821 1857 1900 1708
    ## [31417] 1813 1850 1728 1847 1743 1856 1841 1736 1904 1745 1849 1905 1825 1819
    ## [31431] 1730 1729 1841 1816 1905 1914 2008 1829 1732 1950 1921 1757 1821 1917
    ## [31445] 1915 1933 1914 1825 1855 1904 1751 2016 1930 1927 1835 1857 2001 1859
    ## [31459] 1951 1838 2031 2017 1932 1922 1936 2010 1954 1808 2004 1924 1823 1847
    ## [31473] 1841 1924 1951 1955 2022 1809 1822 1848 1817 1907 1824 2021 2023 1901
    ## [31487] 2013 1850 1833 2022 1952 1836 1853 2035 2001 2002 1918 2037 1955 1912
    ## [31501] 1926 2032 2030 2008 1914 2029 2017 2007 2102 2034 2017 2026 2034 1910
    ## [31515] 2022 2102 1924 2000 1930 2016 2100 2013 2054 2006 1932 1952 1912 2049
    ## [31529] 1916 2101 2050 2023 1937 2136 2102 2019 2128 2121 1954 2118 2009 2156
    ## [31543] 2125 2205 2150 2017 2203 2043 2045 2129 2129 2112 2056 2105 2159 2137
    ## [31557] 2010 2131 2133 2239 2216 2215 2153 2014 2152 2049 2226 2226 2216 2041
    ## [31571] 2249 2241 2206 2129 2111 2221 2217 2113 2209 2229 2226 2105 2107 2240
    ## [31585] 2139 2112 2131 2114 2253 2257 2119 2232 2134 2210 2123 2211 2323 2325
    ## [31599] 2206 2344 2252   33 2400    5 2337 2213 2314 2353 2302 2229 2332  109
    ## [31613]   32 2254 2257 2318 2335 2349 2400 2348  105  325  742  925  820  704
    ## [31627]  812  845  844  650  703  814  741  709  846  718  845  742  753  744
    ## [31641]  727  850  820  808  848  917  809  908  849  815  825  916  912  858
    ## [31655]  814  921  914  859  751  749  915  924  923 1037  858  949  933  949
    ## [31669] 1042 1011 1007  810  814 1004 1003  952  949  837  925  936  825  809
    ## [31683]  945  943  809 1011  917  832  916 1005 1110 1023 1013 1022 1026 1050
    ## [31697] 1056 1012  952 1125  939 1023 1015 1052 1041 1045  931  939 1018  945
    ## [31711]  930  901  901 1025  930  931 1046  942  958  934  904  906 1047  924
    ## [31725]  946 1136  848 1113 1043 1026  925 1023 1046 1045 1013 1142 1045 1135
    ## [31739] 1055 1047  957  950 1044  939 1028  947 1043 1053 1036 1029 1106 1002
    ## [31753] 1201  935 1038 1107 1040 1016 1135  949 1105 1013 1100 1015 1127  924
    ## [31767] 1029 1009 1204  957 1042  940 1042 1030 1101  940 1007  941 1123 1033
    ## [31781] 1140 1043 1027 1001 1130  946 1122  948 1055 1104 1114 1224 1148 1152
    ## [31795] 1019 1141 1108 1045 1124 1152 1029 1042 1158 1100 1200 1113 1200 1024
    ## [31809] 1123 1131 1009 1222 1209 1207 1152 1222 1132 1131 1146 1022 1239 1215
    ## [31823] 1020 1131 1217 1201 1142 1057 1229 1237 1248 1200 1105 1109 1109 1133
    ## [31837] 1138 1228 1250 1147 1109 1209 1116 1202 1108 1142 1305 1218 1119 1238
    ## [31851] 1109 1415 1108 1214 1244 1123 1245 1158 1132 1155 1207 1250 1249 1157
    ## [31865] 1311 1221 1229 1115 1142 1332 1309 1319 1206 1242 1153 1336 1239 1219
    ## [31879] 1230 1302 1227 1323 1326 1337 1322 1244 1151 1206 1218 1257 1224 1155
    ## [31893] 1337 1207 1330 1313 1354 1241 1238 1342 1328 1223 1346 1201 1221 1408
    ## [31907] 1346 1349 1231 1349 1303 1329 1232 1229 1407 1314 1241 1224 1332 1258
    ## [31921] 1408 1317 1424 1223 1338 1419 1346 1417 1246 1426 1242 1439 1253 1346
    ## [31935] 1436 1435 1323 1407 1345 1331 1500 1305 1435 1308 1356 1322 1439 1359
    ## [31949] 1309 1418 1428 1336 1456 1431 1502 1327 1319 1324 1341 1409 1331 1401
    ## [31963] 1346 1506 1448 1444 1332 1421 1436 1419 1402 1412 1350 1418 1538 1521
    ## [31977] 1528 1521 1439 1446 1403 1535 1444 1539 1529 1530 1400 1420 1401 1441
    ## [31991] 1400 1532 1537 1414 1409 1436 1415 1517 1552 1546 1418 1443 1556 1438
    ## [32005] 1440 1451 1509 1445 1550 1549 1503 1533 1504 1423 1600 1622 1418 1603
    ## [32019] 1609 1503 1432 1559 1559 1536 1523 1810 1550 1637 1503 1443 1537 1518
    ## [32033] 1618 1629 1635 1525 1544 1441 1457 1604 1521 1547 1621 1629 1449 1605
    ## [32047] 1457 1635 1521 1509 1503 1515 1511 1604 1640 1545 1648 1515 1522 1619
    ## [32061] 1622 1610 1701 1606 1633 1603 1718 1707 1553 1702 1711 1702 1721 1605
    ## [32075] 1532 1532 1643 1617 1702 1717 1607 1648 1704 1633 1821 1601 1636 1730
    ## [32089] 1637 1540 1533 1759 1720 1715 1652 1609 1629 1620 1755 1538 1602 1624
    ## [32103] 1733 1733 1639 1648 1720 1703 1723 1611 1658 1645 1738 1755 1743 1641
    ## [32117] 1745 1612 1738 1710 1804 1703 1633 1740 1705 1910 1805 1702 1612 1656
    ## [32131] 1813 1641 1828 1627 1747 1731 1653 1714 1843 1702 1717 1646 1634 1734
    ## [32145] 1718 1656 1855 1853 1812 1821 1722 1705 1643 1819 1814 1726 1705 1713
    ## [32159] 1755 1752 1743 1825 1755 1838 1704 1827 1858 1714 1721 1832 1857 1704
    ## [32173] 1712 1842 1736 1733 1734 1828 1838 1713 1838 1727 1711 1720 1900 1850
    ## [32187] 1928 1859 1914 1757 1746 1733 1802 1841 1909 1949 1819 2008 1815 1756
    ## [32201] 1738 1817 1836 1914 1827 1829 1743 1932 1905 1812 1858 1805 1859 1920
    ## [32215] 1803 1833 1751 1802 1916 1932 1830 1845 1841 1840 1818 1820 1849 1837
    ## [32229] 1949 1943 1925 1859 1936 1757 1913 1852 1943 1933 1841 1812 1912 1953
    ## [32243] 1939 1947 1936 1846 2003 1815 1815 1858 1855 1828 1830 2026 1850 1937
    ## [32257] 2001 2031 1905 1839 2004 2001 1845 1856 1946 2006 1918 1827 2004 2006
    ## [32271] 1901 1959 2001 1848 1939 1939 1906 2006 2028 1855 2044 1957 1914 1913
    ## [32285] 2030 1910 2025 1852 1920 1922 2017 1936 1921 1933 2043 2019 1923 1854
    ## [32299] 2032 1943 1944 1928 2035 2007 2042 1923 1915 2048 2108 2045 2023 2043
    ## [32313] 1858 2103 2026 1950 1912 1916 1919 2032 2036 2029 2031 1947 1924 2051
    ## [32327] 2102 2002 2040 2135 2050 2136 2001 2149 1958 1951 2113 2118 1946 1936
    ## [32341] 2020 2031 1925 2010 2026 1955 2058 2127 2032 2119 2146 2013 2107 2202
    ## [32355] 2006 2142 2111 1940 2019 2133 2057 2150 2027 2124 2117 2000 2143 2059
    ## [32369] 2204 2046 2028 2045 2025 2221 2013 2028 2132 2148 2140 2105 2052 2232
    ## [32383] 2050 2127 2155 2015 2129 2214 2147 2148 2229 2222 2029 2050 2153 2018
    ## [32397] 2034 2223 2242 2208 2219 2111 2258 2202 2246 2205 2036 2213 2213 2246
    ## [32411] 2130 2130 2050 2049 2057 2253 2311 2121 2107 2138 2230 2134 2158 2139
    ## [32425] 2230 2255 2154 2139 2247 2130 2151 2241 2211 2218 2300 2113 2250 2234
    ## [32439] 2118 2257 2109 2200 2256 2134 2243 2121 2150 2213 2236 2136 2147 2133
    ## [32453] 2254 2233 2159 2151 2307 2304 2322 2359 2151 2223 2137 2158 2156 2133
    ## [32467] 2218 2319 2339 2155 2216 2146 2211 2207 2301 2331 2159 2341 2201 2210
    ## [32481] 2215    4 2339 2330 2210 2239 2257 2236 2305 2206 2156 2314 2341 2331
    ## [32495] 2231 2337   46 2359 2325 2352    2 2323 2229 2336 2306 2300 2305 2233
    ## [32509] 2255    3 2244 2338    2 2241   25 2259 2314  144 2300 2318 2300 2351
    ## [32523]  102   47   11   20 2321 2328   40 2331 2346 2341 2351 2356   28  333
    ## [32537]   NA   NA   NA   57  109  318  126  130  209  634  759  826  920  813
    ## [32551]  917  718  700  834  658  713  836  739  852  652  702  736  703  839
    ## [32565]  830  908  819  832  708  727  749  719  809  740  758  745  740  751
    ## [32579]  846  759  711  818  909  839  820  904  912  909  733  741  812  847
    ## [32593]  823  859  740  908  830  811  921  735  818  753  909  844  754  811
    ## [32607]  850  914 1019  849  804  921  926  853  917  743  843  900  900  832
    ## [32621]  818  928  802  812  930  854 1033  940  956  945  755  827  950  953
    ## [32635] 1002  939  821  938  947  818 1001 1000 1006  947 1006  854  952  958
    ## [32649]  832  948  810  932  827 1143 1004 1013 1021 1000 1021  851 1108  920
    ## [32663] 1029 1026  924 1029  928 1040 1022  855 1033 1004 1001  927 1035 1112
    ## [32677] 1015  938 1030 1022  851 1030  907 1138  924  942  918  947  856  926
    ## [32691]  949  928 1044 1013  853 1031  919  950  908 1030 1048  956 1037 1044
    ## [32705] 1021 1057  910 1102  931 1105 1042  924 1058 1039 1049 1138 1054 1047
    ## [32719] 1204 1052 1042 1112 1007 1115 1158 1029 1051 1040 1117  929 1239 1011
    ## [32733] 1125 1118  959 1032 1013 1133 1015  954 1004 1025  944  937 1055  934
    ## [32747] 1127  933  951 1024 1018 1040 1005 1124  949  958 1004 1000 1125 1107
    ## [32761] 1002 1006 1030 1147 1043 1238 1148 1004 1008 1124 1010 1046 1030 1013
    ## [32775] 1126 1144 1148 1144 1012 1202 1145 1211 1116 1146 1122 1152 1142 1133
    ## [32789] 1154 1005 1220 1105 1057 1042 1156 1209 1147 1148 1213 1203 1138 1038
    ## [32803] 1206 1221 1024 1017 1230 1153 1230 1224 1125 1223 1201 1222 1114 1138
    ## [32817] 1126 1217 1235 1203 1101 1216 1056 1205 1258 1215 1201 1241 1136 1140
    ## [32831] 1053 1108 1140 1222 1122 1254 1124 1120 1236 1207 1237 1107 1235 1504
    ## [32845] 1249 1209 1138 1135 1254 1230 1154 1145 1131 1307 1207 1326 1313 1124
    ## [32859] 1204 1155 1240 1207 1325 1321 1306 1240 1319 1154 1305 1317 1130 1308
    ## [32873] 1315 1252 1243 1242 1358 1336 1156 1309 1246 1340 1406 1335 1252 1257
    ## [32887] 1342 1213 1224 1308 1239 1215 1410 1342 1306 1250 1314 1338 1426 1419
    ## [32901] 1253 1335 1431 1254 1255 1253 1320 1311 1243 1431 1403 1327 1343 1359
    ## [32915] 1303 1306 1312 1306 1353 1445 1429 1452 1432 1446 1417 1346 1431 1411
    ## [32929] 1418 1315 1449 1507 1309 1439 1454 1311 1448 1404 1530 1456 1305 1516
    ## [32943] 1348 1425 1502 1415 1347 1329 1459 1435 1441 1500 1336 1432 1428 1430
    ## [32957] 1330 1502 1450 1513 1333 1553 1530 1637 1351 1549 1524 1641 1413 1505
    ## [32971] 1601 1557 1503 1431 1530 1556 1613 1551 1648 1536 1500 1428 1516 1413
    ## [32985] 1603 1430 1524 1424 1538 1458 1615 1616 1617 1631 1457 1542 1420 1614
    ## [32999] 1626 1637 1537 1514 1616 1901 1527 1712 1640 1616 1434 1553 1706 1600
    ## [33013] 1736 1716 1654 1546 1457 1813 1553 1649 1858 1656 1724 1510 1659 1804
    ## [33027] 1736 1746 1652 1749 1631 1712 1700 1723 1702 1731 1741 1652 1735 1718
    ## [33041] 1533 1726 1836 1723 1731 1806 1817 1833 1815 1721 1900 1629 1603 1743
    ## [33055] 1709 1724 1558 1804 1751 1640 1640 1649 1754 1726 1852 1908 1832 1826
    ## [33069] 1833 1755 1748 1711 1706 1845 1828 1620 1658 1844 1838 1904 1820 1757
    ## [33083] 1921 1734 1901 1847 1759 1810 1851 1754 1830 1840 1756 1900 1708 1824
    ## [33097] 1757 1816 1915 1917 1802 1903 1849 1843 1734 1935 1714 1955 1837 1754
    ## [33111] 1922 2014 1902 1907 1806 1756 1719 1930 1756 1909 1949 1938 1918 1859
    ## [33125] 1842 1805 1808 2017 1824 1813 1803 1820 1924 1839 1946 1848 2024 1942
    ## [33139] 1909 1923 1819 1901 2035 1943 1843 1944 2020 2016 1916 1959 2033 2000
    ## [33153] 2028 1928 1809 1917 2011 2014 1824 2021 1956 2010 2005 1933 2043 1944
    ## [33167] 2034 2016 2017 2047 1943 2039 1900 1906 2028 2014 1934 1950 2040 1858
    ## [33181] 1951 2111 2050 1932 1909 2111 1916 1941 2003 1942 2041 2010 2027 1920
    ## [33195] 2040 2049 2019 1916 1932 2047 2015 2036 2020 1928 2121 2038 2056 2104
    ## [33209] 1931 2021 2052 2034 2132 1957 2124 2120 2024 2124 2125 2024 2107 2145
    ## [33223] 2136 2122 2119 2041 1959 1956 2134 2014 2025 2123 2147 2007 2058 2132
    ## [33237] 2202 2039 2117 2152 1949 2021 2206 2025 2012 2055 2214 2025 2151 2101
    ## [33251] 2123 2028 2022 2024 2215 2002 2145 2022 2204 2026 2156 2035 2116 2048
    ## [33265] 2056 2107 2040 2116 2219 2134 2055 2030 2047 2215 2200 2123 2045 2225
    ## [33279] 2216 2145 2210 2240 2057 2154 2234 2040 2155 2231 2146 2059 2049 2145
    ## [33293] 2249 2144 2150 2303 2123 2302 2206 2142 2107 2120 2151 2234 2222 2132
    ## [33307] 2240 2146 2214 2135 2237 2259 2057 2145 2100 2233 2241 2203 2247 2244
    ## [33321] 2112 2249 2108 2134 2130 2122 2113 2158 2117 2222 2323 2222 2209 2309
    ## [33335] 2318 2221 2333 2234 2134 2315 2331 2244 2328 2129 2347 2138 2305 2152
    ## [33349] 2300 2220 2159 2344 2205 2317 2336 2335 2325 2344 2330 2201 2236 2256
    ## [33363] 2216   11 2210 2309 2217 2323 2228 2357 2338   27 2348 2259 2217 2340
    ## [33377] 2252 2355 2252 2220 2356 2222 2330 2226 2317 2310 2334 2233    2   23
    ## [33391] 2342 2351   28    6 2348 2339   15 2311 2317   13 2301   14   31 2344
    ## [33405]   40 2253 2306 2302 2243 2339 2312 2327   16 2311 2348 2306 2332  105
    ## [33419]   57    1 2327   47 2326  116 2321  230    4 2325   22   57   22 2353
    ## [33433]    1   28 2356 2359 2348  239   47  149   48  119  107  117   20   10
    ## [33447]   11    8  143   35   57   28  150  204  131  154   10  120  100   26
    ## [33461]   41  134  202   57  353   56   NA   NA   NA   NA   NA   NA   NA   NA
    ## [33475]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [33489]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [33503]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [33517]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [33531]   NA   NA   NA  254  633  729  922  916  822  647  649  849  844  654
    ## [33545]  838  731  700  825  703  720  856  742  857  706  838  718  908  900
    ## [33559]  845  730  738  716  803  844  802  802  802  716  755  903  720  738
    ## [33573]  739  929  731  828  904  755  725  736  828  831  741  932  817  816
    ## [33587]  804  909  928  750  835  907  951  825  802  935  859  856  826  905
    ## [33601]  937  835  922 1007  801  923  751 1002 1026  853  904  818  928 1026
    ## [33615]  951  856 1017 1014  935  951  904  849 1040  956  744  801  820  953
    ## [33629]  955 1014  959 1019  839 1000  955  819  841  928  945  907  952 1051
    ## [33643] 1014 1104 1023 1016 1050  903 1014  944 1026 1013  955  902 1037  939
    ## [33657] 1027  925  947 1033 1126 1005  923 1055  841  855  921  903 1022  907
    ## [33671] 1107 1019 1041 1032 1024  922  903  955 1058  928  933 1129  904 1027
    ## [33685] 1102  949 1103  928 1025 1049  913 1024 1109 1012 1135 1019 1059  922
    ## [33699] 1049  915 1020 1055 1023 1107 1002 1045  952 1010 1109 1007 1201  955
    ## [33713] 1007 1026 1129 1120 1029 1045  929 1219 1037 1127 1019 1002  935  941
    ## [33727] 1024  940 1034 1020 1033 1039 1044 1155  951  950  941 1015 1112 1146
    ## [33741] 1035  952  954 1028 1052 1112 1000  927 1140 1146 1013 1028  948 1118
    ## [33755]  957 1230 1136 1003 1009 1151 1155 1139 1015 1151 1128 1148 1009 1203
    ## [33769] 1155 1201 1148 1019 1239 1132 1121 1029 1003 1009 1101 1231 1141 1214
    ## [33783] 1202 1142 1052 1039 1139 1135 1022 1127 1232 1241 1102 1134 1203 1125
    ## [33797] 1222 1236 1218 1210 1223 1242 1252 1044 1058 1118 1055 1125 1139 1145
    ## [33811] 1144 1154 1058 1143 1206 1058 1108 1110 1100 1103 1206 1135 1106 1051
    ## [33825] 1214 1127 1208 1221 1233 1157 1229 1255 1129 1144 1201 1131 1206 1316
    ## [33839] 1147 1322 1127 1158 1128 1222 1214 1208 1328 1340 1139 1219 1244 1226
    ## [33853] 1330 1250 1309 1332 1319 1347 1249 1323 1153 1335 1348 1236 1227 1259
    ## [33867] 1221 1201 1335 1244 1220 1226 1217 1228 1249 1411 1404 1347 1345 1345
    ## [33881] 1224 1236 1412 1326 1437 1218 1233 1342 1303 1245 1221 1328 1443 1359
    ## [33895] 1435 1322 1302 1405 1325 1336 1344 1410 1423 1442 1447 1259 1418 1300
    ## [33909] 1341 1321 1307 1329 1256 1439 1438 1505 1437 1504 1448 1302 1429 1357
    ## [33923] 1403 1541 1308 1336 1411 1349 1401 1500 1323 1327 1318 1406 1355 1453
    ## [33937] 1322 1330 1503 1427 1349 1428 1351 1543 1526 1451 1422 1331 1418 1520
    ## [33951] 1531 1441 1416 1545 1452 1555 1354 1438 1403 1545 1534 1404 1546 1404
    ## [33965] 1529 1414 1542 1458 1359 1445 1436 1406 1554 1526 1554 1520 1410 1440
    ## [33979] 1406 1452 1559 1515 1449 1558 1435 1454 1520 1513 1602 1644 1448 1420
    ## [33993] 1547 1553 1640 1533 1758 1533 1645 1649 1457 1624 1516 1550 1718 1442
    ## [34007] 1501 1642 1609 1711 1534 1555 1459 1532 1522 1621 1506 1514 1555 1632
    ## [34021] 1635 1542 1445 1623 1547 1459 1658 1602 1626 1502 1647 1603 1545 1637
    ## [34035] 1710 1539 1703 1642 1708 1720 1535 1643 1736 1609 1733 1732 1536 1537
    ## [34049] 1541 1826 1643 1543 1805 1700 1624 1741 1651 1651 1712 1743 1734 1550
    ## [34063] 1605 1703 1752 1820 1744 1621 1754 1638 1727 1651 1748 1548 1746 1619
    ## [34077] 1612 1631 1621 1757 1615 1633 1714 1716 1629 1734 1650 1749 1811 1856
    ## [34091] 1607 1814 1749 1734 1805 1716 1738 1802 1809 1748 1829 1705 1734 1648
    ## [34105] 1755 1716 1913 1841 1729 1850 1656 1753 1718 1655 1711 1834 1701 1749
    ## [34119] 1650 1638 1637 1855 1838 1852 1703 1741 1829 1752 1717 1845 1850 1741
    ## [34133] 1819 1949 1844 1751 1736 1805 1658 1846 1652 1648 1812 1834 1721 1739
    ## [34147] 1925 1721 1727 1751 1857 1853 1722 1805 1715 1753 1848 1842 1727 1723
    ## [34161] 1912 1857 1922 1815 1829 1723 1903 1826 1723 1807 1950 1839 1822 1723
    ## [34175] 1741 1830 1807 1845 1928 1736 1755 1933 1821 1939 1822 1934 1902 2009
    ## [34189] 1907 1800 1911 1804 1818 1755 1854 1946 1951 1759 1838 1859 1850 1846
    ## [34203] 1942 1949 1838 1849 1908 1847 1833 1819 1809 1932 1818 1822 1913 1954
    ## [34217] 1938 1808 1935 2015 1833 2001 1925 1810 1955 1954 1936 1825 1844 1842
    ## [34231] 1841 1907 1951 2028 1819 2008 1918 2018 1946 1808 1914 1945 1921 1816
    ## [34245] 1824 2015 1911 1944 1823 1913 1916 2030 1918 1934 2011 1929 2015 1904
    ## [34259] 1836 1931 1925 1901 2031 1854 2037 1921 1917 2018 2029 1909 1940 2052
    ## [34273] 1946 1930 2019 2002 2024 2003 2058 1857 2014 1917 2030 1908 2036 2133
    ## [34287] 2018 2024 1918 1926 2041 1954 2003 1942 2100 2103 1915 2054 2017 1938
    ## [34301] 2104 2102 1938 1934 2126 2020 2121 2211 2042 2105 2134 2007 1914 2001
    ## [34315] 2017 2130 1954 2009 2044 1947 2133 1956 2014 2102 2022 1940 2104 2116
    ## [34329] 2000 2002 2118 2148 2004 2104 2146 2016 2134 2052 2220 2120 2031 2148
    ## [34343] 2003 2046 2020 2005 2022 2018 2120 2016 2016 2051 2019 2109 2200 2139
    ## [34357] 2107 2151 2231 2158 2116 2046 2159 2041 2131 2114 2036 2059 2112 2026
    ## [34371] 2110 2156 2042 2126 2114 2208 2150 2115 2123 2112 2030 2146 2202 2110
    ## [34385] 2220 2204 2246 2056 2215 2138 2238 2233 2254 2224 2100 2205 2132 2258
    ## [34399] 2226 2131 2137 2055 2124 2056 2123 2038 2111 2146 2241 2241 2212 2216
    ## [34413] 2233 2225 2135 2122 2111 2243 2121 2111 2225 2140 2124 2147 2141 2214
    ## [34427] 2316 2124 2254 2220 2320 2129 2132 2347 2150 2219 2227 2130 2232 2231
    ## [34441] 2140 2150 2145 2238 2326 2322 2230 2152 2216 2327 2236 2204 2213 2313
    ## [34455] 2342 2204 2202 2329 2301 2255 2348 2348 2244 2249 2349 2337 2243   59
    ## [34469] 2218 2312 2309 2319 2227 2330 2217 2226 2231  137 2245   43 2253 2352
    ## [34483]  101 2348 2316  111 2339 2352 2348 2344    9   25  352   NA   NA   NA
    ## [34497]   NA  638  727  808  920  838  918  701  701  642  830  650  653  819
    ## [34511]  657  709  747  738  729  845  905  845  841  649  811  838  906  715
    ## [34525]  800  732  755  715  814  714  735  753  819  809  757  856  902  911
    ## [34539]  830  916  812  721  833  807  906  732  736  737  923  827  813  945
    ## [34553]  917  748  843  753  802  853  927  749  910  852  851  909  923  912
    ## [34567]  749  859  832  753  841  854  823 1006  941 1030  822  950  817  838
    ## [34581]  934  756  957  809  847 1044  957 1004  812 1011 1006  836  953 1010
    ## [34595] 1011  951 1019  829 1016 1001 1020  919  815 1012  941  942 1013  923
    ## [34609]  913 1037 1107  900 1041 1003 1039 1006 1044  937 1032  846  940  955
    ## [34623] 1035 1133 1039 1049  923 1028  952 1010  907  855  943  921  901  950
    ## [34637]  905 1048 1031  850  939 1033  928  954  904  916 1037  907 1044 1057
    ## [34651] 1104  934  919  917 1048 1028 1101 1043 1054 1048 1041 1030 1032 1010
    ## [34665] 1029 1056 1124  959 1114 1007  956 1213 1102  944 1101  958 1042 1109
    ## [34679] 1054 1010 1027 1026 1204 1030  933 1013 1034 1139 1038 1033 1050  954
    ## [34693] 1027 1008  944  939 1031 1045 1148 1015  959 1008 1150  948 1048 1003
    ## [34707] 1120 1204 1147 1032  944 1027 1013 1022 1038 1057 1150 1021 1133 1157
    ## [34721]  955 1009 1123 1111 1122 1230 1134 1020 1156 1146 1009 1144 1142 1200
    ## [34735] 1148 1203 1157 1027 1026 1107 1016 1106 1017 1223 1209 1058 1125 1146
    ## [34749] 1203 1056 1157 1221 1019 1226 1157 1132 1132 1139 1119 1023 1242 1224
    ## [34763] 1234 1038 1223 1102 1208 1233 1100 1110 1216 1131 1206 1136 1212 1212
    ## [34777] 1136 1101 1134 1419 1121 1129 1102 1326 1051 1231 1219 1241 1108 1056
    ## [34791] 1213 1239 1153 1150 1149 1137 1250 1145 1203 1256 1301 1231 1125 1122
    ## [34805] 1205 1159 1331 1316 1203 1152 1216 1255 1329 1126 1300 1234 1135 1303
    ## [34819] 1323 1323 1331 1239 1206 1253 1149 1358 1317 1236 1208 1338 1203 1340
    ## [34833] 1256 1210 1333 1208 1218 1418 1252 1341 1229 1243 1423 1422 1408 1246
    ## [34847] 1240 1428 1302 1227 1333 1332 1242 1406 1338 1321 1301 1316 1420 1233
    ## [34861] 1351 1359 1251 1337 1226 1419 1355 1430 1455 1304 1427 1452 1406 1304
    ## [34875] 1450 1441 1313 1344 1302 1323 1412 1246 1255 1440 1254 1444 1308 1350
    ## [34889] 1350 1326 1426 1355 1500 1346 1450 1504 1317 1509 1322 1348 1536 1355
    ## [34903] 1528 1451 1457 1417 1355 1504 1433 1512 1432 1344 1335 1428 1451 1530
    ## [34917] 1355 1359 1407 1549 1359 1414 1546 1356 1556 1546 1525 1435 1537 1433
    ## [34931] 1553 1415 1457 1546 1601 1421 1548 1425 1459 1415 1412 1502 1450 1457
    ## [34945] 1506 1513 1440 1503 1618 1610 1751 1625 1548 1518 1633 1527 1639 1638
    ## [34959] 1643 1457 1645 1619 1548 1537 1533 1559 1533 1540 1519 1612 1524 1445
    ## [34973] 1458 1506 1528 1501 1613 1454 1648 1631 1707 1512 1629 1515 1712 1605
    ## [34987] 1540 1604 1505 1553 1614 1608 1631 1650 1644 1537 1644 1536 1727 1648
    ## [35001] 1634 1701 1559 1529 1647 1723 1624 1725 1600 1714 1831 1557 1601 1724
    ## [35015] 1738 1545 1626 1719 1704 1606 1746 1735 1638 1622 1721 1734 1540 1635
    ## [35029] 1634 1705 1631 1552 1636 1734 1644 1800 1727 1616 1714 1644 1734 1642
    ## [35043] 1802 1748 1737 1712 1745 1702 1703 1705 1720 1833 1748 1745 1833 1914
    ## [35057] 1713 1618 1704 1752 1706 1805 1629 1702 1746 1714 1844 1804 1712 1647
    ## [35071] 1749 1644 1732 1638 1836 1631 1826 1834 1711 1706 1835 1717 1649 1821
    ## [35085] 1815 1849 1845 1835 1746 1710 1944 1846 1756 1744 1718 1659 1734 1751
    ## [35099] 1814 1905 1703 1856 1706 1807 1804 1801 1917 1651 1848 1804 1838 1823
    ## [35113] 1735 1851 1840 1710 1809 1735 1744 1719 1812 1714 1740 1919 1905 1836
    ## [35127] 1720 1750 1905 1804 1741 1729 1824 1805 1929 1813 1738 1818 1735 1733
    ## [35141] 1910 1827 1837 1802 1818 1935 1853 1858 1927 1830 1924 1927 1846 1857
    ## [35155] 1820 1826 1915 1925 1915 1850 1936 1943 1819 1758 1907 1911 1848 1954
    ## [35169] 1855 1929 1845 1824 1915 2002 1825 1808 1853 2004 1801 1810 1930 1932
    ## [35183] 1820 1942 1837 1821 1959 1828 1812 1952 1955 1815 1937 1807 1829 2002
    ## [35197] 1845 1824 1944 1939 1904 1831 1907 1834 1849 1959 1836 1852 1913 2022
    ## [35211] 2004 2013 1849 1933 1936 1840 1838 2005 2020 1844 2000 1851 2015 2022
    ## [35225] 2107 2004 1922 1928 2026 2034 2005 1944 1954 1950 1938 1901 1859 2001
    ## [35239] 2038 2021 1911 1900 2048 1940 2103 2004 2051 2031 2052 2013 1918 1914
    ## [35253] 2059 2117 1956 1954 2121 1944 2045 2046 2117 2033 1946 1934 1925 2055
    ## [35267] 2019 2018 2013 2050 1918 1936 2016 2128 2013 2121 1939 2028 2049 2149
    ## [35281] 2017 2019 2138 2023 2102 2128 1948 2136 2110 2002 2026 2133 1954 2210
    ## [35295] 2203 2017 2140 1952 2018 2031 2022 2138 2125 2110 2059 2143 2048 2016
    ## [35309] 2010 2128 2105 2154 2101 2200 2130 2207 2110 2041 2201 2012 2153 2057
    ## [35323] 2200 2047 2148 2043 2111 2126 2230 2147 2031 2102 2126 2111 2217 2217
    ## [35337] 2214 2126 2212 2143 2225 2131 2047 2051 2135 2239 2233 2241 2225 2116
    ## [35351] 2220 2108 2048 2102 2114 2152 2134 2255 2258 2138 2107 2217 2227 2145
    ## [35365] 2226 2230 2146 2220 2206 2201 2211 2259 2138 2112 2118 2107 2140 2125
    ## [35379] 2130 2111 2134 2229 2126 2218 2139 2212 2203 2225 2206 2143 2304 2201
    ## [35393] 2331 2314 2332 2244 2304 2200 2127 2326 2145 2227 2202 2219 2321 2155
    ## [35407] 2328 2253 2145 2317 2205 2217 2149 2358 2216 2157 2214 2203 2217 2347
    ## [35421] 2332   45 2334 2226 2320 2221 2342 2323 2255 2246 2307   21 2222 2254
    ## [35435] 2253 2355 2259  133 2303   39 2331 2242   17 2252 2327 2257 2342 2309
    ## [35449] 2343 2326 2321 2319   20 2346   17 2349 2353  118 2359    4   15    5
    ## [35463]   52  357   NA   NA   NA   NA   NA   NA   NA  637  736  923  845  941
    ## [35477]  811  651  710  649  839  657  809  900  704  659  704  711  854  824
    ## [35491]  741  712  817  658  826  732  800  711  718  800  810  841  754  810
    ## [35505]  803  718  755  906  846  718  829  921  747  911  822  844  754  814
    ## [35519]  739  742  832  857  737  835  902  925  732  747  840  832  919  908
    ## [35533]  910  801  931  918  807  932  902  806 1057  754  921  839  831  755
    ## [35547] 1042  815  859  939  946  802  927 1053  917  901  804  855  948  806
    ## [35561]  939  953 1009  956  816 1001 1010 1004  851  952 1003  951 1016 1004
    ## [35575]  826  829  920  806  851  944  944 1017  952 1009  907  831  959 1021
    ## [35589] 1124 1036 1037 1012  843 1005 1001  931 1015  950 1031  946 1038  951
    ## [35603]  925 1134 1021 1029 1037  939  903 1010  932 1041 1012  927  935  947
    ## [35617]  902 1036 1115  946  933 1045  916  917 1059  859  931  922  921  956
    ## [35631] 1010  945 1059 1032 1108  919 1110  955 1116 1047 1037  938 1022 1055
    ## [35645] 1103 1014 1108 1139 1033 1050  938 1104 1123 1041 1015 1000 1029 1224
    ## [35659] 1023 1030 1212 1158  954 1112 1021 1012 1043 1153 1019 1037 1005 1007
    ## [35673]  935 1050  942 1058 1001 1035 1023  953 1021 1148 1059 1105 1054 1101
    ## [35687] 1048 1015 1147 1121 1011 1042 1207  953 1012 1020 1202 1129 1139 1029
    ## [35701] 1210 1019 1242 1159 1123 1029  957 1035 1159 1213 1201 1131 1145 1035
    ## [35715] 1154 1158 1138 1025 1111 1200 1202 1158 1045 1232 1047 1053 1151 1133
    ## [35729] 1213 1152 1229 1226 1222 1206 1028 1244 1138 1143 1131 1156 1220 1030
    ## [35743] 1228 1241 1232 1231 1231 1222 1250 1111 1116 1114 1213 1055 1155 1157
    ## [35757] 1117 1200 1116 1141 1106 1202 1239 1326 1137 1121 1228 1208 1233 1236
    ## [35771] 1303 1157 1250 1158 1232 1244 1205 1210 1151 1256 1226 1223 1120 1318
    ## [35785] 1122 1239 1143 1334 1123 1316 1214 1342 1326 1221 1337 1246 1228 1328
    ## [35799] 1303 1214 1325 1353 1234 1250 1153 1410 1256 1216 1254 1225 1211 1341
    ## [35813] 1258 1404 1222 1217 1334 1345 1238 1434 1314 1300 1350 1245 1434 1256
    ## [35827] 1228 1344 1229 1323 1450 1409 1214 1353 1319 1316 1355 1350 1440 1336
    ## [35841] 1334 1449 1421 1410 1353 1405 1346 1450 1459 1436 1252 1326 1450 1257
    ## [35855] 1326 1446 1417 1459 1437 1302 1324 1513 1354 1440 1447 1407 1457 1506
    ## [35869] 1406 1532 1323 1338 1520 1329 1532 1332 1435 1349 1431 1418 1519 1400
    ## [35883] 1333 1521 1456 1506 1539 1507 1354 1448 1340 1533 1548 1414 1413 1601
    ## [35897] 1440 1446 1447 1514 1540 1511 1624 1405 1353 1553 1557 1444 1557 1408
    ## [35911] 1450 1436 1500 1544 1515 1458 1616 1510 1506 1512 1446 1451 1543 1551
    ## [35925] 1601 1430 1630 1745 1608 1455 1648 1609 1503 1649 1559 1444 1440 1631
    ## [35939] 1613 1623 1543 1502 1542 1543 1655 1535 1609 1555 1504 1641 1616 1545
    ## [35953] 1508 1639 1712 1732 1715 1545 1543 1604 1559 1545 1505 1653 1532 1553
    ## [35967] 1720 1531 1619 1548 1528 1652 1637 1657 1720 1741 1649 1725 1552 1700
    ## [35981] 1842 1719 1734 1616 1751 1552 1623 1646 1656 1610 1644 1652 1650 1613
    ## [35995] 1547 1652 1745 1722 1636 1641 1645 1746 1608 1804 1738 1641 1717 1626
    ## [36009] 1711 1759 1736 1554 1621 1652 1812 1727 1721 1758 1755 1717 1920 1643
    ## [36023] 1656 1716 1754 1759 1759 1628 1659 1647 1813 1659 1716 1828 1837 1828
    ## [36037] 1823 1659 1801 1814 1653 1802 1653 1839 1648 1656 1831 1817 1839 1758
    ## [36051] 1759 1750 1734 1713 1802 1722 1822 1822 1949 1740 1724 1713 1811 1753
    ## [36065] 1744 1756 1835 1711 1914 1847 1705 1742 1655 1850 1819 1718 1758 1810
    ## [36079] 1855 1829 1749 1848 1732 1812 1842 1809 1838 1821 1801 1738 1704 1734
    ## [36093] 1741 1826 1831 1750 1946 1738 1945 1910 1840 1915 1800 1935 1810 1915
    ## [36107] 1929 1808 1800 1927 1816 1843 1911 1741 1815 1939 1935 1809 1926 1900
    ## [36121] 1822 1850 1821 1820 1950 1942 2019 1922 1955 1829 1933 1921 1924 1950
    ## [36135] 1811 1854 1950 1943 1953 1911 1815 1902 1920 1922 1807 1849 1827 1843
    ## [36149] 1951 1833 1853 1806 1928 1836 1851 1932 1838 1826 1838 1900 2010 1859
    ## [36163] 2023 1839 1828 1922 2026 2003 2021 1853 2005 2022 2026 2033 1840 1847
    ## [36177] 1916 1922 2027 1847 1956 2031 1953 1954 2102 2021 2007 1945 1953 1945
    ## [36191] 1929 1922 1949 1939 2125 2046 1920 2042 2032 2044 2044 1947 2050 1915
    ## [36205] 2056 2035 2112 2036 2057 2039 2101 2103 2011 1956 2015 2137 2118 1957
    ## [36219] 2004 1925 2034 2026 2151 2114 2131 2006 2115 2014 2137 2029 1949 2122
    ## [36233] 2111 2046 2141 2050 2030 2020 2135 2136 2144 2216 2058 2056 2040 2102
    ## [36247] 2152 2018 1957 2135 2016 2017 2217 2036 2157 2035 2014 2140 2032 2038
    ## [36261] 2115 2154 2140 2117 2147 2139 2029 2126 2101 2106 2211 2153 2148 2201
    ## [36275] 2053 2037 2031 2025 2034 2211 2216 2149 2208 2043 2242 2240 2210 2053
    ## [36289] 2214 2238 2229 2158 2104 2043 2128 2111 2215 2148 2045 2229 2104 2138
    ## [36303] 2152 2143 2153 2158 2237 2234 2146 2230 2108 2309 2259 2250 2117 2100
    ## [36317] 2225 2224 2238 2255 2321 2231 2154 2149 2116 2305 2236 2235 2143 2139
    ## [36331] 2237 2149 2133 2241 2208 2311 2251 2153 2241 2135 2208 2152 2246 2315
    ## [36345] 2145 2320 2329 2312 2335 2225 2218 2204 2228 2352 2314 2204 2209 2152
    ## [36359] 2159 2204 2208 2217 2152 2227 2345  452 2202 2250 2200 2215 2245 2247
    ## [36373]   58 2354 2350 2214 2252 2319 2321 2400 2317 2310 2231 2233 2325 2317
    ## [36387]   10 2353 2316 2245 2319 2234 2355 2241 2250 2303   32 2246 2245   27
    ## [36401]  135   21 2329 2320 2302 2310    6    8    2   13 2400 2338 2340 2307
    ## [36415] 2319 2325 2338 2338   22   15 2327   10   49   52 2343    5 2336 2358
    ## [36429]    4  103   31    4 2346   34   57  204   29   52   21   30   36   36
    ## [36443]   12   18  227   46  352   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [36457]   NA   NA   NA   NA   NA   NA   NA   NA   NA  119  109  627  723  804
    ## [36471]  844  816  950  948  658  711  837  706  706  726  716  657  817  701
    ## [36485]  735  806  924  704  902  740  704  853  831  832  837  749  808  714
    ## [36499]  739  800  731  746  757  846  810  720  805  912  750  919  815  732
    ## [36513]  822  822  907  854  906  755  733  821  851  823  730  933  822  821
    ## [36527]  754  903  748  914  824  804  908  932  859  815  948  849  943  954
    ## [36541] 1015  949  805  836  853  836  811 1058 1121  852  749  938  934  937
    ## [36555]  931  931 1014 1019  928  811 1010 1008  939  932  936 1015  811  853
    ## [36569]  827  827 1015 1006 1018  925  926  950  938  946  832  824 1012 1113
    ## [36583]  957 1009  903 1029  905 1005  849 1031  925 1035 1023 1025  917 1034
    ## [36597] 1024 1010  943 1033 1145 1025  846  946  953 1000  859  938  909  933
    ## [36611]  918  947 1109 1034 1112  936  908  947 1039 1037  936 1022 1001  901
    ## [36625]  906  908 1025 1008 1115 1059 1057 1109 1045 1059 1116  928 1040 1051
    ## [36639]  912  951 1038 1054 1017 1111 1130 1043 1031 1015 1034 1122 1048 1140
    ## [36653] 1051  956  930 1033 1023 1219 1039 1242 1008 1021 1120 1044  943 1153
    ## [36667] 1033 1107 1129 1032  957 1036  948 1025 1023 1111   NA 1120 1130 1036
    ## [36681] 1001 1015  959 1139  953 1059 1007 1139 1104 1144 1246 1130 1139 1140
    ## [36695] 1009 1153 1006 1035 1153 1009 1125 1008 1121 1134 1227 1213 1212 1145
    ## [36709] 1227 1059 1121 1140 1033 1024 1150 1208 1153 1151 1200 1218 1206 1159
    ## [36723] 1131 1112 1058 1134 1124 1037 1230 1129 1031 1220 1207 1209 1255 1250
    ## [36737] 1222 1104 1220 1105 1125 1235 1339 1152 1145 1225 1120 1135 1212 1429
    ## [36751] 1112 1112 1233 1118 1248 1157 1242 1150 1210 1151 1257 1104 1115 1212
    ## [36765] 1315 1218 1347 1344 1246 1325 1303 1125 1203 1154 1217 1127 1302 1142
    ## [36779] 1242 1345 1321 1228 1207 1226 1324 1132 1240 1257 1245 1254 1152 1243
    ## [36793] 1324 1306 1338 1217 1224 1235 1214 1411 1229 1329 1259 1350 1349 1337
    ## [36807] 1204 1417 1422 1426 1333 1220 1234 1243 1411 1245 1303 1355 1412 1344
    ## [36821] 1329 1423 1441 1408 1325 1453 1315 1251 1425 1410 1418 1347 1307 1312
    ## [36835] 1457 1244 1532 1251 1446 1434 1350 1342 1421 1435 1423 1307 1413 1513
    ## [36849] 1307 1456 1422 1317 1359 1408 1351 1333 1440 1512 1521 1504 1518 1319
    ## [36863] 1433 1412 1438 1341 1448 1454 1530 1452 1354 1434 1342 1345 1540 1346
    ## [36877] 1439 1544 1440 1546 1456 1402 1424 1422 1600 1549 1410 1400 1500 1453
    ## [36891] 1432 1551 1449 1458 1536 1452 1558 1427 1553 1430 1523 1542 1421 1754
    ## [36905] 1618 1542 1448 1617 1544 1612 1559 1525 1520 1630 1617 1530 1448 1447
    ## [36919] 1515 1559 1617 1625 1444 1533 1504 1518 1643 1630 1455 1642 1449 1603
    ## [36933] 1540 1613 1703 1628 1516 1544 1613 1635 1653 1705 1601 1550 1611 1641
    ## [36947] 1704 1728 1621 1655 1550 1718 1711 1643 1611 1831 1724 1718 1549 1743
    ## [36961] 1550 1554 1547 1610 1709 1650 1718 1751 1613 1646 1551 1717 1634 1553
    ## [36975] 1635 1614 1627 1734 1655 1600 1738 1745 1642 1753 1729 1806 1757 1741
    ## [36989] 1706 1632 1813 1605 1703 1624 1629 1644 1659 1743 1801 1625 1624 1640
    ## [37003] 1636 1837 1652 1711 1714 1806 1711 1728 1643 1817 1831 1726 1940 1824
    ## [37017] 1758 1725 1709 1740 1737 1836 1736 1751 1844 1825 1702 1751 1819 1720
    ## [37031] 1830 1829 1700 1842 1816 1714 1712 1958 1851 1854 1854 1751 1707 1925
    ## [37045] 1831 1832 1838 1758 1837 1814 1806 1840 1837 1712 1727 1725 1829 1840
    ## [37059] 1859 1836 1710 1735 1817 1856 1713 1822 1823 1738 1723 1813 1927 1838
    ## [37073] 1833 1918 1830 1850 1929 1808 1940 1952 1748 1930 1745 1857 1849 1839
    ## [37087] 2008 1911 1844 1810 1936 1934 1901 1846 1943 1927 1829 1816 1759 1807
    ## [37101] 1940 1809 1758 1928 1902 1826 1845 2010 1844 1931 1816 1901 1926 1823
    ## [37115] 1908 2014 2008 1931 2016 1901 1934 2012 1924 2010 2010 1940 1931 1911
    ## [37129] 2040 2044 2019 2014 1924 1843 1933 1854 1855 2010 1932 2044 2051 2028
    ## [37143] 1938 1854 1911 2047 1953 1921 1906 2017 1903 2029 2100 2110 2059 1908
    ## [37157] 2041 2039 2041 2114 1955 2019 2006 2005 1913 2128 2013 1929 2034 2007
    ## [37171] 2111 2055 2107 1940 2050 2042 2023 2121 1924 1959 2146 2112 2004 2002
    ## [37185] 2039 2052 1947 2017 2048 2128 2026 2026 2124 2128 1945 2136 2043 1954
    ## [37199] 2120 2147 2152 2011 2151 2009 2057 2048 2052 2025 2135 2048 2128 2007
    ## [37213] 2038 2013 2102 2101 2023 2139 2145 2025 2119 2213 2024 2032 2049 2035
    ## [37227] 2139 2233 2221 2044 2113 2108 2212 2107 2025 2228 2038 2211 2043 2141
    ## [37241] 2214 2205 2111 2127 2306 2244 2156 2243 2231 2056 2306 2129 2258 2240
    ## [37255] 2249 2057 2124 2112 2126 2114 2240 2134 2141 2241 2211 2113 2233 2157
    ## [37269] 2114 2236 2154 2108 2143 2208 2245 2153 2220 2241 2307 2234 2129 2139
    ## [37283] 2234 2320 2226 2219 2253 2146 2203 2312 2155 2257 2320 2133 2220 2231
    ## [37297] 2310 2316 2155 2158 2319 2331   35 2207 2331 2350 2207 2208 2317 2229
    ## [37311] 2236 2155 2155 2340 2329    5 2335 2339 2202 2321 2207 2211 2206 2256
    ## [37325] 2226 2223 2215 2316 2238 2214 2244   17 2355  122    3 2228 2346 2239
    ## [37339] 2330 2319 2237 2251   13 2234 2255   13   16 2324 2259 2344   27   21
    ## [37353] 2359  100 2303   49 2350 2334   30   51   52   45 2328 2330 2255   25
    ## [37367] 2344  209 2355  100   33 2311   37    9 2356   42   32   31 2318 2356
    ## [37381] 2359 2334  130 2352    2   12   27   13  145  106  151   31   50  202
    ## [37395]   25   27  119  410  103  111  202   NA   NA   NA   NA   NA   NA   NA
    ## [37409]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [37423]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [37437]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [37451]   NA   NA   NA   NA   NA   NA  628  728  825  818  950  723  824  846
    ## [37465]  850  758  752  805  733  713  842  659  827  746  759 1017  923  749
    ## [37479]  713  828  807  745  818  905  909  836  919  821  743  819  742  908
    ## [37493]  901  856  902  837  919  843  912  928  744  950  846  941  916  936
    ## [37507]  801  939 1057  920  959  904  845 1004  826 1020 1008  828 1010  814
    ## [37521]  944 1009  939 1011  841  942  831 1013 1110  902 1014  950 1040  838
    ## [37535]  935 1000  951  948  838 1009  849 1010  933 1132  932  855  935  928
    ## [37549] 1033  834  855 1020  855 1045 1002  925  922 1036 1036 1011 1240 1037
    ## [37563] 1037 1008 1044  935  910 1034 1030  949 1036 1104  950 1150 1055  924
    ## [37577] 1101 1043  949 1031 1221  957 1003 1237 1100 1002  958 1103 1122  939
    ## [37591] 1233 1152 1007 1050 1021 1155 1034 1013 1132 1004 1114  952  948 1001
    ## [37605] 1004  928 1055 1023  940  955  958 1052 1001 1249 1040  954 1010  955
    ## [37619] 1134 1127 1002 1001 1056 1108 1040 1201 1206 1153 1144 1146 1043 1009
    ## [37633] 1144 1208 1143 1311 1056 1026 1029 1206 1039 1200 1211 1154 1029 1025
    ## [37647] 1159 1207 1112 1038 1110 1221 1150 1045 1056 1143 1233 1039 1330 1136
    ## [37661] 1203 1126 1052 1053 1107 1252 1243 1149 1111 1435 1251 1226 1313 1146
    ## [37675] 1150 1233 1303 1221 1102 1309 1158 1203 1210 1121 1205 1307 1225 1328
    ## [37689] 1248 1308 1243 1142 1140 1338 1313 1237 1337 1257 1403 1215 1154 1324
    ## [37703] 1153 1337 1210 1318 1345 1154 1324 1356 1228 1306 1234 1221 1257 1229
    ## [37717] 1407 1409 1259 1236 1222 1319 1405 1227 1348 1302 1418 1220 1426 1240
    ## [37731] 1310 1257 1314 1343 1241 1246 1414 1420 1334 1415 1506 1417 1332 1251
    ## [37745] 1428 1402 1258 1447 1344 1444 1454 1334 1414 1330 1354 1425 1425 1410
    ## [37759] 1459 1314 1449 1327 1326 1317 1345 1350 1453 1338 1313 1458 1414 1452
    ## [37773] 1358 1435 1420 1532 1517 1419 1528 1353 1617 1357 1402 1422 1532 1452
    ## [37787] 1539 1517 1532 1408 1535 1358 1512 1505 1559 1416 1536 1424 1448 1442
    ## [37801] 1528 1431 1448 1442 1604 1432 1514 1536 1606 1614 1602 1627 1530 1619
    ## [37815] 1522 1636 1617 1532 1455 1522 1632 1547 1812 1528 1540 1455 1554 1451
    ## [37829] 1602 1554 1611 1702 1636 1638 1511 1539 1529 1536 1705 1535 1532 1522
    ## [37843] 1625 1635 1722 1536 1530 1654 1821 1551 1756 1641 1631 1644 1648 1626
    ## [37857] 1723 1646 1635 1734 1749 1624 1633 1809 1554 1709 1601 1701 1640 1648
    ## [37871] 1633 1640 1709 1755 1708 1708 1729 1757 1806 1729 1625 1755 1746 1738
    ## [37885] 1744 1734 1811 1621 1635 1700 1852 1645 1820 1717 1754 1739 1722 1905
    ## [37899] 1649 1730 1827 1829 1646 1836 1754 1737 1725 1632 1806 1709 1708 1916
    ## [37913] 1705 1747 1846 1850 1737 1848 1654 1724 1840 1834 1838 1706 1716 1831
    ## [37927] 1806 1806 2007 1841 1734 1833 2002 1716 1848 1744 1734 1905 1740 1716
    ## [37941] 1906 1857 1738 1800 1734 1855 1915 1938 1816 1735 1755 1906 1807 1742
    ## [37955] 1936 1809 1931 1923 1921 1909 1930 1926 1942 1812 1821 2002 1838 1926
    ## [37969] 1911 1938 2007 1948 2001 1945 1839 1935 1843 1817 1800 1957 1838 1825
    ## [37983] 1850 1935 1818 2024 2014 1932 1821 1834 1912 1851 1841 2016 2000 1847
    ## [37997] 1916 1933 1842 1904 2004 1932 2013 2117 1936 1915 2101 1940 2018 2002
    ## [38011] 1932 2022 2052 1932 2002 1855 2038 1938 2031 1910 1912 2027 2040 1922
    ## [38025] 1923 1957 2048 1951 1938 2104 2118 2017 2055 1929 1944 2003 1923 1926
    ## [38039] 2129 2052 1953 2102 2123 2112 1947 2127 1948 2135 2106 1958 2200 2145
    ## [38053] 2124 2012 2126 1952 2147 2138 1959 2117 2105 2212 2114 2022 2114 2154
    ## [38067] 2149 2113 2011 2146 2212 2237 2228 2033 2202 2213 2140 2223 2245 2037
    ## [38081] 2144 2214 2203 2124 2215 2140 2257 2241 2237 2245 2056 2112 2238 2226
    ## [38095] 2125 2152 2137 2132 2158 2340 2306 2219 2143 2153 2316 2211 2243 2350
    ## [38109] 2343 2351   51 2328 2322 2242 2321 2220 2256 2358 2340 2241   37 2243
    ## [38123] 2305  205 2323 2339 2347 2354    9  400   NA   NA  122  429  734  821
    ## [38137]  943  831  656  651  710  722  914  937  812  807  711  740  842  758
    ## [38151]  855  742  842  740  828  932  759  816  744  903  907  826  901  924
    ## [38165]  905  916  824  746  856  749  943  753  746  934  823  922 1043 1012
    ## [38179]  932 1018  859  945 1040  857  806  917  943  958 1017  810  950  809
    ## [38193] 1026  953  901  811  954  855  940  920 1024  913  823  950  933 1018
    ## [38207] 1041 1017 1110 1006 1025 1000 1012  914 1020  933  935  830  911  857
    ## [38221] 1134 1025 1026 1009 1035  956  854 1028 1056 1107  940  851 1008  858
    ## [38235]  921  856  920 1029 1036  942 1032 1037  859  911  924 1142  933 1045
    ## [38249] 1042  956  933  949 1101 1045  907  917 1028 1053 1035 1045  928 1106
    ## [38263] 1027 1224  958  949 1143  958  917  950 1008 1102  938   NA  947  933
    ## [38277] 1005 1116 1058 1102  927 1220 1036 1141 1018  934 1006  941 1010 1054
    ## [38291] 1039 1006 1104 1132 1103 1034 1120  948 1003 1209 1055 1010  956 1212
    ## [38305]  952 1042 1116 1056 1143 1206 1135 1133 1139 1013 1035 1012 1152 1150
    ## [38319] 1151 1203 1104 1212 1110 1214 1015 1224 1057 1200 1206 1131 1138 1019
    ## [38333] 1040 1033 1018 1310 1209 1203 1201 1032 1228 1032 1037 1103 1124 1146
    ## [38347] 1432 1221 1253 1129 1109 1218 1214 1130 1152 1111 1211 1109 1054 1145
    ## [38361] 1054 1117 1123 1220 1307 1243 1246 1129 1204 1214 1118 1243 1332 1200
    ## [38375] 1125 1308 1237 1224 1333 1134 1128 1353 1213 1240 1314 1228 1346 1315
    ## [38389] 1314 1254 1306 1416 1226 1317 1321 1219 1239 1330 1232 1339 1251 1313
    ## [38403] 1213 1217 1334 1209 1333 1325 1201 1407 1358 1404 1404 1206 1246 1350
    ## [38417] 1220 1335 1240 1226 1256 1308 1346 1222 1415 1400 1245 1333 1323 1417
    ## [38431] 1410 1436 1346 1456 1254 1257 1302 1251 1458 1445 1428 1454 1411 1300
    ## [38445] 1444 1351 1331 1505 1350 1350 1440 1336 1508 1344 1449 1418 1316 1522
    ## [38459] 1352 1346 1343 1451 1316 1339 1328 1513 1454 1531 1425 1527 1435 1520
    ## [38473] 1502 1349 1405 1420 1529 1514 1417 1343 1413 1545 1512 1443 1541 1438
    ## [38487] 1458 1556 1433 1415 1500 1442 1440 1524 1417 1352 1404 1420 1635 1608
    ## [38501] 1530 1448 1404 1507 1452 1416 1525 1506 1613 1456 1517 1426 1548 1545
    ## [38515] 1554 1454 1417 1515 1622 1534 1503 1536 1534 1637 1751 1636 1636 1637
    ## [38529] 1604 1640 1507 1434 1539 1620 1531 1525 1505 1613 1526 1602 1616 1527
    ## [38543] 1549 1508 1551 1455 1444 1610 1500 1646 1615 1508 1653 1517 1501 1655
    ## [38557] 1630 1613 1726 1706 1516 1546 1635 1542 1704 1605 1641 1704 1717 1705
    ## [38571] 1646 1621 1726 1713 1701 1727 1700 1713 1822 1555 1636 1705 1638 1615
    ## [38585] 1627 1615 1546 1639 1739 1646 1530 1604 1726 1608 1734 1638 1739 1624
    ## [38599] 1737 1709 1626 1748 1756 1653 1748 1715 1759 1557 1715 1712 1621 1620
    ## [38613] 1643 1642 1753 1712 1703 1813 1733 1825 1745 1634 1931 1832 1822 1659
    ## [38627] 1805 1742 1820 1759 1631 1821 1806 1729 1639 1807 1659 1903 1916 1730
    ## [38641] 1901 1827 1712 1734 1745 1857 1919 1701 1915 1658 1639 1659 1844 1743
    ## [38655] 1643 1912 1742 1657 1742 1957 1902 1723 1809 1802 1909 1655 1708 1710
    ## [38669] 1759 1842 1847 1941 1715 1830 1732 1808 1842 1823 1723 1927 1754 1816
    ## [38683] 1743 1810 1855 1746 1900 1728 1821 1744 1852 1809 1816 1725 1818 1825
    ## [38697] 1911 1836 1743 1737 1927 1742 1845 1954 1931 1932 1936 1849 1931 1840
    ## [38711] 1759 1756 1929 1747 1816 1936 1944 1832 1810 1935 1937 1905 2027 1803
    ## [38725] 1847 1826 1914 1801 1829 1837 1906 1841 1903 1840 1947 1923 1820 2021
    ## [38739] 2011 1758 1857 1916 1958 1945 1814 1810 1903 1848 2016 2000 1836 1824
    ## [38753] 1827 1830 1817 1901 2021 2031 1948 1953 1824 2026 1839 1949 1821 1858
    ## [38767] 1958 1935 1946 2034 2016 2027 2043 1903 1837 1840 1940 2028 1924 2055
    ## [38781] 2022 1912 1923 1939 1844 1852 1910 1948 1959 1916 2048 1947 1934 1935
    ## [38795] 2014 2033 2018 1855 1925 2018 2009 1914 1910 1938 2029 1923 1914 2146
    ## [38809] 1954 2019 1952 2044 2107 1916 2018 2001 2041 2007 2055 2104 2100 1926
    ## [38823] 2058 2003 2132 1941 1953 2109 2148 2035 1950 2132 1928 2119 2113 2012
    ## [38837] 2119 2002 1938 1940 2011 2109 1952 2059 2117 2126 2222 2019 2144 2105
    ## [38851] 2025 2040 2151 2136 2018 2036 2143 1955 2011 2158 2213 2155 2215 2104
    ## [38865] 2103 2006 2005 2050 2106 2133 2216 2028 2154 2057 2236 2034 2056 2059
    ## [38879] 2132 2012 2116 2041 2204 2146 2239 2139 2147 2027 2034 2258 2230 2138
    ## [38893] 2047 2105 2211 2239 2200 2149 2051 2105 2215 2132 2240 2147 2302 2117
    ## [38907] 2143 2202 2043 2237 2222 2239 2300 2252 2046 2345 2052 2156 2254 2228
    ## [38921] 2054 2136 2244 2131 2218 2208 2137 2108 2327 2239 2219 2130 2312 2120
    ## [38935] 2310 2121 2159 2336 2250 2326 2149 2244 2129 2127 2317 2135 2213 2152
    ## [38949] 2151 2316 2206 2312 2147 2223 2355 2216   27 2325 2133 2208 2329 2155
    ## [38963] 2157 2159 2154 2204 2231 2210 2253 2213 2154 2207 2206   14 2212 2156
    ## [38977] 2318    3 2152 2256 2336   32 2344 2248 2200 2212 2327 2314   21 2335
    ## [38991] 2325 2359 2252 2324 2243 2253 2300  120 2346 2342 2240 2311 2235 2352
    ## [39005] 2324 2240 2252 2324  101 2356 2238  135 2305 2251 2254   21 2349 2252
    ## [39019] 2340 2353 2313 2323 2337    3   54   41   18 2359    4    1  230   NA
    ## [39033]   NA   NA  624  733  814  932  824  719  650  646  836  832  724  826
    ## [39047]  823  740  722  819  840  914  713  654  704  812  953  716  708  850
    ## [39061]  754  734  753  736  710  726  858  806  717  805  810  731  900  818
    ## [39075]  747  912  758  818  905  931  829  928  722  946  755  829  854  738
    ## [39089]  827  747  920  832  857  839  755  815  901  745  916  858  818  911
    ## [39103]  916  905  922  756  951  954  927  807  930  848  844 1206  759  847
    ## [39117]  852 1013  930  938  929  846 1053  812 1011  816 1016 1001  945  954
    ## [39131]  813  952 1109  851  833  827  950 1000  943  941  931 1030 1034 1121
    ## [39145] 1022  921 1006 1001 1040  920 1030  855  923  855 1005 1010 1025  837
    ## [39159] 1046 1021  945 1021 1051 1020  933 1117  935  905  935 1027 1031 1219
    ## [39173]  933  916 1025  925  923 1037 1036 1040 1044  902  941 1042  923  845
    ## [39187] 1019  907  943 1006 1048 1046 1059  951 1036 1051 1111  934  910 1112
    ## [39201] 1054  931 1016  922 1038 1044  959 1037 1031 1014 1052 1049 1103  957
    ## [39215] 1213 1014 1201  916 1235 1020 1101 1011 1043 1039 1006 1120  922 1049
    ## [39229] 1040  947  944  955  941 1017   NA 1019  955 1135 1221  936 1014 1125
    ## [39243] 1036 1124 1022 1058  949 1044 1036 1014  942  948 1121  941 1001 1018
    ## [39257] 1059 1147 1242 1211 1146 1039 1117 1115 1142 1015 1029 1216 1014 1217
    ## [39271] 1137 1127 1044 1144 1201 1142 1109 1040 1143 1205 1222 1011 1215 1140
    ## [39285] 1153 1225 1113 1208 1208 1148 1018 1140 1155 1113 1119 1239 1211 1208
    ## [39299] 1240 1219 1147 1242 1104 1113 1132 1042 1146 1046 1117 1231 1230 1222
    ## [39313] 1124 1257 1246 1138 1158 1118 1105 1114 1450 1106 1113 1138 1151 1259
    ## [39327] 1132 1209 1237 1244 1105 1148 1157 1209 1324 1252 1254 1114 1244 1200
    ## [39341] 1129 1250 1124 1246 1253 1157 1128 1258 1150 1340 1329 1231 1351 1338
    ## [39355] 1200 1309 1343 1257 1151 1356 1326 1252 1338 1331 1309 1153 1316 1157
    ## [39369] 1236 1222 1219 1332 1208 1242 1348 1352 1255 1200 1217 1219 1425 1307
    ## [39383] 1412 1258 1358 1306 1348 1411 1340 1331 1221 1413 1312 1213 1335 1318
    ## [39397] 1353 1253 1258 1348 1340 1455 1404 1334 1358 1415 1303 1317 1420 1420
    ## [39411] 1423 1447 1440 1248 1335 1453 1455 1439 1250 1301 1450 1443 1514 1350
    ## [39425] 1457 1349 1322 1321 1348 1415 1327 1513 1316 1521 1349 1334 1510 1409
    ## [39439] 1340 1331 1350 1422 1514 1423 1451 1507 1455 1513 1518 1414 1452 1350
    ## [39453] 1525 1439 1443 1342 1446 1433 1355 1421 1542 1459 1531 1528 1512 1550
    ## [39467] 1444 1404 1531 1426 1558 1505 1625 1515 1429 1623 1420 1409 1507 1446
    ## [39481] 1411 1541 1428 1500 1531 1501 1415 1433 1501 1450 1423 1507 1604 1553
    ## [39495] 1521 1536 1511 1621 1805 1624 1540 1551 1610 1607 1648 1459 1536 1630
    ## [39509] 1452 1646 1638 1432 1538 1502 1528 1556 1531 1530 1457 1702 1621 1639
    ## [39523] 1458 1701 1623 1602 1541 1506 1458 1548 1657 1626 1619 1504 1507 1707
    ## [39537] 1552 1634 1625 1712 1519 1630 1644 1542 1724 1546 1613 1526 1616 1708
    ## [39551] 1541 1607 1747 1706 1701 1539 1835 1623 1749 1657 1620 1741 1637 1542
    ## [39565] 1710 1636 1726 1616 1646 1539 1729 1718 1650 1641 1723 1731 1733 1755
    ## [39579] 1635 1625 1647 1604 1735 1728 1555 1759 1620 1649 1639 1707 1606 1728
    ## [39593] 1631 1715 1624 1712 1750 1738 1659 1735 1615 1732 1749 1635 1736 1750
    ## [39607] 1747 1728 1705 1754 1658 1911 1812 1616 1720 1808 1642 1722 1732 1746
    ## [39621] 1653 1649 1739 1823 1828 1644 1744 1703 1649 1733 1708 1825 1642 1822
    ## [39635] 1831 1840 1849 1741 1658 1813 1812 1721 1708 1803 1928 1727 1700 1743
    ## [39649] 1831 1823 1752 1800 1728 1708 1827 1755 1840 1713 1734 1716 1733 1800
    ## [39663] 1726 1825 1816 1836 1726 1844 1855 1808 1708 1915 1842 1729 1739 1719
    ## [39677] 1835 1803 1720 1932 1923 1736 1919 1809 1815 1735 1727 1815 1744 1821
    ## [39691] 1910 1949 1837 1909 1851 1754 1911 1757 1825 1944 1845 1837 1848 1756
    ## [39705] 1935 1847 1942 1803 1913 1914 1906 1833 1915 1941 1933 1817 1952 1846
    ## [39719] 1954 1803 1908 1840 2016 1837 1810 1937 1843 2011 2014 1945 2010 1805
    ## [39733] 1855 1838 1903 2015 1840 1943 1903 1856 1825 1817 1812 1939 1823 1948
    ## [39747] 1841 1953 1824 1926 2013 2001 1834 2040 2116 1841 1834 1849 2021 1929
    ## [39761] 1832 2024 1959 1920 1919 2050 2034 2016 1933 1913 1923 1937 1838 1959
    ## [39775] 2023 2010 2007 2005 1958 2115 2037 2001 1852 2013 2037 2104 1858 1940
    ## [39789] 1932 2027 2103 2029 2127 2133 1922 2028 2027 1957 2055 2136 1920 2030
    ## [39803] 2154 2048 1934 2000 1955 2153 2141 2013 2103 2037 2045 2045 1939 2029
    ## [39817] 2026 2000 2109 2005 2104 2124 2049 1940 1947 2139 2204 2049 1958 2104
    ## [39831] 2014 2038 1933 2144 1947 2033 2022 1950 2146 2134 2050 2042 2107 2003
    ## [39845] 2152 2215 2022 2218 2012 1950 2201 2247 2223 2028 2132 2239 2035 2059
    ## [39859] 2143 2132 2103 2035 2144 2136 2143 2106 2040 2218 2123 2144 2101 2044
    ## [39873] 2102 2241 2115 2112 2202 2157 2138 2135 2233 2116 2150 2217 2154 2157
    ## [39887] 2209 2051 2110 2117 2226 2249 2045 2219 2113 2216 2232 2151 2229 2151
    ## [39901] 2208 2253 2100 2210 2141 2143 2113 2221 2125 2113 2058 2228 2138 2234
    ## [39915] 2114 2300 2313 2235 2053 2136 2238 2223 2119 2300 2106 2148 2222 2307
    ## [39929] 2201 2136 2149 2110 2124 2112 2224 2317 2132 2240 2234 2112 2234 2231
    ## [39943] 2134 2219 2217 2144 2311 2255 2319 2134 2307 2127 2330 2252 2128 2233
    ## [39957] 2152 2257 2153 2351 2146 2143 2159 2217 2255 2321 2252 2323 2146 2321
    ## [39971] 2231 2247 2321 2245 2214 2213   44    7 2220 2206   58 2330 2313 2248
    ## [39985] 2246 2330 2245 2322 2221 2222 2303 2344 2322 2328   15 2227 2312 2356
    ## [39999] 2240   18 2244 2237    3  125 2239 2302 2305  152 2308 2303 2327 2331
    ## [40013]   38 2338 2350 2356    6 2345  402   NA   NA  636  733  940  823  942
    ## [40027]  818  648  643  822  739  658  833  656  708  837  826  822  906  701
    ## [40041]  656  707  727  839  711  823  755  736  742  903  740  718  757  847
    ## [40055]  804  753  814  751  713  929  819  724  734  856  753  754  904  734
    ## [40069]  741  833  838  932  902  830  824  905  740  825  918  749  839  928
    ## [40083] 1038 1102  911  910  904  839  753  906  918  855  921 1007  811 1046
    ## [40097]  840  937  757 1003 1004  756  932  854  931  803  857 1106  942   NA
    ## [40111] 1028  809  837  849  934 1022 1014  951  943  952  833  826  938  930
    ## [40125]  958  833 1016  933 1122  956 1020  909 1000  922  852 1025 1052 1003
    ## [40139]  845 1021 1007  957 1022 1016 1004 1029 1040 1141  936 1026 1008 1138
    ## [40153] 1018 1027  918  903  941  928 1011  906  905  938 1044 1050  901  906
    ## [40167] 1009 1043  945  955 1112 1019  912 1055  952  921 1040 1119  914 1036
    ## [40181]  957 1039  940 1037  922  921 1110 1041 1025 1106 1051 1049  919 1056
    ## [40195]  917 1042 1044 1002 1236  922 1011  958 1057  937 1012 1027 1114  953
    ## [40209] 1133 1042  954  944 1059 1241 1019 1036 1018 1114 1126 1141 1014 1017
    ## [40223]  946  927 1015 1120 1042 1024 1022  956 1001 1027 1119  940 1038  935
    ## [40237] 1000 1001 1045 1001 1157 1107  954 1147  941 1249 1048 1203 1011 1007
    ## [40251] 1125 1207 1138 1135 1139 1224  955 1203 1151 1022 1139 1128 1053 1102
    ## [40265] 1136 1042 1223 1137 1016 1057 1205 1209 1200 1027 1152 1236 1105 1136
    ## [40279] 1033 1137 1207 1231 1210 1103 1129 1224 1130 1233 1214 1047 1051 1055
    ## [40293] 1032 1223 1131 1217 1152 1138 1145 1124 1149 1230 1057 1107 1141 1058
    ## [40307] 1109 1204 1224 1114 1216 1104 1252 1114 1102 1142 1130 1203 1117 1135
    ## [40321] 1240 1330 1349 1245 1119 1135 1246 1251 1208 1249 1325 1259 1125 1235
    ## [40335] 1155 1234 1329 1225 1133 1314 1301 1216 1215 1148 1327 1303 1317 1146
    ## [40349] 1334 1321 1224 1205 1228 1339 1304 1334 1330 1215 1351 1220 1325 1233
    ## [40363] 1410 1200 1341 1334 1353 1242 1227 1345 1207 1322 1227 1229 1233 1233
    ## [40377] 1307 1248 1221 1423 1319 1349 1305 1410 1354 1347 1336 1311 1354 1404
    ## [40391] 1312 1420 1450 1328 1245 1335 1255 1417 1431 1421 1427 1445 1452 1455
    ## [40405] 1256 1435 1303 1317 1319 1312 1403 1453 1400 1433 1354 1514 1341 1316
    ## [40419] 1513 1400 1352 1412 1509 1514 1338 1421 1402 1504 1455 1335 1524 1424
    ## [40433] 1542 1514 1339 1512 1359 1522 1440 1411 1409 1547 1349 1522 1351 1611
    ## [40447] 1352 1617 1523 1442 1612 1429 1434 1552 1456 1410 1529 1558 1459 1418
    ## [40461] 1544 1428 1500 1441 1446 1532 1529 1538 1431 1512 1628 1449 1750 1548
    ## [40475] 1515 1631 1546 1603 1517 1600 1620 1559 1634 1615 1459 1508 1634 1508
    ## [40489] 1649 1624 1535 1502 1519 1524 1456 1536 1600 1459 1556 1450 1640 1513
    ## [40503] 1702 1706 1656 1624 1645 1541 1555 1645 1629 1553 1652 1602 1655 1650
    ## [40517] 1542 1523 1643 1537 1649 1643 1543 1556 1713 1754 1556 1731 1606 1552
    ## [40531] 1656 1623 1630 1629 1725 1723 1717 1646 1732 1627 1855 1640 1616 1605
    ## [40545] 1634 1557 1644 1621 1729 1630 1715 1721 1650 1654 1736 1742 1609 1711
    ## [40559] 1646 1748 1728 1722 1743 1634 1729 1613 1644 1808 1615 1752 1602 1658
    ## [40573] 1733 1735 1800 1632 1754 1746 1805 1743 1659 1812 1749 1631 1707 1719
    ## [40587] 1733 1928 1824 1802 1748 1715 1832 1820 1824 1715 1739 1632 1703 1801
    ## [40601] 1619 1637 1646 1906 1844 1646 1704 1848 1810 1847 1738 1706 1810 1735
    ## [40615] 1719 1752 1648 1942 1702 1730 1827 1719 1808 1733 1654 1745 1744 1742
    ## [40629] 1812 1704 1814 1827 1726 1852 1859 1820 1751 1907 1827 1808 1823 1751
    ## [40643] 1730 1852 1720 1801 1909 1814 1855 1907 1757 1731 1933 1743 1822 1913
    ## [40657] 1857 1816 1822 1843 1836 1917 1845 1942 1945 1803 1926 1808 1820 1752
    ## [40671] 1924 1939 1915 1843 1922 1914 1847 2003 1828 1838 1835 2009 1910 2003
    ## [40685] 1920 1937 1807 1839 1930 2013 1927 1817 1824 1834 1917 1917 1951 1928
    ## [40699] 1855 1947 1854 1917 2017 1832 2003 1826 2004 2006 2006 1821 1946 1958
    ## [40713] 1940 1954 1815 1837 1824 1916 2029 1859 1937 1859 2006 1853 2025 1956
    ## [40727] 1939 2020 1951 1932 1923 1948 2009 1918 1846 2003 1957 2024 1913 1857
    ## [40741] 1950 2023 1929 1942 1933 1929 1914 1915 2043 1920 2008 2040 2052 2020
    ## [40755] 2019 1953 2035 1952 2037 2023 1907 1924 1915 1937 1945 2040 2111 1957
    ## [40769] 2104 2030 2006 2035 2105 1953 2017 2006 1909 1958 2023 1937 2100 2046
    ## [40783] 2049 2011 1948 2158 2124 2108 2015 2137 2132 2019 2022 2041 2124 2023
    ## [40797] 2102 1953 2105 2127 2054 2026 2036 2125 2047 2018 2109 2118 1954 1946
    ## [40811] 1952 2100 2017 2153 2014 2155 2037 2204 2157 2206 2109 2049 2100 2017
    ## [40825] 2024 2203 2123 2052 2134 2138 2219 2141 2218 2217 2159 2112 2042 2028
    ## [40839] 2210 2208 2212 2211 2143 2230 2047 2240 2116 2224 2042 2233 2113 2105
    ## [40853] 2210 2119 2153 2130 2150 2231 2220 2220 2203 2234 2236 2137 2214 2118
    ## [40867] 2146 2206 2100 2139 2208 2259 2224 2145 2223 2121 2237 2135 2115 2107
    ## [40881] 2259 2141 2206 2218 2139 2140 2141 2226 2131 2108 2236 2113 2220 2132
    ## [40895] 2304 2110 2320 2311 2138 2228 2144 2125 2226 2306 2340 2123 2324 2309
    ## [40909] 2153 2213 2300 2147 2145 2239 2317 2229 2208 2129 2310 2351 2209 2214
    ## [40923] 2220 2236 2322 2259 2221 2312 2158 2234 2216    6 2400 2243 2206 2308
    ## [40937] 2234 2209 2340    1 2207    9  102 2256 2340 2244 2320   43 2331 2355
    ## [40951]    5 2317 2212 2312    3 2236 2234 2244 2359   51 2307  106 2252 2258
    ## [40965]  145 2339 2313   53 2315 2359 2323 2336 2344   14    5    2   28  332
    ## [40979]   NA   NA   NA   NA   NA   NA  625  745  924  822  820  826  655  708
    ## [40993]  652  739  923  825  657  659  819  800  711  649  733  753  649  817
    ## [41007]  930  722  838  834  722  848  733  759  750  801  906  749  714  805
    ## [41021]  808  832  856  753  818  857  821  721  852  802  747  818  811  933
    ## [41035]  912  723  809  824  832  908  902  746  900  745  907  917  805  858
    ## [41049]  757  915  859  805  834  919  950  802 1001 1021  849  744  952  910
    ## [41063]  748  844  856  913  923  805 1009  907  935 1010 1007  823  941 1007
    ## [41077] 1258 1006  952  823  847 1002  943  954  834  759  911 1009  957  947
    ## [41091]  950 1019  957  931 1026 1056  917 1010 1013 1008  901  922 1015  927
    ## [41105]  858 1006 1003 1020 1020 1044 1031  934 1023 1043 1129 1026  940  922
    ## [41119]  854 1011  859  923 1033 1027 1003  904  907  853  929 1023 1050 1037
    ## [41133] 1042 1113 1010  948 1009 1059 1045  938  859 1030  926 1043 1040  919
    ## [41147] 1045  937 1027 1057  954 1057 1101 1106 1038 1142 1047 1004 1055 1038
    ## [41161] 1204  944 1306 1056  935 1146 1030 1026 1041 1148 1043 1026 1025  959
    ## [41175] 1115  933 1021 1003  955 1106 1107 1050  950 1017 1059 1101  946 1100
    ## [41189] 1159 1045 1009 1009 1010  946 1108 1133 1146 1040 1002 1026 1105  949
    ## [41203] 1004 1120 1029 1216 1052 1147 1051 1004 1015 1137 1145 1024 1232 1110
    ## [41217] 1045 1145 1153 1052 1119 1149 1224 1222 1058 1204 1149 1222 1103 1152
    ## [41231] 1210 1207 1123 1018 1107 1138 1139 1156 1211 1204 1137 1126 1128 1203
    ## [41245] 1219 1025 1126 1047 1210 1024 1233 1207 1223 1144 1120 1217 1120 1232
    ## [41259] 1219 1123 1125 1219 1143 1136 1106 1105 1110 1112 1152 1205 1231 1118
    ## [41273] 1153 1238 1052 1149 1218 1310 1443 1146 1241 1221 1148 1230 1158 1244
    ## [41287] 1141 1253 1114 1254 1133 1320 1200 1333 1210 1246 1225 1128 1209 1251
    ## [41301] 1315 1327 1323 1321 1231 1304 1340 1235 1258 1309 1201 1326 1344 1255
    ## [41315] 1224 1238 1246 1230 1335 1213 1246 1210 1244 1350 1159 1338 1334 1230
    ## [41329] 1159 1236 1323 1240 1411 1402 1352 1259 1441 1329 1246 1222 1302 1419
    ## [41343] 1222 1401 1310 1433 1353 1335 1335 1317 1340 1404 1350 1433 1421 1341
    ## [41357] 1411 1301 1251 1324 1459 1301 1249 1459 1339 1509 1429 1441 1450 1257
    ## [41371] 1420 1415 1520 1305 1356 1435 1433 1456 1348 1336 1354 1450 1347 1312
    ## [41385] 1335 1414 1439 1407 1444 1418 1512 1526 1456 1432 1452 1535 1410 1539
    ## [41399] 1345 1442 1535 1452 1345 1436 1455 1518 1549 1559 1407 1356 1533 1424
    ## [41413] 1528 1515 1409 1352 1602 1416 1558 1410 1511 1454 1507 1516 1443 1553
    ## [41427] 1551 1455 1448 1514 1512 1518 1615 1552 1501 1611 1553 1604 1502 1550
    ## [41441] 1624 1537 1518 1722 1742 1531 1527 1547 1639 1614 1518 1642 1625 1522
    ## [41455] 1655 1646 1536 1658 1635 1559 1543 1621 1624 1705 1551 1620 1605 1549
    ## [41469] 1453 1530 1511 1644 1523 1645 1504 1502 1603 1556 1755 1637 1534 1648
    ## [41483] 1616 1617 1649 1659 1557 1551 1700 1710 1636 1537 1525 1729 1605 1739
    ## [41497] 1636 1732 1806 1637 1713 1558 1638 1742 1616 1638 1557 1647 1718 1650
    ## [41511] 1655 1731 1817 1724 1741 1731 1751 1622 1633 1738 1730 1538 1736 1649
    ## [41525] 1742 1602 1614 1642 1653 1716 1736 1746 1759 1629 1656 1650 1733 1826
    ## [41539] 1716 1639 1726 1656 1721 1801 1754 1625 1624 1813 1808 1851 1721 1721
    ## [41553] 1735 1712 1811 1649 1702 1834 1759 1648 1815 1748 1726 1720 1649 1831
    ## [41567] 1727 1846 1630 1853 1715 1649 1901 1746 1835 1840 1721 1814 1659 1706
    ## [41581] 1739 1805 1705 1649 1908 1715 1812 1826 1817 1656 1842 1916 1715 1851
    ## [41595] 1801 1725 1755 1736 1720 1757 1734 1858 1653 1720 1747 1908 1827 1846
    ## [41609] 1843 1829 1808 1822 1808 1808 1741 1837 1745 1737 1817 1726 1835 1805
    ## [41623] 1715 1810 1847 1946 1853 1844 1826 1839 1758 1835 1910 1907 1806 1841
    ## [41637] 1831 1915 1749 1948 1926 1922 1934 1938 1807 1918 1823 1836 1931 1933
    ## [41651] 1959 2001 1831 1755 1852 1856 1845 1851 1841 2001 1835 1942 1929 1944
    ## [41665] 1946 1921 1934 1814 1955 1924 1915 1857 1819 1827 1954 1957 1914 1855
    ## [41679] 1834 1931 1819 1841 1957 2010 2022 1819 1939 2037 1909 1948 2004 2021
    ## [41693] 2019 1907 2011 1828 1905 1819 1958 1835 2002 1924 1834 1818 1957 2011
    ## [41707] 1855 1912 2043 1936 1954 2041 1919 2003 1908 2043 2019 1934 1830 2010
    ## [41721] 2009 2026 2043 1940 1945 2036 2015 2058 2056 1931 2037 2016 2035 1912
    ## [41735] 1910 2049 2010 2023 2013 2003 2104 1939 2043 2049 2054 2200 1946 2035
    ## [41749] 1953 2006 2013 1958 2124 2059 2050 2111 2126 2107 1940 2033 2113 1922
    ## [41763] 2014 2012 2017 1952 2013 2019 2227 2022 2031 2009 2049 2129 2123 2115
    ## [41777] 1954 2036 2004 2103 2153 2033 2014 2200 2000 2026 2158 2119 2150 2118
    ## [41791] 2108 2225 2009 2030 2110 2032 2020 1955 2010 2045 2151 2031 2156 2111
    ## [41805] 2150 2101 2213 2116 2108 2155 2053 2209 2034 2202 2021 2035 2141 2124
    ## [41819] 2201 2143 2144 2103 2153 2104 2225 2035 2223 2134 2135 2058 2138 2145
    ## [41833] 2230 2103 2203 2142 2122 2210 2131 2100 2048 2052 2234 2242 2222 2137
    ## [41847] 2033 2214 2242 2220 2228 2106 2128 2240 2220 2141 2109 2144 2110 2301
    ## [41861] 2143 2310 2117 2313 2049 2123 2201 2125 2223 2237 2115 2225 2134 2107
    ## [41875] 2111 2249 2248 2117 2120 2141 2156 2119 2144 2144 2242 2253 2128 2219
    ## [41889] 2154 2143 2303 2118 2302 2146 2219 2228   NA 2225 2309 2346 2307 2304
    ## [41903] 2206 2159 2151    6 2238 2337 2208 2302 2256   35 2151 2307 2202   46
    ## [41917] 2224 2318 2342 2243 2241 2254 2301 2355 2317 2346 2223 2346   23 2304
    ## [41931] 2242 2225   21 2244 2353 2342 2317 2236   41  124 2300 2300 2256 2307
    ## [41945] 2257 2321   11 2338 2342 2356 2350 2359  148  328   NA   NA   NA   NA
    ## [41959]  629  827  906  827  906  709  813  828  821  654  650  655  655  740
    ## [41973]  747  714 1121  904  736  718  912  855  845  729  707  731  720  752
    ## [41987]  833  733  805  801  757  755  807  813  805  725  916  905  837  844
    ## [42001]  737  815  852  903  913  801  750  905  752  733  836  814  741  819
    ## [42015]  933  748  911  902  921  819  757  904  833  916  901  823  836  900
    ## [42029]  906  840  942  758  818  944  929  833  938  807 1048  808  956  944
    ## [42043]  955  948 1045  905  926  939  955 1010  922 1032  908  936  936  837
    ## [42057] 1021  950  850  830 1013 1001 1012  826  920 1003  955  957  828 1010
    ## [42071]  944 1054  935  916 1014 1003 1042 1030  903 1010 1015 1019 1032  924
    ## [42085]  937 1005 1037  932 1043  943 1026 1115 1037  932 1035  913 1104  923
    ## [42099] 1040 1013  928 1015 1044  953  922 1042 1017  933 1000 1057  911  921
    ## [42113]  924 1101 1051 1044  927  945 1018  931 1050 1058  934 1107 1058 1100
    ## [42127]  932 1124 1030 1049 1111 1052 1207 1109 1025 1006 1004 1040  935 1136
    ## [42141] 1035 1022 1128 1135  941 1116 1018 1216 1129 1026 1007 1043  937  945
    ## [42155] 1013 1113 1044 1157 1131 1033  959 1003  956 1048 1108 1001 1012  950
    ## [42169] 1137 1111 1031 1202 1102  949 1008 1148 1131 1147 1034 1119 1009 1156
    ## [42183]  959 1202 1009 1204 1005 1206 1011 1005 1213 1025 1212 1241 1147 1130
    ## [42197] 1141 1213 1138 1207 1051 1155 1127 1046 1048 1156 1216 1017 1235 1032
    ## [42211] 1108 1127 1114 1156 1214 1158 1145 1234 1153 1039 1224 1255 1210 1144
    ## [42225] 1246 1041 1234 1237 1156 1052 1138 1222 1046 1044 1111 1159 1101 1123
    ## [42239] 1155 1246 1054 1233 1103 1204 1123 1221 1139 1118 1058 1216 1237 1134
    ## [42253] 1235 1151 1153 1307 1101 1208 1244 1133 1142 1252 1313 1204 1140 1301
    ## [42267] 1259 1123 1247 1234 1136 1206 1132 1320 1332 1331 1311 1349 1339 1312
    ## [42281] 1246 1240 1250 1222 1202 1326 1352 1316 1156 1229 1328 1249 1344 1218
    ## [42295] 1214 1234 1342 1345 1357 1258 1152 1347 1237 1248 1322 1213 1327 1236
    ## [42309] 1352 1210 1201 1220 1401 1232 1413 1403 1326 1249 1342 1220 1244 1414
    ## [42323] 1401 1351 1307 1235 1414 1306 1312 1329 1335 1322 1410 1336 1409 1330
    ## [42337] 1352 1435 1242 1419 1433 1408 1510 1304 1254 1455 1453 1441 1352 1441
    ## [42351] 1311 1418 1439 1452 1450 1420 1432 1347 1409 1503 1411 1314 1433 1358
    ## [42365] 1355 1321 1454 1338 1415 1513 1504 1540 1417 1537 1341 1541 1519 1438
    ## [42379] 1543 1357 1556 1354 1509 1604 1351 1349 1438 1555 1431 1536 1539 1432
    ## [42393] 1556 1616 1517 1425 1413 1413 1457 1537 1433 1419 1501 1609 1515 1431
    ## [42407] 1503 1545 1520 1519 1517 1448 1528 1426 1420 1528 1518 1623 1555 1603
    ## [42421] 1606 1607 1558 1504 1802 1600 1628 1437 1631 1618 1541 1516 1629 1544
    ## [42435] 1456 1501 1549 1456 1654 1642 1508 1510 1506 1646 1628 1637 1643 1552
    ## [42449] 1628 1704 1600 1703 1723 1704 1518 1533 1555 1634 1531 1706 1536 1643
    ## [42463] 1659 1548 1544 1703 1657 1625 1630 1705 1624 1546 1725 1813 1636 1538
    ## [42477] 1722 1748 1731 1623 1633 1559 1636 1713 1610 1640 1637 1730 1636 1718
    ## [42491] 1733 1736 1750 1736 1740 1558 1553 1655 1629 1556 1754 1615 1741 1722
    ## [42505] 1703 1612 1705 1740 1802 1724 1811 1621 1741 1648 1630 1626 1706 1756
    ## [42519] 1800 1731 1800 1725 1857 1602 1751 1744 1817 1838 1636 1639 1735 1754
    ## [42533] 1649 1817 1838 1800 1820 1654 1722 1639 1831 1832 1838 1824 1817 1756
    ## [42547] 1724 1729 1845 1815 1724 1736 1803 1717 1848 1651 1853 1740 1934 1718
    ## [42561] 1815 1840 1712 1826 1810 1755 1803 1702 1750 1718 1810 1814 1706 1858
    ## [42575] 1823 1750 1739 1802 1911 1910 1747 1755 1753 1838 1844 1856 1719 1815
    ## [42589] 1735 1730 1829 1810 1726 1753 1936 1910 1726 1922 1807 1923 1856 1819
    ## [42603] 1905 1929 1918 1741 1933 1948 1928 1850 1849 1922 1807 1821 1939 1814
    ## [42617] 1833 1803 1756 1922 1951 1838 1904 1931 1841 1923 1858 1951 1930 1744
    ## [42631] 1942 1932 1753 1956 1939 1919 1940 2006 1813 2018 1836 1821 1858 1822
    ## [42645] 1933 1957 2008 1840 1814 1912 1857 1827 2012 2008 2016 1903 1915 1823
    ## [42659] 1928 1925 1850 2014 1845 1958 1918 1842 1937 1945 1918 2030 2023 1856
    ## [42673] 2025 1927 2042 1902 1835 1843 2030 1849 1900 2039 1853 1932 1950 1953
    ## [42687] 1942 1952 2024 2033 2042 1902 2028 1905 2047 1921 2054 1907 2054 2022
    ## [42701] 1901 2053 2101 1916 2050 1937 2100 2027 1948 2029 2041 2000 2050 2027
    ## [42715] 2109 2045 2018 2107 2027 2007 1929 2049 2101 2046 2132 2105 2001 1943
    ## [42729] 2003 2121 2123 2043 2117 2020 2040 2011 2137 2116 2019 2042 2038 2135
    ## [42743] 2123 2016 2109 1957 2201 2028 2037 2111 2012 2012 1958 2140 2124 2118
    ## [42757] 2111 2117 2153 2222 2023 2024 2140 2136 2208 2208 2040 2049 2019 2156
    ## [42771] 2317 2216 2046 2105 1956 2003 2145 2043 2226 2127 2228 2050 2139 2120
    ## [42785] 2216 2053 2110 2204 2047 2053 2150 2027 2213 2135 2054 2101 2210 2241
    ## [42799] 2216 2216 2120 2227 2201 2219 2235 2212 2126 2246 2238 2210 2045 2219
    ## [42813] 2148 2048 2223 2229 2117 2057 2250 2218 2109 2215 2102 2259 2139 2055
    ## [42827] 2111 2119 2235 2128 2237 2315 2139 2052 2228 2117 2129 2308 2058 2124
    ## [42841] 2315 2243 2240 2321 2227 2132 2155 2125 2105 2335 2238 2326 2127 2139
    ## [42855] 2133 2107 2216 2252 2122 2157 2314 2158 2135 2154 2212 2151 2137 2316
    ## [42869] 2330 2327 2245 2147 2231 2226 2359 2259 2343 2400 2323 2149 2258 2254
    ## [42883] 2208 2350 2211 2217 2240 2226 2317 2327 2208 2216 2314 2155   10    4
    ## [42897] 2259 2213 2354 2301    6 2348 2248 2347    6 2232 2329   44 2348 2355
    ## [42911]   12 2343 2221 2244 2355 2247    6 2336    3 2304 2311 2307    4 2323
    ## [42925]   36 2310 2249 2346   16 2344   36   42   32  153   44 2318   17 2334
    ## [42939]   NA 2343 2339 2354   14 2359    3    7   14   30  328   NA   NA   NA
    ## [42953]   NA  348  645  753  853  904  850  910  648  653  703  848  649  827
    ## [42967]  702  841  854  745  845  831  715  714  853  749  735  724  728  730
    ## [42981]  808  911  813  746  719  807  739  745  854  824  804  827  811  919
    ## [42995]  815  923  924  856  818  842  734  928  907  800  820  730  925  744
    ## [43009]  826  907  755  831  915  837  802 1019  922  943  916  757  924  913
    ## [43023]  910  948  918  816  836  910  748  749  855 1019  759 1022  931 1019
    ## [43037]  954  958  903  918 1018  934  933  845 1025 1025 1004  957 1015 1014
    ## [43051] 1000 1026 1010  844  840  825 1008  959  942 1020  954  819 1013 1021
    ## [43065] 1007 1038  939  917 1055 1017 1014 1033 1016  930  920 1034  911 1031
    ## [43079] 1031 1013  942 1029 1119 1059  929 1037 1057 1052  935  949 1016 1055
    ## [43093]  934 1005  910  925 1020  855  929 1109 1101  933 1018 1057 1049  934
    ## [43107] 1014  927  857 1103 1025  907  945 1024 1043 1102  953 1112 1106  955
    ## [43121] 1033 1209 1047 1105  959 1055 1052 1049 1040 1046 1019 1110 1054 1013
    ## [43135] 1024 1050 1013 1008 1200 1151 1142 1007 1054 1135 1124  953 1023 1030
    ## [43149] 1023  927 1149 1013  959  932 1027 1028 1018 1118 1109 1059 1135  937
    ## [43163]  938 1115 1002 1115 1056 1133 1009 1003 1036 1056  936 1010  956  946
    ## [43177] 1150 1031 1128 1007 1210 1232 1007 1136 1133 1109 1151 1002 1156 1119
    ## [43191] 1035 1153 1219 1031 1149 1220 1217 1149 1128 1206 1040 1054 1215 1022
    ## [43205] 1104 1222 1141 1133 1211 1232 1129 1026 1202 1219 1233 1215 1139 1033
    ## [43219] 1215 1250 1207 1155 1229 1232 1229 1218 1048 1053 1140 1110 1206 1130
    ## [43233] 1222 1137 1244 1052 1104 1046 1153 1051 1122 1139 1153 1250 1135 1109
    ## [43247] 1117 1449 1232 1301 1158 1228 1106 1142 1152 1257 1256 1226 1203 1222
    ## [43261] 1259 1206 1137 1112 1313 1340 1254 1219 1248 1305 1330 1131 1253 1216
    ## [43275] 1236 1157 1239 1333 1326 1337 1155 1342 1327 1337 1257 1308 1234 1321
    ## [43289] 1345 1244 1217 1150 1237 1207 1346 1257 1342 1345 1250 1210 1356 1323
    ## [43303] 1249 1232 1207 1351 1259 1227 1256 1408 1408 1235 1306 1252 1219 1328
    ## [43317] 1347 1439 1321 1310 1411 1339 1408 1341 1359 1420 1432 1452 1453 1436
    ## [43331] 1441 1300 1428 1457 1341 1428 1308 1315 1244 1518 1447 1529 1348 1341
    ## [43345] 1451 1506 1451 1421 1257 1443 1421 1304 1344 1502 1412 1516 1351 1435
    ## [43359] 1443 1505 1325 1410 1332 1337 1320 1522 1407 1501 1507 1428 1425 1359
    ## [43373] 1535 1435 1541 1437 1434 1529 1346 1536 1554 1348 1538 1548 1509 1416
    ## [43387] 1345 1545 1614 1402 1444 1447 1545 1414 1428 1502 1358 1610 1613 1442
    ## [43401] 1417 1515 1525 1454 1431 1415 1548 1536 1410 1530 1436 1455 1452 1531
    ## [43415] 1621 1559 1520 1421 1555 1456 1524 1501 1814 1541 1614 1551 1638 1447
    ## [43429] 1625 1535 1617 1526 1652 1641 1628 1508 1440 1643 1550 1648 1609 1533
    ## [43443] 1706 1553 1447 1511 1647 1450 1624 1644 1702 1453 1558 1637 1535 1614
    ## [43457] 1648 1640 1513 1507 1634 1625 1602 1547 1711 1727 1608 1642 1644 1648
    ## [43471] 1651 1625 1540 1524 1725 1723 1738 1619 1548 1645 1617 1802 1629 1600
    ## [43485] 1620 1749 1558 1631 1627 1638 1734 1723 1652 1638 1632 1750 1554 1756
    ## [43499] 1747 1627 1710 1636 1751 1552 1755 1759 1631 1759 1823 1747 1814 1638
    ## [43513] 1605 1757 1654 1804 1822 1650 1646 1913 1632 1627 1752 1732 1826 1752
    ## [43527] 1803 1752 1713 1844 1745 1824 1808 1701 1846 1732 1701 1819 1706 1644
    ## [43541] 1648 1801 1859 1830 1808 1807 1701 1635 1915 1841 1819 1856 1742 1845
    ## [43555] 1721 1920 1754 1734 1732 1810 1839 1754 1708 1740 1929 1759 1805 1846
    ## [43569] 1834 1728 1717 1720 1733 1722 1829 1910 1709 1839 1728 1730 1822 1804
    ## [43583] 1817 1802 1838 1903 1822 1830 1753 1923 1839 1840 1846 1720 1747 1812
    ## [43597] 1917 1823 1941 1746 1727 1717 1744 1727 1934 1823 1827 1712 1807 1847
    ## [43611] 1931 1737 1904 1943 1948 1929 1809 1906 1933 1931 1949 1743 1754 1951
    ## [43625] 1828 1946 2015 1923 1911 1828 1926 1849 2015 1801 2006 1909 1906 1944
    ## [43639] 1854 2040 1951 1814 1853 2029 1826 2008 1957 1958 1925 1959 1900 1918
    ## [43653] 1945 1820 1906 2027 1959 1856 1941 1928 2018 1859 1905 1845 1826 1919
    ## [43667] 1839 1817 2048 1831 2036 2025 1914 1942 1839 1912 2046 2017 2044 2018
    ## [43681] 1847 1900 2034 1953 1930 1859 2027 2041 1952 2053 2053 1949 2021 2012
    ## [43695] 1908 2049 2036 2052 1846 2032 1907 2044 2018 1939 2018 2031 1902 1949
    ## [43709] 1955 2108 1923 2103 2034 2116 1939 2028 2044 1937 1933 2112 2016 2123
    ## [43723] 2101 2118 2002 2135 2136 2007 1959 2120 2122 2028 2033 2110 2058 2030
    ## [43737] 2004 2024 1958 1919 2043 2002 2244 2023 2036 2127 2140 2112 2112 2041
    ## [43751] 2127 2027 2129 2133 2050 2114 2112 2005 2012 2039 2012 2011 2056 2227
    ## [43765] 2146 2057 2215 2207 2216 1953 2045 2032 2131 2103 2040 2100 2031 2128
    ## [43779] 2031 2042 2102 2207 2104 2117 2041 2203 2214 2204 2139 2154 2157 2048
    ## [43793] 2038 2209 2211 2248 2141 2214 2140 2154 2128 2027 2034 2047 2042 2231
    ## [43807] 2213 2200 2215 2155 2231 2049 2050 2109 2251 2143 2059 2214 2113 2059
    ## [43821] 2104 2225 2235 2145 2221 2044 2213 2116 2043 2135 2139 2119 2246 2136
    ## [43835] 2219 2253 2117 2318 2308 2226 2332 2223 2236 2312 2102 2208 2133 2157
    ## [43849] 2255 2210 2115 2123 2122 2125 2112 2256 2225 2335 2123 2123 2317 2309
    ## [43863] 2345 2139 2339 2156 2201 2149 2242 2120 2316 2154 2202   10 2216 2143
    ## [43877] 2313 2255 2148 2200 2243 2347 2152 2359 2153 2335 2145    8   21 2203
    ## [43891] 2149 2205 2226 2233 2354 2349 2355 2330   28 2356 2240 2241 2309 2327
    ## [43905] 2259 2323 2349 2332 2303 2307 2247   26 2231   33   14 2231 2328 2351
    ## [43919]   20    2 2238   36 2257 2356   19 2343  129   38 2253 2301 2304 2307
    ## [43933] 2312 2310  113  139   25   48 2345    7   13 2359    7   10   10   NA
    ## [43947]  647  811  845  920  844  919  713  843  713  826  900  643  747  842
    ## [43961]  723  836  720  904  858  903  804  808  730  812  848  749  822 1010
    ## [43975]  908  916 1635  942  859  931  830  829  912  852  759  756  916  902
    ## [43989]  926  900  954  805  936  757  804 1009 1036  855  953  932  942  956
    ## [44003] 1024 1050 1005  942  925  929  925 1010  953 1000  826 1024  853  840
    ## [44017] 1013 1030 1002  901 1025  850 1030 1057 1030  912 1022 1016 1033  933
    ## [44031]  907  814  932 1013 1030 1007  959 1034 1046  906  936 1123 1020  921
    ## [44045] 1036 1043  847  917  904  935  855 1005  914 1032 1000 1054  931 1137
    ## [44059] 1118 1050 1031 1056 1023  929 1109 1058  932 1024  948 1049 1115 1138
    ## [44073] 1051 1102  937 1133  958 1044 1048 1003 1022 1038 1154 1113 1000  918
    ## [44087] 1056 1155 1132 1036 1050 1153 1005 1136 1013 1111 1012 1022 1135  929
    ## [44101] 1057  940 1003 1127  958 1108  943  924  944 1146 1013 1056 1203 1222
    ## [44115] 1004 1200 1045 1017 1121 1058 1203 1151 1020 1152 1113 1158 1009 1028
    ## [44129] 1226 1155 1223 1230 1205 1057 1139 1211 1018 1212 1226 1239 1022 1201
    ## [44143] 1046 1056 1237 1301 1159 1150 1129 1148 1328 1255 1210 1105 1201 1057
    ## [44157] 1226 1317 1110 1248 1134 1205 1310 1118 1325 1453 1350 1259 1248 1336
    ## [44171] 1205 1121 1111 1331 1301 1204 1144 1212 1315 1332 1238 1231 1346 1330
    ## [44185] 1244 1300 1359 1225 1354 1249 1137 1342 1333 1344 1225 1248 1202 1309
    ## [44199] 1403 1238 1159 1305 1330 1228 1344 1240 1327 1345 1314 1248 1349 1205
    ## [44213] 1406 1245 1341 1430 1433 1405 1455 1311 1317 1243 1343 1235 1501 1327
    ## [44227] 1319 1449 1248 1402 1246 1406 1328 1433 1410 1505 1354 1425 1351 1440
    ## [44241] 1254 1314 1415 1504 1452 1431 1435 1400 1336 1332 1527 1426 1303 1503
    ## [44255] 1501 1524 1423 1450 1414 1421 1547 1322 1319 1533 1356 1320 1432 1431
    ## [44269] 1338 1441 1408 1549 1542 1443 1554 1342 1601 1428 1536 1451 1401 1531
    ## [44283] 1519 1412 1551 1431 1413 1556 1631 1513 1446 1506 1610 1611 1435 1542
    ## [44297] 1621 1558 1623 1625 1610 1614 1601 1600 1614 1632 1543 1437 1605 1802
    ## [44311] 1555 1629 1644 1702 1505 1607 1645 1612 1700 1550 1448 1632 1646 1627
    ## [44325] 1609 1653 1513 1546 1550 1527 1557 1557 1551 1713 1605 1717 1703 1724
    ## [44339] 1600 1614 1539 1654 1624 1725 1730 1819 1713 1541 1656 1610 1745 1735
    ## [44353] 1700 1719 1737 1736 1547 1614 1702 1638 1752 1808 1601 1804 1716 1736
    ## [44367] 1647 1747 1600 1630 1812 1802 1717 1737 1804 1746 1725 1645 1707 1718
    ## [44381] 1643 1800 1740 1631 1656 1747 1852 1704 1808 1810 1631 1759 1725 1818
    ## [44395] 1830 1658 1719 1835 1757 1710 1843 1843 1651 1837 1728 1634 1646 1801
    ## [44409] 1826 1859 1855 1847 1833 1808 1842 1756 1857 1734 1841 1713 1859 1852
    ## [44423] 1836 1845 1932 1918 1901 1725 1749 1736 1801 1853 1908 1733 1754 1918
    ## [44437] 1926 1914 1722 1932 1940 1747 1809 1811 1732 1911 1804 1749 1915 1937
    ## [44451] 1937 1808 1928 1857 1933 1918 1926 1837 1926 2002 1830 1934 1839 2000
    ## [44465] 1929 1851 1932 1916 1833 1944 1807 1937 1909 2004 2004 1911 2001 2020
    ## [44479] 1949 1932 1955 1901 1839 2008 1903 1901 1816 1908 1806 1829 1947 1825
    ## [44493] 1923 1830 1839 1928 2020 2030 2024 1916 2000 1834 1935 2014 1830 1902
    ## [44507] 1923 1909 1936 1942 2044 2031 2038 2024 1933 2023 2037 1946 2009 1922
    ## [44521] 1852 2058 2039 1934 1919 2032 2059 2040 1906 2051 1917 2106 1959 2037
    ## [44535] 2105 2128 2037 2054 1939 1954 1942 1924 2001 1915 2100 2130 2125 2131
    ## [44549] 2140 2146 2004 2015 2148 2025 2149 2022 2124 2008 2203 2202 2040 2129
    ## [44563] 2130 2203 2205 2046 2112 2219 2146 2043 2158 2214 2140 2250 2031 2052
    ## [44577] 2204 2147 2246 2239 2231 2221 2232 2247 2241 2132 2233 2151 2243 2236
    ## [44591] 2101 2305 2146 2107 2124 2110 2234 2137 2328 2124 2329 2323 2326 2206
    ## [44605] 2252 2303 2331 2331    2 2202   29   46   35    1   22 2325 2230   33
    ## [44619] 2349  131 2251 2256 2325 2344 2353 2335    1  333   NA   NA  754  922
    ## [44633]  843  703  921  713  905  836  650  840  749  906  904  721  847  809
    ## [44647]  818  730  837  755  901  802  919  747  929  905  821  842  914  832
    ## [44661]  908  924  943  923  926  947  940  756 1024  910  816  809  951  957
    ## [44675] 1015  759  918 1008 1040  826  955 1001  945 1023 1011 1004  849  829
    ## [44689] 1010 1014  957 1030  819  855  958  817  812 1019 1018 1036 1000 1033
    ## [44703] 1109  940 1039 1021 1026 1039 1037  959 1108  949 1057 1048 1050 1010
    ## [44717]  935 1052  903 1053  936 1000 1045  939  913  926 1048  927 1053 1049
    ## [44731] 1022 1024  946  952 1035  948  945 1111 1057 1158  911  920 1055 1012
    ## [44745] 1100 1110 1125 1140 1056 1103  955 1054 1038 1110  934 1012 1108 1152
    ## [44759] 1050 1047  918 1012 1128 1012 1019 1055 1121 1119 1004 1142 1027  952
    ## [44773]  922 1031 1139 1040 1032  926 1130  929 1201 1136 1112 1000  930 1045
    ## [44787] 1121  947 1019 1011 1048 1033  958 1033 1214 1035  927 1105 1107  947
    ## [44801] 1116 1139  951 1206 1228 1159 1207 1116 1017 1013 1202 1151 1151 1213
    ## [44815] 1121 1207 1157 1045 1024 1011 1234 1151 1011 1039 1205 1106 1214 1222
    ## [44829] 1136 1132 1202 1032 1143 1146 1213 1025 1223 1243 1230 1036 1222 1131
    ## [44843] 1221 1100 1215 1034 1215 1036 1055 1156 1157 1241 1239 1101 1103 1056
    ## [44857] 1234 1153 1238 1216 1442 1135 1110 1201 1214 1312 1054 1306 1201 1124
    ## [44871] 1232 1208 1136 1136 1318 1228 1324 1226 1316 1238 1140 1246 1235 1122
    ## [44885] 1328 1315 1326 1240 1209 1349 1241 1330 1156 1314 1342 1337 1232 1357
    ## [44899] 1338 1223 1351 1239 1353 1232 1156 1411 1221 1221 1338 1208 1359 1351
    ## [44913] 1241 1202 1219 1251 1419 1420 1240 1241 1410 1325 1331 1231 1425 1326
    ## [44927] 1318 1407 1223 1334 1413 1437 1340 1249 1430 1424 1328 1254 1444 1447
    ## [44941] 1504 1248 1334 1441 1529 1321 1305 1457 1309 1410 1419 1348 1352 1306
    ## [44955] 1456 1438 1437 1258 1457 1459 1319 1300 1403 1339 1433 1451 1346 1406
    ## [44969] 1522 1439 1426 1402 1319 1411 1456 1409 1326 1341 1431 1548 1400 1410
    ## [44983] 1512 1539 1435 1554 1358 1543 1539 1553 1547 1522 1411 1403 1450 1512
    ## [44997] 1406 1525 1553 1556 1459 1433 1601 1440 1557 1452 1542 1417 1606 1430
    ## [45011] 1351 1606 1534 1444 1417 1451 1515 1513 1602 1509 1454 1513 1431 1510
    ## [45025] 1429 1426 1618 1610 1552 1547 1614 1630 1551 1618 1456 1543 1758 1701
    ## [45039] 1539 1645 1633 1506 1608 1645 1656 1650 1611 1440 1540 1514 1458 1551
    ## [45053] 1615 1514 1641 1510 1648 1638 1646 1547 1626 1451 1523 1452 1502 1613
    ## [45067] 1549 1511 1656 1558 1718 1626 1504 1635 1521 1650 1556 1540 1610 1717
    ## [45081] 1709 1656 1711 1702 1629 1547 1621 1603 1731 1626 1624 1827 1825 1621
    ## [45095] 1635 1550 1557 1611 1649 1822 1747 1604 1710 1728 1711 1747 1734 1547
    ## [45109] 1559 1632 1750 1759 1817 1702 1556 1741 1601 1707 1657 1817 1623 1615
    ## [45123] 1732 1806 1736 1711 1714 1650 1701 1639 1758 1743 1721 1754 1704 1617
    ## [45137] 1822 1824 1711 1915 1640 1801 1830 1807 1838 1740 1818 1739 1810 1812
    ## [45151] 1852 1836 1647 1821 1651 1637 1655 1726 1908 1827 1646 1901 1703 1900
    ## [45165] 1719 1746 1657 1701 1717 1659 1823 1906 1744 1756 1855 1847 1700 1912
    ## [45179] 1700 1813 1746 1715 1737 1718 1716 1901 1828 1841 1941 1801 1735 1844
    ## [45193] 1717 1916 1811 1902 1750 1826 1730 1808 1749 1814 1723 1804 1732 1820
    ## [45207] 1931 1916 1846 1918 1918 1835 1831 1802 1825 1727 1737 1818 1843 1744
    ## [45221] 1944 1927 1925 1922 1804 1935 1814 1918 1907 1952 1924 1836 1733 1827
    ## [45235] 1818 1903 1905 1834 1912 1853 1823 1841 1844 1932 1809 1804 1953 1956
    ## [45249] 1927 1835 1956 2004 1856 1954 1806 1927 1853 2004 1956 1845 2013 1824
    ## [45263] 1825 1958 1939 1809 1946 1915 1824 2027 1906 2019 1953 1853 1952 2007
    ## [45277] 1815 2116 1901 2025 2010 1900 2007 1947 1927 2051 1829 1957 1853 2029
    ## [45291] 1916 2024 2030 2020 1843 1837 1858 2052 1945 1836 1840 1932 2003 2109
    ## [45305] 1912 1940 2046 1939 2025 1956 2045 2031 2031 2019 2016 2055 2003 1858
    ## [45319] 1906 1904 2057 2011 1937 1918 1921 2001 2104 2126 1934 2048 2040 2106
    ## [45333] 2115 1950 2045 1949 2103 1956 2123 2002 2136 1951 2137 2141 2003 2052
    ## [45347] 2131 2107 2036 2035 2114 2035 2209 2016 2039 2136 2106 2132 2011 2138
    ## [45361] 2049 2136 2048 1956 2337 2119 2134 2159 2135 2017 1955 2059 2019 2020
    ## [45375] 2200 2103 2048 2139 2050 2212 2122 2009 2131 2119 2212 2201 2132 2019
    ## [45389] 2151 2054 2135 2055 2221 2154 2111 2130 2132 2200 2215 2045 2048 2218
    ## [45403] 2147 2208 2132 2035 2137 2044 2214 2213 2141 2200 2230 2231 2217 2104
    ## [45417] 2223 2112 2159 2233 2223 2203 2200 2149 2238 2135 2114 2245 2246 2106
    ## [45431] 2102 2144 2126 2117 2304 2205 2045 2251 2145 2118 2212 2139 2053 2108
    ## [45445] 2136 2250 2209 2239 2115 2114 2115 2243 2250 2138 2128 2302 2218 2104
    ## [45459] 2314 2118 2259 2149 2121 2311 2319 2147 2120 2207 2120 2235 2148 2315
    ## [45473] 2233 2143 2347 2248 2149 2205 2128 2203 2321   16 2310 2208 2307 2334
    ## [45487] 2156 2335 2253 2333 2359 2331 2147 2219 2208 2344 2157 2257 2158 2359
    ## [45501] 2201 2336 2320   41 2240   17 2247 2210 2341 2340 2300   54    8 2340
    ## [45515] 2221 2356 2337   23 2238 2335 2226   22  107 2241    4   21 2306 2355
    ## [45529] 2245 2258 2259 2306 2255  141 2315 2330   51  121 2342 2359 2354 2357
    ## [45543] 2352   44  330  635  741  825  926  903  819  712  851  844  852  637
    ## [45557]  647  858  744  832  846  859  719  724  710  655  825  743  833  721
    ## [45571]  701  800  714  759  746  911  736  809  820  800  721  809  914  906
    ## [45585]  917  808  750  811  813  957  843  940  817  812  805  825  850  921
    ## [45599]  920  725  847  750  834  740  823  859  920  800  911  931  915  808
    ## [45613]  842  934  806  935  806  908  819  906  815  855  807 1036  935  931
    ## [45627]  804  842 1002 1028  945  855 1013 1025  944  844 1004  955  959  959
    ## [45641] 1003  919  859  845 1015 1008  959 1019  921  906  958  834 1006 1019
    ## [45655]  956  957  924  933  820  925 1011 1029 1025 1027 1037 1034  949 1029
    ## [45669] 1027 1114 1117 1045 1040  917  920 1031 1058 1008 1052  942  946 1034
    ## [45683]  903 1027  950  927  848 1029 1011  901  927  933 1100 1004 1058  931
    ## [45697]  933 1101 1036 1142  935 1102  928 1058 1115 1020  925 1002 1055 1002
    ## [45711]  913 1025 1050 1103  952 1043 1129 1101 1056 1126 1048  929  931 1051
    ## [45725] 1054 1043 1151 1014 1020 1024  919 1018 1130  934 1014 1200 1106  951
    ## [45739]  953 1016 1014 1019  959 1140 1135  957 1055  959 1045 1032  941 1143
    ## [45753] 1032  957  929 1022 1024 1135 1040 1122  952 1112 1104 1044 1125 1201
    ## [45767]  929 1028 1126 1002 1016 1115 1033 1140 1102  956 1152 1202 1228 1141
    ## [45781] 1007 1014 1203 1036 1010 1151 1139 1027 1158 1147 1153 1147 1157 1036
    ## [45795] 1204 1211 1208 1222 1009 1117 1058 1239 1014 1159 1148 1116 1152 1210
    ## [45809] 1218 1228 1153 1226 1224 1153 1030 1226 1124 1215 1119 1217 1141 1105
    ## [45823] 1229 1120 1255 1121 1131 1206 1154 1257 1203 1153 1218 1441 1104 1113
    ## [45837] 1130 1203 1120 1133 1236 1235 1139 1256 1212 1247 1251 1214 1144 1157
    ## [45851] 1304 1124 1146 1244 1211 1212 1144 1132 1203 1326 1235 1320 1259 1221
    ## [45865] 1303 1235 1335 1241 1138 1327 1335 1203 1332 1249 1231 1342 1343 1405
    ## [45879] 1326 1307 1200 1235 1328 1227 1250 1355 1150 1216 1350 1324 1251 1225
    ## [45893] 1332 1418 1224 1341 1214 1257 1209 1210 1245 1201 1229 1418 1249 1331
    ## [45907] 1339 1410 1253 1214 1329 1423 1230 1415 1356 1312 1259 1400 1319 1324
    ## [45921] 1424 1436 1432 1343 1335 1437 1400 1424 1444 1405 1341 1459 1253 1407
    ## [45935] 1256 1447 1355 1447 1452 1424 1415 1334 1321 1449 1322 1533 1449 1320
    ## [45949] 1451 1308 1326 1506 1431 1345 1508 1316 1322 1311 1403 1333 1342 1348
    ## [45963] 1452 1424 1435 1413 1415 1431 1519 1346 1548 1545 1421 1433 1507 1534
    ## [45977] 1602 1448 1349 1354 1456 1442 1357 1610 1546 1537 1348 1359 1352 1516
    ## [45991] 1540 1550 1548 1423 1420 1549 1514 1424 1508 1443 1512 1512 1453 1611
    ## [46005] 1446 1430 1608 1540 1618 1606 1432 1520 1604 1540 1629 1617 1617 1446
    ## [46019] 1548 1627 1515 1606 1513 1553 1631 1533 1512 1636 1710 1609 1450 1608
    ## [46033] 1652 1643 1642 1512 1630 1445 1503 1455 1608 1817 1703 1606 1650 1508
    ## [46047] 1628 1512 1601 1712 1518 1626 1512 1630 1642 1551 1620 1549 1724 1735
    ## [46061] 1611 1601 1550 1653 1715 1651 1730 1544 1609 1623 1556 1525 1830 1731
    ## [46075] 1716 1544 1712 1550 1633 1546 1545 1751 1638 1541 1748 1618 1627 1631
    ## [46089] 1627 1629 1604 1558 1747 1802 1741 1751 1556 1603 1807 1738 1808 1743
    ## [46103] 1720 1708 1628 1711 1757 1641 1622 1749 1735 1716 1626 1715 1704 1742
    ## [46117] 1742 1810 1810 1758 1742 1718 1801 1820 1821 1714 1824 1906 1635 1649
    ## [46131] 1809 1711 1756 1731 1657 1823 1719 1720 1824 1843 1843 1824 1646 1644
    ## [46145] 1746 1708 1702 1852 1835 1842 1719 1848 1651 1658 1656 1759 1812 1858
    ## [46159] 1748 1929 1759 1838 1733 1724 1853 1744 1731 1834 1909 1850 1740 1739
    ## [46173] 1810 1854 1811 1734 1723 1658 1743 1850 1836 1829 1900 1722 1851 1744
    ## [46187] 1725 1753 1752 1809 1919 1904 1900 1845 1718 1819 1818 1732 1914 1742
    ## [46201] 1829 1803 1746 1922 1814 1912 1721 1740 1818 1923 1851 1834 1738 1918
    ## [46215] 1951 1937 1936 1829 1806 1934 2001 1833 1932 1903 1802 1830 1855 1907
    ## [46229] 1949 1918 1827 1941 1943 1914 1824 1903 1839 1805 1935 1758 1952 2005
    ## [46243] 1831 1804 2044 1932 1805 1947 1912 1855 1953 1953 1825 2017 2024 2013
    ## [46257] 1901 1908 2015 1817 1956 1840 1849 2016 1946 1915 1906 1824 1922 1923
    ## [46271] 1905 2022 2030 1932 1825 1937 1910 1908 1944 1937 1902 2023 2018 1830
    ## [46285] 1841 2040 2031 2024 1855 2023 1951 2006 2035 1933 2026 2104 1941 2042
    ## [46299] 2057 2014 1847 1911 2021 1949 2050 1922 1901 2033 1858 2029 2011 2049
    ## [46313] 2054 1956 2045 1939 2020 2100 2024 2021 2117 1944 1945 2012 2138 1953
    ## [46327] 2113 1934 2112 1954 1941 2037 1945 2135 1947 2140 2023 2022 2019 2033
    ## [46341] 1956 2048 2059 1930 2023 2131 2151 2144 2114 2139 2135 1957 2155 2136
    ## [46355] 2023 2152 2103 2148 2036 2104 2011 2146 2009 1945 2002 2046 2018 2200
    ## [46369] 2018 2203 2202 2210 2118 2105 2048 2215 2013 2141 2056 2201 2056 2033
    ## [46383] 2120 2156 2127 2103 2214 2137 2125 2006 2100 2150 2211 2131 2209 2220
    ## [46397] 2106 2106 2032 2141 2159 2031 2223 2225 2047 2145 2254 2237 2228 2107
    ## [46411] 2316 2210 2114 2139 2213 2242 2054 2307 2113 2141 2137 2216 2227 2122
    ## [46425] 2259 2116 2255 2316 2227 2312 2302 2251 2155 2140 2310 2130 2234 2316
    ## [46439] 2102 2229 2247 2249 2254 2158 2130 2204 2153 2149 2135 2325 2152 2124
    ## [46453] 2322 2310 2126 2318 2154 2204 2124 2250 2235 2139 2146 2333 2354 2223
    ## [46467] 2235 2328 2338 2145 2207 2317 2252 2209 2151 2140 2329 2341 2257 2337
    ## [46481] 2204 2211   24 2338 2325 2200 2216 2211 2201    3 2331    9 2230 2207
    ## [46495]   24 2235    3 2319 2244 2300 2300   18   41 2356 2331 2237 2352   11
    ## [46509] 2342 2355    7 2321 2240 2248 2241    4   29 2258  132 2240 2259 2326
    ## [46523] 2354 2311 2325 2336 2337 2355 2334 2357    3  534  351   NA   NA   NA
    ## [46537]  636  758  831  921  921  852  656  930  720  647  832  704  738  752
    ## [46551]  651  642  843  840  742  701  858  847  855  839  717  723  733  757
    ## [46565]  842  742  717  807  803  835  723  816  835  804  740  825  919  921
    ## [46579]  741  900  951  902  828  835  857  945  751  813  741  743  757  852
    ## [46593]  845 1003  908  952  818  914  835  924  920  932  836  943  756  818
    ## [46607]  846 1000  933  842  752  750  917 1009  956 1001  953  819  953 1008
    ## [46621]  928  926 1049 1002  920 1008 1015 1011 1010  846  919  835  843 1002
    ## [46635] 1055 1015 1015  948 1015 1037  818 1030  903  930 1038  955 1008 1010
    ## [46649] 1015 1034  825  912  906  911  952 1045 1035 1008 1047 1004 1052 1025
    ## [46663]  948 1031 1132 1039  943  905 1153  946  927 1009  925  944 1036 1048
    ## [46677]  925 1112  917 1046 1106  848  905 1027  933 1026  955 1027  929  934
    ## [46691] 1037  924 1108 1105  914  915 1029 1035  952 1111 1103 1107 1135 1022
    ## [46705] 1102 1123 1111 1109 1042 1045 1026 1110 1209 1121 1048 1018  943 1027
    ## [46719] 1109 1025 1127  951 1137 1023  921  935 1036 1208 1118 1029 1056  959
    ## [46733] 1057 1019 1106 1054 1041 1014 1214  945 1007 1150 1031 1007 1016 1007
    ## [46747] 1146  948  945  958 1027  952 1018 1149 1143  947 1156 1214 1113 1010
    ## [46761] 1038 1011 1237 1003 1137 1158 1131 1049 1009 1158 1223 1136 1027 1059
    ## [46775] 1222 1202 1009 1205 1152 1222 1107 1129 1218 1222 1138 1233 1135 1113
    ## [46789] 1219 1211 1130 1232 1152 1215 1114 1253 1154 1122 1223 1248 1215 1258
    ## [46803] 1041 1228 1049 1057 1207 1222 1048 1058 1234 1203 1144 1115 1137 1059
    ## [46817] 1050 1119 1214 1113 1051 1135 1258 1238 1110 1232 1110 1153 1119 1217
    ## [46831] 1304 1137 1155 1134 1241 1316 1213 1214 1144 1213 1319 1259 1238 1305
    ## [46845] 1120 1245 1337 1304 1146 1212 1138 1334 1329 1245 1317 1245 1346 1315
    ## [46859] 1240 1307 1153 1331 1344 1207 1329 1345 1352 1225 1230 1207 1155 1239
    ## [46873] 1238 1249 1216 1248 1416 1331 1353 1210 1223 1355 1401 1426 1228 1250
    ## [46887] 1319 1247 1349 1223 1428 1254 1404 1353 1426 1415 1311 1403 1234 1332
    ## [46901] 1317 1334 1336 1431 1404 1255 1427 1300 1439 1322 1409 1311 1419 1439
    ## [46915] 1337 1312 1450 1258 1308 1326 1301 1303 1515 1357 1414 1452 1335 1458
    ## [46929] 1501 1508 1418 1442 1354 1313 1319 1406 1435 1510 1520 1355 1337 1424
    ## [46943] 1419 1516 1538 1551 1521 1534 1529 1534 1516 1353 1429 1402 1347 1446
    ## [46957] 1359 1448 1434 1401 1534 1556 1558 1549 1403 1516 1602 1431 1416 1400
    ## [46971] 1542 1539 1601 1453 1634 1444 1426 1418 1447 1543 1551 1520 1521 1510
    ## [46985] 1458 1439 1630 1610 1601 1448 1550 1536 1521 1526 1506 1636 1553 1638
    ## [46999] 1621 1638 1534 1512 1540 1454 1813 1457 1700 1521 1452 1540 1559 1546
    ## [47013] 1449 1704 1637 1449 1603 1447 1652 1602 1704 1606 1648 1643 1550 1649
    ## [47027] 1458 1629 1636 1544 1651 1710 1519 1720 1540 1705 1704 1552 1757 1610
    ## [47041] 1515 1533 1722 1532 1727 1732 1601 1607 1814 1736 1605 1744 1619 1809
    ## [47055] 1632 1728 1634 1750 1620 1730 1809 1632 1618 1809 1731 1700 1753 1803
    ## [47069] 1757 1555 1716 1735 1807 1558 1541 1743 1732 1611 1802 1657 1618 1701
    ## [47083] 1750 1759 1647 1623 1709 1630 1638 1718 1759 1832 1753 1801 1802 1806
    ## [47097] 1637 1933 1639 1715 1755 1721 1902 1810 1828 1713 1644 1654 1724 1844
    ## [47111] 1813 1754 1642 1650 1640 1714 1836 1834 1709 1749 1852 1658 1833 1838
    ## [47125] 1704 1846 1737 1859 1718 1731 1813 1759 1903 1753 1828 1916 1817 1915
    ## [47139] 1733 1820 1820 1859 1708 1853 1711 1727 1843 1646 1719 1750 1752 1831
    ## [47153] 1844 1752 1734 1828 1853 1938 1854 1933 1749 1908 1850 1712 1816 2019
    ## [47167] 1905 1748 1712 1817 1819 1816 1738 1829 1926 1839 1733 1829 1837 1951
    ## [47181] 1748 1754 1828 1941 1933 1815 1927 1948 1928 1836 1959 1829 1905 1938
    ## [47195] 1942 2016 1850 1905 1811 1844 1919 1901 1833 1816 1836 1949 1759 1856
    ## [47209] 1813 1930 2010 1835 1949 1825 1907 1759 2005 1804 1958 2010 1847 1826
    ## [47223] 2011 2003 2004 1758 1953 1823 1949 1905 1819 2009 1832 1811 2020 2019
    ## [47237] 2006 2013 1817 1929 2021 2009 1842 1908 2017 1859 2011 1938 1821 1923
    ## [47251] 1904 2031 1916 2039 1943 1932 1939 1852 1835 1953 2021 2003 1943 1901
    ## [47265] 2037 1922 1934 2103 2035 1936 1944 2011 2015 2014 1906 1935 2058 2050
    ## [47279] 2017 2037 2109 1954 2049 1926 1919 2043 1854 1910 2109 1938 1914 1930
    ## [47293] 2038 2013 2017 2049 2103 1959 1957 2005 2116 2130 2017 2011 2016 2123
    ## [47307] 2027 1958 2119 1959 1920 2025 2032 1953 2034 2028 2113 2127 2052 2133
    ## [47321] 2058 2137 2136 2150 2114 2016 2203 1957 2027 2026 2149 2129 2023 2206
    ## [47335] 2204 2145 2019 2059 2041 2003 2213 2002 2047 2206 1959 2142 2111 2152
    ## [47349] 2142 2134 2042 2150 2053 2022 2150 2028 2156 2027 2031 2041 2051 2116
    ## [47363] 2123 2201 2142 2217 2213 2149 2123 2233 2204 2043 2233 2153 2224 2144
    ## [47377] 2157 2217 2227 2121 2038 2206 2245 2226 2220 2137 2040 2245 2245 2112
    ## [47391] 2241 2138 2153 2240 2105 2302 2023 2237 2102 2231 2249 2130 2239 2125
    ## [47405] 2104 2053 2158 2107 2153 2059 2106 2232 2311 2248 2154 2112 2247 2251
    ## [47419] 2246 2304 2107 2215 2152 2107 2100 2252 2127 2314 2120 2302 2140 2138
    ## [47433] 2330 2242 2246 2323 2136 2120 2324 2215 2205 2133 2138 2330 2227 2146
    ## [47447] 2205 2252 2137 2350 2349 2211 2158 2232 2249 2156 2153 2400 2143 2301
    ## [47461] 2337 2328 2344 2309 2351   55 2344 2356 2239 2359 2244 2210 2321 2207
    ## [47475] 2243 2338 2306   57 2350 2334 2246   48 2257  124 2303 2245 2257 2248
    ## [47489] 2302   39 2317 2347 2334 2351 2353   17  347   NA   NA   NA  632  749
    ## [47503]  837  935  930  856  711  900  716  735  646  820  734  720  902  705
    ## [47517]  837  650  703  905  746  920  904  710  735  724  809  716  804  856
    ## [47531]  758  701  822  750  727  801  830  731  752  901  917  728  738  743
    ## [47545]  919  850  844  910  809  925  837  945  836  825  751  938  749  819
    ## [47559]  940  917  937  837  808  915  851  915  801  806  831 1009  828  859
    ## [47573]  739  743  802  954  907  905 1051  757  758  922 1035 1005 1009 1021
    ## [47587]  920  944 1008  821  903  954  940  855  833 1018 1032  932  837  838
    ## [47601] 1017 1005 1008  956 1014 1019 1006  958  946 1025  816 1034 1027 1059
    ## [47615] 1124 1025 1020 1030  859 1030 1040 1145 1011  959 1124  955 1051 1055
    ## [47629] 1055  932  914 1055 1036  937 1007 1106  851 1007 1011 1104 1115  921
    ## [47643] 1019  924  916 1052  934 1038 1130 1100  939  921 1003 1021  901 1153
    ## [47657]  913  956  921 1108 1031  945 1111 1055 1102  924 1048 1100 1117 1045
    ## [47671] 1058 1000 1102 1104 1046 1019 1230 1016 1138 1022  914 1018 1114  937
    ## [47685] 1023 1206 1022 1114 1049 1013  935 1011  928  927 1213 1126 1030 1206
    ## [47699] 1118 1027 1057 1142 1113 1049 1043 1053 1018 1018 1117 1014  959  941
    ## [47713] 1116  942 1059 1136 1056 1015 1009 1139 1055 1025 1147 1202 1209 1156
    ## [47727] 1120 1159  958 1128 1224 1241 1010 1148 1201 1142 1025 1224 1048 1048
    ## [47741] 1039 1212 1205 1208 1206 1035 1109 1107 1207 1019 1215 1216 1218 1156
    ## [47755] 1021 1228 1120 1151 1208 1227 1234 1229 1147 1245 1131 1238 1030 1228
    ## [47769] 1202 1248 1227 1108 1101 1132 1100 1152 1111 1206 1149 1217 1101 1137
    ## [47783] 1120 1108 1109 1212 1120 1431 1048 1109 1157 1243 1138 1157 1141 1235
    ## [47797] 1209 1233 1252 1307 1159 1158 1211 1158 1326 1146 1334 1320 1241 1220
    ## [47811] 1235 1116 1306 1204 1345 1345 1228 1132 1342 1242 1301 1320 1246 1143
    ## [47825] 1356 1154 1257 1356 1359 1351 1213 1244 1352 1204 1241 1215 1251 1423
    ## [47839] 1353 1354 1245 1238 1352 1333 1201 1250 1256 1303 1415 1353 1225 1323
    ## [47853] 1204 1401 1253 1410 1349 1337 1446 1504 1301 1318 1307 1233 1335 1440
    ## [47867] 1427 1355 1435 1413 1322 1352 1309 1439 1507 1258 1418 1414 1248 1501
    ## [47881] 1457 1440 1341 1348 1442 1309 1413 1522 1422 1301 1448 1359 1306 1451
    ## [47895] 1349 1409 1417 1527 1349 1449 1316 1354 1401 1333 1314 1442 1337 1531
    ## [47909] 1535 1400 1403 1425 1510 1502 1507 1429 1356 1542 1530 1447 1507 1456
    ## [47923] 1347 1545 1458 1535 1421 1422 1438 1508 1552 1453 1508 1427 1606 1552
    ## [47937] 1627 1602 1552 1555 1556 1416 1408 1419 1421 1508 1605 1444 1617 1557
    ## [47951] 1525 1643 1453 1554 1657 1546 1531 1759 1513 1548 1618 1702 1507 1532
    ## [47965] 1732 1544 1607 1711 1640 1521 1630 1543 1542 1547 1542 1541 1658 1607
    ## [47979] 1626 1514 1706 1522 1614 1502 1452 1451 1616 1555 1546 1607 1715 1643
    ## [47993] 1649 1551 1658 1637 1604 1736 1529 1655 1603 1533 1630 1537 1526 1720
    ## [48007] 1515 1556 1738 1731 1717 1756 1631 1558 1712 1638 1808 1610 1600 1541
    ## [48021] 1558 1637 1719 1856 1738 1645 1638 1756 1705 1712 1802 1640 1718 1603
    ## [48035] 1626 1757 1816 1818 1621 1538 1650 1808 1801 1800 1733 1637 1721 1759
    ## [48049] 1606 1726 1650 1714 1619 1803 1805 1834 1817 1752 1822 1721 1622 1729
    ## [48063] 1641 1655 1730 1740 1809 1648 1723 1623 2004 1832 1703 1807 1744 1734
    ## [48077] 1822 1824 1816 1840 1721 1805 1710 1704 1738 1825 1921 1816 1908 1851
    ## [48091] 1650 1834 1650 1853 1747 1714 1800 1716 1805 1655 1708 1946 1738 1829
    ## [48105] 1845 1751 1915 1826 1721 1900 1845 1722 1714 1729 1806 1854 1744 1730
    ## [48119] 1930 1816 1914 1856 1757 1939 1902 1724 1901 1903 1828 1918 1732 1821
    ## [48133] 1817 1737 1851 1827 1806 1836 1906 1821 1829 1717 1803 1939 1844 1728
    ## [48147] 1808 1923 1847 1851 2002 2018 1904 1823 1927 1758 1923 1830 1954 1759
    ## [48161] 1829 1957 1952 1901 1938 1817 1942 1830 1838 2000 1845 1919 2004 1921
    ## [48175] 1950 1839 1901 2009 1834 1857 1954 1929 1952 1815 1950 2016 1955 2022
    ## [48189] 1843 2324 2014 1825 1936 1852 1814 1813 1947 1900 1847 1846 1905 1815
    ## [48203] 1958 1924 2003 2012 1946 1922 1806 2037 1924 1910 2020 2015 2014 2020
    ## [48217] 2011 2042 2031 1904 1922 1955 1858 1830 1906 2017 1838 2020 1928 1932
    ## [48231] 1833 2038 2013 2042 1935 1918 2051 2037 1933 2029 1937 1900 2059 2049
    ## [48245] 2027 2104 2118 2003 2043 2024 2027 1950 1930 1936 1943 1952 2158 2013
    ## [48259] 2023 2122 2100 1954 1924 2105 2100 2051 1903 2033 1954 2017 1922 2027
    ## [48273] 2122 2030 2044 2028 2125 2202 1915 2126 2106 2023 2039 2028 2159 2008
    ## [48287] 2148 2006 2016 2111 2132 2111 2126 2108 2137 2010 2125 2104 2132 2153
    ## [48301] 2135 2036 2051 2151 2041 2012 2203 2003 2022 2115 2150 2157 2130 2208
    ## [48315] 2047 2030 2041 2131 2025 2241 2159 2111 2019 2147 2112 2214 2152 2209
    ## [48329] 2051 2206 2217 2217 2207 2236 2117 2126 2143 2054 2135 2202 2050 2107
    ## [48343] 2234 2103 2212 2201 2225 2231 2251 2058 2153 2119 2141 2226 2259 2247
    ## [48357] 2149 2139 2048 2218 2213 2244 2244 2200 2306 2251 2304 2044 2135 2223
    ## [48371] 2209 2304 2249 2201 2121 2332 2246 2228 2302 2246 2114 2330 2358 2305
    ## [48385] 2159 2243 2143 2225 2221 2143 2244 2115 2137 2118 2139 2156 2140 2223
    ## [48399] 2126 2212 2223 2333 2146 2334 2336 2214 2151 2331 2316 2138 2221 2250
    ## [48413] 2234   22 2326 2328 2201 2150 2204 2346   41 2233 2312 2205   16 2329
    ## [48427] 2244 2231   26 2320 2327  100   30 2322 2241 2320 2320 2356    3 2346
    ## [48441] 2217 2207 2330 2314 2236 2326 2349 2354 2318 2244   54 2251 2307  140
    ## [48455]   26 2250 2303   51 2252 2304 2346 2343 2355 2326 2330 2335 2346 2356
    ## [48469] 2349  403  339   NA   NA   NA   NA  640  759  834  941  846  947  853
    ## [48483]  837  650  648  830  718  701  856  710  656  707  710  858  754  923
    ## [48497]  848  745  712  739  712  808  907  802  717  743  812  824  831  718
    ## [48511]  800  725  801  845  916  810  933  931  908  747  835  851  745  729
    ## [48525]  818  815  842  935  833  903  747  908  918  922  931  837  845  755
    ## [48539]  811  801  946  936  909  823  939  929  851  858  800  935 1114  838
    ## [48553]  922  748  921  756  940  826  952  808  957 1017  804  954  958  934
    ## [48567] 1102  843 1032 1028 1002  950 1002  852 1009  956  827 1016  827 1000
    ## [48581]  946  948 1012  807 1004  941 1019 1012  957 1021 1024 1128 1047 1037
    ## [48595]  908  908 1017 1030  857  949 1025 1041 1041 1045  933 1010  950 1036
    ## [48609]  903 1138  950  847  926  927  907 1030 1103 1020  934 1011  912  936
    ## [48623]  938  922  919 1121  904 1044 1109  937 1114 1019 1040  909 1048 1107
    ## [48637] 1106  944 1123 1002  930 1104 1101 1132  957 1116 1042 1058 1010 1022
    ## [48651] 1018 1148 1213 1051 1139 1015 1022  958 1215  919 1125 1058 1002 1044
    ## [48665] 1120  959  939  952 1057  950 1138 1124  939 1018  952 1116  948 1004
    ## [48679] 1157 1107 1057 1119 1059  953 1133  930 1138 1037 1140 1013 1123  958
    ## [48693] 1051 1113 1120 1200 1138  956 1120 1105 1008 1150 1132 1007 1151 1025
    ## [48707] 1220 1151 1006 1229 1138 1038 1204 1252 1028 1216 1011 1215 1023 1012
    ## [48721] 1151 1142 1103 1030 1202 1245 1109 1202 1205 1210 1153 1152 1215 1226
    ## [48735] 1200 1211 1214 1224 1151 1027 1244 1147 1228 1125 1130 1235 1050 1029
    ## [48749] 1153 1241 1232 1054 1237 1052 1302 1153 1052 1154 1106 1226 1232 1139
    ## [48763] 1050 1249 1100 1150 1103 1218 1203 1159 1230 1240 1257 1236 1145 1300
    ## [48777] 1227 1132 1204 1213 1331 1237 1318 1133 1150 1143 1130 1215 1205 1145
    ## [48791] 1239 1228 1255 1335 1336 1255 1341 1247 1141 1325 1312 1325 1333 1203
    ## [48805] 1131 1353 1200 1350 1355 1313 1311 1341 1157 1231 1423 1245 1226 1242
    ## [48819] 1345 1206 1307 1223 1327 1221 1342 1222 1241 1440 1324 1300 1218 1406
    ## [48833] 1341 1246 1347 1213 1257 1244 1331 1220 1309 1403 1441 1343 1431 1316
    ## [48847] 1438 1417 1401 1438 1453 1257 1436 1303 1252 1402 1510 1350 1443 1502
    ## [48861] 1444 1253 1328 1454 1301 1337 1453 1449 1450 1308 1309 1526 1310 1454
    ## [48875] 1427 1334 1454 1450 1354 1500 1316 1359 1422 1526 1406 1314 1449 1333
    ## [48889] 1432 1340 1415 1537 1513 1537 1513 1431 1544 1418 1445 1346 1423 1551
    ## [48903] 1510 1334 1352 1428 1441 1355 1553 1401 1421 1351 1611 1406 1506 1349
    ## [48917] 1456 1424 1548 1405 1558 1549 1525 1612 1547 1608 1555 1424 1601 1549
    ## [48931] 1520 1620 1505 1520 1525 1426 1523 1615 1500 1438 1524 1804 1519 1605
    ## [48945] 1622 1615 1555 1701 1442 1450 1654 1647 1544 1537 1644 1548 1638 1634
    ## [48959] 1651 1703 1503 1523 1641 1550 1558 1638 1600 1633 1506 1600 1506 1453
    ## [48973] 1510 1507 1628 1703 1625 1507 1710 1548 1631 1527 1531 1639 1656 1650
    ## [48987] 1708 1708 1605 1700 1546 1700 1559 1608 1715 1540 1719 1616 1619 1724
    ## [49001] 1610 1615 1819 1555 1540 1548 1559 1735 1626 1738 1645 1800 1549 1811
    ## [49015] 1757 1649 1817 1744 1708 1643 1729 1752 1640 1811 1557 1818 1755 1754
    ## [49029] 1803 1632 1630 1607 1558 1702 1631 1825 1601 1610 1749 1648 1652 1633
    ## [49043] 1743 1728 1646 1714 1647 1753 1723 1727 1722 1748 1820 1726 1641 1719
    ## [49057] 1702 1808 1622 1849 1743 1734 1902 1808 1838 1830 1715 1822 1658 1701
    ## [49071] 1645 1849 1755 1856 1711 1823 1755 1835 1840 1902 1756 1805 1830 1721
    ## [49085] 1755 1659 1951 1704 1734 1823 1716 1819 1917 1721 1903 1716 1907 2009
    ## [49099] 1848 1836 1809 1809 1710 1854 1914 1711 1747 1753 1756 1909 1855 1919
    ## [49113] 1745 1726 1809 1736 1840 1731 1745 1743 1913 1752 1812 1741 1824 1909
    ## [49127] 1828 1944 1740 1746 1936 1914 2004 1802 2005 1906 1844 1752 1852 2146
    ## [49141] 1859 1950 1933 1826 1848 1817 1752 1841 1948 1957 1959 1852 1843 1926
    ## [49155] 1850 1857 1913 1815 1808 2001 2002 1931 1934 1847 1936 1835 1954 1808
    ## [49169] 1809 1829 2000 1913 1908 1827 1842 2021 1833 1912 1815 1946 1829 1816
    ## [49183] 2011 2008 2022 1857 2042 1832 2008 1955 1909 1849 2029 2019 1938 1920
    ## [49197] 1852 1940 2026 1949 1901 2023 1850 1905 1954 2035 1948 2025 1853 2024
    ## [49211] 1923 2038 1946 2036 2006 2034 2037 2044 2015 2038 1859 2108 2030 1934
    ## [49225] 1859 1905 2052 1902 2047 2106 1906 2026 1907 1939 1955 2055 1936 1909
    ## [49239] 2007 2103 2056 1908 2018 1955 2004 2151 2035 2123 2113 1937 1932 2112
    ## [49253] 2129 2008 2023 2125 1939 2130 2101 2016 1949 2025 1933 2006 2143 1936
    ## [49267] 2005 2128 2131 2015 2047 2032 2139 1945 2144 2018 2115 2056 2134 1958
    ## [49281] 2004 2133 2016 2144 2202 2111 2037 2017 2156 2138 2050 2048 2152 2140
    ## [49295] 2020 2238 1958 2027 2105 2119 2025 2128 2207 2119 2108 2052 2155 2123
    ## [49309] 2123 2120 2037 2023 2034 2148 2207 2206 2150 2210 2014 2223 2123 2204
    ## [49323] 2151 2216 2027 2121 2224 2232   30 2033 2224 2111 2212 2103 2238 2034
    ## [49337] 2052 2233 2104 2233 2144 2130 2106 2217 2122 2223 2053 2120 2126 2259
    ## [49351] 2237 2200 2220 2045 2051 2127 2208 2209 2247 2245 2254 2146 2104 2059
    ## [49365] 2158 2206 2122 2301 2232 2326 2221 2210 2309 2201 2106 2104 2145 2121
    ## [49379] 2138 2136 2330 2156 2128 2127 2147 2245 2315 2140 2252 2143 2254 2214
    ## [49393] 2129 2130 2317 2312 2341 2337 2334 2248 2328 2148 2248 2151 2204 2145
    ## [49407]    5 2249 2159    6 2150 2207 2302 2229    3 2224   11 2353 2310   54
    ## [49421] 2342 2216 2332 2327 2346 2235 2252   21   10 2230 2358 2255 2353 2221
    ## [49435]   18 2237 2351 2341 2400 2336 2238   14 2301 2308   44 2345 2254 2252
    ## [49449] 2251 2342   25    2 2324  127 2328 2333 2336  117    1 2347   18    6
    ## [49463]  344   NA   NA   NA   NA  401  649  756  924  825  845  929  659  707
    ## [49477]  904  826  734  735  815  717  902  705  833  646  709  904  903  829
    ## [49491]  705  756  733  847  722  755  739  736  800  707  809  915  759  802
    ## [49505]  826  718  831  900  825  738  825  915  725  738  748  733  802  849
    ## [49519]  833  932  927  805  830  917  754  754  901  857  829  837  941  930
    ## [49533]  859  923  845  826 1003  800  803  755  843 1045  753  908  939  913
    ## [49547]  857  849  818  818  937  749  954  949 1012  913  953 1012  813  953
    ## [49561] 1009 1011 1008 1057  830  950 1007 1021  946 1024 1016  909 1009 1005
    ## [49575]  937 1036  953  858 1007 1117 1024 1036  907 1014  946 1029 1018  907
    ## [49589]  951  838  949 1031 1028  954 1134 1056 1043  855 1028  916  907  958
    ## [49603]  857 1040 1053  933  903  913 1055  951 1044  854  925 1017 1005 1005
    ## [49617] 1038  929  911 1049  934 1058 1001 1115  909 1104  912 1102  937 1049
    ## [49631] 1008 1100 1101  929 1111 1053  952 1033 1007 1040 1012 1056 1117  956
    ## [49645] 1031 1121 1010 1215 1050 1006 1013 1101 1000 1057 1208 1105  952  923
    ## [49659] 1008 1016 1117 1130 1020 1001 1042  944 1149 1025 1004 1117  936  943
    ## [49673] 1052  950 1043  934  951 1012  940 1101 1031 1025  950 1104 1027  935
    ## [49687] 1041 1003  956 1150 1050 1130 1011 1137 1152 1005 1006  952 1004 1229
    ## [49701] 1202 1111 1013 1017 1125 1151 1143 1145 1246 1147 1149 1021 1035 1158
    ## [49715] 1159 1124 1122 1012 1159 1145 1056 1224 1239 1207 1111 1210 1154 1029
    ## [49729] 1030 1214 1112 1154 1108 1133 1216 1226 1115 1225 1225 1040 1207 1218
    ## [49743] 1053 1050 1216 1147 1146 1255 1101 1055 1103 1106 1107 1120 1327 1149
    ## [49757] 1202 1114 1207 1129 1422 1102 1204 1242 1225 1205 1119 1304 1236 1232
    ## [49771] 1205 1143 1203 1157 1257 1314 1217 1132 1319 1317 1148 1301 1307 1252
    ## [49785] 1212 1234 1240 1340 1139 1147 1142 1330 1259 1237 1201 1153 1338 1216
    ## [49799] 1330 1235 1339 1355 1226 1204 1228 1400 1207 1242 1351 1157 1232 1324
    ## [49813] 1201 1349 1241 1201 1241 1233 1403 1413 1312 1259 1334 1324 1342 1218
    ## [49827] 1406 1401 1252 1332 1327 1345 1412 1226 1431 1418 1342 1323 1414 1347
    ## [49841] 1259 1255 1358 1253 1401 1446 1435 1326 1334 1311 1249 1451 1347 1444
    ## [49855] 1344 1404 1322 1307 1445 1310 1455 1504 1330 1307 1450 1437 1449 1434
    ## [49869] 1423 1319 1522 1354 1422 1508 1511 1512 1518 1323 1530 1517 1417 1407
    ## [49883] 1349 1411 1530 1500 1413 1521 1438 1348 1353 1444 1531 1342 1446 1552
    ## [49897] 1545 1422 1406 1402 1403 1601 1434 1411 1409 1558 1513 1452 1600 1553
    ## [49911] 1438 1450 1509 1419 1415 1544 1603 1600 1501 1509 1459 1540 1643 1538
    ## [49925] 1419 1528 1544 1606 1513 1525 1604 1632 1533 1624 1738 1516 1454 1630
    ## [49939] 1529 1701 1547 1651 1649 1629 1551 1659 1600 1503 1529 1543 1634 1640
    ## [49953] 1628 1514 1505 1456 1551 1534 1553 1513 1601 1519 1654 1507 1702 1635
    ## [49967] 1458 1510 1608 1554 1638 1618 1724 1607 1656 1708 1602 1725 1710 1644
    ## [49981] 1701 1815 1631 1737 1639 1631 1544 1701 1715 1554 1635 1751 1600 1608
    ## [49995] 1553 1700 1732 1656 1642 1744 1735 1653 1633 1628 1619 1643 1811 1612
    ## [50009] 1715 1808 1631 1605 1826 1646 1742 1637 1728 1618 1621 1606 1753 1816
    ## [50023] 1715 1739 1722 1549 1810 1735 1704 1854 1706 1929 1749 1606 1821 1720
    ## [50037] 1711 1835 1647 1757 1812 1800 1824 1724 1654 1804 1730 1805 1852 1809
    ## [50051] 1852 1654 1900 1719 1809 1731 1823 1846 1758 1908 1908 1805 1838 1743
    ## [50065] 1721 1710 1749 1806 1650 1924 1809 1822 1850 1906 1726 1747 1721 1829
    ## [50079] 1803 1748 1911 1751 1919 1912 1939 1850 1851 1757 1720 1843 1727 1919
    ## [50093] 2008 1757 1845 1754 1818 1908 1750 1841 1823 1856 1757 1722 1803 1855
    ## [50107] 1831 1744 1800 1903 1952 1941 1807 1916 1943 1845 1946 1815 1940 1911
    ## [50121] 1938 1821 1832 1934 1830 1811 1840 1940 1929 1935 1908 1832 1902 1829
    ## [50135] 1758 1952 1859 1834 2021 2023 1901 1941 1854 2010 2013 1926 1843 1909
    ## [50149] 2028 2029 1940 1906 2029 1920 2051 1939 2030 1901 1848 1925 1905 2041
    ## [50163] 1937 2043 2045 2100 1924 2006 1922 2015 2011 1918 2011 1907 2012 2025
    ## [50177] 1848 2008 1900 1952 1941 1959 1941 2030 2036 2025 2034 2011 1918 1910
    ## [50191] 2100 1919 2050 2028 1956 2028 2035 2013 2056 1946 1923 2102 2042 1938
    ## [50205] 2107 2037 2003 2008 2040 2127 1913 2053 2109 1947 2100 2015 1946 2105
    ## [50219] 2144 1934 2032 2033 2055 2033 2131 2009 2013 2048 2105 2005 2203 2129
    ## [50233] 2055 2111 2206 2116 2134 2107 2133 2149 2033 1941 2022 2141 2120 2057
    ## [50247] 2021 1937 2033 2123 2024 2154 2028 2127 2035 2046 2125 2032 2118 2105
    ## [50261] 2129 2107 2006 2104 2208 2029 2159 2100 2154 2047 2105 2043 2156 2148
    ## [50275] 2125 2119 2112 2158 2123 2049 2127 2215 2055 2137 2204 2226 2109 2039
    ## [50289] 2134 2222 2048 2201 2107 2236 2153 2115 2222 2218 2205 2052 2117 2123
    ## [50303] 2211 2024 2130 2213 2254 2100 2048 2215 2154 2243 2206 2132 2249 2121
    ## [50317] 2115 2231 2233 2144 2225 2057 2219 2112 2224 2132 2230 2205 2128 2250
    ## [50331] 2052 2148 2203 2129 2209 2241 2219 2101 2201 2236 2248 2209 2237 2116
    ## [50345] 2158 2229 2048 2246 2302 2122 2257 2203 2323 2135 2218 2217 2135 2238
    ## [50359] 2243 2220 2113 2140 2214 2252 2115 2330 2231 2143 2128 2152 2318 2330
    ## [50373]   19 2137 2237 2324 2219 2221 2230 2257 2222 2343   16 2210    3 2301
    ## [50387] 2225 2306 2151 2348 2335 2341 2248 2352   56    6 2251   31   34 2216
    ## [50401] 2257 2351 2324 2223 2220   18 2313 2304 2330 2341 2231    4 2325 2251
    ## [50415] 2330 2337 2341 2251 2230 2306 2345   41 2337 2314   49   38   17 2257
    ## [50429] 2300  154 2339 2301 2319   56 2330 2303    6 2332  111   10 2350 2347
    ## [50443] 2341 2330   12 2400 2356   18   14  108   15  102   NA   NA   NA   NA
    ## [50457]  636  747  941  826  820  935  712  846  819  846  906  714  723  841
    ## [50471]  857  857  754  838  811  815  728  921  925  910  824  906  822  921
    ## [50485]  826  912  814  839  800  746  906  927  948  928  751  931  903  811
    ## [50499] 1055  743  949  945  941 1013 1042  944  957  834  941  900  854  843
    ## [50513]  954  845  847 1011  944 1020  935  917  952 1017 1035  848  932  909
    ## [50527]  937  959  922 1017  810 1021  852 1013 1021 1020  926 1008 1024 1042
    ## [50541] 1036  949  910 1037  957 1137  922  850  944  932  903  921 1155 1026
    ## [50555]  926  958 1031 1051 1004 1038 1024  954  932 1043  926 1008 1058 1044
    ## [50569]  859 1048 1057 1018 1028  949  920 1150 1057 1044 1053 1044 1105  934
    ## [50583] 1115 1002 1038 1016 1005 1113  958 1104 1201 1018 1002 1013 1122 1114
    ## [50597] 1038 1043 1117  949 1029  937 1131 1028 1046 1107  943  942 1219 1024
    ## [50611]  935  933 1034 1142 1116 1011 1144 1209 1100 1011 1013 1143 1230 1142
    ## [50625]  958 1020 1055 1152 1113 1155 1139 1008 1201 1008 1152 1204 1200 1108
    ## [50639] 1025 1200 1216 1205 1221 1209 1219 1026 1119 1151 1239 1101 1322 1218
    ## [50653] 1114 1134 1303 1154 1302 1108 1213 1214 1101 1202 1133 1110 1225 1131
    ## [50667] 1330 1203 1254 1349 1211 1301 1203 1205 1221 1130 1112 1435 1115 1211
    ## [50681] 1206 1130 1222 1205 1242 1356 1224 1252 1247 1326 1314 1414 1151 1213
    ## [50695] 1243 1314 1330 1322 1214 1347 1136 1342 1336 1147 1311 1414 1301 1342
    ## [50709] 1255 1351 1420 1346 1329 1245 1346 1247 1321 1345 1339 1437 1426 1446
    ## [50723] 1311 1308 1215 1303 1219 1400 1357 1343 1330 1341 1340 1347 1332 1421
    ## [50737] 1422 1411 1417 1430 1409 1519 1355 1400 1442 1342 1439 1414 1518 1446
    ## [50751] 1504 1537 1409 1310 1331 1301 1453 1438 1527 1420 1312 1325 1432 1316
    ## [50765] 1338 1349 1508 1409 1330 1414 1509 1327 1534 1335 1515 1550 1340 1536
    ## [50779] 1454 1600 1553 1508 1541 1447 1438 1503 1417 1530 1550 1403 1547 1427
    ## [50793] 1444 1531 1526 1530 1548 1445 1455 1559 1530 1534 1633 1538 1551 1507
    ## [50807] 1645 1429 1610 1543 1638 1634 1543 1515 1618 1629 1538 1756 1442 1554
    ## [50821] 1539 1646 1627 1638 1656 1536 1546 1444 1652 1546 1548 1702 1656 1458
    ## [50835] 1634 1620 1503 1644 1534 1545 1549 1531 1536 1617 1710 1611 1731 1631
    ## [50849] 1728 1651 1600 1841 1609 1715 1701 1640 1607 1651 1750 1628 1610 1645
    ## [50863] 1600 1607 1636 1633 1807 1731 1738 1721 1803 1702 1610 1707 1814 1637
    ## [50877] 1759 1749 1726 1800 1756 1739 1825 1720 1652 1758 1648 1754 1727 1833
    ## [50891] 1850 1840 1644 1809 1814 1734 1818 1859 1735 1940 1911 1732 1855 1828
    ## [50905] 1711 1654 1726 1947 1820 1710 1728 1702 1725 1704 1826 1901 1841 1839
    ## [50919] 1838 1803 1845 1844 1856 1843 1907 1824 1718 1834 1730 1726 1717 1848
    ## [50933] 1751 1818 1830 1755 1925 1800 1716 1732 1854 1810 1936 1859 1737 1921
    ## [50947] 1920 2245 1739 1939 1801 1916 1737 1847 1843 1940 1923 1955 1934 1913
    ## [50961] 1758 2344 1949 1947 1904 1935 1813 1812 1801 1947 1829 1912 2002 1859
    ## [50975] 1945 1901 1822 1947 1949 1951 1836 1906 1814 1907 1838 2015 1944 1931
    ## [50989] 2008 1858 1839 2010 2013 2000 1952 1825 2015 1816 1905 1837 1937 2020
    ## [51003] 1929 1907 1931 1929 1832 1841 2007 2013 1943 1851 2015 1941 1921 1900
    ## [51017] 1911 2020 2041 2040 2039 2027 1929 1855 1911 2043 1934 2016 2008 2353
    ## [51031] 1955 2033 1930 1951 1933 2110 2108 2111 1935 2043 1931 1920 1943 2021
    ## [51045] 2048 1930 1946 2131 2122 2129 2125 2136 2002 2121 2004 2140 2021 2105
    ## [51059] 2019 2158 2137 2142 2142 2313 2121 2011 2135 2125 2026 2133 2113 2147
    ## [51073] 2027 2213 2214 2217 2227 2211 2215 2227 2032 2153 2140 2132 2153 2233
    ## [51087] 2150 2231 2217 2119 2243 2247 2101 2141 2304 2139 2303 2127 2313 2226
    ## [51101] 2224 2326 2137 2316 2213 2330 2149 2322 2314 2305 2333 2146   39 2335
    ## [51115] 2243 2221 2342    9    3   30   22 2331 2348 2244 2254   29 2358   47
    ## [51129] 2254 2243  133 2319 2336    4 2352 2353  345  349   NA   NA   NA  410
    ## [51143]  757  834  841  711  705  837  856  722  649  749  955  810  708  852
    ## [51157]  743  846  726  754  920  816  903  903  922  806  806  748  829  746
    ## [51171]  926  836  909  917  820  841  849  811 1024  747  802  942  950  941
    ## [51185]  923  949  906  817  938  811  931 1005  912 1052  950 1012  821  932
    ## [51199] 1009 1012  848  949  931  948  813  942  826  901 1006 1033  915  925
    ## [51213]  825 1030 1006  903 1006 1129 1027 1021 1022 1013 1030 1015  944  934
    ## [51227] 1027 1022  917 1048  856 1125  901  902  923 1010  911  956  944 1046
    ## [51241] 1019  931 1102  928 1057  927 1030  900  950 1052  923 1051 1045 1013
    ## [51255] 1040  951 1138 1037 1002  934  958 1119 1047 1104 1100 1056 1033 1057
    ## [51269] 1051  931 1105 1033 1201  935  934 1051 1021 1021  940 1123  944 1027
    ## [51283] 1130 1002 1046 1006  940 1007 1129 1028 1031 1133 1043 1010 1000 1122
    ## [51297] 1001  942 1031 1050 1037 1130  944 1018 1144 1053 1150 1125 1047 1149
    ## [51311]  956 1227  949 1142  959 1148 1029 1116 1157 1133 1101 1134 1008 1200
    ## [51325] 1029 1020 1200 1218 1051 1035 1008 1003 1156 1140 1148 1207 1204 1155
    ## [51339] 1103 1115 1154 1208 1211 1125 1203 1042 1203 1141 1026 1106 1134 1049
    ## [51353] 1215 1107 1330 1129 1034 1209 1037 1103 1148 1124 1132 1234 1249 1044
    ## [51367] 1217   NA 1235 1145 1150 1118 1438 1212 1109 1111 1146 1221 1210 1301
    ## [51381] 1224 1230 1121 1309 1210 1141 1156 1135 1156 1322 1316 1235 1314 1153
    ## [51395] 1258 1216 1136 1233 1310 1227 1324 1249 1152 1349 1332 1336 1343 1339
    ## [51409] 1315 1227 1227 1338 1305 1353 1335 1217 1254 1247 1210 1243 1159 1332
    ## [51423] 1218 1223 1353 1352 1228 1237 1219 1421 1239 1252 1336 1259 1249 1319
    ## [51437] 1246 1344 1407 1414 1344 1240 1427 1428 1457 1246 1326 1245 1254 1445
    ## [51451] 1401 1513 1259 1252 1430 1255 1456 1328 1413 1314 1446 1301 1356 1458
    ## [51465] 1450 1349 1441 1417 1455 1337 1359 1430 1332 1432 1410 1447 1350 1410
    ## [51479] 1509 1350 1323 1427 1459 1422 1407 1449 1342 1523 1506 1418 1409 1335
    ## [51493] 1519 1341 1515 1341 1539 1354 1429 1446 1542 1403 1410 1536 1402 1426
    ## [51507] 1525 1358 1554 1557 1418 1411 1411 1557 1444 1540 1530 1427 1544 1606
    ## [51521] 1704 1511 1359 1520 1516 1606 1448 1510 1422 1559 1451 1524 1623 1608
    ## [51535] 1611 1531 1511 1605 1519 1444 1631 1532 1502 1447 1644 1505 1519 1541
    ## [51549] 1639 1611 1556 1514 1545 1516 1534 1702 1556 1556 1451 1629 1535 1628
    ## [51563] 1651 1509 1706 1456 1616 1504 1520 1531 1627 1618 1656 1629 1728 1651
    ## [51577] 1531 1649 1620 1704 1714 1658 1731 1607 1744 1627 1723 1649 1717 1637
    ## [51591] 1622 1741 1603 1645 1737 1721 1753 1549 1655 1600 1636 1627 1646 1653
    ## [51605] 1706 1622 1732 1551 1740 1541 1613 1701 1744 1701 1642 1804 1754 1613
    ## [51619] 1644 1559 1750 1745 1640 1717 1706 1600 1630 1602 1731 1704 1704 1748
    ## [51633] 1659 1812 1638 1849 1722 1736 1628 1752 1640 1655 1644 1824 1800 1757
    ## [51647] 1913 1743 1820 1840 1805 1647 1851 1702 1659 1757 1813 1643 1641 1846
    ## [51661] 1708 1648 1732 1706 1747 1936 1759 1740 1819 1902 1759 1841 1842 1756
    ## [51675] 1806 1900 1641 1755 1723 1821 1814 1824 1819 1751 1655 1849 1752 1717
    ## [51689] 1713 1824 1744 1935 1718 1730 1755 1811 1851 1914 2006 1736 1823 1816
    ## [51703] 1810 1735 1810 1904 1731 1749 1905 1902 1731 1921 1923 1855 2004 1757
    ## [51717] 1946 1805 1748 1825 1925 1957 1818 1917 1727 1818 1908 1930 1841 1758
    ## [51731] 1934 1856 1829 1837 1832 1936 1806 1756 1859 1815 1943 1746 1934 1819
    ## [51745] 1832 1946 1815 1803 1913 1853 1804 1951 1903 1932 1932 1939 1952 1906
    ## [51759] 1922 1907 2010 1829 1826 1836 1858 2019 1908 2017 2008 1833 1946 1850
    ## [51773] 1935 1854 1846 2000 1931 1821 2048 1841 1837 1945 1906 1915 2040 2007
    ## [51787] 2017 2009 2026 1927 2032 1849 1920 1913 2026 2047 1858 2051 1931 1951
    ## [51801] 1944 1919 1940 2041 2031 1851 2036 2131 1850 1955 1922 2004 2016 1919
    ## [51815] 1851 1851 1921 1930 2006 1927 1925 2058 1923 2025 1935 2004 2055 1959
    ## [51829] 2109 1953 2020 2030 1939 2011 2053 2111 2136 2107 2055 2026 2022 1921
    ## [51843] 1950 2135 2018 2007 1938 2010 2115 2024 2121 2057 1950 2009 1945 2124
    ## [51857] 2138 2011 2041 2121 1958 2122 2039 2107 1952 2011 2142 2006 2155 2011
    ## [51871] 2144 2209 2021 2015 2248 2009 2109 2043 2040 2127 2112 2058 2140 2222
    ## [51885] 2038 2125 2028 2008 2115 2137 2050 2122 2118 2047 2026 2015 2143 2013
    ## [51899] 2148 2139 2220 2251 2134 2220 2157 2132 2151 2200 2217 2215 2142 2130
    ## [51913] 2042 2243 2212 2127 2234 2218 2220 2259 2050 2045 2240 2229 2230 2036
    ## [51927] 2114 2132 2227 2155 2112 2155 2134 2120 2051 2138 2255 2103 2123 2143
    ## [51941] 2119 2116 2302 2230 2213 2239 2326 2259 2245 2247 2150 2127 2302 2259
    ## [51955] 2112 2135 2149 2254 2145 2149 2249 2114 2122 2309 2326 2325 2217    3
    ## [51969] 2139 2340 2236 2315 2144 2347 2232 2220 2206 2158 2247 2345   19 2331
    ## [51983] 2157 2322 2159 2248 2233 2203 2243 2230 2245 2259 2206 2204   40 2359
    ## [51997] 2210 2221   27 2222 2324 2228 2244 2236 2223   14 2343 2215 2337 2345
    ## [52011] 2334  115   31 2345 2333 2308 2309 2242   18   15 2340 2250 2308 2241
    ## [52025]   14   51 2258 2349   30 2327 2241 2353    3 2308 2320 2325 2342 2337
    ## [52039] 2338 2346    2 2348   15   37  102    5  328  339   NA   NA   NA  627
    ## [52053]  745  838  645  842  842  817  829  844  641  809  948  648  729  825
    ## [52067]  717  739  730  914  743  712  910  754  721  716  812  817  854  743
    ## [52081]  852  743  806  803  804  801  714  853  820  742  739  801  833  840
    ## [52095]  930  908  822  732  838  827  854  847  923  725  841  816  919  854
    ## [52109]  914  910 1009  834  747  842  852  827  824  835  757 1028  848  801
    ## [52123]  855  746  832  846  958  827  824  925 1005  808 1100  938  806 1011
    ## [52137] 1035 1016 1047 1006 1044  953  913  948  856  854  824  835  952  922
    ## [52151]  906 1023 1023  926  948 1018  947  905  954  922 1005  947 1123 1039
    ## [52165]  948 1003 1026  842 1001 1107  857 1123 1027  938 1018  926  921 1024
    ## [52179]  945  937 1116  938 1131  855  921 1115  927  849  950  914  851  859
    ## [52193]  929 1003 1018  934  941 1055 1009 1000 1039 1031 1045  959 1048  932
    ## [52207]  932 1055  934 1102  908 1041 1043 1037 1040 1016 1037  941  956 1055
    ## [52221] 1012 1123 1109  919 1053 1042 1111  951 1040 1101 1203 1100 1012  922
    ## [52235] 1056 1106 1107 1026 1140 1014 1004 1123 1041  940 1014  956 1009 1021
    ## [52249] 1155 1020 1114 1042  930  955 1011 1000  936 1132 1131 1001  936 1145
    ## [52263] 1040 1013  955 1107 1029 1046 1144 1104 1232  948 1007 1209 1108 1009
    ## [52277] 1043 1007 1059 1137 1145 1205 1145 1005 1148 1023 1159 1221 1213 1107
    ## [52291] 1042 1145 1156 1014 1218 1056 1008 1027 1206 1135 1126 1110 1129 1206
    ## [52305] 1019 1238 1115 1204 1251 1252 1218 1206 1317 1213 1219 1139 1120 1128
    ## [52319] 1302 1230 1222 1218 1134 1201 1230 1127 1122 1047 1230 1114 1252 1152
    ## [52333] 1204 1104 1212 1138 1109 1119 1141 1217 1246 1122 1159 1233 1153 1309
    ## [52347] 1426 1337 1226 1213 1211 1132 1310 1128 1124 1207 1145 1308 1324 1341
    ## [52361] 1311 1138 1219 1121 1346 1230 1308 1303 1240 1356 1317 1249 1200 1148
    ## [52375] 1140 1308 1224 1338 1410 1335 1232 1322 1412 1208 1245 1204 1337 1233
    ## [52389] 1200 1224 1219 1342 1240 1319 1249 1335 1351 1156 1215 1403 1238 1235
    ## [52403] 1217 1243 1210 1429 1245 1347 1345 1254 1406 1422 1410 1323 1415 1314
    ## [52417] 1343 1328 1444 1344 1410 1428 1429 1513 1343 1331 1307 1307 1449 1426
    ## [52431] 1343 1251 1516 1306 1447 1509 1413 1354 1456 1300 1246 1507 1422 1430
    ## [52445] 1305 1347 1321 1447 1422 1322 1426 1543 1411 1509 1541 1327 1320 1401
    ## [52459] 1406 1523 1405 1334 1412 1502 1403 1507 1516 1521 1505 1507 1337 1610
    ## [52473] 1522 1459 1452 1421 1417 1415 1611 1450 1558 1357 1624 1408 1355 1458
    ## [52487] 1446 1416 1548 1551 1427 1527 1425 1546 1453 1624 1631 1434 1411 1459
    ## [52501] 1423 1729 1500 1603 1527 1423 1611 1451 1423 1601 1606 1518 1502 1610
    ## [52515] 1540 1503 1632 1517 1620 1640 1603 1626 1535 1530 1713 1512 1555 1630
    ## [52529] 1457 1510 1509 1514 1444 1635 1445 1709 1539 1446 1626 1631 1602 1500
    ## [52543] 1644 1538 1634 1548 1602 1619 1532 1707 1654 1631 1704 1636 1546 1800
    ## [52557] 1545 1611 1531 1720 1646 1749 1551 1730 1747 1553 1721 1635 1724 1717
    ## [52571] 1628 1556 1604 1645 1615 1651 1601 1628 1547 1734 1633 1729 1616 1635
    ## [52585] 1627 1634 1807 1639 1547 1542 1705 1609 1656 1839 1622 1753 1549 1710
    ## [52599] 1634 1733 1743 1554 1719 1801 1608 1742 1819 1638 1836 1808 1650 1744
    ## [52613] 1746 1750 1752 1714 1652 1808 1730 1740 1717 1736 1655 1754 1640 1718
    ## [52627] 1837 1710 1715 1809 1814 1709 1809 1847 1736 1828 1711 1709 1730 1642
    ## [52641] 1835 1834 1909 1805 2006 1659 1703 1808 1732 1710 1919 1917 1746 1718
    ## [52655] 1833 1912 1923 1732 1810 1805 1805 1711 1723 1708 1837 1830 1815 1910
    ## [52669] 1727 1701 1934 1858 1840 1801 1835 1714 1825 1718 1835 1852 1719 1800
    ## [52683] 2007 1804 1756 1826 1814 1813 1716 1737 1852 1908 1812 1909 1819 1911
    ## [52697] 1749 1928 1736 1837 1834 1908 1909 1902 2034 1827 1929 1757 1904 1914
    ## [52711] 1749 1929 1824 2016 1805 1736 1820 2023 1912 1757 1848 1854 1846 2018
    ## [52725] 1808 2035 1812 1841 1942 1752 1946 1814 1801 2014 2011 1835 1839 1911
    ## [52739] 1855 1956 1804 1829 2024 1803 1908 1944 1810 2024 2012 1836 1926 1943
    ## [52753] 1821 1808 1843 1925 2048 1855 1856 1817 1955 1825 1919 2008 1851 1915
    ## [52767] 1945 1902 2011 1833 1903 1916 1919 2044 1957 2046 1914 2055 2057 1842
    ## [52781] 2023 1953 2036 2015 2029 2101 2044 2040 2018 1950 1920 1934 1950 1940
    ## [52795] 2036 1958 1936 1913 1918 1846 2038 1948 2109 2030 1929 2127 2005 2034
    ## [52809] 1904 1937 2038 2029 2029 2004 2059 2001 2121 2126 2016 1930 1944 2136
    ## [52823] 1943 2108 2007 2155 2058 2213 1930 1933 2026 1944 2152 2100 2050 2024
    ## [52837] 2138 2106 2109 2154 2034 2155 2032 2109 2010 1959 2002 2156 2040 1940
    ## [52851] 2109 1956 2008 2002 2302 2151 2028 1933 2029 1944 2129 2033 2152 2030
    ## [52865] 2150 2046 2231 2044 2120 2220 2047 2125 2111 2130 2100 2135 2141 2110
    ## [52879] 2213 2218 2153 2037 2115 2056 2154 2008 2058 2013 2141 2207 2154 2021
    ## [52893] 2247 2110 2203 2226 2206 2027 2220 2243 2335 2203 2127 2055 2129 2106
    ## [52907] 2122 2210 2053 2043 2059 2221 2055 2212 2141 2049 2209 2212 2108 2058
    ## [52921] 2152 2213 2026 2119 2124 2111 2319 2115 2249 2229 2129 2225 2245 2133
    ## [52935] 2239 2150 2250 2123 2142 2236 2326 2142 2209 2106 2318 2331 2128 2131
    ## [52949] 2117 2123 2201 2309 2246 2355 2238 2224 2142 2306 2227 2132 2330 2353
    ## [52963] 2216 2311   18 2320 2203 2250 2243 2248 2154 2150 2330   26 2355 2156
    ## [52977] 2242 2327 2147 2252 2205 2259 2216 2254 2324 2317 2229   39 2315 2335
    ## [52991] 2150  104 2259 2236 2256 2322 2307 2330 2339 2346 2357 2245 2238 2229
    ## [53005] 2231 2238 2334 2249 2351    1  103 2247   12 2253 2258 2315 2306 2313
    ## [53019] 2330  142 2347   27 2345 2346 2356   13 2344  359  403  349   NA   NA
    ## [53033]   NA   NA  634  728  814  816  823  651  815  827  919  650  813  843
    ## [53047]  701  739  835  755  710  837  755  644  738  720  718  951  854  735
    ## [53061]  805  833  731  759  806  744  723  852  814  806  821  728  815  731
    ## [53075]  716  912  916  820  859  851  831  912  749  948  805  818  758  831
    ## [53089]  849  918  724  848  859  907  830  809  752  930  850  929  807  918
    ## [53103] 1007 1038  944  903  823  804  853  749 1052  851  957  742  758  914
    ## [53117]  815 1027 1020  919 1005  831  924 1044  904 1104  935 1030 1002 1028
    ## [53131]  824  952 1001  845  947  908  851  958 1046  924  944  941 1020  813
    ## [53145]  940 1046 1008  918 1001 1000  859 1021 1004 1116 1039  857  917  948
    ## [53159]  910 1018 1014 1026  935 1052 1022 1019  904  940  851  917  925  907
    ## [53173] 1033  955 1107  843  904 1028  949  904 1038 1053 1039 1015 1020  947
    ## [53187]  926 1145  933 1038 1015 1114 1032  932 1048 1013 1023 1050 1040  934
    ## [53201] 1057 1031 1047 1117 1050 1047 1147 1029  952 1109 1106  927 1202  918
    ## [53215] 1050  923 1009 1013 1017  956 1013 1142 1035  944 1031 1111 1009 1040
    ## [53229] 1028  958 1125 1127 1038  939 1155 1015 1029 1000 1013  937 1129 1141
    ## [53243] 1109  958 1100 1041 1040 1110 1135 1146  941 1139 1006 1223 1036 1238
    ## [53257] 1054   NA 1003 1221 1232 1008 1023 1127 1216 1147 1138 1007 1037 1122
    ## [53271] 1233 1203 1125 1116 1207 1046 1054 1232 1300 1222 1128 1020 1021 1013
    ## [53285] 1158 1242 1108 1114 1022 1251 1251 1256 1114 1139 1201 1154 1209 1206
    ## [53299] 1125 1215 1236 1122 1154 1035 1059 1056 1058 1127 1152 1142 1248 1132
    ## [53313] 1351 1239 1139 1058 1046 1046 1222 1225 1058 1110 1209 1118 1055 1332
    ## [53327] 1159 1119 1307 1142 1153 1149 1103 1224 1129 1143 1134 1233 1201 1157
    ## [53341] 1345 1227 1252 1258 1215 1153 1111 1244 1349 1251 1247 1216 1131 1334
    ## [53355] 1308 1203 1405 1242 1308 1322 1326 1400 1319 1352 1153 1334 1235 1210
    ## [53369] 1146 1334 1430 1232 1242 1238 1216 1215 1320 1201 1302 1354 1210 1328
    ## [53383] 1158 1350 1234 1242 1402 1406 1319 1434 1250 1335 1323 1302 1246 1326
    ## [53397] 1428 1446 1324 1356 1410 1419 1405 1404 1345 1423 1253 1541 1308 1438
    ## [53411] 1437 1256 1313 1430 1505 1453 1335 1250 1511 1428 1357 1308 1420 1246
    ## [53425] 1334 1513 1500 1335 1456 1504 1444 1437 1429 1341 1550 1407 1316 1429
    ## [53439] 1331 1450 1420 1459 1408 1501 1424 1504 1339 1336 1528 1449 1607 1409
    ## [53453] 1353 1528 1450 1420 1436 1503 1536 1536 1611 1405 1433 1618 1527 1557
    ## [53467] 1537 1415 1512 1618 1645 1413 1530 1514 1717 1409 1435 1458 1447 1512
    ## [53481] 1538 1459 1625 1538 1621 1627 1449   NA 1428 1425 1443 1602 1655 1536
    ## [53495] 1551 1535 1449 1514 1602 1622 1524 1625 1542 1628 1604 1715 1521 1621
    ## [53509] 1524 1619 1527 1642 1544 1527 1616 1621 1534 1457 1507 1723 1617 1639
    ## [53523] 1603 1621 1504 1656 1717 1627 1512 1636 1711 1749 1538 1605 1654 1652
    ## [53537] 1558 1635 1702 1530 1601 1750 1649 1701 1620 1719 1710 1722 1542 1619
    ## [53551] 1649 1551 1735 1607 1552 1754 1719 1830 1654 1651 1726 1721 1704 1722
    ## [53565] 1545 1737 1631 1733 1656 1651 1654 1737 1642 1557 1809 1619 1652 1736
    ## [53579] 1606 1744 1755 1715 1725 1649 1615 1843 1742 1608 1648 1742 1624 1742
    ## [53593] 1649 1750 1726 1725 1731 1733 1633 1755 1819 1714 1820 1741 1820 1727
    ## [53607] 1714 1801 1733 1821 1734 1839 1648 1645 1855 1708 1808 1706 1848 1716
    ## [53621] 1859 1702 1827 1915 1709 1718 1715 1757 1838 1828 1933 1724 1823 1656
    ## [53635] 1926 1808 1729 1922 1722 1821 1804 1810 1737 1744 1704 1712 1837 1746
    ## [53649] 1737 1944 1747 1848 1942 1908 1850 1846 1755 1841 1759 1814 1817 1842
    ## [53663] 1828 1857 1809 1718 1919 1904 1854 1924 1725 1854 1751 1855 1800 1834
    ## [53677] 2012 1746 1858 1833 1848 1914 1904 1916 1931 1859 1759 1805 1945 1743
    ## [53691] 1912 2013 1834 1914 1926 1816 1950 1855 1931 1912 1759 1848 1746 1832
    ## [53705] 2002 1947 1853 1823 1935 2020 1837 1932 1757 1816 1935 1954 1918 2009
    ## [53719] 1959 2023 1934 1911 1841 1843 2029 1757 1952 1854 1807 1913 1904 1914
    ## [53733] 1847 1952 2019 2000 1933 2022 1811 2023 2016 2015 1916 1827 2016 2036
    ## [53747] 1958 1954 2051 1925 2029 1953 2036 1955 1846 1920 1923 2050 1958 1950
    ## [53761] 2036 2019 2050 1929 2019 1917 1948 2001 1848 1856 2032 1853 2051 2113
    ## [53775] 1929 2028 2026 2027 1853 1916 1956 1923 1902 1952 2038 2112 2053 1933
    ## [53789] 2031 1916 2209 1943 2042 2103 2004 1950 2022 2139 2002 2053 1936 2055
    ## [53803] 1932 2143 2014 2127 1947 1922 2051 2105 2044 2022 2036 2047 2209 2009
    ## [53817] 2025 2103 2026 2102 1952 2212 2114 1952 2051 2005 2010 2159 2217 2024
    ## [53831] 2014 2212 2027 2048 2001 2131 2124 2128 2153 2113 2044 2012 2201 2115
    ## [53845] 2135 2117 2038 2135 2150 2024 2223 2042 2136 2042 2131 2154 2210 2026
    ## [53859] 2134 2107 2205 2132 2103 2205 2042 2203 2242 2241 2141 2152 2117 2045
    ## [53873] 2210 2219 2206 2139 2244 2145 2046 2214 2123 2227 2212 2309 2140 2210
    ## [53887] 2222 2104 2111 2104 2124 2237 2039 2117 2249 2117 2312 2138 2221 2214
    ## [53901] 2104 2150 2242 2239 2116 2232 2116 2251 2112 2319 2340 2133 2225 2257
    ## [53915] 2242 2221 2105 2150 2102 2236 2309 2120 2158 2250 2239 2155 2125 2248
    ## [53929] 2325 2311 2258 2222 2149 2203 2131 2152 2144 2311 2211 2238 2148 2352
    ## [53943]   19 2244 2210 2154 2145 2206 2325 2216 2329 2155 2312   29 2339 2306
    ## [53957] 2255 2241   29 2332 2314 2354 2257 2204 2211 2216 2259 2338 2239 2400
    ## [53971] 2241 2349 2307 2241   50   56 2309 2248 2305 2248 2356 2334  122 2355
    ## [53985]    1 2359   14   28   15   31  334  326  325   NA   NA   NA   NA   NA
    ## [53999]   NA  629  844  831  756  708  713  701  705  834  731  723  837  641
    ## [54013]  750  753  705  843  925  821  727  726  837  823  726  918  856  913
    ## [54027]  840  810  715  805  801  741  853  801  712  804  804  832  805  713
    ## [54041]  923  919  901  759  931  841  829  904  849  816  746  821  820  816
    ## [54055]  837  958  736  907  914  759  757  854  830  843  749 1009  821  750
    ## [54069]  811  851  848 1009  821  906  850 1006 1012  949 1019 1006  754  951
    ## [54083]  853  934  947  931 1021  942  936  939  949  817  846 1003  817  826
    ## [54097] 1009  844 1002  959 1024  947 1017  826  942  936  935 1035  918 1014
    ## [54111] 1029 1048  958  927 1021 1102 1014  905 1031  927  859  855 1032  950
    ## [54125] 1022 1046 1100 1016 1116  852 1049  941  915 1045  944  853 1043  928
    ## [54139]  902  846 1037  904 1005  927  924  921  917 1048 1049 1013 1048 1044
    ## [54153] 1056 1014 1024 1026  929 1022  928 1044 1010  943 1029 1048 1050 1031
    ## [54167] 1108 1038  940 1048 1049 1050  921  958 1012  942 1102  935 1057 1017
    ## [54181] 1004  931 1024  952  949  929 1146 1012 1113 1041 1046 1105 1118  955
    ## [54195]  941 1146 1135 1046 1135 1024 1109 1024 1051  959 1036 1158  956  940
    ## [54209] 1119 1045 1039 1049  943  946  952 1122 1001 1200  957  958 1028 1127
    ## [54223]  952 1013 1006 1221  954 1304 1146 1212 1201 1149 1231 1107 1132 1110
    ## [54237] 1021 1141 1026 1032 1107 1201 1211 1204 1143 1013 1131 1210 1045 1221
    ## [54251] 1016 1054 1118 1229 1144 1202 1231 1212 1239 1241 1124 1148 1034 1205
    ## [54265] 1127 1205 1139 1033 1203 1156 1100 1310 1223 1239 1106 1136 1104 1230
    ## [54279] 1132 1228 1232 1221 1429 1135 1128 1113 1058 1130 1236 1049 1109 1122
    ## [54293] 1229 1226 1148 1201 1136 1339 1259 1232 1137 1315 1254 1239 1214 1131
    ## [54307] 1122 1132 1141 1257 1325 1344 1250 1341 1259 1419 1306 1306 1217 1353
    ## [54321] 1324 1228 1244 1150 1150 1256 1339 1321 1321 1238 1219 1206 1238 1206
    ## [54335] 1416 1232 1241 1405 1159 1237 1245 1211 1202 1422 1333 1319 1231 1205
    ## [54349] 1326 1228 1350 1349 1402 1241 1322 1422 1249 1426 1328 1302 1336 1314
    ## [54363] 1338 1402 1307 1348 1428 1424 1409 1424 1300 1323 1343 1429 1500 1258
    ## [54377] 1427 1512 1258 1443 1519 1355 1503 1255 1442 1254 1416 1309 1450 1450
    ## [54391] 1439 1507 1436 1323 1502 1427 1327 1326 1452 1343 1425 1552 1352 1336
    ## [54405] 1411 1350 1507 1343 1412 1453 1406 1402 1450 1422 1424 1341 1431 1420
    ## [54419] 1509 1606 1538 1343 1410 1509 1350 1356 1603 1614 1439 1449 1416 1538
    ## [54433] 1518 1352 1430 1409 1454 1422 1425 1611 1539 1613 1406 1506 1450 1530
    ## [54447] 1419 1557 1448 1451 1432 1625 1502 1457 1732 1456 1422 1631 1514 1547
    ## [54461] 1444 1600 1437 1556 1602 1541 1608 1621 1609 1457 1536 1615 1626 1645
    ## [54475] 1507 1522 1627 1457 1533 1521 1516 1647 1654 1628 1613 1531 1631 1502
    ## [54489] 1644 1542 1538 1710 1725 1612 1503 1615 1538 1605 1522 1538 1601 1708
    ## [54503] 1715 1542 1620 1723 1746 1636 1529 1729 1634 1614 1622 1544 1704 1559
    ## [54517] 1729 1731 1644 1545 1537 1607 1659 1628 1617 1715 1636 1725 1709 1559
    ## [54531] 1728 1808 1629 1633 1744 1734 1744 1736 1750 1642 1605 1635 1733 1729
    ## [54545] 1625 1701 1744 1739 1634 1617 1605 1718 1655 1651 1747 1733 1846 1818
    ## [54559] 1735 1625 1804 1621 1653 1740 1742 1815 1628 1808 1736 1731 1737 1657
    ## [54573] 1808 1705 1721 1834 1755 1845 1810 1618 1911 1821 1814 1809 1735 1727
    ## [54587] 1656 1655 1831 1847 1908 1739 1816 1700 1650 1659 1859 1709 1702 1706
    ## [54601] 1925 1932 1806 1820 1658 1737 1720 1937 1804 1724 1741 1707 1846 1709
    ## [54615] 1900 1735 1811 1758 1851 1726 1712 1745 1831 1830 1734 1908 1926 1846
    ## [54629] 1831 1848 1828 1831 1838 1820 1831 1842 1729 1941 1841 1744 1741 1841
    ## [54643] 1810 1909 1907 1817 1731 1907 1735 1912 1950 1919 1935 1933 1741 1807
    ## [54657] 1917 1902 1757 1932 2006 1829 1748 1753 1820 1833 2019 1830 1942 2009
    ## [54671] 1848 1829 1854 1902 1847 2023 1757 1757 1808 1842 1956 1938 1807 1820
    ## [54685] 1934 1942 2017 2006 1900 2019 1955 1921 1849 1824 1821 2039 1901 1837
    ## [54699] 1842 2008 1818 1854 1957 2003 1906 2013 1918 2006 2018 2009 1946 2013
    ## [54713] 1855 2010 2059 1835 1930 1958 2052 2001 2034 2042 2028 2034 1934 1905
    ## [54727] 1915 2027 1904 1851 1957 2028 2015 2041 2006 2056 2008 2101 2031 2006
    ## [54741] 1835 2021 2007 2001 2117 1919 2032 2036 1922 1920 2018 1933 2042 1915
    ## [54755] 2015 1941 2102 1923 2109 2103 2003 2017 1939 1951 2158 1940 1955 2059
    ## [54769] 1944 2030 2024 2149 2114 2006 2107 2105 2102 2157 2012 2029 1920 2032
    ## [54783] 2035 2044 1942 2120 2010 2039 2028 2143 2016 2014 2001 1957 1952 2103
    ## [54797] 2142 2002 2159 2138 2201 2017 2029 2012 2105 2119 2048 2227 2021 2201
    ## [54811] 1955 2040 2218 2023 2111 2038 2106 2017 2031 2015 2150 2121 2011 2145
    ## [54825] 2224 2136 2209 2201 2245 2106 2155 2211 2047 2102 2113 2139 2204 2053
    ## [54839] 2216 2207 2243 2244 2114 2210 2127 2226 2206 2038 2101 2203 2036 2300
    ## [54853] 2144 2251 2214 2212 2125 2204 2050 2247 2149 2106 2213 2250 2037 2108
    ## [54867] 2123 2229 2131 2237 2152 2221 2154 2110 2128 2329 2120 2111 2111 2334
    ## [54881] 2241 2244 2229 2233 2304 2309 2203 2141 2150 2155 2112 2115 2119 2121
    ## [54895] 2252 2322 2257 2249 2130 2308 2313 2220 2200 2215 2342 2322 2324 2157
    ## [54909] 2245   20 2356 2224 2346 2249 2212 2214 2306 2252 2237 2147 2207 2200
    ## [54923]   31 2325 2337 2203 2328 2308   25 2231 2250 2331 2200 2210 2251 2249
    ## [54937] 2328 2215 2304 2258 2326 2327 2231   10 2232 2238   44   32 2253 2251
    ## [54951] 2256   16    7 2259    7 2349 2342 2353 2353 2352    5    3 2357   48
    ## [54965]   45  324  316  327   NA   NA   NA   NA  638  824  818  852  824  703
    ## [54979]  649  925  713  834  752  707  658  730  721  926  830  657  758  734
    ## [54993]  819  848  839  800  736  851  804  755  757  802  806  718  813  743
    ## [55007]  723  821  723  740  854  837  912  911  752  815   NA  749  757  855
    ## [55021]  725  849  949  916  822  904  856  918  904  904  802  757  822  836
    ## [55035]  902  904  753  932  823  849  852 1007  937  817  809  749  942  835
    ## [55049]  956  802  953  859  841  935 1037  943 1008  929 1003  825 1028  821
    ## [55063] 1018 1008  943  852  932 1033  855  959 1006  953 1016  910 1022 1027
    ## [55077]  941 1024 1021 1027  841 1026  856  956 1002 1030 1116  931 1022 1016
    ## [55091]  942 1027  955 1048  931  925 1024 1056 1011 1021 1015 1147  909  914
    ## [55105]  941 1114 1043 1020 1025  915  923 1102 1005  956  856  936 1001  927
    ## [55119]  853  918 1023 1023 1054 1054  938 1045  941  935 1043  953 1008 1101
    ## [55133] 1057 1046 1018  949  931 1114 1059 1118 1116 1032 1043  925 1019 1034
    ## [55147] 1119 1034 1039 1014 1158 1058 1103 1034 1023  955 1018 1038 1109 1103
    ## [55161]  937  950 1118  958  955 1046 1046 1056 1048 1033 1102 1200  957 1139
    ## [55175]  956 1013 1037 1152 1009 1037 1125 1009 1035 1105 1029 1059 1114 1149
    ## [55189] 1010 1012 1035 1157 1121  957 1149 1159 1133 1219 1141 1005 1154 1019
    ## [55203] 1012 1155 1119 1208 1034 1017 1201 1012 1131 1148 1154 1018 1137 1035
    ## [55217] 1227 1135 1205 1138 1033 1047 1011 1036 1159 1149 1214 1138 1209 1254
    ## [55231] 1231 1202 1129 1210 1214 1205 1123 1251 1224 1116 1206 1135 1240 1200
    ## [55245] 1038 1302 1107 1120 1224 1124 1130 1210 1239 1314 1156 1158 1126 1050
    ## [55259] 1231 1126 1122 1117 1122 1224 1143 1205 1103 1253 1235 1320 1151 1233
    ## [55273] 1223 1144 1246 1153 1204 1225 1213 1133 1244 1249 1146 1340 1254 1324
    ## [55287] 1205 1214 1328 1222 1138 1342 1239 1247 1226 1241 1129 1216 1324 1352
    ## [55301] 1148 1313 1353 1255 1356 1242 1157 1331 1247 1240 1224 1348 1407 1222
    ## [55315] 1304 1344 1232 1203 1330 1220 1422 1240 1403 1411 1236 1325 1308 1344
    ## [55329] 1403 1437 1328 1308 1402 1337 1332 1343 1404 1332 1419 1259 1329 1437
    ## [55343] 1458 1425 1309 1404 1248 1425 1526 1453 1442 1336 1342 1313 1415 1309
    ## [55357] 1302 1436 1343 1455 1449 1452 1433 1334 1438 1444 1429 1331 1316 1519
    ## [55371] 1455 1452 1339 1425 1516 1337 1457 1317 1445 1442 1404 1354 1418 1418
    ## [55385] 1500 1547 1518 1335 1430 1601 1618 1420 1431 1343 1438 1443 1530 1456
    ## [55399] 1403 1424 1556 1535 1505 1413 1554 1441 1547 1536 1519 1525 1427 1438
    ## [55413] 1518 1434 1453 1501 1435 1511 1541 1534 1752 1518 1604 1430 1526 1610
    ## [55427] 1548 1440 1456 1436 1621 1611 1517 1549 1425 1613 1617 1539 1631 1627
    ## [55441] 1555 1636 1510 1537 1526 1512 1509 1516 1634 1501 1642 1630 1605 1616
    ## [55455] 1458 1457 1651 1520 1652 1702 1705 1553 1608 1537 1626 1646 1626 1715
    ## [55469] 1632 1732 1549 1700 1533 1652 1701 1623 1712 1531 1640 1555 1537 1702
    ## [55483] 1629 1524 1733 1727 1555 1636 1632 1551 1727 1657 1700 1706 1727 1601
    ## [55497] 1549 1733 1554 1606 1617 1626 1631 1750 1545 1643 1733 1744 1647 1616
    ## [55511] 1626 1655 1754 1633 1701 1733 1742 1727 1718 1813 1647 1742 1753 1646
    ## [55525] 1641 1643 1904 1720 1906 1816 1607 1809 1803 1744 1748 1724 1705 1703
    ## [55539] 1633 1831 1644 1843 1723 1804 1913 1806 1819 1823 1744 1652 1703 1808
    ## [55553] 1707 1826 1706 1752 1716 1738 1911 1939 1755 1825 1733 1720 1844 1904
    ## [55567] 1814 1824 1726 1800 1810 1845 1801 1709 1735 1910 1740 1904 1826 1838
    ## [55581] 1830 1855 1815 1852 1813 1756 1756 1728 1932 1833 1906 1738 1926 1804
    ## [55595] 1817 1806 1831 1726 1911 1732 1939 1831 1742 1811 1936 1810 1917 1955
    ## [55609] 1808 1852 1834 1957 1911 1946 1930 1759 1805 1948 1830 1943 2000 1832
    ## [55623] 1817 1857 1944 1830 2006 1831 1830 1926 1934 1940 1946 1837 1832 1821
    ## [55637] 2008 2016 1819 2015 1834 1905 1853 1851 2007 1841 1810 1909 1955 1845
    ## [55651] 1917 1929 1908 1912 2027 2005 1927 1908 1938 1953 2046 1913 1900 2102
    ## [55665] 1908 1858 2012 1940 2028 2037 2019 1931 1854 1955 1914 2026 2035 1949
    ## [55679] 1958 2009 2038 1927 1929 2030 2026 1915 2034 1955 1936 2043 2008 2041
    ## [55693] 2027 2050 1941 2045 2056 1914 2013 2012 2019 1937 2017 1959 2052 2122
    ## [55707] 2117 1946 2016 2052 2119 2217 2118 2026 1940 2105 2123 1921 1956 2122
    ## [55721] 2126 2058 2223 2121 2027 2043 2026 2102 2133 1953 2118 2117 2131 2154
    ## [55735] 2008 2103 2055 2012 2012 2149 2156 2215 2034 2144 1955 2147 2117 2155
    ## [55749] 2133 2146 2043 2017 2042 2234 2020 2133 2134 2153 2240 2050 2127 2220
    ## [55763] 2029 2113 2051 2139 2115 2120 2217 2226 2311 2124 2053 2213 2115 2044
    ## [55777] 2209 2158 2221 2137 2242 2242 2052 2215 2253 2128 2215 2150 2217 2216
    ## [55791] 2225 2140 2058 2107 2120 2345 2219 2210 2207 2154 2315 2240 2108 2125
    ## [55805] 2118 2258 2324 2150 2237 2325 2138 2137 2303 2203 2135 2155 2105 2335
    ## [55819] 2145 2320 2147 2218 2152 2144 2233 2321 2158 2325 2347   11 2340 2200
    ## [55833] 2235 2204 2216 2321 2240 2339 2215 2207 2216 2240 2219   40   15 2326
    ## [55847] 2353 2235 2301 2224 2231 2220 2211 2345 2345   31 2257 2241 2242 2338
    ## [55861]   27 2318 2253    2   16    5 2247   26 2307   10 2254 2248 2258 2317
    ## [55875]   23 2353 2317 2342  103 2346 2342 2353 2357 2348 2351   43  327  337
    ## [55889]  345   NA   NA   NA   NA   NA  352  123  641  856  831  912  705  659
    ## [55903]  826  749  847  839  929  834  727  650  914  720  756  709  725  853
    ## [55917]  803  843  717  855  746  807  752  857  816  807  810  753  725  723
    ## [55931]  837  754  839  806  806  834  927  926  907  901  806  920  818  905
    ## [55945]  946  801  938  920  921  735  812  931  936  918  948  830  838  837
    ## [55959]  817  814  837  758  926  812  801  945  842  912  956  913  802  803
    ## [55973]  850  947  816   NA  944  910 1030 1036  936 1005  940  809  952  936
    ## [55987] 1329  832 1016  841  954 1018  911 1011 1024 1016 1005  950 1008  922
    ## [56001] 1023 1033 1022 1021 1003 1030 1007 1035 1040 1054  832 1015 1110 1031
    ## [56015]  914  949 1146 1015  906 1016 1056 1024 1123 1037  940  905 1040  938
    ## [56029] 1052 1100  912  951 1054  907  946  851 1036 1004  954 1056 1001 1032
    ## [56043]  905 1048 1100  922 1103  931 1033  940 1017 1035  955 1102 1107  952
    ## [56057]  924 1109 1056 1132 1041  937 1123 1044 1054 1051 1036  956 1016 1028
    ## [56071] 1053 1042  929 1210 1034 1018 1127  946 1109 1123 1015  951 1021 1131
    ## [56085] 1042 1049 1027 1134 1132  949 1021  959 1016 1106 1141 1153 1140 1028
    ## [56099]  949 1058 1013 1028 1158 1134 1106 1201  953 1007 1013 1108 1010 1015
    ## [56113]  953 1217 1015 1102 1227 1146 1235  958 1146 1143 1128 1147 1020 1135
    ## [56127] 1031  954 1217   NA 1630 1141 1122 1219 1157 1034 1205 1207 1117 1106
    ## [56141] 1027 1040 1234 1101 1032 1013 1059 1235 1151   NA 1223   NA 1203 1141
    ## [56155] 1239 1153 1213 1156 1606 1253 1152 1247 1144 1248 1316 1153 1255 1219
    ## [56169] 1112 1158 1247 1307 1219 1205 1136 1304 1440 1125 1254 1151 1144 1231
    ## [56183] 1224 1119 1209 1315 1118 1323 1312 1108 1225 1141 1224 1203 1136 1214
    ## [56197] 1205 1122 1322 1238 1322 1336 1218 1136 1245 1335 1213 1336 1419 1518
    ## [56211] 1307 1341 1249 1243 1345 1301 1344 1226 1256 1341 1307 1439 1146 1231
    ## [56225] 1332 1224 1342 1236 1334 1417 1227 1158 1224 1347 1350 1258 1222 1343
    ## [56239] 1336 1430 1258 1531 1328 1307 1246 1333 1332 1316 1426 1445 1250 1424
    ## [56253] 1440 1417 1455 1303 1429 1316   NA 1252 1403 1448 1408 1451 1447 1458
    ## [56267] 1435 1328 1321 1301 1452 1455 1509 1502 1339 1400 1416 1311 1516 1408
    ## [56281] 1422 1308 1342 1339 1536 1441 1542 1323 1408 1428 1328 1502 1358 1449
    ## [56295] 1405 1415 1422 1528 1523 1544 1536 1531 1346 1344 1555 1511 1346 1526
    ## [56309] 1401 1525 1359 1551 1605 1526 1443 1557 1451 1611 1421 1426 1549 1606
    ## [56323] 1546 1450 1508 1738 1423 1442 1502 1519 1418 1512 1530 1626 1808 1602
    ## [56337] 1518 1444 1457 1811 1620 1642 1530 1507 1533 1701 1500 1630 1534 1501
    ## [56351] 1530 1635 1701 1459 1547 1552 1634 1448 1507 1602 1529 1638 1646 1618
    ## [56365] 1658 1625 1458 1549 2030 1640 1523 1659 1548 1621 1623 1721 1705 1543
    ## [56379] 1520 1651 1539 1529 1631 1720 1613 1811 1539 1724 1620 1731 1741 1543
    ## [56393] 1557 1709 1716 1614 1740 1740 1811 1634 1616 1755 1635 1749 1753 1633
    ## [56407] 1750 1555 1753 1752 1715 1715 1757 1633 1635 1629 1550 1706 1641 1749
    ## [56421] 1805 1837 1712 1558 1554 1750 1803 1754 1734 1620 1756 1753 1708 1824
    ## [56435] 1730 1639 1723 1736 1804 1707 1635 1636 1812 1705 1641 1913 1837 1732
    ## [56449] 1808 1648 1835 1824 1748 1642 1817 1846 1726 1709 1814 1850 1710 1639
    ## [56463] 1714 1648 1811 1709 1827 1849 1748 1732 1853 1933 1845 1818 1650 1717
    ## [56477] 1847 1811 1755 1912 1726 1831 1722 1729 1845 1945 1711 1814 1903 1802
    ## [56491] 1842 1805 1933 1757 1806 1926 1717 1912 1935 1944 1717 1823 1824 1716
    ## [56505] 1746 1911 1922 1809 1820 1929 1807 1751 1845 1745 1837 1940 1814 1800
    ## [56519] 1946 1911 1746 1801 1849 1938 1906 1842 1846 1900 1806 1939 1859 1856
    ## [56533] 1820 1804 1833 2002 1959 1952 1829 1758 2005 1925 2105 1812 1959 1819
    ## [56547] 1824 2010 1915 1837 1852 1813 1907 1942 1958 1909 1832 1943 1943 1840
    ## [56561] 1818 1917 1916 1931 2120 2030 1923 2040 2002 1907 1927 1937 2015 2034
    ## [56575] 1932 1934 1905 2036 2024 2022 1951 2011 2031 2025 2047 2108 1923 1841
    ## [56589] 2035 2048 2012 2000 2047 1853 1902 2024   NA 2000 2122 1943 1924 2008
    ## [56603] 1928 2100 2041 2044 2123 2051 2127 2116 1913 1958 2016 2000 2014 1956
    ## [56617] 2008 1918 2236 1928 2059 2103 2128 2058 2125 2028 2104 1940 2114 1955
    ## [56631] 2116 2026 2126 2006 2120 2129 2026 2041 2123 2112 2045 2052 2142 2154
    ## [56645] 2038 2139 2136 2130 2104 2034 2001 2155 2138 2019 2045 2040 2341 2022
    ## [56659] 2118 2025 2120 2159 2103 2100 2040 2017 2134 2138 2130 2117 2016 2028
    ## [56673] 2032 2142 2037 2103 2203 2027 2023 2240 2137 2215 2109 2246 2150 2058
    ## [56687] 2135 2213 2114 2120 2231 2243 2245 2252 2118 2219 2314 2212 2145 2309
    ## [56701] 2147 2128 2208 2243 2220 2110 2243 2254 2058 2121 2121 2249 2228 2144
    ## [56715] 2128 2124 2212 2109 2056 2131 2202 2148 2141 2214 2044 2125 2140 2303
    ## [56729] 2226 2122 2226 2120 2257 2251 2238 2309 2105 2306 2125 2112 2315 2242
    ## [56743] 2105 2123 2239 2314 2145 2201 2221 2153 2231 2317 2120 2153 2302 2308
    ## [56757] 2323 2124    9 2327 2255 2330 2143 2143 2315 2214 2341 2307 2154 2332
    ## [56771] 2351 2203 2305 2356 2258 2248 2232 2212 2157 2359 2211 2148 2328 2204
    ## [56785]   NA 2355 2306   34 2349 2215 2217 2302 2255 2318 2259 2254 2335 2240
    ## [56799] 2227 2213 2339   24 2322    1 2233    7 2345 2241   29   12 2257 2317
    ## [56813] 2335 2239   28   38 2308 2352 2258 2327 2301  106 2344  115   46 2355
    ## [56827] 2328   38   41  110 2332 2336 2344 2347  148  137    6   51   13    3
    ## [56841]   34  329  333   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [56855]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [56869]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA  644  806
    ## [56883]  856  829  726  713  648  710  919  854  833  847  746  845  906  819
    ## [56897]  709  717  849  814  946  813  950  912  719  914  916  835  855  930
    ## [56911]  922  734  853  745  849  915  745  932  835  931  937  923  919  805
    ## [56925]  906  758  953  903  912 1007  913  751  842  911  914 1035 1004   NA
    ## [56939] 1100 1013  912  812  924  824 1019 1021  955  837 1019 1016  825 1014
    ## [56953] 1036 1004 1005  901  836  917 1113 1025 1042 1642  854 1053  841  906
    ## [56967] 1028 1004 1051  858 1007  858  912 1007  932 1046  906 1148 1003  941
    ## [56981] 1015  908 1057  957 1040 1026 1142 1038  908 1100 1032 1020 1105 1124
    ## [56995]  950 1118  947  925  949 1110 1111 1118  950 1112 1100 1057 1125  922
    ## [57009] 1014 1001 1021 1003 1024  937 1152 1114  939 1141 1134  930 1010 1002
    ## [57023] 1028 1143 1040 1009  959 1052 1129 1002 1147 1038 1257  954 1138 1151
    ## [57037]  930 1016  950 1202 1115  958 1123 1209  959 1154 1018 1252 1020 1015
    ## [57051] 1220 1237 1202 1017 1117 1016 1123 1046 1211 1420 1156 1031 1153 1114
    ## [57065] 1234 1231 1118 1112 1131 1108 1243 1232 1149 1337 1047 1255 1049 1330
    ## [57079] 1250 1133 1050 1259 1104 1257 1135 1237 1217 1326 1220 1103 1457 1253
    ## [57093] 1123 1312 1336 1103 1051 1202 1324 1220 1137 1314 1227 1251 1228 1211
    ## [57107] 1211 1239 1233 1143 1317 1126 1330 1336 1317 1348 1256 1301 1428 1223
    ## [57121] 1349 1319 1224 1338 1251 1354 1312 1215 1350 1155 1208 1407 1249 1213
    ## [57135] 1337 1311 1436 1242 1314 1359 1243 1214 1418 1436 1236 1343 1410 1230
    ## [57149] 1336 1318 1304 1347 1315 1321 1249 1312 1315 1417 1430 1504 1459 1249
    ## [57163] 1344 1253 1344 1517 1332   NA 1328 1304 1446 1456 1302 1413 1444 1514
    ## [57177] 1310 1306 1438 1416 1434 1325 1319 1506 1400 1433 1422 1354 1317 1501
    ## [57191] 1507 1353 1325 1446 1421 1458 1535 1344 1603 1437 1553 1549 1340 1514
    ## [57205] 1429 1522 1502 1408 1419 1415 1516 1604 1412 1528 1520 1540 1443 1412
    ## [57219] 1534 1555 1514 1445 1505 1627 1751 1509 1619 1432 1539 1633 1546 1433
    ## [57233] 1631 1533 1453 1635 1600 1542 1654 1542 1530 1644 1654 1630 1542 1704
    ## [57247] 1623 1449 1637 1605 1458 1624 1657 1701 1653 1622 1518 1532 1716 1532
    ## [57261] 1531 1648 1650 1721 1815 1607 1739 1611 1649 1549 1703 1606 1618 1600
    ## [57275] 1728 1703 1739 1642 1746 1629 1747 1752 1708 1700 1543 1632 1746 1856
    ## [57289] 1547 1652 1633 1638 1637 1807 1718 1720 1751 1647 1740 1740 1657 1715
    ## [57303] 1811 1722 1819 1747 1802 1813 1746 1902 1638 1655 1632 1710 1825 1823
    ## [57317] 1654 1828 1759 1701 1625 1704 1614 1830 1758 1826 1745 1857 1819 1700
    ## [57331] 1840 1846 1652 1728 1640 1724 1641 1827 1851 1929 1829 1718 1758 1924
    ## [57345] 1842 1904 1852 1758 1748 1714 1720 1821 1716 1830 1720 1902 1742 1901
    ## [57359] 1932 1729 1918 1855 1935 1856 1736 1938 1912 1914 1824 1832 1937 1727
    ## [57373] 1936 1911 1726 1908 1803 1821 1754 1945 1904 1752 1828 2007 1933 1817
    ## [57387] 1917 1836 1805 1944 1933 1838 1948 1949 1924 1946 1836 1757 1851 1750
    ## [57401] 1950 1948 1811 1917 1850 1953 2020 1906 1945 1834 1809 1936 1828 1949
    ## [57415] 1904 2036 2007 2001 1934 1812 2008 1850 1817 2012 1906 2031 1907 2023
    ## [57429] 1954 1919 2025 1943 1910 1930 1837 1937 2035 2033 2011 2042 2044 1954
    ## [57443] 2006 2030 2028 2025 2010 2046 1945 1855 1917 2116 1915 1957 2015 1944
    ## [57457] 2113 2037 2024 1922 1952 2011 1941 1921 2143 2012 2116 1949 2129 2121
    ## [57471] 2022 2134 2149 2137 2137 2037 1950 2117 1956 2157 2010 2138 2147 2044
    ## [57485] 2151 2002 2156 2022 2110 2137 2024 2208 2036 2205 2114 2149 2226 2120
    ## [57499] 2128 2216 2218 2027 2223 2226 2222 2158 2217 2120 2224 2234 2321 2148
    ## [57513] 2105 2309 2311 2236 2237 2259 2158 2242 2108 2126 2259 2158 2259 2120
    ## [57527] 2303 2315 2131 2346 2342 2241 2152 2247   10 2344 2259 2153 2322 2326
    ## [57541] 2348 2210    3 2313 2246 2346 2243   43   22   28 2252 2302  114 2331
    ## [57555] 2341 2341 2351    5 2339  353  338  350   NA   NA   NA   NA   NA   NA
    ## [57569]   NA  751  824  918 1028  709  839  848  703  700  643  754  900  805
    ## [57583]  852  829  844  712  753  750  905  814  907  719  753  736  859  939
    ## [57597]  929  840  920  913  802  910  749  947  834  825  740  752 1011  813
    ## [57611]  948  951  925 1135 1143 1031  817  923 1021  945  909 1013  943 1001
    ## [57625]  828 1001  938  813  911  835  808 1040 1007  936  915  936 1006  820
    ## [57639] 1047 1036 1007 1212 1004 1004 1012  901  930 1036  956 1222 1102 1026
    ## [57653]  959 1020  908 1100 1035  942 1027  918 1028  941  920  915  902  856
    ## [57667]  915  911 1028 1054  859 1246 1018 1008  943  917 1043 1051  957 1107
    ## [57681] 1042  938 1008  944 1108 1018 1054 1105 1122 1049 1032 1057 1045 1054
    ## [57695]  945  917 1016 1023 1017 1142 1040 1051  943 1114 1109  947  947 1020
    ## [57709] 1121 1030 1141 1012  931 1151 1034 1028 1328  956 1137  952 1105 1005
    ## [57723] 1035 1106 1005 1123 1133 1145  952 1055 1124 1131 1223  956 1018 1328
    ## [57737] 1235 1008 1129 1202 1139 1006 1153 1119 1216 1009 1102 1129 1106 1207
    ## [57751] 1058 1206 1254 1232 1012 1034 1205 1155 1143 1026 1155 1152 1211 1213
    ## [57765] 1134 1208 1242 1231 1050 1232 1118 1114 1034 1158 1201 1057 1406 1034
    ## [57779] 1232 1226 1056 1117 1103 1143 1226 1319 1209 1106 1115 1242 1054 1125
    ## [57793] 1106 1230 1537 1220 1251 1059 1154 1158 1238 1153 1200 1326 1124 1325
    ## [57807] 1116 1218 1331 1208 1124 1328 1304 1112 1208 1305 1304 1129 1138 1223
    ## [57821] 1340 1257 1346 1243 1305 1341 1217 1345 1312 1244 1317 1406 1210 1223
    ## [57835] 1227 1200 1248 1148 1414 1338 1400 1231 1322 1211 1421 1351 1253 1241
    ## [57849] 1318 1324 1237 1403 1205 1420 1319 1245 1323 1405 1345 1419 1303 1320
    ## [57863] 1252 1333 1322 1420 1414 1341 1347 1243 1432 1511 1255 1428 1504 1451
    ## [57877] 1249 1437 1452 1254 1327 1243 1432 1256 1419 1415 1506 1452 1335 1514
    ## [57891] 1516 1335 1333 1416 1448 1516 1436 1323 1314 1313 1457 1444 1446 1345
    ## [57905] 1420 1404 1502 1316 1327 1353 1411 1455 1344 1405 1523 1510 1409 1327
    ## [57919] 1410 1341 1516 1334 1353 1457 1356 1448 1435 1536 1602 1535 1543 1445
    ## [57933] 1431 1613 1530 1535 1507 1414 1631 1402 1409 1543 1550 1607 1434 1626
    ## [57947] 1438 1501 1422 1405 1836 1633 1502 1511 1432 1615 1511 1424 1502 1455
    ## [57961] 1433 1452 1624 1514 1609 1624 1641 1522 1529 1642 1548 1504 1526 1452
    ## [57975] 1636 1649 1709 1533 1623 1719 1546 1525 1708 1652 1516 1616 1455 1524
    ## [57989] 1517 1640 1717 1525 1706 1546 1554 1514 1650 1631 1659 1612 1647 1541
    ## [58003] 1644 1554 1659 1629 1638 1725 1700 1601 1741 1559 1538 1556 1534 1716
    ## [58017] 1701 1534 1804 1642 1754 1630 1654 1726 1634 1633 1748 1740 1743 1535
    ## [58031] 1745 1654 1700 1934 1628 1735 1639 1611 1706 1609 1636 1804 1607 1619
    ## [58045] 1659 1752 1604 1743 1757 1749 1608 1652 1608 1757 1653 1736 1712 1744
    ## [58059] 1810 1705 1750 1844 1721 1753 1959 1808 1702 2008 1704 1736 1813 1733
    ## [58073] 1641 1804 1842 1859 1734 1825 1739 1830 1733 1643 1854 1809 1840 1857
    ## [58087] 1636 1659 1653 1651 1901 1642 1747 1846 1714 1803 1753 1746 1643 1746
    ## [58101] 1728 1908 1803 1841 1653 1655 1740 1721 1651 1721 1857 1824 1849 1855
    ## [58115] 1858 1723 1825 1751 1756 1843 1714 1834 1935 1737 1743 1903 1846 1740
    ## [58129] 1853 1807 1820 1730 1836 1911 1922 1813 1840 1839 1904 1818 1744 1822
    ## [58143] 1906 1717 1801 1725 1954 1904 1930 1747 1750 1840 1946 1925 2015 1800
    ## [58157] 1924 1805 1824 1949 1921 1908 2004 1801 1827 1847 1924 1904 1915 1743
    ## [58171] 1824 1803 1935 1851 1842 1940 1952 1941 1836 1814 2022 1946 1950 2021
    ## [58185] 1939 1823 1927 1957 2033 1845 1916 1832 1826 1907 1848 2015 1839 1820
    ## [58199] 2002 1958 2040 1820 1951 1909 1913 2000 2018 1818 1848 1838 2013 2127
    ## [58213] 1946 2044 2031 2049 1915 1930 2100 1924 1944 2019 1918 2029 1950 1845
    ## [58227] 2059 2053 2102 2051 1956 2023 2044 1901 1945 1857 2041 2052 2025 1947
    ## [58241] 1928 1942 2043 1857 1928 2107 1929 2051 1942 1946 2048 2121 2037 2039
    ## [58255] 2106 2152 2020 2043 2021 2131 2102 2111 2015 2125 1956 2045 2124 1938
    ## [58269] 2225 2109 2013 2054 2044 2021 2022 2155 2046 2118 2047 2052 2203 2147
    ## [58283] 2024 2001 1955 2020 2035 2004 2152 2038 2118 2019 2056 2235 2141 2045
    ## [58297] 2118 2153 2214 2049 2028 2107 2233 2116 2031 2043 2024 2032 2054 2230
    ## [58311] 2037 2159 2217 2200 2224 2032 2106 2204 2121 2314 2242 2209 2139 2045
    ## [58325] 2259 2026 2206 2145 2232 2131 2209 2120 2216 2255 2230 2057 2245 2041
    ## [58339] 2309 2155 2227   23 2325 2102 2055 2215 2229 2137 2204 2131 2224 2259
    ## [58353] 2104 2125 2242 2103 2254 2120 2046 2246 2245 2209 2047 2201 2058 2148
    ## [58367] 2200   42 2148 2053 2310 2222 2122 2117 2222 2230 2137 2256 2319 2334
    ## [58381] 2131 2247 2349 2115 2152 2248 2230 2132 2202 2357 2336 2152 2248 2148
    ## [58395] 2304 2339 2253 2136 2306 2154 2202 2324 2325 2251 2346  119 2147 2210
    ## [58409] 2153 2204 2342 2153 2238 2307   13 2254 2341 2329 2248 2152 2154 2344
    ## [58423] 2202 2300 2201 2256 2258 2228 2256 2343 2317 2227 2219 2322 2228 2244
    ## [58437] 2251 2340 2331 2218 2302 2358 2313   17 2237 2317 2354    1 2231 2249
    ## [58451] 2350 2308 2250   11 2258 2307 2303  101 2338 2347 2348 2357 2353 2350
    ## [58465] 2352   14  424  435  423   NA   NA  120  629  804  821  830  648  841
    ## [58479]  650  826  726  644 1027  830  732  704  927  850  715  843  733  833
    ## [58493]  748  853  816  714  735  757  728  800  717  731  904  802  714  807
    ## [58507]  818  819  826  856  912  857  833  914  807  759  923  912  815  911
    ## [58521]  819 1013  809  755 1003  918  841  732  752  918  915  759  758  743
    ## [58535]  806  840  921  938  847  747  820 1031  747  838  915 1136  900  758
    ## [58549]  925  952  949 1013  821 1032 1056  933 1035  847  944 1142  929  834
    ## [58563] 1030 1041 1020  905  945 1042  941  903 1005  953  907  847 1001  857
    ## [58577]  908  855  947 1012 1026  811  928 1043  913  829  938 1009 1102 1036
    ## [58591]  903 1020 1022  924 1013  938 1000  902 1034  906 1025 1207 1024 1034
    ## [58605]  959  847  947 1103  934  922  930  902 1023  933  849 1043 1016  850
    ## [58619] 1051  932  917 1030  920  932 1008 1032  940 1004 1048 1040 1235 1033
    ## [58633]  940 1041 1109  930 1052 1101 1054  925 1131 1122  934 1021 1058 1152
    ## [58647] 1250 1031 1040 1057 1000 1006  934 1002  923 1101 1155 1009 1006 1008
    ## [58661] 1019 1014 1044 1020 1051 1041  947  931 1125 1026 1216  932 1035 1207
    ## [58675] 1116 1123 1140 1117  941 1125 1111 1044 1020 1010 1147 1151  946 1159
    ## [58689] 1001 1016 1117 1217 1105 1206 1013 1019 1026 1209 1207 1220 1336 1112
    ## [58703] 1143 1003 1007 1146 1040 1221 1027 1050 1204 1200 1115 1143 1231 1228
    ## [58717] 1133 1237 1054 1113 1158 1138 1200 1221 1240 1117 1235 1154 1209 1139
    ## [58731] 1133 1217 1216 1357 1230 1223 1234 1120 1257 1126 1319 1125 1123 1254
    ## [58745] 1226 1240 1206 1155 1115 1111 1320 1151 1140 1055 1146 1102 1125 1223
    ## [58759] 1210 1317 1324 1219 1153 1143 1558 1314 1150 1150 1240 1240 1308 1320
    ## [58773] 1157 1206 1133 1227 1207 1206 1139 1357 1127 1235 1311 1354 1304 1304
    ## [58787] 1223 1348 1239 1218 1418 1352 1312 1351 1152 1314 1145 1140 1408 1345
    ## [58801] 1244 1251 1217 1203 1359 1211 1244 1418 1330 1419 1220 1302 1235 1204
    ## [58815] 1420 1227 1250 1248 1431 1343 1303 1418 1421 1438 1329 1348 1347 1328
    ## [58829] 1329 1320 1434 1439 1413 1413 1341 1420 1401 1513 1253 1306 1331 1350
    ## [58843] 1254 1504 1403 1257 1514 1437 1408 1420 1249 1343 1522 1502 1346 1514
    ## [58857] 1526 1500 1302 1347 1449 1452 1510 1421 1314 1405 1306 1335 1513 1410
    ## [58871] 1539 1539 1502 1350 1352 1405 1331 1324 1522 1554 1459 1534 1522 1421
    ## [58885] 1327 1500 1453 1456 1424 1449 1449 1532 1543 1527 1558 1352 1538 1405
    ## [58899] 1452 1614 1454 1600 1627 1535 1423 1506 1531 1610 1407 1537 1400 1528
    ## [58913] 1435 1431 1507 1442 1639 1503 1544 1447 1557 1701 1458 1506 1501 1641
    ## [58927] 1556 1448 1913 1530 1436 1628 1541 1512 1604 1532 1543 1617 1537 1511
    ## [58941] 1443 1649 1548 1643 1646 1640 1533 1524 1456 1528 1557 1707 1627 1702
    ## [58955] 1723 1527 1512 1735 1458 1642 1520 1640 1545 1732 1446 1602 1728 1717
    ## [58969] 1613 1611 1500 1658 1536 1604 1606 1701 1713 1659 1601 1639 1720 1746
    ## [58983] 1531 1651 1602 1538 1726 1749 1625 1612 1641 1721 1621 1651 1556 1723
    ## [58997] 1544 1719 1659 1610 1718 1710 1658 1610 1630 1618 1642 1733 1755 1808
    ## [59011] 1711 1621 1601 1746 1703 1738 1753 1640 1600 1658 1930 1813 1748 1804
    ## [59025] 1645 1651 1803 1642 1809 1548 1723 1625 1956 1723 1636 2004 1815 1759
    ## [59039] 1721 1631 1820 1814 1733 1833 1818 1806 1805 1802 1827 1820 1759 1746
    ## [59053] 1729 1852 1738 1836 1809 1705 1911 1702 1820 1701 1853 1749 1706 1907
    ## [59067] 1717 1743 1657 1914 1733 1712 1930 1820 1818 1655 1845 1815 1844 1738
    ## [59081] 1712 1908 1908 1750 1719 1759 1758 1852 1835 1832 1757 1759 1716 1806
    ## [59095] 1847 1903 1845 1821 1904 1851 1854 1805 1900 1750 1951 1724 1822 1912
    ## [59109] 1842 1948 1933 1759 1940 1926 1722 1845 1856 1834 1949 1732 1852 1809
    ## [59123] 1959 1812 1928 1956 2011 1825 1941 1802 1804 1943 1831 1944 2021 1933
    ## [59137] 1820 2015 1935 1817 2041 1834 1908 1752 1914 1920 1855 2005 1901 1825
    ## [59151] 2002 1855 1849 1948 1955 2001 1757 1835 2034 1754 2000 1905 2021 2032
    ## [59165] 1957 1844 2038 1830 1938 1931 1924 1903 2028 2020 1825 1857 2023 1854
    ## [59179] 1906 1914 2013 1909 1913 2016 2011 2010 2019 1946 2110 1945 2051 1916
    ## [59193] 2031 2024 2100 2049 2040 2034 1915 1918 2116 1858 2010 2052 2023 1944
    ## [59207] 1844 2031 2039 1845 2005 2108 2051 2113 1941 2035 2054 2046 2103 1947
    ## [59221] 2048 1924 2121 2058 2056 1943 1926 2052 2012 2007 1938 2129 1930 2010
    ## [59235] 2030 2054 2034 2137 2050 2116 2128 1938 2153 2117 2047 2024 2002 2127
    ## [59249] 2035 1945 2012 2143 2126 2149 2051 2121 2010 2026 2108 2034 2010 2054
    ## [59263] 2125 2046 2050 2010 2048 2006 2020 2022 2009 2122 2243 2050 2154 2225
    ## [59277] 2207 2053 2048 2159 2016 2257 2218 2040 2129 2036 2129 2047 2144 2028
    ## [59291] 2135 2204 2104 2210 2031 2155 2050 2240 2248 2122 2203 2152 2142 2249
    ## [59305] 2124 2156 2054 2248 2143 2018 2234 2238 2133 2058 2236 2108 2102 2117
    ## [59319] 2133 2156 2210 2147 2231 2232 2133 2239    4 2238 2146 2236 2240 2234
    ## [59333] 2247 2039 2226 2130 2254 2208 2219 2130 2301   14 2235 2145 2230 2208
    ## [59347] 2153 2231 2139 2224 2248 2131 2306 2234 2306 2331 2323 2113 2227 2252
    ## [59361] 2314 2104 2150 2115 2230 2253 2359 2301 2336 2213 2146 2333 2204 2136
    ## [59375] 2136 2141 2332 2307 2240 2221 2155 2134 2300 2306 2220    2 2225   12
    ## [59389] 2212 2356 2232 2216 2158 2309 2257 2343 2237 2310 2207 2223 2330 2350
    ## [59403] 2301 2322 2324 2357 2228 2323 2327 2316 2229 2228   31 2311 2310   14
    ## [59417] 2327 2300 2324 2220 2221 2226 2345 2250 2238 2251 2339  308 2240    1
    ## [59431] 2259    9 2254 2311 2256 2314 2337 2400 2346   21   48  420  428  420
    ## [59445]   NA   NA   NA   NA   NA  425  636  805  819  839  833  643  654  751
    ## [59459]  645  729  839  705  728 1018  723  745  841  819  754  846  953  947
    ## [59473]  839  804  729  841  718  758  850  823  832  903  909  804  736  826
    ## [59487]  729  802  853  903  753  919  721  742  833  757  801 1008  905  911
    ## [59501]  855  737  907  839  907  803  851  914  827  742  834  915  914  914
    ## [59515]  952  912  800  834  801  758 1003  937  916  852  852  852  752  932
    ## [59529]  740  842  851  946 1022  759 1042 1023 1000 1131  927  812 1125  853
    ## [59543] 1043  934  822 1002  853  953 1010  903  850 1007  906  947  959  956
    ## [59557] 1005  942  926 1043 1044 1005 1058  846 1030 1202 1029  913  902 1011
    ## [59571]  833 1052 1001  915  921 1024  846  934 1045  955 1214 1029 1021  857
    ## [59585] 1043 1039 1103  849  909  947  918  921 1050 1044  948 1056  850  919
    ## [59599] 1008  928  929 1038 1024 1018 1038  949  924  918 1011 1127 1038 1040
    ## [59613] 1047  940 1202 1108 1118 1058 1031  918 1022 1057 1041 1110 1153 1243
    ## [59627] 1124 1113 1016 1021 1018  950 1212  944 1143  921  950 1019 1013  934
    ## [59641]  914  943 1051 1020 1030 1117  955 1019 1121 1050 1000 1114 1046  945
    ## [59655] 1159 1146 1038 1115 1118 1055 1130 1056 1110 1041 1203 1200 1143 1005
    ## [59669] 1059 1150 1216  959 1307 1230 1007 1231 1015 1212 1152 1232 1020 1129
    ## [59683] 1137 1148 1211 1137 1207 1010 1136 1057 1133 1040 1140 1010 1141 1121
    ## [59697] 1232 1051 1202 1143 1225 1136 1124 1214 1208 1148 1248 1153 1217 1042
    ## [59711] 1208 1117 1240 1532 1301 1226 1223 1045 1253 1125 1108 1140 1209 1403
    ## [59725] 1234 1128 1153 1318 1058 1200 1158 1228 1328 1106 1130 1107 1153 1244
    ## [59739] 1252 1259 1217 1156 1251 1231 1217 1224 1139 1321 1130 1257 1205 1135
    ## [59753] 1144 1137 1128 1314 1353 1212 1213 1322 1314 1334 1229 1353 1204 1346
    ## [59767] 1338 1405 1143 1351 1310 1309 1140 1153 1223 1245 1301 1235 1136 1334
    ## [59781] 1244 1238 1221 1219 1218 1204 1240 1404 1259 1338 1332 1409 1413 1201
    ## [59795] 1425 1310 1249 1353 1423 1413 1419 1351 1317 1240 1257 1240 1421 1336
    ## [59809] 1427 1343 1336 1339 1406 1247 1355 1250 1332 1300 1412 1250 1418 1337
    ## [59823] 1439 1351 1340 1244 1327 1424 1437 1251 1457 1509 1448 1523 1504 1315
    ## [59837] 1353 1251 1437 1352 1500 1332 1426 1336 1442 1515 1349 1503 1511 1459
    ## [59851] 1509 1343 1423 1407 1520 1605 1407 1416 1329 1428 1332 1533 1513 1346
    ## [59865] 1337 1426 1559 1336 1359 1334 1527 1410 1556 1530 1520 1430 1432 1342
    ## [59879] 1426 1407 1615 1440 1544 1356 1443 1513 1522 1528 1544 1609 1537 1546
    ## [59893] 1442 1455 1536 1545 1423 1412 1428 1548 1553 1648 1454 1508 1434 1511
    ## [59907] 1501 1522 1426 1453 1633 1616 1611 1507 1612 1657 1554 1622 1627 1515
    ## [59921] 1541 1509 1739 1624 1641 1456 1715 1721 1548 1549 1521 1456 1458 1451
    ## [59935] 1706 1623 1722 1531 1622 1605 1551 1609 1705 1714 1630 1637 1704 1553
    ## [59949] 1544 1631 1650 1640 1644 1620 1621 1652 1725 1534 1557 1715 1539 1726
    ## [59963] 1746 1650 1626 1604 1728 1702 1735 1757 1730 1631 1735 1611 1655 1627
    ## [59977] 1740 1555 1559 1628 1743 1640 1601 1813 1736 1802 1713 1811 1606 1718
    ## [59991] 1913 1715 1712 1628 1750 1648 1813 1729 1755 1942 1718 1626 1742 1755
    ## [60005] 1812 1649 1800 1643 1746 1736 1625 1627 1843 1816 1947 1818 1652 1744
    ## [60019] 1803 1710 1706 1653 1707 1623 1752 1731 1634 1845 1807 1750 1644 1621
    ## [60033] 1704 1811 1851 1848 1816 1906 1818 1839 1640 1709 1814 1748 1756 1740
    ## [60047] 1711 1639 1831 1845 1903 1746 1708 1655 1848 1837 1839 1924 1721 1732
    ## [60061] 1806 1716 1656 1841 1838 1711 1727 1822 1857 1816 1855 1808 1753 1755
    ## [60075] 1817 1819 1831 1733 1831 1809 1824 1909 1926 1822 1850 1913 1810 1857
    ## [60089] 1854 1803 1739 1751 1812 1752 1916 1911 1837 1744 1743 1918 1805 1905
    ## [60103] 1935 1916 2002 1928 1752 1947 2014 1852 1906 2005 1918 1830 1922 2002
    ## [60117] 1758 1801 1749 1907 1918 1859 2025 2012 1941 1858 1749 1807 1835 2002
    ## [60131] 1937 1802 1803 2010 1844 1947 1816 2033 1748 1955 2024 1834 1847 1905
    ## [60145] 2006 1819 2005 1802 1958 1945 1913 1804 1945 2006 1856 2014 1908 1811
    ## [60159] 1859 1831 2050 2030 1921 2030 2033 1925 2032 1918 2021 2047 1924 2007
    ## [60173] 2028 1925 2008 1843 2054 1959 2038 2127 2013 1849 2012 2105 2020 2049
    ## [60187] 1909 2022 2016 2034 1909 1918 2001 1946 2045 2016 2115 1917 2026 2051
    ## [60201] 2029 2025 1902 1901 1914 1936 2026 1923 1944 2100 2049 2035 1954 1923
    ## [60215] 1959 2015 2111 2147 2125 2142 2103 2037 1942 1935 2004 1920 2024 2016
    ## [60229] 2059 2022 2016 2112 2023 2142 1946 2128 2026 2206 2127 1948 2154 2004
    ## [60243] 2204 2119 2104 2128 2118 1951 2016 2003 2130 2141 2219 2214 2211 2100
    ## [60257] 2137 2043 2019 2151 2125 2048 2143 2016 2057 2008 2055 2119 2127 2033
    ## [60271] 2148 2241 2220 2251 2149 2051 2144 2147 2222 2212 2301 2035 2040 2227
    ## [60285] 2024 2153 2043 2145 2130 2217 2228 2121 2137 2245 2221 2247 2058 2159
    ## [60299] 2053 2153 2212 2141 2057 2243 2212 2057 2109   24 2120 2056 2210 2149
    ## [60313] 2130 2048 2223 2305 2055 2217 2111 2137 2212 2310 2149 2229 2230 2131
    ## [60327] 2103 2246 2127 2107 2213 2123 2056 2306 2331 2252 2249 2348 2241 2156
    ## [60341] 2300 2212 2150 2306 2345 2150 2143 2301 2130 2318   56 2356 2146 2237
    ## [60355] 2151   13 2147 2311    3 2153 2340 2347 2252 2320 2200 2206 2322 2314
    ## [60369] 2244 2203 2236 2228 2235 2156 2255 2323   29 2327 2205 2248 2216 2344
    ## [60383] 2207 2220 2250   10 2314 2316 2358 2235 2244 2241   22    2 2258 2325
    ## [60397] 2303 2257 2249 2320 2351 2331 2325 2341 2347   13 2340    2  424  420
    ## [60411]   NA   NA   NA   NA   NA   NA  643  749  820  829  655  916  703  748
    ## [60425]  657  642  659 1015  737  834  819  829  850  848  752  856  750  717
    ## [60439]  908  751  842  732  811  903  752  844  818  858  737  757  801  824
    ## [60453]  909  812  750  919  723  754  808  756  730  924  907  758  820  905
    ## [60467]  949  900  844  932  901  736  913 1021  807  916  919  814  851  901
    ## [60481]  757  835  824  759 1012  837  851  913  849  753  902  819 1007  802
    ## [60495]  801  846  835  846 1024  938 1125  950 1012  801 1020  957  910 1000
    ## [60509]  934 1130  858  954 1035  857  956  904 1045  917  905  836 1039  943
    ## [60523] 1008 1044 1151  919  830  943 1017 1012 1001 1019  902 1040 1013 1028
    ## [60537]  906  923  939 1021 1208 1008 1001 1038 1020  926 1025  854  900 1016
    ## [60551] 1045  920 1142  952 1052  852  948 1051 1031  954 1055  925   NA 1025
    ## [60565]  911  925  916 1028  947 1045 1043 1039 1106 1000  945 1114 1137 1101
    ## [60579] 1041 1041 1017 1038  930  931 1126 1100 1055 1021 1013 1101  924 1100
    ## [60593] 1054 1120 1143 1010 1244 1016  953 1029 1129  935  938  921 1042 1115
    ## [60607] 1019 1005 1117 1107 1029 1040  936 1152  942  957 1029 1047  951 1014
    ## [60621] 1022 1107 1032 1033 1121 1139 1141 1037 1209 1122 1140 1219 1336 1225
    ## [60635] 1004 1041 1131 1015 1130 1144 1213 1018 1204  959 1221 1103 1228 1159
    ## [60649] 1014 1125 1119 1214 1206 1137 1225 1224 1133 1115 1234 1119 1021 1059
    ## [60663] 1005 1107 1229 1217 1204 1224 1228 1117 1154 1254 1207 1231 1115 1024
    ## [60677] 1222 1211 1155 1603 1209 1220 1049 1112 1136 1401 1149 1123 1130 1302
    ## [60691] 1151 1103 1220 1609 1248 1233 1138 1106 1219 1228 1239 1236 1319 1215
    ## [60705] 1201 1139 1211 1222 1126 1157 1133 1128 1235 1307 1254 1327 1118 1308
    ## [60719] 1302 1331 1347 1210 1300 1248 1325 1312 1230 1241 1151 1308 1407 1130
    ## [60733] 1310 1358 1155 1305 1251 1211 1236 1242 1309 1233 1219 1152 1228 1430
    ## [60747] 1329 1228 1240 1319 1411 1250 1331 1213 1341 1204 1355 1427 1349 1410
    ## [60761] 1249 1415 1253 1322 1243 1344 1259 1433 1349 1305 1235 1222 1228 1428
    ## [60775] 1312 1424 1336 1331 1426 1240 1419 1502 1349 1312 1319 1342 1408 1345
    ## [60789] 1310 1523 1422 1402 1304 1255 1355 1310 1546 1303 1437 1522 1306 1449
    ## [60803] 1427 1408 1342 1500 1451 1345 1500 1348 1350 1327 1307 1454 1447 1326
    ## [60817] 1506 1320 1417 1451 1525 1423 1356 1449 1357 1550 1327 1336 1452 1424
    ## [60831] 1514 1430 1340 1333 1508 1517 1350 1353 1520 1338 1529 1557 1415 1414
    ## [60845] 1609 1355 1354 1449 1442 1541 1616 1440 1410 1539 1551 1528 1542 1517
    ## [60859] 1533 1625 1452 1438 1545 1414 1543 1527 1453 1608 1652 1445 1442 1507
    ## [60873] 1445 1605 1430 1524 1630 1455 1546 1611 1629 1622 1715 1505 1548 1628
    ## [60887] 1514 1629 1636 1540 1524 1534 1630 1625 1544 1533 1719 1455 1506 1535
    ## [60901] 1647 1730 1450 1713 1618 1629 1502 1701 1556 1636 1602 1538 1535 1617
    ## [60915] 1624 1707 1728 1612 1605 1647 1617 1708 1718 1541 1645 1648 1703 1735
    ## [60929] 1649 1733 1651 1642 1608 1729 1643 1653 1726 1723 1556 1646 1607 1725
    ## [60943] 1817 1552 1559 1732 1736 1744 1623 1730 1740 1925 1600 1716 1604 1640
    ## [60957] 1557 1620 1741 1756 1800 1922 1658 1813 1633 1724 1644 1642 1722 1611
    ## [60971] 1812 1705 1755 1821 1746 1726 1737 1626 1755 1710 1707 1631 1637 1950
    ## [60985] 1715 1820 1655 1718 1855 1715 1829 1743 1655 1834 1732 1624 1705 1708
    ## [60999] 1841 1639 1710 1805 1657 1905 1821 1824 1657 1719 1730 1818 1637 1800
    ## [61013] 1901 1715 1749 1842 1835 1741 1732 1839 1708 1858 1902 1737 1913 1738
    ## [61027] 1830 1742 1809 1700 1805 1733 1856 1821 1757 1833 1706 1926 1806 1816
    ## [61041] 1806 1856 1803 1823 1923 1755 1816 1858 1834 1801 1906 1849 1824 1735
    ## [61055] 1843 1733 1825 1752 1858 1911 1833 1907 1918 1919 1910 1928 1839 1934
    ## [61069] 1905 1959 1944 1820 1806 1802 2008 1753 1946 1937 1915 1953 1758 1857
    ## [61083] 1825 1751 1908 1748 1914 1914 1954 1955 1916 1849 1842 2011 1859 1938
    ## [61097] 2004 1819 1951 1812 1955 1806 1920 1805 1812 2023 1839 1850 1838 1834
    ## [61111] 1857 1909 1944 1833 2015 1857 1922 1833 1818 1901 1905 1936 1825 2011
    ## [61125] 1917 1917 2015 2015 2019 1914 1934 2010 2041 1950 1914 2017 1957 1943
    ## [61139] 2053 2100 2057 2049 2014 1925 2037 1850 2011 1937 1859 2045 1910 2127
    ## [61153] 1922 2015 2053 2111 2052 2140 1921 2022 2029 1856 1913 2032 2013 1917
    ## [61167] 2028 2113 1948 1943 2048 2029 1957 2125 2048 2127 1944 2019 2221 2055
    ## [61181] 2129 2117 1936 1952 2125 2007 2108 2018 2148 1947 2039 2006 2030 2030
    ## [61195] 2032 2105 2145 2024 2135 2026 1939 2206 2028 2155 2036 2101 2009 2136
    ## [61209] 2126 2230 2011 2211 2218 2148 2017 2117 2201 2106 2046 1952 2240 2130
    ## [61223] 2126 2033 2249 2148 2012 2110 2105 2251 2143 2222 2043 1954 2008 2030
    ## [61237] 2019 2049 2029 2053 2233 2039 2240 2206 2156 2209 2057 2158 2034 2024
    ## [61251] 2106 2207 2214 2038 2247 2224 2119 2243 2242 2211 2117 2358 2143 2131
    ## [61265] 2147 2220 2041 2254 2227 2228 2137 2228 2117 2118 2109 2225 2159 2228
    ## [61279] 2252 2231 2137 2048 2234 2055 2102 2113 2147 2111 2309 2228 2124 2221
    ## [61293] 2101 2230 2151 2204 2144 2127 2245 2325 2220 2114 2302 2203 2233   42
    ## [61307] 2202 2328 2248 2251 2259 2247   12 2338 2150 2144 2137 2122 2151 2226
    ## [61321] 2155 2153 2142 2343 2359 2246 2150    7    5 2344 2347 2253    5 2328
    ## [61335] 2149 2312 2145 2309 2202 2318 2326 2238 2207 2219 2326 2207 2303 2246
    ## [61349] 2341 2250  126   33 2356 2305 2308   13 2358 2344   44 2258   15 2243
    ## [61363] 2249 2328 2305 2259 2317 2255 2309 2334 2327 2331 2337 2350 2348    7
    ## [61377]  144   12   18  424  426  425   NA   NA   NA   NA   NA   NA   NA  643
    ## [61391]  752  829  830  657  705  716  707  837  750  810  815  704  712  723
    ## [61405]  847  909 1025  739  843  805  713  925  826  826  729  806  915  803
    ## [61419]  730 1044  832  919  858  930  821  821  724  839  817  752  811  842
    ## [61433]  749  750  854  912  917  855  910  743  842  730  910  912  803 1016
    ## [61447]  933  917  933  923  820  952  915  946  757  806  858  903  905  920
    ## [61461]  739  859  854  835  749 1120 1026  921  818  948  812 1023  933  815
    ## [61475]  819  927  956 1029 1019  901 1008  856  956 1137 1000  849  831 1014
    ## [61489]  949  954 1005 1017  859 1039  953  851  856 1001  930 1033  943 1006
    ## [61503]  825 1028 1028 1030 1004 1054 1034  914  911 1211  936  933 1032 1048
    ## [61517]  924  857 1002 1029 1035  914 1033  919 1043  946  906  958  844  902
    ## [61531] 1107 1047 1052 1030 1028  912 1036  928 1109 1004 1232  936 1109 1040
    ## [61545] 1022 1105 1107 1135 1049 1102 1047  949  930 1048 1114 1117  924 1052
    ## [61559] 1111 1010 1106 1034 1027 1112  958 1140 1029 1209 1007  957 1033 1125
    ## [61573] 1040 1034 1140  958 1304 1036 1127 1050  938  951  921 1023 1143  958
    ## [61587]  947  949 1057 1037 1136 1203 1036 1118 1147 1158 1105 1133 1209 1152
    ## [61601] 1105  959  959 1329 1117 1139 1202 1017 1154 1153 1201 1134 1033 1150
    ## [61615] 1216 1025 1005 1021 1157 1224 1206 1130 1134 1048 1043 1043 1109 1219
    ## [61629] 1254 1207 1219 1117 1233 1104 1205 1416 1217 1155 1054 1217 1231 1234
    ## [61643] 1021 1546 1251 1134 1301 1203 1239 1055 1232 1236 1246 1145 1232 1323
    ## [61657] 1311 1103 1229 1112 1244 1058 1159 1049 1110 1115 1144 1233 1316 1301
    ## [61671] 1110 1134 1312 1248 1228 1228 1432 1144 1259 1140 1120 1243 1201 1150
    ## [61685] 1124 1135 1136 1336 1328 1306 1154 1114 1140 1231 1320 1257 1238 1232
    ## [61699] 1337 1328 1307 1349 1146 1300 1355 1417 1354 1356 1135 1313 1214 1333
    ## [61713] 1207 1333 1326 1314 1238 1234 1354 1153 1359 1400 1245 1404 1318 1401
    ## [61727] 1337 1358 1218 1244 1217 1410 1406 1422 1301 1448 1255 1259 1352 1330
    ## [61741] 1324 1425 1436 1422 1458 1316 1241 1246 1438 1425 1404 1506 1356 1421
    ## [61755] 1334 1253 1300 1510 1401 1438 1336 1402 1302 1504 1449 1518 1533 1307
    ## [61769] 1324 1537 1457 1342 1406 1425 1503 1453 1345 1523 1417 1329 1513 1326
    ## [61783] 1446 1332 2047 1456 1327 1350 1425 1527 1410 1337 1538 1409 1343 1607
    ## [61797] 1400 1419 1550 1517 1527 1357 1449 1550 1406 1608 1500 1434 1415 1558
    ## [61811] 1620 1608 1529 1421 1535 1415 1435 1550 1617 1546 1617 1507 1519 1552
    ## [61825] 1420 1701 1508 1459 1519 1502 1427 1639 1520 1624 1621 1502 1527 1626
    ## [61839] 1448 1454 1446 1516 1630 1636 1633 1549 1541 1702 1520 1559 1648 1527
    ## [61853] 1550 1549 1646 1451 1705 1708 1619 1735 1625 1508 1713 1706 1715 1700
    ## [61867] 1528 1603 1715 1715 1556 1729 1707 1619 1533 1738 1529 1640 1720 1643
    ## [61881] 1625 1658 1810 1544 1749 1717 1743 1739 1630 1550 1552 1650 1743 1610
    ## [61895] 1629 1808 1753 1616 1622 1759 1936 1607 1646 1551 1827 1734 1635 1724
    ## [61909] 1643 1750 1803 1553 1750 1933 1707 1803 1752 1757 1807 1809 1739 1659
    ## [61923] 1826 1837 1807 1741 1654 1639 1638 1749 1744 1808 1827 1742 2019 1651
    ## [61937] 1838 1822 1742 1650 1730 1852 1826 1909 1917 1842 1801 1823 1655 1842
    ## [61951] 1737 1910 1843 1735 1659 1806 1920 1810 1645 1652 1719 1708 1857 1733
    ## [61965] 1805 1821 1740 1857 1738 1816 1834 1755 1800 1847 1923 1810 1925 1722
    ## [61979] 1733 1822 1759 1738 1710 1735 1825 1833 1913 1859 1725 1801 1856 1728
    ## [61993] 1824 1841 1903 1919 1900 1816 1834 1913 1743 1853 1825 1822 1755 1753
    ## [62007] 1841 1838 1835 1956 1808 1918 1802 1928 1735 1946 1952 1743 1931 1840
    ## [62021] 1817 1958 2003 2033 1931 1822 2004 2019 1805 1827 1940 1824 1837 1913
    ## [62035] 2004 1936 1846 2033 1844 2018 1956 1910 2022 1847 2000 1807 2046 1806
    ## [62049] 1858 1932 2015 2028 2010 1822 1948 2046 1952 1851 2036 2001 2042 1912
    ## [62063] 1850 1904 1934 1848 1839 1932 1940 2022 2027 2008 2015 2014 1939 2034
    ## [62077] 2026 2013 1916 2110 1946 1907 2059 2121 2123 2106 1925 1938 2031 2050
    ## [62091] 2033 2047 2103 2011 2058 1936 2059 2058 1914 1956 1944 2128 1945 1920
    ## [62105] 2059 2121 2036 2103 1933 2123 1945 2109 2116 2127 1918 2124 2025 2127
    ## [62119] 2027 2122 2143 2103 2122 2038 1956 1954 2031 2055 2052 2040 2126 2110
    ## [62133] 2014 1936 2047 2057 1946 2208 2016 2127 2123 2023 2145 2152 2133 2020
    ## [62147] 2041 2058 2158 2121 2034 2107 2207 2141 2055 2210 2156 2208 2023 2141
    ## [62161] 2205 2033 2200 2133 2013 2228 2238 2005 2147 2007 2005 2109 2032 2043
    ## [62175] 2241 2106 2056 2142 2212 2206 2205 2204 2224 2223 2039 2220 2202 2213
    ## [62189] 2110 2210 2028 2134 2115 2207 2041 2100 2239 2241 2156 2250 2234 2300
    ## [62203] 2301 2129 2143 2256 2242 2059 2213 2257 2128 2234 2226 2106 2120 2315
    ## [62217] 2115 2300 2241 2248 2136 2225 2151 2240 2127 2113 2121 2340 2210 2321
    ## [62231] 2329 2111 2130   44 2307 2259 2132 2114 2135 2127 2336 2205 2227 2219
    ## [62245] 2131 2214 2229 2134 2136 2335 2313 2256 2220 2235 2214 2340 2400 2231
    ## [62259] 2348 2143 2335 2201 2210   11 2241 2220   10 2329 2258 2314   14 2208
    ## [62273] 2205 2334   32   27   30 2218 2353 2345 2333 2315 2211 2254 2217 2212
    ## [62287] 2209 2239 2306 2243 2302 2223 2400 2338    1 2241   58 2229 2247 2340
    ## [62301] 2239    3 2300   25 2245   54 2232 2345    5 2351   26   18 2257   20
    ## [62315]   25 2307   47   14 2300 2302   59 2338   49  100 2353 2249 2340   13
    ## [62329]   18   55 2337    9 2337 2347 2326 2307 2325 2356 2347  113 2323  132
    ## [62343]   11    8    5    2   NA   41 2350   22  349   24   38  517  442  440
    ## [62357]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [62371]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA  654  809  839  843
    ## [62385]  648  648  810  808  716 1032  700  849  836  821  721  958  732  856
    ## [62399]  756  920  903  727  750  653  826  813  724  748  746  838  800  906
    ## [62413]  802  833  912  907  805  716  836  850  736  749  852  912  933  737
    ## [62427]  754  855  929  840  822  833  732  918  801  827  915  849  852  922
    ## [62441] 1022  836  749  923  917 1006  954  750  918  854  826  840  743  914
    ## [62455]  750 1129  848  809  829 1009  807  819  955  815  934  937  903 1002
    ## [62469] 1007  849  946  829 1210 1034 1003  844  958  845 1025  847  959 1036
    ## [62483]  946 1012  920  832 1000 1007  947 1029 1015  919 1035  929  919 1012
    ## [62497] 1023 1213 1103  918 1033 1017 1026 1044 1225 1040 1003 1106  958  958
    ## [62511]  936  913 1008 1050  911 1101  856 1044  957  849  951  929 1042  921
    ## [62525] 1028  941 1102 1113  900 1033 1041 1117 1042  916  908 1056 1030 1100
    ## [62539]  953 1054 1040 1053 1115  933  941 1131  951 1114 1115 1033 1131 1014
    ## [62553] 1057  958 1020 1015 1142 1038 1114  946 1022  932 1029  945 1133  955
    ## [62567] 1122 1047  939 1025  932 1104 1156 1041 1034 1342 1043  954 1016  940
    ## [62581] 1046 1132 1202 1048 1106 1142 1044 1144 1132 1157 1046 1236 1222 1148
    ## [62595] 1208 1210 1114 1010 1101 1029 1144 1336 1006 1216 1010 1025 1036 1253
    ## [62609] 1115 1200 1218 1135 1204 1057 1215 1031 1219 1020 1037 1052 1227 1216
    ## [62623] 1046 1236 1222 1231 1103 1147 1238 1239 1104 1043 1235 1236 1223 1145
    ## [62637] 1114 1110 1030 1221 1529 1052 1100 1239 1103 1144 1203 1247 1246 1429
    ## [62651] 1244 1141 1239 1550 1113 1235 1201 1141 1111 1348 1322 1215 1113 1254
    ## [62665] 1204 1245 1237 1234 1206 1116 1114 1307 1131 1140 1123 1226 1129 1319
    ## [62679] 1125 1140 1246 1317 1416 1208 1224 1211 1327 1117 1310 1303 1232 1322
    ## [62693] 1154 1406 1405 1350 1328 1311 1314 1150 1156 1245 1203 1423 1258 1220
    ## [62707] 1230 1237 1252 1234 1349 1329 1146 1331 1221 1417 1216 1238 1245 1203
    ## [62721] 1201 1400 1231 1240 1355 1341 1408 1422 1334 1329 1338 1313 1235 1257
    ## [62735] 1425 1455 1244 1423 1329 1420 1438 1257 1428 1429 1521 1333 1410 1259
    ## [62749] 1459 1413 1252 1418 1254 1248 1250 1325 1316 1444 1324 1533 1510 1312
    ## [62763] 1457 1427 1458 1353 1509 1402 1300 1507 1422 1353 1514 1435 1324 1312
    ## [62777] 1453 1402 1448 1515 1441 1313 1427 1525 1439 1340 1335 1323 1410 1422
    ## [62791] 1517 1558 1506 1504 1421 1357 1339 1604 1540 1534 1407 1414 1426 1438
    ## [62805] 1607 1356 1536 1354 1618 1441 1404 1601 1434 1440 1410 1521 1554 1353
    ## [62819] 1615 1529 1505 1502 1644 1549 1421 1506 1608 1605 1419 1538 1434 1509
    ## [62833] 1441 1633 1447 1428 1533 1501 1442 1610 1557 1457 1452 1548 1630 1442
    ## [62847] 1628 1638 1636 1631 1648 1545 1516 1518 1728 1658 1519 1636 1633 1445
    ## [62861] 1511 1523 1505 1458 1710 1612 1733 1643 1734 1542 1641 1533 1551 1705
    ## [62875] 1504 1545 1707 1557 1608 1625 1734 1646 1644 1552 1736 1609 1655 1652
    ## [62889] 1721 1617 1529 1724 1740 1552 1623 1650 1651 1618 1653 1732 1603 1749
    ## [62903] 1740 1746 1735 1736 1644 1603 1609 1554 1750 1647 1610 1712 1627 1821
    ## [62917] 1756 1917 1730 1602 1728 1758 1602 1811 1759 1656 1625 1940 1601 1647
    ## [62931] 1647 1745 1645 1622 1809 1708 1751 1814 1639 1701 1802 1745 1634 1743
    ## [62945] 1708 1758 1844 1819 1646 1835 1832 1800 1815 1856 1722 1717 1850 1657
    ## [62959] 1723 1811 1837 1707 1646 1636 1749 1827 1917 1828 1639 1848 1656 1718
    ## [62973] 1812 1935 1731 1706 1800 1755 1737 1900 1659 1657 1754 1711 1724 1728
    ## [62987] 1746 1839 2035 1654 1923 1850 1856 1753 1944 1758 1826 1705 1820 1713
    ## [63001] 1751 1850 1811 1815 1745 1730 1817 1837 1825 1910 1738 1837 1847 1848
    ## [63015] 1807 1818 1923 1745 1931 1926 1820 1827 1846 1844 1957 1815 1744 1807
    ## [63029] 2003 1936 1752 1948 1915 1919 1942 1919 1851 1810 1926 2007 1853 2002
    ## [63043] 1914 1801 1839 1759 1752 1811 1957 1829 1932 1808 1945 1849 1804 1948
    ## [63057] 1859 2011 1830 1915 2038 1937 2014 1821 2017 1931 1956 2024 1826 1806
    ## [63071] 1941 1822 1817 2055 1919 1956 1813 1943 2010 1908 1929 2025 1903 1901
    ## [63085] 1914 1901 2016 2004 1932 2001 2030 2030 1851 2057 2003 1909 1902 2030
    ## [63099] 2009 1921 2044 2000 1909 2052 2056 1836 1849 2104 1955 1949 2020 2017
    ## [63113] 2036 1859 1940 1931 2120 2009 1920 1934 2125 2104 2043 2016 2116 1904
    ## [63127] 2048 2035 2109 2044 2102 2044 1947 1945 1927 1959 1922 1951 2102 2121
    ## [63141] 2037 2056 1938 2134 2130 1924 2125 2031 2131 2204 1942 1938 2029 2139
    ## [63155] 1956 2032 2018 2158 2035 2114 1940 2031 2132 2145 2031 2148 2019 2058
    ## [63169] 2128 2134 2002 2042 2157 2204 2108 2206 2022 1937 2054 2038 2054 2225
    ## [63183] 2242 2156 2215 2112 2042 2150 2035 2144 2108 2046 2140 2027 2131 2027
    ## [63197] 2128 2057 2237 2144 2246 2215 2148 2039 2036 2156 2120 2228 2024 2029
    ## [63211] 2039 2124 2036 2135 2105 2241 2245 2055 2055 2127 2218 2135 2233 2047
    ## [63225] 2053 2213 2246 2219 2113 2144 2303 2202 2231 2109 2249 2256 2252 2249
    ## [63239]   18 2216 2044 2221   24 2154 2152 2101 2318 2232 2221 2107 2200 2225
    ## [63253] 2323 2305 2148 2242 2140 2315 2235 2138 2209 2124 2132 2137 2116 2156
    ## [63267] 2204 2244 2118 2323 2311 2257 2300 2136 2229 2304 2317 2341 2208 2226
    ## [63281] 2141 2156    6 2141 2222 2204    8 2216 2339 2259 2237 2250   10 2202
    ## [63295] 2343 2335 2217 2257 2334 2358 2304 2204 2214 2218 2339 2322 2258 2227
    ## [63309]   12 2247 2332 2321 2315  131    7 2203 2218 2252   11    2 2358 2206
    ## [63323] 2358   42 2222 2232 2250 2349   13   19    2 2308 2235 2246 2327 2252
    ## [63337] 2302 2319 2335 2327   23 2349 2344   53 2250   37 2334 2351  108 2341
    ## [63351] 2349 2345   17   16 2358   56   14  446  424  451   NA   NA   NA   NA
    ## [63365]   NA   NA  526  639  755  822  842  708  941  836  636  916  704  849
    ## [63379]  819  848  854 1025  736  835  905  846  740  758  714  801  735  914
    ## [63393]  856  925  739  806  859  933  848  822  849  928  852  804  756  928
    ## [63407]  846  745  930 1019  804  932  752  917  934  936  904  745 1007  817
    ## [63421]  921  914 1116  955  934 1026  825 1008 1028 1002 1011 1132  835  948
    ## [63435]  947 1008  954  852  929  910  905  948  857 1034  840 1053  957  944
    ## [63449] 1206  906 1053  907  935 1035 1030  856 1100 1028 1216 1024 1053 1013
    ## [63463]  941  945 1033  857  948  910  914 1045 1012 1111 1006  924 1054 1012
    ## [63477] 1231 1057 1041 1047 1040 1048 1117 1101 1107 1121 1140  937  934 1017
    ## [63491]  905  916 1019 1110 1036 1017 1036 1306 1019 1025  923 1031 1000 1153
    ## [63505] 1016 1003 1114 1028 1043  944 1003  956 1120 1006 1056 1155 1028  930
    ## [63519]  948  938 1109 1130 1115 1124 1209 1152 1044 1043  951 1157 1109 1338
    ## [63533]  955 1010 1143 1000 1021 1147 1040 1154 1142 1020 1220 1116 1118 1121
    ## [63547] 1034 1133 1209 1234 1224 1103 1024 1224 1032 1216 1046 1233 1235 1217
    ## [63561] 1152 1159 1409 1044 1150 1205 1217 1045 1210 1051 1109 1052 1240 1128
    ## [63575] 1100 1549 1217 1051 1105 1235 1241 1230 1155 1254 1105 1241 1116 1147
    ## [63589] 1203 1249 1156 1056 1221 1217 1221 1251 1102 1228 1126 1614 1319 1301
    ## [63603] 1116 1309 1435 1302 1121 1156 1327 1215 1234 1304 1305 1348 1116 1302
    ## [63617] 1333 1341 1151 1305 1307 1336 1313 1409 1228 1157 1254 1154 1324 1150
    ## [63631] 1219 1238 1241 1352 1226 1237 1406 1310 1359 1336 1249 1158 1401 1317
    ## [63645] 1312 1324 1209 1346 1414 1401 1319 1426 1243 1321 1432 1519 1252 1319
    ## [63659] 1244 1354 1352 1248 1358 1440 1440 1313 1432 1341 1240 1252 1414 1356
    ## [63673] 1441 1428 1422 1257 1456 1250 1415 1259 1445 1313 1357 1449 1513 1434
    ## [63687] 1502 1437 1345 1342 1455 1443 1406 1455 1341 1514 1343 1331 1532 1426
    ## [63701] 1338 1558 1530 1433 1403 1456 1512 1357 1601 1521 1427 1523 1501 1546
    ## [63715] 1628 1443 1609 1615 1559 1406 1604 1431 1428 1449 1615 1440 1534 1623
    ## [63729] 1634 1503 1618 1610 1626 1644 1657 1545 1700 1452 1617 1505 1621 1529
    ## [63743] 1636 1622 1600 1635 1536 1646 1619 1714 1448 1637 1530 1613 1650 1602
    ## [63757] 1546 1711 1553 1643 1725 1702 1630 1700 1645 1653 1618 1537 1700 1532
    ## [63771] 1534 1657 1726 1553 1735 1653 1731 1743 1809 1626 1748 1615 1650 1628
    ## [63785] 1812 1544 1616 1759 1635 1646 1613 1633 1719 1921 1806 1649 1552 1837
    ## [63799] 1706 1629 1609 1649 1739 1806 1741 1722 1739 1632 1840 1723 1738 1803
    ## [63813] 1702 1632 1759 1708 1720 1945 1702 1710 1643 1828 1811 1808 2007 1755
    ## [63827] 1649 1701 1843 1655 1839 1902 1649 1816 1824 1753 1653 1834 1711 1718
    ## [63841] 1714 1843 1804 1658 1900 2210 1732 1825 1848 1739 1808 1737 1844 1923
    ## [63855] 1750 1749 1825 1851 1820 1842 1906 1916 1847 1718 1809 1815 1828 1800
    ## [63869] 1751 1912 1856 1734 1724 1834 1746 1838 1857 1945 1741 1911 1728 1920
    ## [63883] 1753 1936 1847 1914 1934 1931 1909 1913 2005 1805 1926 1932 1929 1931
    ## [63897] 1919 2002 1756 1935 1800 1918 2014 1934 1844 1804 1934 1750 1932 1806
    ## [63911] 1845 1941 1840 1751 1757 1953 1920 1955 1946 1849 1812 1850 1951 1808
    ## [63925] 1959 1841 1841 2016 2008 1851 1843 1934 1945 2039 1901 1833 1901 1947
    ## [63939] 1855 1946 2003 1907 2034 2035 2006 2014 1839 2039 1948 2037 2101 1910
    ## [63953] 2026 2008 1859 1916 2025 2051 1931 2028 2021 2045 2103 2051 2006 1914
    ## [63967] 2135 2001 2057 2025 2109 2124 1926 2022 1958 1944 1922 2106 1954 2145
    ## [63981] 2124 2155 2145 2118 2048 2142 2124 2006 2035 2138 1951 2056 2043 2014
    ## [63995] 2147 2131 2146 2108 2025 2014 2236 2229 2026 2039 2119 2015 2238 2209
    ## [64009] 2154 2157 2210 2215 2204 2142 2223 2029 2224 2125 2252 2355 2154 2220
    ## [64023] 2232 2239 2127 2034 2205 2059 2149    7 2142 2221 2243 2239 2100 2202
    ## [64037] 2235 2228 2242 2112 2056 2145 2111 2327 2255 2247 2203 2341 2125 2301
    ## [64051] 2204    1   14 2336 2329 2309  108 2151 2326 2230 2318 2305 2343 2334
    ## [64065]   12 2247 2234   35   25 2249 2259 2332 2330 2341    5 2346   26 2355
    ## [64079]  417  456   NA  629  749  830  846  832  741  641  711  741 1021  802
    ## [64093]  924  820  707  834  839  853  913  754  709  801  844  833  917  818
    ## [64107]  800 1017  925  855  914  812  917  911  823  852  936  913  911  857
    ## [64121]  755  949  913  751 1122  823  839  949  945 1004 1000  835  932 1001
    ## [64135]  839 1134 1013  917  945 1005  941 1001  830 1021 1012  946  904 1059
    ## [64149]  820 1006  826  835 1009 1018 1034 1009  958 1203  927  913  955 1023
    ## [64163] 1048 1206 1119 1119  928  941  852  905  934 1055 1117  911  908 1035
    ## [64177]  927 1042 1034 1013  928 1052 1050 1013 1003 1040 1017 1044 1039 1119
    ## [64191] 1030 1105  935 1243 1021 1103 1122 1039  924 1047 1020 1033 1122 1105
    ## [64205] 1100 1102 1251 1007 1113 1117  925 1026  935  940 1028 1047  935 1018
    ## [64219] 1033 1033 1202 1049 1030 1104 1013  926  959 1129 1025 1105 1017 1138
    ## [64233] 1145 1216 1033 1221 1103  952 1056 1106 1320 1143 1011 1148 1018 1114
    ## [64247] 1156 1139 1148 1106 1001 1142 1209 1143 1056 1118 1122 1233 1201 1048
    ## [64261] 1016 1201 1215 1159 1210 1159 1025 1157 1218 1202 1048 1231 1050 1031
    ## [64275] 1204 1157 1231 1400 1227 1112 1024 1539 1220 1109 1047 1059 1215 1422
    ## [64289] 1056 1130 1238 1235 1119 1114 1214 1102 1151 1133 1233 1243 1049 1625
    ## [64303] 1254 1201 1314 1309 1201 1111 1209 1122 1140 1219 1237 1258 1332 1139
    ## [64317] 1223 1159 1308 1326 1114 1149 1327 1405 1401 1243 1316 1318 1312 1353
    ## [64331] 1403 1305 1207 1155 1207 1406 1310 1226 1200 1226 1349 1242 1345 1328
    ## [64345] 1251 1243 1407 1316 1309 1318 1201 1356 1219 1347 1318 1209 1238 1407
    ## [64359] 1359 1412 1409 1405 1452 1250 1344 1312 1254 1234 1358 1424 1311 1243
    ## [64373] 1431 1436 1404 1334 1256 1451 1306 1301 1356 1325 1241 1406 1425 1255
    ## [64387] 1508 1418 1439 1250 1356 1339 1515 1459 1315 1309 1258 1440 1516 1335
    ## [64401] 1445 1454 1258 1340 1442 1425 1446 1406 1424 1333 1455 1405 1521 1345
    ## [64415] 1539 1408 1317 1356 1336 1429 1459 1502 1405 1515 1532 1447 1441 1336
    ## [64429] 1418 1558 1542 1345 1400 1536 1548 1551 1408 1421 1528 1409 1449 1525
    ## [64443] 1511 1616 1601 1421 1524 1453 1421 1609 1431 1608 1551 1457 1407 1402
    ## [64457] 1440 1522 1636 1512 1609 1427 1529 1504 1604 1610 1444 1506 1542 1504
    ## [64471] 1508 1622 1620 1612 1500 1515 1632 1544 1640 1531 1633 1445 1711 1632
    ## [64485] 1513 1538 1540 1448 1629 1507 1637 1645 1653 1544 1507 1627 1724 1541
    ## [64499] 1654 1542 1545 1607 1549 1701 1545 1702 1508 1553 1552 1643 1644 1704
    ## [64513] 1631 1648 1724 1721 1701 1613 1544 1653 1745 1555 1653 1735 1709 1646
    ## [64527] 1620 1727 1558 1745 1701 1718 1642 1610 1800 1745 1741 1644 1713 1617
    ## [64541] 1705 1609 1739 1644 1639 1644 1653 1845 1725 1717 1928 1715 1740 1745
    ## [64555] 1816 1626 1710 1757 1724 1741 1836 1755 1807 1804 1708 1820 2005 1700
    ## [64569] 1642 1745 1631 1828 1648 1658 1809 1718 1716 1705 1807 1631 1639 1655
    ## [64583] 1708 1830 1825 1657 1903 1832 1717 1846 1643 1638 1900 1832 1754 1817
    ## [64597] 1828 1842 1708 1718 1702 1818 1754 1757 1755 1916 1758 1817 1728 1841
    ## [64611] 1919 1716 1922 1734 1818 1816 1737 1812 1800 1941 1850 1732 1902 1821
    ## [64625] 1744 1837 1909 1828 1914 1842 1823 1824 1811 1914 1856 1823 1810 1723
    ## [64639] 1850 1752 1909 1939 1821 1749 1845 1800 1920 1803 1853 1953 1815 1946
    ## [64653] 1756 1829 1942 1943 2117 1856 1918 2001 1948 1758 2015 1950 1921 1814
    ## [64667] 2008 1833 1752 1858 2021 1930 1809 1931 1848 1907 1839 1841 1846 1918
    ## [64681] 1845 1915 1900 1952 2011 1950 1825 1935 2023 1838 2025 2039 2016 1852
    ## [64695] 1849 1816 1809 1935 1919 1954 1937 2023 2005 1915 1922 1854 1926 2014
    ## [64709] 1959 2049 2007 2005 2007 1908 1936 2035 2027 2010 2050 2041 2016 2044
    ## [64723] 1917 2046 2043 1943 2026 1914 2042 2006 1926 1916 2054 1937 2039 2136
    ## [64737] 2036 1945 2049 2130 1926 2036 2103 2045 2048 2015 2020 2002 2149 1933
    ## [64751] 2109 1926 1921 2047 2104 2130 1932 2123 2149 2125 2047 2134 2035 2121
    ## [64765] 2136 2034 1946 2210 2121 2057 2152 2153 1957 2109 2024 2035 2110 2056
    ## [64779] 2149 2200 2047 2016 2016 1938 2029 2145 2125 2103 2218 2125 2052 2024
    ## [64793] 2211 2038 2035 2028 2027  144 2252 2208 2224 2053 2218 2200 2152 2247
    ## [64807] 2211 2047 2128 2109 2109 2205 2307 2053 2206 2204 2029 2050 2245 2127
    ## [64821] 2216 2226 2124 2226 2315 2201   23 2222 2152 2252 2136 2250 2332 2300
    ## [64835] 2334 2129 2118 2146 2118 2125 2139 2224 2047 2207 2220 2306 2302 2158
    ## [64849] 2233 2222 2102 2243 2253 2235 2141 2136 2258 2239 2139 2126 2215 2120
    ## [64863] 2146 2118 2259 2340  106 2333 2136 2226 2310 2138 2337 2220 2229 2353
    ## [64877] 2241   28 2305 2251 2251 2225 2304 2222 2237 2319 2318 2156 2400 2214
    ## [64891] 2159 2252 2152 2311 2206 2146 2157   43 2209 2151 2259 2221 2225 2334
    ## [64905] 2153 2252   15 2223 2359    5 2242 2314 2157    7  119 2205 2233    7
    ## [64919] 2301 2318 2344 2217 2334 2331 2324 2357   27 2356 2311 2256 2252 2244
    ## [64933] 2340    2 2359 2250 2326 2259 2313   21 2329 2250 2249   19 2245 2301
    ## [64947]   14 2325 2248    5   17 2309   14 2343 2358 2343 2347  115  140    9
    ## [64961]    4 2354 2349    8 2352 2357    1  143   34  204   33  420  422   NA
    ## [64975]   NA   NA  631  759  852  851  809  749  754  838  720  709  635  812
    ## [64989]  903  743  846  841 1029  849  720  704  738  743  843  718  907  710
    ## [65003]  830  729  816  817  849  848  927  747  759  733  802  828  738  720
    ## [65017]  806  912  849  807  830  845  751  926  746  918  829  734  740  901
    ## [65031]  817  918  829  755  843  924  906  922  747  806  845  922  901  857
    ## [65045]  853  913  914  754 1018  913 1124 1013  946  747  933  803  938  820
    ## [65059]  931  951  919  942  824  817 1024 1000  948  849 1138  834 1016  948
    ## [65073] 1018 1024  953 1017 1019 1000  921  832  915  852  930  832  929  902
    ## [65087]  952 1004  838  908 1016 1012 1021 1044 1021 1040  906 1014  847  908
    ## [65101]  911 1041 1047 1008 1034 1215  851 1100  929 1219  913  939  947 1007
    ## [65115]  859 1031 1035 1054  950 1055 1016  841 1008 1048 1118  920 1034 1031
    ## [65129] 1045 1049  931 1023  919  929  906 1112  944 1046  942 1055 1007 1048
    ## [65143] 1045  929 1104 1031 1022 1053 1021 1103 1247 1022  958 1007  941 1111
    ## [65157] 1022 1122 1133 1108  929  942  930 1028  948  915 1038 1023 1109 1141
    ## [65171] 1018  919 1048 1027  957  934 1103 1039 1027 1103 1136 1029 1014 1053
    ## [65185] 1139 1128 1200 1105 1027 1203 1127 1012 1026 1009 1335 1116 1006 1136
    ## [65199]  958 1145 1128 1005 1202 1145 1001 1146 1145 1228 1035 1027 1056 1149
    ## [65213] 1200 1153 1050 1120 1007 1216 1011 1102 1134 1152 1125 1236 1112 1209
    ## [65227] 1200 1140 1241 1231 1141 1217 1213 1154 1150 1225 1116 1202 1216 1230
    ## [65241] 1027 1107 1035 1127 1053 1518 1416 1254 1238 1210 1240 1121 1231 1113
    ## [65255] 1120 1109 1220 1057 1059 1158 1214 1304 1245 1230 1156 1627 1341 1126
    ## [65269] 1127 1242 1238 1229 1128 1306 1138 1317 1123 1130 1315 1210 1300 1121
    ## [65283] 1305 1200 1145 1114 1237 1351 1157 1309 1238 1147 1344 1340 1244 1314
    ## [65297] 1312 1347 1159 1255 1324 1255 1246 1242 1203 1330 1158 1142 1230 1335
    ## [65311] 1246 1322 1350 1237 1427 1258 1201 1224 1402 1227 1401 1332 1330 1225
    ## [65325] 1313 1315 1349 1410 1410 1237 1357 1219 1251 1323 1334 1402 1404 1337
    ## [65339] 1238 1443 1400 1248 1421 1323 1245 1352 1433 1421 1258 1359 1353 1456
    ## [65353] 1244 1306 1315 1252 1430 1443 1412 1242 1427 1343 1325 1516 1442 1345
    ## [65367] 1402 1340 1305 1507 1305 1444 1510 1449 1440 1416 1339 1346 1454 1428
    ## [65381] 1313 1451 1404 1359 1524 1512 1340 1336 1457 1336 1422 1455 1326 1404
    ## [65395] 1506 1404 1545 1543 1351 1504 1335 1535 1338 1530 1423 1523 1403 1530
    ## [65409] 1500 1358 1537 1502 1604 1522 1437 1443 1553 1555 1436 1527 1407 1419
    ## [65423] 1432 1458 1556 1429 1457 1412 1615 1615 1503 1602 1409 1558 1431 1605
    ## [65437] 1457 1534 1621 1517 1517 1540 1511 1509 1448 1618 1623 1431 1618 1635
    ## [65451] 1607 1621 1512 1637 1539 1440 1617 1513 1646 1649 1540 1537 1628 1544
    ## [65465] 1451 1448 1534 1632 1620 1543 1605 1643 1455 1535 1533 1645 1719 1643
    ## [65479] 1724 1626 1709 1542 1653 1633 1644 1649 1700 1702 1650 1719 1615 1645
    ## [65493] 1654 1654 1632 1548 1544 1614 1631 1637 1739 1655 1743 1634 1553 1728
    ## [65507] 1614 1604 1648 1643 1915 1638 1614 1742 1728 1922 1735 1600 1729 1558
    ## [65521] 1644 1759 1825 1700 1800 1715 1748 1746 1756 1647 1608 1745 1808 1717
    ## [65535] 1743 1740 1731 1727 1623 1713 1843 1639 1634 1755 1731 1956 1810 1724
    ## [65549] 1748 1813 1805 1819 1804 1714 1718 1716 1847 1824 1828 1702 1851 1813
    ## [65563] 1648 1847 1710 1819 1742 1630 1653 1650 1846 1843 1734 1849 1749 1710
    ## [65577] 1750 1654 1804 1756 1805 1759 1757 1844 1831 1843 1703 1900 1818 1754
    ## [65591] 1758 1833 1719 1847 1911 1828 1807 1756 1850 1811 1843 1804 1836 1828
    ## [65605] 1758 1932 1728 1808 1735 1814 1852 1847 1901 1840 1843 1924 1739 1909
    ## [65619] 1831 1757 1923 1744 1908 1726 1839 1833 1914 1836 1920 1746 1915 1902
    ## [65633] 1935 1935 1758 1746 1928 1919 1939 1742 1957 1826 1834 1910 1846 1857
    ## [65647] 2005 1810 1827 1750 1820 1925 1933 1910 1753 1907 1929 1752 1950 2018
    ## [65661] 2036 1806 1937 2002 1935 1936 1851 1927 1817 1941 1953 2025 1803 2019
    ## [65675] 1803 2006 2011 1813 1855 1930 2017 1825 1835 1855 2014 1858 1924 1845
    ## [65689] 2046 2014 1950 1912 1951 1925 1828 2029 1901 1943 2030 1919 1856 2001
    ## [65703] 2011 1959 2106 1946 2058 1929 2010 1911 2001 2029 1840 1845 1942 2048
    ## [65717] 1909    5 2000 1924 2035 2035 1936 2015 2057 2030 1904 1856 1948 2027
    ## [65731] 1930 2109 2046 2021 2103 1959 1943 2057 2109 2024 1929 1949 2140 1939
    ## [65745] 2112 2012 2046 2103 2032 2121 2039 2113 2117 2007 2122 2002 2046 1954
    ## [65759] 2049 2108 1926 1951 2115 2112 2036 2109 2145 2209 2154 2045 2141 2054
    ## [65773] 2102 1946 2141 2020 2215 2137 2128 2028 2038 2128 2014 2155 2218 2300
    ## [65787] 2150 2021 2146 2104 2053 2044 2124 2033 2159 1953 2221 2007 2200 2122
    ## [65801] 2056 2151 2138 2100 2022 2201 2018 2209 2221 2124 2246 2124 2025 2154
    ## [65815] 2158 2144 2159 2033 2123 2119 2203 2216 2237 2149 2225 2219 2154 2122
    ## [65829] 2144 2108 2036 2244 2114 2315 2052 2125 2221 2228 2144 2131 2152 2115
    ## [65843] 2035   35 2201 2240 2225 2245 2153 2259 2047 2051 2228 2216 2106 2230
    ## [65857] 2100 2241 2247 2245 2308 2152 2235 2123 2319 2227 2254 2300 2311 2312
    ## [65871] 2137 2330 2308 2124 2200 2322 2130 2143 2238 2159 2222 2312 2251 2146
    ## [65885] 2331 2139 2327 2212 2237 2342 2234 2311 2339  112 2203 2220 2335 2346
    ## [65899]    7 2202 2204 2157 2210 2319 2311 2332 2315 2251 2230 2212 2234 2313
    ## [65913] 2249   11 2218 2339 2334 2241 2212 2204 2352 2243 2358   48   16    5
    ## [65927] 2232   28    7 2245 2251 2242 2306   48   32 2328 2252 2329 2349 2318
    ## [65941] 2259 2252 2316 2307 2318 2321 2340 2315 2357 2355 2346 2357    5  428
    ## [65955]  443  420   NA   NA   NA  639  803  818  828  700  841  643  854  728
    ## [65969]  721  836  822  751  753  657 1024  833  835  715  649  852  910  835
    ## [65983]  855  735  724  908  901  830  731  807  806  756  927  802  832  813
    ## [65997]  936  925  902  750  715  821  734  906  912  932  903  815  920  919
    ## [66011]  929  805  841  733  825  811  850  943  817  846  809  850  937  816
    ## [66025]  917  815  951  843  933  913  847  830  841 1005  740  823  945 1115
    ## [66039]  820  959  841  926  848  855 1010  806  933  948  901  819 1001  917
    ## [66053]  942  941  919 1028 1143 1005  847 1008 1011  953  854  851 1019 1021
    ## [66067]  944  918  856 1015  952  823 1016 1042 1048 1203 1124  903  936  941
    ## [66081] 1038  840 1036  941 1039 1042 1039 1057 1028 1057  923 1017 1051  853
    ## [66095] 1104 1007 1026  942  956 1043  915 1113 1058  909 1008 1135 1057 1021
    ## [66109] 1122 1001 1102  917 1052 1111 1115  938 1107 1020 1123 1125 1303 1139
    ## [66123] 1022 1036 1004 1030 1213  941 1119 1055 1034 1117 1000 1023 1114 1059
    ## [66137] 1330 1157 1126 1028 1215 1156 1101 1034 1018 1004  916 1029 1035 1020
    ## [66151] 1114 1041 1217 1035 1123  936 1224 1127 1046 1047 1147 1120 1223 1148
    ## [66165] 1223 1141 1034 1216 1044 1203 1027 1251 1240 1142 1143 1226 1315 1158
    ## [66179] 1031 1236 1237 1221 1243 1103 1209 1056 1251 1205 1121 1152 1243 1109
    ## [66193] 1203 1025 1217 1323 1242 1204 1100 1233 1020 1234 1234 1129 1210 1210
    ## [66207] 1237 1256 1205 1422 1258 1238 1351 1100 1049 1309 1227 1120 1125 1630
    ## [66221] 1315 1215 1215 1439 1321 1134 1236 1239 1302 1300 1634 1348 1303 1300
    ## [66235] 1208 1235 1230 1133 1310 1205 1142 1228 1315 1126 1146 1221 1252 1147
    ## [66249] 1224 1312 1318 1242 1132 1245 1335 1209 1114 1232 1239 1230 1215 1248
    ## [66263] 1159 1225 1353 1354 1327 1400 1207 1335 1304 1221 1411 1326 1415 1224
    ## [66277] 1348 1342 1143 1236 1221 1258 1318 1221 1319 1350 1344 1157 1241 1236
    ## [66291] 1246 1346 1243 1337 1356 1439 1413 1407 1403 1346 1452 1334 1336 1332
    ## [66305] 1306 1232 1330 1509 1305 1303 1347 1433 1254 1504 1254 1401 1254 1404
    ## [66319] 1507 1438 1303 1348 1446 1515 1408 1352 1409 1506 1330 1511 1417 1259
    ## [66333] 1403 1245 1446 1339 1500 1503 1315 1411 1350 1530 1312 1325 1427 1516
    ## [66347] 1317 1315 1447 1508 1512 1343 1324 1510 1518 1409 1403 1321 1426 1406
    ## [66361] 1427 1542 1417 1439 1531 1528 1346 1335 1542 1458 1552 1558 1549 1545
    ## [66375] 1503 1550 1421 1415 1511 1556 1404 1505 1358 1412 1453 1347 1532 1514
    ## [66389] 1625 1551 1534 1618 1602 1442 1558 1502 1451 1443 1621 1504 1435 1412
    ## [66403] 1537 1506 1520 1600 1627 1937 1444 1435 1553 1701 1505 1544 1517 1717
    ## [66417] 1458 1700 1617 1645 1525 1548 1700 1554 1617 1653 1657 1655 1556 1457
    ## [66431] 1705 1520 1617 1722 1622 1638 1555 1507 1512 1704 1641 1652 1558 1507
    ## [66445] 1657 1617 1541 1709 1553 1701 1557 1558 1741 1543 1709 1525 1628 1632
    ## [66459] 1727 1633 1733 1728 1634 1618 1707 1659 1624 1549 1738 1757 1653 1742
    ## [66473] 1727 1651 1637 1813 1611 1627 1545 1644 1608 1730 1736 1724 1634 1709
    ## [66487] 1619 1806 1823 1547 1714 1758 2002 1633 1624 1808 1748 1615 1652 1819
    ## [66501] 1810 1805 1752 1813 1622 1808 1703 1807 1824 1626 1823 1722 1719 1731
    ## [66515] 1744 1757 1842 1639 1819 1818 1627 1658 1718 1719 1822 1959 1632 1807
    ## [66529] 1643 1810 1813 1625 1854 1837 1840 1836 1839 1826 1654 1748 1840 1708
    ## [66543] 1709 1900 1908 1829 1826 1715 1652 1714 1806 1822 1901 1728 1904 1655
    ## [66557] 1655 1801 1726 1741 1859 1719 1731 1859 1716 1803 1901 1828 1749 1728
    ## [66571] 1937 1907 1837 1752 1856 1814 1946 1736 1913 1824 1817 1909 1816 1807
    ## [66585] 1855 2004 1857 1917 1917 1819 1834 1958 1838 1942 1922 1822 1927 1932
    ## [66599] 1814 1923 1754 1837 1827 1758 1816 1903 1810 1945 1906 1948 1953 2024
    ## [66613] 2007 1933 1932 1843 1838 1849 1942 2003 1845 1918 1854 1931 2026 1937
    ## [66627] 1823 1808 1901 1904 2003 2011 1848 2011 2021 1809 2007 1906 1830 1855
    ## [66641] 2007 2028 1814 1812 1805 1951 1830 2005 1845 1945 1959 1946 1956 1900
    ## [66655] 1811 1817 1904 2021 1953 2016 1854 1937 2033 2158 2004 1947 2020 2006
    ## [66669] 2011 1909 1932 2023 2020 1926 2032 1947 2031 1903 2032 2053 2041 2006
    ## [66683] 2051 1904 1947 1851 1952 1944 2038 2022 2054 1958 2057 1956 2034 1942
    ## [66697] 1916 2034 2020 2103 2139 2050 1930 2028 1943 2125 1948 2046 2029 1942
    ## [66711] 2048 1936 2000 1936 2049 1936 1936 2108 2056 2024 2126 2123 2112 2153
    ## [66725] 2058 2038 2010 2118 2216 2018 2045 2140 1931 2135 2145 2050 2123 2103
    ## [66739] 1935 2107 2034 2126 2116 2048 2047 2008 2036 2012 2027 2235 2200 2147
    ## [66753] 2208 2134 2003 2133 2026 2026 2140 2153 2122 2253 1943 2126 2040 2204
    ## [66767] 2202 2200 2135 2050 2019 2139 2121 2201 2207 2227 2010 2122 2150 2025
    ## [66781] 2212 2206 2129 2133 2240 2104 2201 2202 2047 2140 2121 2232 2218 2256
    ## [66795] 2147 2256 2158 2132 2222 2130 2140 2237 2324 2245 2216 2131 2105 2319
    ## [66809] 2251   16 2201 2127 2122 2121 2151 2221 2201 2152 2154 2049 2230 2236
    ## [66823] 2201 2146 2205 2157 2149 2148 2119 2221 2146 2307 2306 2143 2106 2249
    ## [66837] 2141 2208 2220 2111 2153 2122 2307 2244 2305 2318 2127 2307 2147 2125
    ## [66851] 2324 2155 2223 2147   58 2132 2202 2326 2316 2230 2347 2307 2343 2241
    ## [66865] 2349 2143 2352 2147 2233 2158 2344 2329 2226 2206 2227    6 2225 2332
    ## [66879] 2303 2206 2304 2302    6 2349 2320 2224 2356 2342   25   20 2324 2316
    ## [66893] 2231 2315 2226 2239 2335 2245   19   13 2348   39 2302 2322 2245 2322
    ## [66907] 2314   51 2324 2336   44   34 2341   11 2356 2347  131 2350   12   24
    ## [66921]  424  439  429   NA   NA   NA   NA   NA   NA   NA   NA   NA  442  632
    ## [66935]  809  817  831  638  729  717  805  806  650  746  846  847  733  659
    ## [66949]  859  850  709  707 1040  847  825  711  709  808  748  731  744  837
    ## [66963]  741  758  800  847  855  906  757  857  713  718  758  818  725  747
    ## [66977]  904  902  855  824  913  903  915  917  851  747  740  832  731  827
    ## [66991]  732  739  747  926  845  749  840  758  826  751  829  917  919  749
    ## [67005]  803  830  746  910  926 1135  753  823  915  954  836  819  801 1006
    ## [67019]  952 1009  947  935  949  820  945  932 1001 1149  817  846  958  842
    ## [67033] 1000  850 1009  843  946  914  948 1006  828  914  954  949 1014 1218
    ## [67047] 1023 1039  840 1026  856  904  855  920 1026  905  942 1030 1021 1026
    ## [67061] 1235  854  926 1005 1031  914  902  925 1034 1011 1011 1013 1101  853
    ## [67075]  948  857  916 1048  924 1051   NA 1032  859  858  915 1023 1046 1039
    ## [67089] 1051  937 1104 1039 1110 1104 1007  925  923 1117 1055 1025 1105 1020
    ## [67103] 1016  946 1022 1046 1336 1009 1037 1003 1026  946  929 1119 1122  942
    ## [67117] 1146 1024  927 1048 1023  955 1034 1019 1037  951  950 1019 1025 1117
    ## [67131]  943 1012 1139 1146 1130 1013 1112 1034 1143 1054 1048 1156 1013 1045
    ## [67145] 1024 1148 1018 1128 1345 1035 1017 1029 1011 1026 1014 1030 1149 1220
    ## [67159] 1158 1217 1154 1149 1158 1055 1223 1111 1140 1202 1209 1158 1036 1046
    ## [67173] 1144 1135 1232 1227 1207 1035 1142 1154 1213 1145 1122 1108 1218 1227
    ## [67187] 1220 1202 1246 1201 1245 1047 1051 1158 1111 1125 1107 1437 1234 1238
    ## [67201] 1157 1253 1232 1133 1219 1150 1108 1140 1140 1123 1110 1115 1208 1315
    ## [67215] 1247 1124 1231 1222 1213 1203 1130 1200 1301 1219 1550 1303 1144 1251
    ## [67229] 1245 1159 1206 1116 1339 1242 1153 1120 1305 1324 1200 1154 1225 1251
    ## [67243] 1259 1245 1316 1325 1307 1227 1130 1334 1155 1330 1137 1237 1250 1202
    ## [67257] 1208 1231 1218 1413 1235 1351 1240 1250 1607 1214 1349 1330 1215 1350
    ## [67271] 1311 1337 1209 1210 1415 1240 1228 1353 1308 1438 1308 1246 1254 1358
    ## [67285] 1324 1400 1229 1246 1418 1327 1253 1304 1317 1424 1259 1429 1239 1421
    ## [67299] 1340 1245 1257 1338 1358 1406 1305 1332 1247 1434 1419 1327 1302 1253
    ## [67313] 1340 1339 1321 1414 1403 1303 1449 1309 1423 1413 1459 1300 1451 1442
    ## [67327] 1319 1302 1321 1502 1433 1433 1444 1451 1354 1334 1400 1332 1348 1329
    ## [67341] 1420 1326 1456 1351 1520 1345 1434 1332 1348 1428 1536 1529 1340 1448
    ## [67355] 1528 1451 1347 1358 1400 1359 1533 1446 1504 1444 1419 1521 1512 1451
    ## [67369] 1543 1526 1515 1438 1532 1458 1612 1415 1544 1605 1453 1603 1609 1452
    ## [67383] 1417 1437 1440 1444 1510 1503 1607 1447 1440 1435 1621 1458 1621 1501
    ## [67397] 1634 1543 1619 1448 1509 1446 1628 1447 1647 1516 1540 1508 1619 1530
    ## [67411] 1517 1640 1627 1655 1508 1649 1607 1453 1520 1540 1504 1649 1620 1629
    ## [67425] 1645 1634 1540 1641 1656 1634 1543 1611 1659 1610 1604 1532 1532 1548
    ## [67439] 1603 1552 1520 1553 1638 1620 1639 1711 1724 1625 1555 1741 1731 1723
    ## [67453] 1630 1630 1724 1629 1742 1612 1618 1754 1605 1652 1742 1655 1603 1943
    ## [67467] 1633 1720 1647 1719 1941 1604 1655 1647 1708 1701 1604 1807 1742 1622
    ## [67481] 1741 1817 1755 1716 1701 1638 1631 1650 1849 1811 1734 1626 1706 1752
    ## [67495] 1740 1730 1757 1643 2019 1652 1714 1756 1612 1725 1656 1720 1855 1627
    ## [67509] 1810 1714 1828 1836 1651 1817 1848 1736 1805 1836 1706 1726 1711 1817
    ## [67523] 1718 1727 1738 1708 1756 1811 1828 1729 1732 1750 1845 1700 1742 1901
    ## [67537] 1914 1711 1652 1734 1745 1737 1759 1854 1914 1736 1901 1843 1718 1751
    ## [67551] 1736 1811 1736 1812 1754 1906 1916 1714 1757 1852 1736 1905 1859 1802
    ## [67565] 1820 1734 1811 1857 1929 1806 1900 1852 1833 2007 1731 1748 1752 1826
    ## [67579] 1750 1849 1917 1817 1910 1905 1742 1933 1923 1902 1904 1909 1817 1759
    ## [67593] 1910 1940 1832 1939 1915 1943 1855 1827 1857 1922 1800 1901 1926 1839
    ## [67607] 1844 1921 1814 1902 1852 1930 2012 2011 1933 1803 1835 2017 1833 2002
    ## [67621] 1942 1820 1851 1847 2003 1947 1837 1825 1915 1908 1852 1847 1945 1929
    ## [67635] 1834 1948 1811 1911 2006 1926 1859 1819 1837 2000 1845 1948 1953 1943
    ## [67649] 1840 2002 2020 1928 1956 1916 1907 2002 1854 2029 2025 2005 1901 2019
    ## [67663] 2001 2037 1840 1925 2019 1924 1854 2046 2120 2018 2023 1850 1947 2009
    ## [67677] 1928 1947 2014 2041 2115 1959 2037 2035 1958 2039 2058 1942 2052 1934
    ## [67691] 1915 2102 2030 2033 2047 2046 1927 2127 2036 1958 2029 2102 1956 2032
    ## [67705] 2027 2041 1953 2059 2118 2111 2015 2119 2004 2009 2006 2156 2127 2017
    ## [67719] 2120 2127 2119 1935 2200 2130 2056 2114 1949 2031 2027 2127 1951 2007
    ## [67733] 2145 2217 2038 2008 2110 2144 2224 2046 2200 2039 2142 2018 2038 2152
    ## [67747] 2048 2108 2152 2132 2253 2012 2023 2041 2146 2201 2021 2058 2148 2128
    ## [67761] 2140 2039 2006 2136 2102 2135 2217 2037 2158 2106 2031 2057 2155 2118
    ## [67775] 2124 2135 2217 2355 2121 2047 2046 2114 2225 2128 2200 2200 2138 2123
    ## [67789] 2116 2230 2121 2223 2057 2210 2103 2139 2241 2057 2141 2217   23 2054
    ## [67803] 2138 2237 2243 2058 2123 2131 2254 2100 2122 2037 2202 2147 2109 2137
    ## [67817] 2205 2240 2107 2102 2152 2123 2301 2205 2124 2255 2238 2247 2203 2145
    ## [67831] 2305 2133 2145 2128 2136 2251 2308 2309 2145 2208 2337 2225 2212 2256
    ## [67845] 2327 2331 2314 2243 2322 2320 2304 2159 2202 2256 2203 2304 2158 2313
    ## [67859] 2338 2254 2228 2338 2233 2320 2300 2253 2246 2217 2338 2213 2220 2223
    ## [67873] 2231    8 2225 2301 2230   22 2358 2323 2243  203   23 2235    8   18
    ## [67887] 2251   29 2308 2240 2258 2355 2314 2255   24   14 2356 2351 2350 2345
    ## [67901] 2341 2341 2356 2355  127  450  439   NA  625  756  811  833  702  749
    ## [67915] 1023  647  650  912  742  706  646  723  741  716  820  840  843  714
    ## [67929]  818  725  823  650  810  833  752  926  807  852  755  731  747  813
    ## [67943]  921  723  856  804  733  740  943  825  827  914  902  901  829  748
    ## [67957]  749  850  912  924  746  801  735  855  845  824  810  957  914  903
    ## [67971]  750  819  853  806  855  822  940  747  811  848  908  945  832  929
    ## [67985]  751  823 1126  804 1005  906 1036 1010  936  933 1015  816  905  858
    ## [67999] 1211  959 1037  825  845 1016 1005  832 1007 1012 1012  841 1007  917
    ## [68013]  950  956  942  918  858  823 1013 1034 1008 1216 1053  827  841 1008
    ## [68027]  920 1032 1008 1021 1047  900 1026 1020  907  950 1041  858 1037 1216
    ## [68041]  850  914  918 1025 1047  905  919 1022  946  850  955  945  859 1036
    ## [68055]  918  920  916 1108 1022 1034 1049  859 1017  951 1109 1047 1100  951
    ## [68069]  918 1110 1043  947 1048 1102 1045 1040  947  944 1019 1050 1033  959
    ## [68083] 1025 1129 1059 1303 1015  921 1057 1008 1016  924 1032 1024  939 1001
    ## [68097]  932  955 1023  959  940 1126 1020 1033  936 1030 1141  949 1103  955
    ## [68111] 1008 1115 1020 1136 1112 1047 1015 1101 1125 1202 1150 1046 1203 1104
    ## [68125] 1138  956 1327 1003 1001 1149 1153 1001 1152 1140 1013 1008 1155 1120
    ## [68139] 1116 1139 1116 1022 1152 1158 1019 1049 1156 1049 1240 1045 1116 1155
    ## [68153] 1059 1154 1141 1127 1207 1207 1016 1213 1213 1155 1147 1216 1237 1106
    ## [68167] 1225 1123 1029 1217 1419 1220 1206 1051 1100 1523 1412 1143 1238 1215
    ## [68181] 1117 1105 1256 1240 1249 1049 1256 1058 1323 1159 1128 1230 1226 1257
    ## [68195] 1117 1116 1222 1222 1103 1237 1154 1222 1255 1203 1152 1131 1131 1121
    ## [68209] 1201 1145 1128 1312 1311 1115 1202 1358 1228 1307 1343 1153 1121 1242
    ## [68223] 1136 1303 1311 1243 1133 1311 1348 1314 1357 1202 1352 1147 1218 1238
    ## [68237] 1226 1246 1232 1417 1331 1159 1254 1304 1352 1226 1314 1218 1354 1220
    ## [68251] 1358 1159 1212 1220 1226 1353 1325 1410 1357 1350 1407 1245 1414 1301
    ## [68265] 1443 1436 1239 1228 1326 1252 1321 1427 1306 1332 1404 1334 1359 1414
    ## [68279] 1440 1258 1410 1245 1417 1253 1447 1258 1309 1250 1322 1358 1259 1352
    ## [68293] 1504 1500 1455 1432 1450 1332 1333 1306 1500 1507 1520 1310 1438 1333
    ## [68307] 1309 1432 1450 1415 1320 1419 1355 1430 1510 1343 1355 1447 1514 1500
    ## [68321] 1322 1326 1408 1521 1426 1410 1519 1350 1436 1342 1553 1521 1346 1436
    ## [68335] 1551 1402 1358 1422 1410 1348 1558 1534 1555 1605 1411 1517 1435 1410
    ## [68349] 1520 1543 1624 1405 1416 1524 1449 1553 1603 1553 1416 1548 1632 1448
    ## [68363] 1506 1453 1605 1646 1443 1517 1445 1506 1441 1609 1633 1550 1612 1615
    ## [68377] 1450 1632 1506 1519 1441 1623 1538 1529 1518 1702 1620 1635 1512 1507
    ## [68391] 1510 1646 1637 1536 1651 1642 1531 1628 1518 1452 1453 1454 1514 1628
    ## [68405] 1716 1647 1501 1649 1613 1508 1538 1534 1730 1540 1628 1616 1647 1622
    ## [68419] 1724 1529 1703 1624 1653 1701 1611 1724 1559 1749 1537 1729 1621 1713
    ## [68433] 1748 1708 1641 1555 1727 1607 1637 1644 1742 1732 1633 1745 1622 1617
    ## [68447] 1758 1713 1557 1705 1607 1602 1754 1942 1745 1728 1645 1710 1748 1808
    ## [68461] 1641 1646 1617 1808 1711 1603 1741 1649 1717 1759 1726 1819 1959 1755
    ## [68475] 1619 1748 1712 1723 1746 2007 1631 1615 1720 1643 1830 1818 1620 1645
    ## [68489] 1710 1844 1741 1759 1714 1638 1836 1627 1713 1809 1811 1835 1900 1755
    ## [68503] 1853 1715 1719 1659 1824 1747 1736 1845 1744 1753 1706 1655 1845 1850
    ## [68517] 1758 1733 1752 1750 1752 1850 1845 1701 1854 1811 1703 1718 1848 1732
    ## [68531] 1734 1757 1914 1718 1736 1748 1910 1856 1843 1735 1841 1841 1805 1814
    ## [68545] 1805 1840 1830 1848 1721 1838 1816 1912 1820 1737 1722 1914 1750 1927
    ## [68559] 1942 1926 1926 1906 1957 1824 1920 1750 1904 1929 1739 1929 1917 1753
    ## [68573] 1746 1919 2006 1856 1757 1748 1744 1812 1830 2016 1810 1744 2001 1912
    ## [68587] 1815 1838 1830 1942 1854 1812 1800 1853 1950 2027 1939 1839 1915 1838
    ## [68601] 1810 1828 1917 1821 2008 1946 1943 2001 2007 2008 1853   NA 1946 1820
    ## [68615] 1834 1826 1958 1920 2015 1847 1846 1918 1943 1925 2017 2039 1908 1835
    ## [68629] 2046 1939 2019 1854 2001 2105 2043 1914 2033 1949 1944 1936 2104 2025
    ## [68643] 1915 1841 1912 2028   19 1919 2101 1935 1851 1918 2007 2019 1905 2009
    ## [68657] 2035 2039 2046 2052 2034 2053 2039 1856 2052 2037 2022 1936 1917 2025
    ## [68671] 2051 2051 2104 2000 2140 1936 2055   NA 2123 1943 1953 2033 2009 2141
    ## [68685] 2132 2014 2132 2122 2000 2012 1938 2031 2214 2034 2059 2034 2034 2138
    ## [68699] 1954 1919 2037 2157 2143 2115 2106 2127 2005 2226 2137 2057 2115 2103
    ## [68713] 2017 2158 2054 2051 2003 2133 2008 1957 2136 2222 2156 2101 2228 2156
    ## [68727] 2154 2030 2104 2006 2152 2039 2022 2207 2124 2228 2043 2218 2156 2012
    ## [68741] 2040 2039 2033 2152 2044 2139 2008 2206 2220 2030 2045 2229 2116 2110
    ## [68755] 2148 2031 2143 2136 2123 2236 2227 2400 2045 2149 2250 2158 2134 2210
    ## [68769] 2221 2229 2212 2309 2136 2105 2237 2146 2130 2304 2244 2315 2232 2100
    ## [68783] 2114 2204 2234 2106 2243 2127   20 2206 2052 2152 2132 2155 2104 2155
    ## [68797] 2212 2217 2056 2132 2234 2231 2243 2129 2053 2247 2122 2109 2312 2218
    ## [68811] 2300 2307 2143 2144 2247 2335 2348 2355 2306 2240 2328 2137 2301 2156
    ## [68825] 2202 2224 2206   14 2159 2342 2334 2345 2257 2200 2326 2200 2153 2339
    ## [68839] 2157 2154 2344 2319 2152 2231 2205 2157 2311 2221 2233 2203 2225 2311
    ## [68853] 2303 2352 2316 2348 2217 2252 2219 2306 2216   42   17 2332    3 2237
    ## [68867] 2240   11 2346 2327   36 2249 2233   18 2257 2250 2304 2311 2254 2313
    ## [68881] 2310 2339 2255   30 2338 2345    4 2349 2350 2357  124  425  425  428
    ## [68895]   NA   NA  438  634  819  829  838  719  646  735  637  723  728  738
    ## [68909]  842  850  651  915  741  849  705  703 1019  743  813  918  858  848
    ## [68923]  717  926  841  750  739  819  757  732  856  806  931  756  916  741
    ## [68937]  731  737  910  912  858  747  820  823  747  930  915  740  816  942
    ## [68951]  848  914  922  819  910  734  751  911 1000  913  945  835  919  754
    ## [68965]  745  821  849  812  927  814  744  829  748  943 1113  949  844  804
    ## [68979]  851 1021  940  942  954  938 1008  854  806  815 1015 1015 1022  944
    ## [68993]  820  755 1149 1006  846  857 1002 1008 1015  957  831  853 1005  935
    ## [69007] 1026  839 1025 1017  949  907  943  822 1021 1042  928 1021 1035 1150
    ## [69021] 1014  903  906  908 1039 1047 1026  915  851 1212  908 1108  959 1049
    ## [69035]  920  943 1044  856  924  849  926  915  849 1010 1054 1052 1052 1109
    ## [69049] 1024  959 1142 1100  931  955 1103  923  944 1049 1055 1022 1113 1027
    ## [69063] 1101 1129  939 1103 1052 1121 1121 1025 1044 1104 1100 1008 1236 1059
    ## [69077] 1134 1013  953 1015 1017  936 1036  948 1007  951  932 1040  954 1005
    ## [69091] 1011 1121 1041 1141 1030  939 1020  941 1120 1123 1159 1036 1137 1025
    ## [69105] 1113 1158 1039 1054 1005 1128 1142 1150 1134 1151 1212 1157 1004 1015
    ## [69119] 1008 1101 1002 1141 1143 1026 1154 1325 1218 1158 1136 1020 1223 1005
    ## [69133] 1219 1009 1131 1111 1210 1044 1049 1228 1200 1031 1214 1206 1027 1045
    ## [69147] 1220 1217 1219 1224 1159 1232 1217 1250 1150 1521 1235 1119 1238 1031
    ## [69161] 1106 1033 1050 1252 1128 1118 1057 1203 1240 1407 1241 1244 1056 1130
    ## [69175] 1100 1114 1545 1253 1101 1245 1051 1151 1202 1305 1255 1240 1312 1306
    ## [69189] 1302 1228 1119 1248 1221 1135 1119 1116 1202 1209 1141 1152 1308 1342
    ## [69203] 1124 1317 1330 1330 1139 1230 1238 1114 1339 1314 1321 1314 1149 1346
    ## [69217] 1139 1318 1405 1336 1324 1312 1410 1246 1343 1212 1231 1229 1316 1233
    ## [69231] 1345 1207 1410 1216 1244 1149 1419 1353 1237 1214 1218 1411 1347 1214
    ## [69245] 1159 1313 1355 1404 1255 1242 1333 1242 1411 1400 1236 1316 1314 1422
    ## [69259] 1320 1440 1235 1431 1444 1434 1332 1423 1337 1245 1257 1348 1406 1449
    ## [69273] 1438 1502 1357 1247 1252 1303 1252 1329 1301 1503 1501 1451 1332 1327
    ## [69287] 1321 1445 1356 1303 1511 1321 1402 1450 1513 1334 1451 1314 1453 1452
    ## [69301] 1520 1502 1423 1317 1340 1416 1510 1533 1406 1553 1511 1354 1401 1416
    ## [69315] 1336 1345 1342 1600 1424 1552 1421 1356 1424 1547 1348 1425 1420 1353
    ## [69329] 1516 1449 1448 1528 1535 1604 1553 1410 1518 1610 1418 1401 1627 1427
    ## [69343] 1404 1551 1508 1627 1427 1407 1517 1449 1449 1656 1628 1513 1500 1632
    ## [69357] 1511 1430 1629 1624 1553 1517 1631 1454 1611 1643 1655 1533 1525 1649
    ## [69371] 1509 1440 1647 1549 1644 1629 1558 1707 1504 1653 1738 1542 1531 1540
    ## [69385] 1459 1658 1743 1501 1724 1708 1621 1702 1618 1537 1721 1705 1658 1531
    ## [69399] 1635 1650 1730 1630 1609 1658 1703 1654 1554 1732 1619 1540 1735 1532
    ## [69413] 1704 1617 1549 1805 1551 1649 1650 1553 1738 1632 1649 1602 1812 1751
    ## [69427] 1634 1605 1740 1623 1600 1617 1615 1814 1631 1808 1810 1548 1803 1742
    ## [69441] 1831 1601 1644 1727 1636 1809 1554 1721 1932 1742 1755 1815 1805 1734
    ## [69455] 1822 1653 1710 1646 1825 1755 1700 1700 1641 1727 1745 1756 1953 1835
    ## [69469] 1623 2008 1827 1651 1804 1806 1709 1754 1704 1718 1634 1829 1857 1706
    ## [69483] 1733 1842 1845 1844 1831 1758 1848 1856 1714 1700 1646 1804 1701 1747
    ## [69497] 1641 1758 1707 1726 1745 1852 1910 1655 1847 1737 1700 1845 1711 1903
    ## [69511] 1800 1905 1710 1759 1853 1732 1856 1922 1729 1904 1820 1748 1732 1840
    ## [69525] 1851 1747 1814 1738 1807 1805 1905 1937 1835 1901 1904 1849 1851 1912
    ## [69539] 1835 1853 1832 1804 1908 1746 1759 1801 1944 1908 1933 1959 1845 1740
    ## [69553] 1951 1753 2013 2006 1942 1940 1924 1918 1932 1758 1946 1901 1750 1754
    ## [69567] 1915 1830 1957 1951 1757 1839 1828 1751 1842 1957 1936 1933 1803 1958
    ## [69581] 2015 1902 1959 1832 1809 1806 1940 1956 1855 1933 1850 1803 2011 1819
    ## [69595] 1931 1826 2011 1917 1849 2004 1856 2020 1942 1846 2007 1815 1819 1914
    ## [69609] 1851 2010 1942 1959 2039 1939 1829 2039 2027 2011 2059 2102 1925 2006
    ## [69623] 2006 2017 1933 1910 2028 2047 1901 1833 2030 2052 2124 2031 1930 1840
    ## [69637] 1936 2058 2055 1931 1850 1919 2054 1921 1933 1932 2117 2012 2059 2034
    ## [69651] 2117 2045 2050 1940 1919 2122 2123 2020 2024 2049 1923 2106 1914 2050
    ## [69665] 2122 2002 2157 1925 2132 2055 1938 2126 2126 2044 2109 2024 1946 2121
    ## [69679] 2057 2032 2035 2131 2157 2004 2112 2137 1919 1934 2021 2030 2039 2155
    ## [69693] 2051 2043 2020 1951 2200 1957 2206 2019 2001 2211 2139 2153 2035 2202
    ## [69707] 2227 2159 2023 2154 2059 2023 2221 2015 2048 2100 2027 2146 2129 2148
    ## [69721] 2212 2017 2035 2242 2304 2026 2039 2115 2013 2234 2203 2217 2145 2016
    ## [69735] 2145 2030 2211 2145 2227 2138 2208 2039 2036 2023 2140 2236 2351 2145
    ## [69749] 2118 2218 2030 2124 2246 2143 2240 2201 2124 2246 2108 2238 2128    1
    ## [69763] 2239 2052 2241 2256 2227 2225 2051 2134 2250 2113 2035 2150 2227 2208
    ## [69777] 2146 2302 2230 2147 2056 2156 2304 2107 2221 2151 2139 2249 2229 2050
    ## [69791] 2308 2131 2307 2315 2238 2314 2249 2143 2106 2128 2243 2149 2110 2211
    ## [69805] 2106 2337 2325 2327 2132 2237 2330 2243 2204 2204 2349 2153 2140 2240
    ## [69819] 2324 2338 2140 2353 2259 2204 2158 2204 2332 2158    2 2343 2157 2143
    ## [69833] 2200 2150 2316 2222 2205 2244  110 2341 2316 2351 2321 2248 2341 2216
    ## [69847] 2246   11 2330 2333 2305 2318 2340   22   38 2351   26 2240 2248  100
    ## [69861] 2254 2255   26 2352   22 2239 2253 2303 2309 2307 2313 2334 2357    2
    ## [69875] 2342 2351    3  423  421   NA   NA  650  839  840  940  646  749  839
    ## [69889]  704  724  818  735  720  826  837 1025  928  836  836  854  734  910
    ## [69903]  758  853  805  852  808  917  742  844  743  713  927  733  818  813
    ## [69917]  923  902  921  745  856  916 1021  845  948  846  917  932  751  904
    ## [69931]  934  939 1114 1003 1017  919  933  929 1042 1017  835 1023  942  953
    ## [69945]  820  914 1153  949  840  954 1008  848  855 1025  927  954  952  839
    ## [69959]  852 1159  953  845  835 1017  858 1032  922 1025  855  940  959 1029
    ## [69973]  844 1014  911 1037 1031  918 1208 1025  954  913  956 1053  921 1030
    ## [69987] 1031  852 1039  937 1051  918 1047 1019 1035 1121 1050 1130  955 1231
    ## [70001] 1056 1034 1100 1133 1153 1107 1056 1059  935 1256 1003 1031  923 1015
    ## [70015]  916 1128 1114 1038 1053  933 1023 1104 1002 1055 1034 1022  933 1009
    ## [70029] 1150 1033 1128 1020  938  929 1128 1031 1108 1124 1120 1037 1205 1057
    ## [70043] 1221 1141 1108 1146  949 1025 1323  955 1038 1227 1026 1206 1155 1128
    ## [70057] 1003 1124 1151 1203 1211 1009 1129 1017 1027 1057 1040 1153 1059 1218
    ## [70071] 1029 1237 1155 1212 1221 1351 1148 1209 1053 1024 1103 1234 1157 1113
    ## [70085] 1214 1529 1108 1108 1229 1035 1117 1251 1234 1104 1253 1222 1232 1107
    ## [70099] 1138 1150 1149 1310 1140 1215 1120 1233 1306 1245 1257 1317 1251 1428
    ## [70113] 1249 1320 1133 1333 1304 1106 1344 1217 1215 1326 1150 1308 1325 1348
    ## [70127] 1311 1358 1341 1622 1312 1204 1410 1225 1236 1414 1254 1158 1209 1154
    ## [70141] 1238 1237 1238 1332 1359 1339 1221 1249 1236 1404 1326 1210 1204 1304
    ## [70155] 1418 1358 1335 1420 1352 1233 1330 1243 1355 1321 1426 1327 1253 1432
    ## [70169] 1415 1343 1348 1419 1250 1459 1405 1350 1458 1316 1420 1412 1405 1257
    ## [70183] 1433 1258 1249 1449 1401 1442 1249 1253 1450 1438 1355 1420 1429 1426
    ## [70197] 1517 1316 1338 1513 1401 1522 1513 1447 1532 1424 1417 1341 1524 1529
    ## [70211] 1400 1427 1541 1538 1356 1432 1449 1557 1623 1425 1528 1402 1619 1545
    ## [70225] 1456 1609 1410 1650 1449 1415 1551 1444 1509 1601 1439 1458 1622 1705
    ## [70239] 1649 1425 1632 1513 1537 1452 1540 1637 1524 1633 1451 1636 1559 1622
    ## [70253] 1608 1634 1630 1720 1651 1548 1723 1629 1531 1554 1715 1459 1602 1619
    ## [70267] 1708 1606 1727 1546 1610 1749 1700 1711 1644 1640 1539 1659 1530 1702
    ## [70281] 1727 1703 1704 1646 1550 1650 1652 1607 1735 1730 1710 1807 1803 1638
    ## [70295] 1636 1553 1600 1727 1649 1635 1627 1613 1908 1735 1553 1607 1611 1741
    ## [70309] 1731 1737 1624 1643 1622 1933 1618 1613 1820 1743 1753 1750 1735 1750
    ## [70323] 1650 1727 1658 1612 1819 1637 1736 1627 1654 1746 1759 1714 1812 1853
    ## [70337] 1954 1836 1636 1829 1847 1824 1648 1653 1651 1852 1752 1720 1701 1824
    ## [70351] 1812 1702 1651 1729 1833 1653 1756 1741 1756 1844 1838 1920 1839 1818
    ## [70365] 1835 1821 1758 1811 1743 1849 1719 1926 1742 1814 1900 1814 1719 1727
    ## [70379] 1819 1722 1802 1854 1756 1843 1756 1851 1859 1754 1915 1939 1930 1752
    ## [70393] 2005 1738 1952 1833 1932 1948 1925 1840 1853 1933 1907 1912 1945 1750
    ## [70407] 1744 1914 1905 1933 1957 1759 1940 1929 1742 1915 1747 1924 1934 1822
    ## [70421] 1907 1910 1807 2008 1752 2009 2008 1948 1751 1842 1841 1847 1955 2018
    ## [70435] 1817 2021 1850 1810 1808 1858 1840 1943 2023 1843 2054 1845 1957 2017
    ## [70449] 1909 1838 1857 2036 1953 1953 2108 2001 2011 2021 2040 1919 1929 2058
    ## [70463] 2031 1934 2018 1901 1912 2055 2024 2157 2108 1910 2032 2008 2051 2051
    ## [70477] 2044 2124 1950 1931 1933 1938 1940 1923 2031 2103 1936 2124 2011 2141
    ## [70491] 2050 2113 2017 2014 1941 2151 2126 2100 2056 2145 2201 2137 1957 2004
    ## [70505] 2143 2127 2031 2009 2105 2029 2212 2159 2125 2029 2133 2251 2227 2150
    ## [70519] 2058 2125 2206 2225 2142 2034 2023 2230 2122 2111 2154 2124 2228 2239
    ## [70533] 2144 2349 2238 2200 2138 2109 2208 2049 2233 2218 2231 2055 2049 2300
    ## [70547] 2219 2231 2235 2056 2234 2229   17 2305 2103 2356 2208 2302 2144    3
    ## [70561] 2143 2208    1 2351 2359 2325 2320 2318  105 2243 2237    5 2353 2351
    ## [70575] 2249 2356   27 2346 2255 2305 2256 2331 2332  139 2336 2353 2351 2357
    ## [70589]   16  402  444  417   NA   NA   NA  111  440  118  206  214  413  813
    ## [70603]  829  852  650  725  851 1012  715  844  733  832  830  713  930  852
    ## [70617]  904  803  901  807  715  850  831  926  910  909  800  915 1013  835
    ## [70631]  919  853  909  901  910  920  807  930  853  802  756 1059  940 1016
    ## [70645] 1016  924  951 1010  823 1140 1006  823  925 1022  954  837  949  930
    ## [70659] 1021  904 1011  836 1016 1017  944  918  823 1029 1020 1147  833 1101
    ## [70673] 1038 1022  908 1003  943 1029 1157  933 1029 1007 1030 1033 1036 1056
    ## [70687]  940  918 1034  923 1109  958 1032  929 1028 1112 1051 1052  900 1130
    ## [70701] 1034  932 1028 1044 1039 1212 1113 1108 1136 1040 1050 1130 1040  937
    ## [70715] 1133  909 1036 1104 1029 1056 1117 1020 1234 1042 1141 1007  918  937
    ## [70729] 1040 1010 1017 1103 1053  924 1047 1113 1025  922 1023 1214  946 1006
    ## [70743] 1103 1016 1124 1109 1129 1201 1055 1112 1159 1048 1243 1157 1128 1134
    ## [70757] 1121 1205 1307 1157 1143 1205 1133 1010 1132 1156 1035 1012 1245 1105
    ## [70771] 1115 1007 1220 1148 1036 1238 1147 1244 1014 1202 1206 1203 1150 1232
    ## [70785] 1045 1051 1210 1059 1153 1234 1246 1031 1134 1351 1520 1228 1028 1218
    ## [70799] 1304 1106 1223 1035 1113 1241 1231 1116 1249 1145 1408 1156 1547 1115
    ## [70813] 1243 1144 1304 1314 1303 1645 1113 1114 1322 1258 1212 1204 1133 1236
    ## [70827] 1214 1213 1257 1246 1333 1146 1406 1129 1356 1311 1308 1206 1107 1313
    ## [70841] 1310 1253 1256 1358 1347 1149 1407 1157 1427 1303 1239 1330 1239 1242
    ## [70855] 1249 1200 1324 1241 1244 1254 1453 1409 1540 1453 1206 1420 1331 1306
    ## [70869] 1349 1402 1325 1239 1513   NA 1432 1326 1410 1401 1313 1426 1408 1234
    ## [70883] 1420 1351 1248 1247 1342 1254 1255 1426 1333 1418 1423 1657 1537 1425
    ## [70897] 1314 1334 1249 1318 1514 1335 1246 1442 1522 1256 1444 1428 1459 1317
    ## [70911] 1442 1522 1252 1500 1433 1304 1438 1513 1349 1441 1456 1444 1444 1553
    ## [70925] 1450 1504 1341 1543 1410 1332 1320 1430 1451 1408 1339 1334 1532 1445
    ## [70939] 1352 1527 1428 1520 1432 1406 1348 1543 1355 1601 1623 1534 1359 1417
    ## [70953] 1613 1525 1501 1601 1548 1543 1619 1429 1634 1456 1555 1547 1652 1405
    ## [70967] 1451 1612 1417 1454 1520 1609 1537 1508 1428 1628 1521 1601 1502 1502
    ## [70981] 1626 1612 1615 1623 1631 1607 1643 1645 1506 1515 1648 1720 1534 1537
    ## [70995] 1436 1631 1541 1456 1453 1632 1534 1545 1635 1638 1720 1631 1707 1708
    ## [71009] 1602 1708 1546 1657 1506 1708 1610 1709 1656 1701 1812 1619 1626 1720
    ## [71023] 1654 1737 1724 1541 1712 1632 1638 1549 1707 1720 1631 1726 1645 1601
    ## [71037] 1827 1643 1728 1900 1746 1639 1639 1727 1605 1623 1557 1812 1555 1802
    ## [71051] 1638 1743 1608 1647 1625 1915 1637 1707 1757 1752 1637 1654 1628 1758
    ## [71065] 1617 1806 1723 1741 1738 1752 1819 1932 1826 1755 1810 1821 1708 1719
    ## [71079] 1813 1750 1840 1716 1830 1718 1649 1652 1801 1827 1633 1626 1700 1705
    ## [71093] 1907 1902 1635 1805 1924 1725 1741 1658 1732 1813 1737 1653 1833 1813
    ## [71107] 1832 1745 1823 1750 1807 1851 1719 1835 1742 1815 1844 1839 1843 1655
    ## [71121] 1844 1926 1856 1808 1713 1855 1907 1811 1837 1904 1923 1856 1915 1806
    ## [71135] 1840 1945 1942 1948 1748 1911 1800 1904 1904 1933 1950 1915 2001 1802
    ## [71149] 1759 1942 1745 1929 1914 1738 1948 1750 1916 1850 1938 1844 1757 1938
    ## [71163] 1920 1914 2023 2038 1953 2013 1938 2016 1810 1940 1957 1921 2008 2032
    ## [71177] 2049 2018 1906 2007 1932 2030 1941 1848 2045 1949 1837 2013 1924 2045
    ## [71191] 2036 1947 1923 2023 2042 2019 2015 2040 2002 1953 1924 2015 1924 2030
    ## [71205] 1931 2030 2021 1919 1955 1929 2001 2119 2044 2156 1952 1922 2125 2143
    ## [71219] 2138 1929 2046 1901 2141 2103 2031 2037 2128 2037 2130 2051 2116 1917
    ## [71233] 2020 2121 1912 2157 2137 2204 2054 2030 2045 2118 2113 2150 2136 2042
    ## [71247] 2136 2127 1935 2000 2044 2035 2200 2141 1939 2123 2107 2037 2041 2040
    ## [71261] 2207 2154 2133 2144 2156 2206 2111 2212 2138 2129 2111 2203 2030 2127
    ## [71275] 2127 2035 1958 2057 2127 2055 2053 2145 2323 2200 2046 2101 2218 2159
    ## [71289] 2132 2209 2205 2124 2213 2126 2222 2241 2241 2126 2136 2306 2231 2155
    ## [71303] 2229 2121 2206 2203 2218 2159 2202 2240 2247 2242 2153 2215 2313    7
    ## [71317] 2210 2127 2325 2108 2239 2229 2220 2251 2150 2223 2306 2250 2246 2228
    ## [71331] 2210 2218 2323 2312 2157 2213 2222 2119 2148 2202 2133 2250 2339 2211
    ## [71345] 2342 2228   51 2246 2247 2329 2219 2323 2137 2159 2153 2330 2335 2139
    ## [71359]   20 2204    7 2341 2233 2250 2211 2353 2136 2323 2202 2323 2222 2248
    ## [71373] 2348 2156 2219 2202 2321  107 2249 2236 2202 2216 2149    1 2233   36
    ## [71387] 2320 2210 2158 2322 2212 2314 2241 2218 2323 2311    1 2212 2339    9
    ## [71401]    8 2353    5 2315 2353 2332 2222 2246 2258    4 2349 2252   31   51
    ## [71415] 2318 2305 2323 2356   44   15 2349   17  128 2304 2305 2340   35   43
    ## [71429]   44 2305 2304   43 2316 2322 2328 2333   47   24  111   37 2338 2344
    ## [71443]  134 2400 2337 2345   14 2350   32   13 2359   21  229    3  128   54
    ## [71457]  136  147   15   54  244   31   26   49  232  107  405  235   57  139
    ## [71471]  419   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [71485]   NA   NA   NA   NA   NA   NA   NA  431  635  752  829  828  831  749
    ## [71499]  709  928  654   NA  717 1014  817  655  742  929  702  833  712  723
    ## [71513]  732  814  832  731  829  850  718  846  754  857  808  808  748  915
    ## [71527]  910  834  812  836  819  958  809  722  834  914  746  928  858  924
    ## [71541]  900  825  729  814  857  839  908  726  839  912  932  925  904  752
    ## [71555]  959  856  842  802  834  915  812  749  824  806 1000 1002  930 1121
    ## [71569]  952 1039  829 1141  804  929  941 1017  948 1008  831  849 1014 1025
    ## [71583] 1017  852  912  955 1041 1003 1037 1002  928  901  856  947  939  831
    ## [71597]  910 1013 1033  958 1053  830  851 1024 1017 1207  933 1103 1023  913
    ## [71611] 1006  907  840 1030 1030 1002 1109 1250  924 1214 1126  903  928  932
    ## [71625] 1050  953 1116  844 1035 1025  918 1039  900 1109  924 1044 1104 1031
    ## [71639]  933 1127 1026 1041 1010  925 1039 1039 1049 1102  945  934 1018 1052
    ## [71653] 1028 1038 1119 1102 1013 1100 1103  943 1055 1248 1005 1029 1111 1001
    ## [71667] 1026  926 1043 1047  936 1024 1012 1013 1028  953 1158  940 1156  937
    ## [71681] 1039 1036 1035 1151 1103 1036 1118   NA 1144 1142 1128 1028 1124 1025
    ## [71695]  953 1105 1049 1121 1218  958 1224 1141 1014 1159 1155 1000 1143 1111
    ## [71709]  955 1130 1007 1016 1143 1021 1227 1220 1038 1151 1016 1156 1207 1215
    ## [71723] 1222 1216 1049 1123 1002 1004 1240 1220 1149 1037 1128 1041 1227 1127
    ## [71737] 1149 1229 1140 1129 1244 1210 1152 1045 1229 1254 1114 1114 1524 1223
    ## [71751] 1218 1400 1234 1129 1107 1056 1133 1035 1303 1229 1241 1220 1108 1059
    ## [71765] 1239 1057 1106 1210 1051 1326 1114 1120 1559 1315 1246 1246 1233 1229
    ## [71779] 1421 1151 1132 1202 1212 1130 1143 1232 1126 1304 1342 1134 1208 1149
    ## [71793] 1351 1145 1317 1111 1220 1349 1300 1233 1331 1356 1308 1410 1322 1321
    ## [71807] 1154 1154 1320 1300 1235 1335 1245 1200 1342 1341 1254 1409 1444 1244
    ## [71821] 1331 1301 1206 1354 1349 1210 1234 1342 1336 1408 1235 1222 1238 1330
    ## [71835] 1427 1407 1321 1254 1429 1245 1234 1304 1454 1243 1338 1333 1421 1354
    ## [71849] 1425 1455 1409 1517 1253 1251 1329 1302 1301 1247 1424 1451 1346 1413
    ## [71863] 1441 1333 1439 1322 1251 1323 1511 1450 1514 1344 1506 1349 1522 1456
    ## [71877] 1332 1433 1400 1418 1428 1326 1346 1325 1441 1353 1458 1514 1453 1548
    ## [71891] 1346 1350 1330 1423 1527 1430 1359 1529 1522 1540 1535 1601 1448 1346
    ## [71905] 1423 1538 1349 1554 1356 1442 1416 1349 1642 1543 1436 1536 1441 1626
    ## [71919] 1534 1407 1530 1602 1549 1526 1509 1614 1519 1605 1550   NA 1505 1436
    ## [71933] 1443 1456 1416 1607 1613 1644 1444 1520 1646 1456 1438 1619 1443 1432
    ## [71947] 1549 1458 1625 1507 1425 1637 1638 1551 1642 1532 1636 1705 1634 1444
    ## [71961] 1524 1537 1726 1659 1529 1447 1501 1705 1733 1556 1519 1525 1700 1709
    ## [71975] 1541 1722 1630 1631 1532 1701 1634 1547 1656 1552 1716 1646 1632 1603
    ## [71989] 1711 1740 1752 1631 1714 1620 1544 1613 1615 1612 1738 1724 1801 1709
    ## [72003] 1658 1640 1733 1828 1559 1642 1739 2007 1624 1724 1646 1648 1802 1741
    ## [72017] 1643 1828 1809 1751 1737 1645 1600 1706 1830 1721 2002 1757 1836 1745
    ## [72031] 1602 1754 1727 1720 2030 1819 1812 1635 1831 1843 1701 1636 1725 1800
    ## [72045] 1830 1808 1630 1751 1610 1718 1824 1651 1703 1823 1637 1829 1904 1650
    ## [72059] 1913 1920 1753 1753 1749 1919 1845 1720 1640 1756 1815 1700 1713 1745
    ## [72073] 1801 1751 1743 1707 1732 1705 1907 1806 1719 1716 1737 1758 1839 1915
    ## [72087] 1851 1709 1658 1949 1814 1848 1850 1930 1832 1718 1721 1817 1851 1836
    ## [72101] 1832 1744 1738 1742 1911 1811 1906 1834 1805 1854 1851 1821 1907 1902
    ## [72115] 1809 1831 1735 1825 1822 1915 1916 1817 1830 1811 1902 1744 1809 1843
    ## [72129] 1753 1931 1801 1805 1904 1954 1959 1757 2032 1939 1947 1919 1827 1917
    ## [72143] 1931 2010 2015 1856 1916 1935 1754 1947 1804 1908 1954 2022 1752 1903
    ## [72157] 1822 1918 1937 2010 2029 1812 1851 1959 2014 1802 1941 1927 1755 2033
    ## [72171] 1800 1841 1820 1953 1824 1807 1839 1934 1847 2039 1901 1824 1906 1957
    ## [72185] 1848 1815 1830 1852 1956 1821 1939 1845 2015 2021 1917 2048 1943 2027
    ## [72199] 1949 2033 2051 1908 2007 1853 2033 1950 1938 2010 2059 1934 1850 1935
    ## [72213] 2057 2005 1926 2007 1845 1952 1909 2024 2036 2008 2034 2053 2020 1930
    ## [72227] 1906 2031 1937 2032 1845 1956 2043 1935 2100 1919 1941 1958 2135 1932
    ## [72241] 2038 2131 1918 2055 2013 2050 2016 2118 1951 2120 1943 1940 2117 2037
    ## [72255] 2033 2116 2112 2117 2000 2155 2048 2019 1924 2116 2036 2153 2021 2039
    ## [72269] 1956 2154 2019 2129 1943 2046 2128 2015 2001 2228 2044 2209 2236 2054
    ## [72283] 2156 2151 2034 2028 2143 2019 2256 2247 2142 2102 2156 2021 2200 2107
    ## [72297] 1949 2150 2141 2102 2057 2034 2242 2136 2011 2047 2151 2231 2010 2135
    ## [72311] 2026 2201 2054 2032 2210 2138 2152 2033 2153 2032 2325   51 2325 2239
    ## [72325] 2215   43 2107 2209 2229 2026 2213 2144 2130 2247 2143 2219 2351 2231
    ## [72339] 2157 2212 2132 2111 2130 2158 2212 2145 2159 2219 2055 2053 2127   10
    ## [72353] 2224 2154 2155 2254 2251 2100 2324 2307 2129 2111 2156 2107 2052 2336
    ## [72367] 2212 2211 2149 2129 2112 2253 2151 2230 2134 2346 2215 2214 2356 2159
    ## [72381] 2335 2320   32 2214 2348 2155 2305 2204 2144 2154 2140   43 2311 2254
    ## [72395]   22 2159 2153 2324    1   23 2225 2144 2243 2327 2148 2208 2341 2311
    ## [72409] 2301 2240 2340 2259 2200 2245 2234 2255    1   40 2306 2335 2356   10
    ## [72423] 2246 2354   47    1    2 2341 2309 2246   31 2250 2249 2308 2307 2243
    ## [72437] 2256 2253   31 2340   38 2326 2357 2336   42   46 2354 2355    1   40
    ## [72451]   10   28   33  431  420   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [72465]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA  535  633
    ## [72479]  755  822  833  827  703  645  930  739  707  728  837  808  646  746
    ## [72493]  752  810  655  825  719  824  809  837  844 1034  947  729  727  803
    ## [72507]  828  838  813  808  905  807  839  850  740  930  724  918  919  747
    ## [72521]  816  843  910  835  854  929  757  757  855  855  850  903  953  822
    ## [72535]  753  900  921  913  735  739  806  804  939 1001  955  916  857  810
    ## [72549]  847  758  830  908  950 1115  926  951  842  858 1027  958  910 1025
    ## [72563] 1007  821  821  756  930 1150 1031 1034  909  813 1001  810  834  922
    ## [72577]  953  838  829 1011 1054 1007  853 1007  954 1036  829 1003  924  940
    ## [72591]  938 1052  920 1008 1035  830 1022 1021  858 1034  931  903 1040  848
    ## [72605]  956  902 1029 1221  941  854 1109 1007 1007 1050  859  903  924  942
    ## [72619]  956  908 1045 1111 1003 1034  924 1007 1050  919  932  915  912 1045
    ## [72633] 1031 1146  917 1057 1115 1045 1011 1055  952 1109  927 1057 1113 1043
    ## [72647] 1102 1046 1015 1107  933 1105 1041 1033 1308 1256 1015 1045 1017 1149
    ## [72661]  931 1000 1137 1032  922 1035 1042 1022 1018 1053 1014 1124 1016  929
    ## [72675] 1040  954  931 1022 1146  939 1146 1045 1109  958 1037 1023 1145 1148
    ## [72689] 1125 1218 1145 1312 1149 1213 1031 1127 1118 1157 1130 1030 1139 1007
    ## [72703] 1149 1102 1022 1020 1245 1057 1218 1027 1053 1214 1152 1122 1146 1135
    ## [72717] 1226 1146 1207 1224 1117 1158 1025 1026 1106 1149 1126 1024 1228 1218
    ## [72731] 1227 1211 1157 1241 1227 1232 1231 1214 1136 1535 1039 1233 1238 1114
    ## [72745] 1148 1301 1115 1131 1218 1213 1424 1051 1049 1232 1122 1200 1309 1230
    ## [72759] 1118 1355 1109 1201 1320 1316 1133 1129 1211 1247 1217 1227 1247 1150
    ## [72773] 1155 1241 1148 1241 1148 1128 1124 1331 1148 1122 1206 1330 1221 1109
    ## [72787] 1336 1220 1247 1304 1226 1140 1240 1338 1147 1255 1323 1152 1201 1327
    ## [72801] 1210 1247 1306 1307 1220 1348 1312 1256 1240 1212 1332 1215 1216 1402
    ## [72815] 1416 1329 1230 1409 1502 1412 1246 1423 1343 1342 1420 1350 1248 1300
    ## [72829] 1408 1338 1518 1423 1329 1333 1316 1525 1320 1431 1351 1244 1251 1531
    ## [72843] 1444 1324 1413 1356 1321 1354 1443 1248 1453 1358 1256 1303 1514 1250
    ## [72857] 1454 1503 1348 1510 1355 1319 1404 1442 1450 1310 1539 1424 1500 1410
    ## [72871] 1510 1325 1523 1456 1339 1610 1404 1433 1435 1547 1408 1341 1454 1329
    ## [72885] 1326 1455 1441 1359 1339 1346 1614 1334 1355 1526 1540 1517 1458 1441
    ## [72899] 1439 1417 1635 1426 1413 1600 1512 1604 1547 1607 1545 1439 1520 1536
    ## [72913] 1417 1510 1415 1527 1408 1459 1445 1544 1620 1551 1554 1516 1644 1439
    ## [72927] 1558 1426 1443 1519 1651 1526 1603 1524 1456 1531 1638 1507 1632 1439
    ## [72941] 1521 1638 1644 1645 1531 1521 1540 1701 1637 1701 1718 1526 1638 1653
    ## [72955] 1558 1639 1514 1459 1505 1611 1445 1639 1635 1637 1654 1655 1656 1542
    ## [72969] 1609 1540 1536 1625 1711 1551 1544 1610 1714 1744 1650 1646 1647 1627
    ## [72983] 1631 1720 1520 1733 1553 1617 1809 1725 1623 1650 1738 1911 1700 1722
    ## [72997] 1644 1624 1654 1557 1803 1732 1631 1648 1657 1606 1558 1814 1604 1620
    ## [73011] 1632 1706 1629 1730 1802 1806 1821 1742 1704 1739 1720 1708 1748 1743
    ## [73025] 1708 1759 1831 1637 1812 1754 1612 1631 1735 1705 1754 1815 1822 1633
    ## [73039] 1623 1734 1847 2006 1703 1746 1754 1841 1719 1720 1702 1705 1710 1817
    ## [73053] 1645 1700 1901 1818 1839 1825 1858 1629 1639 1648 2033 1731 1739 1710
    ## [73067] 1918 1757 1749 1722 1726 1751 1812 1806 1847 1657 1854 1659 1723 1728
    ## [73081] 1841 1901 1721 1802 1857 1839 1738 1755 1743 1914 1928 1800 1721 1912
    ## [73095] 1727 1804 1823 1843 1753 1837 1854 1934 1837 1744 1807 1732 1914 1821
    ## [73109] 1856 1826 1855 1822 1838 1853 1938 1949 1730 1907 1748 1828 1841 1807
    ## [73123] 1801 1934 1905 1923 1751 1943 1809 1929 1941 1933 1927 1934 1807 1756
    ## [73137] 1858 1805 1918 2007 1752 1821 1910 1830 1950 1953 2024 1859 1745 1918
    ## [73151] 1834 1945 2005 1811 1825 1927 1846 1956 2012 2013 1819 1851 1959 1811
    ## [73165] 2003 2002 1936 1902 1950 1815 1832 1947 1919 1925 1913 1850 1907 1940
    ## [73179] 2025 1828 1823 2000 1925 1908 1812 1851 2001 1854 2020 1822 1930 2032
    ## [73193] 2027 1938 2007 1929 2028 2010 2002 1938 1903 1920 1903 1850 2021 2102
    ## [73207] 1852 1900 2040 2108 1934 2009 2117 1857 1846 2100 2059 2055 2024 2034
    ## [73221] 1942 2044 1921 1957 1923 2036 1908 2101 1930 2044 1916 2055 2003 1911
    ## [73235] 2005 2120 2003 1953 2029 2048 2126 2118 2055 1930 2107 2100 1943 2035
    ## [73249] 2146 2113 2112 2025 2122 2016 2205 2036 1944 1937 1953 2130 2110 2159
    ## [73263] 2106 2134 2023 2120 2002 2207 2157 2209 1929 2147 2220 2149 2210 2007
    ## [73277] 2012 2012 2025 2148 2208 2157 2031 2125 2104 2105 2110 2031 2133 2107
    ## [73291] 2142 2052 2006 2121 2005 2243 2159 2028 2037 2234 2103 2009 2048 2158
    ## [73305] 2159   NA 2204 2113 2051 2128 2208 2226 2146 2227 2257 2050 2054 2141
    ## [73319] 2057 2027 2238 2230 2229 2218 2218 2120 2118 2129 2220 2036 2221 2154
    ## [73333] 2131 2230    2 2058 2206 2102 2241 2110 2104 2148 2049 2236 2212 2044
    ## [73347] 2053 2213 2136 2211 2148 2209 2152 2333 2255 2120 2312 2209 2105 2122
    ## [73361] 2236 2153 2238 2100 2117 2259 2141 2307 2234 2219 2113 2154 2252 2325
    ## [73375]   20 2223 2151 2130 2339  106 2142 2137 2352 2149 2235 2243 2332 2354
    ## [73389] 2239 2237 2325 2334 2205 2205 2328 2323 2212 2332 2218 2159 2358 2308
    ## [73403] 2245 2214 2244 2159 2207 2321 2254   12 2333 2201 2343 2207 2154 2242
    ## [73417] 2259 2351 2349 2350 2301 2332   27 2234 2245 2306   16   31 2245 2335
    ## [73431] 2314 2252 2238 2324   41 2329 2330 2337    6 2349 2341    9  417  428
    ## [73445]   NA   NA   NA   NA   NA  631  749  806  831  852  716  726  659  647
    ## [73459]  742  735  751  836  743  826  704  702  830  922  725  921  845 1029
    ## [73473]  830  737  850  800  728  653  851  718  733  834  755  825  902  855
    ## [73487]  804  802  846  809  713  914  856  737  818  804  822  840  740  908
    ## [73501]  730  742  907  942  919  901  839  825  735  849  932  911  748  800
    ## [73515]  755  844  819  840  740 1127  817  956  923  819  842  955  756  935
    ## [73529]  957 1004  857  935  759  839  916  837 1022 1008  904  825 1011  850
    ## [73543] 1150  852  958 1023  832 1014  951  959 1010  952  844  910 1017 1000
    ## [73557]  919  923 1002  955  836  829 1027 1013 1044 1015 1207  856  906 1027
    ## [73571] 1030 1027 1036  840 1002 1222  932 1030  940  910 1140  949 1055  901
    ## [73585] 1045  933  944 1028  903  931  851  958  933  902 1023 1035 1053  928
    ## [73599] 1017 1046 1038 1043 1037 1114 1124  927 1057  954  942  935 1128 1059
    ## [73613] 1025 1042 1129  917  933 1107  930 1052 1021 1100 1020 1024 1256 1020
    ## [73627] 1133 1017  948 1154  919 1007  935 1025 1032  938  940 1138  951 1140
    ## [73641]  952 1043  925  946  950 1019 1018 1053 1052 1042 1037 1132  949 1022
    ## [73655] 1034 1120 1140 1204 1128 1151  959 1158 1109 1037 1054 1211 1116 1136
    ## [73669] 1232 1158 1141 1319 1049 1145 1027 1212 1207 1005 1011 1019 1002 1103
    ## [73683] 1114 1155 1024 1146 1120 1209 1107 1054 1121 1250 1045 1055 1014 1148
    ## [73697] 1157 1222 1053 1218 1136 1211 1241 1214 1126 1552 1135 1240 1217 1221
    ## [73711] 1238 1220 1049 1242 1049 1032 1051 1044 1105 1225 1110 1239 1232 1255
    ## [73725] 1436 1101 1423 1110 1157 1047 1228 1210 1116 1053 1150 1110 1313 1336
    ## [73739] 1230 1149 1224 1217 1120 1118 1136 1304 1210 1639 1129 1133 1320 1247
    ## [73753] 1206 1328 1124 1427 1407 1314 1200 1132 1231 1118 1300 1323 1355 1249
    ## [73767] 1355 1143 1215 1227 1358 1227 1213 1223 1220 1239 1231 1221 1334 1231
    ## [73781] 1249 1355 1218 1416 1349 1253 1335 1158 1407 1230 1332 1400 1302 1435
    ## [73795] 1437 1245 1338 1309 1416 1225 1408 1346 1237 1317 1318 1335 1435 1434
    ## [73809] 1317 1355 1317 1411 1353 1245 1425 1318 1450 1339 1346 1259 1244 1309
    ## [73823] 1507 1432 1355 1255 1457 1259 1346 1520 1500 1431 1357 1458 1516 1518
    ## [73837] 1330 1335 1323 1309 1515 1408 1446 1356 1457 1327 1356 1602 1543 1408
    ## [73851] 1452 1550 1430 1327 1438 1500 1536 1430 1508 1557 1353 1351 1514 1422
    ## [73865] 1338 1331 1530 1559 1521 1439 1612 1539 1417 1420 1533 1411 1352 1454
    ## [73879] 1516 1542 1506 1623 1521 1436 1610 1403 1609 1430 1531 1534 1548 1449
    ## [73893] 1548 1635 1639 1424 1435 1413 1612 1441 1503 1612 1436 1503 1449 1644
    ## [73907] 1432 1546 1518 1536 1615 1532 1704 1537 1503 1533 1628 1546 1634 1637
    ## [73921] 1627 1714 1449 1524 1544 1610 1642 1552 1716 1447 1524 1522 1524 1531
    ## [73935] 1704 1722 1653 1644 1714 1658 1723 1552 1727 1652 1552 1614 1606 1625
    ## [73949] 1706 1723 1705 1612 1711 1655 1648 1750 1723 1600 1753 1631 1645 1712
    ## [73963] 1635 1539 1637 1634 1550 1649 1551 1735 1628 1752 1704 1556 1732 1703
    ## [73977] 1612 1816 1712 1617 1554 1638 1607 1818 1928 1746 1733 1803 1710 1633
    ## [73991] 1727 1805 1640 1743 1629 1732 1742 1806 1605 1744 1800 1718 1751 1950
    ## [74005] 1707 1639 1710 2003 1826 1813 1823 1752 1656 1737 1647 1834 1618 1705
    ## [74019] 1745 1753 1845 1703 1707 1840 1643 1709 1732 1709 1759 1817 1800 1918
    ## [74033] 1847 1634 1649 1733 1624 1828 1848 1933 1654 1656 1845 1816 1736 1733
    ## [74047] 1804 1718 1823 1646 1759 1702 1745 1704 1842 1724 1901 1937 1859 1900
    ## [74061] 1713 1839 1855 1942 1830 1849 1754 1735 1812 1849 1752 1739 1800 1800
    ## [74075] 1846 1829 1822 1755 1911 1836 1910 1804 1800 1831 1813 1910 1910 1841
    ## [74089] 1854 1736 1920 1756 1955 1917 1754 1918 1740 1848 1858 1805 1819 1905
    ## [74103] 1914 1926 1812 1946 1915 2000 1917 1951 1807 1744 2019 1748 1845 1947
    ## [74117] 1835 1952 2012 1739 1952 1928 1756 1806 1938 1908 1920 1826 1807 2015
    ## [74131] 1858 1826 2014 1943 1846 1957 2009 2003 1823 2034 2015 1837 1949 1901
    ## [74145] 1816 1940 1953 1954 2048 1844 1822 1851 1815 1823 1908 1850 1908 1856
    ## [74159] 1943 1931 2011 1900 2017 1902 1920 1923 2015 2013 2040 1909 1957 2007
    ## [74173] 1923 2028 1928 1947 1958 1840 1918 2051 2100 2041 2108 2033 1932 2017
    ## [74187] 1906 1857 2058 2042 1928 1856 2102 2017 2056 2100 1952 2125 2052 2044
    ## [74201] 2045 1947 2016 1937 2022 1946 2033 2044 2007 2117 2123 2148 2054 2013
    ## [74215] 2025 1942 1945 2149 2126 2133 1950 2030 2127 2120 2004 2031 2114 2013
    ## [74229] 2157 2105 2122 2123 2058 1921 2056 2211 2135 2102 2000 1959 2159 2232
    ## [74243] 2040 2223 2224 2010 1948 2212 2026 2131 2129 2001 2157 2028 2237 2217
    ## [74257] 2209 2043 2053 2129 2130 2214 2006 2056 2153 2149 2037 2052 2222 2133
    ## [74271] 2130 2112 2206 2151 2130 2119 2215 2142 2144 2222 2225 2051 2035 2042
    ## [74285] 2048 2115 2259 2050 2128 2113 2240 2142 2234 2226 2140 2047 2236 2119
    ## [74299] 2035 2047 2038 2258 2206 2045 2233 2118   32 2130 2107 2258 2113 2235
    ## [74313] 2032 2133 2212 2320 2113 2223 2257 2047 2118 2129 2149 2145 2236 2126
    ## [74327] 2152 2300 2204 2156 2311 2111 2254 2056 2127 2101 2120 2249 2227 2240
    ## [74341] 2057 2253 2159 2137 2317 2156 2147 2311 2216 2256 2138 2144 2318 2300
    ## [74355] 2255 2311 2143   13 2119 2226 2337  104 2141 2317 2359 2345 2244 2151
    ## [74369] 2344 2217    2 2214 2243 2148 2312 2228 2243 2257 2146 2316 2325 2242
    ## [74383] 2202 2228  130 2343 2159 2247 2349 2339 2239 2337 2306 2253 2220 2353
    ## [74397] 2222   40 2248 2237    8  104   38 2232 2325  102 2355 2256 2308 2303
    ## [74411]   33 2258 2327 2337 2318   40 2342 2335 2351 2347 2344    5  451  448
    ## [74425]  426   NA  424  433  122  634  814  831  820 1026  722  654  641  704
    ## [74439]  801  758  950  857  851  800  721  716  645  649  826  850  819  756
    ## [74453]  740 1037  843  829  730  723  935  815  805  853  809  814  920  751
    ## [74467]  908  858  830  918  745  721  734  842  859  935  912  828  825  808
    ## [74481]  911  753  914 1012  734  859  904  754  826  850  912  844  920 1001
    ## [74495]  917  804  745  801 1014  936  748  846  819  845  848  909  746  931
    ## [74509]  815  934 1014  912 1023 1134  830  748 1026  756 1034  943  830 1007
    ## [74523]  815  855 1005  854  819  944 1033  842 1001 1026 1006 1157  850  936
    ## [74537]  914  933  839 1047 1011 1044 1102 1002 1202 1016 1050 1011  905  924
    ## [74551]  908  833 1020 1019  830 1018  846 1005 1044 1033 1002  906 1040  925
    ## [74565]  945 1022 1241  858  900  923 1234  949  912  959 1102 1112 1054  942
    ## [74579] 1109 1045  953  938 1029 1032 1015  900 1046 1130 1058 1051 1243 1035
    ## [74593] 1124 1101 1140 1023  914 1119 1010 1107 1026 1058 1056 1144 1045 1023
    ## [74607] 1019  930  949  932 1024  959 1215  925 1156 1023 1038 1110 1127  953
    ## [74621]  940 1011 1040 1012 1014  933 1001 1004 1000 1032 1105 1046 1119 1037
    ## [74635] 1216  952 1134 1137 1210 1136 1220 1034 1052 1225 1316 1027 1010 1008
    ## [74649] 1207 1133  959 1203 1237 1039 1222 1216 1241 1031 1200 1158 1204 1125
    ## [74663] 1235 1229 1005 1146 1146 1207 1225 1026 1058 1013 1203 1127 1147 1238
    ## [74677] 1154 1247 1046 1228 1114 1205 1028 1419 1239 1225 1211 1224 1037 1251
    ## [74691] 1154 1220 1031 1309 1237 1209 1226 1114 1228 1145 1558 1224 1107 1249
    ## [74705] 1412 1246 1246 1139 1238 1123 1054 1608 1314 1145 1309 1111 1143 1151
    ## [74719] 1227 1300 1154 1125 1253 1308 1138 1216 1109 1306 1319 1219 1224 1205
    ## [74733] 1220 1249 1237 1212 1134 1337 1208 1209 1355 1308 1209 1344 1141 1347
    ## [74747] 1344 1228 1133 1552 1244 1220 1355 1119 1141 1343 1315 1439 1358 1247
    ## [74761] 1343 1319 1151 1224 1357 1228 1324 1225 1218 1228 1216 1355 1330 1341
    ## [74775] 1227 1311 1414 1159 1345 1437 1428 1430 1353 1356 1457 1435 1419 1328
    ## [74789] 1414 1355 1339 1347 1241 1433 1344 1313 1231 1503 1336 1334 1429 1440
    ## [74803] 1358 1418 1405 1247 1415 1332 1327 1536 1433 1512 1331 1249 1357 1415
    ## [74817] 1319 1315 1416 1459 1256 1454 1342 1525 1309 1400 1356 1312 1453 1541
    ## [74831] 1347 1531 1457 1527 1350 1532 1500 1359 1506 1343 1601 1447 1342 1415
    ## [74845] 1413 1458 1323 1445 1536 1411 1437 1343 1350 1341 1348 1431 1428 1600
    ## [74859] 1348 1632 1406 1525 1601 1356 1631 1414 1558 1400 1522 1401 1509 1415
    ## [74873] 1533 1456 1454 1521 1422 1542 1431 1619 1602 1541 1633 1547 1549 1501
    ## [74887] 1411 1426 1518 1504 1646 1605 1447 1507 1646 1500 1459 1442 1521 1432
    ## [74901] 1622 1517 1614 1624 1602 1527 1549 1507 1620 1626 1710 1621 1440 1652
    ## [74915] 1526 1644 1534 1539 1732 1634 1635 1521 1447 1456 1624 1511 1645 1647
    ## [74929] 1633 1724 1530 1653 1736 1608 1731 1626 1742 1639 1523 1755 1628 1627
    ## [74943] 1647 1554 1651 1529 1538 1607 1729 1715 1614 1800 1559 1604 1658 1657
    ## [74957] 1724 1630 1540 1742 1721 1802 1800 1618 1631 1615 1809 1814 1635 1953
    ## [74971] 1923 1628 1617 1631 1737 1555 1735 1633 1802 1824 1743 1755 1719 1613
    ## [74985] 1745 1725 1756 1601 1735 1816 1837 1654 1806 1602 1618 1624 1707 1738
    ## [74999] 1814 1704 1659 1834 1757 1954 1700 1708 1746 1712 1809 1651 1745 1707
    ## [75013] 1710 1818 1850 1649 1911 1851 1928 1701 1728 1712 1625 1812 1802 1827
    ## [75027] 1836 1700 1749 1707 1831 1901 1743 1714 1807 1733 1654 1815 1712 1730
    ## [75041] 1816 1831 1650 1902 1744 1827 1915 1913 1710 1916 1752 1902 1852 1841
    ## [75055] 1729 2004 1718 1726 1930 1916 1832 1806 1844 1823 1755 1719 1823 1807
    ## [75069] 1814 1843 1911 1913 1907 1811 1805 1753 1832 1916 1830 1944 1758 1746
    ## [75083] 1823 1746 1836 1843 1927 1832 1800 1852 2057 1738 1957 1931 1917 1920
    ## [75097] 1910 2003 1758 1938 1959 1849 1738 1741 1909 2006 1932 1758 1915 1803
    ## [75111] 1931 2026 2025 1835 2020 1857 1947 2017 2013 1808 1817 1850 1757 2023
    ## [75125] 1823 2027 1848 1812 2003 1839 1850 1949 1802 1816 2049 1821 1835 2024
    ## [75139] 2041 1924 1839 2019 2017 1912 1904 1818 1909 1828 1830 1917 1855 2022
    ## [75153] 1847 1848 2046 2320 1953 2007 1853 2024 1950 1934 1825 2100 1932 2043
    ## [75167]   11 2019 2105 2107 1922 2055 2046 2025 1938 2119 1927 1851 2110 2117
    ## [75181] 2023 2040 1947 1856 2030 2127 1955 2038 1928 2129 2115 1933 2122 2133
    ## [75195] 1911 1919 1952 2027 2002 1940 2056 2049 2121 2059 2003 2200 2158 2103
    ## [75209] 2022 2128 2145 2118 1953 2106 1941 2000 2014 2011 2206 2215 2034 2031
    ## [75223] 2029 2142 2151 2039 2112 1938 2110 2220 2100 2021 2019 2104 2221 2139
    ## [75237] 2056 2038 2111 2156 2029 2121 2156 2017 2032 2137 2216 2207 2036 2149
    ## [75251] 2051 2204 2224 2006 2221 2122 2236 2246 2031 2027 2147 2031 2211 2010
    ## [75265] 2116 2028 2006 2237 2327 2227 2040 2203 2158 2110 2246 2213 2054 2149
    ## [75279] 2120 2120 2225 2255 2056 2050 2228 2042 2112 2223 2147 2135 2359 2232
    ## [75293] 2220 2224 2305 2048 2249 2145 2054 2217 2242 2238 2045 2142 2145 2035
    ## [75307] 2220 2119 2328 2115 2306 2126 2141 2155 2141 2314 2227 2117 2144 2231
    ## [75321] 2206 2114 2226 2105 2115 2134 2155 2312 2122 2106 2247 2306 2116 2339
    ## [75335] 2352 2309 2305 2224 2310 2301 2144 2154 2159 2255 2201 2211 2341 2242
    ## [75349] 2156 2306 2305 2302 2149 2235    3 2348   22 2210   20 2320 2350  110
    ## [75363] 2303 2207 2304 2155 2250 2201 2358 2201 2215    6 2154 2213 2237 2317
    ## [75377] 2245 2159 2225 2308 2341 2216 2243 2342 2245 2345 2215 2332 2329 2339
    ## [75391] 2322 2354 2317   47 2225   56   44 2251   35 2247 2334 2326   19 2311
    ## [75405] 2253   29   41 2253   54 2313 2308  112 2258   53 2331 2335   54  114
    ## [75419]    5 2351  152   14  430   NA   NA   NA  113  632  755  829  824  820
    ## [75433]  645  801  658  701  726  916 1021  847  652  759  736 1024  753  758
    ## [75447]  715  731  933  838  852  814  717  832  847  751  850  738  812  827
    ## [75461]  905  805  907  909  824  848 1010  857  830  742  731  743  850  833
    ## [75475]  936  922  918 1017  903  736  920  822  858  910  847  956  849  947
    ## [75489]  806  753  859  953  816  838  829  926  848  803  816  933  752  831
    ## [75503] 1031  832 1137  846 1010 1055  942 1031  758 1019  752 1017  815  856
    ## [75517] 1038  930  959 1036 1134  841  945  951 1008 1008  910 1051  948  848
    ## [75531]  948  909  949  909  915  924 1019 1013 1057  849 1015 1007 1041  944
    ## [75545] 1004 1157 1046  832 1037  929  915 1105 1047  905  910 1029  956 1032
    ## [75559] 1022 1215 1055  924 1043  851 1211  848  925  927 1103  926 1049  852
    ## [75573] 1132 1020  856  952  858 1116 1002  955  944  903 1059 1119 1041 1043
    ## [75587] 1106 1053 1234  942  941 1038  942 1055 1137 1143 1021 1012 1119 1126
    ## [75601]  938 1043 1048  929 1104  922 1151  959 1024  925 1218  952  948 1018
    ## [75615] 1022 1149 1005  952 1041 1025  959 1050 1057 1041  940 1125 1110 1032
    ## [75629] 1149 1134  943 1045 1045 1142 1143 1228 1143 1044 1049 1121 1138 1043
    ## [75643] 1009 1015 1132  945 1117 1130 1211 1212 1125 1015 1146 1126 1019 1159
    ## [75657] 1011 1013 1212 1117 1045 1231 1240 1215 1143 1209 1206 1102 1107 1128
    ## [75671] 1110 1144 1150 1202 1005 1206 1230 1206 1009 1236 1343 1032 1148 1243
    ## [75685] 1151 1527 1209 1156 1242 1148 1227 1048 1129 1215 1030 1250 1258 1243
    ## [75699] 1125 1410 1231 1300 1142 1121 1229 1100 1556 1052 1130 1234 1153 1316
    ## [75713] 1107 1136 1111 1308 1320 1220 1320 1213 1349 1152 1308 1132 1134 1254
    ## [75727] 1205 1152 1139 1220 1312 1256 1202 1127 1207 1328 1219 1355 1257 1333
    ## [75741] 1406 1127 1155 1254 1314 1331 1355 1401 1429 1236 1348 1322 1316 1414
    ## [75755] 1204 1230 1355 1311 1301 1319 1255 1242 1216 1338 1202 1326 1200 1338
    ## [75769] 1355 1301 1244 1204 1259 1228 1315 1415 1329 1354 1343 1335 1327 1347
    ## [75783] 1434 1420 1404 1323 1236 1248 1340 1326 1308 1432 1359 1429 1422 1717
    ## [75797] 1311 1429 1351 1347 1310 1322 1416 1402 1322 1303 1342 1529 1418 1316
    ## [75811] 1421 1421 1331 1423 1316 1502 1310 1258 1519 1340 1344 1451 1336 1350
    ## [75825] 1401 1329 1311 1400 1515 1533 1452 1532 1404 1450 1501 1503 1356 1357
    ## [75839] 1506 1444 1512 1329 1430 1542 1456 1423 1522 1440 1345 1352 1403 1509
    ## [75853] 1351 1525 1603 1404 1605 1446 1419 1549 1611 1403 1632 1410 1611 1541
    ## [75867] 1526 1640 1556 1401 1454 1609 1440 1506 1442 1445 1433 1544 1516 1548
    ## [75881] 1519 1451 1552 1549 1428 1528 1536 1705 1455 1556 1628 1611 1610 1525
    ## [75895] 1438 1604 1556 1512 1450 1600 1636 1631 1648 1643 1547 1729 1550 1636
    ## [75909] 1708 1452 1501 1449 1749 1619 1522 1720 1557 1650 1552 1529 1536 1713
    ## [75923] 1707 1749 1657 1640 1602 1533 1739 1604 1623 1807 1814 1639 1714 1646
    ## [75937] 1816 1525 1638 1648 1718 1712 1707 1607 1744 1640 1709 1555 1704 1637
    ## [75951] 1639 1708 1713 1739 1712 1559 1642 1704 1612 1545 1805 1603 1620 1734
    ## [75965] 1936 1803 1637 1625 1750 1743 1726 1930 1600 1647 1752 1622 1716 1754
    ## [75979] 1746 1638 1746 1759 1752 1820 1719 1632 1740 1750 1817 1654 1650 1634
    ## [75993] 1754 1717 1828 1836 1648 1748 1624 1836 1728 1706 1804 1716 1706 1839
    ## [76007] 1756 1825 1821 1840 1644 1851 1909 1802 1841 1720 1707 1833 1710 1728
    ## [76021] 1848 1829 1735 1731 1838 1744 1711 1701 1817 1652 1806 1908 1854 1726
    ## [76035] 1848 1712 1746 1939 1825 1912 1702 1830 1830 1918 2000 1718 1737 1816
    ## [76049] 1853 1801 1859 1809 1812 1834 1901 1907 1832 1744 1921 1749 1951 1752
    ## [76063] 1857 1749 1930 1833 2009 1859 1913 2054 1851 1759 1819 1812 1945 2013
    ## [76077] 1742 1850 2024 1934 1745 2022 2007 1906 1818 1921 2146 1751 2026 1942
    ## [76091] 1806 1928 1817 1812 1807 1809 1947 2023 1828 1940 1856 1827 1908 2012
    ## [76105] 2013 1947 1953 1811 1953 2039 1807 2019 1939 1810 1928 2033 2000 1954
    ## [76119] 1932 1942 1950 2033 1901 1823 1835 1938 1953 1932 1957 1918 1850 2034
    ## [76133] 2031 2113 1845 1941 1949 2047 2057 1851 2003 2033 2058 2011 1914 2002
    ## [76147] 1904 1907 1957 2045 2026 1855 1933 1857 2018 1854 2126 2054 2126 1942
    ## [76161] 2029 1931 1917 2009 2046 2051 1948 2040 2100 1951 1938 2113 2058 2136
    ## [76175] 2015 2021 1927 2027 2142 2042 1959 2037 2107 2055 2009 2049 2302 2139
    ## [76189] 2251 2016 2102 2227 2015 1939 2138 1952 2118 2025 2010 2015 2040 2026
    ## [76203] 2032 2045 2120 2152 2136 1948 2028 2034 2105 2043 2202 2205 2159 1941
    ## [76217] 2025 2020 2141 2002 2123 2013 2124 2000 2223 2038 2257 2024 2039 2137
    ## [76231] 2207 2027 2226 2232 2106 2144 2336 2211 2121 2324 2049 2133 2022 2245
    ## [76245] 2047 2144 2005 2200 2248 2039 2143 2036 2050 2109 2304 2027 2047 2123
    ## [76259] 2220 2206 2124 2234 2121 2235 2046 2122 2106 2208 2204 2207 2312 2041
    ## [76273] 2300 2304 2133 2309 2240 2305 2042 2051 2036 2221 2246 2037 2118   39
    ## [76287] 2205 2132 2052 2255 2138 2126 2219 2209 2112 2228 2152 2222 2056 2221
    ## [76301] 2313 2243 2134 2248 2226 2250 2212 2221 2324 2253 2241 2115 2224 2146
    ## [76315] 2123  140 2256 2306 2400 2236 2251 2302 2300 2302 2150   48 2348 2225
    ## [76329] 2326 2116 2123 2158 2149 2238 2128 2245 2219    6 2159 2215   21 2350
    ## [76343] 2343   27 2333 2225 2347    6 2317 2313 2318 2157 2209 2256  121 2315
    ## [76357] 2330   19 2239 2355 2347 2326  100 2358   12 2342 2258 2244 2324 2311
    ## [76371] 2322 2251 2226 2240   32   40 2256 2240  100    5 2256  123 2247   23
    ## [76385]  143   25 2302 2350 2330   59   55 2257 2316   42  135   26    4 2308
    ## [76399]   59 2339 2332  109   30   32 2342    1 2341    5  126    4 2347   17
    ## [76413]    7  122   10  235  455  413  425   NA   NA   NA   NA   NA   NA  658
    ## [76427]  834  826 1012  732  645  816  702  834  716  748  844  849 1026  709
    ## [76441]  839  825  856  734  915  954  856  800  824  913  937  722  739  912
    ## [76455]  737  835  821  914  929  812  905  729  932  832 1033 1018  923  859
    ## [76469]  853  812  945  919 1005  744  946  920 1130 1005  818  835  913  928
    ## [76483] 1018 1148 1034  929 1058  948  922  947 1053 1037  954  948 1007  917
    ## [76497] 1000 1016 1013 1023  949 1017 1055  917  822 1003  857  850 1008 1114
    ## [76511]  908 1209  938  904 1016 1023  942  841 1004  913 1050 1040 1033 1036
    ## [76525]  908 1039  940 1045 1042 1008  850 1010 1134 1045 1029  928  924 1049
    ## [76539] 1240 1109 1008 1113 1137 1108 1023 1112 1009 1111 1151 1025  958  932
    ## [76553] 1052 1032 1131 1033 1013 1035 1204  924  957 1003 1006 1012 1042 1109
    ## [76567] 1146 1055  942 1057 1029 1015 1004 1116 1111 1019  920 1146  955  929
    ## [76581] 1103 1158 1054 1053  952 1203 1138 1000 1328 1102 1243 1331 1047 1135
    ## [76595] 1035 1000 1255 1151 1200 1154 1156 1117 1019 1202 1151 1008 1257 1122
    ## [76609] 1131 1227 1158 1146 1214 1222 1150 1025 1128 1307 1243 1050 1031 1155
    ## [76623] 1111 1045 1123 1215 1102 1217 1239 1203 1211 1139 1233 1250 1119 1202
    ## [76637] 1309 1232 1043 1240 1240 1204 1142 1233 1420 1105 1152 1045 1545 1135
    ## [76651] 1309 1123 1208 1142 1228 1154 1153 1356 1256 1145 1534 1234 1331 1322
    ## [76665] 1242 1215 1407 1133 1246 1253 1244 1504 1109 1336 1339 1347 1402 1401
    ## [76679] 1134 1313 1319 1200 1233 1417 1341 1403 1403 1338 1340 1351 1418 1221
    ## [76693] 1324 1252 1347 1242 1335 1410 1158 1324 1346 1401 1253 1437 1538 1412
    ## [76707] 1422 1337 1442 1435 1406 1311 1421 1254 1235 1330 1346 1318 1333 1310
    ## [76721] 1510 1433 1237 1400 1423 1310 1440 1242 1256 1409 1440 1416 1354 1439
    ## [76735] 1400 1543 1533 1313 1240 1408 1320 1440 1340 1516 1515 1322 1502 1435
    ## [76749] 1340 1513 1504 1329 1630 1511 1415 1407 1455 1459 1535 1336 1328 1446
    ## [76763] 1608 1527 1451 1352 1357 1512 1523 1544 1447 1403 1418 1528 1535 1557
    ## [76777] 1650 1437 1629 1551 1557 1511 1427 1605 1720 1612 1409 1555 1456 1519
    ## [76791] 1643 1433 1548 1600 1703 1452 1521 1748 1625 1701 1701 1544 1548 1643
    ## [76805] 1711 1623 1459 1549 1434 1641 1526 1632 1718 1625 1634 1734 1655 1618
    ## [76819] 1645 1735 1702 1657 1647 1625 1634 1642 1648 1542 1742 1641 1703 1602
    ## [76833] 1708 1742 1554 1736 1830 1713 1743 1741 1714 1641 1620 1607 1737 1732
    ## [76847] 1751 1648 1610 1542 1648 1611 1725 1559 1822 1737 1701 1901 1801 1621
    ## [76861] 1632 1617 1732 1938 1823 1651 1629 1757 1619 1758 1823 1723 1647 1728
    ## [76875] 1741 1809 1821 1759 1911 1652 1753 1712 1707 1832 1755 1620 1748 1727
    ## [76889] 1719 1759 1644 1902 1712 1826 1723 1741 1910 1849 1817 1626 1840 1654
    ## [76903] 1910 1904 1726 1740 1832 1854 1727 1742 1724 1918 1846 1834 1837 1845
    ## [76917] 1852 1857 1829 1853 1852 1714 1903 1836 1856 1846 1928 1825 1725 1852
    ## [76931] 1836 1815 1818 1720 1751 1737 1902 1821 1902 1901 1924 1802 1813 1907
    ## [76945] 1745 1832 1848 1825 1829 1915 1936 1803 2038 1807 2105 1937 1800 2016
    ## [76959] 1744 1936 2018 1807 1925 1746 1956 1938 2015 1907 2037 1923 1905 1910
    ## [76973] 1919 1937 2001 1942 1827 1941 2025 2024 1949 2041 1804 1805 1806 1843
    ## [76987] 1923 1822 1925 2033 1905 1810 1953 2009 2032 2043 1856 2046 2034 1820
    ## [77001] 1801 1919 1916 1858 2020 1952 1823 1907 1853 1816 2029 2116 1959 2108
    ## [77015] 1835 2107 2030 2045 2020 2047 1937 2004 2050 1911 2207 2234 1922 1958
    ## [77029] 1923 1901 2010 1920 2027 1958 2029 1904 1900 2035 2026 2118 2217 2134
    ## [77043] 1955 1918 2110 2111 2205 2125 2047 2157 2050 2000 1944 2128 1946 2234
    ## [77057] 2105 2201 2057 2032 2138 2126 2122 2148 2145 2028 2156 2207 2208 2208
    ## [77071] 2200 2147 2228 2050 2009 2154 2107 2033 2113 2347 2223 2311 2041 2224
    ## [77085] 2215 2215 2157 2118 2135 2041 2141 2211 2138   16 2204 2124 2039 2251
    ## [77099] 2233 2239 2158 2227 2209 2220   52 2315 2224 2057 2244 2301 2154 2316
    ## [77113] 2246 2343 2306 2337 2242 2117 2255 2311 2116 2106 2400 2319 2306 2310
    ## [77127] 2228 2343   10    9 2351 2339   21 2210  123 2338 2325 2231 2237 2216
    ## [77141] 2308 2347   22   28   52 2357 2259 2254   53   39   10   55   12   38
    ## [77155]   49 2303 2258 2338 2343 2350 2345    5 2347  503  448  439   NA   NA
    ## [77169]   NA  109  325  749  839 1020  638  852  734  735  844  847  811  708
    ## [77183]  838 1050  704  903  810  914  859  911  803  818  926  809  901  814
    ## [77197]  850  926  858  918  940 1016  911  904  938  756  851  938 1010  809
    ## [77211]  851  830  943  944  816  826  945  945  926  838  907  957 1010 1154
    ## [77225]  955 1017 1015  905  836 1007 1004 1023 1023  831 1020  836 1007 1033
    ## [77239] 1035  958  848 1020  852  910 1029 1027 1046 1222  958 1043  928  856
    ## [77253]  933  906 1228  953 1018  902 1035 1015  942 1038  936 1048  926 1230
    ## [77267] 1033  856 1109 1032 1008 1043 1057  852 1101 1113 1045 1039 1101 1020
    ## [77281] 1123 1106 1055 1158 1112 1102 1050 1019  920 1017 1056 1027 1022 1027
    ## [77295] 1144  952 1029 1020 1047 1124  932 1016 1018 1314 1045 1049 1129 1038
    ## [77309] 1034  937 1120 1141 1156 1011 1218 1037  950 1046 1148 1131 1102 1208
    ## [77323] 1150 1156 1157 1113 1211 1145 1155 1207 1153 1045 1200 1014 1153 1118
    ## [77337] 1205 1218 1022 1346 1202 1148 1202 1050 1124 1211 1225 1220 1222 1232
    ## [77351] 1034 1233 1154 1203 1236 1027 1232 1202 1028 1228 1039 1224 1140 1225
    ## [77365] 1228 1247 1145 1250 1244 1116 1419 1059 1440 1524 1118 1228 1058 1123
    ## [77379] 1526 1111 1237 1123 1227 1235 1209 1227 1458 1220 1110 1225 1253 1233
    ## [77393] 1256 1259 1206 1149 1356 1147 1322 1315 1208 1207 1312 1308 1239 1222
    ## [77407] 1231 1141 1118 1317 1401 1319 1255 1327 1151 1253 1143 1241 1324 1347
    ## [77421] 1324 1306 1316 1207 1350 1337 1156 1242 1253 1209 1325 1242 1220 1356
    ## [77435] 1215 1335 1257 1318 1336 1211 1416 1400 1351 1427 1322 1329 1405 1421
    ## [77449] 1336 1424 1430 1437 1453 1408 1443 1439 1350 1357 1430 1406 1448 1427
    ## [77463] 1306 1417 1300 1320 1253 1258 1501 1254 1321 1303 1451 1309 1424 1458
    ## [77477] 1507 1411 1404 1358 1441 1521 1510 1336 1412 1321 1538 1343 1501 1356
    ## [77491] 1459 1313 1401 1349 1454 1409 1438 1459 1442 1449 1419 1402 1349 1543
    ## [77505] 1340 1406 1438 1547 1438 1356 1420 1512 1454 1427 1510 1548 1538 1408
    ## [77519] 1412 1616 1449 1612 1607 1504 1437 1600 1553 1408 1604 1449 1509 1635
    ## [77533] 1616 1448 1515 1505 1518 1623 1527 1607 1631 1504 1608 1632 1458 1614
    ## [77547] 1703 1440 1550 1629 1641 1647 1509 1658 1539 1526 1539 1651 1441 1703
    ## [77561] 1658 1650 1632 1507 1516 1539 1649 1545 1525 1502 1621 1551 1608 1605
    ## [77575] 1507 1543 1548 1609 1652 1617 1646 1706 1716 1602 1726 1627 1712 1725
    ## [77589] 1629 1653 1721 1659 1731 1657 1555 1633 1539 1615 1725 1713 1648 1742
    ## [77603] 1648 1618 1725 1641 1658 1635 1733 1650 1648 1748 1631 1746 1740 1618
    ## [77617] 1938 1743 1732 1623 1739 1603 1628 1808 1638 1717 1758 1727 1626 1803
    ## [77631] 1724 1811 1835 1826 1648 1708 1805 1816 1616 1704 1743 1756 1650 1822
    ## [77645] 1704 1641 2003 1716 1705 1729 1809 1703 1806 1815 1619 1647 1700 1712
    ## [77659] 1846 1821 1649 1650 1716 1756 1829 1643 1815 1753 1742 1853 1648 1747
    ## [77673] 1707 1713 1851 1703 1848 1802 1851 1719 1813 1900 1729 1841 1709 1850
    ## [77687] 1729 1652 1717 1815 1909 1905 1714 1830 1805 1920 1735 1907 1718 1806
    ## [77701] 1933 1826 1808 1752 1846 1814 1906 1848 1924 1808 1902 1830 2059 1840
    ## [77715] 1745 1854 1927 1754 1759 2003 1846 1943 1919 1935 1853 1927 1942 1816
    ## [77729] 1800 2136 2006 1853 1950 1810 1943 1955 1923 1822 1828 1929 1810 1850
    ## [77743] 1942 1956 1957 1936 1806 1811 1853 1946 2009 1835 2023 1922 1832 1955
    ## [77757] 1836 2007 1940 1950 2003 1903 1851 1950 1845 1850 1850 1925 1856 1953
    ## [77771] 1829 1910 1915 2019 2015 1859 2032 1832 1925 1900 1935 2008 1942 1945
    ## [77785] 1941 1946 1849 1957 2030 1908 2013 1948 2053 2046 2023 1834 1927 2051
    ## [77799] 2030 1844 2011 2011 1855 1901 2107 1901 1929 1943 2026 2051 1902 2035
    ## [77813] 1929 1911 2101 1913 2029 2043 2036 2135 2025 1931 2112 2038 2038 2026
    ## [77827] 2102 2014 2104 2101 1925 2125 2138 1949 2011 2046 1954 2109 2057 2019
    ## [77841] 2111 2018 2116 2204 2048 2034 2012 2110 2132 2026 1942 2127 2104 1949
    ## [77855] 2132 2038 2024 2209 2107 2143 2015 2029 2025 2129 2022 2026 2057 2101
    ## [77869] 2041 2200 2217 2152 2059 1944 2150 2212 2109 2105 2229 2121 2234 2019
    ## [77883] 2146 2048 2113 2234 2020 2018 2148 2117 2236 2115 2034 2220 2210 2134
    ## [77897] 2218 2113 2053 2149 2043 2230 2130 2054 2229 2201 2233 2248 2109 2206
    ## [77911] 2122 2137 2155 2155   22 2126 2114 2136 2253 2325 2223 2137 2323 2129
    ## [77925] 2239 2228 2110   31 2252 2300 2130 2226 2159 2309 2255 2117 2250 2113
    ## [77939] 2110 2320 2252 2135 2215 2203 2231 2128 2147 2257 2323 2227 2143 2218
    ## [77953] 2232 2255 2202 2250 2158  151 2201 2330 2204   11 2340 2247    1 2316
    ## [77967] 2211 2322 2335 2351    6 2217    7 2354 2246 2357 2223 2214   27 2327
    ## [77981] 2323 2339 2329 2258 2308 2222  133 2235 2358 2257 2335 2212 2225 2217
    ## [77995] 2349 2345 2326 2324 2318 2234 2335 2216 2243   10 2322 2355   19 2317
    ## [78009] 2308 2346 2222 2211 2350 2358 2332  100   24 2333 2238 2348   47 2336
    ## [78023]   37   37   35   57   37 2251 2322   18   47 2324   50   10 2337 2347
    ## [78037]    5 2332 2351    7 2326   12  124 2359   22    9 2357   15  149   54
    ## [78051]  103  438  436  420  246   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [78065]   NA  436  647  801  827  845  843  647 1019  657  826  721  834  653
    ## [78079]  823  815  713  646  856  838 1033  923  834  811  716  716  726  835
    ## [78093]  744  752  801  844  859  902  758  756  904  824  808  716  932  905
    ## [78107]  744  810  855  919  913  942  807  829  744  751  909  900  842  812
    ## [78121]  735  933  927  951  817  944  851  858  758  753  801  912  757  825
    ## [78135]  943 1000  949  924  949 1130 1018  922  834  747  829  902  941  951
    ## [78149]  817 1034  825 1001 1023  827  957  958  953  858 1010  829 1147  941
    ## [78163] 1022  850  938 1022 1016 1013  840  909 1043  942 1156 1034  959  820
    ## [78177] 1019 1008 1025 1010  905  925  914 1027 1036  957 1033 1047  848 1057
    ## [78191] 1027 1033  856  949 1030 1229 1042  852 1043  944  943 1053 1229  906
    ## [78205] 1018  853  914 1055 1102 1039  851  847 1128 1048  945  859 1035 1237
    ## [78219]  921 1004 1110  941 1049 1235 1024 1037 1050 1041 1055 1033  932  921
    ## [78233]  916  958 1006  947  954 1122 1010  957  952 1031 1015  958 1040 1021
    ## [78247] 1145 1006 1056 1128 1058 1029  948  936  927 1124 1055 1027 1122 1033
    ## [78261] 1129 1032 1020 1143 1012 1155 1053 1145 1023 1204 1111 1052  958 1149
    ## [78275] 1001 1315  958 1018 1204 1129 1146 1056 1007 1207 1134 1051 1152 1048
    ## [78289] 1150 1052 1231 1142 1130 1057 1146 1011 1142 1227 1223 1105 1017 1202
    ## [78303] 1153 1026 1158 1209 1215 1210 1242 1223 1227 1214 1244 1132 1510 1209
    ## [78317] 1059 1220 1052 1041 1114 1137 1237 1242 1115 1211 1219 1229 1250 1542
    ## [78331] 1244 1104 1111 1127 1208 1213 1253 1430 1120 1237 1112 1257 1254 1238
    ## [78345] 1140 1209 1158 1306 1333 1202 1124 1233 1255 1312 1142 1144 1157 1200
    ## [78359] 1132 1328 1337 1225 1137 1253 1355 1315 1257 1319 1151 1155 1351 1331
    ## [78373] 1343 1405 1235 1153 1335 1328 1253 1310 1221 1345 1237 1203 1352 1201
    ## [78387] 1241 1152 1359 1315 1248 1343 1244 1155 1355 1344 1355 1412 1418 1441
    ## [78401] 1257 1313 1237 1334 1404 1345 1325 1421 1414 1448 1437 1335 1252 1258
    ## [78415] 1250 1309 1311 1450 1332 1242 1444 1410 1423 1348 1246 1405 1459 1406
    ## [78429] 1457 1311 1511 1300 1254 1304 1428 1318 1350 1441 1445 1331 1523 1357
    ## [78443] 1358 1334 1430 1425 1450 1500 1434 1345 1439 1312 1348 1515 1329 1412
    ## [78457] 1529 1431 1331 1340 1453 1323 1421 1330 1515 1543 1355 1424 1421 1552
    ## [78471] 1347 1349 1347 1516 1529 1435 1551 1343 1553 1442 1558 1403 1607 1558
    ## [78485] 1410 1415 1429 1529 1602 1606 1458 1533 1540 1607 1505 1557 1615 1501
    ## [78499] 1502 1607 1438 1415 1444 1456 1436 1619 1429 1625 1625 1612 1634 1454
    ## [78513] 1622 1656 1525 1638 1534 1516 1536 1558 1646 1642 1643 1540 1457 1650
    ## [78527] 1452 1626 1450 1655 1624 1642 1631 1712 1542 1501 1516 1722 1655 1542
    ## [78541] 1609 1539 1712 1653 1637 1549 1600 1650 1722 1630 1639 1736 1534 1538
    ## [78555] 1537 1716 1608 1601 1752 1616 1543 1600 1752 1655 1630 1643 1736 1730
    ## [78569] 1600 1751 1641 1654 1759 1748 1617 1630 1730 1605 1647 1601 1739 1552
    ## [78583] 1554 1741 1930 1730 1808 1559 1723 1634 1607 1808 1727 1716 1735 1626
    ## [78597] 1754 1748 1749 1752 1814 1655 1959 1632 1707 1829 1818 1821 1727 1701
    ## [78611] 1823 1835 1653 1753 1714 1820 1716 1706 1837 1821 1709 1708 1800 1850
    ## [78625] 1659 1658 1801 1814 1840 1713 1853 1841 1825 1857 1751 1705 1738 1838
    ## [78639] 1845 1854 1804 1709 1712 1843 1703 1744 1745 1914 1808 1825 1654 1648
    ## [78653] 1905 1802 1824 1807 1902 1848 1919 1821 1715 1758 1920 1852 1758 1922
    ## [78667] 1915 1815 1932 1949 1834 1845 1809 1803 1746 1920 1751 1735 1930 1942
    ## [78681] 1939 1825 1759 1801 1928 1955 1837 1900 1939 2103 1933 1858 1922 1746
    ## [78695] 1929 1744 1821 1756 2006 1749 1857 1944 1754 1942 1749 1925 1748 2012
    ## [78709] 1837 1818 1858 1943 1935 1858 1900 1914 1753 1857 1826 1941 1751 2014
    ## [78723] 2006 1947 1815 2016 1936 1828 2011 1859 1901 1822 2055 1858 2020 1839
    ## [78737] 1841 2009 2033 1857 1856 2013 1817 2043 1915 1836 2031 2033 1841 1828
    ## [78751] 1914 2007 1920 1953 1957 1948 2042 2035 2030 2059 1839 2009 2004 2004
    ## [78765] 1922 2047 1949 2033 1925 2058 1908 1938 1924 2057 2035 2050 2123 2010
    ## [78779] 1907 1926 1924 1853 2119 1939 1913 2101 1941 2038 1947 1932 2045 2040
    ## [78793] 2133 2011 2016 2104 2119 2104 2041 2101 1957 1933 2014 1954 2112 1952
    ## [78807] 2142 2140 2019 1933 2148 2156 2147 2108 2128 2147 2014 2158 2135 2051
    ## [78821] 2057 2108 1939 1957 2031 2146 2125 2149 2015 2008 2159 2046 2038 2019
    ## [78835] 2021 2210 2211 2158 2134 2021 2139 2150 2056 1955 2027 1956 2246 2129
    ## [78849] 2234 2015 2128 2110 2159 2333 2215 2042 2052 2035 2147 2013 2039 2203
    ## [78863] 2150 2144 2107 2213 2229 2225 2355 2129 2028 2025 2245 2039 2235 2110
    ## [78877] 2208 2138 2127 2248 2356 2050 2234 2243 2203 2124 2113 2236 2207 2137
    ## [78891] 2137 2245 2241 2131 2032 2300 2227 2101 2215 2141 2049 2120 2216 2239
    ## [78905] 2057 2230 2104 2051 2226 2250 2134 2209 2254 2143 2257 2346 2108 2300
    ## [78919] 2307 2314 2323 2309 2342 2146 2154 2151 2157 2256 2158 2158 2334 2231
    ## [78933] 2145 2239 2348 2338 2345 2328 2329 2322 2347 2351 2210 2345 2201 2320
    ## [78947] 2252   15 2200    8 2359 2328 2319 2204 2315 2338 2156 2224 2238 2204
    ## [78961] 2255 2241 2330 2351 2358   19   11 2335 2332 2249 2237 2326 2246 2236
    ## [78975]    3   16   22   28 2337   26 2339 2308 2257  102 2257   52 2254 2252
    ## [78989] 2300 2347  116 2334 2347 2359 2354 2348   29  155  158   41  418  418
    ## [79003]   NA   NA   NA   NA   NA  648  809  829  830 1004  801 1024  704  843
    ## [79017]  858  840  646  737  706  915  755  726  915  850  834  749  839  932
    ## [79031]  656  700  808  858  814  916  727  910  924  914  732  809  830  817
    ## [79045]  845  915  901  923  813  721  906  820  811  915  826 1017  850  904
    ## [79059]  918  741  809 1011  830  931  920  838  756  736  920  945  850 1004
    ## [79073]  801  845  925  957 1001  755  837  942 1120  931  914  943  812 1001
    ## [79087] 1009 1034  826  806 1008  943  910  927 1024  821  821  944  900  824
    ## [79101]  917  838  901 1024  955 1009 1021 1016 1203 1025  908  947 1019 1037
    ## [79115] 1048 1001 1004 1102  919 1036 1007 1155  828 1019  915 1028 1053 1038
    ## [79129]  909  901  917  959 1035 1039 1005  940 1041 1033 1017 1112 1039  914
    ## [79143]  929 1222  850  916 1012 1110 1030 1005 1016  913  855 1051 1116 1042
    ## [79157]  956  934 1018  857 1240 1112 1052  906 1121  930 1017 1105  949  911
    ## [79171] 1133 1235 1128 1048 1053 1051 1101 1017 1103  914 1042 1047  928 1117
    ## [79185] 1110 1148 1139 1024  949  954 1109 1119 1123 1046  928 1032 1039  954
    ## [79199] 1008  946 1006 1036 1022  926 1029 1042 1044 1149 1019 1005  933 1109
    ## [79213] 1041  958 1154 1036 1006 1141 1037 1202 1304 1229 1151 1131 1220 1131
    ## [79227] 1021 1152  957 1111 1140 1059 1204 1149 1133 1025 1207 1204 1204 1009
    ## [79241] 1215 1151 1207 1128 1210 1033 1054 1059 1212 1006 1153 1212 1117 1231
    ## [79255] 1008 1219 1157 1010 1022 1205 1028 1223 1227 1219 1230 1200 1222 1125
    ## [79269] 1041 1024 1154 1200 1515 1206 1125 1233 1123 1104 1046 1135 1539 1243
    ## [79283] 1234 1245 1221 1424 1224 1255 1103 1153 1040 1133 1128 1243 1129 1314
    ## [79297] 1301 1250 1201 1320 1206 1126 1254 1238 1218 1116 1309 1252 1143 1114
    ## [79311] 1138 1322 1133 1238 1139 1312 1144 1211 1256 1145 1316 1337 1308 1247
    ## [79325] 1322 1332 1349 1254 1132 1329 1154 1302 1339 1219 1238 1315 1210 1333
    ## [79339] 1257 1159 1349 1205 1211 1245 1359 1226 1253 1401 1407 1436 1244 1213
    ## [79353] 1408 1223 1343 1353 1411 1257 1401 1418 1410 1250 1413 1305 1222 1311
    ## [79367] 1436 1307 1330 1317 1242 1350 1425 1301 1348 1354 1443 1439 1330 1432
    ## [79381] 1333 1307 1400 1343 1244 1302 1459 1258 1517 1257 1322 1324 1338 1310
    ## [79395] 1446 1435 1439 1501 1455 1342 1457 1455 1517 1407 1319 1451 1511 1345
    ## [79409] 1333 1450 1353 1539 1525 1420 1401 1433 1501 1520 1320 1519 1503 1429
    ## [79423] 1542 1525 1612 1543 1409 1339 1403 1346 1558 1408 1605 1538 1416 1442
    ## [79437] 1541 1419 1430 1355 1414 1437 1420 1611 1534 1633 1405 1524 1503 1605
    ## [79451] 1604 1543 1550 1623 1504 1500 1444 1503 1518 1608 1636 1552 1509 1546
    ## [79465] 1517 1430 1633 1511 1458 1626 1630 1634 1458 1629 1628 1524 1652 1638
    ## [79479] 1445 1546 1631 1535 1644 1521 1653 1637 1640 1701 1658 1649 1542 1444
    ## [79493] 1541 1608 1639 1447 1512 1710 1600 1537 1655 1522 1642 1659 1726 1658
    ## [79507] 1702 1655 1510 1533 1642 1600 1735 1613 1653 1621 1717 1741 1628 1734
    ## [79521] 1743 1728 1659 1551 1759 1617 1750 1604 1701 1619 1800 1738 1738 1747
    ## [79535] 1804 1754 1705 1700 1635 1619 1924 1719 1644 1725 1751 1753 1749 1701
    ## [79549] 1559 1710 1641 1817 1813 1801 1609 1818 1819 1747 1702 1750 1819 1812
    ## [79563] 1720 1713 1603 1642 1623 1801 1638 1815 1626 1807 1713 1707 1829 1647
    ## [79577] 1813 1801 1637 1812 1647 1658 1737 1720 1726 1644 2020 1744 1822 1848
    ## [79591] 1817 1853 1706 1711 1812 1900 1715 1933 1855 1740 1732 1801 1715 1900
    ## [79605] 1656 1844 1751 1900 1843 1833 1840 1734 1835 1904 1812 1747 1703 1713
    ## [79619] 1913 1854 1724 1909 1736 1947 1718 1804 1815 1915 1755 1840 1902 1818
    ## [79633] 1806 1909 1933 1917 1842 1908 1906 1901 1951 1829 1814 1828 1920 1741
    ## [79647] 1952 1751 1942   NA 1816 1947 1949 2007 1816 1813 1848 1942 1934 1756
    ## [79661] 1933 1936 1946 1838 2126 1835 1948 1928 1750 1846 1853 1833 1950 2008
    ## [79675] 1925 1913 2007 1947 1943 1759 2010 1902 1933 1934 1835 1912 2008 1829
    ## [79689] 1952 2028 2022 1916 2020 1920 2011 2023 1907 1803 1826 1937 2033 2001
    ## [79703] 2011 1858 1830 1914 1906 1927 2006 1823 2039 2036 1900 1950 1818 2018
    ## [79717] 1828 1929 1826 2026 2010 1940 1936 2010 2029 1934 2020 1856 2057 2053
    ## [79731] 1943 1856 1942 1920 1938 1954 2013 1855 2102 2030 2058 2044 1955 2000
    ## [79745] 2044 1937 2036 2100 2047 2057 1927 1918 2109 1912 2047 1948 1956 2112
    ## [79759] 2105 1917 1954 2050 2106 1958 2143 1946 1945 2150 2123 2010 2126 2134
    ## [79773] 2141 2057 2154 2134 2003 2010 2025 2008 2125 2128 2118 2034 2145 2126
    ## [79787] 2024 2201 2048 2203 2154 2006 2125 2026 2146 2004 2203 2046 1955 2006
    ## [79801] 2133 2040 2030 2013 2147 2035 2152 2145 2036 2024 1959 2203 2109 2149
    ## [79815] 2055 2137 2136 2221 2225 2208 2138 2215 2214 2126 2032 2053 2206 2111
    ## [79829] 2039 2038 2219 2229 2022 2113 2240 2117 2352 2010 2204 2059 2046 2256
    ## [79843] 2239 2052 2234 2112 2224 2219 2138 2205 2119 2106 2232 2308   27 2243
    ## [79857] 2259 2247 2111 2141 2226 2256 2118 2314 2210 2134 2253 2147 2207 2256
    ## [79871] 2247 2154 2250   31 2128 2129 2205 2155 2211 2132 2212 2134 2239 2110
    ## [79885] 2242 2141 2208 2300 2137 2318 2222 2157 2247 2129 2149 2225 2245 2346
    ## [79899] 2317 2244 2323 2148 2327 2201 2316 2318 2131 2215 2157 2238 2345 2202
    ## [79913]    2 2341 2151 2359 2213   48 2355 2240 2330 2328 2226    8 2348 2356
    ## [79927] 2258   10 2225   18 2217   15    3 2316   20 2355   50 2354 2223 2339
    ## [79941] 2357 2329 2322 2343   24 2256    8 2359 2245 2303 2317 2252 2400   42
    ## [79955]    9 2336 2359 2258 2352   10  126   17 2312  126  105   56   35   53
    ## [79969]   31   20  115 2325  106 2339 2358 2315 2313 2339 2349 2337  219   30
    ## [79983]    7    1   18  243   26   24  157  100  445  438  445   NA   NA   NA
    ## [79997]  129  703  743  907  815  920  918  719  707  907  857  757  744  906
    ## [80011]  727  813  841  829  714  743  721  820  837  815  857  922  712 1133
    ## [80025]  830  751 1006 1053  935  942  951  746  751 1056  736  721  743  923
    ## [80039] 1002  807  944  955  835  839  757  911  917  951  853  945  846  830
    ## [80053]  858  822  826  745 1043  942  840  930  925  853  938  813  756  903
    ## [80067]  825  958  821  903  846 1202  953  813 1037 1018 1029  817  959  910
    ## [80081]  834  950 1038 1019 1037  803  851  851 1223 1042  853 1032 1053  919
    ## [80095] 1036  949  849 1005  900 1021  939 1024  958  832 1103  948  919 1012
    ## [80109]  832 1058 1207  853 1101 1050  910 1114  906 1027 1042  839 1116  919
    ## [80123]  911 1013 1112 1142 1006 1055  856 1030 1256 1030 1047 1228  926 1134
    ## [80137]  948  913  943 1051 1121 1032  904 1047  916  927 1136 1139  926 1017
    ## [80151]  924 1132 1139 1137 1138 1111 1129 1023 1046 1152 1100 1138 1123 1110
    ## [80165] 1327 1048  930 1006 1127 1034 1014 1018 1001 1024 1059 1005  950 1045
    ## [80179] 1003  959 1051 1008 1034 1015 1029  949 1035 1039 1106 1204  958 1033
    ## [80193] 1157 1048 1132 1128  959 1042 1137 1109 1140 1030 1132 1346 1055 1214
    ## [80207] 1024 1123  959 1215 1216 1409 1149 1007 1230 1044 1156 1220 1136 1108
    ## [80221] 1057 1211 1239 1050 1202 1051 1120 1228 1231 1132 1253 1027 1110 1101
    ## [80235] 1238 1242 1044 1046 1237 1225 1221 1138 1307 1241 1307 1233 1030 1300
    ## [80249] 1042 1309 1156 1051 1508 1050 1125 1316 1050 1221 1213 1251 1332 1536
    ## [80263] 1103 1054 1228 1320 1318 1139 1236 1224 1114 1253 1231 1230 1215 1102
    ## [80277] 1232 1214 1158 1300 1305 1131 1310 1120 1122 1128 1458 1339 1350 1314
    ## [80291] 1121 1306 1245 1326 1319 1133 1232 1327 1138 1309 1344 1156 1304 1341
    ## [80305] 1418 1309 1300 1205 1325 1238 1418 1401 1227 1232 1336 1447 1257 1222
    ## [80319] 1236 1247 1205 1431 1302 1221 1221 1434 1213 1359 1233 1420 1324 1454
    ## [80333] 1357 1229 1231 1420 1221 1335 1404 1230 1438 1433 1501 1339 1331 1429
    ## [80347] 1309 1346 1500 1444 1447 1344 1303 1332 1256 1341 1309 1325 1257 1449
    ## [80361] 1417 1333 1436 1438 1529 1307 1538 1516 1447 1404 1508 1322 1551 1444
    ## [80375] 1424 1428 1439 1440 1340 1549 1349 1345 1547 1534 1525 1324 1359 1458
    ## [80389] 1504 1426 1558 1433 1355 1527 1407 1443 1539 1549 1539 1351 1351 1425
    ## [80403] 1356 1508 1439 1353 1554 1551 1419 1521 1526 1556 1409 1533 1547 1414
    ## [80417] 1511 1405 1629 1654 1530 1449 1606 1708 1511 1557 1543 1545 1442 1626
    ## [80431] 1556 1409 1608 1514 1504 1506 1436 1610 1501 1512 1708 1703 1551 1430
    ## [80445] 1546 1440 1441 1547 1726 1710 1608 1537 1453 1648 1556 1637 1509 1652
    ## [80459] 1545 1657 1554 1658 1626 1502 1601 1750 1646 1649 1642 1651 1514 1645
    ## [80473] 1746 1542 1523 1738 1603 1513 1635 1707 1547 1758 1709 1757 1806 1814
    ## [80487] 1558 1639 1620 1656 1723 1620 1641 1805 1727 1745 1617 1603 1546 1805
    ## [80501] 1708 1636 1633 1556 1705 1748 1601 1700 1643 1751 1649 1805 1733 1810
    ## [80515] 1611 1940 1747 1726 1640 1841 1813 1736 1757 1748 1645 1742 1624 1631
    ## [80529] 1830 1628 1614 1723 1844 1750 1808 1752 1652 1819 1637 1723 1647 1854
    ## [80543] 1735 1755 1749 1754 1732 1911 1624 1834 1702 1821 1759 1818 1649 1722
    ## [80557] 1842 1846 1644 1748 1802 1836 1628 1903 1724 1726 2030 1640 1849 1823
    ## [80571] 1824 1845 1821 1734 1715 1752 1828 1809 1935 1947 1737 1747 1752 1859
    ## [80585] 1739 1857 1907 1924 1859 1851 1955 1748 1811 1919 1846 1952 1829 1730
    ## [80599] 1851 1858 1916 2012 1741 1832 1819 2035 1855 1815 1744 2119 1924 1749
    ## [80613] 2002 1958 1922 1938 1901 1827 1737 1750 2011 1930 1801 1745 2016 1920
    ## [80627] 1749 1911 1927 1820 1953 1959 1857 1822 1837 1848 2002 1939 1906 1756
    ## [80641] 1838 1905 1845 1951 1815 2045 2010 1951 1947 2022 1951 1806 2041 1835
    ## [80655] 1937 1937 1828 1910 1849 1842 1900 2021 1833 1947 1935 1816 2026 1902
    ## [80669] 2013 1927 1918 2003 2005 2056 2036 1830 1940 2024 1850 1849 1855 1853
    ## [80683] 1941 1907 1927 1944 2050 2038 2037 1933 2044 2046 2029 2021 2021 1958
    ## [80697] 1929 1909 2114 2103 2053 1902 2114 2045 2120 2018 2119 1926 1921 2138
    ## [80711] 1926 2124 2115 1926 2120 2029 2007 2002 2109 1946 1939 2133 2045 2042
    ## [80725] 2053 2027 2011 2052 2119 2127 2028 2021 2102 2047 1955 2133 2002 1926
    ## [80739] 2040 2152 2023 2030 1943 2055 2158 2006 2118 2128 2132 2109 2217 2201
    ## [80753] 2115 2129 2203 2138 2036 2022 2125 2059 2009 2100 2008 2014 2023 2103
    ## [80767] 2235 2024 1956 2003 2007 2213 2207 2209 2200 2158 2147 2117 2016 2022
    ## [80781] 2219 2220 2135 2132 2153 2227 2106 2218 2104 2229 2104 2144 2158 2042
    ## [80795] 2127 2246 2235 2209   17 2225 2040 2054 2049 2137 2257 2207 2053 2225
    ## [80809] 2305 2045 2146 2129 2205 2134 2049 2203 2249 2239 2059 2242 2131 2332
    ## [80823] 2221 2148 2313 2127 2249 2250  141 2221 2104 2149 2233 2143 2119 2255
    ## [80837] 2317 2207 2235 2155 2227 2117 2155 2141 2203 2256 2303 2238 2342 2147
    ## [80851] 2141 2107 2237 2349 2127 2212 2133 2300  136 2208 2228 2201 2213 2125
    ## [80865] 2228 2130    5 2218 2327 2355 2330 2257 2351 2200 2153 2141 2255 2156
    ## [80879]    8 2219   25 2141 2238   30    4 2131   31   32 2214 2300 2336 2154
    ## [80893] 2247 2306 2205  145 2240 2341 2314  103 2230 2323   46   28 2331 2324
    ## [80907] 2202   46   41    8 2247 2314   52 2216   26 2239 2347 2249   43 2330
    ## [80921] 2353 2214    3   20 2308   53 2309 2247 2347    6 2338 2355   11 2345
    ## [80935]   38 2258 2301 2252   38   34  114   56 2256 2314   50   28   59 2318
    ## [80949] 2340 2337   40 2326 2358 2400 2358   23  136   26 2345   12  156    1
    ## [80963]   24  206   16   15    4    1  200   27   29   37  503  505  515   NA
    ## [80977]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [80991]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [81005]   NA   NA   NA   NA   NA   NA  753  658  837  825 1033  853  849  831
    ## [81019]  702  703  735  717  651  842  809  805  839  708  723  854 1109  826
    ## [81033]  929  912  721  754  816  859  912  725  850  845  856  802  817  714
    ## [81047]  831  721  903  749  738  817  806  744  818  739  925  925 1001  819
    ## [81061]  806  911  826  857  846  941  922  912  846  933  915  930  749 1142
    ## [81075]  903  900  931  816  808  832  841  945  915  949 1026  926  756 1016
    ## [81089] 1015  945  813 1009  845 1021  904  955 1021  852  953 1012  930  908
    ## [81103] 1017  837  919 1228  913 1012  943  908 1036 1004 1111 1020 1053 1044
    ## [81117] 1036 1044  843  935 1035  843 1037  914 1019 1029 1031  924 1033 1236
    ## [81131] 1057 1037  907  923 1004  906  953 1039 1013 1103  909 1107  944 1030
    ## [81145]  925  944 1254  924 1007 1123 1041 1057 1014 1257  930 1107 1116 1049
    ## [81159]  953 1053 1110 1110 1046 1024 1050 1041  959 1021 1132  957  938 1103
    ## [81173] 1029 1033 1007 1131 1027 1035  936 1032 1027 1046  927 1023 1110  951
    ## [81187] 1039  922 1052 1040 1117  937 1114 1136 1144 1101 1140 1030 1144 1034
    ## [81201] 1125 1059 1211 1046 1343 1102 1142 1040 1103 1215 1155 1224 1156 1046
    ## [81215] 1223 1144 1118 1028 1204 1113 1006 1203 1111 1052 1131 1051 1140 1034
    ## [81229] 1215 1214 1009 1118 1108 1156 1026 1123 1212 1024 1118 1209 1116 1234
    ## [81243] 1415 1221 1300 1238 1136 1446 1247 1241 1037 1100 1041 1309 1248 1129
    ## [81257] 1300 1258 1116 1225 1230 1227 1509 1112 1156 1244 1124 1101 1259 1242
    ## [81271] 1238 1224 1206 1304 1219 1159 1207 1233 1217 1243 1315 1152 1133 1201
    ## [81285] 1120 1328 1249 1157 1132 1327 1223 1319 1332 1145 1327 1256 1148 1157
    ## [81299] 1316 1237 1125 1318 1344 1231 1228 1246 1307 1200 1349 1221 1358 1338
    ## [81313] 1408 1150 1254 1238 1551 1240 1226 1227 1208 1233 1255 1338 1352 1219
    ## [81327] 1330 1342 1303 1422 1335 1358 1337 1350 1424 1403 1255 1232 1320 1312
    ## [81341] 1235 1419 1235 1439 1443 1417 1417 1354 1315 1427 1303 1254 1330 1441
    ## [81355] 1339 1408 1443 1433 1309 1421 1300 1503 1300 1311 1338 1427 1517 1447
    ## [81369] 1313 1504 1415 1449 1459 1303 1444 1426 1452 1313 1355 1413 1334 1525
    ## [81383] 1329 1426 1437 1410 1357 1337 1527 1359 1432 1414 1604 1410 1533 1445
    ## [81397] 1512 1525 1512 1609 1630 1607 1426 1418 1436 1518 1413 1548 1541 1608
    ## [81411] 1421 1603 1454 1455 1448 1602 1605 1518 1415 1426 1448 1542 1448 1430
    ## [81425] 1636 1538 1523 1656 1614 1636 1523 1529 1649 1623 1443 1505 1623 1642
    ## [81439] 1621 1701 1700 1632 1642 1735 1622 1729 1630 1715 1507 1705 1636 1707
    ## [81453] 1650 1727 1734 1616 1534 1734 1717 1714 1547 1620 1602 1727 1729 1558
    ## [81467] 1739 1655 1653 1720 1544 1731 1938 1730 1627 1807 1956 1755 1749 1813
    ## [81481] 1759 1634 1708 1812 1630 1651 1643 1655 1656 1707 1759 1656 1841 1746
    ## [81495] 1659 1809 1731 1626 1852 1826 1743 1824 1743 1734 1716 1810 1849 1840
    ## [81509] 1710 1807 1850 1734 1841 1853 1833 1846 1818 1739 1711 1812 1736 1725
    ## [81523] 1902 1820 1856 1739 1929 1722 1811 1935 1923 2120 1909 1833 1802 1750
    ## [81537] 1800 1852 1945 1901 1758 1948 2007 2056 1744 1948 1947 2011 1855 1756
    ## [81551] 1838 1923 1952 1844 1923 1921 2022 1924 1820 1941 2024 1942 2025 2133
    ## [81565] 1959 2054 1845 2100 2053 2022 2029 2042 1915 1914 1908 2115 2056 2045
    ## [81579] 2113 1951 2008 2133 2136 2138 2018 1918 2025 2024 2144 2141 2100 2003
    ## [81593] 2148 2200 2139 2158 2209 2058 2025 2021 2149 2229 2208   11 2200 2049
    ## [81607] 2152 2109 2132 2139 2047    4 2201 2107 2236 2208 2026 2048 2238 2106
    ## [81621]   20 2219 2123 2126 2247 2222 2048 2304 2145 2339 2343 2210 2313 2219
    ## [81635] 2235 2345   38 2333 2329   11 2342   31  453  440  749  850 1023  851
    ## [81649] 1054  812  712  750  749  904  905  813  833  754  807  838  911  850
    ## [81663]  925 1138  945  930 1005  903  812 1002  832  841  816  959  833 1200
    ## [81677] 1000  929 1020  950 1029  947  826 1004 1005  904  937  822 1038 1226
    ## [81691] 1051  922  908 1034 1103 1031 1024 1030 1248 1057 1006 1110 1029  933
    ## [81705] 1052 1120 1122 1018  957 1314  942 1049 1108 1039 1055  951 1017  952
    ## [81719] 1027  917 1035 1145 1032 1052 1012 1011  932 1150 1125 1017 1145 1132
    ## [81733] 1051 1058 1334 1341 1102 1009 1049 1129 1053 1059 1019 1215 1151 1150
    ## [81747] 1051 1110 1210 1020 1234 1053 1106 1212 1203 1220 1028 1225 1206 1026
    ## [81761] 1150 1218 1044 1243 1215 1238 1219 1227 1039 1448 1035 1211 1246 1102
    ## [81775] 1240 1226 1431 1246 1223 1220 1300 1225 1245 1105 1211 1547 1253 1208
    ## [81789] 1254 1148 1120 1152 1126 1322 1143 1131 1300 1331 1216 1109 1307 1304
    ## [81803] 1125 1203 1342 1327 1320 1237 1145 1319 1346 1317 1307 1201 1255 1218
    ## [81817] 1337 1224 1412 1309 1207 1244 1211 1353 1337 1351 1210 1334 1206 1416
    ## [81831] 1442 1404 1321 1400 1252 1233 1339 1322 1306 1412 1414 1242 1246 1310
    ## [81845] 1434 1415 1349 1436 1336 1351 1233 1258 1347 1401 1410 1313 1409 1516
    ## [81859] 1416 1259 1352 1448 1326 1523 1343 1512 1324 1315 1425 1459 1446 1448
    ## [81873] 1410 1343 1536 1405 1437 1601 1353 1510 1449 1328 1401 1417 1350 1339
    ## [81887] 1424 1528 1357 1526 1336 1427 1344 1411 1423 1528 1419 1452 1420 1534
    ## [81901] 1543 1527 1607 1411 1517 1358 1548 1415 1622 1504 1433 1636 1546 1500
    ## [81915] 1548 1430 1440 1615 1449 1455 1427 1505 1431 1650 1440 1445 1610 1626
    ## [81929] 1449 1502 1543 1707 1704 1530 1606 1535 1436 1444 1630 1534 1519 1621
    ## [81943] 1602 1709 1646 1710 1604 1619 1716 1616 1647 1647 1623 1523 1740 1636
    ## [81957] 1618 1636 1718 1738 1718 1616 1741 1530 1547 1634 1638 1715 1732 1731
    ## [81971] 1650 1730 1642 1729 1822 1644 1629 1607 1950 1637 1636 1631 1730 1708
    ## [81985] 1631 1749 1937 1742 1814 1740 1706 1619 1627 1715 1810 1742 1731 1559
    ## [81999] 1742 1749 1750 1618 1757 1717 1806 1810 1809 1630 1818 1651 1806 1639
    ## [82013] 1711 1756 1703 1627 1705 1812 1819 1611 1614 1654 1716 1848 1800 1719
    ## [82027] 1823 1623 1901 1644 1702 1819 1644 1702 1649 1828 1741 1816 1859 1907
    ## [82041] 1756 1654 1801 1843 1848 1842 1756 1805 1734 1821 1905 1846 1807 1819
    ## [82055] 1902 1719 1843 1924 1811 1902 1808 1857 1904 1855 1850 1731 1830 1908
    ## [82069] 1825 1809 2134 1727 1854 1909 1931 1744 1831 2119 1919 1751 1742 1926
    ## [82083] 1740 1800 2002 1901 1745 1747 1830 1851 2019 2003 1849 1842 1948 1910
    ## [82097] 1748 1817 2013 1850 1954 1945 1811 1835 1802 2015 1948 1933 1809 1946
    ## [82111] 1836 1752 2030 2024 2008 1853 2002 1835 1844 1901 1830 2031 1810 1919
    ## [82125] 2006 1918 2005 1939 1818 1935 1959 2046 1903 1955 1921 2032 1903 1858
    ## [82139] 2029 2050 1948 2032 1908 1847 1840 2009 2119 1917 1845 1949 2057 2047
    ## [82153] 1905 2015 1926 2119 2037 2004 2057 2013 1947 2041 1918 1929 2119 2101
    ## [82167] 2058 2141 2011 1938 1932 2117 2130 2122 2030 2152 2127 2047 2114 2034
    ## [82181] 2113 2003 2028 2131 2055 1949 2013 2017 2122 2155 2027 2146 2215 2058
    ## [82195] 2202 2206 2005 2118 2158 2009 2006 2228 2225 2348 2132 2245 2156 2156
    ## [82209] 2052 2216 2156 2040 2037 2058 2149 2200 2214   11 2116 2130 2245 2030
    ## [82223] 2213 2037 2139 2208 2046 2113 2205 2230 2211   25 2119 2125 2101 2129
    ## [82237] 2235 2246 2211 2035 2123 2239 2133 2216 2244 2047 2249 2105 2243 2231
    ## [82251] 2123 2302 2126 2148 2317 2133 2138 2148 2150 2326 2143 2240 2340 2327
    ## [82265] 2341 2248 2157 2254 2215 2312 2153 2157 2253 2349 2251  155    5   10
    ## [82279] 2218 2344   42   52 2358 2257   16 2328   20   19   17   25   28 2307
    ## [82293]   29 2245 2251 2333 2331   26 2347 2338    5 2358  432  446  445  457
    ## [82307]  636  753  828 1026  831  814  943  737  840  656  732  836  741  754
    ## [82321]  857  844 1042  717  827  718  732  907  821  808  849  847  853  909
    ## [82335]  851  718  814  728  732  906  745  733  923  856  757  836  846  931
    ## [82349]  910  823  914  740  908 1004 1008  926  937  852  901  747  934  906
    ## [82363]  915 1002  918  830  802  817 1019  833 1031  950  941  836  831 1157
    ## [82377]  826  952 1012 1033  949  849 1154  841 1033  826  920  900 1009  942
    ## [82391]  957 1028 1004  938 1002  927 1043 1015 1040 1212  904 1011 1023  904
    ## [82405]  857  902 1020 1013 1024 1034 1022  849 1237  956  923 1241 1029 1046
    ## [82419] 1031  917 1103 1046  855  947 1019  952 1116 1108  903 1040 1028 1042
    ## [82433] 1054 1055 1117  911 1025  905 1048  932 1046 1050 1103 1003 1114  934
    ## [82447]  949 1315  948 1009  951 1159 1028 1012 1030 1013 1013  946  952 1023
    ## [82461] 1039 1001 1026 1000  944 1049  935  933 1005 1032 1053 1131  956 1033
    ## [82475] 1115 1039 1143 1123 1141 1155 1055 1005 1355 1042 1104 1123 1046 1128
    ## [82489]  951 1143 1211 1138 1129  954 1131 1110 1048 1132 1050 1159 1131 1026
    ## [82503] 1208 1051 1002 1150 1132 1137 1208 1205 1157 1119 1156 1226 1159 1207
    ## [82517] 1159 1030 1202 1141 1428 1229 1232 1043 1121 1047 1236 1048 1444 1237
    ## [82531] 1104 1430 1230 1216 1226 1104 1533 1215 1255 1306 1150 1249 1258 1102
    ## [82545] 1109 1147 1148 1120 1256 1326 1244 1215 1140 1157 1122 1301 1300 1125
    ## [82559] 1321 1117 1219 1320 1323 1411 1239 1132 1406 1341 1253 1343 1314 1145
    ## [82573] 1149 1331 1225 1148 1252 1236 1334 1218 1217 1343 1255 1154 1238 1353
    ## [82587] 1334 1211 1347 1330 1317 1216 1216 1304 1403 1324 1352 1408 1417 1259
    ## [82601] 1325 1419 1234 1321 1409 1500 1416 1325 1301 1422 1253 1304 1256 1437
    ## [82615] 1247 1353 1503 1428 1254 1421 1436 1311 1326 1305 1310 1458 1442 1400
    ## [82629] 1512 1459 1323 1450 1434 1309 1424 1414 1533 1359 1354 1321 1523 1331
    ## [82643] 1410 1450 1512 1419 1510 1557 1420 1533 1404 1341 1344 1435 1506 1335
    ## [82657] 1530 1542 1504 1532 1446 1354 1502 1504 1548 1527 1441 1531 1509 1547
    ## [82671] 1532 1459 1411 1631 1612 1443 1419 1409 1411 1619 1442 1409 1508 1614
    ## [82685] 1423 1547 1447 1507 1512 1406 1517 1515 1654 1524 1604 1619 1616 1456
    ## [82699] 1425 1432 1614 1530 1525 1629 1642 1614 1627 1712 1659 1515 1712 1547
    ## [82713] 1502 1615 1652 1652 1540 1457 1624 1628 1519 1613 1532 1518 1619 1527
    ## [82727] 1704 1651 1607 1647 1535 1631 1643 1600 1732 1711 1609 1722 1545 1642
    ## [82741] 1718 1725 1620 1727 1644 1637 1602 1647 1553 1739 1556 1602 1728 1735
    ## [82755] 1734 1732 1623 1745 1940 1745 1704 1724 1630 1546 1938 1733 1734 1626
    ## [82769] 1747 1739 1733 1715 1802 1708 1708 1731 1630 1603 1714 1814 1750 1812
    ## [82783] 1624 1742 1700 1648 1652 1808 1821 1821 1638 1639 1703 1640 1825 1700
    ## [82797] 1707 1805 1643 1709 1836 1806 1906 1640 1850 1721 1731 1749 1656 1651
    ## [82811] 1800 1836 1850 1647 1754 1725 1851 1845 1656 1738 1847 1708 1739 1703
    ## [82825] 1717 1736 1724 1857 1705 1806 1652 1848 1818 1703 1858 1837 1712 1808
    ## [82839] 1705 1838 1902 1702 1927 1756 1834 1851 1753 1930 1759 1923 1833 1905
    ## [82853] 1810 1800 1751 1855 1823 1831 1908 1953 1928 1904 1750 2119 1905 1930
    ## [82867] 1840 1726 1906 1951 1816 1813 1903 1847 1855 1746 1829 1752 1946 1837
    ## [82881] 1759 1927 1815 2001 1934 1814 1843 1919 1805 1947 1838 1809 1755 1958
    ## [82895] 1945 1818 2002 2001 1800 2012 2003 1759 2011 1847 1810 1903 1817 1953
    ## [82909] 1937 1905 1902 1951 1848 1813 1839 2001 1917 1832 1836 2027 1934 1926
    ## [82923] 2015 1820 2016 2002 2009 2001 1925 1946 1856 1916 2047 2031 2018 2034
    ## [82937] 2010 2006 2053 1934 2038 1839 1858 2104 2015 1855 1907 1951 1916 2012
    ## [82951] 1924 1905 2044 2027 2053 2023 2057 2054 1916 1908 1918 2021 1924 2124
    ## [82965] 2050 1920 1956 1914 2121 2108 1956 2056 2112 1951 2131 2126 2010 2014
    ## [82979] 2103 2015 2045 2055 1947 2125 2042 2135 2025 2021 2031 2126 1950 2100
    ## [82993] 2134 1947 2117 2024 1946 1956 2122 2137 2131 2152 2124 2124 2227 1954
    ## [83007] 2048 2156 2010 2108 2107 2126 2048 2214 2045 2202 2139    2 2110 2057
    ## [83021] 2217 2114 2154 2019 2244 2054 2105 2204 2206 2149 2151 2148 2029 2037
    ## [83035] 2025 2106 2227 2218 2231 2205 2132 2150 2105 2131 2227 2233 2222 2056
    ## [83049] 2217 2108 2200 2133 2103 2230 2227 2206 2235 2044 2055 2135 2048 2150
    ## [83063] 2246 2153 2236 2124 2221 2249 2125 2239 2232 2229 2244 2155 2129   47
    ## [83077] 2254 2110 2243 2129 2244 2204 2315 2118 2336 2124 2334 2232 2345 2245
    ## [83091] 2342 2159 2346 2240 2321 2337  127 2149 2133 2338 2352   17 2204 2322
    ## [83105] 2339 2254 2320 2254 2326    1 2205 2349 2214 2321 2312 2320 2324 2225
    ## [83119] 2258 2211 2219 2222 2256 2351 2357   12 2348 2219 2357 2259    1 2357
    ## [83133]   48 2254   13   17  207   18 2326    7 2248   23 2315 2348 2259   31
    ## [83147] 2254 2315 2323   59  126 2336 2352 2352 2344 2351 2343  423  430   NA
    ## [83161]   NA   NA  446  443  636  749  845 1005  734  826  648  825  827  748
    ## [83175]  712  645  805  846  742  733  828  841  721  718  724  709 1041  717
    ## [83189]  724  731  818  827  900  749  925  857  851  853  912  810  759  804
    ## [83203]  727  857  855  855 1007  823  815  856  907  751  931  909  853  907
    ## [83217]  910  838  951  759  750  930  837  845  813  943  818  836  802  903
    ## [83231]  811  818  945 1009  940  935 1023 1018 1134  924 1015  827 1005 1010
    ## [83245]  944  833  934  914 1005  819 1000  952 1225  848  808 1004 1040  844
    ## [83259]  849 1020 1007  953  824  911 1021  819 1012 1038  828 1033  943 1027
    ## [83273]  927  904  829  904 1015 1034 1037 1008  951 1224 1025 1003 1034  845
    ## [83287]  916  903  943  921 1042 1051  949  854 1026 1048 1029 1246 1044 1020
    ## [83301] 1044 1116  923 1035  944 1041 1052 1043  930  936 1010 1012 1041 1101
    ## [83315] 1059 1111  930 1312 1056 1033 1022 1112 1250 1052  926 1142 1041  952
    ## [83329]  917 1003 1003  938 1109  933 1044  942 1008  946 1010  933  936  931
    ## [83343]  949 1036 1130  941  940 1007 1037 1120 1114 1044 1119 1128 1011 1105
    ## [83357] 1200 1036 1145 1149 1034 1051  952 1202 1155 1141  959 1001 1157 1203
    ## [83371] 1049 1102 1128 1119 1010 1142 1333 1015 1212 1047 1143 1125 1058 1223
    ## [83385] 1008 1217 1115 1016 1013 1047 1003 1211 1236 1210 1107 1230 1210 1151
    ## [83399] 1214 1025 1227 1230 1148 1231 1413 1220 1216 1158 1217 1036 1055 1532
    ## [83413] 1120 1222 1244 1050 1511 1103 1243 1417 1114 1227 1226 1045 1105 1237
    ## [83427] 1219 1119 1244 1156 1157 1108 1102 1237 1308 1200 1148 1104 1231 1131
    ## [83441] 1129 1232 1309 1304 1322 1205 1226 1134 1123 1119 1148 1322 1205 1315
    ## [83455] 1320 1303 1222 1221 1125 1154 1206 1325 1328 1306 1256 1214 1356 1335
    ## [83469] 1242 1334 1159 1309 1157 1342 1334 1332 1321 1400 1142 1256 1240 1240
    ## [83483] 1341 1215 1250 1318 1208 1250 1328 1405 1418 1215 1342 1222 1254 1357
    ## [83497] 1320 1232 1422 1242 1407 1350 1240 1222 1430 1319 1414 1409 1334 1316
    ## [83511] 1341 1252 1355 1416 1415 1441 1305 1333 1402 1406 1443 1355 1248 1254
    ## [83525] 1301 1351 1420 1312 1324 1309 1500 1347 1310 1332 1447 1425 1323 1514
    ## [83539] 1405 1510 1517 1458 1324 1504 1322 1347 1319 1431 1542 1346 1515 1502
    ## [83553] 1514 1504 1338 1337 1423 1341 1500 1431 1431 1518 1354 1412 1606 1417
    ## [83567] 1415 1550 1545 1406 1411 1558 1446 1435 1408 1456 1548 1440 1548 1406
    ## [83581] 1515 1605 1553 1528 1617 1552 1520 1416 1421 1614 1419 1439 1553 1414
    ## [83595] 1450 1450 1517 1613 1607 1634 1422 1513 1623 1435 1427 1619 1633 1621
    ## [83609] 1614 1617 1619 1507 1638 1642 1618 1531 1641 1630 1544 1531 1507 1719
    ## [83623] 1650 1526 1503 1557 1642 1518 1649 1700 1503 1457 1619 1543 1715 1607
    ## [83637] 1645 1515 1506 1520 1506 1555 1651 1524 1624 1646 1623 1652 1728 1742
    ## [83651] 1749 1613 1534 1617 1752 1641 1735 1755 1659 1542 1604 1625 1543 1629
    ## [83665] 1602 1726 1704 1723 1615 1640 1650 1625 1711 1636 1558 1733 1607 1649
    ## [83679] 1633 1757 1754 1945 1725 1723 1930 1735 1646 1651 1640 1708 1727 1758
    ## [83693] 1808 1815 1755 1813 1744 1715 1734 1708 1614 1710 1832 1657 1618 1807
    ## [83707] 1628 1619 1843 1642 1807 1621 1744 1654 1725 1904 1643 1717 1709 1702
    ## [83721] 1758 1826 1805 1650 1846 1643 1840 1659 1856 1808 1801 1746 1710 1629
    ## [83735] 1824 1854 1842 1830 1748 1641 1842 1746 1724 1759 1715 1859 1758 1735
    ## [83749] 1900 1916 1728 1801 1856 1750 2007 1718 1827 1830 1739 1903 1918 1721
    ## [83763] 1903 1813 1743 1732 1853 1820 1807 1716 1818 1834 1808 1909 1813 1839
    ## [83777] 1830 1924 1915 1731 1749 1754 1852 1817 1817 1829 1744 1917 1821 1909
    ## [83791] 1758 2104 1913 1746 1908 1935 1941 1856 1822 1855 1910 1852 1923 2010
    ## [83805] 1820 1819 1947 1800 1854 1806 1926 1950 1814 1801 1906 1939 1942 2013
    ## [83819] 2000 1938 1852 1807 1900 1757 1933 1938 1827 1947 1909 2002 2015 2103
    ## [83833] 1850 1816 2023 1856 1908 1837 1852 1821 1957 1950 1830 2031 1915 2002
    ## [83847] 1851 2032 1922 1927 1913 1921 2026 1848 1942 1909 2026 1856 2031 2048
    ## [83861] 2036 1835 2037 1953 1901 2023 1918 2032 1901 2000 1929 1909 1948 2016
    ## [83875] 1947 2048 2029 1853 2058 1855 2021 1857 2045 2025 2051 1946 1933 1913
    ## [83889] 1914 2106 2032 1907 2050 2115 2118 2055 2027 2118 2024 1955 2045 2004
    ## [83903] 1938 2029 1950 1958 1953 1945 2119 2123 2003 2112 1946 2043 2021 2127
    ## [83917] 1938 2023 1942 2127 2112 1948 2123 2043 2034 2225 2023 2053 2033 2048
    ## [83931] 2044 1936 1958 2200 2159 2106 1952 2023 2158 2033 2111 2004 2109 2148
    ## [83945] 2101 2129 2036 2218 2217 2150 2042 2208 2105 2354 2016 2030 2101 2033
    ## [83959] 2230 2201 2250 2211 2032 2138 2159 2207 2114 2025 2035 2216 2056 2044
    ## [83973] 2249 2146 2151 2223 2210 2212 2205 2133 2054 2038 2223 2225 2226 2035
    ## [83987] 2222 2102   12 2156 2146 2137 2306 2050 2032 2043 2124 2213 2227 2250
    ## [84001] 2101 2035 2255 2105 2223 2212 2058 2235 2249 2037 2112 2202 2250 2303
    ## [84015] 2140 2159 2100 2121 2138 2313 2227 2210 2227 2251 2132 2242 2249 2117
    ## [84029] 2317  104 2129 2336 2231 2106 2331 2124 2241 2147 2125 2127 2311 2234
    ## [84043] 2324 2146 2145 2334 2325 2232 2207 2246 2150 2332 2126   10 2156 2328
    ## [84057] 2324 2152   NA 2155 2135 2231 2342 2237   29 2159 2351 2252 2343 2208
    ## [84071] 2158 2148 2306 2203 2323 2212 2207 2214 2348 2223 2311 2312 2330 2351
    ## [84085] 2248   19 2255 2342   11 2214 2308 2236 2234   31 2331 2219 2240 2301
    ## [84099] 2355 2343 2315 2245 2350   57    8   12   25   33   18 2327 2331 2252
    ## [84113] 2258   21  213   34  111 2327 2321 2311   56   42    8 2314 2359   49
    ## [84127] 2308 2333 2342  102   NA 2345  127    4 2328 2357  102   50    1 2350
    ## [84141]   19   23  429   NA   NA   NA   NA   NA   NA  103  626  742  833 1006
    ## [84155]  642  651  719  825  838  851  809  932  847  703  812  849 1026  703
    ## [84169]  842  752  658  750  851  737  722  905  729  827  724  851  908  800
    ## [84183]  818  953  753  908  809  854  731  806  932  759  715  814  829  857
    ## [84197]  824  736  821  828  924  951  916  933  744  856  743  906  805  912
    ## [84211]  734  847  922  942  927  849  957  842  841  826  802  919  756  935
    ## [84225]  753  901  749  945  944  817 1004  952 1001  813  918  759 1156 1029
    ## [84239]  819 1040  834  930 1011  908  840  848  819 1157 1009 1002 1019 1040
    ## [84253] 1212 1013  913 1027  958 1007  859  922 1005 1019  832  828 1209 1027
    ## [84267] 1010 1036 1117 1046 1055  907  851 1030 1018  934  902 1033  847 1031
    ## [84281] 1012 1037 1021 1040 1215 1217  903  921  943  900 1048 1012  938  847
    ## [84295]  859  901 1023  901  908 1139  854 1103  927 1127 1036 1008 1053 1019
    ## [84309]  907  912  931 1040 1030 1109 1139  948 1041 1103 1049 1056 1053 1014
    ## [84323] 1007 1013 1107 1315 1248 1050 1053  942 1010  953  931  932 1135 1024
    ## [84337] 1001 1115 1104 1022 1016  953  935 1142 1056  943  931  946 1035 1007
    ## [84351] 1016  938  935 1218 1039 1058 1058 1029  936 1030 1007 1150 1132 1037
    ## [84365] 1032 1125 1006 1148 1144 1106 1232 1126 1001 1004 1036 1131 1156 1211
    ## [84379] 1220 1139 1338 1149 1219 1015 1049 1209 1146 1124 1004 1212 1117 1209
    ## [84393] 1043 1032 1108 1015 1015 1104 1217 1242 1216 1221 1221 1213 1025 1237
    ## [84407] 1223 1216 1134 1525 1223 1154 1246 1213 1043 1325 1210 1526 1311 1116
    ## [84421] 1232 1228 1050 1307 1048 1233 1050 1152 1207 1205 1049 1117 1101 1104
    ## [84435] 1122 1228 1307 1239 1125 1051 1320 1331 1125 1158 1254 1240 1201 1130
    ## [84449] 1202 1119 1213 1205 1147 1253 1329 1316 1159 1202 1258 1137 1157 1339
    ## [84463] 1127 1309 1344 1317 1319 1252 1240 1142 1256 1155 1151 1404 1407 1342
    ## [84477] 1440 1147 1200 1229 1300 1317 1419 1335 1521 1221 1225 1208 1153 1146
    ## [84491] 1340 1155 1246 1315 1247 1204 1243 1408 1204 1415 1258 1421 1215 1227
    ## [84505] 1415 1358 1241 1425 1331 1412 1353 1419 1250 1345 1313 1408 1247 1457
    ## [84519] 1347 1333 1305 1417 1358 1441 1414 1259 1454 1335 1245 1454 1250 1340
    ## [84533] 1355 1254 1248 1251 1511 1522 1454 1359 1306 1325 1500 1449 1522 1407
    ## [84547] 1357 1325 1313 1506 1327 1425 1352 1317 1454 1437 1415 1421 1327 1523
    ## [84561] 1405 1319 1433 1445 1341 1338 1546 1516 1457 1506 1522 1410 1330 1402
    ## [84575] 1524 1434 1342 1554 1339 1435 1529 1500 1605 1436 1445 1432 1355 1527
    ## [84589] 1535 1604 1416 1407 1622 1534 1541 1405 1630 1437 1408 1452 1539 1621
    ## [84603] 1427 1558 1533 1547 1622 1453 1509 1552 1611 1514 1529 1440 1427 1631
    ## [84617] 1612 1433 1452 1451 1601 1622 1436 1513 1440 1528 1623 1715 1701 1501
    ## [84631] 1536 1618 1504 1640 1456 1508 1523 1721 1625 1655 1505 1450 1708 1627
    ## [84645] 1717 1612 1509 1731 1644 1700 1708 1516 1528 1615 1629 1755 1641 1747
    ## [84659] 1618 1642 1731 1626 1710 1631 1525 1614 1647 1618 1724 1553 1726 1741
    ## [84673] 1639 1812 1654 1613 1637 1607 1726 1742 1725 1645 1818 1736 1644 1732
    ## [84687] 1806 1813 1624 1747 1717 1556 1637 1614 1713 1705 1802 1749 1620 1832
    ## [84701] 1942 1556 1607 1750 1650 1752 1741 1751 1657 1807 1819 1621 1650 1718
    ## [84715] 1621 1722 1823 1744 1652 1649 1654 1813 1818 1740 1823 1639 1701 1658
    ## [84729] 1736 2014 1751 1650 1645 1702 1715 1718 1856 1925 1707 1647 1828 1831
    ## [84743] 1825 1912 1754 1930 1751 1648 1716 1701 1640 1842 1637 1731 1858 1908
    ## [84757] 1649 1802 1802 1744 1754 1836 1802 1707 1728 1701 1723 1911 1930 1814
    ## [84771] 1829 1841 1740 1807 1726 1730 1859 1722 1714 1846 1935 1824 1811 1758
    ## [84785] 1827 1853 1808 1917 1822 1902 1837 1750 1911 1822 1906 1739 1842 1831
    ## [84799] 1820 1737 1827 1848 2026 1752 1958 1924 1834 1928 1947 2128 1753 1850
    ## [84813] 1935 1751 1913 1911 1804 2042 2031 2014 1826 1758 1937 1832 1928 1933
    ## [84827] 2007 2018 1850 1845 1833 2005 1926 1949 1859 1949 1800 1847 1757 1931
    ## [84841] 1821 1933 2118 1821 1801 1955 1944 1954 1952 1901 1755 1822 1923 1906
    ## [84855] 1916 1845 1932 1858 1940 2014 1841 2000 1824 1856 1950 1939 1953 1830
    ## [84869] 2001 2050 2054 2111 2011 1848 1846 2001 2015 1950 1906 1845 2047 2111
    ## [84883] 1925 2115 2008 1854 2112 2122 2102 1848 1855 2013 2116 2038 1930 1932
    ## [84897] 1919 2054 1927 1916 1914 2036 1915 1950 2038 1953 1937 1948 2022 2042
    ## [84911] 1937 2055 1903 2052 2022 2146 2100 2035 2101 1921 1920 1913 2011 2123
    ## [84925] 1955 2105 1954 2139 2037 1930 2116 1931 2115 2008 2006 2201 2056 2210
    ## [84939] 2020 2050 2019 2105 1951 2123 1944 2120 2029 2017 2106 1936 2122 2125
    ## [84953] 2116 2108 2001 2235 2225 2135 2013 1956 2009 2108 2049 2104 2038 1955
    ## [84967] 2127 2156 2007 2042 2019 2149 2230 2153 2149 2300 2000 2207 2059 2037
    ## [84981] 2047 2355 2032 2141 2005 2221 2205 2118 2229 2121 2044 2144 2120 2240
    ## [84995] 2139 2224 2115 2049 2156 2038 2100 2111 2048 2217 2232 2221 2148   14
    ## [85009] 2127 2222 2042 2120 2239 2110 2044 2219 2143 2125 2109 2223 2314 2239
    ## [85023] 2245 2312 2134 2105 2042 2254 2301 2236 2102 2253 2220 2245 2103 2232
    ## [85037] 2055 2133 2116 2154 2158 2116 2236 2152 2239 2117 2246 2238 2242 2322
    ## [85051] 2206 2123  110 2205 2153 2220 2228 2236 2115 2328 2205 2123 2257   24
    ## [85065] 2356 2136 2319 2149 2354 2322 2132 2141 2234 2356 2147   23 2356 2317
    ## [85079] 2346 2150 2350 2210 2248 2334 2315 2214 2205 2155 2305 2323 2302 2326
    ## [85093] 2228 2308 2349 2156 2219   25 2321 2209 2337 2341 2353 2306   49 2220
    ## [85107] 2305 2230 2303 2345 2234 2307 2326 2327  102 2231 2241 2351  135 2246
    ## [85121]    1 2300   33 2250 2240   29 2258   44 2309 2320   30   21 2250 2340
    ## [85135]   42 2327 2318 2314   42 2330 2342 2358 2353 2336 2344   20  500  457
    ## [85149]  447  129   NA   NA   NA  643  805  833 1032  652  720  745  828  734
    ## [85163]  648  851  845  700  743  735  848  821  941  845  703  709  940  651
    ## [85177]  851  754  810  840  738  856  720  830  847  807  857  901 1049  840
    ## [85191]  830  806  848  810  713  908  831  908  859  919  759  917  827  821
    ## [85205]  825  806  917  900  902  830  759  725  737  758  924  850  930  937
    ## [85219] 1021  851  752 1015  743  749  848  826  927  958  858  917  753  826
    ## [85233]  950  841  901  954  829 1137  915 1030  802  930 1015  857 1036 1152
    ## [85247] 1042 1031  846 1041  915  904  831 1001  918  842  933 1011  946  852
    ## [85261]  915  918 1009  946  836 1022  841 1112 1036 1210 1028 1024 1019  905
    ## [85275] 1112  928 1056 1046 1002  903  923 1019  844 1029 1038 1044  847 1227
    ## [85289] 1251 1022 1009 1103  852 1055  946  937  858 1049 1046  902  923 1021
    ## [85303] 1007  918  949  949   NA 1134  912 1051 1038  927 1204 1026  902 1045
    ## [85317] 1109 1048 1247  930 1046  943 1034 1057 1021 1207 1014 1103 1203 1059
    ## [85331] 1034  947  929 1037 1041  935 1153 1021  945 1020 1016 1027 1013  930
    ## [85345] 1022  955 1055 1034 1055 1031  935 1047 1107 1036 1113 1118 1043  958
    ## [85359] 1038 1018 1058 1227 1211 1056 1232 1052 1039 1302 1009 1126 1136 1114
    ## [85373] 1131 1009 1009 1220 1218 1054 1133 1042 1008 1210 1210 1213 1223 1150
    ## [85387] 1026 1336 1141 1156 1244 1013 1033 1113 1209 1139 1300 1202 1145 1016
    ## [85401] 1146 1237 1027 1144 1206 1022 1059 1201 1158 1238 1207 1050 1304 1032
    ## [85415] 1250 1530 1055 1354 1240 1316 1239 1238 1115 1143 1242 1232 1211 1244
    ## [85429] 1101 1252 1117 1051 1203 1056 1205 1136 1109 1252 1206 1347 1519 1258
    ## [85443] 1338 1117 1149 1238 1308 1126 1239 1149 1202 1230 1501 1122 1339 1315
    ## [85457] 1137 1150 1256 1200 1158 1319 1403 1115 1314 1211 1343 1258 1223 1413
    ## [85471] 1238 1201 1408 1325 1336 1408 1342 1154 1320 1329 1204 1251 1447 1231
    ## [85485] 1241 1316 1621 1413 1342 1147 1246 1234 1300 1251 1233 1238 1328 1357
    ## [85499] 1253 1203 1216 1236 1442 1408 1409 1344 2046 1509 1421 1302 1254 1228
    ## [85513] 1323 1321 1335 1314 1430 1411 1254 1535 1437 1442 1307 1328 1325 1417
    ## [85527] 1421 1402 1357 1322 1304 1248 1409 1309 1335 1511 1345 1302 1439 1411
    ## [85541] 1301 1402 1314 1452 1342 1508 1437 1545 1459 1507 1532 1544 1457 1310
    ## [85555] 1329 1550 1400 1547 1442 1515 1412 1410 1340 1402 1515 1409 1453 1530
    ## [85569] 1324 1354 1518 1428 1352 1348 1422 1343 1636 1353 1356 1540 1527 1637
    ## [85583] 1544 1554 1451 1550 1457 1420 1614 1546 1552 1605 1538 1632 1511 1557
    ## [85597] 1607 1451 1639 1432 1410 1653 1606 1424 1510 1455 1442 1454 1514 1615
    ## [85611] 1512 1436 1541 1535 1634 1536 1702 1631 1455 1455 1613 1635 1634 1547
    ## [85625] 1438 1537 1516 1623 1454 1637 1544 1708 1639 1508 1738 1750 1643 1535
    ## [85639] 1736 1626 1509 1732 1537 1652 1708 1640 1756 1536 1645 1554 1725 1629
    ## [85653] 1530 1551 1713 1603 1624 1728 1703 1644 1726 1610 1742 1655 1637 1628
    ## [85667] 1823 1643 1642 1820 1715 1539 1632 1644 1705 1656 1745 1736 1728 1613
    ## [85681] 1739 1651 1642 1623 1735 1753 1734 1754 1604 1746 1633 1937 1734 1633
    ## [85695] 1730 1629 1758 1826 1746 1752 1651 1749 1736 1754 2005 1806 1837 1852
    ## [85709] 1621 1835 1611 1622 1749 1829 1709 1751 1831 1831 1845 1624 1728 1844
    ## [85723] 1837 1658 1759 1745 1714 1907 1700 1737 1722 1635 1715 1721 1730 1719
    ## [85737] 1653 1928 1802 1656 1627 1814 1724 1702 1704 1923 1735 1913 1839 1841
    ## [85751] 1659 1855 1709 1746 1936 1816 1849 1821 1735 1738 1839 1917 1916 1951
    ## [85765] 1845 1733 1725 1726 1827 1919 1919 1809 1805 2014 1936 1859 1901 1816
    ## [85779] 1826 1808 1907 1847 1801 1811 1904 1951 1727 1943 1924 1802 1811 2003
    ## [85793] 1926 1835 1815 1849 2019 1831 1909 1905 1954 1857 2009 1753 1828 1801
    ## [85807] 1911 1915 2008 2013 1921 1845 1832 2022 2030 1757 1756 1935 1839 1930
    ## [85821] 1914 1935 1937 1843 2056 1837 1927 2126 1754 1812 1911 2032 1906 1803
    ## [85835] 1740 1812 1803 1806 2019 2034 1947 1819 2010 1959 2138 2019 1908 1959
    ## [85849] 1816 1918 1902 1953 1857 2049 2041 2051 1830 2005 2013 2021 1841 1840
    ## [85863] 2012 1824 2003 1944 1853 1919 1826 2030 2041 1829 1837 2041 2016 1920
    ## [85877] 1924 1901 2120 2129 2043 2022 2016 2020 1921 1914 2131 2028 1949 2121
    ## [85891] 1840 2115 2122 2033 2127 2046 2036 1954 1943 1927 1933 2020 2107 2045
    ## [85905] 2100 1858 2041 1904 2057 2010 2008 2055 2204 1943 1930 2133 2051 2134
    ## [85919] 2049 2021 2109 2030 1934 2158 2200 2209 2129 1958 2126 2024 1954 2112
    ## [85933] 2229 2036 2001 1932 2154 1929 2134 2111 2127 2029 2222 1951 2216 2124
    ## [85947] 2122 2131 2147 2001 2128 2020 2214 2030 2123 2214 2026 2015 1945 1953
    ## [85961] 2026 2104 2120 2243 2204 2054 2105 2009 2248 2347 2157 2031 2142 2130
    ## [85975] 2103 2049 2150 2136 2136 2011 2056 2157 2203 2025 2045 2250 2122 2218
    ## [85989] 2215   17 2027 2122 2203 2052 2056 2123 2048 2140 2119 2314 2053 2102
    ## [86003] 2256 2237 2210 2207 2218 2317 2122 2140 2054 2117 2046 2238 2144 2212
    ## [86017] 2100 2134 2132 2157 2133 2147 2055 2146 2256 2137 2219 2329 2049 2329
    ## [86031] 2104 2122 2235 2304 2220 2105 2242 2110 2303 2354 2359 2351 2324 2220
    ## [86045] 2357 2309 2154 2258 2151 2246 2228 2156 2339   30 2315 2313    7 2218
    ## [86059] 2207 2327 2252 2316 2158 2208 2322   32 2211 2215 2211 2150 2333 2235
    ## [86073] 2154 2210 2213 2321 2239 2255 2355 2348 2214   19  155 2308 2337 2346
    ## [86087]    6 2324 2232 2354 2324 2229   55 2327 2240 2257  128   19 2242   19
    ## [86101] 2249   16 2347 2304 2301 2241 2314 2301   44 2352 2325 2335  108  112
    ## [86115] 2344    4   55 2342  116    8  427  436  441   NA   NA   NA  645  806
    ## [86129]  826  821 1029  802  648 1005  652  805  819  651  834  837  838  704
    ## [86143]  745  853  756  835  706  753  852  949  724  827  733  957 1041  844
    ## [86157]  859  839  753  834  904  810  909  903  915  910  720  740  740  838
    ## [86171]  809  857  824  824  908  723  833  920  858  743  900  858  735  902
    ## [86185]  808 1000  913  932  937  804  801  843  851  845  932  936 1026  753
    ## [86199]  932  932  947  757  842 1127 1104  836  913 1149  807  945 1037 1046
    ## [86213] 1035 1037  831  853  953  946  854  815  928  922  901  959 1041  828
    ## [86227]  921  946  823 1015 1214 1002 1056 1019 1108 1029 1005  924  900 1124
    ## [86241] 1030  906 1136 1052 1019 1050 1020 1023 1035  911 1249 1023  942 1045
    ## [86255] 1229  930 1043 1010  939 1029  916  857 1032 1000 1040 1039  928 1149
    ## [86269]  851  937  952  907 1006 1245 1153  939 1041 1017  909 1033 1038  959
    ## [86283] 1008 1153 1040  919 1047 1029 1045  946 1025 1101 1109  925 1022  934
    ## [86297] 1211 1038  947 1012 1025  949 1239 1112  944 1134 1117  944 1021 1106
    ## [86311] 1151 1055 1219 1014  959 1049 1031 1005 1009  952 1005 1014 1005 1105
    ## [86325] 1035 1008 1230 1125 1023 1200 1249 1144 1042 1009 1232 1105 1145  957
    ## [86339]  957 1020 1228 1148 1105 1027 1129 1329 1122 1051 1157 1159 1212 1007
    ## [86353] 1224 1102 1207 1205 1016 1143 1016 1124 1243 1307 1115 1141 1208 1032
    ## [86367] 1136 1040 1143 1211 1248 1204 1324 1215 1215 1044 1207 1108 1040 1206
    ## [86381] 1148 1132 1519 1517 1224 1129 1114 1155 1413 1311 1332 1216 1249 1137
    ## [86395] 1111 1048 1104 1228 1124 1119 1102 1250 1219 1132 1228 1258 1356 1132
    ## [86409] 1137 1341 1221 1131 1211 1312 1259 1203 1136 1218 1206 1314 1349 1134
    ## [86423] 1341 1238 1301 1321 1308 1230 1421 1355 1215 1307 1201 1216 1413 1229
    ## [86437] 1255 1227 1430 1426 1321 1343 1243 1239 1411 1338 1148 1239 1229 1345
    ## [86451] 1316 1255 1202 1230 1408 1213 1425 1233 1409 1327 1322 1330 1401 1355
    ## [86465] 1255 1230 1253 1317 1415 1415 1311 1412 1402 1247 1339 1334 1421 1404
    ## [86479] 1313 1451 1519 1501 1413 1317 1300 1430 1241 1433 1249 1527 1423 1347
    ## [86493] 1540 1534 1453 1341 1503 1436 1335 1548 1309 1440 1322 1345 1342 1457
    ## [86507] 1312 1554 1500 1406 1440 1400 1346 1353 1339 1446 1428 1518 1436 1545
    ## [86521] 1413 1604 1336 1505 1349 1542 1413 1628 1348 1510 1609 1542 1525 1539
    ## [86535] 1442 1454 1545 1436 1514 1650 1531 1648 1642 1452 1513 1419 1536 1422
    ## [86549] 1703 1540 1512 1614 1600 1519 1704 1556 1546 1408 1453 1507 1548 1449
    ## [86563] 1520 1437 1420 1524 1611 1534 1456 1614 1444 1651 1505 1621 1636 1630
    ## [86577] 1709 1526 1536 1641 1602 1448 1512 1637 1514 1450 1623 1531 1525 1729
    ## [86591] 1644 1617 1646 1456 1625 1624 1508 1652 1655 1852 1604 1809 1616 1504
    ## [86605] 1651 1623 1749 1627 1745 1641 1654 1552 1548 1548 1647 1802 1532 1705
    ## [86619] 1623 1809 1726 1643 1628 1611 1522 1700 1641 1549 1613 1656 1735 1722
    ## [86633] 1735 1708 1652 1658 1616 1647 1630 1732 1716 1816 1634 1708 1724 1617
    ## [86647] 1626 1808 1739 1604 1603 1555 1746 1640 1632 1636 1620 1647 1746 1736
    ## [86661] 1610 1816 1840 1739 1658 1711 1810 1951 1740 1727 1942 1731 1644 1707
    ## [86675] 1820 1812 1758 1645 1744 1715 1829 1818 1704 1819 1644 1900 1707 1803
    ## [86689] 1626 1919 1827 1703 1659 1649 1642 1849 1817 1847 1740 1910 1736 1825
    ## [86703] 1843 1857 1818 1805 1738 1804 1757 1814 1715 1719 1737 1840 1850 1927
    ## [86717] 1839 1756 1751 1717 1735 1853 1707 1927 1836 1848 1832 1916 1714 1748
    ## [86731] 1756 1901 1832 1811 1857 1808 1826 1842 1831 1847 1749 1737 1922 1845
    ## [86745] 1823 2005 1822 1755 1928 2010 1912 1816 1724 2024 1809 2210 1743 1946
    ## [86759] 1746 1916 1858 1911 2020 1742 1933 1831 1940 1858 1757 2017 2157 1952
    ## [86773] 2048 1839 1935 1952 1844 1911 1752 1941 2008 1758 2000 1812 2103 1819
    ## [86787] 1917 1957 1853 1825 2101 1933 2029 2035 2002 1837 1823 1904 2005 2028
    ## [86801] 1848 1839 2024 1951 1948 1943 1832 1806 2023 2055 1959 2011 1912 2012
    ## [86815] 1828 1815 2117 1912 1917 2114 1834 2121 2122 2039 2105 2010 2018 1956
    ## [86829] 1925 1846 1948 1945 1953 1930 2104 1933 1927 2138 1912 1942 1909 2037
    ## [86843] 2141 2017 1931 1908 2049 2102 2021 2054 2005 1911 1920 2035 1941 2219
    ## [86857] 2114 2148 1935 2208 2057 2159 2056 1934 2205 1952 2151 2042 1952 2129
    ## [86871] 2038 2012 2008 2223 2041 2104 2130 2021 2125 2208 2103 2017 2028 2147
    ## [86885] 2025 2027 2224 2007 2113 1948 2239 2145 2218 2112 2029 2052 1933 2014
    ## [86899] 2117 2014 2122 2012 2129 2008 2136 2227 2009 2009 2049 1958 2022 1956
    ## [86913] 2032 1957 2145 2157 2035 2253 2206 2104 2027 2206 2031 2121 2119 2240
    ## [86927] 2038 2117 2117 2021 2227 2158 2142 2133 2212 2101 2157 2227 2147 2056
    ## [86941] 2237 2052 2252 2343 2134 2357 2317 2325 2124 2233 2134 2054 2113 2044
    ## [86955] 2122 2042 2235 2116 2156 2134 2324 2221 2147 2057 2136 2046 2120 2236
    ## [86969] 2114 2216 2228 2135 2213 2103 2055 2246 2347 2059 2051 2151 2240 2117
    ## [86983] 2241 2229 2319 2238   28   27 2230 2220 2255 2353 2257 2251 2232 2246
    ## [86997] 2157 2141   16 2248 2144 2229 2252 2331 2342 2216 2322 2332 2204 2357
    ## [87011] 2155 2146 2225 2353 2204   31 2249 2357 2215 2232 2335 2245 2247 2314
    ## [87025] 2152 2212 2301 2211 2231 2314 2150 2157 2322 2334 2331 2203 2314 2209
    ## [87039]  125 2220 2340 2214 2301 2253 2226    2 2230 2232 2249    6   32 2353
    ## [87053] 2336 2258 2323   37   NA 2257   30  137 2312 2318 2314 2334 2331 2340
    ## [87067]    5 2343 2345 2350    4    4 2350  419  434  410   NA   NA   NA   NA
    ## [87081]   NA   NA   NA   NA  117  143  153  228  505  233  510  445  637  753
    ## [87095]  657  832  822  959  738  804  919  645  751  830  828  654  933  654
    ## [87109]  718  743  711  951  858  713  819  703  851  754  730 1024  753  814
    ## [87123]  850  857  834  849  909  909  719  831  818  843  810  857  725  935
    ## [87137]  806  752  823  830  841  857  918  843  910  810  912  752 1102  911
    ## [87151]  801 1007  914  809  941  923  917  855  945  859 1038  954  920  929
    ## [87165] 1036  910 1011  922  745  803 1038  935  840  901 1101 1052  854  848
    ## [87179] 1058 1001  837 1138  836 1156  857  949 1008  821  912  952  918 1009
    ## [87193]  839  949 1055  929  915 1133  827 1022 1027 1036 1006 1125 1053 1006
    ## [87207] 1203  910 1023  930  917  913 1024  907 1045 1023 1055 1045  912  855
    ## [87221]  915 1030 1104  917 1215  928 1026 1055 1032 1037 1052 1040  913 1024
    ## [87235] 1013 1006 1154  927 1100 1058 1048  854 1003 1047  929 1141  856 1044
    ## [87249] 1048 1201 1009 1031 1053 1107   NA  959 1018 1102 1121 1124  948 1248
    ## [87263] 1056 1216 1026 1214 1119 1229 1044 1018 1140 1046 1104 1102  955 1026
    ## [87277] 1141 1053 1033 1222 1105 1148 1128 1104 1129 1023 1029 1029 1029 1128
    ## [87291] 1135 1208 1118 1153 1040 1116 1255 1311 1204 1225 1028 1321 1203 1249
    ## [87305] 1053 1325 1223 1045 1024 1026 1300 1248 1023 1122 1155 1004 1200 1228
    ## [87319] 1132 1318 1043 1223 1043 1423 1226 1228 1412 1154 1244 1322 1609 1327
    ## [87333] 1122 1342 1155 1126 1304 1546 1307 1335 1355 1121 1429 1305 1347 1310
    ## [87347] 1354 1318 1321 1139 1330 1412 1406 1418 1337 1332 1417 1418 1252 1405
    ## [87361] 1149 1236 1329 1335 1247 1346 1350 1239 1437 1455 1359 1449 1229 1240
    ## [87375] 1313 1438 1401 1410 1409 1414 1528 1525 1344 1506 1502 1545 1511 1545
    ## [87389] 1529 1344 1510 1342 1405 1447 1402 1541 1419 1520 1555 1404 1629 1622
    ## [87403] 1635 1428 1539 1655 1454 1506 1430 1551 1642 1551 1714 1534 1458 1612
    ## [87417] 1444 1612 1627 1541 1608 1513 1649 1625 1517 1554 1725 1510 1450 1534
    ## [87431] 1741 1601 1455 1513 1740 1630 1741 1452 1615 1636 1736 1513 1613 1523
    ## [87445] 1514 1655 1728 1657 1554 1643 1534 1813 1639 1709 1623 1517 1720 1612
    ## [87459] 1647 1712 1707 1607 1726 1721 1521 1550 1757 1712 1839 1753 1741 1639
    ## [87473] 1610 1554 1533 1657 1736 1800 1728 1740 1739 1751 1731 1804 1708 1613
    ## [87487] 1818 1653 1626 1634 1703 1600 1751 1726 1731 1738 1709 1618 1933 1723
    ## [87501] 1622 1759 1739 1610 1709 1727 1708 1801 1749 1604 1744 1702 1638 1745
    ## [87515] 1642 1819 1757 1804 1843 1903 1833 1819 1719 1903 1829 1832 1717 1826
    ## [87529] 1731 1707 1849 1903 1929 1959 1702 1832 1913 1916 1703 1903 1850 1712
    ## [87543] 1717 1743 1731 1848 1812 1757 1800 1700 1838 1941 1720 1830 1730 1854
    ## [87557] 1907 1725 1812 1858 1843 1757 1801 1808 1902 1746 1933 1829 1814 1827
    ## [87571] 1916 1849 1859 1943 1742 1828 2045 1916 1833 2023 1801 1838 1856 1948
    ## [87585] 1927 1928 2021 2040 1938 1836 1801 1817 1755 1824 1821 1843 2050 1916
    ## [87599] 2000 1836 2035 1856 1814 2032 1932 2043 1911 2013 1955 2044 2030 2107
    ## [87613] 1856 2044 2040 1919 1854 1854 2054 2016 1931 1942 2013 1928 1922 1825
    ## [87627] 1851 1954 1831 2108 2112 2020 2100 1901 2023 2013 1927 2021 2018 2123
    ## [87641] 2009 1909 2138 1956 2132 1959 2059 1939 2141 2023 1919 2033 1903 1935
    ## [87655] 2130 2205 2020 1908 2006 1930 2034 2031 2054 2104 1933 1922 2013 2134
    ## [87669] 2120 1956 2014 1921 2026 2015 2111 2137 1927 2220 1925 2111 2020 2221
    ## [87683] 2035 2050 2000 2139 2207 2112 2112 2012 2109 2033 2059 2224 2107 2201
    ## [87697] 2009 2058 2213 2026 2130 2215 2201 2140 2030 2000 2106 2055 2120 2147
    ## [87711] 2142 2049 2138 2116 2212 2032 2200 2043 2115 2338 2132 2208 2239 2005
    ## [87725] 2313 2134 2128 2043 2210 2144 2108 2116 2101 2059 2140 2100 2108 2048
    ## [87739] 2120 2203 2309 2121 2237 2245 2044 2233 2342 2115 2120 2213 2326 2235
    ## [87753] 2252 2057 2217 2232 2251 2235 2054 2035 2234 2113 2146 2153 2106 2310
    ## [87767] 2232 2200 2124 2136 2120 2133 2247 2306 2245 2104 2143 2156 2347 2132
    ## [87781] 2138 2128 2246 2235 2242 2147 2223 2211 2205 2143 2302 2136 2336 2333
    ## [87795] 2357 2155 2118 2136 2259 2154 2321 2134   19 2304 2307 2151 2318 2324
    ## [87809] 2134 2125   14 2132 2332 2155 2317 2203 2217 2129   44 2354 2305 2233
    ## [87823] 2145 2254 2223 2156    7 2317 2209 2310 2336   37 2205 2157 2231 2316
    ## [87837] 2315 2239   38 2330 2220 2338  130 2224 2239 2255 2230    7 2227   12
    ## [87851] 2250 2224 2227 2344    4 2237 2254   14   33   33 2302 2346   34   36
    ## [87865]    4 2302   53  148 2336   55 2339  100 2319 2322   30  127 2352 2350
    ## [87879] 2400 2356   32  249   48  308   51   30   38  153   56  101   35  143
    ## [87893]  130  113  427   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [87907]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [87921]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [87935]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [87949]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [87963]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [87977]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [87991]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [88005]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [88019]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [88033]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [88047]   NA   NA   NA   NA   NA   NA   NA  439  636  813  901 1011  649  705
    ## [88061]  655  744  842  812  729  811  801  949 1006  707  858  726  830  851
    ## [88075]  735 1020  822  733  757  920  933  852  847  903  817  726  811  819
    ## [88089]  931  900  928  745  846  830  914  816  846  815  752  922  939  914
    ## [88103]  856  929  921  741  905  822  759 1045  805  854  845  920  856  756
    ## [88117]  939 1029  957  931  752  841  826  805  854 1036  933 1043 1149  936
    ## [88131] 1056 1050 1051  841 1002  839 1140  904  933 1001  852 1002 1037  913
    ## [88145]  946  913  944  839  814  912 1030  941  956 1109  854  959 1103 1013
    ## [88159] 1028 1205 1058 1018  916  914 1032  921  922  842 1117 1145 1054 1048
    ## [88173] 1001 1102 1226 1031  929 1220 1149  920  937 1119 1042 1101 1042 1148
    ## [88187] 1017  857  919 1043 1045  932  941 1009  941 1204 1054  900 1049 1055
    ## [88201] 1050 1109 1102  935 1043 1047 1027 1110  954 1042 1031 1057 1121 1118
    ## [88215] 1119 1128  923 1028 1017 1047 1016 1023  948 1041  959  956 1225 1036
    ## [88229] 1000  950 1038 1119 1201 1041 1125 1101 1040 1129  953 1033 1017 1240
    ## [88243] 1016 1306 1021 1052 1112 1247 1135 1016 1143 1039 1050 1212 1202 1017
    ## [88257] 1021 1143 1009 1243 1236 1219 1022 1133 1036 1208 1028 1040 1015 1128
    ## [88271] 1329 1206 1249 1302 1008 1327 1054 1224 1248 1303 1031 1144 1148 1213
    ## [88285] 1257 1256 1158 1240 1044 1226 1021 1239 1310 1545 1054 1220 1136 1207
    ## [88299] 1033 1608 1109 1249 1129 1248 1255 1136 1301 1222 1131 1408 1307 1128
    ## [88313] 1238 1233 1342 1130 1116 1300 1105 1305 1309 1227 1157 1133 1244 1154
    ## [88327] 1311 1215 1222 1340 1142 1330 1156 1214 1343 1241 1357 1411 1221 1221
    ## [88341] 1335 1205 1208 1228 1145 1415 1230 1119 1314 1402 1422 1212 1336 1313
    ## [88355] 1323 1434 1326 1244 1225 1405 1415 1200 1428 1302 1224 1418 1202 1404
    ## [88369] 1303 1241 1402 1241 1235 1243 1219 1418 1352 1234 1428 1208 1441 1236
    ## [88383] 1432 1401 1440 1416 1339 1301 1342 1228 1435 1342 1359 1350 1326 1446
    ## [88397] 1406 1401 1347 1511 1553 1402 1349 1539 1436 1259 1344 1438 1310 1535
    ## [88411] 1303 1414 1247 1359 1326 1507 1558 1414 1515 1414 1441 1509 1507 1507
    ## [88425] 1430 1338 1421 1540 1511 1422 1525 1455 1326 1521 1600 1512 1345 1356
    ## [88439] 1358 1432 1412 1503 1547 1514 1714 1403 1522 1447 1405 1353 1640 1644
    ## [88453] 1641 1635 1545 1552 1535 1427 1651 1431 1503 1635 1607 1611 1440 1458
    ## [88467] 1610 1533 1512 1428 1455 1453 1459 1427 1441 1517 1555 1449 1602 1635
    ## [88481] 1618 1444 1444 1520 1436 1626 1726 1508 1528 1602 1623 1725 1659 1512
    ## [88495] 1636 1541 1532 1634 1659 1523 1440 1648 1518 1507 1559 1547 1643 1728
    ## [88509] 1749 1501 1659 1617 1507 1623 1626 1736 1746 1649 1659 1518 1650 1658
    ## [88523] 1624 1553 1728 1735 1806 1646 1645 1713 1739 1738 1655 1815 1548 1612
    ## [88537] 1703 1641 1711 1647 1628 1756 1740 1646 1704 1655 1653 1637 1739 1652
    ## [88551] 1601 1759 1818 1806 1605 1555 1746 1637 1717 1825 1814 1722 1625 1750
    ## [88565] 1742 1717 1810 1750 1824 1757 1707 1817 1703 1808 1725 1711 1828 1642
    ## [88579] 1706 1648 1822 1717 1820 1731 1941 1646 1939 1717 1854 1721 1808 1906
    ## [88593] 1903 1625 1853 1915 1832 1733 1758 1815 1717 1704 1705 1949 1715 1959
    ## [88607] 1915 1745 1945 1742 1911 1832 1951 1858 1737 1850 1844 1749 1854 1903
    ## [88621] 1757 1847 1844 1916 1721 1818 1746 1906 1925 1913 1845 1738 1954 1830
    ## [88635] 1728 1912 1754 1822 1811 1926 1935 1920 1931 2015 2041 1724 1917 1841
    ## [88649] 2021 1831 1842 1840 1924 1943 1950 2328 1918 1924 1815 2105 2028 1758
    ## [88663] 1821 1939 2028 2039 1827 1936 1802 1753 2037 1817 1910 2052 1829 1814
    ## [88677] 1834 2029 1811 1913 1940 1828 2028 2026 1916 1912 1821 2031 1904 2040
    ## [88691] 1902 2105 2324 1811 2135 2016 2001 2030 1907 1816 1918 1956 2036 1917
    ## [88705] 2017 2006 2032 2107 1919 2206 2047 1953 1910 2026 1943 1905 1929 2029
    ## [88719] 2125 1931 1921 1952 2200 2112 1942 1927 2036 1936 2041 2225 2049 2115
    ## [88733] 1937 2131 1917 2101 2135 2112 1932 2051 1944 2005 2201 2025 2114 2148
    ## [88747] 1930 1950 2143 2205 2105 2212 2209 2104 2009 2134 2030 2124 2023 2049
    ## [88761] 2213 2108 2234 2044 2020 2038 2142 2257 2023 2021 2039 2041 2137 2012
    ## [88775] 1956 2002 2121 2041 2131 2212 2035 2035 2151 2127 2126 2126 2212 2212
    ## [88789] 2024 2108 2018 2236 2016 2300 2050 2033 2230 2220 2232 2307 2212 2111
    ## [88803] 2155 2159 2209 2257 2102 2128 2250 2126 2156 2308 2354 2143 2302 2227
    ## [88817] 2123 2309 2311 2123 2053 2256 2143 2206 2209 2124 2224 2225 2119 2229
    ## [88831] 2256 2228 2344 2229 2229 2304 2228 2207 2121 2252 2114 2058 2146 2115
    ## [88845] 2247 2224 2213 2239 2104 2126 2155 2341 2237 2247 2155 2203 2350    2
    ## [88859] 2158 2214   46 2202 2249 2236 2211 2121 2333 2316 2203 2150 2240    3
    ## [88873] 2137 2211 2240 2219 2314   18 2305 2343 2345  304 2246 2255 2329   57
    ## [88887] 2202 2233 2213  107 2331 2233 2301  137 2237 2209 2233   47 2238 2310
    ## [88901] 2249 2328 2351 2324  106 2358  128   55   32 2316   13   10  105 2235
    ## [88915] 2340 2253 2239 2316 2400   12   21   27 2240 2235 2339  110 2358 2304
    ## [88929]   10 2332   14   54  116 2332  101 2308   21 2311 2326   58  135 2342
    ## [88943] 2334  127 2343 2341  112  131   12 2352  122   16 2350  116   54  238
    ## [88957]   46  238  425  454   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [88971]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [88985]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [88999]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [89013]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA  431  447  219
    ## [89027]  823  833  840 1014 1023  851  755  736  852  827  831  743  833  716
    ## [89041]  759 1055 1032  907  907  849  814  855  711  910  739  935  945  822
    ## [89055]  748  913  739  812  948  829  917  934  855  954  925  924 1032  902
    ## [89069]  929  936  746 1035 1014  916 1126  831  927 1052  929  851 1058  950
    ## [89083] 1041  827 1057  833  959  907 1008  828 1027  949 1206 1106  904  822
    ## [89097]  908 1014 1023  850  813 1120  910  906  922  940 1027 1059 1014 1049
    ## [89111]  914 1045 1119 1117 1042 1030 1223 1036 1114 1235  921 1004 1035  857
    ## [89125] 1044 1057 1004 1049 1105 1040 1030 1058 1242 1201  947 1106 1023 1155
    ## [89139] 1005 1047  954 1257 1210 1128 1117  930 1016 1024 1032 1002 1027 1209
    ## [89153] 1038  923 1218 1115 1040  926  920 1016 1031 1111 1124 1018 1006 1100
    ## [89167] 1130 1138 1013  952 1058 1131 1108 1132 1119 1058  952  948 1026 1213
    ## [89181] 1011 1003 1141  949 1012 1121 1201 1322 1205 1031 1209 1208 1254 1129
    ## [89195] 1059 1208 1009 1243 1258 1006 1259 1152 1216 1324 1053 1321 1055 1058
    ## [89209] 1425 1206 1208 1145 1549 1056 1256 1051 1223 1226 1534 1213 1240 1236
    ## [89223] 1234 1210 1238 1205 1046 1118 1237 1043 1127 1338 1212 1113 1126 1209
    ## [89237] 1135 1345 1404 1328 1303 1139 1224 1220 1119 1314 1325 1209 1348 1441
    ## [89251] 1412 1123 1414 1404 1314 1400 1216 1242 1126 1413 1320 1359 1230 1419
    ## [89265] 1457 1159 1335 1224 1335 1330 1203 1242 1202 1347 1400 1347 1254 1357
    ## [89279] 1244 1319 1204 1410 1607 1351 1250 1335 1238 1515 1256 1401 1410 1321
    ## [89293] 1358 1328 1430 1356 1503 1229 1347 1306 1443 1348 1531 1520 1435 1352
    ## [89307] 1420 1440 1438 1407 1356 1309 1250 1246 1333 1457 1307 1546 1311 1442
    ## [89321] 1314 1434 1317 1519 1601 1357 1401 1519 1418 1455 1341 1403 1347 1335
    ## [89335] 1433 1339 1548 1434 1336 1358 1548 1451 1546 1513 1406 1638 1811 1603
    ## [89349] 1529 1700 1540 1624 1600 1514 1428 1519 1517 1630 1448 1610 1411 1723
    ## [89363] 1640 1620 1618 1434 1532 1614 1647 1630 1452 1550 1616 1432 1742 1551
    ## [89377] 1609 1551 1802 1537 1659 1642 1728 1538 1742 1617 1500 1547 1514 1705
    ## [89391] 1755 1642 1649 1714 1621 1654 1753 1658 1642 1726 1656 1655 1540 1639
    ## [89405] 1531 1654 1710 1704 1908 1602 1800 1708 1759 1652 1742 1821 1706 1842
    ## [89419] 1625 1545 1946 1620 1742 1802 1740 1702 1907 1636 1928 1647 1800 1803
    ## [89433] 1747 1724 1727 1610 1648 1731 1653 1755 1709 1852 1745 1808 1611 1641
    ## [89447] 1933 1716 1654 1625 1722 1759 1835 1657 1735 1614 1657 1815 1648 1816
    ## [89461] 1850 1935 1747 1913 1744 1655 1923 1819 1806 1706 1806 1702 1829 1933
    ## [89475] 1850 1737 1936 1735 1744 1705 1729 1823 1809 1723 1807 1814 1817 1949
    ## [89489] 1730 1906 1729 1834 1854 1732 1809 1917 1858 1915 1822 1815 1746 1722
    ## [89503] 1907 1821 1855 1837 1922 1911 2055 1922 1937 1745 1844 1829 1728 1817
    ## [89517] 1816 1953 1931 1916 1808 1914 2049 2017 1824 2048 1843 2107 1753 1957
    ## [89531] 1955 1756 2023 2014 2110 2032 1838 1957 1956 1844 1841 2106 2003 1900
    ## [89545] 2113 1925 1901 1810 1957 1959 1805 1922 1957 2104 2059 1902 2114 1759
    ## [89559] 1904 1926 1910 2008 2037 2010 1828 1913 2134 2005 2025 2042 1922 2026
    ## [89573] 1902 2006 2127 2018 2117 1933 1900 1912 2025 2040 2020 2026 2002 2224
    ## [89587] 2008 2207 2305 2136 2113 2219 2322 2102 1957 2042 2146 2112 1929 2021
    ## [89601] 2242 2024 2003 2117 2108 1952 2049 2137 2137 2046 2006 2127 2203 2121
    ## [89615] 2007 2036 2147 2226 2248 2212 2206 2109 2143 2033 2222 2223 2114 2136
    ## [89629] 2114 2043 2248 2343 2037 2202 2035 2316 2155 2157 2250 2212 2029 2347
    ## [89643] 2033 2053 2308 2130 2210 2124 2046 2205 2140 2304 2221 2352 2131 2248
    ## [89657] 2130   22 2245 2057 2055 2357 2306 2257 2114 2305 2305 2127   29 2328
    ## [89671] 2151   57    6   20   40   25 2158 2250 2334 2250 2349 2306  126   20
    ## [89685] 2231    2 2300    2   30 2253 2322 2333 2335    8   55  506   NA   NA
    ## [89699]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [89713]   NA   NA  231  416  509  207  204  700  420  814  835  845  828  831
    ## [89727]  848 1050  702  840  951  858  734 1038  909  813  912  800  727  844
    ## [89741]  947  939  917  754  902  926  931  832  758  911  917  949  757 1124
    ## [89755] 1006  948  820  937  907 1032 1032  928 1040 1004 1146  833 1043 1052
    ## [89769]  824 1031  954  852  920  939 1016 1012  852  958  817 1027 1017 1003
    ## [89783] 1037 1108 1103 1113 1051 1212  915  945 1055 1044 1054 1056 1036 1040
    ## [89797]  920  918 1042 1103 1230 1232  911 1038  935 1054 1040 1054 1020  943
    ## [89811] 1051  854 1113 1045 1000 1205 1045  948  959  922 1129 1009 1041 1246
    ## [89825] 1044 1054 1111 1121 1117 1126 1008 1120 1009  928 1027  955 1003 1030
    ## [89839] 1059 1213  921 1038 1238 1006  952 1121 1123 1044 1032 1040 1208 1106
    ## [89853] 1027 1041 1101 1134 1119 1030 1126  943 1221 1017 1151 1235 1219 1214
    ## [89867]  934 1048 1223 1055 1105 1230 1237 1152 1212 1142 1150 1333 1114 1008
    ## [89881]  955 1238 1135 1046 1102 1153 1203 1251 1015 1018 1306 1221 1159 1221
    ## [89895] 1033 1158 1214 1255 1025 1315 1125 1223 1200 1257 1031 1239 1520 1115
    ## [89909] 1150 1203 1144 1251 1254 1114 1326 1239 1227 1120 1110 1249 1533 1134
    ## [89923] 1127 1048 1252 1428 1139 1349 1319 1145 1337 1215 1131 1215 1323 1303
    ## [89937] 1444 1327 1314 1206 1429 1222 1229 1240 1342 1326 1241 1138 1320 1322
    ## [89951] 1331 1155 1445 1346 1413 1426 1346 1344 1357 1404 1339 1432 1237 1251
    ## [89965] 1426 1338 1237 1350 1207 1339 1228 1253 1328 1300 1210 1350 1353 1205
    ## [89979] 1414 1222 1226 1218 1358 1414 1411 1425 1334 1503 1517 1340 1428 1226
    ## [89993] 1315 1345 1442 1438 1316 1518 1327 1428 1421 1448 1526 1418 1246 1257
    ## [90007] 1504 1440 1406 1249 1335 1341 1506 1352 1538 1448 1548 1457 1505 1418
    ## [90021] 1335 1308 1416 1354 1604 1533 1448 1424 1537 1350 1425 1556 1331 1358
    ## [90035] 1552 1431 1336 1458 1426 1503 1424 1345 1532 1728 1500 1510 1611 1544
    ## [90049] 1555 1559 1413 1621 1651 1447 1604 1508 1440 1559 1626 1543 1659 1626
    ## [90063] 1510 1557 1627 1524 1645 1444 1535 1622 1439 1407 1601 1640 1512 1743
    ## [90077]   NA 1420 1419 1501 1612 1601 1543 1546 1547 1625 1645 1726 1653 1534
    ## [90091] 1708 1704 1546 1554 1530 1518 1546 1550 1625 1808 1701 1601 1834 1551
    ## [90105] 1703 1654 1646 1612 1458 1504 1610 1744 1545 1640 1702 1740 1654 1711
    ## [90119] 1632 1621 1835 1711 1654 1717 1515 1806 1528 1809 1646   NA 1811 1633
    ## [90133] 1746 1747 1811 1733 1651 1601 1629 1720 1635 1656 1657 1733 1739 1702
    ## [90147] 1738 1756 1650 1808 1752 1952 1819 1752 1750 1832 1750 1739 1741 1731
    ## [90161] 1558 1810 1811 1715 1638 1759   NA 1807 1718   NA 1727 1814 1619 1803
    ## [90175] 1827 1738 1703 1728 1846 1855 1848 1742 1641 1655 2011 1738 1709 1756
    ## [90189] 1810 1841 1809 1837 1908 1828 1858 1859 1714 1920 1832 1817 1832 1910
    ## [90203] 1850 1851 1805 1707 1756 1853 1839 1925 1853 1926 1900 1652 1828 1852
    ## [90217] 1839 1837 1824 1657 1900 1725 1952 1904 1736 1836 1925 1733 1913 1857
    ## [90231] 1937 1957 1908 1857 1823 1821 1808 1914 2023 1917 1906 1747 1911 1931
    ## [90245] 1911 1915 1925 1934 1806 1927 2055 1937 1833 1933 2016 2048 2000 2101
    ## [90259] 2042 2007 2051 2057 1821 2018 2057 2024 2103 2054 2115 1931 2042 1924
    ## [90273] 2141 2051 1946 2050 2013 2119 2116 2013 2224 1909 1851 2000 2001 2147
    ## [90287] 2107 1933 2100 2015 2136 2112 2121 2120 2146 2105 2138 2007 2045 2128
    ## [90301] 2051 2231 2148 2110 2101 2133 2129 2138 1921 2120 2009 1955 2151 2122
    ## [90315] 2029 2000 2047 1942 2017 2001 2016 2208 1929 2136 2018 2212 2012 2140
    ## [90329] 2017 2106 2204 2119 2155 2136 2029 2202 2150 2216 2258 2248 2104 2204
    ## [90343] 2120 2200 2130 2042 2110 2105 2233 2215 2223 2233 2246 2113 2202 2118
    ## [90357] 2242 2232 2203 2042 2226 2218 2226 2327 2117 2251 2141 2135 2254 2347
    ## [90371] 2127 2159 2059 2329 2345 2232 2250 2200 2314 2143 2334    1 2201 2312
    ## [90385]    7 2249 2137 2220 2358  114 2115 2208 2205 2235 2145 2143 2120 2303
    ## [90399] 2225 2252 2201 2258   22 2156 2328 2127 2339  117 2317 2319 2216 2235
    ## [90413]   41   41 2349 2208 2335 2312 2250    1 2227 2240 2338 2141   11 2337
    ## [90427] 2302 2136 2327 2209 2317   NA 2207 2240 2337 2245   16 2213 2143  159
    ## [90441] 2316   44 2339   45  111 2300  110   50 2325   58 2258 2239 2350 2208
    ## [90455] 2319   56    2 2232  117   33  125   24  120    7 2326  123   NA 2312
    ## [90469]  101 2349 2311 2305   49 2352    8  133   23 2308   34   49 2347   51
    ## [90483]  105  236 2358   41  153  135   54 2324   51   29 2357 2330 2353   22
    ## [90497]    7  259  148   54   11    3   NA  104  141   11  116 2400   28   26
    ## [90511]  231  141   18   38  250  210   31   21   14   37  115  111   57  308
    ## [90525]   32  152  306  141  454   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [90539]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [90553]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [90567]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [90581]   NA   NA   NA   NA   NA   NA   NA   NA   NA  121  122  327  515  702
    ## [90595]  845  837 1016  843  657  856  650  857  758  841  917  716  900  855
    ## [90609]  803  827 1048  817  902  732  906  854  840  933  758  823  721  857
    ## [90623]  938  943  835  828  931  833  921  908  922  948  840  830  801  952
    ## [90637]  853 1413 1030 1004  818  937  919  745  940  943  852 1005 1005  956
    ## [90651]  747  923 1032 1144  749 1011 1009  859 1028  915  817 1026  948  858
    ## [90665] 1043 1038 1142  901 1018 1039 1057  820  908 1023  843  955 1030 1043
    ## [90679]  937  913  919  918  955  905  906 1023 1011  859 1044 1303  931 1020
    ## [90693] 1103 1102 1048 1109 1107 1032 1055  955 1146 1049 1038  934 1054 1043
    ## [90707] 1053  937  906  906 1103   NA  943 1243 1054  959  953 1049 1012 1104
    ## [90721] 1315  958 1028 1130 1130 1205  909 1010 1140  958 1151 1107 1142  914
    ## [90735] 1008 1257 1119  951 1054 1004 1031 1031 1052 1144 1127  954  954 1042
    ## [90749] 1130 1043 1033 1018  948 1108 1218 1015 1142 1037 1135 1215 1249 1117
    ## [90763] 1007 1108 1126 1136 1104 1117 1131 1126  958 1147 1100 1014 1152 1003
    ## [90777] 1228 1239 1132 1112 1042 1110 1034 1151 1216 1158 1159 1350 1104 1235
    ## [90791] 1256 1022 1015 1245 1020 1230 1027 1150 1008 1230 1201 1032 1226 1128
    ## [90805] 1158 1106 1133 1301 1032 1152 1223 1040 1242 1244 1231 1227 1204 1139
    ## [90819] 1257 1229 1134 1045 1134 1243 1104 1319 1150 1116 1528 1233 1259 1258
    ## [90833] 1237 1533 1137 1317 1313 1156 1129 1332 1150 1242 1300 1146 1211 1317
    ## [90847] 1440 1249 1331 1121 1314 1131 1320 1230 1116 1221 1115 1312 1200 1203
    ## [90861] 1151 1205 1332 1306 1208 1320 1342 1311 1231 1353 1209 1228 1209 1315
    ## [90875] 1310 1302 1425 1334 1434 1325 1337 1348 1227 1403 1412 1349 1314 1232
    ## [90889] 1146 1248 1244 1200 1219 1400 1425 1400 1341 1415 1404 1305 1412 1204
    ## [90903] 1242 1259 1346 1352 1229 1228 1251 1359 1241 1431 1448 1432 1334 1409
    ## [90917] 1336 1431 1434 1227 1309 1442 1412 1333 1302 1352 1437 1314 1410 1301
    ## [90931] 1341 1455 1400 1416 1407 1344 1419 1441 1357 1320 1525 1506 1506 1433
    ## [90945] 1529 1516 1519 1514 1439 1522 1240 1430 1329 1508 1543 1544 1542 1346
    ## [90959] 1454 1322 1420 1323 1622 1533 1531 1533 1545 1342 1611 1558 1508 1535
    ## [90973] 1342 1524 1448 1437 1432 1610 1659 1631 1402 1630 1551 1428 1552 1621
    ## [90987] 1632 1557 1632 1611 1425 1617 1426 1643 1505 1710 1612 1458 1518 1623
    ## [91001] 1500 1726 1527 1601 1528 1612 1537 1631 1537 1513 1502 1628 1632 1656
    ## [91015] 1641 1548 1628 1455 1601 1542 1638 1714 1719 1655 1659 1527 1556 1456
    ## [91029] 1609 1640 1539 1655 1636 1621 1559 1705 1659 1604 1815 1719 1640 1510
    ## [91043] 1713 1522 1632 1621 1745 1701 1739 1639 1520 1649 1839 1814 1757 1742
    ## [91057] 1721 1800 1757 1640 1546 1745 1617 1649 1803 1644 1641 1935 1837 1810
    ## [91071] 1809 1748 1744 1629 1738 1616 1804 1650 1640 1709 1808 1711 1704 1707
    ## [91085] 1752 1757 1737 1751 2023 1808 1743 1837 1645 1631 1659 1800 1832 1725
    ## [91099] 1804 1633 1706 1812 1620 1748 1927 1902 1630 1824 1920 1844 1920 1706
    ## [91113] 1713 1805 1831 1830 1635 1743 1723 1720 1838 1706 1721 1916 1844 1918
    ## [91127] 1718 1741 1811 1901 1917 1921 1739 1704 1904 1914 1934 1752 1856 1859
    ## [91141] 1711 1716 1918 1720 1954 1755 1832 1810 1845 1746 1848 1917 1917 1802
    ## [91155] 1936 1840 1913 2012 1912 1941 1828 1931 1926 1756 1951 1814 1818 1929
    ## [91169] 1842 2013 1918 1757 2009 1943 1826 1944 2002 1952 1906 1909 2016 1950
    ## [91183] 1815 1843 2008 2041 1928 2033 1912 2029 2014 2021 1857 1942 2018 1907
    ## [91197] 1903 1837 1919 1845 1903 1824 2018 2009 2042 2015 2049 1913 2105 2101
    ## [91211] 2057 1948 1855 2005 2111 2118 1930 2035 2013 1937 1857 1931 2007 1904
    ## [91225] 1933 1958 2055 1947 1855 1950 2020 2039 1940 1930 2023 1952 2132 1940
    ## [91239] 1858 2139   NA 1857 1907 2051 1941 2116 1944 2044 2050 2028 1917 2049
    ## [91253] 1956 2144 2203 2203 2057 2113 2023 2141 2157 1957 2033 2123 1935 2107
    ## [91267] 2116 2018 2116 1927 2302 2106 1938 2105 2104 2139 2217 2113 2121 2206
    ## [91281] 2223 2139 2141 1952 2015 2050 2226 2101 2047 2011 1943 2241 2033 2214
    ## [91295] 2303 2202 2055 2126 2206 2143 2029 2133 2104 2123 2151 2212 2200 2218
    ## [91309] 2058 2056 2210 2258 2120 2233 2259 2044 2230 2233 2217 2227 2038 2256
    ## [91323] 2059 2027 2019 2240 2235 2116 2130 2211 2123 2246 2255 2209 2155 2234
    ## [91337] 2315 2104 2046 2115 2101 2106 2226 2252 2111 2232 2256 2224 2130 2150
    ## [91351] 2245 2122 2131 2249 2147 2246 2119 2123 2213 2206 2325 2245 2157 2055
    ## [91365] 2156 2152 2202 2104   43 2206 2137 2344 2239 2108 2205 2303 2217 2130
    ## [91379] 2204 2135 2253 2328 2158 2210 2349   53 2324 2303 2306 2130   25 2301
    ## [91393] 2310 2335    1 2206 2356 2241 2212 2319 2338 2212 2354 2212 2214 2319
    ## [91407] 2311   41 2303 2335   17   40   29 2309 2224 2349 2326 2253 2300 2325
    ## [91421]    5 2208 2158 2357 2315 2332 2252   25   11 2348   23 2207 2349 2256
    ## [91435] 2233   17 2305 2354 2319 2359   58 2338 2226   14 2335    6  122   47
    ## [91449]   30    9 2323  115 2318 2243 2319 2341  106   29   45   58 2347   40
    ## [91463]  109 2351   25 2400  102 2348   27    3   16  230 2355 2326   38   46
    ## [91477]   22 2345  121  100  101   27    2  114   31   23  137  228  218  117
    ## [91491]   51   40  759  432   59   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [91505]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [91519]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [91533]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [91547]   NA   NA   NA   NA   NA  451  446  119  651  701  830  907 1022  854
    ## [91561]  920  853  744  659  745  825  716  836  651  906  802  828  913 1011
    ## [91575]  809  807  934  903  744  823  917 1043 1002  836  852  825  922  932
    ## [91589]  930  919  928  725  815  945  935  943  808  923  904  939  900  759
    ## [91603]  828  934  737  927  805  840  920  806  921 1026  827 1006 1001  809
    ## [91617] 1005  958 1008 1132 1040 1029 1039  804  904  805 1053 1031 1213 1026
    ## [91631]  851 1015  905  931  857 1022 1020  900 1012  828  907  841 1008  856
    ## [91645]  928 1104 1007 1005  812 1050  945  925 1002 1024 1027  851 1147 1220
    ## [91659] 1135 1109 1118  936  933 1150 1205 1053 1055 1044 1240 1107 1240 1113
    ## [91673] 1149  950 1125 1141 1140 1047  934 1103 1248  956 1006 1020 1137 1044
    ## [91687] 1027 1200 1039 1125 1110 1136 1022 1135 1050 1137 1157 1113 1124 1054
    ## [91701] 1203 1000 1246 1135 1021 1053 1101 1321 1053 1135 1025 1116 1122 1206
    ## [91715] 1013 1159 1212 1050 1149 1238 1046 1306 1120 1216 1318 1147 1121 1307
    ## [91729] 1253 1036 1256 1119 1111 1314 1121 1219 1136 1304 1233 1257 1250 1030
    ## [91743] 1211 1325 1303 1313 1107 1043 1309 1057 1152 1259 1202 1158 1245 1257
    ## [91757] 1330 1237 1136 1343 1251 1414 1356 1159 1148 1244 1112 1221 1253 1223
    ## [91771] 1355 1331 1221 1128 1437 1329 1333 1415 1523 1404 1231 1349 1207 1412
    ## [91785] 1431 1231 1732 1340 1204 1353 1425 1255 1433 1454 1355 1404 1325 1226
    ## [91799] 1319 1332 1357 1422 1400 1418 1213 1603 1244 1333 1210 1232 1452 1208
    ## [91813] 1456 1221 1440 1508 1559 1356 1426 1511 1356 1424 1231 1449 1426 1311
    ## [91827] 1330 1450 1455 1455 1501 1501 1439 1529 1510 1434 1501 1527 1510 1612
    ## [91841] 1519 1559 1550 1327 1550 1356 1451 1615 1344 1617 1524 1619 1359 1525
    ## [91855] 1603 1559 1446 1427 1604 1420 1406 1417 1607 1414 1458 1613 1529 1557
    ## [91869] 1650 1619 1649 1647 1735 1652 1425 1619 1455 1601 1600 1434 1541 1611
    ## [91883] 1600 1729 1428 1657 1738 1540 1623 1631 1635 1645 1618 1714 1438 1634
    ## [91897] 1735 1616 1817 1533 1539 1636 1706 1745 1736 1805 1530 1551 1818 1719
    ## [91911] 1547 1732 1801 1658 1726 1635 1724 1831 1810 1839 1625 1806 1757 1810
    ## [91925] 1611 1722 1616 1659 1725 1748 1800 1755 2020 1805 1752 1819 1904 1833
    ## [91939] 1658 1650 1830 1620 2011 1709 1731 1646 1731 1628 1853 1814 1825 1805
    ## [91953] 1825 1839 1807 1911 1846 1801 1858 1802 1653 1905 1828 1657 1749 1902
    ## [91967] 1901 1836 1748 1901 1654 1735 1922 1835 1921 1922 1916 1836 1853 1947
    ## [91981] 1914 1859 1753 1757 1847 1816 1928 1927 1808 1911 1745 1851 1803 1918
    ## [91995] 1912 1946 1747 1939 1914 1855 2001 1843 1836 1936 1940 2014 1909 1930
    ## [92009] 1743 1831 1735 1720 2052 1943 2030 1932 1905 2153 1810 1848 2012 1813
    ## [92023] 1959 1920 1828 2032 2023 1934 2016 1811 1808 1853 1956 2023 1926 1818
    ## [92037] 2109 1916 2027 1932 2022 1924 2004 1819 1902 2100 1956 1842 1852 2035
    ## [92051] 2050 1849 1959 1847 2054 2118 2044 1830 2105 2052 2033 2117 2033 2053
    ## [92065] 1927 1935 2046 1946 2006 2145 1908 2047 1924 2109 2036 2111 2151 1847
    ## [92079] 1938 2046 1943 2059 2146 2122 1927 2019 2046 2109 2026 1935 2044 2027
    ## [92093] 1928 1938 1957 2017 2148 2006 1933 2030 2157 2023 2140 2151 2006 2015
    ## [92107] 2113 2011 2030 2042 2023 2003 1957 1928 2035 2155 2141 2056 2204 2257
    ## [92121] 2022 2011 2227 2028 2154 2036 2205 2035 2134 2013 2220 1952 2005 2148
    ## [92135] 2153 2227 2238 2115 2032 2216 2037 2227 2255 2210 2154 2029 2121 2231
    ## [92149] 2032 2116 2231 2211 2327 2213 2214 2228 2052 2124 2237 2240 2309 2104
    ## [92163] 2030 2235 2043 2037 2120 2241 2258 2206 2056 2054 2252 2153 2239 2112
    ## [92177] 2245 2225 2234 2046 2136 2300 2151 2241 2253 2154 2133 2307 2332 2214
    ## [92191] 2235 2303 2140 2232 2148 2327 2248 2146 2252 2159 2133 2231    2 2138
    ## [92205] 2328 2110 2249 2217 2324 2353 2145 2332 2156 2212 2315 2316 2322 2339
    ## [92219] 2359 2346 2328 2336 2339 2205 2218 2354 2216   33 2335 2209   20 2207
    ## [92233]   52 2214 2306  151 2155 2213 2241 2340 2208    1 2314 2237  108   18
    ## [92247] 2341   33 2350  109 2245  118 2247 2304   17   17 2246   47   37 2315
    ## [92261]  104   39 2249 2343  100  146 2323 2306   18 2311 2319 2314 2315 2332
    ## [92275] 2340  113  325  117   16   14  126  134  144 2350   24   33  135   46
    ## [92289]  103  132   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [92303]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [92317]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [92331]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [92345]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [92359]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [92373]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [92387]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [92401]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [92415]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [92429]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [92443]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [92457]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [92471]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [92485]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA  651  825  841  838
    ## [92499] 1021  927  712  644  753  656  856  922  837  844  821  659  747  853
    ## [92513]  948  918  723  716  716  834  747  905 1052  800  845  820  944  913
    ## [92527]  826  816  841  723  757  910  940  805  814  929  851  904  909  939
    ## [92541]  912  826  925  948  941  843  932  806  737  809  954  916  906 1030
    ## [92555]  835  931  839  937 1010  759  858 1013  745  941 1134  903  951 1202
    ## [92569] 1025  942  847 1010  909 1021 1017  817  833  840 1034 1005  912 1014
    ## [92583] 1039  919  913 1023  822  816 1039  938 1023  902 1048  927 1014  935
    ## [92597] 1028 1052 1026 1055 1053 1221 1044  956 1013  915  920 1038 1001  923
    ## [92611] 1045 1052 1046 1046 1108 1124 1242 1059 1126 1048  937  925 1113 1051
    ## [92625] 1006 1054  953 1058  846 1031  924 1015 1128 1108 1123 1100 1040 1041
    ## [92639] 1115  945 1245  924 1105  945 1023 1126  945 1037 1257 1122 1004 1047
    ## [92653] 1114  955 1138 1154  956 1037 1019  949  931 1123 1041 1027  950 1120
    ## [92667] 1016 1027 1225  944 1040 1026 1035 1131 1027 1159 1114 1028 1202 1051
    ## [92681] 1032 1001 1202 1050 1248 1017  950 1102 1046 1143 1217 1148 1028 1236
    ## [92695] 1054 1126 1140 1216  958 1041 1356 1104 1237 1148 1035 1009 1219 1226
    ## [92709] 1129 1033 1222 1044 1224 1241 1027 1221 1047 1213 1121 1151 1030 1036
    ## [92723] 1231 1215 1230 1221 1129 1113 1205 1141 1247 1237 1256 1235 1105 1219
    ## [92737] 1149 1040 1213 1103 1539 1503 1230 1054 1320 1109 1246 1254 1217 1133
    ## [92751] 1306 1121 1211 1239 1204 1433 1243 1228 1114 1116 1158 1050 1100 1103
    ## [92765] 1128 1307 1303 1153 1307 1257 1149 1317 1309 1327 1203 1126 1209 1250
    ## [92779] 1246 1159 1331 1204 1151 1355   NA 1212 1350 1231 1340 1318 1212 1306
    ## [92793] 1239 1333 1306 1330 1351 1312 1430 1207 1400 1346 1212 1404 1350 1248
    ## [92807] 1309 1147 1252 1230 1359 1228 1406 1409 1328 1253 1316 1207 1214 1203
    ## [92821] 1217 1410 1335 1350 1433 1258 1226 1359 1309 1419 1335 1414 1434 1333
    ## [92835] 1329 1428 1341 1326 1331 1505 1347 1450 1312 1431 1414 1436 1458 1430
    ## [92849] 1243 1509 1310 1322 1303 1456 1424 1455 1327 1345 1254 1449 1440 1405
    ## [92863] 1532 1400 1304 1507 1532 1502 1520 1421 1401 1445 1536 1519 1534 1431
    ## [92877] 1328 1346 1435 1411 1401 1407 1533 1403 1415 1533 1556 1541 1624 1353
    ## [92891] 1350 1612 1346 1352 1454 1613 1525 1429 1455 1546 1539 1556 1529 1510
    ## [92905] 1458 1437 1621 1540 1537 1538 1621 1513 1700 1633 1614 1529 1457 1502
    ## [92919] 1432 1625 1531 1511 1651 1510 1631 1652 1446 1554 1535 1426 1627 1637
    ## [92933] 1629 1427 1531 1628 1647 1650 1601 1706 1536 1703 1702 1523 1643 1637
    ## [92947] 1652 1738 1705 1554 1745 1723 1447 1506 1529 1636 1629 1709 1453 1546
    ## [92961] 1534 1509 1657 1721 1634 1635 1713 1732 1533 1559 1547 1621 1723 1529
    ## [92975] 1559 1739 1612 1746 1702 1524 1638 1716 1616 1716 1639 1714 1723 1603
    ## [92989] 1739 1652 1749 1753 1808 1754 1746 1808 1651 1659 1647 1653 1832 1659
    ## [93003] 1751 1745 1627 1927 1805 1945 1809 1652 1610 1751 1739 1601 1823 1711
    ## [93017] 1747 1826 1655 1812 1802 1719 1717 1803 1810 1751 1822 1630 1650 1729
    ## [93031] 1634 1710 1716 1830 1827 1844 1712 1751 1800 1814 1719 1747 1746 1738
    ## [93045] 1755 1852 1712 1842 1721 1849 1742 1729 1813 1626 1639 1848 1834 1904
    ## [93059] 1655 1822 1846 1912 1852 1846 1852 1737 1904 1649 1908 1821 1826 1750
    ## [93073] 1743 1941 1914 1912 1910 1733 1845 1759 1900 1710 1926 1723 1839 1822
    ## [93087] 1924 1848 1941 1934 1813 1838 1738 1724 1847 1908 1933 1812 1847 1841
    ## [93101] 1954 1757 1750 1941 1929 1848 1842 1756 1909 1946 1858 1735 1937 1925
    ## [93115] 1958 1817 1731 1830 2115 2017 1801 1846 1919 1759 1830 1910 1949 1948
    ## [93129] 2010 1745 2013 1801 1833 1944 1831 1924 1817 1937 1906 2040 2013 2025
    ## [93143] 1825 2009 1947 1911 1954 1849 1807 1811 2004 2025 1924 1944 2012 1955
    ## [93157] 1759 2005 1923 2017 1903 2033 1827 1901 1902 2032 1950 2018 2026 1902
    ## [93171] 2034 2029 1947 1823 1903 1918 1914 2023 2031 1911 2021 1931 1958 2054
    ## [93185] 2045 2010 2028 1942 2033 1936 2015 1939 1855 1847 2056 1939 2116 1838
    ## [93199] 1924 2005 1854 2104 1915 2059 2104 2000 2011 1947 1914 2105 2023 2036
    ## [93213] 1945 2032 1910 2017 1947 2131 2119 1950 2001 2019 2109 1947 2112 2111
    ## [93227] 2139 2136 2111 2110 2107 2007 2135 1926 2211 2151 2157 2143 2027 2048
    ## [93241] 2202 2020 2131 2038 2101 2141 2009 2035 2116 2210 2204 2042 2019 2216
    ## [93255] 2153 2006 2133 2158 2137 2209 2142 2131 2104 2045 2231 2108 2034 2040
    ## [93269] 2208 2215 2205 2049 2008 2228 2103 2344 2006 2014 2201 1954 2043 2039
    ## [93283] 2225 2208 2058 2229 2010 2157 2210 2255 2231 2128 2245 2038 2350 2124
    ## [93297] 2242 2225 2220 2029 2132 2132 2057 2053 2307 2221 2233 2215 2210 2155
    ## [93311] 2215    8 2210 2233 2251 2149 2124 2144 2259 2235 2221 2057 2245   32
    ## [93325] 2146 2106 2256 2121 2229 2201 2239 2255 2217 2120 2223 2224 2140 2103
    ## [93339] 2132 2054 2230 2245 2120 2308 2114 2241 2314 2313 2320 2328 2337 2254
    ## [93353] 2322 2146 2229 2256 2308 2132 2159 2216 2148 2213 2335 2158    4 2225
    ## [93367] 2340 2317 2227 2157   14   13  107 2338 2352    3 2158 2254 2324 2328
    ## [93381] 2219 2302 2225 2331 2304 2201 2350 2232 2313 2248  131    5 2355    8
    ## [93395] 2342 2301 2318 2352 2339 2224 2323 2328   55 2240   55   31   34   44
    ## [93409]   24 2334 2253 2305   34 2251 2316   47 2310   38    1 2256 2301 2353
    ## [93423] 2321 2324 2342 2301 2328 2324 2332 2350 2356 2352    1   19   15  430
    ## [93437]  449  440   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA  431  440
    ## [93451]  502  135  646  757  820  848 1024   NA  701  849  711  814  920  821
    ## [93465]  812  647  848  752  756  845  720  834  722  740  917  946  814  747
    ## [93479] 1050  912  921  807  713  740  845  930  920  916  823  832  919  832
    ## [93493]  835  808  802  941  900  919  836  728  756  940  837  849  837  743
    ## [93507]  922  901  820  809  954  935  850  801  853  808 1009  800  942 1011
    ## [93521]  813 1008  913  826  927  752 1006  844  959 1033  805  810 1000 1145
    ## [93535] 1018  944  940 1022  909 1029  954  843 1205  841  827  957  855 1035
    ## [93549]  829  917 1029  909 1013  818  835  927 1047 1029 1009  829 1046 1033
    ## [93563] 1035 1033 1036 1033  930 1217  911  939 1024  918 1055 1036 1049 1049
    ## [93577] 1020 1100 1100  905 1243  935  903  937 1101  910 1114  927 1043 1106
    ## [93591] 1032 1054  943 1257 1128 1124 1108 1011 1129 1024 1113 1137 1109 1020
    ## [93605] 1026  942 1255 1007 1028  908 1129 1111 1126 1101 1125 1014 1120 1006
    ## [93619] 1001 1056 1005 1029  946  931 1019 1107  948 1027 1132  930 1204 1012
    ## [93633] 1029 1047 1051 1028 1012 1056 1113 1032 1133 1027  959 1130 1036 1044
    ## [93647]  937 1138 1019 1047 1145 1007 1045 1115 1159 1146 1113 1029 1205 1049
    ## [93661] 1157 1000 1218 1013 1002 1047 1121 1008 1113 1113 1248 1050 1235 1014
    ## [93675] 1231 1027 1350 1143 1008 1219 1032 1223 1102 1236 1216 1058 1248 1141
    ## [93689] 1034 1254 1227 1234 1057 1237 1159 1241 1240 1040 1123 1252 1101 1253
    ## [93703] 1241 1047 1259 1250 1255 1238 1057 1200 1111 1521 1209 1113 1244 1118
    ## [93717] 1243 1220 1251 1442 1136 1345 1155 1302 1119 1129 1101 1114 1313 1311
    ## [93731] 1236 1245 1236 1237 1157 1316 1211 1128 1150 1123 1332 1144 1146 1356
    ## [93745] 1210 1334 1217 1337 1225 1120 1347 1322 1144 1233 1153 1328 1242 1323
    ## [93759] 1234 1300 1353 1315 1256 1351 1412 1341 1205 1219 1242 1335 1313 1411
    ## [93773] 1223 1152 1238 1420 1416 1356 1425 1308 1336 1353 1357 1222 1228 1303
    ## [93787] 1324 1315 1320 1408 1359 1326 1321 1348 1419 1408 1247 1238 1337 1433
    ## [93801] 1435 1305 1306 1453 1438 1334 1312 1321 1401 1354 1452 1421 1449 1242
    ## [93815] 1452 1404 1445 1439 1333 1435 1457 1501 1427 1314 1350 1306 1505 1338
    ## [93829] 1517 1411 1431 1504 1519 1446 1440 1410 1349 1522 1457 1348 1459 1524
    ## [93843] 1433 1415 1446 1501 1423 1524 1324 1327 1507 1429 1357 1529 1414 1347
    ## [93857] 1345 1433 1611 1558 1601 1437 1418 1545 1407 1633 1405 1355 1457 1406
    ## [93871] 1451 1545 1402 1636 1424 1551 1430 1435 1536 1536 1542 1608 1429 1351
    ## [93885] 1612 1625 1428 1555 1608 1526 1436 1511 1603 1506 1448 1504 1513 1534
    ## [93899] 1439 1628 1624 1500 1451 1456 1648 1558 1431 1532 1641 1651 1652 1639
    ## [93913] 1648 1707 1540 1525 1728 1557 1622 1503 1502 1617 1709 1711 1537 1701
    ## [93927] 1542 1706 1648 1619 1706 1502 1511 1707 1611 1630 1602 1628 1540 1616
    ## [93941] 1640 1746 1652 1727 1707 1715 1659 1714 1739 1525 1726 1640 1652 1620
    ## [93955] 1650 1658 1706 1621 1812 1824 1633 1610 1752 1641 1702 1728 1832 1652
    ## [93969] 1600 1644 1635 1804 1929 1739 1601 1810 1722 1634 1607 1613 1745 1758
    ## [93983] 1746 1746 1753 1807 1613 1949 1702 1705 1808 1721 1621 1706 1730 1746
    ## [93997] 1743 1759 1812 1825 1654 1652 1819 1826 1748 1736 1745 1655 1654 1641
    ## [94011] 1838 1836 1916 1810 1748 1720 1842 1656 1636 1716 1720 1820 1845 1741
    ## [94025] 1737 1908 1924 1921 1701 1820 1745 1729 1853 1737 1718 1712 1847 1821
    ## [94039] 1655 1852 1747 1759 1757 1749 1825 1716 1706 1753 1809 1728 1903 1854
    ## [94053] 1716 1858 1818 1831 1734 1855 1833 1905 1819 1752 1729 1734 1923 1930
    ## [94067] 1911 1721 1756 1840 1921 1906 1825 1930 1855 2028 1842 1809 1816 1913
    ## [94081] 1923 1951 1732 2107 1944 1855 1923 1840 1948 1925 1737 1731 1850 1941
    ## [94095] 2003 1808 1830 1845 1902 1803 2013 1815 1817 1823 1850 1948 1754 1750
    ## [94109] 1749 1941 1841 1836 1806 1816 1939 1808 1934 1917 1942 1950 2002 1841
    ## [94123] 1910 1951 1845 1912 2004 2003 2000 1911 1858 1840 2012 1956 2008 1955
    ## [94137] 2021 1926 1926 1844 1825 2018 1847 1859 2022 2031 1953 1942 1937 1912
    ## [94151] 2055 2247 2030 2004 2010 1949 1917 2016 2056 2025 2038 2026 2040 1919
    ## [94165] 1920 1932 2028 1840 2028 1900 2104 2015 2027 1935 2122 2021 1940 2013
    ## [94179] 2022 2050 2050 2112 1904 2045 1913 2100 1950 1959 2024 2101 1920 1950
    ## [94193] 2047 2106 2029 2100 2039 2027 1917 2115 2016 2139 2047 2116 2020 2014
    ## [94207] 2142 2158 2006 2037 2019 2113 2011 2012 2158 2047 2021 2131 2020 2216
    ## [94221] 2029 2026 2142 2220 2020 2153 1958 2026 2022 2057 2136 2014 2049 2036
    ## [94235] 2242 2124 2033 2123 2056 2205 2150 2139 2236 2215 2202 2119 2250 2045
    ## [94249] 2013 2203 2008 2037 2340 2047 2030 2056 2126 2012 2203 2246 2330 2215
    ## [94263] 2134 2222 2119 2111 2254 2204 2226    6 2139 2131 2312 2115 2032 2202
    ## [94277] 2300 2149 2147 2220 2212 2133 2043 2108 2155 2238 2229 2137 2046 2216
    ## [94291] 2210 2226 2327 2244 2135 2123 2328 2121 2254 2208 2128 2243 2206 2126
    ## [94305] 2243 2124 2116 2125 2121 2210 2058 2114 2212 2105 2255 2315 2306 2258
    ## [94319] 2257  101 2226 2158 2337 2317 2315 2232 2227    4 2159 2249 2127 2311
    ## [94333] 2219 2303 2200 2229 2232 2224 2151   12 2349 2200 2304 2231 2342 2318
    ## [94347] 2338    2 2337 2242 2319 2207 2328 2346 2232  131 2327 2330 2208 2351
    ## [94361] 2148 2331   11 2309 2330 2211 2232    6 2218 2319   12 2300   14 2259
    ## [94375]   13 2250 2326 2252   26 2230   13 2254 2304   23   33  152 2349 2304
    ## [94389]   45 2255 2303   35 2318 2307   20 2325 2332   20   39 2326   45 2344
    ## [94403] 2346   48   17    9 2400   30   38   42  107   NA   NA   NA   NA   NA
    ## [94417]  451  218  639  757  827 1015  822  749  651  819  713  741  904  848
    ## [94431]  841  713  905  814  818  708  810  908  929  738  716  927  808  827
    ## [94445]  729  857  833  800  907  808 1050  854  825  917  914  843  729  837
    ## [94459]  812  908  812  748  906  909  810  910  848  902  903  930  756  732
    ## [94473]  922  918  759  850  830  952  812  936  851  840  728  811  951  942
    ## [94487] 1001  801  825  906  916 1125  925  928  751  810  802  844 1014  933
    ## [94501] 1009  920 1026  841  832  910 1043 1004 1002 1208  911  921 1012 1223
    ## [94515] 1033  933  835  858  959  954  917  902 1030 1006 1109 1040  910  834
    ## [94529] 1025 1038 1204 1018 1053 1017 1010  955  914 1020 1031 1057 1035 1036
    ## [94543]  946  915  927 1053 1234 1049 1229  925  935 1033 1026 1004  941 1103
    ## [94557]  859  851 1059 1047 1100  924 1045 1024 1052 1017 1021  920 1132  957
    ## [94571]  959 1042  933  904 1030 1004  925 1112 1240 1012 1050 1024 1005 1019
    ## [94585] 1107 1102 1113 1030  909  932  909 1049  953 1001 1019  938 1102 1120
    ## [94599]  941  928  956  945 1136 1011 1038  958  959 1208 1051 1103 1055 1146
    ## [94613] 1100 1046 1016 1043  952 1011  953 1102  953 1136 1032 1136 1146 1101
    ## [94627] 1047 1129 1022 1208 1003  940 1114 1016 1224 1123 1138 1121 1014 1114
    ## [94641] 1003 1133 1211 1159 1117 1004 1217 1206 1156 1201 1019 1207 1036 1114
    ## [94655] 1226 1055 1228 1146 1359 1215 1015 1127 1036 1043 1225 1037 1056 1234
    ## [94669] 1208 1226 1238 1155 1244 1240 1122 1035 1108 1158 1245 1527 1057 1058
    ## [94683] 1121 1046 1514 1123 1228 1240 1232 1120 1427 1059 1252 1121 1259 1249
    ## [94697] 1302 1127 1256 1131 1130 1103 1220 1252 1228 1320 1300 1238 1157 1247
    ## [94711] 1151 1142 1306 1214 1242 1312 1153 1344 1337 1211 1347 1208 1232 1132
    ## [94725] 1338 1252 1312 1215 1150 1359 1213 1122 1214 1214 1340 1328 1309 1350
    ## [94739] 1328 1300 1335 1337 1358 1251 1330 1157 1403 1200 1222 1201 1351 1324
    ## [94753] 1325 1217 1406 1410 1425 1401 1303 1301 1338 1400 1312 1316 1359 1256
    ## [94767] 1240 1341 1410 1416 1242 1417 1320 1443 1430 1249 1408 1452 1338 1332
    ## [94781] 1427 1339 1420 1314 1331 1252 1418 1424 1521 1348 1248 1359 1337 1504
    ## [94795] 1415 1456 1506 1519 1510 1316 1427 1354 1451 1432 1331 1335 1508 1330
    ## [94809] 1402 1350 1504 1434 1322 1456 1341 1511 1519 1534 1354 1324 1333 1446
    ## [94823] 1411 1441 1349 1436 1529 1342 1430 1525 1625 1430 1500 1406 1346 1424
    ## [94837] 1539 1558 1559 1613 1438 1524 1601 1528 1405 1536 1554 1610 1433 1439
    ## [94851] 1429 1615 1448 1534 1623 1544 1509 1439 1414 1455 1500 1558 1633 1426
    ## [94865] 1448 1504 1508 1526 1520 1625 1455 1547 1634 1637 1459 1442 1639 1648
    ## [94879] 1457 1531 1626 1541 1539 1650 1538 1655 1655 1545 1542 1551 1640 1453
    ## [94893] 1706 1716 1744 1624 1648 1633 1649 1641 1655 1525 1636 1714 1501 1748
    ## [94907] 1559 1508 1531 1702 1551 1625 1651 1658 1658 1645 1700 1735 1746 1701
    ## [94921] 1625 1755 1644 1745 1640 1526 1635 1628 1709 1716 1614 1735 1735 1610
    ## [94935] 1700 1647 1759 1818 1641 1725 1614 1935 1644 1813 1800 1625 1634 1654
    ## [94949] 1743 1645 1731 1754 1723 1646 1620 1649 1652 1601 1622 1701 1618 1756
    ## [94963] 1737 1824 1821 1755 1613 1702 1700 1801 1707 1658 1636 1808 1732 1659
    ## [94977] 1810 1722 1816 1705 1637 1750 1850 1849 1715 1805 1642 1641 1849 1808
    ## [94991] 1835 1839 1834 1740 1755 1628 1650 1837 1735 1721 1744 1920 1805 1748
    ## [95005] 1729 1912 1741 2031 1758 1915 1903 1904 1711 1742 1836 1915 1735 1918
    ## [95019] 1924 1717 1855 1846 1857 1802 1844 1813 1715 1756 1745 1902 1841 1812
    ## [95033] 1804 1904 1711 1721 1858 1731 1837 1828 1800 1943 1934 1842 1818 1750
    ## [95047] 1839 1901 1807 1903 1932 1804 1825 1841 1956 1918 2009 1743 2113 1931
    ## [95061] 1801 1924 1939 1735 1844 1838 1859 1752 2001 1813 1957 1910 1911 2007
    ## [95075] 2002 2013 1841 1800 1837 1947 1852 1939 1847 1801 1811 2015 1827 2005
    ## [95089] 2018 1757 1955 1940 1953 2012 1949 1827 1816 1928 1909 1953 1906 2016
    ## [95103] 1948 2012 2024 2031 2024 1832 2031 1809 1911 2031 2016 2000 2052 2020
    ## [95117] 1955 2025 1906 1956 2015 1955 2049 2057 1827 1922 2052 2039 1918 2041
    ## [95131] 1931 2100 1903 1943 1929 1945 2003 2035 1901 2040 1938 2105 1849 2048
    ## [95145] 1900 2103 1946 2101 2039 1916 2025 1916 2023 2020 2047 1858 2053 2128
    ## [95159] 1945 1932 2000 2006 2033 2011 1942 2107 2108 1950 2103 2002 1922 2009
    ## [95173] 1953 2058 2133 2003 2025 2049 2010 2141 2125 2057 2158 2111 1942 2037
    ## [95187] 2005 1955 2029 2152 2114 2107 2133 2039 2128 2034 2040 2010 2151 2147
    ## [95201] 2143 2040 2221 2030 2123 2133 2007 2025 2116 2159 2250 2042 2154 2109
    ## [95215] 1946 2032 2040 2140 2226 2049 2109 2047 2004 2236 2043 2038 2208 2225
    ## [95229] 2041 2344 2205 2032 2204 2158 2107 2109 2200 2010 2223 2155 2100 2236
    ## [95243] 2105 2218 2238 2256 2033 2207 2246 2152 2359 2034 2057 2124 2038 2141
    ## [95257] 2136 2246 2241 2229 2152 2143 2238 2111 2112 2222 2137 2146 2250 2115
    ## [95271] 2149 2156 2215 2143 2234 2158 2120 2051 2155 2224 2238 2229 2053 2059
    ## [95285] 2317 2318 2224 2315 2243 2222   42 2226 2250 2219 2252 2111 2253 2311
    ## [95299] 2252 2339 2118 2154 2145 2244 2218 2224 2156 2326 2153 2134 2243 2307
    ## [95313] 2248 2202 2316   15 2203 2306 2320 2307 2145 2312 2302 2230 2137 2215
    ## [95327]  118 2213 2310 2301 2325   29 2226 2300 2341 2344 2217 2301 2235   42
    ## [95341] 2252 2303 2321 2355 2228   30 2353 2346 2320 2241 2245 2238   33   57
    ## [95355] 2333   32 2309 2302 2247  126 2256 2315 2251 2302 2309 2400    4   40
    ## [95369] 2320  104  102 2328 2344 2336 2342 2356 2324   20 2346  429  432   NA
    ## [95383]   NA   NA   NA   NA  459  451  131  516  408  204  340  856  846  749
    ## [95397]  709  801  850 1103  913  904  842  921  841  744  844  932  856  845
    ## [95411] 1057  910  908  846  815  941  712  822  957  826  914  746  828  852
    ## [95425]  939  930  901  932  952  755  930  953  940 1010  919  949  852  743
    ## [95439] 1124  929  908  913  934 1001 1032  848 1003 1021 1025 1017  901 1204
    ## [95453] 1013  838 1027 1021  929 1021  916 1027  944  916  829 1031 1210 1040
    ## [95467]  900  901 1027 1027 1003  906  951  939 1053 1022 1037  922 1034  841
    ## [95481] 1052  916 1048 1049 1040 1046 1040 1111 1051 1017  849 1124  907  954
    ## [95495] 1100 1237 1032  939 1047  956 1003 1050 1117 1012 1105 1251 1035 1106
    ## [95509] 1033 1016 1052 1248 1044 1035 1131 1047 1100 1142 1021 1019  932 1035
    ## [95523]  935 1037 1053 1031 1120 1039 1138 1044 1206 1210 1116 1105  954 1112
    ## [95537]  947 1206 1123 1112 1214 1150 1057 1101 1247 1007 1210 1151 1018 1031
    ## [95551] 1230 1116 1151 1338 1133 1234 1150 1228 1256 1218 1045 1238 1131 1223
    ## [95565] 1210 1213 1039 1212 1118 1234 1125 1120 1108 1110 1225 1302 1054 1144
    ## [95579] 1256 1256 1533 1128 1220 1300 1451 1229 1319 1314 1105 1215 1302 1310
    ## [95593] 1459 1228 1324 1220 1146 1139 1203 1116 1317 1304 1241 1238 1152 1345
    ## [95607] 1418 1341 1329 1158 1325 1240 1238 1358 1143 1222 1331 1337 1306 1351
    ## [95621] 1241 1356 1358 1156 1410 1403 1311 1249 1226 1415 1345 1407 1418 1242
    ## [95635] 1404 1421 1328 1426 1317 1244 1451 1404 1442 1342 1503 1427 1420 1412
    ## [95649] 1328 1355 1542 1247 1417 1421 1338 1458 1337 1358 1319 1523 1453 1432
    ## [95663] 1324 1415 1502 1454 1329 1419 1514 1503 1324 1440 1544 1320 1617 1427
    ## [95677] 1530 1414 1605 1514 1547 1341 1414 1517 1434 1431 1512 1546 1418 1500
    ## [95691] 1600 1605 1420 1624 1446 1601 1650 1432 1610 1540 1541 1643 1422 1612
    ## [95705] 1615 1522 1636 1434 1552 1623 1431 1523 1703 1632 1629 1555 1516 1653
    ## [95719] 1708 1718 1658 1612 1643 1457 1747 1712 1625 1712 1733 1711 1712 1557
    ## [95733] 1722 1718 1751 1625 1721 1739 1840 1726 1720 1654 1527 1720 2012 1747
    ## [95747] 1754 1604 1739 1729 1808 1818 1650 1647 1759 1814 1717 1808 1830 1759
    ## [95761] 1916 1802 1716 1747 1731 1718 1842 1628 1812 1742 2000 2036 1859 1833
    ## [95775] 1701 1810 1706 1845 1820 1904 1857 1921 1756 1745 1838 1736 1856 1909
    ## [95789] 1713 1926 1929 1919 1939 1845 1957 1901 1730 1938 1939 1954 1744 1947
    ## [95803] 1825 1750 1929 1858 1811 2023 2008 1749 1819 1848 2024 2024 2027 1857
    ## [95817] 2006 2008 1907 2052 2048 2022 2023 2017 2049 2023 2043 2058 2038 1846
    ## [95831] 1911 2035 1943 1902 2106 1902 2011 1852 2009 2050 2025 2052 2126 1918
    ## [95845] 2050 2056 2103 1939 2019 2107 2143 2152 2054 2121 2109 2022 2142 2002
    ## [95859] 2148 2114 2200 2034 2117 2136 2128 2213 2123 2112 2236 2012 2050 2047
    ## [95873] 2324 1959 2045 2108 2148 2206 2044 2109 2227 2213   NA 2238 2210 2229
    ## [95887] 2046 2318 2350 2215 2204 2224 2133 2121 2236 2201 2123   NA   NA  107
    ## [95901] 2342 2231 2310 2301 2333   17    1 2321   NA  111   51  134  101 2348
    ## [95915] 2145    3    1  132   37  152   21  118 2351  149  143  200   53  143
    ## [95929]   59   19  129  329  136 2336  152  206  158  123  133  215  213  221
    ## [95943]  322  237 1003  256  111  109  326  123  136  114  136   NA   NA   NA
    ## [95957]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [95971]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [95985]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [95999]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [96013]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [96027]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [96041]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [96055]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [96069]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA  514  145  820  859
    ## [96083]  836  704  908  734  921  819  827  849 1116  812 1014  842  933  947
    ## [96097]  851  939  851  951  910  959 1020 1032  815  927 1031 1039 1032 1011
    ## [96111] 1142 1033 1000 1007  814 1025 1153 1207  826  849  902 1032  903 1051
    ## [96125] 1011 1030 1226 1044  900 1026 1055 1035 1016 1048 1133 1057 1055 1107
    ## [96139] 1006 1055 1106 1112 1011 1025 1105 1103 1125  944  940 1111 1132 1108
    ## [96153] 1031 1303 1007  958 1347 1035 1059 1122 1047 1042 1032  954 1040 1025
    ## [96167] 1126 1113 1023  944 1043 1059 1026 1147 1158 1141 1125 1144 1144 1046
    ## [96181] 1020 1122 1048 1009 1117 1224 1005 1127 1105 1150 1049 1202 1144 1209
    ## [96195] 1230 1032 1054 1130 1105 1258 1405 1234 1116 1218 1237 1049 1236 1029
    ## [96209] 1057 1144 1430 1237 1029 1045 1105 1236 1236 1259 1232 1244 1301 1243
    ## [96223] 1039 1318 1527 1059 1321 1106 1253 1437 1059 1241 1225 1111 1232 1309
    ## [96237] 1058 1147 1113 1305 1141 1237 1330 1258 1528 1330 1327 1131 1147 1133
    ## [96251] 1335 1127 1331 1330 1337 1149 1331 1321 1242 1154 1318 1507 1225 1150
    ## [96265] 1335 1258 1253 1323 1247 1137 1343 1348 1353 1342 1403 1231 1208 1329
    ## [96279] 1411 1447 1237 1205 1232 1152 1229 1608 1356 1247 1417 1337 1349 1428
    ## [96293] 1238 1403 1432 1217 1235 1324 1258 1310 1420 1444 1408 1324 1432 1423
    ## [96307] 1453 1333 1446 1404 1431 1357 1350 1335 1315 1323 1451 1316 1342 1305
    ## [96321] 1305 1500 1405 1519 1508 1450 1259 1453 1501 1322 1344 1432 1432 1436
    ## [96335] 1337 1451 1352 1425 1513 1545 1400 1541 1518 1323 1343 1438 1532 1425
    ## [96349] 1516 1355 1604 1420 1605 1437 1546 1544 1503 1454 1559 1526 1520 1426
    ## [96363] 1416 1550 1527 1635 1403 1454 1504 1435 1624 1426 1516 1425 1433 1527
    ## [96377] 1542 1436 1501 1632 1622 1640 1519 1429 1456 1504 1638 1442 1607 1532
    ## [96391] 1659 1544 1649 1639 1651 1442 1551 1631 1635 1545 1639 1537 1447 1506
    ## [96405] 1647 1508 1715 1712 1612 1517 1656 1657 1701 1704 1456 1514 1504 1551
    ## [96419] 1642 1712 1715 1524 1542 1540 1729 1724 1654 1701 1736 1519 1729 1657
    ## [96433] 1644 1617 1621 1605 1600 1732 1741 1627 1556 1650 1814 1758 1532 1607
    ## [96447] 1538 1737 1604 1751 1733 1712 1619 1637 1548 1822 1659 1643 1748 1730
    ## [96461] 1853 1744 1940 1701 1712 1603 1646 1752 1815 1726 1743 1743 1734 1712
    ## [96475] 1649 1819 1705 1731 1621 1805 1834 1833 1613 1800 1837 1708 1735 1646
    ## [96489] 1754 1637 1806 2005 1626 1648 1826 1750 1701 1658 1626 1844 1702 1710
    ## [96503] 1829 1859 1712 1856 1729 1645 1709 1845 1911 1704 1800 1729 1649 1717
    ## [96517] 1846 1902 1910 1752 1727 1812 1828 1916 1655 1733 1730 1914 1947 1731
    ## [96531] 1746 1829 1727 1917 1923 1713 1719 1727 1752 1939 1816 1900 1824 1718
    ## [96545] 1831 1737 1757 1929 1839 1923 1919 1928 1755 1944 1838 1735 1850 1937
    ## [96559] 1945 1927 1854 1932 1840 1807 1844 1824 2010 1841 1748 1929 1805 1903
    ## [96573] 2216 1904 1754 1919 1835 1819 1759 1810 1833 1850 1920 1909 1935 1906
    ## [96587] 1948 1958 1758 1756 2023 2004 1937 1900 1957 2021 1959 1809 2027 2018
    ## [96601] 1829 1829 2013 1816 1946 2022 1951 2011 1953 1823 1941 1859 2029 2006
    ## [96615] 1903 1914 1809 1845 2000 2036 1855 1825 2041 2011 1959 2204 1908 1932
    ## [96629] 2031 1909 2000 1942 1923 2100 2053 2026 1928 1851 2043 1941 2051 2037
    ## [96643] 2016 1850 2027 1919 2037 2043 2048 2055 2019 2106 2114 2056 1917 1937
    ## [96657] 2021 1941 1904 2116 2043 1922 1908 1941 2051 2117 2102 1933 2253 2000
    ## [96671] 1859 2055 2112 2016 2017 2122 2021 1953 2113 2023 2128 2036 2049 2105
    ## [96685] 1949 2112 2041 2021 2154 2132 2103 2137 2047 2032 1942 2020 2017 2034
    ## [96699] 1958 1943 2142 2158 2129 2003 2139 2007 1957 2202 2032 2055 2042 2024
    ## [96713] 2018 2212 1953 2031 2016 2215 2151 2017 2135 2025 1945 2204 2214 2019
    ## [96727] 2043 2140 2050 2103 2044 2014 2128 2206 2107 2137 2357 2202 2027 2225
    ## [96741] 2239 2235 2216 2130 2033 2047 2209 2126 2147 2250 2111 2123 2027 2210
    ## [96755] 2059 2142 2205 2111 2213 2134 2107 2222 2103 2239 2046 2239 2124   44
    ## [96769] 2132 2229 2301 2145 2210 2143 2250 2203 2313 2150 2259 2225 2243 2138
    ## [96783] 2043 2108 2248 2106 2256 2228 2200 2120 2258 2219 2126 2256 2319 2230
    ## [96797] 2114 2255 2125 2313 2133 2134 2154 2345 2352 2146 2339 2233 2335 2342
    ## [96811] 2334 2144 2335 2228 2346 2202 2350 2346 2209 2338 2223 2239 2203 2148
    ## [96825] 2216 2210 2328   38 2351   41 2210 2154 2315 2240 2201 2310 2357  147
    ## [96839]    4 2340 2349 2337 2258 2250 2259 2236   35 2324 2345   17 2322 2248
    ## [96853] 2240   48 2245   37   24 2338 2243 2317 2251   41 2257 2327 2257    1
    ## [96867]   56   41 2356   54  106 2341 2321 2358 2326 2334 2348    7 2321    2
    ## [96881] 2358   11  153 2356  402  228   19    5  213   15  242   45  153  226
    ## [96895]   45  458  123   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [96909]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [96923]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [96937]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [96951]   NA   NA   NA   NA   NA   NA   NA   NA  447  111  453  119  517  641
    ## [96965]  800  953  832 1045  717  648  801  647  719  901  655  717  746  817
    ## [96979]  827  944  715  916  849  822  750  811  901  838  834  839  805  922
    ## [96993]  805  818  929  823 1102  950  938  748  754  915  738  823  930  822
    ## [97007]  828  929  906  759  849  809  831  736  937  924  806  943  935  949
    ## [97021]  956  923  807  806  854  855  950  943  941 1004  942  946 1136  755
    ## [97035]  819  745  753  927  836  910  821 1009 1029 1005 1031  951  842  915
    ## [97049]  819 1016 1015  920  840  832 1019  909 1021 1201  921 1047 1037  824
    ## [97063]  823 1004 1039  905  839 1006 1025  935 1037 1013 1031 1113 1059 1014
    ## [97077] 1047  919 1228  906  911 1033 1028  937 1030 1106  958 1041 1107 1041
    ## [97091] 1047 1011  921 1028 1049  931  902  945  929 1014 1248  920  908  922
    ## [97105] 1117 1009  938  937 1052 1020 1054 1122  957  908 1058 1131 1021 1120
    ## [97119] 1135 1107 1021  922  945 1254 1034 1030 1052 1110  940 1032 1038 1011
    ## [97133] 1017 1313 1015 1116  956 1123 1133  932  923 1051  948 1147 1035  950
    ## [97147] 1031 1007 1026 1056 1026 1044 1103 1050 1028 1128 1040 1120 1033 1031
    ## [97161]  948 1151 1001 1040  932 1046 1101 1100 1000 1147 1200 1042 1210 1041
    ## [97175] 1131 1105 1158 1023  944 1129 1006 1008 1012 1200 1139 1010 1155 1229
    ## [97189] 1024 1116 1208 1207 1245 1025 1200 1359 1022 1119 1004 1222 1014 1207
    ## [97203] 1205 1006 1237 1040 1139 1050 1213 1146 1048 1117 1237 1237 1140 1241
    ## [97217] 1230 1225 1245 1041 1514 1246 1100 1120 1223 1236 1159 1305 1209 1233
    ## [97231] 1124 1304 1107 1222 1529 1056 1342 1104 1115 1324 1124 1236 1216 1135
    ## [97245] 1120 1148 1242 1136 1337 1307 1214 1153 1328 1318 1129 1141 1147 1303
    ## [97259] 1126 1201 1352 1141 1334 1126 1333 1120 1224 1213 1250 1240 1331 1506
    ## [97273] 1145 1310 1355 1328 1408 1253 1253 1413 1352 1403 1239 1346 1213 1355
    ## [97287] 1405 1154 1146 1229 1246 1412 1416 1331 1220 1244 1337 1434 1428 1353
    ## [97301] 1422 1339 1255 1449 1321 1237 1412 1443 1220 1342 1321 1332 1328 1440
    ## [97315] 1424 1349 1253 1309 1405 1448 1301 1455 1451 1341 1342 1458 1412 1246
    ## [97329] 1437 1344 1409 1511 1308 1506 1505 1303 1309 1447 1625 1349 1507 1414
    ## [97343] 1430 1523 1440 1422 1351 1315 1520 1358 1454 1354 1346 1328 1433 1416
    ## [97357] 1329 1528 1510 1321 1537 1510 1532 1342 1339 1504 1422 1523 1458 1437
    ## [97371] 1338 1403 1443 1609 1407 1411 1345 1430 1535 1358 1616 1344 1427 1447
    ## [97385] 1603 1604 1537 1414 1546 1452 1536 1647 1419 1430 1540 1453 1550 1433
    ## [97399] 1559 1442 1629 1600 1416 1409 1505 1437 1647 1613 1439 1441 1434 1536
    ## [97413] 1652 1446 1542 1602 1530 1531 1648 1627 1647 1539 1652 1649 1650 1514
    ## [97427] 1622 1519 1556 1655 1440 1653 1659 1646 1515 1731 1700 1558 1705 1528
    ## [97441] 1712 1651 1637 1509 1642 1701 1726 1612 1531 1547 1648 1551 1545 1722
    ## [97455] 1648 1633 1838 1613 1622 1733 1710 1746 1644 1707 1652 1803 1816 1653
    ## [97469] 1755 1649 1628   NA 1748 1707 1742 1714 1557 1649 1612 1644 1756 1734
    ## [97483] 1652 1651 1727 1745 1608 1653 1752 1618 1833 1751 1959 1712 1826 1733
    ## [97497] 1833 1818 1640 1621 1808 1733 1703 1819 1719 1851 1711 1804 1656 1823
    ## [97511] 1610 1803 1638 1817 1745 1755 1733 1744 1817 1850 1708 1838 1647 2032
    ## [97525] 1738 1734 1655 1902 1922 1836 1857 1910 1903 1637 1718 1824 1933 1831
    ## [97539] 1834 1855 1758 1708 1744 1858 1712 1900 1759 1921 1719 1729 1833 1804
    ## [97553] 1719 1701 1725 1825 1755 1924 1801 1712 1910 1908 1836 1742 1905 1707
    ## [97567] 1917 1837 1818 1927 1811 1927 1851 1836 2001 1858 1933 1927 1824 1834
    ## [97581] 1735 1838 1942 1853 1912 1738 1927 1916 1957 1843 1839 1817 1901 1950
    ## [97595] 1819 1808 1739 1850 1939 1958 1752 1831 1936 1904 1849 1826 1904 1843
    ## [97609] 1825 2017 1831 2141 1957 1847 1832 1801 1935 1844 2010 1930 1955 2029
    ## [97623] 1949 1812 1823 2016 2039 1843 1918 1807 2008 2040 2009 1834 1956 2010
    ## [97637] 1921 2038 1901 1831 2000 1851 1826 1945 2022 1821 1853 1822 2037 2048
    ## [97651] 2004 1856 1950 2021 1945 2054 2001 1922 2024 1842 2023 1934 2053 1905
    ## [97665] 1919 2045 1938 1847 1947 2023 2118 2051 2102 1847 1933 2008 1841 2029
    ## [97679] 2020 1955 2055 1944 2107 2056 2016 1933 1936 2114 1917 1927 2137 2034
    ## [97693] 2114 2059 1955 1905 2051 2034 2110 1935 2020 2000 2108 2053 2019 2153
    ## [97707] 2104 2024 1953 2000 2131 2134 1951 2024 2137 1950 2110 2130 2036 2054
    ## [97721] 2139 2152 2212 1933 2152 1948 2105 2013 2156 2226 2126 2134 2137 2014
    ## [97735] 2016 2107 2130 2034 2057 2204 2011 2124 2217 2214 2212 2154 2028 1945
    ## [97749] 1943 2005 2237 2013 2356 2206 2220 2142 2000 2151 2251 2020 2209 2236
    ## [97763] 2057 2209 2230 2038   17 2225 2121 2108 2058 2034 2235 2257 2032 2314
    ## [97777] 2157 2245 2039 2133 2042 2149 2126 2233 2138 2140 2215 2244 2142 2217
    ## [97791] 2224 2104 2124 2220 2145 2140 2249 2148 2113 2101 2306 2111 2254 2156
    ## [97805] 2234 2211 2157 2250 2114   52 2134 2132 2256 2051 2209 2156 2146 2246
    ## [97819] 2127 2114 2345 2323 2107 2316 2245 2228 2102 2111 2242 2219 2228 2337
    ## [97833] 2135 2208 2302 2152 2317 2209 2354 2204 2144 2154 2257 2336 2216 2204
    ## [97847] 2227 2353 2355 2302 2322 2217 2202    3 2321 2150 2354 2222 2349 2250
    ## [97861] 2341 2224 2220 2157 2146 2309 2339 2313 2220 2206 2332 2347 2209 2222
    ## [97875] 2307 2206 2310   23   11 2302 2257 2255 2309 2310   22 2241 2229    1
    ## [97889]    6   11 2242 2240   26 2349   49 2248 2248  105  105   19 2252    9
    ## [97903] 2304 2322 2304 2311 2317 2336 2312 2353 2335   39    3   19  240   35
    ## [97917]   NA   NA   NA   NA   NA   NA  459  155  313  135  313  122  303  212
    ## [97931]  206  140  545  555  152  500  654  759  854  843 1059  910  721  734
    ## [97945]  854  748  921  840  709  705  817  733  807  857  721  932  858  749
    ## [97959]  933  837  933  849  842 1140  825  834  902  948  944  827  950  744
    ## [97973]  847  915  840  814  802  926 1003  758  941  953 1002  948  942  850
    ## [97987]  922  947 1019  935  848  846  914  954  835 1014  958  913  814  830
    ## [98001]  929 1124  946  819 1149  934 1020 1033 1105  902 1017  952 1258  901
    ## [98015]  906 1026  902  859  930  948 1012 1047  922   NA 1050 1031 1002  940
    ## [98029]  921 1053 1054 1116 1100 1146 1056 1101  931 1121  933 1112 1114  948
    ## [98043] 1105  952  918 1129 1112 1113 1131 1056 1120 1324 1013  933 1005 1136
    ## [98057]  942 1038 1112 1135 1313 1042  924  936 1045 1129  958 1142 1111 1136
    ## [98071] 1004 1009 1136 1207 1158 1117 1110 1122 1114  953 1116 1038 1036 1116
    ## [98085] 1053 1322 1115  956 1141 1034 1019 1210 1046 1034 1148 1101 1200 1207
    ## [98099] 1050 1353 1120 1203 1002 1112 1142 1114 1007 1057 1156 1213 1131 1024
    ## [98113] 1112 1221 1036 1207 1058 1115 1215 1258 1009 1126 1059 1221 1210 1245
    ## [98127] 1047 1253 1144 1433 1243 1212 1013 1225 1059 1241 1241 1142 1204 1211
    ## [98141] 1234 1241 1228 1228 1058 1308 1148 1257 1102 1320 1242 1112 1310 1250
    ## [98155] 1113 1237 1059 1319 1302 1209 1136 1306 1307 1553 1202 1205 1150 1131
    ## [98169] 1251 1137 1126 1303 1150 1132 1246 1259 1136 1259 1214 1313 1314 1332
    ## [98183] 1333 1257 1143 1201 1520 1320 1334 1313 1345 1213 1311 1201 1150 1347
    ## [98197] 1353 1158 1254 1401 1327 1331 1314 1232 1157 1246 1148 1349 1341 1233
    ## [98211] 1328 1426 1418 1235 1406 1358 1305 1416 1209 1314 1410 1255 1230 1416
    ## [98225] 1402 1251 1431 1457 1233 1256 1321 1252 1415 1437 1406 1243 1305 1344
    ## [98239] 1440 1455 1248 1518 1423 1448 1353 1455 1449 1457 1437 1428 1335 1434
    ## [98253] 1304 1409 1436 1437 1408 1535 1517 1510 1516 1555 1607 1514 1543 1532
    ## [98267] 1421 1545 1418 1341 1425 1542 1437 1552 1557 1602 1420 1408 1458 1542
    ## [98281] 1638 1459 1548 1504 1438 1432 1453 1425 1630 1431 1629 1629 1636 1642
    ## [98295] 1526 1627 1634 1824 1622 1544 1519 1540 1512 1621 1701 1602 1453 1609
    ## [98309] 1643 1512 1636 1625 1635 1457 1641 1506 1647 1544 1557 1726 1703 1700
    ## [98323] 1640 1607 1616 1522 1634 1728 1711 1701 1607 1706 1643 1735 1717 1721
    ## [98337] 1745 1750 1710 1710 1535 1752 1547 1554 1724 1545 1551 1632 1712 1809
    ## [98351] 1804 1726 1547 1614 1738 1821 1740 1612 1841 1656 1826 1830 1741 1720
    ## [98365] 1632 1819 1823 1707 1820 1636 1719 1648 1742 1917 1816 1804 2015 1831
    ## [98379] 2056 1852 1803 1835 1825 1814 1724 1737 1757 1729 1744 1711 1838 1835
    ## [98393] 1735 1702 1721 1820 1704 1721 1701 1809 1859 1812 1748 1731 1713 1850
    ## [98407] 1822 1815 1803 1724 1852 1857 1804 1924 1825 1732 1917 1854 1921 1833
    ## [98421] 1906 1912 1914 1723 1747 1845 1850 1716 1956 1856 1813 1900 1922 1937
    ## [98435] 1919 1815 1929 1749 1903 1906 1811 1928 1758 1919 2018 1714 1943 1953
    ## [98449] 1736 1938 1931 1843 1928 1935 1759 1914 1853 1934 1938 1742 1928 1903
    ## [98463] 1943 1958 2008 1906 1849 2033 1914 1936 1926 1945 2011 2011 2030 1819
    ## [98477] 1955 2201 2018 1928 1838 1940 1857 2053 2039 2058 2035 1916 2001 1934
    ## [98491] 2012 2017 2005   NA 1847 1933 1953 1951 1909 1912 1941 1941 2045 1841
    ## [98505] 1911 2116 1905 1856 2046 2017 2045 2157 1925 2056 2003 2032 1939 2117
    ## [98519] 2110 1846 2218 2026 2055 2025 2031 2059 2147 1926 2135 2121 1933 2108
    ## [98533] 2149 2126 2122 2157 1950 2126 2029 2039 2147 2136 2211 2140 2043 1944
    ## [98547] 2110 2119 2053 2114 1947 2224 2138 2033 2020 2115 2203 2016 2104 2036
    ## [98561] 2224 2127 2225 2206 2157 2052 2206 1959 2151 2118 2027 2004 1951 2119
    ## [98575] 2121 2133 2100 2047 2105 1940 2229 2133 2229 2038 2149 2142 2112 2303
    ## [98589] 2116 2031 2146 2047 2307 2041 2200 2251 2203 2010 2317 2221 2044 2225
    ## [98603] 2301 2154 2111 2304 2253 2226 2123 2103 2211 2238 2309 2303 2124 2220
    ## [98617] 2235 2209 2306 2108 2131 2307 2108 2156 2239 2049 2218 2155 2253 2243
    ## [98631] 2332 2234 2334 2318 2244 2355 2123 2232 2224 2219 2221 2144 2150  130
    ## [98645] 2307 2302 2211 2212 2331 2253 2351 2139 2326 2255   28 2318 2158 2213
    ## [98659] 2217 2336  226 2306    1 2255 2345 2345 2229 2303 2334 2339 2338    4
    ## [98673] 2225 2243 2311 2235 2330 2313 2231 2223   56 2354 2346 2318   14 2232
    ## [98687]   58 2250    3 2336 2238 2247 2254 2310  247 2246   19    1   17 2248
    ## [98701] 2245  119   45 2319   34   27 2247 2347 2335 2351 2336  126  103 2351
    ## [98715] 2307  111  110 2310   13    4 2357    8 2329   47   27    3  103 2344
    ## [98729]   54  146   48   16   25  120   48  101 2342    9  200    1    8    1
    ## [98743]  102  200    3   56   30  241  134  141   38  251  146  106  237   44
    ## [98757]  102   57  120  129  128   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [98771]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [98785]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [98799]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [98813]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [98827]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [98841]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [98855]   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA   NA
    ## [98869]   NA   NA   NA  640  812  833 1022  728  851  723  853  934   NA  727
    ## [98883]  751  807  854  836  701  650  813  726  717  743  800  845 1053  814
    ## [98897]  844  828  846  827  913  835  753  917  923  901  954  844  923  740
    ## [98911]  858  824  853  911  845  814  821  858  806  937  833  935  804  955
    ## [98925] 1013  823  816  930  901  950  828  837  930  817  944  937  921 1005
    ## [98939]  852  835  812  814  943 1158 1012  939 1045 1034  906  938  856 1044
    ## [98953] 1008 1026 1054  913  849 1002  934 1041  839 1006  952  926  853 1031
    ## [98967]  943 1000 1013 1030 1104 1058  903 1038  923 1036 1021 1034 1055  904
    ## [98981]  911 1026 1107 1012 1030 1111  945  928 1246 1142  923 1037 1259 1239
    ## [98995]  941  902  955 1032  946 1013 1043 1137  917 1023 1118 1015 1034 1048
    ## [99009] 1058 1058 1134 1050  906  949 1044 1106  955  907 1044  935 1140 1057
    ## [99023] 1034 1034 1146 1006  936 1049 1331 1107  951 1312  943 1105 1157 1045
    ## [99037] 1057 1055 1132 1034 1044 1045 1011 1123  959 1020 1009 1118 1051 1021
    ## [99051] 1140 1043 1055 1037 1024 1017 1002 1041 1153 1010 1051 1019 1111 1054
    ## [99065] 1014 1042 1148 1059 1104 1140 1117 1053 1013 1203 1225 1044 1049 1239
    ## [99079] 1358 1124 1149 1019 1241 1120 1155 1212 1154 1023 1213 1202 1103 1210
    ## [99093] 1129 1146 1151 1311 1232 1056 1236 1233 1319 1233 1241 1108 1238 1158
    ## [99107] 1148 1228 1232 1109 1108 1244 1242 1543 1241 1125 1127 1247 1136 1145
    ## [99121] 1242 1144 1329 1209 1142 1247 1241 1114 1130 1248 1332 1234 1131 1120
    ## [99135] 1134 1130 1255 1242 1232 1303 1342 1212 1358 1125 1154 1319 1159 1302
    ## [99149] 1115 1314 1259 1335 1222 1204 1212 1234 1353 1342 1321 1335 1232 1214
    ## [99163] 1228 1221 1408 1331 1135 1140 1221 1359 1244 1159 1415 1357 1322 1237
    ## [99177] 1302 1326 1424 1414 1412 1239 1408 1225 1323 1248 1343 1237 1206 1231
    ## [99191] 1435 1325 1538 1421 1316 1443 1224 1430 1419 1347 1442 1415 1259 1352
    ## [99205] 1438 1332 1336 1509 1404 1347 1413 1253 1331 1423 1456 1402 1338 1327
    ## [99219] 1439 1517 1407 1406 1333 1514 1358 1254 1426 1344 1457 1347 1530 1455
    ## [99233] 1508 1432 1314 1432 1444 1512 1321 1318 1524 1334 1343 1437 1522 1459
    ## [99247] 1423 1442 1451 1408 1352 1424 1421 1358 1404 1347 1332 1352 1345 1442
    ## [99261] 1531 1408 1549 1459 1442 1343 1453 1453 1403 1423 1402 1352 1529 1405
    ## [99275] 1429 1424 1457 1525 1543 1457 1448 1506 1538 1510 1358 1633 1650 1634
    ## [99289] 1552 1547 1636 1836 1601 1648 1455 1638 1448 1500 1633 1541 1516 1546
    ## [99303] 1506 1529 1601 1454 1600 1543 1610 1437 1450 1535 1444 1525 1523 1644
    ## [99317] 1524 1638 1700 1631 1536 1453 1445 1547 1533 1650 1628 1515 1640 1648
    ## [99331] 1641 1656 1553 1507 1630 1709 1641 1633 1521 1714 1634 1702 1744 1605
    ## [99345] 1642 1516 1628 1603 1714 1752 1701 1531 1620 1517 1535 1638 1641 1630
    ## [99359] 1610 1558 1659 1608 1604 1734 1733 1641 1620 1745 1608 1643 1756 1654
    ## [99373] 1658 1655 1622 1821 1738 1640 1637 1653 1720 1722 1607 1756 1633 1744
    ## [99387] 1805 1710 1736 1650 1749 1646 1742 1749 1800 1729 1611 1806 1651 1744
    ## [99401] 1827 1756 1707 1632 1753 1946 1806 1718 1948 1755 1630 1659 1817 1705
    ## [99415] 1817 1709 1714 1713 1800 1712 1649 1858 1722 1803 1708 1716 1846 1728
    ## [99429] 1736 1624 1843 1734 1855 1907 1811 1859 1708 1647 1644 1824 1855 1816
    ## [99443] 1906 1752 1744 1808 1724 1905 1839 1824 1724 1717 1844 1900 1828 1804
    ## [99457] 1830 1801 1906 1741 1907 1753 1758 1718 1758 1839 1709 1748 2005 1759
    ## [99471] 1827 2001 1732 1912 1828 1844 1904 1917 1919 1858 1930 1826 1806 1807
    ## [99485] 1746 2016 1743 1950 2005 1947 2030 1859 1916 2121 1807 1915 1813 1933
    ## [99499] 1853 1804 1921 1858 1953 1831 1953 1855 1844 1935 1916 1747 1910 1800
    ## [99513] 1907 2015 1855 1856 1822 1955 1751 1951 1829 1818 1839 2023 1814 1843
    ## [99527] 1900 1909 1958 1836 1933 1940 1833 2006 2013 2013 1850 2019 2051 1858
    ## [99541] 2004 1820 1819 2017 1836 2028 1919 2049 1845 2006 2012 2009 2106 2000
    ## [99555] 1926 1853 2008 1833 2013 1910 2101 2041 1921 2056 2018 1914 1847 2053
    ## [99569] 2017 2001 2126 1923 2045 2128 1850 1902 2029 1854 2119 2017 1944 1948
    ## [99583] 2127 2118 1936 2044 2145 1957 2145 2117 2005 2144 2042 1940 2050 2157
    ## [99597] 1921 1909 2051 2031 1958 2126 2025 1949 1925 2048 2023 2140 2021 2130
    ## [99611] 2002 2032 2057 2001 1948 2056 1948 2010 2121 2033 2033 2034 2000 2201
    ## [99625] 2007 2025 2015 2139 2041 2103 2146 2022 2034 2111 2025 1945 2121 2202
    ## [99639] 1955 2126 2040 2021 2041 2239 2110 2127 2019 2226 2222 2237 2025 2106
    ## [99653] 2118 2044 2129 2036 2043 2228 2006 2138 2250 2049 2225 2242 2039 2034
    ## [99667] 2049 2226 2302 2108 2008 2112 2207 2028 2044 2200 2052 2205 2153 2138
    ## [99681] 2050 2151 2255 2246 2213 2049 2249 2229 2111 2211 2105 2152 2044 2215
    ## [99695] 2030 2151 2139   18 2212 2258 2235 2156 2232 2108 2056 2214 2150 2058
    ## [99709] 2140 2305 2234 2306 2250 2153 2106 2203 2318 2234 2213 2216 2104 2228
    ## [99723] 2224 2233 2247 2212 2110 2118 2144 2129 2237 2126 2246   11 2327 2151
    ## [99737] 2309 2154 2244 2358 2324 2153 2202 2244  133 2314 2322 2313    1 2239
    ## [99751] 2234 2341 2218 2308 2225 2303 2256 2159 2304 2334 2217 2233 2234 2204
    ## [99765] 2239 2302 2225  156   34 2236 2158 2243   11 2210 2351 2222 2359 2218
    ## [99779] 2350 2309 2349  153   30 2353 2225 2239 2349 2239  109    6 2358  100
    ## [99793]    9 2337 2339    5 2325   28 2353 2356   12   53 2358  138 2305 2330
    ## [99807] 2357   53 2353    5  111    8    4  133   23   14   12   34  249  158
    ## [99821]  406  441  506  453   NA   NA   NA  507  457  632  800  826 1013  816
    ## [99835]  924  833  642  800  740  830  651  753  820  900  901  843  725  824
    ## [99849] 1001  822  945  738  833  736  916 1037  808  729  846  724  858  758
    ## [99863]  825  817  824  735  911  857  924  747  930  745  754  806  805  916
    ## [99877]  830  739 1024  909  822  908  957  844  804  938  839  903 1025  938
    ## [99891]  901  854 1014 1017  930  745 1018  824  813  902  859  848 1038  820
    ## [99905]  954  929  917 1333  839  953 1055  948 1034  959  935  941  832 1021
    ## [99919]  916 1147  922  841  904 1048  910 1045  908 1023 1013  844  819  948
    ## [99933] 1029 1011 1203 1053 1016 1039  845 1046 1055 1019  958  905  952 1040
    ## [99947] 1110  955 1017 1039 1025  925 1005 1037  924 1225 1038  922 1046 1002
    ## [99961] 1102  943  953  931  926 1106  849  854 1106 1011 1053 1016  909 1245
    ## [99975]  923  916 1030 1044 1035 1057 1038 1051 1029 1143 1159 1249 1058 1044
    ## [99989] 1052  956 1109 1059  940 1104 1035 1133  920 1033 1117
    ##  [ reached getOption("max.print") -- omitted 236777 entries ]

``` r
### vuelos <- datos
### n <- da el número de posiciones de adelanto o atraso por defecto. 
### default <-El valor predeterminado es NA
```

### 6.Mira cada destino. ¿Puedes encontrar vuelos sospechosamente rápidos? (es decir, vuelos que representan un posible error de entrada de datos). Calcula el tiempo en el aire de un vuelo relativo al vuelo más corto a ese destino. ¿Cuáles vuelos se retrasaron más en el aire?

``` r
rapidez = flights %>%
  filter(air_time < 45) %>%
  arrange(desc(air_time)) %>% 
  head(10)
 
rapidez
```

    ## # A tibble: 10 x 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     1      559            559         0      702            706
    ##  2  2013     1     1     2240           2245        -5     2340           2356
    ##  3  2013     1     1     2312           2000       192       21           2110
    ##  4  2013     1     1     2323           2200        83       22           2313
    ##  5  2013     1     2     1504           1443        21     1607           1553
    ##  6  2013     1     2     1821           1714        67     1945           1824
    ##  7  2013     1     3     2033           2035        -2     2133           2154
    ##  8  2013     1     4      106           2245       141      201           2356
    ##  9  2013     1     4      648            645         3      801            757
    ## 10  2013     1     4      657            700        -3      812            809
    ## # ... with 11 more variables: arr_delay <dbl>, carrier <chr>, flight <int>,
    ## #   tailnum <chr>, origin <chr>, dest <chr>, air_time <dbl>, distance <dbl>,
    ## #   hour <dbl>, minute <dbl>, time_hour <dttm>

### 7.Encuentra todos los destinos que son volados por al menos dos operadores. Usa esta información para clasificar a las aerolíneas.

``` r
salio<-flights %>%
  select(carrier, dest) %>%
  count(dest, carrier) %>%
  group_by(dest) %>%
  filter(rank(desc(carrier)) > 2)
unique(salio$dest)
```

    ##  [1] "ATL" "AUS" "BNA" "BOS" "BTV" "BUF" "BWI" "CHS" "CLE" "CLT" "CMH" "CVG"
    ## [13] "DCA" "DEN" "DFW" "DTW" "FLL" "IAD" "IND" "JAX" "LAS" "LAX" "MCI" "MCO"
    ## [25] "MEM" "MIA" "MKE" "MSP" "MSY" "OMA" "ORD" "ORF" "PBI" "PDX" "PHL" "PHX"
    ## [37] "PIT" "PWM" "RDU" "ROC" "RSW" "SAN" "SAT" "SDF" "SEA" "SFO" "SJU" "SRQ"
    ## [49] "STL" "STT" "SYR" "TPA"

### 8.Para cada avión, cuenta el número de vuelos antes del primer retraso de más de 1 hora.

``` r
o<-flights%>%
  select(dep_delay, tailnum) %>%
  count(tailnum, dep_delay) %>%
  group_by(tailnum) %>%
  filter(dep_delay < 60) %>%
  summarise(sum(n))
```
