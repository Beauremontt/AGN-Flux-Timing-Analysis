# AGN Flux Timing Analysis

This repository contains a time series analysis pipeline for searching for quasi-periodic oscillations in active galactic nucleus (AGN) flux data. The code is written in Python and structured as a single Jupyter Notebook.

The expected way to use this project is through Google Colab. The notebook is designed so that most interaction happens through input forms, rather than by editing code directly.

You can open and run the notebook here:  
[Google Colab - AGN Flux Timing Analysis](https://colab.research.google.com/github/Beauremontt/AGN-Flux-Timing-Analysis/blob/main/AGNFluxTimingAnalysis.ipynb)


## Overview

The pipeline takes irregularly sampled AGN flux measurements and performs a sequence of timing analyses aimed at identifying periodic or quasi-periodic signals. The focus is exploratory rather than automated detection.

A typical workflow looks like this:
* Load flux data from a URL or uploaded text file
* Inspect sampling gaps and basic properties of the time series
* Optionally filter data using a signal-to-noise threshold
* Compute a Lomb-Scargle periodogram
* Identify and tabulate the strongest peaks
* Select a candidate peak and examine it via phase folding

Most plotting parameters and several analysis options are adjustable through form inputs near the tops of the notebook cells. The underlying code is commented, but hidden by default to keep the notebook usable without modification.


## Analysis outputs

The notebook produces several plots during a standard run. The example images in this repository all use MAXI data for the blazar Markarian 421.

<img src="sample_plots/Mrk 421 lc_filtered.png" alt="light curve plot" width=640>
Raw flux measurements as a function of time, after optional filtering.

<br><br>

<img src="sample_plots/Mrk 421 gap_hist.png" alt="sampling gap histogram" width=640>
Histogram of time gaps between observations, useful for diagnosing cadence effects.

<br><br>

<img src="sample_plots/Mrk 421 LSP (frequencies, log).png" alt="lomb–scargle periodogram" width=640>
Power spectrum generated using the Lomb–Scargle method, with optional peak annotations and a user-selectiod reference period overlaid.

The strongest peaks in the periodogram are also tabulated and displayed directly in the notebook. The table includes peak power, frequency, period, and false-alarm probability.

<br><br>

<img src="sample_plots/Mrk 421 lc folded on peak 2.png" alt="folded light curve" width=640>
Phase-folded light curve using the period of a selected peak.


## Noise modeling and significance

The periodogram background can be fit to a power law, under the assumption that AGN variability follows pink or fractional noise. This fit is used when estimating false-alarm probabilities for detected peaks.


## Data sources

The notebook expects plain-text flux data with well-defined columns. It was tested primarily using data from the following sources:
* **RXTE AGN timing & spectral database**
	* https://cass.ucsd.edu/~rxteagn/
	* Data columns: MJD, selected keV flux, error, good exposure term of ObsID
* **MAXI source list and light curves**
	* Source list: http://maxi.riken.jp/top/slist.html
	* Light curves: http://maxi.riken.jp/top/lc.html
	* Data columns: MJD; 2–20 keV flux and error; 2–4, 4–10, and 10–20 keV fluxes and errors
	* MAXI README: http://maxi.riken.jp/top/lc_readme.txt
* **Swift/BAT transient sources (historically detected)**
	* https://swift.gsfc.nasa.gov/results/transients/BAT_detected.html
	* Data columns: MJD, flux, multiple error terms, data quality flags, and exposure information

Notes on expected formats and column handling are included in the notebook itself.
