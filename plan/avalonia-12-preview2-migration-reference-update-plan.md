# Avalonia 12.0.0-preview2 Migration Reference Update Plan

## Objective

Extend the skill with a dedicated Avalonia 12 preview migration lane without changing the repository-wide stable pin of `11.3.12`.

## Plan

1. Verify the latest upstream preview tag.
- status: completed
- result: `12.0.0-preview2` verified on `2026-03-14`.

2. Build a reproducible break/new API inventory.
- status: completed
- deliverables:
  - `scripts/generate_api_migration_report.py`
  - `scripts/test_generate_api_migration_report.py`
  - generated preview migration catalog under `references/69-...`

3. Generate a preview-specific public API index.
- status: completed
- deliverable:
  - `references/api-index-12.0.0-preview2-generated.md`

4. Author a curated migration chapter.
- status: completed
- deliverable:
  - `references/68-avalonia-12-preview2-migration-guide.md`

5. Wire the preview lane into the repository entry points.
- status: completed
- files:
  - `SKILL.md`
  - `README.md`
  - `references/compendium.md`

6. Re-run repository validation.
- status: completed
- commands:
  - `python3 -m unittest scripts.test_generate_api_migration_report scripts.test_find_uncovered_apis`
  - `python3 scripts/find_uncovered_apis.py --output plan/api-coverage-not-covered.md`
  - `python3 scripts/generate_api_migration_report.py --repo /Users/wieslawsoltes/GitHub/Avalonia --from-ref 11.3.12 --to-ref 12.0.0-preview2 --output /Users/wieslawsoltes/GitHub/avalonia-app-development/references/69-avalonia-12-preview2-breaking-changes-and-new-api-catalog.md`

## Deliverable Set

- preview migration chapter
- official break/new API catalog
- preview API index
- plan and analysis docs
- generator and tests
- navigation updates in top-level skill docs
