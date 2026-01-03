# Score Extension Analytics

This document tracks all analytics in the [Score browser extension](https://getscore.app), as of **version 3.0.1+** on the Chrome Web Store.

**Last Updated:** January 2026

---

## Privacy-First Commitment (Version 3.0 - January 2026)

Score V3 represents our complete commitment to user privacy. We have **removed all personal data collection and link tracking** that existed in V2.

### What Changed in V3:

**NO LONGER COLLECTED:**
- User agent / browser information
- Operating system details
- URLs or page locations
- Image URLs
- Product titles, prices, or details
- Result counts or search timing
- Click result details (title, price, URL)
- Filter preferences
- Search types

**ONLY COLLECTED (minimal, non-identifiable data):**
- `extensionVersion` - Current extension version number
- `distinctId` - Anonymous user ID (Supabase user hash)
- Subscription status (active/inactive, subscription type)
- Error messages (for debugging and fixing bugs)

---

## Analytics Opt-Out

**Users have complete control.** You can disable ALL analytics tracking:

1. Open the Score modal on any product page
2. Click the filter icon to open Settings
3. Check **"Disable analytics tracking"**

When enabled, **zero analytics events** are sent to Mixpanel. This preference is stored locally in your browser and never leaves your device.

**Storage key:** `ANALYTICS-optOut` in `chrome.storage.local`

---

## What We Use Analytics For

We use minimal analytics **only** to:
- Understand which features are used (to prioritize development)
- Identify bugs and errors (to fix problems faster)
- Track subscription status (to provide Pro features)
- Measure extension adoption (install/update counts)

We **DO NOT** use analytics for:
- Advertising or retargeting
- Behavioral profiling
- Selling or sharing data
- Tracking your shopping or browsing history

---

## Third-Party Services

**Mixpanel:** We use Mixpanel to store analytics events.
- **Mixpanel Token:** `8f29c4724d93413d06968741ac2be51d`
- **Mixpanel Privacy Policy:** [https://mixpanel.com/legal/privacy-policy/](https://mixpanel.com/legal/privacy-policy/)
- **Data Retention:** Per Mixpanel's policy (30 days for event data)

**Your Rights:**
- You can opt-out of all tracking (see above)
- You can request data deletion by emailing getscoreapp@gmail.com
- You can view all analytics events in this document

---

## Common Properties

These properties are included with **every** event (when analytics is enabled):

### extensionVersion
- **Example:** `3.0.1`
- **Description:** Score extension version number
- **Why we collect it:** To identify which version users are on for debugging

### distinctId
- **Example:** `a3f7b2c1...` (hashed)
- **Description:** Anonymous user ID (Supabase user hash)
- **Why we collect it:** To count unique users without identifying them
- **Note:** This is a one-way hash that cannot be reversed to identify you

### subscriptionActive
- **Example:** `true` or `false`
- **Description:** Whether you have an active Score Pro subscription
- **Why we collect it:** To provide Pro features and track conversions

### subscriptionType
- **Example:** `PRO_UNLIMITED` or `null`
- **Description:** Your subscription plan type
- **Why we collect it:** To deliver the correct features for your plan

### subscriptionId
- **Example:** `sub_1A2B3C...`
- **Description:** Stripe subscription ID (if subscribed)
- **Why we collect it:** To validate subscription status

---

## Events Reference

Below is every analytics event we track, organized by category.

---

## Installation & Updates

### extension_firstTimeOnboard
**Fired when:** User installs the extension for the first time

**Additional Properties:** None

**Why we track it:** To count new installations

---

### extension_updateVersion
**Fired when:** User updates the extension to a new version

**Additional Properties:** None

**Why we track it:** To track update adoption rates

---

## User Authentication

### extension_setNewDistinctId
**Fired when:** User signs in to Score on the web

**Additional Properties:**
- `id` - User ID (hashed)

**Why we track it:** To link web and extension accounts

---

### extension_setUserError
**Fired when:** Error occurs during user setup

**Additional Properties:**
- `errorString` - Error message

**Why we track it:** To identify and fix sign-in bugs

---

### extension_getUserAndSubscriptionDetails
**Fired when:** Extension retrieves user and subscription details

**Additional Properties:**
- `userId` - User ID (hashed)
- `subscriptionId` - Subscription ID
- `subscriptionActive` - Boolean
- `subscriptionType` - Plan type

**Why we track it:** To confirm subscription sync

---

## Subscription Events

### extension_setSubscriptionComplete
**Fired when:** Subscription setup completes in extension

**Additional Properties:** None

**Why we track it:** To verify subscription activation

---

### extension_getSubscriptionActiveSuccess
**Fired when:** Successfully checked if subscription is active

**Additional Properties:**
- `active` - Boolean (true/false)

**Why we track it:** To monitor subscription validation

---

### extension_getSubscriptionActiveError
**Fired when:** Error checking subscription status

**Additional Properties:**
- `errorString` - Error message

**Why we track it:** To fix subscription checking bugs

---

## Search Events

### modal_performImageSearch
**Fired when:** User initiates an automatic image search

**Additional Properties:** None

**Why we track it:** To count total searches

---

### modal_performImageSearchRightClick
**Fired when:** User right-clicks an image and selects "Search with Score"

**Additional Properties:** None

**Why we track it:** To measure right-click feature usage

---

### modal_performImageSearchCropSearch
**Fired when:** User uses the screenshot/crop search feature

**Additional Properties:** None

**Why we track it:** To measure screenshot search usage

---

### extension_performImageSearchComplete
**Fired when:** Image search completes successfully

**Additional Properties:** None

**Why we track it:** To track search success rate

---

### extension_imageSearchApiError
**Fired when:** Error occurs during image search API call

**Additional Properties:**
- `errorString` - Error message

**Why we track it:** To identify and fix search bugs

---

## Search Limit Events

### extension_dailyLimitReached
**Fired when:** User hits daily search limit (10 for free users)

**Additional Properties:**
- `extendCount` - Number of extensions used
- `extensionsExhausted` - Boolean (true if all 3 extensions used)

**Why we track it:** To understand limit usage patterns

---

### extension_extendDailyLimit
**Fired when:** User uses one of their 3 "One More Search" extensions

**Additional Properties:** None

**Why we track it:** To measure extension usage

---

## Modal Interaction Events

### modal_openoptions
**Fired when:** User clicks the "X cheaper options" button on a product page

**Additional Properties:**
- `loading` - Boolean (whether results were still loading)

**Why we track it:** To measure feature engagement

---

### sticky_openExtension
**Fired when:** User clicks the floating Score button on a product page

**Additional Properties:** None

**Why we track it:** To track sidebar usage

---

### modal_closeExtension
**Fired when:** User closes the Score modal

**Additional Properties:** None

**Why we track it:** To track engagement duration

---

### modal_clickLogo
**Fired when:** User clicks the Score logo in the modal

**Additional Properties:** None

**Why we track it:** To track logo clicks

---

### modal_openScoreProPage
**Fired when:** User clicks to open the Score Pro upgrade page

**Additional Properties:**
- `source` - Where the click came from (e.g., "modal", "screenshot")

**Why we track it:** To measure upgrade page views and attribution

---

## Result Interaction Events

### modal_clickResult
**Fired when:** User clicks on a search result

**Additional Properties:** None

**Why we track it:** To measure result click-through rate

**Note:** In v2.0, this event included title, price, URL, and merchant. **In v3.0+, we collect NONE of that data.**

---

## Error Events

### modal_cannotFindImage
**Fired when:** Extension cannot find an image to search

**Additional Properties:** None

**Why we track it:** To identify pages where Score doesn't work

---

### modal_amazonCannotParseBox
**Fired when:** Extension cannot parse Amazon product page

**Additional Properties:** None

**Why we track it:** To fix Amazon parsing bugs

---

### modal_cannotParseJsonLd
**Fired when:** Extension cannot parse JSON-LD product data

**Additional Properties:** None

**Why we track it:** To fix product page parsing

---

### page_cannotLoadOnPageLoadOrChange
**Fired when:** Generic error during page load or navigation

**Additional Properties:**
- `errorName` - Type of error (e.g., "TypeError")
- `errorMessage` - Error description

**Why we track it:** To identify and fix page loading bugs

---

## Notification Events

### extension_getToastSuccess
**Fired when:** Extension successfully fetches a notification from Score's servers

**Additional Properties:** None

**Why we track it:** To verify notification delivery

---

### extension_getToastError
**Fired when:** Error fetching notification

**Additional Properties:**
- `errorString` - Error message

**Why we track it:** To fix notification bugs

---

### extension_clickToast
**Fired when:** User clicks on a notification

**Additional Properties:** None

**Why we track it:** To measure notification engagement

**Note:** In v2.0, this included notification title and link. **In v3.0+, we collect NONE of that data.**

---

## Site Hiding Events

### extension_hideSite
**Fired when:** User disables Score on a specific website

**Additional Properties:** None

**Why we track it:** To understand which sites users hide Score on

**Note:** We do NOT track which specific site was hidden (no URLs collected)

---

### extension_unhideSite
**Fired when:** User re-enables Score on a previously hidden site

**Additional Properties:** None

**Why we track it:** To track re-enablement

---

### extension_unhideAllSites
**Fired when:** User re-enables Score on all hidden sites

**Additional Properties:** None

**Why we track it:** To track bulk re-enablement

---

## Event Flow Example

Here's what happens when you use Score:

```
1. Install Extension
   → extension_firstTimeOnboard

2. Sign In on Website
   → extension_setNewDistinctId
   → extension_getUserAndSubscriptionDetails

3. Visit Product Page
   → modal_performImageSearch
   → extension_performImageSearchComplete

4. Click Floating Button
   → sticky_openExtension

5. Click a Result
   → modal_clickResult

6. Close Modal
   → modal_closeExtension
```

**Total data points collected:** 6 events with only version, anonymous ID, and subscription status.

**What we DON'T know:**
- What product you searched for
- What website you were on
- What result you clicked
- How much it cost
- Where you bought it

---

## Version History

### Version 3.0.1+ (January 2026)
**Privacy-First Redesign**
- Removed all URLs, images, product details, result data
- Removed user agent and browser info
- Removed timing and performance metrics
- Added complete analytics opt-out
- Reduced to minimal, non-identifiable data only

### Version 2.0.0 (2024)
**Previous Analytics**
- Tracked URLs, images, search results, clicks
- Collected user agent, browser version, OS
- Measured result counts and timing
- Much more invasive data collection

### Version 1.x (2023)
**Initial Release**
- Similar to v2.0 tracking model

---

## Contact & Questions

**Have privacy concerns?** We're here to listen.

- **Email:** getscoreapp@gmail.com
- **Reddit:** [r/ScoreApp](https://www.reddit.com/r/ScoreApp/)
- **X (Twitter):** [@GetScoreApp](https://x.com/GetScoreApp)

**Want to verify this?**
- View the extension source code (it's packaged with the extension)
- Check network requests in Chrome DevTools
- Enable analytics opt-out and confirm zero Mixpanel requests

---

## Related Documents

- **Privacy Policy:** [https://getscore.app/privacy](https://getscore.app/privacy)
- **Terms of Service:** [https://getscore.app/terms](https://getscore.app/terms)
- **Chrome Web Store:** [Score Extension](https://chrome.google.com/webstore/detail/score-app-find-great-deal/bcppghiggoobhkjlkfpmonlcigffpime)

---

**Summary:** Score V3 collects the absolute minimum data needed to operate and fix bugs. Your shopping activity is private. We don't track, sell, or share your browsing history. Period.
