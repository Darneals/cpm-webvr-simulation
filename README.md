# Immersive Browser WebVR Simulation for Project Management Education
### A Mixed-Methods Evaluation of CPM Knowledge, Cognitive Load, and Engagement in a BYOD Classroom

> A zero-cost, browser-native WebVR simulation for teaching the Critical Path Method in undergraduate project management education.

[![Live Simulation](https://img.shields.io/badge/Live%20Simulation-Launch%20Now-blue?style=for-the-badge)](https://darneals.github.io/cpm-webvr-simulation/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)
[![A-Frame](https://img.shields.io/badge/A--Frame-v1.4.0-orange?style=for-the-badge)](https://aframe.io)
[![No Installation](https://img.shields.io/badge/No%20Installation-Required-brightgreen?style=for-the-badge)](#access)

---

## Associated Paper

**Oyefidein, D. T. (2025).** Immersive Browser WebVR Simulation for Project Management Education: A Mixed-Methods Evaluation of CPM Knowledge, Cognitive Load, and Engagement in a BYOD Classroom. *Computers & Education: X Reality*. Elsevier. [Under review]

---

## Overview

This repository contains a browser-based WebVR simulation for teaching the Critical Path Method (CPM) to undergraduate Computer Science and Engineering students. The simulation was designed, built, and evaluated as part of a PhD research study at Universiti Teknologi PETRONAS (UTP), Malaysia.

The simulation renders a nine-task software development project as a navigable three-dimensional CPM network. Students physically move through the network by gazing at task nodes, receive audio-narrated pedagogical explanations within each node scene, and interact with a Consequence Simulator that demonstrates cascade delay propagation in real time.

**The entire simulation runs in a standard web browser. No installation, no headset, no account, no cost.**

---

## Live Simulation

🔗 **https://darneals.github.io/cpm-webvr-simulation/**

Open this URL in Chrome on any device — Android phone, iPhone, tablet, or desktop — and the simulation loads immediately.

| Browser | Platform | Status |
|---------|----------|--------|
| Google Chrome | Android, iOS, Windows, macOS | ✅ Recommended |
| Safari | iOS, macOS | ✅ Fully functional |
| Microsoft Edge | Windows, macOS | ✅ Fully functional |

---

## The CPM Scenario

The simulation embeds a nine-task software development project. The scenario was selected for contextual relevance to Computer Science undergraduates.

| Node | Task | Duration | Predecessors | ES | EF | LS | LF | TF | FF | Path |
|------|------|----------|-------------|----|----|----|----|----|----|------|
| A | Requirements Analysis | 3 days | None | 0 | 3 | 0 | 3 | 0 | 0 | **Critical** |
| B | UI/UX Design | 3 days | A | 3 | 6 | 4 | 7 | 1 | 0 | Non-Critical |
| C | Database Schema Design | 2 days | A | 3 | 5 | 3 | 5 | 0 | 0 | **Critical** |
| D | Backend API Development | 6 days | C | 5 | 11 | 5 | 11 | 0 | 0 | **Critical** |
| E | Frontend Development | 4 days | B | 6 | 10 | 7 | 11 | 1 | 1 | Non-Critical |
| F | API Integration | 3 days | D+E | 11 | 14 | 11 | 14 | 0 | 0 | **Critical** |
| G | Unit Testing | 2 days | F | 14 | 16 | 14 | 16 | 0 | 0 | **Critical** |
| H | User Acceptance Testing | 3 days | G | 16 | 19 | 16 | 19 | 0 | 0 | **Critical** |
| I | Deployment | 1 day | H | 19 | 20 | 19 | 20 | 0 | 0 | **Critical** |

**Critical path:** A → C → D → F → G → H → I = **20 days**  
**Non-critical path:** A → B → E → F = 19 days  
**Float:** Nodes B and E each carry 1 day total float

---

## Simulation Structure

The simulation comprises 11 HTML scenes served as static files from GitHub Pages.

```
index.html              ← Hub scene — full CPM network view
node-a.html             ← Requirements Analysis
node-b.html             ← UI/UX Design (non-critical, Float: 1)
node-c.html             ← Database Schema Design
node-d.html             ← Backend API Development (longest critical task)
node-e.html             ← Frontend Development (non-critical, Float: 1)
node-f.html             ← API Integration (convergence point)
node-g.html             ← Unit Testing
node-h.html             ← User Acceptance Testing
node-i.html             ← Deployment (project end, Day 20)
consequence.html        ← Cascade Delay Simulator
```

### Hub Scene
The hub scene presents all nine task nodes as colour-coded emissive spheres in a navigable 3D environment:
- 🔴 **Red** — Critical path nodes (zero float)
- 🟢 **Green** — Non-critical nodes (float available)
- 🟡 **Gold** — Project end node (Node I, Day 20)

### Node Scenes
Each of the nine node scenes contains three components:
1. **360° photorealistic background** — a workplace environment relevant to the task
2. **Floating information panel** — task name, duration, ES, EF, LS, LF, Total Float, Free Float, path status
3. **Audio narration** — a 30–45 second pedagogical explanation of the task's significance

### Consequence Simulator
Allows students to trigger a one-day delay on any task node and observe the effect in real time:
- **Critical path node** → cascade animation propagates downstream; Project End counter: Day 20 → Day 21
- **Non-critical node** → float absorption demonstrated; Project End counter remains at Day 20

---

## Navigation

The simulation uses **gaze-based interaction** — compatible with all devices without controllers.

| Action | Method |
|--------|--------|
| Enter a node scene | Gaze at any node sphere for 2 seconds |
| Launch Consequence Simulator | Gaze at the simulator portal for 2 seconds |
| Return to hub | Gaze at the Return button inside any node scene |
| Trigger cascade delay | Gaze at any task node in the simulator |

> On desktop Chrome and Edge, mouse hover replaces gaze activation.

---

## Technology Stack

Every tool in this simulation is free and open source. Total development and hosting cost: **$0.00**

| Tool | Version | Purpose | Cost |
|------|---------|---------|------|
| [A-Frame](https://aframe.io) | v1.4.0 | 3D/WebVR scene rendering | Free (MIT) |
| [GitHub Pages](https://pages.github.com) | — | Static hosting and HTTPS delivery | Free |
| [Brand Studio](https://brandstudio.ai) | — | 360° background image generation | Free tier |
| [ttsmp3.com](https://ttsmp3.com) | — | Text-to-speech audio narration (MP3) | Free |
| [Squoosh](https://squoosh.app) | — | Image compression (<200 KB per image) | Free (open source) |

---

## Device Compatibility

| Device | Browser | Confirmed |
|--------|---------|-----------|
| Android smartphone | Chrome | ✅ |
| Android tablet | Chrome | ✅ |
| iPhone / iPad | Safari | ✅ |
| Windows laptop | Chrome / Edge | ✅ |
| macOS | Safari / Chrome | ✅ |

No installation. No user account. No institutional network beyond standard internet access.

---

## Running Locally

```bash
# Clone the repository
git clone https://github.com/Darneals/cpm-webvr-simulation.git
cd cpm-webvr-simulation

# Serve locally using Python (no install required)
python -m http.server 8000

# Or using Node.js
npx live-server
```

Open `http://localhost:8000` in Chrome.

> The simulation must be served over HTTP/HTTPS — opening `index.html` directly as `file://` will not work due to browser security restrictions on local audio loading.

---

## Adapting the Simulation

To adapt this simulation to a different CPM scenario:

1. Edit duration, float, and schedule values in each `node-x.html` file
2. Replace background images in `/assets/images/` with your own 360° environments
3. Replace audio narrations in `/assets/audio/` with your own recordings or TTS files
4. Update dependency lines and node positions in `index.html`

No JavaScript expertise required for basic scenario modifications — all content is in readable HTML attributes.

---

## Study Summary

This simulation was evaluated in a counterbalanced within-subjects quasi-experimental mixed-methods study.

| Measure | WebVR | Traditional | Statistic |
|---------|-------|-------------|-----------|
| Quiz score (0–13) | M = 8.93, SD = 2.13 | M = 7.22, SD = 1.91 | t(26) = 19.0, p < .001, d = 3.66 |
| NASA-TLX (0–10) | M = 4.04, SD = 0.694 | M = 5.11, SD = 0.659 | t(26) = −36.1, p < .001, d = −6.95 |
| UES-SF (1–5) | M = 3.75, SD = 0.441 | — | Above scale midpoint |
| Engagement–performance | r(25) = 0.959 | — | p < .001 |
| Retention (Week 10) | M = 7.59 | M = 7.22 (post-test) | Retained advantage at 3 weeks |

**Qualitative themes:** Spatial discovery of critical dependencies · Float comprehension through embodied navigation · Self-directed exploration and pacing · Perceived authenticity of the scenario

---

## Supplementary Materials

```
supplementary/
├── instruments/
│   ├── quiz-form-a.pdf           ← CPM Knowledge Quiz Form A (13 items)
│   ├── quiz-form-b.pdf           ← CPM Knowledge Quiz Form B (13 items)
│   ├── quiz-form-c.pdf           ← CPM Knowledge Quiz Form C — Retention (13 items)
│   ├── reflection-journal.pdf    ← Structured Reflection Journal (2 prompts)
│   ├── nasa-tlx-form.pdf         ← NASA Task Load Index (6 subscales)
│   ├── ues-sf-form.pdf           ← User Engagement Scale Short Form (12 items)
│   ├── interview-protocol.pdf    ← Semi-structured Interview Protocol (8 questions)
│   └── quiz-scoring-rubric.pdf   ← Model answers and marking criteria
```

---

## Data Availability

The anonymised dataset supporting the quantitative findings is available from the corresponding author upon reasonable request, subject to institutional ethics guidelines.

---

## Citation

```bibtex
@article{oyefidein2025cpmwebvr,
  title   = {Immersive Browser {WebVR} Simulation for Project Management Education:
             A Mixed-Methods Evaluation of {CPM} Knowledge, Cognitive Load,
             and Engagement in a {BYOD} Classroom},
  author  = {Oyefidein, Daniel Tonye},
  journal = {Computers \& Education: X Reality},
  publisher = {Elsevier},
  year    = {2025},
  note    = {Under review},
  url     = {https://github.com/Darneals/cpm-webvr-simulation}
}
```

---

## Licence

This project is licensed under the MIT Licence — see the [LICENSE](LICENSE) file for details.

---

## Contact

**Daniel Tonye Oyefidein**  
PhD Candidate, Department of Computer and Information Sciences  
Universiti Teknologi PETRONAS, Perak, Malaysia

For questions about the simulation, the research, or adaptation for your institution, please open a GitHub Issue.

---

*Built for accessible, zero-cost immersive education.*
