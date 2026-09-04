Title: Add province 'Dominant Culture' column to Provinces Editor

Summary:
- Compute population-weighted dominant culture per province.
- Display a new "Dominant Culture" column next to the province capital column in the Provinces Editor, showing a swatch, culture name and percentage share.

Files changed:
- public/modules/ui/provinces-editor.js
  - Added computation of `p.dominantCulture` and `p.dominantCultureShare` in `collectStatistics()`.
  - Inserted `provinceDominantCulture` markup into province row HTML.
  - Inline styling added to keep the UI compact.

Why:
- Helps users quickly see which culture is dominant in a province by population.

Testing instructions:
1. Run the app locally (open the project and serve `public/` with a static server or run the project's dev workflow).
2. Generate or load a map with cultures and provinces.
3. Open UI → Provinces Editor and enable the Dominant Culture column if hidden (column elements use `hide` class by default).
4. Verify that each province row shows a swatch, culture name, and percentage that matches expected population distribution. Check edge cases: provinces without cells, provinces with no burgs, or ties.

Notes / Suggestions:
- The percentage is population-weighted (rural + urban). If you prefer cell-count weighting instead, I can adjust the calculation.
- Consider adding a toggle in the UI header to show/hide the Dominant Culture column, and a tooltip explaining the calculation.

Next steps I can take:
- Add a CSS rule in the main stylesheet instead of inline styles.
- Add a unit test or logger for the dominant-culture computation (if project has test harness).
- Create a Git branch and a PR with these changes and this draft as description.

Reviewer checklist:
- Confirm computation logic aligns with project expectations (population weights and urbanization handling).
- Confirm where the column should be shown by default and any localization strings.
