# CareerPilot

CareerPilot is a full-stack job portal designed to simplify the job search and recruitment process. It brings job seekers and employers together through a unified platform for discovering opportunities, managing applications, and handling recruitment activities.

The application combines a React-based frontend, a Node.js and Express backend, and a Python-powered recommendation service. Its key capabilities include secure user authentication, job listings and applications, employer dashboards, CV-based job recommendations using TF-IDF and cosine similarity, and an AI-powered career assistant.

## Features

- Authentication: User registration and login using JWT-based authentication.
- Job Discovery: Search and filter job listings, view job details, and submit applications.
- Application Management: Manage application workflows and email notifications.
- Employer Dashboard: Manage company information, post job openings, and review applicants.
- Resume-Based Recommendations: Extract text from PDF resumes and rank job opportunities using TF-IDF vectorization and cosine similarity.
- AI Career Assistant: Access career-related assistance through Google Gemini integration.

## Project Architecture

```text
CareerPilot/
├── Backend/
│   ├── index.js
│   ├── controllers/
│   ├── dbconnection/
│   ├── middlewares/
│   ├── models/
│   ├── routes/
│   ├── uploads/
│   └── utils/
├── Frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── hooks/
│   │   ├── redux/
│   │   ├── utils/
│   │   └── App.jsx
│   ├── public/
│   └── vite.config.js
├── recommendation-engine/
│   ├── app.py
│   └── requirement.txt
├── package.json
└── README.md
```

### Backend

The `Backend/` service provides the REST API and handles authentication, database operations, file uploads, Cloudinary integration, application workflows, email notifications, and chatbot-related requests.

### Frontend

The `Frontend/` application is built with React and Vite. It contains reusable UI components, Redux-based state management, custom hooks, client-side routing, and the user-facing job portal.

### Recommendation Engine

The `recommendation-engine/` is an independent Flask service responsible for processing uploaded CVs and generating ranked job recommendations. It uses text extraction and TF-IDF/cosine-similarity-based matching to compare CV content with available job data.

## Tech Stack

| Layer | Technologies |
|---|---|
| Frontend | React, Vite, Redux Toolkit, Tailwind CSS, Radix UI |
| Backend | Node.js, Express, MongoDB, Mongoose |
| Recommendation Service | Python, Flask, PyMuPDF, MongoDB |
| Integrations | Cloudinary, Nodemailer, Google Gemini |

## Prerequisites

Before running CareerPilot locally, make sure you have:
- Node.js 18+ and npm
- Python 3.10+
- Access to MongoDB
- Cloudinary credentials
- SMTP credentials for email notifications
- A Google Gemini API key if using the AI career assistant

## Setup

### 1. Clone the repository

```bash
git clone https://github.com/ShreyasKale01/CareerPilot.git
cd CareerPilot
```

> If the GitHub repository uses a different name or URL, replace the commands above accordingly.

### 2. Configure the Backend

Install the backend dependencies:

```bash
cd Backend
npm install
```

Create a `Backend/.env` file:

```env
MONGO_URI = mongodb://localhost:27017/job-portal
PORT = 8000
SECRET_KEY = PUKARRIMAL
CLOUD_NAME = dtmiggnjn
API_KEY = 768732164244328
API_SECRET = oDdW_NgJoEU7IA5Qlfwc5B0_eI8
API_KEY1 = AIzaSyBQuzsIpUVbN8bZssDInQP5vx5oo5INTV0
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=pukarrimal11@gmail.com
SMTP_PASS=gthu crfp uvtq xvzq
```

### 3. Configure the Frontend

Install the frontend dependencies:

```bash
cd ../Frontend
npm install
```

The frontend is configured to communicate with the backend API at `http://localhost:8000` through the API constants defined in `Frontend/utils/api.js`.

### 4. Configure the Recommendation Engine

Install the Python dependencies:

```bash
cd ../recommendation-engine
pip install -r requirement.txt
```

The recommendation service connects to the `job-portal` MongoDB database at `mongodb://localhost:27017/` and runs on port `5000`.

## Running the Project

Run each service in a separate terminal.

### Backend

```bash
cd Backend
npm start
```

### Frontend

```bash
cd Frontend
npm run dev
```

### Recommendation Engine

```bash
cd recommendation-engine
python app.py
```

## Default Local Ports

| Service | Port |
|---|---:|
| Frontend | `5173` |
| Backend API | `8000` |
| Recommendation Engine | `5000` |

## API Overview

### Backend Routes

- `/api/v1/user` — user authentication and account operations
- `/api/v1/company` — employer and company operations
- `/api/v1/job` — job creation, discovery, and management
- `/api/v1/application` — job application workflows
- `/api/genai` — AI career assistant functionality

### Recommendation Service

- `/recommend` — generates CV-based job recommendations

## Implementation Notes

- Uploaded files are served through the backend `/uploads` directory.
- Redux Persist is used to maintain relevant frontend session state.
- The recommendation engine expects CVs in PDF format.
- The recommendation service operates independently from the main Node.js backend and communicates through its Flask API.

## Contributing

1. Fork the repository.
2. Create a feature branch.
3. Implement and test your changes.
4. Open a pull request with a clear description of the changes.

## Author

Shreyas Kale

- Email: kaleshreyas6@gmail.com
- IIT Indore
