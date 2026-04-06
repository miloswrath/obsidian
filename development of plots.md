## Act
---
### Plan
---
- [x] Grab act abstracts into pgdb
- [ ] contract for plots 1/2
- [ ] Build plots 1/2
- [ ] Contract for time series 
- [ ] contract for plot 3
- [ ] build plot 3
- [ ] import hr data
- [ ] build contracts for hr plots 1/2/3
- [ ] run implementation


### DB SCHEMA COMPLETE
---
#### Subject

- **Purpose**: Represents a participant whose actigraphy data appears in the GGIR derivatives
  tree.
- **Key fields**:
  - `subject_id`: Internal primary key
  - `subject_code`: Stable external identifier such as `sub-1001`
  - `created_at`: Record creation timestamp
- **Validation rules**:
  - `subject_code` must be present
  - `subject_code` must be unique within the local dataset
- **Relationships**:
  - One subject has many sessions

#### Session

- **Purpose**: Represents one actigraphy collection session for a single subject.
- **Key fields**:
  - `session_id`: Internal primary key
  - `subject_id`: Foreign key to `Subject`
  - `session_number`: Session identifier derived from the source path
  - `session_date`: Optional first calendar date observed for the session
  - `created_at`: Record creation timestamp
- **Validation rules**:
  - `subject_id` must reference an existing subject
  - `session_number` must be present and positive
  - A subject may have only one record per `session_number`
- **Relationships**:
  - Many sessions belong to one subject
  - One session has many session days

#### Session Day

- **Purpose**: Stores one day of imported actigraphy summary data for a subject session.
- **Key fields**:
  - `session_day_id`: Internal primary key
  - `session_id`: Foreign key to `Session`
  - `day_date`: Calendar date from the source row
  - `weekday`: Day label from the source row
  - `nonwear_minutes`: Derived from source percentage
  - `sleep_minutes`: Imported sleep duration
  - `sedentary_minutes`: Imported sedentary duration
  - `light_pa_minutes`: Imported light activity duration
  - `moderate_pa_minutes`: Imported moderate activity duration
  - `vigorous_pa_minutes`: Imported vigorous activity duration
  - `mvpa_minutes`: Imported MVPA duration
  - `source_file`: Matched GGIR CSV path used for the row
  - `created_at`: Record creation timestamp
- **Required source columns**:
  - `weekday`
  - `calendar_date`
  - `nonwear_perc_day`
  - `dur_spt_min`
  - `dur_day_total_IN_min`
  - `dur_day_total_LIG_min`
  - `dur_day_total_MOD_min`
  - `dur_day_total_VIG_min`
- **Validation rules**:
  - `session_id` must reference an existing session
  - `day_date` must be present and valid
  - Source metric fields must be numeric when provided
  - `nonwear_minutes` must be derived from a percentage in the inclusive range 0-100
  - A session may have only one canonical record per `day_date`
- **Relationships**:
  - Many session days belong to one session


