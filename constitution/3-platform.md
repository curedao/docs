👈 [Back to Table of Contents](../README.md)
# 3. The Software Framework

This chapter describes the functional description of the proposed software framework to be develped in more detail. Scope is the development of an software framework for the aggregation, managing, processing and storage of health data from different sources 

The goal is to achieve better interoperability, portability, availability, analysis, security of the data and to a stable set of software for this basic technology layer suitable for a number of applications that can be built on top of it.

A simplified representation of the Software architecture to be developed can be seen in the following graphic:


![framework diagram](../assets/platform-architecture.png)

The framework consists of two primary components:

1. **Core Framework** - This will be open-source and include only universally necessary features.  This primarily consists of user authentication, data owner access controls, data storage, data validation, and an API for storage and retrieval. The DAO will compensate contributors to the core platform.
2. **Plugins** - These will be modules that provide additional functionality such as data import from specific sources, data mapping to various formats, data analysis, data visualization, notifications. These may be free or monetized by their creator or even be integated into the core based on community voting.

The possibility for development teams to easily create software modules on top of the core framework out of the box opens up the basis for no-code marketplaces for plugins for easier and quicker applications. A widely known successful example is Wordpress and it's plugin ecosystem. An example of an envisioned plugin marketplace is illustrated in the graphic below:

![framework diagram](../assets/plugins/plugin-marketplace.png)

## 3.1 Core Components

### 3.1.1 Data Ingestion API

Challenge: To acquire, extract, transform, and normalize the countless unstandardized data export file formats and data structures and load them into a standardized structure that can be easily analyzed to derive clinical insight.

Approach: Development of an application programming interface (API) and OpenAPI specification for receiving and sharing data with the core database.  Development of Software development kits (SDK’s) made available for 3rd party applications to use to interact with the API. Plugins will enable spreadsheet upload/import and scheduled imports from existing third-party APIs.

Impact: The API connector framework will allow the ongoing regular import of user data after a single user authorization.  SDK’s will enable developers to implement easy automatic sharing options in their applications. An increase in the quantity of data will produce a proportional increase in the number of clinical discoveries made.

Adressed Health Data sources:
- Laboratory and Home tests (Standard Blood panels, Metabolomics, Proteomics, Genetics, Urinalysis, Toxins, etc)
- Wearables (Sleep and Fitness trackers, etc)
- Health apps (Meal tracking, Fertility, etc)
- User reported symptoms and intervention application
- Electronic Heath Records
- Imaging
- Questionnaires
- Functional tests
- Environmental and context data (Exosome)
- Life events, Calendar, Social media and Lifestyle
- Digital biomarkers
- Location

Adressed existing health data formats:
- FHIR
- openEHR
- LOINC
- SNOMED
- RXNORM
- MEddra
- ICD-10
- openMhealth

In theory any kind of generated health data source which could be ingested and saved in an accessible form for further machine analysis to generate more knowledge for the mission described within this paper.


### 3.1.2 Raw Data and Files Storage

To preserve originality in case of data processing errors or protocol changes the ingested raw files like CSV files or PDF reports from the sources and the raw API responses are stored separately in a raw data and file storage.
Data will be encrypted and stored in its raw format in flat files on a secure cloud provider defined in the framework instance platform settings.  Preservation of the data in its original format will allow for:

1. Asynchronous Queued Data Parsing Jobs - This is necessary to allow for the data to be parsed in parallel offline and avoid overloading the webserver.
2. Storage of data incompatible with a time-series relational data store.
3. Storage of data formats that do not yet have defined parser plugins.  This will allow for the data to be imported at a later date when the data mapper has been defined.
4. Updating parsers to support changes in the response format for a particular API.

The original raw data and files can be accessed at any time by the owner, independently from any other process involved with the structured data storage.

### 3.1.3 Data Mappers

To make the standardized stuctured storage of health data and the envisioned queries possible, the data has to be ingested from files or API requests and mapped from many differents standards and proprietary formats into a single purpose built definition.
These will be executed in an asynchronous queue to map the raw data to a standardized format and provide it to the validator.  The most common data mappers will be defined in the framework. Less common data mappers will be available as plugins from 3rd party developers.

Core data mappers (Initial proposal)
- FHIR
- LOINC
- SNOMED 
- RXNORM
- openEHR

The within here proposed format and data standard is built out of existing formats with filled gaps of missing definitions and is defined by the database design and the reference definitions mentioned in the next paragraphs. The goal is to make multi-omics data as well as environmental, social and new types e.g. digital biomarkers quickly accessible and usable for health data analysis.

### 3.1.4. Data Validation

To ensure the quality and consistency of ingested data, the validation in many different aspects is necessary to avoid malformed data entered in the database.

- Allowed biological ranges detect outliers based on value or unit
- Data type checks detect errors from applications or data transfers
- Data deviating from expected formats are filtered
- Duplicated data is ignored

The data validation middleware will validate the data before it is stored in the time series database. The scope is to create this data processing in a peer reviewed and professional way to make this accessible for the use in healthcare and clinical trials.

