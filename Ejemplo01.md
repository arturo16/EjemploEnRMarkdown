Title: "Primer reporte en R Markdown"
Author: "José Arturo Reséndiz Lira"
output: html_document
========================================================


```r
library(ggmap)
```

```
## Warning: package 'ggmap' was built under R version 3.1.2
```

```
## Loading required package: ggplot2
```

```
## Warning: package 'ggplot2' was built under R version 3.1.2
```


```r
clave.unica <- rep("000136989",3)
es.mixto <- c(universidad = 1, preparatoria = 1, secundaria = 1)
universidad <- geocode("ITAM")
preparatoria <- geocode("Escuela Cristobal Colon")
secundaria <- geocode("Instituto Ovalle Monday")

educacion <- rbind(universidad, preparatoria, secundaria)
educacion <- cbind(clave.unica, es.mixto, educacion)
```


```r
limites <- make_bbox(lon, lat, educacion, f = 0.7)
mapa <- get_map(location = limites, 
                maptype = "roadmap", 
                source = "google")
```

![plot of chunk GraficarLocalizaciones](figure/GraficarLocalizaciones-1.png) 
