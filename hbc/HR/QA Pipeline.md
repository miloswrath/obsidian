#boost #hr

> *the following notes go over requirements, planning, implementation, and next steps*

---
## Requirements

### data storage and rules
- *Data is stored on the LSS*
- there are supervised, unsupervised, and submax files
- **supervisesd** sessions have various rules as seen in the table below

| Week             | %HRmax | Zone  | RPE goal | Feels like                 | Warm Up | Bounded Minutes | Unbounded Minutes | Cool down |
| ---------------- | ------ | ----- | -------- | -------------------------- | ------- | --------------- | ----------------- | --------- |
| **Supervised**   |        |       |          |                            |         |                 |                   |           |
| *1*              | 55-70% | 1 & 2 | 11-12    | Conversation pace          | 5       | 15              | 15                | 5         |
| *2*              | 55-70% | 1 & 2 | 11-12    | Conversation pace          | 5       | 20              | 10                | 5         |
| *3*              | 60-70% | 2     | 11-12    | Conversation pace          | 5       | 25              | 5                 | 5         |
| *4*              | 60-75% | 2     | 12-13    | Comfortable, little harder | 5       | 30              | 0                 | 5         |
| *5*              | 65-75% | 2 & 3 | 12-13    | Comfortable, little harder | 5       | 30              | 0                 | 5         |
| *6*              | 65-75% | 2 & 3 | 12-14    | Comfortable, little harder | 5       | 30              | 0                 | 5         |
| **Unsupervised** |        |       |          |                            |         |                 |                   |           |
| *7*              | 65-75% | 2 & 3 | 12-14    | Comfortable, little harder | 5       | 30              | 0                 | 5         |
| *8*              | 65-75% | 2 & 3 | 12-14    | Comfortable, little harder | 5       | 30              | 0                 | 5         |
| *9*              | 65-75% | 2 & 3 | 12-14    | Comfortable, little harder | 5       | 30              | 0                 | 5         |
| *10*             | 65-80% | 2 & 3 | 12-14    | Comfortable, more harder   | 5       | 30              | 0                 | 5         |
| *11*             | 70-80% | 3     | 13-14    | Comfortable, more harder   | 5       | 30              | 0                 | 5         |
| *12*             | 70-80% | 3     | 13-14    | Comfortable, more harder   | 5       | 30              | 0                 | 5         |
---
- 📈 **Check for extended heart rate elevation**
- 📉 **Check for unreasonably low heart rate for extended periods**
- 🎯 **Ensure goals are met on the low end**  
  _→ Especially during each **supervised** session_
- ⏱️ **Verify bounded minutes**  
  _→ Should be met for both **supervised** and **unsupervised**_
- 📊 **Categorize subjects by adherence**

---

### 💡 **Extras**

- 📋 **Review total adherence numbers**
- 🔄 **Compare supervised vs. unsupervised adherence categories**
- 🧠 **Analyze heart rate deceleration over time**

## planning 

> everything is going to be done at the subject level - not by exercise type

### preprocess the data
- for *supervised* no real work needs to be done - just make sure you are only doing the QCs the middle 30 mins but saving min/max of last 5 for extras tracking
- for unsupervised, many participants don't stop their watches after exercise so there is just a lot of useless data - this needs to be cleaned, it will take looking at the data first tho to understand what is the deadgiveaway. is it always mins 5-35? what else?

### Review Supervised Data
- any missing data?
- extended heart rate elevation (zone 6)
- also any extended low? are they not hitting their zones?
- are the sessio;n goals met (determined by week)
- track adherence for all supervised

### Review Unsupervised 
- missing data?
- extended zone or low?
- goals met? (this is all the same for all unsup sessions)
- track adherence

#### implementation notes 
- need to loop through the files in main first 













