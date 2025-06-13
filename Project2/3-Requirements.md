# 3. Requirement

## 3.1 Functions

This section details the functional requirements of CPP, starting with overall requirement, followed by requirements of each feature of the system. Figure 3.1 shows the overall use case of CPP:

### Table 3.1.1 Use Case Explanation

| **Actor**           | **Use Case**                      | **Explanation**                                                                                           |
|---------------------|-----------------------------------|-----------------------------------------------------------------------------------------------------------|
| Student             | Submit Feedback & Request         | When a student submits feedback or a request, the system shall store and forward it for review.          |
|                     | Manage Enrollment                 | When a student initiates course enrollment, the system shall validate prerequisites and schedule conflicts. |
| Student, Parent     | Access Academic Info              | When a student or parent requests academic information (grades, schedule, attendance, transcript), the system shall retrieve and display details. |
| Lecturer            | Record Attendance                 | When a lecturer marks attendance for a class, the system shall update student attendance records.         |
|                     | Input & Release Grades            | When a lecturer finalizes grades, the system shall store and release them for student access.             |
|                     | Post Announcement & Materials     | When a lecturer posts an announcement or study material, the system shall publish it to relevant users.   |
| Administrator       | Manage Student's Request          | When an administrator reviews student requests, the system shall allow approval, rejection, or modification. |
|                     | Update Billing Information        | When an administrator modifies billing details, the system shall validate and update financial records.   |
|                     | Manage Academic Calendar          | When an administrator updates the academic calendar, the system shall reflect changes and notify relevant users. |
| SMS Gateway         | Send SMS                          | When a notification requires SMS dispatch, the system shall send the message through the external SMS gateway. |

<!-- Requirement REQ_F001 -->
<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F001</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall record in log after each operation</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Seow Jiun Wen</td>
  </tr>
</table>

<br>

<!-- Requirement REQ_F002 -->
<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F002</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall send SMS messages through the integrated SMS Gateway when triggered.</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Seow Jiun Wen</td>
  </tr>
</table>

<br>

<!-- Requirement REQ_F003 -->
<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F003</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall restrict student data access based on the user role (student, parent, lecturer, administrator).</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Seow Jiun Wen</td>
  </tr>
</table>


### 3.1.1 F001 Access Academic Information
The functional requirements for Access Academic Information are as followed:

<!-- Requirement REQ_F101 -->
<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F101</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall display error message for CMS API fails or time out</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Seow Jiun Wen</td>
  </tr>
</table>

<br>

<!-- Requirement REQ_F102 -->
<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F102</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall display the academic information</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Seow Jiun Wen</td>
  </tr>
</table>

The following table (Table 3.1.2) shows the details of this feature, followed by an activity diagram that illustrate the workflow and transition of the feature.

<!-- Table 3.1.2 Use Case Specification – Access Academic Information -->
<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Use Case ID</strong></td>
    <td>UC001</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Feature</strong></td>
    <td colspan="3">Access academic info</td>
  </tr>
  <tr>
    <td><strong>Purpose</strong></td>
    <td colspan="3">Allow users to view academic-related information</td>
  </tr>
  <tr>
    <td><strong>Actor</strong></td>
    <td colspan="3">Student, Parent</td>
  </tr>
  <tr>
    <td><strong>Trigger</strong></td>
    <td colspan="3">Actor clicks the “Academic Information” option from the dashboard</td>
  </tr>
  <tr>
    <td rowspan="6"><strong>Main Flow</strong></td>
    <td>1.</td>
    <td colspan="2">Actor clicks the “Academic Information” button</td>
  </tr>
  <tr>
    <td>2.</td>
    <td colspan="2">System retrieves the student’s latest grades, class schedule, attendance summary, and transcript link via CMS API.</td>
  </tr>
  <tr>
    <td>3.</td>
    <td colspan="2">
      System compiles the data into the Academic Information page:<br>
      • Grades: list of completed courses and grades.<br>
      • Schedule: calendar view of upcoming classes.<br>
      • Attendance: summary of present/absent status per course.<br>
      • Transcript: download button for official PDF.
    </td>
  </tr>
  <tr>
    <td>4.</td>
    <td colspan="2">System displays the Academic Information page to the actor.</td>
  </tr>
  <tr>
    <td>5.</td>
    <td colspan="2">Actor views the data and may click “Download Transcript” to retrieve a PDF copy.</td>
  </tr>
  <tr>
    <td>6.</td>
    <td colspan="2">System logs the access event for auditing.</td>
  </tr>
  <tr>
    <td rowspan="2"><strong>Alternative Flow – CMS unavailable</strong></td>
    <td>2.1</td>
    <td colspan="2">CMS API fails or times out</td>
  </tr>
  <tr>
    <td>2.2</td>
    <td colspan="2">System displays an error message: “Unable to load academic information. Please try again later.”</td>
  </tr>
  <tr>
    <td rowspan="2"><strong>Alternative Flow – No transcript available</strong></td>
    <td>3.1</td>
    <td colspan="2">No student transcript record exists</td>
  </tr>
  <tr>
    <td>3.2</td>
    <td colspan="2">System replaces the Download Transcript button with:<br>“Transcript not yet available.”</td>
  </tr>
  <tr>
    <td><strong>Rules</strong></td>
    <td colspan="3">Only authenticated students or their authorized parents may view academic information. Data is shown only if available in the CMS.</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Seow Jiun Wen</td>
  </tr>
