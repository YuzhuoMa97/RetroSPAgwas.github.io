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

WtGxE is an extension of the **SPAGxE** series (e.g., SPAGxE, SPAGxEmix+) and the broader retrospective analysis framework with saddlepoint approximation. It integrates **external allele frequency information** to enhance the statistical power of genome-wide gene-environment interaction (G×E) studies, while maintaining fast computation and accurate type I error control.  


## Introduction to WtGxE  

G×E studies aim to identify genetic variants that interact with environmental factors to influence complex traits (e.g., diseases). However, limited statistical power (due to small effect sizes, rare variants, or imbalanced trait distributions) and challenges in handling extreme phenotypes hinder discovery.  

WtGxE addresses these limitations by building on the retrospective analysis framework and saddlepoint approximation (SPA):  
- It leverages **publicly available external allele frequency data** (e.g., from reference panels like 1000 Genomes) to refine variant-specific weights, boosting the detection of G×E associations.  
- It retains the “fast and accurate” advantages of SPA, enabling scalable analysis of genome-wide data without sacrificing type I error control.  


## Core Methodological Ideas  

WtGxE extends the SPAGxE pipeline with three key innovations:  

1. **Integration of External Allele Frequency**  
   External allele frequency (from reference populations) is incorporated to adjust variant-specific weights. This improves the characterization of genetic effects, especially for rare variants or populations with unique allele frequency profiles.  

2. **Retrospective Analysis Framework**  
   Following SPAGxE, WtGxE uses a retrospective likelihood-based approach to model G×E associations. This framework efficiently handles large-scale genomic data and complex trait distributions (e.g., binary, continuous, or time-to-event traits).  

3. **Saddlepoint Approximation (SPA)**  
   SPA is applied to compute accurate p-values for G×E tests, even under extreme phenotypic distributions (e.g., highly skewed binary traits or small sample sizes). This ensures valid type I error control while maintaining computational efficiency.  


## Main Features of WtGxE  

- **Enhanced Power**: By integrating external allele frequency, WtGxE boosts power to detect G×E associations, particularly for rare variants or underpowered studies.  
- **Fast & Accurate**: Leverages the retrospective framework and SPA for scalable, high-speed analysis with precise type I error control.  
- **Flexible & Robust**: Compatible with diverse trait types (binary, continuous, survival) and study designs (case-control, cohort, family-based).  
- **User-Friendly**: Implemented in efficient, easy-to-use code (with clear documentation and tutorials).  


## Citation  

If you use WtGxE, please cite:  

> **Ma, Y.**, [Co-authors], *WtGxE: efficiently leveraging external allele frequency to boost powers of genome-wide gene-environmental interaction studies*.  
> **Manuscript in preparation (to be submitted)**.  

*Note*: Yu-Zhuo Ma is the **first author** of this work. Please acknowledge this contribution when using or extending WtGxE.  


## License & Copyright  

All code and materials in this repository are © [Your Name/Institution]. All rights reserved.  

WtGxE is licensed under the [MIT License](LICENSE) (or your preferred license). Redistribution and use (with or without modification) are permitted, provided the copyright notice and this permission notice are included.  

For permissions beyond the scope of this license, please contact [Your Email].  


## Contact  

For questions, collaborations, or feedback, please:  
- Open an issue in this repository.  
- Email [Your Email] (e.g., yuzhuoma97@github.io).
