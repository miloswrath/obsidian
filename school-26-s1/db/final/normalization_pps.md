## Story Problems
>Identifying FDs, normal forms, and then further normalizing
### Example Problem 1: Airline Flights

You are given the relation **FlightRuns** to track airline flights. A **RouteID** defines a fixed route (origin/destination) and a standard scheduled duration. Over time, different aircraft may be used for the same route, but only **one aircraft** operates a specific route on a specific **FlightDate**.

**FlightRuns(AircraftID, RouteID, FlightDate, StdDuration, NumBooked, Seats)**

- **AircraftID**: unique ID for each aircraft
    
- **RouteID**: unique ID for each route (e.g., ORD→LAX)
    
- **FlightDate**: date the flight occurs
    
- **StdDuration**: standard duration for the route (minutes)
    
- **NumBooked**: number of passengers booked for that route on that date
    
- **Seats**: maximum seats on the aircraft
    

**(a)** Identify all non-trivial functional dependencies in **FlightRuns**.  
**(b)** What is the highest normal form satisfied (up to BCNF)? Justify.  
**(c)** If not in BCNF, decompose into BCNF. Justify.


**Response**
*A*
AircraftID, RouteID -> All others
AircraftID -> Seats
RouteID -> StdDuratoin

*B*
1NF, no repeats in tables allowed, each tuple must have unique AircraftID and RouteID. Though, there are partial dependencies (AircraftID, RouteID) and transitive dependencies (RouteID -> AircraftID -> Seats)

*C*
BCNF:
Aircraft(AircraftID, Seats, FK RouteID)
Routes(RouteID, StdDuration)
Scheduled(RouteID, AircraftID, FlightDate, NumBooked)

---

### Example Problem 2: Hospital Surgery Scheduling

You are given the relation **Surgeries** to track surgeries at a hospital. A **ProcedureCode** has a fixed standard duration. A surgeon has exactly one specialty. Each surgery scheduled on a given **SurgeryDate** in a given **OR** (operating room) occurs at a unique **StartTime** and is performed by exactly one surgeon.

**Surgeries(ProcedureCode, SurgeonID, Specialty, OR_ID, SurgeryDate, StartTime, StdMinutes, PatientCount)**

- **ProcedureCode**: unique code for procedure type
    
- **SurgeonID**: unique ID for surgeon
    
- **Specialty**: surgeon’s specialty
    
- **OR_ID**: operating room identifier
    
- **SurgeryDate**: date of surgery
    
- **StartTime**: scheduled start time
    
- **StdMinutes**: standard minutes for the procedure type
    
- **PatientCount**: number of patients in that scheduled surgery (assume 1 normally, but allow >1 for batch procedures)
    

**(a)** Identify all non-trivial functional dependencies in **Surgeries**.  
**(b)** What is the highest normal form satisfied (up to BCNF)? Justify.  
**(c)** If not in BCNF, decompose into BCNF. Justify.

**Reponses**
*A*
SurgeonID -> speciality
ProcedureCode -> StdMinutes
OR_ID, SurgeryDate, StartTime -> ProcedureCode, SurgeonID, PatientCount, StdMinutes, Speciality

*B*
There are both partial (OR_ID, SurgeryDate -> StdMinutes) and transitive (OR_ID,SurgeryData,StartTime -> SurgeonID -> specialty)

*C*
Procedures(ProcedureCode, StdMinutes)
Surgeons(SurgeonID, Specialty)


## FD Problems
---
![[normalization_pps 2025-12-13 17.12.02.excalidraw]]

**R(A, B, C, D, E, F, G)**  
**Q = { A → BC, B → C, CD → E, E → G }**

**R(A, B, C, D, E, F, G)**  
**Q = { AB → CD, A → C, C → D, D → E }**

![[normalization_pps 2025-12-13 17.15.32.excalidraw]]

Consider the relational schema [ A B C D E F G ] with Functional Dependencies  
AB -> CD,  
D -> EF,  
CF -> G,  
FG -> A  
Give all minimal keys for this relational schema
![[normalization_pps 2025-12-13 17.34.13.excalidraw]]

