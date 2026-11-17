
# Community Lost & Found Matching Network – SE Lab

**Name:** Niyatee Singh  
**SRN:** PES1UG24CS305

## Overview

This repository contains my Software Engineering lab work for the Community Lost & Found Matching Network.

The system is designed to help people find their lost belongings. Users can report lost or found items, upload pictures and provide descriptions. The system extracts tags from the images and descriptions, matches items based on tags and location, and verifies ownership through security questions before handing over an item.

## Actors

- Finder / Owner
- Community Admin

---

## Lab 1: Requirements Engineering & UML Use-Case Modelling

Files are in the `LAB1/` folder.

- **Requirements_Table_PES1UG24CS305.pdf** – Contains 5 functional (FR-001 to FR-005) and 2 non-functional (NFR-001, NFR-002) requirements with ID, Type, Description, Priority, Acceptance Criteria and Rationale.
- **Use-Case_Diagram_PES1UG24CS305.pdf** – UML use-case diagram showing all three actors (Finder, Owner, Community Admin) and the main use cases, including `<<include>>` and `<<extend>>` relationships.
- **Use-Case Flow_PES1UG24CS305.pdf** – One-page flow specification for UC-05 Claim Item, with preconditions, postconditions, the main success scenario and an alternate flow (incorrect answer).

---

## Lab 2: Agile Backlog Creation & Sprint Simulation in Jira

Files are in the `LAB2/` folder.

For this lab, I used Jira to convert the requirements from Lab 1 into Epics, user stories and smaller tasks. I worked with Scrum and Kanban boards to understand how tasks are planned, organized and tracked in Agile development.

### Scrum

I created a Scrum project for the Community Lost and Found application and divided the requirements into four main Epics:

1. Item Reporting
2. Tag Extraction
3. Matching and Notification
4. Ownership Verification and Handover

I created user stories under the respective Epics and assigned story points based on the estimated effort and complexity.

I then created sprints and simulated task progress by moving stories between To Do, In Progress and Done.

In one sprint, I planned 16 story points but completed 13, leaving one 3-point task unfinished. The burndown chart helped me understand the team's progress and showed that I had slightly overestimated the amount of work that could be completed.

### Kanban

I also created a separate Kanban project to manage the user stories using a continuous workflow.

The board consists of four columns:

- Backlog
- Selected for Development
- In Progress
- Done

I added 7 user stories related to Matching and Notification and Ownership Verification, linked them to their Epics and created subtasks for individual implementation steps.

The List view helped me see all the stories, Epics, priorities and statuses together.

### Bug Tracking

I created a separate bug-tracking board and added three sample defects:

- Map search radius slider crashing on mobile
- Push notification emails being delayed
- Uploaded item images appearing distorted on the matched dashboard

This was to understand how bugs are recorded and tracked during development.

### Files

- **Scrum_Project_PES1UG24CS305.pdf** – Epics and backlog, story points, active sprint, burndown chart and answers to the reflection questions.
- **KANBAN.pdf** – Kanban board screenshots, user stories, subtasks and List view.
- **BugReport.pdf** – Bug-tracking board with the reported defects.

---

## Lab 3: Component Modelling & Architectural Pattern Selection

Files are in the `LAB3/` folder.

- **Lab3_Component_Diagram_PES1UG24CS305.png** – UML component diagram of the system.
- **Lab3_Justification_PES1UG24CS305.pdf** – One-page justification for the chosen architecture.
- **Lab3_Justification_PES1UG24CS305.docx** – Word version of the justification.

### Architecture Chosen: Microservices

I compared Layered, Client-Server and Microservices architectures and chose Microservices.

Tag extraction from photos requires more processing than the other features, so having it as a separate service allows it to scale independently. Separating the services also makes the system easier to maintain and reduces the effect of failures in individual services.

### Components

| Component | What it does |
|---|---|
| Client App (Web / Mobile UI) | Lets users report items, upload photos and answer verification questions |
| Item Management Service | Handles lost/found reports and coordinates the other services |
| Tag Extraction Service | Extracts visual and text tags from photos and descriptions |
| Geo-Matching Service | Matches lost and found items using tags and location |
| Ownership Verification Service | Stores security questions and verifies the claimant's answers |
| Item Database | Stores items, tags, locations and user information |

### Interfaces

| Interface | Provided by | Required by | Type |
|---|---|---|---|
| IItemReport | Item Management Service | Client App | REST API (HTTPS) |
| IVerification | Ownership Verification Service | Client App | REST API (HTTPS) |
| ITagExtraction | Tag Extraction Service | Item Management Service | REST API / async queue |
| IMatchQuery | Geo-Matching Service | Item Management Service | REST API |
| IItemData | Item Database | Item Management Service | SQL queries |
| ILocationQuery | Item Database | Geo-Matching Service | Geo-spatial DB queries |

---

## Tools Used

- **Jira** – Scrum, Kanban, sprint simulation and bug tracking
- **draw.io (diagrams.net)** – UML diagrams
- **Microsoft Word** – Documentation and reports
