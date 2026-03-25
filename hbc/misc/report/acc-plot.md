
# Group Accelerometer Plot Specification

**Version:** 2.0 — Post-Implementation  
**Last updated:** March 25, 2026  
**Study context:** Wrist-worn accelerometer study, 7–10 day wear period, 200 participants, repeated measures design (up to 4 sessions), two groups (Intervention and Observational/Control).  
**Processing pipeline:** GGIR (any version ≥ 2.5). Raw outputs are post-processed to person-level and day-level summaries before plotting.

---

## Canvas & Layout

The three plots share a single **1440 × 1024 px** frame with a light off-white background (`#F7F7F9`).

|Region|X|Y|Width|Height|
|---|---|---|---|---|
|Plot 1 card|60|40|1320|296|
|Plot 2 card|60|375|640|610|
|Plot 3 card|740|375|640|610|

All cards have `12px` corner radius and a white (`#FFFFFF`) background. Internal padding is `24px` on all sides.

**Font:** Inter (system fallback: -apple-system, sans-serif). Weights used: Regular (400), Medium (500), Semi Bold (600), Bold (700).

---

## Shared Color Palette

|Role|Hex|Usage|
|---|---|---|
|Sedentary|`#6B7890`|Activity band, heatmap scale base|
|Light|`#8CC299`|Activity band|
|Moderate|`#FCBA42`|Activity band|
|Vigorous|`#DE4545`|Activity band|
|Intervention|`#247F8F`|Teal — group color, MVPA heatmap scale|
|Observational|`#DE7833`|Orange — group color, radial clock line|
|Missing/neutral|`#E0E0E8`|Missing heatmap cells, grid lines|
|Background|`#F7F7F9`|Canvas background|
|Card surface|`#FFFFFF`|Plot card background|
|Text primary|`#212130`|Titles, row labels|
|Text secondary|`#737380`|Subtitles, axis labels, legends|

---

## Plot 1: Stacked Proportional Activity Bar

### Purpose

Show how the average waking day is divided across four movement intensity levels, comparing weekday vs. weekend vs. all-days averages at the group level.

### Data requirements

One summary row per day-type category. Required columns:

|Column|Type|Description|
|---|---|---|
|`day_type`|string|"All Days", "Weekdays", "Weekends"|
|`sed_min`|numeric|Mean sedentary minutes|
|`light_min`|numeric|Mean light activity minutes|
|`mod_min`|numeric|Mean moderate activity minutes|
|`vig_min`|numeric|Mean vigorous activity minutes|

**Important constraint:** The four minute values per row must sum to a consistent total representing the waking day. The recommended target total is **960 minutes** (16 waking hours). If your observed totals differ due to non-wear, invalid data, or different waking window definitions, normalize each row to 100% before plotting — the bars represent proportions, not raw minutes. Raw minutes are shown only in tooltips. The original spec noted "any minutes under // overcalculated must be accounted for" — in practice this means: compute proportions as `value / row_sum`, not `value / 960`, so each bar always sums exactly to 100% regardless of valid-data hours.

**Simulated values used in prototype:**

|Day type|Sedentary|Light|Moderate|Vigorous|
|---|---|---|---|---|
|All Days|498|320|108|34|
|Weekdays|520|305|98|37|
|Weekends|455|352|130|23|

### Visual encoding

- **Chart type:** Horizontal 100% stacked bar
- **X-axis:** Percentage of waking day (0–100%), with gridlines and tick labels at 0, 25, 50, 75, 100%
- **Y-axis:** Day type label (left of bar, 13px Medium, no axis line)
- **Bar height:** 46px per row, 20px gap between rows
- **Segment colors:** Sedentary → Light → Moderate → Vigorous, left to right (cool to warm)
- **Segment dividers:** 2px white lines between each color segment
- **Inline labels:** Percentage value centered in each segment if the segment width exceeds 44px; white Semi Bold 11px text. Narrow segments (vigorous typically) get no label.
- **Legend:** Colored 13×13px squares with 3px radius, labeled in 12px Regular secondary text, positioned below bars. Left-aligned starting at the bar left edge. Spacing: 115px between each item.
- **CI note:** Footnote text at 10px in secondary color: "CI/error bands available in interactive D3 version"

