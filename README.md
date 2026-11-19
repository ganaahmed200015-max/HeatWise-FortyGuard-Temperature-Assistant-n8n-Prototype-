# 🌡️ HeatWise — FortyGuard Temperature Assistant

A Telegram bot built with n8n that uses the FortyGuard Temperature API to analyze temperature data for a requested time range and provide a short, cautious activity suggestion.

> **Project status: Work in progress.** The current version uses a fixed test area in Miami, Florida. It does not yet support arbitrary locations.

## ✨ Features

- Receives location, date, and time range requests through Telegram.
- Submits a heatmap request to the FortyGuard API.
- Checks the request status until the results are ready.
- Summarizes the returned average, minimum, and maximum temperatures when available.
- Sends the summary back to Telegram.

## 🧰 Tech Stack

- **Automation:** n8n Cloud
- **Messaging:** Telegram Bot API
- **Temperature data:** FortyGuard API
- **AI model access:** OpenRouter
- **Workflow format:** JSON

## 🔄 Workflow

```text
Telegram Trigger
→ AI Agent: extracts the requested date and time range
→ HTTP Request: submits a FortyGuard heatmap request
→ Wait and status check: polls until processing is complete
→ AI Agent: summarizes the returned temperature data
→ Telegram: sends the response

## ⚠️ Current Limitations
- The heatmap area is hard-coded to a small test area in Miami.
- Requests mentioning other locations still receive data for the Miami test area.
- The result summarizes the requested area and time range; it does not necessarily provide hourly readings.
- Suggestions are based on the available temperature data only. The workflow does not assess rain, wind, or other conditions.
- Support for other locations and geocoding is not implemented yet.
## 🚀 Setup
1. Download fortygaurd-project-public.json from this repository.
2. Import the workflow into n8n.
3. Configure your own Telegram, OpenRouter, and FortyGuard credentials in n8n.
4. Review the fixed Miami test polygon and request settings.
5. Test the workflow with a Telegram message.
Never commit API keys, bot tokens, or exported credentials. Add credentials through n8n after importing the workflow.
## 🗺️ Planned Improvements
- Add US location lookup and validation.
- Generate the heatmap area from the resolved location.
- Improve handling of unsupported locations and API errors.
- Add clearer reporting of the analyzed area and available data.
