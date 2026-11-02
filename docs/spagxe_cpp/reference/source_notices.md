---
layout: "default"
title: "C++ source and dependency notices"
parent: "C++ technical reference"
nav_order: 5
permalink: "/docs/spagxe_cpp/source_notices.html"
has_children: false
has_toc: true
grand_parent: "SPAGxE C++ manual"
---

**Development source.** SPAGxE 1.2.0 is published on [develop](https://github.com/YuzhuoMa97/SPAGxECCT/tree/develop). [Hosted checks for d90fb4c](https://github.com/YuzhuoMa97/SPAGxECCT/actions/runs/41416750904) passed Windows and Ubuntu; macOS numerical unit checks failed and the platform remains unvalidated. The C++ release tag and runtime assets are not yet published. See the [validation record](/RetroSPAgwas.github.io/docs/spagxe_cpp/validation.html) and [development status](/RetroSPAgwas.github.io/docs/spagxe_cpp/development_status.html) for the tested revision and download instructions. Later source commits require their own checks.

# Incorporated source and dependency notices {#incorporated-source-and-dependency-notices}

SPAGxE algorithms and new standalone changes: Yuzhuo Ma, yuzhuoma@amss.ac.cn.
The method's published authorship is retained in CITATION_CPP.cff.

New SPAGxE work includes the paper-defined interaction policy, guarded partial-normal SPA with full-CGF diagnostics, AF/input/numerical corrections, local G/H analysis and packing,
standalone interfaces, examples and validation. Historical R files in this
repository keep their existing contents and license scope.

| Component | Location | License |
|---|---|---|
| Incorporated GPL application code | cpp/src, Makefile, tests | GPL-3.0-or-later; cpp/LICENSE |
| Eigen 5.0.0 | cpp/third_party/eigen-5.0.0 | MPL-2.0 and included notices |
| Boost 1.80.0 | cpp/third_party/boost-1.80.0 | Boost Software License 1.0 |
| pgenlib / libdeflate | cpp/third_party/plink2-a.6.33 | Included LGPL-3-or-later / MIT notices |
| BGEN library | cpp/third_party/bgen-1.2.0 | Boost Software License 1.0 |
| htslib | cpp/third_party/htslib-1.23.1 | MIT and included notices |
| zlib | cpp/third_party/zlib-1.3.2 | zlib license |
| zstd | cpp/third_party/zstd-1.5.7 | Included BSD/GPL choices |
| SQLite | cpp/third_party/sqlite-3.53.2 | Public domain dedication |

Bundled sample inputs are provided for format and tutorial validation.
Other bundled association examples are synthetic SPAGxE data.
No private external-project source, manuscripts or real study datasets are
included in the new standalone distribution.

Windows source builds additionally use POSIX-regex libraries supplied by the
selected MinGW toolchain. A custom source build may have runtime requirements
different from the tested, statically linked Windows release bundle.

## Authorship and ownership {#authorship-and-ownership}

# SPAGxE authorship and ownership {#spagxe-authorship-and-ownership}

The SPAGxE method family is described in the published SPAGxE paper. The software maintainer is
Yuzhuo Ma, yuzhuoma@amss.ac.cn.

Copyright in the new standalone SPAGxE changes and project materials is asserted
for Yuzhuo Ma, 2026, subject to the licenses of incorporated components.

The historical R sources and root license remain in their original scope.
DESCRIPTION declares GPL (>=3), while the historical root LICENSE contains
additional research/non-commercial restrictions. This release preserves those
historical texts; it does not silently resolve that discrepancy.

The standalone C++ application is distributed under cpp/LICENSE, with its
retained source and dependency notices. THIRD_PARTY_NOTICES.md records the
component licenses and the scope of bundled example inputs.
Renaming files or functions does not change those origins or license terms.


## Author-designated official C++ channel {#author-designated-official-c-channel}

Yuzhuo Ma designates this repository and its maintainer-published C++ releases
as the sole official standalone C++ distribution of the SPAGxE method family.
Yuzhuo Ma is the method designer and author/maintainer of the original SPAGxE
software. Questions about methods, implementation, installation or results
may be sent to yuzhuoma@amss.ac.cn.

This designation identifies the maintainer's release channel. It does not
claim exclusive authorship of incorporated infrastructure, alter third-party
license rights, or state that every other implementation is incorrect.
The paper's coauthorship and the historical R package remain acknowledged.