### Layout specifics

- **Label column width:** 84px (accommodates "Weekends" at 13px)
- **Bar left edge:** 196px from frame left (= 60 card x + 24 pad + 84 label + 12 gap + 16 for 0% tick)
- **Bar total width:** ~1124px
- **Gridline style:** 1px, `#E0E0E8`, full height of bar area
- **Gridline position:** Calculated as `bar_left + (pct / 100) * bar_width`

### D3 implementation notes

- Use `d3.scaleLinear([0, 1], [bar_left, bar_right])` for x positioning
- Compute proportion values on the fly: `d.sed / (d.sed + d.light + d.mod + d.vig)`
- Use `d3.stack()` with keys `['sed','light','mod','vig']` on normalized data
- Tooltip: on mouseover show `{band_name}: {raw_minutes} min ({pct}%)`

---

## Plot 2: Participant × Session Heatmap

### Purpose

Reveal individual-level longitudinal change in sedentary behavior and unbouted MVPA across up to 4 study sessions, making the group-level trend and individual heterogeneity visible simultaneously.

### Data requirements

One row per participant per session. Required columns:

|Column|Type|Description|
|---|---|---|
|`participant_id`|string|Unique ID|
|`session`|integer|1, 2, 3, or 4|
|`group`|string|"Intervention" or "Observational"|
|`sed_min`|numeric|Mean sedentary minutes for that session|
|`mvpa_min`|numeric|Mean unbouted MVPA minutes for that session|

**Missing sessions:** If a participant did not complete a session (e.g., only has S1, S2, S4), the missing session cell renders as neutral gray (`#E0E0E8`). Do not impute.

**MVPA definition used here:** Unbouted MVPA — all minutes meeting the moderate-to-vigorous acceleration threshold, regardless of whether they occur in sustained bouts. This is distinct from bouted MVPA (which requires a minimum continuous duration). Both come from the same GGIR output file but are different columns. This distinction was a deliberate design choice made during brainstorming.

**Simulated ranges used in prototype:**

- Sedentary: 250–620 min/day
- Unbouted MVPA: 5–110 min/day
- Intervention group (n=30): Sedentary decreases ~30–90 min over study; MVPA increases ~8–33 min
- Observational group (n=30): Sedentary changes modestly (~±25 min); MVPA changes ~2–14 min

### Row sorting

Participants are sorted by their **change in sedentary time** from first to last available session (`sed_last - sed_first`), ascending. This puts the participants with the greatest decrease in sedentary time at the top of the chart, maximizing the visual "mirror effect" between the two panels. Participants with identical change scores can be sorted by baseline sedentary time as a tiebreaker.

### Panel layout

Two side-by-side heatmap panels within the 640×610px card:

|Element|Position/Size|
|---|---|
|Card padding|24px all sides|
|Inner width|592px|
|Sedentary panel width|~270px (4 columns × ~67px cell width)|
|Δ column (sedentary)|16px wide, 4px gap from panel|
|Gap between panels|10px|
|MVPA panel width|~270px|
|Δ column (MVPA)|16px wide, 4px gap from panel|
|Session column labels|"S1" "S2" "S3" "S4" above each column, 8px Medium|
|Row height|`floor(available_height / N_participants)`|

**Exact cell dimensions from prototype (60 participants):**

- Cell width: 66px per session column
- Cell height: 8px per participant row (compact, no row labels)

### Color scales

**Sedentary panel:** White (low) → Deep red (high)

- Low sedentary = healthy = white/light
- High sedentary = problematic = `#DE4545` deep red
- Interpolation: `r = clamp(0.90 + 0.50*t), g = clamp(0.90 - 0.65*t), b = clamp(0.90 - 0.65*t)` where `t` = normalized value 0–1
- Global min/max computed across all participants and sessions (not per-session)

