# Codelab: Zero to Deployed — Building "AnakKost Eats" with Google Stitch & AI Studio

A hands-on, non-technical guide to generating front-end interfaces, infusing them with Gemini operational logic, and deploying a production-ready application to Cloud Run.

---

## 1. Overview & Architecture

### What You Will Build
You will build **AnakKost Eats (Surabaya Campus Edition)**: A survival food-finder built specifically for university students (ITS, UNAIR, UPN, UBAYA, Petra). It solves the daily student dilemma: *"Makan di mana yang murah, porsi kuli, buka sampai malam, dan wifi kenceng buat nugas?"*

### The Two-Engine Concept
* **Front of House (Google Stitch):** Designs the visual dining room — screens, typography, layout, buttons, and aesthetic vibes. No manual CSS or HTML authoring required.
* **The Kitchen Engine (Google AI Studio):** Connects the internal machinery — wires actions to buttons, hooks up the Gemini model API with live search and maps grounding, manages local persistence, and serves live app traffic.

```
┌────────────────────────┐      Direct Export       ┌────────────────────────┐      1-Click Deploy      ┌────────────────────────┐
│     Google Stitch      │ ───────────────────────> │  Google AI Studio      │ ───────────────────────> │   Google Cloud Run     │
│  (UI / Visual Canvas)  │    "Build with AI"       │ (Gemini 3.6/3.8 Flash) │      "Deploy App"        │   (Live Public URL)    │
└────────────────────────┘                          └────────────────────────┘                          └────────────────────────┘
                                                                │
                                                    ┌───────────┴───────────┐
                                                    │ Grounding + Cache     │
                                                    │ - Google Maps/Search  │
                                                    │ - IndexedDB Cache     │
                                                    └───────────────────────┘
```

---

## 2. Step 1: Design the UI in Google Stitch (0–20 min)

