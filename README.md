# 🎯 Audit Workflow Application (AWA)

![ASP.NET MVC](https://img.shields.io/badge/ASP.NET%20MVC-5.0-blue)
![Entity Framework](https://img.shields.io/badge/Entity%20Framework-6.0-green)
![License](https://img.shields.io/badge/License-All%20Rights%20Reserved-red)
![Platform](https://img.shields.io/badge/Platform-Windows-lightgrey)

---

## 🧾 Project Overview

The **Audit Workflow Application (AWA)** is a **role-based system** for managing and tracking internal quality audits (like ISO audits) end-to-end.

It is built using **ASP.NET MVC 5** and **Entity Framework (Code First)**, enforcing a structured workflow among:

* **Auditors**
* **Auditees**
* **Sectional Heads (SH)**
* **Management Representatives (MR)**

The application focuses on handling **Non-Conformities (NCs)** and **Opportunities for Improvement (OFIs)**, with automated **PDF report generation** once approvals are complete.

---

## ✨ Key Features

* 🔐 **Role-Based Authentication**
  Secure dashboards for each role. *(See `User.cs`, `AccController.cs`)*

* 🧾 **Structured Audits**
  Comprehensive forms to record NCs and OFIs.

* ✅ **Multi-Stage Approvals**
  Independent approval pipeline for SH and MR. *(See `AuditReviewers.cs`)*

* 🕓 **Audit Logging**
  Complete log of approvals, reverts, and remarks. *(See `AuditApproval.cs`)*

* 🧩 **NC/OFI Management**
  Track root causes, corrective actions, and closure timelines.

* 📄 **PDF Report Generation**
  Generate high-quality reports via **Rotativa**. *(See `AuditController.cs`)*

* 📊 **Dashboards**
  Role-specific dashboards for pending and completed audits.

---

## 🛠️ Technology Stack

| Layer              | Technology                                       |
| ------------------ | ------------------------------------------------ |
| **Frontend**       | HTML5, CSS3, JavaScript, jQuery, Razor (.cshtml) |
| **Backend**        | C#, ASP.NET MVC 5                                |
| **ORM**            | Entity Framework 6 (Code First)                  |
| **PDF Generation** | Rotativa                                         |
| **UI/UX**          | Bootstrap, SweetAlert2                           |

---

## 📁 Project Structure (Key Files)

| File / Folder            | Purpose                                  |
| ------------------------ | ---------------------------------------- |
| `AppDbContext.cs`        | Entity Framework context defining DbSets |
| `Audit.cs`               | Core audit data model                    |
| `AuditReviewers.cs`      | Tracks SH/MR approval status             |
| `AuditApproval.cs`       | Logs approvals and reverts               |
| `AuditController.cs`     | Main business logic + PDF generation     |
| `AccController.cs`       | User registration/login management       |
| `DashbordsController.cs` | Role-based dashboards                    |
| `User.cs`                | User model and `UserRole` enum           |
| `Details.cshtml`         | Razor logic for conditional role actions |

---

## 🚀 Getting Started

### 🔧 Prerequisites

* Visual Studio 2019 or newer
* .NET Framework 4.6.1 or later
* SQL Server / LocalDB

### ⚙️ Installation Steps

1. **Clone the Repository**

   ```bash
   git clone [Your Repository URL]
   cd AuditApp
   ```

2. **Restore NuGet Packages**

   ```powershell
   Update-Package -reinstall
   ```

3. **Configure Database**

   * Edit `Web.config`
   * Update the connection string named `"AWA"`

4. **Run Code-First Migrations**

   ```powershell
   Enable-Migrations
   Add-Migration InitialSetup
   Update-Database
   ```

   > Ensure at least one user exists with the roles `Sectional_Head` and `MR`.

5. **Run the Application**
   Press **F5** in Visual Studio to launch via IIS Express.

---

## 👤 User Roles & Workflow

| Role                    | Responsibility                | Status Column         | Approval Dependency |
| ----------------------- | ----------------------------- | --------------------- | ------------------- |
| **Auditor**             | Creates audits, NCs, and OFIs | *(N/A)*               | None                |
| **Auditee**             | Responds to NCs/OFIs          | `AuditeeStatus`       | None                |
| **Sectional Head (SH)** | Reviews and approves          | `SectionalHeadStatus` | Independent         |
| **Management Rep (MR)** | Final quality review          | `MrStatus`            | Independent         |

📌 **Final report** becomes downloadable **only after both SH and MR approvals**.

---

## 🧩 Credits

Developed with 💻 using **ASP.NET MVC 5**, **Entity Framework**, and **Rotativa**.
Frontend powered by **Bootstrap 5** and **SweetAlert2**.

---

## 🛡️ License

© [Your Name / Company], [Year].
All Rights Reserved.
This repository is for informational and educational use only.
Unauthorized copying, modification, or distribution is prohibited.
