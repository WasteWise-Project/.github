<div align="center">
  <h1>WasteWise</h1>
  <h3>Smart Waste Management System for Sustainable Cities</h3>
  
  <p>
    <b>Real-time IoT Monitoring</b> • <b>AI Route Optimization</b> • <b>ML Predictive Routing</b>
  </p>

  <p>
    <img src="https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB" alt="React" />
    <img src="https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript" />
    <img src="https://img.shields.io/badge/NestJS-E0234E?style=for-the-badge&logo=nestjs&logoColor=white" alt="NestJS" />
    <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python" />
    <img src="https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi" alt="FastAPI" />
    <img src="https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white" alt="PostgreSQL" />
    <img src="https://img.shields.io/badge/MQTT-660066?style=for-the-badge&logo=mqtt&logoColor=white" alt="MQTT" />
    <img src="https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white" alt="C++" />
  </p>
</div>

---

## Project Overview

**WasteWise** is a full-stack IoT-enabled waste management platform designed to replace static collection schedules with a dynamic, data-driven approach. Smart sensor nodes monitor bin fill levels in real-time, while an AI engine calculates the most efficient collection routes — reactively for today, and proactively for tomorrow using machine learning.

### Key Objectives
* **Monitor:** Real-time tracking of waste bin fill levels via ultrasonic sensors on ESP32 nodes.
* **Optimize:** Capacitated Vehicle Routing Problem (CVRP) solver using Google OR-Tools.
* **Predict:** Random Forest ML model that forecasts which bins will overflow in the next 24 hours.
* **Sustain:** Reduce unnecessary trips, fuel consumption, and CO₂ emissions.

---

## System Architecture

WasteWise is a four-layer system where each layer has a dedicated service:

| Layer | Tech Stack | Description |
| :--- | :--- | :--- |
| **IoT Hardware** | `ESP32` `HC-SR04` `MQTT` `C++` | Sensor nodes measure fill levels and publish telemetry to the backend. |
| **Frontend** | `React` `Vite` `TypeScript` `TailwindCSS` | Web dashboard with separate Admin and Driver views. |
| **Backend** | `NestJS` `TypeScript` `Drizzle ORM` | REST API handling auth, bins, vehicles, routes, and algorithm orchestration. |
| **Algorithm** | `FastAPI` `Python` `OR-Tools` `scikit-learn` | CVRP route solver and Random Forest predictive routing engine. |
| **Database** | `Neon` `PostgreSQL` | Cloud-hosted relational database storing telemetry, bin states, and route history. |

### How They Connect

```
IoT Nodes  →  MQTT  →  Backend (NestJS)  →  Algorithm (FastAPI)
                              ↕
                         Database (Neon)
                              ↕
                       Frontend (React)
```

---

## Core Features

### Reactive Route Generation
Scans all bins with `fill_level ≥ 75%` and feeds them into a CVRP solver. Returns the shortest collection path respecting the vehicle's weight capacity.

### Predictive ML Routing (+24h)
A **Random Forest Regressor** trained on 90 days of synthetic historical data predicts each bin's fill level 24 hours ahead. Bins forecast to overflow are proactively added to the route before they become critical.

### Admin Dashboard
- Live bin map with color-coded fill status (green / amber / red)
- Generate reactive or predictive routes and assign them to vehicles
- Simulation panel to fast-forward time for demos
- Manage bins, operator accounts, and routes

### Driver Dashboard
- View the active assigned route with ordered waypoints on a map
- Mark collection stops as completed one by one
- Track route progress and summary

---

## Repositories

### [wastewise-backend](https://github.com/WasteWise-Group/wastewise-backend)
> NestJS REST API — the central hub of the platform.
> * **Auth:** JWT-based authentication with `ADMIN` and `DRIVER` roles.
> * **Modules:** `bins`, `sensors`, `vehicles`, `routes`, `auth`.
> * **Integration:** Orchestrates calls to the FastAPI algorithm service and validates responses with Zod.

### [wastewise-frontend](https://github.com/WasteWise-Group/wastewise-frontend)
> React + Vite web dashboard for administrators and drivers.
> * **Admin view:** Map surveillance, route generation, simulation, and account management.
> * **Driver view:** Active route display, step-by-step collection completion.
> * **Stack:** TanStack Query for data fetching, React Router for navigation, Leaflet for maps.

### [wastewise-algorithm](https://github.com/WasteWise-Group/wastewise-algorithm)
> FastAPI Python microservice — the intelligence layer.
> * **CVRP:** Google OR-Tools solves the capacitated routing problem for critical bins.
> * **ML:** scikit-learn Random Forest predicts future fill levels for proactive routing.
> * **Simulation:** `/simulate-next-day` endpoint adds realistic fill increments for demos.

### [wastewise-hardware](https://github.com/WasteWise-Group/wastewise-hardware)
> ESP32 firmware for the IoT sensor nodes.
> * **Sensing:** HC-SR04 ultrasonic sensor calculates fill percentage from distance.
> * **Comms:** MQTT client publishes telemetry to the `bins/telemetry` topic.
> * **Power:** Deep sleep cycles conserve the 18650 Li-Ion battery between readings.

### [wastewise-docs](https://github.com/WasteWise-Group/wastewise-docs)
> Project documentation and research.
> * **Reports:** Graduation Project thesis and research papers on CVRP and smart waste systems.
> * **Diagrams:** UML, circuit schematics (Fritzing), and system architecture diagrams.
> * **Presentations:** Slide decks and project showcases.

---

## The Team

**WasteWise** is developed as a Graduation Project at **Haliç University, Department of Computer Engineering**.

<table>
  <tr>
    <td align="center">
      <a href="https://github.com/glory42">
        <img src="https://github.com/glory42.png?size=100" width="100px;" alt=""/><br />
        <sub><b>Görkem Karyol</b></sub>
      </a><br />
      Full Stack Web & Server Infrastructure <br />
      <i>(Frontend, Backend, IoT Support)</i>
    </td>
    <td align="center">
      <a href="https://github.com/osnn96">
        <img src="https://github.com/osnn96.png?size=100" width="100px;" alt=""/><br />
        <sub><b>Osman Şener Gürel</b></sub>
      </a><br />
      Algorithm Design & IoT Systems <br />
      <i>(Optimization Logic, Database, Hardware)</i>
    </td>
  </tr>
</table>

<div align="center">
  <sub>Built with care by the WasteWise Team.</sub>
</div>
