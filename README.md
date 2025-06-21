# 📧 GreenTEK x OpenFn – Email Automation Project

This project automates the process of reading, filtering, and logging emails using [OpenFn](https://www.openfn.org), Gmail, and Google Sheets.

---

## ✅ Update Summary – June 2025

After testing and refining the automation pipeline, the following improvements were made:

### 🔄 Changes & Fixes
- 🛠 **Fixed crash errors** caused by undefined `filteredEmails` using a safe fallback.
- ✅ Added a logic check before pushing to Google Sheets to avoid `map()` errors when no emails are found.
- 🧠 Improved the data extraction logic to ensure consistent formatting from Gmail message contents.
- 📋 Updated the Google Sheets adaptor job to use `appendValues()` instead of the incorrect `updateValues()`.

### 😮 Challenges Encountered
- Emails weren’t being picked up initially — caused by no matching Gmail query results (like no unread job-related messages).
- Runtime errors occurred due to `.map()` being used on `undefined` — solved by setting a default empty array and conditionally checking.
- Confusion between adaptor function names (`appendValues` vs `updateValues`) — clarified through documentation and error logs.
![image](https://github.com/user-attachments/assets/f71fb9a9-6fc2-490e-93ea-cd03ab3c05b3)

![image](https://github.com/user-attachments/assets/4a7c3837-19fb-4913-8000-b95f9d196f0f)



---

## 🧠 What I Learned
- Understanding how **`state` flows across OpenFn jobs** is crucial for error-free automation.
- Simple checks like `if (!state.filteredEmails)` can save your entire pipeline from breaking.
- The importance of **reading adaptor documentation** to understand function behavior.
- OpenFn's logs and error tracebacks are super helpful when debugging!

---

## ⚙️ Workflow Overview

| Step | Description |
|------|-------------|
| ✅ **Job 1:** Fetch unread Gmail messages matching keywords like "job", "application" |
| ✅ **Job 2:** Extract subject, sender, date, body snippet, and create Gmail link |
| ✅ **Job 3:** Append formatted rows to Google Sheet for easy review & tracking |

---

## 🔗 Spreadsheet Output Example

| Date | From | Subject | Body Preview | Message ID | Gmail Link |
|------|------|---------|---------------|------------|-------------|
| 2025-06-22 | hr@company.com | Job Application | Thank you for applying to... | 17e4a8... | [Open](https://mail.google.com/mail/u/0/#inbox/... |

---

## 🙌 Next Steps
- Add logic to detect **phishing or scam** messages based on suspicious keywords
- Build in **SMS or email alerts** for specific types of urgent messages
- Offer this as a **template** for NGOs and small orgs struggling with email overload

---

## 👤 Built by Innocent Ikuku  
Founder @ **GreenTEK Digitals**  
OpenFn Affiliate Partner | DevOps | Cloud & Cybersecurity Explorer  
