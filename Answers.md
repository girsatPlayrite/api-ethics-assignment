#Task 1 — Classify and Handle PII Fields
The dataset contains the following fields:

full_name, email, date_of_birth, zip_code, job_title, diagnosis_notes

1. full_name
Type: Direct PII
Action: Drop
#Full names uniquely identify individuals and are not necessary for most research purposes. Removing them eliminates a major re-identification risk.
2. email
Type: Direct PII
Action: Drop
#Email addresses are unique identifiers and can directly trace back to individuals. They provide no analytical value in most health research contexts.
3. date_of_birth
Type: Indirect PII
Action: Mask (generalize to age or age range)
#Exact birth dates can enable re-identification when combined with other fields. Converting to age or age bands (e.g., 30–35) preserves analytical value while reducing risk.
4. zip_code
Type: Indirect PII
Action: Mask (truncate or generalize)
#Full ZIP codes can narrow down identity significantly. Using only the first 2–3 digits or mapping to broader regions maintains geographic insights while improving privacy.
5. job_title
Type: Indirect PII
Action: Mask (generalize categories)
#Specific or rare job titles can make individuals identifiable. Grouping into broader categories (e.g., “Healthcare Worker,” “Engineer”) reduces this risk.
6. diagnosis_notes
Type: Sensitive Personal Data (may contain Direct + Indirect PII)
Action: Pseudonymize + Clean (remove identifiers)
#Free-text fields often contain embedded identifiers (names, locations, etc.). 

Task 2 — Audit the API Script for Ethical Compliance

1. Excessive Data Scraping / Ignoring API Limits
Ignore pagination rules (some APIs provide next-page tokens instead)
Breach TOS if bulk downloading is restricted (especially on free-tier keys)

2. Storing Raw Personal Data Without Minimization
Violates data minimization principles
Increases risk of data breaches
May violate API’s data usage restrictions

