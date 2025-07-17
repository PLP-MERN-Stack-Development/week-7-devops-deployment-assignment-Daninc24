# MERN Stack Deployment Assignment

## Table of Contents
- [Project Overview](#project-overview)
- [Live Demo](#live-demo)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Setup & Installation](#setup--installation)
- [Environment Variables](#environment-variables)
- [CI/CD Pipeline](#cicd-pipeline)
- [Deployment](#deployment)
- [Monitoring & Maintenance](#monitoring--maintenance)
- [Screenshots](#screenshots)
- [License](#license)

---

## Project Overview

This is a full MERN stack application deployed with CI/CD, environment-based configuration, and production best practices.

---

## Live Demo

- **Frontend:** [https://your-frontend-url.vercel.app](https://your-frontend-url.vercel.app)
- **Backend API:** [https://your-backend-url.onrender.com/api/notes](https://your-backend-url.onrender.com/api/notes)

---

## Features

- React frontend with code splitting and environment variables
- Express backend with security, logging, and error handling
- MongoDB Atlas for persistent storage
- Full CRUD API for notes
- Health check endpoint
- CI/CD with GitHub Actions
- Production-ready deployment scripts
- Monitoring and backup documentation

---

## Tech Stack

- **Frontend:** React, Vite, Tailwind CSS
- **Backend:** Node.js, Express, Mongoose
- **Database:** MongoDB Atlas
- **CI/CD:** GitHub Actions
- **Deployment:** Vercel (frontend), Render/Railway/Heroku (backend)

---

## Setup & Installation

### Prerequisites
- Node.js (v18+ recommended)
- npm

### Clone the repository
```sh
git clone https://github.com/your-username/your-repo.git
cd your-repo
```

### Backend Setup
```sh
cd backend
cp .env.example .env
# Fill in your MongoDB URI and other secrets in .env
npm install
npm run dev
```

### Frontend Setup
```sh
cd frontend
cp .env.example .env
# Set VITE_API_URL to your backend URL
npm install
npm run dev
```

---

## Environment Variables

### Backend (`backend/.env.example`)
```
PORT=5000
MONGO_URI=mongodb+srv://<username>:<password>@cluster0.mongodb.net/myapp?retryWrites=true&w=majority
JWT_SECRET=your_jwt_secret
CLIENT_URL=http://localhost:5173
```

### Frontend (`frontend/.env.example`)
```
VITE_API_URL=http://localhost:5000
```

---

## CI/CD Pipeline

- **CI:** `.github/workflows/ci.yml` runs lint and tests on every push and PR.
- **CD:** `.github/workflows/deploy.yml` auto-deploys to Render (or your chosen platform) on push to `main`.

**Example Workflow:**
```yaml
name: CI

on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Setup Node
        uses: actions/setup-node@v3
        with:
          node-version: 18
      - run: npm install
      - run: npm run lint
      - run: npm test
```

---

## Deployment

### Frontend
- Deployed to Vercel/Netlify.
- Build command: `npm run build`
- Output directory: `dist`
- Set environment variables in the platform dashboard.

### Backend
- Deployed to Render/Railway/Heroku.
- Set environment variables (`PORT`, `MONGO_URI`, etc.) in the platform dashboard.
- Serves static frontend from `frontend/dist` in production.

---

## Monitoring & Maintenance

- **Health Check:** `GET /health` returns `OK`
- **Monitoring Tools:** (Describe what you use, e.g., UptimeRobot, Sentry, LogRocket)
- **Database Backups:** Enabled in MongoDB Atlas
- **Security:** Use `npm audit` and Dependabot for vulnerability checks
- **Rollbacks:** Keep last stable build or enable auto-rollback on deploy failure

---

## Screenshots

### CI/CD Pipeline Example
![CI/CD Screenshot](./screenshots/cicd.png)

### App UI
![App Screenshot](./screenshots/app.png)

---

## License

MIT 