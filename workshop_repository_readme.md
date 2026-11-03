# AnakKost Eats — Surabaya Campus Food Survival Guide
> A 90-Minute No-Code to Cloud Run Workshop powered by Google Stitch & Google AI Studio.

![Status](https://img.shields.io/badge/Status-Workshop--Ready-brightgreen)
![Target Audience](https://img.shields.io/badge/Audience-Non--Technical-orange)
![Stack](https://img.shields.io/badge/Stack-Stitch%20%2B%20AI%20Studio%20%2B%20Cloud%20Run-blue)
![Model](https://img.shields.io/badge/Gemini-3.6%20Flash%20%2F%203.8%20Flash-violet)

---

## 🎯 About The Workshop

**AnakKost Eats** is designed to take complete non-tech participants from an idea to a fully shipped web application deployed on Google Cloud Run within 90 minutes. 

Instead of getting bogged down in boilerplate code, local environment configs, or Git commands, attendees leverage:
1. **Google Stitch ("Front of House"):** To visually generate and iterate responsive mobile interfaces using natural language prompts.
2. **Google AI Studio ("The Kitchen Engine"):** To wire logic, add dynamic Google Maps/Search grounding with Gemini 3.6 Flash / 3.8 Flash, and store findings in a client-side IndexedDB cache.
3. **1-Click Google Cloud Run Deployment:** To publish an actual live URL accessible on any mobile browser.

---

## 🕒 Session Schedule (90 Minutes)

| Segment | Timing | Activity | Milestone Output |
| :--- | :--- | :--- | :--- |
| **1. Hook & Brief** | 00–10 min | Inspect the live app on mobile; pick campus persona (ITS, UNAIR, UPN, UBAYA, Petra). | App Brief Locked |
| **2. Design in Stitch** | 10–30 min | Prompt UI screens, refine themes, export directly to AI Studio. | 2 Complete Screens |
| **3. Build in AI Studio** | 30–65 min | Seed initial spots, wire grounding, connect "Senior Kampus" AI advice, set up cache. | Working Interactive App |
| **4. Ship to Cloud Run** | 65–80 min | One-click build & deploy directly from Google AI Studio. | Live `*.a.run.app` Link |
| **5. Demo Showdown** | 80–90 min | Attendees vote on peer apps; prizes awarded to deployed solutions. | Winner Crowned |

---

## 📂 Repository Contents

```text
├── README.md       # Workshop overview, prerequisites, and evaluation rubric
└── codelabs.md     # Step-by-step participant guide with exact copy-paste prompts
```

---

## 🎒 Prerequisites

* A desktop/laptop with **Google Chrome** installed.
* A Google Account logged into:
  * [Google Stitch](https://stitch.withgoogle.com/)
  * [Google AI Studio](https://aistudio.google.com/)
* No prior coding experience, Git knowledge, or CLI tools required.

---

## 🏆 Scoring Rubric (Demo Showdown)

At minute 80, participants display their QR codes or submit their live links. Submissions are judged on:

1. **Authenticity & Flavor (40%):** Does the "Senior Kampus" advice feel genuine, humorous, and localized (Surabaya student slang like *rek*, *cak*, *wareg*, *porsi kuli*)?
2. **Dynamic Logic & Interactivity (30%):** Do category chips and mood filters update the menu? Does the local cache work seamlessly?
3. **Shipped to Production (30%):** Is the app accessible live on an external mobile device via a valid Cloud Run URL (`https://...a.run.app`)?

---

## 📖 Getting Started

To begin building the project, follow the instructions in [`codelabs.md`](./codelabs.md).