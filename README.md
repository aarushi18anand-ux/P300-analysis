# P300-analysis
Adding projects using MNE to analyse P300 data
# **TASK 1** Auditory oddball P300 (work in progress) P300analysis.ipynb

**Status: Work in Progress. Preprocessing and a data-quality audit are done; the P300 analysis is not.** I am using this repo to document what I have learned so far.

## Goal
Test whether the brain response 300-600 ms after a rare tone is larger than after a frequent tone (P300), using open EEG data.

## Data
"EEG data from an auditory oddball task" (Delorme, 2020), OpenNeuro ds003061, CC0 licence. 13 participants, 64 scalp electrodes, 256 Hz, eyes closed. Participants pressed a key for a rare 1000 Hz tone among frequent 500 Hz tones and noise bursts. According to the dataset README, recordings were made in India. The data are not included in this repo.

## Decisions made before looking at any ERP results
- Use run 2 for every participant
- Measure at electrode Pz, 300-600 ms
- Reject any window with a spike over 100 microvolts
- Keep a participant only if at least 40 clean rare-tone windows remain

## What is done
1. Loaded the recordings; removed a temperature sensor that MNE had mislabelled as an EEG channel
2. Band-pass filtered 0.1-30 Hz and re-referenced to the average of all electrodes
3. Cut 1-second windows around each tone (0.2 s before to 0.8 s after) with baseline correction
4. Audited window rejection per participant

## Finding so far
On the first pass, only **7 of 13 participants** kept at least 40 rare-tone windows. The rejection log showed that a few persistently noisy electrodes (for example P7 and TP8 in one participant) caused most rejections. This is a data-quality problem, not a result. My planned fix, which I have not yet verified, is to interpolate persistently bad electrodes before epoching. This change was decided before examining any ERP amplitudes.

## Not done yet
Averaging into ERPs, the rare-vs-frequent comparison, statistics and figures. I paused to learn the methods more carefully.

## Limitations
Small sample; no ICA for eye or muscle artefacts; average reference rather than mastoids; exclusion rules still being finalised.


# **TASK 2** P300 Auditory Oddball EEG Analysis for **P300(2)** p300(2).ipynb

A beginner project for learning EEG analysis with Python and MNE. The notebook explores EEG recorded during an auditory oddball task.

# Project question

How does the EEG response to a rare oddball sound differ from the response to a frequent standard sound?

The project looks for a possible P300 response. The current analysis is exploratory; it does not yet establish a group-level result.

## Dataset

This project uses OpenNeuro dataset ds003061, “EEG data from an auditory oddball task.”

The dataset includes 13 participants and three runs per participant. Sounds include:

Standard: frequent 500 Hz tone

Oddball: rare 1000 Hz tone; participants were asked to respond

Distractor: white noise

The EEG was recorded with a BioSemi system and resampled to 256 Hz. The dataset is released under a CC0 license.

## Current notebook status

The notebook currently explores sub-001, run 1:

Keeps the scalp EEG channels and removes non-EEG channels.

Filters the signal from 0.1 to 30 Hz.

Uses an average EEG reference.

Cuts epochs from 0.2 seconds before to 0.8 seconds after an event.

Uses the pre-sound interval as the baseline.

Compares standard sounds with oddball_with_reponse events.

The dataset spells that label oddball_with_reponse. The current comparison includes correctly answered oddballs only; oddball sounds without a recorded response are not included yet.

## Next steps

Include both answered and unanswered oddball sounds in the main comparison.

Check data quality and epoch rejection across runs.

Extend the analysis from one run to all participants and runs.

Compare the group response across scalp sensors.

## Citation

Delorme, A. (2022). EEG data from an auditory oddball task [Dataset]. OpenNeuro, ds003061. https://doi.org/10.18112/openneuro.ds003061.v1.1.2
