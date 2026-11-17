# IAO — Paris

Training materials and practical exercises with French and English versions. The existing Paris course slides are supplemented with the labs and resources from IAA Metz. The LLM infographic is not included.

## Resources

| Resource | English | French |
| --- | --- | --- |
| Course slides — Paris, 5–6 November 2026 | [PDF](Generative_Artificial_Intelligence_Paris_5-6_November_2026.pdf) | [PDF](IAG_Paris_5-6_Novembre.pdf) |
| Prompting lab | [Notebook](TP_Prompting_English.ipynb) · [Colab](https://colab.research.google.com/github/RMoulla/IAO_Syn/blob/main/TP_Prompting_English.ipynb) | [Notebook](TP_Prompting.ipynb) |
| From needs to specifications | [Skill](SKILL_EN.md) | [Skill](SKILL.md) |
| User story quality audit — n8n | [Workflow](US_Quality_IAA_EN.json) | [Workflow](US_Quality_IAA.json) |
| RAG correction | [Notebook](TP_RAG_Correction_EN.ipynb) · [Colab](https://colab.research.google.com/github/RMoulla/IAO_Syn/blob/main/TP_RAG_Correction_EN.ipynb) | [Notebook](TP_RAG_Correction.ipynb) |
| E-commerce agent with MCP | [Notebook](Copie_de_TP_Agent_LLM_EN.ipynb) · [Colab](https://colab.research.google.com/github/RMoulla/IAO_Syn/blob/main/Copie_de_TP_Agent_LLM_EN.ipynb) | [Notebook](Copie_de_TP_Agent_LLM.ipynb) |
| Real-estate dataset | [CSV](selogerdata.csv) · [English data guide](DATA_EN.md) | Same source dataset |
| Product catalogue (already in English) | [CSV](products.csv) | Same source dataset |


## Download and prepare

Open a file, then select **Download raw file** on GitHub. Preserve filenames and extensions. For Colab, open the link, choose **File → Save a copy in Drive**, connect to a Python 3 CPU runtime, and run cells from top to bottom with **Shift + Enter**. No GPU is required.

For RAG and Agents, add `OPENAI_API_KEY` to **Secrets** in the Colab sidebar and enable notebook access. The notebooks use `gpt-4o`; the n8n workflow uses `gpt-4o-mini`. A valid API key, model access and available API quota are required. API calls may incur charges. Keep your key in Secrets rather than notebook code.

## Prompting and specifications

The Prompting lab contains four exercises: writing and revising a LinkedIn post, comparing prompt tone, extracting structured JSON and analysing a dataset. Copy the prompts into your AI assistant; this lab has no code to execute. For exercise 4, attach `selogerdata.csv` and consult the English data guide for the original column names.

Use `SKILL_EN.md` in a tool that supports Skills, or attach its content to your assistant and ask it to apply the method. It guides an interview of at most five questions and produces specifications with acceptance criteria.

## User story audit with n8n

1. Download and import `US_Quality_IAA_EN.json` into n8n.
2. Select your own OpenAI credentials in **LLM API Call**. No credentials are included.
3. Start a test run and open **User Story Form**.
4. Submit a title and description. Review the five criterion scores, verdict and suggestions.

The result supports a human review; it is not a substitute for it.

## RAG lab

Download the English course PDF from the table and upload it to your Colab session. Opening a notebook does not upload the PDF automatically. Use selectable-text PDFs: these labs do not perform OCR.

For **RAG correction**, run extraction and chunking, embeddings, retrieval, then answer generation. Rename the downloaded course PDF to `Cours.pdf` before uploading it: this is the filename expected by the original correction and its English translation. Change `query` and rerun retrieval and generation to try another question. Use a dedicated Colab runtime: this source lab retains `openai==0.28`. Only the final generation stage needs the API key.


## Agent lab

Download `products.csv` and run sections 1–7 in order. Upload the CSV when prompted. The lab uses the first 1,000 products, builds a FAISS index and creates an MCP server. Check that tool discovery lists `search_products`, `add_to_cart` and `view_cart`.

After “Agent ready.”, rerun only the final cell for each request:

- “I am looking for black men's track pants.”
- “Add two of the first product to my cart.”
- “Show me my cart.”

The output shows MCP calls, tool results and Buddy's replies. The cart is a simulation. Rerunning section 2 empties it; rerunning section 6 resets conversation history. Prices retain the source catalogue format; no currency is assumed.

## Troubleshooting

| Problem | Action |
| --- | --- |
| Missing secret or access denied | Check the exact name `OPENAI_API_KEY` and enable notebook access. |
| Authentication or quota error | Check your API key, model access and API quota. |
| No PDF pages or chunks | Upload a text-based PDF into `/content/`, then rerun loading and indexing. |
| Missing `products.csv` | Upload the file with its exact name, without `(1)` or `.txt`. |
| Unknown variable or import error | Resume in order from the first failing cell; restart the runtime when required. |

Your saved notebook remains in Drive. Uploaded files and installed packages belong to the temporary Colab runtime; upload and install again after a reset.

Contact: **redha.moulla@axia-conseil.com**. Further reading: [Courants de fond](https://redhamoulla.substack.com).
