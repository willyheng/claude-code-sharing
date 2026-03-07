---
marp: true
theme: custom
paginate: true
header: ''
footer: 'Claude Code for Non-Coders'
---

<!-- _class: title -->
<!-- _paginate: false -->
<!-- _footer: '' -->

# Claude Code Without Coding

## A Practical Guide to Building with Claude Code

Willy Heng | March 2026

---

# What You'll Leave With

- **Tools** — A toolkit for fast, stable, usable app building
- **Workflow** — A repeatable process for building with Claude Code
- **Confidence** — Know what to check, when to intervene, and how to stay in control

> Goal: Upskill on "non-code coding" to build usable tools and apps quickly using Claude Code.

---

<!-- _class: divider -->

# 1. What is Claude Code?

## The CLI tool and its capabilities

---

# Claude Code — What It Is

An **AI coding assistant** you run from your terminal (CLI).

### What it can do:
- **Read & write files** in your project
- **Run commands** (tests, scripts, builds) and show outputs
- **Navigate code** — "Where is X implemented?"
- **Generate new code** from your description
- **Access your local context** — folders, files, command execution

> All within the permissions and scope you give it.

---

# Claude Code — How It Looks

```
$ claude

> Build me a simple web app that tracks my reading list

● I'll create a reading list web app for you. Let me start
  by setting up the project structure...

● Creating files:
  - index.html
  - style.css
  - app.js

● Done! Run `open index.html` to see your app.
```

It's a **conversation in the terminal** — you ask, Claude builds.

---

<!-- _class: divider -->

# 2. Development Value Chain

## Where Claude fits — and where you do

---

<!-- _class: highlight -->

# The Development Value Chain

```
  User Need  →  Spec  →  Build  →  Test  →  Deploy  →  Iterate
     👤          📋        🔨        ✅       🚀         🔄
  (Domain)    (PM/       (Dev)     (QA)    (Ops)
              Analyst)
```

### Claude Code primarily accelerates **Build**
…and supports **Test** by generating checks.

**It does not replace the human roles.**

---

# Your Roles Remain Essential

| Role | Responsibility |
|------|---------------|
| **User / Domain expert** | Define the need + validate outputs |
| **PM / Analyst** | Write the spec + success criteria |
| **QA / Reviewer** | Sanity-check + confirm correctness |
| **Ops / Owner** | Runbook + keep it usable over time |

> Claude is the **builder**, but you are the **architect, reviewer, and owner**.

---

<!-- _class: divider -->

# 3. Interaction & Outputs

## The Claude Code loop

---

# The Interaction Loop

```
   You ask for a change
         ↓
   Claude proposes edits + commands
         ↓
   You run locally
         ↓
   Claude helps interpret results
         ↓
   Repeat
```

It's a **conversation**, not a one-shot prompt.

---

# What Claude Produces

For any non-trivial request, expect:

1. **A short plan** — what it intends to do
2. **File changes** — edits and new files with explanations
3. **A diff summary** — what changed and why
4. **Commands to run** — install, run, test
5. **Outputs** — logs, tables, charts + how to interpret them

---

# What You Should Always Check

- Did it change the **files you expected**?
- Did it **run successfully**?
- Do outputs pass basic **sanity checks**?
  - Totals, date ranges, units, missing values

### If something looks wrong:

> Ask: *"Summarise current state, what you changed, and the next smallest fix."*

Revert / discard changes back to last working state if needed.

---

<!-- _class: divider -->

# 4. Terminal Survival Kit

## Key bash commands and port conflicts

---

# Must-Know Terminal Commands

| Command | What it does |
|---------|-------------|
| `pwd` | Print working directory (where am I?) |
| `ls` | List files in current folder |
| `cd folder_name` | Change directory (go into a folder) |
| `cd ..` | Go up one level |
| `cat file.txt` | Display file contents |
| `mkdir new_folder` | Create a new folder |
| `python script.py` | Run a Python script |

---

# Port Conflicts

If you see: **"Address already in use"**

This means another process is using that port.

### Fix it:
- **Stop the prior run** (Ctrl+C in the other terminal)
- **Or change the port**: `python app.py --port 8081`

> Common ports: `3000` (Node), `5000`/`8000` (Python), `8080` (general)

---

<!-- _class: divider -->

# 5. Repo Basics

## Git, GitHub, and version control

---

# Git — An Analogy

Think of Git as a **manual Google Drive for code**.

You choose **when** to save a snapshot and **when** to share it.

### The three key commands:

| Command | What it does |
|---------|-------------|
| `git status` | What changed since the last snapshot? |
| `git add .` | Select what goes into the snapshot |
| `git commit -m "…"` | Save a named snapshot (checkpoint) |

---

# Local vs Server

### Local
Code + app runs on **your laptop** (`localhost`).

