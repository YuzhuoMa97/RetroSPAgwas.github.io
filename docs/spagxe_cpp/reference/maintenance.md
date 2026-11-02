---
layout: "default"
title: "C++ maintenance notes"
parent: "C++ technical reference"
nav_order: 6
permalink: "/docs/spagxe_cpp/maintenance.html"
has_children: false
has_toc: true
grand_parent: "SPAGxE C++ manual"
---

**Maintenance candidate.** This page accompanies local SPAGxE 1.2.0 maintenance source that has not yet been pushed or tagged. The [public baseline](https://github.com/YuzhuoMa97/SPAGxECCT/commit/c7c11590efbd10504115cd0ad8dbb9c6ca2634e1) passed hosted Windows and Ubuntu checks; its macOS build failed. Those hosted results do not validate this new candidate. Read the [candidate validation record](/RetroSPAgwas.github.io/docs/spagxe_cpp/validation.html) and [development status](/RetroSPAgwas.github.io/docs/spagxe_cpp/development_status.html) for the current evidence and download boundaries.

# Maintenance revision {#maintenance-revision}

Prepared on 1 November 2026.

This revision keeps the published-method statistical policy, file formats,
result columns and executable version. It improves implementation structure
without introducing a second statistical profile.

## Numerical contracts {#numerical-contracts}

- Shared-AF, sparse-GRM, individual-AF and known-H local workflows continue
  to use the same guarded partial-normal SPA.
- Quantile interpolation, summation order, SIMD lane/reduction order,
  root thresholds and convergence rules are preserved.
- Individual-AF fitting, failure diagnostics and allele orientation retain
  their existing definitions.
- Unpublished joint individual-AF and cross-subject-GRM interaction tests
  are not part of this distribution.

## Engineering changes {#engineering-changes}

| Area | Maintenance purpose |
|---|---|
| Subject mapping | Reuse union-to-dense indexing and sample traversal |
| File resources | Scope-based release during construction failures |
| Text parsing | Share delimiter and buffer contracts |
| Logging | Share message formatting while keeping serialized writes |
| Null-model assembly | Centralize phenotype specification and result mapping |
| Outlier selection | Separate fence selection from ordered data gathering |
| CGF execution | Share private tier selection and terminal-correction policy |
| SIMD constants | Keep coefficient definitions consistent across vector widths |

The canonical sparse-GRM table option is --grm-file. An obsolete pre-release
option alias was removed. Use the canonical option in all new commands.
Developer comparisons against a previous executable can supply
--baseline-grm-flag to the full-reference comparison script when that
executable uses a different option name.

## Validation and release {#validation-and-release}

Implementation changes require a fresh build, numerical units, all method and
reader regressions, and a paired comparison with the previously accepted
executable. Source and extracted runtime tutorials must also match. Detailed
acceptance scope is recorded in [validation](/RetroSPAgwas.github.io/docs/spagxe_cpp/validation.html) and
[release status](/RetroSPAgwas.github.io/docs/spagxe_cpp/release_scope.html).

Preserved R sources keep their historical interface and dependency chain.
The standalone C++ executable does not use R at runtime. Dependency-specific
copyright and license files remain with the distributed components.
