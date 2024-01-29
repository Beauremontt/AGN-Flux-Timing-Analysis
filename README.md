# AGN Flux Timing Analysis
Load flux data, then analyze it for periodic features using the [Jupyter script](https://colab.research.google.com/drive/1dE4RIztuHOyESiAoxBiUjtdFmgXicig-).

<br>

#### Sources of flux data
* RXTE [AGN Timing & Spectral Database](https://cass.ucsd.edu/~rxteagn/)
  * Data columns are: MJD, chosen keV flux, error, good exposure term of ObsID(sec)
* MAXI [source list](http://maxi.riken.jp/top/slist.html), [light curves](http://maxi.riken.jp/top/lc.html) (both links lead to the same data)
  * Data columns are: MJD, 2-20 keV flux, error, 2-4 keV flux, error, 4-10 keV flux, error, 10-20 keV flux, error
  * MAXI's [README](http://maxi.riken.jp/top/lc_readme.txt)
* Swift/BAT [Transient Sources (Historically Detected)](https://swift.gsfc.nasa.gov/results/transients/BAT_detected.html)
  * Data columns are: MJD, flux, error, year, day, statistical error, systematic error, data quality flag, exposure time, exposure time scaled by partial coding, exposure time while dithered

<br>

#### To Do
* Create histogram for the spacing of data points
* Filter out low SNR and negative (?) flux data
* ~~Load flux data automatically (from Drive or directly from a URL?)~~
* Create list of LSP peaks sorted by power