</table>

---

### 3.1.2 F002 Manage Enrollment
The functional requirements for Manage Enrollment are as followed:

<!-- Functional Requirements: Manage Enrollment -->

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F201</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall display the information of subject and classes</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Seow Jiun Wen</td>
  </tr>
</table>

<br>

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F202</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall enroll the student into the chosen class</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Seow Jiun Wen</td>
  </tr>
</table>

<br>

<!-- Table 3.1.3 Use Case Specification – Manage Enrollment -->

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Use Case ID</strong></td>
    <td>UC002</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Feature</strong></td>
    <td colspan="3">Manage Enrollment</td>
  </tr>
  <tr>
    <td><strong>Purpose</strong></td>
    <td colspan="3">Allow students to view, add, or drop course enrollments</td>
  </tr>
  <tr>
    <td><strong>Actor</strong></td>
    <td colspan="3">Student</td>
  </tr>
  <tr>
    <td><strong>Trigger</strong></td>
    <td colspan="3">Student selects “Enrollment” option from the dashboard</td>
  </tr>
  <tr>
    <td rowspan="8"><strong>Main Flow</strong></td>
    <td>1.</td>
    <td colspan="2">Actor selects the “Enrollment” option</td>
  </tr>
  <tr>
    <td>2.</td>
    <td colspan="2">System retrieves list of currently enrolled courses and available courses from CMS API</td>
  </tr>
  <tr>
    <td>3.</td>
    <td colspan="2">System displays current enrollments and available courses</td>
  </tr>
  <tr>
    <td>4.</td>
    <td colspan="2">Actor selects a course to add or drop</td>
  </tr>
  <tr>
    <td>5.</td>
    <td colspan="2">System sends request to CMS API to update enrollment</td>
  </tr>
  <tr>
    <td>6.</td>
    <td colspan="2">CMS API confirms success</td>
  </tr>
  <tr>
    <td>7.</td>
    <td colspan="2">System updates the enrollment list and displays confirmation</td>
  </tr>
  <tr>
    <td>8.</td>
    <td colspan="2">System logs the enrollment change</td>
  </tr>
  <tr>
    <td rowspan="2"><strong>Alternative Flow – CMS unavailable</strong></td>
    <td>2.1</td>
    <td colspan="2">CMS API fails or times out</td>
  </tr>
  <tr>
    <td>2.2</td>
    <td colspan="2">System displays an error message: “Unable to load academic information. Please try again later.”</td>
  </tr>
  <tr>
    <td rowspan="2"><strong>Alternative Flow – Enrollment rejected</strong></td>
    <td>5.1</td>
    <td colspan="2">CMS API returns error</td>
  </tr>
  <tr>
    <td>5.2</td>
    <td colspan="2">System displays appropriate message and does not change enrollment</td>
  </tr>
  <tr>
    <td><strong>Rules</strong></td>
    <td colspan="3">Only authenticated students can manage enrollment. Enrollment must comply with course prerequisites, schedule constraints, and max capacity.</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Seow Jiun Wen</td>
  </tr>
</table>

### 3.1.3 F003 Submit Feedback & Request
The functional requirements for Submit Feedback & Request are as followed:

<!-- Functional Requirements for Submit Feedback & Request -->

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F301</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall display a form for submitting feedback or requests</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Seow Jiun Wen</td>
  </tr>
</table>
<br>

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F302</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall allow users to select a category and input message</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Seow Jiun Wen</td>
  </tr>
</table>
<br>

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F303</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall store feedback/request in the database</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Seow Jiun Wen</td>
  </tr>
</table>
<br>

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F304</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall display a confirmation message after submission</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Seow Jiun Wen</td>
  </tr>
</table>

<br>

