# End-User Discovery Agent

**Project Type:** AI Agent / Company Discovery Tool  
**Date:** February 2026  
**Developer:** Dima Alkalfa  

---

## Overview

The **End-User Discovery Agent (ERD)** is an AI-powered agent that discovers, evaluates, and ranks real companies for a given business use-case.  
It focuses solely on company-level discovery and does **not provide contacts or personal information**.  

The agent leverages:

- **Tavily Web Search** for company discovery  
- **Aixplain SDK** for agent creation and reasoning  
- **GPT-4o Mini** for analyzing and scoring relevance  

The output is a **strictly structured JSON** containing:

- `brand_matches`: companies directly relevant to the use-case  
- `category_matches`: companies indirectly relevant or in adjacent industries  

This tool is useful for market research, lead discovery, and identifying relevant business partners.

---

## Features

- Uses **real web data** to identify companies  
- Separates **brand matches vs category matches**  
- Assigns **relevance scores (0-10)** based on criteria such as:
  - Relevance to the domain
  - Alignment with target customers
  - Market presence / credibility
  - Sustainability / innovation fit
- Returns results in **strict JSON format** for easy integration  

---

## Installation

1. Clone the repository:

```bash
git clone https://github.com/Zaatarr/End-User-Discovery-Agent.git
cd End-User-Discovery-Agent

```
2. Install dependencies: (Aixplain's SDK)

```
!pip install -r requirements.txt

```

3. Set your API keys for Aixplain in your environment

```
export AIXPLAIN_API_KEY="your_aixplain_api_key"

```

## Usage
1. Open the main notebook:

```
ERD_Aixplain_project.ipynb

```
2. Update the use-case input in the notebook, for example:

```
USE_CASE_INPUT = """
Domain: Smart Construction Technology

Task: Identify European companies developing AI + IoT solutions
for monitoring construction sites in real-time.

Target: Large construction firms and infrastructure developers in Europe.
"""
```
3. Run the notebook.

4. The agent will produce a JSON output:
```
{
  "brand_matches": [...],
  "category_matches": [...]
}
```
## Example Output
```
{
  "brand_matches": [
    {
      "company": "WatchBuilt",
      "relevance_score": 9,
      "signals": ["IoT-enabled construction monitoring", "Real-time LiDAR tracking"],
      "reason": "Directly addresses the task with specific IoT solutions."
    }
  ],
  "category_matches": [
    {
      "company": "EPIC iO",
      "relevance_score": 7,
      "signals": ["24/7 site monitoring", "Advanced connectivity"],
      "reason": "Focuses on construction security, indirectly relevant."
    }
  ]
}
```
## Notes

* The agent performs a single search per request to Tavily.

* Maximum 5 companies are returned per run.

* The scoring and separation logic is strictly aligned with the ARD (Agent Requirements Document).