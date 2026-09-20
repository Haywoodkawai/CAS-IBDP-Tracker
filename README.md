# CAS Tracker

An offline-first tracker for IB Diploma CAS: activities, dated entries, a calendar,
and a two-year timeline that flags any stretch with nothing going on.

No account, no server, no build step. Everything is saved in the browser on the device.

## Put it online with GitHub Pages

1. Create a new **public** repository on GitHub (for example `cas-tracker`).
2. Upload every file in this folder to the repository root:
   `index.html`, `sw.js`, `manifest.webmanifest`, the three `icon-*.png` files and `.nojekyll`.
3. In the repository go to **Settings > Pages**. Under *Build and deployment* choose
   **Deploy from a branch**, branch `main`, folder `/ (root)`, then **Save**.
4. After a minute the site is live at `https://<your-username>.github.io/cas-tracker/`.

The same folder works unchanged on Netlify, Cloudflare Pages, Vercel or any static web host.

## Use it offline

- Open the site once while online. From then on it opens without a connection.
- Install it like an app: in Chrome or Edge use the install icon in the address bar;
  on iPhone or iPad use **Share > Add to Home Screen**.
- With no hosting at all, double-click `index.html`. It runs straight from the file.
  (Installing as an app needs the hosted version.)

## Where the data lives

Data stays in the browser's storage for that site on that device. It does not sync by itself.

- **Settings > Download backup** saves one `.json` file. Do this regularly.
- **Settings > Restore from backup** loads that file on another device or browser.
- Clearing site data in the browser removes the record, which is why the backup matters.
- The hosted site and a double-clicked `index.html` keep separate data.

## Updating the app later

If you change `index.html`, also change `VERSION` in `sw.js` (for example from `cas-tracker-v7` to `cas-tracker-v8`)
so devices that already cached the old copy fetch the new one. Saved data is not affected.

## How gaps are worked out

- **Activity dates**: a day is covered if any activity's start-to-end range includes it.
  An activity with no end date that is not marked Completed is assumed to continue.
- **Logged entries**: stricter. A week counts only if at least one entry was logged in it.
- A run of uncovered days becomes a gap once it reaches the threshold in
  **Settings** (14 days by default).

## Entries, supervisor feedback and photos

- An activity holds two kinds of dated record. **Add entry** logs a session, milestone, reflection or
  planning step. **Add supervisor feedback** records what the supervisor said, what the student thinks
  about it, and what they will do next. Both appear on the activity's timeline and on the calendar.
- Either kind can carry up to 6 photos. Photos are resized in the browser (longest side 1600 px) and
  stored in the browser's IndexedDB on that device. They are never uploaded anywhere.
- **Download backup** puts the photos inside the backup file, so restoring it on another device brings
  them along. A record with many photos makes a larger backup file; that is expected.
- iPhone HEIC photos may not open in every browser. If one is refused, share it as JPG first.

## Strand balance and the IBDP countdown

- The ring chart on the overview shows each strand's share, measured by **hours logged** on entries
  or by **days active** (days, up to today, on which an activity of that strand was running).
  Hours of an activity with two strands are split evenly between them.
- The IB asks for a reasonable balance across Creativity, Activity and Service rather than identical
  hours, so the one-third marks are a guide. Check what your own CAS coordinator expects.
- The countdown shows one square per week from the CAS start date to the **IBDP ends** date, which you
  set with "Edit name and dates" or under Settings.

## Fonts

Source Sans 3 and Source Serif 4 (Adobe, SIL Open Font License 1.1) are embedded in
`index.html`, so the typography is identical online and offline.
