# DevSecOps Pipeline Implementation for Tic Tac Toe Game

![Screenshot 2025-03-04 at 7 16 48 PM](https://github.com/user-attachments/assets/7ed79f9c-9144-4870-accd-500085a15592)

![image](https://github.com/user-attachments/assets/5b2813a5-f493-4665-8964-77359b5be93a)

## Features

- 🎮 Fully functional Tic Tac Toe game
- 📊 Score tracking for X, O, and draws
- 📜 Game history with timestamps
- 🏆 Highlights winning combinations
- 🔄 Reset game and statistics
- 📱 Responsive design for all devices

## Technologies Used

- React 18
- TypeScript
- Tailwind CSS
- Lucide React for icons

## Project Structure

```
src/
├── components/
│   ├── Board.tsx       # Game board component
│   ├── Square.tsx      # Individual square component
│   ├── ScoreBoard.tsx  # Score tracking component
│   └── GameHistory.tsx # Game history component
├── utils/
│   └── gameLogic.ts    # Game logic utilities
├── App.tsx             # Main application component
└── main.tsx           # Entry point
```

## Game Logic

The game implements the following rules:

1. X goes first, followed by O
2. The first player to get 3 of their marks in a row (horizontally, vertically, or diagonally) wins
3. If all 9 squares are filled and no player has 3 marks in a row, the game is a draw
4. Winning combinations are highlighted
5. Game statistics are tracked and displayed

## Getting Started

### Prerequisites

- Node.js (v14 or higher)
- npm or yarn

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/devsecops-demo.git
   cd devsecops-demo
   ```

2. Install dependencies:
   ```bash
   npm install
   # or
   yarn
   ```

3. Start the development server:
   ```bash
   npm run dev
   # or
   yarn dev
   ```

4. Open your browser and navigate to `http://localhost:5173`

## Building for Production

To create a production build:

```bash
npm run build
# or
yarn build
```

The build artifacts will be stored in the `dist/` directory.








# GitOps DevSecOps Pipeline with Argo CD & Kubernetes (Tic Tac Toe)

![DevSecOps Pipeline Architecture](https://github.com/user-attachments/assets/7ed79f9c-9144-4870-accd-500085a15592)

![Application Screenshot](https://github.com/user-attachments/assets/5b2813a5-f493-4665-8964-77359b5be93a)

## 🚀 Overview

This repository demonstrates a **production-style DevSecOps GitOps pipeline** that builds, scans, and deploys a containerized application to **Kubernetes** using **GitHub Actions** and **Argo CD** — **without Jenkins**.

A **React + TypeScript Tic Tac Toe application** is used as the sample workload to showcase real-world CI/CD, security scanning, immutable image versioning, and GitOps-based continuous delivery.

---

## 🧩 Architecture (High Level Flow)

1. Developer pushes code to GitHub  
2. **GitHub Actions** runs CI stages (tests, linting/static checks, build)  
3. Docker image is built and scanned  
4. Image is pushed to a container registry  
5. Kubernetes manifests are updated with the new image tag  
6. **Argo CD** detects the Git change and syncs to **Kubernetes**

---

## 🔐 DevSecOps Pipeline Stages

| Stage | Tooling | Purpose |
|------|---------|---------|
| Unit Tests | npm / TypeScript | Validate application logic |
| Static Checks | ESLint / npm audit (optional) | Catch code & dependency issues |
| Build | Vite | Produce production build artifacts |
| Container Build | Docker | Build an immutable image |
| Image Scan | Trivy | Detect OS/package vulnerabilities |
| Push Image | DockerHub/GHCR | Store versioned images |
| Update Manifests | Git commit | GitOps source of truth |
| Continuous Delivery | Argo CD | Sync manifests to Kubernetes |

> ✅ The goal is to keep **deployment driven by Git** (GitOps) and keep CI responsible for build + security gates.

---

## 🧠 Key DevSecOps Concepts Demonstrated

- GitHub Actions based CI (**no Jenkins**)
- Security gates before deployment
- Immutable Docker image tagging (traceable releases)
- GitOps workflow (Git as the single source of truth)
- Argo CD reconciliation loop for Kubernetes deployments
- Separation of concerns: CI builds/scans, CD syncs

---

## 🎮 Application Features (Sample Workload)

- 🎮 Fully functional Tic Tac Toe game
- 📊 Score tracking for X, O, and draws
- 📜 Game history with timestamps
- 🏆 Highlights winning combinations
- 🔄 Reset game and statistics
- 📱 Responsive design for all devices

---

## 🛠 Tech Stack

### App
- React 18
- TypeScript
- Tailwind CSS
- Lucide React

### DevSecOps / GitOps
- GitHub Actions (CI)
- Docker
- Trivy (image vulnerability scanning)
- Kubernetes
- Argo CD (GitOps CD)

---

## 📁 Project Structure

```text
src/
├── components/
│   ├── Board.tsx       # Game board component
│   ├── Square.tsx      # Individual square component
│   ├── ScoreBoard.tsx  # Score tracking component
│   └── GameHistory.tsx # Game history component
├── utils/
│   └── gameLogic.ts    # Game logic utilities
├── App.tsx             # Main application component
└── main.tsx            # Entry point


