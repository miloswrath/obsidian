
> *the following notes go over requirements, planning, implementation, and next steps*

---
## Requirements

### data storage and rules
- *Data is stored on the LSS*
- there are supervised, unsupervised, and submax files
- **supervisesd** sessions have various rules as seen in the table below




![[QA Pipeline 2026-01-05 16.33.23.excalidraw]]
![[Pasted image 20260105163317.png]]
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






## TODO 
- move to kde forecast modeling






