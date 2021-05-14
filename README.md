# SCDeep Applied ML Submission
Authors: Matthew Finley, Bernice Kubicek, Jacob Nishimura, Broderick Schwartz

## Overview
This repository contains files to run experiments for the Applied ML final project. The set of notebooks takes in original depth files, encodes and saves them as images, decodes them back into depth, and applies error correction in multiple ways. Results are evaluated by comparing average RMS error over the test dataset.

## Structure and Running
The notebooks for the experiments are split into 4 categories:

### 0 - Dataset Generation
The only script in this category reads in the original depth files, encodes them using the SCD technique, and saves them out for future tasks.

### 1 - Segmentation
The training script is used to train and save out the U-Net model to segment/predict the stair map used in phase unwrapping. The evaluation script loads in the U-Net model and uses it on the test set images to decode depth and evaluate RMS error compared to the true depth values. The evaluation script also has an option to save out all its prediction images to use in future steps.

### 2 - Error Correction
This category is split into 3 folders - one for each error correction approach. In all three folders (Classic GAN, Multiscale DCNN, and NAC), there is a TrainModel notebook which trains the model on the depth which used the predictions in part 1. There is also an EvaluateModel script which reads in the model, applies the error correction, and calculates the RMS error.

### 3 - Analysis
This category has one script which loads in all 4 trained models, runs through the test dataset for each model, and generates statistics/figures for each model.

### Running the Scripts
The scripts were written using TensorFlow 2.4, and requires an environment with compatible Nvidia drivers and CuDA installed. The group used a Docker/Singularity image to simplify dependency management.

Unfortunately, the "Faces" dataset the group is using doesn't permit duplicating/sharing the dataset. Many of the notebooks should still contain outputs from running them, and the group can provide other documentation of the scripts running if required.
