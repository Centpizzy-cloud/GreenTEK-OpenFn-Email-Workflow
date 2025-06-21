# 📧 GreenTEK x OpenFn – Email Automation Project

This project automates the process of reading, filtering, and logging emails using [OpenFn](https://www.openfn.org), Gmail, and Google Sheets.

---

## 🚨 Problem

Many individuals and NGOs are overwhelmed with too many emails — job applications, requests, spam, and even phishing. There's no structure, and important messages get lost or ignored.

---

## ✅ Solution

Using OpenFn's automation tools, this project:

- Automatically fetches recent Gmail messages
- Filters emails into categories:
  - **Important** – e.g., messages with keywords like _job_, _interview_, _application_
  - **Suspicious** – e.g., messages with keywords like _verify_, _click here_, _confirm password_
- Saves email details (subject, sender, snippet, date) into Google Sheets
- (Coming soon): Sends summary notifications or alerts

---

## ⚙️ Tools & Services Used

| Tool/Service        | Description                         |
|---------------------|-------------------------------------|
| **Gmail**           | Source of emails                    |
| **Google Sheets**   | Destination for email logs          |
| **OpenFn**          | Workflow automation platform        |
| **Adaptors**        | Gmail, Google Sheets, HTTP, Common  |
| **JavaScript `fn()`** | For formatting/filtering logic     |
| **Cron Trigger**    | For daily automation scheduling     |

---

## 🧠 How It Works

Each OpenFn job is a step in the pipeline:

1. **📥 Fetch Emails from Gmail**  
   - Uses keyword filters (subject/body)
   - Only unread and recent messages
2. **🧹 Extract & Format Data**  
   - Pulls: Subject, Sender, Snippet, Date, Message ID
3. **📤 Save to Google Sheets**  
   - Appends formatted data to a connected sheet
4. **(Optional) 🔔 Notify via summary**  
   - Future feature to send alert summaries via email/SMS

---

## 🔄 Workflow Diagram (Simplified)

![image](https://github.com/user-attachments/assets/c2ad6f2b-1cd7-4e16-a832-579d051a0848)


## 🔄 2. Workflow Steps

| Step | Description | Adaptor |
|------|-------------|---------|
| 1️⃣ | Fetch unread Gmail messages with job-related keywords | `@openfn/language-gmail` |
| 2️⃣ | Extract key data from messages | `@openfn/language-common` |
| 3️⃣ | Format the email records | `@openfn/language-common` |
| 4️⃣ | Append formatted data to Google Sheets | `@openfn/language-googlespreadsheet` |
| 5️⃣ | (Optional) Send notifications or summary | `http` or `email` |

---

## 🔑 3. Credentials Used

| Service | Method | Notes |
|---------|--------|-------|
| Gmail | OAuth via OpenFn | Token must be refreshed periodically |
| Google Sheets | OAuth via OpenFn | Ensure permissions are properly granted |

---

## 🧠 4. Code Snippets

### 📥 Fetching Emails

```js
getContentsFromMessages({
  query: 'is:unread (subject:(job OR application OR request) OR body:(job OR application OR request))',
  maxResults: 50,
  contents: ['from', 'date', 'subject', 'body']
});




