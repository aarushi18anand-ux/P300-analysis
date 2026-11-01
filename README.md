# P300-analysis
Adding projects using MNE to analyse P300 data
P300 Auditory Oddball EEG Analysis

A beginner project for learning EEG analysis with Python and MNE. The notebook explores EEG recorded during an auditory oddball task.

Project question

How does the EEG response to a rare oddball sound differ from the response to a frequent standard sound?

The project looks for a possible P300 response. The current analysis is exploratory; it does not yet establish a group-level result.

Dataset

This project uses OpenNeuro dataset ds003061, “EEG data from an auditory oddball task.”

The dataset includes 13 participants and three runs per participant. Sounds include:

Standard: frequent 500 Hz tone

Oddball: rare 1000 Hz tone; participants were asked to respond

Distractor: white noise

The EEG was recorded with a BioSemi system and resampled to 256 Hz. The dataset is released under a CC0 license.

Current notebook status

The notebook currently explores sub-001, run 1:

Keeps the scalp EEG channels and removes non-EEG channels.

Filters the signal from 0.1 to 30 Hz.

Uses an average EEG reference.

Cuts epochs from 0.2 seconds before to 0.8 seconds after an event.

Uses the pre-sound interval as the baseline.

Compares standard sounds with oddball_with_reponse events.

The dataset spells that label oddball_with_reponse. The current comparison includes correctly answered oddballs only; oddball sounds without a recorded response are not included yet.

Next steps

Include both answered and unanswered oddball sounds in the main comparison.

Check data quality and epoch rejection across runs.

Extend the analysis from one run to all participants and runs.

Compare the group response across scalp sensors.

Citation

Delorme, A. (2022). EEG data from an auditory oddball task [Dataset]. OpenNeuro, ds003061. https://doi.org/10.18112/openneuro.ds003061.v1.1.2
