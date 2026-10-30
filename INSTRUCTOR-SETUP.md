# Instructor setup (one time, about 15 minutes)

The course runs as two Google Apps Script sites, both limited to **@rtu.edu.ph** accounts, plus this GitHub
site as the public entry point. It works exactly like the PHYMECH modules.

| What | Address | Who can open it |
|------|---------|-----------------|
| Entry point | https://mrvitalez.github.io/IntegCal-online-module/ | Anyone. It immediately sends visitors to the student site. |
| Student site | your web app URL (ends in `/exec`) | Only signed-in **@rtu.edu.ph** accounts. Google tells the site who the student is, so nobody types an email. |
| Admin site | the same URL + `?page=admin` | Only **rmvitalez@rtu.edu.ph** (edit `ADMIN_EMAILS` at the top of `Code.gs` to add co-teachers). |

All records are kept in a Google Sheet in your Drive: submissions (one tab per module, sorted by block section and
last name), video answers, the student list, the recordbook, settings, block sections, modules and the answer key.

Do every step signed in to Google as **rmvitalez@rtu.edu.ph**. Use a **new** Sheet and a **new** Apps Script
project for this course; do not reuse the PHYMECH ones.

## 1. Create the Sheet and the Apps Script project

1. In Google Drive, create a new blank Google Sheet named **CAL02 Online Modules (records)**.
2. In the Sheet: **Extensions → Apps Script**. Name the project **CAL02**.

## 2. Add the five files

In the Apps Script editor, create these files and paste in their contents. For each file in `apps-script/` of this
repository, open it on GitHub, click **Raw**, select all (Ctrl+A), copy, and paste it into the editor file
(press Ctrl+A in the editor file first, so the paste replaces what is there).

| Editor file | Type (the **+** next to *Files*) | Copy from |
|-------------|------|-----------|
| `Code.gs` | already exists; replace its contents | [`apps-script/Code.gs`](apps-script/Code.gs) |
| `Seed.gs` | Script | the **private** `Seed.gs` file you received separately (it holds the answer key, so it is not on GitHub) |
| `Student` | HTML | [`apps-script/Student.html`](apps-script/Student.html) |
| `Admin` | HTML | [`apps-script/Admin.html`](apps-script/Admin.html) |
| `Styles` | HTML | [`apps-script/Styles.html`](apps-script/Styles.html) |

The editor adds `.html` to HTML files by itself: name them exactly `Student`, `Admin` and `Styles`. A new HTML file
starts with some sample text; delete it before pasting. Click **Save**.

## 3. Run setup once

1. In the editor's function menu (top bar) choose **setup** (not `myFunction`), then click **Run**.
2. Google asks for permission the first time: **Review permissions →** your account **→ Allow**. If you see
   "Google hasn't verified this app", click **Advanced → Go to CAL02 (unsafe)**; it is your own script.
3. When it finishes, the Sheet has the tabs *Settings, Block Sections, Modules, Answer Key, Students,
   Video Responses, Recordbook, Archive Log* and one tab per module. Setup also installs the daily check that
   archives the records after the semester. It is safe to run setup again; it never overwrites your data.

## 4. Deploy the web app

1. **Deploy → New deployment →** gear icon **→ Web app**.
2. Description: `CAL02`. **Execute as: Me (rmvitalez@rtu.edu.ph)**.
   **Who has access: Anyone within Rizal Technological University.**
3. **Deploy**, then copy the **Web app URL** (it ends in `/exec`).
4. Open `URL?page=admin` in your browser. This is your admin site; bookmark it.

## 5. Point the GitHub site at the student site

1. In GitHub, open `assets/config.js`, click the pencil (Edit), paste the web app URL between the quotes:
   ```js
   window.CAL02_STUDENT_URL = "https://script.google.com/a/macros/rtu.edu.ph/s/XXXXXXXX/exec";
   ```
   and commit.
2. Make sure GitHub Pages is on: **Settings → Pages → Deploy from a branch → main → / (root) → Save**.
3. Give students https://mrvitalez.github.io/IntegCal-online-module/ (or the web app URL directly).

## 6. First things to do in the admin site

1. **Semester:** paste your web app URL (the one ending in `/exec`) into **Student site address**. All links between
   pages use it. Then check the semester name, set the start and end dates, and check attempts, answer reveal and
   automatic archive. The Syllabus and Consultation links are already filled in.
2. **Block sections:** type your sections, one per line (they appear as a dropdown in every activity).
3. **Modules & videos:** choose which modules are visible, optional open and due dates, and check each video.
4. Open the student site yourself and submit one activity as a test. Then, in **Results**, use **Allow retake** to
   delete your test attempt.

## What is new compared with PHYMECH

