# ⚡ Post-Workshop Challenge: From Toy to Needle-Mover

> Building a prototype is fun. Solving an expensive operational headache is what gets you paid, promoted, or funded.

Now that you've built and deployed **AnakKost Eats**, it's time to translate these capabilities into your actual business, department, or client work.

---

## 🧭 Part 1: The Needle-Mover Diagnostic

Do not open Stitch or AI Studio until you have answered these three questions in plain writing:

### 1. What business use case do you actually want to tackle?
Don't build another generic chat window. Identify an existing **"Human Router"** bottleneck where an employee manually acts as middleware:
- **Operations:** Vendor quotation comparison, material yield estimation, shift scheduling triage.
- **Customer Experience:** Messy WhatsApp order intake, warranty claim triage, return eligibility routing.
- **Sales & Commercial:** Instant custom proposal generation, B2B product specification matching.
- **Internal Knowledge:** Frontline SOP lookup for on-duty staff when managers are off-site.

> **Fill in the blank:**  
> *"Our business currently loses [X hours / Rp Y] every week because [Role/Person] manually reviews [Messy Input] and types out [Actionable Output]. We will replace that manual step with an automated interface."*

### 2. Will that move your needle?
Be brutally honest with impact metrics. If it doesn't move a needle, pick another problem:
* **Time:** Does it save at least 5–10 staff hours every week?
* **Cost:** Does it directly reduce operating overhead, agency retainers, or margin leak?
* **Revenue:** Does it cut response latency from 4 hours to 60 seconds so you win more deals?
* **Capacity:** Does it enable your current team of 3 to handle the volume of 10 without hiring?

### 3. What kind of solution will you build?
Map out the two halves of your architecture:
* **The Front of House (Stitch):** Who is the user? (Field technician on mobile, desk-bound account rep, or external client?)
* **The Kitchen Engine (AI Studio + Gemini Flash):** What decision rules or grounded lookups must it execute?
* **The Output:** What single ticket, quotation table, or database entry needs to be created?

---

## 🏢 Part 2: Real-World Business Blueprints (Pick One)

If you don't have a clear project in mind, build one of these three battle-tested business archetypes:

### Blueprint A: The Instant B2B Quotation Engine (Agencies / Manufacturing / Retail)
* **The Problem:** Clients send multi-paragraph, messy WhatsApp specifications (*"Mau sablon kaos polo 200 pcs, bordir dada & punggung, bahan combed 24s adem, budget under 90rb, kirim ke Surabaya barat"*). Sales reps spend 45 minutes manually calculating margins.
* **The Solution:** 
  * Paste raw client text into a single input field.
  * Gemini Flash extracts quantities, dimensions, fabric types, and delivery deadlines.
  * Calculates margins against pricing thresholds and outputs a client-ready formatted quotation table.

### Blueprint B: Frontline Shift & SOP Triage (Hospitality / F&B / Clinics)
* **The Problem:** Frontline staff hit on-duty emergencies (*"AC kamar 302 bocor air"*, *"Mesin kasir offline waktu rush hour"*). They panic, call the off-duty manager, or give poor customer responses.
* **The Solution:**
  * Clean mobile triage screen with 4 category buttons: Facilities, Payment, Guest Complaints, Kitchen.
  * Staff types or voice-inputs the issue.
  * App checks grounded SOP rules and returns a 3-step immediate action plan + auto-generates a maintenance log.

### Blueprint C: Client Eligibility & Document Gatekeeper (Consulting / Legal / Financial Services)
* **The Problem:** 70% of inbound client inquiries waste senior consultant time because they lack required paperwork, licenses, or minimum turnover requirements.
* **The Solution:**
  * Interactive qualification questionnaire.
  * Evaluates responses against criteria, issues a green/yellow/red readiness score, and provides a clear checklist of missing items before booking an appointment.

---

## 🏆 Part 3: The Antigravity "Knead & Bake" Hacker Challenge

Ready for the ultimate builder flex? Move your prototype from a single-file sandbox to a hardened, agentic workflow using **Project Antigravity**:

```
┌────────────────────────┐      1. Export Code      ┌─────────────────────────┐
│    Google AI Studio    │ ───────────────────────> │   Project Antigravity   │
│  (Working Prototype)   │                          │    (Agent Workspace)    │
└────────────────────────┘                          └────────────┬────────────┘
                                                                 │
                                                            2. Add Skills
                                                                 │
                                                                 ▼
┌────────────────────────┐      4. Redeploy         ┌─────────────────────────┐
│    Google Cloud Run    │ <─────────────────────── │ 3. "Knead & Let Rest"   │
│   (Hardened Service)   │   "Ship to Production"   │    (Self-Healing Loop)  │
└────────────────────────┘                          └─────────────────────────┘
```

### The Step-by-Step Recipe:
1. **Export Code:** Export your generated application bundle from AI Studio Build mode.
2. **Import into Antigravity:** Open the project inside your Antigravity agent workspace.
3. **Equip Skills:** Connect external tools and connectors:
   * Google Sheets / BigQuery connector for transaction logging.
   * Webhook dispatcher (Slack / WhatsApp / Email notification).
4. **"Knead the Code" (The Refactor Prompt):** Instruct your agent to harden the logic:
   ```text
   Knead this codebase:
   1. Break down the monolithic file into clean, modular components.
   2. Wrap API calls with retry backoff and user-friendly error banners.
   3. Ensure all environment secrets and API keys are strictly encapsulated.
   4. Format the final output as clean, schema-validated JSON.
   ```
5. **Let It Rest:** Let the agent run test cases, identify syntax or layout edge cases, and patch them automatically.
6. **Redeploy:** Push the refactored, hardened service back to **Google Cloud Run** and grab your updated live HTTPS URL!

---

## 📤 Submission & Community Showcase

When your needle-mover is live:
1. Record a 30-second screen capture of your app taking messy input and producing business output.
2. Grab your live Cloud Run URL.
3. Post it on LinkedIn / X and tag the mentors:
   - What operational bottleneck did you tackle?
   - How much time or cost does it save?
   - Stack used: `Google Stitch` + `AI Studio` + `Cloud Run`.