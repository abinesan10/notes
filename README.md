<details open>
<summary><strong>Version: 1.0       Last Update: Febraruy 16, 2024.</strong></summary>
<br>

<details>
<summary><strong>Artifacts</strong></summary>

| Base Dir | Sub Dir | Description |
| - | - | - |
| `C:\WISE\PDF` | `adobe_zip\`, `uploaded_pdfs` | Working folder for local files, save pdf/extracted pdfs etc |
</details>

<details> 
    <summary><strong>Application Workflow</strong></summary> <br>
PDF texts:

1) wise_adobe_pdf_extract
2) wise_parse_structured_pdf
3) wise_finalise_pdf_texts

web parsing:

1) wise_get_texts_from_websites
2) wise_finalise_www_texts

Vector DB:

1) wise_upload_data_to_vectordb (upload PDF and WWW texts to vector db)

RestAPI:

1) wise_restapi_main (for serving requests between user - LLM/embedding models - vecotorDB queries)

Embeddings:

1) wise_embedding_prepare_dataset
2) wise_embedding_finetune

Classifier:

1) wise_classifier_prepare_dataset
2) wise_classifier_finetune

Text to SQL

1) wise_sql_to_text_prepare_dataset
2) wise_sql_to_text_finetune

Postgres DB:

Postgres_DB dump for restore
</details>

<details >
<summary><strong>Data Connections</strong></summary>

- Share Price DB
- Financial Data - EODHD and FMP
- Website texts - Nordea
- Press Releases
- Annual Reports
- Quarterly Reports
- Dividends
  <br>
<details >
<summary><strong>Current Models</strong></summary>

| Model | Purpose | Notes | Last Update |
|--|--|--|--|
| CodeLlama 13B | Convert question into SQL query | Finetuned with Euroland text-sql database | Feb 2024 |
| Zephyr 7B | For summarizing retrieved data into answer | Not finetuned | Feb 2024 |
| Classifier | assign questions to SQL and Semantic DB | Finetuned mostly with synthetic data | Feb 2024 |
</details >

</details >

<details>
    <summary><strong>Versioning info</strong></summary>

Once the `versioning` plug-in has been applied, a `versioning` extension is available for the project.

Getting the read-only `ìnfo` provides access to the following information, computed from the SCM information:

Property | Description | `master` | `feature/great` | `release/2.0`
---|---|---|---|---
`branch` | Branch name | `master` | `stage` | `develop`
`Last commit` | Full commit hash | `09ef6297deb065f14704f9987301ee6620493f70` | `09ef6297deb065f14704f9987301ee6620493f70` | `09ef6297deb065f14704f9987301ee6620493f70`
`build` | Short commit/revision indicator, suitable for a build number | `09ef629` | `09ef629` | `09ef629`
`versionNumber` | Version number containing major, minor, patch, qualifier and versionCode |  |  |  
`versionNumber.major` | Major version | 0 | 0 |  2
`versionNumber.minor` | Minor version | 0 | 0 |  0
`versionNumber.patch` | Patch version | 0 | 0 |  0, 1, 2, ...
</details>


<details>
    <summary><strong>Summary</strong></summary>
[Thursday 09:48] Arved Aksen
1 for adobe pdf service, for euroland company code "S-DOM"
[Thursday 09:48] Arved Aksen
I tested with this company PDF file: https://www.dometicgroup.com/globalassets/4-dometicgroup/investors/financial-reports/2023/dometic-q42023-report-eng.pdf?ref=3FD069CB85

[Thursday 09:59] Arved Aksen
currently this API creates C:\WISE\PDF\uploaded_pdfsv + euroland_companycode + pdf file for local pdf copy
[Thursday 09:59] Arved Aksen
and returned .zip file from Adobe service is saved under: C:\WISE\PDF\adobe_zip
[Thursday 10:00] Arved Aksen
2) After running second application: wise_parse_structured_pdf
[Thursday 10:02] Arved Aksen
it has hardcoded conf there, "currently" with data, 
run_conf
[Thursday 10:02] Arved Aksen
we need to make it more practical in the future
[Thursday 10:02] Arved Aksen
so it will take the Adobe zip file, for ex. 
C:\WISE\PDF\adobe_zip\S-DOM\dometic-q42023-report-eng.zip
[Thursday 10:03] Arved Aksen
unzip it and also parse all texts + excels
[Thursday 10:03] Arved Aksen
it will create folder "pages" where all pages are
[Thursday 10:04] Arved Aksen
and finally it will save data in: final_structure.json and parsed_data.json
[Thursday 10:04] Arved Aksen
this C:\WISE\PDF\adobe_zip\parsed_data.json is like conf file for next step which is
[Thursday 10:05] Arved Aksen
3) wise_finalise_pdf_texts
[Thursday 10:06] Arved Aksen
this will split texts into max size so it fits into max sequence lenght (512 this case)
[Thursday 10:06] Arved Aksen
and uploads into database
[Thursday 10:07] Arved Aksen
and finally. 4) wise_upload_data_to_vectordb
[Thursday 10:07] Arved Aksen
this will take the chunks, embedd it with model and upload it vector database
[Thursday 10:07] Arved Aksen
WISE.zip I send has this local embeddings models I used now
[Thursday 10:08] Arved Aksen
ps! dont run adobe pdf parsing service too many times as they have a counter and max limit per month per pages, so its better not to over use it
[Thursday 10:14] Arved Aksen
adobe keys are in the wise_adobe_pdf_extract project folder also, but can you make another account in adobe for same use case

https://developer.adobe.com/

[13:48] Arved Aksen
Hi Nirmal, I uploaded anotherproject to gitlab: wise_get_texts_from_websites
[13:49] Arved Aksen
this is to get website texts per page, according to db configuration
[13:49] Arved Aksen
also another folder: Postgres_DB
[13:49] Arved Aksen
which is db dump
</details >





## System Prompt
You are a helpful assistant. You will answer the user question based on provided context only about the {{company name}}.
last updated: November 2023

## Assistant Prompt
    I am going to ask you a question, which I would like you to answer based only on the provided context below, and do not any other information.  
    Break your answer up into nicely readable paragraphs. Each section starts with "SOURCE" information, provide also details from which source answer was found from. Return only first most relevant answer.  
    Do not use wording \"Based on the provided context\" in your response and answer only question and keep the answer short  
    Dont give any explanations and do not return or mention copy of my original original question, just return me SOURCE information and your answer to my question.  
    If answer is not available in context, just respond "Information missing", do not make up anything.  
    Keep you answer as short as possible and do not add any extra comments, just answer the question based on the context below, do not make up anything. if answer is missing, just answer: Missing information  
      
    #Important Instructions:  
    - Keep you answer as short as possible  
    - Do not use more than 300 words in your Answer  
    - If answer is longer than 300 words, try to summarize it so it fits into 300 words length


</details>
