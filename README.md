# Singapore Job Search OS · v1

A responsive, buildless job application dashboard. All CSS and JavaScript live in `index.html`; no dependencies, account, backend or API key required.

## Open / publish

Open `index.html` locally, or publish with GitHub Pages:

1. In this repository, open **Settings → Pages**.
2. Under **Build and deployment**, choose **Deploy from a branch**.
3. Select **main**, **/ (root)**, then **Save**.
4. Wait for the Pages deployment to complete. Expected address: https://kennethkiew.github.io/jobsearching/ . This address is only live after Pages is enabled and deployment succeeds.

Source: https://github.com/KennethKiew/jobsearching

## Features

- Mobile responsive dashboard, full-database KPIs, search and status / sponsorship filters.
- Add, edit and delete records; optional JD URL and application / evidence dates.
- Separate application status and employer sponsorship evidence.
- Browser localStorage persistence with visible storage failure messages.
- JSON and CSV backup export/import. Import validates the entire file before replacing records and asks for confirmation. Export includes all records, regardless of filters. Empty backups are supported.
- CSV uses quoted fields and spreadsheet formula protection. JSON is the preferred lossless backup.

## Audit baseline · 7 November 2026

Nine identifiable records, **six confirmed recruiting processes**, three uncertain submissions. This supersedes the prior prototype's unsupported claim of nine confirmed processes / thirteen total records. It is not a complete job history.

| Company / process | Baseline status |
| --- | --- |
| UOB BDE | Rejected |
| UOB wealth | Conditional offer declined |
| SPH Media | Assessment unsuccessful |
| Great Eastern | Interviewed — outcome unknown |
| Neuberger Berman | Applied |
| Tech in Asia | Applied |
| Rogo | Needs confirmation |
| ShopBack | Needs confirmation |
| AlphaSense | Needs confirmation |

Based on the user's audit instruction and referenced conversation. Earlier assistant claims are not submission receipts. Role wording remains editable, and GE's exact title needs verification. Application dates are deliberately blank when exact dates are not established. JD URLs are historical references, not claims that vacancies remain open. No new applications were submitted by this dashboard.

“Confirmed processes” counts every record except `Needs confirmation` and `Shortlisted — not applied`. “Waiting / outcome unknown” counts Applied, Interview scheduled and Interviewed — outcome unknown; it does not establish active employer interest. KPI totals ignore table filters.

All initial sponsorship values are Unknown. Relocation assistance is not equivalent to employer sponsorship or EP / S Pass eligibility. The dashboard does not calculate pass eligibility, salary thresholds or approval probability. Record dated role-specific evidence and consult current MOM guidance at https://www.mom.gov.sg/passes-and-permits .

## Data and privacy

The baseline in this public repository and on Pages is public. Personal edits are stored only in the current browser/origin under `sg-job-search-os-v1`; they are not sent to GitHub or synced across devices. Local-file storage behavior varies by browser. Clearing browser storage can delete edits. Export regular JSON backups and keep them private. Moving from local preview to Pages creates a separate store: export and import to transfer data. Source updates preserve existing stored data rather than overwriting it with the baseline.

Import expects a v1 JSON object (`schemaVersion: 1`, `records: [...]`), a raw records array, or CSV with `company,role,status,visa` headers. The dashboard's own exports include all supported fields. Import replaces the complete database, not a merge. Each import is limited to 5 MB and 5,000 records. No external scripts, fonts or analytics are loaded.


## Public opportunity feed

`jobs.json` is the GitHub-maintained feed. The site fetches it when opened or refreshed. For each new opportunity, add a complete record with a unique, permanent `feed-` ID, company, role, status `Shortlisted — not applied`, visa `Unknown`, and any evidenced notes and source URL. Use only the status and visa options defined in the HTML. Never reuse or change an ID; duplicate IDs reject the feed. Do not mark a job applied without evidence. Validate links and distinguish employer statements from work-pass eligibility. Commit the feed to the Pages branch; deployment can take a few minutes.

The browser keeps a copy of the last feed and performs a field-by-field merge: a field untouched locally can receive a feed update; a locally changed field wins. Locally deleted feed entries stay deleted, even if the feed still lists them. Records removed from the feed stay in the browser, preserving personal history. Manual records and prior v1 data remain intact. JSON/CSV exports contain the complete visible database; the feed sync history is local to each browser and is not included in backups. After importing on a new browser, matching IDs preserve imported values during the first sync. New feed entries can be added on refresh; a previously deleted feed record may reappear on a different browser after importing a backup because deletion history is not exported.

The feed and all its contents are public. Application edits and notes remain in local browser storage and do not sync to GitHub or other devices. If the feed cannot be loaded, saved records remain usable and a notice appears. `file://` cannot fetch the feed: use GitHub Pages or a local HTTP server.
