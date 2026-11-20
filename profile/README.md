# NOVA: Non-connected Object Vision and Actuation for Smart Home Routines

> 26-2 Hanyang University Software Engineering Project

<img src="hero.png" width="100%" alt="NOVA: a phone app with quick control of the main light and the robot task light, beside a light switch card and the tracked robot arm.">

---

## 📚 Documents

**Reports**
- Tech blog (Notion): *coming soon*
- Presentation slides: *coming soon*
- [Proposal (PDF)](https://sweg9.github.io/docs/papers/proposal.pdf): the reference document for the project
- [Proposal (LaTeX)](https://github.com/sweg9/docs/blob/main/public/papers/proposal.tex): the LaTeX source of the proposal
- [Development wiki](https://sweg9.github.io/docs/): every document below, with search and rendered API specs

**Overview**
- [Introduction](https://sweg9.github.io/docs/overview/): the problem, the seven stages, autonomy by risk and privacy
- [Requirements](https://sweg9.github.io/docs/product/requirements): FR-01 to FR-12, owners and how each is built
- [Architecture](https://sweg9.github.io/docs/overview/architecture): parts, data and interfaces
- [Stack](https://sweg9.github.io/docs/overview/stack): run modes, libraries, Kubernetes, logging and backups

<details>
<summary><b>Design · 4 docs</b></summary>

- [Database](https://sweg9.github.io/docs/overview/database): tables, enums and migrations
- [Modules](https://sweg9.github.io/docs/overview/modules): code layout of each repo
- [Models](https://sweg9.github.io/docs/product/models): detectors, state classifier and fingerprints
- [Related work](https://sweg9.github.io/docs/overview/related-work): what existing products and research leave open

</details>

<details>
<summary><b>API · 4 docs</b></summary>

- [Conventions](https://sweg9.github.io/docs/api/): rules shared by every API
- [backend-server API](https://sweg9.github.io/docs/api/backend-server): the HTTP API for the web app
- [Hub messages](https://sweg9.github.io/docs/api/hub-messages): WebSocket messages between the hub and the server
- [ai-engine interface](https://sweg9.github.io/docs/api/ai-engine): what the hub calls in ai-engine

</details>

<details>
<summary><b>Data, demo and environment · 5 docs</b></summary>

- [Labeling spec](https://sweg9.github.io/docs/dataset/labeling): how switch-panel photos are labeled
- [Dataset plan](https://sweg9.github.io/docs/dataset/PLAN): collection and split plan
- [live-demo plan](https://sweg9.github.io/docs/live-demo/PLAN): the web app and the demo screens
- [Simulator](https://sweg9.github.io/docs/product/simulator): Unity and web simulator, current state
- [Development environment](https://sweg9.github.io/docs/product/environment): tools and setup

</details>

<details>
<summary><b>Standards · 5 docs</b></summary>

- [Common rules](https://sweg9.github.io/docs/standards/common): rules C-01 to C-13 for every repo
- [Data model](https://sweg9.github.io/docs/standards/data-model): shared vocabulary and enums
- [Execution log](https://sweg9.github.io/docs/standards/execution-log): the run log format
- [AI output](https://sweg9.github.io/docs/standards/ai-output): rules for model outputs
- [Per-repo obligations](https://sweg9.github.io/docs/standards/per-repo): what each repo must provide

</details>

---

## 💁🏻‍♂️ Proposal

This project proposes NOVA, a system that lets a proactive smart-home agent operate controls that are not on the network: wall switches, toggles and power strips. Smart-home routines work only if every control the resident cares about is connected and registered, yet many are not, and in rented homes the wiring often cannot be changed.

In the proposed system, a camera finds each control and the system works out which device it operates, by watching the resident use it or by pressing it and comparing before and after. Routines then use these controls through wireless channels (Wi-Fi, IR, Bluetooth) first. When a wireless command fails and the Safety Guard finds no person or obstacle in the way, a robot presses the control and the camera checks the result. In the prototype, the robot is a set of linear actuators on a cart.

Every action is checked rather than assumed, high-risk devices always ask first, and every run updates channel scores and link confidence. Recognition runs on a hub at home with local models and the backend runs on the same laptop, so nothing leaves the home. This proposal demonstrates how unconnected controls can take part in proactive smart-home routines without replacing them.

---

## ⚙️ System Architecture

![NOVA System Architecture](./architecture.png)

---

## 📹 Video

**Demo video: coming soon**

Until then, the [web demo](https://sweg9.github.io/sim-demo/) runs the 20-second process (mapping, Wi-Fi failure, Safety Guard, physical press, camera check) in a browser, with no install. Its [source](https://github.com/sweg9/sim-demo/tree/main/web) also runs offline from a local copy.

---

## 🔗 Links

NOVA | Tech Blog - *coming soon*

NOVA | Presentation Slides - *coming soon*

[NOVA | Development Wiki](https://sweg9.github.io/docs/)

[NOVA | Proposal - PDF](https://sweg9.github.io/docs/papers/proposal.pdf)

[NOVA | Proposal - LaTeX](https://github.com/sweg9/docs/blob/main/public/papers/proposal.tex)

[NOVA | Web Demo](https://sweg9.github.io/sim-demo/)

---

## 👨🏻‍💻 Team Members

| Name | Organization | Email |
|------|---------------|-------|
| Geonhak Lee | Department of Information Systems, Hanyang University | [thisiscrane@hanyang.ac.kr](mailto:thisiscrane@hanyang.ac.kr) |
| Jemin An | Department of Information Systems, Hanyang University | [ajm6396@hanyang.ac.kr](mailto:ajm6396@hanyang.ac.kr) |
| Jiwon Han | Department of Information Systems, Hanyang University | [hjw9657@hanyang.ac.kr](mailto:hjw9657@hanyang.ac.kr) |
| Hyunseo Choi | Department of Information Systems, Hanyang University | [hyunseo615@hanyang.ac.kr](mailto:hyunseo615@hanyang.ac.kr) |