**MVPA panel:** White (low) → Deep teal (high)

- Low MVPA = less active = white/light
- High MVPA = active = `#247F8F` teal
- Interpolation: `r = clamp(0.95 - 0.80*t), g = clamp(0.95 - 0.43*t), b = clamp(0.95 - 0.39*t)`
- Global min/max computed across all participants and sessions

**The intentional mirror effect:** A participant who improved will show a row fading from red→white (left to right) in the sedentary panel AND deepening from white→teal in the MVPA panel. This simultaneous pattern is the core visual story.

### Delta bars

A narrow 16px-wide column appears to the right of each panel showing each participant's net change:

- **Sedentary Δ bar:** Bar height proportional to `|Δsed| / max_abs_delta_sed`. Color: teal if delta is negative (improvement = less sedentary), red if delta is positive (worsening).
- **MVPA Δ bar:** Bar height proportional to `|Δmvpa| / max_abs_delta_mvpa`. Color: teal if delta is positive (improvement = more MVPA), red if negative.
- Background of delta column: `#EDEDED` light gray strip
- Bar centered vertically within the row

### Group divider

A 2px horizontal line in primary text color (`#212130`) separates the Intervention group rows from the Observational group rows. Labels "▲ Intervention" and "▼ Observational" appear in 8px Semi Bold secondary text immediately above and below the divider line. In the prototype, the Intervention group (n=30) is sorted to the top and Observational (n=30) to the bottom, each group internally sorted by delta.

### Color scale legends

At the bottom of the card, two gradient bars (70px wide × 7px tall, rendered as 70 individual 1px-wide rectangles) with "Low" and "High" text labels. The sedentary gradient appears at the left starting position of the sedentary panel; the MVPA gradient at the left starting position of the MVPA panel.

### D3 implementation notes

