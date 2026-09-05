# CIV5802 Case Study 2: J19–J20 Two-Intersection Simulation

[中文](README.md) | **English**

This SUMO course project models two adjacent intersections, J19 and J20, in Penang, Malaysia. It documents network construction, a direction correction, and signal-timing comparisons for learning and possible teaching use. **Traffic keeps to the left**, so lane connections, turns, and signal movements must follow left-hand traffic rules.

> Current status: this is a private backup, not a fully verified teaching release. None of the four stored output sets is complete enough for final analysis.

![Map reference for the J19–J20 study area](assets/J19_J20_map_reference.png)

*Google Maps screenshot supplied by the author for location reference only. It does not replace the traffic survey source. The original attribution remains visible; reuse requirements must be checked before public release.*

## Assignment Scope

According to the lecturer's instructions and the author's later confirmation, the task is to select two intersections, develop a SUMO model from the supplied information, run the simulation, identify critical movements at each intersection and across the network, and propose data-supported measures to reduce delay.

Simulation of the proposed solution was not mandatory. This project additionally creates AM/PM baseline and candidate signal-timing scenarios. These four scenarios are a project choice, not a guaranteed formula for a particular grade. Future students must follow the requirements for their own course offering.

Traffic survey information comes from the publicly accessible ADB report [*Penang Smart Mobility Micro-Simulation Model Development: Final Report*](https://events.development.asia/materials/20240408/penang-smart-mobility-micro-simulation-model-development-final-report). The course-extracted PDF is not included or redistributed. Obtain the complete report from the official page and follow its copyright and attribution terms.

## Project Process

The author built the baseline → organized AM/PM demand → corrected the invalid J46-to-J20 direction while retaining J20-to-J46 → manually tested a minimal corrected model → expanded it into four scenarios → backed it up on GitHub.

See the [project record](sandbox03/J19_J20_project_record.txt). Historical summaries do not prove that the current XML outputs are complete; short SUMO-GUI runs may overwrite files with the same names.

## Files and Running the Model

Models are stored in [sandbox03/SUMO_case_study_2_MIAO](sandbox03/SUMO_case_study_2_MIAO/):

| Scenario folder | Purpose |
| --- | --- |
| J19_J20_AM_baseline | AM baseline |
| J19_J20_PM_baseline | PM baseline |
| J19_J20_AM_signal_optimization | AM candidate timing |
| J19_J20_PM_signal_optimization | The same candidate timing tested under PM demand |

Copy a scenario folder before testing, then open its matching `.sumocfg` in SUMO-GUI. The historical environment used SUMO 1.27.1. A run overwrites files in `outputs/`, so back them up first. The PM candidate is a transfer test, not a PM-specific optimum.

Complete backup: [2026-09-04 snapshot](sandbox03_snapshot_2026-09-04.zip). The course PDF, final report document, and complete post-processing scripts are not included.

## Read Before Using the Results

- **Time:** demand runs from 0 to 3600 s and the simulation ends at 4200 s. The final 600 s is a clearance period, not a warm-up. Historical queue averages included this period; changing the analysis window requires recalculation.
- **Demand:** PCU values are represented by SUMO's default passenger vehicle as a simplified equivalent flow, not a reconstructed mixed-vehicle fleet. Some multi-intersection flows were derived from turning proportions and still require page-level source tracing.
- **Metrics:** `timeLoss`, `waitingTime`, and `departDelay` are different. Route-level delay cannot automatically be attributed to one intersection movement. Vehicles scheduled within the demand period may enter after 3600 s because of insertion delay.
- **Current outputs:** when checked on 2026-09-04, AM baseline had no valid queue time steps. AM candidate, PM baseline, and PM candidate ended at 345, 314, and 565 s respectively. These files cannot support complete simulation conclusions.

See the official SUMO documentation for [TripInfo](https://sumo.dlr.de/docs/Simulation/Output/TripInfo.html) and [QueueOutput](https://sumo.dlr.de/docs/Simulation/Output/QueueOutput.html).

## Before Public Release

Rerun and preserve complete outputs; use one documented analysis window; add data traceability and reproducible post-processing; remove invalid files and personal information; and verify rights for the map and all third-party material. The author will perform the final check and make the repository public manually.

## Disclaimer

This package is based on a baseline created by the author and was organized and summarized with AI assistance. It is shared free of charge for personal learning and discussion. It is not official material from the university, lecturer, or SUMO project and carries no guarantee of model or result accuracy. Users must verify the work independently, follow academic-integrity requirements, and must not use it directly for real-world signal deployment. Free sharing does not change third-party rights; reuse remains subject to the applicable permissions and final repository license.
