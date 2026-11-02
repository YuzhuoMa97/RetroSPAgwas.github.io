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

**Development source, checked 2 November 2026.** SPAGxE 1.2.0 is available on [develop](https://github.com/YuzhuoMa97/SPAGxECCT/tree/develop). [Hosted checks for 2a14885](https://github.com/YuzhuoMa97/SPAGxECCT/actions/runs/41438512290) passed on Windows, Ubuntu and macOS, including source builds, numerical units, regressions and source/extracted-bundle tutorials. The C++ release tag and runtime assets are not yet published; macOS currently uses a source build. See the [validation record](/RetroSPAgwas.github.io/docs/spagxe_cpp/validation.html) and [development status](/RetroSPAgwas.github.io/docs/spagxe_cpp/development_status.html) for the exact revision, scope and installation routes. Later commits require their own checks.

<a id="current-candidate"></a>
<a id="current-repaired-candidate"></a>
<a id="remaining-limits"></a>

# Validation records and interpretation {#validation-records-and-interpretation}

SPAGxE uses the documented paper-oriented statistical policy with guarded
partial-normal CGF acceleration. The checked public commit and historical
local implementation comparisons are recorded separately. Read
[release scope](/RetroSPAgwas.github.io/docs/spagxe_cpp/release_scope.html) and
[maintenance notes](/RetroSPAgwas.github.io/docs/spagxe_cpp/maintenance.html).

## Latest checked public source {#latest-checked-public-source}

Develop commit `2a14885bd9ebc1bcf51910db852a38e212793225` passed the
[2 November 2026 hosted workflow](https://github.com/YuzhuoMa97/SPAGxECCT/actions/runs/41438512290).
All Windows, Ubuntu and macOS jobs completed their source build, numerical
unit, reader/regression and source/extracted-runtime tutorial checks.
The output comparison checks completed successfully. Check Actions for
later commits instead of assuming that this record covers them.

This verifies the tested source and CI runner routes. It does not publish a
macOS binary or guarantee compatibility with all OS/CPU/compiler versions.
At this review there was no C++ Release with public runtime attachments;
users can build the complete develop source. A later Release must identify
its own source commit, platform packages and checksums.

## Portable reference calculations {#portable-reference-calculations}

Earlier macOS failures exposed test references that assumed extra native
long-double precision/range or used cancellation-prone linear probabilities.
The corrected oracles use exact conditional-HWE fixtures, multiprecision
calculations and independent reference identities. The original accuracy
criteria remain. Production analysis formulas were not changed.

The final log-probability suite has 54 cases: the original 53 and one focused
normal-reference underflow-band regression. The CGF suite retains all 28
cases and the original identity grid. There are no newly added skips or
tolerance relaxations. Existing guards for 13 wider-long-double CGF
measurements remain; these measurements do not run on hosts without the
required native precision/range. The successful hosted run is not presented
as evidence that they ran on such hosts.

Native floating-point diagnostics remain visible in test output. Generation
scripts and HWE fixtures are included in cpp/tests/. A portable oracle
correction is distinct from a change to the statistical model.

## Earlier local implementation checks {#earlier-local-implementation-checks}

- Fresh Windows build and numerical units passed.
- Seventeen local regression suites passed. Two reference invocations were
  rerun after correcting a private driver path-escaping error; their original
  diagnostics were retained.
- Previous/current full walkthroughs produced 85 byte-identical files and
  145,985 identical numeric fields.
- Scanner, sample-mapping, file-resource, null-model, outlier and CGF checks
  supplement those application regressions.
- Linux local build, numerical units, regression routes, complete walkthrough
  and installed-prefix execution passed, as recorded in ACCEPTANCE.json.

These are earlier local records, not counts newly extracted from the latest
hosted run. Earlier public CI results are retained in the machine-readable
history instead of replacing them with the newer successful result.

Developer scripts regenerate summaries under cpp/results/. Reference tests
may use Python or R; analysis and bundled tutorials do not require them.
Matching implementations is reproducibility evidence. Independent reference
checks and population-level calibration answer different questions.

## Scope and remaining limits {#scope-and-remaining-limits}

Binary compatibility depends on OS, CPU and runtime libraries. No finite test
set guarantees every input, extreme tail, historical default P value or
biobank-scale speed claim. The partial-normal diagnostic threshold is not a
uniform bound on P-value error.

Preserved R code keeps its original dependency chain. The original full-CGF
R baseline and accelerated default need not give identical P values in every
case. Historical results are not relabeled as newly executed tests.

## Current acceptance summary {#current-acceptance-summary}

This record separates the checked public source from earlier local comparisons and historical hosted results.

<details><summary>Read the acceptance JSON</summary>

<pre><code>{
  &quot;software&quot;: &quot;SPAGxE&quot;,
  &quot;version&quot;: &quot;1.2.0&quot;,
  &quot;date&quot;: &quot;2026-11-02&quot;,
  &quot;scope&quot;: &quot;Published develop source; Windows/Ubuntu/macOS hosted CI passed for the pinned commit; final C++ tag/assets pending&quot;,
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
  &quot;macOS_validated&quot;: true,
  &quot;maintenance_candidate_hosted_CI_executed&quot;: true,
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
  },
  &quot;historical_local_validation_date&quot;: &quot;2026-11-01&quot;,
  &quot;reviewed_public_commit&quot;: &quot;2a14885bd9ebc1bcf51910db852a38e212793225&quot;,
  &quot;hosted_CI&quot;: {
    &quot;commit&quot;: &quot;2a14885bd9ebc1bcf51910db852a38e212793225&quot;,
    &quot;run&quot;: &quot;https://github.com/YuzhuoMa97/SPAGxECCT/actions/runs/41438512290&quot;,
    &quot;Windows&quot;: &quot;success&quot;,
    &quot;Ubuntu&quot;: &quot;success&quot;,
    &quot;macOS&quot;: &quot;success&quot;,
    &quot;overall&quot;: &quot;success&quot;
  },
  &quot;website_deployed_commit&quot;: &quot;d389e486035d94c1aceb6acc23acf52a6a10f505&quot;,
  &quot;post_publication_documentation_patch_changes_mathematics&quot;: false,
  &quot;portable_test_reference_update&quot;: {
    &quot;analysis_code_changed&quot;: false,
    &quot;original_accuracy_criteria_retained&quot;: true,
    &quot;new_test_cases_skipped&quot;: false,
    &quot;new_tolerance_relaxation&quot;: false,
    &quot;Windows_local_affected_unit_targets_passed&quot;: true,
    &quot;log_probability_cases&quot;: 54,
    &quot;CGF_cases&quot;: 28,
    &quot;new_hosted_CI_executed&quot;: true,
    &quot;actual_MacOS_rerun_passed&quot;: true,
    &quot;existing_wide_long_double_measurement_guards&quot;: 13,
    &quot;existing_guards_changed&quot;: false,
    &quot;all_wide_measurements_claimed_to_run_on_binary64&quot;: false
  },
  &quot;historical_hosted_CI&quot;: [
    {
      &quot;commit&quot;: &quot;d90fb4c45849757c816c5d1ba5d191911443e83c&quot;,
      &quot;run&quot;: &quot;https://github.com/YuzhuoMa97/SPAGxECCT/actions/runs/41416750904&quot;,
      &quot;Windows&quot;: &quot;success&quot;,
      &quot;Ubuntu&quot;: &quot;success&quot;,
      &quot;macOS&quot;: &quot;failure&quot;,
      &quot;overall&quot;: &quot;failure&quot;
    }
  ],
  &quot;macOS_validation_scope&quot;: &quot;Source build, numerical unit target, reader/regression and source/extracted-runtime tutorial checks on the macos-latest CI job for the recorded commit; no macOS precompiled Release&quot;,
  &quot;documentation_status_update&quot;: {
    &quot;base_commit&quot;: &quot;2a14885bd9ebc1bcf51910db852a38e212793225&quot;,
    &quot;analysis_code_changed&quot;: false,
    &quot;new_documentation_commit_CI_required&quot;: true,
    &quot;historical_local_counts_reused_as_new_hosted_counts&quot;: false
  }
}</code></pre>

</details>
