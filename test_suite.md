# Master Resume — Comprehensive Test Suite

**Feature Under Test:** Master Resume (Creation, Editing, and Multi-Profile Management)  
**Document Version:** 1.0  
**Date:** April 17, 2026  
**Prepared By:** Edelle Gibben Lumabi  

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

---

## 1. Test Scope & Objectives

### In Scope
- Creating a via upload
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
| Upload & Creation | 4 | ✓ | ✓ | ✓ | ✓ |
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
| **TOTAL** | **85** | | | | |

---

## Section A — Resume Upload & Initial Creation

### TC-A-001: Upload an existing resume file (PDF)

| Field | Detail |
|-------|--------|
| **Test ID** | TC-A-001 |
| **Priority** | P0 — Critical |
| **Type** | Functional |

**Preconditions:** User has a valid PDF resume under 10MB.

**Steps:**
1. Click "Upload Resume."
2. Select a PDF file from the file picker.
3. Wait for parsing/processing to complete.
4. Observe the editor page.

**Expected Results:**
- File is accepted without error.
- Parsed content populates relevant sections (name, email, employment, etc.) where recognizable.
- Unparsed or ambiguous data is placed in the most relevant field or left blank.
- A success confirmation is shown.

---

### TC-A-002: Upload an existing resume file (DOCX)

| Field | Detail |
|-------|--------|
| **Test ID** | TC-A-002 |
| **Priority** | P1 — High |
| **Type** | Functional |

**Steps:** Same as TC-A-001, using a .docx file.

**Expected Results:** Same as TC-A-001. DOCX content is parsed and populated correctly.

---

### TC-A-003: Upload unsupported file type

| Field | Detail |
|-------|--------|
| **Test ID** | TC-A-003 |
| **Priority** | P1 — High |
| **Type** | Negative / Validation |

**Steps:**
1. Attempt to upload a `.png`, `.xlsx`, or `.txt` file as a resume.

**Expected Results:**
- Upload is rejected before or immediately after submission.
- An inline error message is displayed: e.g., "Only PDF or DOCX files are supported."
- No profile is created.
- The file picker resets cleanly.

---

### TC-A-004: Upload file exceeding size limit

| Field | Detail |
|-------|--------|
| **Test ID** | TC-A-004 |
| **Priority** | P1 — High |
| **Type** | Negative / Validation |

**Steps:**
1. Attempt to upload a PDF larger than the stated file size limit (e.g., 20MB file).

**Expected Results:**
- Upload is blocked with a clear error: e.g., "File size exceeds the 10MB limit."
- No profile is created.

---

## Section B — Contact Info

### TC-B-001: Save all Contact Info fields successfully

| Field | Detail |
|-------|--------|
| **Test ID** | TC-B-001 |
| **Priority** | P0 — Critical |
| **Type** | Functional |

**Steps:**
1. Open editor → Contact Info section.
2. Enter: Full Name, Email, Phone, LinkedIn URL, GitHub URL, Portfolio URL.
3. Click Save (or trigger auto-save).
4. Reload the page.

**Expected Results:**
- All six fields are saved and repopulated correctly after reload.
- LinkedIn and GitHub fields accept full URLs (e.g., `https://linkedin.com/in/username`).

---

### TC-B-002: Email field validation

| Field | Detail |
|-------|--------|
| **Test ID** | TC-B-002 |
| **Priority** | P1 — High |
| **Type** | Validation |

**Steps:**
1. Enter invalid email formats one at a time: `notanemail`, `@domain.com`, `user@`, `user@domain`.
2. Attempt to save after each.

**Expected Results:**
- Each invalid entry triggers an inline validation error.
- Save is blocked until a valid email is provided.
- Valid format `user@domain.com` passes without error.

---

### TC-B-003: Phone field accepts international formats

| Field | Detail |
|-------|--------|
| **Test ID** | TC-B-003 |
| **Priority** | P2 — Medium |
| **Type** | Functional / Validation |

**Steps:**
1. Enter the following phone numbers one at a time and save each: `(555) 123-4567`, `+1-555-123-4567`, `+63 917 123 4567`, `555.123.4567`.

**Expected Results:**
- All above formats are accepted without validation errors.
- Values are stored as entered (no forced reformatting unless documented).

---

### TC-B-004: URL fields reject non-URL values

| Field | Detail |
|-------|--------|
| **Test ID** | TC-B-004 |
| **Priority** | P1 — High |
| **Type** | Validation |

**Steps:**
1. Enter `just text` in the LinkedIn URL field.
2. Enter `ftp://invalid` in the Portfolio URL field.
3. Attempt to save.

**Expected Results:**
- Inline validation errors appear for fields that expect valid `http/https` URLs.
- Save is blocked.

---

### TC-B-005: All Contact Info fields are optional except Full Name

