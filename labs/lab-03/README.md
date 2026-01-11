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

- Create a Prompt tool for Shopping List generation using GPT‑4.1.
- Implement normalization to metric units and duplicate merging.
- Verify the tool in isolation and via the agent’s flow.

***

## 🛠️ Instructions

1. In the agent, navigate to **Tools** and select **Add a tool**.
2. In the pop‑up, select **New tool** and choose **Prompt**.
![Select Prompt type](../../assets/3-prompt-tool.png)
3. Configure the prompt:
   - Rename the tool to `Caffio — Shopping List`.
   - Switch the model to `GPT‑4.1`.
   - Paste the following into **Instructions**:
    ```
    You are Caffio’s Shopping List Generator. Your only purpose is to transform a recipe into a formatted shopping list.
    #Task
    Build a shopping list for using the provided recipe. Always assume servings = 5.
    #Search order
    Do not search again. The recipe has already been extracted. Use the given as ground truth.
    #Steps
    Scale all ingredient quantities from the original recipe to 5 servings.
    Normalize units to metric (grams/ml as default; for spices use tsp/tbsp).
    Merge duplicates (e.g., “milk 100 ml” + “milk 50 ml” → “milk 150 ml”).
    Keep ingredient names brand‑agnostic (e.g., “whole milk”, “unsweetened cocoa”).
    Add concise notes if needed for clarity.
    #Output style
    Present the shopping list as a formatted list with: Recipe name, Ingredient, Quantity, Notes.
    After the list, add a short “Substitutions” block if needed.
    No JSON, no extra prose. Just the formatted list
    Recipe:
    <extracted_recipe>
    ```
   - Replace `<extracted_recipe>` with a variable of type `Text` (type / to insert the variable).
   - Add sample data to the variable:
   ```
    Here's a delightful Halloween-themed coffee recipe for you: Pumpkin Patch Latte.
    Ingredients:
    - 1 shot espresso
    - 200 ml steamed milk
    - 2 tbsp pumpkin purée
    - 1 tsp pumpkin spice
    - Ginger cookies
    Preparation Steps:
    1. Whisk the pumpkin purée and pumpkin spice into the espresso.
    2. Add steamed milk and stir gently.
    3. Crush ginger cookies and sprinkle them on top.
    Serving Twist:
    - Serve with a tiny plastic pumpkin on the saucer for a festive touch.
    This recipe brings cozy autumn flavors and a playful Halloween vibe to your cup, making it perfect for spooky gatherings or a seasonal treat at home ​1​.
    Would you like a shopping list for this recipe?
   ```
4. Select **Test** to validate the prompt and view the generated shopping list.
![Test prompt](../../assets/3-test-prompt.png)

5. Select **Save**.
6. On the tool page, select **Add and configure**.
7. Replace the tool description with: `Trigger this tool immediately after the agent has presented a full recipe to the user. Do not run if no recipe was shown or if the user explicitly said they don’t want a shopping list.`
8. Expand Advanced. Select the **Gear** icon next to **Output** variable and update its description: `Shopping list for AI provided recipes`.
9. Select **Save**.
10. On the agent **Overview** page, append to the agent instructions: `After the recipe always prepare and send to the user Shopping List with units`.
11. Refresh the **Test** pane and ask: `Suggest me a Christmas recipe`.
12. Review the response. If asked about a shopping list, agree and examine the generated list. Review the activity, input, and output.
![Test tool](../../assets/3-test-tool.png)

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
