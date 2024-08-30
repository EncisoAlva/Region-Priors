# Electric Source Imaging with Binary Region Priors

A central task for Neuroscience is to determine the location of electrical activity of neural origin inside the brain. 
Electrical Source Imaging (ESI) is a particular framework for neural electrical source location.

Although the basic formulation of ESI constitutes an ill-posed problem (in the sense of Hadamard), it may be augmented by modeling any additional information we may have about the electrical sources. For instance, minimal-norm estimators assume that the most plausible estimation is that with a lower norm. 
However, minimal-norm ESI estimators possess a low resolution in space.

In my PhD dissertation, we constructed a novel ESI estimator incorporating binary anatomical data from pathologies observed in the post-mortem to improve its spatial resolution.

Furthermore, the methodology developed in my PhD dissertation can be extended to incorporate similar types of binary data derived from various imaging modalities, such as fMRI, NIRS, and CT, among others.

The interested reader may refer to [my dissertation](https://mavmatrix.uta.edu/math_dissertations/162/). 
The presentation was recorded, and it is available [here](https://drive.google.com/file/d/1jC29LfYxnKniUrf4qTJaTYbJNPSoyBz7/view?usp=sharing); 
the slides can be accessed [https://drive.google.com/file/d/1jCc60A6hyuYjBBVgBPFIjxB2DwLOZxNE/view?usp=sharing](here).

## Algorithm Summary

_A grosso modo_, we construct the spatial priors based on observations from low-resolution imaging modalities. For instance, we use pictures from post-mortem symptoms of a stroke.

<img src="doc_img/sketch02_v2.png" width="600" height="178">

# Brainstorm Implementation

Brainstorm is a Matlab toolbox for analyzing brain recordings, including, but not limited to, MEG, EEG, fNIRS, ECoG, etc. In the context of Electrical Source Imaging, Brainstorm offers integrations with state-of-the-art toolboxes such as CAT12 for processing anatomical MRI data and OPENMEEG for solving the forward problems of EEG vs. electrical dipoles.

# Setup

To run these scripts, you need a working installation of [Brainstorm](https://neuroimage.usc.edu/brainstorm/Installation). 

To **install** the algorithm into your local Brainstorm, do as follows:

1. Note the folder `~/.brainstorm/process`, designated for user-defined processes. 

2. Go to this repository's `Brainstorm' folder and download `process_RegionPriors.m'.

3. Download the file `process_(...).m` and move it to `~/.brainstorm/process`

Notice that other algorithms are included in the `Brainstorm' folder. They were implemented to compare against the proposed method.

Now, to **use** the algorithm, you need data pre-processed to perform a Source Reconstruction. 
This requires that the database contains the subject's anatomy data, sensor data, and electrode positions. 

The appropriate methods are beautifully explained in the [Brainstorm tutorials](https://neuroimage.usc.edu/brainstorm/Tutorials#Get_started). 

Once the data is already in the database, the algorithms provided here can be run as follows:

0. Start Brainstorm as usual.

1. Select the sensor data and drag it to the `Run' section.

2. Select the `Run' button to open the Pipeline editor.

3. Use the cog to open the menu of processes.

4. Navigate to `Sources / Binary Region Priors'.

5. Multiple options are available for selection, such as the heuristic for hyperparameter tuning.

<img src="doc_img/Brainstorm_instructions_02.png" width="400" height="456">

The results will be saved to the database as any other Source Reconstruction method mentioned in the tutorials.

Double-click on it on the new file **and** the sensor data to explore visually the sources as they evolve in time.