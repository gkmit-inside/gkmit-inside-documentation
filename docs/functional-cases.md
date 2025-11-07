# **Functional Use Cases**

This section describes the interactive behavior and workflows within the **GKMIT_INSIDE** platform.

## Post Submission Flow

This workflow describes how developers create and submit content for review.

### Step-by-Step Process

**Step 1: Navigate to Add Post**

- Developer logs in
- Clicks "Add Post" from navigation menu
- System verifies Developer/Admin role

**Step 2: Fill Post Form**

Required fields:

- Post title
- Description/content body
- Image upload (optional)
- Code snippet (if applicable)
- Tags for categorization

**Step 3:Submit**

- Post status changed to "Pending"
- Appears in Admin's pending queue

**Step 4: Confirmation**

- User redirected to "Your Posts" page
- Post visible with current status
- The post changes to "Success" state (if approved)

---

## Post Approval Flow

This workflow describes how administrators review and approve content.

### Step-by-Step Process

**Step 1: Access Admin Dashboard**

- Admin logs in
- Navigates to Admin Dashboard
- Views pending posts count

**Step 2: Review Pending Posts**

- Admin clicks "Pending Posts" section
- System displays list of submitted posts
- Each post shows:  
  -> Title and author  
  -> Submission timestamp  
  -> Preview/summary

**Step 3: Detailed Review**

Admin clicks on a specific post to view:

- Complete post content
- Attached images
- Code snippets
- Tags and category
- Author information

**Step 4: Decision Making**

Admin chooses one of two actions:

**Option A: Approve**

- Post status changes to "Accepted"
- Post immediately appears on main feed
- Author receives approval at "Your Post"
- Post visible to all users in "Feed"

**Option B: Reject**

- Post status changes to "Rejected"
- Post returns to author's "Your Posts"
- Feedback message attached (optional)
- Author can edit and resubmit

**Step 5: Workflow Completion**

- Post removed from pending queue
- Dashboard statistics updated
- Feed refreshed if approved

---

## Content Display Flow

This workflow describes how content appears and loads on the main feed.

### Step-by-Step Process

**Step 1: User Accesses Feed**

- Any logged-in user navigates to feed page.
- System queries database for accepted posts

**Step 2: Content Rendering**

Each post displays:

- Post title (bold, prominent)
- Author username
- Relative timestamp
- Post description/preview
- Featured image (if provided)

**Step 3: User Interactions**

Users can:

- Click post to view full details
- Save post to personal collection
- Search for specific content
- Filter by tags/categories

---

## User Activity Tracking Flow

This workflow describes how user actions are tracked and displayed.

### Activity Types

The system tracks and displays:

- New post submissions
- Post updates/edits
- New user registrations
- Post approvals
- Significant interactions

### Display Format

Activities shown as:

-> "Username performed action on timestamp"

- Examples:
  - "Akash posted 'Understanding REST APIs' 3hrs ago"
  - "Divyansh updated 'React Best Practices' 1hr ago"
  - "New user Priya joined the platform today"

### Update Mechanism

- Real-time or near-real-time updates
- Activity feed refreshes periodically
- Recent activities prioritized
- Historical activities archived after period

---

<!--
## Save Post Flow

Simple workflow for bookmarking content.

**Step 1:** User views post on feed

**Step 2:** User clicks "Save" button/icon

**Step 3:** System adds post to user's saved collection

**Step 4:** Confirmation message appears

**Step 5:** Post accessible via `/saved` endpoint

**To Remove:**

- Navigate to saved posts
- Click "Remove" on specific post
- Post removed from collection

---

## Edit Post Flow

Workflow for modifying existing content.

**Step 1:** Developer navigates to "Your Posts"

**Step 2:** Filters for posts needing edits (usually Rejected)

**Step 3:** Clicks edit icon/button on specific post

**Step 4:** System loads post data into edit form

**Step 5:** Developer modifies content as needed

**Step 6:** Developer saves changes (returns to Draft) or resubmits

**Step 7:** Post enters appropriate workflow based on action

---

## Search Flow

Workflow for finding specific content.

**Step 1:** User enters search query in search bar

**Step 2:** System queries database across:

- Post titles
- Post descriptions
- Tags
- Author names

**Step 3:** Results displayed with relevance ranking

**Step 4:** User clicks result to view full post

**Step 5:** Search history maintained for session (optional) -->
