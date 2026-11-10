# Build Apps with Stitch + Google AI Studio 🍜✨

### Workshop Project: "AnakKost Eats"
*From Prompt to Production: Build and ship a student food discovery app to Google Cloud Run in 90 minutes.*

---

## 0. The Idea Behind This Workshop

Most business software projects stall not because teams lack ideas, but because they build **toys instead of tools**. They ask, *"What cool app can I make?"* instead of asking, ***"Where is information getting stuck in our daily operations?"***

### The "Human Router" Bottleneck
In almost every business—from agencies to retail, clinics to hospitality—the single biggest operational drag is a human acting as a manual router:
* A client sends a chaotic, unstructured WhatsApp message.
* A staff member reads it, manually calculates numbers against pricing rules or internal SOPs.
* The staff member spends 30 minutes typing an email or quotation back.

This workshop teaches you how to dismantle that bottleneck in 90 minutes using AI:
1. **Google Stitch ("Front of House"):** Builds an intuitive front door for messy human input in minutes without designers or CSS.
2. **Google AI Studio ("The Kitchen Engine"):** Applies decision rules, dynamic reasoning (Gemini Flash), and grounding without backend developers.
3. **Google Cloud Run:** Ships a production-grade, shareable tool to the web in one click.

### Why "AnakKost Eats"?
We use a Surabaya student food finder as our workshop playground because everyone understands hunger, tight budgets, and late-night cravings. It is a lightweight, relatable sandbox. But the exact architecture you build today—**messy input $\rightarrow$ AI evaluation $\rightarrow$ cached rules $\rightarrow$ actionable output**—is the exact blueprint you will use on Monday morning to automate instant B2B quotes, internal SOP triage, or customer intake funnels.

---

## 🧭 The 4-Step Business Friction Audit

Before writing a single prompt, evaluate your workflow through this 4-step framework:

```
┌─────────────────────────────────┐
│ 1. The Human Chaos (Input)      │ ──> Where do clients/staff send messy, unstructured requests?
└────────────────┬────────────────┘
                 │
                 ▼
┌─────────────────────────────────┐
│ 2. The Decision Friction        │ ──> What repetitive rule or evaluation does a human currently calculate?
└────────────────┬────────────────┘
                 │
                 ▼
┌─────────────────────────────────┐
│ 3. Does It Move Your Needle?    │ ──> Does automating this save Time, cut Cost, or unlock Capacity?
└────────────────┬────────────────┘
                 │
                 ▼
┌─────────────────────────────────┐
│ 4. The Actionable Output        │ ──> What single ticket, quotation, or status needs to update?
└─────────────────────────────────┘
```

---

## 📚 What You'll Learn

- How to translate a real operational process into a responsive UI with **Google Stitch**.
- How to execute the direct **"Build with AI Studio"** handover bridge without exporting code files.
- How to power dynamic discovery using **Gemini 3.6 Flash / 3.8 Flash** with live Google Search & Maps Grounding.
- How to prompt an AI agent to build a client-side **IndexedDB / LocalStorage cache** to eliminate redundant API roundtrips and cut token costs.
- How to deploy a live web app directly to **Google Cloud Run** in 1 click.
- How to troubleshoot UI/logic bugs using the **Screenshot Debug Protocol** without inspecting code.

---

## 🛠️ What You'll Build

- **Screen 1 (Campus Food Feed):** Campus selector dropdown, price filters ("Porsi Kuli <20rb", "Free Nasi & Es Teh"), dynamic card feed, and a "Pilihin Makan Dong Cak!" surprise button.
- **Screen 2 (Detail & AI Senior):** Interactive concierge powered by Gemini with a "Senior Kampus" persona sharing insider student survival tips in Surabaya slang (*rek*, *wareg pol*, *cak*).
- **Smart Cache Engine:** Instant loading for previously fetched warungs to keep token usage lean and avoid repetitive API latency.
- **Production Deployment:** A live HTTPS container running on Google Cloud Run (`*.a.run.app`).

---

## 🧰 What You'll Need

- A laptop with **Google Chrome** installed.
- A Google Account logged into [Google Stitch](https://stitch.withgoogle.com/) and [Google AI Studio](https://aistudio.google.com/).
- No prior coding, Git, Docker, or command line experience required.

---

## 🎯 Workshop Goals

By the end of this 90-minute workshop, you will:
1. Master the mental model: UI Canvas (Stitch) vs Reasoning Engine (AI Studio) vs Host (Cloud Run).
2. Experience zero-boilerplate prompt-driven app development.
3. Deploy an authentic, working web application to Cloud Run and test it live on your phone.
4. Identify at least one "Human Router" bottleneck in your daily work that you can automate on Monday.

---

## 🕒 Schedule & Milestones

| Time | Segment | Focus | Milestone Output |
| :--- | :--- | :--- | :--- |
| **00–10 min** | **Brief & The Framework** | Demo live app on mobile; introduce the Human Router & Needle Metric. | Problem & brief locked |
| **10–30 min** | **Design in Stitch** | Prompt screens, iterate styling, test mobile viewport. | 2 UI screens ready |
| **30–65 min** | **Build in AI Studio** | Bridge export, wire Gemini Flash, grounding, and cache. | Interactive working app |
| **65–80 min** | **Deploy to Cloud Run** | 1-click build and live container generation. | Live `*.a.run.app` URL |
| **80–90 min** | **Demo Showdown** | Test on real smartphones; audience vote on best execution. | Winner awarded |

---

## 🚀 Get Started

👉 **[Open the Codelab →](./codelabs.md)**  
👉 **[Take the Business Challenge →](./challenge.md)**

---

*© Google Developer Workshop — Educational use only.*
