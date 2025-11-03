# Entity (Table) Descriptions

- **Patients(PatientID PK, Name, DOB, Phone)**  
    Tracks each person receiving care. One row = one patient.
    
- **Staff(StaffID PK, Position, StaffName, Phone, DOB)**  
    Tracks all personnel employed by the clinic (e.g., admin, aides, therapists). One row = one staff member.
    
- **Therapist(Specialty, StaffID PK/FK → Staff)**  
    Subtype of Staff for clinical providers who deliver therapy. Inherits Staff attributes (StaffID, StaffName, Position, Phone, DOB) and adds **Specialty**.
    
- **Referrals(ReferralID PK, PatientID FK → Patients, DxCode, ReferringProvider, ReferralDate)**  
    Captures inbound referrals for a patient, including diagnosis code, who referred, and the referral date. One row = one referral event.
    
- **Sessions(SessionID PK, PatientID FK → Patients, Therapist [ideally FK → Therapist/Staff], SessionDate, Status, PainPre, PainPost, Notes)**  
    Each therapy visit/encounter for a patient. Records supervising therapist, date, status, pain ratings, and notes.
    
- **Exercises(ExerciseID PK, Name, BodyRegion, Difficulty)**  
    Library of exercises that can be prescribed/performed during sessions.
    
- **SessionExercises(SessionExerciseID PK, SessionID FK → Sessions, ExerciseID FK → Exercises, Sets, Reps, Resistance)**  
    Associative table that logs which exercises were performed in a given session and with what dosage (sets/reps/resistance).
    
- **OutcomeMeasures(OutcomeID PK, PatientID FK → Patients, MeasureName, Score, TakenOn)**  
    Standardized assessments/scores recorded for patients over time.
    

---

# Relationship Descriptions

- **Has (Patients — Referrals)**  
    _Meaning:_ A patient can **have** multiple referrals across time.  
    _Cardinality:_ **Patients 1 — N Referrals** (each referral belongs to exactly one patient).
    
- **Creates (Therapist — Referrals)**  
    _Meaning:_ A therapist (or external provider recorded in `ReferringProvider`) **creates** a referral for a patient.  
    _Cardinality:_ **Therapist 0..N — 0..N Referrals** (in practice: a referral is typically associated with one referrer; if referrers are external, this may be stored as text rather than a FK).
    
- **Attends (Patients — Sessions)**  
    _Meaning:_ A patient **attends** therapy sessions.  
    _Cardinality:_ **Patients 1 — N Sessions** (each session is for exactly one patient).
    
- **Supervises (Therapist — Sessions)**  
    _Meaning:_ A therapist **supervises** (conducts) a session.  
    _Cardinality:_ **Therapist 1 — N Sessions** (each session has one supervising therapist; stored as `Therapist` in the table, ideally a FK to `Therapist/Staff`).
    
- **Contains / ConsistsOf (Sessions — SessionExercises — Exercises)**  
    _Meaning:_ A session **contains** many performed exercises; details (sets/reps/resistance) are captured in `SessionExercises`.  
    _Cardinality:_ Sessions and Exercises are **many-to-many**, resolved via **SessionExercises** into:
    
    - **Sessions 1 — N SessionExercises**
        
    - **Exercises 1 — N SessionExercises**
        
- **Measures (Patients — OutcomeMeasures)**  
    _Meaning:_ Outcome measures **are recorded for** a patient over time.  
    _Cardinality:_ **Patients 1 — N OutcomeMeasures**.
    
- **Specialization / ISA (Therapist ⊂ Staff)**  
    _Meaning:_ **Therapist** is a specialization of **Staff**. Every therapist **is a** staff member and inherits Staff attributes; **Therapist** adds a **Specialty**.

---

# Attribute Descriptions
### IDs (no ambiguity)

- **PatientID (PK)**: System-generated unique identifier for each patient (surrogate key; immutable).
    
