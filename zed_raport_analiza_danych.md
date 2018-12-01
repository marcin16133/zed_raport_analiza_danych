---
title: "ZED Raport z analizy danych"
author: "Marcin Burczyk"
output: 
  html_document:
    keep_md: yes
    toc: yes
    toc_float: yes
date: '01 grudzień 2018'
---




```r
library(dplyr)
library(ggplot2)
```



```r
set.seed(123)
```

## Dane

```r
all_data <- read.csv2("all_summary.csv", nrows = 1000, header = TRUE, stringsAsFactors = FALSE)
```



