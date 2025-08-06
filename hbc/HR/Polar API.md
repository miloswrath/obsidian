#act #hr

## Polar Flow AccessLink API

[Official Polar API Documentation](https://www.polar.com/accesslink-api/?srsltid=AfmBOoq7EJHrnuZgP5hzvjp3Bl7ggqsaL8Rbsp5Ni2FkpqYSvRXCu_AQ#polar-accesslink-api)

### Overview:

- [!] **Access Requires Approval:** Integration with Polar Flow AccessLink requires formal permission and API credentials from Polar.
    
- **Real-Time Data Streaming:** Unlike retrospective data exports, the API supports **live heart rate and activity data collection**.
    
- **Authentication:** Uses **OAuth 2.0** for secure user authorization.
    
- **Use Case in #boost:** Continuous heart rate data is gathered over a **6-week period**, including both supervised and unsupervised sessions.
    
    - Enables **real-time monitoring and analytics** during interventions.
        
- **Technical Implementation:**
    
    - A **Node.js API wrapper** is used to interface with AccessLink for live data ingestion.
        
- **API Rate Limits:**
    
    - **500 requests/day** per client, plus **20 requests/day per connected user**.

## Authentication
- [!] The API requires Oauth2 - new territory!!

### Implementation

- [I] _Collecting data and visualizing progress is valuable_
    
    - _However, this may **not be feasible or interpretable during unsupervised sessions**_
        
    - **Note:** Consider privacy, compliance, and technical constraints.
        
- **Co-Design Process:**  
    Collaborate with Olivia and relevant stakeholders to define design and functionality requirements.
    
- **Prototype Testing:**  
    Develop example designs and gather feedback from end users through iterative testing.
    
- **Technical Planning:**  
    Identify necessary **data streams**, required **libraries**, and supporting **packages**.
    
- **Implementation:**
    
    - Use `React` for front-end development.
        
    - Create a `Docker` container for deployment and reproducibility.  
        _(Note: Docker setup will remain free and open-source.)_


## Steps
1. get credentials from Olivia on monday
2. follow the api steps on documentation
3. understand what privileges are given currently and which ones are needed
4. develop around what we have

