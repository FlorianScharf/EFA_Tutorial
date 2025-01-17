# PCA Tutorial
Accompanying scripts and material to conduct a temporal EFA on ERP data as explained in Scharf, Widmann, Bonmassar & Wetzel (2022; https://www.sciencedirect.com/science/article/pii/S1878929322000160).

## Abstract
Developmental researchers are often interested in event-related potentials (ERPs) as a measure of brain activity occurring time-locked to an event of interest. The traditional data-analytic approach for ERPs is based on the observed ERP and suffers from two major problems: First, the definition of analysis time windows as well as regions of interest often proceeds in a relatively arbitrary manner. Second, the observed signal at the scalp is a mixture of underlying signals generated in the brain. The temporal exploratory factor analysis (EFA) for ERP data, also known as temporal principal component analysis (PCA), aims to address these problems. However, its application in developmental ERP research settings comes with the unique challenge that the component structure differs between children and adults (so-called measurement non-invariance). Separate EFAs for the groups can be used to cope with this challenge and gain valuable insights into developmental processes. Here, we demonstrate how to make results from separate EFAs accessible for inferential statistics by re-scaling to original units. In addition, separate EFAs enable analyses of latency differences between groups. We propose the application of an established Jackknife approach to the factor solution for this purpose. With this tutorial, we want to enable readers with a focus on developmental research to conduct an EFA-based ERP analysis of amplitude and latency differences to address their research questions. We explain the benefits of an EFA-based approach, introduce the EFA model and demonstrate its application to a developmental research question step-by-step using real-data from a child and an adult group (code and data are made available). Finally, we discuss how to cope with typical challenges during the analysis and name potential limitations.

## Structure 
The repository is structured as follows:
- The main scripts "01*.R" to "05*.R" conduct the EFA-based ERP analysis step by step as explained in the article.
- The directory "tools" contains some custom functions which are called in the main scripts.
- The directory "data" contains the participant average data after pre-processing for both groups and conditions as MATLAB files<sup>1</sup>. 
- The subdirectories in "results" contain the output files of the respective script.

Readers who want to use MATLAB for their analyses, may want to have look at Joseph Dien's ERP PCA Toolkit (https://sourceforge.net/projects/erppcatoolkit/) which provides all functionality to replicate the analyses in MATLAB. We provided a MATLAB implementation of the Empirical Kaiser Criterion in the directory "Tools".

<sub><sup>1</sup> Note: The epochs in the set-files are participant averages, **not** trials. We use the electrode positions from these files to make plotting the factor tropographies easier. See *03b_topoplot_allFactors.R* for further details.</sub> 

## How to get started
To use the code, please follow these steps:
1. Make sure that current versions of R (https://cran.r-project.org) and RStudio (https://www.rstudio.com) are installed. 
2. Download the whole repository (Code -> Download ZIP).
3. Unzip to a local folder on your computer.
4. Open the file "00_EFAtutorial.Rproj". 
5. This should open a separate instance of Rstudio with all necessary paths.
6. You can open and run all code from this point.

In case you encounter bugs or unexpected behavior, please, open an issue or report via mail to 

florian.scharf dot uni-muenster dot de 


## Transparency note on the data set
For the sake of completeness, we note that the dataset is not equivalent to Bonmassar et al. (2020) because the pre-processing differed in some aspects. Specifically, the following details differed: (1) We did not reject data due to artifacts in the co-registered pupil data, (2) the data were filtered with a 48 Hz low-pass filter (length: 414 points), (3) bad channels were excluded and interpolated when they exceeded a robust z-score of 3 of the robust standard deviation of the channels (Bigdely-Shamlo et al., 2015), (4) epochs exceeding amplitude differences of 750 µV (based on 0.1 Hz high-pass and low-pass filtered data) were excluded before ICA to remove non-stereotypical artifacts, and (5) the ICA was re-computed using AMICA (Delorme et al., 2012) on the 1 Hz high-pass filtered data without baseline correction (Klug & Gramann, 2020). ICA components classification was redone (but with identical constraints).
