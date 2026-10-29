# TrustFlow

> **Ask Better. Know Better. Trust Your Data.**  
> *ExaThon India 2026 — Track 04: The Work Behind the Work*

TrustFlow is a self-service business analytics and explainable data-trust platform designed to help employees obtain answers to routine business questions rapidly while providing mathematical proof of whether the underlying data is reliable.

---

## 🎯 Problems Addressed

TrustFlow tackles two core friction points from Track 04:

- **Problem B (Credibility Crisis):** Dashboards lose credibility when different reports show conflicting numbers or contain silent duplicate rows, missing attributes, or stale synchronization.
- **Problem C (Turnaround Bottleneck):** Business teams wait 2–3 business days for data analysts to answer routine queries that could be handled instantly via self-service analytics.

Instead of displaying numbers in a black box, TrustFlow evaluates explicit, explainable data-quality assertions in parallel with every query and presents the result alongside trust ratings, supporting evidence, and actionable remediation guidance.

---

## 🏛️ Project Structure

```
online hackthon/
├── pom.xml                               # Maven project configuration (Jakarta Servlet 6.0, Exasol JDBC)
├── README.md                             # Comprehensive project documentation
├── LICENSE                               # MIT Open Source License
├── .gitignore                            # Standard Git ignore rules
│
├── src/
│   └── main/
│       ├── java/com/trustflow/           # Java backend (servlets, services, DAOs)
│       └── webapp/                       # Web application frontend
│           ├── index.html                # Public Landing Page (Modern Glassmorphism Pattern)
│           ├── dashboard.html            # Main Operational Analytics & Trust Dashboard
│           ├── questions.html            # Self-Service Business Analytics Explorer
│           ├── trust-checks.html         # Data Trust Checks Catalog (18 Rules)
│           ├── issue-details.html        # Discrepancy Evidence & Remediation Drilldown
│           └── assets/
│               ├── css/
│               │   ├── design-system.css # Shared design tokens, buttons, tables, badges
│               │   ├── glassmorphism.css # Frosted glass, backdrop-blur, glowing radial orbs
│               │   └── dashboard.css     # Sidebar, topbar, grid layout, KPI widgets, SVG charts
│               └── js/
│                   ├── mock-data.js      # Single source of truth (Apex Retail Global dataset)
│                   ├── trust-engine.js   # Scoring engine, status pills, number formatting
│                   ├── landing.js        # Interactive live sandbox toggling on landing page
│                   ├── dashboard.js      # Dashboard KPI cards, SVG trend charts, audit simulation
│                   ├── questions.js      # Self-service inquiry processor and breakdown tables
│                   ├── trust-checks.js   # Filtering, search, and catalog management
│                   └── issue-details.js  # Evidence table, confirmed findings vs hypotheses
│
└── database/                             # Exasol SQL Schemas & Test Data (Phase 2)
    ├── 01_create_schema.sql
    ├── 02_create_tables.sql
    ├── 03_insert_sample_data.sql
    ├── 04_quality_test_data.sql
    └── 05_analytics_queries.sql
```

---

## 🚀 How to Run the Frontend (Phase 1)

The frontend is built with modern standard **HTML5, CSS3, and ES6 JavaScript** without heavy build tools or npm dependencies, allowing immediate preview in any modern browser:

### Option 1: Direct File Opening
- Navigate to `src/main/webapp/` and double-click `index.html` to open it in Chrome, Edge, Firefox, or Safari.
- Or open the root `index.html` which immediately forwards to `src/main/webapp/index.html`.

### Option 2: VS Code Live Server
1. In Visual Studio Code, right-click `src/main/webapp/index.html` (or root `index.html`).
2. Select **"Open with Live Server"**.
3. View the application at `http://localhost:5500/`.

The Maven backend targets **Java 25 LTS**. Use a Java 25 JDK to build it with `mvn clean package`.

---

## 💎 Design Highlights (Glassmorphism Pattern)

- **Dark Navy/Charcoal Palette:** Enterprise-grade background (`#080c14`, `#0c1220`, `#111a2e`).
- **Frosted Glass Cards:** `backdrop-filter: blur(18px)`, translucent background fills (`rgba(255, 255, 255, 0.035)`), and delicate light reflections (`border: 1px solid rgba(255, 255, 255, 0.09)`).
- **Ambient Glowing Radial Orbs:** Subtle coral (`#f43f5e`), electric cyan (`#06b6d4`), and indigo (`#6366f1`) mesh highlights creating visual depth.
- **Explainable Indicators:** Distinct color tokens for **Passed** (Emerald), **Warning** (Amber), and **Failed** (Coral Red).

---

## 📊 Fictional Dataset: Apex Retail Global

All frontend pages share a unified mock dataset (`assets/js/mock-data.js`) to ensure figures never contradict each other:

- **Total Sales (MTD):** \$1,428,950.00 across 12,480 completed transactions.
- **Payment Gateway Settlements:** \$1,424,750.00 settled across 12,478 matched transactions.
- **Reconciliation Delta (RC-104):** **-$4,200.00** discrepancy isolated to 2 transactions (`TX-9021` for \$2,400.00 and `TX-9044` for \$1,800.00) pending settlement capture.
- **Active Monitored Quality Rules:** 18 rules (14 Passed, 3 Warnings, 1 Failed).
- **Composite Trust Score:** **83.3%** (*Conditional Trust / Action Required*).

---

## ⚖️ Next Steps (Phases 2–4)

1. **Phase 2 (Database):** Provision Exasol schema and populate SQL tables (`sales_transactions`, `orders_fact`, `customer_master`, `payment_gateway_settlements`).
2. **Phase 3 (Java Backend):** Compile Jakarta Servlets with Maven (`mvn clean package`) and connect to Exasol via JDBC.
3. **Phase 4 (Integration):** Switch frontend `fetch()` calls from `mock-data.js` to live servlet REST endpoints.
