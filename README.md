
# 🔐 LangGraph-Powered call agent Audio Processing Pipeline

A fully automated, secure, and scalable solution to fetch audio files from an SFTP server, transcribe using Groq, analyze via Gemini, and store results in AWS S3, MySQL, and CSV — all built using **LangGraph** for modular flow control.

---

## 📌 Project Overview

This pipeline is designed for enterprise-level use cases (e.g., customer service call audits) where call recordings need to be:

1. **Securely fetched** from a remote SFTP server.
2. **Stored in the cloud** (AWS S3) for durability and access.
3. **Transcribed** using high-performance models (Groq Whisper).
4. **Analyzed** for QA parameters via Gemini (Google's AI).
5. **Logged & stored** in MySQL for downstream dashboards or reporting.
6. **Logged to CSV** for backup or audit trails.

> ⚙️ **Built on LangGraph** to provide step-by-step state management, observability, error isolation, and scalable execution.

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|------|---------|
| **LangGraph** | Orchestrate modular steps with retry/error handling |
| **Groq Whisper** | Fast and accurate transcription of Urdu audio |
| **Gemini 2.5** | Analyze transcripts for compliance and QA |
| **AWS S3** | Cloud storage for original files |
| **MySQL** | Structured storage for call metadata and results |
| **Paramiko** | Secure SFTP connection |
| **Pandas** | Data manipulation for CSV export |
| **dotenv** | Secure environment variable loading |
| **boto3** | S3 client for upload & check |
| **mysql-connector-python** | MySQL access |
| **Python 3.9+** | Core runtime |

---

## ✅ Key Features

- **End-to-End Workflow:** Fetch → Transcribe → Analyze → Upload → Log.
- **LangGraph Controlled:** Modular, traceable, and restartable nodes.
- **Multichannel Logging:** Results stored in both CSV and MySQL.
- **Cloud Native:** Secure upload to AWS S3 with fallback to local.
- **Language Aware:** Transcription and analysis optimized for Pakistani Urdu audio.
- **Error Resilience:** Failure at any step is logged with file context.

---

## 🧠 Our Approach

1. **LangGraph Modularization:** Each step (SFTP, Transcription, Analysis, Storage) is built as a LangGraph node.
2. **Secrets Management:** All credentials (SFTP, AWS, Gemini, DB) are stored in a `.env` file and excluded via `.gitignore`.
3. **Retry-Resilient Logic:** Critical operations like Gemini API calls are retried on transient errors (e.g. 429).
4. **File Safety:** Local audio is only deleted after successful S3 upload.
5. **Transcripts Analyzed, Not Assumed:** Gemini works on intent rather than syntax — ideal for noisy speech-to-text.

---

## 🧾 Folder Structure

```plaintext
📁 project-root/
│
├── 🧠 langgraph_pipeline.py      # Main LangGraph-based entry point
├── 🔑 .env                      # All secrets (never shared)
├── 📦 requirements.txt          # Python dependencies
├── 📘 README.md                 # Project documentation
├── 📄 failed_files.csv          # Optional: Logging for failures
├── 📁 downloaded_audio/         # Local fallback storage
├── 📄 results_structured.csv    # Transcripts and metadata
├── .gitignore                   # Prevents secrets from being committed
