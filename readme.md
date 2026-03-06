# lingua-map
*started August 13, 2019*

## lingua-map

**lingua-map** is a pipeline for automatically generating an HTML report summarizing results from a patient’s presurgical functional MRI (fMRI). The report includes task activation maps and region-of-interest (ROI) statistics used to evaluate language lateralization prior to neurosurgery.

The tool was originally developed for epilepsy patients undergoing pre-surgical evaluation to determine language dominance before resection.

### Overview

lingua-map takes a BIDS-formatted dataset and corresponding **fMRIPrep** outputs as inputs. The pipeline performs a general linear model (GLM) analysis of preprocessed BOLD time-series images to estimate task-related activation and quantify hemispheric language lateralization.

It then compiles the results into an automatically generated HTML report containing task activation maps in a glass brain model, a scrollable activation map superimposed on the subject's structural image, and ROI statistics and data visualizations.

### Pipeline Components

The pipeline includes the following steps:

1. **Data input**

   * BIDS dataset
   * fMRIPrep preprocessing outputs

2. **Statistical modeling**

   * First-level GLM applied to BOLD time series
   * Implemented using FSL commands wrapped with **Nipype**

3. **Activation map generation**

   * Task activation contrasts are estimated from the GLM results

4. **ROI-based laterality analysis**

   * Laterality indices are calculated within language ROIs
   * ROIs are defined based on recommendations from the ASFNR white paper:
     http://www.ajnr.org/content/38/10/E65

5. **Report generation**

   * Results are compiled into an HTML report using **Jinja templating**
   * Output includes activation maps and summary statistics

### Deployment

For reproduciblity purposes, the pipeline is **Dockerized** and designed to run as a gear on the **Flywheel neuroinformatics platform**.

Because the workflow relies on Flywheel data structures and environment configuration, it is not currently recommended for standalone use outside that platform.

### Technologies Used

* Python
* Nipype
* FSL
* Docker
* Jinja templating
* BIDS / fMRIPrep neuroimaging standards

### Purpose

The goal of lingua-map is to automate generation of clinically interpretable language lateralization reports from presurgical fMRI datasets, improving reproducibility and reducing manual processing steps in neuroimaging workflows.
