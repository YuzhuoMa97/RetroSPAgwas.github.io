---
layout: default
title: SPAmix-GENE
nav_order: 3
description: "Extending SPAmix to gene-based rare-variant association tests in admixed populations."
parent: Genome-wide association studies
has_children: false
has_toc: false
---

# SPAmix-GENE

SPAmix-GENE is a gene-based extension of [```SPAmix```](https://github.com/YuzhuoMa97/SPAmix), designed for rare-variant set tests in admixed populations under the same retrospective saddlepoint approximation (retrospective-SPA) framework.

Like SPAmix extends single-variant testing across multiple trait types, SPAmix-GENE extends the framework from variant-level GWAS to **gene-level (set-based) association analysis** by aggregating multiple variants within a gene or genomic region.

---

## Introduction to SPAmix-GENE

Single-variant tests often have limited power for rare variants because each variant has a very small minor allele count. Gene-based tests increase power by jointly testing multiple variants in a predefined set (for example, all variants in one gene).

SPAmix-GENE follows this strategy for admixed-population GWAS and keeps the key strengths of retrospective-SPA:
- accurate p-values under phenotype imbalance,
- robust calibration for low-frequency and rare variants,
- scalability for biobank-scale analyses.

---

## Core methodological ideas

1. **Set-based association on top of SPAmix scores**  
   SPAmix-GENE aggregates variant-level score information from SPAmix into gene-level tests, supporting common set-test families such as Burden, SKAT, and SKAT-O style analyses.

2. **Retrospective-SPA calibration for tail probability**  
   The retrospective-SPA idea is retained at the set-test stage to improve type I error control in challenging settings (rare variants, skewed case-control ratios, and other unbalanced outcomes).

3. **Flexible variant-set construction**  
   Inspired by practical strategies used in SAIGE-GENE+, SPAmix-GENE supports multi-threshold and multi-annotation testing workflows (e.g., multiple MAF cutoffs and functional categories such as LoF/missense/synonymous), then combines evidence across configurations.

4. **Ultra-rare variant handling**  
   For very sparse variants, SPAmix-GENE can use collapsing-style handling before set testing to improve numerical stability and power.

---

## Main features

- **Gene-based rare-variant association tests** under the SPAmix framework.
- **Compatibility with admixed-population modeling**, including the SPAmix population-structure/local-ancestry setup.
- **Accurate calibration for unbalanced phenotypes** through retrospective-SPA.
- **Scalable implementation** suitable for large cohort analyses.

---

## Citation

If you use SPAmix-GENE, please cite:

- **SPAmix-GENE (this work):**  
  **Ma, Y. et al.**, *SPAmix-GENE: extending retrospective-SPA GWAS to gene-based rare-variant association analysis in admixed populations*.  
  **Manuscript in preparation (to be submitted).**

- **SPAmix (foundational framework):**  
  Ma, Y., Xu, H., Li, Y. et al. (2025). SPAmix: a scalable, accurate, and universal analysis framework for large-scale genetic association studies in admixed populations. *Genome Biology*, 26, 356.  
  [DOI: 10.1186/s13059-025-03827-9](https://doi.org/10.1186/s13059-025-03827-9)

- **Retrospective-SPA original thesis idea:**  
  Ma, Y. (2022). Empirical Saddlepoint Approximation and Its Application to Genome-Wide Association Studies.
  [DOI: 10.27272/d.cnki.gshdu.2022.002946](https://doi.org/10.27272/d.cnki.gshdu.2022.002946)
