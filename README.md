# AI-Powered HTML Email Notification Automation

An end-to-end automation workflow built with **Make.com**, **Airtable**, and **OpenAI**. It automatically transforms raw database records added to Airtable into beautifully formatted, responsive HTML emails generated dynamically by GPT models and delivers them to recipients.

---

## 🚀 Overview & Business Impact

Manual email drafting or sending unstyled, raw database notifications leads to poor user engagement and looks unprofessional. 

This automation solves that problem by:
- Monitoring **Airtable** for new or updated records.
- Sending record metadata to **OpenAI API** with a strictly enforced HTML design system prompt.
- Dynamically generating responsive, beautifully styled HTML emails with proper typography, CTA buttons, and structured lists.
- Dispatching the email seamlessly to the intended recipient.

---

## 🛠️ Tech Stack

- **Workflow Automation:** [Make.com](https://www.make.com/)
- **Database:** [Airtable](https://airtable.com/)
- **AI / LLM Engine:** [OpenAI API](https://platform.openai.com/) (GPT-4o / GPT-3.5-Turbo)
- **Email Service:** Gmail / SMTP Email Module via Make.com

---

## 📐 Architecture & Workflow

```text
┌──────────────┐      ┌──────────────┐      ┌──────────────┐      ┌──────────────┐
│   Airtable   │      │   Make.com   │      │  OpenAI API  │      │  Email Output│
│ (New Record) ├─────►│ (Trigger/FC) ├─────►│ (HTML Prompt)├─────►│(HTML Email)  │
└──────────────┘      └──────────────┘      └──────────────┘      └──────────────┘
```

1. **Trigger (Airtable):** Listens for new entries in a designated view/table.
2. **Processing (Make.com):** Extracts record details (Name, Description, Links, Recipient Email).
3. **Generation (OpenAI):** Calls OpenAI API with raw details and custom system instructions for inline-styled HTML generation.
4. **Delivery (Email):** Sends the clean HTML body via email action.

---

## 🤖 OpenAI System Prompt

The core magic lies in forcing the LLM to output pure, valid inline HTML without Markdown wrappers:

```text
Generate the body of this email as clean, beautifully styled HTML ready for sending.

Formatting rules:
1. Use pure HTML with inline CSS (styles directly within tags).
2. Use a modern, readable font (e.g., font-family: Arial, sans-serif), subtle/neutral colors, and constrain the email container to a maximum width of 600px with proper padding (e.g., 20px).
3. Break the content into short paragraphs. Emphasize key information using bold text or clean bulleted lists (<ul>).
4. If the email includes a call-to-action (CTA), style it as a modern button with a solid background color and white text.
5. Return ONLY the raw HTML code. Do NOT wrap it in Markdown code blocks (like ```html) and do NOT add any introductory or concluding conversational text.
```

---

## 📦 Repository Structure

```text
.
├── README.md               # Project documentation
├── blueprint.json          # Exported Make.com scenario blueprint
└── assets/                 # Screenshots & visual proof
    ├── scenario-make.png   # Make.com scenario visual
    ├── airtable-base.png   # Sample Airtable schema
    └── email-preview.png   # Before vs. After HTML email preview
```

---

## 🔧 How to Set Up

1. **Airtable Setup:**
   - Create a base with fields: `Name`, `Email`, `Details`, `Status`.
   - Create a view filtered for unprocessed records.

2. **Make.com Scenario Import:**
   - Clone this repository.
   - In Make.com, create a new scenario, click **... (More Options)** -> **Import Blueprint**.
   - Select `blueprint.json` from this repo.

3. **Connect API Credentials:**
   - Link your **Airtable** account.
   - Link your **OpenAI API Key**.
   - Configure your **Email / Gmail** module.

4. **Test & Activate:**
   - Run the scenario once with test data in Airtable.
   - Turn on the schedule for automated background runs.

---

## 👤 Author

Created for portfolio demonstration. Feel free to connect or adapt this workflow for your own projects!
