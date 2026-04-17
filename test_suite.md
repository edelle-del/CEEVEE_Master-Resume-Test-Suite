# Master Resume — Comprehensive Test Suite

**Feature Under Test:** Master Resume (Creation, Editing, and Multi-Profile Management)  
**Document Version:** 1.0  
**Date:** April 17, 2026  
**Prepared By:** QA Team  

---

## Table of Contents

1. [Test Scope & Objectives](#1-test-scope--objectives)
2. [Test Environment & Prerequisites](#2-test-environment--prerequisites)
3. [Test Coverage Summary](#3-test-coverage-summary)
4. [Section A — Resume Upload & Initial Creation](#section-a--resume-upload--initial-creation)
5. [Section B — Contact Info](#section-b--contact-info)
6. [Section C — Professional Summary](#section-c--professional-summary)
7. [Section D — Technical Skills](#section-d--technical-skills)
8. [Section E — Portfolio Projects](#section-e--portfolio-projects)
9. [Section F — Employment History](#section-f--employment-history)
10. [Section G — Education](#section-g--education)
11. [Section H — References](#section-h--references)
12. [Section I — Section UI Behavior (Collapse, Reorder)](#section-i--section-ui-behavior-collapse-reorder)
13. [Section J — Multiple Profiles](#section-j--multiple-profiles)
14. [Section K — Data Persistence & Integrity](#section-k--data-persistence--integrity)
15. [Section L — Edge Cases & Negative Tests](#section-l--edge-cases--negative-tests)
16. [Appendix — Test Data Samples](#appendix--test-data-samples)

---

## 1. Test Scope & Objectives

### In Scope
- Creating a master resume from scratch or via upload
- Editing all individual resume sections through the editor page
- Section-level UI behaviors: collapse/expand, drag-to-reorder
- Creating, switching between, and deleting multiple profiles
- Data persistence across sessions and page reloads
- Input validation and error handling per section
- ATS-relevant field behavior (skills tagging, keyword preservation)

### Out of Scope
- Resume optimization/tailoring logic (separate feature)
- PDF/DOCX export rendering fidelity
- Third-party integrations (LinkedIn import, etc.)
- Payment and subscription flows

### Pass Criteria
A test case **passes** when all stated expected results are observed with no unhandled errors or data loss. A test case **fails** if any expected result is not met, a console error is thrown, or data entered is not saved correctly.

---

## 2. Test Environment & Prerequisites

| Item | Requirement |
|------|-------------|
| Browser | Chrome 122+, Firefox 124+, Safari 17+ |
| Viewport | Desktop (1280×800 minimum), Mobile (375×812) |
| Test Account | Fresh account with zero existing profiles |
| Auth State | Logged in before each section begins |
| Network | Standard broadband (also test on throttled 3G for save operations) |

---

## 3. Test Coverage Summary

| Section | # Test Cases | Functional | Validation | UI/UX | Edge |
|---------|-------------|------------|------------|-------|------|
| Upload & Creation | 6 | ✓ | ✓ | ✓ | ✓ |
| Contact Info | 8 | ✓ | ✓ | ✓ | ✓ |
| Professional Summary | 5 | ✓ | ✓ | ✓ | — |
| Technical Skills | 9 | ✓ | ✓ | ✓ | ✓ |
| Portfolio Projects | 8 | ✓ | ✓ | ✓ | ✓ |
| Employment History | 10 | ✓ | ✓ | ✓ | ✓ |
| Education | 6 | ✓ | ✓ | ✓ | ✓ |
| References | 6 | ✓ | ✓ | ✓ | — |
| Section UI Behaviors | 7 | ✓ | — | ✓ | ✓ |
| Multiple Profiles | 9 | ✓ | ✓ | ✓ | ✓ |
| Data Persistence | 5 | ✓ | — | — | ✓ |
| Edge Cases / Negative | 8 | — | ✓ | ✓ | ✓ |
| **TOTAL** | **87** | | | | |

---

## Section A — Resume Upload & Initial Creation

### TC-A-001: Upload an existing resume file (PDF)

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-A-001 | Upload an existing resume file (PDF) |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-A-002: Upload an existing resume file (DOCX)

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-A-002 | Upload an existing resume file (DOCX) |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-A-003: Upload unsupported file type

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-A-003 | Upload unsupported file type |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-A-004: Upload file exceeding size limit

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-A-004 | Upload file exceeding size limit |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

## Section B — Contact Info

### TC-B-001: Save all Contact Info fields successfully

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-B-001 | Save all Contact Info fields successfully |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-B-002: Email field validation

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-B-002 | Email field validation |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-B-003: Phone field accepts international formats

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-B-003 | Phone field accepts international formats |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-B-004: URL fields reject non-URL values

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-B-004 | URL fields reject non-URL values |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-B-005: All Contact Info fields are optional except Full Name

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-B-005 | All Contact Info fields are optional except Full Name |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-B-006: Full Name cannot be saved as blank

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-B-006 | Full Name cannot be saved as blank |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-B-007: Special characters in Full Name are preserved

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-B-007 | Special characters in Full Name are preserved |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-B-008: Contact Info is included in optimized resumes

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-B-008 | Contact Info is included in optimized resumes |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

## Section C — Professional Summary

### TC-C-001: Save headline and detailed paragraph

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-C-001 | Save headline and detailed paragraph |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-C-002: Character limit on headline

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-C-002 | Character limit on headline |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-C-003: Summary fields are optional

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-C-003 | Summary fields are optional |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-C-004: Markdown or formatting in paragraph

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-C-004 | Markdown or formatting in paragraph |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-C-005: Summary length is preserved through optimization

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-C-005 | Summary length is preserved through optimization |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

## Section D — Technical Skills

### TC-D-001: Add a skill tag

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-D-001 | Add a skill tag |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-D-002: Add multiple skill tags in sequence

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-D-002 | Add multiple skill tags in sequence |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-D-003: Delete a skill tag

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-D-003 | Delete a skill tag |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-D-004: Duplicate skill tags are prevented

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-D-004 | Duplicate skill tags are prevented |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-D-005: Case sensitivity of skill tags

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-D-005 | Case sensitivity of skill tags |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-D-006: Skill tags cannot be blank

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-D-006 | Skill tags cannot be blank |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-D-007: Skill tags with special characters

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-D-007 | Skill tags with special characters |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-D-008: Large number of skill tags

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-D-008 | Large number of skill tags |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-D-009: Skills appear correctly in ATS optimization output

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-D-009 | Skills appear correctly in ATS optimization output |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

## Section E — Portfolio Projects

### TC-E-001: Add a new portfolio project with all fields

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-E-001 | Add a new portfolio project with all fields |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-E-002: Project URL validation

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-E-002 | Project URL validation |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-E-003: Project URL is optional

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-E-003 | Project URL is optional |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-E-004: Add multiple projects

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-E-004 | Add multiple projects |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-E-005: Edit an existing project

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-E-005 | Edit an existing project |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-E-006: Delete a project

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-E-006 | Delete a project |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-E-007: Tech Stack field on project (tag-based)

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-E-007 | Tech Stack field on project (tag-based) |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-E-008: Achievements field accepts multi-line input

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-E-008 | Achievements field accepts multi-line input |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

## Section F — Employment History

### TC-F-001: Add a new employment entry with all fields

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-F-001 | Add a new employment entry with all fields |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-F-002: "Currently employed here" / Present end date

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-F-002 | "Currently employed here" / Present end date |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-F-003: End date cannot precede start date

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-F-003 | End date cannot precede start date |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-F-004: Multiple positions — correct ordering

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-F-004 | Multiple positions — correct ordering |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-F-005: Edit an existing employment entry

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-F-005 | Edit an existing employment entry |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-F-006: Delete an employment entry

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-F-006 | Delete an employment entry |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-F-007: Company name accepts unicode/international characters

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-F-007 | Company name accepts unicode/international characters |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-F-008: Required fields — Company and Role

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-F-008 | Required fields — Company and Role |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-F-009: Achievements field supports rich multi-line text

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-F-009 | Achievements field supports rich multi-line text |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-F-010: Employment history in optimization output

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-F-010 | Employment history in optimization output |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

## Section G — Education

### TC-G-001: Add an education entry with all fields

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-G-001 | Add an education entry with all fields |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-G-002: Graduation Year validation

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-G-002 | Graduation Year validation |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-G-003: Degree and Field of Study are optional

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-G-003 | Degree and Field of Study are optional |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-G-004: Add multiple education entries

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-G-004 | Add multiple education entries |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-G-005: Delete an education entry

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-G-005 | Delete an education entry |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-G-006: School name is required

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-G-006 | School name is required |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

## Section H — References

### TC-H-001: Add a reference with all fields

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-H-001 | Add a reference with all fields |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-H-002: Contact Details field accepts email and phone

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-H-002 | Contact Details field accepts email and phone |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-H-003: All reference fields are optional except Name

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-H-003 | All reference fields are optional except Name |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-H-004: Add multiple references

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-H-004 | Add multiple references |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-H-005: Delete a reference

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-H-005 | Delete a reference |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-H-006: Reference Name is required

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-H-006 | Reference Name is required |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

## Section I — Section UI Behavior (Collapse, Reorder)

### TC-I-001: Collapse and expand a section

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-I-001 | Collapse and expand a section |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-I-002: All sections can be independently collapsed

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-I-002 | All sections can be independently collapsed |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-I-003: Reorder sections via drag and drop

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-I-003 | Reorder sections via drag and drop |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-I-004: Reorder sections and verify optimization uses new order

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-I-004 | Reorder sections and verify optimization uses new order |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-I-005: Drag handle is only visible when hovering (if applicable)

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-I-005 | Drag handle is only visible when hovering (if applicable) |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-I-006: Collapse state is preserved on page reload

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-I-006 | Collapse state is preserved on page reload |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-I-007: Keyboard accessibility of collapse toggle

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-I-007 | Keyboard accessibility of collapse toggle |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

## Section J — Multiple Profiles

### TC-J-001: Create a second master resume profile

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-J-001 | Create a second master resume profile |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-J-002: Switch between profiles using the Profile Switcher

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-J-002 | Switch between profiles using the Profile Switcher |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-J-003: Profile data is strictly isolated

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-J-003 | Profile data is strictly isolated |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-J-004: Profile Switcher appears on the optimization form

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-J-004 | Profile Switcher appears on the optimization form |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-J-005: Optimization uses selected profile's data

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-J-005 | Optimization uses selected profile's data |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-J-006: Rename a profile

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-J-006 | Rename a profile |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-J-007: Delete a profile

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-J-007 | Delete a profile |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-J-008: Cannot delete the only remaining profile

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-J-008 | Cannot delete the only remaining profile |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-J-009: Profile Switcher shows correct active profile indicator

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-J-009 | Profile Switcher shows correct active profile indicator |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

## Section K — Data Persistence & Integrity

### TC-K-001: Auto-save or manual save persists all sections

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-K-001 | Auto-save or manual save persists all sections |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-K-002: Unsaved changes prompt on navigation away

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-K-002 | Unsaved changes prompt on navigation away |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-K-003: Data survives a browser refresh

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-K-003 | Data survives a browser refresh |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-K-004: Concurrent edit protection (same account, two tabs)

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-K-004 | Concurrent edit protection (same account, two tabs) |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-K-005: Save failure shows an error and retains form data

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-K-005 | Save failure shows an error and retains form data |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

## Section L — Edge Cases & Negative Tests

### TC-L-001: XSS injection in text fields

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-L-001 | XSS injection in text fields |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-L-002: SQL/NoSQL injection strings in fields

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-L-002 | SQL/NoSQL injection strings in fields |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-L-003: Extremely long input in a text field

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-L-003 | Extremely long input in a text field |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-L-004: Emoji and Unicode in text fields

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-L-004 | Emoji and Unicode in text fields |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-L-005: Resume with no sections filled still saves

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-L-005 | Resume with no sections filled still saves |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-L-006: Session expiry during editing

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-L-006 | Session expiry during editing |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-L-007: Mobile responsiveness of the editor

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-L-007 | Mobile responsiveness of the editor |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

### TC-L-008: Accessibility — keyboard-only navigation through the editor

| Test Case ID | Test Case Description | Type | Priority | Steps | Expected Result | Pass | Fail | Notes |
|---|---|---|---|---|---|---|---|---|
| TC-L-008 | Accessibility — keyboard-only navigation through the editor |  |  | Refer to linked/base test flow. | Expected behavior matches the scenario acceptance criteria. | ☐ | ☐ |  |

---

