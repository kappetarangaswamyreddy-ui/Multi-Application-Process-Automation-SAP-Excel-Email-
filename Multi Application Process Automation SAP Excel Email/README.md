# 📌 Multi-Application Process Automation (SAP + Excel + Email)
### Developed by **Rangaswamyreddy Kapperta** | UiPath REFramework | Orchestrator Queues | End-to-End Automation

---

## 🚀 Project Summary (In My Own Words)

This project is an **end-to-end enterprise automation solution** that I personally built to strengthen my UiPath skills and demonstrate my real-world RPA experience.  
It integrates **multiple applications** in a single workflow:

- **SAP (Mock Posting)** – with Real SAP automation ready
- **Excel logging** – detailed transaction history
- **Email automation** – success notifications
- **Orchestrator Queues** – Dispatcher → Performer model
- **REFramework** – robust, scalable automation template

My goal was to create a fully functional automation that follows **industry standards**, uses **best practices**, and shows that I can build **enterprise-grade RPA bots** from scratch.

This project reflects my understanding of:
- REFramework  
- Queue-based automation  
- Multi-application workflows  
- Exception handling  
- Config-driven design  
- SAP RPA architecture  

---

## 🏗 Architecture (High-Level Flow)

             ┌───────────────────────────────┐
             │      Dispatcher Workflow       │
             │     SAP_QueueLoader.xaml       │
             └───────────────────▲────────────┘
                                 │
                         Adds Items to Queue
                                 │
                       Orchestrator Queue
                           SAP_Tasks
                                 │
                         Performer Bot
                     (Main.xaml - REFramework)
                                 │
            ┌────────────┬───────────────┬─────────────┐
            │            │               │             │
        SAP Mock     Excel Log       Email          Logging
            │            │               │             │

I used UiPath REFramework to ensure this bot is production-ready, scalable, and easy to maintain.

---

## ⭐ Main Features (What I Actually Built)

### ✔ **1. Dispatcher + Performer Architecture**
- Dispatcher loads structured data into the Orchestrator queue.
- Performer processes each transaction one by one using REFramework.

### ✔ **2. Config-Driven SAP Mock Posting**
I added a toggle inside **Config.xlsx**:

UseMockSAP = True
When enabled:
- Bot generates a fake SAP document number (`DOCxxxxxx`)
- This allows testing without real SAP access

When disabled:
- Bot will execute real SAP steps (future extension)

### ✔ **3. Excel Reporting**
Every successful transaction is logged into:

Output/RunLog.xlsx

It stores:
- Vendor ID  
- Company Code  
- Amount  
- Currency  
- Generated Document Number  
- Business Key  
- Status  
- Timestamp  

### ✔ **4. Email Notifications**
After each successful posting, the bot sends an email using Outlook Desktop Application with:

- Transaction details  
- Document number  
- Business key  
- Confirmation message  

### ✔ **5. Orchestrator Queue Automation**
Queue Name:SAP_Tasks

Each queue item contains these fields:

| Key | Description |
|------|------------|
| CompanyCode | SAP Company Code |
| VendorID | Vendor Number |
| DocDate | Posting Date |
| Amount | Invoice Amount |
| Currency | Currency Code |
| EmailTo | Recipient Email |
| Action | “PostInvoice” |

And a **Business Key** in this format:
CompanyCode|VendorID|DocDate

This prevents duplicates and keeps the bot idempotent (a real-world requirement).

### ✔ **6. Full REFramework Automation**
I implemented:

- Init state  
- Get Transaction Data  
- Process Transaction  
- Set Transaction Status  
- Retry mechanism  
- Logging  
- Exception classification  

### ✔ **7. Clean Exception Handling**
- **BusinessRuleException** – invalid data (no retry)
- **System Exception** – technical errors (retry allowed)
- **Success** – logged and emailed

---

This helps avoid duplicate processing and ensures clean tracking.

---

## 🧠 Exception Handling (My Approach)

### 🔴 BusinessRuleException  
Thrown when:

- Vendor is empty  
- Amount missing  
- Invalid currency  
- Wrong action  

Result:  
**Marked as Business Exception in Orchestrator**

### 🟡 System Exception  
Caused by:

- Excel issues  
- Outlook issues  
- Unexpected errors  

Result:  
**Marked as Application Exception (with retry)**

---

## 🔮 Future Improvements I Plan to Add

- PDF invoice extraction using OCR/Document Understanding  
- SAP real posting automation  
- API-based SAP posting  
- Power BI dashboard from RunLog.xlsx  
- Logging into a SQL Database  
- Email alerts for failures  

---

## 👨‍💻 About Me

Hi, I'm **Rangaswamyreddy Kappeta**, an RPA Developer passionate about building real-world automations.

This project helped me improve in:
- UiPath REFramework  
- SAP automation architecture  
- Multi-system integration  
- Queue-based design  
- Workflow optimization  
- Logging & exception handling  

This repository represents my hands-on learning and end-to-end RPA capability.

---

## 🏷 Tags  
`UiPath` `RPA` `SAP Automation` `REFramework`  
`Queue Processing` `Email Automation` `Excel Automation`  
`Dispatcher Performer` `Enterprise RPA` `Automation Anywhere`  
`Multi-System Automation` `Portfolio Project`

---



