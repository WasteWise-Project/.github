<div align="center">
  <h1>WasteWise</h1>
  <h3>Smart Waste Management System for Sustainable Cities</h3>

  <p>
    <b>Real-time Monitoring</b> • <b>AI Route Optimization</b> • <b>ML Predictive Routing</b>
  </p>

  <p>
    <img src="https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB" alt="React" />
    <img src="https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript" />
    <img src="https://img.shields.io/badge/NestJS-E0234E?style=for-the-badge&logo=nestjs&logoColor=white" alt="NestJS" />
    <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python" />
    <img src="https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi" alt="FastAPI" />
    <img src="https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white" alt="PostgreSQL" />
  </p>
</div>

---

## Project Overview

**WasteWise** is a full-stack smart waste management platform that replaces static collection schedules with a dynamic, data-driven approach. Bin fill levels are tracked in real-time, and an AI engine calculates the most efficient collection routes — reactively for bins that are already critical, and proactively for bins predicted to overflow using machine learning.

### Key Objectives
- **Monitor:** Real-time bin fill levels managed through a live admin dashboard.
- **Optimize:** Shortest collection paths solved with the Capacitated Vehicle Routing Problem (CVRP) using Google OR-Tools.
- **Predict:** Random Forest ML model forecasts which bins will cross the critical threshold in the next 24 hours, enabling proactive dispatch before overflow.
- **Sustain:** Fewer unnecessary trips means lower fuel consumption and CO₂ emissions.

---

## System Architecture

WasteWise is a three-service system, each with a dedicated technology stack:

| Service | Tech Stack | Responsibility |
| :--- | :--- | :--- |
| **Frontend** | `React 19` `Vite` `TypeScript` `TailwindCSS` `TanStack Query` `TanStack Router` `Leaflet` | Web dashboard with Admin and Driver views |
| **Backend** | `NestJS` `TypeScript` `Drizzle ORM` `Neon PostgreSQL` `Zod` `JWT` | REST API for auth, bins, vehicles, routes, and algorithm orchestration |
| **Algorithm** | `FastAPI` `Python` `OR-Tools` `scikit-learn` `pandas` `psycopg2` | CVRP solver and Random Forest predictive routing engine |

```
Frontend (React)
     ↕
Backend (NestJS)  →  Algorithm (FastAPI)
     ↕                     ↕
  Database (Neon PostgreSQL)
```

---

## Core Features

### Reactive Route Generation
Fetches all bins with `fill_level ≥ 75%` and feeds them into the OR-Tools CVRP solver. A dynamic depot is placed at the average coordinate of all critical bins, and `PATH_CHEAPEST_ARC` finds the shortest collection sequence within the vehicle's weight capacity.

### Predictive ML Routing (+24h)
A **Random Forest Regressor** is trained on 90 days of historical sensor data using features like `hour_of_day`, `day_of_week`, `is_weekend`, and `bin_id_encoded`. Given any time horizon, it predicts each bin's fill increase and proactively routes the truck to bins that will exceed 75% — before they become a problem.

### Simulation Engine
A `/simulate-next-day` endpoint adds 5–25% fill to all bins in one database transaction, allowing the system to be demoed from an empty state to a critical collection scenario in seconds.

### Admin Dashboard
- Live Leaflet map with color-coded bin status (green / amber / red)
- Generate reactive or predictive routes and assign them to a vehicle
- Simulation and safe-reset controls for demos
- Full management of bins, operator accounts, and routes

### Driver Dashboard
- View the active assigned route with ordered waypoints on a map
- Mark each collection stop as complete one by one
- Track overall route progress and summary

---

## Repositories

### [WasteWise](https://github.com/WasteWise-Project/WasteWise)
> The main monorepo — all three services live here.

**`wastewise-frontend`**
React 19 + Vite dashboard for admins and drivers. Uses TanStack Query for server state, TanStack Router for navigation, and react-leaflet for interactive maps.

**`wastewise-backend`**
NestJS REST API with five modules: `auth`, `bins`, `sensors`, `vehicles`, and `routes`. Authenticates with JWT, uses Drizzle ORM against a Neon PostgreSQL database, and validates all algorithm responses with Zod before persisting.

**`wastewise-algorithm`**
FastAPI Python microservice with three domains:
- `/optimize-cvrp` — OR-Tools CVRP solver for currently critical bins
- `/ml/predictive-cvrp` — Random Forest model predicts fill levels ahead and routes proactively
- `/simulate-next-day` and `/reset-bins` — simulation controls for demos

---

### [WasteWise-docs](https://github.com/WasteWise-Project/WasteWise-docs)
> Project documentation and research.
- Graduation Project thesis and research papers on CVRP and smart waste systems
- UML, circuit schematics, and system architecture diagrams
- Slide decks and project showcases

---

## The Team

**WasteWise** is developed as a Graduation Project at **Haliç University, Department of Computer Engineering**.

<div align="center">
<table>
  <tr>
    <td align="center">
      <div align="center">
        <a href="https://github.com/glory42">
          <img src="https://github.com/glory42.png?size=100" width="100px;" alt=""/><br />
          <sub><b>Görkem Karyol</b></sub>
        </a><br />
        Full Stack Web & Server Infrastructure<br />
        <i>(Frontend, Backend, IoT Support)</i>
      </div>
    </td>
    <td align="center">
      <div align="center">
        <a href="https://github.com/osnn96">
          <img src="https://github.com/osnn96.png?size=100" width="100px;" alt=""/><br />
          <sub><b>Osman Şener Gürel</b></sub>
        </a><br />
        Algorithm Design & IoT Systems<br />
        <i>(Optimization Logic, Database, Hardware)</i>
      </div>
    </td>
  </tr>
</table>
</div>

<div align="center">
  <sub>Built with care by the WasteWise Team.</sub>
</div>
