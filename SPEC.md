# CodeStudyPlan — Specification

## Why

Learning a large, unfamiliar codebase is hard. Developers regularly face one or more of the following challenges:

- **No entry point** — a project may have hundreds of files but no guided walk-through that explains *where to start*.
- **Lack of structure** — reading code randomly leads to poor retention and wasted time.
- **No existing alternative that fits** — while a number of tools exist in the ecosystem, none of them solve the full problem:
  | Existing tool / project | What it does | What it lacks |
  |---|---|---|
  | GitHub's built-in file browser | Browse and search code online | No learning path, no progress tracking |
  | `ctags` / `universal-ctags` | Symbol indexing for editors | Navigation aid only, no study plan concept |
  | `Sourcegraph` | Code search and intelligence | Enterprise-focused, no personal study workflow |
  | `Obsidian` / `Notion` | General note-taking | No native code-awareness or repo integration |
  | `Roadmap.sh` | Curated technology roadmaps | Generic, not tailored to a specific codebase |

  **CodeStudyPlan** fills this gap by providing a lightweight, opinionated framework for building and executing a *personal* study plan that is tied to a specific repository or open-source project.

---

## What

### Purpose

CodeStudyPlan is a developer-focused, open-source framework that helps you:

1. **Plan** — define the areas of a codebase you want to understand and the order in which to explore them.
2. **Execute** — work through the plan incrementally, taking notes and recording insights as you go.
3. **Review** — revisit completed sections and reinforce understanding over time.

### Target audience

| Audience | Example use case |
|---|---|
| Junior engineers onboarding to a new team | Understand the company's monorepo in the first 30 days |
| Open-source contributors | Learn a project well enough to submit a meaningful PR |
| Self-learners / students | Study a reference implementation (e.g. a compiler, database, OS kernel) |
| Technical writers | Produce accurate documentation for an unfamiliar project |

### Technologies, libraries, and architecture

The project intentionally keeps its own technology footprint minimal so it can be adopted by the widest possible audience:

- **Markdown** — all study plans and notes are plain Markdown files; no proprietary format lock-in.
- **Git / GitHub** — plans live in a repository alongside (or linked to) the code being studied; progress is naturally version-controlled.
- **YAML / JSON** (optional) — structured front-matter or metadata files can capture plan configuration (milestones, effort estimates, tags).
- **CLI tooling** (planned) — a small command-line interface to scaffold new plans, mark items complete, and generate progress reports.
- **AI assistance** (planned) — optional integration with LLM-backed tools (e.g. GitHub Copilot, local models via Ollama) to generate first-draft study plans from a repository's README, directory tree, or dependency graph.

---

## How

### Guiding principles

1. **Plain text first** — every artifact produced by CodeStudyPlan should be readable without any special tooling.
2. **Composable** — the framework is a set of conventions and lightweight scripts, not a monolithic application. Users can adopt as much or as little as they need.
3. **Build on the shoulders of giants** — rather than reinventing the wheel, CodeStudyPlan integrates with best-in-class open-source tools:

### Key open-source foundations

| Tool / resource | Role in CodeStudyPlan |
|---|---|
| **Git** | Version-control for plans and notes |
| **GitHub / GitLab / Gitea** | Hosting, issues for tracking study tasks, pull-requests for collaborative learning |
| **`tree` / `fd`** | Quickly generate a directory outline of the target repo to seed a plan |
| **`ripgrep` (`rg`)** | Fast code search while executing a study session |
| **`bat`** | Syntax-highlighted file viewing during study sessions |
| **`glow`** | Render Markdown plans in the terminal |
| **`tokei`** | Count lines of code per language to estimate study effort |
| **GitHub Copilot / Ollama + `llama.cpp`** | AI-generated summaries of modules and files (optional, privacy-respecting local option available) |
| **Obsidian** (optional) | Rich note-taking on top of the plain-text Markdown files |

### Workflow

```
1. Clone the target repository.
2. Run `csp init <repo-path>` (or copy the template) to scaffold a study plan.
3. Inspect the generated plan: review auto-detected modules and adjust priorities.
4. Work through each plan item: read code, run it, write notes in the corresponding Markdown file.
5. Mark items done and commit progress.
6. Use `csp report` to see a progress summary.
```

### Repository structure (planned)

```
CodeStudyPlan/
├── SPEC.md              # This file — project specification
├── README.md            # Quick-start guide
├── templates/           # Starter plan templates for common project types
│   ├── default.md
│   ├── library.md
│   └── monorepo.md
├── cli/                 # CLI source code
└── examples/            # Example study plans for well-known open-source projects
```

---

## Contributing

Contributions are welcome! Please open an issue to discuss your idea before submitting a pull request. This project follows the [Contributor Covenant](https://www.contributor-covenant.org/) code of conduct.

## License

MIT — see [LICENSE](LICENSE).