| Field | Detail |
|-------|--------|
| **Test ID** | TC-B-005 |
| **Priority** | P1 — High |
| **Type** | Validation |

**Steps:**
1. Enter only the Full Name. Leave all other fields blank.
2. Save.

**Expected Results:**
- Save succeeds without errors.
- Blank optional fields remain blank after reload.

---

### TC-B-006: Full Name cannot be saved as blank

| Field | Detail |
|-------|--------|
| **Test ID** | TC-B-006 |
| **Priority** | P0 — Critical |
| **Type** | Validation |

**Steps:**
1. Clear the Full Name field.
2. Click save.
3. Reload

**Expected Results:**
- Full name is not deleted upon reload.

---

### TC-B-007: Special characters in Full Name are preserved

| Field | Detail |
|-------|--------|
| **Test ID** | TC-B-007 |
| **Priority** | P2 — Medium |
| **Type** | Functional / Edge |

**Steps:**
1. Enter `José María O'Brien-Ñúñez` in the Full Name field.
2. Save and reload.

**Expected Results:**
- Name is saved and displayed with all special characters intact (no encoding artifacts).

---

### TC-B-008: Contact Info is included in optimized resumes

| Field | Detail |
|-------|--------|
| **Test ID** | TC-B-008 |
| **Priority** | P1 — High |
| **Type** | Integration (cross-feature) |

**Steps:**
1. Save complete Contact Info.
2. Trigger a resume optimization from the optimization form.
3. Review the generated/tailored resume output.

**Expected Results:**
- Full Name, Email, Phone, and at least one URL appear in the optimized resume output.

---

## Section C — Professional Summary

### TC-C-001: Save headline and detailed paragraph

| Field | Detail |
|-------|--------|
| **Test ID** | TC-C-001 |
| **Priority** | P0 — Critical |
| **Type** | Functional |

**Steps:**
1. Open Professional Summary section.
2. Enter a headline: `"Full-Stack Engineer | React & Node.js | 7 Years Experience"`.
3. Enter a multi-sentence paragraph summary (150–300 words).
4. Save and reload.

**Expected Results:**
- Both fields are saved independently and correctly repopulated after reload.
- Paragraph preserves line breaks if any were entered.

---

### TC-C-002: Character limit on headline

| Field | Detail |
|-------|--------|
| **Test ID** | TC-C-002 |
| **Priority** | P2 — Medium |
| **Type** | Validation / UI |

**Steps:**
1. Enter a headline exceeding the expected character limit (try 500 characters).

**Expected Results:**
- Input is capped or a visible character count/limit indicator is shown.
- If capped, text stops accepting input at the limit.
- If a counter is shown, it turns red or warns near/at the limit.

---

### TC-C-003: Summary fields are optional

| Field | Detail |
|-------|--------|
| **Test ID** | TC-C-003 |
| **Priority** | P2 — Medium |
| **Type** | Validation |

**Steps:**
1. Leave both headline and paragraph blank.
2. Save.

**Expected Results:** Save succeeds with no errors.

---

### TC-C-004: Markdown or formatting in paragraph

| Field | Detail |
|-------|--------|
| **Test ID** | TC-C-004 |
| **Priority** | P2 — Medium |
| **Type** | Functional / Edge |

**Steps:**
1. Enter text with special characters and symbols: `**bold**`, `—`, `&`, `<strong>`.
2. Save and reload.

**Expected Results:**
- Content is stored and displayed as entered (raw text) or rendered correctly if markdown is supported.
- No XSS injection occurs. HTML tags are either escaped or stripped safely.

---

### TC-C-005: Summary length is preserved through optimization

| Field | Detail |
|-------|--------|
| **Test ID** | TC-C-005 |
| **Priority** | P1 — High |
| **Type** | Integration |

**Steps:**
1. Save a detailed 3-paragraph summary.
2. Run an optimization.

**Expected Results:**
- The summary data from the master resume is used as source material for the optimized output.
- The original master resume summary is not modified by the optimization process.

---

## Section D — Technical Skills

### TC-D-001: Add a skill tag

| Field | Detail |
|-------|--------|
| **Test ID** | TC-D-001 |
| **Priority** | P0 — Critical |
| **Type** | Functional |

**Steps:**
1. Open Technical Skills section.
2. Type `React` in the tag input and press Enter (or click Add).
3. Save.

**Expected Results:**
- "React" appears as a tag/chip in the skills list.
- Tag persists after page reload.

---

### TC-D-002: Add multiple skill tags in sequence

| Field | Detail |
|-------|--------|
| **Test ID** | TC-D-002 |
| **Priority** | P0 — Critical |
| **Type** | Functional |

**Steps:**
1. Add the following tags one by one: `Python`, `Docker`, `PostgreSQL`, `AWS`, `TypeScript`.
2. Save and reload.