### 3.1.5. Reference Data Definitions

Mapping data from different formats into a one standardized format suitable for a measurements analysis requires a reference data base with tables of definitions and descriptions to be used by the data mappers and by the API for displaying this information in applications. The type of data to be defined includes biomarkers, health related variables of any kind, interventions, therapies, outcomes, conditions, etc. 

Examples of currently used existing reference databases include LOINC, RXNORM, ICD-10 but are partly not suitable enough and have to be unified for the scope of more efficient data handling and analysis. Especially definitions for environmental factors, natural supplementation or therapies, digital biomarkers and social and lifestyle data sources have a lack of integration.

The proposed solution for overcoming challenges with interoperating with data formats like FHIR is a single Table with all definitions query-able by beforehand mentioned categories and types. The main reason for this solution is the complexity of the nature of the definition of a health related measurement, that can be a observation, a intervention or an predictor. Being the input or the status or the output of the black-box system human body is not that strictly defineable always, so all measured values are thrown in one "pool" and can be queried according to the needs of analysis without having to worry about the aggregation of the data.

### 3.1.6. Time Series Data Storage

After validation and mapping, the data will be stored in a purpose designed database. The storing of standardized and structured time series data requires a purpose built database design to make data access and analysis queries efficient and scalable. Especially with value attachment, decentralized storage and big data in mind the architecture and technology stack used needs to be carefully selected and tested.

Functional Requirements:
- Large scale data storage for time-series data
- Standardized format
- Atomicity
- Data veracity
- Compatibility with value pointing
- Combatibility with decentralized storage
- Safety and Security

This core feature is the center of functionality and used for central storage of platforms or for decentralized storage for users privately.

### 3.1.7. Data Ownership management

Data should be owned and controlled by the person in the whole cycle from generation, while processing until deletion. The end user is put into the center of data management and can access all functionalities necessary for these type of actions. This is the touch point for individuals to their so called health identity. 

Ownership management functionalities will allow the individial to manage their data and access control settings for sharing purposes. It will allow them to:

- View and Access their data
- View the OAuth clients with access to the data
- Modify read/write permissions for specific OAuth clients
- Restrict data access to specific users, groups, researchers or applications
- Restrict data access to specific data categories, types and markers
- Restrict time and expiration of data access
- Configure security measures such as encryption or 2-factor authentication
- Overview of statistics of data (amount, averages, sources, etc..)
- Export stored data or the original files
- Delete data

This feature can be used by user centered applications and dashboards for personal health management, direct sharing with docotrs or research or for participation in trials.

### 3.1.8. Data Value Stream management

Health data is a very sensitive and highly valuable form of personal data of individuals. Many business cases profit from the direct use or further processing  of this data including the individual himself. Therefore the handling of the data alongside its attached value is proposed to be built natively into the core.
Value stream management functionalities will allow the exchange from data against tokenized value assets in different szenarios. It will allow:

- Individuals to share data against specified amounts of compensation
- Groups create and attach insights from grouped data sets to values and exchange to buyers against value assets
- Researchers apply, formulate and visualize values of data sets
- Connect data to value in general for administration purposes
- Applications to create a value based feedback loop for research or behavioral outcomes

Data Value Szenarios:
- Raw data sets or streams of individuals 
- Cohort raw data sets of grouped individuals 
- Interpreted data, scores and recommendations 
- Generated insights and IP out of data analysis
- Specifically aggregated data according requested needs from buyers
- Phentypic, demographic, lifestyle, conditions, environmental context

This feature can be used for exchanging data on marketplace applications or clinical trial platforms.

## 3.2 Plugins

Plugins will be stored in their own repositories based on a plugin template repository.  The plugin template
repository will contain defined interfaces required for interoperability with the core framework.

### 3.2.1 Data Analysis

Challenge: To quantify the effectiveness of treatments for specific individuals, reveal hidden factors exacerbating their illness, determine personalized optimal values for these factors, find new insights and relationships between the variables to create new interventions or protocols for more health

Approach: We will develop time-series machine learning algorithms to

- quantify the effect size of all factors on symptom severity
- determine the optimal dosage or values of health related variables like nutrients or medications.

Impact: This will mitigate the incidence of chronic illnesses by informing the user of symptom triggers, such as dietary sensitivities, to be avoided. This will also assist patients and clinicians in assessing the effectiveness of treatments despite the hundreds of uncontrollable variables in any prescriptive experiment.

### 3.2.2 Data Visualization

Data visualization plugin modules will be utilized to visualize the data from a given subject or group to make insights and correlation visible. The task of such a plugin is to query the data pools with defined filters such as time frames to get to defined data sets and transform them into formats readable by e.g. frontend charting libraries. Some regular ways to visualize data a are Scatter plots, timeline charts, heatmaps or novel ways like the proposed outcome labels in the next paragraph. Visualizations can be displayed in studies, publications or to the end user.

#### Example Visualizations

Currently, all foods carry nutrition labels such as this one:

