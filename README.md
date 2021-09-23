# KOI CNN vetting results

Welcome! If you're viewing this page, you've probably read our paper, "Identification of Candidate Exomoon Signals with Convolutional Neural Networks" (Teachey & Kipping 2021, accepted to MNRAS). The repository hosts the results of our vetting of 1880 KOIs (confirmed and candidate planets) with periods >= 10 days in search of exomoon signals.

## Background
Convolutional Neural Networks have proven to be effective tools in analyzing large volumes of time domain photometry in search of candidate planet signals, and distinguishing between genuine planets and false positive scenarios.

We decided to apply this tool to the *Kepler* data to search for exomoon signals. All the gory details about how we went about generating the training set, and validated the performance of the neural network ensemble, can be found in the paper: https://ui.adsabs.harvard.edu/abs/2021arXiv210910503T/abstract 


## About this resource
The main (only?) file in this repository is our summary report of vetting 3223 KOIs with our neural network ensemble. Here's a breakdown of the columns:

1. **KOI** -- the planet in question. Should be self-explanatory.

2. **disposition** -- "CONFIRMED" or "CANDIDATE" based on the NASA Exoplanet Archive designation at runtime.

3. **period** -- orbital period in days, as reported by NASA Exoplanet Archive at runtime.

4. **ntransits** -- the number of transits vetted *minus* the number of transits excluded (likely for failure of the MAD test). This may or may not be the number of transits the planet actually displays in the *Kepler* data. If a transit didn't meet our criteria, it wasn't vetted.

5. **ncontams** -- the number of transit windows that were contaminated by the transit of a neighboring planet (can be nonzero for multiplanet systems). As detailed in the paper, these contaminating transits were removed with a mask and replace methodology. Nevertheless, they are documented here.

6. **nmadfailed** -- the number of transit windows that failed the Median Absolute Deviation (MAD) test (described in the paper) for detecting stellar / instrumental variability that might have been insufficiently detrended.

7. **nexcluded** -- The number of systems left out of the vetting. For this run, systems that failed the MAD test were excluded.

8. **orig_nmoons** -- the number of transits vetted that were classified as showing a moon feature. What does "original" mean? See below, and / or read the paper :)

9. **orig_frac_wmoons** -- the number above divided by the total number of transits vetted.

10. **nmoons_agth** -- the number of moon classifications for which the "agreement metric" was above our specified threshold (detailed in the paper, this is how well the CNN ensemble agrees on a classification). Less than or equal to "orig_nmoons", since some or all original classifications may meet the agreement threshold.

11. **frac_wmoons_agth** -- the number above divided by the number of transits vetted.

12. **agth** -- we set an agreement threshold of 0.95 for this run.

13. **median_agreement** -- the median agreement metric across all the transits that were vetted.

14. **fp_nexcluded** -- the number of false positive test light curves that were rejected (zero for all systems).

15. **fp_median_agreement** -- the median agreement metric across all the transits vetted in the false positive test run.

16. **FP_rate** -- the fraction of false positive test runs that erroneously resulted in a moon classification. NOTE that the FP rate quoted is based on the *agreement metric*. That is, if a FP test light curve was classified as having a moon, but without meeting the agreement threshold, it was reclassified as "no moon". Since we rely on the agreement metric for our classifications, this is the number we are most interested in: how often do we falsely identify a moon to high confidence?


## Caveats
If you have one takeaway from this paper / result, it should be this: *These classifications should not be casually interpreted as evidence for the presence of an exomoon.* We also caution against making strong inferences about the occurrence rate of exomoons based on these results. They may be indicative of a low occurrence rate, but we consider such a conclusion to be premature based on these results alone. Ideally they would be used to zero in on systems you might find interesting for closer examination. If nothing else, it's just a record of what we did in this paper. I hope it's useful.


## Citation
If you use this resource we would appreciate your citing our paper: https://ui.adsabs.harvard.edu/abs/2021arXiv210910503T/abstract 

