Here’s a polished **`README.md`** you can drop straight into your repo, updated with:

* AI AED dispatch + guidance for cardiac arrest
* 5th place at AVESHSAN 2025
* Clear sections for hackathons / recruiters / GitHub

---

````md
# 🚑 SAHAYAK — AI AED Dispatch & Cardiac Arrest Guidance System

SAHAYAK is an AI-powered emergency response platform that automatically identifies and dispatches the nearest available AED and guides bystanders through CPR and defibrillation during sudden cardiac arrest.

By combining real-time mapping, intelligent dispatch, and generative AI guidance, SAHAYAK aims to reduce response times and improve out-of-hospital cardiac arrest survival — directly contributing to **UN Sustainable Development Goal 3: Good Health and Well-being**.

> 🏅 **Recognition:** 5th Place at **AVESHSAN 2025** (Project Showcase)

---

## 💡 Core Idea

Most cardiac arrest victims never receive timely CPR or defibrillation, even when AEDs are nearby. SAHAYAK turns bystanders into effective first responders by:

- Finding the closest AED
- Guiding them step-by-step in real time
- Supporting dispatchers and EMS with AI-driven intelligence

---

## 🔑 Key Features

### 1. Real-Time AED Fleet Management
- Live map of public-access AEDs using **MapLibre GL**
- Status tracking for each AED:
  - `Operational`
  - `Active Incident`
  - `Maintenance Required`
- Device-level details: battery level, last self-test, last usage.

### 2. AI-Powered Incident Triage
- Analyzes caller/incident descriptions using **Google Gemini** via **Genkit**
- Classifies emergency type (e.g., *Cardiac Arrest*, *Chest Pain*, *Collapse Unconscious*)
- Returns:
  - Triage label
  - Confidence score
  - Suggested follow-up questions for the dispatcher

### 3. Intelligent AED Dispatch System
- Automatically identifies the **nearest AED(s)** to the incident location
- Calculates **routes and ETAs** in real time
- Simulates responder/AED movement on the map:
  - Base → Incident → Hospital → Base
- Special logic for complex scenarios (e.g., multi-victim / mass casualty events)

### 4. Real-Time CPR & AED Guidance
- Generates **scenario-aware text + audio instructions** using TTS:
  - Hands-only CPR steps
  - Compression rate and depth prompts
  - AED placement and shock instructions
- Tailored to:
  - Adult vs child
  - Single rescuer vs multiple rescuers
- Designed for **non-medical lay responders** under stress.

### 5. AI-Driven Post-Incident Analysis
- **AI Eyes**:
  - Analyzes event logs to estimate CPR quality:
    - Compression rate
    - Compression depth (approx. via cadence & timing)
    - Pauses and no-flow time
- **AI Brain**:
  - Uses ECG rhythms and timeline events to:
    - Suggest possible causes (e.g., VF, VT, asystole)
    - Summarize clinical events
- Generates **text and audio debriefs** for:
  - Training
  - QA review
  - Documentation

### 6. Predictive Maintenance for AEDs
- Monitors:
  - Device logs
  - Battery levels
  - Usage patterns
- Predicts:
  - Next service window
  - Battery replacement needs
- Flags devices **before** they fail, reducing downtime.

---

## 🧩 Tech Stack

**Frontend**
- [Next.js](https://nextjs.org/)
- React + TypeScript
- Tailwind CSS
- ShadCN UI Components

**Mapping & Simulation**
- MapLibre GL for real-time maps and unit movement

**AI / GenAI**
- Google Gemini models
- Genkit (Google’s open-source GenAI framework)

**State Management**
- React Context API

**Auth**
- Mocked authentication (can be replaced with Firebase Auth or other providers)

---

## 🏗️ High-Level Architecture

- **Client (Next.js App)**
  - Dashboard and live map for AEDs and incidents
  - Incident creation + triage interface
  - Responder and AED simulation view
- **AI Services (via Genkit + Gemini)**
  - Incident triage
  - Guidance generation (CPR / AED scripts)
  - Post-incident summaries (text + audio script)
- **Backend / APIs (Prototype Level)**
  - Mock services for:
    - AED registry
    - Incident logs
    - Device telemetry
  - Can be replaced with:
    - FHIR/HL7 compatible systems
    - Real AED telematics APIs

---

## 🚀 Getting Started

This is a Next.js project bootstrapped with `create-next-app`.

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/sahayak.git
cd sahayak
````

### 2. Install Dependencies

```bash
npm install
# or
yarn install
```

### 3. Environment Setup

Create a `.env.local` file and configure:

```env
GENKIT_API_KEY=your_gemini_or_genkit_key
MAP_TILE_API_KEY=your_map_tiles_key
```

> For now, the project uses mock data where real API keys are not available.

### 4. Run the Dev Server

```bash
npm run dev
# or
yarn dev
```

Open your browser at: `http://localhost:3000`

The main dashboard page lives at:

```bash
src/app/(main)/page.tsx
```

---

## 📂 Project Structure (Simplified)

```text
src/
  app/
    (main)/
      page.tsx          # Main dashboard UI (map, incidents, AEDs)
  components/
    map/                # MapLibre-based components
    incidents/          # Incident cards, triage views
    aeds/               # AED list, status tags, details
    analysis/           # AI Eyes & AI Brain views
  lib/
    ai/                 # Genkit flows, Gemini prompts
    mock/               # Mock data and APIs for demo
    utils/              # Helper functions (routing, ETAs, etc.)
```

---

## 🧭 Roadmap / Future Work

* Integrate real AED APIs and EMS systems
* Add real-time websocket updates for incidents and responder locations
* Support multi-language CPR & AED guidance
* Compliance-focused logging for medico-legal requirements
* Mobile-first responder app version

---

## 🙏 Acknowledgements

* **AVESHSAN 2025** organizers and judges for the platform and recognition.
* Mentors, peers, and testers who provided feedback during prototyping.
* Open-source communities behind Next.js, MapLibre, Tailwind, ShadCN, and Genkit.

---

## 📫 Contact

If you’re interested in:

* Collaborating on research / pilot deployments
* Integrating SAHAYAK with existing EMS/AED networks
* Using this as a base for academic or healthcare innovation

Feel free to reach out or open an issue in the repository.

> **When a heart stops, every second counts.
> SAHAYAK’s goal is to make sure technology doesn’t. ❤️‍🩹**

```


