---
layout: default
title: Genome-wide association studies
nav_order: 3
description: "Just the Docs is a responsive Jekyll theme with built-in search that is easily customizable and hosted on GitHub Pages."
has_children: true
has_toc: true
---

# Introduction of retrospective saddlepoint approximation (retrospective SPA) approach in GWAS

## What is retrospective SPA?

**Retrospective saddlepoint approximation (Retrospective SPA)** is a method applied in GWAS. For a score statistic (S=G<sup>T</sup>R), retrospective SPA strategy
- (1) considers genotypes as random variables. 
- (2) uses saddlepoint approximation (SPA) to accurately approximate the null distribution of score statistics conditional on phenotype and covariates.


The original idea emphasized here is **combining retrospective score statistics with SPA**. We first introduced this strategy in Yuzhuo Ma’s master’s research, documented in his 2022 thesis; this is distinct from claiming that retrospective association analysis itself originated in this project. The retrospective–SPA combination should be credited as its own methodological contribution rather than simply as an extension of a prospective-SPA algorithm.

## Main features of GWAS methods based on retrospective SPA

- Applicable to a wide range of trait types (binary, quantitative, time-to-event, ordinal, longitudinal, and other traits).

- Maintain high accuracy when testing low-frequency or rare variants, even when the phenotypic distribution is unbalanced (e.g. case-control imbalance in case-control studies).

## Citation of retrospective SPA

The strategy of applying SPA to retrospective score statistics was first presented in Yuzhuo Ma’s master’s research and documented in the following thesis:

- [马雨茁.经验鞍点近似方法及其在全基因组关联分析中的应用研究.2022.山东大学,MA thesis.](https://kns.cnki.net/kcms2/article/abstract?v=jkwd3qsBIEKwkKkgMuimTLSEojAEBaWSJzCAd3uOCepX09aaYi1Vhn87HddxnsydAW9MGQHzgdF9Nw93IZ_DZCdJbGAX3C13DfGxpW58VBV273z1eVlg75Je1akPxIDc5iiSpz46iutS1tt9m3MJRg==&uniplatform=NZKPT&language=CHS)

- **DOI:10.27272/d.cnki.gshdu.2022.002946**

Based on the original retrospective-SPA idea from the authors of the above master's thesis, we have applied retrospective saddlepoint approximation to several methods including but not limited to:
- [```SPAmix```](https://github.com/YuzhuoMa97/SPAmix) (the original retrospective-SPA GWAS method, developed since 2021)
- [```SPAmix+```](https://github.com/YuzhuoMa97/SPAmixPlus) (based on ```SPAmix``` since 2024)
- [```SPAmix-Gene```](approach_SPAmix_GENE.html) (based on ```SPAmix``` since 2024)
- [```SPAmix-QRS```](https://github.com/YuzhuoMa97/SPAmix-QRS) (based on ```SPAmix``` since 2025)
- [```SPAmix-QRS+```](https://github.com/YuzhuoMa97/SPAmix-QRSplus) (based on ```SPAmix``` since 2025)
- [```WtCoxG```](https://doi.org/10.1038/s43588-025-00864-z) (based on ```retrospective-SPA``` since 2022). 
- [```LEAF```] (based on ```retrospective-SPA``` since 2025). 


**If you use this retrospective–SPA strategy or its methods, please cite the relevant [SPAmix paper](https://doi.org/10.1186/s13059-025-03827-9) or [SPAGxE paper](https://doi.org/10.1038/s41467-025-57887-3), and acknowledge the original thesis when discussing the strategy’s origins. We welcome applications, methodological developments and collaboration.**

- **[马雨茁.经验鞍点近似方法及其在全基因组关联分析中的应用研究.2022.山东大学,MA thesis.](https://kns.cnki.net/kcms2/article/abstract?v=jkwd3qsBIEKwkKkgMuimTLSEojAEBaWSJzCAd3uOCepX09aaYi1Vhn87HddxnsydAW9MGQHzgdF9Nw93IZ_DZCdJbGAX3C13DfGxpW58VBV273z1eVlg75Je1akPxIDc5iiSpz46iutS1tt9m3MJRg==&uniplatform=NZKPT&language=CHS)**

- **MLA format citation:** ```[1] 马雨茁.经验鞍点近似方法及其在全基因组关联分析中的应用研究. 2022. 山东大学, MA thesis.```

- **DOI:** ```10.27272/d.cnki.gshdu.2022.002946```

**in accordance with academic standards.**

## Questions about retrospective SPA

Two pivotal papers first applied retrospective-SPA to GWAS and GxE studies.

- (1) **SPAmix**: Ma, Y., Xu, H., Li, Y. et al. SPAmix: a scalable, accurate, and universal analysis framework for large-scale genetic association studies in admixed populations. Genome Biology 26, 356 (2025). [DOI:10.1186/s13059-025-03827-9](https://doi.org/10.1186/s13059-025-03827-9).

- (2) **SPAGxE**: Ma, Y., Zhao, Y., Zhang, J.-F., and Bi, W. (2025). Efficient and accurate framework for genome-wide gene-environment interaction analysis in large-scale biobanks. Nature Communications, 16, 3064. [DOI:10.1038/s41467-025-57887-3](https://doi.org/10.1038/s41467-025-57887-3).

The original strategy is the application of SPA to retrospective score statistics, first presented in Yuzhuo Ma's master's research and documented in the 2022 thesis. The papers above provide the published methodological references.

**Suggestions or comments on retrospective saddlepoint approximation methods are also welcome.**