**Expected Results:**
- All 5 tags are present and correctly labeled after reload.
- Order is preserved (or alphabetical if sorting is applied — document behavior).

---

### TC-D-003: Delete a skill tag

| Field | Detail |
|-------|--------|
| **Test ID** | TC-D-003 |
| **Priority** | P0 — Critical |
| **Type** | Functional |

**Steps:**
1. With existing tags present, click the "×" or delete icon on one tag.
2. Save and reload.

**Expected Results:**
- The deleted tag is no longer shown after reload.
- Remaining tags are unaffected.

---

### TC-D-004: Duplicate skill tags are prevented

| Field | Detail |
|-------|--------|
| **Test ID** | TC-D-004 |
| **Priority** | P1 — High |
| **Type** | Validation |

**Steps:**
1. Add `JavaScript`.
2. Attempt to add `JavaScript` again.

**Expected Results:**
- Duplicate is rejected. Either the input clears with a toast ("Skill already added") or the duplicate is silently ignored.
- Only one "JavaScript" tag exists in the list.

---

### TC-D-005: Case sensitivity of skill tags

| Field | Detail |
|-------|--------|
| **Test ID** | TC-D-005 |
| **Priority** | P2 — Medium |
| **Type** | Validation / Edge |

**Steps:**
1. Add `react` (lowercase).
2. Attempt to add `React` (capitalized).

**Expected Results:**
- Behavior is consistent and documented. Either: (a) treated as duplicates and second entry blocked, or (b) both stored separately. Document which is expected.

---

### TC-D-006: Skill tags cannot be blank

| Field | Detail |
|-------|--------|
| **Test ID** | TC-D-006 |
| **Priority** | P1 — High |
| **Type** | Validation |

**Steps:**
1. Press Enter in the tag input field while it is empty.

**Expected Results:**
- No blank tag is added.
- Input field remains focused.

---

### TC-D-007: Skill tags with special characters

| Field | Detail |
|-------|--------|
| **Test ID** | TC-D-007 |
| **Priority** | P2 — Medium |
| **Type** | Edge |

**Steps:**
1. Add skill tags: `C++`, `C#`, `.NET`, `Node.js`, `Vue 3`.

**Expected Results:**
- All tags are saved and displayed exactly as entered (symbols preserved).

---

### TC-D-008: Large number of skill tags

| Field | Detail |
|-------|--------|
| **Test ID** | TC-D-008 |
| **Priority** | P2 — Medium |
| **Type** | Performance / Edge |

**Steps:**
1. Add 50 skill tags.
2. Save and reload.

**Expected Results:**
- All 50 tags save and reload correctly.
- UI wraps gracefully (no overflow or layout breakage).
- Performance is acceptable (no noticeable lag when rendering tags).

---

### TC-D-009: Skills appear correctly in ATS optimization output

| Field | Detail |
|-------|--------|
| **Test ID** | TC-D-009 |
| **Priority** | P1 — High |
| **Type** | Integration |

**Steps:**
1. Add 10 skills including `Python`, `REST APIs`, `Agile`.
2. Run an optimization against a job description that includes those keywords.

**Expected Results:**
- The optimized resume includes matching skills from the master resume.
- The master resume skill list is not modified after optimization.

---

## Section E — Portfolio Projects

### TC-E-001: Add a new portfolio project with all fields

| Field | Detail |
|-------|--------|
| **Test ID** | TC-E-001 |
| **Priority** | P0 — Critical |
| **Type** | Functional |

**Steps:**
1. Open Portfolio Projects section.
2. Click "Add Project."
3. Fill in: Title, URL, Description, Tech Stack, Achievements.
4. Save and reload.

**Expected Results:**
- Project appears in the list with all entered data.
- All fields persist correctly after reload.

---

### TC-E-002: Project URL validation

| Field | Detail |
|-------|--------|
| **Test ID** | TC-E-002 |
| **Priority** | P1 — High |
| **Type** | Validation |

**Steps:**
1. Enter `not-a-url` in the Project URL field.
2. Attempt to save.

**Expected Results:**
- Inline validation error on the URL field.
- Save is blocked until a valid URL or blank value is provided.

---

### TC-E-003: Project URL is optional

| Field | Detail |
|-------|--------|
| **Test ID** | TC-E-003 |
| **Priority** | P1 — High |
| **Type** | Validation |

**Steps:**
1. Add a project with Title, Description, and Tech Stack but no URL.
2. Save.

**Expected Results:** Save succeeds. URL field shows blank/empty after reload.

---

### TC-E-004: Add multiple projects

| Field | Detail |
|-------|--------|
| **Test ID** | TC-E-004 |
| **Priority** | P0 — Critical |
| **Type** | Functional |

