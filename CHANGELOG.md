# Changelog

All notable public changes to Project State Governor are documented here.

## [Unreleased]

### Fixed

- Align workstream completion with `COMPLETED` and retain the `CANCELLED` milestone lifecycle state in the canonical schema.

## [1.0.4] - 2026-08-24

### Added

- Add a worked compact-state example showing evidence classification, status preservation, and the verification gate before `DONE`.

## [1.0.3] - 2026-08-24

### Fixed

- Apply complete candidate-directory and recursive nested `AGENTS.md` discovery in the routed reconstruction workflow.
- Preserve verified terminal task and workstream transitions explicitly in scaled-mode `STATE.md`.
- Preserve the existing lifecycle status when a completion claim lacks sufficient verification instead of inventing an `ACTIVE` or `BLOCKED` transition.

## [1.0.2] - 2026-08-24

### Fixed

- Include an existing candidate directory itself, plus every nested instruction file for recursive operations, when resolving applicable `AGENTS.md` rules.
- Add `PAUSED` to the canonical milestone lifecycle so paused work is not misreported as blocked or deferred.
- Preserve terminal `COMPLETED` and `CANCELLED` workstream transitions in the canonical schema and consolidation guidance.
- Put applicable legal, authorization, non-waivable security/safety, and objective constraints outside the owner-mutable evidence hierarchy.

## [1.0.1] - 2026-08-20

### Fixed

- Require the complete applicable `AGENTS.md` chain before inspecting or mutating nested cleanup targets.
- Add `DONE` and `CANCELLED` to the canonical task-state schema and define terminal-record consolidation.

## [1.0.0] - 2026-08-20

### Added

- English and Simplified Chinese user documentation.
- Reusable directory-listing copy for catalogs and community showcases.
- Contribution and security guidance.
- Codex UI metadata with a concise description and default prompt.
- An original project icon for the public distribution.

### Included

- Canonical project-state schema and compact/scaled layout guidance.
- Evidence-aware persistence lifecycle.
- Repository state reconstruction workflow.
- Manifest routing guidance for larger projects.
