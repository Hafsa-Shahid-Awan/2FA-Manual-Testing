# BUG-01: Recovery Codes Not Downloading on Android

| Field | Details |
|---|---|
| Bug ID | BUG-01 |
| Module | Two-Factor Authentication |
| Platform | Android Mobile Application |
| Severity | Medium |
| Priority | Medium |
| Status | Unresolved |

## Description
The Download button displays a successful download confirmation message, but no recovery codes file appears in the device's Downloads folder.

## Preconditions
- User is logged into the Android application.
- Two-Factor Authentication is enabled.
- Recovery codes are generated and available.

## Steps to Reproduce
1. Open the Android mobile application.
2. Navigate to 2FA settings.
3. Open the recovery codes section.
4. Tap the Download button.
5. Observe the success message.
6. Check the device's Downloads folder.

## Expected Result
Recovery codes should be downloaded and saved to the device's Downloads folder.

## Actual Result
A successful download message is displayed, but no file is saved in the Downloads folder.

## Additional Observation
The Copy option works as expected.

## Reproducibility
Reproducible during testing.

## Impact
Users may believe their recovery codes have been downloaded when no file is actually available.

## Evidence
Not attached due to company confidentiality.
