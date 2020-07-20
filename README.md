[![Build Status](https://travis-ci.org/hasacat/GlimmaV2.svg?branch=master)](https://travis-ci.org/hasacat/GlimmaV2)
# GlimmaV2
GlimmaV2 is an interactive R widget for creating plots for differential expression analysis, created using the [Vega](https://vega.github.io/vega/) and [htmlwidgets](https://www.htmlwidgets.org/) frameworks. New features include:
- multiple gene selections
- full integration with R markdown
- exporting plots to PNG/SVG/CSV formats

Feedback is welcome, please feel free to open an issue for any enhancements you would like to see in future.
### MA Plot
![MA plot](https://github.com/hasacat/GlimmaV2/blob/master/documentation/maplot.png "MA Plot")
### MDS Plot
![MDS plot](https://github.com/hasacat/GlimmaV2/blob/master/documentation/mds_plot.png "MDS Plot")
## Installation
You can install the development version of GlimmaV2 using devtools from the R command line.
```R
devtools::install_github("hasacat/GlimmaV2")
```
## Options
### MA & XY Plot Colouring
The default mapping between the status vector and color of the gene is given below:
```
-1 (downreg) => "dodgerblue"
0 (not DE) => "silver"
1 (upreg) => "firebrick"
```
Accordingly, the default status.colours argument is ```c("dodgerblue", "silver", "firebrick")```. If no status vector is provided, all genes are given a status value of 0. The colour mapping can be changed by varying the status.colours argument which must be a vector of three valid CSS strings (for example: ```#f304d3```, ```#fff```, ```rgb(253, 12, 134)```, ```steelblue```):
```R
glimmaMA(fit, counts=counts, groups=groups, status.colours=c("#3977db","#3d3f42","#db0d4e"))
```
```R
glimmaXY(x=fit$coef, y=fit$lod, status=dtFit, status.colours=c("cyan", "grey", "hotpink"))
```
### Sizing
The width and height parameters can be adjusted to change the dimensions of the widget in pixels in the RStudio viewer and in knitted HTML:
```
glimmaMA(fit, counts=counts, groups=groups, width=1200, height=1200)
```
glimmaMA, glimmaXY, and glimmaMDS each take the additional width/height arguments. The default width and height are both 920px; width and height should be scaled in a 1:1 ratio if preserving the original scale is desired.
