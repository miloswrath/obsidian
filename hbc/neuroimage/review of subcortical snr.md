#extend #fmri
## preface

> overall there is little evidence showing cortical depth as a contributing factor of snr. while it seems inevitable for the relationship to exist, examining the mathematical principles of functional analysis strategies might show relations that prove overexamination of key regions while suppressing the natively noisy regions of subcortex

## Overall idea
- SNR decreases as some nomial function with respect to cortical depth (as you get deeper SNR gets worse)
- Modern FC tools may not deal with this correctly, allowing areas with high activity to overshadow FC that may still be important

### Things to follow up on
- [I] from a physics perspective - WM has a higher accumulation of **Iron**, which has magnetic properties. GM also has iron which causes two things to happen:
	1. when signal goes though and out of GM to reach WM - magentic properties can cause interference.
	2. when signal reaches the WM, interference is stronger due its higher levels of iroin

## Lit review on SNR
### 1 - snr review paper
https://doi.org/10.1016/j.neuroimage.2016.09.008
> [!PDF|yellow] [[snr-review.pdf#page=2&selection=192,1,213,3&color=yellow|snr-review, p.142]]
This function is always normalized by the inital magnetization term 

> [!PDF|red] [[snr-review.pdf#page=3&selection=251,2,258,67&color=red|snr-review, p.143]]
> > In contrast, the background noise was found to constitute a significant portion of the overall noise variance, with levels ranging from 40% to 90% of total variance in white matter and 10% to 50% of total noise variance in gray matter.
> 
> Differences between background noise in white and gray matter suggest that either 
> 	a. the tissue composition is susceptible to background noise within the scanner
> 	b. (more interestingly) perhaps the depth of this tissue means that the background noise is gray matter activity?

> [!PDF|note] [[snr-review.pdf#page=3&selection=302,44,310,28&color=note|snr-review, p.143]]
> >  In certain brain regions, such as the brainstem, the proximity to large vessels and fluid- filled spaces leads to a higher relative contribution of physiological noise (Brooks et al., 2013).
> 
> May be worth looking at vascular differences in gray and white matter - average vessel diameter and density of vessels in white vs. gray. Could also be worth looking at gray matter regions near white matter with high vascular density

![[Pasted image 20250717081304.png]]
**subcortical density is greater than supercortical  due to connections leading inwards**

> [!PDF|yellow] [[snr-review.pdf#page=3&selection=334,60,335,60&color=yellow|snr-review, p.143]]
> > ncrease in power as compared to the spectrum in white matter.
> 
> Kind of contradicts earlier statements - although warrants further investigation - could be a good read.


> [!PDF|yellow] [[snr-review.pdf#page=4&selection=11,0,12,14&color=yellow|snr-review, p.144]]
> > Pulsation-related artifacts tend to be most pronounced near the large arteries

> [!PDF|red] [[snr-review.pdf#page=4&selection=46,7,48,58&color=red|snr-review, p.144]]
> > In these methods, an external measurement of cardiac activity is acquired (typically with a pulse oximeter) and the data is sorted with respect to its relation to the cardiac phase. 
> 
> the easiest way is usually not the best but this happens to make much sense

> [!PDF|note] [[snr-review.pdf#page=4&selection=51,27,52,47&color=note|snr-review, p.144]]
> > dominated by physiological noise, such as the large vessels, white matter, and ventricles
> 
> Once again contradicting with the 1993 paper -> this basically says that white matter has an elevated noise characteristic

This is enough for me to be intrigued, now I will look into SNR calculations in MRIQC and fmriPrep
## Calculation of SNR
*I hope to look at how SNR is calculated both structurally and functionally - this should allow me to further understand the avenues for possible changes to include depth/density*

### MRIQC 

*SNR is calculated as*

$$
\begin{align*}
SNR = \cfrac{\mu_F}{\sigma_F\sqrt{n/(n-1)}} \\
&\text{where } \mu_F = \text{mean foreground, } \\
& \sigma_{F} = \text{standard deviation of foreground, } \\
& n = \text{number of voxels in foreground}
\end{align*}
$$
- Potential to add a distance from superior surface to the denominator as higher distance would mean lower SNR 
*tSNR is calculated as*
$$
\begin{align*}
tSNR = \cfrac{\langle S_t \rangle}{\sigma_t} \\
& \text{where } \langle S_t \rangle = \text{average BOLD signal scross time} \\
& \sigma_t = \text{Corresponding temporal S.D. map } \\
& \text{higher = better of course!}
\end{align*}
$$
- after modeling what the anatomical noise looks like - it may be useful to add the same relationship to F.C. while FC may be too complicated for such a short time

