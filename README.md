# 🧠 AI-Powered Interview Prep Workflow (n8n + Gemini + Sheets + Gmail)

An automated AI system for generating **custom interview questions** based on user input via a form. The workflow uses **Google Gemini for intelligent question generation**, stores the results in **Google Sheets**, and sends them to the user via **email** — all orchestrated with **n8n**.

---

## 🎯 Objective

To build an automated pipeline where a user submits a form with their **name, email, role, topic, and difficulty level**, and receives:
- ✅ AI-generated interview questions
- 📩 A personalized email with those questions
- 📊 A logged entry in Google Sheets for future reference

---

## 🧩 Workflow Overview

| Step | Description |
|------|-------------|
| 📝 Form Submission | User fills a form with required details |
| 🤖 AI Agent | Uses Google Gemini Chat Model to generate contextual questions |
| 🧠 Information Extractor | Extracts structured data from AI output |
| 📈 Google Sheets | Stores the generated questions and user metadata |
| ✉️ Gmail | Sends the interview questions to the user's email address |

---

## 📌 Tech Stack

| Tool/Service | Purpose |
|--------------|---------|
| [n8n](https://n8n.io) | Visual automation workflow builder |
| Google Gemini Chat Model | Context-aware question generation |
| Structured Output Parser | Converts AI output into structured format |
| Google Sheets | Stores user data and generated questions |
| Gmail | Sends email to the user |
| Simple Memory Node | Maintains conversation context for AI agent |

---

## 📋 Form Fields (Trigger)

- **Name**: Candidate's name  
- **Email**: Candidate’s email address  
- **Role**: Target job role (e.g., Frontend Developer, Data Analyst)  
- **Topic**: Desired topic for interview questions (e.g., React, SQL, Machine Learning)  
- **Difficulty**: One of `easy`, `medium`, or `hard`  

---

## 🧠 AI Agent Setup

### Prompt (Example):

> "Generate 5 **interview questions** for a candidate applying for the role of a `{{role}}` on the topic `{{topic}}`. Keep the difficulty level `{{difficulty}}`. Output should be in bullet format."

### Output Parser

Ensures output is structured as:
```json
{
  "questions": [
    "Question 1?",
    "Question 2?",
    ...
  ]
}
```
### Output
Google Sheets:

Columns: Name, Email, Role, Topic, Difficulty, Questions (comma-separated)

Email via Gmail:

Subject: Your AI Interview Questions - {{role}}

Body:
Hi {{name}},

Based on your selected topic: {{topic}} and difficulty: {{difficulty}}, here are your AI-generated interview questions:

1. ...
2. ...
3. ...

Best of luck!
