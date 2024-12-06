---
layout: default
title: Home
nav_order: 1
description: "Main page for GRAB package."
permalink: /
---

# Main features of GRAB package

The ```GRAB``` is an R package for Genome-wide Robust Analysis designed for Biobank data **(GRAB)**. 
The main features of the package are as below. 

- Support multiple complex traits including 
  - quantitative trait
  - binary trait 
  - time-to-event trait 
  - ordinal categorical trait
  - longitudinal trait
- Perform single-variant and set-based association tests 
- Account for sample relatedness using Genetic Relationship Matrix **(GRM)**
- Calibrate p-values using normal distribution approximation and Saddlepoint approximation **(SPA)** 
  - are computationally efficient for large data sets (e.g. UK Biobank)
  - can handle unbalanced phenotypic distribution (e.g. case-control imbalance of binary traits)
  - are robust for both common variants and rare variants

For set-based association tests, ```GRAB``` package
- performs Burden test, SKAT, and SKAT-O 
- allows for tests on multiple minor allele frequency cutoffs and functional annotations
- allows for specifying weights for single variants in the set-based tests
- performs conditional analysis to identify associations independent from nearly GWAS signals


## Supported Approaches

### POLMM / POLMM-GENE:
- Support ordinal categorical trait
- Single-variant / set-based tests
- Can account for sample relatedness
- Reference
  - Bi, Wenjian, Wei Zhou, Rounak Dey, Bhramar Mukherjee, Joshua N. Sampson, and Seunggeun Lee. **Efficient mixed model approach for large-scale genome-wide association studies of ordinal categorical phenotypes.** *The American Journal of Human Genetics* 108, no. 5 (2021): 825-839.
  - Bi, Wenjian, Wei Zhou, Peipei Zhang, Yaoyao Sun, Weihua Yue, and Seunggeun Lee. **Scalable mixed model approaches for set-based association studies on large-scale categorical data analysis and its application to 450k exome sequencing data in UK Biobank.** *The American Journal of Human Genetics* 110, no. 5 (2023): 762-773.

### SPACox:
- Support (but not limited to) time-to-event trait
- Support model residuals (whose sum is zero) after fitting a null model to any type of trait 
- Single-variant tests
- Cannot account for sample relatedness
- Reference
  - Bi, Wenjian, Lars G. Fritsche, Bhramar Mukherjee, Sehee Kim, and Seunggeun Lee. **A fast and accurate method for genome-wide time-to-event data analysis and its application to UK Biobank.** *The American Journal of Human Genetics* 107, no. 2 (2020): 222-233.

### SPAmix:
- Support (but not limited to) time-to-event trait
- Support model residuals (whose sum is zero) after fitting a null model to any type of trait 
- Can support admixture population or multiple populations
- Single-variant tests
- Cannot account for sample relatedness
- Reference (to be submitted)

### SPAGRM:
- Support (but not limited to) time-to-event trait
- Support model residuals (whose sum is zero) after fitting a null model to any type of trait 
- Single-variant tests
- Can account for sample relatedness
- Reference (to be submitted)

### SAIGE / SAIGE-GENE+ (supported later, please refer to SAIGE package):
- Support quantitative and binary trait
- Single-variant / set-based tests
- Can account for sample relatedness
- Reference
  - Zhou, Wei, Jonas B. Nielsen, Lars G. Fritsche, Rounak Dey, Maiken E. Gabrielsen, Brooke N. Wolford, Jonathon LeFaive et al. **Efficiently controlling for case-control imbalance and sample relatedness in large-scale genetic association studies.** *Nature genetics* 50, no. 9 (2018): 1335-1341.
  - Zhou, Wei, Zhangchen Zhao, Jonas B. Nielsen, Lars G. Fritsche, Jonathon LeFaive, Sarah A. Gagliano Taliun, Wenjian Bi et al. **Scalable generalized linear mixed model for region-based association tests in large biobanks and cohorts.** *Nature genetics* 52, no. 6 (2020): 634-639.
  - Zhou, Wei, Wenjian Bi, Zhangchen Zhao, Kushal K. Dey, Karthik A. Jagadeesh, Konrad J. Karczewski, Mark J. Daly, Benjamin M. Neale, and Seunggeun Lee. **SAIGE-GENE+ improves the efficiency and accuracy of set-based rare variant association tests** *Nature genetics* 54, no. 10 (2022): 1466-1469.

## License
```GRAB``` is distributed under an GPL license.

## Contact
If you have any questions about ```GRAB``` package, please contact **wenjianb@pku.edu.cn**
