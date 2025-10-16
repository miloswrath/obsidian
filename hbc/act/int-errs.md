8011 - missing one from the lss - not recognizing for some reason
8014 - same as above
8016 - same as above
8030 - missing one file from rdss
	- have 1200 (2025-08-22)RAW.csv, 1200 (2025-05-10)RAW.csv
8031 - says ses 1 / ses 2 are there missing session 3

*TO MOVE*
```
#8011
1151 (2025-09-13)RAW.csv

#8014
1160 (2025-09-11)RAW.csv

#8016
1163 (2025-08-30)RAW.csv



#8031
1201 (2025-09-19)RAW.csv # as session 4
1201 (2025-08-13)RAW.csv # as session 3
1201 (2025-04-23)RAW.csv # as session 2
1201 (2025-02-22)RAW.csv # as session 1 remove current


```

so i've found the basics of what is missing and sort of why, I have a general idea for code diagnosis of why this is, but it will take some more debugging so this will keep happening until I figure it out. It seems to not want to move things because it thinks they are there already. it might label session 3 as session 1 but it already exists and so it doesn't move it

I have the following notes:
- 8011 is missing one from the lss but there are four files from the period. Should i add all 4 and save as session 4?
- 8014 and 8016 only have three files I can transfer these manually now
- 8030 is missing one file from the rdss. I have these right now
	- 1200 (2025-08-22)RAW.csv, 1200 (2025-05-10)RAW.csv
- 8031 also has 4. should i also add all four as session 4 here as well?