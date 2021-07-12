# Neural Working Memory Mechanisms

## Purpose of repository
This repository contains the code for stimulating a delayed retro-cued working memory task (WM) described by Wolff and colleagues (2017) using biologically plausible spiking neuron models. All models are based on the activity-silent model of WM developed by Pals and colleagues (2020) implementing a calcium-based short-term synaptic plasticity (STSP) mechanism and an adjustment of this original model (Wijs, 2020; Knol, 2020; source code can be found [here](https://github.com/ChielWijs/Dynamic-Coding-in-Working-Memory)) but have been modified to incorporate activity-based mechanisms instead. Models were developed in Nengo 2.8.0. The repository contains the following models: 

- Persistent activity model of WM (exp2_PA.py), retaining information in the pattern of spikes by means of sustained neural activation. STSP mechanism was replaced by a simple recurrent activity connection.
- Generic reactiation model of WM (exp2_GR.py), retaining information my means of an activity-silent, calcium-mediated STSP mechanism (based on Pals et al., 2020; also see Mongillo et al., 2008). The population storing information is reactivated with generic current on the basis of a 10 Hz rhythm to maintain the pattern of synaptic facilitation over time and to evoke sustained neural activation. 
- Content-specific reactivation model of WM (ex2_CSR.py). This model also retains information on the basis of STSP, but the reactivation current is not generic, as in the GR model, but stimulus-specific. In addition, the model receives reactivation pulses in line with a 30 Hz rhythm.
- Integrated model of WM (exp2_integrated.py). Contains a model that retains unattended information in activity-silent STSP-mediated states (Knol, 2020; Wijs, 2020) amd attended information in activity-based states (as in CSR model). Additionally, the model contains a clearance mechanism (based on the GR mechanism, which has been found to distort rather than maintain information) to clear information from WM after they have become task-irrelevant.

## Setup
- Download and install conda from [this website](https://docs.anaconda.com/anaconda/install/index.html).

- Create conda environment from the requirement.txt file as described [here](https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#building-identical-conda-environments). 

- Run simulation 1 or 2 in either file to generate data for a respective model. 

    - Simulation 1 runs 100 trials to generate an overview of calcium and neurotransmitter resource levels during the course of the trial (if STSP mechanism is used in the model) as well as neural spiking patterns and the extent to which the neural activation reflected information about the experimental stimuli.
    
    - Simulation 2 runs 1728 trials over 19 'model participants', replicating Wolff and colleagues' (2017) experiment. Behavioural performance data as well as neural spiking activity on each trial is saved. Data can be used to decode the neural activation and replicate Wolff and colleagues' (2017) (cross-temporal) decoding analyses. Decoding and cross-temporal decoding functions adjusted to work with model data can be found [here](https://github.com/Valkje/dynamic-coding).

## References
Knol, L. (2020). Dynamic Coding in a Large-Scale, Functional, Spiking-Neuron Model. (Unpublished Bachelor's Thesis). University of Groningen, Groningen, The Netherlands. Retrieved from https://fse.studenttheses.ub.rug.nl/22884/1/bAI_2020_KnolL.pdf

Mongillo, G., Barak, O., & Tsodyks, M. (2008). Synaptic Theory of Working Memory. Science, 319(5869), 1543–1546. https://doi.org/10.1126/science.1150769

Pals, M., Stewart, T. C., Akyürek, E. G., & Borst, J. P. (2020). A functional spiking-neuron model of activity-silent working memory in humans based on calcium-mediated short-term synaptic plasticity. PLoS Computational Biology, 16(6). https://doi.org/10.1371/journal.pcbi.1007936

Wijs, C. (2020). Dynamic Coding in a Neural Model of Activity-Silent-Working Memory. (Unpublished Bachelor's Thesis). University of Groningen, Groningen, The Netherlands. Retrieved from https://fse.studenttheses.ub.rug.nl/22521/1/AI_BA_2020_CHIELWIJS.pdf

Wolff, M. J., Jochim, J., Akyürek, E. G., & Stokes, M. G. (2017). Dynamic hidden states underlying working-memory-guided behavior. Nature Neuroscience, 20(6), 864–871. https://doi.org/10.1038/nn.4546