---
layout: default
title: Installation
nav_order: 3
description: "Just the Docs is a responsive Jekyll theme with built-in search that is easily customizable and hosted on GitHub Pages."
has_children: false
has_toc: false
---

The ```GRAB``` package can be installed in R or via docker. 

## Install GRAB package via docker

UK Biobank Research Analysis Platform (RAP) supports docker installation. For more details about the ```GRAB``` package build, installation, and usage, please check the section ```UK Biobank RAP```. 

## Install GRAB package in R (current version: 0.0.3.9)

### In **Linux** operation system

```
library(remotes)  
install_github("GeneticAnalysisinBiobanks/GRAB")  
library(GRAB)
```

### In **Windows** operation system

```
library(remotes)
# options(download.file.method = "wininet")
install_github("GeneticAnalysisinBiobanks/GRAB", INSTALL_opts=c("--no-multiarch"))  # The INSTALL_opts sometimes is required in Windows OS.
library(GRAB)
```

We note that package installation in **Windows** system is not as stable as in **Linux** system. Possible errors could be due to package dependency, network issue, et al.

### The **Linux** environment of the maintainer

```
> sessionInfo()
R version 4.0.5 (2021-03-31)
Platform: x86_64-conda-linux-gnu (64-bit)
Running under: CentOS Linux 7 (Core)

Matrix products: default
BLAS/LAPACK: /gdata01/user/wenjianb/software/miniconda3/envs/myEnvR4.0/lib/libopenblasp-r0.3.21.so

locale:
 [1] LC_CTYPE=en_US.UTF-8       LC_NUMERIC=C
 [3] LC_TIME=en_US.UTF-8        LC_COLLATE=en_US.UTF-8
 [5] LC_MONETARY=en_US.UTF-8    LC_MESSAGES=en_US.UTF-8
 [7] LC_PAPER=en_US.UTF-8       LC_NAME=C
 [9] LC_ADDRESS=C               LC_TELEPHONE=C
[11] LC_MEASUREMENT=en_US.UTF-8 LC_IDENTIFICATION=C

attached base packages:
[1] stats     graphics  grDevices utils     datasets  methods   base

other attached packages:
 [1] GRAB_0.1       Rcpp_1.0.10        igraph_1.4.3       dbplyr_2.3.2
 [5] dplyr_1.1.2        tidyr_1.3.0        SKAT_2.2.5         RSpectra_0.16-1
 [9] SPAtest_3.1.2      Matrix_1.5-3       ordinal_2022.11-16 survival_3.4-0
[13] remotes_2.4.2

loaded via a namespace (and not attached):
 [1] compiler_4.0.5      pillar_1.9.0        prettyunits_1.1.1
 [4] tools_4.0.5         pkgbuild_1.3.1      lifecycle_1.0.3
 [7] tibble_3.2.1        nlme_3.1-159        lattice_0.20-45
[10] ucminf_1.2.0        pkgconfig_2.0.3     rlang_1.1.1
[13] DBI_1.1.3           cli_3.6.1           curl_5.0.0
[16] withr_2.5.0         generics_0.1.3      vctrs_0.6.2
[19] rprojroot_2.0.3     grid_4.0.5          tidyselect_1.2.0
[22] glue_1.6.2          R6_2.5.1            processx_3.8.1
[25] fansi_1.0.4         callr_3.7.3         purrr_1.0.1
[28] magrittr_2.0.3      ps_1.7.5            MASS_7.3-58.1
[31] splines_4.0.5       numDeriv_2016.8-1.1 utf8_1.2.3
[34] RcppParallel_5.1.7  crayon_1.5.2
```

### The **Windows** environment of the maintainer

```
> sessionInfo()
R version 4.1.0 (2021-05-18)
Platform: x86_64-w64-mingw32/x64 (64-bit)
Running under: Windows 10 x64 (build 19045)

Matrix products: default

locale:
[1] LC_COLLATE=English_United States.1252 
[2] LC_CTYPE=English_United States.1252   
[3] LC_MONETARY=English_United States.1252
[4] LC_NUMERIC=C                          
[5] LC_TIME=English_United States.1252    
system code page: 936

attached base packages:
[1] stats     graphics  grDevices utils     datasets  methods  
[7] base     

other attached packages:
 [1] GRAB_0.1       Rcpp_1.0.10        igraph_1.2.6      
 [4] dbplyr_2.3.2       dplyr_1.1.2        tidyr_1.3.0       
 [7] SKAT_2.2.5         RSpectra_0.16-1    SPAtest_3.1.2     
[10] Matrix_1.3-3       ordinal_2022.11-16 survival_3.2-11   
[13] remotes_2.4.2     

loaded via a namespace (and not attached):
 [1] compiler_4.1.0      pillar_1.9.0        prettyunits_1.1.1  
 [4] tools_4.1.0         pkgbuild_1.2.0      lifecycle_1.0.3    
 [7] tibble_3.2.1        nlme_3.1-152        lattice_0.20-44    
[10] ucminf_1.2.0        pkgconfig_2.0.3     rlang_1.1.1        
[13] DBI_1.1.3           cli_3.6.1           rstudioapi_0.13    
[16] curl_4.3.2          withr_2.5.0         generics_0.1.3     
[19] vctrs_0.6.2         rprojroot_2.0.2     grid_4.1.0         
[22] tidyselect_1.2.0    glue_1.6.2          data.table_1.14.2  
[25] R6_2.5.1            processx_3.5.2      fansi_1.0.4        
[28] purrr_1.0.1         callr_3.7.0         magrittr_2.0.3     
[31] ps_1.6.0            MASS_7.3-54         splines_4.1.0      
[34] numDeriv_2016.8-1.1 utf8_1.2.3          RcppParallel_5.1.7 
[37] crayon_1.5.1  
```
