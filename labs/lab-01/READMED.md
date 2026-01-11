# LAB 1 — Create an agent in Copilot Studio with public weblinks as knowledge
*Build a Copilot Studio agent, give it clear operating instructions, and connect two public websites as knowledge sources.*

## Why This Matters  
For makers building their first production‑ready agent: getting the basics right saves you from chaotic behavior and inconsistent answers. An agent with explicit scope, tone, and guardrails is faster to test and safer to ship.

Common challenges solved by this lab:

- "The agent wanders off topic."
- "Responses feel random or too technical."
- "No citations or unclear sourcing."
- "I don’t know where to put behavior rules."

## 🌐 Introduction
You’ll stand up a focused agent called Caffio. It behaves like a friendly coffee expert and recipe assistant. You’ll author explicit instructions (scope, tone, behavior, and tasks) and connect two public websites as knowledge sources. You’ll also map the agent to a solution via advanced settings and validate the conversation in the Test pane.

## 🎓 Core Concepts Overview
| Concept | Why it matters |
|----------|----------|
| Agent instructions | Set the non‑negotiables: scope, tone, behavior rules, and tasks to guide every response. |
| Knowledge sources  | Provide the factual backbone so the agent can cite and summarize reliable content.  |
| Solution mapping  | Keeps assets organized for ALM, transport, and environment hygiene. |
| Test pane  | Test pane	Fast feedback loop for validating behavior before going live. |

## 📄 Documentation and Additional Training Links
- [Microsoft Copilot Studio documentation hub](https://learn.microsoft.com/en-us/microsoft-copilot-studio/)
- [Write agent instructions](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-instructions)
- [Knowledge sources overview](https://learn.microsoft.com/en-us/microsoft-copilot-studio/knowledge-copilot-studio)
- [Solutions in Power Apps](https://learn.microsoft.com/en-us/power-apps/maker/data-platform/solutions-overview)

## ✅ Prerequisites
- A prepared workshop environment, or the ability to create a new one per prerequisites.
- Access to an environment in make.powerapps.com with permissions to create solutions and agents.

## 🎯 Summary of Targets
In this lab, you will:
- Create a new Solution for workshop assets.
- Create an Agent with defined scope, tone, behavior rules, and tasks.
- Add two web knowledge sources and descriptions.
- Map the agent to your Solution using Advanced Settings.
- Validate the agent’s answers using the Test pane.

## 🛠️ Instructions
1. Navigate to [make.powerapps.com](make.powerapps.com), sign in, and open the environment you prepared for the workshop. If you haven’t prepared it yet, create a new environment as described on the [prerequisite page](https://github.com/christineadriane/cevora-copilotstudio-training/tree/main/labs/lab-00).
2. Create a new solution. Name it `HR-Agent`.
3. Navigate to https://copilotstudio.preview.microsoft.com/ and select the `Advance Create`.
   ![Advanced Create](https://github.com/christineadriane/cevora-copilotstudio-training/blob/main/resources/AdvancedCreate.png)
5. Select language (the main language can not be changed after creation).
6. Select the `Solution` you just created in step 2.
7. Select a Scehma Name. The schema name is independent of your agent's display name.
8. `Confirm and create`
9. You have created an agent and it should look something like this:
   ![Advanced Create](https://github.com/christineadriane/cevora-copilotstudio-training/blob/main/resources/AgentCreation.png)
10. Test the agent in the right‑hand Test pane.

### Configuration of the newly created agent
1. Change name to HR-Agent (or something else fitting)
2. Enter the following description:
   ```bash
   This agent is a HR assistant designed to help users quickly find answers to common HR questions.
   It retrieves grounded information from the HR knowledge base and guides employees through typical HR processes.
   ```
4. Enter the following instructions:
   ```bash
   # Purpose
   HR-Agent assists employees by providing accurate and clear information about company HR policies, procedures, and employment conditions.

   # General Guidelines
   - Use a formal but friendly tone in all responses.
   - Always search connected knowledge sources before answering.
   - Summarize information clearly; do not copy raw text.
   - Include a source with a clickable link for all factual answers.
   - Use short, numbered steps when explaining processes.
   - If information is missing, respond with: “I couldn’t find this information in our current documentation. Please contact hr@cevora.be for further assistance with your enquiry.”
   - If the user asks about something outside HR, respond with: “I’m HR-Agent, your HR assistant. I can only help with company policies, procedures, and employment-related questions.”
   
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
5. In `Knowledge` add a ublic website and use this link: - https://employment.belgium.be/en/themes
6. Test the agents with the new information 

---

#### 🏅 Congratulations! You’ve completed the Lab 1!

## 📑 Summary of Learnings
- Scope before style: a tight scope prevents drift.
- Grounding is a feature: explicit knowledge sources raise answer quality.
- Organize assets: mapping to a solution helps with ALM and governance.
- Test early and often: use the Test pane to catch issues before release.

## 🔑 Golden rules
- Author instructions that are short, testable, and source‑aware.
- Ground answers in curated sites; require citations.
- Validate redirect behavior with off‑topic prompts.
- Store the agent in a Solution for lifecycle management.