**Steps:**
1. Add 3 separate portfolio projects, each with distinct data.
2. Save and reload.

**Expected Results:**
- All 3 projects are listed in the correct order.
- No data from one project bleeds into another.

---

### TC-E-005: Edit an existing project

| Field | Detail |
|-------|--------|
| **Test ID** | TC-E-005 |
| **Priority** | P0 — Critical |
| **Type** | Functional |

**Steps:**
1. Click "Edit" on an existing project.
2. Change the Title and add an achievement bullet.
3. Save and reload.

**Expected Results:**
- Updated fields are saved. Other projects are unaffected.

---

### TC-E-006: Delete a project

| Field | Detail |
|-------|--------|
| **Test ID** | TC-E-006 |
| **Priority** | P1 — High |
| **Type** | Functional |

**Steps:**
1. Click "Delete" on a project.
2. Confirm deletion in the dialog (if one appears).
3. Reload.

**Expected Results:**
- Project is permanently removed.
- Remaining projects are unaffected and their order is preserved.

---

### TC-E-007: Tech Stack field on project (tag-based)

| Field | Detail |
|-------|--------|
| **Test ID** | TC-E-007 |
| **Priority** | P1 — High |
| **Type** | Functional |

**Steps:**
1. In a project's Tech Stack field, add tags: `React`, `Firebase`, `TailwindCSS`.
2. Save and reload.

**Expected Results:**
- Tags save correctly and display as chips/tags.
- Follows same duplicate prevention behavior as TC-D-004.

---

### TC-E-008: Achievements field accepts multi-line input

| Field | Detail |
|-------|--------|
| **Test ID** | TC-E-008 |
| **Priority** | P2 — Medium |
| **Type** | Functional |

**Steps:**
1. Enter 3 achievement bullet points in the Achievements field (using Enter for newlines).
2. Save and reload.

**Expected Results:**
- All 3 achievements are preserved with correct line breaks.

---

## Section F — Employment History

### TC-F-001: Add a new employment entry with all fields

| Field | Detail |
|-------|--------|
| **Test ID** | TC-F-001 |
| **Priority** | P0 — Critical |
| **Type** | Functional |

**Steps:**
1. Open Employment History section.
2. Click "Add Position."
3. Fill in: Company, Role, Start Date, End Date, Description, Tech Stack (tags), Achievements.
4. Save and reload.

**Expected Results:**
- Entry appears with all entered data intact.

---

### TC-F-002: "Currently employed here" / Present end date

| Field | Detail |
|-------|--------|
| **Test ID** | TC-F-002 |
| **Priority** | P1 — High |
| **Type** | Functional |

**Steps:**
1. Add a position with a Start Date but check "Currently Working Here" (or leave End Date blank/set to "Present").
2. Save and reload.

**Expected Results:**
- Entry shows "Present" or equivalent for the End Date.
- Value is stored appropriately (e.g., null or `"Present"` string).

---

### TC-F-003: End date cannot precede start date

| Field | Detail |
|-------|--------|
| **Test ID** | TC-F-003 |
| **Priority** | P1 — High |
| **Type** | Validation |

**Steps:**
1. Set Start Date to `January 2023` and End Date to `December 2022`.
2. Attempt to save.

**Expected Results:**
- Validation error: "End date must be after start date."
- Save is blocked.

---

### TC-F-004: Multiple positions — correct ordering

| Field | Detail |
|-------|--------|
| **Test ID** | TC-F-004 |
| **Priority** | P1 — High |
| **Type** | Functional |

**Steps:**
1. Add 3 employment entries with different date ranges.
2. Save and reload.

**Expected Results:**
- All 3 entries are listed. Default order is most recent first (or preserve entry order — document expected behavior).

---

### TC-F-005: Edit an existing employment entry

| Field | Detail |
|-------|--------|
| **Test ID** | TC-F-005 |
| **Priority** | P0 — Critical |
| **Type** | Functional |

**Steps:**
1. Edit the Role field on an existing entry.
2. Save and reload.

**Expected Results:** Updated role is reflected. Other entries unaffected.

---

### TC-F-006: Delete an employment entry

| Field | Detail |
|-------|--------|
| **Test ID** | TC-F-006 |
| **Priority** | P1 — High |
| **Type** | Functional |

**Steps:**
1. Delete one employment entry.
2. Reload.

**Expected Results:** Entry is permanently removed. Other entries are preserved.

---

### TC-F-007: Company name accepts unicode/international characters

| Field | Detail |
|-------|--------|
| **Test ID** | TC-F-007 |
| **Priority** | P2 — Medium |
| **Type** | Edge |

**Steps:**
1. Enter company name: `Ñoño & Asociados S.A.`.
2. Save and reload.

