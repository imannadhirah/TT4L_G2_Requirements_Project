# 4. Verification

## 4.1 Verification Approach

**Table 4.1 Verification Approach**

| **Aspect** | **Details**                                                                                                    |
|------------|-----------------------------------------------------------------------------------------------------------------|
| How        | • Test each module on its own  <br> • Test connections between portal and CMS, SMS service, and LMS  <br> • Test the whole system using each use case  <br> • Test speed and user load |
| Who        | • Development team  <br> • Quality assurance (QA) department                                                    |
| When       | • Performance and usability tests run before each major release                                                 |
| Where      | • QA testing environment that matches production                                                                |

## 4.2 Verification Criteria

**Table 4.2.1 Verification Criteria**

| **Criterion ID** | **Description**                                                                                         | **Reference**                  |
|------------------|----------------------------------------------------------------------------------------------------------|--------------------------------|
| VC001            | Dashboard pages load within 2 seconds under normal load.                                                | PERF_001                       |
| VC002            | Academic information page loads within 3 seconds under normal load.                                     | PERF_002                       |
| VC003            | System supports 500 concurrent users without errors or significant slowdown.                            | PERF_003                       |
| VC004            | Enrollment and feedback forms submit successfully at least 99% of the time under normal load.           | USAB_004 / REQ_F301–304       |
| VC005            | SMS alerts are delivered to the SMS gateway in 100% of tested cases.                                    | REQ_F304                       |
| VC006            | Primary tasks (e.g., view grades, enroll course) can be completed in no more than 3 clicks.             | USAB_001                       |

---

