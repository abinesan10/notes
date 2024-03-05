
<details open>
<summary><strong>Version: 1.0       Last Update: Febraruy 16, 2024.</strong></summary>
<br>
<details >
<summary><strong>Current Models:</strong></summary>

| Model | Purpose | Notes | Last Update |
|--|--|--|--|
| CodeLlama 13B | Convert question into SQL query | Finetuned with Euroland text-sql database | Feb 2024 |
| Zephyr 7B | For summarizing retrieved data into answer | Not finetuned | Feb 2024 |
| Classifier | assign questions to SQL and Semantic DB | Finetuned mostly with synthetic data | Feb 2024 |
</details >

<details >
<summary><strong>Data Connections:</strong></summary>

- Share Price DB
- Financial Data - EODHD and FMP
- Website texts - Nordea
- Press Releases
- Annual Reports
- Quarterly Reports
- Dividends

</details >

<details>
    <summary><strong>Versioning info</strong></summary>

Once the `versioning` plug-in has been applied, a `versioning` extension is available for the project.

Getting the read-only `ìnfo` provides access to the following information, computed from the SCM information:

Property | Description | Git: `master` | Git: `feature/great` | Git: `release/2.0`
---|---|---|---|---
`scm` | SCM source | `git` | `git` | `git`
`branch` | Branch name | `master` | `feature/great` | `release/2.0`
`branchType` | Type of branch | `master` | `feature` | `release`
`branchId` | Branch as an identifier | `master` | `feature-great` | `release-2.0`
`commit` | Full commit hash | `09ef6297deb065f14704f9987301ee6620493f70` | `09ef6297deb065f14704f9987301ee6620493f70` | `09ef6297deb065f14704f9987301ee6620493f70`
`build` | Short commit/revision indicator, suitable for a build number | `09ef629` | `09ef629` | `09ef629`
`full` | Branch ID and build | `master-09ef629` | `feature-great-09ef629` | `release-2.0-09ef629`
`base` | Base version for the display version | `` | `great` | `2.0`
`gradle` | Project's version |  |  | 
`display` | Display version | `master` | `great` | `2.0.0`, `2.0.1`, ...
`tag` (1) | Current tag | (2) | (2) | (2)
`lastTag` (1) | Last tag | (4) | (4) | (4)
`dirty` | Current state of the working copy | (3) | (3) | (3)
`versionNumber` | Version number containing major, minor, patch, qualifier and versionCode |  |  |  
`versionNumber.major` | Major version | 0 | 0 |  2
`versionNumber.minor` | Minor version | 0 | 0 |  0
`versionNumber.patch` | Patch version | 0 | 0 |  0, 1, 2, ...
`versionNumber.qualifier` | Version qualifier (alpha, beta, engineer, ...)| '' | '' | '' 
`versionNumber.versionCode` | Version code | 0 | 0 |  20000, 20001, 20002, ...

(1) not supported for Subversion
(2) will be the name of the current tag if any, or `null` if no tag is associated to the current `HEAD`.
(3) depends on the state of the working copy the plug-in is applied to. `true` if the working copy contains uncommitted
files.
(4) Name of the last tag on the branch. It can be on the current `HEAD` but not
necessarily - it will be `null` if no previous tag can be found. The last tags are
matched against the `lastTagPattern` regular expression defined in the configuration. It
defaults to `(\d+)$`, meaning that we just expect a sequence a digits at the end
of the tag name.
</details>

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



<details >
<summary><strong>Version: 2.0       Last Update: Febraruy 16, 2024.</strong></summary>
<br>
<details >
<summary><strong>Current Models:</strong></summary>

| Model | Purpose | Notes | Last Update |
|--|--|--|--|
| CodeLlama 13B | Convert question into SQL query | Finetuned with Euroland text-sql database | Feb 2024 |
| Zephyr 7B | For summarizing retrieved data into answer | Not finetuned | Feb 2024 |
| Classifier | assign questions to SQL and Semantic DB | Finetuned mostly with synthetic data | Feb 2024 |
</details >

## Data Connections:

- Share Price DB
- Financial Data - EODHD and FMP
- Website texts - Nordea
- Press Releases
- Annual Reports
- Quarterly Reports
- Dividends

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

