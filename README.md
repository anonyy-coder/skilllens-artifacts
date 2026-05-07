# SkillLens — Artifacts

Artifacts accompanying the SkillLens paper submission: per-skill evaluation
reports (utility + security) across eight harness × model runs, the
constructed judge-item task suite, and (forthcoming) replayable execution
traces.

> **Anonymous review build.** This repository is maintained for the duration of
> peer review. All identifying information (author names, affiliations, contact
> details, funding sources) has been intentionally omitted in accordance with
> double-blind review policy.

## Browse

**→ https://anonyy-coder.github.io/skilllens-artifacts/**

The site provides:

- A search-first **skill explorer** — open any of 227 skills and see its
  pass-rate gain, efficiency, security score, and finding counts side-by-side
  across all eight runs.
- A **judge sheet** view exposing the constructed task suite per skill: three
  capability-targeted scenarios (`U1`, `U2`, `U3`) with their full set of
  binary judge items and per-item rationales (`wi_skills` vs `wo_skills`).
- A **run matrix** showing which harnesses and models cover which evaluation
  axis (utility, security, or both).
- A **traces** placeholder for the upcoming sandbox replay artifacts.

## Layout

```
docs/
├── index.html         # the page
├── assets/
│   ├── style.css
│   └── app.js
└── data/
    ├── index.json     # all skills × all runs (light index)
    ├── stats.json     # aggregate statistics
    └── skills/        # 226 per-skill files (utility details + security)
```

## Sanitization

The published artifacts pass through a sanitization step before reaching this
repository. Specifically:

- **Owner identifiers** (50 unique upstream skill creators in the source
  dataset) are replaced with deterministic anonymous tokens in the form
  `anon-NNN`. The mapping is not published.
- **Internal pipeline paths** of the form `/home/<user>/...`,
  `/Users/<user>/...`, and the literal substring naming the offline build
  harness are replaced with `[redacted-path]` / `[redacted]`.
- **Path-bearing fields** (`skill_path`, `wi_path`, `wo_path`) are dropped.

Skill names, judge criteria, and behavioral evidence are preserved verbatim
to retain benchmark transparency. Some skill names and finding texts may
reference upstream tooling whose names happen to match an anonymized owner;
this is the skill's own behavior under test, not an identity leak.

## Related

- Project page: https://anonyy-coder.github.io/

## License

License terms will be finalized upon de-anonymization.
Until then, all material is provided **for peer-review purposes only**.
