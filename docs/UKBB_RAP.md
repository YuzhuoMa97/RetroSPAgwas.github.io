---
layout: default
title: UK Biobank RAP
nav_order: 3
description: "Just the Docs is a responsive Jekyll theme with built-in search that is easily customizable and hosted on GitHub Pages."
has_children: false
---

# UK Biobank Research Analyses Platform (RAP)

UK Biobank Research Analyses Platform (RAP) enables researchers working with UK Biobank's large-scale biomedical database and research resource, to access it in the cloud from anywhere in the world. It has been designed to accommodate the vast and increasing scale of the UK Biobank resource.

## Using docker to conduct POLMM-GENE anaysis

We record the process of POLMM-GENE analysis on UK Biobank RAP via docker

- Put all files in https://github.com/GeneticAnalysisinBiobanks/GRAB/tree/main/docker to a local directory

- Run the following command to install the GRAB package via docker

```
docker build --build-arg version=0.0.3.3 -t user/grab:0.0.3.3 .
docker save user/grab:0.0.3.3 > grab_0.0.3.3.tar
gzip grab_0.0.3.3.tar
```

- Move the below files to UK Biobank RAP
  - grab_0.0.3.3.tar.gz
  - grab_ReadGeno.wdl
  - grea_Region.wdl
  - results of null model fitting

The below is an example we used

```
dx upload grab_0.0.3.3.tar.gz   # the location should be the same as in XXX.wdl files
dx mkdir /WES_450k/cognitive_120042_batch
dx cd /WES_450k/cognitive_120042_batch
cd /home/wenjianb/POLMM-GENE/UKB-450K/cognitive_120042_batch
dx upload cognitive_120042_batch.RData
```

Try the following codes

```
docker run wenjianb/grab:0.0.3.3 Rscript GRAB.Region.R --help
docker run wenjianb/grab:0.0.3.3 Rscript GRAB.ReadGeno.R --help
```

- Build the workflow of GRAB

```
java -jar dxCompiler-2.9.0.jar compile grab_Region.wdl -project project-G7KJj3QJyFVxfVvBKGxQP2kX -folder /workflows/ -f
# record workflow ID, e.g. workflow-GB3q1YjJyFVgYj3v0V66YqzV
```

- Conduct the analysis

The below is an example we used.

```
for chr in 1 2 3 6 7 11 12 16 17 19
do
dx run workflow-GB3q1YjJyFVgYj3v0V66YqzV \
-istage-common.objNullFile=UK_Biobank_WES:/WES_450k/cognitive_120042_batch/cognitive_120042_batch.RData \
-istage-common.GenoFile=UK_Biobank_WES:/Bulk/Exome\ sequences/Population\ level\ exome\ OQFE\ variants,\ PLINK\ format\ -\ interim\ 450k\ release/ukb23149_c${chr}_b0_v1.bed \
-istage-common.GenoMarkerIndexFile=UK_Biobank_WES:/Bulk/Exome\ sequences/Population\ level\ exome\ OQFE\ variants,\ PLINK\ format\ -\ interim\ 450k\ release/ukb23149_c${chr}_b0_v1.bim \
-istage-common.GenoSampleFile=UK_Biobank_WES:/Bulk/Exome\ sequences/Population\ level\ exome\ OQFE\ variants,\ PLINK\ format\ -\ interim\ 450k\ release/ukb23149_c${chr}_b0_v1.fam \
-istage-common.GroupFile=UK_Biobank_WES:/WES_450k/groupFilesByZhouWeiTabSeperatedCombineByChr/UKBexomeOQFE_chr${chr}.ukb23149.groupFile.txt \
-istage-common.SparseGRMFile=UK_Biobank_WES:/WES_450k/SparseGRM_0.05.txt \
-istage-common.ControlFile=UK_Biobank_WES:/WES_450k/ControlFile_maxMAC_5.txt \
-istage-common.MaxMAFVec="0.01,0.001,0.0001" \
-istage-common.annoVec="lof,lof:missense" \
-istage-common.OutputPrefix=cognitive_120042_batch_maxMAC_5_chr${chr} \
--folder UK_Biobank_WES:/WES_450k/cognitive_120042_batch/ \
--instance-type mem1_ssd2_v2_x4 \
--priority low \
--yes
done
```

## Notes prior to analysis

We complete null model fitting in local service and conduct set-based analysis in UK Biobank RAP. Please ensure the subjects in null model fitting are also in genotype files.
