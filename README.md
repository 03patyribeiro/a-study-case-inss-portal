# 🧪 QA Case Study: Irish Immigration Portal (INIS)
## Real-World Analysis of Cross-Platform Data Inconsistency

![Project Status](https://img.shields.io/badge/Status-Completed-success)
![Focus](https://img.shields.io/badge/Focus-Cross--Platform%20%7C%20Data%20Sync-blue)

---

### 📌 1. Introduction
This project presents a real-world QA analysis of the **INIS (Irish Naturalisation and Immigration Service)** portal. During a live visa renewal process, I identified a critical synchronization bug between the Desktop and Mobile platforms. This discrepancy directly affects how application statuses are displayed to the user, creating significant uncertainty in a high-stakes administrative process.

---

### 🎯 2. Objectives
- **Validate** system consistency across different operating systems and browsers.
- **Document** technical vulnerabilities using industry-standard reporting (Severity/Priority).
- **Analyze** the psychological and functional impact on User Experience (UX).
- **Propose** technical solutions to bridge the gap between frontend display and backend data.

---

### 🐞 3. Bug Report: BUG-001 (The "Zero" Badge Logic Failure)
**Title:** Critical mismatch in "Submitted Forms" status between Desktop and Mobile environments.

| Field | Detail |
| :--- | :--- |
| **Environment** | Chrome (Windows 11) vs. Chrome (Android 13) |
| **Severity** | **High** (Critical information mismatch) |
| **Priority** | **High** (Urgent fix required to prevent user distress) |

#### 🔁 Steps to Reproduce:
1. Log in to the INIS portal on a **Desktop** browser.
2. Navigate to the **"My Forms"** dashboard.
3. Observe that the "Submitted" badge displays **(0)** and no cards are visible.
4. Log in to the same account on a **Mobile** browser.
5. Navigate to **"My Forms"** and observe the "Submitted" badge correctly displays **(1)** with the form card visible.

#### ❌ Actual Result:
The Desktop UI fails to retrieve or render the submitted application record, indicating an empty status, whereas the Mobile UI correctly displays the database record.

---

### 📸 4. Evidence (Comparative Analysis)

#### 💻 Desktop Environment (Bugged View)
![Desktop View](https://github.com/03patyribeiro/a-study-case-inss-portal/blob/main/Texto%20Analyze%20the%20Ireland%20immigration%20website%20using%20a%20computer.Ado%20seu%20par%C3%A1grafo.png?raw=true)
*Figure 1: Desktop interface showing an empty dashboard and a "0" counter for submitted forms.*

#### 📱 Mobile Environment (Correct View)
![Mobile View](https://github.com/03patyribeiro/a-study-case-inss-portal/blob/main/Platforms%20This%20mobile%20phone%20capture.png?raw=true)
*Figure 2: Mobile interface correctly synchronizing with the backend to show the active application.*

---

### 🧠 5. Technical Root Cause Analysis
The discrepancy suggests a failure in **Frontend State Management** or **Conditional Rendering logic** specific to Desktop User Agents. While the backend database is clearly updated (as evidenced by the mobile view), the Desktop build may be:
* **API Versioning:** Calling an outdated API endpoint that doesn't track "Old Registration" types.
* **Cache Persistence:** Failing to clear or revalidate the local cache upon login.
* **Filter Logic:** Improperly filtering data on the client-side based on screen resolution or device type.

---

### 💡 6. Professional Recommendations & Improvements
To resolve this and improve the overall Quality Assurance of the portal, I suggest the following:

* **Endpoint Uniformity:** Audit API calls to ensure both Mobile and Desktop builds consume the same v-latest endpoints for the "My Forms" counter.
* **State Revalidation:** Implement a "SWR" (Stale-While-Revalidate) or a manual **"Sync Data"** button on the dashboard to allow users to force a refresh of their status directly from the server.
* **User Feedback Loops:** Introduce a "Status Confirmed" banner or an automated **Success Email** triggered immediately upon database entry. This provides a secondary source of truth for the user outside of the UI.
* **Cross-Browser Automated Testing:** Implement automated regression tests using tools like **Cypress** or **Playwright** specifically targeting cross-platform synchronization to catch these discrepancies before deployment.

---

### 🚀 7. Conclusion
This study case demonstrates my proactive **"QA Mindset"**—the ability to turn a personal user challenge into a structured technical investigation. It highlights my skills in **Cross-Platform Testing**, **Bug Documentation**, and **Impact Analysis**, all of which are essential for ensuring software reliability in critical public services.

---
**Author:** Patrícia de Cássia Ribeiro dos Santos
*Software Engineering Student & QA Analyst in Training*
