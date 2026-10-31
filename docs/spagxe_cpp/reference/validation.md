---
layout: "default"
title: "C++ validation record"
parent: "C++ technical reference"
nav_order: 4
permalink: "/docs/spagxe_cpp/validation.html"
has_children: false
has_toc: true
grand_parent: "SPAGxE C++ manual"
---

**Local repaired candidate documentation.** This page includes the input/build repairs and local Windows/Linux verification prepared after public commit [`ce9c2473649e`](https://github.com/YuzhuoMa97/SPAGxECCT/commit/ce9c2473649e0be2a8b70dd2f6186a03b25d21aa). The candidate changes still await a public push and matching hosted CI; they are not asserted to exist in that published pre-fix commit. [Current development status](/RetroSPAgwas.github.io/docs/spagxe_cpp/development_status.html).

# Validation records and interpretation {#validation-records-and-interpretation}

The current candidate is a local repair of public development commit
`ce9c2473649e0be2a8b70dd2f6186a03b25d21aa`. Read
[release status](/RetroSPAgwas.github.io/docs/spagxe_cpp/release_scope.html) for the distinction between the failed
public Actions run and locally passing repaired source.

The [acceptance summary](/RetroSPAgwas.github.io/docs/spagxe_cpp/validation.html#current-acceptance-summary) records the current Windows/Linux
scope and retains the earlier acceptance object under a historical key.
Historical source counts, hashes and test dates describe those snapshots;
they are not the identities of a later repaired release asset.

## Current repaired candidate {#current-repaired-candidate}

- CRLF/LF/no-final-newline BIM metadata and cross-format integration are
  explicitly tested in cpp/tests/run_integration.py.
- The Windows full-static link mode is checked from the compiler-driver
  command and PE imports, with native minimal-PATH tutorials.
- Windows numerical units, 17 regression suites, six tutorials and the full
  33-group walkthrough have passing local records.
- Ubuntu 24.04.5 x86-64/WSL2, GCC 13.3: 22 stages cover units, 14 CI suites,
  integration, tutorials, bundle extraction and PREFIX installation.
- Cross-platform association/CCT values agree within the documented floating
  point tolerance. This does not replace actual-R, independent scalar or
  high-precision references, nor population-level type-I error studies.

Developer scripts regenerate their own JSON summaries under cpp/results/.
Analysis and example execution do not require Python or R; developer/reference
tests may require them. Source-only checks and actual binary execution are
different evidence.

## Remaining limits {#remaining-limits}

The original public CI run failed. A repaired local source tree is not a new
remote commit, and its checks must run again after the maintainer pushes it.
macOS remains unverified. No finite test collection proves universal extreme-
tail calibration, every historical default P value, every possible input or
a biobank-scale speed advantage. Native Linux testing under WSL2 does not
measure bare-metal biobank throughput or support all older glibc releases.

Original R/full-CGF comparisons apply only to matched common domains. The
guarded partial default deliberately adds an approximation; full-CGF candidate
diagnostics are not a P-value error bound. The historical R source and interface
remain available, with their own versions and dependencies.

## Current acceptance summary {#current-acceptance-summary}

This is the local repaired candidate record, not the old JSON at the pre-fix public commit. It retains historical data under its dated key.

<details><summary>Read the current acceptance JSON</summary>
<pre><code class="language-json">{
  &quot;software&quot;: &quot;SPAGxE&quot;,
  &quot;version&quot;: &quot;1.2.0&quot;,
  &quot;date&quot;: &quot;2026-10-31&quot;,
  &quot;scope&quot;: &quot;Local repaired development candidate; hosted final-commit rerun remains required&quot;,
  &quot;base_public_commit&quot;: &quot;ce9c2473649e0be2a8b70dd2f6186a03b25d21aa&quot;,
  &quot;methods&quot;: [
    &quot;SPAGxE&quot;,
    &quot;SPAGxE+&quot;,
    &quot;SPAGxEmix&quot;,
    &quot;SPAGxEmix_local&quot;
  ],
  &quot;statistical_policy&quot;: &quot;paper-defined weights; guarded partial-normal CGF&quot;,
  &quot;statistical_equations_changed&quot;: false,
  &quot;input_reader_repair&quot;: &quot;Remove trailing CR from CRLF BIM lines before tokenizing&quot;,
  &quot;build_repair&quot;: &quot;Honor full-static Windows library lookup for implicit runtime libraries&quot;,
  &quot;local_candidate_passed&quot;: true,
  &quot;Windows&quot;: {
    &quot;numerical_units&quot;: true,
    &quot;regression_suites&quot;: 17,
    &quot;tutorial_output_files&quot;: 45,
    &quot;full_walkthrough_groups&quot;: 33,
    &quot;full_walkthrough_output_files&quot;: 85,
    &quot;minimal_PATH&quot;: true,
    &quot;compiler_runtime_DLLs_required&quot;: false,
    &quot;platform&quot;: &quot;x86-64 Haswell/AVX2&quot;
  },
  &quot;Linux&quot;: {
    &quot;distribution&quot;: &quot;Ubuntu 24.04.5&quot;,
    &quot;kernel_environment&quot;: &quot;WSL2 Linux ELF&quot;,
    &quot;architecture&quot;: &quot;x86_64&quot;,
    &quot;compiler&quot;: &quot;GCC 13.3&quot;,
    &quot;stages&quot;: 22,
    &quot;numerical_units&quot;: true,
    &quot;CI_regression_suites&quot;: 14,
    &quot;integration_checks&quot;: 51,
    &quot;integration_rows&quot;: 52416,
    &quot;source_bundle_tutorial_files_equal&quot;: 45,
    &quot;PREFIX_installation_passed&quot;: true,
    &quot;all_older_Linux_runtime_compatibility&quot;: false
  },
  &quot;cross_platform&quot;: {
    &quot;tables&quot;: 43,
    &quot;numeric_fields&quot;: 139709,
    &quot;max_absolute_delta&quot;: 1.4210854715202004e-14,
    &quot;kind&quot;: &quot;Same repaired implementation; portability/reproducibility, not independent calibration&quot;
  },
  &quot;public_actions&quot;: {
    &quot;run_id&quot;: 41034171345,
    &quot;conclusion&quot;: &quot;failure&quot;,
    &quot;url&quot;: &quot;https://github.com/YuzhuoMa97/SPAGxECCT/actions/runs/41034171345&quot;,
    &quot;local_repair_not_pushed_by_agent&quot;: true
  },
  &quot;macOS_validated&quot;: false,
  &quot;universal_calibration_proven&quot;: false,
  &quot;biobank_speed_advantage_proven&quot;: false,
  &quot;historical_acceptance_20261029&quot;: {
    &quot;software&quot;: &quot;SPAGxE&quot;,
    &quot;version&quot;: &quot;1.2.0&quot;,
    &quot;date&quot;: &quot;2026-10-29&quot;,
    &quot;passed&quot;: true,
    &quot;methods&quot;: [
      &quot;SPAGxE&quot;,
      &quot;SPAGxE+&quot;,
      &quot;SPAGxEmix&quot;,
      &quot;SPAGxEmix_local&quot;
    ],
    &quot;policy&quot;: &quot;guarded_partial_normal&quot;,
    &quot;production_sources_changed_from_accepted_baseline&quot;: false,
    &quot;Windows_fresh_source_build_and_units&quot;: true,
    &quot;regression_suites_passed&quot;: 17,
    &quot;source_transport&quot;: {
      &quot;passed&quot;: true,
      &quot;core_autocrlf&quot;: true,
      &quot;normal_git_add_files&quot;: 16726,
      &quot;cpp_files_byte_identical_after_archive&quot;: 16618,
      &quot;git_add_force&quot;: false,
      &quot;remote_operations&quot;: false,
      &quot;source_download_sha256&quot;: &quot;b58492a8d4dc8bef28fc13aa8c1d3dc7d0658654d26dd7b961f7f0b83d1f7983&quot;
    },
    &quot;fresh_build_seconds&quot;: 220.80451150000002,
    &quot;current_partial_baseline_fields&quot;: 64960,
    &quot;current_partial_baseline_max_difference&quot;: 0,
    &quot;native_local_preparation_commands&quot;: 4,
    &quot;text_packed_local_results_identical&quot;: true,
    &quot;source_bundle_tutorial_results_identical&quot;: 45,
    &quot;binary_sha256&quot;: &quot;e8c970c68fbb9b901d23535dd692ac22b03d88ae556e705f4a22763bb71483b4&quot;,
    &quot;binary_bytes&quot;: 7265792,
    &quot;platform&quot;: &quot;Windows x86-64 Haswell/AVX2&quot;,
    &quot;runtime_R_Python_compiler_required&quot;: false,
    &quot;Linux_macOS_run_locally&quot;: false,
    &quot;remote_Actions_executed&quot;: false,
    &quot;remote_pushed_or_published&quot;: false,
    &quot;inherited_original_R_GRAB_timing_evidence&quot;: &quot;Accepted 2026-10-28 records, linked by exact production-source hashes&quot;,
    &quot;scope&quot;: &quot;Defined implementation/format/runtime checks, not universal calibration or a representative biobank benchmark&quot;,
    &quot;documentation_feature_review&quot;: {
      &quot;date&quot;: &quot;2026-10-29&quot;,
      &quot;guide&quot;: &quot;docs/USER_GUIDE.md&quot;,
      &quot;runnable_groups&quot;: 33,
      &quot;native_calls_per_walkthrough&quot;: 38,
      &quot;canonical_CLI_parameters_covered&quot;: 53,
      &quot;source_Windows_and_Bash_walkthroughs_passed&quot;: true,
      &quot;source_Windows_Bash_files_identical&quot;: 85,
      &quot;production_sources_or_numerical_policy_changed&quot;: false,
      &quot;fresh_build_and_17_suites_above&quot;: &quot;Earlier acceptance retained by exact production-source and build-input identity; not rerun for documentation-only changes&quot;,
      &quot;scope&quot;: &quot;Executable usage examples and representation consistency; not universal calibration or all-platform runtime validation&quot;
    }
  }
}
</code></pre>
</details>
