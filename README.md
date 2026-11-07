# Bite Club

Luke & Gill's food diaries. A Manchester restaurant hit list, plus sandwich and pizza ratings.

It's a single-page web app with no server and no login. Everything you add, including photos, is saved on the phone you add it on.

## Put it live on GitHub Pages

1. Copy these files into the repo, keeping the `icons` folder:
   - `index.html`
   - `manifest.webmanifest`
   - `sw.js`
   - `icons/`
2. On GitHub, go to **Settings → Pages**, set the source to **Deploy from a branch**, and pick your main branch and the root folder.
3. After a minute, it's live at `https://<your-username>.github.io/<repo-name>/`.

## Turn on Google Maps (optional)

Without a key, the Hit List uses the built-in drawn map. Adding a key gets you three things:

- a real Google map with your pins
- a **Near me** button
- **Find it on Google** in the Add place form, which fills in the name, exact pin, Google link, area and price

1. Go to [console.cloud.google.com](https://console.cloud.google.com) and create a project (e.g. "Bite Club").
2. Link a billing account. Google asks for a card even for free use. Two people logging their meals will stay well inside the free monthly allowance.
3. Go to **APIs & Services → Library** and enable **Maps JavaScript API** and **Places API (New)**.
4. Go to **APIs & Services → Credentials → Create credentials → API key**, then edit the key:
   - **Application restrictions:** choose *Websites* and add `https://<your-username>.github.io/*`
   - **API restrictions:** choose *Restrict key* and tick Maps JavaScript API and Places API (New)
5. Optional: go to **Google Maps Platform → Map management**, create a Map ID (JavaScript, Vector) and copy it.
6. Open `index.html`, find `GOOGLE_MAPS_API_KEY = ""` near the top of the script, and paste the key between the quotes. Paste the Map ID into `GOOGLE_MAPS_MAP_ID` if you made one. Commit and push.
7. Recommended: go to **Billing → Budgets & alerts** and set a small budget (e.g. £5), so you get an email if usage ever climbs.

The key is visible in the page source. That's normal for Google Maps keys: the website restriction in step 4 stops anyone using it on another site.

## Add it to your phone

- **iPhone:** open the link in Safari, tap **Share**, then **Add to Home Screen**.
- **Android:** open the link in Chrome, tap the **⋮** menu, then **Add to Home screen** (or **Install app**).

It opens full screen like an app and works offline once it has loaded.

## Backups and moving lists between phones

Each phone keeps its own lists. To back up, or to copy your lists to another phone:

1. Tap **Export** on any tab, then **Back up everything**. Save the file or send it to yourself.
2. On the other phone, tap **Export → Restore a backup** and pick the file.

Restoring adds the entries from the backup and updates any that are already there. It never deletes anything.

It's worth backing up now and then. If the browser's data is cleared, the lists go with it.

## Updating the app

After you change `index.html`, bump `VERSION` at the top of `sw.js` (e.g. `bite-club-v2`). That way phones pick up the new copy instead of the saved one. Your saved entries aren't affected.
