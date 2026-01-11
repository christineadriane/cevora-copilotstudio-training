# LAB 4 — Add a Power Automate Flow: “Register Leave Request (SharePoint)”

*Add a flow‑based action that validates basic leave details and registers the request in a SharePoint list, then returns a confirmation (ID + summary) to the agent.*

## Why This Matters

When a copilot can trigger a Power Automate flow and write structured data into a system like SharePoint, it becomes a:
- Transactional system, not just a Q&A bot
- Workflow initiator
- Business process accelerator
- Consistent intake mechanism for data
- Safe and governed bridge between conversation and actual work

## 🌐 Introduction

You’ll create a Power Automate flow that:
- Accepts inputs from the HR agent (employee name, leave type, start/end date, reason)
- Optionally performs simple validation (dates, duration)
- Creates a new SharePoint list item (“LeaveRequests”)
- Returns structured outputs: request ID, summary, next steps

Then you’ll connect it to your HR‑Agent as a Flow Action and wire it into a “Request leave” topic.

## 🎓 Core Concepts Overview

|Concept|Why it matters|
|--|--|
|Flow action|Encapsulates the business process (create SharePoint item) with validation + outputs.|
|Inputs/outputs|Make the action reusable across leave scenarios.|
|Copilot → Flow → Copilot|Server‑side processing + clean confirmation back to the user.
|SharePoint list|Central, auditable store that HR can manage without code.|

## 📄 Documentation and Additional Training Links

- [Event triggers overview](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-triggers-about)
- [Office 365 Outlook connector](https://learn.microsoft.com/en-us/connectors/office365/)
- [Email triggers in Power Automate - When a new email arrives (V3)](https://learn.microsoft.com/en-us/power-automate/email-triggers)

## ✅ Prerequisites

- Working agent from [Lab 1](../lab-01/README.md) and [Lab 2](../lab-02/README.md) [Lab_3](../lab-03/README.md).
- Power Automate enabled; DLP allows SharePoint connector
- A SharePoint site to host the list (e.g., “HR Operations Demo”)
- Permission to create lists and flows in the environment

## 🎯 Summary of Targets

- Create a SharePoint list named LeaveRequests
- Define a Power Automate flow triggered by Copilot
- Add inputs: employee_name, leave_type, start_date, end_date, reason
- Create a list item; return outputs: request_id, summary, next_steps
- Bind the flow as an action in the HR agent
- Test in isolation and conversation

***

## 🛠️ Instructions


***

**🏅 Congratulations! You’ve completed the Lab 4!**

## 📑 Summary of Learnings

- Copilot Studio can register HR requests via Power Automate flows
- Inputs/outputs make actions reusable across topics
- Returning results to Copilot gives users a clear confirmation

## 🔑 Golden rules

- Single‑purpose flow: Create item + respond; keep logic simple
- Validate inputs: Dates, leave type (avoid bad data)
- Stable outputs: Always return ID + summary + next steps
- Governance: Keep the flow + list inside a Solution

## 🧩 Optional Extensions

- Add Approvals (Power Automate) to move Status → Approved/Rejected
- Create an Adaptive Card in Teams to show the confirmation neatly
- Add email notifications to HR/shared mailbox with the request details
- Include duration calculation and reject if end_date < start_date

