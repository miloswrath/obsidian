> after realizing the low sampling rate is causing many issues - next steps are to use the gt3x files and see if there's a major difference

#act 

## Steps
- first test a few files with higher sampling rate to see if there is a difference



**Describe the bug**
One file is having trouble generating meta outputs for part 2, stalling any processing afterwards.

**To Reproduce**
Using actigraph 1hz .csv files, I ran the code below to generate part 2 outputs, 
```
library(GGIR)

main <- function() {
        GGIR(
          # ==== Initialization ====
          mode = 1:2,
          datadir = input,
          outputdir = output
          studyname = "boost",
          overwrite = TRUE,
          desiredtz = "America/Chicago",
          print.filename = TRUE,
          idloc = 6,

          # ==== Part 1: Data loading and basic signal processing ====
          do.report = c(4, 5, 6),
          epochvalues2csv = TRUE,
          do.ENMO = TRUE,
          acc.metric = "ENMO",
          windowsizes = c(5, 900, 3600),

          # ==== Part 2: Non-wear detection ====
          ignorenonwear = TRUE,

          # ==== Part 3: Sleep detection ====

          # ==== Part 4: Physical activity summaries ====
          timewindow = c("WW", "MM", "OO"),

          # ==== Part 5: Day-level summaries ====
          hrs.del.start = 4,
          hrs.del.end = 3,
          maxdur = 9,
          threshold.lig = 44.8,
          threshold.mod = 100.6,
          threshold.vig = 428.8,

          # ==== Part 6: CR and other metrics ====
          part6CR = TRUE,
          visualreport = TRUE,
          old_visualreport = FALSE
        )
      }

# Run main if executed as script
if (!interactive()) {
  main()
}

```


> which finishes with a warning about a footer


```
Checking that user has write access permission for directory specified by argument outputdir: Yes

   GGIR version: 3.2.6

   Do not forget to cite GGIR in your publications via a version number and
   Migueles et al. 2019 JMPB. doi: 10.1123/jmpb.2018-0063.
   See also: https://cran.r-project.org/package=GGIR/vignettes/GGIR.html#citing-ggir

   To make your research reproducible and interpretable always report:
     (1) Accelerometer brand and product name
     (2) How you configured the accelerometer
     (3) Study protocol and wear instructions given to the participants
     (4) GGIR version
     (5) How GGIR was used: Share the config.csv file or your R script.
     (6) How you post-processed / cleaned GGIR output
     (7) How reported outcomes relate to the specific variable names in GGIR
________________________________________________________________________________
 Part 1

Checking that user has read access permission for all files in data directory: Yes
1
File name: sub-8019_ses-3_accel.csv
P1 file 1

Investigate calibration of the sensors with function g.calibrate:

Loading chunk: 1
Extract signal features (metrics) with the g.getmeta function:

Loading chunk: 1
Save .RData-file with: calibration report, file inspection report and all signal features...

________________________________________________________________________________
 Part 2
1 Warning message:
In data.table::fread(filename, nrows = blocksize, skip = startpage,  :
  Discarded single-line footer: <<-0.>>
```

> This does not generate meta files for part 2, generating errors in running part 3 and above.


1. Sensor brand: 'Actigraph'
2. Data format: 1hz csv
3. Approximate recording duration 10 days
4. Are you using a sleep diary to guide the sleep detection: NO, testing without for the moment.
5. Copy of R command used: Above
6. YES, still does not save meta for part 2
7.

**Expected behavior**
A clear and concise description of what you expected to happen.

**Screenshots**
If applicable, add screenshots to help explain your problem. Note that usually we are not only interested in see the error message in red, but all GGIR output to the console.

**Desktop (please complete the following information):**
 - OS: linxu x86
 - GGIR Version 3.2.6


