---
layout: default
title: Introduction of retrospective SPA approaches in GWAS
nav_order: 2
description: "Just the Docs is a responsive Jekyll theme with built-in search that is easily customizable and hosted on GitHub Pages."
has_children: true
has_toc: true
---

# Introduction of retrospective saddlepoint approximation (retrospective SPA) approach in GWAS

## What is retrospective SPA?

**Retrospective saddlepoint approximation (Retrospective SPA)** is a method applied in GWAS. For a score statistic (S=G<sup>T</sup>R), retrospective SPA strategy
- (1) considers genotypes as random variables. 
- (2) uses saddlepoint approximation (SPA) to accurately approximate the null distribution of score statistics conditional on phenotype and covariates.

## Main features of GWAS methods based on retrospective SPA

- Applicable to a wide range of trait types (binary, time-to-event, ordinal, longitudinal, and other traits).

- Maintain high accuracy when testing low-frequency or rare variants, even when the phenotypic distribution is unbalanced (e.g. case-control imbalance in case-control studies).

## Citation of retrospective SPA

Retrospective saddlepoint approximation (Retrospective SPA) methods were first proposed in the master's thesis:

- [马雨茁.经验鞍点近似方法及其在全基因组关联分析中的应用研究.2022.山东大学,MA thesis.](https://kns.cnki.net/kcms2/article/abstract?v=jkwd3qsBIEKwkKkgMuimTLSEojAEBaWSJzCAd3uOCepX09aaYi1Vhn87HddxnsydAW9MGQHzgdF9Nw93IZ_DZCdJbGAX3C13DfGxpW58VBV273z1eVlg75Je1akPxIDc5iiSpz46iutS1tt9m3MJRg==&uniplatform=NZKPT&language=CHS)

- **DOI:10.27272/d.cnki.gshdu.2022.002946**

Based on the idea from the authors of the above master's thesis, we have applied retrospective saddlepoint approximation to several methods including:
- [```SPAmix```](https://github.com/YuzhuoMa97/SPAmix) (since 2020)
- [```SPAmix+```](https://github.com/YuzhuoMa97/SPAmixPlus) (based on ```SPAmix``` since 2024)
- [```SPAGxE```](https://github.com/YuzhuoMa97/SPAGxECCT) (based on ```SPAmix``` since 2021)
- [```SPAGxE+```](https://github.com/YuzhuoMa97/SPAGxECCT) (based on ```SPAmix``` since 2021)
- [```SPAGxEmix```](https://github.com/YuzhuoMa97/SPAGxECCT) (based on ```SPAmix``` since 2021)
- [```SPAGxEmix+```](https://github.com/YuzhuoMa97/SPAGxECCT) (based on ```SPAmix``` since 2024). 

**If you utilized the retrospective saddlepoint approximation method in your proposed methods or tools, please acknowledge and respect the original ideas presented in the two works ([```SPAmix```](https://github.com/YuzhuoMa97/SPAmixPlus) and [```SPAGxE```](https://github.com/YuzhuoMa97/SPAGxECCT)). Additionally, kindly cite the original papers ([```SPAmix```](https://github.com/YuzhuoMa97/SPAmixPlus) and [```SPAGxE```](https://github.com/YuzhuoMa97/SPAGxECCT)) or the master's thesis:**

- **[马雨茁.经验鞍点近似方法及其在全基因组关联分析中的应用研究.2022.山东大学,MA thesis.](https://kns.cnki.net/kcms2/article/abstract?v=jkwd3qsBIEKwkKkgMuimTLSEojAEBaWSJzCAd3uOCepX09aaYi1Vhn87HddxnsydAW9MGQHzgdF9Nw93IZ_DZCdJbGAX3C13DfGxpW58VBV273z1eVlg75Je1akPxIDc5iiSpz46iutS1tt9m3MJRg==&uniplatform=NZKPT&language=CHS)**

- **MLA format citation:** ```[1] 马雨茁.经验鞍点近似方法及其在全基因组关联分析中的应用研究. 2022. 山东大学, MA thesis.```

- **DOI:** ```10.27272/d.cnki.gshdu.2022.002946```

**in accordance with academic standards.**

## Questions about retrospective SPA

Given that the two pivotal papers  

- (1) **SPAmix**: A scalable, accurate, and universal analysis framework using individual-level allele frequency for large-scale genetic association studies in an admixed population

- (2) **SPAGxE**: A scalable and accurate framework for large-scale genome-wide gene-environment interaction analysis and its application to time-to-event and ordinal categorical traits

have not yet been published--despite the retrospective saddlepoint approximation method being proposed in 2021 (**first proposed in 2021 and published in the master thesis of [马雨茁.经验鞍点近似方法及其在全基因组关联分析中的应用研究.2022.山东大学,MA thesis.doi:10.27272/d.cnki.gshdu.2022.002946.](https://kns.cnki.net/kcms2/article/abstract?v=jkwd3qsBIEKwkKkgMuimTLSEojAEBaWSJzCAd3uOCepX09aaYi1Vhn87HddxnsydAW9MGQHzgdF9Nw93IZ_DZCdJbGAX3C13DfGxpW58VBV273z1eVlg75Je1akPxIDc5iiSpz46iutS1tt9m3MJRg==&uniplatform=NZKPT&language=CHS), please consult the relevant authors and supervisors the reasons for the delay in publication.**

**Suggestions or comments on retrospective saddlepoint approximation methods are also welcome.**





## Timeline of Restropective SPA Project

### March 2021
- **Event**: The idea of a retrospective saddlepoint approximation (SPA) was conceived.

### October 2021
- **Event**: The SPAmix algorithm was successfully designed.

### October 2021 - February 2022
- **Event**: Work on the SPAGxE algorithm was initiated.

### May 2022
- **Event**: The master's thesis (DOI:10.27272/d.cnki.gshdu.2022.002946), which initially introduced the concept of retrospective SPA, was completed.


![RetroSPA_timeline](https://raw.githubusercontent.com/YuzhuoMa97/RetroSPAgwas.github.io/main/docs/assets/images/RetroSPA_timeline.png)




