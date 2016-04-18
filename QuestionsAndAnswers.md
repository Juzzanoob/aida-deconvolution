# Introduction #

This is a compilation of questions that AIDA users have had, along with some answers.  Hopefully, this will be useful to new users.

# Details #
1) **What size/format should the images be (both science images and PSFs)?**

**_Answer:_**
The larger is the image , the longer the deconvolution process will take (5 min in mono-frame with nPSF of 256x256 on a Mac OS X Mac Book Pro computer). So the size of the image is directly related to your patience, and the speed of your computer.  Ideally AIDA can deal with any type of images, square or not, however we discovered a bug (no yet fully identified) in the current version (1.2.2i). It has been solved in the latest version of AIDA (1.3).
We recommend you start deconvolving square frames first, make sure that when you crop the target and the PSF frames, there is enough background to estimate the RON (which is estimated from the negative pixels value), if you don't have this information then you should add either a dark image (best alternative), or a background and/noise value in the Setting file.
#background = 0.
#sigma\_det = 5
#dark\_image = None
Another difficulty to take into consideration is that the stdev of the negative pixels should be larger than sqrt(!pi/2) (see Eq 32 in Hom et al., JOSA, 2007). If not, you need to "artificially" increase the value of the frame by a factor 10-100. This is an issue that we will solve in the next version of AIDA.


2) **How many PSF images do we have to provide to AIDA? Do they have to be normalized?**

**_Answer:_**
This depend of the variation of the PSF which varies with the AO that you are using, the seeing condition and the brightness of your target. With NACO or Keck AO I generally have 3 PSF frames when I observed Io (V=5!), at least 6 when I observe something fainter (V=13) to fully capture the variability of the PSF. Check the FWHM of your PSFs, for Io (V=5) the variation should be less than 5%, for the V=13 target I typically get a variation of the FWHM by 7%.
Do NOT normalize the PSF frames since AIDA will clean them up after extracting the noise (see point 1), and then normalize them.


3) **My VLT/NACO image is the medium average product of a set of 19 raw frames. Should I apply the AIDA algorithm to the 19 dark-subtracted/flatfielded images...or to the final combined image?**

**_Answer:_**
This depends of your target, its brightness, its structure (faint halo?) and the quality of your images. I will try both and compare.
Rules of thumb: Multi-object and 1 PSF deconvolution works fine in L-M band (>3 um) because the AO system is stable (stdev(FWHM)/FWHM < 2%)  in the wavelength range and because of the strong thermal background the SNR is poor. For anything at shorter wavelength (1-2.5 um) we recommend using the averaged image and multi-PSF since the PSF variability is predominant in this case (except if your target is extremely bright).


4) **How to generate the PSF images if I do not have PSF observations?** The NGS reference is inside the FoV of my images. Can I generate a model PSF using DAOPHOT/PSF routine within IRAF/Pyraf from the NGS in my image... or,  should I use 2-3 stars close to my extended object to have a more accurate PSF?

**_Answer:_**
This question is related to point 3. You definitely need to prioritize the average target frame / multi-pSF deconvolution since you don't have a good PSF. Now the response to your question. Ideally, it is better to use stars as bright as your target. If you have enough of it, I recommend you extract those and use them in the multi-PSF algorithm as estimates of the real PSF.


5) **In which cases is the AIDA algorithm useable?  My object is extended but not very large (~ 2x FWHM of the diffraction-limited PSF) and faint (SNR ~ 10 and  SNR ~ 2 in the faintest parts).**

**_Answer:_**
AIDA is useable in a lot of cases, it all depends of the science that you want to do. It works better on extended target (planets, cells,...) with a separation larger than the FWHM (we do super-resolve but this is still controversial), however it should also work on point star images with a separation larger than the FWHM. If one of your companions has feature around it (Galaxy disk, cocoon) AIDA may help revealing it but if this feature has a brightness ratio larger than 10<sup>3</sup> you should not use AIDA. In these complex cases, the restoration may be only cosmetic since you lose the photometric information on the images.  The best way to find out if it is the case is to run series of deconvolution tests with an artificial object (use for instance the clean Rpsf provided by AIDA).
Something to keep in mind: Always check if Rpsf contains a _shadow_ of your object, if it is the case then the deconvolution photometry is flawed.