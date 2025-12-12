# Exploratory Testing Report

**Tester:** Nafiz Al Zawad  
**Date:** 6–7 December 2025  
**Duration:** 40 minutes

## Platforms Tested:
- **Windows 11** (Chrome, Edge)
- **Moto Edge 50** (Android 15 – Chrome, Opera, App v1.0.1 & 1.0.5)
- **iPhone 14 Pro Max** (iOS – Chrome)

## Scope:
- Navigation behavior
- Contact form validation
- EchoGPT login, registration, and chatbot
- Offline behavior
- Layout/UI behavior on mobile
- Orientation changes
- Unexpected inputs (invalid emails, no internet, rapid actions)

---

## Exploratory Charter 1 – Website Navigation & Routing
**Goal:** Discover any broken links, routing failures, or navigation issues across both websites.  
**Approach:** Rapid clicking between menu and footer links, switching between browsers, opening multiple links quickly.

### Findings:
- **Major Issue:** Navigation links in the header and footer fail to redirect across all browsers.
- Footer links such as “About Us” and “Blog” do not respond at all.
- No console error message is shown, but redirection does not happen.

### Severity:
- **Critical**

### Evidence:
- All test cases for navigation (TC-002) failed across all devices.
- Execution log shows failure on Windows, Android, and iOS.

---

## Exploratory Charter 2 – Contact Form Behavior
**Goal:** Validate how the form behaves with valid, invalid, and empty inputs.  
**Approach:** Try various combinations of email formats, empty fields, rapid submission, and edge-case formats.

### Findings:
- Valid email input still triggers a false “Invalid email” warning under the Subject field.
- Invalid emails (e.g., invalid@mail) are sometimes accepted or trigger validation under the wrong field.
- Form accepts submissions even with poor formatting in some cases.

### Severity:
- **High**

### Evidence:
- TC-003, TC-004, TC-005 failures.
- Execution log notes inconsistent validation behavior.

---

## Exploratory Charter 3 – EchoGPT Login / Registration
**Goal:** Identify security and validation gaps.  
**Approach:** Test with incorrect formats, reused emails, missing fields, and rapid submissions.

### Findings:
- Login accepts incorrect email format (missing TLD) and proceeds to OTP screen.
- Registration form accepts emails that already exist in the database without showing a warning.

### Severity:
- **High (security/data integrity)**

### Evidence:
- TC-014 and TC-015 failed on all platforms.
- Bugs BG-003 and BG-004 raised.

---

## Exploratory Charter 4 – Chatbot & Network Error Handling
**Goal:** Understand chatbot’s response handling and system stability when network is lost.  
**Approach:** Input various messages, upload wrong file types, disable network mid-response, throttle bandwidth.

### Findings:
- With internet turned off, no user-facing error message appears.
- The page becomes unresponsive with no feedback.
- File upload test not fully executable without premium subscription.

### Severity:
- **Medium**

### Evidence:
- TC-021 failed on all web platforms.
- Bug BG-005 raised.

---

## Exploratory Charter 5 – Mobile UI & Orientation
**Goal:** Assess responsiveness and orientation stability.  
**Approach:** Rotate screens, open side menus, interact with chatbot, check mobile layout.

### Findings:
- Misaligned buttons in the Pricing section (ATS website).
- History list in EchoGPT mobile does not load properly from the “New Chat” section.
- Orientation change causes text clipping in EchoGPT Android app.

### Severity:
- **Medium**

### Evidence:
- TC-007, TC-020, TC-026 failures.
- Screens in execution log show alignment issues.

---

## Overall Exploratory Conclusion:
The exploratory session revealed critical navigation failures, validation loopholes, and UI inconsistencies, many of which significantly impact user experience and business workflows. These align with formal test failures and bug reports, confirming the reliability of findings.
