# 🧠 AI PRD Research & Generator

An AI-powered **product research and PRD generation workflow built with n8n, LLMs, JavaScript, and web research**.

The workflow takes a product/company brief, researches the market and users, extracts structured evidence, identifies pain points and unmet needs, discovers product opportunities, performs deeper validation research, and prepares the final PRD for delivery.

---

## 🚀 Project Overview

The goal of this project is to transform a simple product research brief into **evidence-backed product opportunities and a structured PRD**.

The workflow combines:

- **n8n** for workflow orchestration
- **LLMs** for research planning, synthesis, and PRD generation
- **HTTP Requests** for external web research
- **JavaScript** for query generation, batching, and data transformation
- **Structured evidence extraction**
- **Pain-point and opportunity analysis**
- **Deep product validation research**
- **File generation and webhook response**

Instead of directly generating a PRD from a prompt, the workflow follows a research-first approach.

---

## 🔄 Workflow

## 📸 n8n Workflow

![n8n Workflow](docs/n8nworkflow.png)

The overall workflow is:

**Product Brief → Research Queries → Web Research → Evidence → Pain Points → Opportunities → Deep Research → PRD → File Output**

### What happens in the workflow?

1. The workflow receives a product/company research request through a **Webhook**.
2. The request is normalized using **Edit Fields**.
3. An LLM generates research queries across multiple research categories.
4. JavaScript converts those queries into executable search requests.
5. HTTP requests collect external research.
6. Another LLM extracts structured evidence from the research.
7. The workflow synthesizes customer pain points, unmet needs, competitor gaps, and market signals.
8. Product opportunities are generated and scored.
9. A second research phase generates deeper validation queries.
10. Additional web research is performed.
11. The downstream workflow uses the research to generate the final PRD.
12. The generated content is converted into a file and returned through the webhook.

---

# 📥 Input

The workflow starts with a product/company research brief.

Example input from the analyzed execution:

```json
{
  "product_or_company": "District Zomato",
  "market": "Global",
  "additional_context": "Research opportunities to make planning trips with groups easier"
}
