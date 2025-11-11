# DFD Level 2: User Management

---

## Overview

The **User Management** module acts as the administrative gatekeeper for the system. Its primary role is to enforce access control by managing the approval or rejection of new accounts and providing the Admin with a comprehensive, read-only view of all registered users.

This module ensures that only approved users can gain full access to the application after their initial registration.

---

## Workflow Explanation

The module is structured around two key processes, both exclusively controlled by the **Admin** role, and interacting solely with the **USERS (MongoDB)** data store.

![User MGMT DFD: Level - 2](assets/images/user-dfd-level-2.png){ width="1000" height="1000" }

---

## 1. User Data Retrieval & Search (P1)

This flow enables the Admin to monitor the status of all registered users.

1. **Admin → 6.0 User Data Retrieval & Search (1) Request All / Pending Users**  
   The Admin initiates a request to the system to fetch the user list, optionally filtered to show only pending users or a specific account.

2. **6.0 User Data Retrieval & Search → USERS (2) Read All User Records**  
   The process queries the **USERS** collection to retrieve relevant user data.

3. **USERS → 6.0 User Data Retrieval & Search (3) All User Data (with Status)**  
   The database returns all user records, including their current `isApproved` status.

4. **6.0 User Data Retrieval & Search → Admin (4) Display List & Search Results**  
   The retrieved list is displayed on the Admin dashboard, allowing the Admin to identify and select accounts for approval.

---

## 2. User Status Update (Approval) (P2)

This flow manages the activation or rejection of user accounts after administrative review.

1. **Admin → 7.0 User Status Update (Approval) (5) User ID + Approval/Rejection Action**  
   The Admin selects a user and issues an action: Approve (sets `isApproved: true`) or Reject (keeps `isApproved: false`).

2. **7.0 User Status Update (Approval) → USERS (6) Update 'isApproved' Status**  
   The process updates the corresponding user record in the **USERS** collection with the chosen status.

3. **7.0 User Status Update (Approval) → Admin (7) Success Message + Updated List Request**  
   The Admin receives confirmation of the successful update, and the dashboard automatically refreshes to reflect the change.

---

## Summary

- The **User Management** module has a simple but critical governance function. By limiting its capabilities to reading user data and updating the binary approval flag, it centralizes system-level access control.
- This design ensures that no user can access the main application features without explicit administrative approval.
- It maintains strict oversight of user onboarding and upholds security and operational integrity across the GKMIT_INSIDE platform.
