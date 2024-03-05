
<details>
<summary>Version: 1.0</summary>
<br>
Last Update: Febraruy 16, 2024.
<br><br>
<pre>
## Current Models:
<table>
<tr> 
| Model | Purpose | Notes | Last Update |
|--|--|--|--|
| CodeLlama 13B | Convert question into SQL query | Finetuned with Euroland text-sql database | Feb 2024 |
| Zephyr 7B | For summarizing retrieved data into answer | Not finetuned | Feb 2024 |
| Classifier | assign questions to SQL and Semantic DB | Finetuned mostly with synthetic data | Feb 2024 |
</tr>
</table>

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

</pre>
</details>

---

<details open>
<summary>Want to ruin the surprise?</summary>
<br>
Well, you asked for it!
<br><br>
<pre>
&lt;details open&gt;
&lt;summary&gt;Want to ruin the surprise?&lt;&#47;summary&gt;
&lt;br&gt;
Well, you asked for it!
&lt;&#47;details&gt;
</pre>
