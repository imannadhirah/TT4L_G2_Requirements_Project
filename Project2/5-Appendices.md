# 5. Appendices

## 5.1 Assumptions and Dependencies

**Table 5.1.1 Assumptions and Dependencies**

| **ID** | **Assumption / Dependency** | **Description**                                                                                                 |
|--------|-----------------------------|-----------------------------------------------------------------------------------------------------------------|
| A1     | CMS Availability            | Campus Management System API must be online and return accurate student, course, attendance, and billing data. |
| A2     | LMS Integration             | Learning Management System must provide a stable REST API for course rosters and materials.                    |
| A3     | SMS Service                 | Third party SMS gateway must be operational to send text alerts reliably.                                      |
| A4     | Modern Browsers             | Users will access the portal using up to date browsers (Chrome, Firefox, Edge, Safari) with HTML5/JavaScript support. |
| A5     | Internet Connection         | End users need a minimum 3 Mbps network connection for acceptable performance.                                 |
| A6     | Pre-Provisioned Accounts    | Student, lecturer, parent, and administrator accounts must exist in the CMS prior to use.                      |
| A7     | Camera Support              | Devices used for attendance must have a working camera and browser access to scan QR codes.                    |

---

## 5.2 Acronyms and Abbreviations

| **Term** | **Definition**                    |
|----------|-----------------------------------|
| CPP      | CampusPulse Portal                |
| SMS      | Short Message Service             |
| API      | Application Programming Interface |
| CMS      | Campus Management System          |
| LMS      | Learning Management System        |

---

## 5.3 Glossary

**Table 5.3.1 Glossaries**

| **Term** | **Definition** | **Synonyms** | **Related Terms** | **Examples** |
|----------|----------------|--------------|-------------------|--------------|
| CPP      | CampusPulse Portal, the unified web interface for student, lecturer, parent, and administrator interactions with the Campus Management System. | Campus Portal | CMS Front End, University Portal | A student logs into the CPP to view grades and submit feedback. |
| SMS      | Short Message Service, a text messaging service component of most telephone, internet, and mobile device systems. | Text Message | Push Notification, Email Alert | An SMS alert reminding a student of an upcoming deadline. |
| API      | Application Programming Interface, a set of rules and protocols for building and interacting with software applications. | Endpoint, Service Interface | REST API, JSON API | The CPP calls the CMS API to fetch a student’s transcript data. |
| CMS      | Campus Management System, the central database and service layer that stores student records, grades, attendance logs, and billing information. | Student Information System (SIS) | ERP, Academic Records System | When a lecturer inputs grades in the CPP, those grades are saved back to the CMS. |
| LMS      | Learning Management System, a software application for the administration, documentation, tracking, and delivery of educational courses and materials. | Course Management System | eLearning Platform, Virtual Classroom | CPP synchronizes course rosters with the LMS before a semester begins. |
