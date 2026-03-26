# Goals
---
- Cover basic adherence to exercise 
- Group level analyses
- 2 plots max

## Prompt
---
Help generate ideas for 2 plots for group-level analyses on the following abstract metrics derived from raw HR data (60Hz readings). Below is a short snippet of the csv that contains the files as well as a variable dictionary. MAZD and Trimp are not available at this time.
ONLY GENERATE IDEAS - NO PLOTS
```csv
group,subject,week,session,time_in_allowed_s,time_above_s,time_below_s,longest_bounded_bout_s,bounded_met,mazd,trimp
Supervised,sub8000,1,1,173.0,2228.0,0.0,2401.0,True,,
Supervised,sub8000,1,2,1844.0,557.0,0.0,2401.0,True,,
Supervised,sub8000,1,3,545.0,1848.0,8.0,2393.0,True,,
Supervised,sub8000,1,5,939.0,1376.0,86.0,2315.0,True,,
Supervised,sub8000,2,10,958.0,1404.0,39.0,1338.0,True,,
Supervised,sub8000,2,6,1572.0,801.0,28.0,2373.0,True,,
Supervised,sub8000,2,7,1847.0,474.0,80.0,2321.0,True,,
Supervised,sub8000,2,9,1294.0,1085.0,22.0,2014.0,True,,
Supervised,sub8000,3,12,1791.0,443.0,167.0,2234.0,True,,
Supervised,sub8000,3,13,1640.0,654.0,107.0,2286.0,True,,
Supervised,sub8000,3,14,1609.0,687.0,105.0,704.0,False,,
Supervised,sub8000,3,15,1619.0,679.0,103.0,2298.0,True,,
Supervised,sub8000,4,16,2131.0,184.0,85.0,2200.0,True,,
Supervised,sub8000,4,17,2051.0,22.0,328.0,1230.0,False,,
Supervised,sub8000,4,18,2297.0,0.0,104.0,2164.0,True,,
Supervised,sub8000,4,19,2395.0,0.0,6.0,2395.0,True,,
Supervised,sub8000,4,20,2340.0,54.0,7.0,2394.0,True,,
Supervised,sub8000,5,21,1893.0,0.0,508.0,260.0,False,,
Supervised,sub8000,5,22,1710.0,617.0,74.0,2327.0,True,,
Supervised,sub8000,5,23,2095.0,115.0,191.0,1919.0,True,,
Supervised,sub8000,5,24,2091.0,175.0,135.0,2094.0,True,,
Supervised,sub8000,5,25,2083.0,221.0,97.0,817.0,False,,
Supervised,sub8000,6,26,1454.0,700.0,247.0,2032.0,True,,
Supervised,sub8000,6,27,2037.0,137.0,227.0,2174.0,True,,
Supervised,sub8000,6,28,1961.0,2.0,438.0,1868.0,True,,
Supervised,sub8000,6,29,1999.0,137.0,265.0,2110.0,True,,
Supervised,sub8000,6,30,1961.0,25.0,415.0,1944.0,True,,
Supervised,sub8002,1,1,385.0,2002.0,14.0,2387.0,True,,
Supervised,sub8002,2,10,207.0,2166.0,28.0,2369.0,True,,
Supervised,sub8002,2,6,348.0,2053.0,0.0,2401.0,True,,
Supervised,sub8002,2,7,675.0,2441.0,6737.0,2623.0,True,,
Supervised,sub8002,2,9,314.0,2044.0,43.0,2350.0,True,,
Supervised,sub8002,3,11,484.0,1037.0,880.0,1094.0,False,,
Supervised,sub8002,3,12,241.0,1967.0,193.0,2062.0,True,,
Supervised,sub8002,3,13,109.0,2161.0,131.0,2260.0,True,,
Supervised,sub8002,3,14,95.0,2173.0,133.0,2259.0,True,,
Supervised,sub8002,3,15,619.0,1775.0,7.0,2394.0,True,,
Supervised,sub8002,4,16,167.0,1845.0,389.0,1889.0,True,,
Supervised,sub8002,4,17,327.0,1865.0,209.0,1947.0,True,,
Supervised,sub8002,4,18,318.0,1964.0,119.0,2282.0,True,,
Supervised,sub8002,4,20,217.0,2047.0,137.0,2254.0,True,,
Supervised,sub8002,5,21,1371.0,538.0,492.0,1342.0,False,,
Supervised,sub8002,6,26,1293.0,714.0,5493.0,1022.0,False,,
```
```txt
Zone summary (`~/zone_out.csv`)
-------------------------------
group: Session grouping derived from file path; "Supervised" or "Unsupervised".
subject: Participant identifier (e.g., sub01).
week: Study week number associated with the file; nullable.
session: Session number from filename.
time_in_allowed_s: Seconds of heart rate within the allowed zone.
time_above_s: Seconds above the allowed zone.
time_below_s: Seconds below the allowed zone.
longest_bounded_bout_s: Duration in seconds of the longest continuous bout within the allowed zone (bounded by excursions).
bounded_met: Boolean flag indicating whether the bounded-zone adherence criterion was met.
mazd: Mean Absolute Zone Deviation = (1/T) * sum(|z_i - z_target|); lower values indicate tighter adherence to target zone(s).
trimp: Banister-Edwards TRIMP score computed from resting/max HR and the HR trace; uses pre-trimmed HR (first 45 minutes for supervised; unsupervised = 5 minutes before first in-zone sample + 40 minutes after); higher values indicate greater training load.
```