**Expected Results:** Company name is displayed correctly with all characters intact.

---

### TC-F-008: Required fields — Company and Role

| Field | Detail |
|-------|--------|
| **Test ID** | TC-F-008 |
| **Priority** | P1 — High |
| **Type** | Validation |

**Steps:**
1. Add an entry with no Company or Role.
2. Attempt to save.
3. Reload

**Expected Results:**
- Validation errors on Company and Role fields.
- Previous inputs remain.

---

### TC-F-009: Achievements field supports rich multi-line text

| Field | Detail |
|-------|--------|
| **Test ID** | TC-F-009 |
| **Priority** | P1 — High |
| **Type** | Functional |

**Steps:**
1. Enter 5 achievement bullets with quantified results (e.g., "Reduced load time by 40%").
2. Save and reload.

**Expected Results:**
- All 5 bullets are preserved with correct formatting and line breaks.

---

### TC-F-010: Employment history in optimization output

| Field | Detail |
|-------|--------|
| **Test ID** | TC-F-010 |
| **Priority** | P1 — High |
| **Type** | Integration |

**Steps:**
1. Save 2 employment entries.
2. Run an optimization.

**Expected Results:**
- Both entries appear in the tailored resume output.
- Master resume data is not mutated.

---

## Section G — Education

### TC-G-001: Add an education entry with all fields

| Field | Detail |
|-------|--------|
| **Test ID** | TC-G-001 |
| **Priority** | P0 — Critical |
| **Type** | Functional |

**Steps:**
1. Open Education section.
2. Fill in: School, Degree, Field of Study, Graduation Year.
3. Save and reload.

**Expected Results:** All fields saved and repopulated correctly.

---

### TC-G-002: Graduation Year validation

| Field | Detail |
|-------|--------|
| **Test ID** | TC-G-002 |
| **Priority** | P1 — High |
| **Type** | Validation |

**Steps:**
1. Enter `1800` as graduation year.
2. Enter `2100` as graduation year.
3. Enter `abcd` as graduation year.

**Expected Results:**
- Unrealistic years (pre-1950 or far future) trigger a warning or are rejected.
- Non-numeric input is rejected with a validation error.

---

### TC-G-003: Degree and Field of Study are required

| Field | Detail |
|-------|--------|
| **Test ID** | TC-G-003 |
| **Priority** | P2 — Medium |
| **Type** | Validation |

**Steps:**
1. Add an entry with School only.
2. Save.
3. Reload.

**Expected Results:** Save fails. Previous inputs remain.

---

### TC-G-004: Add multiple education entries

| Field | Detail |
|-------|--------|
| **Test ID** | TC-G-004 |
| **Priority** | P1 — High |
| **Type** | Functional |

**Steps:**
1. Add two education entries (e.g., BS and MS).
2. Save and reload.

**Expected Results:** Both entries are listed with correct data.

---

### TC-G-005: Delete an education entry

| Field | Detail |
|-------|--------|
| **Test ID** | TC-G-005 |
| **Priority** | P1 — High |
| **Type** | Functional |

**Steps:**
1. Delete one education entry.
2. Reload.

**Expected Results:** Entry removed. Remaining entries unaffected.

---

### TC-G-006: School name is required

| Field | Detail |
|-------|--------|
| **Test ID** | TC-G-006 |
| **Priority** | P1 — High |
| **Type** | Validation |

**Steps:**
1. Attempt to save an education entry with blank School field.

**Expected Results:** Validation error. Save blocked.

---

## Section H — References

### TC-H-001: Add a reference with all fields

| Field | Detail |
|-------|--------|
| **Test ID** | TC-H-001 |
| **Priority** | P1 — High |
| **Type** | Functional |

**Steps:**
1. Open References section.
2. Fill in: Name, Title, Company, Contact Details (email and/or phone).
3. Save and reload.

**Expected Results:** All fields saved correctly.

---

### TC-H-002: Contact Details field accepts email and phone

| Field | Detail |
|-------|--------|
| **Test ID** | TC-H-002 |
| **Priority** | P2 — Medium |
| **Type** | Functional |

**Steps:**
1. Enter both an email and phone number in the Contact Details field (or separate fields if provided).
2. Save and reload.

**Expected Results:** Both values are preserved.

---

### TC-H-003: All reference fields are optional except Name

| Field | Detail |
|-------|--------|
| **Test ID** | TC-H-003 |
| **Priority** | P2 — Medium |
| **Type** | Validation |

**Steps:**
1. Add reference with Name only.
2. Save.

**Expected Results:** Save succeeds.

---

### TC-H-004: Add multiple references

| Field | Detail |
|-------|--------|
| **Test ID** | TC-H-004 |
| **Priority** | P1 — High |
| **Type** | Functional |

**Steps:**
1. Add 3 references.
2. Save and reload.

