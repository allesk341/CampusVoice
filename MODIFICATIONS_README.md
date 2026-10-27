# CampusVoice update

This update applies the feature list from the shared “Update CampusVoice Features” conversation while keeping the existing pages, colors, cards, and navigation structure.

## Included changes

- Added an optional public `landing.html`; the existing sign-in page remains the authentication entry point and links to the landing page.
- Removed the footer from sign-in and from the student concern form. Student, staff, and admin workspaces use the shared shell, which has no footer.
- Removed the separate student “Report a Concern” navigation item. The form now opens from **My Concerns** in a popup and refreshes the concern list after a successful submission.
- Changed the staff dashboard header to a single time-of-day greeting and added a Quick Action when a newly assigned task has a due/assignment date today.
- Concern photos open in a lightbox instead of a new browser tab.
- Admin **Needs Your Attention** shows urgent open concerns only and links to Notifications.
- Student submissions now select Minor, Major, or Urgent. Apply `database/migrations/20261026_concern_classification.sql` to an existing Supabase database before using the form.
- The Assignment Queue now contains only unassigned concerns. Reassignment remains in the Current Assignments table.
- The app already uses asynchronous Supabase client requests. The new report popup also refreshes My Concerns without navigating or reloading the whole page. Authentication and the existing multi-page navigation still use their current page flow; this update does not add a custom AJAX server.

## Database setup

For an existing database, run the SQL migration once in the Supabase SQL editor. For a fresh database, use the updated `database/supabase_schema.sql`. Confirm the priorities table contains active `Minor`, `Major`, and `Urgent` records before testing a student submission.

## Entry points

- Public landing: `landing.html`
- Sign in: `index.html`
- Student popup form: open **My Concerns** and choose **New Concern**
