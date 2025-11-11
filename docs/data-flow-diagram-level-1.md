# **Level 1 — System Level Data Flow Diagram**

This Level 1 DFD expands on the **GKMIT_INSIDE** platform — a role-based internal social network designed for company employees and administrators.  
It illustrates how different system modules interact with each other, how users exchange data with these modules, and how all information flows to and from the **MongoDB** data stores.

---

## **Overview**

At the core of the system lies the **GKMIT_INSIDE** platform — the central application responsible for handling user actions, post management, engagement tracking, and analytics.  
There are two primary user roles:

- **Employee:** A regular user who can register, log in, post content, view feeds, and engage (comment/react/bookmark).
- **Admin:** A privileged user responsible for managing employees, moderating posts, and analyzing platform metrics.

All these interactions are supported by a **MongoDB Database**, organized into specific collections for users, posts, and interactions.

---

## Data Flow Diagram: Level 1

![DFD: Level - 0](assets/images/dfd-level-1.png){ width="2900" height="2600" }

---

## **Module Descriptions**

---

### **Employee**

The **Employee** represents a regular user of the system.

Employees can:

- Register and authenticate within the platform.
- Create, edit, or delete their posts.
- View the company-wide feed of approved posts.
- Engage with other posts via comments, reactions, and bookmarks.

All employee actions are routed through the **GKMIT_INSIDE System**, which controls business logic and data flow.

---

### **Admin**

The **Admin** has elevated privileges within the platform, including all the features of the employee.

Admins can:

- Manage user accounts (approve/reject new users, change access levels).
- Moderate and approve posts submitted by employees.
- View analytical dashboards that summarize system usage, engagement, and post activity.

Admins interact mainly with the **User Management**, **Post Management**, and **Analytics** modules.

---

## **System Modules**

---

### **1. Authentication & Authorization**

- Handles user registration, login, and access token generation.
- Verifies credentials and determines access based on role (`Employee` or `Admin`).
- Reads/writes user data from the **USERS** collection.

**Data Flow:** `Employee/Admin → AUTH → USERS`

---

### **2. User Management (Admin)**

- Enables the admin to manage employee profiles and statuses.
- Supports actions like approving pending users, updating roles, or deactivating accounts.
- Syncs all changes with the **USERS** collection.

**Data Flow:** `Admin → Dashboard → USERS`

---

### **3. Post Management**

- Core module for content creation and moderation.
- Employees can create, edit, and delete posts.
- Admins can approve or reject posts before they appear in the feed.
- All posts are stored in the **POSTS** collection.

**Data Flow:** `Employee → Post → POSTS`

---

### **4. Feed & Content Delivery**

- Responsible for serving approved posts to employees.
- Fetches data from **POSTS** and applies filters (e.g., tags, search queries).
- Ensures only _approved_ posts are visible in feeds.

**Data Flow:** `Employee → FEED → POSTS`

---

### **5. Interaction System**

- Handles all post interactions, including:
  - **Comments**
  - **Reactions** (emoticons)
  - **Bookmarks**
- Each type of engagement is stored in a separate collection for scalability and analytics.

**Data Flow:** `Employee → INTERACT → COMMENTS / REACTIONS / BOOKMARKS`

---

### **6. Analytics & Dashboard**

- Available only to the admin.
- Aggregates system-wide metrics such as:
  - Total active users
  - Post engagement trends
  - Reaction and bookmark counts
- Pulls and aggregates data from all collections for visual insights and reporting.

**Data Flow:** `ANALYTICS ↔ USERS / POSTS / COMMENTS / REACTIONS / BOOKMARKS`

---

---

## **Summary**

This **Level 1 Data Flow Diagram (DFD)** provides a holistic overview of the **GKMIT_INSIDE** system’s data flow.

It clearly defines:

- How users (**Employees** and **Admins**) interact with various modules.
- How those modules depend on and exchange information with the **MongoDB Database**.
- How internal processes communicate to create a **seamless**, **secure**, and **scalable** internal platform.

---
