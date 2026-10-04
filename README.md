# Paired Outcome Diagnostics for Residual Robot-Policy Refinement: An Empirical Study

Curated reproducibility dataset for the paired-outcome-diagnostics repository, version 1.0.0. This local candidate has not been uploaded or published. Project-produced data and metadata are licensed under CC BY 4.0; see LICENSE and CITATION.cff.

## Scope and contents

This package contains frozen paired-count/statistical tables, selected secondary payloads, recorded bootstrap indices and identities, final-blind noise/state bindings, and documented configuration/software records. It supports inspection of reported results and count-level checks. It is not a complete simulator/training environment or an executable historical-analysis distribution.

The package excludes model checkpoints, third-party-derived training/evaluation code, historical statistics.py, raw episode archives, binary simulator states, third-party task assets, and the R4A secondary payload pending a focused metadata review. No new experiments or inferential statistics were run to build it. Reported historical model hashes do not establish that model binaries are present.

## Paired outcomes

The first letter is the base outcome and the second is the refined outcome: P means success, F means failure. PP is preservation, PF corruption, FP rescue, FF unresolved failure. Thus N=PP+PF+FP+FF, base successes=PP+PF, refined successes=PP+FP and change in success rate=(FP-PF)/N. Preservation is PP/(PP+PF), rescue is FP/(FP+FF); a zero denominator makes that conditional rate undefined. Reused states/checkpoints/scales are not independent replications.

## File-to-paper map

| Paper / Supplement | Files | Role and limit |
|---|---|---|
| Definitions; Figure 1; S1–S2 | This README; statistics/ | Figure 1 is conceptual; recorded DEV resampling config/indices support provenance, not executable bootstrap replay by themselves |
| Longitudinal Peg; S1–S2 | data/PEG_DEV.csv; data/R1B_MULTISEED_PAIRWISE.csv | Development set: 32 physical initial states, two repeats; three existing training seeds, five checkpoints; conditional cluster bootstrap outputs |
| Mature historical Peg; S3 | data/PEG_MATURE200.csv | Historical mature setting: 100 physical states with two repeats, 200 episodes, base 156/200; keep separate from both new-set and sealed evaluations |
| New-evaluation-set longitudinal Peg; Figure 2; S4 | data/PEG_A.csv | Study A, 200 states; existing seeds; base 141/200; archived descriptive/statistical columns |
| Authority; Figure 3; S5 | data/AUTHORITY.csv; figure_data/figure3_residual_authority_data.csv | Discovery seed 2 and confirmation seeds 1/3 share one 100-state set, base 68/100; six authority scales; Figure 3 is its archived display subset |
| StackCube boundary; Figure 4; S6 | data/STACK_LONG.csv | BeT base, 200 states, base 150/200; single-control transition budgets differ from Peg action blocks |
| Final sealed endpoint; S7 | final_blind/ | FINAL_BLIND_PEG_V1: distinct sealed 200-state set, base 141/200, mature 500032 checkpoints; existing seeds, not new training replications |
| Policy Decorator; S8 | secondary/R2_payload.csv | Bounded local comparison, not longer-budget upstream replication |
| Local DICE; S9 | secondary/R4B_payload.csv; secondary/R4B_CONTRASTS_payload.csv; secondary/R9_C_payload.csv | Selected local variant results; R4A remains in the scientific Supplement but its file is excluded here |
| Secondary diagnostics; S10 | secondary/R5_payload.csv, R6A_payload.csv, R6B_payload.csv, R7_payload.csv | Existing diagnostic payloads; retain the Supplement's bounded interpretation |
| Unevaluated settings; S11 | No task assets supplied | No implication of zero success or scientific failure for tasks never evaluated |
| Configuration/provenance; S12 | configuration/; final_blind/FROZEN_CONFIG.json | Three Peg and three StackCube seed configs, software freeze, final evaluation config; source-level historical evidence, not exact runtime replay |

Figure 2 CSV bytes are exactly data/PEG_A.csv; Figure 4 CSV bytes are exactly data/STACK_LONG.csv. The figure_data/figure2_data_location.json and figure4_data_location.json descriptors identify these files and their hashes without duplicating the CSVs. Figure 3 retains the archived display subset; the full grid is data/AUTHORITY.csv. Do not merge PEG_A and FINAL_BLIND_PEG_V1 because both happen to have base 141/200.

## Reading and checking the outputs

CSV files can be read by ordinary CSV readers. Core CSVs retain archived counts, rates and intervals without recalculation. Their PP/PF/FP/FF columns permit direct checks of counts and success-rate identities. final_blind/summary.json and paired_statistics.csv retain the recorded endpoint results. statistics/bootstrap_cluster_identity.json and bootstrap_cluster_indices.npy retain the cluster order and recorded 10000-by-32 draws; the raw paired DEV episode matrix is not supplied, so these files alone cannot regenerate the bootstrap confidence intervals.

The archived statistics configuration records Python 3.10.12, NumPy 1.23.5 and SciPy 1.15.3. These are historical analysis versions, not a freshly tested environment requirement. configuration/environment_freeze.txt records the historical environment (including ManiSkill2 0.5.3 and PyTorch 2.1.2), not a validated installation lockfile. Read NumPy arrays with allow_pickle=False. No executable analysis script is supplied, and no command is advertised as reproducing all statistics.

## Sanitized provenance copies

Selected CSV provenance cells and JSON configurations/manifests replace the private server/project root with ARCHIVED_ID: or ARCHIVED_PROJECT_ID:. These labels retain the archive artifact suffix; they are not package paths and do not promise that the referenced binaries or scripts are available. The machine-specific GPU UUID in each StackCube config is replaced with DEVICE_UUID_REMOVED; device model assumptions are not added. Scientific numbers, seed/state bindings, checkpoints, hashes and other configuration values are preserved. Original-file hashes remain original-file identities and will differ from the hashes of sanitized copies.

FILE_MANIFEST.json records original and candidate hashes without disclosing private source locations. PEG_SEAL_METADATA_EXTRACT.json remains a source-identified excerpt, not an independent historical seal certificate. It does not establish missing first-access timestamps.

## Reproducibility limits and release status

Neither configurations nor release identities recover every historical optimizer, replay-buffer, RNG or simulator state. Undocumented Adam settings are not inferred. The data support a bounded audit of reported outcomes, not exact replay of all historical execution or upstream papers. This is a data-only release. No executable analysis, training or evaluation code is supplied. Project-produced data and metadata are licensed under CC BY 4.0. Original rights in referenced third-party software are not granted by this dataset license. No DOI or repository URL has been assigned to this local candidate. This repository contains the frozen curated data package supporting the manuscript. The released files were validated against the publication package and reported results using the supplied publication validation records. For a subset of curated artifacts, complete independent reconstruction of the historical upstream file lineage was not available; this does not affect the frozen reported values or the scope of the released dataset.

## Main tables

Table 1 describes the distinct experiment settings documented above. Table 2 selects paired outcomes from data/PEG_A.csv, data/AUTHORITY.csv, data/STACK_LONG.csv and final_blind/paired_statistics.csv; the full tables remain available in those files.
