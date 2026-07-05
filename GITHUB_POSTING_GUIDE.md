# GitHub Posting Guide

Use this guide when creating the public GitHub repository.

## Suggested repository name

```text
gohighlevel-gtm-form-tracker
```

Alternative names:

```text
ghl-gtm-form-tracker
gohighlevel-form-tracker
gohighlevel-dataLayer-form-tracker
gohighlevel-confirmation-form-tracker
```

## Repository description

```text
Confirmation-render-based GoHighLevel form tracking for Google Tag Manager. Tracks inline and iframe forms with consent gating, PII redaction, dedupe, optional hashing, and SPA support.
```

## Suggested topics

```text
google-tag-manager
gtm
dataLayer
ga4
gohighlevel
ghl
leadconnector
form-tracking
conversion-tracking
server-side-gtm
meta-capi
enhanced-conversions
analytics
javascript
```

## Files to publish

```text
README.md
LICENSE
CHANGELOG.md
.gitignore
gohighlevel-form-tracker.js
gohighlevel-form-tracker.gtm.html
GITHUB_POSTING_GUIDE.md
```

## First commit message

```text
Initial GoHighLevel GTM form tracker release
```

## Release title

```text
GoHighLevel GTM Form Tracker v3.0.1
```

## Release notes

```text
Initial standalone GoHighLevel release.

Includes:
- Inline form success/failure tracking
- Iframe form success tracking via verified postMessage payloads
- dataLayer events for success, failure, interaction, and initialization
- Consent detection for Google Consent Mode v2, OneTrust, and Cookiebot
- PII redaction when consent is denied
- Optional SHA-256 hashing for email and phone
- Duplicate success suppression
- SPA route-change support
- Raw JS and GTM Custom HTML versions
```

## Publish from local terminal

If the GitHub repo already exists and is empty:

```bash
cd "/Users/iyke-abel/Documents/Form Trackers/gohighlevel-gtm-form-tracker"
git init
git add README.md LICENSE CHANGELOG.md .gitignore gohighlevel-form-tracker.js gohighlevel-form-tracker.gtm.html GITHUB_POSTING_GUIDE.md
git commit -m "Initial GoHighLevel GTM form tracker release"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/gohighlevel-gtm-form-tracker.git
git push -u origin main
```

If this folder is already a Git repo, skip `git init`.

## GitHub UI checklist

1. Create a new public repository.
2. Use the suggested description above.
3. Do not initialize with README, license, or gitignore if you are pushing these files from local.
4. Push the local files.
5. Add the suggested topics in the repo sidebar.
6. Confirm the README renders correctly.
7. Open `gohighlevel-form-tracker.js` and confirm it does not include `<script>` tags.
8. Open `gohighlevel-form-tracker.gtm.html` and confirm it does include `<script>` tags.
9. Create release `v3.0.1`.
10. Paste the release notes above.

## Pre-publish QA

Before announcing it publicly:

1. Install `gohighlevel-form-tracker.gtm.html` in a GTM Preview container.
2. Submit a real GHL inline form with valid data.
3. Submit invalid inline data and confirm `ghl_form_failed` fires.
4. Submit a real GHL iframe form and confirm `ghl_form_success` fires.
5. Confirm booking/calendar iframe messages do not fire lead events.
6. Confirm `ec_tracker_initialized` fires once.
7. Confirm `ec_form_interaction` fires once for inline forms after input.
8. Test a redirect action and check `ec_detection_method`.
9. Test late-loaded popup iframe forms.
10. Test `debug:true` only in preview.
11. Test `pii:false` through `EC_FORM_CONSENT_CHECK` and confirm raw PII is removed.
12. Confirm raw PII is not mapped into GA4 event parameters.
13. Check `window._ecFormTrackers.ghl.status()` in the browser console.

## Important README promise

Keep the README privacy wording aligned with the code. If you change dedupe, storage, hashing, postMessage parsing, or consent behavior later, update the README in the same commit.
