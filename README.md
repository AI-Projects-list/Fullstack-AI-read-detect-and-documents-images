
---

# 🧠 Document & Image Chat (React + Node.js + GPT-4o-mini)

### 🤖 AI Chat with Uploaded Documents & Images

This project is a **full-stack AI assistant** that lets you **upload documents and images**, then **chat with GPT** about their contents.
You can ask questions like:

> * “Summarize my PDF/TXT.”
> * “What’s inside this image?”
> * “What’s the problems inside this image?”


The system automatically reads, parses, and sends your uploaded files to **OpenAI GPT-4o-mini** via the **LangChain** library.

---

## 🚀 Features

✅ **Multi-File Uploads**

* Upload multiple files at once (`.txt`, `.pdf`, `.jpg`, `.jpeg`, `.png`).
* Supports **drag-and-drop** and **browse**.

✅ **Automatic File Replacement**

* Each upload replaces all previous files in the backend `/documents` folder.
* Ensures the model always reads the **latest batch** of files.

✅ **Integrated AI Chat**

* Ask GPT-4o-mini questions about your uploaded files.
* GPT automatically reads all files (text + image) each time you send a message.

✅ **Text + Image Understanding**

* Texts (PDFs, TXT) are extracted and summarized.
* Images (JPEG/PNG) are analyzed visually by GPT (via base64).

✅ **Clean React Frontend**

* Shows file previews for PDFs, text, and images.
* Real-time chat interface with markdown formatting.

✅ **Express + LangChain Backend**

* Uses `multer` for file upload handling.
* Uses `pdf-parse` for extracting text from PDFs.
* All uploaded files are stored in `/documents` folder.

---

## 🧩 Folder Structure

```
project-root/
│
├── backend/
│   ├── app.js                 # Main Node.js + Express server
│   ├── documents/             # Uploaded files (auto-cleared each upload)
│   ├── package.json
│   └── .env                   # OPENAI_API_KEY=your_key_here
│
├── frontend/
│   ├── src/
│   │   ├── App.js             # Main React UI
│   │   ├── Chat.css           # Styles
│   │   └── index.js
│   ├── package.json
│   └── public/
│
└── README.md
```

---

## ⚙️ Installation

### 1️⃣ Backend Setup

```bash
cd backend
npm install express multer pdf-parse dotenv cors @langchain/openai @langchain/core
```

Create a `.env` file inside `/backend`:

```
OPENAI_API_KEY=your_openai_api_key_here
```

Start backend:

```bash
node app.js
```

Backend runs at:

> [http://localhost:3001](http://localhost:3001)

---

### 2️⃣ Frontend Setup

```bash
cd frontend
npm install react react-dom react-markdown
npm start
```

Frontend runs at:

> [http://localhost:3000](http://localhost:3000)

---

## 💡 How It Works

### 🖼 File Upload

* When you upload or drag-drop files, they are sent to `/upload`.
* The backend deletes all previous files in `/documents` and saves the new ones.
* Supported types: `.pdf`, `.txt`, `.jpg`, `.jpeg`, `.png`.

### 📄 Chat Message

* When you send a chat message:

  1. Backend reads **all files** in `/documents`.
  2. Text is extracted from TXT/PDF.
  3. Images are converted to Base64.
  4. Everything is sent to GPT-4o-mini via LangChain.
  5. GPT’s response is returned to the frontend.

### 💬 AI Response

* GPT replies with markdown-formatted text.
* The frontend displays it in a styled chat interface.

---

## 🧠 Example Use-Case

| Type           | Example                                                        |
| -------------- | -------------------------------------------------------------- |
| 📄 PDF         | Upload a financial report → ask “Summarize the main findings.” |
| 📜 TXT         | Upload a long essay → ask “What is the conclusion?”            |
| 🖼 Image       | Upload a receipt → ask “What items were purchased?”            |
| 🗂 Multi-Files | Upload several PDFs → ask “Compare all uploaded documents.”    |

---

## 🔒 Notes

* Each upload **replaces** all previous files — ensures no outdated data remains.
* All files are stored in `/documents/` — auto-created if missing.
* No cloud storage — all local.
* You can extend this to store chat history or multiple sessions later.

---

## 🛠 Tech Stack

| Layer             | Technology                         |
| ----------------- | ---------------------------------- |
| **Frontend**      | React, ReactMarkdown               |
| **Backend**       | Node.js, Express                   |
| **AI Engine**     | OpenAI GPT-4o-mini (via LangChain) |
| **File Handling** | Multer, pdf-parse, fs/promises     |
| **Style**         | Custom CSS                         |

---




---
can generate the Markdown + placeholders for images (e.g. `/docs/demo.gif`).
