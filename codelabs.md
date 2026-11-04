# Codelab: Build & Ship "AnakKost Eats" with Stitch + AI Studio

Learn how to design, wire, and deploy a full-stack student food finder app to Google Cloud Run in 90 minutes.

---

## 1. Architecture Overview

We separate the application into two clear roles:

* **Front of House (Google Stitch):** Visual layout, typography, responsive card containers, buttons, and color schemes.
* **The Kitchen Engine (Google AI Studio):** State management, API bindings to Gemini 3.6 Flash / 3.8 Flash with live Google Search & Maps grounding, local caching, and cloud deployment.

```text
+-----------------------+      Direct Export      +------------------------+      1-Click Deploy      +-----------------------+
|     Google Stitch     | ----------------------> |    Google AI Studio    | -----------------------> |   Google Cloud Run    |
| (UI / Visual Canvas)  |   "Build with AI"       | (Gemini 3.6/3.8 Flash) |       "Deploy App"       |   (Live Public URL)   |
+-----------------------+                         +------------------------+                          +-----------------------+
                                                              |
                                                    +---------+---------+
                                                    | Grounding + Cache |
                                                    | - Google Maps/Web |
                                                    | - IndexedDB Cache |
                                                    +-------------------+
```

---

## 2. Step 1: Design the UI in Google Stitch (00–20 min)

### 2.1 Prompt the UI Layout
1. Open [Google Stitch](https://stitch.withgoogle.com/) and click **New Project**.
2. In the bottom prompt console, paste the master UI prompt and press **Enter**:

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

### 2.2 Refine
Select any element directly on the Stitch canvas to refine it:
```text
Make the quick action button 'Pilihin Makan Dong Cak!' glowing amber with rounded-full pill corners.
```
> **Tip:** Keep your design strictly to 2 screens to ensure fast export and clean generation.

---

## 3. Step 2: Bridge Stitch to Google AI Studio (20–25 min)

1. In the upper-right toolbar of Google Stitch, click **Export**.
2. In the modal, choose **AI Studio**.
3. In the **Description** field (where it says *"Make this real"*), replace the text with:

```text
Keep the visual Tailwind UI and campus styling intact. Connect the campus dropdown and filter chips to filter the food cards list. Connect the 'Pilihin Makan Dong Cak!' button to randomly select a campus warung and trigger a pop-up modal with humorous advice from 'Senior Kampus' speaking authentic Surabaya slang (rek, cak, wareg pol, kantong aman). Prepare the app to load live grounded data via Gemini Flash.
```

4. Click **Build with AI Studio**. A new tab will open with your UI code loaded into AI Studio Build mode.

---

## 4. Step 3: Implement Gemini Logic & Smart Cache (25–55 min)

### 4.1 Seed Initial Default Data
In the AI Studio Build chat prompt box at the bottom, send:

```text
Populate the app with these iconic Surabaya student food spots as initial default state:
1. Warung Tombo Luwe (Keputih ITS) - Porsi barbar, masakan rumahan prasmanan, Rp 12.000, 4.8 bintang.
2. Bebek Bagong (Keputih Utara ITS) - Bebek gurih bumbu hitam + protolan, Rp 18.000, 4.7 bintang.
3. Soto Ayam Barokah (Keputih Tegal) - Soto kuah koya gurih melimpah, Rp 15.000, 4.8 bintang.
4. Tahu Telur Pak Jayen (Dharmahusada UNAIR B) - Tahu telur bumbu petis jumbo, Rp 20.000, 4.9 bintang.
5. Ayam Geprek Joder (Gebang ITS) - Pedas nampol level bebas, free refill nasi, Rp 14.000, 4.8 bintang.

Ensure clicking campus selector or filter chips immediately filters these cards.
```

### 4.2 Add Grounded Discovery & Local Storage Cache
Next, instruct AI Studio to connect dynamic live data and client caching:

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

### 4.3 Test Interactivity
* In the live preview pane, test the campus dropdown and category filters.
* Click **"Pilihin Makan Dong Cak!"** to verify the modal triggers with advice in Surabaya student slang.

---

## 5. Step 4: Rapid Screenshot Debugging (55–65 min)

If something doesn't work or an element looks misaligned, do not open Developer Tools or inspect code. Use the **Screenshot Debug Protocol**:

1. **Capture:** Take a screenshot snippet of the broken element or layout.
2. **Attach:** Paste or drag the image directly into the AI Studio prompt console.
3. **Prompt:** Describe what didn't happen:
   ```text
   The button highlighted in this screenshot does not open the modal on click. Inspect the event handlers and ensure clicking it opens the modal with the chosen warung details.
   ```

### Common Quick Fixes

* **Filter Doesn't Update:**
  ```text
  Clicking the filter chips does not update the card grid. Verify the active state tracking and ensure the card list re-renders based on the selected tag.
  ```
* **Modal Cannot Be Closed:**
  ```text
  The modal cannot be dismissed. Add an explicit close icon button ('✕') and allow clicking the backdrop to close it.
  ```

---

## 6. Step 5: Ship to Google Cloud Run (65–80 min)

1. In Google AI Studio, locate the top-right toolbar and click **Deploy**.
2. Select **Google Cloud Run**.
3. Name your application: `anakkost-eats`.
4. Click **Confirm & Deploy**.
5. Once deployment completes (typically 60–90 seconds), copy your live production URL:
   ```text
   https://anakkost-eats-xxxxxxxxxx-as.a.run.app
   ```
6. Open the URL on your mobile phone to verify responsive layout and test live AI queries.

---

## 7. Step 6: Demo Showdown (80–90 min)

1. Turn your live URL into a QR code (using any browser extension or QR generator).
2. Have attendees and mentors scan and test your food app.
3. Vote for:
   * **Most Authentic Persona:** Funniest and most accurate Surabaya slang.
   * **Best Interaction:** Fastest filter response and seamless caching.
   * **Speed to Ship:** First apps successfully running live on Cloud Run!
