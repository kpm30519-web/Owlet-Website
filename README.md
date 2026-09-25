# Owlet Recipe Saver v0.7.0 — early local build

Owlet is a no-build Chrome/Edge extension that captures structured recipes from a webpage the user selects and lets the user review, edit, print, and export them. Server storage is optional; this build supports KitchenOwl as its first server destination. Owlet is independent and is not affiliated with, endorsed by, or sponsored by KitchenOwl.

## What this build does

- Captures, reviews, prints, and exports recipes without requiring a server connection.
- Organizes the hamburger menu into Import / Export, Connections, Print Options, View Options, and Help.
- Opens Connections when **Connect to save** is clicked without an active server connection.
- Provides persistent print toggles for Description / Notes, Nutrition, and Source URL; all are enabled by default and affect printing only.
- Provides independent View Options for hiding Description / Notes, Nutrition, and Source URL without removing their data or preventing enabled items from printing.
- Provides persistent Small, Medium, and Large interface text sizes, with two-pixel increases between sizes, plus Light, Dark, and System themes.
- Includes an in-extension user guide, About information, privacy link, and diagnostic download under Help.
- Optionally connects to `https://app.kitchenowl.org` using the same request flow as the supplied bulk importer.
- Connects to a user-provided hosted or self-hosted KitchenOwl URL.
- Persists only the server and username. KitchenOwl access and refresh tokens are held in `chrome.storage.session`; passwords are never stored.
- Lets you choose a KitchenOwl household.
- Reads Schema.org `Recipe` metadata from the currently active page when you click **Read/Refresh Recipe**.
- Standardizes metric weights and volumes to practical US customary units, and Celsius oven temperatures to Fahrenheit, before review.
- Formats decimal ingredient quantities as familiar US kitchen fractions, such as `0.5` to `1/2` and `0.333333` to `1/3`.
- Gives you an editable recipe review before printing, exporting, or saving to server storage.
- Captures the Schema.org recipe description into the editable Description / Notes field and falls back to visible nutrition tables when structured nutrition is absent.
- Provides an editable comma-separated tag field and sends only the tags the user explicitly enters.
- Saves recipe ingredients, instructions, timings, yields, and source URL to KitchenOwl.
- Combines repeated ingredient names into one KitchenOwl item while retaining later quantities as additional amounts.
- Normalizes duplicated recipe yields such as `6, 6 servings` to a single serving count.
- Opens a clean recipe-only print page in Full Recipe or landscape 7×5 Recipe Card format, including a safely validated recipe image when available.
- Builds explicit, measured Letter pages and 7×5 landscape card pages before opening Chrome print preview, so the on-screen document and PDF pagination agree. Ingredients use balanced two-column layouts to use the available width while instructions stay full-width; every overflow page puts its Ingredients (continued) or Instructions (continued) heading before the continued entry. Full Recipe repeats its title and page number; recipe cards repeat their title and Card N of M.
- Warns instead of printing the whole webpage when Owlet does not have a complete recipe.
- Exports a `ko-pellet-recipe-bundle` JSON file compatible with the existing Python importer bundle.

## Deliberate first-build limits

- No OCR, AI service, server, database, or subscription is used.
- A page needs complete recipe data before it can be saved or printed. Owlet warns when extraction is incomplete rather than printing the entire webpage.
- On the first **Read/Refresh Recipe**, Owlet asks once for optional access to HTTP and HTTPS sites. This broad optional grant lets recipe reading work after navigation and lets found recipe images load in review and printouts. Connecting KitchenOwl requests access only to the selected server if broad access has not already been granted. Disconnect does not revoke permissions.
- A finished-dish image may be shown in review and printed. It is downloaded and sent to the selected KitchenOwl server only when you choose Save; Owlet does not persist image bytes.
- Opens as a persistent Chrome side panel instead of a temporary toolbar popup.
- The toolbar icon only opens or focuses the side panel. **Read/Refresh Recipe** explicitly reads the currently active tab, including after navigation while the side panel remains open. Owlet does not monitor navigation or inspect pages automatically. The current review remains visible until another read, a successful server save, or another explicit clearing action replaces it.
- Provides JSON export and multi-file Owlet/ko-pellet JSON bulk import from the header menu.
- Imports both Owlet bundles and native KitchenOwl recipe-export JSON.
- Keeps a privacy-conscious diagnostic log that can be downloaded from the header menu.
- Diagnostic entries deliberately omit source URLs, recipe titles/content, authentication data, request headers, and image URLs.

