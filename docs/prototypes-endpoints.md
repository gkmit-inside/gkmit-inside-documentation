# **Prototypes and Endpoints**

This section outlines all platform pages, their corresponding endpoints, and permitted user roles.

## Public Pages

### Landing Page (Before Login)

**Endpoint:** `/`

**Description:** The entry point for all visitors, providing project information and login option.

**Content:**

- Welcome message
- Platform overview
- Login button

**Access:** All Visitors (including external)

---

## User Pages

### Home/Feed

**Endpoint:** `/feed`

**Description:** Main content feed displaying all accepted posts.

**Features:**

- Chronological post listing
- Search integration
- Activity stream

**Access:** All Users (Developer, Admin)

### Saved Posts

**Endpoint:** `/saved`

**Description:** Personal collection of bookmarked posts.

**Features:**

- List of saved posts
- Quick access to bookmarked content
- Remove from saved option

**Access:** All Users (Developer, Admin)

---

## Developer Pages

### Add Post

**Endpoint:** `/addpost`

**Description:** Form interface for creating new posts.

**Form Fields:**

- Title
- Image upload
- Description
- Code snippet section (optional)
- Tags (for categorisation)

**Actions:** Submit for Review

**Access:** Developer, Admin

### Your Posts

**Endpoint:** `/yourpost`

**Description:** Personal workspace showing all posts submitted by the logged-in user.

**Filters:**

- All posts
- Pending review
- Accepted posts
- Rejected posts

**Access:** Developer, Admin

### Edit/Delete Post

**Endpoint:** `/edit/<post_id>`

**Description:** Interface for modifying existing posts.

**Capabilities:**

- Edit post content
- Update images
- Modify tags and categories
- Delete post
- Resubmit rejected posts

**Access:** Developer, Admin (own posts only)

---

## Admin Pages

### Admin Dashboard

**Endpoint:** `/dash`

**Description:** Central administrative interface with platform overview.

**Dashboard Sections:**

- Pending users count
- Pending posts count
- Total registered users
- Total accepted posts

**Access:** Admin Only

### Pending Users

**Endpoint:** Sub-section of Admin Dashboard

**Description:** User management interface for new registrations.

**Actions:**

- View and check user details
- Approve registration
- Reject registration

**Access:** Admin Only

### Pending Posts

**Endpoint:** Sub-section of Admin Dashboard

**Description:** Content review queue for submitted posts.

**Actions:**

- View full post content
- Approve for publication
- Reject with feedback

**Access:** Admin Only

---

## System Pages

### Logout

**Endpoint:** `/logout`

**Description:** Terminates the current user session.

**Action:** Redirects to landing page (`'/'`) after session termination.

**Access:** All Users

---

## Endpoint Summary Table

| Endpoint          | Description       | Developer | Admin |
| ----------------- | ----------------- | --------- | ----- |
| `/`               | Landing page      | Yes       | Yes   |
| `/feed`           | Main content feed | Yes       | Yes   |
| `/saved`          | Saved posts       | Yes       | Yes   |
| `/addpost`        | Create new post   | Yes       | Yes   |
| `/yourpost`       | User's posts      | Yes       | Yes   |
| `/edit/<post_id>` | Edit/delete post  | Yes       | Yes   |
| `/dash`           | Admin dashboard   | No        | Yes   |
| `/logout`         | Logout            | Yes       | Yes   |
