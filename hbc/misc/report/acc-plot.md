
## Group Plot Goals
---
#### Plot 1: Stacked Proportional Activity Bar — Group-Level Time Budget

**What it shows:** A horizontally stacked bar chart where each bar represents 100% of the waking day, divided into four activity intensity segments: sedentary, light, moderate, and vigorous. Two bars are shown side by side — one for weekdays and one for weekend days — allowing direct comparison of how daily time use shifts between work/school days and leisure days. A third bar can optionally show the overall average across all days.

**Data structure needed:** One row per group (weekday / weekend / all-days), with four columns representing the mean number of minutes spent in each intensity band. These should sum to a consistent total (e.g., ~960 waking minutes). If you have subgroups (intervention vs. control), you can extend this to one pair of bars per subgroup.

**Visual encoding:**

- X-axis: percentage of the day (0–100%)
- Y-axis: day type category (weekday, weekend)
- Fill color: four-segment color ramp from cool to warm — blue-gray for sedentary, yellow-green for light, orange for moderate, red for vigorous
- Tooltip on hover: shows the raw minutes and percentage for that segment
- Any minutes under // overcalculated must be accounted for

**Layout notes:** Bars are horizontal and thick. Legend sits below or to the right. Title reads something like "Group Average Daily Activity Composition." Axis labels show percentage ticks at 0, 25, 50, 75, 100%. The segment boundaries should have a thin white dividing line for readability.

---

#### Plot 2: Dual Heatmap — Sedentary Time and MVPA Across Study Sessions

**What it shows:** Two side-by-side rectangular heatmaps, each with participants as rows and study sessions (up to four) as columns. The left panel tracks sedentary behavior; the right panel tracks unstructured moderate-to-vigorous activity. The two panels are intentionally color-coded in opposite directions so that a "healthy" shift — less sedentary time and more active time — produces a visual mirror effect: the left panel fades from dark to light while the right panel deepens from light to dark as sessions progress.

**Data structure needed:** One row per participant per session, with columns for participant ID, session number (1–4), sedentary minutes, and MVPA minutes. Missing sessions are acceptable and will render as gray cells. Participants are sorted by their total change in sedentary time from first to last session so that the greatest improvers appear at the top.

**Visual encoding:**

- Rows: individual participants (no labels, too many to show)
- Columns: sessions 1 through 4
- Left panel color scale: white (low sedentary) → deep red (high sedentary); so improvement over time reads as the row getting lighter from left to right
- Right panel color scale: white (low MVPA) → deep teal (high MVPA); so improvement reads as the row getting darker from left to right
- Gray cells: missing session data
- A narrow diverging bar appended to the far right of both panels shows each participant's net change score (positive or negative delta from session 1 to last available session)
- Optional thin horizontal stripe between subgroups (intervention vs. control) with a label on the side
- Tooltip on hover: shows participant ID, session number, and the raw minute value

**Layout notes:** The two panels share the same row ordering and are separated by a small gap with a dividing label ("Sedentary" on the left, "MVPA" on the right). Color scale legends sit below each panel. A note beneath clarifies that participants are sorted by change in sedentary time.

---

#### Plot 3: Radial Activity Clock — Mean Acceleration by Hour of Day

**What it shows:** A circular 24-hour clock chart where the face is divided into 24 equal wedges, one per hour of the day. Midnight sits at the top (12 o'clock position), noon at the bottom. The outward length of each wedge represents the average movement intensity of the group at that hour. A shaded band around each wedge shows the spread across participants (±1 standard deviation). The chart conveys the group's daily activity rhythm at a glance — when they are most active, when they are sedentary, and whether there is a morning or afternoon activity peak.

**Data structure needed:** One row per hour of day (0–23), with columns for mean acceleration value and standard deviation across all participants. If you have subgroups, you can overlay two separate radial lines on the same clock face with different colors. The values can be simulated as a smooth daily curve peaking in the late morning and early afternoon, with a trough in the early morning hours.

**Visual encoding:**

- Angular position: hour of day (0–23), clockwise from midnight at top
- Radial distance: mean acceleration (in arbitrary movement units, scaled so the chart fills the circle comfortably)
- Shaded band: ±1 SD shown as a semi-transparent filled area between the inner and outer bounds of the deviation
- Fill/stroke color: a single accent color for the mean line (e.g., teal), with a lighter tint for the SD band
- Reference rings: two or three faint concentric circles at fixed acceleration values to act as a radial grid
- Hour tick marks around the outer edge at every 3 hours (midnight, 3am, 6am, 9am, noon, 3pm, 6pm, 9pm)
- Optional annotation markers at the hours corresponding to the most active 5-hour window midpoint and least active 5-hour window midpoint, labeled directly on the chart
- If subgroups are shown, two overlapping radial shapes in contrasting colors with a legend

**Layout notes:** The chart is square. The clock face is centered with a small white circle at the origin to avoid visual clutter at the center. The title sits above. A short caption below explains what the radial distance represents. No cartesian axes are shown — the circular grid rings serve as the scale reference.

---

These three descriptions should be self-contained enough to hand off to another tool, a collaborator, or a future version of yourself without needing to reference GGIR variable names at all. Want me to now go ahead and build the D3 interactive versions?



![[acc-plot.excalidraw 2026-03-25 09.42.15.excalidraw]]