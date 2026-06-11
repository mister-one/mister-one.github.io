# Design System

## Direction

A restrained personal publishing surface. The timeline borrows the structural
clarity of an exhibition chronology: a strong vertical axis, explicit direction
labels, and content grouped by time period. Decoration remains secondary to
article titles and dates.

## Color

- Canvas: warm near-white
- Primary text: soft near-black
- Secondary text: muted warm gray
- Timeline accent: restrained amber
- Rules: pale warm gray

All text and interactive states must meet WCAG AA contrast requirements.

## Typography

Use the existing system sans-serif stack. Create hierarchy through size, weight,
spacing, and alignment rather than adding typefaces.

## Layout

- Keep the existing readable page width.
- Use a two-column timeline on larger screens.
- The left rail explains direction from Present to Past.
- The right column groups articles by month and year.
- Collapse to a compact single-column chronology on narrow screens.

## Components

### Timeline rail

A vertical line with endpoint markers and persistent Present and Past labels.
The labels communicate reading direction without relying on color.

### Time group

A month-and-year heading followed by article rows. Each row contains a precise
publication date and an article link.

### Links

Use underlines and strong contrast for recognition. Hover and focus states should
be visible without moving surrounding content.

## Motion

No motion is required. The chronology should be understandable in a static view.
