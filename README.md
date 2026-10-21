# nce_notification
# 🏛️ NCE Campus Notice Board & Academic Routine Portal
### Nalanda College of Engineering, Chandi (Nalanda), Bihar — Batch 2K26

A modern, responsive, beginner-friendly web application designed for students, faculty, class representatives, and administrators of **Nalanda College of Engineering (NCE), Chandi, Bihar** for the **1st Semester (Batch 2K26)**.

The application integrates the official six-page college timetable (`TIME TABLE 2K26 NEW SYLLABUS.pdf`) with 100% fidelity, featuring branch filters, real-time push and in-app notifications, notice publication, role-based backend permission guards, an admin approval workflow, and timetable version archives.

---

## 🌟 Key Features

1. **Faithful 6-Page Timetable Digitization**:
   - Preserves all subject names, course codes, time slots, lab groups (G1/G2), room numbers, and faculty names directly from `TIME TABLE 2K26 NEW SYLLABUS.pdf`.
   - **Computer Science Engineering (CSE)**: Theory in Room No-005
   - **Artificial Intelligence Engineering (AI)**: Theory in RoomNo-007
   - **Electrical & Electronics Engineering (EEE)**: Theory in Room No-004
   - **Mechanical Engineering (ME)**: Theory in Room No-004
   - **Civil Engineering (CE)**: Theory in Room No-005
   - **Aeronautical Engineering (Aero)**: Theory in Room No-007
   - Labs (Comm. English Lab & EGD Lab): Room No-006

2. **Homepage Academic Hub**:
   - College branding in College Navy Blue (`#0f2b5c`, `#1e3a8a`) and Crisp White with Academic Gold accents.
   - **Today's Timetable Widget**: Automatically displays classes for the current day of the week, with branch filtering and live period indicators.
   - **Latest Announcements & Urgent Pinned Alerts**: Emergency circulars and key academic deadlines.
   - **Prominent Actions**: "View Full Routine", "Download Official PDF (397 KB)", "Subscribe Alerts", and "Post Notice".

3. **Complete Notice Board**:
   - 7 Categories: `General Notices`, `Class Updates`, `Exams`, `Assignments`, `Holidays`, `Events`, and `Timetable Updates`.
   - Real-time search by title, content, or publisher.
   - Category filter pills with counters and target branch filtering (`All Branches` vs specific branch).
   - Rich notice details modal with file attachment downloads, publisher role badges, and expiry indicators.

4. **Role-Based Access Control (RBAC) & Backend Security**:
   - **Student**: View notices, view/print/download timetable routines, subscribe to push notifications, and filter announcements. *Strictly prevented from publishing notices or altering routines on the backend layer.*
   - **Teacher**: Secure login, publish campus/departmental notices with attachments, edit own notices, and submit routine adjustment proposals.
   - **Class Representative (CR)**: Publish class updates for assigned branch/batch, and propose timetable modifications.
   - **Admin**: Approve or reject pending timetable proposals, rollback/restore earlier timetable versions, moderate notices, toggle pinned urgent status, and inspect complete audit trail logs.
   - **Enforcement**: Permissions are verified by a central `BackendService` data guard—not just by hiding UI buttons.

5. **Browser Push & In-App Notification System**:
   - Native Web Push API integration (`Notification.requestPermission()`, `new Notification()`).
   - Graceful fallback: If browser push is blocked or unsupported, in-app notification toasts and the top notification bell dropdown deliver all updates smoothly.
   - Instant notifications on newly published notices and approved routine revisions.

6. **Routine Revision & Approval Workflow**:
   - Teachers and CRs can propose schedule changes with justification and revised draft PDFs.
   - Submissions appear in the Admin Portal queue.
   - Admin confirmation updates the active routine, moves the prior routine to version history, and automatically publishes an official notice to students.

---

## 🚀 How to Run the Website (Beginner-Friendly)

You can run this portal with **zero software installation** or using standard developer tools:

### Option 1: Double-Click Local Server (Recommended for Windows)
1. Open the project folder:
   `c:\Users\laksh\Desktop\website\student registration`
2. **Double-click `start-server.bat`**.
3. It uses Windows' built-in `.NET HttpListener` (via `start-server.ps1`), launches a local server on port 3000, and automatically opens your web browser at `http://localhost:3000`!

### Option 2: Direct File Launch (No server needed)
1. Double-click `index.html` in Windows Explorer.
2. It will open directly in Google Chrome, Microsoft Edge, Brave, or Firefox.

### Option 3: VS Code Live Server
1. Open the project folder in **Visual Studio Code**.
2. Right-click `index.html` and select **"Open with Live Server"**.
3. The site opens at `http://127.0.0.1:5500/index.html`.

### Option 4: Using Node.js & Vite (If Node.js is installed)
```bash
npm install
npm run dev
```

---

## 👥 Pre-Configured Demo Accounts for Testing

Click the **Role Badge** in the top navigation bar or go to the **Admin Portal** tab to switch between accounts with a single click:

| Role | Name | Email | Password | Allowed Capabilities |
| :--- | :--- | :--- | :--- | :--- |
| **Admin** | Dr. Academic Dean | `admin@nce.ac.in` | `adminpassword123` | Full administrative control: approve/reject routine updates, rollback timetable, delete notices, view audit log. |
| **Teacher** | Prof. Rashmi Sinha (CSE) | `rashmi.sinha@nce.ac.in` | `teacherpassword123` | Publish faculty notices, upload attachments, propose routine revisions. |
| **CR** | Aman Sharma (CR CSE 2K26) | `cr.cse26@nce.ac.in` | `crpassword123` | Publish branch notices, propose timetable updates. |
| **Student** | Priya Sharma (Batch 2K26) | `student2k26@nce.ac.in` | `studentpassword123` | View routine, download PDF, search notices, manage push notifications. |

