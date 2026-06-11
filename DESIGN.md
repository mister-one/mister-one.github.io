# Design System

## Direction

A restrained personal publishing surface. The timeline borrows the structural
clarity of an exhibition chronology: a strong vertical axis, explicit direction
labels, and content grouped by time period. Decoration remains secondary to
article titles and dates.

## Color

- **Warm Ivory**: `rgb(250, 249, 241)`. Use as the global background on
  every page.
- **True Black**: `rgb(0, 0, 0)`. Use for long-form paragraphs and primary
  reading text.
- **Soft Black**: `rgb(22, 22, 22)`. Use for navigation, dates, metadata,
  labels, and other interface elements.
- **Pale Lavender**: `rgb(228, 230, 252)`. Use as a background highlight for
  page titles, article titles, and selected link treatments. Do not use it as
  text on Warm Ivory because the contrast is insufficient.
- **Soft Chartreuse**: `rgb(234, 234, 173)`. Use for timeline lines, endpoint
  markers, separators, borders, and focus accents.

Use the colors by role rather than decoratively. All text and interactive states
must meet WCAG AA contrast requirements.

## Typography

Use the existing system sans-serif stack for navigation, dates, and body copy.
Article titles use Titan One, a chunky rounded display face that gives the archive
a playful retro character. Create the remaining hierarchy through size, weight,
spacing, and alignment.

## Layout

- Keep the existing readable page width.
- Use a two-column timeline on larger screens.
- The left rail explains direction from Present to Past.
- The right column groups articles by month and year.
- Collapse to a compact single-column chronology on narrow screens.

## Components

### Timeline rail

A vertical line with endpoint markers and persistent Present and Past labels.
The line, markers, and timeline borders use Soft Chartreuse. The labels use Soft
Black and communicate reading direction without relying on color.

### Time group

A month-and-year heading followed by article rows. Each row contains a precise
publication date and an article link.

### Links

Article links use Soft Black text with a Pale Lavender highlight. Navigation uses
Soft Black. Hover and focus states should be visible without moving surrounding
content.

## Motion

No motion is required. The chronology should be understandable in a static view.
