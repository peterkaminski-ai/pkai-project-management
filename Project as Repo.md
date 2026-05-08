# Project as Repo

The container for a project is a folder. That folder is, simultaneously:

- An **Obsidian vault** (because it has `.obsidian/` inside).
- A **Git repo** (because it has `.git/` and a `.gitignore` inside).
- A **Claude Code project** (because it has `CLAUDE.md` at the root, and Claude Code is invoked from this directory).

These aren't three different things laid on top of each other. They're three roles of the same folder.

## The collapse

When you're new to this stack, vault and repo and project sound like distinct concepts. They aren't. The same folder, with a few dotfiles inside, plays all the roles:

| Tool | What it adds |
|---|---|
| Obsidian | `.obsidian/` |
| Git | `.git/`, `.gitignore` |
| Claude Code | `CLAUDE.md`, sometimes `.claude/` |
| MarkPub | a MarkPub config folder |

You don't pick one and commit to it. You let the folder be all of them.

## Why one folder per project

Two reasons:

1. **Boundary for Claude Code.** Claude Code reasons within the folder it was launched in. If the folder *is* the project, Claude Code's attention is the project. If the folder is a catch-all and the project is a sub-folder of a sub-folder, you're spending tokens and risk on irrelevant context.

2. **Boundary for memory.** `CLAUDE.md`, `MEMORY.md`, and any project-specific memory files all live in the project folder. They describe *this* project. When you switch projects, you switch contexts entirely.

## When *not* to make a new repo

Plenty of work doesn't need its own repo. The lighter-weight alternative: a sub-folder under `Projects/` inside an existing vault.

A common shape:

```
Atlas/                    # your main vault
├── .obsidian/
├── .git/
├── CLAUDE.md
├── Projects/
│   ├── Research Agents/
│   │   ├── wish.md
│   │   └── plan.md
│   ├── Get Signed Up to Discord/
│   │   └── notes.md
│   └── Cat House/
│       └── ...
└── ...
```

For lots of personal work, this is the right grain. The whole vault gets one repo, one Obsidian config, one set of memories. Each project is just a folder.

## When *to* make a new repo

Spin out a new repo when:

- The project will be **shared with collaborators** who shouldn't see the rest of your vault.
- The project will be **made public** at some point — open source, MarkPub-published, or otherwise.
- The project has **its own substantial conventions** (different language, framework, build, etc.) that deserve a dedicated `CLAUDE.md`.
- The project has **substantial size or activity** that would clutter the parent vault's git history.

See [Starting a New Project](Starting%20a%20New%20Project.md) for the decision walk-through.

## What lives at the root

When you've decided a project deserves its own folder (sub-folder or full repo), the root should have:

- **`README.md`** — what this project is, in human terms.
- **`CLAUDE.md`** — what this project is, in agent-facing terms. Conventions, vocabulary, do's and don'ts.
- **The wish** (or whatever you're calling it) — a short note that started the project. Often this becomes part of the README later.
- **The plan** — what you and Claude Code agreed to do, refined over a few iterations.
- **Project-specific memory** if relevant.
- **Session logs**, accumulating over time.

## The `~/Documents/GitHub/` convention

Wherever you keep these folders, **don't put them inside iCloud, OneDrive, Dropbox, or any cloud-synced directory.** Git and cloud sync collide and produce conflicts and corruption.

A common location on a Mac is `~/Documents/GitHub/` (so each project sits at `~/Documents/GitHub/some-project/`). That path is conventional, easy to remember, and not synced anywhere weird.

## See also

- [Starting a New Project](Starting%20a%20New%20Project.md) — the decision tree for new repo vs. sub-folder.
- [The Iteration Loop](The%20Iteration%20Loop.md) — what to do once you have your project folder.
- [Memory Across Sessions](Memory%20Across%20Sessions.md) — what `CLAUDE.md` and `MEMORY.md` are for.
