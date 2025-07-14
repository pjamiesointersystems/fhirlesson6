# Lesson 6: Creating and Updating FHIR Resources via RESTful API

**Author**: Patrick W. Jamieson, M.D.  
**Organization**: InterSystems – Creative Data Technology Curriculum

---

## 🔍 Overview

Lesson 6 introduces students to creating, retrieving, and updating key FHIR resources using RESTful HTTP operations. Students learn how to interact programmatically with a FHIR server by building **Patient**, **Observation**, and **MedicationRequest** resources using HTTP methods such as `POST`, `PATCH`, and `PUT`.

---

## 🎯 Learning Objectives

- Construct valid FHIR-compliant JSON resource bodies for Patient, Observation, and MedicationRequest.
- Understand RESTful operations (`POST`, `GET`, `PATCH`) in the context of FHIR.
- Simulate typical clinical workflows including patient registration, blood pressure capture, and medication ordering.
- Use tools such as Postman, REST Client in VS Code, or curl to interact with FHIR APIs.

---

## 🧰 Repository Contents

| File | Purpose |
|------|---------|
| `patientbodysolution.json` | JSON body for creating a Patient resource |
| `observationbodysolution.json` | JSON body for posting an Observation resource (e.g. blood pressure) |
| `medrequestbodysolution.json` | JSON body for creating a MedicationRequest resource |
| `createpatientsolution.http` | HTTP script to POST a new Patient |
| `createobservationsolution.http` | HTTP script to POST a new Observation |
| `createmedicationreqsolution.http` | HTTP script to POST a MedicationRequest |
| `updateobservationsolution.http` | HTTP PATCH example to update an Observation |
| `patchmedicationreqsolution.http` | HTTP PATCH to update notes in a MedicationRequest |
| `getrequests.http` | HTTP script to retrieve resources (GET by ID, search queries) |
| `fhirheaderendpoint.http` | Sample header template and base endpoint format |
| `FHIRLesson6.pptx` | Slide deck for instructional context and step-by-step walkthrough |

---

## 🏥 Real-World Clinical Workflow Simulated

This lesson models a simple clinical scenario:

1. **Patient Registration**: A patient named Jane L. Smith is created with demographic, contact, and ethnicity/race details:contentReference[oaicite:0]{index=0}.
2. **Vital Signs Recording**: A blood pressure observation with systolic (150 mmHg) and diastolic (95 mmHg) values is captured using the LOINC panel:contentReference[oaicite:1]{index=1}.
3. **Medication Ordering**: A new medication order for Lisinopril 10mg is placed, with dosage instructions and clinical notes:contentReference[oaicite:2]{index=2}.
4. **Resource Updates**: Simulated updates include modifying the observation result or adding rationale to a medication request.

---

## ▶️ Getting Started

### ✅ Prerequisites

- Basic familiarity with REST APIs
- A running FHIR server (e.g., HAPI FHIR, InterSystems IRIS for Health)
- REST testing tool: Postman, REST Client (VS Code), or curl
- Install REST Client extension in VS Code (if using `.http` files)

### 💻 Running the Scripts

1. Configure your base URL and Authorization header in `fhirheaderendpoint.http`.
2. Open each `.http` file in VS Code.
3. Run individual HTTP requests using the **Send Request** button.
4. Monitor server responses and note generated resource IDs for chaining.

---

## 🧪 Resource Examples

### Patient

```json
"resourceType": "Patient",
"name": [{ "given": ["Jane L"], "family": "Smith" }],
"gender": "female",
"birthDate": "1979-08-10"


Observation
json
Copy
Edit
"code": { "coding": [{ "code": "85354-9", "display": "Blood pressure panel" }] },
"component": [
  { "code": { "code": "8480-6" }, "valueQuantity": { "value": 150 } },
  { "code": { "code": "8462-4" }, "valueQuantity": { "value": 95 } }
]
MedicationRequest

"medicationCodeableConcept": {
  "coding": [{ "code": "23488011000036103", "display": "Lisinopril 10 mg tablet" }]
},
"dosageInstruction": [{ "text": "Take one 10mg tablet once daily" }]
🧠 Tips & Insights
Use GET to verify resource creation and IDs before linking.

PATCH is ideal for updating small fields like dosage notes or status.

Follow HL7 coding systems (e.g., LOINC, SNOMED) for semantic consistency.

Review server responses for error codes like 400, 422, or 500.



📦 Attribution
This repository is part of a progressive curriculum teaching hands-on FHIR application development using real-world healthcare data workflows.