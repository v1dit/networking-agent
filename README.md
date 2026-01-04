# Networking Agent — End-to-End AI Outreach Automation

An AI-powered networking agent that automates **personalized professional outreach** end-to-end.

Given a LinkedIn profile URL and a resume, the system:
1. Scrapes and structures the LinkedIn profile
2. Finds and verifies a professional email
3. Generates a personalized outreach message using an LLM
4. Optionally sends the email via Gmail (OAuth-secured)

This project is designed as a **realistic AI agent**, not a toy demo — it integrates multiple external APIs, enforces safety constraints, and supports full orchestration through a single endpoint.

---

## Key Features

- **LinkedIn Profile Parsing**
  - Uses Proxycurl to extract structured profile data
- **Email Discovery & Verification**
  - Combines Hunter + Clearbit with confidence scoring
- **LLM-Powered Email Generation**
  - Context-aware (coffee chat, networking, etc.)
  - Strict prompting to reduce hallucinations
- **Gmail OAuth + Sending**
  - Secure OAuth flow
  - Sends emails directly via Gmail API
- **End-to-End Orchestration**
  - One endpoint runs the full pipeline
- **Hallucination Safeguards**
  - Strict prompt constraints
  - Post-generation validation warnings

---

## End-to-End Flow

LinkedIn URL
↓
Parse Profile (Proxycurl)
↓
Find Email (Hunter + Clearbit)
↓
Generate Email (LLM)
↓
(Optional) Send via Gmail

yaml
Copy code

---

## 📦 Tech Stack

- **Backend:** FastAPI (Python)
- **LLM:** OpenAI (configurable)
- **APIs:** Proxycurl, Hunter.io, Clearbit
- **Email:** Gmail API (OAuth 2.0)

---

## 🔌 API Endpoints

### `POST /demo/run`
Run the **entire pipeline** in one request.

Example:
```json
{
  "linkedin_url": "https://www.linkedin.com/in/...",
  "resume_text": "Computer science student interested in AI and startups.",
  "context": "coffee_chat",
  "tone": "friendly",
  "send": false
}
🛡️ Safety & Hallucination Controls
LLM is forbidden from inventing achievements or projects

Output is grounded only in provided data

Validation warnings are surfaced when assumptions are detected

⚠️ Limitations
No bulk emailing

Rate limiting is minimal

Designed for ethical professional networking

🧪 Running Locally
bash
Copy code
pip install -r requirements.txt
cp .env.example .env
uvicorn main:app --reload
Visit:

http://localhost:8000/docs

yaml
Copy code

⬆️ **END OF WHAT YOU PASTE** ⬆️

---

## 4️⃣ Save the file

---

## 5️⃣ Commit it (this is another counted commit)

```bash
git add README.md
git commit -m "docs: expand README with architecture and API overview"
git push origin main
