---
layout: default
title: WtGxE
nav_order: 7
description: "Efficiently leveraging external allele frequency to boost powers of genome-wide gene-environmental interaction studies."
parent: Genome-wide gene-environment interaction (GxE) studies
has_children: false
has_toc: false
---

<head>
    <script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
    <script type="text/x-mathjax-config">
        MathJax.Hub.Config({
            tex2jax: {
            skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'],
            inlineMath: [['$','$']]
            }
        });
    </script>
</head>

# WtGxE  

WtGxE is an extension of the **SPAGxE** family (including SPAGxE, SPAGxE+, SPAGxEmix+, etc.) and builds upon the **retrospective analysis framework combined with saddlepoint approximation (SPA)** originally proposed by Yuzhuo Ma in his [master’s thesis (2022)](https://kns.cnki.net/kcms2/article/abstract?v=jkwd3qsBIEKwkKkgMuimTLSEojAEBaWSJzCAd3uOCepX09aaYi1Vhn87HddxnsydAW9MGQHzgdF9Nw93IZ_DZCdJbGAX3C13DfGxpW58VBV273z1eVlg75Je1akPxIDc5iiSpz46iutS1tt9m3MJRg==&uniplatform=NZKPT&language=CHS) (**DOI:10.27272/d.cnki.gshdu.2022.002946**) and later formalized in the SPAGxE paper ([Ma et al., *Nature Communications*, 2025](https://doi.org/10.1038/s41467-025-57887-3)).  

While SPAGxE methods successfully apply the retrospective–SPA framework [(Ma, 2022)](https://kns.cnki.net/kcms2/article/abstract?v=jkwd3qsBIEKwkKkgMuimTLSEojAEBaWSJzCAd3uOCepX09aaYi1Vhn87HddxnsydAW9MGQHzgdF9Nw93IZ_DZCdJbGAX3C13DfGxpW58VBV273z1eVlg75Je1akPxIDc5iiSpz46iutS1tt9m3MJRg==&uniplatform=NZKPT&language=CHS), **DOI:10.27272/d.cnki.gshdu.2022.002946**) to genome-wide gene–environment interaction (G×E) studies, WtGxE goes a step further by **integrating external allele frequency (AF) information** from public resources (e.g., 1000 Genomes, gnomAD) to substantially boost statistical power, while preserving the fast computation and accurate type I error control inherent to the original framework.

---

## Introduction to WtGxE  

G×E studies aim to identify genetic variants whose effects on complex traits are modified by environmental factors. However, statistical power is often limited due to small effect sizes, rare variants, imbalanced phenotypic distributions, and case–control ascertainment.  

The retrospective analysis framework treats genotype as random and conditions on phenotype and covariates, making it robust to model misspecification and naturally applicable to diverse traits. Combined with **saddlepoint approximation (SPA)**, it provides accurate p-values even under extreme phenotypic distributions.  

**WtGxE** inherits these advantages and enhances them by:  
- Incorporating **externally estimated allele frequencies** to improve the precision of score statistics, thereby increasing power to detect G×E associations.  
- Retaining the computational scalability of the retrospective–SPA framework ([Ma, 2022](https://kns.cnki.net/kcms2/article/abstract?v=jkwd3qsBIEKwkKkgMuimTLSEojAEBaWSJzCAd3uOCepX09aaYi1Vhn87HddxnsydAW9MGQHzgdF9Nw93IZ_DZCdJbGAX3C13DfGxpW58VBV273z1eVlg75Je1akPxIDc5iiSpz46iutS1tt9m3MJRg==&uniplatform=NZKPT&language=CHS)), enabling genome-wide analysis of large biobank-scale cohorts.

---

## Core Methodological Ideas  

WtGxE extends the SPAGxE pipeline with the following innovations:

1. **Integration of External Allele Frequency**  
   Publicly available AF estimates (e.g., from gnomAD, UK10K, or other large reference panels) are used to refine the variant-specific weights in the score test. This is especially beneficial for rare variants or when the study cohort has a limited sample size.

2. **Retrospective Analysis Framework**  
   Following the original framework of retrospective–SPA ([Ma, 2022](https://kns.cnki.net/kcms2/article/abstract?v=jkwd3qsBIEKwkKkgMuimTLSEojAEBaWSJzCAd3uOCepX09aaYi1Vhn87HddxnsydAW9MGQHzgdF9Nw93IZ_DZCdJbGAX3C13DfGxpW58VBV273z1eVlg75Je1akPxIDc5iiSpz46iutS1tt9m3MJRg==&uniplatform=NZKPT&language=CHS)) and SPAGxE ([Ma et al., 2025](https://doi.org/10.1038/s41467-025-57887-3)), WtGxE models the genotype distribution conditional on phenotype, environment, and covariates. This retrospective perspective avoids fitting a full model for each variant and enables straightforward handling of complex trait types.

3. **Saddlepoint Approximation (SPA)**  
   SPA is employed to accurately approximate the null distribution of the test statistic, ensuring valid type I error control even for low-frequency variants and unbalanced case–control ratios.

---

## Main Features of WtGxE  

- **Enhanced Power**: By leveraging external AF, WtGxE achieves substantial power gains over existing G×E methods.  
- **Fast & Accurate**: Inherits the computational efficiency of the retrospective–SPA framework ([Yuzhuo Ma, 2022](https://kns.cnki.net/kcms2/article/abstract?v=jkwd3qsBIEKwkKkgMuimTLSEojAEBaWSJzCAd3uOCepX09aaYi1Vhn87HddxnsydAW9MGQHzgdF9Nw93IZ_DZCdJbGAX3C13DfGxpW58VBV273z1eVlg75Je1akPxIDc5iiSpz46iutS1tt9m3MJRg==&uniplatform=NZKPT&language=CHS)), requiring only a single null model fit and a lightweight score test for each variant.  
- **Flexible & Robust**: Applicable to binary with imbalanced case–control ratios and adjusting for sample relatedness.  
- **User-Friendly**: Implemented in efficient, well-documented code (available in this repository).

---

## Citation  

If you use WtGxE, please cite the following references:

- **WtGxE (this work):**  
  **Ma, Y. et al.**, *WtGxE: efficiently leveraging external allele frequency to boost powers of genome-wide gene-environmental interaction studies*.  
  **Manuscript in preparation (to be submitted).**  


- **SPAGxE (foundational framework):**  
  Ma, Y., Zhao, Y., Zhang, J.-F., & Bi, W. (2025). Efficient and accurate framework for genome-wide gene-environment interaction analysis in large-scale biobanks. *Nature Communications*, 16, 3064.  
  [DOI: 10.1038/s41467-025-57887-3](https://doi.org/10.1038/s41467-025-57887-3)

- **WtCoxG (related method using external AF for time-to-event GWAS):**  
  Li, Y., Ma, Y., Xu, H., et al. (2025). Applying weighted Cox regression to genome-wide association studies of time-to-event phenotypes. *Nature Computational Science*, 5, 1064–1079.  
  [DOI: 10.1038/s43588-025-00864-z](https://doi.org/10.1038/s43588-025-00864-z)

---

## License & Copyright  

All code, documentation, and materials related to **SPAGxE** (including SPAGxE, SPAGxE+, SPAGxEmix+, etc.) and **WtGxE** are **Copyright © 2025 Yuzhuo Ma and collaborators**. All rights reserved.  

**Neither SPAGxE nor WtGxE, nor any part of their implementations, may be used, copied, modified, or distributed without explicit written permission from the first author (Yuzhuo Ma).**  

If you wish to use SPAGxE or WtGxE in your research, collaborate, or extend the methods, please contact:  
- **Email:** yuzhuoma@amss.ac.cn  
- Or open an issue in this repository to initiate a discussion.  

Unauthorized use or pre‑publication disclosure without proper attribution may violate academic norms and intellectual property rights.  

*Note: All future use of both SPAGxE and WtGxE is governed by this more restrictive policy to protect the original intellectual contributions of the first author.*

---

## Contact  

For questions, collaborations, or feedback:  
- Open an issue in this repository.  
- Email: yuzhuoma@amss.ac.cn