**Expected Results:** All 3 references saved and listed correctly.

---

### TC-H-005: Delete a reference

| Field | Detail |
|-------|--------|
| **Test ID** | TC-H-005 |
| **Priority** | P1 — High |
| **Type** | Functional |

**Steps:**
1. Delete one reference.
2. Reload.

**Expected Results:** Reference removed. Others unaffected.

---

### TC-H-006: Reference Name is required

| Field | Detail |
|-------|--------|
| **Test ID** | TC-H-006 |
| **Priority** | P1 — High |
| **Type** | Validation |

**Steps:**
1. Leave Name blank and attempt to save a reference.

**Expected Results:** Validation error. Save blocked.

---

## Section I — Section UI Behavior (Collapse, Reorder)

### TC-I-001: Collapse and expand a section

| Field | Detail |
|-------|--------|
| **Test ID** | TC-I-001 |
| **Priority** | P1 — High |
| **Type** | UI |

**Steps:**
1. Click the collapse toggle on the Employment History section.
2. Verify section content is hidden.
3. Click again to expand.

**Expected Results:**
- Section collapses (content hidden, header remains visible).
- Section expands to show content again.
- Animation/transition is smooth (no layout jump).

---

### TC-I-002: All sections can be independently collapsed

| Field | Detail |
|-------|--------|
| **Test ID** | TC-I-002 |
| **Priority** | P2 — Medium |
| **Type** | UI |

**Steps:**
1. Collapse all 7 sections one by one.

**Expected Results:**
- All sections collapse independently.
- Collapsing one does not affect others.

---

### TC-I-003: Reorder sections via drag and drop

| Field | Detail |
|-------|--------|
| **Test ID** | TC-I-003 |
| **Priority** | P1 — High |
| **Type** | Functional / UI |

**Steps:**
1. Drag the "Education" section above "Employment History."
2. Release.
3. Save (if manual save required) and reload.

**Expected Results:**
- Section order visually updates on drop.
- New order persists after reload.

---

### TC-I-004: Reorder sections and verify optimization uses new order

| Field | Detail |
|-------|--------|
| **Test ID** | TC-I-004 |
| **Priority** | P2 — Medium |
| **Type** | Integration |

**Steps:**
1. Move "Portfolio Projects" above "Employment History."
2. Run an optimization.

**Expected Results:**
- Optimized resume respects the section order set in the master resume (or documents if optimization overrides ordering).

---

### TC-I-005: Drag handle is only visible when hovering (if applicable)

| Field | Detail |
|-------|--------|
| **Test ID** | TC-I-005 |
| **Priority** | P3 — Low |
| **Type** | UI |

**Steps:**
1. Hover over a section header.

**Expected Results:** Drag handle appears on hover. Not visible when not hovering.

---

### TC-I-006: Collapse state is preserved on page reload

| Field | Detail |
|-------|--------|
| **Test ID** | TC-I-006 |
| **Priority** | P2 — Medium |
| **Type** | Persistence |

**Steps:**
1. Collapse 3 sections.
2. Reload the page.

**Expected Results:** Sections remain collapsed after reload (if collapse state is persisted — document expected behavior if not).

---

### TC-I-007: Keyboard accessibility of collapse toggle

| Field | Detail |
|-------|--------|
| **Test ID** | TC-I-007 |
| **Priority** | P2 — Medium |
| **Type** | Accessibility |

**Steps:**
1. Tab to a section's collapse toggle.
2. Press Enter or Space.

**Expected Results:** Section toggles collapsed/expanded state via keyboard only.

---

## Section J — Multiple Profiles

### TC-J-001: Create a second master resume profile

| Field | Detail |
|-------|--------|
| **Test ID** | TC-J-001 |
| **Priority** | P0 — Critical |
| **Type** | Functional |

**Steps:**
1. From the editor or dashboard, create a second profile named "Product Management — 2026."
2. Add distinct contact info and skills to this profile.
3. Save.

**Expected Results:**
- Second profile is created and appears in the Profile Switcher.
- Data is isolated from Profile 1.

---

### TC-J-002: Switch between profiles using the Profile Switcher

| Field | Detail |
|-------|--------|
| **Test ID** | TC-J-002 |
| **Priority** | P0 — Critical |
| **Type** | Functional |

**Steps:**
1. With 2+ profiles, open the Profile Switcher.
2. Select Profile 2.
3. Verify Profile 2's data loads.
4. Switch back to Profile 1.

**Expected Results:**
- Correct data loads for each profile on switch.
- No data from one profile appears in another.

---

### TC-J-003: Profile data is strictly isolated

| Field | Detail |
|-------|--------|
| **Test ID** | TC-J-003 |
| **Priority** | P0 — Critical |
| **Type** | Functional / Data Integrity |

