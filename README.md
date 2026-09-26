# Nexus - Personal Finance Management App

A comprehensive Flutter-based personal finance management app with automated transaction detection, intelligent insights, vehicle management, and Firebase cloud synchronization.

## Overview

Nexus helps you take total control of your financial life—from daily automated transaction parsing to investment tracking, vehicle maintenance, family expense sharing, and savings goals. Built with Material Design 3 and an expressive dark glassmorphic theme.

---

## What's New & Key Highlights

* **Over-The-Air (OTA) Updates:** In-app GitHub release checker with interactive consent dialog, progress tracking, release notes, and automated package installer.
* **N-Box Automated Transaction Inbox:** Real-time SMS & Gmail parsing for bank transaction alerts with AI-assisted merchant categorization learning.
* **Android Home Screen Widgets:** Interactive widgets for quick balance checks, instant transaction entry, and logging fuel entries.
* **Android Auto Integration:** Vehicle garage overview, service tracking, and quick fuel logging on car infotainment displays.
* **Bank Statement Import (PDF):** Parse and reconcile PDF bank statements (SBI, IDFC, Slice, etc.) with password support.
* **Live Mutual Fund NAVs & Fuel Prices:** Real-time NAV updates via MFAPI and state-wise live petrol/diesel price tracking.

---

## Core Features

### 1. N-Box Automated Transaction Inbox
* **SMS Parsing:** Real-time background and foreground SMS listener (`another_telephony`) for bank debits, credits, and balance alerts.
* **Gmail Sync:** Secure Google Sign-In & Gmail API integration to scan bank e-statements and transaction alert emails.
* **Merchant Knowledge Base:** Self-learning system (`MerchantKnowledge`) that remembers merchant-to-category mappings and account links.
* **Bank Statement Parser:** Import PDF bank statements (SBI, IDFC, Slice, etc.), auto-extract transactions, and reconcile missing entries.
* **Inbox Review:** Single-tap approval, categorization, or dismissal of detected transactions.

### 2. Over-The-Air (OTA) Updates
* **GitHub Releases Integration:** Fetches release metadata directly from `Nadhiii/Nexus-APK`.
* **In-App Consent Dialog:** Prompts user with "What's New" release notes, file size badge, pre-release/beta tag, and current vs. new version comparison.
* **Live Download Progress:** In-app progress bar with percentage, background notification progress, and cancel option.
* **Automated Installation:** Prompts native Android package installer upon download completion.
* **Background Checks:** Workmanager periodic task (every 6 hours) and startup check notifying when new updates are available.
* **Channel Toggle:** Switch between Stable and Beta release channels.

### 3. Android Widgets & Android Auto
* **Home Screen Widgets:**
  * **Balance Widget:** Displays total balance across accounts with quick dashboard access.
  * **Quick Transaction Widget:** One-tap buttons for logging income/expenses or viewing transaction history.
  * **Garage Widget:** Quick fuel logging, vehicle overview, and mileage check directly from the home screen.
* **Android Auto Support:**
  * Native Automotive OS interface (`NexusCarAppService`) showing vehicle details, fuel logs, and service reminders on car infotainment screens.

### 4. Finance Management
* **Accounts:** Create and manage multiple account types (Savings, Salary, Credit Card, Investment, Cash, Wallet). Track real-time net worth, store bank details (with encrypted CVV storage), and view activity history.
* **Transactions:** Track Income, Expense, and Transfers. Attach notes, tags, and category metadata. Includes multi-select batch operations, advanced filtering, and smart duplicate detection.
* **Budgets:** Category-based budget limits with custom intervals. Features a real-time progress bar, 80% threshold warnings, overspend detection, and daily safe-to-spend calculations.
* **Categories:** System defaults and custom user categories with emoji icons, custom colors, and reordering.

