# Auto Ticket Classification Using Flow Designer

![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)
![Platform: ServiceNow](https://img.shields.io/badge/Platform-ServiceNow-blue)

A complete end-to-end automation solution for a school IT helpdesk built on the ServiceNow platform. The system automatically classifies incoming IT tickets based on keywords in the issue's short description, dynamically populates categories and dependent subcategories, and dispatches automated email acknowledgments to the caller.

---

## 🎥 Demo Video

![Auto Ticket Classification Demo](media/demo.gif)

https://github.com/user-attachments/assets/30f270fd-9658-458f-8e08-48bde0914f5c

---

## 📁 Repository Contents

* **`sys_remote_update_set(NM5).xml`**: Exported ServiceNow Update Set containing all schema configurations, choice fields, and Flow Designer logic.
* **`Auto_Ticket_Classification_using_Flow_Designer.pdf`**: Complete technical design documentation and requirement checklist.
* **`media/`**: Demo video and visual assets.

---

## ✨ Business Requirements & Features

- **Automated Classification:** Automatically classifies IT tickets based on short description keywords.
- **Category & Subcategory Assignment:** Dynamically populates `Category` and `Subcategory` fields without manual intervention.
- **Dependent Choice Logic:** Ensures subcategory picklists dynamically align with parent categories.
- **Automated Notification:** Sends immediate email notifications to ticket callers upon creation.
- **Standardized Data Schema:** Maintains data integrity by storing ticket details within standard ServiceNow schema fields.
- **Scalability & Maintenance:** Utilizes no-code Flow Designer logic for easy extension and low maintenance overhead.

---

## 🛠️ Technical Implementation

### Custom Table Schema (`u_ticket_record`)
- **Number** (`String`)
- **Caller** (`Reference` to Sys User)
- **Category** (`Choice`)
- **Subcategory** (`Choice` — Dependent on Category)
- **Short Description** (`String`)
- **Description** (`String`)
- **State** (`Choice`)
- **Assignment Group** (`Reference`)
- **Assigned To** (`Reference`)

### Workflow Engine (`Auto Classify School IT Tickets`)
- **Trigger:** Incident Created
- **Flow Actions:**
  1. `If` Short Description contains **Wireless / Network** $\rightarrow$ Sets Category to `Network` & Subcategory to `Wi-Fi`.
  2. `Else If` Short Description contains **Operating System / Hardware** $\rightarrow$ Sets Category to `Hardware` & Subcategory to `Monitor`.
  3. `Else If` Short Description contains **Forgot Password** $\rightarrow$ Sets Category to `Account` & Subcategory to `Password`.
  4. `Send Email` $\rightarrow$ Dispatches confirmation notification to the ticket caller.

---

## 🚀 Installation & Setup

1. **Download Update Set:** Download `sys_remote_update_set.xml` from this repository.
2. **Import XML:**
   - Log in to your ServiceNow Personal Developer Instance (PDI) as Administrator.
   - Navigate to **System Update Sets** $\rightarrow$ **Retrieved Update Sets**.
   - Click **Import Update Set from XML** and select `sys_remote_update_set.xml`.
3. **Preview & Commit:**
   - Open **Project Update Set**.
   - Click **Preview Update Set**, then click **Commit Update Set**.
4. **Activate Flow:**
   - Navigate to **Workflow Studio** / **Flow Designer**.
   - Open **Auto Classify School IT Tickets** and click **Activate**.

---

## 📄 License

Distributed under the MIT License. See `LICENSE` for details.

