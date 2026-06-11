# Automated Credit Risk Assessment & Application Workflow

An end-to-end automated pipeline built with **n8n** and **Orange Data Mining** that trains a predictive risk model, ingests financial application data from **Google Sheets**, evaluates applicants through multi-tiered conditional logic, and sends automated decision notifications via **Gmail**. It features a frontend conversational assistant interface via **Kommunicate**.

---

## 🚀 System Architecture & Workflow

The entire automation engine is driven by an asynchronous node-based workflow in n8n. It processes batch applications sequentially, passing them through structured evaluation matrices (`IF` filters) to arrive at three primary states: **Auto-Approve**, **Manual Review**, or **Auto-Reject**.

### Workflow Visual Map
<img src="./workflow.jpeg" alt="n8n Automated Decisioning Workflow" width="100%"/>

### Workflow Breakdown
1. **Trigger**: Manually executed or webhook-driven initiation (`When clicking 'Execute workflow'`).
2. **Data Ingestion**: Pulls raw applicant profiles from a secure Google Sheet ledger.
3. **Conditional Logic Filters (`If`, `If1`, `If2`, `If3`)**: 
   * Segregates applications based on risk factors such as credit health, baseline income tiering, and debt leverage ratios.
   * Out of 40 baseline items initialized, applications are successfully bucketed into specific validation branches.
4. **Data Synchronization & Notification**: Writes final pipeline updates back to the respective sheets while triggering personalized transactional emails.

---

## 🧠 Predictive Modeling Pipeline (Orange)

Before applications enter the live automation routing, risk evaluation thresholds are validated using a predictive machine learning pipeline designed in **Orange Data Mining**. This layer tests classification stability to ensure decision logic boundaries are mathematically sound.

### Data Science Canvas
<img src="./WhatsApp Image 2026-06-11 at 13.56.30.jpeg" alt="Orange Data Mining Predictive Workflow" width="100%"/>

### Model Components
* **File Node**: Ingests historical credit application training profiles.
* **Select Columns**: Sets the target classification variable (e.g., `System_Initial_Decision`) and isolates key predictive features like credit score and DTI ratios.
* **Logistic Regression**: Trains a generalized linear classification model to calculate risk probabilities.
* **Test and Score**: Evaluates model accuracy, AUC-ROC statistics, and confusion matrices prior to production logic deployment.

---

## 💬 Conversational Interface (FinAssist Bot)

Applicants and clients interact directly with the front-facing AI layer via a customized web widget deployed through **Kommunicate**. 

### Live Chat Interface Demo
<img src="./WhatsApp Image 2026-06-11 at 14.11.55.jpeg" alt="Kommunicate Chatbot Interface Demo" width="100%"/>

### Key Capabilities Deployed:
* **Financial Ratio Assistance**: Real-time evaluation explanations for client queries.
* **Investment Planning**: Conversational pre-screening before formal database ingestion.
* **Loan Guidance**: Guided onboarding explaining specific credit requirement criteria dynamically.

---

## 📊 Dataset Structure (Google Sheets)

The underlying decision logic evaluates financial metrics across multiple columns to flag anomalies, compliance warnings, or immediate rejections.

### Input Data Profile
<img src="./Screenshot (19).png" alt="Google Sheets Application Database" width="100%"/>

| Column Name | Description | Key Target Thresholds Evaluated |
| :--- | :--- | :--- |
| `Annual_Income` | Total gross yearly earnings | Evaluated for low-income tier audits |
|
