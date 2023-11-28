# Interfacial excess caluclation across phase boundaries from atom probe data
## Overview
These methods allow the calculation of the interfacial excess across phase boundaries in proximity to grain boundaries. I have provided a few example datasets and exported data from the paper cited below. Please feel free to use these functions and reference them appropriately, thank you.  

## Calculations
The first step is obtaining high-quality proximity histograms (proxigrams) from your atom probe reconstruction. I found a step size of 0.05 nm and width +- 15 nm works very well. However, large and more diffuse interfaces may require adjustments, but you will always need to keep the step size reasonably fine.
From the proxigrams, the script automatically calculates concentration difference profiles: Step-wise difference in concentration over the step-wise difference in its spatial coordinate x. If both are present, the global maximum and minimum are used to determine the interface location. In some instances, only maxima and minima are present, and you may need to make minor manual adjustments to the interface location.
Next, cumulative profiles (or ladder diagrams) are calculated from the summation of solute atom counts over the summation of all atom counts. The interface location spatial coordinate is placed to its corresponding coordinate in the cumulative profile. The solute excess is determined via extrapolation towards this interface location. The detailed equations and error estimations are accessible in the paper below.

## Example data
Here is a proximity histogram across a M<sub>6</sub>C / M<sub>6</sub>C interface. The enrichment and depletion of different elements are obvious.
![Example data of a proximity histogram](./interfacial_excess/export/Proxi-M6C_M6C-2091-R18_61180_concentration_profile.svg)

This is an example of a concentration difference profile, corresponding to the proximity histogram above. The M<sub>6</sub>C / M<sub>6</sub>C interface exhibits the strongest variation for all elements. Black dashed lines mark the interface location identified from each element. Their consistent location allows to calculate the average from all elements.
![Example data of a concentration difference profile](./interfacial_excess/export/Proxi-M6C_M6C-2091-R18_61180_differential_profile.svg)

Here is an exemplary cumulative profile of the above proximity histogram and concentration difference profiles. The solute excess is calculated via extra polation to the interface location. Error estimations are indicated in the upper and lower range providing the standard deviation of the solute excess. The interface location is required to then calculate the interfacial excess.
![Example data of a cumulative profile](./interfacial_excess/export/Proxi-M6C_M6C-2091-R18_61180_B_cumulative.svg)

Finally, the interfacial excess across different interfaces can be summarised in this 'interface plot'. The line width corresponds to the interfacial excess. Colored lines indicate enrichment, black lines indicate depletion. 
![Example data of an interface plot](./interface_plots/export/interface_plot_Co.svg)

## Input & export
Input:
- Proximity histogram csv data
- Interface area
- Elements of interests

Output:
- Plotted proximity histogram
- Concentration difference profile
- Cumulative profiles
- Interfacial excess and standard deviation
- Interface plot if desired

## Citing
Please cite this paper when using this code: https://doi.org/10.1016/j.ultramic.2023.113885

## Acknowledgements
This research is funded via the Australian Research Council projects (LP180100144, LP190101169, and DP230101063). Special acknowledgements are given to Michael Lison-Pick and Dr. Steven Street for providing the materials used in this study. The authors thank Drs Charlie Kong and Richard Webster for technical assistance and use of facilities supported by Microscopy Australia at the Electron Microscope Unit at the Mark Wainwright Centre of Microscopy and Microanalysis at UNSW. The authors also thank Dr Takanori Sato and the Australian Centre of Microscopy and Microanalysis at the University of Sydney. Fruitful discussions with Prof. Peter Felfer (FAU Erlangen), Dr. Nima Haghdadi (UNSW Sydney), Dr Daniel Scheiber (Montanuniversität Leoben) and Mr. Han Lin Mai (The University of Sydney) are also acknowledged.