### 5. Investment Tracking
* **Supported Types:** Mutual Funds (live NAV via MFAPI), Stocks, Cryptocurrencies, Gold & Precious Metals, Real Estate, and Fixed Deposits.
* **Features:** Real-time profit/loss calculations, portfolio growth charts, SIP linking to savings goals, and Folio/ISIN tracking.

### 6. Debt & Loan Management
* **Loan Types:** Personal, Home, Car, Education, Business, Gold, Two-Wheeler Loans, and Credit Cards.
* **Features:** EMI calculator (Principal vs. Interest breakdown), payment schedules, payoff date calculation, and overdue detection.
* **Family Debts (IOUs):** Track money lent/borrowed with net balance calculations and settlement history.

### 7. Vehicle & Garage Management
* **Garage Hub:** Manage multiple vehicles. Store Make, model, year, registration number, and RTO info.
* **Fuel & Mileage:** Log fuel entries (odometer, quantity, price) for automatic fuel efficiency calculation (km/L). Track cost-per-kilometer and view live state/city petrol and diesel prices.
* **Documents & Challans:** Store RC, Insurance, and PUC expiry dates with alerts. Log traffic challans with payment status and receipts.

### 8. Subscriptions & Savings Goals
* **Subscriptions:** Recurring billing tracking with automatic due date calculation, overdue warnings, and monthly cost analysis.
* **Savings Goals:** Target amount/date tracking, visual progress bars, and direct linking to accounts or SIP investments.

### 9. Payday Checklist & Analytics
* **Payday Checklist:** Auto-generated priority checklist upon receiving income (EMI payments, IOUs, subscriptions, budget allocations).
* **Financial Health Score:** 0–100 rating based on savings rate, debt-to-income ratio, budget adherence, and emergency fund size.
* **Reports:** Export to PDF/CSV. View Income vs. Expense charts, category breakdowns, and spending forecasts.

### 10. Family & Shared Expenses
* Shared expense splitting (Equal, Custom Amount, Percentage-based).
* Participant balance summaries ("Who owes whom") and settlement tracking.

### 11. Security & Backup
* **Security:** Biometric Fingerprint & Face Unlock (`local_auth`). Encrypted local storage for sensitive card data (`flutter_secure_storage`).
* **Backup:** Automatic and manual Firebase Cloud Firestore backup/restore.
* **Stability:** Integrated Firebase Crashlytics.

---

## Technical Architecture

* **Framework:** Flutter (Dart 3.x)
* **State Management:** Provider (`ChangeNotifier`, `ProxyProvider`)
* **Theme:** Expressive dark theme with frosted glass navigation blur (`ui.ImageFilter.blur`).
* **Backend & Storage:**
  * Firebase Cloud Firestore & Authentication
  * Firebase Crashlytics
  * `shared_preferences` & `flutter_secure_storage`
* **Networking & API:**
  * `dio` & `http` (GitHub API, MFAPI, Fuel Price API)
  * Google APIs (`googleapis`, `google_sign_in`)
* **Native Android Integrations:**
  * `flutter_local_notifications` & `workmanager` (Background OTA polling)
  * `another_telephony` (SMS Broadcast Receiver)
  * `open_file` (Package installer launcher)
  * Android Home Screen Widgets (`AppWidgetProvider`)
  * Android Auto (`CarAppService`)

---

## Key Screens & Navigation

The bottom navigation bar features 6 core tabs:

1. **Home:** Dashboard overview, total balance, recent transactions, financial health score, payday checklist, and quick action buttons.
2. **Wallet:** Accounts list, card details, transaction history, filtering, and add transaction screen.
3. **Wealth:** Investments, portfolio performance, mutual fund NAVs, and savings goals.
4. **Garage:** Vehicle details, fuel log, mileage stats, document expiry alerts, and challan tracking.
5. **N-Box:** Automated SMS & Gmail transaction inbox for approval and category learning.
6. **More:** Reports & PDF export, category manager, family splitter, backup settings, OTA updates, and notification preferences.
