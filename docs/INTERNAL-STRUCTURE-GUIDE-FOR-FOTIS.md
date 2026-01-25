# Internal Guide: Alerts & Notifications Structure (DO NOT PUBLISH)

**For:** Fotis
**Purpose:** Understand the restructured alerts documentation layout

---

## Why This Restructure?

Docs previously lived under nested `/Alerts & Notifications/The Book/` path which didn't surface well on learn.netdata.cloud. Flattened to `/Alerts & Notifications/` for better discoverability.

---

## Structure Overview

```
docs/alerts/
├── understanding-alerts/           # Chapter 1 - Fundamentals
│   ├── index.md                   # Landing page
│   ├── what-is-a-netdata-alert.md
│   ├── alert-types-alarm-vs-template.md
│   └── where-alerts-live.md
├── creating-alerts-pages/          # Chapter 2 - Getting Started
│   ├── index.md
│   ├── quick-start-create-your-first-alert.md
│   ├── creating-and-editing-alerts-via-config-files.md
│   ├── creating-and-editing-alerts-via-cloud.md
│   ├── managing-stock-vs-custom-alerts.md
│   └── reloading-and-validating-alert-configuration.md
├── alert-configuration-syntax/    # Chapter 3 - Deep Dive
│   ├── index.md
│   ├── alert-configuration-syntax.md
│   ├── alert-definition-lines.md
│   ├── lookup-and-time-windows.md
│   ├── calculations-and-transformations.md
│   ├── expressions-operators-functions.md
│   ├── variables-and-special-symbols.md
│   └── optional-metadata.md
├── controlling-alerts-noise/      # Chapter 4
│   └── index.md
├── receiving-notifications/       # Chapter 5
│   └── index.md
├── alert-examples/                # Chapter 6
│   ├── index.md
│   ├── core-system-alerts.md
│   ├── service-availability.md
│   ├── trend-capacity.md
│   ├── anomaly-alerts.md
│   └── application-alerts.md
├── troubleshooting-alerts/        # Chapter 7
│   ├── index.md
│   ├── alert-never-triggers.md
│   ├── always-critical.md
│   ├── flapping.md
│   ├── variables-not-found.md
│   └── notifications-not-sent.md
├── advanced-techniques/           # Chapter 8
│   ├── index.md
│   ├── hysteresis.md
│   ├── multi-dimensional.md
│   ├── label-targeting.md
│   ├── custom-actions.md
│   └── performance.md
├── apis-alerts-events/            # Chapter 9
│   └── index.md
├── cloud-alert-features/          # Chapter 10
│   └── index.md
├── built-in-alerts/              # Chapter 11
│   ├── application-alerts.md     # 11.1
│   ├── container-alerts.md      # 11.2
│   ├── hardware-alerts.md        # 11.X
│   ├── network-alerts.md        # 11.X
│   └── system-resource-alerts.md # 11.X
├── best-practices/               # Chapter 12
│   ├── designing-useful-alerts.md      # 12.1
│   ├── sli-slo-alerts.md                 # 12.2
│   ├── notification-strategy.md         # 12.3
│   ├── maintaining-configurations.md   # 12.4
│   └── scaling-large-environments.md    # 12.5
└── architecture/                 # Chapter 13
    ├── alert-lifecycle.md             # 13.1
    ├── evaluation-architecture.md    # 13.2
    ├── configuration-layers.md       # 13.3
    ├── notification-dispatch.md      # 13.4
    └── scaling-topologies.md        # 13.5
```

---

## File Naming Conventions

| Category | Pattern | Example |
|-----------|---------|---------|
| Landing page | `index.md` | `controlling-alerts-noise/index.md` |
| Concept/topic | `kebab-case.md` | `alert-types-alarm-vs-template.md` |
| Chapter intro | `index.md` with `# X. Chapter Name` | All chapter folders |

---

## Header Format

Each topic file should start with:

```markdown
# X.Y Topic Title

Content...

## Related
- Link to parent index.md
- Links to related sections
```

---

## map.csv Entry Format

```
https://github.com/netdata/netdata/edit/master/docs/alerts/{folder}/{filename}.md,Sidebar Label,Published,Alerts & Notifications/{Folder Name},
```

**Critical:** Never use `Alerts & Notifications/The Book/...` - that nesting is gone.

---

## Landing Page Template (index.md)

```markdown
# X. Chapter Title

One-paragraph description of what this chapter covers.

## What You'll Find in This Chapter

| Section | Topic |
|---------|-------|
| **X.Y** | Description |

## How to Navigate

- Start at **X.Y** if [condition]
- Jump to **X.Z** if [condition]

## What's Next

- **[Next Chapter]** Brief description
```

---

## Cross-Reference Pattern

Link to other chapters like this:

```markdown
- **Chapter Y: Chapter Name** for topic
- **[Section Y.Z](/docs/alerts/folder/specific-page.md)** for specifics
```

Never use HTML anchors like `#81` - use proper markdown links.

---

## Chapters That Need Attention

1. **built-in-alerts/** - Has `application-alerts.md` with `# 11.3` header but no index.md landing page
2. **best-practices/** - Individual `.md` files exist but no `index.md` landing page
3. **architecture/** - Same pattern - subfiles exist, no landing page

**Action needed:** Create `index.md` landing pages for ch11, ch12, ch13 that follow the template above.

---

## Key Changes From Old Structure

| Old | New |
|-----|-----|
| `Alerts & Notifications/The Book/Understanding Alerts/` | `Alerts & Notifications/Understanding Alerts/` |
| Scattered `.md` files at `docs/alerts/*.md` | Consolidated into chapter directories |
| No consistent naming | All lowercase, kebab-case |
| Manual sidebar mapping | Automated via `docs/.map/map.csv` |

---

## Testing the Structure

After making changes:
1. Run docs builder locally to catch broken links
2. Check `git diff docs/.map/map.csv` to verify only intended changes
3. Visit preview site to verify navigation works

---

## Questions?

Ask in the docs channel or check `src/health/*.c` files for source of truth on terminology.