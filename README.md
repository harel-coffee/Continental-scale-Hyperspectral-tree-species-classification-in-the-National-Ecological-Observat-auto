# Continental-scale-Hyperspectral-tree-species-classification-in-the-National-Ecological-Observatory-N

This repo contains the code for reproducing data cleaning, model developing, evaluation and all the analyses from the manuscript: Continental-scale Hyperspectral tree species classification in the National Ecological Observatory Network.


To reproduce the analysis in this paper, please, downolad inputs and outputs from the zenodo archive at: link and paste them in the indir and outdir respectively.

The data in the vst.csv file represents the field data collected by the National Ecologicla Observatory Network. Data was downloaded and cleaned using the NeonDataWrangler repo (link).
The remote sensing data in the spectral_library.csv file was extracted and brdf corrected before hand using the NeonDataWrangler repo.

To reproduce the data preprocessing and train-test splitting discussed in the paper, run the `run_data_filtering()` in R environment from within the project folder.

An example on how to achieve it:
`library(tidyverse)`

`library(data.table)`

`r_sources = list.files("./src/R/functions/")`

`sapply(paste("./src/R/functions/", r_sources, sep=""), source)`
`run_data_filtering()`

To reproduce the model training and testing, run the `species_classification_sript.py` python script in `src/Python`. This script will perform training and testing and generate outputs for the test set. Beware, this step will likely take hours.
To reproduce model training and testing for each individual site, run the `site_level_loop_script.py`

To perform outputs analysis and generate figures 1-4 and 6, run the `accuracy_and_uncertainty()` function in `src/R`.

Figure 6 was generated by using qgis. Predictions for all tiles in the BART NEON site were performed running the `prediction_at_tile.py` script in batches. Beware, if you try to reproduce this section of the analysis it may take several hours to make predictions for a tile. 
