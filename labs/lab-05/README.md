# LAB 5 — Intercept "AI‑generated response" and post‑process

*Create a topic that halts auto‑send, extracts HR‑relevant action points from an AI‑generated message, and returns a polished, aggregated response for employees.*

## Why This Matters

Interception gives you editorial control. You can enrich or sanitize before users see the message.

## 🌐 Introduction

In this lab, your HR agent will:
- Intercept an AI-generated response before it is sent.
- Prevent auto‑delivery.
- Run a prompt that extracts the key HR actions from the response.
- Return an aggregated message:
   - the original response from the prompt builder
   - plus a structured list of HR action items or next steps
- This ensures that employees always get clean, actionable guidance.

## 🎓 Core Concepts Overview

|Concept|Why it matters|
|--|--|
|Pre‑send interception|Prevents premature delivery of raw outputs.|
|System variables|Allow control of sending, continuation, and message flow.|
|Structured parsing prompt|Converts free‑form text into actionable lists.|
|Aggregated messaging|Combines original content with value‑add artifacts.|

## 📄 Documentation and Additional Training Links

- [Variables overview](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-variables-about)
- [Work with variables](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-variables)
- [Orchestrate agent behavior with generative AI](https://learn.microsoft.com/en-us/microsoft-copilot-studio/advanced-generative-actions)

## ✅ Prerequisites

- [Lab 3](../lab-03/README.md) tool available or equivalent extraction prompt.
- Permission to create Topics and modify triggers.

## 🎯 Summary of Targets

- Create a topic that intercepts the AI response.
- Populate an input variable with Response.FormattedText.
- Extract HR action points into a variable called hr_action_items
- Send one clean message back to the employee

***

## 🛠️ Instructions

1. Create a new topic: in your Agent navigate to **Topics**, select **Add a topic** -> **From blank**.
2. Change the trigger: Hover near the trigger name → click the double arrows → select:
   - An AI‑generated response is about to be sent
3. Prevent immediate sending
   - Add a Set variable value node:
   - Variable: System.ContinueResponse
   - Value: false
4. Add a Prompt tool
- Add a Tool → Prompt node.
5. Configure the prompt
   - Name: extract_hr_actions
   - Model: GPT‑4.1
   - Instructions:
```
You are an HR action extractor.  
Input is a full assistant message that may include explanations, policies, lists, and HR guidance.

Task: Extract ONLY the concrete HR action items that the employee needs to take. 
Your output must be a clean, bullet-point list. 

Rules:
- Remove all emojis and decorative symbols.
- No policy text, background explanation, or definitions.
- No inventing steps not present in the input.
- If an action is vague in the source (e.g., “submit the form”), do NOT add details unless stated explicitly.
- Merge duplicates.
- Final result = ONLY the employee-facing action list.

Assistant input (verbatim AI response to parse):
<ai_response>

Output: return only the HR action items as formatted text.
```
- Replace <ai_response> with the Text variable you insert using /.
- Use this sample text in the test area:
```
Here is an overview of your parental leave support options:

1. Parental Leave Application
You may submit your parental leave request through the HR Portal. 
Make sure to upload documentation from NAV if applicable.

2. Flexible Working Arrangements
Employees can request temporary flexible working hours during the transition period. 
This requires manager approval.

3. Salary Information
During parental leave you may be entitled to salary compensation according to company policy.
```
- Click Test → verify the output is a clean list of action items.

6. Map variables. In the Prompt node:
   - Map ai_response → Response.FormattedText
   - Create new variable hr_action_items for predictionOutput

7. Add a Message node. Compose the final aggregated message, e.g.:
```
Here is your HR guidance along with clear action items you may need to complete

Original Information:

{System.Response.FormattedText}

Action Items:

{Topic.hr_action_items.text}
```
9. Rename and Save
   - Name it: hr_action_interceptor
   - Save the topic.
10. Test
   - Start a new conversation and try `“How do I apply for parental leave?”`
   - Expect one message that includes both:
   - Original HR explanation
   - Clean extracted action items


### 🧩 (Optional addition) Replace text message with an Adaptive Card
- Follow the same steps as the original lab, but fields now represent:
   - original HR response
   - extracted HR action items
- Example Adaptive Card JSON:
```
{
    "type": "AdaptiveCard",
    "body": [
        {
            "type": "TextBlock",
            "text": "${System.Response.FormattedText}",
            "wrap": true
        },
        {
            "type": "TextBlock",
            "text": "${Topic.hr_action_items.text}",
            "wrap": true
        }
    ],
    "$schema": "https://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.5"
}
```

***

**🏅 Congratulations! You’ve completed the Lab 5!**

## 📑 Summary of Learnings

- How to intercept AI-generated messages before they are sent
- How to transform content into structured action items
- How to aggregate and deliver clean, compliant guidance
- How to use system variables as control switches

## 🔑 Golden rules

- Freeze the response before transforming it
- Keep parsing prompts strict and observable.
- Pass only the required text into the tool.
- Return one consolidated message to avoid spam (Add value, not noise).
- Log all transformations for traceability.
