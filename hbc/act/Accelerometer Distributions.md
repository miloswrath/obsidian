There are two main potential approaches to solving issues where a single metric has its own bias
## Statistical Ensemble
https://digitalcommons.georgefox.edu/cgi/viewcontent.cgi?article=1035&context=hhp_fac
- use a mix of two or more metrics and provide a weighted consensus technique to mitigate the false negative subtle static posture changes in ENMO
## Machine Learning
https://pmc.ncbi.nlm.nih.gov/articles/PMC11495570/
- Simulate data trhough physics based models (add noise to low amplitude sine waves for standing sway?) or data driven models (SMOTE) ensure labels are accurate via domain rules
- Train models on ENMO and Neishabouri counts then stack or vote
- Can boost sensitivity

## Main Choice 
If interpretability is key, start with non-ML ensembles (e.g., consensus cut-points). For higher accuracy, use ML with synthetic augmentation—it's robust if synthetics faithfully replicate distributions (validate via KS-tests). Combine with posture metrics (e.g., Anglez) for even better standing detection.

## Implementation in GGIR
- can use external functions in GGIR for at least parts 1 and 2 but I asked the GGIR group if it will use the external function as main metrics in parts 3 -> 6


## Problems with sampling frequency
https://journals.humankinetics.com/view/journals/jmpb/4/4/article-p298.xml
Paper found that as frequency lowered there was less light activity and sleep classified (when relying on guider this would end up going to sedentary for us)

https://journals.biologists.com/jeb/article/221/23/jeb184085/20503/High-accuracy-at-low-frequency-detailed
machine learning methods have higher accuracy when using low sampling frequency

https://onlinelibrary.wiley.com/doi/full/10.1111/joim.12908
Some evidence points to the need for advanced ML to correctly classify with wrist worn devices
