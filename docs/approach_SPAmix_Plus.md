---
layout: default
title: SPAmix+
nav_order: 2
description: "SPAmix+ for GWAS in admixed and diverse populations with relatedness."
parent: Genome-wide association studies
has_children: false
has_toc: false
---

# SPAmix+

[```SPAmix+```](https://github.com/YuzhuoMa97/SPAmixPlus) is an extension of [```SPAmix```](https://github.com/YuzhuoMa97/SPAmix), developed from **Yuzhuo Ma's retrospective saddlepoint approximation (retrospective-SPA) idea** first described in his master's thesis ([Ma, 2022](https://kns.cnki.net/kcms2/article/abstract?v=jkwd3qsBIEKwkKkgMuimTLSEojAEBaWSJzCAd3uOCepX09aaYi1Vhn87HddxnsydAW9MGQHzgdF9Nw93IZ_DZCdJbGAX3C13DfGxpW58VBV273z1eVlg75Je1akPxIDc5iiSpz46iutS1tt9m3MJRg==&uniplatform=NZKPT&language=CHS), DOI: [10.27272/d.cnki.gshdu.2022.002946](https://doi.org/10.27272/d.cnki.gshdu.2022.002946)).

SPAmix+ is designed as a scalable, unified toolbox for genome-wide association studies in admixed and diverse populations, and it can:

- adjust for population structure,
- adjust for sample relatedness,
- support local ancestry,
- keep the retrospective-SPA advantages in accuracy and scalability.

## Method comparison

| Method | Account for population structure | Account for local ancestry | Account for family relatedness | Prospective/Retrospective |
|:------:|:-------------------------------:|:--------------------------:|:------------------------------:|:-------------------------:|
| SPACox | NO | NO | NO | Prospective |
| SPAmix | YES | YES | NO | Retrospective |
| SPA<sub>GRM</sub> | NO | NO | YES | Retrospective |
| SPAmix+ | YES | YES | YES | Retrospective |

## Relationship with SPAmix

SPAmix+ and SPAmix are distinct works. SPAmix+ extends SPAmix from admixed-population association analysis to a broader setting that simultaneously addresses **admixture, diversity, and relatedness**.

## Citation

If you use SPAmix+, please cite:

- **SPAmix+ (this work):**  
  **Ma, Y. et al.**, *SPAmix+: a scalable, unified toolbox for genome-wide association studies in admixed and diverse populations with relatedness*.  
  **Manuscript in preparation (to be submitted).**

- **SPAmix (foundational framework):**  
  Ma, Y., Xu, H., Li, Y. et al. (2025). SPAmix: a scalable, accurate, and universal analysis framework for large-scale genetic association studies in admixed populations. *Genome Biology*, 26, 356.  
  [DOI: 10.1186/s13059-025-03827-9](https://doi.org/10.1186/s13059-025-03827-9)

- **Retrospective-SPA original thesis idea:**  
  马雨茁. 经验鞍点近似方法及其在全基因组关联分析中的应用研究. 山东大学, 2022 (MA thesis).  
  [DOI: 10.27272/d.cnki.gshdu.2022.002946](https://doi.org/10.27272/d.cnki.gshdu.2022.002946)