- **Formula answers.** Many activity items ask for a formula (a derivative, an antiderivative, a general term).
  Students type it the way they would on a calculator, for example `x^2 sin(x)`, `(1/3)e^(3x) + C`,
  `ln|x+1|`, `arctan(x)`, `sqrt(1+x^2)`. Under the box the site shows how it read the answer, typeset, so typing
  mistakes are caught before submitting. A formula is marked correct when it agrees with the key at 14 sample
  points, so **every equivalent form is accepted** (`2sin x cos x` = `sin 2x`). For indefinite integrals the
  student must include `+ C`, and any answer that differs from the key by a constant is accepted.
- **Exact numbers.** Number items accept decimals (within 0.5%) or exact values such as `pi/4`, `3/8`, `2ln(3)`.
- **Problem sets.** Each part of the course has a problem set page (a link under each part on the home page and in
  the module banner). Students answer them in their notebook; they are not graded online. The answers are in your
  private `answer-key.html`.
- **Optional modules.** Modules marked *Optional* (enrichment topics) have activities that are recorded but left out
  of the "Activities Done" count and the average in the recordbook.

## Using the admin site

- **Overview:** semester status, number of students and submissions, which activities are open.
- **Semester:** dates, attempts (0 = unlimited), show correct answers after the last attempt, automatic archive.
  Before the start date students see a "semester starts on …" message. After the end date lessons can still be
  reviewed but activities are closed.
- **Block sections:** the dropdown list students choose from. Change it every semester.
- **Modules & videos:** show or hide a module, set an *opens on* date (hidden until then) and a *due on* date (last
  day the activity accepts submissions). **Edit video** changes the YouTube video, its citation, and the questions
  that pause the video. A question's *pause at* time can be seconds (`95`), minutes:seconds (`1:35`) or a
  percentage of the video (`40%`, `100%` = at the end).
- **Answer key:** change an answer or tolerance; new submissions are graded with it. Formula answers use the same
  syntax as the students, written without `+ C`.
- **Results:** every submission for a module, sorted by block section and last name. Filter by section, search,
  view each student's answers and written solutions (equations are shown rendered), set a **Final score** that
  overrides the automatic score, add **Remarks**, or **Allow retake** (deletes that attempt).
- **Recordbook:** one row per student with the best score in each module (your final score if you set one), the
  number of required activities done, the average of the required modules, and video questions answered
  correctly; sorted by block section, last name, first name. It is also written to the *Recordbook* tab of the
  Sheet, and refreshed every night.
- **Archive:** shows when the automatic archive will run (default: 7 days after the end date). Archiving saves a full
  copy of the Sheet in the Drive folder **CAL02 Archives**, then clears submissions, video answers, students and
  the recordbook. Settings, sections, modules, videos and the answer key stay, ready for the next semester.
  You can also archive manually by typing ARCHIVE.

## Course information on the student home page

The home page shows the course information, major requirements, grading system, transmutation table, references
and consultation hours from [`content/syllabus.json`](content/syllabus.json). To change them (for example a new
consultation schedule), edit that file on GitHub, then click **Refresh lesson content from GitHub** in the admin
Overview tab. The **Syllabus** button and the **Book a consultation** button use the links set in the admin
**Semester** tab.

## Updating the lessons or the code

- **Lesson text, activity questions and problem sets** are read from the `content/` folder of this repository.
  After you change a file there, click **Refresh lesson content from GitHub** on the admin Overview tab.
- **Code changes** (a new version of `Code.gs`, `Student.html`, `Admin.html` or `Styles.html`): paste the new file
  into the editor, then **Deploy → Manage deployments →** pencil **→ Version: New version → Deploy**. The URL
  stays the same. (Never use *New deployment* for an update: that makes a new URL.)

## Good to know

- **Videos:** each module embeds one free lecture with its citation (mostly MIT OpenCourseWare 18.01 Single
  Variable Calculus, Fall 2006, Prof. David Jerison, CC BY-NC-SA 4.0). The questions pause the video at 35%, 70%
  and the end, and ask about the lecture's topic. After watching a video, you may move them to exact times in
  **Modules & videos**. If YouTube is blocked on a network, students get an "open on YouTube" link and can answer
  the same questions below the player.
- **What is public:** the lesson text, figures, activity questions and problem sets in `content/` are in this
  public repository, so they are readable on GitHub. Answers, scores and student data never are: they live only in
  your Sheet, in the private `Seed.gs`, and in the private `answer-key.html`.
- **Quotas:** Apps Script handles a class of a few hundred students comfortably. If many students submit in the same
  second, each submission waits its turn (up to 25 seconds) rather than failing.
- **If a page shows "Sorry, unable to open the file at this time":** the browser is signed in to several Google
  accounts. Open the link in an Incognito window signed in only to the RTU account.
