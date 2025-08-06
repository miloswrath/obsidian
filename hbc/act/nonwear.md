# nonwear detection using advanced  sleep log

## formatting
| ID  | D1_date    | D1_wakeup | D1_inbed | D1_nap_start | D1_nap_end | D1_nonwear1_off | D1_nonwear1_on | D2_date    | …   |
| --- | ---------- | --------- | -------- | ------------ | ---------- | --------------- | -------------- | ---------- | --- |
| 123 | 2015-03-30 | 09:00:00  | 22:00:00 | 11:15:00     | 11:45:00   | 13:35:00        | 14:10:00       | 31/03/2015 | …   |
| 567 | 2015-04-20 | 08:30:00  | 23:15:00 |              |            |                 |                |            |     |

this is an example of what an advanced log looks like

```csv
Date/Time Start,Date/Time Stop,Wear or Non-Wear,Length (minutes),Use?
3/10/2020 12:00 AM,3/10/2020 7:04 AM,Non-Wear,424,FALSE
3/10/2020 7:04 AM,3/14/2020 3:41 AM,Wear,5557,TRUE
3/14/2020 3:41 AM,3/14/2020 3:59 AM,Non-Wear,18,FALSE
3/14/2020 3:59 AM,3/18/2020 12:00 AM,Wear,5521,TRUE

```

example of what the nonwear logs look like on `rdss`
- [i]  The data does have unneededlines above this - which would need to be parsed out dynamically - since they aren't all the same length