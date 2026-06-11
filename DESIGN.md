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
- **Main Blue**: `rgb(104, 106, 168)`. Reserve for the timeline rail,
  endpoint markers, directional arrow, button hover shadows, and keyboard focus
  outlines. Do not use it for broad surface fills or resting button fills.
- **Main Green**: `rgb(80, 110, 95)`


The active palette is Warm Ivory, Soft Black, and Main Blue. All text and
interactive states must meet WCAG AA contrast requirements.

## Typography

Use the native system sans-serif stack for all text, including article titles,
navigation, dates, and body copy. Do not load an external web font. Create
hierarchy through size, weight, spacing, and alignment.

## Layout

- Keep the existing readable page width.
- Use a two-column timeline on larger screens.
- The left rail remains sticky and fills the available viewport height while
  the page's article column scrolls.
- The right column groups articles by month and year.
- Collapse to a compact single-column chronology on narrow screens.

## Components

### Timeline rail

A vertical line with endpoint markers and persistent Present and Past labels.
The line, markers, and directional arrow use Main Blue. The labels use Soft
Black and communicate reading direction without relying on color. The Present
marker is filled Main Blue; the Past marker is hollow. On desktop, the rail is
sticky and sized to the viewport. On mobile, it becomes a horizontal guide.

### Time group

A month-and-year heading followed by article rows. Each row contains a precise
publication date, one or more categories, an article link, and a Read article
button. Categories come from a YAML array in article front matter:

```yaml
categories:
  - Technology
  - Essays
```

### Links

All text links use Soft Black with conventional underlines. Main Blue is used
for keyboard focus outlines. Hover and focus states should be visible without
moving surrounding content.

### Read article button

Every timeline entry includes a pill-shaped "Read article" link beside its title.
The button is transparent at rest, with Soft Black text, a subtle white edge,
inner light, restrained backdrop blur, and a faint Main Blue shadow. On hover,
the Main Blue shadow becomes darker and the pill lifts slightly; when hover ends,
the shadow returns smoothly to its resting intensity. Main Blue must not appear
as a resting fill or border. The label must remain readable without depending on
the glass effect.

## Motion

The chronology must remain understandable in a static view. Limit motion to the
Read article button: a short ease-out lift, a deepening Main Blue shadow, and a
small arrow shift. Respect the user's reduced-motion preference.