### 2.1 Prompt the Interface
1. Open [Google Stitch](https://stitch.withgoogle.com/) and click **New Project**.
2. In the bottom prompt console, paste the master UI prompt below and press **Enter**:

```text
Create a modern mobile web app called "AnakKost Eats" - Surabaya Student Food Survival Guide.
Aesthetic: High-energy street style with deep navy slate background and electric lime/amber badges.

Screen 1: Campus Food Feed
- Header: App name "AnakKost Eats" with campus selector dropdown ("Keputih/Gebang ITS", "Dharmawangsa UNAIR", "Siwalankerto Petra", "Rungkut UPN").
- Hero Banner: Headline "Tanggal Tua Tetap Makan Enak!" with subtitle "Kurasi warung porsi kuli, murah meriah, ramah dompet mahasiswa."
- Filter Chips:
  * "Porsi Kuli (<20rb)"
  * "Buka 24 Jam / Begadang"
  * "Free Nasi & Es Teh"
  * "Wifi Kenceng Nugas"
- Quick Action Button: "Pilihin Makan Dong Cak!" (styled as a high-contrast accent button).
- Food Cards Grid: Showing spot name, distance in km, price badge (e.g. "Rp 12.000 - 18.000"), signature menu, and "Rating Dompet" (1-5 koin).

Screen 2: Detail & Warung Advice
- Big food photo container with warung name and live status badge ("Buka Sampe Jam 03:00").
- "Petuah Senior Kampus" container (AI advice section) with interactive prompt input and button "Tanya Menu Rahasia".
- Direct action buttons: "Buka Google Maps" and "Simpan Favorit".
- Fixed bottom navigation: Jelajah, Favorit, Dompet Tracker.
```

### 2.2 Refine and Tweak
1. Inspect the generated screens in the preview window.
2. If you want to tweak styles, select the element directly on the canvas and submit a targeted refinement:
   ```text
   Make the quick action button 'Pilihin Makan Dong Cak!' glowing amber with rounded-full pill corners.
   ```
3. Keep the layout focused on 2 cohesive screens for maximum build speed.

---

## 3. Step 2: Bridge Stitch to Google AI Studio (20–25 min)

1. In the upper-right toolbar of Google Stitch, click **Export**.
2. Select **AI Studio** in the export format list.
3. Replace the default text in the **Description** field with this logic directive:

```text
Keep the visual Tailwind UI and campus styling intact. Connect the campus dropdown and filter chips to filter the food cards list. Connect the 'Pilihin Makan Dong Cak!' button to randomly select a campus warung and trigger a pop-up modal with humorous advice from 'Senior Kampus' speaking authentic Surabaya slang (rek, cak, wareg pol, kantong aman). Prepare the app to load live grounded data via Gemini Flash.
```

4. Click **Build with AI Studio**. A new browser tab will open directly with your UI loaded into Google AI Studio Build mode.

---

## 4. Step 3: Implement Gemini Logic & Smart Cache (25–55 min)

In Google AI Studio Build mode, use the chat console to guide the coding agent.

### 4.1 Seed the Default Warung Data
Submit this prompt to populate an immediate fallback state:

```text
Populate the app with these iconic Surabaya student food spots as initial default state:
1. Warung Tombo Luwe (Keputih ITS) - Porsi barbar, masakan rumahan prasmanan, Rp 12.000, 4.8 bintang.
2. Bebek Bagong (Keputih Utara ITS) - Bebek gurih bumbu hitam + protolan, Rp 18.000, 4.7 bintang.
3. Soto Ayam Barokah (Keputih Tegal) - Soto kuah koya gurih melimpah, Rp 15.000, 4.8 bintang.
4. Tahu Telur Pak Jayen (Dharmahusada UNAIR B) - Tahu telur bumbu petis jumbo, Rp 20.000, 4.9 bintang.
5. Ayam Geprek Joder (Gebang ITS) - Pedas nampol level bebas, free refill nasi, Rp 14.000, 4.8 bintang.

Ensure clicking campus selector or filter chips immediately filters these cards.
```

### 4.2 Add Grounded Discovery & Local Cache
Next, inject real-time grounding via Gemini 3.6 Flash / 3.8 Flash, backed by local storage caching to conserve tokens:

```text
Implement dynamic discovery with Gemini 3.6 Flash / 3.8 Flash:
1. Grounding: Enable Google Search and Google Maps grounding tools.
2. Discovery Trigger: When user selects a campus zone or enters a custom search (e.g., 'nasi kulit unair', 'kopi giras nugas'), query Gemini 3.6 Flash / 3.8 Flash with system prompt:
"You are Senior Kampus Surabaya, a veteran student guide. Return realistic student warungs and late-night spots around Surabaya universities (ITS, UNAIR, UPN, Petra) matching the query. Include estimated price under Rp 25.000, distance, signature dish, and 1 short funny review in Surabaya casual slang (rek, mantep pol, nambah nasi)."
3. Cache Engine:
- Before firing an API call, check browser IndexedDB / LocalStorage under key 'anakkost_eats_cache'.
- If matching spots exist in cache, load immediately with zero API delay.
- If not cached, query Gemini with grounding, render the cards with an amber badge "Baru Ditemukan Senior (Live)", and upsert the new items into the local cache using 'name + campus' as key.
```

### 4.3 Verify in Live Preview
1. Click the interactive preview tab on the right side.
2. Select **"Keputih/Gebang ITS"** and tap **"Free Nasi & Es Teh"**.
3. Tap **"Pilihin Makan Dong Cak!"** to confirm the modal displays dynamic advice in authentic Surabaya student slang.

---

## 5. Step 4: Rapid Screenshot Debugging (55–65 min)

If a button does not respond or styling breaks, do not open Developer Tools or inspect code. Use the **Screenshot Debug Protocol**:

```
┌─────────────────────────────────┐
│ 1. Capture screen snippet of UI │
└────────────────┬────────────────┘
                 │
                 ▼
┌─────────────────────────────────┐
│ 2. Drag & Drop into AI Studio   │
└────────────────┬────────────────┘
                 │
                 ▼
┌─────────────────────────────────────────────────────────────┐
│ 3. Prompt:                                                  │
│ "The button highlighted here does not open the modal on     │
│ click. Verify the event listener and make sure the modal    │
│ pops up with the selected food card details."               │
└─────────────────────────────────────────────────────────────┘
```

#### Handy Fallback Debug Prompts:
* **Filter Doesn't Update:**
  ```text
  Clicking the filter chips does not update the card grid. Verify the active state tracking and ensure the card list re-renders based on the selected tag.
  ```
* **Modal Won't Close:**
  ```text
  The pop-up advice modal cannot be dismissed. Add an explicit close icon button ('✕') and allow clicking outside the backdrop to close it.
  ```

---

## 6. Step 5: Ship to Google Cloud Run (65–80 min)

1. In Google AI Studio, locate the top-right toolbar and click **Deploy**.
2. Select **Google Cloud Run**.
3. Name your application: `anakkost-eats`.
4. Click **Confirm & Deploy**.
5. Once deployment finishes (typically 60–90 seconds), copy your live production URL:
   ```text
   https://anakkost-eats-xxxxxxxxxx-as.a.run.app
   ```
6. Open the URL on your mobile phone to verify real device touch response and test the live AI flow.

---

## 7. Step 6: Demo Showdown (80–90 min)

Showcase your creation to the room:
* Generate a QR code for your live Cloud Run URL.
* Project your screen or let attendees scan and test your food generator.
* Vote on the most creative campus prompts, best use of Surabaya slang, and fastest deploy!