<div align="center">

# 🖨️ PrintFlow

<a href="https://readme-typing-svg.herokuapp.com">
  <img src="https://readme-typing-svg.herokuapp.com/?lines=The+Future+of+Campus+Printing;Automated.+Efficient.+Seamless.;Built+for+Students,+Shops,+and+Admins&font=Inter&center=true&width=550&height=50&color=3B82F6&vCenter=true&size=22" alt="Typing SVG" />
</a>

<p align="center">
  <a href="https://github.com/JudeeeeeV/printflow-frontend"><img src="https://img.shields.io/badge/Frontend-React%20%7C%20Tailwind-61DAFB?style=for-the-badge&logo=react&logoColor=black" alt="Frontend" /></a>
  <a href="https://github.com/JudeeeeeV/printflow-backend"><img src="https://img.shields.io/badge/Backend-NestJS%20%7C%20Node.js-E0234E?style=for-the-badge&logo=nestjs&logoColor=white" alt="Backend" /></a>
  <a href="https://github.com/JudeeeeeV/printflow-admin"><img src="https://img.shields.io/badge/Admin-React%20%7C%20Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white" alt="Admin" /></a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/License-MIT-blue.svg?style=flat-square" alt="License" />
  <img src="https://img.shields.io/badge/Status-Active_Development-brightgreen?style=flat-square" alt="Status" />
  <img src="https://img.shields.io/badge/PRs-Welcome-brightgreen.svg?style=flat-square" alt="PRs Welcome" />
</p>

---

<!-- PRODUCT DEMO PLACEHOLDER -->
<img src="https://via.placeholder.com/800x450.png?text=✨+Insert+Animated+Product+Demo+GIF+Here+✨" alt="PrintFlow Demo" width="800" style="border-radius: 8px; box-shadow: 0 4px 6px rgba(0,0,0,0.1);"/>

</div>

<br />

<details>
<summary><b>📖 Table of Contents</b></summary>

- [About The Project](#-about-the-project)
- [Repository Directory](#-repository-directory)
- [Architecture](#-architecture)
- [Tech Stack](#-tech-stack)
- [Quick Start & Setup](#-quick-start--setup)
- [License](#-license)

</details>

## 🚀 About The Project

PrintFlow is a comprehensive, multi-platform ecosystem designed to modernize and automate printing operations for university campuses and local print shops. It bridges the gap between **Students** submitting documents, **Shops** managing printing queues, and **Administrators** overseeing the platform and resolving disputes.

The project is modularized into three distinct environments to ensure high scalability, security, and strict separation of concerns.

---

## 📂 Repository Directory

PrintFlow operates as a monorepo-style ecosystem across three dedicated repositories. Click the badges below to navigate to each specific codebase:

| Module | Description | Repository Link |
| :--- | :--- | :--- |
| **🎨 Main Frontend** | The unified portal for Students (to upload files & checkout) and Print Shops (to manage queues & analytics). | [![Go to Frontend](https://img.shields.io/badge/View_Repo-Frontend-3B82F6?style=for-the-badge&logo=github)](https://github.com/JudeeeeeV/printflow-frontend) |
| **⚙️ Backend API** | The central NestJS server handling business logic, Supabase integration, real-time sockets, and payments. | [![Go to Backend](https://img.shields.io/badge/View_Repo-Backend-10B981?style=for-the-badge&logo=github)](https://github.com/JudeeeeeV/printflow-backend) |
| **🛡️ Admin Portal** | The secure dashboard for platform administrators to manage shop onboarding, revenue, and user disputes. | [![Go to Admin](https://img.shields.io/badge/View_Repo-Admin_Portal-F59E0B?style=for-the-badge&logo=github)](https://github.com/JudeeeeeV/printflow-admin) |

---

## 🏗 Architecture

The system utilizes a modern decoupled architecture. The Backend acts as the single source of truth, communicating securely with Supabase for data persistence and authentication, while serving both the Main Frontend and the Admin Portal.

```mermaid
graph TD
    subgraph "Client Applications"
        F[🎨 Main Frontend<br/>Student & Shop]
        A[🛡️ Admin Portal<br/>System Admins]
    end

    subgraph "Core Backend Services"
        B[⚙️ NestJS API Gateway<br/>REST & WebSockets]
    end

    subgraph "Infrastructure"
        DB[(🐘 Supabase PostgreSQL<br/>Auth & DB)]
        S3[🪣 Cloud Storage<br/>PDFs & Assets]
    end

    F <-->|HTTPS / WSS| B
    A <-->|HTTPS| B
    B <-->|Prisma / PostgREST| DB
    B <-->|Uploads| S3
```

---

## 💻 Tech Stack

We leverage industry-leading technologies to deliver a blazing fast and reliable experience.

<div align="center">
  <img src="https://skillicons.dev/icons?i=react,ts,tailwind,vite,nodejs,nestjs,postgres,supabase,github&theme=dark" alt="Tech Stack" />
</div>

---

## 🏎 Quick Start & Setup

Want to spin up the entire PrintFlow ecosystem locally? Follow these steps to run all three environments concurrently.

### 1. Prerequisites
Ensure you have the following installed:
- [Node.js](https://nodejs.org/) (v18+)
- [npm](https://npmjs.com/) or [yarn](https://yarnpkg.com/)
- A [Supabase](https://supabase.com/) account for the database

### 2. Clone the Repositories
Since the project is split into three repos, clone them into a central `printflow` directory:

```bash
mkdir printflow && cd printflow

git clone https://github.com/JudeeeeeV/printflow-frontend.git
git clone https://github.com/JudeeeeeV/printflow-backend.git
git clone https://github.com/JudeeeeeV/printflow-admin.git
```

### 3. Install Dependencies
Install dependencies for all three projects. You can do this quickly by opening three terminal tabs or running:

```bash
# Frontend
cd printflow-frontend && npm install

# Backend
cd ../printflow-backend && npm install

# Admin
cd ../printflow-admin && npm install
```

### 4. Environment Variables
You will need to configure `.env` files for each repository. Create a `.env` in the root of each project using their respective `.env.example` templates. 

*(Make sure to add your Supabase URL, Anon Key, and Service Role keys where appropriate!)*

### 5. Spin Up the Environments
Open three separate terminal windows and start the development servers:

**Terminal 1 (Backend):**
```bash
cd printflow-backend
npm run start:dev
# API will run on http://localhost:3000
```

**Terminal 2 (Frontend):**
```bash
cd printflow-frontend
npm run dev
# Frontend will run on http://localhost:5173
```

**Terminal 3 (Admin):**
```bash
cd printflow-admin
npm run dev
# Admin will run on http://localhost:3001
```

> [!TIP]
> **Pro-Tip:** If you prefer running them all in one terminal window, consider using a package like `concurrently` from a root `package.json`.

---

## 📜 License

Distributed under the MIT License. See `LICENSE` for more information.

<div align="center">
  <sub>Built with ❤️ for better campus printing.</sub>
</div>
