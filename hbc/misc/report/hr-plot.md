
# D3 Plot Specification: HR Zone Analysis Dashboard

## Background & Data Context

These plots visualise heart rate (HR) zone adherence from a cardiac exercise study.
Participants wore HR monitors during sessions over 6 weeks. Each session's HR trace
(60 Hz readings) was summarised into the following zone-time metrics per row in the
source CSV (`zone_out.csv`):

| Field               | Type    | Description                                                                                         |
| ------------------- | ------- | --------------------------------------------------------------------------------------------------- |
| `group`             | string  | `"Supervised"` or `"Unsupervised"` — whether sessions were clinician-led                            |
| `subject`           | string  | Participant ID, e.g. `sub8000`                                                                      |
| `week`              | integer | Study week number (1–6)                                                                             |
| `session`           | integer | Session number (not used in these plots)                                                            |
| `time_in_allowed_s` | float   | Seconds with HR inside the target zone                                                              |
| `time_above_s`      | float   | Seconds with HR above the target zone                                                               |
| `time_below_s`      | float   | Seconds with HR below the target zone                                                               |
| `bounded_met`       | boolean | `true` if the subject maintained a sufficiently long continuous bout within zone; `false` otherwise |

The total session length is approximately 2401 seconds (40 minutes).
All time values are in seconds.

---

## Overall Layout

- Canvas: `1440 × 1024 px`, background `#fafafc`
- Two side-by-side white cards with `border-radius: 12px` and a subtle drop shadow
  (`box-shadow: 0 2px 16px rgba(0,0,0,0.07)`)
- Font: **Inter** throughout. Sizes: 14px bold titles, 10px regular subtitles,
  9px axis labels/legend, 8px heatmap labels
- Label colour: `#1a1a26` (titles), `#80808f` (all axis labels, subtitles, legend text)
- Grid line colour: `#e5e5ed`, 1px height

---

## Colour Tokens

```

BLUE (Supervised) #3378de 
ORANGE (Unsupervised) #f5802e 
GREEN (In Zone) #3bbd8c 
RED (Above) #f04545 
LIGHT_BLUE (Below) #8cb8f5 
GREY (No Data) #e5e5ed

```

---

## Plot 1 — Zone Time Allocation by Group & Week

### What it shows
A grouped stacked bar chart. For each of the 6 study weeks, two bars appear
side-by-side: one for Supervised sessions (blue group), one for Unsupervised
(orange group). Each bar is divided into three stacked segments representing the
mean seconds spent **below**, **in**, and **above** the HR target zone.

### Card dimensions
- Position: top-left of canvas, `x: 60, y: 50`
- Width: `620px`, Height: `380px`

### Chart area margins (inside the card)
- Left: `80px` (for y-axis labels)
- Top: `60px` (for title + subtitle)
- Right: `20px`
- Bottom: `80px` (for x-axis labels + legend)

### Data preparation
Aggregate `zone_out.csv` by `(group, week)`:
- Compute mean of `time_in_allowed_s`, `time_above_s`, `time_below_s` per group per week.
- Each bar therefore has exactly three stacked segments.

### Scales
- **y-axis**: linear, domain `[0, 2401]` (total session seconds), range `[chartHeight, 0]`
- **x-axis**: two nested levels
  - Outer: `scaleBand` over weeks 1–6, with `paddingOuter(0.1)` and `paddingInner(0.2)`
  - Inner: `scaleBand` over `["Supervised", "Unsupervised"]` within each week cluster,
    with `paddingInner(0.1)`

### Stacking
Use `d3.stack()` with keys `["time_below_s", "time_in_allowed_s", "time_above_s"]`
applied separately per group. Stack order bottom-to-top: below → in-zone → above.

### Bar colours
- `time_below_s` → `#8cb8f5` (light blue)
- `time_in_allowed_s` → `#3bbd8c` (green)
- `time_above_s` → `#f04545` (red)

### Grid lines
Horizontal lines at y = 0, 600, 1200, 1800, 2400 seconds.
Colour `#e5e5ed`, no tick marks, labels left-aligned at `chartLeft - 4px`.

### Axis labels
- y-axis title: `"Seconds"`, rotated -90°, positioned mid-chart-height, `14px` left of axis
- x-axis: week labels `"Wk 1"` … `"Wk 6"` centred on each cluster, `8px` below chart bottom

### Legend (bottom of card)
Five items in a horizontal row at `y = cardTop + cardHeight - 28`:
1. Green square → `"In Zone"`
2. Red square → `"Above"`
3. Light-blue square → `"Below"`
4. Blue square → `"Supervised"`
5. Orange square → `"Unsupervised"`