<!-- Table 3.1.4 Use Case Specification – Submit Feedback & Request -->

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Use Case ID</strong></td>
    <td>UC003</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Feature</strong></td>
    <td colspan="3">Submit feedback & request</td>
  </tr>
  <tr>
    <td><strong>Purpose</strong></td>
    <td colspan="3">Allow users to submit feedback or service requests to university administration</td>
  </tr>
  <tr>
    <td><strong>Actor</strong></td>
    <td colspan="3">Student</td>
  </tr>
  <tr>
    <td><strong>Trigger</strong></td>
    <td colspan="3">Student clicks “Feedback & Request” option from the dashboard</td>
  </tr>
  <tr>
    <td rowspan="7"><strong>Main Flow</strong></td>
    <td>1.</td>
    <td colspan="2">Actor selects the “Feedback & Request” option</td>
  </tr>
  <tr>
    <td>2.</td>
    <td colspan="2">System displays a form with fields: category, subject (optional), and message</td>
  </tr>
  <tr>
    <td>3.</td>
    <td colspan="2">Actor fills in the form and submits it</td>
  </tr>
  <tr>
    <td>4.</td>
    <td colspan="2">System validates the input</td>
  </tr>
  <tr>
    <td>5.</td>
    <td colspan="2">System stores the submission in the database</td>
  </tr>
  <tr>
    <td>6.</td>
    <td colspan="2">System displays a confirmation message: “Your message has been submitted.”</td>
  </tr>
  <tr>
    <td>7.</td>
    <td colspan="2">System logs the submission event for reference</td>
  </tr>
  <tr>
    <td rowspan="2"><strong>Alternative Flow – Validation failed</strong></td>
    <td>4.1</td>
    <td colspan="2">Required fields are empty or invalid</td>
  </tr>
  <tr>
    <td>4.2</td>
    <td colspan="2">System displays message: “Please complete all required fields.”</td>
  </tr>
  <tr>
    <td rowspan="2"><strong>Alternative Flow – System error</strong></td>
    <td>5.1</td>
    <td colspan="2">Database insertion fails</td>
  </tr>
  <tr>
    <td>5.2</td>
    <td colspan="2">System displays error: “Submission failed. Please try again later.”</td>
  </tr>
  <tr>
    <td><strong>Rules</strong></td>
    <td colspan="3">Feedback must include a message and category</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Seow Jiun Wen</td>
  </tr>
</table>

<!-- Functional Requirements for Submit Feedback & Request -->

### 3.1.4 F004 Record Attendance

The functional requirements for Record Attendance are as followed:

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F401</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall generate a unique, time-bound QR code for each lecture session.</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Adam Lotfi</td>
  </tr>
</table>
<br>

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F402</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall validate scanned QR codes against course schedule and expiry time.</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Adam Lotfi</td>
  </tr>
</table>
<br>

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F403</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall update attendance records in CMS after successful validation.</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Adam Lotfi</td>
  </tr>
</table>
<br>

The following table (Table 3.1.5) shows the details of this feature, followed by an activity diagram that illustrates the workflow and transition of the feature.
<!-- Table 3.1.4 Use Case Specification –  -->

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Use Case ID</strong></td>
    <td>UC004</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Feature</strong></td>
    <td colspan="3">Record Attendance</td>
  </tr>
  <tr>
    <td><strong>Purpose</strong></td>
    <td colspan="3">Enable lecturers to mark student attendance via QR code scanning.</td>
  </tr>
  <tr>
    <td><strong>Actor</strong></td>
    <td colspan="3">Lecturer</td>
  </tr>
  <tr>
    <td><strong>Trigger</strong></td>
    <td colspan="3">Lecturer Initiates an attendance session in the portal.</td>
  </tr>
  <tr>
    <td rowspan="5"><strong>Main Flow</strong></td>
    <td>1.</td>
    <td colspan="2">Lecturer clicks “Get Attendance” in the course dashboard.</td>
  </tr>
  <tr>
    <td>2.</td>
    <td colspan="2">System generates a QR code that is valid for 15 minutes.</td>
  </tr>
  <tr>
    <td>3.</td>
    <td colspan="2">Students can scan the generated QR via their phones</td>
  </tr>
  <tr>
    <td>4.</td>
    <td colspan="2">System validates the scan via course enrolment and expiry time checking.</td>
  </tr>
  <tr>
    <td>5.</td>
    <td colspan="2">System updates CMS attendance records and confirms to the lecturer. </td>
  </tr>
  
  <tr>
    <td rowspan="2"><strong>Alternative Flow – Invalid Scan</strong></td>
  </tr>
  <tr>
    <td>2.1</td>
    <td colspan="2">System displays “Invalid QR Code” and logs the attempt.</td>
  </tr>
  <tr>
    <td><strong>Rules</strong></td>
    <td colspan="3">QR codes expire 15 minutes after generation. Only enrolled students can mark attendance.</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Adam Lotfi</td>
  </tr>
