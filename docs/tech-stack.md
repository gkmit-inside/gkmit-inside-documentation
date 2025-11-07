# Technology Stack

GKMIT_INSIDE is built using modern web technologies to ensure performance, scalability, and maintainability.

## Stack Overview

| Category                   | Technology        | Purpose                    |
| -------------------------- | ----------------- | -------------------------- |
| **Frontend Framework**     | ReactJS           | Core UI framework          |
| **State Management**       | Context API       | Global state management    |
| **Styling Framework**      | TailwindCSS       | Utility-first CSS styling  |
| **Styling Alternative**    | Styled Components | CSS-in-JS approach         |
| **UI Component Library**   | Shadcn UI         | Pre-built UI components    |
| **UI Library Alternative** | Material UI       | Component library          |
| **Backend Framework**      | Express.js        | Web application framework  |
| **Database**               | MongoDB           | NoSQL document database    |
| **Authentication**         | JWT               | Token-based authentication |
| **Frontend Deployment**    | Vercel            | Frontend hosting platform  |
| **Backend Deployment**     | Render            | Backend hosting platform   |

---

## System Architecture Diagram

```
┌─────────────────────────────────────────────────┐
│                   Client Layer                  │
│  (React + Context API + TailwindCSS + Shadcn)   │
└──────────────────┬──────────────────────────────┘
                   │ HTTPS/REST API
┌──────────────────┴──────────────────────────────┐
│              Application Layer                  │
│         (Node.js + Express + JWT)               │
└──────────────────┬──────────────────────────────┘
                   │ MongoDB Driver
┌──────────────────┴─────────────────────────────-─┐
│               Database Layer                     │
│                  (MongoDB)                       │
└──────────────────────────────────────────────────┘
```

---
