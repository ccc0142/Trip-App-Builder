# Trip App Builder

Turn an Excel itinerary into a clean, phone-friendly offline trip app.

The Builder is intentionally lightweight: `index.html` contains the interface, Excel reader, preview, and export logic. It runs entirely in the browser. Your itinerary workbook is not uploaded to a server.

## Quick start

1. Open `index.html` in Chrome or Edge, or host this repository with GitHub Pages.
2. For a new trip, click **Download template** and fill in the workbook.
3. Or drop in an existing `.xlsx` itinerary. The Builder auto-maps common column names and shows a mapping screen so you can correct anything it does not recognize.
4. Customize the cover, theme, map provider, completed-item behavior, day titles, and Quick Info.
5. Export either:
   - **Standalone HTML** — one file, easiest to keep or share.
   - **PWA ZIP** — installable offline app package for an HTTPS static host.

## Recommended Excel fields

The template uses:

`Date | City | Start Time | End Time | Type | Location | Activity | Notes | Address | Fees | Option | Link`

Minimum required mappings are:

- Date
- Start Time
- Type
- Location

See [`docs/excel-format.md`](docs/excel-format.md) for details and recognized aliases.

## Alternative plans

The preferred approach is the **Option** column:

- `A` → Plan A
- `B` → Plan B
- `C` → Plan C

Alternative rows are kept in the Excel row order and shown with section dividers. Overlap checks are isolated by option so Plan A and Plan B do not create false timing warnings.

For backward compatibility, older workbooks that use a row containing only `Plan A: ...` or `Plan B: ...` in the Date column are still supported.

## GitHub Pages deployment

1. Create a GitHub repository, for example `trip-app-builder`.
2. Upload the contents of this package so `index.html` is at the repository root.
3. In GitHub, open **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**.
5. Select `main` and `/ (root)`, then save.
6. GitHub will provide a URL such as `https://YOURNAME.github.io/trip-app-builder/`.

The generic Builder can be public without exposing any itinerary: spreadsheet parsing happens locally in the browser. Do not commit personal trip workbooks to a public repository unless you intend to publish them.

## Default design

The default theme preserves the original Field Notes design:

- Alpine green `#18302e`
- Warm amber `#d99a52`
- Warm paper `#f5f2eb`
- Alpine illustration cover

A photo cover can be uploaded in the Builder and is embedded into the exported app.

## Maps and offline use

**Navigate** opens Google Maps or Apple Maps using `Address` first; if Address is blank, it uses `Location + City`.

The generated itinerary can work offline, but map routing is handled by the selected map app. Download the relevant offline map area before travel if reception may be poor.

## Privacy

The Builder does not send the Excel workbook anywhere. Parsing, column mapping, preview, and generation happen in the browser.