</table>

### 3.1.5 F005 Input & Release Grades

The functional requirements for Input & Release Grades are as followed:

<!-- Functional Requirements: Input & Release Grades -->

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F501</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall enforce grade submission deadlines set by lecturers.</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Adam Lotfi</td>
  </tr>
</table>
<br>

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F502</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall validate grade formats</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Adam Lotfi</td>
  </tr>
</table>
<br>

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F503</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall require lecturer confirmation before releasing grades to students.</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Adam Lotfi</td>
  </tr>
</table>

<br>

<!-- Table 3.1.6 Use Case Specification – Input & Release Grades -->
The following table (Table 3.1.6) shows the details of this feature, followed by an activity diagram that illustrates the workflow and transition of the feature.

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Use Case ID</strong></td>
    <td>UC005</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Feature</strong></td>
    <td colspan="3">Input & Release Grades</td>
  </tr>
  <tr>
    <td><strong>Purpose</strong></td>
    <td colspan="3">Allow lecturers to enter, validate, and publish student grades.</td>
  </tr>
  <tr>
    <td><strong>Actor</strong></td>
    <td colspan="3">Lecturer</td>
  </tr>
  <tr>
    <td><strong>Trigger</strong></td>
    <td colspan="3">Lecturer selects "Grade Input" for a course.</td>
  </tr>
  <tr>
    <td rowspan="5"><strong>Main Flow</strong></td>
    <td>1.</td>
    <td colspan="2">Lecturer clicks “Insert Grades” in the course dashboard.</td>
  </tr>
  <tr>
    <td>2.</td>
    <td colspan="2">Lecturer uploads grades in a form entry.</td>
  </tr>
  <tr>
    <td>3.</td>
    <td colspan="2">System validates format and checks for missing entries.</td>
  </tr>
  <tr>
    <td>4.</td>
    <td colspan="2">Lecturer reviews and confirms submission.</td>
  </tr>
  <tr>
    <td>5.</td>
    <td colspan="2">Grades are locked, Admin approves submission, and grades are released to students via CPP.</td>
  </tr>
  <tr>
    <td rowspan="1"><strong>Alternative Flow – Missing Scans</strong></td>
    <td>2.1</td>
    <td colspan="2">System detects empty or malformed forms</td>
  </tr>
  <tr>
    <td><strong>Rules</strong></td>
    <td colspan="3">Grades cannot be changed after submission unless approved by admin.</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Adam Lotfi</td>
  </tr>
</table>

### 3.1.6 F006 Post Announcements & Materials

The functional requirements for Post Announcements & Materials are as followed:

<!-- Functional Requirements: Post Announcements & Materials -->

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F601</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall support file uploads up to 50MB with virus scanning.</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Adam Lotfi</td>
  </tr>
</table>
<br>

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F602</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall allow scheduling announcements for future publication.</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Adam Lotfi</td>
  </tr>
</table>
<br>

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F603</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall notify enrolled students via SMS and portal alerts for urgent posts.</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Adam Lotfi</td>
  </tr>
</table>

<br>

<!-- Table 3.1.7 Use Case Specification – Post Announcements & Materials -->

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Use Case ID</strong></td>
    <td>UC006</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Feature</strong></td>
    <td colspan="3">Post Announcements & Materials</td>
  </tr>
  <tr>
    <td><strong>Purpose</strong></td>
    <td colspan="3">Enable lecturers to share course content and announcements with students.</td>
  </tr>
  <tr>
    <td><strong>Actor</strong></td>
    <td colspan="3">Lecturer</td>
  </tr>
  <tr>
    <td><strong>Trigger</strong></td>
    <td colspan="3">Lecturer selects "New Post" for a course.</td>
  </tr>
  <tr>
    <td rowspan="7"><strong>Main Flow</strong></td>
    <td>1.</td>
    <td colspan="2">Lecturer clicks “New Post” in the course dashboard.</td>
  </tr>
  <tr>
    <td>2.</td>
    <td colspan="2">Lecturer chooses post type: Announcement or Material.</td>
  </tr>
  <tr>
    <td>3.</td>
    <td colspan="2">For Materials: lecturer uploads files with title and descriptions.</td>
  </tr>
  <tr>
    <td>4.</td>
    <td colspan="2">For Announcements: lecturer enters text.</td>
  </tr>
  <tr>
    <td>5.</td>
    <td colspan="2">Optionally, lecturer may schedule their posts.</td>
  </tr>
  <tr>
    <td>6.</td>
    <td colspan="2">System validates content, scans files for malware.</td>
  </tr>
  <tr>
    <td>7.</td>
    <td colspan="2">Post appears in feed and notifies students via SMS.</td>
  </tr>
  <tr>
    <td rowspan="2"><strong>Alternative Flow – Large File</strong></td>
    <td>5.1</td>
    <td colspan="2">File exceeds 50MB.</td>
  </tr>
  <tr>
    <td>5.2</td>
    <td colspan="2">System rejects upload with error: "Max size: 50MB. Compress or split file."</td>
  </tr>
  <tr>
    <td><strong>Rules</strong></td>
    <td colspan="3">Edited posts preserve version history for 30 days.</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Adam Lotfi</td>
  </tr>
