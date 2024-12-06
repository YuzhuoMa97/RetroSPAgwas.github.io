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

All of these approaches share the same analysis framework including the following two steps

- Step 1: Fit a null model using trait, covariates, and GRM (if applied).
- Step 2: Conduct single-variant or set-based tests to identify marker or marker-set (e.g. gene) significantly associated with the trait of interest.

The ```RetroSPAgwas``` package supports multiple traits including

- Ordianl categorical trait (POLMM / POLMM-GENE), and
- Time-to-event trait (SPACox)
- Model residuals after fitting a null model

For binary/quantitative traits analysis, we plan to incorporate SAIGE/SAIGE-GENE in the ```GRAB``` package in the future. Currently, ```SAIGE``` package is still being continuously updated.

The ```RetroSPAgwas``` package includes ```SPACox```, ```SPAmix```, and ```SPAGRM``` methods in which model residuals are supported as input. For any type of trait,  users can select an appropriate model to fit the trait to confounding factors and then calculate model residuals. If the sum of the residuals is zero, then it can serve as an input for a GWAS.

The ```RetroSPAgwas``` package supports the below genotype file format for association studies

- ```PLINK``` binary files (.bed, .bim, .fam)
- ```BGEN``` (.bgen, .bgi, .sample)

## Preparation before using GRAB package

```RetroSPAgwas``` package supports using genotype data to adjust for sample relatedness via genetic relationship matrix (GRM). PLINK binary files with high-quality genotyped variants are required for that purpose. In UK Biobank real data analysis, we used the following cutoffs in PLINK to select ~ 340K SNPs for White British subjects.

```
--maf 0.05
--indep-pairwise 500 50 0.2
```

If the sample size in analysis is greater than 100,000, we recommend using sparse GRM (instead of dense GRM) to adjust for sample relatedness. The function ```getSparseGRM()``` internally uses ```GCTA``` software (gcta_1.93.1beta) to make a ```SparseGRMFile``` which will be passed to functions if needed. As required by ```GCTA``` software, the function can only support Linux and PLINK files. Two steps are needed as below. 

- Step 1: Run ```getTempFilesFullGRM()``` to save temporary files to tempDir.

- Step 2: Run ```getSparseGRM()``` to combine the temporary files to make a ```SparseGRMFile```.

Users can customize parameters including ```(minMafGRM, maxMissingGRM, nPartsGRM)```, but the above parameters should be consistant for functions ```getTempFilesFullGRM()``` and ```getSparseGRM()```. Otherwise, the temporary files cannot be accurately located.

## Other functions in ```GRAB``` package

The ```RetroSPAgwas``` package provides some additional functions to facilitate users. More details can be seen in the corresponding sections. 

### Data Simulation

The ```RetroSPAgwas``` package can be used to simulate genotype/phenotype data.

### Genetic Relationship Matrix (GRM)

The ```RetroSPAgwas``` package supports sparse GRM to adjust for family relatedness. Functions ```getTempFilesFullGRM()``` and ```getSparseGRM()``` can be used to generate a sparse GRM using PLINK files.

### Read in Genotype Data

The ```RetroSPAgwas``` package can also be used to read in genotype data to R from ```PLINK``` and ```BGEN``` files.


