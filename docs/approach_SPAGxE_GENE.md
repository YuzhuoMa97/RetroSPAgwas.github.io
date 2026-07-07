---
layout: default
title: SPAGxE‑GENE
nav_order: 8
description: "Extending the retrospective SPA G×E framework to gene‑based set tests for rare‑variant gene‑environment interaction analysis."
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

# SPAGxE‑GENE  

SPAGxE‑GENE is an extension of the **SPAGxE** family (including SPAGxE, SPAGxE+, SPAGxEmix+, etc.) that moves from single‑variant G×E tests to **gene‑based (set‑based) G×E association tests**. It builds on the **retrospective analysis framework combined with saddlepoint approximation (SPA)** originally proposed by Yuzhuo Ma in his [master’s thesis (2022)](https://kns.cnki.net/kcms2/article/abstract?v=jkwd3qsBIEKwkKkgMuimTLSEojAEBaWSJzCAd3uOCepX09aaYi1Vhn87HddxnsydAW9MGQHzgdF9Nw93IZ_DZCdJbGAX3C13DfGxpW58VBV273z1eVlg75Je1akPxIDc5iiSpz46iutS1tt9m3MJRg==&uniplatform=NZKPT&language=CHS) (**DOI:10.27272/d.cnki.gshdu.2022.002946**) and later formalized in the SPAGxE paper ([Ma et al., *Nature Communications*, 2025](https://doi.org/10.1038/s41467-025-57887-3)).  

While SPAGxE methods successfully apply the retrospective–SPA framework to single‑variant G×E analysis, SPAGxE‑GENE aggregates multiple rare variants within a gene (or a predefined region) to test for joint G×E effects. This approach mirrors the rationale of classic gene‑based tests (e.g., SKAT, SKAT‑O, Burden tests) used in main‑effect rare‑variant association studies, but adapted to the G×E context with rigorous type I error control via SPA.

---

## Introduction to SPAGxE‑GENE  

Gene‑environment interaction (G×E) studies typically examine one variant at a time. However, many complex traits are influenced by multiple rare variants within the same gene, and single‑variant tests may lack power due to low minor allele counts. **Gene‑based (set‑based) tests** aggregate information across a set of variants (e.g., all coding variants in a gene) to increase power, especially for rare variants.  

SPAGxE‑GENE brings this paradigm to G×E analysis by:  
- Aggregating variant‑level G×E test statistics (or scores) across a predefined variant set using **Burden, SKAT, or SKAT‑O** meta‑tests.  
- Applying the **retrospective SPA framework** ([Ma, 2022](https://kns.cnki.net/kcms2/article/abstract?v=jkwd3qsBIEKwkKkgMuimTLSEojAEBaWSJzCAd3uOCepX09aaYi1Vhn87HddxnsydAW9MGQHzgdF9Nw93IZ_DZCdJbGAX3C13DfGxpW58VBV273z1eVlg75Je1akPxIDc5iiSpz46iutS1tt9m3MJRg==&uniplatform=NZKPT&language=CHS)) to ensure accurate p‑values even under extreme phenotypic distributions (e.g., highly unbalanced case‑control ratios).  
- Handling **multiple MAF cutoffs** and **functional annotations** (e.g., LoF, missense, synonymous) to flexibly define variant sets, as advocated by recent large‑scale set‑based methods (e.g., SAIGE‑GENE+).

---

## Core Methodological Ideas  

SPAGxE‑GENE extends the SPAGxE pipeline with the following innovations:

1. **Set‑Based Aggregation for G×E**  
   Instead of testing each variant individually, SPAGxE‑GENE combines G×E score statistics across all variants in a set using weighted linear combinations (Burden) or variance‑component tests (SKAT/SKAT‑O). This captures both directional and heterogeneous effects.

2. **Retrospective Analysis Framework**  
   Following the original framework of retrospective–SPA ([Ma, 2022](https://kns.cnki.net/kcms2/article/abstract?v=jkwd3qsBIEKwkKkgMuimTLSEojAEBaWSJzCAd3uOCepX09aaYi1Vhn87HddxnsydAW9MGQHzgdF9Nw93IZ_DZCdJbGAX3C13DfGxpW58VBV273z1eVlg75Je1akPxIDc5iiSpz46iutS1tt9m3MJRg==&uniplatform=NZKPT&language=CHS)) and SPAGxE ([Ma et al., 2025](https://doi.org/10.1038/s41467-025-57887-3)), SPAGxE‑GENE derives the joint score statistic for the set conditional on phenotype, environment, and covariates. This avoids fitting a full model per variant and naturally accommodates binary, time‑to‑event, and quantitative traits.

3. **Saddlepoint Approximation (SPA) for Set Tests**  
   SPA is applied to calibrate the p‑value of the set‑based test statistic, providing accurate tail probabilities even when the set contains very rare variants (e.g., MAF ≤ 0.1% or ≤ 0.01%). This ensures valid type I error control comparable to state‑of‑the‑art methods like SAIGE‑GENE+.

4. **Multi‑Cutoff & Multi‑Annotation Strategy**  
   Users can specify multiple maximum MAF thresholds (e.g., 1%, 0.1%, 0.01%) and multiple functional annotation categories (e.g., LoF only, LoF+missense, LoF+missense+synonymous). Results from different configurations are combined via Cauchy combination or minimum P‑value with Bonferroni correction.

---

## Main Features of SPAGxE‑GENE  

- **Enhanced Power for Rare Variant G×E**: Aggregating rare variants within a gene boosts detection of G×E associations that would be missed by single‑variant tests.  
- **Accurate Type I Error Control**: SPA ensures correct calibration even for extremely unbalanced phenotypes and very low MAF thresholds.  
- **Flexible Set Definition**: Supports user‑defined variant sets (genes, regions, pathways) with customizable MAF cutoffs and functional annotations.  
- **Computationally Efficient**: Only one null model fit is required; set‑based tests are computed quickly using pre‑computed score statistics.  
- **Unified with SPAGxE Family**: Shares the same underlying framework, making it easy to apply alongside single‑variant G×E analyses.

---

## Citation  

If you use SPAGxE‑GENE, please cite the following references:

- **SPAGxE‑GENE (this work):**  
  **Ma, Y. et al.**, *SPAGxE‑GENE: extending the retrospective SPA G×E framework to gene‑based set tests for rare‑variant gene‑environment interaction analysis*.  
  **Manuscript in preparation (to be submitted).**  

- **SPAGxE (foundational framework):**  
  Ma, Y., Zhao, Y., Zhang, J.-F., & Bi, W. (2025). Efficient and accurate framework for genome-wide gene-environment interaction analysis in large-scale biobanks. *Nature Communications*, 16, 3064.  
  [DOI: 10.1038/s41467-025-57887-3](https://doi.org/10.1038/s41467-025-57887-3)

- **WtGxE (related weighted G×E method):**  
  Ma, Y. et al., *WtGxE: efficiently leveraging external allele frequency to boost powers of genome-wide gene-environmental interaction studies*. Manuscript in preparation.

---

## License & Copyright  

All code, documentation, and materials related to **SPAGxE** (including SPAGxE, SPAGxE+, SPAGxEmix+, etc.), **WtGxE**, and **SPAGxE‑GENE** are **Copyright © 2025 Yuzhuo Ma and collaborators**. All rights reserved.  

**Neither SPAGxE, WtGxE, nor SPAGxE‑GENE, nor any part of their implementations, may be used, copied, modified, or distributed without explicit written permission from the first author (Yuzhuo Ma).**  

If you wish to use SPAGxE, WtGxE, or SPAGxE‑GENE in your research, collaborate, or extend the methods, please contact:  
- **Email:** yuzhuoma@amss.ac.cn  
- Or open an issue in this repository to initiate a discussion.  

Unauthorized use or pre‑publication disclosure without proper attribution may violate academic norms and intellectual property rights.  

*Note: All future use of these methods is governed by this more restrictive policy to protect the original intellectual contributions of the first author.*

---

## Contact  

For questions, collaborations, or feedback:  
- Open an issue in this repository.  
- Email: yuzhuoma@amss.ac.cn
