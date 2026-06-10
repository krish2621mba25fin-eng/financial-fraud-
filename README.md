# Automated Fraud Monitoring & Alerting Workflow

An enterprise-grade, automated Intelligent Risk Assessment and Incident Response pipeline built on n8n. The system processes transaction data records dynamically, evaluates multiple conditional risk tiers, updates backend auditing logs, and dispatches real-time email notifications for flagged accounts.

---

## 📸 Workflow & Execution Architecture

The system uses a multi-conditional router to process customer transaction risk assessments across 4 distinct severity tiers.

### 1. Central n8n Automation Engine
The master workflow orchestration blueprint managing data reading, JavaScript formatting transformations, conditional routers (`If` engines), ledger updates, and messaging alerts.

<p align="center">
  <img src="Screenshot 2026-06-10 143308 - Copy.png" alt="n8n Master Workflow" width="100%">
</p>

### 2. Transaction Monitoring Ledger (Google Sheets Data Source)
The centralized customer database tracking metrics such as `Transaction_Amount`, `Location_Risk`, `Fraud_Label`, and automated risk scoring dimensions (`Amount_Status`, `Final_Risk`).

<p align="center">
  <img src="Screenshot 2026-06-10 143459.png" alt="Google Sheets Ledger Database" width="100%">
</p>

### 3. Real-Time Incident Response & Alerts (Gmail Engine)
When a customer profile hits a dangerous risk threshold, the automated notification node fires immediate high-priority investigation alerts to analysts.

<p align="center">
  <img src="Screenshot 2026-06-10 143551 - Copy.png" alt="Automated Risk Mitigation Email Notification" width="100%">
</p>

---

## ⚙️ Core Pipeline Mechanics

```mermaid
graph LR
    A[Execute Workflow] --> B[Get Rows from Sheet]
    B --> C[JavaScript Processing Engine]
    C --> D{Risk Router Tier 1-4}
    D -- Tier Match --> E[Update Specific Sheet Tab]
    E --> F[Dispatch Gmail Fraud Alert]
