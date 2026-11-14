# Supporters page: host on GitHub Pages

`index.html` is the full page: OpenStreetMap (Leaflet) map, embedded GPX course, estimated passing and finish times, logged passing times, and live location. One file, no build step.

## Host it (web UI, about 3 minutes)
1. github.com, New repository. Name it e.g. `marathon-supporters`. Make it **Public** (Pages on private repos needs a paid plan). Create.
2. Add file, Upload files, drop `index.html`, Commit changes.
3. Settings, Pages, Build and deployment. Source: **Deploy from a branch**. Branch: `main`, folder `/ (root)`. Save.
4. After about a minute the URL shows at the top of that page: `https://<username>.github.io/marathon-supporters/`. Open it on your phone and share the link.

## Host it (command line)
```
git init
git add index.html
git commit -m "supporters page"
git branch -M main
git remote add origin https://github.com/<username>/marathon-supporters.git
git push -u origin main
```
Then do step 3 above.

## Change things
Edit `index.html` on GitHub (pencil icon) and commit. The site updates in about a minute.
- Default start and estimated paces: `DEFAULTS={start:36000,pf:280,ps:310}` in seconds (36000 = 10:00, 280 = 4:40/km, 310 = 5:10/km). Paces are used for estimates but are not shown as controls.
- Entering a passing time collapses earlier points; tap a point heading to reopen it and correct its time. **Alles resetten** clears passing times and restores the default start and paces.
- Plek texts and links: the `SP` array.
- Course: `POLY` (encoded polyline) and `TOT` (km).

## Notes
- Open it through the https URL. On GitHub Pages the default map is OpenStreetMap. In a preview or from disk (`file://`) there is no referrer and OSM blocks its tiles, so the page then offers only the PDOK layers and defaults to those. Location also needs https.
- Location needs the browser's permission. It only works on https.
- Logged times are stored per device (localStorage). They are not shared between supporters.
- Map layers (button top left): PDOK Kaart, Grijs, Pastel and Luchtfoto (Netherlands, no key), plus OpenStreetMap, OpenTopoMap and CyclOSM when hosted on https. None needs an API key. Keep the attribution on the map; OSM, OpenTopoMap and CyclOSM have fair-use policies, fine for a small group.
- CARTO (Positron, Voyager, Dark Matter) now needs a free API key, so it is not used. To add a keyed provider, add one more entry to the `base` object in `index.html`.
- Needs internet for tiles and for Leaflet (loaded from cdnjs).