**Steps:**
1. Profile 1: Skills = `[React, Node.js]`. Profile 2: Skills = `[Excel, PowerPoint]`.
2. Switch to Profile 2 and verify skills.
3. Switch to Profile 1 and verify skills.

**Expected Results:**
- Profile 2 only shows `[Excel, PowerPoint]`.
- Profile 1 only shows `[React, Node.js]`.
- No cross-contamination.

---

### TC-J-004: Profile Switcher appears on the optimization form

| Field | Detail |
|-------|--------|
| **Test ID** | TC-J-004 |
| **Priority** | P1 — High |
| **Type** | Functional / Integration |

**Steps:**
1. Navigate to the optimization form.
2. Verify the Profile Switcher is present.

**Expected Results:**
- Profile Switcher dropdown or selector is visible.
- It lists all created profiles.

---

### TC-J-005: Optimization uses selected profile's data

| Field | Detail |
|-------|--------|
| **Test ID** | TC-J-005 |
| **Priority** | P0 — Critical |
| **Type** | Integration |

**Steps:**
1. Select Profile 2 in the optimization form.
2. Run an optimization.

**Expected Results:**
- Output reflects Profile 2's data (skills, employment, etc.).
- Profile 1's data does not appear.

---

### TC-J-006: Rename a profile

| Field | Detail |
|-------|--------|
| **Test ID** | TC-J-006 |
| **Priority** | P2 — Medium |
| **Type** | Functional |

**Steps:**
1. Rename Profile 1 from "Untitled" to "Backend Engineering."
2. Save and reload.

**Expected Results:**
- Profile Switcher reflects the new name.
- Existing data in the profile is unchanged.

---

### TC-J-007: Delete a profile

| Field | Detail |
|-------|--------|
| **Test ID** | TC-J-007 |
| **Priority** | P1 — High |
| **Type** | Functional |

**Steps:**
1. With 2 profiles, delete Profile 2.
2. Reload.

**Expected Results:**
- Profile 2 is removed from the Profile Switcher.
- Profile 1 remains with all its data intact.
- A confirmation dialog is shown before deletion.

---

### TC-J-008: Cannot delete the only remaining profile

| Field | Detail |
|-------|--------|
| **Test ID** | TC-J-008 |
| **Priority** | P1 — High |
| **Type** | Validation / Edge |

**Steps:**
1. Delete profiles until only 1 remains.
2. Attempt to delete the last profile.

**Expected Results:**
- Delete is blocked or a warning is shown: "You must have at least one profile."
- The last profile is not deleted.

---

### TC-J-009: Profile Switcher shows correct active profile indicator

| Field | Detail |
|-------|--------|
| **Test ID** | TC-J-009 |
| **Priority** | P2 — Medium |
| **Type** | UI |

**Steps:**
1. Switch to Profile 2 via the Profile Switcher.

**Expected Results:**
- Profile 2 is visually highlighted/checked as the active profile in the switcher.

---

## Section K — Data Persistence & Integrity

### TC-K-001: Auto-save or manual save persists all sections

| Field | Detail |
|-------|--------|
| **Test ID** | TC-K-001 |
| **Priority** | P0 — Critical |
| **Type** | Persistence |

**Steps:**
1. Fill in all 7 sections completely.
2. Save.
3. Close the browser tab.
4. Reopen the application and navigate to the editor.

**Expected Results:**
- All data from all sections is intact.

---

### TC-K-002: Unsaved changes prompt on navigation away

| Field | Detail |
|-------|--------|
| **Test ID** | TC-K-002 |
| **Priority** | P1 — High |
| **Type** | UI / Persistence |

**Steps:**
1. Make a change in the editor without saving.
2. Click to navigate away (e.g., to Dashboard).

**Expected Results:**
- A confirmation dialog appears: "You have unsaved changes. Are you sure you want to leave?"
- Choosing "Stay" keeps the user on the editor with changes intact.
- Choosing "Leave" navigates away (changes may be lost if no auto-save).

---

### TC-K-003: Data survives a browser refresh

| Field | Detail |
|-------|--------|
| **Test ID** | TC-K-003 |
| **Priority** | P0 — Critical |
| **Type** | Persistence |

**Steps:**
1. Save the resume.
2. Press F5 / Cmd+R to hard refresh.

**Expected Results:** All saved data is present after refresh.

---

### TC-K-004: Concurrent edit protection (same account, two tabs)

| Field | Detail |
|-------|--------|
| **Test ID** | TC-K-004 |
| **Priority** | P2 — Medium |
| **Type** | Concurrency / Edge |

**Steps:**
1. Open the editor in Tab A and Tab B with the same account.
2. Edit the headline in Tab A and save.
3. Edit the headline in Tab B and save.
4. Reload.