Each legend marker is a `10×10px` rectangle with `border-radius: 2px`, followed
by text `12px` to the right. Items spaced `90px` apart horizontally.

### Title block
- Title: `"Zone Time Allocation by Group & Week"`, `14px`, bold, `#1a1a26`
- Subtitle: `"Mean seconds per session · Supervised vs Unsupervised"`, `10px`, `#80808f`
- Both left-aligned, `8px` vertical gap, positioned `18px` from card top, starting
  at `chartLeft`

---

## Plot 2 — bounded_met Adherence Rate Over Weeks

### What it shows
This card contains **two stacked panels**:
1. **(Top) Line chart** — the proportion of sessions per week where `bounded_met == true`,
   for each group, with a shaded ±1 SD confidence band.
2. **(Bottom) Heatmap** — individual subject adherence across all 6 weeks; one row per
   subject, one column per week, coloured by met / not met / no data.

### Card dimensions
- Position: `x: 723, y: 40`
- Width: `660px`, Height: `501px`

### Chart area margins (shared left/right)
- Left: `70px`
- Right: `20px`
- Top (line chart): `60px`
- The line chart occupies the top **~62%** of the inner height
- The heatmap occupies the lower **~38%**, with a `36px` gap below the line chart's x-axis

---

### Panel A — Line Chart

#### Data preparation
Group `zone_out.csv` by `(group, week, subject)`. For each `(group, week)`:
1. Count sessions where `bounded_met == true` divided by total sessions → **adherence rate**
2. Compute standard deviation of per-subject adherence rates → **SD band**

#### Scales
- **x**: `scalePoint` over weeks 1–6, range `[0, lineChartWidth]`, padding `0.1`
- **y**: linear, domain `[0, 1]`, range `[lineChartHeight, 0]`

#### SD band
Render as a `d3.area()` path for each group:
- `y0 = rate - sd`, `y1 = rate + sd`, clipped to `[0, 1]`
- Fill: group colour at **15% opacity**
- No stroke on the band

#### Lines
One `d3.line()` path per group, `stroke-width: 2.5px`, no fill.
- Supervised → `#3378de`
- Unsupervised → `#f5802e`

#### Dots
`r: 5px` circle at each data point, filled with group colour, no stroke.

#### Grid lines
Horizontal lines at 0%, 25%, 50%, 75%, 100%.
Colour `#e5e5ed`. y-axis labels: `"0%"` … `"100%"` left of axis.

#### x-axis labels
`"Wk 1"` … `"Wk 6"` centred on each x-position, `8px` below the axis.

#### Legend (top-right of card)
Two items stacked vertically at top-right of card (`x ≈ cardRight - 80px`):
- Blue square + `"Supervised"`
- Orange square + `"Unsupervised"`
Each `10×10px` marker, `border-radius: 2px`, label `12px` to the right.

---

### Panel B — Heatmap

#### Position
Starts `36px` below the line chart x-axis baseline.

#### Dimensions
- **Rows**: one per unique subject (sort alphabetically)
- **Columns**: 6 (weeks 1–6)
- Cell width: `(lineChartWidth / 6) - 2px`
- Cell height: `18px` (or shrink proportionally if more subjects)
- Row gap: `2px`, column gap: `2px`
- Cell `border-radius: 2px`

#### Colour encoding
| `bounded_met` value | Colour |
|---|---|
| `true` | `#3bbd8c` (green) |
| `false` | `#f04545` (red) |
| missing / no session | `#e5e5ed` (grey) |

#### Labels
- **Column headers** (`"W1"` … `"W6"`): centred above each column, `8px` font, `#80808f`,
  `12px` above the first row
- **Row labels** (subject IDs): right-aligned `60px` to the left of the grid, `8px` font,
  vertically centred on each row

#### Sub-panel title
`"Individual Adherence Heatmap (bounded_met per subject × week)"`, `9px`, `#80808f`,
bold, `14px` above the column headers.

#### Legend (bottom of card)
Three items horizontal, `4px` below the last heatmap row:
1. Green square → `"Met"`
2. Red square → `"Not Met"`
3. Grey square → `"No Data"`

---

## D3 Implementation Notes

- Use `d3.rollup` or `d3.group` to aggregate the CSV before drawing.
- Both plots share the same SVG coordinate system if rendered in one `<svg>`; otherwise
  use two separate SVGs absolutely positioned to match the card layout.
- The SD band and line chart should use `clipPath` to prevent overflow beyond the
  chart area.
- Recommend `d3.v7` (`import * as d3 from "https://cdn.jsdelivr.net/npm/d3@7/+esm"`).
- Load the CSV with `d3.csv("zone_out.csv", d3.autoType)` — `autoType` will correctly
  parse `bounded_met` as a boolean and numeric columns as numbers.