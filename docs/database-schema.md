# **Database Schema**

## Overview

The database for the platform is designed using a modular approach, primarily centered around users, posts, and their interactions. Each user can create posts, react, comment, and bookmark them. Posts are moderated and managed by admins.

Soft deletion is implemented for reversible actions and moderation flexibility.  
This design ensures scalability, maintainability, and clear ownership across entities.

## Schema

![Database Schema](assets/images/schema.png){ width="1800" }

## **Table Description**

### Table: `USERS`

| Field          | Type     | Description                                                 |
| -------------- | -------- | ----------------------------------------------------------- |
| `_id`          | ObjectId | Unique ID created after registration                        |
| `name `        | string   | Name of the user                                            |
| `email `       | string   | Email ID for unique identification (no duplicates)          |
| `passwordHash` | string   | Hashed password string                                      |
| `roleUserId`   | ObjectId | References to USERS_ROLES                                   |
| `department `  | string   | Department of the user (`hr` / `recruitment` / `developer`) |
| `isApproved`   | boolean  | `false` by default; becomes `true` once approved by admin   |
| `approvedAt`   | date     | Timestamp when post was approved                            |
| `createdAt `   | date     | Timestamp of creation                                       |
| `updatedAt `   | date     | Timestamp of last update                                    |
| `deletedAt`    | date     | Timestamp of soft deletion                                  |

### Table: `POSTS`

| Field         | Type     | Description                                                        |
| ------------- | -------- | ------------------------------------------------------------------ |
| `_id `        | ObjectId | Auto-generated post ID                                             |
| `userId`      | ObjectId | Reference to USERS                                                 |
| `mediaUrl  `  | string   | Cloud storage link of uploaded media                               |
| `title  `     | string   | Title of the post                                                  |
| `subtitle`    | string   | Subtitle of the post                                               |
| `description` | string   | Detailed content of the post                                       |
| `tags`        | array    | List of tags for categorization (e.g., ['web', 'api', 'ui'])       |
| `postStatus`  | string   | `pending` by default; updated to `approved` or `rejected` by admin |
| `approvedAt`  | date     | Timestamp when post was approved                                   |
| `createdAt`   | date     | Timestamp of post creation                                         |
| `updatedAt`   | date     | Timestamp of last update                                           |
| `deletedAt`   | date     | Timestamp of soft deletion                                         |

### Table: `COMMENTS`

| Field       | Type     | Description                     |
| ----------- | -------- | ------------------------------- |
| `_id  `     | ObjectId | Generated when comment is added |
| `postId `   | ObjectId | Reference to POSTS              |
| `userId  `  | ObjectId | Reference to USERS              |
| `content `  | string   | Text content of the comment     |
| `createdAt` | date     | Timestamp of creation           |
| `updatedAt` | date     | Timestamp of last update        |
| `deletedAt` | date     | Timestamp of soft deletion      |

### Table: `REACTIONS`

| Field          | Type     | Description                            |
| -------------- | -------- | -------------------------------------- |
| `_id `         | ObjectId | Generated when a user reacts to a post |
| `postId `      | ObjectId | Reference to POSTS                     |
| `userId`       | ObjectId | Reference to USERS                     |
| `reactionType` | string   | Type of reaction (emoji, like, etc.)   |
| `createdAt`    | date     | Timestamp of creation                  |
| `updatedAt`    | date     | Timestamp of last update               |
| `deletedAt`    | date     | Timestamp of soft deletion             |

### Table: `BOOKMARKS`

| Field       | Type     | Description                         |
| ----------- | -------- | ----------------------------------- |
| `_id `      | ObjectId | Generated when a post is bookmarked |
| `postId `   | ObjectId | Reference to POSTS                  |
| `userId`    | ObjectId | Reference to USERS                  |
| `createdAt` | date     | Timestamp of creation               |
| `updatedAt` | date     | Timestamp of last update            |
| `deletedAt` | date     | Timestamp of soft deletion          |
