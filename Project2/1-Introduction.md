# 1. Introduction
## 1.1 Purpose
The purpose of CampusPulse Portal (CPP) is to centralize academic and administrative information, enhance communication among students, lecturers, administrators, and parents, and ensure timely delivery of critical updates through SMS notifications.

## 1.2 Scope

The CPP will:

- Provide a web-based interface for students, parents, lecturers, and administrators.
- Allow secure access to academic records, attendance, schedules, transcripts, and billing details.
- Support student actions such as enrollment, feedback submission, and academic tracking.
- Enable lecturers to record attendance, input grades, and share materials and announcements.
- Allow administrators to manage enrollments, billing, calendar updates, and student requests.
- Integrate with the CMS for real-time academic and administrative data, and the SMS Gateway to send alerts.

## 1.3 Product Overview

The CPP is a centralized, web-based front end that unifies the university’s academic, administrative, and communication services. Through a single sign-on (SSO) interface, CPP allows students and parents to view grades, schedules, attendance records, and billing information; enables students to enroll in courses and submit feedback; empowers lecturers to record attendance, release grades, and post course materials; and provides administrators with tools to manage student requests, billing, and the academic calendar. By surfacing data from the existing CMS and Learning Management System (LMS), and by dispatching SMS alerts via an external gateway, CPP streamlines workflows and improves transparency without altering any underlying back-end services.

### 1.3.1 Product perspective

CPP operates as the user-facing module in the campus’s digital ecosystem. It sits atop the core CMS, the master repository for student records and financial data—and pulls course content from the LMS. For timely communication, CPP invokes a third-party SMS Gateway to send reminders and alerts. Authentication is managed by the university’s centralized Identity Provider. From the end-user’s standpoint, all these integrations are invisible, the portal presents a consistent, role-based dashboard that hides the complexity of disparate systems and delivers a seamless experience across desktop and mobile browsers.

### 1.3.2 Product Functions

**Table 1.1 Product Functions**

| **Function**                          | **Features**                                                                                                                                           |
|--------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| User Authentication and Profile Management | - Secure login for all user roles  <br> - Profile viewing and updating capabilities  <br> - Role-specific dashboards with relevant information         |
| Academic Information Management      | - Course enrollment and registration  <br> - Grade viewing and reporting  <br> - Attendance tracking through QR code scanning  <br> - Academic calendar access  <br> - Transcript downloading |
| Financial Services                   | - Tuition fee payment processing  <br> - Billing information updates and history  <br> - Payment reminders and confirmations                          |
| Communication Functions              | - SMS notifications for critical updates  <br> - Announcements from lecturers and administration  <br> - Support request submission and tracking  <br> - Parent-lecturer communication channel |
| Administrative Functions             | - Student request approval workflow  <br> - Grade input and release management  <br> - Attendance recording and monitoring  <br> - System-wide announcements creation |

---

### 1.3.3 User Characteristics

**Table 1.2 User Characteristics**

| **User Type**    | **Characteristics**                                                                                                                                   |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| Students         | - Primary users with frequent access needs  <br> - Need access to academic records, schedules, and payment information  <br> - Require timely notifications about classes, grades, and administrative updates  <br> - Access the system predominantly through mobile devices and personal computers |
| Lecturers        | - Regular users focused on academic and administrative functions  <br> - Need efficient tools to manage classes, attendance, and grades  <br> - Require capabilities to communicate with students and administrators  <br> - Access the system primarily through desktop computers and tablets |
| Parents          | - Occasional users focused on monitoring student performance  <br> - Need simple interfaces to access grades, attendance records, and payment information  <br> - Require timely notifications about student performance and administrative matters  <br> - May access the system through various devices including mobile phones |
| Administrators   | - Power users with system management responsibilities  <br> - Need comprehensive access to manage student records, billing, and system settings  <br> - Require tools to generate reports and respond to user requests  <br> - Access the system predominantly through desktop workstations |

### 1.3.4 Limitations

### 1.3.4 Limitations

**Table 1.3 Limitations**

| **Limitation**               | **Details**                                                                                                                                                          |
|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Technical Limitations**   | • The portal requires internet connectivity for all operations  <br> • System performance depends on the scalability of the underlying Campus Management System <br> • SMS notifications are limited by the capacity and reliability of the third-party SMS gateway <br> • Real-time synchronization between integrated systems may experience latency during peak usage periods |
| **Functional Limitations**  | • The system does not replace face-to-face communications for complex issues <br> • Bulk uploads for grades and attendance require specific formatting and validation <br> • Payment processing is dependent on integration with external payment processors <br> • Document management capabilities are limited to academic transcripts and study materials |
| **User Access Limitations** | • Users must maintain updated contact information for SMS notifications to function properly <br> • Mobile app functionality may be limited compared to the web interface <br> • Concurrent user capacity depends on server infrastructure and may require scaling during peak periods <br> • Offline functionality is limited to previously cached information |
| **Security and Compliance Limitations** | • Data retention policies must comply with educational privacy regulations <br> • Cross-border data transfer may be subject to regional privacy laws <br> • User authentication relies on standard username/password protocols with optional two-factor authentication <br> • System access is restricted to university network or VPN for certain administrative functions |


### 1.4 Definitions

| **Term**              | **Definition**                                                                                                                                      |
|-----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
| Academic Information  | Refers to details about a student’s learning records, such as the courses they take, the grades they receive, their attendance, and academic status. |
| Attendance            | The record of whether a student is present or absent during a scheduled class or academic session.                                                 |
| Dashboard             | The main page or interface where a user can see important information and access features like attendance, notifications, and personal updates.     |
| User                  | Anyone who uses the portal, including students, parents, lecturers, and administrators.                                                             |
| QR Code               | A type of barcode that can be scanned using a phone or device. In this portal, QR codes are used to mark attendance or access specific services quickly. |

---