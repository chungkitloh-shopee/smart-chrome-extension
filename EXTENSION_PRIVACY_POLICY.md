# DW Knowledge Helper Privacy Policy

Last updated: November 10, 2026.

This policy describes DW Knowledge Helper version 1.1.0, formerly SMART KB Helper.
Version-specific retention and handoff behavior below applies to 1.1.0; older
releases may use different local handoff storage and cleanup behavior.

## Purpose and information accessed

DW Knowledge Helper helps you import a webpage into Digital Worker, Smart or
EE Smart. When you click **Capture page**, it reads the active tab's URL and
your choice of destination and login requirement. It does not continuously
record browsing history or read the page's visible content itself. The selected
platform fetches the webpage when you proceed with its import flow.

For a page marked **requires login**, the extension requests site access and
reads cookies applicable to the captured hostname, including HTTP-only and
path-specific cookies. These cookies may contain sign-in tokens or other
authentication information. Collection uses the active tab's cookie store and,
where supported, its partition key. Cookie permission requests include HTTP
and HTTPS for the hostname and its parent hosts up to the registrable domain;
cookie collection filters out unrelated sibling hosts.

For a page marked **doesn't require login**, the extension does not read or
include cookies. Google Workspace and Confluence links open the selected
platform's knowledge page without capturing cookies through this extension.

## Use and destination

Captures contain the webpage URL, cookie names and values when applicable,
capture time, page type, destination origin and a random capture identifier.
The extension hands the capture only to your selected production destination:

- Digital Worker: `https://de.shopee.io`
- Smart: `https://smart.shopee.io`
- EE Smart: `https://smart-ee.shopee.io`

Authentication cookies enable the selected platform to retrieve the page you
asked to import. Only capture pages whose contents and sign-in information you
are authorized to share with that platform. The extension contains no
advertising, analytics or sale-of-data functionality. It does not request your
password or record form input. Imported content and authentication information
received by a platform are subject to that platform's policies and access controls.

## Local storage and retention

Pending captures are stored in `chrome.storage.local`, outside Chrome sync,
under separate capture identifiers. Their validity is limited to 30 minutes.
A background service worker schedules expiration and restores expiry alarms
when Chrome starts or the extension is installed or updated. Expiration cleanup
may wait until Chrome and the service worker can run.

Smart and EE Smart receive captures through the callback tab's `sessionStorage`.
The extension copy is removed after that handoff. The tab copy is cleared on
expiry; an expired public capture can retain its URL with an empty cookie list.
Closing the tab discards its session storage. The compatible SMART receiver
also clears capture credentials after successful upload or leaving the flow.

Digital Worker receives a temporary `localStorage` inbox record and a readiness
event. Its receiver must consume and remove the record. The extension retains
its pending copy until consumption is acknowledged or the capture expires;
closing the callback clears its inbox record and retains the pending copy for
retry within its original lifetime. Local storage is not a password vault.

The extension does not control server-side retention after a platform receives
the capture. Ask the selected platform's support team about server retention
and deletion of imported content.

## Your controls and contact

You choose when to capture, which destination receives it, and whether cookies
are required. You can cancel an import, revoke site access in Chrome's extension
settings, disable the extension or uninstall it. Revoking access does not
retroactively delete information already received by a platform. Contact the
Smart Platform Assistant SeaTalk bot for questions about the extension and
this policy. Policy changes should update the date above and the public copy.
