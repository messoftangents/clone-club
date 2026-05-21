# Shared Availability Calendar

A visual, interactive calendar showing shared availability across multiple people for May–August 2026.

## Features

- **Color-coded days** — Each person has a unique color gradient
- **Interactive filtering** — Check/uncheck names in the legend to show/hide their availability
- **Overlap highlighting** — Days when all selected people are available show a glittery gold background with a sparkle ✨
- **Multi-person dates** — Days with 2+ people show a count in magenta-purple
- **Click for tooltips** — Click any colored day to see who is available

## How It Works

The calendar reads availability data from a JavaScript object in `index.html` and automatically generates color-coded calendar views. Each person has a distinct color, and overlapping availability is highlighted.

## Current People

- **ANNA** — Magenta-Purple
- **Emily** — Pink
- **jenn** — Cyan
- **Jenna** — Teal
- **AK** — Red
- **Melissa** — Green
- **Amy** — Orange

## Adding a New Person's Availability

1. Open `index.html` in a text editor
2. Find the `availability` object in the `<script>` section:
   ```javascript
   const availability = {
       ANNA: { ... },
       Emily: { ... },
       // ... other people
   };
   ```

3. Add a new person's availability data:
   ```javascript
   YourName: {
       5: [23, 24, 25],  // May dates
       6: [14, 27],      // June dates
       7: [11, 12],      // July dates
       8: [1, 2, 8]      // August dates
   }
   ```

4. Add a color style for the day in the CSS section:
   ```css
   .day.available.yourname {
       background: linear-gradient(135deg, #startColor 0%, #endColor 100%);
       border: 1px solid #darkColor;
   }
   ```

5. Add a matching legend color style:
   ```css
   .yourname-color {
       background: linear-gradient(135deg, #startColor 0%, #endColor 100%);
   }
   ```

6. Add the person to the legend in the HTML:
   ```html
   <div class="legend-item" data-person="YourName">
       <input type="checkbox" class="person-checkbox" checked>
       <div class="legend-color yourname-color">Y</div>
       <span>Your Name</span>
   </div>
   ```

7. Update the `getClassNameFromPerson()` function:
   ```javascript
   const classMap = {
       'ANNA': 'anna',
       'Emily': 'emily',
       // ... add:
       'YourName': 'yourname'
   };
   ```

8. Update the `getAbbrFromPerson()` function:
   ```javascript
   const abbrMap = {
       'ANNA': 'A',
       'Emily': 'E',
       // ... add:
       'YourName': 'Y'
   };
   ```

9. Save and refresh the browser to see the changes.

## Editing Someone's Availability

1. Open `index.html` in a text editor
2. Find the `availability` object and locate the person you want to edit
3. Update the date arrays for any month:
   - **Add dates**: Insert the day number into the array (e.g., `5: [23, 24, 25, 30]`)
   - **Remove dates**: Delete the day number from the array
   - **Clear a month**: Replace the array with `[]` (e.g., `6: []`)

4. Save and refresh the browser to see the updated calendar

## Special Display States

- **Single person**: Shows person's color with their initial/abbreviation
- **Multiple people (2+)**: Shows count in magenta-purple
- **All selected people available**: Shows sparkle ✨ with glittery gold background and count

## Notes

- The calendar automatically handles overlapping availability
- Filter using the interactive legend to show specific people
- All HTML/CSS/JS is in one file (`index.html`) for easy sharing
- Month data is based on 2026 calendar dates
- Dates are specified as day numbers (1–31)
