# KYCR - Know Your Chex Report

> **Parse, visualize, and understand your ChexSystems report** – all locally in your browser.

KYCR is a privacy‑first, client‑side web application that lets you upload a ChexSystems consumer disclosure PDF, extract hard and soft inquiries, view your consumer profile, estimate a **ChexScore™**, simulate additional inquiries, and manage multiple report sessions – **without ever sending your data to a server**.

![MIT License](https://img.shields.io/badge/license-MIT-blue.svg)
![JavaScript](https://img.shields.io/badge/JS-ES6+-yellow)
![PDF.js](https://img.shields.io/badge/PDF.js-3.3.122-orange)

---

## ✨ Key Features

- 📄 **PDF Upload & Parsing** – Drag‑and‑drop or click to upload your ChexSystems report.  
  Extracts hard inquiries ("Viewed by Others") and soft inquiries ("Viewed Only by You").

- 👤 **Customer Profile** – Automatically pulls Consumer ID, name, associated names, addresses, phone, email, date of birth, and report date.

- 📊 **ChexScore™ Estimator**  
  - Calculates a proprietary risk score (100–899) based on recent inquiry volume, recency, and duplicates.  
  - Visual meter from Poor → Excellent.  
  - **Score Simulator** – add hypothetical inquiries to see the impact.  
  - **Calibration factor** – fine‑tune the algorithm (0.8–1.2).  
  - **Score History** – tracks your score over time (local storage).

- 🔍 **Inquiry Tables**  
  - Filter by bank name or date.  
  - Sort by name or date (ascending/descending).  
  - Duplicate detection & one‑click merge.

- 📈 **Charts & Stats**  
  - Bar chart showing inquiry counts per time window (1m, 2m, 3m, 6m, 12m, 24m).  
  - Cumulative stats summary.

- 💾 **Session Management**  
  - Save entire report (inquiries + profile + score history) to browser **localStorage**.  
  - Load, rename, or delete sessions.  
  - All data stays on your machine – no cloud upload.

- 📎 **Export to Excel** – Downloads hard and soft inquiries as separate sheets (`.xlsx`).

---

## 🧠 How It Works

1. **PDF Parsing** – Uses [PDF.js](https://mozilla.github.io/pdf.js/) to extract raw text.  
   Regular expressions locate the “Inquiries Viewed By Others” and “Inquiries Viewed Only By You” sections and parse each inquiry block (Inquirer, address, phone, date).

2. **ChexScore Calculation** – A proprietary model that considers:  
   - Number of unique hard inquiries in the last 6 & 12 months.  
   - Duplicate inquiries (same bank + phone) give a small bonus.  
   - Base deduction table derived from typical ChexSystems patterns.  
   - Final score clamped between 100 and 899.

3. **Local Storage** – All session data is saved using `localStorage`.  
   No external API calls, no tracking, no analytics.

---

## 🛠 Technologies Used

- **HTML5 / CSS3** – Responsive layout, Material Design 3 inspired components.
- **JavaScript (ES6+)** – Core logic, DOM manipulation, Chart.js integration.
- **[PDF.js](https://mozilla.github.io/pdf.js/)** – PDF text extraction (client‑side).
- **[Chart.js](https://www.chartjs.org/)** – Inquiry bar chart & score history line chart.
- **[SheetJS (XLSX)](https://sheetjs.com/)** – Export inquiries to Excel.
- **[Google Fonts & Material Symbols](https://fonts.google.com/icons)** – Icons and typography.

---

## 🚀 Getting Started

### Prerequisites
- Any modern web browser (Chrome, Firefox, Edge, Safari).
- No server, build step, or installation required.

### Run Locally
1. **Clone or download** this repository.
2. Open the `index.html` file in your browser (double‑click, or use a local web server like `npx serve .` if you prefer).
3. Start by dragging a ChexSystems PDF into the upload zone – **that’s it**.

> ⚠️ **Important:** Because the app uses `localStorage` for sessions, it works best when served over `http://` or `file://`. Some browsers may restrict `localStorage` for `file://` – if you encounter issues, use a simple local server.

---

## 📖 Usage Guide

### 1. Upload a ChexSystems Report
- Click the upload zone or drag & drop a PDF file.
- A progress bar shows parsing status.
- Once complete, the **Customer Profile** and **Inquiry tables** appear.

### 2. Explore Inquiries
- Switch between **Hard** and **Soft** tabs.
- Use the filter inputs to search by bank name or date (MM/DD/YYYY).
- Click **Merge Duplicates** to combine inquiries with identical bank name + phone number.
- Click on **Name** or **Date** column headers to sort.

### 3. Understand Your ChexScore
- The score is automatically calculated from your hard inquiries.
- Hover over the score meter to see the category.
- Use the **Score Simulator** sliders to add hypothetical inquiries for 1,2,3,6,12 months – the score updates in real time.
- Adjust the **Calibration factor** to tweak sensitivity.
- Score history is saved automatically (max 10 entries). Click **Clear History** to reset.

### 4. Save & Load Sessions
- Click **Manage Sessions** → **Save** to store the current report.
- Give the session a custom name (defaults to PDF name).
- Load any saved session from the list – all inquiries, profile, and score history are restored.

### 5. Export Data
- Click **Export Excel** to download an `.xlsx` file with two sheets: `Hard Inquiries` and `Soft Inquiries`.

---

## ⚠️ Disclaimer & Limitations

- **Not official** – KYCR is **not affiliated with ChexSystems, Inc.** The ChexScore shown is an **estimate** based on publicly observable patterns and may not reflect the actual score used by financial institutions.
- **Parsing accuracy** – The PDF extraction relies on specific ChexSystems report formatting. If your report uses a different layout, some inquiries may be missed. Improvements are welcome via pull requests.
- **No data leaves your device** – All processing happens in your browser. No uploads to any server.
- **For educational & personal use only** – Do not rely solely on this tool for financial decisions.

---

## 🤝 Contributing

Contributions, bug reports, and feature requests are welcome!  
Please open an issue or submit a pull request.

---

## 📄 License

[MIT](LICENSE) – free to use, modify, and distribute.

---

## 🙏 Acknowledgements

- [PDF.js](https://mozilla.github.io/pdf.js/) – Mozilla & contributors
- [SheetJS](https://sheetjs.com/) – SheetJS Community Edition
- [Chart.js](https://www.chartjs.org/)
- [Google Fonts & Material Symbols](https://fonts.google.com/icons)

---

**Made with ❤️ for financial literacy & data privacy.**
