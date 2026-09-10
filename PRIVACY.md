# Privacy policy — NU Professor Ratings

Effective September 10, 2026. This policy describes version 1.0.0.

NU Professor Ratings is an unofficial browser extension that displays RateMyProfessors information in Northeastern Banner. It has no developer-operated backend.

## Data read and purpose

On the supported Banner registration pages, the extension reads instructor names, course subject/description, course number, and course title from class tables. It uses these fields to identify and distinguish professor candidates and place ratings beside the correct instructor. It also reads the minimum DOM structure and visibility/layout information needed to locate these fields and display the card.

It does not intentionally read or collect student names, account identity, Northeastern credentials, CRNs, schedules or registration selections, payment information, or browsing history. It does not intercept registration requests or automate registration. No code runs on unrelated websites.

## Requests to RateMyProfessors

Metadata lookup requests are sent directly from the browser to `https://www.ratemyprofessors.com/graphql` over HTTPS. Their application payload contains a normalized professor-name search, a fixed Northeastern University school filter, pagination settings/cursors, and a fixed query for the fields needed to identify professors and display ratings. Course context, raw Banner text, account identity, and registration information are not included.

The request uses `credentials: 'omit'`: no Northeastern or RMP login credentials/cookies are supplied by the extension. As the network recipient, RMP receives the professor query and ordinary connection/request information, such as the source IP address and browser-generated headers. Requests are not anonymous to the receiving service.

Returned metadata includes professor identity, school/department, rating average/count, difficulty, would-take-again percentage, and profile identifiers. The extension does not request review text. It allowlists metadata before using or caching it; unsolicited review/comment fields are not retained.

## Local memory and retention

The extension uses temporary JavaScript memory, not `chrome.storage`, local storage, a database, files, or browser synchronization. The tab and service worker each maintain bounded lookup caches (up to 250 entries), sharing duplicate requests. Successful and empty lookups are eligible for reuse for 30 minutes. Failures are eligible for short reuse, normally 30 seconds or longer during rate limiting. Expiry ends reuse; it does not guarantee immediate deletion from memory. Entries are replaced or evicted during later lookups and disappear when their tab/worker execution context ends. Closing/reloading Banner clears the tab cache; stopping the worker clears its separate cache. Reloading the extension and Banner resets both contexts.

Rendered row details may remain in memory and on the page until those rows are replaced or the page is closed/refreshed. The extension does not poll existing rows for new ratings. Browser-managed network caches and browser diagnostics are outside the extension's own storage implementation.

## Logging, analytics, and sharing

There are no analytics, tracking pixels, advertising SDKs, or automatic crash-report uploads. Successful/recoverable outcomes are quiet by default. Unexpected failures can create local browser-console warnings. If a developer manually enables the local `DEBUG` constant, detailed professor/course resolution diagnostics are printed to the local console. The extension does not upload those logs; retention of console output is controlled by the browser and the user.

The extension does not sell data or transfer it to advertising, marketing, data-broker, or credit-scoring services. It sends only the described requests to RMP to provide its single purpose. Its use of data adheres to the Chrome Web Store User Data Policy, including the Limited Use requirements.

## Links and services outside the extension

Clicking a badge/card opens the RMP professor page as a normal new-tab website visit. That website may use its own cookies and collect data according to [RMP's privacy policy](https://www.ratemyprofessors.com/privacy); the extension's credential-free lookup policy does not govern ordinary website visits. Profile links use `noopener noreferrer`.

Northeastern controls Banner authentication. The extension neither requests nor stores Northeastern passwords, tokens, or session cookies. GitHub and the Chrome Web Store may process information when you visit the repository/store, install an item, or voluntarily submit a report under their own policies. Such reports are not collected automatically by this extension.

## Questions and changes

Use the repository's issue tracker or the support contact on its Chrome Web Store listing, once published. Do not send sensitive account information in public reports. Any future changes to the extension's data practices must be reflected in this policy and the store disclosures before release.