</table>

### 3.1.7 F007 Manage Student Request

The functional requirements for Post Announcements & Materials are as followed:

<!-- Functional Requirements: Manage Student Request -->

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F701</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall display a list of pending student requests categorized by type (e.g., academic, administrative, financial).</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Karim Hamzaoui</td>
  </tr>
</table>
<br>

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F702</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall allow administrators to view detailed information for each student request.</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Karim Hamzaoui</td>
  </tr>
</table>
<br>

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F703</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall provide options to approve, reject, or modify each student request.</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Karim Hamzaoui</td>
  </tr>
</table>
<br>

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F704</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall update the status of the request in the database after administrator action.</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Karim Hamzaoui</td>
  </tr>
</table>
<br>

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F705</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall notify the student of the request outcome via SMS and portal notification.</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Karim Hamzaoui</td>
  </tr>
</table>

<br>

The following table (Table 3.1.8) shows the details of this feature, followed by an activity diagram that illustrates the workflow and transition of the feature.
<!-- Table 3.1.8 Use Case Specification – Manage Student's Request -->

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Use Case ID</strong></td>
    <td>UC007</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Feature</strong></td>
    <td colspan="3">Manage Student's Request</td>
  </tr>
  <tr>
    <td><strong>Purpose</strong></td>
    <td colspan="3">Allow administrators to process and respond to student service requests efficiently</td>
  </tr>
  <tr>
    <td><strong>Actor</strong></td>
    <td colspan="3">Administrator</td>
  </tr>
  <tr>
    <td><strong>Trigger</strong></td>
    <td colspan="3">Administrator accesses the "Student Requests" section from the dashboard</td>
  </tr>
  <tr>
    <td rowspan="7"><strong>Main Flow</strong></td>
    <td>1.</td>
    <td colspan="2">Administrator selects “Student Requests” from the dashboard</td>
  </tr>
  <tr>
    <td>2.</td>
    <td colspan="2">System displays list of pending requests retrieved from the database</td>
  </tr>
  <tr>
    <td>3.</td>
    <td colspan="2">Administrator selects a specific request to review details</td>
  </tr>
  <tr>
    <td>4.</td>
    <td colspan="2">Administrator chooses to approve, reject, or modify the request</td>
  </tr>
  <tr>
    <td>5.</td>
    <td colspan="2">System updates the request status accordingly in the CMS</td>
  </tr>
  <tr>
    <td>6.</td>
    <td colspan="2">System sends SMS and portal alert to student about the decision</td>
  </tr>
  <tr>
    <td>7.</td>
    <td colspan="2">System logs the action and updates the request history</td>
  </tr>
  <tr>
    <td rowspan="1"><strong>Alternative Flow – No Request Found</strong></td>
    <td>2.1</td>
    <td colspan="2">System displays message: “No pending requests.”</td>
  </tr>
  <tr>
    <td rowspan="2"><strong>Alternative Flow – Database Error</strong></td>
    <td>5.1</td>
    <td colspan="2">If CMS update fails, system displays error: “Unable to update request status. Try again later.”</td>
  </tr>
  <tr>
    <td><strong>Rules</strong></td>
    <td colspan="3">Only authenticated administrators can manage student requests.</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Karim Hamzaoui</td>
  </tr>
</table>

### 3.1.8 F008 Update Billing Information

The functional requirements for Post Announcements & Materials are as followed:

<!-- Functional Requirements: Update Billing Information -->

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F801</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall allow administrators to search and view individual student billing records.</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Karim Hamzaoui</td>
  </tr>
</table>
<br>

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F802</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall allow administrators to modify tuition fees, penalties, and discounts.</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Karim Hamzaoui</td>
  </tr>
