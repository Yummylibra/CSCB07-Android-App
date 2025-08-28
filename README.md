# CSCB07 Fall 2023 – Android Student/Admin Portal

## Overview
This Android application was developed as the final project for **CSCB07: Software Design** (Fall 2023) at the University of Toronto Scarborough.  
It implements a **student/admin portal** with features such as announcements, event management, RSVP, complaints, and feedback.  
The app uses the **Model–View–Presenter (MVP)** architecture and integrates with **Firebase Authentication** and **Firebase Realtime Database**.

## Demo

 [Watch Demo Video]( https://www.youtube.com/watch?v=K81ct-dIwNg)  
 [Watch Demo Video]( https://youtube.com/shorts/h2eI4FhIVes?feature=share)  

 Note: The Firebase backend used in this project (Fall 2023) is no longer active, so live login and database operations may not work 
if you try to run the code locally.
UI features are still demonstrable through screenshots and the recorded demo.



**Prototype Navigation**


![UI Prototype](2023%20CSCB07%20project.png)

**Login Screen**


![Login Screen](b07%20login.png)

**Register Screen**


![Register Screen](B07%20register.png)


---

## Features and Implementation Details

### Authentication (Login & Registration)
- **Files:**
  - `MainActivity.java` + `activity_main.xml` → Login screen (email, password, login button).
  - `RegisterActivity.java` + `activity_register.xml` → Registration screen with input for name, email, password, and admin checkbox.
  - `User.java` → User model storing role (student/admin).  
- **Flow:**  
  The app starts at `MainActivity` (defined in `AndroidManifest.xml`:contentReference[oaicite:0]{index=0}).  
  Firebase Authentication handles login and registration; `User.java` stores user role to redirect either to `AdminOperations` or `StudentOperations`.

---

### Admin Features

1. **Admin Dashboard**
   - **Files:** `AdminOperations.java` + `activity_admin_operations.xml`
   - **Function:** Provides entry points for posting announcements, creating events, viewing events, viewing complaints, and logging out.

2. **Post Announcements**
   - **Files:** `AdminGenerateAnnouncement.java` + `admin_generate_announcement.xml`
   - **Function:** Allows admin to enter title/content and submit.  
   - **Backend:** Stored in Firebase via `Model.java`.

3. **Create Events**
   - **Files:** `AdminGenerateEvents.java` + `admin_generate_event.xml`
   - **Function:** Admin enters event name, description, and capacity.  
   - **Model:** Represented by `Event.java` object.  
   - **Backend:** Events saved to Firebase through `Model.java`.

4. **View Events & Details**
   - **Files:** 
     - List: `AdminViewEvents.java` + `admin_view_events.xml`
     - Detail: `AdminViewEventDetail.java` + `admin_view_event_detail.xml`
   - **Function:** Lists events, shows RSVP count, student comments, and average ratings.

5. **View Complaints**
   - **Files:** `AdminViewComplains.java` + `admin_view_complains.xml`
   - **Function:** Displays student-submitted complaints from Firebase.

---

### Student Features

1. **Student Dashboard**
   - **Files:** `StudentOperations.java` + `activity_student_operations.xml`
   - **Function:** Entry page with options for qualification check, viewing announcements/events, RSVP, complaints, and comments.

2. **Qualification Check**
   - **Files:** 
     - `StudentCheckQualification.java` + `activity_student_check_qualification.xml`
     - `StudentCheckQualificationQuestions.java` + `activity_student_check_qualification_questions.xml`
     - `QualificationQuestions.java` (defines survey content)
   - **Function:** Students answer survey questions to check program eligibility.

3. **Submit Complaints**
   - **Files:** `StudentGenerateComplaint.java` + `student_generate_complaint.xml`
   - **Function:** Allows students to submit complaints stored in Firebase.

4. **RSVP to Events**
   - **Files:** 
     - `StudentSignupRSVPEvent.java` + `student_signup_rsvp_event.xml`
     - `StudentViewRSVPEvents.java` + `student_view_rsvp_events.xml`
   - **Function:** Students can RSVP to events and view their registered events.

5. **View Announcements & Events**
   - **Files:** `StudentViewAnnouncementEvent.java` + `student_view_announcement_event.xml`
   - **Function:** Lists announcements and events for browsing.

6. **Comment on Events**
   - **Files:** 
     - `StudentChooseCommentEvents.java` + `student_choose_comment_events.xml`
     - `StudentCommentEvent.java` + `activity_student_comment_event.xml`
   - **Function:** Students select an event and submit feedback (rating + comment).

---

## Architecture

- **MVP Pattern**
  - **Model:** `Model.java`, `Event.java`, `PublicMessage.java`, `User.java`, `QualificationQuestions.java`
  - **View:** XML layout files (e.g., `activity_main.xml`, `admin_generate_event.xml`)
  - **Presenter:** `Presenter.java` mediates between View (Activities) and Model (Firebase).

- **Navigation:**  
  Defined in `AndroidManifest.xml`, starting from `MainActivity`:contentReference[oaicite:1]{index=1}.  
  Each Activity corresponds to a screen defined in `res/layout`.

---

## Tech Stack
- **Language:** Java (Android SDK)  
- **Frontend:** Android XML layouts  
- **Backend:** Firebase Authentication + Realtime Database  
- **Testing:** JUnit + Mockito (for Presenter logic)  
- **IDE:** Android Studio  

---

## How to Run
1. Clone the repository:
   ```bash
   git clone https://github.com/Yummylibra/CSCB07-Android-App.git
