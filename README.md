# lms_web_platform
# NordWest LMS — Akademia
### Learning Management System · NordWest Business School

---

> **"Becoming the most digital private university in Germany."**
> This repository documents and delivers the full product development lifecycle for NordWest University's new Learning Management System, built around the four lecturer lifecycle stages: **meetMyStudent → teachMyStudent → testMyStudent → gradeMyStudent**.

---

## Table of Contents

1. [Project Overview](#1-project-overview)
2. [Stakeholder Analysis](#2-stakeholder-analysis)
3. [Requirement Engineering](#3-requirement-engineering)
   - 3.1 [Functional Requirements](#31-functional-requirements)
   - 3.2 [Non-Functional Requirements](#32-non-functional-requirements)
   - 3.3 [Business Rules](#33-business-rules)
   - 3.4 [AI-Powered Features](#34-ai-powered-features)
4. [User Story Mapping](#4-user-story-mapping)
5. [Product Vision & Roadmap](#5-product-vision--roadmap)
6. [To-Be Concept (UML / System Design)](#6-to-be-concept-uml--system-design)
7. [Scrum Team & Ceremonies](#7-scrum-team--ceremonies)
8. [Release Plan & Versioning](#8-release-plan--versioning)
9. [Product Prototype](#9-product-prototype)
10. [Technology Stack](#10-technology-stack)
11. [Getting Started](#11-getting-started)
12. [Folder Structure](#12-folder-structure)
13. [Contributing](#13-contributing)
14. [License](#14-license)

---

## 1. Project Overview

NordWest Business School is executing a digital transformation strategy centred on reimagining the academic experience for both lecturers and students. The **Akademia LMS** is the cornerstone of this initiative — a modern, AI-augmented learning management system designed to support the full **Lecturer Lifetime Journey**.

### The Four Lifecycle Stages

| Stage | Label | Core Purpose |
|---|---|---|
| 1 | **meetMyStudent** | Student management, registration, task assignment, Teams integration |
| 2 | **teachMyStudent** | Content upload, course materials, AI-generated study resources |
| 3 | **testMyStudent** | Exam creation, question banks, eligibility filtering, AI auto-marking |
| 4 | **gradeMyStudent** | Result review, AI essay assessment, grade publishing, student notification |

### Design Variants
The system ships in two UI tiers, selectable via a toggle in the interface:

- **Standard** — Clean, card-based UI built with Tailwind CSS. Optimised for lecturers who are less familiar with digital tools.
- **Advanced (Akademia)** — Dense, data-rich interface with full sidebar navigation, animated background effects, and extended AI features for power users.

---

## 2. Stakeholder Analysis

### Stakeholder Table

| Stakeholder | Role | Interest | Influence | Priority |
|---|---|---|---|---|
| **Lecturers** | Primary Users | Upload content, manage students, create exams, publish grades | High | 🔴 Critical |
| **Students** | End Users (Portal) | Access materials, submit work, view results | High | 🔴 Critical |
| **University Administration** | Sponsor / Governance | Digital transformation KPIs, compliance, data governance | High | 🔴 Critical |
| **IT Department** | Technical Owner | Infrastructure, security, integrations (Teams, SSO) | High | 🟠 High |
| **Product Owner (PO)** | Strategic Direction | Feature prioritisation, stakeholder alignment | High | 🟠 High |
| **Scrum Master** | Process Facilitation | Sprint ceremonies, impediment removal | Medium | 🟡 Medium |
| **Development Team** | Delivery | Implementation, code quality, testing | Medium | 🟡 Medium |
| **External Exam Bodies** | Compliance | Grade accuracy, academic integrity standards | Medium | 🟡 Medium |
| **Microsoft (Teams)** | Technology Partner | Blended learning integration | Low | 🟢 Low |
| **Legal / GDPR Officer** | Regulatory | Data privacy, GDPR compliance for student data | High | 🔴 Critical |

### Stakeholder Prioritisation Matrix

```
HIGH INFLUENCE
      │
      │  IT Dept        Administration
      │  Legal/GDPR     Lecturers
      │                 Students (portal)
      │─────────────────────────────────
      │  Dev Team       Product Owner
      │  Scrum Master   Exam Bodies
LOW   │  Microsoft
      └──────────────────────────────────
         LOW INTEREST        HIGH INTEREST
```

---

## 3. Requirement Engineering

### Elicitation Techniques Used

- **Stakeholder Interviews** — Sessions with representative lecturers across faculties
- **Document Analysis** — Review of the business brief, existing LMS data flows, and the provided UI prototype
- **Observation / Job Shadowing** — Observation of lecturer workflows during a typical semester week
- **Prototyping / Wireframing** — Interactive HTML/CSS prototype (see Section 9)
- **User Story Workshops** — Collaborative mapping sessions with lecturers and PO

---

### 3.1 Functional Requirements

#### FR-01 · Dashboard & Navigation

| ID | Requirement |
|---|---|
| FR-01.1 | The system shall display a personalised dashboard greeting the lecturer by name upon login. |
| FR-01.2 | The dashboard shall show all active courses with progress indicators. |
| FR-01.3 | The system shall display today's schedule (lectures, seminars, office hours). |
| FR-01.4 | Quick-access buttons shall be available for: Create Assignment, Grade Submissions, Upload Materials, New Exam Draft. |
| FR-01.5 | The lecturer shall be able to switch between Lecturer and Student portal views. |
| FR-01.6 | An action-required panel shall highlight pending deadlines and notifications. |

#### FR-02 · meetMyStudent — Student Management

| ID | Requirement |
|---|---|
| FR-02.1 | The system shall display a student overview showing: name, student ID, course, semester level, number of attempts, and project assignment status. |
| FR-02.2 | Lecturers shall be able to filter students by course, semester, student ID, and attempt count. |
| FR-02.3 | Lecturers shall be able to send bulk or individual reminder notifications to students. |
| FR-02.4 | The system shall support carry-over exam registration reminders for eligible students. |
| FR-02.5 | Lecturers shall be able to activate a Microsoft Teams virtual class session from within the LMS. |
| FR-02.6 | The system shall display a mini-calendar with all relevant deadlines and events. |
| FR-02.7 | A weekly timetable view shall be available for schedule planning. |

#### FR-03 · teachMyStudent — Materials Management

| ID | Requirement |
|---|---|
| FR-03.1 | Lecturers shall be able to upload teaching materials in formats: PDF, PPTX, DOCX, MP4, MP3, external links, and glossaries. |
| FR-03.2 | Each course shall support a dedicated course description section with avatar, course name, and description text. |
| FR-03.3 | The slide-set section shall display: file title, upload date, file type badge, and action buttons (edit, delete, download). |
| FR-03.4 | A drag-and-drop file upload zone shall be provided. |
| FR-03.5 | External links shall be supported as a material type alongside uploaded files. |
| FR-03.6 | Blended learning attendance statistics shall be visible (average attendance %, coursework pass count). |

#### FR-04 · testMyStudent — Exam & Question Management

| ID | Requirement |
|---|---|
| FR-04.1 | Lecturers shall be able to create exam questions of the following types: Multiple Choice (MCQ), Essay, Yes/No, and Mathematical. |
| FR-04.2 | Each question shall have a configurable mark/point allocation. |
| FR-04.3 | For MCQ and Yes/No questions, lecturers shall enter correct answers in advance to activate automatic marking. |
| FR-04.4 | Lecturers shall be able to edit and preview questions before publishing an exam. |
| FR-04.5 | A student eligibility filter shall allow filtering by: course, semester, student ID, attempt count, and blended learning completion. |
| FR-04.6 | Students must have passed all coursework to be eligible for an exam. |
| FR-04.7 | The system shall display eligible vs total student count based on active filters. |
| FR-04.8 | A live preview of the exam (student view) shall be accessible before publishing. |
| FR-04.9 | Exam scheduling shall include: exam title, course, date/time, and duration. |

#### FR-05 · gradeMyStudent — Results & Publishing

| ID | Requirement |
|---|---|
| FR-05.1 | Lecturers shall be able to view all student submissions for a given exam. |
| FR-05.2 | The gradebook shall display: student name, student ID, MCQ score, essay score, total score, grade letter, and publication status. |
| FR-05.3 | Lecturers shall be able to individually or bulk-publish results. |
| FR-05.4 | Upon publishing, students shall receive an automatic email notification. |
| FR-05.5 | Students shall be able to view published results via the student portal. |
| FR-05.6 | A grade distribution panel shall show the breakdown of A, B, C, D, F grades. |
| FR-05.7 | Summary statistics shall be shown: total enrolled, pass rate, class average, pending to publish. |
| FR-05.8 | Results in "Draft" state shall not be visible to students. |

---

### 3.2 Non-Functional Requirements

| ID | Category | Requirement |
|---|---|---|
| NFR-01 | **Performance** | Page load time shall not exceed 2 seconds on a standard university network (100Mbps). |
| NFR-02 | **Availability** | The system shall maintain 99.5% uptime during teaching semesters. |
| NFR-03 | **Scalability** | The system shall support up to 10,000 concurrent users without degradation. |
| NFR-04 | **Security** | All data transmissions shall be encrypted using TLS 1.3 or higher. |
| NFR-05 | **Security** | Authentication shall support Single Sign-On (SSO) via the university's identity provider. |
| NFR-06 | **Privacy / GDPR** | Student personal data shall be processed in compliance with EU GDPR. Data shall be stored within EU jurisdictions only. |
| NFR-07 | **Usability** | The interface shall be usable by lecturers with low digital literacy, with an average task completion time under 3 minutes for core workflows. |
| NFR-08 | **Accessibility** | The interface shall conform to WCAG 2.1 Level AA standards. |
| NFR-09 | **Responsiveness** | The UI shall be fully functional on desktop (1280px+), tablet (768px+), and mobile (375px+). |
| NFR-10 | **Integration** | The system shall integrate with Microsoft Teams for virtual class functionality. |
| NFR-11 | **Maintainability** | The codebase shall maintain a test coverage of ≥ 80% for all core modules. |
| NFR-12 | **Internationalisation** | The system shall support English and German languages in the UI. |
| NFR-13 | **Data Retention** | Exam results and student records shall be retained for a minimum of 10 years per academic regulations. |
| NFR-14 | **Audit Logging** | All grade changes and exam publications shall be logged with timestamp and actor ID. |

---

### 3.3 Business Rules

| ID | Rule |
|---|---|
| BR-01 | A student may not sit an exam if they have not passed all blended learning coursework for that course. |
| BR-02 | A student is limited to a maximum of 3 exam attempts per course per academic year. |
| BR-03 | A grade may only be published by a lecturer; automated systems may draft but not publish grades. |
| BR-04 | Exam results in "Draft" status are invisible to students and the student portal. |
| BR-05 | All AI-assessed essay scores must be reviewed and confirmed by the lecturer before publication. |
| BR-06 | Student ID format must follow the pattern: `NW-[YEAR]-[4-digit number]` (e.g., NW-2023-4412). |
| BR-07 | Carry-over exam registrations must be managed separately from first-attempt registrations. |
| BR-08 | A lecturer can only manage students and courses assigned to them by the university administration. |
| BR-09 | File uploads are limited to 500MB per file and 5GB per course. |
| BR-10 | Exam papers must be published (made visible to students) at least 30 minutes before the scheduled exam start time. |

---

### 3.4 AI-Powered Features

These features were identified through stakeholder workshops and the business brief and are integrated as **Advanced-tier** additions:

| ID | Feature | Stage | Description |
|---|---|---|---|
| AI-01 | **AI Study Guide Generator** | teachMyStudent | Automatically generates student-facing study guides from uploaded lecture slides and PDFs. Supports regeneration and PDF export. |
| AI-02 | **AI Question Bank Generator** | testMyStudent | Generates MCQ, essay, Yes/No, and mathematical questions from uploaded course materials using LLM. Lecturer reviews before publishing. |
| AI-03 | **AI Essay Assessor** | gradeMyStudent | Assesses student essay responses against a configurable rubric with weighted criteria (depth of analysis, theoretical application, writing quality, citations). |
| AI-04 | **AI Mathematical Solver** | testMyStudent | Provides step-by-step solutions for mathematical exam questions, enabling automated marking and solution path display. |
| AI-05 | **AI Auto-Marking (MCQ/Yes-No)** | gradeMyStudent | Instant scoring for objective questions once correct answers are pre-entered by the lecturer. |
| AI-06 | **AI Rubric Configuration** | testMyStudent | Allows lecturers to define custom weighting criteria for AI-based essay scoring. |
| AI-07 | **AI Analytics Dashboard** | gradeMyStudent | Provides cohort-level insights: performance trends, risk flags for at-risk students, grade distribution analytics. |
| AI-08 | **AI Content Summariser** | teachMyStudent | Summarises lecture content into key points and glossaries for student quick-reference. |

---

## 4. User Story Mapping

### Backbone (Epic Level)

```
[Authenticate] → [Dashboard] → [meetMyStudent] → [teachMyStudent] → [testMyStudent] → [gradeMyStudent] → [Student Portal]
```

### Story Map — Sample Extracts

#### Epic: meetMyStudent

| User Goal | User Stories |
|---|---|
| View all my students | As a lecturer, I want to see all students enrolled in my courses so that I can manage them efficiently. |
| Filter students | As a lecturer, I want to filter students by course, semester, and attempt count so that I can find relevant subsets quickly. |
| Notify students | As a lecturer, I want to send bulk reminder emails to students about submission deadlines so that I reduce late submissions. |
| Register for carry-over | As a lecturer, I want to flag and notify carry-over students to register for repeat exams. |

#### Epic: testMyStudent

| User Goal | User Stories |
|---|---|
| Create MCQ | As a lecturer, I want to create multiple-choice questions with a correct answer pre-entered so that the system can auto-mark them. |
| Generate questions via AI | As a lecturer, I want the AI to generate a set of exam questions from my uploaded slides so that I save preparation time. |
| Filter eligible students | As a lecturer, I want to filter students eligible for an exam based on coursework completion and attempt count so that only qualified students sit the exam. |

#### Epic: gradeMyStudent

| User Goal | User Stories |
|---|---|
| View exam results | As a lecturer, I want to see a complete gradebook for a specific exam so that I can review performance. |
| AI essay review | As a lecturer, I want the AI to assess student essays and provide draft scores so that I can validate and confirm them. |
| Publish results | As a lecturer, I want to publish selected student results and trigger email notifications so that students are informed promptly. |

---

## 5. Product Vision & Roadmap

### Product Vision Statement

> **For NordWest Business School lecturers and students, the Akademia LMS is a digital academic companion that transforms the entire teaching lifecycle — from student onboarding through to final result publication — into an intuitive, AI-augmented experience. Unlike legacy LMS platforms, Akademia embeds intelligence at every touchpoint, reducing administrative burden and elevating the quality of assessment and feedback.**

### Product Roadmap

```
──────────────────────────────────────────────────────────────────────────
VERSION   │ TIMEFRAME       │ FOCUS                     │ KEY DELIVERABLES
──────────────────────────────────────────────────────────────────────────
v0.1.0    │ Week 1–2        │ Foundation                │ Project setup, DB schema,
(Alpha)   │                 │                           │ Auth/SSO, CI/CD pipeline
──────────────────────────────────────────────────────────────────────────
v0.5.0    │ Week 3–6        │ Core Lecturer Features    │ Dashboard, Course view,
(Beta)    │                 │                           │ Student list (FR-01, FR-02)
──────────────────────────────────────────────────────────────────────────
v1.0.0    │ Week 7–10       │ Teaching & Testing        │ Materials upload, Question
(RC1)     │                 │                           │ bank, Exam creation (FR-03,
          │                 │                           │ FR-04), Eligibility filter
──────────────────────────────────────────────────────────────────────────
v1.1.0    │ Week 11–13      │ Grading & Publishing      │ Gradebook, Result publish,
(RC2)     │                 │                           │ Email notification (FR-05)
──────────────────────────────────────────────────────────────────────────
v1.2.0    │ Week 14–16      │ AI Features (Phase 1)     │ AI auto-marking MCQ,
          │                 │                           │ AI essay assessment (AI-01
          │                 │                           │ to AI-05)
──────────────────────────────────────────────────────────────────────────
v1.5.0    │ Week 17–20      │ AI Features (Phase 2)     │ AI question generator,
          │                 │                           │ AI analytics, Student portal
          │                 │                           │ (AI-06 to AI-08)
──────────────────────────────────────────────────────────────────────────
v2.0.0    │ Week 21–24      │ Teams Integration &       │ Microsoft Teams virtual
(GA)      │                 │ Hardening                 │ class, WCAG audit, load
          │                 │                           │ testing, security pen test
──────────────────────────────────────────────────────────────────────────
```

---

## 6. To-Be Concept (UML / System Design)

### 6.1 Use Case Diagram (Textual Representation)

```
┌─────────────────────────────────────────────────────────────┐
│                        Akademia LMS                         │
│                                                             │
│  ┌──────────┐    ┌──────────────────────────────────────┐  │
│  │          │───►│ View Dashboard                       │  │
│  │          │───►│ Manage Students (meetMyStudent)      │  │
│  │ Lecturer │───►│ Upload Materials (teachMyStudent)    │  │
│  │          │───►│ Create Exam (testMyStudent)          │  │
│  │          │───►│ Publish Grades (gradeMyStudent)      │  │
│  │          │───►│ Switch to Student Portal             │  │
│  └──────────┘    └──────────────────────────────────────┘  │
│                                                             │
│  ┌──────────┐    ┌──────────────────────────────────────┐  │
│  │          │───►│ View Course Materials                │  │
│  │  Student │───►│ Submit Assignments                   │  │
│  │          │───►│ Register for Exam                    │  │
│  │          │───►│ View Published Results               │  │
│  └──────────┘    └──────────────────────────────────────┘  │
│                                                             │
│  ┌──────────┐    ┌──────────────────────────────────────┐  │
│  │          │───►│ Manage Users & Roles                 │  │
│  │  Admin   │───►│ Assign Courses to Lecturers          │  │
│  │          │───►│ System Configuration                 │  │
│  └──────────┘    └──────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────┘
```

### 6.2 High-Level Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                        Client Layer                         │
│   Browser (React/HTML5)  ·  Mobile (Responsive)             │
└──────────────────────────┬──────────────────────────────────┘
                           │ HTTPS
┌──────────────────────────▼──────────────────────────────────┐
│                        API Gateway                          │
│           REST API · Rate Limiting · Auth Middleware         │
└──────┬────────────────┬──────────────────┬──────────────────┘
       │                │                  │
┌──────▼─────┐  ┌───────▼──────┐  ┌───────▼──────────────────┐
│  Auth      │  │  Core LMS    │  │  AI Services             │
│  Service   │  │  Service     │  │  - Essay Assessor        │
│  (SSO/JWT) │  │  - Courses   │  │  - Question Generator    │
└────────────┘  │  - Students  │  │  - Auto-Marker           │
                │  - Exams     │  │  - Math Solver           │
                │  - Grades    │  └──────────────────────────┘
                └──────┬───────┘
                       │
┌──────────────────────▼──────────────────────────────────────┐
│                    Data Layer                               │
│   PostgreSQL (core data)  ·  File Storage (S3/Azure Blob)  │
│   Redis (cache/sessions)  ·  Audit Log (append-only)        │
└─────────────────────────────────────────────────────────────┘
                       │
┌──────────────────────▼──────────────────────────────────────┐
│              External Integrations                          │
│   Microsoft Teams API  ·  Email Service (SMTP/SendGrid)    │
│   University SSO (SAML 2.0)                                │
└─────────────────────────────────────────────────────────────┘
```

### 6.3 Entity Relationship (Core Entities)

```
LECTURER ────< COURSE >──── STUDENT
    │               │
    │           MATERIAL
    │               │
    └── EXAM ──< QUESTION
          │
          └──< SUBMISSION >── RESULT ──► GRADE
```

### 6.4 Key State Machine — Exam Lifecycle

```
[Draft] ──(publish)──► [Published] ──(exam window)──► [In Progress]
                                                            │
                                                      (submissions)
                                                            │
                                                     [Marking/AI Review]
                                                            │
                                                   (lecturer confirms)
                                                            │
                                                      [Results Draft]
                                                            │
                                                    (publish results)
                                                            │
                                                    [Results Published]
                                                     (email triggered)
```

---

## 7. Scrum Team & Ceremonies

### Scrum Team Composition

| Role | Name (Placeholder) | Responsibilities |
|---|---|---|
| **Product Owner** | Dr. Ingrid Hoffmann (Head of Digital Transformation) | Vision, backlog prioritisation, stakeholder communication |
| **Scrum Master** | Lars Bergmann | Sprint facilitation, impediment removal, Agile coaching |
| **Lead Developer** | [Dev Lead] | Architecture decisions, code review, technical direction |
| **Frontend Developer** | [FE Dev 1] | UI implementation (Standard + Advanced views) |
| **Frontend Developer** | [FE Dev 2] | Student portal, responsive design |
| **Backend Developer** | [BE Dev 1] | Core LMS API, data models, auth |
| **Backend Developer** | [BE Dev 2] | File storage service, email service |
| **AI/ML Engineer** | [AI Eng] | Essay assessor, question generator, auto-marker models |
| **QA Engineer** | [QA] | Test planning, UAT coordination, regression |
| **UX Designer** | [UX] | Wireframes, usability testing, accessibility |

### Sprint Cadence

- **Sprint Duration:** 2 weeks
- **Sprint Planning:** Every other Monday, 09:00–11:00
- **Daily Standup:** Weekdays, 09:15–09:30 (async on Fridays via Slack)
- **Sprint Review:** Every other Friday, 14:00–15:00 (includes stakeholder demo)
- **Sprint Retrospective:** Every other Friday, 15:15–16:00

### JIRA Project Configuration

```
Project Key:  NWLMS
Board Type:   Scrum
Issue Types:  Epic · Story · Task · Bug · Spike
Workflows:    To Do → In Progress → In Review → Done
              (Bugs additionally: To Do → Triaged → In Progress → Testing → Done)
```

#### Sample JIRA Epics

| Epic Key | Epic Name | Linked FRs |
|---|---|---|
| NWLMS-E01 | Lecturer Dashboard | FR-01 |
| NWLMS-E02 | meetMyStudent | FR-02 |
| NWLMS-E03 | teachMyStudent | FR-03 |
| NWLMS-E04 | testMyStudent | FR-04 |
| NWLMS-E05 | gradeMyStudent | FR-05 |
| NWLMS-E06 | AI Features Phase 1 | AI-01 to AI-05 |
| NWLMS-E07 | AI Features Phase 2 | AI-06 to AI-08 |
| NWLMS-E08 | Student Portal | All |
| NWLMS-E09 | Integrations (Teams, Email, SSO) | NFR-05, NFR-10 |
| NWLMS-E10 | Compliance & Security | NFR-04, NFR-06, NFR-14 |

### Definition of Done (DoD)

- [ ] Code reviewed and approved by at least one peer
- [ ] Unit tests written and passing (≥ 80% coverage)
- [ ] Acceptance criteria met and confirmed by PO
- [ ] Tested on Chrome, Firefox, Safari (desktop) and mobile
- [ ] No critical or high-severity open bugs
- [ ] Documentation updated (API docs, README)
- [ ] Deployed to staging environment successfully

---

## 8. Release Plan & Versioning

### Versioning Convention

This project follows **Semantic Versioning (SemVer)**: `MAJOR.MINOR.PATCH`

| Segment | Meaning | Example |
|---|---|---|
| MAJOR | Breaking changes / architectural changes | `2.0.0` |
| MINOR | New features, backwards-compatible | `1.5.0` |
| PATCH | Bug fixes, minor improvements | `1.1.1` |

### Full Release Schedule

| Version | Release Date | Type | Audience | Key Deliverables |
|---|---|---|---|---|
| `v0.1.0` | Week 2 | Alpha (Internal) | Dev Team only | Project scaffolding, DB schema, CI/CD pipeline, Auth skeleton |
| `v0.5.0` | Week 6 | Beta (Internal) | Dev + QA | Dashboard, course list, student overview (meetMyStudent) |
| `v1.0.0-rc1` | Week 10 | Release Candidate | Pilot Lecturers (5) | Full teachMyStudent + testMyStudent features |
| `v1.0.0` | Week 12 | **General Release** | All Lecturers | v1.0.0-rc1 + gradeMyStudent core, basic publishing |
| `v1.1.0` | Week 14 | Minor Release | All Users | AI auto-marking (MCQ/YesNo), email notification |
| `v1.2.0` | Week 17 | Minor Release | All Users | AI essay assessor, AI study guide, AI question generator |
| `v1.3.0` | Week 19 | Minor Release | All Users | Student portal, result self-service view |
| `v1.5.0` | Week 21 | Minor Release | All Users | AI analytics dashboard, cohort insights, risk flags |
| `v2.0.0` | Week 24 | **Major Release** | All Users + Public Announcement | Teams integration, German i18n, full WCAG 2.1 AA, pen-test cleared |

### Hotfix / Patch Policy

- Security patches: Released within **24 hours** of discovery
- Critical bugs affecting exam/grading: Released within **48 hours**
- Non-critical bugs: Bundled into next minor release

### Stakeholder Communication Plan

| Milestone | Communication | Channel | Audience |
|---|---|---|---|
| v0.5.0 Beta | Internal demo | Teams call | Dev + QA + PO |
| v1.0.0-rc1 | Pilot launch briefing | Email + Teams | Pilot lecturers + IT Dept |
| v1.0.0 GA | Launch announcement | Email + Intranet | All staff + Admin |
| v2.0.0 | Press release + faculty tour | Email + Live Demo | All stakeholders + Leadership |

---

## 9. Product Prototype

The interactive prototype is delivered as two HTML files representing the Standard and Advanced UI tiers, with full in-browser navigation between pages.

### Screens Included

| Screen | Standard | Advanced |
|---|---|---|
| Dashboard | ✅ | ✅ |
| meetMyStudent — Student List | ✅ | ✅ |
| teachMyStudent — Materials | ✅ | ✅ |
| testMyStudent — Exam Creation | ✅ | ✅ |
| gradeMyStudent — Gradebook | ✅ | ✅ |
| Academic Calendar | ❌ | ✅ |
| Course Browser | ❌ | ✅ |

### Running the Prototype

```bash
# No build step required — open directly in any modern browser
open prototype/index.html
```

Or serve with a local HTTP server:

```bash
npx serve prototype/
# → http://localhost:3000
```

### AI Features Flagged in Prototype

Items tagged with the **"Advanced"** pill in the Standard view and the **✦ AI** badge in the Advanced view represent AI-powered capabilities. These are currently rendered as UI stubs to support stakeholder demonstrations and UAT planning.

---

## 10. Technology Stack

| Layer | Technology | Rationale |
|---|---|---|
| **Frontend** | HTML5, CSS3, Tailwind CSS (Standard) / Vanilla CSS (Advanced) | Rapid prototyping; production will migrate to React |
| **Production Frontend** | React 18 + TypeScript | Component reuse, type safety |
| **Fonts** | Figtree, Inter, JetBrains Mono (Standard) · Syne, DM Sans (Advanced) | Distinctive brand typography |
| **Backend** | Node.js (Express) or Python (FastAPI) | TBD based on team expertise |
| **Database** | PostgreSQL | Relational integrity for academic records |
| **File Storage** | Azure Blob Storage | EU-hosted, GDPR compliant |
| **AI/ML** | OpenAI API / Azure OpenAI | Essay assessment, question generation |
| **Auth** | SAML 2.0 + JWT | University SSO integration |
| **Email** | SendGrid | Reliable transactional email |
| **Teams Integration** | Microsoft Graph API | Virtual class activation |
| **CI/CD** | GitHub Actions | Automated test + deploy |
| **Hosting** | Azure App Service | EU-region, GDPR compliant |
| **Monitoring** | Datadog / Azure Monitor | Uptime, error tracking |
| **Project Management** | JIRA + Confluence | Scrum ceremonies + documentation |

---

## 11. Getting Started

### Prerequisites

```
Node.js >= 18
Git
A modern browser (Chrome 120+, Firefox 120+, Safari 17+)
```

### Clone & Run (Prototype)

```bash
# 1. Clone the repository
git clone https://github.com/nordwest-university/akademia-lms.git
cd akademia-lms

# 2. Open the prototype
open prototype/index.html

# Or serve with npx
npx serve prototype/
```

### Environment Setup (Production App — TBD)

```bash
# Copy environment template
cp .env.example .env

# Configure the following in .env:
# DATABASE_URL=postgresql://...
# AZURE_BLOB_CONNECTION_STRING=...
# OPENAI_API_KEY=...
# JWT_SECRET=...
# SSO_SAML_METADATA_URL=...
# SENDGRID_API_KEY=...

# Install dependencies
npm install

# Run development server
npm run dev
```

---

## 12. Folder Structure

```
akademia-lms/
├── prototype/                  # HTML/CSS interactive prototype
│   ├── index.html              # Switcher shell (Standard ↔ Advanced)
│   ├── standard.html           # Standard UI (Tailwind-based)
│   └── advanced.html           # Advanced UI (Akademia, custom CSS)
│
├── docs/                       # Project documentation
│   ├── stakeholders.md
│   ├── requirements.md
│   ├── user-story-map.md
│   ├── roadmap.md
│   └── architecture/
│       ├── use-case-diagram.png
│       ├── system-architecture.png
│       └── er-diagram.png
│
├── src/                        # Production source (v1.0+ — TBD)
│   ├── frontend/
│   │   ├── components/
│   │   ├── pages/
│   │   └── styles/
│   └── backend/
│       ├── api/
│       ├── services/
│       └── models/
│
├── tests/                      # Test suites
│   ├── unit/
│   ├── integration/
│   └── e2e/
│
├── .github/
│   └── workflows/
│       └── ci.yml              # GitHub Actions pipeline
│
├── .env.example
├── README.md                   ← You are here
└── LICENSE
```

---

## 13. Contributing

1. Create a feature branch from `develop`: `git checkout -b feature/NWLMS-XXX-short-description`
2. Follow the Definition of Done checklist (Section 7)
3. Write or update tests for your changes
4. Submit a Pull Request targeting `develop`
5. Request review from at least one team member
6. Link the PR to the relevant JIRA ticket

**Branch Naming Convention:**
- Features: `feature/NWLMS-XXX-description`
- Bug fixes: `fix/NWLMS-XXX-description`
- Hotfixes: `hotfix/NWLMS-XXX-description`
- Spikes: `spike/NWLMS-XXX-description`

---

## 14. License

This project is proprietary software developed for **NordWest Business School**.
All rights reserved. Unauthorised reproduction or distribution is prohibited.

For licensing enquiries, contact: **digitaltransformation@nordwest.edu**

---

*README last updated: April 2026 · Akademia LMS v1.0 · NordWest Business School Digital Transformation*
