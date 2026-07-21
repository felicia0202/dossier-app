# Subject Property Dossier

A single-page tool that pulls a "Subject Property Dossier" (structural
characteristics, legal/parcel record, tax assessment history, sale/deed
history, owner of record, and nearby comparables) for any US address, using
the RentCast Property Data API. This is the first build-out of the **Desk
Package** described in the business plan: administrative, public-record data
intake — no opinions of value, no comparable selection, no appraisal
conclusions.

## 1. One-time setup

1. Open `config.js` in any text editor.
2. Replace `PASTE_YOUR_RENTCAST_API_KEY_HERE` with your real RentCast API key
   (no quotes added/removed — keep the existing quote marks).
3. Save the file.

`config.js` is listed in `.gitignore`, so if you push this folder to GitHub,
your key will **not** be uploaded. Never remove `config.js` from
`.gitignore`, and never paste your key directly into `index.html`.

## 2. Running it

This is a static HTML file — no server or build step required.

- **Easiest:** double-click `index.html` to open it in your browser.
- **If your browser blocks `fetch()` on a `file://` page** (some do, as a
  security measure), run a tiny local server instead, from this folder:

  ```bash
  python3 -m http.server 8000
  ```

  Then visit `http://localhost:8000` in your browser.

## 3. Using it

1. Type a full address (street, city, state, ZIP) into the search bar.
2. Click **Pull Record**.
3. The dossier renders below: structural data, parcel/legal info, tax
   history, sale history, owner of record, and (if the toggle is on)
   RentCast's automated value estimate and comparable properties.
4. Use **Print / Save PDF** to generate a clean printable/PDF version, or
   **Copy Summary** to copy a plain-text summary to your clipboard.

## 4. If you see a CORS / network error

RentCast's API is designed to be called from a browser or no-code tool, so
this should work out of the box. If your browser console shows a CORS error
when pulling a record, it means RentCast (or your network) is blocking
direct browser-to-API calls. If that happens, let your developer (or future
Gemini-led build) know — the fix is to route the request through a tiny
local backend (a few lines of Python/Flask or Node) that holds the API key
server-side and forwards the request. This is a quick follow-up, not a
rebuild.

## 5. What this app intentionally does NOT do

In line with the business plan's legal boundary: this tool presents public
record and listing data only. It does not generate, suggest, or imply any
opinion of value, condition rating, or comparable selection on the
appraiser's behalf. The "comparables" shown are RentCast's automated
valuation model output, clearly labeled as such — not appraiser-selected
comps.

## 6. Next steps (when you're ready)

- Swap the manual address box for a small intake form matching an AMC order
  (order #, due date, client name) so the dossier can be saved per-job.
- Add CubiCasa/field-package fields once fieldwork tooling starts.
- Move from a single HTML file to the Airtable/Make.com pipeline described
  in the project notebook, once volume justifies it.