### Server / Remote repo
Shared place where code is hosted — so others can access it.

**GitHub** = the most common remote host for code.

| Command | What it does |
|---------|-------------|
| `git push` | Upload your commits to the server |
| `git pull` | Download latest changes from the server |

---

# Practical Git Tips

- Use a **private repo** by default for work-related code
- **Never commit sensitive data** (API keys, passwords)
- Use `.gitignore` to prevent committing:

```
.env                # Environment variables / secrets
*.db                # Local databases
node_modules/       # Installed packages
dist/               # Build outputs
.DS_Store           # macOS junk
```

---

<!-- _class: divider -->

# 6. Hosting Basics

## Local vs server hosting

---

# Local vs Server Hosting

### Local hosting
- Run on your laptop (e.g., `localhost:3000`)
- Fast testing, no setup needed
- Only you can see it

### Server hosting
- Run on an external service
- Others can access it (links, auth, network controls)
- Needed for sharing with users

---

# Free-ish Starter Options

Great for prototypes and personal tools:

| Service | Best for |
|---------|---------|
| **Vercel** | Web apps (React, Next.js) |
| **Netlify** | Static sites + simple web apps |
| **Cloudflare Pages** | Static sites + edge functions |
| **Render / Railway** | Simple app hosting (backend) |

> These are free-tier friendly. Good for learning and prototypes.

---

<!-- _class: divider -->

# 7. Database Basics

## Storing data — local vs server

---

# Local Database

Simplest persistence — runs on your laptop.

| Type | What it is |
|------|-----------|
| **SQLite** | Single file database — no setup needed |
| **Local Postgres** | Full database as a service on your machine |

Great for quick prototyping and solo use.

---

# Server Database

Shared persistence for multi-user / server-hosted apps.

| Type | What it is |
|------|-----------|
| **Supabase** | Hosted Postgres + auth (generous free tier) |
| **Managed Postgres/MySQL** | Cloud-hosted by AWS, GCP, etc. |

### Practical framing

- **Files / CSVs** are fine for quick work
- **Databases** help when you need history, querying, and shared access

---

<!-- _class: divider -->

# 8. Testing Basics

## Why test and how

---

# Why Test?

Confirm that changes **didn't break expected behaviour**.

### Common test types:

| Type | What it tests |
|------|--------------|
| **Unit** | A small function/module in isolation |
| **Integration** | Multiple components working together (e.g., app ↔ database) |
| **End-to-end (E2E)** | The whole workflow like a user would (UI/CLI → output) |

---

# Practical Testing Habits

1. **Build tests for new features** — including edge cases
2. **When fixing a bug** — add a test that reproduces it first
3. **Run tests before committing** — catch problems early

> You don't need to write tests by hand — Claude Code can generate them for you.

```
> Write unit tests for the add_book function including edge cases
```

---

<!-- _class: divider -->

# 9. CLAUDE.md

## Guiding Claude's behaviour

---

# What is CLAUDE.md?

An **instruction file** that guides how Claude behaves in your project.

### Two levels:

| Level | Scope | Example |
|-------|-------|---------|
| **Global** | Your personal defaults across all projects | "Always work step-by-step, show diffs" |
| **Local** (repo) | Project-specific rules | "Run with `npm start`, test with `npm test`" |

---

# CLAUDE.md — Practical Tips

Keep the **local CLAUDE.md** short and operational:

```markdown
# My App

## How to run
npm install && npm start

## How to test
npm test

## Key files
- src/index.ts — entry point
- src/db.ts — database connection
```

> Treat it like the repo's **mini runbook**.

---

<!-- _class: divider -->

# 10. MCP & Tool Integrations

## Extending Claude Code

---

# MCP — Model Context Protocol

**MCP** = controlled integrations beyond local files.

- Connect Claude to external data sources and APIs
- Enables richer context and actions
- A pathway for future scaling

### Other useful CLI tools

- **GitHub CLI** (`gh`) — manage repos, PRs, issues from terminal
- **Node.js** — run JavaScript projects
- **Python** — data scripts, backends, automation

> These are optional but powerful add-ons to your workflow.

---

<!-- _class: divider -->

# Wrap-up

## Summary and Q&A

---

# Key Takeaways

1. **Claude Code** is a terminal-based AI coding assistant
2. It accelerates **building**, but humans own the **spec, review, and ops**
3. The interaction is a **loop** — ask, review, run, repeat
4. Learn the basics: **terminal, git, hosting, databases, testing**
5. Use **CLAUDE.md** to guide Claude's behaviour per project
6. **Start small** — build a prototype, iterate from there

---

<!-- _class: title -->
<!-- _paginate: false -->
<!-- _footer: '' -->

# Questions?

## Let's build something together

Thank you!
