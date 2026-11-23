# Two-Factor Authentication (2FA) — Manual Testing Project

![Testing](https://img.shields.io/badge/Testing-Manual%20Testing-blue)
![Status](https://img.shields.io/badge/Status-Completed-success)
![Test Cases](https://img.shields.io/badge/Test%20Cases-22-informational)
![Defects](https://img.shields.io/badge/Confirmed%20Defects-1-red)

## Project Overview

This project focuses on the manual testing of a Two-Factor Authentication (2FA) feature integrated with an authenticator application that generates Time-Based One-Time Passwords (TOTP).

The objective was to evaluate authentication functionality, reliability, recovery code management, account protection, and session handling through positive and negative testing.

The testing process also involved identifying, reproducing, and documenting functional defects.

## Testing Information

| Attribute | Details |
|---|---|
| Project | Two-Factor Authentication (2FA) |
| Testing Type | Manual Testing |
| Authentication Method | TOTP |
| Platforms | Web Application and Android Mobile Application |
| Test Cases Executed | 22 |
| Passed | 21 |
| Failed | 1 |
| Confirmed Defects | 1 |
| Status | Completed |

## Testing Objectives

- Verify 2FA setup using an authenticator application.
- Validate TOTP generation, expiration, and authentication.
- Test invalid, expired, and reused authentication codes.
- Verify recovery code generation and single-use functionality.
- Evaluate account protection after repeated failed attempts.
- Test 2FA activation, deactivation, and reactivation.
- Validate session handling and unauthorized access prevention.
- Identify and document functional defects.

## Testing Scope

- 2FA Setup and QR Code Verification
- TOTP Authentication
- Login Verification
- Recovery Code Management
- Failed Login Attempt Restrictions
- 2FA Activation and Deactivation
- Access Control
- Session Management

## Testing Methodology

### 1. Happy Path Testing

**Objective:** Verify successful application behavior when valid inputs and credentials are provided.

Scenarios covered:

- Scanning the QR code using an authenticator application.
- Activating 2FA with a valid TOTP.
- Logging in with a valid authentication code.
- Logging in using a valid recovery code.
- Copying generated recovery codes.
- Disabling 2FA using the correct password.
- Logging in after disabling 2FA.
- Re-enabling 2FA using a newly generated QR code.
- Authenticating using a newly generated TOTP.
- Verifying generation of a new code after its validity interval.

**Result: 10 Passed**

### 2. Negative Testing

**Objective:** Verify that invalid, expired, or previously consumed authentication credentials are rejected.

Scenarios covered:

- Submitting an invalid TOTP during setup.
- Submitting an expired TOTP during setup.
- Logging in with an invalid TOTP.
- Logging in with an expired TOTP.
- Reusing a previously accepted TOTP within its original validity period.
- Reusing a previously consumed recovery code.
- Attempting to use the previous authenticator key after re-enabling 2FA.

**Result: 7 Passed**

### 3. Security & Access Control Testing

**Objective:** Evaluate authentication enforcement and basic protection against unauthorized access.

Scenarios covered:

- Triggering login restrictions through repeated incorrect authentication attempts.
- Accessing the protected dashboard URL without authentication.

**Result: 2 Passed**

### 4. Session Management Testing

**Objective:** Verify authentication behavior across browser navigation and separate sessions.

Scenarios covered:

- Using browser Back and refresh after logout.
- Logging in from a separate browser session while 2FA is enabled.

**Result: 2 Passed**

### 5. Recovery Code Download Testing

**Objective:** Verify that generated recovery codes can be downloaded and accessed on Android.

Scenario:

- Attempting to download recovery codes.
- Checking the Android Downloads folder.
- Repeating the download attempt to verify reproducibility.

**Result: 1 Failed**

## Test Execution Summary

| Testing Category | Executed | Passed | Failed |
|---|---:|---:|---:|
| Happy Path Testing | 10 | 10 | 0 |
| Negative Testing | 7 | 7 | 0 |
| Security & Access Control | 2 | 2 | 0 |
| Session Management | 2 | 2 | 0 |
| Recovery Code Download | 1 | 0 | 1 |
| **Total** | **22** | **21** | **1** |

**Pass Rate:** 95.45%  
**Fail Rate:** 4.55%

## Defect Report

### BUG-01: Recovery Codes Are Not Downloaded Despite Success Notification

| Attribute | Details |
|---|---|
| Defect ID | BUG-01 |
| Module | 2FA — Recovery Codes |
| Platform | Android Mobile Application |
| Severity | Medium (Initial Assessment) |
| Priority | Medium (Provisional) |
| Status | Confirmed and Reproducible |

**Preconditions:**

- Two-Factor Authentication is enabled.
- Recovery codes have been generated.

**Steps to Reproduce:**

1. Navigate to the Recovery Codes section.
2. Tap the Download option.
3. Observe the success notification.
4. Open the Android Downloads folder.
5. Repeat the download attempt.

**Expected Result:**

Recovery codes should be downloaded successfully as a file and made accessible to the user.

**Actual Result:**

The application displays a successful download notification, but no file is available in the Android Downloads folder. The issue occurs repeatedly.

**Additional Observation:**

The Copy Recovery Codes functionality works as expected.

**Impact:**

Users may believe their recovery codes have been saved successfully when no file has actually been downloaded. This could create difficulties recovering account access if the authenticator application becomes unavailable.

**Recommendation:**

Investigate Android download handling and ensure that a success notification is displayed only after the file has been successfully generated and made accessible.

## Key Testing Observations

- Eight recovery codes were provided after initial 2FA activation.
- Each recovery code was intended for single use.
- Previously consumed recovery codes were rejected.
- A previously accepted TOTP was rejected when reused within its original validity period.
- Repeated incorrect authentication attempts triggered a login restriction.
- Re-enabling 2FA generated a new QR code, and the previous authenticator key stopped working.
- Protected dashboard access was restricted after logout and when accessed without authentication.
- Recovery code copying worked, while recovery code downloading failed on Android.

## Testing Limitations

- Testing was limited to the available application features and tested environments.
- No source-code review or backend security assessment was performed.
- The exact failed-attempt threshold and login restriction duration were not established.
- Testing did not constitute a comprehensive penetration test or security certification.
- Confidential screenshots and company-identifying information have been excluded.

## Final QA Assessment

The tested 2FA functionality behaved as expected across the majority of executed test scenarios, including setup, TOTP verification, recovery code validation, account access, and session handling.

One reproducible defect was identified in the Android mobile application: recovery codes were not downloaded despite the application displaying a successful download notification.

The issue requires further investigation to ensure users can reliably save their recovery codes.

**Overall Assessment:** Core 2FA functionality passed the tested scenarios, with one confirmed defect requiring attention.

## Skills Demonstrated

Manual Testing · Functional Testing · Happy Path Testing · Negative Testing · Authentication Testing · TOTP Validation · Recovery Code Testing · Security-Oriented Testing · Session Management · Access Control Testing · Defect Identification · Bug Reporting · Test Documentation

## Confidentiality Notice

This project report has been anonymized for portfolio presentation. Company names, application identifiers, private URLs, authentication secrets, recovery codes, and confidential screenshots have been excluded.

No confidential company information is included in this repository.
