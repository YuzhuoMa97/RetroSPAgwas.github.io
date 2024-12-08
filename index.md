---
layout: default
title: Overview
nav_order: 1
description: "Overview of Restropective saddlepoint approximation (SPA) methods in GWAS."
has_children: false
has_toc: false
---

# Overview of Restropective saddlepoint approximation (SPA) methods in GWAS

The ```RetroSPAgwas``` package is mainly designed to conduct **genome-wide association studies (GWAS)** in terms of both single-variant and set-based analysis. In addition, the package can also be used 
- to simulate genotype/phenotype data, 
- to calculate sparse GRM, and 
- to read in genotype data from PLINK/BGEN files.  

## Genome-wide association studies

All retrospective-SPA-based GWAS approaches share the same analysis framework including the following two steps

- Step 1: Fit a null model using trait, covariates, and GRM (if applied).
- Step 2: Conduct single-variant or set-based tests to identify marker or marker-set (e.g. gene) significantly associated with the trait of interest.


###  Genome-wide gene-environment interaction (GxE) studies

All retrospective-SPA-based GxE approaches share the same analysis framework including the following two steps

- Step 1: Fit a genotype-independent (covariates-only) model using trait, covariates, and GRM (if applied).
- Step 2: Conduct single-variant or set-based tests to identify marker or marker-set (e.g. gene) significantly associated with the trait of interest.

### Read in Genotype Data

The ```RetroSPAgwas``` package can also be used to read in genotype data to R from ```PLINK``` and ```BGEN``` files.


