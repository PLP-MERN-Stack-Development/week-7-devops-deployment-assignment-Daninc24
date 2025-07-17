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

- **Frontend:** [https://week-7-devops-deployment-assi-git-9b4229-daniel-mailus-projects.vercel.app/](https://week-7-devops-deployment-assi-git-9b4229-daniel-mailus-projects.vercel.app/)
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
CLIENT_URL=http://localhost:5173
```

### Frontend (`frontend/.env.example`)
```
VITE_API_URL=http://localhost:5000
```

---

## CI/CD Pipeline

- **CI/CD:** `.github/workflows/mern-ci-cd.yml` runs build, deploy, and health checks on every push to `main`.
- **Frontend and backend are deployed automatically on push.**

---

## Deployment

### Frontend (Vercel)
1. Go to [Vercel](https://vercel.com/) and log in with your GitHub account.
2. Click **Add New Project** and import your frontend repo.
3. Set the build command to `npm run build` and the output directory to `dist`.
4. Set the environment variable `VITE_API_URL` to your backend's deployed URL.
5. (Optional) Add a `vercel.json` file to your frontend directory for SPA routing:
   ```json
   {
     "rewrites": [
       { "source": "/(.*)", "destination": "/" }
     ]
   }
   ```
6. Deploy and visit: [https://week-7-devops-deployment-assi-git-9b4229-daniel-mailus-projects.vercel.app/](https://week-7-devops-deployment-assi-git-9b4229-daniel-mailus-projects.vercel.app/)

### Backend (Render/Railway/Heroku)
1. Go to your chosen backend platform and create a new web service.
2. Connect your GitHub repo and select the backend folder.
3. Set environment variables (`PORT`, `MONGO_URI`, `CLIENT_URL`) in the platform dashboard.
4. Set the start command to `npm start` or `node server.js`.
5. Deploy and note the backend URL for use in the frontend's `VITE_API_URL`.

---

## Monitoring & Maintenance

- **Health Check:**
  - Backend: `GET /health` returns `OK`
  - Frontend: `GET /ping` returns `pong`
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