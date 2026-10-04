# Accessibility Baseline & Repository Architecture Audit

**Internship Task:** 02  
**Audited Website:** National Portal of India  
**URL:** https://www.india.gov.in/  
**Audit Type:** Accessibility baseline + keyboard-only navigation + repository architecture review

---

## 1. Introduction

The purpose of this task is to reverse-engineer a real public-service website from an accessibility and software-architecture perspective.

The selected website is the **National Portal of India**. It provides citizens with government information, online services, schemes and other public resources.

The audit has two main parts:
1. Accessibility baseline.
2. Repository architecture and project skeleton.

---

## 2. Audit Method

### Tools and techniques

- Google Chrome Lighthouse
- Keyboard-only navigation
- Browser inspection
- Manual accessibility review
- Repository structure analysis

### Lighthouse procedure

1. Open `https://www.india.gov.in/`.
2. Open Chrome DevTools.
3. Select **Lighthouse**.
4. Select **Accessibility**.
5. Run the audit in the desired device mode.
6. Save a screenshot of the Accessibility result.
7. Record the exact score and failed/flagged audits in the table below.

### Keyboard-only procedure

1. Open the website.
2. Do not use the mouse.
3. Press `Tab` repeatedly.
4. Use `Shift + Tab` to move backward.
5. Use `Enter` or `Space` to activate controls.
6. Check whether the focus indicator is visible.
7. Check whether menus, search, buttons and links can be reached.
8. Record any control that cannot be reached or operated.

---

## 3. Lighthouse Evidence

**Insert screenshot:** `docs/screenshots/lighthouse-accessibility.png`

**Lighthouse Accessibility Score:** `________ / 100`

**Date tested:** `04 October 2026`

**Device mode:** `Desktop / Mobile: __________`

> The exact Lighthouse score should be copied from the actual Lighthouse run. It is intentionally not fabricated in this report.

---

## 4. Keyboard Navigation Evidence

**Insert screenshots:**
- `docs/screenshots/keyboard-focus-01.png`
- `docs/screenshots/keyboard-focus-02.png`
- `docs/screenshots/keyboard-focus-03.png`

### Keyboard test checklist

| Test | Result | Evidence |
|---|---|---|
| Tab reaches navigation controls | Pass / Needs review | Screenshot |
| Search control is keyboard reachable | Pass / Needs review | Screenshot |
| Interactive buttons can be activated | Pass / Needs review | Screenshot |
| Focus indicator is visible | Pass / Needs review | Screenshot |
| No keyboard trap observed | Pass / Needs review | Screenshot |

---

## 5. Five Accessibility / Architecture Issues

The following five items are the issues to investigate and document during the actual audit. Attach Lighthouse or browser evidence before final submission.

### Issue 1 — Image alternative text

**Category:** Accessibility  
**Priority:** Medium

**Observation to verify:** Some image elements may not communicate useful alternative text to screen-reader users.

**Impact:** A user who cannot see images may miss important information when the image carries meaning.

**Remediation:**
- Provide meaningful `alt` text for informative images.
- Use empty `alt=""` for decorative images.
- Avoid repeating nearby visible text in the alt attribute.

**Evidence:** Add Lighthouse screenshot or DevTools evidence.

---

### Issue 2 — Link / button naming

**Category:** Accessibility  
**Priority:** High

**Observation to verify:** Interactive elements should have accessible, descriptive names.

**Impact:** Screen-reader users depend on accessible names to understand what a link or button does.

**Remediation:**
- Use descriptive visible text.
- Add an accessible name where required.
- Avoid vague labels such as “Click here” when the purpose is unclear.

**Evidence:** Add Lighthouse screenshot or DOM inspection screenshot.

---

### Issue 3 — Keyboard focus visibility

**Category:** Accessibility  
**Priority:** High

**Observation to verify:** Check whether the keyboard focus indicator is consistently visible while using `Tab`.

**Impact:** Keyboard users may lose track of their current position on a complex page.

**Remediation:**
- Keep a strong visible `:focus` / `:focus-visible` style.
- Do not remove browser focus outlines without providing an equivalent indicator.

**Evidence:** Add keyboard navigation screenshot.

---

### Issue 4 — Heading / landmark structure

**Category:** Accessibility + Architecture  
**Priority:** Medium

**Observation to verify:** Review the page heading hierarchy and semantic landmarks such as `header`, `nav`, `main`, `footer` and complementary regions.

**Impact:** Screen-reader users use headings and landmarks to navigate large pages quickly.

**Remediation:**
- Maintain a logical heading hierarchy.
- Use semantic HTML landmarks.
- Ensure the main content has a clear `main` region.

**Evidence:** Add DevTools or Lighthouse evidence.

---

### Issue 5 — Large-page component and repository boundaries

**Category:** Architecture  
**Priority:** Medium

**Observation:** A public portal contains many functional areas such as services, schemes, information categories and citizen resources.

**Impact:** If all frontend, backend, documentation and tests are mixed together, maintenance becomes difficult.

**Remediation:**
- Separate `client`, `server`, `docs` and `test`.
- Keep API/business logic outside the UI layer.
- Document boundaries and the first vertical feature slice.

**Evidence:** Repository architecture tree included in this submission.

---

## 6. Remediation Priority

| Priority | Issue | Recommended action |
|---|---|---|
| High | Link/button accessible names | Fix unclear interactive names |
| High | Keyboard focus visibility | Ensure visible keyboard focus |
| Medium | Image alternative text | Add meaningful or decorative alt handling |
| Medium | Heading/landmark structure | Improve semantic navigation |
| Medium | Repository boundaries | Maintain client/server/docs/test separation |

---

## 7. Repository Architecture

```text
internship-task-02/
│
├── client/
│   ├── index.html
│   └── README.md
│
├── server/
│   └── README.md
│
├── docs/
│   ├── README.md
│   ├── accessibility-audit-report.md
│   └── screenshots/
│
├── test/
│   └── README.md
│
├── .gitignore
└── README.md
```

### Client boundary
Handles presentation, navigation, accessibility and API communication.

### Server boundary
Handles API routes, business rules, validation and data operations.

### Documentation boundary
Contains architecture decisions, audit findings and evidence.

### Test boundary
Contains unit, integration and accessibility tests.

---

## 8. First Vertical Feature Slice

### Feature: Public Service Search

```text
User
  ↓
Accessible Search UI
  ↓
GET /api/services
  ↓
Server/API
  ↓
Service Data
  ↓
Search Results
```

Accessibility requirements for this feature:
- Keyboard-accessible search.
- Visible focus indicator.
- Label associated with the search input.
- Clear error/status messages.
- Meaningful button names.
- Responsive layout.

---

## 9. Conclusion

This task establishes an accessibility baseline for a real public-service website and converts the findings into an implementation-ready repository architecture.

The repository separates client, server, documentation and testing responsibilities. The first planned feature slice is a keyboard-accessible public-service search.

The final proof package should contain:
- Lighthouse accessibility screenshot
- Keyboard navigation screenshots
- Five documented issues
- Repository architecture tree
- GitHub repository link
- Setup-ready project skeleton
- README documentation
