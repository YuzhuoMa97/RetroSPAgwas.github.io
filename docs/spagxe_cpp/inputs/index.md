---
layout: "default"
title: "C++ inputs and local ancestry"
parent: "SPAGxE C++ manual"
nav_order: 3
permalink: "/docs/spagxe_cpp/inputs.html"
has_children: true
has_toc: true
grand_parent: "Genome-wide gene-environment interaction (GxE) studies"
---

**Maintenance candidate.** This page accompanies local SPAGxE 1.2.0 maintenance source that has not yet been pushed or tagged. The [public baseline](https://github.com/YuzhuoMa97/SPAGxECCT/commit/c7c11590efbd10504115cd0ad8dbb9c6ca2634e1) passed hosted Windows and Ubuntu checks; its macOS build failed. Those hosted results do not validate this new candidate. Read the [candidate validation record](/RetroSPAgwas.github.io/docs/spagxe_cpp/validation.html) and [development status](/RetroSPAgwas.github.io/docs/spagxe_cpp/development_status.html) for the current evidence and download boundaries.

# C++ inputs and local ancestry {#c-inputs-and-local-ancestry}

The [complete tutorial](/RetroSPAgwas.github.io/docs/spagxe_cpp/full_tutorial.html#choose-a-method-and-prepare-input) describes phenotype/covariate tables, sample IDs and global PLINK BED/PGEN, BGEN and VCF/BCF input. The command-line and schema checks must be read before preparing cohort data.

- [Local ancestry workflow](/RetroSPAgwas.github.io/docs/spagxe_cpp/local_overview.html)
- [G/H text and packed count formats](/RetroSPAgwas.github.io/docs/spagxe_cpp/local_counts.html)
- [Known-H local BGEN](/RetroSPAgwas.github.io/docs/spagxe_cpp/local_bgen.html)
- [Prepare ancestry-specific G/H](/RetroSPAgwas.github.io/docs/spagxe_cpp/local_preparation.html)
- [Native count packing and BIM/FAM reuse](/RetroSPAgwas.github.io/docs/spagxe_cpp/local_packing.html)
- [Individual-AF export format](/RetroSPAgwas.github.io/docs/spagxe_cpp/af_model.html)

Local ancestry is supplied upstream. The software does not infer ancestry or construct a genotype posterior from a dosage. Hardcall packing requires integer counts; dosage and known-H BGEN have separate input routes.
