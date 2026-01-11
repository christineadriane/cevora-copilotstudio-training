# LAB 2 — Extend knowledge with PDFs
*Enrich the agent with PDF documents, prioritize knowledge from PDFs, and refine instructions for clear sourcing and output quality.*

## Why This Matters
When users ask for HR-related information, you want consistent, complete answers pulled from **your** approved documents, not random web snippets. Prioritizing PDFs yields reliability and repeatability.

Common challenges solved by this lab:

- "Agent mixes partial information from different places."
- "Citations are vague or missing."
- "Too many options; not enough detail."
 
 ## 🌐 Introduction
You’ll update descriptions of existing websites, add PDFs as knowledge, and modify instructions so the agent searches PDFs first for HR-requests. You’ll test the changes and check the status of added documents.

## 🎓 Core Concepts Overview
| Concept | Why it matters |
|----------|----------|
| Knowledge descriptions | Help reviewers understand which source is for what. |
| Document ingestion status | Ensures PDFs are ready before testing behavior. |
| Source prioritization | Drives predictable outputs and consistent citations. |
| Instruction hygiene | Keeps responses short, structured, and well‑sourced. |

## 📄 Documentation and Additional Training Links
- [Knowledge sources overview](https://learn.microsoft.com/en-us/microsoft-copilot-studio/knowledge-copilot-studio)
- [Add knowledge to an existing agent](https://learn.microsoft.com/en-us/microsoft-copilot-studio/knowledge-add-existing-copilot)
- [Generative answers node (citations and summarization)](https://learn.microsoft.com/en-us/microsoft-copilot-studio/nlu-boost-node)

## ✅ Prerequisites
- PDFs downloaded from sample-docs folder.
- An existing agent from Lab 1 with two website knowledge sources.

## 🎯 Summary of Targets
- Update descriptions for existing web sources.
- Add PDFs as knowledge; wait for Ready status.
- Replace or augment instructions to prioritize PDFs for recipes.
- Test that answers cite PDFs first when relevant.

## 🛠️ Instructions
1. Open your Agent and navigate to Knowledge.
2. Open the three‑dot menu for `https://employment.belgium.be/en/themes` and select **Edit**.
3. Update the description to `Use this site for explanations of HR-related rules across Belgium`, then save.
4. Add PDF files as additional knowledge:
   - Select Add knowledge.
   - Select the file downloaded in the Prerequisites section.
   - For the document, set a description such as: `HR policies for Cevora. Mainly use this when asking HR-related questions for the user or within the company`.
   - Select Add to agent.
   - Wait until the document status is `Ready`
5. If needed, update the agent’s instructions to prioritize PDFs:
   - On **Overview** in **Instructions**, select **Edit**, update, and **Save**.
   - If unsure, you can replace the agent’s instructions with the provided template:
```bash
# Purpose
HR-Agent assists employees by providing accurate and clear information about company HR policies, procedures, and employment conditions.

# General Guidelines
- Use a formal but friendly tone in all responses.
- Always search connected knowledge sources before answering, prioritize uploaded PDFs first.
- Summarize information clearly; do not copy raw text.
- Avoid technical jargon unless explicitly asked for deeper detail.
- Include a source with a clickable link for all factual answers.
- Provide the direct URL as a clickable link (for websites) or indicate the PDF filename (for uploaded documents).
- Use short, numbered steps when explaining processes.
- If information is missing, respond with: “I couldn’t find this information in our current documentation. Please contact hr@cevora.be for further assistance with your enquiry.”
- If the user asks about something outside HR, respond with: “I’m HR-Agent, your HR assistant. I can only help with company policies, procedures, and employment-related questions.”
- If asked for something unavailable, acknowledge limits and suggest the closest useful info.

# Skills
- Knowledge retrieval from connected HR documentation.
- Summarization and clear explanation of HR processes.
- Providing structured, step-by-step instructions.

# Step-by-Step Instructions
1. Identify the user query: Determine if the question relates to HR policies, procedures, or employment conditions.
2. Search knowledge sources: Use connected HR knowledge bases or documents to find relevant information.
3. Summarize findings: Present the answer in a concise, clear format, using numbered steps for processes.
4. Include source link: Add a clickable link to the original source for verification.
5. Handle missing information: If no relevant information is found, use the fallback message provided.
6. Handle out-of-scope queries: If the question is unrelated to HR, provide the out-of-scope response.

# Error Handling and Limitations
- If knowledge sources are unavailable, inform the user politely and suggest contacting hr@cevora.be.

# Interaction Example
User: “How do I apply for parental leave?”
Agent: “Here’s how you can apply for parental leave:
1. Complete the parental leave request form.
2. Submit the form to your manager for approval.
3. Send the approved form to HR via email.”
```
7. Test how responses change after these updates
8. If you have some time, test out other knowledge sources and instructions and test!

---

🏅 Congratulations! You’ve completed the Lab 2!

📑 Summary of Learnings
- Treat knowledge like a library with a catalog; descriptions matter.
- Prioritization keeps answers predictable and easier to review.
- PDFs often have more complete, ready‑to‑serve recipes than ad‑hoc web pages.
- Clear sourcing builds trust with readers and reviewers.
