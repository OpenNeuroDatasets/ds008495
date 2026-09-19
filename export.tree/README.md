# SI-Neural-Computations fMRI Dataset

## Overview

This dataset accompanies:

**Malik, M., Kim, M., Shu, T., Liu, S., & Isik, L. (2026).  
*Bottom-up and generative computations uniquely explain neural responses across the social brain*.**

The study examines the neural computations supporting visual social interaction recognition. Participants viewed videos of animated agents depicting real-life social interactions and completed several functional localizer tasks.

## Participants

The dataset contains 29 participants, labeled `sub-M02` through `sub-M30`. Twenty-five participants were included in the analyses reported in the accompanying manuscript after applying the preregistered exclusion criteria.

Participant demographics, task availability, analysis inclusion, and exclusion reasons are documented in `participants.tsv`.

## Tasks

### Main task (`task-main`)

Participants viewed 50 ten-second videos selected from the PHASE dataset (Netanyahu et al., 2021), which contains procedurally generated animated interactions between two agents. The selected videos depicted friendly, neutral, and adversarial interactions.

Most participants completed 10 runs, with each video presented five times. Participants M15, M19, and M22 completed 8 runs.

### Social interaction perception localizer (`task-sipsts`)

Participants viewed point-light figures either interacting or performing independent actions (Isik et al., 2017). Each participant completed 2 runs.

### Theory of mind localizer (`task-tom`)

Participants completed a false-belief localizer containing belief and photo conditions (Dodell-Feder et al., 2011). Each participant completed 2 runs.

### Physics localizer (`task-physics`)

Participants viewed videos depicting either physical-object motion or social interaction (Fischer et al., 2016). Each participant completed 1 run, except M23, for whom physics-localizer data are unavailable.

The physics localizer was not used in the analyses reported in the accompanying manuscript.

*Note: Participants were instructed to respond on each ToM and physics trial, but missed or mistimed button presses were not treated as task failures when participants were otherwise following the task; response data were not analyzed.*

## Additional behavioral measures

Participant-level post-scan relationship judgments for the 50 main-task PHASE videos are included in each participant's `beh/` directory. The mapping from task-specific stimulus identifiers to the original PHASE filenames is provided in `stimuli/phase_stimulus_id_mapping.tsv`.

Participants also completed the 50-item Autism Spectrum Quotient, but those data are not included in this release.

## MRI acquisition

MRI data were collected on a 3 Tesla Philips Elition RX scanner with a 32-channel head coil.

- T1-weighted anatomical resolution: 1 mm isotropic
- Functional repetition time: 2 s
- Functional voxel size: 3 mm isotropic

Additional acquisition details are provided in the BIDS JSON sidecars and accompanying manuscript.

## Dataset structure

```text
dataset_description.json
participants.tsv
participants.json
task-postscan_events.json
stimuli/
    phase_stimulus_id_mapping.tsv
sub-M02/
    anat/
    func/
    beh/
...
sub-M30/
derivatives/
    fmriprep/
    GLMsingle/
```

## fMRIPrep derivatives

The `derivatives/fmriprep` directory contains a selected subset of outputs generated using fMRIPrep 21.0.2:

- MNI152NLin2009cAsym preprocessed BOLD images
- BOLD JSON sidecars
- MNI152NLin2009cAsym brain masks
- Confounds TSV and JSON files

Native-space functional outputs, anatomical derivatives, HTML reports, and figures are not included.

## GLMsingle derivatives

The `derivatives/GLMsingle` directory contains Type-D HDF5 outputs for the `main`, `sipsts`, and `tom` tasks.

The estimates were generated from fMRIPrep-preprocessed data in MNI152NLin2009cAsym space after 4 mm FWHM spatial smoothing. GLMsingle was run with voxel-wise HRF fitting, GLMdenoise, fractional ridge regression, autoscaling, and conversion to percent BOLD signal.

Physics-localizer GLMsingle outputs are not included.

## Code and model representations

Analysis code and the model & behavioral representations used in the study are available in the companion GitHub repository:

https://github.com/manasimalik/SI-Neural-Computations

## Ethics

The study received ethical approval from the Johns Hopkins Medicine Institutional Review Board and complied with all relevant ethical regulations. All participants provided written informed consent.

## Citation

Malik, M., Kim, M., Shu, T., Liu, S., & Isik, L. (2026).  
*Bottom-up and generative computations uniquely explain neural responses across the social brain*.  
https://doi.org/10.64898/2026.02.20.707082

Preregistration: https://osf.io/hq3r7

## References

Dodell-Feder, D., Koster-Hale, J., Bedny, M., & Saxe, R. (2011). fMRI item analysis in a theory of mind task. *NeuroImage, 55*(2), 705–712. https://doi.org/10.1016/j.neuroimage.2010.12.040

Fischer, J., Mikhael, J. G., Tenenbaum, J. B., & Kanwisher, N. (2016). Functional neuroanatomy of intuitive physical inference. *Proceedings of the National Academy of Sciences, 113*(34), E5072–E5081. https://doi.org/10.1073/pnas.1610344113

Isik, L., Koldewyn, K., Beeler, D., & Kanwisher, N. (2017). Perceiving social interactions in the posterior superior temporal sulcus. *Proceedings of the National Academy of Sciences, 114*(43), E9145–E9152. https://doi.org/10.1073/pnas.1714471114

Netanyahu, A., Shu, T., Katz, B., Barbu, A., & Tenenbaum, J. B. (2021). PHASE: PHysically-grounded Abstract Social Events for Machine Social Perception. *Proceedings of the AAAI Conference on Artificial Intelligence, 35*(1), 845–853. https://doi.org/10.1609/aaai.v35i1.16167

