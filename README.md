# release-readiness-copilot
Release Readiness Copilot
# Release Readiness Copilot

A lightweight go / no-go decision aid for software releases. Enter release signals and get a clear verdict, the reasons behind it, and the steps that would change the call.

**Live demo:** [Netlify link here]
**Walkthrough video:** [Loom link here]

Problem
Release go/no-go decisions are often made in meetings from scattered inputs (spreadsheets, test reports, verbal updates). Important points can be missed, and the reasoning is hard to reconstruct later, especially in regulated domains.

In several organizations I worked in, the go/no-go decision was rarely written down in a consistent way. Some teams tracked it in Excel, and many decisions were made in face-to-face conversations. Important points could get missed, and it was hard to look back and see why a decision was made.

Solution
Eight release signals go in; a Go, Conditional Go, or No-Go verdict comes out, with:
- a 0 to 100 readiness score on a live gauge
- a gate-by-gate explanation in plain language
- a "What would change it" path, with the projected verdict after each step
- a read-only stakeholder view with a copyable memo and print/PDF option

Key product decisions
- Hard blockers (open critical bugs, security or compliance issues) always force a No-Go, whatever the score.
- Three outcomes, not two, because real releases often ship with owned mitigations.
- Every verdict is explained, so the tool supports human judgment instead of replacing it.
- Separate team and stakeholder views for two different audiences.
- Plain-language inputs with a one-line explanation each.

Trade-offs
- Transparent rules instead of a predictive model: no historical release data, and teams trust what they can audit.
- Manual entry instead of integrations (Jira, CI/CD): keeps it free and instantly usable.
- Fixed weights and thresholds: deliberately cut configurability until there is evidence teams need it.

Technical implementation
- Single static file: vanilla HTML, CSS, and JavaScript, no framework or build step.
- Weighted-gate scoring, with hard-blocker gates checked first.
- Path to Go: unresolved gates are fixed in priority order (blockers first, then by points gained), and the verdict is recomputed after each step.
- Responsive layout, light and dark themes, sticky verdict bar on mobile.
- Runs entirely in the browser; no data is stored or sent anywhere.

Run locally
Open `index.html` in any browser.

Deploy
Drag this folder onto https://app.netlify.com/drop, or connect the GitHub repo to Netlify with no build command and the publish directory set to the repo root.

What I would build next
1. Jira and CI/CD integrations to fill in the signals automatically.
2. Trend history across releases.
3. Configurable weights and thresholds, if usability testing shows teams need them.
4. Calibrating the weights against past release and incident outcomes.
