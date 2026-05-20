# Shared Availability Calendar

A visual calendar showing shared availability across multiple people for May–August 2026.

## How It Works

The calendar reads availability data from a JavaScript object and automatically generates color-coded calendar views. Days are color-coded by person, and days when multiple people are available show combined initials in purple.

## Adding a New Person's Availability

1. Open `availability-calendar.html` in a text editor
2. Find the `availability` object:
   ```javascript
   const availability = {
       ANNA: { ... },
       Emily: { ... },
       jenn: { ... }
   };
   ```

3. Add a new person by inserting a new entry. Follow this format:
   ```javascript
   YourName: {
       5: [23, 24, 25],  // May dates
       6: [14, 27],      // June dates
       7: [11, 12],      // July dates
       8: [1, 2, 8]      // August dates
   }
   ```

4. Add a color style in the CSS section. Pick a gradient pair:
   ```css
   .yourname-color {
       background: linear-gradient(135deg, #color1 0%, #color2 100%);
   }
   ```
   Example color gradients: `#e8b4d1` to `#d492b8`, `#a8d8ea` to `#7fc8d9`, `#f4d89f` to `#ecc881`

5. Add a day style:
   ```css
   .day.yourname {
       background: linear-gradient(135deg, #color1 0%, #color2 100%);
   }
   ```

6. Add the person to the legend:
   ```html
   <div class="legend-item">
       <div class="legend-color yourname-color">Y</div>
       <span>Your Name</span>
   </div>
   ```

7. Save and refresh the browser to see the changes.

## Editing Someone's Availability

1. Open `availability-calendar.html` in a text editor
2. Find the `availability` object and locate the person you want to edit
3. Update the date arrays for any month:
   - **Add dates**: Insert the day number into the array (e.g., `5: [23, 24, 25, 30]`)
   - **Remove dates**: Delete the day number from the array
   - **Clear a month**: Replace the array with `[]` (e.g., `6: []`)

4. Save and refresh the browser to see the updated calendar

## Example: Adding "Charlie"

```javascript
const availability = {
    ANNA: { ... },
    Emily: { ... },
    jenn: { ... },
    Charlie: {
        5: [1, 2, 8, 9],
        6: [15, 16, 22, 23],
        7: [6, 7, 13, 14, 20, 21, 27, 28],
        8: [3, 4, 10, 11]
    }
};
```

Then add CSS and legend entries as shown above.

## Notes

- The calendar automatically handles overlapping availability (2+ people on same day)
- Days with multiple people show combined initials in purple with a star
- The HTML/CSS/JS is all in one file for easy sharing and editing
- Month data is based on 2026 calendar dates
