# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a single-file web application called "Full-Date Challenge – DoW Trainer" (Day of Week Trainer). The entire application is self-contained in `whatday.html` - an educational game that teaches mental calculation techniques for determining the day of the week for any historical date.

## Architecture

The application consists of:
- **Single HTML file** (`whatday.html`) containing all code
- **Inline JavaScript** (lines 37-186) implementing game logic
- **Tailwind CSS** loaded from CDN for styling
- **No build process, dependencies, or server requirements**

### Core Game Logic

The game uses the Doomsday algorithm variant with three key components:
1. **Date Value (DV)**: Calculated from month and day using a lookup table
2. **Year Code (YC)**: Calculated as `(year + floor(year/4)) % 7`, then converted to signed format
3. **Century Code (CC)**: Fixed values for each century (1700s: +2, 1800s: 0, 1900s: -2, 2000s: +3)

The weekday is determined by: `(DV + CC + YC) mod 7`

### Key Functions and Data Structures

- `toSigned()`: Converts values > 3 to negative (4→-3, 5→-2, 6→-1) for easier mental math
- `yearCode()`: Calculates the year code for any two-digit year
- `DATE_TABLE`: Pre-computed date values for all month/day combinations
- `CENTURY_CODES`: Array of century adjustments
- `SIGNED_DAY`: Maps signed values to weekday names

## Development Commands

Since this is a standalone HTML file with no build process:

- **Run locally**: Open `whatday.html` directly in a web browser
- **Test changes**: Refresh the browser after editing
- **Deploy**: Upload the single HTML file to any web server

## Code Conventions

When modifying this application:
- Keep all code in the single HTML file to maintain portability
- Use Tailwind utility classes for styling (loaded from CDN)
- Follow the existing inline JavaScript structure
- Maintain the self-contained nature - avoid adding external dependencies