</table>
<br>

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F803</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall validate changes before updating records.</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Karim Hamzaoui</td>
  </tr>
</table>
<br>

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F804</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall update financial records in the CMS upon confirmation.</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Karim Hamzaoui</td>
  </tr>
</table>
<br>

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F805</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall send confirmation via SMS and portal notification to the affected student.</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Karim Hamzaoui</td>
  </tr>
</table>

<br>

The following table (Table 3.1.9) shows the details of this feature, followed by an activity diagram that illustrates the workflow and transition of the feature.

<!-- Table 3.1.9 Use Case Specification – Update Billing Information -->

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Use Case ID</strong></td>
    <td>UC008</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Feature</strong></td>
    <td colspan="3">Update Billing Information</td>
  </tr>
  <tr>
    <td><strong>Purpose</strong></td>
    <td colspan="3">Allow administrators to update a student’s financial records securely and accurately</td>
  </tr>
  <tr>
    <td><strong>Actor</strong></td>
    <td colspan="3">Administrator</td>
  </tr>
  <tr>
    <td><strong>Trigger</strong></td>
    <td colspan="3">Administrator accesses the "Billing Management" section from the dashboard</td>
  </tr>
  <tr>
    <td rowspan="9"><strong>Main Flow</strong></td>
    <td>1.</td>
    <td colspan="2">Administrator selects “Billing Management” from the dashboard</td>
  </tr>
  <tr>
    <td>2.</td>
    <td colspan="2">System displays a search interface to locate student billing records</td>
  </tr>
  <tr>
    <td>3.</td>
    <td colspan="2">Administrator selects a student and views current billing info</td>
  </tr>
  <tr>
    <td>4.</td>
    <td colspan="2">Administrator edits applicable fields (tuition, fees, discounts)</td>
  </tr>
  <tr>
    <td>5.</td>
    <td colspan="2">System validates the input against billing rules and constraints</td>
  </tr>
  <tr>
    <td>6.</td>
    <td colspan="2">On successful validation, system updates CMS financial records</td>
  </tr>
  <tr>
    <td>7.</td>
    <td colspan="2">System displays a confirmation message to the administrator</td>
  </tr>
  <tr>
    <td>8.</td>
    <td colspan="2">System sends SMS and portal notification to student</td>
  </tr>
  <tr>
    <td>9.</td>
    <td colspan="2">System logs the transaction for audit purposes</td>
  </tr>
  <tr>
    <td rowspan="2"><strong>Alternative Flow – Validation Failed</strong></td>
    <td>5.1</td>
    <td colspan="2">If validation fails, system shows error: “Invalid input. Please check values.”</td>
  </tr>
  <tr>
    <td rowspan="2"><strong>Alternative Flow – CMS Error</strong></td>
    <td>6.1</td>
    <td colspan="2">If CMS update fails, system shows: “Billing update failed. Please retry.”</td>
  </tr>
  <tr>
    <td><strong>Rules</strong></td>
    <td colspan="3">Only authenticated administrators can access and modify billing data</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Karim Hamzaoui</td>
  </tr>
</table>

### 3.1.9 F009 Manage Academic Calendar

The functional requirements for Post Announcements & Materials are as followed:

<!-- Functional Requirements: Manage Academic Calendar -->

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F901</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall display the current academic calendar with semester events and holidays.</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Karim Hamzaoui</td>
  </tr>
</table>
<br>

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F902</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall allow administrators to add, edit, or remove calendar events.</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Karim Hamzaoui</td>
  </tr>
</table>
<br>

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F903</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall validate event dates to prevent conflicts or past scheduling.</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Karim Hamzaoui</td>
  </tr>
</table>
<br>

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F904</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall update the CMS and CPP portal upon successful changes.</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Karim Hamzaoui</td>
  </tr>
</table>
<br>

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Requirement ID</strong></td>
    <td>REQ_F905</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Description</strong></td>
    <td colspan="3">System shall notify students and lecturers of relevant calendar updates via SMS and portal alerts.</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Karim Hamzaoui</td>
  </tr>
</table>

<br>

The following table (Table 3.1.10) shows the details of this feature, followed by an activity diagram that illustrates the workflow and transition of the feature.
<!-- Table 3.1.10 Use Case Specification – Manage Academic Calendar -->