---

## 🧪 Testing the Main User Flows

### Flow 1: Student Views Routine & Downloads PDF
1. Ensure the active role is **Student** (default).
2. On the **Home** tab, observe "Today's Class Schedule" for CSE. Switch branches (AI, EEE, ME, CE, Aero) and days (Mon–Sat) to see real-time updates.
3. Click **"View Full Routine"** to open the Master Timetable.
4. Click **"Download PDF"** to download the official 6-page college syllabus PDF (`assets/TIME_TABLE_2K26_NEW_SYLLABUS.pdf`).
5. Click **"View Official PDF"** to inspect the embedded 6-page document in an interactive modal.
6. Click **"Print Routine"** to trigger a clean, formatted A4 printable view complete with HOD, Coordinator, and Principal signature lines.

### Flow 2: Teacher Publishes a Notice with Attachment
1. Click the top role badge and switch to **Teacher (Prof. Rashmi Sinha)**.
2. Click **"Publish New Notice"** on the Notice Board tab or Hero section.
3. Fill in the title (e.g., `PPS Lab Problem Set 2 Viva`), select category `Assignments`, choose branch `CSE`, write a description, optionally select a file attachment, and submit.
4. The notice appears instantly at the top of the Notice Board with an in-app audio chime, toast alert, and notification bell counter increment.

### Flow 3: CR Proposes a Timetable Update
1. Switch role to **Class Representative (Aman Sharma)**.
2. Go to the **Timetable Routine** tab and click **"Propose Update"**.
3. Fill in the proposed revision (e.g., `Shift Friday Remedial slot to Thursday Tutorial`), provide rationale, and submit.
4. The proposal is queued in the system awaiting administrative approval.

### Flow 4: Admin Approves Routine Update & Inspects Audit Log
1. Switch role to **Admin (Dr. Academic Dean)**.
2. Navigate to the **Admin Portal** tab.
3. In the **"Pending Timetable Update Proposals"** section, locate the CR proposal.
4. Click **"✓ Approve Update"** and enter an approval confirmation note.
5. The active timetable version increments, an official announcement is automatically posted on the campus notice board, and students receive a broadcast notification!
6. Scroll down to the **"System Audit Trail"** to verify that the approval event was logged with timestamp and user details.
7. To revert, click **"↺ Restore this snapshot"** in the Timetable Revision History archive.

### Flow 5: Push Notifications & Fallback
1. Click the **Notification Bell** at top right and choose **"Settings ⚙️"**.
2. Click **"Enable Push"** to request browser notification permission via the Web Push API.
3. If permission is granted, native browser notifications will pop up; if denied or running from a local file, the graceful in-app toast notification engine handles all alerts.
4. Click **"Send Test Notification"** to test the alert mechanism.

---

## 📁 Project Architecture & File Tree

```text
student registration/
├── index.html                                # Semantic HTML5 responsive single-page portal shell
├── start-server.ps1                          # Zero-install PowerShell .NET local web server
├── start-server.bat                          # Double-click launcher for Windows
├── package.json                              # Vite/Node configuration for developer workflows
├── assets/
│   ├── TIME_TABLE_2K26_NEW_SYLLABUS.pdf      # Official 6-page college syllabus PDF (397 KB)
│   ├── nce-logo.svg                          # Official Nalanda College of Engineering crest
│   └── favicon.svg                           # Portal browser tab icon
├── css/
│   └── portal.css                            # College branding, timetable grid, animations & print styles
├── js/
│   ├── app.js                                # Main application controller & tab views router
│   ├── data/
│   │   ├── officialTimetable.js              # Complete 6-page digitized timetable data
│   │   ├── initialNotices.js                 # Realistic seed notices for Batch 2K26
│   │   └── initialUsers.js                   # Seed user credentials & permissions
│   └── services/
│       ├── db.js                             # Persistent storage service (localStorage + schema versioning)
│       ├── auth.js                           # User session manager & role-based helpers
│       ├── backend.js                        # Security guard: permission validation, sanitization & audit logs
│       └── notificationService.js            # Browser push API + graceful in-app notification engine
└── README.md                                 # Comprehensive documentation & setup instructions
```

---

## 🌐 Free Deployment Options

You can deploy this portal online for **$0 free cost** in under 2 minutes:

### Option 1: GitHub Pages (Free)
1. Push this folder to a GitHub repository (e.g., `nce-campus-notice-board`).
2. In your repository on GitHub, navigate to **Settings** > **Pages**.
3. Under **Branch**, select `main` and folder `/ (root)`, then click **Save**.
4. Your site will be live at `https://<your-username>.github.io/<repo-name>/`.

### Option 2: Vercel (Free)
1. Install Vercel CLI (`npm i -g vercel`) or sign in at [vercel.com](https://vercel.com).
2. Import the GitHub repository or run `vercel` in this directory.
3. Framework Preset: **Other** (or Vite).
4. Click **Deploy**.

### Option 3: Netlify (Free)
1. Drag and drop the project folder onto [app.netlify.com/drop](https://app.netlify.com/drop).
2. Netlify instantly deploys your site with free SSL.

---

## 📄 License & Attribution

- **Institution**: Nalanda College of Engineering, Chandi, Nalanda, Bihar – 801108
- **Affiliation**: Bihar Engineering University (BEU), Patna & AICTE, New Delhi
- **Document Source**: `TIME TABLE 2K26 NEW SYLLABUS.pdf` (Batch 2K26)
