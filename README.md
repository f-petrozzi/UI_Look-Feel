# EduInsight — Static Website Prototype

A static prototype for an academic analytics web app used in ISM 6225. EduInsight summarizes enrollment and performance metrics, visualizes trends with Chart.js, simulates CRUD navigation, and integrates a Botpress chatbot for dataset Q&A.

> Live (MyWeb): `https://myweb.usf.edu/~<your-netid>/index.html`  
> Bot page: `https://myweb.usf.edu/~<your-netid>/mybot.html`  
> Repository: https://github.com/f-petrozzi/UI_Look-Feel/

---

## ✨ Overview
EduInsight helps academic stakeholders quickly understand student enrollment and GPA performance. The prototype is built with HTML, CSS, and vanilla JavaScript and is intentionally static to match course requirements while laying the groundwork for the final MVC project.

### Key Goals
- Present a clear **Home** dashboard with core metrics.
- Provide **Data Visualization** using **Chart.js** (3+ charts with meaningful dummy data).
- Simulate **CRUD** user flows via navigation buttons (Create/Read/Update/Delete).
- Show the **logical data model (ERD)** with at least two **1→many** relationships.
- Embed a **Botpress** chatbot that answers questions from a structured dataset.
- Ensure **responsive** layout and consistent look & feel across pages.

---

## 🧭 Pages
- `index.html` — Home page with project intro, purpose, key features, and KPI cards.
- `data.html` — Interactive charts (Chart.js) using dummy CSV data.
- `about.html` — Team roles & contributions, ERD image, GitHub link, and navigation.
- `mybot.html` — Published Botpress chatbot embedded for on-page Q&A.
- Optional CRUD navigation pages:
  - `create.html` — Explain “Create” flow.
  - `read.html` — Simulate a read-only list/table of dummy data.
  - `update.html` — Explain “Update” flow and sample form.
  - `delete.html` — Explain “Delete” flow and confirmation pattern.

---

## 🧰 Tech Stack
- **HTML5**, **CSS3**, **JavaScript (ES6+)**
- **Chart.js v4** (+ `chartjs-plugin-datalabels`)
- **Botpress** (hosted; embedded via script)
- CSV for dummy data (`data/enrollments.csv`)

CDNs used in pages:
```html
<script src="https://cdn.jsdelivr.net/npm/chart.js@4"></script>
<script src="https://cdn.jsdelivr.net/npm/chartjs-plugin-datalabels@2"></script>
```

---

## 📁 Project Structure
```
.
├── index.html
├── data.html
├── about.html
├── mybot.html
├── create.html
├── read.html
├── update.html
├── delete.html
├── style.css               # Site styles (class names referenced by all pages)
├── main.css                # Additional/legacy styles (if used)
├── assets/
│   ├── erd.svg            # Logical data model (Student→Enrollment, Program→Enrollment)
│   └── screenshots/       # (optional) home.png, data.png, about.png, bot.png
└── data/
    └── enrollments.csv    # Dummy CSV used for metrics & charts
```

---

## 🚀 Run Locally
You can open `index.html` directly, but some browsers block `fetch()` for local files. If you see errors loading the CSV, start a tiny local server:

**Python 3**
```bash
python -m http.server 8000
```
Now open: http://localhost:8000

---

## 📊 Data & Charts
- **CSV**: `data/enrollments.csv` is read via `fetch()` and parsed in the page script(s).
- **Metrics (Home)**: total students, average GPA, programs count, and most-active term.
- **Charts (Data page)**: at least three charts (e.g., bar, line, pie) using Chart.js with meaningful dummy data.

Example parsing (from `index.html`):
```js
const r = await fetch('data/enrollments.csv');
const t = await r.text();
const rows = t.trim().split('\n').slice(1).map(line => {
  const [id,name,program,term,gpa,date] = line.split(',');
  return { id, name, program, term, gpa: parseFloat(gpa), date };
});
```

---

## 🤖 Botpress Integration
1. Create a Botpress account and complete **Botpress 101**.
2. Build a **Table** (≥10 rows) aligned with this project’s domain.
3. Create a **Knowledge Base** from the table.
4. Wire the **Start Node → Autonomous Node** with clear instructions and “Search Knowledge.”
5. **Publish** the bot and copy the embed script.
6. Paste the embed script into `mybot.html` (just before `</body>`).

`mybot.html` includes:
- A bot title/description.
- The Botpress embed code.
- Verification instructions for testing two+ queries.

---

## 🧩 ERD (Logical Data Model)
- File: `assets/erd.svg`
- Relationships displayed (minimum):
  - **Student → Enrollment** (1→many)
  - **Program → Enrollment** (1→many)
- Primary/foreign keys are labeled in the diagram.

---

## ✅ Assignment Alignment (Checklist)
**Home Page**
- [x] Introduces project idea, purpose, and key features
- [x] Includes navigation links to other pages

**Data Visualization Page**
- [x] ≥ 3 interactive charts using Chart.js with meaningful dummy data
- [x] Navigation to other pages

**About Us Page**
- [x] Team member details (name, role, contributions)
- [x] ERD image with ≥ two 1→many relationships
- [x] Link to GitHub repository
- [x] Navigation links to other pages

**Botpress**
- [x] Table (≥10 rows) + Knowledge Base
- [x] Start → Autonomous node with instructions + search knowledge
- [x] Published & embedded in `mybot.html`
- [x] Tested with ≥2 queries

**Responsiveness & Consistency**
- [x] Consistent header/nav/buttons/typography
- [x] Mobile/tablet/desktop layout considerations

**Submission Bundle**
- [x] MyWeb URLs for `index.html` and `mybot.html`
- [x] Screenshots (Home, Data, About, Bot)
- [x] ERD image
- [x] Git log output
- [x] Self-reflection(s)

---

## 👥 Team
- **Fabrizio Petrozzi** — Data Visualization & Styling  
  Built `data.html` and the data table (CSV), finalized website styling, authored `main.css`, and edited the final report.
- **Andrey Martynenko** — Front-End & Documentation  
  Created `index.html` (Home) and the About Us page; wrote the final report.
- **Bryan Reeder** — Data Model & CRUD Engineering  
  Designed the ERD and implemented CRUD code (Read, Write, Update, Delete).
- **Hammaz Buksh** — Product & Chatbot  
  Led idea generation and project outline; built the chatbot.

---

## 📸 Screenshots (placeholders)
Add these for the submission document:
- `assets/screenshots/home.png`
- `assets/screenshots/data.png`
- `assets/screenshots/about.png`
- `assets/screenshots/bot.png`

---

## 📦 Deployment (USF MyWeb via Cyberduck)
1. Connect to your MyWeb space with your USF credentials.
2. Upload the entire project folder (HTML/CSS/JS, `assets/`, `data/`).
3. Verify:
   - `https://myweb.usf.edu/~<your-netid>/index.html`
   - `https://myweb.usf.edu/~<your-netid>/mybot.html`

---

## 📄 License
Educational use for ISM 6225 coursework. If you want an open-source license, consider MIT.

---

## 🙏 Acknowledgments
- USF ISM 6225 assignment specs
- Chart.js & chartjs-plugin-datalabels
- Botpress
