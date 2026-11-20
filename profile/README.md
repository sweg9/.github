# NOVA

**Non-connected Object Vision and Actuation for Smart Home Routines**

> 26-2 Hanyang University Software Engineering Project

## Overview

Smart-home routines work only if every control the resident cares about is on the network. Many are not: wall
switches, toggles and power strips, and in rented homes the wiring often cannot be changed. NOVA lets a proactive
smart-home agent use these controls anyway. A camera finds them, the system works out which device each one
operates, and routines then use them through wireless channels or, when those fail, a physical press by a robot.

The system rests on three ideas:

- **The home learns its own controls.** A detector finds each control, and the system links it to a device by
  watching the resident use it or by pressing it and comparing before and after. The resident only confirms the link.
- **A command is not a result.** Every action is checked: from the state the platform reports, or by camera. When
  wireless fails, the Safety Guard checks for people and obstacles, a robot presses the control (linear actuators
  on a cart in the prototype) and the camera checks the press.
- **Nothing leaves the home.** Recognition runs on the hub at home with local models, and the backend runs on the
  same laptop, so frames never go to the cloud.

## Architecture

<img src="architecture.png" width="560" alt="NOVA architecture: everything runs on one laptop at home. A k3d cluster holds the ingress, the server and the logging stack; the hub runs outside it and drives the webcam and the actuators.">

## Key Features

- **Control recognition:** wall switches, toggles and power strips are detected, their state read and each saved with a picture fingerprint.
- **Device mapping:** each control is linked to the device it operates, and a link is used only after it is verified.
- **Proactive routines:** routines come from repeated habits or are built by hand, and the resident can keep, change or remove them.
- **Wireless first, physical fallback:** channels (Wi-Fi, IR, Bluetooth) are ranked by learned score; if all fail, the robot presses the control.
- **Autonomy by risk:** low-risk devices act and then tell; high-risk devices ask first and always notify.
- **Learning from every run:** channel scores, link confidence and routine usefulness update after each run, even a cancelled one.

## Demo

- Web demo: [sim-demo/web](https://github.com/sweg9/sim-demo/tree/main/web) runs the 20-second process (mapping, Wi-Fi failure, Safety Guard, physical press, camera check) in a browser, with no install and no internet.
- Demo video: *coming soon*

## Tech Stack

| Layer | Technologies |
|---|---|
| Recognition | Ultralytics YOLO11, DINOv2, OpenCV 4, all local on CPU |
| Backend | Python 3.11, FastAPI, WebSocket (hub to server), APScheduler, Pydantic v2 |
| Database | SQLite (WAL) with SQLAlchemy 2 and Alembic |
| Web app | React 18, TypeScript 5, Vite, TanStack Query |
| Hardware | Arduino Nano, 12 V linear actuator, USB webcam |
| Infrastructure | Kubernetes (k3d) on one laptop at home, Traefik, Grafana and Loki |
| Simulator | Unity 6, three.js |

## Repositories

| Repo | Role |
|---|---|
| [ai-engine](https://github.com/sweg9/ai-engine) | Recognition on the hub: detectors, state classifier, result check, fingerprints, motion planner |
| [backend-server](https://github.com/sweg9/backend-server) | FastAPI backend: `server` mode for the registry, routines and log; `hub` mode for channels, the Safety Guard and the robot |
| [dataset](https://github.com/sweg9/dataset) | Switch-panel photos and labels for the detector |
| [live-demo](https://github.com/sweg9/live-demo) | The resident's web app and the presenter's demo screens |
| [sim-demo](https://github.com/sweg9/sim-demo) | Unity simulator and web demo, without the real hardware |
| [docs](https://github.com/sweg9/docs) | Development wiki |
| [harness](https://github.com/sweg9/harness) | Shared standards, skills and CI/CD |

## Links

- Proposal: [PDF](https://sweg9.github.io/docs/papers/proposal.pdf)
- Development wiki: https://sweg9.github.io/docs/
- Presentation slides: *coming soon*

## Team

| Name | Organization | Email |
|---|---|---|
| Geonhak Lee | Department of Information Systems, Hanyang University | thisiscrane@hanyang.ac.kr |
| Jemin An | Department of Information Systems, Hanyang University | ajm6396@hanyang.ac.kr |
| Jiwon Han | Department of Information Systems, Hanyang University | hjw9657@hanyang.ac.kr |
| Hyunseo Choi | Department of Information Systems, Hanyang University | hyunseo615@hanyang.ac.kr |
