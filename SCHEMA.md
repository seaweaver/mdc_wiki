# Wiki Schema

## Domain

This wiki is the shared markdown knowledge base for the data development team.
It is used to accumulate durable knowledge for projects, data sources, vendor behavior,
field definitions, engineering decisions, troubleshooting notes, and research findings.

The goal is not just note-taking.
The goal is a compounding, auditable knowledge system that any coding agent or teammate
can continue from without rediscovering everything from scratch.

## Conventions

- Wiki root: the current repository root is the wiki root
- File names: lowercase, hyphens, no spaces
- Every wiki page starts with YAML frontmatter
- Use `[[wikilinks]]` between related pages whenever possible
- Keep pages scannable; split large pages instead of letting them grow without structure
- When updating a page, always bump the `updated` date
- Every new page must be added to `index.md`
- Every meaningful operation must be appended to `log.md`
- Raw sources are immutable after capture; corrections belong in wiki pages, not in `raw/`
- Contradictions, unknowns, and `null` findings are valid knowledge states and must not be hidden

## Repository Layout

- `SCHEMA.md`: domain rules, taxonomy, and update policy
- `index.md`: top-level navigation and page catalog
- `log.md`: append-only activity log
- `raw/`: immutable source material
- `entities/`: people, organizations, systems, vendors, datasets, platforms
- `concepts/`: metrics, business concepts, architectures, methods, workflows
- `comparisons/`: side-by-side analysis and trade-off documents
- `queries/`: high-value answers and synthesized findings worth preserving
- `_archive/`: superseded content retained for traceability

## Frontmatter

```yaml
---
title: Page Title
created: YYYY-MM-DD
updated: YYYY-MM-DD
type: entity | concept | comparison | query | summary
tags: [from taxonomy below]
sources: [raw/articles/source-name.md]
status: draft | active | archived
---
```

## Tag Taxonomy

All tags used in wiki pages must appear in this taxonomy first.

- Team and scope: team, project, domain, internal, external
- Data work: datasource, lineage, metric, schema, field, quality, validation, cache
- Engineering: architecture, pipeline, workflow, tooling, automation, integration, testing
- Operations: incident, troubleshooting, deployment, runbook, monitoring
- Research: vendor, methodology, benchmark, assumption, contradiction, unknown
- Business context: fund, stock, strategy, report, compliance, metadata

## Page Thresholds

- Create a new page when a concept or entity is central to one source or recurs across work
- Update an existing page when new information extends something already covered
- Do not create pages for passing mentions or transient fragments with no reuse value
- Split a page when it is no longer easy to scan in under a minute
- Archive a page when it is superseded but still historically relevant

## Entity Pages

Entity pages are for notable things such as:
- vendors
- systems
- datasets
- business entities
- external tools
- internal services

Typical sections:
- Overview
- Key facts
- Relationships
- Usage in our environment
- Known caveats
- Sources

## Concept Pages

Concept pages are for durable knowledge such as:
- metric definitions
- data modeling conventions
- ingestion patterns
- validation rules
- workflow patterns
- architectural decisions

Typical sections:
- Definition
- Why it matters
- Current team understanding
- Rules or constraints
- Related pages
- Sources

## Comparison Pages

Comparison pages should explain:
- what is being compared
- why the comparison matters
- dimensions of comparison
- recommendation or synthesis
- sources and caveats

Table format is preferred when helpful.

## Queries Pages

Only file a query result into `queries/` when:
- the answer required non-trivial synthesis
- the result is likely to be reused
- re-deriving it later would be costly

Do not file trivial lookups.

## Update Policy

When new information conflicts with existing content:

1. Check the date and source quality first
2. Preserve both claims if the conflict is real
3. Mark the contradiction explicitly in the page body
4. Add or keep the `contradiction` tag when appropriate
5. Surface unresolved contradictions during lint or review

## Team Recommendations

- Prefer incremental maintenance over periodic rewrites
- Prefer markdown and csv-first workflows for portability and batch checks
- Keep raw evidence separate from synthesized conclusions
- Use commit history plus `log.md` for traceability
- Default to project-root wiki layout unless there is a strong reason to isolate it
- When a database lacks a structured field but a vendor API can answer by code and report date,
  prefer local cache plus incremental collection and treat `null` as a valid terminal state
