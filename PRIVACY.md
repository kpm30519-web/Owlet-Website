# Owlet Recipe Saver Privacy Policy

**Effective date:** Replace with the publication date before release.

Owlet Recipe Saver (“Owlet”) is an independent browser extension that captures structured recipe information from a webpage the user chooses and allows the user to review, edit, print, and export it without connecting a server. KitchenOwl is an optional server-storage destination selected by the user. Owlet is not affiliated with, endorsed by, or sponsored by KitchenOwl.

## Information Owlet handles

Owlet may handle the KitchenOwl username or email entered by the user; authentication access and refresh tokens returned by the selected KitchenOwl server; recipe title, ingredients, instructions, times, servings, user-entered tags, and source URL; recipe images; the selected KitchenOwl household; import/export files selected by the user; and minimal diagnostic information.

Recipe information is read only when the user clicks **Read/Refresh Recipe** in Owlet's side panel; clicking the toolbar icon only opens or focuses that panel. Owlet does not monitor navigation or inspect pages automatically. The current review remains visible until another read, a successful server save, or another explicit clearing action replaces it. The source URL is retained as recipe metadata only when the user chooses to save or export the recipe. Before use, Owlet removes URL credentials, query strings, and fragments. Recipe images may load in review and be included in printouts. They are downloaded and sent to the selected KitchenOwl server only when the user chooses Save for a recipe containing an image. Optional description/notes and nutrition are local review, print, and export fields and are not sent to KitchenOwl. Owlet does not persist image bytes.

## How information is used and shared

Owlet uses this information solely to provide its recipe capture, review, printing, import/export, and KitchenOwl-saving functions. When the user chooses Save, recipe data and any recipe image are sent directly to the KitchenOwl server the user selected. Authentication credentials are used solely to authenticate to that selected server. Owlet does not operate a service that receives recipe data or images.

Owlet does not sell user data; use it for advertising, marketing, profiling, or personalized recommendations; use browsing history for advertising or profiling; or operate analytics or tracking services. Owlet does not automatically inspect pages as the user browses.

KitchenOwl servers, including self-hosted servers, are controlled by their respective operators. Their privacy and security practices are separate from Owlet's.

## Local storage and security

Owlet persistently stores the selected KitchenOwl server address and username, print-option preferences, interface visibility/font/theme preferences, print handoff data, and a limited diagnostic log in extension-local storage. It does not store the KitchenOwl password. Access and refresh tokens are held in browser session storage, not persistent local storage, and are intended to disappear when the browser/extension session ends. Disconnecting or a failed connection removes those session credentials.

On the first Read/Refresh Recipe action, Owlet requests optional access to HTTP and HTTPS sites from that direct user gesture. This broad permission lets the action access the active page after navigation and lets recipe images load for review and printing. Connecting KitchenOwl may request access to the selected server origin if broad access has not already been granted. Owlet does not revoke permissions on Disconnect; the user can manage them in Chrome or Microsoft Edge.

The diagnostic log is optional to download from Owlet's menu and can be cleared by removing extension data or uninstalling the extension. It is designed to contain only timestamps, operation names, counts, response status, format, and generic error categories. It does not intentionally contain passwords, tokens, Authorization headers, cookies, session identifiers, recipe contents, recipe titles, source URLs, or image URLs.

## Permissions

Owlet uses `activeTab` and `scripting` for explicit recipe reading; `sidePanel` to provide its interface; and `storage` for the limited storage described above. It requests optional HTTP and HTTPS host access from the user's direct Read/Refresh Recipe action and may request access to an optional server destination from the direct Connect action. These permissions do not trigger automatic page access.

## Chrome Web Store Limited Use

Owlet's use of information received from Chrome extension APIs complies with the Chrome Web Store User Data Policy, including the Limited Use requirements. User data is used only to provide or improve Owlet's single purpose and related operational functionality.

## Contact and changes

For privacy questions, contact: **[REPLACE WITH SUPPORT/PRIVACY EMAIL BEFORE PUBLICATION]**.

This policy may be updated when Owlet changes. The current version should be published at the privacy-policy URL linked in the extension before Chrome Web Store submission.