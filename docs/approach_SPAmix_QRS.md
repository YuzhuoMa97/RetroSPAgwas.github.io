---
layout: default
title: SPAmix‑QRS
nav_order: 3
description: "SPAmix‑QRS for quantile regression GWAS with individual‑specific allele frequencies and local ancestry in admixed and multi‑ancestry cohorts."
parent: Genome-wide association studies
has_children: false
has_toc: false
---

# SPAmix‑QRS

[```SPAmix‑QRS```](https://github.com/YuzhuoMa97/SPAmix-QRS) is a quantile‑regression GWAS method that extends my previously published **SPAmix** framework (Ma, et al., *Genome Biology* 2025) from mean‑/link‑based retrospective score tests to **convolution‑smoothed quantile regression (SQR)**. It builds directly on my **retrospective saddlepoint approximation (retrospective‑SPA) idea** first described in my master’s thesis ([Ma, 2022](https://kns.cnki.net/kcms2/article/abstract?v=jkwd3qsBIEKwkKkgMuimTLSEojAEBaWSJzCAd3uOCepX09aaYi1Vhn87HddxnsydAW9MGQHzgdF9Nw93IZ_DZCdJbGAX3C13DfGxpW58VBV273z1eVlg75Je1akPxIDc5iiSpz46iutS1tt9m3MJRg==&uniplatform=NZKPT&language=CHS), DOI: [10.27272/d.cnki.gshdu.2022.002946](https://doi.org/10.27272/d.cnki.gshdu.2022.002946)).

SPAmix‑QRS is designed for quantile‑specific association testing in admixed and multi‑ancestry cohorts, and it can:

- estimate **individual‑specific allele frequencies (ISAF)** from raw genotypes and SNP‑derived PCs,
- apply a **retrospective score test** with **saddlepoint approximation (SPA)** for accurate p‑values,
- incorporate **local ancestry** via the SPAmixlocal‑QRS module,
- combine results across quantiles using **Cauchy combination**.

## Method comparison

| Method | Account for population structure | Account for local ancestry | Account for family relatedness | Quantile regression |
|:------:|:-------------------------------:|:--------------------------:|:------------------------------:|:-------------------:|
| SPAmix | YES | YES | NO | NO (mean‑based) |
| **SPAmix‑QRS** | **YES** | **YES** | **NO** | **YES** |

## Relationship with SPAmix

SPAmix‑QRS is a direct extension of SPAmix. While SPAmix focuses on mean‑/link‑based association tests, SPAmix‑QRS introduces **convolution‑smoothed quantile regression** to detect effects across the entire phenotypic distribution. It retains SPAmix’s core innovations (ISAF, retrospective SPA) and adds local‑ancestry‑aware quantile testing.

## Citation

If you use SPAmix‑QRS, please cite:

- **SPAmix‑QRS (this work):**  
  **Ma, Y. et al.**, *SPAmix‑QRS: quantile regression GWAS with individual‑specific allele frequencies and local ancestry for admixed and multi‑ancestry cohorts*.  

- **SPAmix (foundational framework):**  
  Ma, Y., Xu, H., Li, Y. et al. (2025). SPAmix: a scalable, accurate, and universal analysis framework for large‑scale genetic association studies in admixed populations. *Genome Biology*, 26, 356.  
  [DOI: 10.1186/s13059‑025‑03827‑9](https://doi.org/10.1186/s13059‑025‑03827‑9)

- **Retrospective‑SPA original thesis idea:**  
  Ma, Y. (2022). Empirical Saddlepoint Approximation and Its Application to Genome‑Wide Association Studies.  
  [DOI: 10.27272/d.cnki.gshdu.2022.002946](https://doi.org/10.27272/d.cnki.gshdu.2022.002946)