## Install privately (free)

1. In Chrome, open `chrome://extensions`; in Microsoft Edge, open `edge://extensions`.
2. Turn on **Developer mode**.
3. Choose **Load unpacked**.
4. Select the unzipped `owlet-recipe-saver` folder.
5. Pin **Owlet Recipe Saver** to the toolbar.
6. Open a normal recipe webpage, click the extension, then choose **Read/Refresh Recipe**. Chrome or Edge asks for optional HTTP/HTTPS site access on the first read. Connect KitchenOwl only if you want server storage.

## Before real-world use

Test with a non-critical recipe first. The KitchenOwl endpoint shapes were copied from the supplied importer, but this extension has not been signed in to or used against an account yet.

## Next build steps

1. Test authentication and saving with the user's KitchenOwl account.
2. Add a direct handoff to the existing batch workflow, if its source/parsing component becomes available.
3. Generate printable recipe-card and Recipe Flow Chart outputs from reviewed recipe data.

## Chrome Web Store Listing

### What Owlet does
Owlet captures structured recipe information from the webpage you choose, lets you review and edit it, and lets you print or export it without a server connection. KitchenOwl is an optional server-storage destination.

### How it works
Select a recipe webpage, open Owlet from the toolbar, then click **Read/Refresh Recipe** and approve optional HTTP/HTTPS site access on the first read. Owlet reads Schema.org Recipe data (and limited visible recipe sections when needed) only on that click and presents an editable review including optional description/notes and nutrition. Printing and JSON export work without server storage. If KitchenOwl is connected, Owlet sends the recipe only after you choose **Save to KitchenOwl**. Description/notes and nutrition remain local to review/export/print.

### Data and privacy
Owlet handles the KitchenOwl username you enter, short-lived authentication tokens, selected recipe data, source URL, optional recipe image, household choices, tags, and minimal diagnostic events. It does not sell data, use advertising or analytics, profile browsing, or automatically monitor pages. Passwords are used only to sign in and are not stored. Tokens are kept in browser session storage rather than persistent extension storage. See the published Privacy Policy URL configured before release for details.

### Permissions
- `activeTab` and `scripting`: support explicit recipe reading from the active page.
- `sidePanel`: display Owlet as a side panel.
- `storage`: retain non-sensitive connection, print-option, and view-preference settings, recipe print handoff data, diagnostics, and session-only credentials.
- Optional host access: HTTP and HTTPS site access is requested from the direct **Read/Refresh Recipe** gesture. It lets Owlet read only when that button is clicked and load recipe images for review or printing. Connecting a server may request access to that server origin.

### Self-hosted servers and independence
Owlet supports the KitchenOwl server you specify, including self-hosted installations. A self-hosted server is operated by its owner, whose privacy and security practices are separate from Owlet. Owlet is an independent extension and is not affiliated with, endorsed by, or sponsored by KitchenOwl.

## Security and data flow

**Data flow:** webpage selected by user → explicit Read/Refresh extraction → user review/edit → print or local export; optionally, KitchenOwl server selected by user on Save. On server Save, an optional recipe image is transferred directly to that selected KitchenOwl server. Owlet has no service that receives recipe or image data.

`activeTab` and `scripting` support the packaged extractor; `sidePanel` supplies the panel UI. `storage` holds optional server/username settings, print preferences, view preferences, and local diagnostic/print data; access and refresh tokens are only in `chrome.storage.session` and are cleared on logout, failed connect, or browser-session end. Optional HTTP/HTTPS host permission is requested on the first Read/Refresh action and remains granted until the user changes it in Chrome or Edge. It does not cause automatic reading. Source and image URLs are accepted only as credential-free HTTP(S) URLs; source query strings and fragments are removed. There are no remote scripts, remote modules, `eval`, `new Function`, analytics, or tracking code.