- Use `d3.scaleSequential` with a custom interpolator for each color scale
- Cell rendering: `d3.select().append('rect')` for each cell — avoid canvas unless N > 500
- Tooltip: show `participant_id`, `session`, `sed_min` or `mvpa_min` depending on panel
- Group divider: computed as `interventionCount * cellHeight` from the top of the grid
- For real data with hundreds of participants, compress row height to 2–3px and remove session column labels from view (they're still readable at that scale as hairline bands)

---

## Plot 3: Radial Activity Clock

### Purpose

Show when during the day the group is most and least active, using a 24-hour polar chart that maps mean acceleration intensity at each hour to radial distance from center. Overlays two group lines and a spread band.

### Data requirements

One row per hour of day (hours 0–23), repeated for each group. Required columns:

|Column|Type|Description|
|---|---|---|
|`hour`|integer|0–23, where 0 = midnight|
|`group`|string|"Intervention" or "Observational"|
|`mean_enmo`|numeric|Mean acceleration (mg) at that hour across all participants and valid days|
|`sd_enmo`|numeric|Standard deviation of acceleration at that hour|

**What "acceleration" means here:** ENMO (Euclidean Norm Minus One, in milli-g units). This is the primary movement metric from GGIR. Values near 0 indicate rest/sleep; values around 30–60mg indicate light movement; values above 100mg indicate moderate-to-vigorous activity. The MVPA threshold used in this chart is **100mg**.

**Simulated curve used in prototype:** The daily acceleration curve was modeled as a smooth composite of Gaussian peaks:

- Primary peak centered at 10:30am (amplitude ~70mg above baseline)
- Secondary peak at 3pm (amplitude ~50mg)
- Morning ramp at 8am (amplitude ~20mg)
- Lunch dip at 1pm (suppression ~15mg)
- Baseline sleep level: ~8mg
- SD modeled as `8 + mean * 0.28` (higher SD during active hours)
- Intervention group multiplied by 1.12 during hours 8–21 (12% more active)

### Coordinate system

- **Origin:** Chart center
- **Angle 0°:** Top of circle (12 o'clock = midnight)
- **Direction:** Clockwise
- **Hour-to-angle:** `angle_degrees = (hour / 24) * 360`
- **Converting to x,y:** `x = cx + r * cos((angle - 90) * π/180)`, `y = cy + r * sin((angle - 90) * π/180)`

### Radial scale

|Parameter|Value|
|---|---|
|Max radius (R_MAX)|195px from center|
|Min radius / hub (R_MIN)|46px (white circle covers center clutter)|
|Value → radius|`R_MIN + (value / global_max) * (R_MAX - R_MIN)`|
|Global max|`max(mean_enmo + sd_enmo)` across all hours and groups|

**Three reference rings** at 33%, 66%, and 100% of R_MAX:

- Ring 1: `R_MIN + 0.33 * (R_MAX - R_MIN)` ≈ 95px
- Ring 2: `R_MIN + 0.66 * (R_MAX - R_MIN)` ≈ 145px
- Ring 3: R_MAX = 195px
- Style: 1px stroke, `#E0E0E8`, opacity 30–50%

**MVPA threshold ring** at radius corresponding to 100mg:

- `R_MIN + (100 / global_max) * (R_MAX - R_MIN)`
- Style: 1.5px stroke, orange `#FCBA42`, opacity 70%
- Labeled "MVPA threshold (100mg)" in 8px orange text near the 11 o'clock position

### Rendered elements (in draw order)

1. Reference rings (3 faint circles)
2. ±1 SD filled band — a closed polygon formed by the outer edge (mean + SD for each hour) going clockwise then the inner edge (mean − SD) going counter-clockwise. Fill: teal `#247F8F`, opacity 12%. Smoothed using 4 interpolation steps between hour samples.
3. Observational group mean line — vector path connecting 25 points (hours 0–24, wrapping back to 0), 1.5px orange stroke
4. Intervention group mean line — same structure, 2.5px teal stroke
5. MVPA threshold ring
6. Hub white circle (R = 44px, white fill, covers origin clutter)
7. Hour tick marks — 24 ticks around the outer edge: major ticks (every 3 hours) extend 14px, minor ticks extend 8px. Major ticks: 1.5px, secondary color. Minor ticks: 1px, divider color.
8. Hour labels — 8 labels at 3-hour intervals (12am, 3am, 6am, 9am, 12pm, 3pm, 6pm, 9pm), 9px Regular, positioned 26px beyond R_MAX tick. Offset logic: top/bottom labels center-aligned, left labels right-offset, right labels left-offset.
9. Ring value labels — mg annotation at ~5° angle for each ring (e.g., "38mg", "76mg", "115mg"), 8px, ring color
10. M5 and L5 annotation dots — 5px radius filled circles at the hours of peak (M5, ~10:30am) and trough (L5, ~2:30am) acceleration. M5 dot: teal; L5 dot: orange. Labels: "M5 peak" and "L5 trough" in 8px Semi Bold text, offset so they don't overlap the line.

### Clock center position

In the prototype: `cx = card_x + card_width/2 = 1060px`, `cy = card_y + title_height + (remaining_height/2) + 10px ≈ 695px`

### Legend (bottom of card)

Four items at the base of the card:

1. **±1 SD band** — 20×10px teal rectangle at 12% opacity + label
2. **Intervention** — 20×2.5px teal rectangle (simulating a line) + label
3. **Observational** — 20×1.5px orange rectangle + label
4. **MVPA threshold** — 20×1.5px orange rectangle + label

### D3 implementation notes

- Use `d3.lineRadial()` with `.angle(d => (d.hour / 24) * 2 * Math.PI)` and `.radius(d => rScale(d.mean_enmo))` for group mean lines
- Build SD band using `d3.areaRadial()` with `.innerRadius()` and `.outerRadius()`
- For smooth curves, set `.curve(d3.curveCardinalClosed)` or interpolate to sub-hour resolution before drawing
- Append duplicate of hour-0 point at end of array to close the line cleanly
- MVPA threshold ring: `d3.arc()` with full 2π sweep at the threshold radius, or simply draw a full circle using SVG `<circle>`

---

## Implementation Assumptions & Decisions Made

The following are decisions made implicitly during implementation that are not obvious from the original brief:

### General

- **N displayed in prototype:** 60 participants for Plot 2 (not the full 200) for Figma render performance. D3 implementation should use full N.
- **Simulated data seed:** All random data used a seeded LCG (seed=42) for reproducibility. In D3 implementation, real data replaces all simulated values.
- **Font:** Inter was chosen as the Figma system font. In D3/HTML, use `font-family: 'Inter', -apple-system, sans-serif`.
- **Group names:** "Control" was relabeled to "Observational" in the final Figma render (visible in Plot 3 legend as "Observational"). Ensure consistency with what your study protocol calls the non-intervention arm.

### Plot 1 specific

- The three bar rows are ordered top-to-bottom: All Days, Weekdays, Weekends. This is arbitrary — reorder based on what comparison is most important for your audience.
- If you add Intervention vs. Observational as separate sub-bars, the card height will need to increase and rows will need to be grouped visually (e.g., with a small divider or background band).
- The vigorous segment (typically <5% of the day) often renders too narrow for an inline label. The 44px threshold for showing inline text was determined empirically.

### Plot 2 specific

- **"Unbouted MVPA"** is clearly labeled in the panel header to distinguish from bouted MVPA. This is important because bouted MVPA values are substantially lower and the two metrics are not interchangeable.
- **Delta bar normalization:** The sedentary delta bar is normalized to the maximum absolute change across all participants. The MVPA delta bar uses its own maximum. This means the two delta columns are not directly comparable in scale — they show relative change within each variable.
- **Row ordering applies globally:** Both the sedentary and MVPA panels share the same row ordering (sorted by sedentary delta). This is intentional — the MVPA panel is a companion view, not independently sorted.
- **Color channel math:** All RGB color interpolation values are clamped to [0, 1] to prevent Figma API errors. In D3, `d3.interpolateRgb` handles this automatically.
- The legend gradient bars were rendered as 70 individual 1px-wide rectangles in Figma (due to Plugin API limitations). In D3, use a `linearGradient` SVG element instead for cleaner output.

### Plot 3 specific

- **Clock orientation:** Midnight at top (12 o'clock position) was chosen to match how accelerometer data is conventionally displayed in circadian rhythm research. This means the active period (daytime) occupies the bottom half of the clock and the sleep period occupies the top.
- **M5/L5 annotation placement:** M5 (most active 5-hour window) peak was placed at ~10:30am; L5 (least active 5-hour window) trough at ~2:30am. These are derived from your GGIR output (variables `M5hr` and `L5hr`) and will differ for your actual data. The annotation positions must be updated accordingly.
- **SD band polygon smoothing:** The ±1 SD band was computed at 4 interpolation steps per hour (96 points total) to produce a smooth curve rather than a jagged 24-point polygon. In D3, using `curveCardinalClosed` on 24 hourly points achieves a similar result without manual interpolation.
- **Hub radius:** The white center circle (R=44px) was sized to mask the visual clutter where all radial lines converge at low-activity hours (overnight). Without it, the overnight lines bunch into a visually noisy cluster at the origin.
- **Intervention line weight:** 2.5px vs 1.5px for Observational. The heavier weight for Intervention reflects that this is typically the "primary" group of interest. Swap if your study is observational-only.
- **The MVPA threshold ring** is drawn at 100mg ENMO. This threshold is commonly used in the literature for wrist-worn accelerometers using ENMO, but your study may have used a different cut-point (e.g., 80mg, 120mg). The ring position in the chart will scale automatically if you update the threshold value relative to the global max.

---

## File Reference

**Figma file:** https://www.figma.com/design/yteer4gUc7ZkGKFOBgKlPk/Boost-Report-Figures  
**Page:** Accelerometer Plot  
**Frame node ID:** 16:3 (Desktop - 1, 1440×1024px)