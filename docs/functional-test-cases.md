# **TC 2: Authentication and Authorization**

---

## TC 1.A: Registration Test Cases

This section ensures the user registration process functions correctly, enforcing all **validation rules**, **data integrity**, and **business logic** for onboarding new users.

| **Test Case No.** | **Module Name** | **Test Case Description**                                                                                                              | **Acceptance Criteria**                                                                                                                                                                                                  |
| ----------------- | --------------- | -------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| T_C_1.1           | Registration    | Verify a new user can successfully register with valid, unique, and required data.                                                     | A success message must be displayed, the user must be redirected to a waiting/login page, and a new record must be created in the `USERS` table with: `isApproved = false`, `createdAt` set, and a valid `passwordHash`. |
| T_C_1.2           | Registration    | Verify registration fails if the user attempts to register with an email that already exists in the system.                            | An appropriate error message must be displayed (e.g., “Email already registered”), and the user must remain on the registration page. No new record should be created.                                                   |
| T_C_1.3           | Registration    | Verify registration fails if the Name field is left empty.                                                                             | An error message indicating the field is required (e.g., “Name is mandatory”) must be displayed.                                                                                                                         |
| T_C_1.4           | Registration    | Verify registration fails if the Email field is left empty.                                                                            | An error message indicating the field is required (e.g., “Email is required”) must be displayed.                                                                                                                         |
| T_C_1.5           | Registration    | Verify registration fails if the Password field is left empty.                                                                         | An error message indicating the field is required (e.g., “Password is required”) must be displayed.                                                                                                                      |
| T_C_1.6           | Registration    | Verify registration fails if the user provides an invalid email format (e.g., missing '@' or using spaces).                            | A format validation error message (e.g., “Please enter a valid email address”) must be displayed.                                                                                                                        |
| T_C_1.7           | Registration    | Verify registration fails if the Password does not meet complexity requirements (e.g., missing a special character or capital letter). | A specific error message detailing the required password criteria must be displayed.                                                                                                                                     |
| T_C_1.8           | Registration    | Verify that the department field only accepts pre-defined valid values (`hr`, `recruitment`, `developer`).                             | If the user attempts to submit a department value not in the list (e.g., “finance”), the system must reject the submission and display an error.                                                                         |
| T_C_1.9           | Registration    | Verify the system handles the maximum length allowed for the name field.                                                               | If a name exceeds the allowed character limit, the system must either truncate the input or display an error message and prevent submission.                                                                             |
| T_C_1.10          | Registration    | Verify that the system automatically assigns a default `userRoleId` upon registration (likely the Employee role).                      | After successful registration (T_C_1.1), the created user record must have a valid `userRoleId` reference corresponding to the Employee role.                                                                            |

---

## TC 1.B: Login Test Cases

This section validates the authentication process to ensure only authorized users can access the platform using valid credentials.

