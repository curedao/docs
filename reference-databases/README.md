# Reference Data Sources

The Unified Health API integrates the disparate health data standards in order to accelerate clinical research.

## [Online Data Browser](https://data.crowdsourcingcures.org)

Contact m@thinkbynumbers.org if you desire access.

### [1. Nutritional Supplements](supplements/supplements.md)

### [2. Units of Measurement](units/units.md)

### [3. Medication](medications/medications.md)

### [4. Symptoms and Diseases](diseases/diseases.md)

### [5. Observations, Lab Test Results, and Biomarkers](biomarkers/biomarkers.md)

### 6. Clinical Trials

[AACT](https://aact.ctti-clinicaltrials.org/) is a publicly available relational database that contains all information (protocol and result data elements) about every study registered in ClinicalTrials.gov.

### 7. Medical Codes, Terms, and Synonyms

[The Systematized Nomenclature of Medicine (SNOMED)](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwiP-bmSy8f0AhXxJzQIHZw1DyMQFnoECA4QAQ&url=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FSystematized_Nomenclature_of_Medicine&usg=AOvVaw0OEA6yHcGONHJwDX9OrbKc)  is a systematic collection of medical codes, terms, synonyms and definitions which cover

- anatomy
- diseases
- findings
- procedures
- microorganisms
- substances
- etc.

**SnoMed Databases**

- [SnomedRfsMySql.zip](https://s3.amazonaws.com/static.quantimo.do/unified-health-api/SnomedRfsMySql.zip)
- [snomed-release-service-4.4.0.zip](https://s3.amazonaws.com/static.quantimo.do/unified-health-api/snomed-release-service-4.4.0.zip)

## Data Schema

### Wearables

- [Open mHealth](https://www.openmhealth.org/documentation/#/schema-docs/schema-library) - common schemas define the meaningful distinctions for each clinical measure
- [Apple HealthKit](https://github.com/openmhealth/schemas/tree/develop/schema/granola) - a set of schemas for the Apple HealthKit platform

### EHR

- [FHIR](https://www.hl7.org/fhir/) - a standard for electronic health records
- [openEHR](https://www.openehr.org/) - openEHR is a technology for e-health consisting of open platform specifications, clinical models, and software that together define a domain-driven information systems platform for healthcare and medical research.

## Synthetic Data

- [allergies](https://static.quantimo.do/data/synthetic-data/allergies.csv)
- [careplans](https://static.quantimo.do/data/synthetic-data/careplans.csv)
- [conditions](https://static.quantimo.do/data/synthetic-data/conditions.csv)
- [devices](https://static.quantimo.do/data/synthetic-data/devices.csv)
- [encounters](https://static.quantimo.do/data/synthetic-data/encounters.csv)
- [imaging_studies](https://static.quantimo.do/data/synthetic-data/imaging_studies.csv)
- [immunizations](https://static.quantimo.do/data/synthetic-data/immunizations.csv)
- [medications](https://static.quantimo.do/data/synthetic-data/medications.csv)
- [observations](https://static.quantimo.do/data/synthetic-data/observations.csv)
- [organizations](https://static.quantimo.do/data/synthetic-data/organizations.csv)
- [patients](https://static.quantimo.do/data/synthetic-data/patients.csv)
- [payer_transitions](https://static.quantimo.do/data/synthetic-data/payer_transitions.csv)
- [payers](https://static.quantimo.do/data/synthetic-data/payers.csv)
- [procedures](https://static.quantimo.do/data/synthetic-data/procedures.csv)
- [providers](https://static.quantimo.do/data/synthetic-data/providers.csv)
- [supplies](https://static.quantimo.do/data/synthetic-data/supplies.csv)
