---
title: "Doctoral Research"
excerpt: "<br/><img align='right' width='200px' src='/images/supernova.png'>Throughout my PhD, I have developed several bodies of code used to update the simulation capabilities in the SuperNova Explosion Code [(SNEC)](https://stellarcollapse.org/index.php/SNEC.html), and for data analysis. Repositories for these projects can be found here."
collection: portfolio
---

Bolometric Corrections and Time-Delay Post-Processing | 
[Project Repository](https://github.com/annahaynie/BolCorr_Magnitudes)

The various pieces of code in this repository represent new algorithms I developed to be implemented into the Supernova Explosion Code (SNEC, https://stellarcollapse.org/index.php/SNEC.html). SNEC is a one-dimensional code, which is great because this means it is very fast, however, it relies on some assumptions that can be limiting. To improve the accuracy of SNEC's outputs, I built a numerical integration algorithm to include the impacts of time-delay as photons released from different points on the surface of the star travel slightly different distances after explosion. I also build several algorithms to expand the number of wavebands that SNEC produces light curves in, which is necessary for modeling various phenomena that are brightest in different frequency ranges. 

Swift_Magnitudes.c and swift_mag2.c calculate magnitudes (luminosity in a given frequency range) of a supernova over time given bolometric luminosity, temperature, and radius information from SNEC, excluding and including the effects of light travel time delay, respectively. These codes are quite slow due to the nested integration necessary for calculating the magnitudes. To remedy this we utilize bolometric corrections to approximate the magnitude at a given temperature. make_BC2.c calculates updated Bolometric Correction tables for the set of wavebands ugriz, UBVRI, and implements the new bands GALEX NUV/FUV, and SWIFT bands M2, W1, W2. The included SNEC.zip has these updated corrections already implemented. BC_mag_td.c calculates the magnitudes with time delay taken into account using the updated bolometric corrections to speed up the post-processing.


Stripped-Envelope Supernova Model Calibration| 
[Project Repository](https://github.com/annahaynie/SESN_tail_slope_fitting)

This repository holds example code for for the fitting procedure of the late time bolometric light curve of a stripped envelope supernova as described in [Haynie & Piro (2023)](https://iopscience.iop.org/article/10.3847/1538-4357/acf844#apjacf844s1). This example shows a subset of the 77 models fit to calibrate an analytic model using linear regression to connect the late time slope to the properties of the supernova progenitor. The normalization notebook shows how I used the full grid of models to calibrate an analytic model using linear regression, and the result of testing the model on the data set.
