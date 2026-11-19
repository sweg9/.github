# NOVA

**Non-connected Object Vision and Actuation**

A camera finds wall switches, toggles and power strips, works out which device each one operates, and routines use them through wireless channels or, when those fail, a physical press by a robot (linear actuators on a cart in the prototype).

## Blog

https://app.notion.com/p/41776e6f9e9f8117aa9efc686be79329

## Architecture Design

![NOVA architecture: everything runs on one laptop at home. A k3d cluster holds the ingress, the server and the logging stack; the hub runs outside it and drives the webcam and the actuators.](architecture.png)

## Team

Department of Information Systems, Hanyang University

| Name | Organization | Email |
|---|---|---|
| Geonhak Lee | Department of Information Systems, Hanyang University | thisiscrane@hanyang.ac.kr |
| Jemin An | Department of Information Systems, Hanyang University | ajm6396@hanyang.ac.kr |
| Jiwon Han | Department of Information Systems, Hanyang University | hjw9657@hanyang.ac.kr |
| Hyunseo Choi | Department of Information Systems, Hanyang University | hyunseo615@hanyang.ac.kr |

## Repositories

| Repo | Role |
|---|---|
| [ai-engine](https://github.com/sweg9/ai-engine) | Control detection, VLM, state check, robot motion planner |
| [backend-server](https://github.com/sweg9/backend-server) | FastAPI backend: mapping, routines, orchestrator, channels, safety gate |
| [dataset](https://github.com/sweg9/dataset) | Switch-panel photos and labels for the detector |
| [live-demo](https://github.com/sweg9/live-demo) | Front end for the real camera and robot hand |
| [sim-demo](https://github.com/sweg9/sim-demo) | Unity simulator for demos without real hardware |
| [docs](https://github.com/sweg9/docs) | Development wiki: https://sweg9.github.io/docs/ |
| [harness](https://github.com/sweg9/harness) | Shared standards, skills and CI/CD |
