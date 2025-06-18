# 📧 GreenTEK x OpenFn – Email Automation Project

This project automates the process of reading, filtering, and logging emails using [OpenFn](https://www.openfn.org), Gmail, and Google Sheets.

---

## 🚨 Problem

Many individuals and NGOs are overwhelmed with too many emails — job applications, requests, spam, and even phishing. There's no structure, and important messages get lost.

---

## ✅ Solution

Using OpenFn's automation tools, this project:

- Automatically fetches recent Gmail messages
- Filters emails into categories:
  - Important (e.g., contains "job", "interview", "application")
  - Suspicious (e.g., contains "verify", "click here", "confirm password")
- Saves email info (subject, sender, snippet) into Google Sheets
- (Optional future step): Sends summary alerts to email or WhatsApp

---

## ⚙️ Tools Used

- Gmail adaptor (OpenFn)
- Google Sheets adaptor
- JavaScript operations (via `fn()`)
- Cron triggers

---

## 🧠 How It Works

Every OpenFn job is a pipeline: 