- **StaffID (PK)**: Unique identifier for any staff member; reused in **Therapist** to denote therapist subtype.
    
- **ReferralID (PK)**: Unique identifier per referral event.
    
- **SessionID (PK)**: Unique identifier per therapy visit.
    
- **ExerciseID (PK)**: Unique identifier per cataloged exercise.
    
- **SessionExerciseID (PK)**: Unique identifier per exercise instance within a session (not reused).
    
- **OutcomeID (PK)**: Unique identifier per recorded outcome measure.
    

> **Foreign keys**  
> **Referrals.PatientID → Patients.PatientID**; **Sessions.PatientID → Patients.PatientID**;  
> **Sessions.Therapist → Therapist.StaffID** (recommended FK);  
> **SessionExercises.SessionID → Sessions.SessionID**; **SessionExercises.ExerciseID → Exercises.ExerciseID**;  
> **OutcomeMeasures.PatientID → Patients.PatientID**.

### Non-obvious attributes (by table)

#### Staff

- **Position**: Role label (e.g., Admin, PT, PTA); controlled vocabulary recommended.
    
- **Phone**: E.164 format recommended; may include extensions.
    
- **DOB**: Used for HR/verification; consider access controls.
    

#### Therapist (subtype of Staff)

- **Specialty**: Primary domain of practice (e.g., Orthopedic, Neuro).
    
    - _Potentially multi-valued._ Current schema allows **one** specialty; if therapists can have multiple specialties, model with a junction table (TherapistSpecialty).
        

#### Referrals

- **DxCode**: Diagnosis code at referral (ICD-10 string).
    
- **ReferringProvider**: Free-text name or NPI of external provider; if internal, prefer FK to **Therapist.StaffID** (optional dual field strategy).
    
- **ReferralDate**: Calendar date referral was created/received (no time component).
    

#### Sessions

- **Therapist**: Identifier of supervising therapist. **Use StaffID (FK to Therapist)** rather than free text to ensure integrity.
    
- **SessionDate**: Date (and optionally time) of encounter; store timezone if time used.
    
- **Status**: Encounter state; recommended enum: {Scheduled, Completed, Canceled, No-Show}.
    
- **PainPre / PainPost**: Patient-reported pain scores immediately before and after the session.
    
    - Scale should be fixed and documented (e.g., integer 0–10). Consider constraints (0–10).
        
- **Notes**: Unstructured clinical note; consider length limits and privacy tagging.
    

#### Exercises

- **Name**: Short exercise label (e.g., “SLR”).
    
- **BodyRegion**: Controlled vocabulary (e.g., Cervical, Lumbar, Shoulder, Hip, Knee, Ankle).
    
- **Difficulty**: Ordinal scale; define explicitly (e.g., 1–5 or {Easy, Moderate, Hard}); enforce via CHECK.
    

#### SessionExercises (bridge)

- **Sets / Reps / Resistance**: Dosage parameters for the performed exercise.
    
    - **Resistance**: Free text or numeric with unit (e.g., “5 lb”, “Blue band”). If numeric, store unit separately to avoid ambiguity.
        

#### OutcomeMeasures

- **MeasureName**: Assessment instrument label (e.g., “ODI”, “LEFS”, “TUG”). Use controlled list if possible.
    
- **Score**: Numeric or structured string depending on instrument; document allowable ranges per measure.
    
- **TakenOn**: Date assessment was administered (no time unless needed for same-day repeats).
    

### Multi-valued / composite notes

- **Specialty (Therapist)**: _Potentially multi-valued_ in real life; current model treats as single. If multiple specialties are required, add `TherapistSpecialty(TherapistID FK, Specialty)` with unique (TherapistID, Specialty).
    
- No composite attributes are modeled; addresses are not present.
    
- No other multi-valued attributes appear in the ERD; repeated per-session exercises are handled via **SessionExercises** (1-to-many from Session).