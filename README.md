# n8n Smart Decision-based Email Automation 📧

An n8n workflow that automates priority-based email notifications from Google Sheets using conditional logic and switch-case routing.

## Overview

This workflow demonstrates decision-based automation: when a new row is added to a connected Google Sheet, the workflow evaluates the `Priority` field and sends a tailored email depending on whether the task is **High**, **Medium**, **Low**, or **Lowest** priority.

## Workflow Diagram 🖼️

<img width="958" height="449" alt="Smart Decision-based Automation" src="https://github.com/user-attachments/assets/f3d537fb-f811-4cfe-9f4f-a5279f4b9851" />


## How It Works ⚙️

1. **Google Sheets Trigger** — Watches a spreadsheet and fires when a new row is added
2. **If Node** — Checks whether `Priority` equals `High`
   - **True** → sends an urgent email immediately
   - **False** → passes to the Switch node for further routing
3. **Switch Node** — Routes based on `Priority` value:
   - `Medium` → sends a medium-priority email
   - `Low` → sends a low-priority email
   - `Lowest` → additional branch for lowest-priority handling

```
Google Sheets Trigger → If → (High → Send Email)
                            → (Else → Switch → Medium/Low/Lowest → Send Email)
```

## Tech Stack 🛠️

- [n8n](https://n8n.io/) — workflow automation platform
- Google Sheets API — data source / trigger
- Gmail API — email delivery

## Setup Instructions 🚀

1. Clone this repository
   ```
   git clone https://github.com/Hamza07-debug/n8n-smart-decision-email-automation.git
   ```
2. Open your n8n instance and go to **Workflows → Import from File**
3. Import `Smart_Decision_Automation.json`
4. Connect your own **Google Sheets** and **Gmail** OAuth credentials in the respective nodes
5. Set the `documentId` in the Google Sheets Trigger node to your own spreadsheet
6. Ensure your sheet has columns: `Name`, `Email`, `Task`, `Priority`
7. Activate the workflow

## Security Note 🔒

All spreadsheet IDs, credential references, and instance identifiers have been removed or replaced with placeholders. You must connect your own Google Sheets and Gmail credentials before running this workflow. The workflow is set to inactive by default for safety.

## Future Improvements 💡

- Add a "High" case within the Switch node for full parity with the If branch
- Use HTML email templates for better formatting
- Log sent notifications back to the sheet
- Add a Slack or Teams notification branch alongside email

## Author

**Muhammad Hamza Afzaal**
[GitHub](https://github.com/Hamza07-debug)
