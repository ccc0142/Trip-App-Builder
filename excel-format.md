# Excel format

The downloadable template is the recommended input, but it is not mandatory.

## Canonical fields

| App field | Required | Purpose | Common aliases recognized |
|---|---:|---|---|
| Date | Yes | Groups itinerary items by trip day | Date, Day, Trip Date, Itinerary Date, Travel Date |
| City | No | Context label and map fallback | City, Town, Area, Region |
| Start Time | Yes | Timeline ordering | Start Time, Start, From, Begin, Beginning, Time |
| End Time | No | Duration and overlap checks | End Time, End, Finish, To |
| Type | Yes | Card category/color | Type, Category, Kind |
| Location | Yes | Main card title | Location, Place, Destination, Venue, Stop |
| Activity | No | Primary instruction | Activity, Details, Description, Plan, What to Do, Itinerary |
| Notes | No | Smaller secondary text | Notes, Note, Comments, Comment, Remarks |
| Address | No | Preferred map destination | Address, Map Address, Location Address |
| Fees | No | Cost/pass/parking note | Fees, Fee, Cost, Costs, Price, Pass |
| Option | No | Alternative-plan grouping | Option, Plan Option, Alternative, Alt, Choice, Scenario |
| Link | No | Reservation/ticket/booking URL | Link, URL, Website, Reservation Link, Booking Link, Ticket Link |
| Display Time | No | Optional preformatted time range | Display Time, Time Range |

## Column mapping

When a workbook is imported, the Builder:

1. looks for an exact canonical header;
2. checks the common aliases above;
3. displays the mapping screen for review;
4. blocks export only when a required field is still unmapped.

This means an existing workbook such as:

`Trip Date | Start | Finish | Category | Place | Details`

can import without being rewritten to the template.

If your headers are completely different, select the corresponding source column from the mapping dropdowns.

## Dates and times

Real Excel dates and times are preferred. Text dates/times can also work when the browser can interpret them consistently.

## Alternative plans

Use the `Option` column for future workbooks. Example:

| Date | Start Time | Type | Location | Option |
|---|---|---|---|---|
| 2026-09-17 | 08:30 | Activity | Grassi Lakes | A |
| 2026-09-17 | 08:45 | Tour | Vermilion Lakes | B |

The generated app shows `PLAN A` and `PLAN B` dividers.

Older spreadsheets can still use divider rows where the Date cell contains text such as `Plan A: Dinner in Banff` and the rest of the row is blank.

## Links

Use a full `https://...` URL when possible. The generated app shows a context-aware button such as **Reservation**, **Booking**, **Ticket**, or **Open link**.

## Type values

The template includes a dropdown with:

- Travel
- Tour
- Meal
- Hotel
- Shopping
- Fuel
- Flight
- Activity
- Rest
- Other

Other text values are still accepted; they simply use the fallback card color.
