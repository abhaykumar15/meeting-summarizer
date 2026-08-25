

https://github.com/user-attachments/assets/23c33260-d576-46fb-96bc-86a51438f96b







# MeetFlow — AI Meeting Summarizer

> Transform recorded meetings into concise summaries, key decisions, action items, and searchable transcripts.

## 🎥 Working Demo

<p align="center">
  <a href="https://youtu.be/Rfiw1qawgho">
    <img src="https://img.youtube.com/vi/Rfiw1qawgho/maxresdefault.jpg" alt="MeetFlow Working Demo" width="850">
  </a>
</p>

<p align="center">
  <a href="https://youtu.be/Rfiw1qawgho"><strong>▶ Watch the complete working demo</strong></a>
</p>

---

## 📌 Overview

MeetFlow is an AI-powered meeting summarization application that converts recorded meeting audio into structured and actionable information.

Instead of manually reviewing an entire recording, the application processes the meeting, generates a transcript, and produces useful meeting insights such as:

- Executive summary
- Key decisions
- Action items
- Available action-item owners
- Available due dates
- Full transcript
- Meeting history

The application provides a simple web interface while the backend handles audio processing, transcription, AI-based analysis, and persistence.

---

## ✨ Features

### 🎙️ Meeting Recording Upload
Upload supported meeting audio/video recordings directly through the web interface.

### 📝 Automatic Transcription
The application uses **Faster-Whisper** to convert spoken content into text.

### 🧠 AI Meeting Analysis
The generated transcript is processed by the configured **Groq-powered language model** to extract structured meeting insights.

### 📋 Executive Summary
Generates a concise overview of the meeting discussion.

### ✅ Key Decisions
Identifies important decisions made during the meeting.

### 📌 Action Items
Extracts tasks from the discussion and displays available:
- Task
- Owner
- Due date

### 📜 Full Transcript
Provides access to the complete generated transcript.

### 🗂️ Meeting History
Previously processed meetings are stored and can be reopened from the history section.

### 📱 Responsive Interface
The frontend is designed to work across desktop and smaller screen sizes.

---

## 🏗️ Architecture

```text
                    ┌──────────────────────┐
                    │      MeetFlow UI     │
                    │ HTML / CSS / JS      │
                    └──────────┬───────────┘
                               │
                         HTTP / REST API
                               │
                               ▼
                    ┌──────────────────────┐
                    │    FastAPI Backend   │
                    └──────────┬───────────┘
                               │
                  ┌────────────┴────────────┐
                  │                         │
                  ▼                         ▼
        ┌──────────────────┐      ┌──────────────────┐
        │  Faster-Whisper  │      │  Groq LLM        │
        │ Speech-to-Text   │      │ Meeting Analysis │
        └────────┬─────────┘      └────────┬─────────┘
                 │                         │
                 └────────────┬────────────┘
                              ▼
                    ┌──────────────────────┐
                    │       SQLite         │
                    │ Meeting Persistence  │
                    └──────────────────────┘
```

### Processing Flow

```text
Meeting Recording
       │
       ▼
    Upload
       │
       ▼
FastAPI Backend
       │
       ▼
Faster-Whisper
       │
       ▼
    Transcript
       │
       ▼
    Groq LLM
       │
       ├──► Summary
       ├──► Key Decisions
       └──► Action Items
                │
                ▼
             SQLite
                │
                ▼
          Web Interface
```

---

## 🛠️ Technology Stack

| Layer | Technology |
|---|---|
| Frontend | HTML, CSS, JavaScript |
| Backend | Python, FastAPI |
| Speech-to-Text | Faster-Whisper |
| AI Analysis | Groq API / configured LLM |
| Database | SQLite |
| API Server | Uvicorn |
| Environment Configuration | python-dotenv |

---

## 📁 Project Structure

```text
Meeting-Summarizer/
│
├── backend/
│   ├── main.py
│   └── ...
│
├── frontend/
│   └── index.html
│
├── sample_data/
│
├── .env.example
├── .gitignore
├── LICENSE
├── README.md
└── requirements.txt
```

---

## ⚙️ Prerequisites

- Python 3.10+
- Git
- A Groq API key

---

## 🚀 Installation

### 1. Clone the repository

```bash
git clone https://github.com/abhaykumar15/meeting-summarizer.git
cd meeting-summarizer
```

### 2. Create a virtual environment

#### Windows PowerShell

```powershell
python -m venv venv
venv\Scripts\activate
```

#### Linux / macOS

```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

---

## 🔐 Environment Configuration

Create a `.env` file in the project root:

```env
GROQ_API_KEY=your_groq_api_key
```

Use `.env.example` as the template.

**Never commit your `.env` file or expose your API key publicly.**

---

## ▶️ Running the Application

MeetFlow uses a separate backend API server and frontend development server.

### Terminal 1 — Backend

```powershell
python -m uvicorn backend.main:app --reload --port 8000
```

Backend:

```text
http://localhost:8000
```

FastAPI documentation:

```text
http://localhost:8000/docs
```

### Terminal 2 — Frontend

From the project root:

```powershell
python -m http.server 8080 --directory frontend
```

Open:

```text
http://localhost:8080
```

---

## 🔌 API Endpoints

| Method | Endpoint | Purpose |
|---|---|---|
| GET | `/health` | Check backend availability |
| POST | `/upload` | Upload and process a meeting recording |
| GET | `/meetings` | Retrieve meeting history |
| GET | `/meetings/{id}` | Retrieve a specific meeting |

Interactive API documentation:

```text
http://localhost:8000/docs
```

---

## 🧪 Testing the Application

1. Start the backend.
2. Start the frontend.
3. Open `http://localhost:8080`.
4. Upload a meeting recording.
5. Start the analysis.
6. Wait for transcription and AI processing.
7. Verify the summary.
8. Verify key decisions.
9. Verify action items.
10. Review the transcript.
11. Open Meeting History.
12. Reopen the processed meeting.

---

## 🎬 Demo

The complete working demonstration shows:

**Upload → Transcription → AI Analysis → Summary → Decisions → Action Items → Transcript → Meeting History**

### ▶️ Watch the demo

[**Watch MeetFlow — Complete Working Demo on YouTube**](https://youtu.be/Rfiw1qawgho)

---

## 🔒 Security Notes

- API credentials are stored in environment variables.
- `.env` is excluded from Git using `.gitignore`.
- API keys should never be committed to the repository.
- Uploaded recordings are intended for local application use.

---

## 🔮 Future Improvements

- Speaker diarization and speaker labels
- Real-time meeting summarization
- Search across historical meetings
- Export summaries to PDF or DOCX
- Authentication and user accounts
- Cloud storage integration
- Calendar integration
- Improved multilingual transcription
- Background processing for large recordings

---

## 📄 License

This project is provided under the terms specified in the included `LICENSE` file.

---

## 👨‍💻 Author

**Abhay Kumar**

GitHub: https://github.com/abhaykumar15