| **Test Case No.** | **Module Name** | **Test Case Description**                                                            | **Acceptance Criteria**                                                                                                                                    |
| ----------------- | --------------- | ------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| T_C_1.11          | Login           | Verify a valid combination of Employee email and Password allows successful login.   | The system must grant access to the Employee `/feed` page, and the correct name must be displayed.                                                         |
| T_C_1.12          | Login           | Verify a valid combination of Admin email and Password allows successful login.      | The system must grant access to the Admin dashboard, and the correct user name must be displayed.                                                          |
| T_C_1.13          | Login           | Verify login fails with a valid email and an invalid password (for any role).        | An appropriate error message must be displayed (e.g., "Invalid credentials" or "Invalid password"), and the user must remain on the login page.            |
| T_C_1.14          | Login           | Verify login fails with an invalid email and a valid password (for any role).        | An appropriate error message must be displayed (e.g., "Invalid credentials" or "Invalid email"), and the user must remain on the login page.               |
| T_C_1.15          | Login           | Verify login fails with both invalid email and invalid password.                     | An appropriate error message must be displayed, and the user must remain on the login page.                                                                |
| T_C_1.16          | Login           | Verify case sensitivity for the email field.                                         | Login must fail if the email case does not match the stored value (e.g., `JohnDoe@service.com` should fail if the correct email is `johndoe@service.com`). |
| T_C_1.17          | Login           | Verify the system handles repeated failed login attempts (Brute-Force Protection).   | After **N** consecutive failed attempts (e.g., 5), the account must be temporarily locked or a CAPTCHA/other protective measure must be required.          |
| T_C_1.18          | Login           | Verify login fails when the email field is empty and the password field has data.    | An error message for the missing email (e.g., "Email is required") must be displayed, and the user must remain on the login page.                          |
| T_C_1.19          | Login           | Verify login fails when the password field is empty and the email field has data.    | An error message for the missing password (e.g., "Password is required") must be displayed, and the user must remain on the login page.                    |
| T_C_1.20          | Login           | Verify login fails with an improperly formatted email (e.g., missing '@' or '.com'). | An appropriate format validation error message (e.g., "Please enter a valid email address") must be displayed.                                             |
| T_C_1.21          | Logout          | Verify that clicking the Logout button successfully terminates the user session.     | The user must be redirected to the login page, and attempting to use the browser's "Back" button should not display any protected internal content.        |
| T_C_1.22          | Logout          | Verify that session cookies are properly cleared/invalidated upon successful logout. | After logging out, checking the browser's developer tools should show that the session identifier/token cookie is removed or set to expired/invalid.       |

---

## TC 1.C: Session Management Test Cases

This section covers the test scenarios for **session management** and **logout functionality**, ensuring security, stability, and user session integrity.

| **Test Case No.** | **Module Name** | **Test Case Description**                                                                                                       | **Acceptance Criteria**                                                                                                                                                                                |
| ----------------- | --------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| T_C_1.23          | Session         | Verify a logged-in user is automatically logged out after a period of inactivity (Session Timeout).                             | The user must be redirected to the login page, and attempting to access an internal page must redirect them back to the login page.                                                                    |
| T_C_1.24          | Session         | Verify the system does not allow simultaneous logins for the same account (or enforces specific session rules).                 | When a user is logged in on Device A, a subsequent successful login on Device B must either terminate the session on Device A or the system must disallow the login on Device B and display a warning. |
| T_C_1.25          | Session         | Verify the application handles security vulnerability warnings when accessing the application over HTTP (if HTTPS is required). | If the application is accessed via `http://` instead of `https://`, the user should be automatically redirected to the secure HTTPS connection, or a security warning should be displayed.             |

---

## TC 1.D: Authorization (Role-based Access Control) Test Cases

This section validates that users can only access resources permitted by their assigned roles, ensuring **data security** and **role integrity** throughout the system.

| **Test Case No.** | **Module Name** | **Test Case Description**                                                                                     | **Acceptance Criteria**                                                                                                                           |
| ----------------- | --------------- | ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| T_C_1.26          | Authorization   | Verify an Employee user cannot access a URL/page specific to the Admin role via direct URL navigation.        | The system must display an “Access Denied” error message, or redirect the user to their own dashboard.                                            |
| T_C_1.27          | Authorization   | Verify an Admin user cannot perform Employee-only actions with differing business logic (if applicable).      | The Admin must be either permitted where applicable or properly denied for Employee-only restricted actions.                                      |
| T_C_1.28          | Authorization   | Verify an Employee user cannot access an Admin-only API endpoint (via Postman or browser dev tools).          | The API must return `403 Forbidden` or `401 Unauthorized`, and no data should be modified or accessed.                                            |
| T_C_1.29          | Authorization   | Verify an unauthenticated/Guest user cannot access any authenticated internal page via direct URL navigation. | The user must be immediately redirected to the Login page when attempting to access any protected resource (e.g., `/feed` or `/admin/dashboard`). |

---
