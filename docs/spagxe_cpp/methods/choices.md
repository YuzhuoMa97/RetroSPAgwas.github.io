---
layout: "default"
title: "C++ implementation choices"
parent: "C++ four methods"
nav_order: 12
permalink: "/docs/spagxe_cpp/choices.html"
has_children: false
has_toc: true
grand_parent: "SPAGxE C++ manual"
---

Documentation source: [ce9c2473649e](https://github.com/YuzhuoMa97/SPAGxECCT/blob/ce9c2473649e0be2a8b70dd2f6186a03b25d21aa/docs/IMPLEMENTATION_CHOICE.md). [Current development checks](/RetroSPAgwas.github.io/docs/spagxe_cpp/development_status.html).

**Source and validation status.** The text below mirrors the published pre-fix source. Local Windows/Linux validation passed after input/build repairs; those repairs still await a public push and matching CI. [Read the required repairs and current evidence](/RetroSPAgwas.github.io/docs/spagxe_cpp/development_status.html).

# Implementation choices for the official C++ release {#implementation-choices-for-the-official-c-release}

The release preserves the published SPAGxE weight definitions and uses one
statistical policy with declared guarded partial-normal CGF acceleration. A different implementation is not a reason, by
itself, to replace an equation or declare either complete test superior.
The incorporated-source provenance remains in ../THIRD_PARTY_NOTICES.md.

| Item | Official release decision | Evidence and tradeoff |
|---|---|---|
| Branch B | Use E*R0 after residualizing R on intercept and G | Reproduces the published definition |
| Further weight projection | Do not add silently | Can reduce a fixed working variance and remove E-origin dependence, but changes the working test |
| CGF | Guarded partial-normal CGF beyond the normal threshold, in all four methods | Reduces repeated central CGF work; adds an approximation with full-CGF candidate-root diagnostics and automatic full evaluation |
| AF policy | Minor-oriented pooled/OLS/carrier-logistic with two-sided bounds and strict 90% criterion | Matches the stated method; carrier count and minor MAC are not interchangeable |
| Failed AF fits | NA/status 9; model export -2 | Finite but unconverged coefficients are not a valid fitted reference law |
| Wald | Eligible unrelated raw-trait Branch B only | Residual-only and GRM paths do not acquire a fictitious independent-sample Wald leg |
| Cox ties | Breslow for the native fits | Historical R default Efron comparisons must explicitly match ties |
| Root and tails | Bracket/support checks and log-domain arithmetic | Numerical safeguards preserve valid tails and expose failed computations |
| CCT | Explicit weights, stable log-domain combination | Legal P below 1 is not blanket-clipped; exact P=1 uses the documented endpoint policy |
| Local G/H | Known H, Bin(H,q), H-G, H*q, rank-aware Wald | Respect ancestry copy counts and stated input/missingness contracts |

The extra covariance-metric projection has useful mathematical properties.
They do not alone prove that a complete data-dependent SPA/CCT has better
type-I error or power in all settings: R0 itself depends on observed G.
The paper's Branch-B working approximation can depend on environmental origin.
Choose and report E coding before inspecting association P values.

The partial-CGF acceleration is an explicit implementation revision, described
in [partial SPA](/RetroSPAgwas.github.io/docs/spagxe_cpp/partial_spa.html). It preserves the first two working cumulants
but not every higher cumulant or P value. Fixed 1.5-IQR partitioning and 1e-3
full-CGF diagnostics define one policy; automatic full evaluation is its
protection path, not a second user-selectable method. Diagnostic tolerance is
not a theorem about P-value error. Performance claims require measured workloads.
A further weight revision would require separate calibration, power and coding
sensitivity studies; it is not silently included with this acceleration.
Current code is not known to be universally worse or better than an alternative
complete implementation.

The four methods have distinct scopes: homogeneous unrelated SPAGxE,
homogeneous GRM-adjusted SPAGxE+, individual-AF unrelated SPAGxEmix, and
known-H local-ancestry unrelated SPAGxEmix_local.
The combined individual-AF plus cross-subject-GRM interaction extension is not
provided. Local input does not infer ancestry or integrate arbitrary uncertain H.

R agreement requires matched samples, masks, alleles, E coding, PCs/AF routing,
residuals/null fits, ties, thresholds and CCT weights. Boundary repairs are not
required to reproduce historical defects. Smaller P does not establish accuracy.
See [method policy](/RetroSPAgwas.github.io/docs/spagxe_cpp/policy.html), [equations](/RetroSPAgwas.github.io/docs/spagxe_cpp/equations.html),
[release scope](/RetroSPAgwas.github.io/docs/spagxe_cpp/release_scope.html) and [validation](/RetroSPAgwas.github.io/docs/spagxe_cpp/validation.html).


Coverage of the three global interaction workflows does not mean that every
alternative approximation, selector or historical R extension is preserved.
The single documented statistical policy is deliberate; see
[feature coverage](/RetroSPAgwas.github.io/docs/spagxe_cpp/features.html). Historical reference comparisons and
current executable regressions are different evidence layers. Matched-domain
agreement is not an assertion of all-default, all-input equality.
