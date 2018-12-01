---
title: "ZED Raport z analizy danych"
author: "Marcin Burczyk"
output: 
  html_document:
    keep_md: yes
    toc: yes
date: '01 grudzień 2018'
---



##Podsumowanie analizy


#Wykorzystane biblioteki

```r
library(dplyr)
library(ggplot2)
```


##Dane


```r
set.seed(123)
```


```r
all_data <- read.csv2("all_summary.csv", nrows = 1000, header = TRUE, stringsAsFactors = FALSE)
```


```r
cleaned_data <- all_data %>% filter(!res_name %in% c('UNK', 'UNX', 'UNL', 'DUM', 'N', 'BLOB', 'ALA', 'ARG', 'ASN', 'ASP', 'CYS', 'GLN', 'GLU', 'GLY', 'HIS', 'ILE', 'LEU', 'LYS', 'MET', 'MSE', 'PHE', 'PRO', 'SEC', 'SER', 'THR', 'TRP', 'TYR', 'VAL', 'DA', 'DG', 'DT', 'DC', 'DU', 'A', 'G', 'T', 'C', 'U', 'HOH', 'H20', 'WAT')) 
```


Zebrane dane zawierają 412 kolumn oraz 1000 wierszy.


```r
top_50_res_name <- cleaned_data %>% 
  select(res_name) %>% 
  group_by(res_name) %>% 
  count() %>% 
  arrange(desc(n)) %>%
  head(50)

top_50_res_name
```

```
## # A tibble: 50 x 2
## # Groups:   res_name [50]
##    res_name     n
##    <chr>    <int>
##  1 SO4        116
##  2 HEM         95
##  3 GOL         64
##  4 NAG         54
##  5 ZN          40
##  6 MLY         32
##  7 MG          30
##  8 CD          25
##  9 K           24
## 10 CA          21
## # ... with 40 more rows
```

```r
data_with_most_common_res_names <- cleaned_data %>% filter(res_name %in% top_50_res_name$res_name)
dim(data_with_most_common_res_names)
```

```
## [1] 820 412
```