![](https://crowdsourcingcures.org/wp-content/uploads/2021/02/nutrition-label-436x1024-1.jpg)

But how useful is it to the average person to know the amount of Riboflavin in something? The purpose of nutritional labels is to help individuals make choices that will improve their health and prevent disease.

Telling the average person the amount of riboflavin in something isn’t going to achieve this. This is evidenced by the fact that these labels have existed for decades and during this time, we’ve only seen increases in most diseases they were intended to reduce.

We have created a new and improved **Outcomes Label** that instead lists the degree to which the product is likely
to improve or worsen specific health outcomes or symptoms. We currently have generated Outcome Labels for thousands
of foods, drugs, and nutritional supplements that can be found at [Journal of Citizen Science](https://studies.crowdsourcingcures.org/). These labels are derived from the analysis of 10 million data points anonymously donated by over 10,000 study participants via [our web app](https://app.crowdsourcingcures.org/?swcfpc=1#/app/intro).

![](https://crowdsourcingcures.org/wp-content/uploads/2021/05/nutrition-facts-vs-outcome-labels-melatonin-1024x592.png)

#### Data Quantity Required for Outcome Labels

The Foundation has collected over 10 million data points on symptom severity and influencing factors from over 10,000 people. The Foundation develops and applies predictive machine learning algorithms to the data to reveal the effectiveness and side-effects of treatments and the degree to which hidden dietary and environmental improve or exacerbate chronic illnesses

These analytical results have been used to freely publish 90,000 studies on the effects of various treatments and food ingredients on symptom severity.

![](https://crowdsourcingcures.org/wp-content/uploads/2021/03/johnny-5-need-input.gif)

Although 10 million data points sound like a lot, currently, the usefulness and accuracy of these Outcome Labels are currently limited. This is due to the fact there are only a few study participants have donated data for a particular food paired with a particular symptom. In observational research such as this, a very large number of participants are required to cancel out all the errors and coincidences that can influence the data for a single individual.

For instance, someone with depression may have started taking an antidepressant at the same time they started seeing a therapist. Then, if their depression improves, it’s impossible to know if the improvement was a result of the antidepressant, the therapist, both, or something else. These random factors are known as confounding variables. However, random confounding factors can cancel each other out when looking at large data sets. This is why it’s important to collect as much data as possible.

#### Data Sources for Outcome Labels

Several types of data are used to derive the Outcome Labels:

1. **Individual Micro-Level Data** – This could include data manually entered or imported from other devices or apps in [our app](http://app.crowdsourcingcures.org/?swcfpc=1), This could also include shopping receipts for foods, drugs, or nutritional supplements purchased and insurance claim data.
2. **Macro-Level Epidemiological Data** – This includes the incidence of various diseases over time combined with data on the amounts of different drugs or food additives. This is how it was initially discovered that smoking caused lung cancer. With macro-level data, it’s even harder to distinguish correlation from causation. However, different countries often enact different policies that can serve as very useful natural experiments. For instance, 30 countries have banned the use of glyphosate. If the rates of Alzheimer’s, autism, and depression declined in these countries and did not decline in the countries still using glyphosate, this would provide very powerful evidence regarding its effects. Unfortunately, there is no global database that currently provides easy access to the incidence of these conditions in various countries over time and the levels of exposure to various chemicals.
3. **Clinical Trial Data** – This is the gold standard with regard to the level of confidence that a factor is truly the cause of an outcome. However, it’s also the most expensive to collect. As a result, clinical trials are often very small (less than 50 people). Exclusion criteria in trials often prevent study participants from being representative of real patients. There are ethical considerations that prevent us from running trials that have any risk of harm to participants. Due to the expense involved, we have very few trials run on anything other than a molecule that can be patented and sold as a drug.

### 3.2.3 API Connectors

API Connector plugins will be called by the webserver to:

1. handle the OAuth2 authorization flow and store their credentials in the relational database
2. provide the original raw response to the framework for encryption and storage

A job scheduler will call the API connectors periodically (usually daily) to:

1. Refresh the user's OAuth access token
2. Fetch new data or data that has been modified since the last import
3. Map the response to the standard format as defined by the OpenAPI specification for the framework API
4. Provide the processed data to the framework's validation middleware.
5. All valid data will be stored in the relational database. Otherwise, the data will be rejected and the plugin developer and data owner will be notified.

### 3.2.4 File importer (e.g. Spreadsheets, PDF's, Genomics raw files)

Upon upload, the webserver will call the File Importer plugin:

1. Provide the original file to the framework for encryption and storage
2. Add the file to a queue for processing by the job scheduler
   The background job scheduler will:
3. Retrieve the file from the encrypted storage
4. Extract the data from the file
5. Mapped to the standard format as defined by the framework OpenAPI specification
6. The processed data will be provided to the framework's validation middleware.
7. Valid data will be stored in the relational database.
8. Invalid data from the plugin will be rejected and the plugin developer and data owner will be notified.

## 3.3 Research Platform

### [Next Incentivization](./4-incentivization.md) 👉

<sub><sub>
This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/">Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License</a>.
</sub></sub>
