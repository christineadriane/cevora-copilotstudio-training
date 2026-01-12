# LAB 3 — Add a tool: Prompt Action (“HR Policy Explainer”) to Your HR Agent

*Add a Prompt‑type tool that summarizes an HR policy into a clear, employee‑friendly explanation and wire it into your agent’s conversation flow.*

## Why This Matters

In HR workflows, employees often struggle with long, formal, legal‑style policies.
This tool solves real‑world problems:

- “The policy text is too long.”
- “I don’t understand what steps I need to take.”
- “I need a short answer, not a full 10‑page PDF.”

## 🌐 Introduction
You will create a Prompt action that takes a piece of HR policy text and:
- Summarizes it into employee‑friendly language
- Extracts key steps, eligibility, deadlines, and required documents
- Flags missing information
- Returns a structured, readable HR answer

You will then connect this tool to your HR agent so it can reformat policy text before giving it back to users.

## 🎓 Core Concepts Overview

|Concept|Why it matters|
|--|--|
|Prompt tool|Encapsulates a narrow task so the agent can delegate reliably.|
|Input/output variables|Make tools reusable and testable across topics.||Deterministic formatting rules|Prevents messy outputs and unit chaos.|
|Post‑answer automation|Delivers value immediately after content is generated.|

## 📄 Documentation and Additional Training Links

- [Add tools to custom agents](https://learn.microsoft.com/en-us/microsoft-copilot-studio/advanced-plugin-actions)
- [Use prompts to make your agent perform specific tasks](https://learn.microsoft.com/en-us/microsoft-copilot-studio/nlu-prompt-node)
- [Bring your own model for your prompts](https://learn.microsoft.com/en-us/ai-builder/byom-for-your-prompts)
- [Work with variables](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-variables)

## ✅ Prerequisites

- Agent from [Lab 1](../lab-1-create-agent/README.md) and [Lab 2](../lab-2-extend-knowledge/README.md) available in Copilot Studio.
- Access to Tools with permission to create a Prompt tool.

## 🎯 Summary of Targets

In this lab, you will:
- Create a Prompt action called HR Policy Explainer
- Bind an input variable called policy_text
- Bind an output variable called simplified_policy
- Connect the action to a topic
- Test the action both standalone and in conversation

***

## 🛠️ Instructions

1. In the agent, navigate to **Tools** and select **Add a tool**.
2. In the pop‑up, select **New tool** and choose **Prompt**.
3. Configure the prompt:
   - Rename the tool to `HR Policy Explainer`.
   - Switch the model to `GPT‑4.1`.
   - Paste the following into **Instructions**:
   ```
   You are the HR Policy Explainer. Your single purpose is to transform raw HR policy text into a clear, employee-friendly explanation.
   
   # Task
   Summarize the provided HR policy text into simple, helpful language. Extract all relevant steps, deadlines, eligibility rules, documentation requirements, and exceptions.
   
   # Search Order
   Do NOT search again. Use the given policy text as the single source of truth.
   
   # Steps
   1. Rewrite the policy in clear, friendly, formal HR language.
   2. Provide key points as bullet lists.
   3. Extract eligibility rules.
   4. Extract required documents.
   5. Extract steps the employee must take.
   6. Extract deadlines or submission rules.
   7. Highlight any exceptions or special cases.
   8. If information is missing, state what is unclear.
   
   # Output Style
   Return the result in this structure:
   
   **Summary**
   <short explanation>
   
   **Eligibility**
   - …
   
   **Steps to Follow**
   1. …
   2. …
   
   **Required Documents**
   - …
   
   **Deadlines**
   - …
   
   **Exceptions**
   - …
   
   # Error Handling
   If the policy text is unclear, incomplete, or contradictory, politely say so.
   
   Policy text:
   <policy_text>
    ```
5. Replace `<policy_text>` with a variable of type `Text` (type / to insert the variable).
6. Add sample data to the variable:
   ```
   Employees who are unable to work due to illness must inform their manager before 09:00 on the first day of absence. A medical certificate is required for absences longer than 2 consecutive days. The certificate must be submitted to HR no later than the third day of absence. Sick pay follows company guidelines: the employer covers the first 30 days of sickness, after which statutory benefits apply. Repeated absences may require a return-to-work meeting to discuss support options.
   ```
7. Test the Prompt Action
   - Click Test
   - Ensure the summary is correct
   - Ensure the steps and eligibility are extracted
   - Ensure formatting matches your instructions
   - If needed, refine instruction wording.
8. Select **Save**.
9. On the tool page, select **Add and configure**.
10. Replace the tool description with: `Use this action whenever the agent retrieves a HR policy from knowledge sources. The action will simplify the text into clear steps and eligibility rules.`
8. Change After Running from `Don't respond (Default)` to `Send specific response (specify below)`
9. Set the message to display to `Output.predictionOutput.text`
10. Select **Save**.
11. On the agent **Overview** page, change step 3 in the agents instructions to: `After retrieving any HR policy from a knowledge source, always summarize it using the HR Policy Explainer tool and send the simplified version to the user.`.
12. Refresh the **Test** pane and ask for example: `how do i apply for sick leave?`.
13. Review the response. 

***

**🏅 Congratulations! You’ve completed the Lab 3!**

## 📑 Summary of Learnings

- Small, well‑scoped tools make big UX gains.
- Consistency comes from strict formatting rules, not luck.

## 🔑 Golden rules

- Keep tool instructions single‑purpose and testable.
- Normalize units; don’t invent quantities.
- Always surface a stable output variable.
- Don’t duplicate what the agent already says; augment it.
