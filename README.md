# KOI CNN vetting results

Welcome! If you're viewing this page, you've probably read our paper, "Identification of Candidate Exomoon Signals with Convolutional Neural Networks" (Teachey & Kipping 2020, *submitted to MNRAS*). The repository hosts the results of our vetting of 3223 KOIs (confirmed and candidate planets) in search of exomoon signals.

## Background
Convolutional Neural Networks have proven to be effective tools in analyzing large volumes of time domain photometry in search of candidate planet signals, and distinguishing between genuine planets and false positive scenarios.

We decided to apply this tool to the *Kepler* data to search for exomoon signals. All the gory details about how we went about generating the training set, and validated the performance of the neural network ensemble, can be found in the paper (will link it when it's public).


## About this resource
The main (only?) file in this repository is our summary report of vetting 3223 KOIs with our neural network ensemble. Here's a breakdown of the columns:

1. **KOI** -- the planet in question. Should be self-explanatory.

2. **disposition** -- "CONFIRMED" or "CANDIDATE" based on the NASA Exoplanet Archive designation at runtime.

3. **period** -- orbital period in days, as reported by NASA Exoplanet Archive at runtime.

4. **ntransits** -- the number of transits vetted. This may or may not be the number of transits the planet actually displays in the *Kepler* data. If a transit didn't meet our criteria, it wasn't vetted.

5. **ncontams** -- the number of transit windows that were contaminated by the transit of a neighboring planet (can be nonzero for multiplanet systems). As detailed in the paper, these contaminating transits were removed with a mask and replace methodology. Nevertheless, they are documented here.

6. **nmadfailed** -- the number of transit windows that failed the Median Absolute Deviation (MAD) test (described in the paper) for detecting stellar / instrumental variability that might have been insufficiently detrended.

7. **nexcluded** -- equals zero for all systems. The generating code allowed for excluding transits with contaminants and/or systems that failed the MAD test. For this run, we did not exclude such systems. Therefore, systems having a moon detection but that also failed many MAD tests should be viewed with some skepticism.

8. **orig_nmoons** -- the number of transits vetted that were classified as showing a moon feature. What does "original" mean? See below, and / or read the paper :)

9. **orig_frac_wmoons** -- the number above divided by the total number of transits vetted.

10. **nmoons_agth** -- the number of moon classifications for which the "agreement metric" was above our specified threshold (detailed in the paper, this is how well the CNN ensemble agrees on a classification). Less than or equal to "orig_nmoons", since some or all original classifications may meet the agreement threshold.

11. **frac_wmoons_agth** -- the number above divided by the number of transits vetted.

12. **agth** -- we set an agreement threshold of 0.95 for this run.

13. **median_agreement** -- the median agreement metric across all the transits that were vetted.

14. **fp_nexcluded** -- the number of false positive test light curves that were rejected (zero for all systems).

15. **fp_median_agreement** -- the median agreement metric across all the transits vetted in the false positive test run.

16. **FP_rate** -- the fraction of false positive test runs that erroneously resulted in a moon classification. 


## Caveats
If you have one takeaway from this paper / result, it should be this: *These classifications should not be casually interpreted as evidence for the presence of an exomoon.* As we detail in the paper, there is a sizeable fraction of these systems that our code suggests show evidence of a moon, and the training and validation of the CNN ensemble suggests we're doing a pretty good job with these classifications. But can we use this inferences about the exomoon population? Maybe, but be careful. Can we say a moon is present based on this CNN classification? Again, be careful.

The purpose of developing this CNN ensemble classifier was to rapidly identify systems that deserve further scrutiny, that is, running them through a battery of more rigorous tests and close examination to see if the exomoon hypothesis holds water. As we describe in the paper, we pulled out 9 systems for further analysis, and only a few of them emerged as potentially viable. We stopped short of naming any of these systems new "candidate" exomoons (a fraught term).

So anyway, please be careful with your interpretation of these results. Ideally they would be used to zero in on systems you might find interesting for closer examination. I hope it's useful.


## Citation
The paper isn't yet online, but when it is, we will provide the citation here. If you find this work useful, we would appreciate your giving us a shoutout in the bibliography.

