<div align="center">
  <h1>🌱 WasteWise</h1>
  <h3>Smart Waste Management System for Sustainable Cities</h3>
  
  <p>
    <b>Real-time Monitoring</b> • <b>Dynamic Route Optimization</b> • <b>Operational Efficiency</b>
  </p>

  <p>
    <img src="https://img.shields.io/badge/Node.js-43853D?style=for-the-badge&logo=node.js&logoColor=white" alt="Node.js" />
    <img src="https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript" />
    <img src="https://img.shields.io/badge/Supabase-181818?style=for-the-badge&logo=supabase&logoColor=3ECF8E" alt="Supabase" />
    <img src="https://img.shields.io/badge/Docker-2CA5E0?style=for-the-badge&logo=docker&logoColor=white" alt="Docker" />
    <img src="https://img.shields.io/badge/MQTT-660066?style=for-the-badge&logo=mqtt&logoColor=white" alt="MQTT" />
    <img src="https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white" alt="C++" />
  </p>
</div>

---

## 🚀 Project Overview

**WasteWise** is an IoT-enabled waste management solution designed to replace traditional, static waste collection schedules with a dynamic, data-driven approach. By monitoring bin fill levels in real-time and optimizing collection routes, WasteWise reduces fuel consumption, operational costs, and the carbon footprint of urban logistics.

### 🎯 Key Objectives
* **Monitor:** Real-time tracking of waste bin fill levels using ultrasonic sensors.
* **Optimize:** Algorithmic calculation of the most efficient collection routes.
* **Sustain:** Reduce unnecessary fuel usage and CO2 emissions.

---

## 🛠️ System Architecture

The WasteWise ecosystem is divided into three core layers:

| Layer | Tech Stack | Description |
| :--- | :--- | :--- |
| **Hardware** | `ESP32` `HC-SR04` `GPS` | IoT sensor nodes that measure fill levels and transmit data via MQTT. |
| **Backend** | `Node.js` `Express` `TypeScript` | Processes sensor data, executes optimization algorithms, and serves APIs. |
| **Data** | `Supabase` `PostgreSQL` | Stores real-time telemetry, bin locations, and route history. |

---

## 📂 Repositories

We have organized our work into distinct repositories to ensure modularity and clean code practices.

### 🖥️ [wastewise-backend](https://github.com/WasteWise-Group/wastewise-backend)
> The central nervous system of the project.
> * **API:** RESTful endpoints for frontend clients.
> * **Logic:** Route optimization algorithms.
> * **Database:** Supabase integration and real-time listeners.

### 📡 [wastewise-hardware](https://github.com/WasteWise-Group/wastewise-hardware)
> Firmware for the IoT Sensor Nodes.
> * **Sensors:** Logic for Ultrasonic (distance) and GPS modules.
> * **Comms:** MQTT client implementation for lightweight data transmission.
> * **Platform:** C++/Arduino code optimized for ESP32/Microcontrollers.

### 📄 [wastewise-docs](https://github.com/WasteWise-Group/wastewise-docs)
> Comprehensive documentation and research.
> * **Reports:** Graduation Project Thesis and interim reports.
> * **Diagrams:** UML, Circuit (Fritzing), and System Architecture diagrams.
> * **Presentations:** Slide decks and project showcases.

---

## 👥 The Team

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
  <sub>Built with 💙 and ☕ by the WasteWise Team.</sub>
</div>