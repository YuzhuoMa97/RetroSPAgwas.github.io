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

**Maintenance candidate.** This page accompanies local SPAGxE 1.2.0 maintenance source that has not yet been pushed or tagged. The [public baseline](https://github.com/YuzhuoMa97/SPAGxECCT/commit/c7c11590efbd10504115cd0ad8dbb9c6ca2634e1) passed hosted Windows and Ubuntu checks; its macOS build failed. Those hosted results do not validate this new candidate. Read the [candidate validation record](/RetroSPAgwas.github.io/docs/spagxe_cpp/validation.html) and [development status](/RetroSPAgwas.github.io/docs/spagxe_cpp/development_status.html) for the current evidence and download boundaries.


<a id="current-repaired-candidate"></a>

# Validation records and interpretation {#validation-records-and-interpretation}

This maintenance candidate changes production implementation structure while
preserving the documented statistical policy. The public source baseline is
recorded separately from the not-yet-pushed local maintenance source.
Read [release scope](/RetroSPAgwas.github.io/docs/spagxe_cpp/release_scope.html) and
[maintenance notes](/RetroSPAgwas.github.io/docs/spagxe_cpp/maintenance.html).

## Current candidate {#current-candidate}

- Fresh Windows build and numerical units passed.
- Seventeen regression suites passed. An initial private driver path-escaping
  defect affected two reference invocations; only those two were rerun after
  fixing the driver, with the original diagnostics retained.
- Previous/current full walkthroughs produced 85 byte-identical files and
  145,985 identical numeric fields.
- Focused scanner, sample mapping, file-resource, null-model specification,
  outlier and CGF checks supplement the full application regressions.
- Linux results are recorded explicitly in ACCEPTANCE.json when complete.

Developer scripts regenerate their summaries under cpp/results/. Reference
tests may use Python or R; analysis and bundled tutorials do not require them.
Matching old/current implementations is reproducibility evidence. Independent
scalar/R/high-precision checks and population-level calibration answer
different questions.

## Remaining limits {#remaining-limits}

macOS remains unvalidated. The current maintenance source has not yet been
pushed or checked by hosted CI. Binary compatibility depends on OS, CPU and
runtime libraries; no finite test set guarantees every input, extreme tail,
historical default P value or biobank-scale speed claim.

Preserved R code keeps its original dependency chain. The original full-CGF
R baseline and the accelerated default need not have identical P values in
every case. Historical results are not relabeled as new tests.

## Current acceptance summary {#current-acceptance-summary}

The record below is generated from this local candidate. Historical evidence retains its own date and scope; a previous hosted job is not a new candidate run.

<details><summary>Read the candidate acceptance JSON</summary>

<pre><code>{
  &quot;software&quot;: &quot;SPAGxE&quot;,
  &quot;version&quot;: &quot;1.2.0&quot;,
  &quot;date&quot;: &quot;2026-11-01&quot;,
  &quot;scope&quot;: &quot;Local maintenance candidate; hosted CI and final tag/assets pending&quot;,
  &quot;public_baseline_commit&quot;: &quot;c7c11590efbd10504115cd0ad8dbb9c6ca2634e1&quot;,
  &quot;statistical_policy&quot;: &quot;paper weights; guarded partial-normal CGF&quot;,
  &quot;methods&quot;: [
    &quot;SPAGxE&quot;,
    &quot;SPAGxE+&quot;,
    &quot;SPAGxEmix&quot;,
    &quot;SPAGxEmix_local&quot;
  ],
  &quot;production_sources_changed&quot;: true,
  &quot;mathematical_definitions_changed&quot;: false,
  &quot;Windows_fresh_build_and_units&quot;: true,
  &quot;Windows_regression_suites&quot;: 17,
  &quot;Windows_previous_current_comparison&quot;: {
    &quot;passed&quot;: true,
    &quot;files&quot;: 85,
    &quot;byte_differences&quot;: [],
    &quot;numeric_fields&quot;: 145985,
    &quot;maximum_numeric_delta&quot;: 0.0,
    &quot;non_numeric_differences&quot;: [],
    &quot;before_sha256&quot;: &quot;11032005f42cd97b2bfb55bcfe12f63989f2b4fa54743fe942368379f3ddad6c&quot;,
    &quot;after_sha256&quot;: &quot;21d4497bc8f7e6612233d38abdecfff97be48c329519e63bef65270298522d1c&quot;
  },
  &quot;focused_checks&quot;: {
    &quot;CGF_source_checks&quot;: 54,
    &quot;CGF_module_assembly_equal&quot;: true,
    &quot;tokenizer_cases&quot;: 5307078,
    &quot;subject_mapping_cases&quot;: 910,
    &quot;subject_filter_cases&quot;: 1048,
    &quot;mmap_success_cycles&quot;: 2000,
    &quot;mmap_failure_cases&quot;: 400,
    &quot;outlier_cases&quot;: 550,
    &quot;null_spec_cases&quot;: 80
  },
  &quot;Linux_locally_validated&quot;: true,
  &quot;macOS_validated&quot;: false,
  &quot;maintenance_candidate_hosted_CI_executed&quot;: false,
  &quot;public_CXX_release_published&quot;: false,
  &quot;universal_calibration_proven&quot;: false,
  &quot;biobank_speed_advantage_proven&quot;: false,
  &quot;original_R_sources_preserved&quot;: true,
  &quot;default_x86_binary_baseline&quot;: &quot;Haswell/AVX2&quot;,
  &quot;Linux_validation_summary&quot;: {
    &quot;passed&quot;: true,
    &quot;complete&quot;: true,
    &quot;stages&quot;: [
      {
        &quot;name&quot;: &quot;source_build&quot;,
        &quot;returncode&quot;: 0,
        &quot;seconds&quot;: 168.22417330900004
      },
      {
        &quot;name&quot;: &quot;numerical_units&quot;,
        &quot;returncode&quot;: 0,
        &quot;seconds&quot;: 56.64930980999998
      },
      {
        &quot;name&quot;: &quot;version&quot;,
        &quot;returncode&quot;: 0,
        &quot;seconds&quot;: 0.005693000000007942
      },
      {
        &quot;name&quot;: &quot;cli&quot;,
        &quot;returncode&quot;: 0,
        &quot;seconds&quot;: 0.1413400000000138
      },
      {
        &quot;name&quot;: &quot;single_policy&quot;,
        &quot;returncode&quot;: 0,
        &quot;seconds&quot;: 0.1128869990000112
      },
      {
        &quot;name&quot;: &quot;scope&quot;,
        &quot;returncode&quot;: 0,
        &quot;seconds&quot;: 0.09996769999997923
      },
      {
        &quot;name&quot;: &quot;af_convergence&quot;,
        &quot;returncode&quot;: 0,
        &quot;seconds&quot;: 0.07109789999998384
      },
      {
        &quot;name&quot;: &quot;af_utility&quot;,
        &quot;returncode&quot;: 0,
        &quot;seconds&quot;: 0.07514560000004167
      },
      {
        &quot;name&quot;: &quot;observed_mac&quot;,
        &quot;returncode&quot;: 0,
        &quot;seconds&quot;: 0.1787191999999891
      },
      {
        &quot;name&quot;: &quot;integration&quot;,
        &quot;returncode&quot;: 0,
        &quot;seconds&quot;: 2.443352294999954
      },
      {
        &quot;name&quot;: &quot;local_oracle&quot;,
        &quot;returncode&quot;: 0,
        &quot;seconds&quot;: 0.23177479899999298
      },
      {
        &quot;name&quot;: &quot;local_io&quot;,
        &quot;returncode&quot;: 0,
        &quot;seconds&quot;: 0.3182480000000396
      },
      {
        &quot;name&quot;: &quot;local_bgen&quot;,
        &quot;returncode&quot;: 0,
        &quot;seconds&quot;: 0.5378758990000279
      },
      {
        &quot;name&quot;: &quot;local_absolute&quot;,
        &quot;returncode&quot;: 0,
        &quot;seconds&quot;: 0.06712529899999709
      },
      {
        &quot;name&quot;: &quot;local_pack&quot;,
        &quot;returncode&quot;: 0,
        &quot;seconds&quot;: 0.09384370000003628
      },
      {
        &quot;name&quot;: &quot;local_unicode&quot;,
        &quot;returncode&quot;: 0,
        &quot;seconds&quot;: 0.2473693999999682
      },
      {
        &quot;name&quot;: &quot;cct&quot;,
        &quot;returncode&quot;: 0,
        &quot;seconds&quot;: 0.07558289999997214
      },
      {
        &quot;name&quot;: &quot;source_tutorials&quot;,
        &quot;returncode&quot;: 0,
        &quot;seconds&quot;: 0.5542821989999993
      },
      {
        &quot;name&quot;: &quot;full_walkthrough&quot;,
        &quot;returncode&quot;: 0,
        &quot;seconds&quot;: 1.6558226960000297
      },
      {
        &quot;name&quot;: &quot;install_prefix&quot;,
        &quot;returncode&quot;: 0,
        &quot;seconds&quot;: 0.5406787990000339
      },
      {
        &quot;name&quot;: &quot;installed_version&quot;,
        &quot;returncode&quot;: 0,
        &quot;seconds&quot;: 0.00478669999995418
      },
      {
        &quot;name&quot;: &quot;baseline_full_walkthrough&quot;,
        &quot;returncode&quot;: 0,
        &quot;seconds&quot;: 1.6388363959999879
      },
      {
        &quot;name&quot;: &quot;baseline_file_equivalence&quot;,
        &quot;returncode&quot;: 0
      }
    ],
    &quot;binary_sha256&quot;: &quot;c1bedb883d85f8b5aa9e072fade6f63df4e61e8e44c18548cc3ed42974f60b6c&quot;
  }
}</code></pre>

</details>
