# Fake Job & Internship Detection System 🚨

This project uses a combination of Rule-Based NLP and a Memory-Based system (SQLite) to detect fake jobs and prevent students/professionals from falling victim to scams. It includes a Chrome Extension for user interaction seamlessly on job sites alongside a Flask backend to fulfill the NLP and DB operations.

## Features
- **Chrome Extension UI:** Shows Real/Fake label, Risk Score (0-100), and flags suspicious keywords.
- **Memory-Based Fraud Detection:** Checks memory (SQLite) before running the model. This is quick and powerful for highly-reported scams.
- **NLP/Model Analysis:** Flag keywords like "pay fee", "security deposit", "whatsapp only".
- **Dynamic Highlighting:** Highlights the suspicious words directly on the webpage for easy visual cues.
- **User "Report" System:** A convenient "Report as Scam" function allowing users to save the job profile permanently as fake.

---

## 🏗️ Project Structure
```
Fake_Job_Detection/
│
├── backend/
│   ├── app.py              # Flask server API endpoints
│   ├── database.py         # SQLite memory database logic
│   ├── model.py            # AI / NLP rule analysis model
│   ├── requirements.txt    # Python dependencies
│   └── scam_jobs.db        # SQLite DB (Generated Automatically)
│
└── extension/
    ├── manifest.json       # Chrome Manifest v3 
    ├── content.js          # Injected into webpage to read job info & highlight text
    ├── popup.html          # Extension UI
    ├── popup.js            # Talks between UI and Backend API
    └── styles.css          # Styling for Extension UI
```

---

## 🚀 Setup Instructions

### 1. Backend Setup
You must have Python installed.

1. Open your terminal/command prompt.
2. Navigate to the `backend` folder:
   ```bash
   cd "Fake_Job_Detection\backend"
   ```
3. Install the dependencies:
   ```bash
   pip install -r requirements.txt
   ```
4. Run the Flask Server:
   ```bash
   python app.py
   ```
The server will start locally at `http://127.0.0.1:5000/`. Keep this terminal window open.

### 2. Extension Setup (Chrome)
1. Open Google Chrome.
2. Go to the URL bar and type: `chrome://extensions/`
3. Enable **Developer Mode** (toggle switch on the top right).
4. Click on **Load unpacked** (top left).
5. Select the `Fake_Job_Detection\extension` folder on your computer.
6. The extension will now appear in your browser. Pin it to the toolbar for easy access!

---

## 🛠️ How to Use

1. Go to any job site like **LinkedIn**, **Naukri**, or even a standard career page.
2. Click on the **Job Fraud Detector** extension icon.
3. Click the **"Analyze Job"** button.
4. The system will grab the title, company, and description, then:
   - Check its Memory Database (if it was previously marked/reported as fake, it will instantly alert you).
   - If not in memory, it will perform NLP testing and generate a **Risk Score** out of 100.
5. Watch the webpage: **Suspicious words are highlighted in red instantly!**
6. Find a scam? Hit the **Report as Scam** button! The system will store the company/job-role in its memory and flag it for anyone else encountering it.