<table border="1" cellspacing="0" cellpadding="5">
  <tr>
    <td><strong>Use Case ID</strong></td>
    <td>UC009</td>
    <td><strong>Version</strong></td>
    <td>1.0</td>
  </tr>
  <tr>
    <td><strong>Feature</strong></td>
    <td colspan="3">Manage Academic Calendar</td>
  </tr>
  <tr>
    <td><strong>Purpose</strong></td>
    <td colspan="3">Allow administrators to update and broadcast the academic calendar</td>
  </tr>
  <tr>
    <td><strong>Actor</strong></td>
    <td colspan="3">Administrator</td>
  </tr>
  <tr>
    <td><strong>Trigger</strong></td>
    <td colspan="3">Administrator accesses the "Academic Calendar" section from the dashboard</td>
  </tr>
  <tr>
    <td rowspan="9"><strong>Main Flow</strong></td>
    <td>1.</td>
    <td colspan="2">Administrator selects “Academic Calendar” from the dashboard</td>
  </tr>
  <tr>
    <td>2.</td>
    <td colspan="2">System displays current calendar with events and dates</td>
  </tr>
  <tr>
    <td>3.</td>
    <td colspan="2">Administrator selects option to add, edit, or remove an event</td>
  </tr>
  <tr>
    <td>4.</td>
    <td colspan="2">Administrator fills in or updates event details (e.g., title, date, description)</td>
  </tr>
  <tr>
    <td>5.</td>
    <td colspan="2">System validates event timing for conflicts or invalid entries</td>
  </tr>
  <tr>
    <td>6.</td>
    <td colspan="2">System updates calendar data in CMS and CPP</td>
  </tr>
  <tr>
    <td>7.</td>
    <td colspan="2">System shows confirmation to administrator</td>
  </tr>
  <tr>
    <td>8.</td>
    <td colspan="2">System sends SMS and portal notification to relevant users (students, lecturers)</td>
  </tr>
  <tr>
    <td>9.</td>
    <td colspan="2">System logs update for audit trail</td>
  </tr>
  <tr>
    <td rowspan="2"><strong>Alternative Flow – Invalid Input</strong></td>
    <td>5.1</td>
    <td colspan="2">System displays: “Invalid event date or missing details. Please correct and try again.”</td>
  </tr>
  <tr>
    <td rowspan="1"><strong>Alternative Flow – CMS Error</strong></td>
    <td>6.1</td>
    <td colspan="2">System displays: “Calendar update failed. Please retry.”</td>
  </tr>
  <tr>
    <td><strong>Rules</strong></td>
    <td colspan="3">All changes are logged with timestamps and user credentials</td>
  </tr>
  <tr>
    <td><strong>Author</strong></td>
    <td colspan="3">Karim Hamzaoui</td>
  </tr>
</table>

--------
## 3.2 Performance Requirements

**Table 3.2.1 Performance Requirements**

| **Requirement ID** | **Description**                                                                 | **Priority** | **Author**       |
|--------------------|----------------------------------------------------------------------------------|--------------|------------------|
| PERF_001           | The system shall respond to dashboard navigation requests within 2 seconds.     | High         | Seow Jiun Wen    |
| PERF_002           | The system shall support up to 500 concurrent users.                             | Medium       | Seow Jiun Wen    |
| PERF_003           | The system shall store feedback submissions within 1.5 seconds.                  | Medium       | Seow Jiun Wen    |
| PERF_004           | The system shall maintain at least 99.5% uptime per month.                       | High         | Seow Jiun Wen    |
| PERF_005           | The system shall display class schedule updates within 5 seconds of CMS change. | Medium       | Seow Jiun Wen    |

---

## 3.3 Usability Requirements

The usability requirements for CPP are as follow:

**Table 3.3.1 Usability Requirements**

| **Req. ID**  | **Description**                                                                                             | **Priority** | **Author**       |
|--------------|-------------------------------------------------------------------------------------------------------------|--------------|------------------|
| USAB_001     | The interface shall allow users to complete any primary task (e.g., view grades, enroll in a course) within 3 clicks. | High         | Seow Jiun Wen    |
| USAB_002     | The portal shall maintain a maximum error rate of 1% on form submissions (e.g., enrollment, feedback).       | High         | Seow Jiun Wen    |
| USAB_003     | The average page load indicator (e.g., spinner or progress bar) shall appear within 0.5 seconds.             | Medium       | Seow Jiun Wen    |

---

## 3.4 Interface Requirements

### 3.4.1 System Interface

**Table 3.4.1 System Interface**

| **External System**        | **Description**                                                                                     |
|---------------------------|-----------------------------------------------------------------------------------------------------|
| Campus Management System (CLiC) | Fetches and updates student profiles, enrollments, grades, attendance, billing.              |
| Learning Management System (eBwise) | Retrieves course rosters, announcements, and study materials.                          |
| SMS Gateway               | Sends real-time SMS alerts (attendance warnings, fee reminders).                                   |
| Email Service             | Sends e-mail notifications for announcements, confirmations, and support.                          |

