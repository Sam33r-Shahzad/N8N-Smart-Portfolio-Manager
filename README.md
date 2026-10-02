# Portfolio Manager - n8n AI Agent Workflow

An automated, AI-driven portfolio rebalancing workflow built for [n8n](https://n8n.io/). This workflow uses an LLM agent equipped with market data and spreadsheet tools to automatically read, analyze, and rebalance an investment portfolio based on dynamic user instructions.

---

## Features

* **Dynamic Form Input:** Accepts custom rebalancing instructions directly from a user-submitted form (e.g., target equity-to-fixed-income ratios).
* **Autonomous AI Agent:** Uses OpenAI's `gpt-4o-mini` model configured with up to 80 iterations to calculate exact position changes, update records, and verify that the target allocation has been successfully met.
* **Integrated Tools:**
* **Google Sheets:** Automatically retrieves current portfolio rows and updates quantities, prices, and valuations.
* **Marketstack:** Fetches real-time end-of-day (EoD) asset pricing.
* **Pushover:** Delivers instant mobile push notifications for workflow status updates.
* **Gmail:** Sends a comprehensive email summary outlining the final trading decisions.


* **Automated Validation:** Uses a conditional logic node to verify successful completion and trigger the appropriate success or failure notification.

---

## Prerequisites & Credentials

To run or deploy this workflow, you will need active accounts and credentials for the following services:

1. **n8n Instance** (Self-hosted or Cloud)
2. **OpenAI API**
3. **Google Sheets OAuth2 API**
4. **Marketstack API**
5. **Pushover API**
6. **Gmail OAuth2**

---

## Google Sheets Structure

Ensure your target Google Sheet contains the following columns for proper tool matching and updating:

* `Ticker`
* `Quantity`
* `Equity ratio`
* `Fixed income ratio`
* `Price`
* `Total Value`
* `New Quantity After Rebalancing`
* `New Total Value`

---

## Setup & Installation

1. Clone or download this repository.
2. Open your n8n dashboard and create a new workflow.
3. Click on the options menu (`...`) in the top right corner, select **Import from File**, and upload the `Workflow.json` file located in this repository.
4. Re-authorize your personal credentials (OpenAI, Google Sheets, Marketstack, Pushover, and Gmail) as exported JSON files exclude sensitive keys for security reasons.
5. Update the Google Sheet Document ID inside the Google Sheets nodes if you are using your own custom sheet.
6. Save and activate the workflow.