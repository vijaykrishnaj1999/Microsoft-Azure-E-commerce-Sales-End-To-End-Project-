# Microsoft-Azure-E-commerce-Sales-End-To-End-Project-
To design and implement a complete, automated Medallion Lakehouse (Bronze, Silver, Gold) on Azure for Adventure Works Sales LT data, using dynamic ADF ingestion, Delta Lake transformations in Databricks, and Synapse-served Gold views for analytics - as my first end-to-end Azure project as a Data Analyst
<img width="1190" height="562" alt="screenshot 0" src="https://github.com/user-attachments/assets/facf732d-1ba9-4e2c-8965-8b39fc437f6b" />

2. ## Structure
I mapped your actual resources from rg-data-engineering-project screenshot:
•	5 services (ADF, Databricks, Key Vault, Storage, Synapse) all in Australia East
<img width="1887" height="720" alt="screenshot 5" src="https://github.com/user-attachments/assets/b9ce0670-fceb-4cbe-9c4f-f1fbd4534d54" />
•	Storage containers silver and gold with _delta_log + snappy.parquet proof
<img width="1911" height="711" alt="screenshot 2" src="https://github.com/user-attachments/assets/98dc71bc-49d6-4372-aee1-ae1d15321f51" />
<img width="1832" height="770" alt="screenshot 3" src="https://github.com/user-attachments/assets/a47962ec-78ac-418b-b75f-6cfa7a1c19e7" />
•	Synapse views dbo.address, dbo.Customer, dbo.Product etc.
<img width="1772" height="742" alt="screenshot 1" src="https://github.com/user-attachments/assets/f57270c4-2e5b-4474-82c8-7b358144d6e6" />

3. ## Pipeline Details (from your 2 pipelines)
•	Pipeline copy_all_tables: Lookup (Look for all tables) -> ForEach Schema Table (Copy Each Table) -> Bronze to Silver Notebook -> Silver to Gold Notebook. Dynamic pattern using @activity('Look for all tables').output.value - no hardcoding.
<img width="1901" height="507" alt="screenshot 4" src="https://github.com/user-attachments/assets/3511b025-acd3-4dec-8e43-e1cdea7ec998" />
<img width="1317" height="342" alt="Screenshot 7" src="https://github.com/user-attachments/assets/73b6b485-c980-46fe-94f6-9dab514635ef" />
<img width="1312" height="351" alt="Screenshot 11" src="https://github.com/user-attachments/assets/fd0cfd03-b4a6-4e06-85da-00d0ec72d41e" />

## Pipeline Creation View
•	Pipeline create view: Get Metadata (Get Tablenames) -> ForEach table name -> Stored Procedure to auto-create Synapse views.
<img width="1257" height="580" alt="screenshot 8" src="https://github.com/user-attachments/assets/9005e5fa-34e8-4360-8dfc-152f81475b68" />
<img width="1320" height="316" alt="screenshot 10" src="https://github.com/user-attachments/assets/3fd05f6b-397a-4b00-9860-3d3ccdde3dd9" />

## Triggers
•	Trigger: Daily 00:25 AM Auckland time, Monitor shows Succeeded in 00:05:45 with 14 activity runs.
<img width="1532" height="865" alt="screenshot 6" src="https://github.com/user-attachments/assets/f1fe540c-bae8-4eab-9d52-dda74eca58f3" />
<img width="1532" height="865" alt="screenshot 6" src="https://github.com/user-attachments/assets/9015f899-bd83-440b-a95f-d6fe89d889ee" />

## Key Highlights (Recruiter bullets)
•	Dynamic ingestion pattern (scalable to 100+ tables)
•	True Delta Lake (your screenshots prove _delta_log)
•	Security with Key Vault kv-mrk-demo-001
•	Analyst-ready Synapse views
•	Cost-aware single-region deployment

## Enhancements - This is critical for you as an Analyst
I split it into 2 parts:
Immediate (Do this before LinkedIn):
•	Add Power BI connected to Gold views (1 dashboard = Sales by Category)
•	Add Data Quality checks in Silver notebook
•	Change to incremental load using ModifiedDate (currently full load)
Advanced:
•	Unity Catalog, CI/CD, Log Analytics alerts, Cost optimization with Job clusters