---

### 3.4.2 User Interface

**Table 3.4.2 User Interface**

| **Req. ID**   | **Description**                                                                                                                                           | **Priority** | **Author**       |
|---------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------|------------------|
| REQ_UI001     | Fixed top navigation bar with institution logo, role-based menu, and user profile link; adapts to desktop, tablet, and mobile screens.                   | High         | Seow Jiun Wen    |
| REQ_UI002     | Customizable widgets for each user type (Student, Lecturer, Parent, Administrator) showing relevant metrics and shortcuts.                                | High         | Seow Jiun Wen    |
| REQ_UI003     | A bell icon or inbox area showing unread portal alerts (grade releases, announcements, reminders).                                                        | Medium       | Seow Jiun Wen    |
| REQ_UI004     | Search box in header for quick lookup of courses, records, and announcements; breadcrumb trails and tabs for easy section switching.                      | High         | Seow Jiun Wen    |
| REQ_UI005     | Hoverable “?” icons next to complex fields or features, offering inline guidance without leaving the page.                                                | Medium       | Seow Jiun Wen    |

---

### 3.4.3 Software Interface

**Table 3.4.3 Software Interface**

| **Software / API**  | **Purpose**                                      |
|---------------------|--------------------------------------------------|
| CLiC CMS API        | CRUD operations on academic and billing data     |
| eBwise LMS API      | Sync course content and retrieve announcements   |
| SMS Gateway HTTP API| Dispatch SMS notifications                       |
| Email Service API   | Send automated emails                            |


### 3.4.4 Communication interface

- HTTPS/TLS : All browser–portal and portal–service traffic must be encrypted.
- REST/JSON: Standard message format for all API calls to CMS, LMS, and SMS Gateway.
- WebSocket : Realtime in portal notifications to connected clients.

## 3.5.	Logical database requirements


## 3.6. Design constraints

The system design will adhere to the following constraints and limitations:

**Table 3.6.1 Design Constraints**

| **Constraint ID** | **Description**                                                                                                                                                      |
|-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| DC-001            | Technology stack must use Node.js 18+ (backend), React 18+ (frontend), PostgreSQL for storage, Redis for caching, and Docker/Kubernetes on Linux.                   |
| DC-002            | User authentication must be handled by the university’s single-sign-on (SAML/OpenID Connect); no custom login modules.                                               |
| DC-003            | All client–server and server–service communications must use HTTPS/TLS.                                                                                              |
| DC-004            | Role-Based Access Control (RBAC) policies defined by the university must be enforced at every API endpoint.                                                          |
| DC-005            | The system must support at least 500 concurrent users with dashboard actions completing within 2 seconds and academic pages within 3 seconds.                       |
| DC-006            | Architecture must be stateless microservices to enable horizontal scaling; database must support read replicas for reporting.                                       |
| DC-007            | The portal must comply with Malaysia’s PDPA for data privacy and meet WCAG 2.1 AA accessibility standards.                                                           |
| DC-008            | SMS notifications must be sent via the existing SMS Gateway’s HTTP API without bypassing that service.                                                               |

---

## 3.7 Software System Attributes

**Table 3.7.1 Software System Attributes**

| **Attribute**   | **Requirement**                                                                                                                                         |
|----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| Reliability    | Automatic failover within 1 minute of any service disruption; target uptime ≥ 99.9%.                                                                    |
| Availability   | Available 24×7 (except planned maintenance with 48 h notice); supports ≥ 500 concurrent users with no degradation.                                      |
| Security       | Authentication via campus SSO (with optional 2FA); RBAC enforced; all data encrypted in transit (HTTPS/TLS) and at rest.                                |
| Maintainability| Modular codebase with CI/CD pipelines, automated tests, and monthly code reviews; fully documented APIs and modules.                                    |
| Portability    | Deployable on both Linux and Windows server environments without additional configuration; client runs on modern browsers.                              |
| Scalability    | Stateless services with horizontal scaling under Kubernetes; database supports read-replicas and auto-scaling for peak loads.                           |
| Usability      | Compliant with WCAG 2.1 AA; users complete primary tasks in ≤ 3 clicks; contextual help and onboarding guides provided.                                 |

---

## 3.8 Supporting Information

**Tools and Methodologies Used**  
- **Kano Model**: Utilized in requirements elicitation to categorize and prioritize features into dissatisfiers, satisfiers, and delighters.











