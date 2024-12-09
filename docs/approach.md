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

**Retrospective saddlepoint approximation (Retrospective SPA)** is a method applied in GWAS. For a score statistic (S=G<sup>T</sup>R), retrospective SPA strategy considers genotypes as random variables and uses saddlepoint approximation to accurately approximate the null distribution of score statistics conditional on phenotype and covariates.

## Citation of retrospective SPA

Retrospective saddlepoint approximation (Retrospective SPA) methods were first proposed in the master's thesis:

- [马雨茁.经验鞍点近似方法及其在全基因组关联分析中的应用研究.2022.山东大学,MA thesis.](https://kns.cnki.net/kcms2/article/abstract?v=jkwd3qsBIEKwkKkgMuimTLSEojAEBaWSJzCAd3uOCepX09aaYi1Vhn87HddxnsydAW9MGQHzgdF9Nw93IZ_DZCdJbGAX3C13DfGxpW58VBV273z1eVlg75Je1akPxIDc5iiSpz46iutS1tt9m3MJRg==&uniplatform=NZKPT&language=CHS)

- **DOI:10.27272/d.cnki.gshdu.2022.002946**

Based on the idea from the authors of the above master's thesis, we have applied retrospective saddlepoint approximation to several methods including:
- [```SPAmix```](https://github.com/YuzhuoMa97/SPAmixPlus) (since 2020)
- ```SPAmix+``` (based on SPAmix since 2024)
- ```SPAGxE``` (based on ```SPAmix``` since 2021)
- ```SPAGxEmix+``` (based on ```SPAmix``` since 2024). 

**If you utilized the retrospective saddlepoint approximation method in your proposed methods or tools, please acknowledge and respect the original ideas presented in the two works (```SPAmix``` and ```SPAGxE```). Additionally, kindly cite the original papers (```SPAmix``` and ```SPAGxE```) or the master's thesis:**

- **[马雨茁.经验鞍点近似方法及其在全基因组关联分析中的应用研究.2022.山东大学,MA thesis.](https://kns.cnki.net/kcms2/article/abstract?v=jkwd3qsBIEKwkKkgMuimTLSEojAEBaWSJzCAd3uOCepX09aaYi1Vhn87HddxnsydAW9MGQHzgdF9Nw93IZ_DZCdJbGAX3C13DfGxpW58VBV273z1eVlg75Je1akPxIDc5iiSpz46iutS1tt9m3MJRg==&uniplatform=NZKPT&language=CHS)**

- **MLA format citation:** ```[1] 马雨茁.经验鞍点近似方法及其在全基因组关联分析中的应用研究. 2022. 山东大学, MA thesis.```

- **DOI:** ```10.27272/d.cnki.gshdu.2022.002946```

**in accordance with academic standards.**

## Questions about retrospective SPA

Given that the two pivotal papers  

- (1) **SPAmix**: A scalable, accurate, and universal analysis framework using individual-level allele frequency for large-scale genetic association studies in an admixed population

- (2) **SPAGxE**: A scalable and accurate framework for large-scale genome-wide gene-environment interaction analysis and its application to time-to-event and ordinal categorical traits

have not yet been published--despite the retrospective saddlepoint approximation method being proposed in 2021 (**first proposed in 2021 (in ```SPAmix```) and published in 2022 [马雨茁.经验鞍点近似方法及其在全基因组关联分析中的应用研究.2022.山东大学,MA thesis.doi:10.27272/d.cnki.gshdu.2022.002946.](https://kns.cnki.net/kcms2/article/abstract?v=jkwd3qsBIEKwkKkgMuimTLSEojAEBaWSJzCAd3uOCepX09aaYi1Vhn87HddxnsydAW9MGQHzgdF9Nw93IZ_DZCdJbGAX3C13DfGxpW58VBV273z1eVlg75Je1akPxIDc5iiSpz46iutS1tt9m3MJRg==&uniplatform=NZKPT&language=CHS), please consult the relevant authors and supervisors the reasons for the delay in publication.**

**Suggestions or comments on retrospective saddlepoint approximation methods are also welcome.**
