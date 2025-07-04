# PromotionN8N Workflow Setup Guide

This guide will help you set up and run the PromotionN8N workflow in [n8n](https://n8n.io/). The workflow is designed to automate personalized promotional email campaigns using Google Sheets as the data source and Gmail for sending emails.

---

## Prerequisites

- **n8n Instance:** Make sure you have n8n installed and running. [Installation Guide](https://docs.n8n.io/hosting/installation/)
- **Google Account:** For Google Sheets and Gmail integration.
- **Google Sheets:** Prepare a sheet for products and a sheet for customers.
- **Gmail Account:** For sending emails.

---

## 1. Import the Workflow

1. Download or copy the `Promotion.json` file.
2. In your n8n dashboard, click **Workflows** > **Import from File**.
3. Select the `Promotion.json` file and import.

---

## 2. Set Up Google Credentials

### Google Sheets

1. Go to **Credentials** in n8n.
2. Create new credentials for **Google Sheets OAuth2**.
3. Authorize with your Google account.
4. Share your product and customer Google Sheets with the connected Google account.

### Gmail

1. Create new credentials for **Gmail OAuth2**.
2. Authorize with your Gmail account.

---

## 3. Prepare Your Google Sheets

### Product Sheet

- Must include columns: `name`, `description`, `price`, `sku`, `is_active` (set to `TRUE` for active products).

### Customer Sheet

- Must include columns: `id`, `name`, `email`, `customer_type` (e.g., VIP, Regular, New).

---

## 4. Configure Workflow Nodes

- **ProductSheet** and **CustomerSheet** nodes: Set the correct Google Sheets document and worksheet.
- **Gmail** nodes: Select your Gmail OAuth2 credentials.
- **Google Gemini Chat Model**: If using, set up the required API credentials.
- **Mail Templates**: Review and adjust the email HTML templates in the code nodes if needed.

---

## 5. Run the Workflow

1. Click **Execute Workflow** in n8n.
2. The workflow will:
   - Fetch customer and product data from Google Sheets.
   - Generate personalized promo codes and email templates.
   - Send emails to customers via Gmail.

---

## 6. Customization

- **Email Content:** Edit the code nodes (`templateProduct`, `templateProduct1`) to change the email design or content.
- **Promotion Logic:** Adjust the code in `CampainVIP`, `CampainREG`, and `CampainNEW` nodes for different discount rules or tracking.

---

## Troubleshooting

- Ensure all credentials are correctly set and authorized.
- Make sure your Google Sheets are shared with the service account.
- Check that all required columns exist in your sheets.
- Review node logs in n8n for error details.

---

## Support

For more help, visit the [n8n documentation](https://docs.n8n.io/) or community forums.

---