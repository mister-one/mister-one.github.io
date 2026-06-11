# Design System

## Direction

A restrained personal publishing surface. The timeline borrows the structural
clarity of an exhibition chronology: a strong vertical axis, explicit direction
labels, and content grouped by time period. Decoration remains secondary to
article titles and dates.

## Color

- **Warm Ivory**: `rgb(250, 249, 241)`. Use as the global background on
  every page.
- **Soft Black**: `rgb(22, 22, 22)`. Use for navigation, dates, metadata,
  labels, headings, links, body copy, and other interface elements.
- **Main Blue**: `rgb(0, 55, 162)`. Reserve for the timeline rail,
  endpoint markers, directional arrow, and keyboard focus outlines. Do not use
  it for text or broad highlights because its contrast on Warm Ivory is low.

The active palette is Warm Ivory, Soft Black, and Main Blue. All text and interactive states must meet WCAG AA contrast
requirements.

## Typography

Use the native system sans-serif stack for all text, including article titles,
navigation, dates, and body copy. Do not load an external web font. Create
hierarchy through size, weight, spacing, and alignment.

## Layout

- Keep the existing readable page width.
- Use a two-column timeline on larger screens.
- The left rail explains direction from Present to Past.
- The right column groups articles by month and year.
- Collapse to a compact single-column chronology on narrow screens.

## Components

### Timeline rail

A vertical line with endpoint markers and persistent Present and Past labels.
The line, markers, and directional arrow use Pale Lavender. The labels use Soft
Black and communicate reading direction without relying on color.

### Time group

A month-and-year heading followed by article rows. Each row contains a precise
publication date and an article link.

### Links

All links use Soft Black with conventional underlines. Pale Lavender is limited
to focus outlines. Hover and focus states should be visible without moving
surrounding content.

## Motion

No motion is required. The chronology should be understandable in a static view.
