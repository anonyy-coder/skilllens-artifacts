# SkillLens — Artifacts

Artifacts accompanying the SkillLens paper submission: per-skill evaluation
reports (utility + security) across eight harness × model runs, the
constructed judge-item task suite, the aggregate CSV / index / SHA-256
checksums, and a search-first browser UI over all of it. Full per-trial
trajectories are scheduled for a separate post-review release (see below).

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
- A **traces** placeholder reserved for the post-review trajectory bundle
  (see "Trajectory release timing" below).

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
    ├── skills/        # 227 per-skill files (utility details + security)
    └── checksums.txt  # SHA-256 over every published file in this tree
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

## Trajectory release timing

The artifacts published here cover the **evaluation outcomes** of the
227-skill × 8-run sweep — what each LLM judge concluded, scored against
the constructed task suite, with full integrity checksums. They are
sufficient to evaluate the methodology and reproduce the headline numbers
when paired with the published evaluator code.

Full per-trial trajectories — the raw `trajectory.json`, agent stdout,
verifier output, and Harbor sandbox state for each rollout — are not
included in this repository. Two reasons:

1. **Size.** The unpacked corpus is ~150–300 GB. A bundled, compressed
   release on GitHub is workable but not appropriate inside an active
   review repository.
2. **Sanitization audit.** Per-trial output requires an additional
   sanitization pass beyond what summary JSONs already received
   (mock-network capture logs, transient sandbox API endpoints,
   container-internal absolute paths). That audit is best done with
   the de-anonymized author identity available, so reviewers and
   downstream users can trace the audit decisions back to a real
   maintainer rather than a placeholder account.

The trajectory bundle will be released as a companion download
(GitHub Release attached to this repository) **after the review period
concludes**. Reviewers do not need it to assess the paper's claims:
the per-skill JSONs under `docs/data/skills/*.json` already carry the
LLM-judge verdicts and capability-dimension scoring.

## Related

- Project page: https://anonyy-coder.github.io/SkillLens/
- Code framework: https://github.com/anonyy-coder/SkillLens

## License

License terms will be finalized upon de-anonymization.
Until then, all material is provided **for peer-review purposes only**.
