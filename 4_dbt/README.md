# 4 · dbt 

<div align="center">

![dbt](https://img.shields.io/badge/dbt-Core-FF694B?style=for-the-badge&logo=dbt&logoColor=white)
![Databricks](https://img.shields.io/badge/Databricks-Free_Edition-FF3621?style=flat-square)
![Python](https://img.shields.io/badge/Python-3.12-green?style=flat-square)
![Status](https://img.shields.io/badge/Status-Planned-lightgrey?style=flat-square)

**dbt in 3 focused hours, or 5 if I want the extras.**

[← Back to Data Engineering Master Class](../README.md)

</div>

---

## 📖 About This Module

This is **Module 4** of my [Data Engineering Master Class](../README.md). It covers **dbt** (data build tool), the transformation layer of the modern data stack. Snowflake is also planned for this module and will get its own folder later.

**This is still a learning journal, not a polished course.** All credit for the original material goes to the two creators. The depth lives in the **Stretch Goals** at the bottom, for later.

---

## ⏱️ Ground Rules

Time estimates are mine, not measured. They assume I:

- watch at **1.5–2x** and use the timestamps to skip banter
- **type along** instead of copy-pasting
- use **two tables only**, which is enough to learn every concept

---

## 🗺️ Track 1 · The 3-Hour Core

| # | Block | Time | What to do | Source |
|:--|:---|:---|:---|:---|
| 1 | Setup & first model | 35 min | Install dbt Core and the adapter, `dbt init`, fill in `profiles.yml`, run `dbt debug` | Ansh 0:31–1:32 |
| 2 | Sources, `ref`, materializations | 25 min | Bronze for **two** tables. Add `sources.yml`, use `source()` and `ref()`, switch view → table | Ansh 1:34–2:10 |
| 3 | Tests | 25 min | `unique` and `not_null`, one `accepted_values`, one singular test. **Break one on purpose** to see a failure | Ansh 2:24–2:57 |
| 4 | Jinja & macros | 25 min | A variable, a loop, `loop.last` for commas, one macro called from a model | Ansh 3:17–3:56 |
| 5 | Snapshots (SCD2) | 25 min | Dedup model, then a YAML snapshot. Change a source row, rerun, check `dbt_valid_from` / `dbt_valid_to` | Ansh 4:16–4:41 |
| 6 | `dbt build` & dev/prod | 15 min | Run with `--target prod`, see tests run inside `dbt build` | Ansh 4:41–4:58 |
| 7 | Incremental models | 20 min | Convert one model to incremental, insert a new row, rerun, then try `--full-refresh` | Jay 2:51–3:15 |
| 8 | Wrap-up | 10 min | Fill the notes template, write the one-page cheat sheet | — |

**Total: ~3 hours.**

**Skipped in this track:** seeds (read the docs page, 2 min), custom schema macro, custom generic tests, silver layer, docs site, packages, source freshness, slim CI, GitHub Actions.

---

## 🗺️ Track 2 · +2 Hours for the 5-Hour Version

Only after Track 1 is done.

| # | Block | Time | Source |
|:--|:---|:---|:---|
| 9 | Silver layer with CTEs and a macro | 25 min | Ansh 3:56–4:16 |
| 10 | Seeds, config precedence, custom schema macro | 20 min | Ansh 3:04–3:15, 1:58–2:17 |
| 11 | Custom generic test | 10 min | Ansh 2:57–3:04 |
| 12 | Docs & lineage | 20 min | Jay 5:25–5:50 |
| 13 | Packages & `dbt_utils` | 15 min | Jay 6:26–6:45 |
| 14 | Slim CI with `state:modified+` | 25 min | Jay 4:57–5:25 |
| 15 | Source freshness | 10 min | Jay ~3:52–3:57, demo ~4:13–4:15 |

**Total: ~2 hours 5 minutes.**

---

## 🚦 Staying on Schedule

1. **Timebox every block.** If one runs over by 10 minutes, move on and leave a `TODO` in the notes.
2. **Don't debug setup for long.** The likely time sinks are an expired token, forgetting to `cd` into the project, and YAML indentation.
3. **If I'm running late, cut in this order:** block 6, then the loop example in block 4, then the custom tests.

---

## 🗂️ Module Structure

```
4_Modern_Data_Stack/
├── README.md          → you are here
├── dbt/               → the dbt project (dbt_project.yml lives here)
│   ├── models/
│   │   ├── sources/   → sources.yml
│   │   ├── bronze/
│   │   └── silver/    → Track 2 only
│   ├── macros/
│   ├── snapshots/
│   ├── tests/         → singular tests
│   └── analysis/      → scratch queries, not part of the build
├── notes.md           → one section per block, using the template below
└── cheatsheet.md      → commands and selectors on one page
```

Track 2 adds `seeds/` and `packages.yml` inside `dbt/`.

---

## 🧰 Setup

**Stack:** dbt Core · `dbt-databricks` adapter · Databricks Free Edition (the warehouse) · uv · VS Code · Git

```bash
# from inside 4_Modern_Data_Stack/
uv add dbt-core dbt-databricks   # into its own environment, see warning below
cd dbt
dbt debug                        # checks profiles.yml, project file and connection
dbt build                        # runs models, tests and snapshots
dbt build --target prod          # same, against the prod target
```

> ⚠️ **Python version:** in Ansh's video, the dbt version he used did not support Python 3.13, so he installed 3.12. The root `pyproject.toml` says 3.9+. Check the current dbt Core support matrix and keep this module in its own environment so it doesn't fight the rest of the repo.

> ⚠️ **Nested git repo:** Ansh runs `uv init`, which can also initialize a git repo. Inside an existing repo, check that no `.git` folder appeared in this module. If one did, delete it.

### Dataset (two tables only)

I use just two of the retail CSVs from Ansh Lamba's GitHub repo, linked in his video description: **fact sales** and **dim store**. I upload them as tables in a `source` schema in a Databricks catalog. For the snapshot block I also create a small `items` table by hand, as he does in the video.

### Secrets

**Never commit tokens.** `profiles.yml` holds connection details, so keep it out of git and read credentials with `{{ env_var('...') }}`. Ansh's access token expired mid-video; expect the same.

---

## 📝 Note Template

Every block in `notes.md` gets the same five fields:

```markdown
## Block N: <name>
### What
### Why
### Command
### Gotcha
### Interview question
```

---

## ⚠️ Gotchas I Expect to Hit

Collected from watching both videos:

| Gotcha | Fix |
|:---|:---|
| `dbt` command fails with "no dbt_project.yml found" | `cd` into the dbt project folder first |
| YAML errors | Indentation, and a space after every hyphen |
| A macro in `models/` gets treated as a model | dbt is strict about folder placement |
| Connection suddenly fails | Expired token, create a new one |
| Incremental model keeps the old columns after a change | Run once with `--full-refresh` |
| Two versions of the same key break a snapshot | Dedup in a model first, snapshot the model |

---

## 🎯 Definition of Done

**Track 1 (3 hours)**

- [ ] Project connects: `dbt debug` passes
- [ ] Two bronze models built from `sources.yml`
- [ ] Tests run, and I saw one fail on purpose
- [ ] One macro called from a model
- [ ] A snapshot shows an SCD2 history
- [ ] `dbt build` passes on dev and prod targets
- [ ] An incremental model processes only new rows
- [ ] `notes.md` and `cheatsheet.md` filled in

**Track 2 (+2 hours)**

- [ ] Silver model with CTEs and a macro
- [ ] Docs site generated, lineage screenshot saved
- [ ] `dbt_utils` installed and one macro used
- [ ] Modified-only run works with `state:modified+`
- [ ] Source freshness runs

## 🙏 Credits

- **Ansh Lamba**: *[Data Build Tool] DBT - The Ultimate Guide | With CI/CD*
- **Data with Jay**: *DBT for Data Engineers Full Course 2026 | Basics to Advanced*

These are my own notes and re-implementations. Watch the originals for the full walkthroughs.

---

*I'll tick the boxes as I go.*