# AGN Flux Timing Analysis

This is the repository for the time series analysis pipeline created for the sake of researching quasi-periodic oscillations of AGN. The code is written in Python, using the Jupyter Notebook IDE.

You can access and run the code online by using my Google Colab notebook: [LINK](https://colab.research.google.com/drive/1dE4RIztuHOyESiAoxBiUjtdFmgXicig-)

The actual code is hidden by default, as the input forms should be all you need to run the script. I commented most of the code, and especially the input variables that show up in the forms. If it isn't clear what the input variables are for, show the code and read the comments for those variables -- they should all be near the tops of the code cells.

<br>

#### Features
* Most of the relevant plotting parameters and some of the analysis can be adjusted using form inputs
* Load flux data from URL or uploaded text file (see Sources below for expected data formats)
* Data can be filtered using a user-specified signal-to-noise ratio
* Creates a histogram of gaps between measurements with choice of scaling the y-axis in linear or log
* Processes the data using the Lomb-Scargle periodogram
* Can fit data to a power law, assuming inputted AGN data has pink/fractional noise
  * (WIP) Perform ANOVA using the fitted power law to determine more accurate false-alarm probabilities for each peak
* Peaks of the generated periodogram are tabulated and displayed in descending order of power
  * Table includes: peak's power, frequency, period, and false-alarm probability
* Displays the power spectrum of the periodogram with a chosen number of the highest peaks annotated
  * Options of frequency or period on the x-axis
  * Can choose points along the x-axis to draw vertical bars, for reference and to ease comparisons
* From either the table or the power spectrum, choose a peak to get its best estimate period and uncertainty
* Plots a folded light curve using the period of the chosen peak

<br>

#### Some sources of AGN flux data
* RXTE [AGN Timing & Spectral Database](https://cass.ucsd.edu/~rxteagn/)
  * Data columns are: MJD, chosen keV flux, error, good exposure term of ObsID(sec)
* MAXI [source list](http://maxi.riken.jp/top/slist.html), [light curves](http://maxi.riken.jp/top/lc.html) (both links lead to the same data)
  * Data columns are: MJD, 2-20 keV flux, error, 2-4 keV flux, error, 4-10 keV flux, error, 10-20 keV flux, error
  * MAXI's [README](http://maxi.riken.jp/top/lc_readme.txt)
* Swift/BAT [Transient Sources (Historically Detected)](https://swift.gsfc.nasa.gov/results/transients/BAT_detected.html)
  * Data columns are: MJD, flux, error, year, day, statistical error, systematic error, data quality flag, exposure time, exposure time scaled by partial coding, exposure time while dithered
