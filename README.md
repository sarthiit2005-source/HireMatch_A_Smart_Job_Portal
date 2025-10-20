# HireMatch

HireMatch is a full-stack job portal that connects job seekers and employers through a modular web application built with a MERN-style architecture and a Python-based recommendation service. The platform supports secure authentication, job discovery, application tracking, employer-side job management, CV-driven job recommendations, and an AI-powered career assistant.

## Features

- JWT-based authentication for user registration and login
- Job discovery with search, filtering, detailed job views, and application workflows
- Application tracking with email notifications
- Employer dashboard for company management, job posting, and applicant review
- CV-based job recommendation using TF-IDF vectorization and cosine similarity
- AI-powered career assistance using Google Gemini

## Project Architecture

```text
HireMatch/
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

Before running HireMatch locally, ensure the following are available:

- Node.js 18+ and npm
- Python 3.10+
- MongoDB connection string
- Cloudinary account credentials
- Gmail SMTP credentials or another SMTP provider
- Google Gemini API key

## Setup

### 1. Clone the repository

```bash
git clone https://github.com/Pukar77/HireMatch.git
cd HireMatch
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
MONGO_URI=your_mongodb_connection_string
PORT=8000
SECRET_KEY=your_jwt_secret
CLOUD_NAME=your_cloudinary_cloud_name
API_KEY=your_cloudinary_api_key
API_SECRET=your_cloudinary_api_secret
API_KEY1=your_gemini_api_key
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=your_email_address
SMTP_PASS=your_app_password
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

Sarth Mhatre

- Email: sarth.iit2005@gmail.com
- IIT Indore