**Expected Results:**
- One of the saves wins (last-write-wins is acceptable).
- No data corruption or blank fields.
- Optionally: a conflict warning is shown.

---

### TC-K-005: Save failure shows an error and retains form data

| Field | Detail |
|-------|--------|
| **Test ID** | TC-K-005 |
| **Priority** | P1 — High |
| **Type** | Error Handling |

**Steps:**
1. Throttle network to offline using browser DevTools.
2. Make edits and click Save.

**Expected Results:**
- An error message appears: "Failed to save. Please try again."
- Form data is NOT cleared — the user's inputs remain visible in the form.
- Retry succeeds once network is restored.

---

## Section L — Edge Cases & Negative Tests

### TC-L-001: XSS injection in text fields

| Field | Detail |
|-------|--------|
| **Test ID** | TC-L-001 |
| **Priority** | P0 — Critical (Security) |
| **Type** | Security |

**Steps:**
1. Enter `<script>alert('XSS')</script>` into the Full Name, Headline, and Project Description fields.
2. Save and reload.

**Expected Results:**
- Scripts are not executed.
- Content is either stripped or displayed as escaped plain text (e.g., `&lt;script&gt;`).
- No alert dialogs appear.

---

### TC-L-002: SQL/NoSQL injection strings in fields

| Field | Detail |
|-------|--------|
| **Test ID** | TC-L-002 |
| **Priority** | P0 — Critical (Security) |
| **Type** | Security |

**Steps:**
1. Enter `' OR '1'='1` and `{"$gt": ""}` in text fields.
2. Save.

**Expected Results:**
- Values are treated as plain strings, stored safely.
- No database errors or unexpected behavior.

---

### TC-L-003: Extremely long input in a text field

| Field | Detail |
|-------|--------|
| **Test ID** | TC-L-003 |
| **Priority** | P2 — Medium |
| **Type** | Edge |

**Steps:**
1. Paste 10,000 characters into the Professional Summary paragraph field.
2. Save and reload.

**Expected Results:**
- Input is either accepted and stored correctly, or capped at a documented limit with a user-facing message.
- No application crash or data truncation without warning.

---

### TC-L-004: Emoji and Unicode in text fields

| Field | Detail |
|-------|--------|
| **Test ID** | TC-L-004 |
| **Priority** | P2 — Medium |
| **Type** | Edge |

**Steps:**
1. Enter `🚀 Full-Stack Dev 🌍` in the Professional Headline field.
2. Save and reload.

**Expected Results:**
- Emojis are displayed correctly.
- No encoding errors or broken characters.

---

### TC-L-005: Resume with no sections filled still saves

| Field | Detail |
|-------|--------|
| **Test ID** | TC-L-005 |
| **Priority** | P2 — Medium |
| **Type** | Edge |

**Steps:**
1. Create a blank profile.
2. Click Save without filling in any section.

**Expected Results:**
- Save succeeds.
- Profile is listed in the Profile Switcher as a valid (empty) profile.

---

### TC-L-006: Session expiry during editing

| Field | Detail |
|-------|--------|
| **Test ID** | TC-L-006 |
| **Priority** | P1 — High |
| **Type** | Edge / Auth |

**Steps:**
1. Open the editor.
2. Simulate session expiry (clear auth cookies or wait for timeout).
3. Attempt to save.

**Expected Results:**
- User is redirected to the login page.
- A message is shown: "Your session has expired. Please log in again."
- Ideally, in-progress edits are recoverable after re-login (or user is warned they may be lost).

---

### TC-L-007: Mobile responsiveness of the editor

| Field | Detail |
|-------|--------|
| **Test ID** | TC-L-007 |
| **Priority** | P1 — High |
| **Type** | UI / Responsive |

**Steps:**
1. Open the editor on a 375×812 mobile viewport (iPhone SE simulation).
2. Expand each section.
3. Enter data in at least 3 fields.
4. Save.

**Expected Results:**
- All sections are accessible and scrollable.
- Inputs are usable (no overlapping elements, no text cut off).
- Save succeeds on mobile.

---

### TC-L-008: Accessibility — keyboard-only navigation through the editor

| Field | Detail |
|-------|--------|
| **Test ID** | TC-L-008 |
| **Priority** | P2 — Medium |
| **Type** | Accessibility |

**Steps:**
1. Without using a mouse, Tab through every interactive element on the editor page.
2. Fill in the Full Name and one skill tag using keyboard only.
3. Save using keyboard.

**Expected Results:**
- All interactive elements are reachable via Tab.
- Focus indicators are clearly visible.
- Skill tag can be added by pressing Enter.
- Save button is reachable and activatable via Enter/Space.

---

*End of Test Suite — Master Resume Feature*  
*Total Test Cases: 85 | Sections Covered: 12*