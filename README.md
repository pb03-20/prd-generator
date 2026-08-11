PRD Generator

AI-powered workflow for generating a Product Requirements Document (PRD) from a product/company research brief.

The workflow is implemented in n8n and combines LLM-based research planning, JavaScript processing, web-search HTTP requests, research synthesis, and document generation.

Overview

The PRD Generator accepts a product/company, target market, and additional context through a webhook. It then:

Normalizes the incoming request.

Uses an LLM to generate structured research queries.

Converts those queries into executable search requests.

Performs web research through HTTP requests.

Processes and organizes the collected research.

Uses additional LLM stages to synthesize the research.

Produces the final PRD output.

Converts the result to a text file and returns it through the workflow response.

Workflow Screenshot



The screenshot above shows the n8n workflow structure and the sequence of processing, research, synthesis, and output nodes.

Repository

Repository name: prd-generator

Description:AI-powered Product Requirements Document generator that researches products, market trends, customer pain points, competitors, user behavior, and business strategy to produce structured PRD content.

Input

The workflow starts with a webhook and accepts a JSON payload containing:

{
  "product_or_company": "District Zomato",
  "market": "Global",
  "additional_context": "Research opportunities to make planning trips with groups easier"
}

The execution record confirms that these fields were received by the Webhook node and passed to the next processing stage.

Workflow Architecture

The workflow shown in n8n follows this general pattern:

Webhook
   ↓
Edit Fields
   ↓
LLM — Research Query Generation
   ↓
JavaScript — Query Preparation
   ↓
HTTP Request — Web Research
   ↓
JavaScript — Research Processing
   ↓
LLM — Research Synthesis
   ↓
JavaScript / LLM — Additional Research & Synthesis
   ↓
HTTP Request — Additional Research
   ↓
JavaScript — Final Processing
   ↓
LLM — Final PRD Generation
   ↓
JavaScript — Output Preparation
   ↓
Convert to File
   ↓
Respond to Webhook

The exact n8n canvas contains multiple JavaScript and LLM stages for transforming and synthesizing the research data.

Research Areas

The initial LLM stage generated research queries across these areas:

Company / Product

Product features

Product launch

Product capabilities

Product integrations

Product teardown/reviews

Customer Pain Points

Customer complaints

Product/app issues

Group dining problems

Booking and coordination difficulties

Refund and ticketing issues

Feature Requests

Missing features

User suggestions

Bill-splitting requirements

Group coordination

Itinerary sharing

Competitors

Direct competitors

Feature comparisons

Group dining alternatives

Event-ticketing competitors

Reservation platforms

Market Trends

Dining and experience trends

Social planning

Group travel and dining

Event ticketing

Gen Z activity planning

User Behavior

Group dinner planning workflows

User journeys

Discovery vs. booking behavior

Going-out use cases

Business Strategy

Monetization

Product launch strategy

Business-segment growth

Revenue and acquisition strategy

Example Research Flow

For the supplied execution, the LLM generated multiple search queries for the different research categories. A JavaScript node then transformed those queries into HTTP request payloads, including settings such as:

{
  "search_depth": "basic",
  "max_results": 3,
  "include_answer": false,
  "include_raw_content": false
}

The HTTP research stage returned search results that were subsequently passed through additional processing and LLM stages.

Execution Verification

The supplied execution record reports:

Property

Value

Execution ID

567

Workflow ID

5kHvKq1n2vI7jXZi

Overall status

success

Recorded node count

16

Start time

2026-08-09T16:22:44.501Z

Stop time

2026-08-09T16:22:44.564Z

The execution record contains 16 node entries, and all 16 recorded node entries have executionStatus: "success".

The recorded nodes are:

Webhook

Edit Fields

Message a model

Code in JavaScript

HTTP Request

Code in JavaScript4

Message a model1

Code in JavaScript1

Message a model2

Code in JavaScript5

Message a model3

Code in JavaScript2

Message a model4

Code in JavaScript6

HTTP Request1

Code in JavaScript3

Important execution note

The execution JSON provided for analysis records 16 executed nodes. The supplied n8n screenshot shows a larger workflow canvas, including downstream output nodes such as Convert to File and Respond to Webhook.

Therefore, the statement supported by the supplied execution data is:

The recorded execution completed successfully and all 16 nodes present in that execution record have a success execution status.

It should not be interpreted as proof that every node visible in the screenshot was executed in that particular execution, because the screenshot contains additional downstream nodes that are not present in the 16-node execution record.

Output

The workflow's downstream output section prepares the generated PRD for file conversion and returns the result through the webhook response.

The n8n canvas shows the final stages as:

Final processing
     ↓
Convert to File
     ↓
Respond to Webhook

This makes the workflow suitable for integrating a PRD-generation API into another application or automation.

Technology / Components

n8n — workflow orchestration

LLM / AI model nodes — research-query generation and PRD synthesis

JavaScript Code nodes — transformation, validation, and preparation of workflow data

HTTP Request nodes — external web research

File conversion — prepares the generated PRD as a file

Webhook — API-style workflow entry point and response

Project Goal

The goal of prd-generator is to automate the research-heavy parts of PRD creation so that a product idea can be transformed into structured product research and requirements with minimal manual effort.

For a request such as:

Research opportunities to make planning trips with groups easier.

the workflow gathers evidence around the product, customers, competitors, market, user behavior, and business strategy before using the collected information to generate the PRD.

Documentation

Workflow diagram:

docs/n8nworkflow.png
