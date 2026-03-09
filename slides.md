---
marp: true
theme: custom
paginate: true
header: ''
footer: 'Claude Code Without Coding'
---

<!-- _class: title -->
<!-- _paginate: false -->
<!-- _footer: '' -->

# Claude Code Without Coding

## A Practical Guide to Building Applications

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

An **AI coding assistant** you run from your terminal or Claude app.

### What it can do:
- **Access your local context** — read & write files, manage your project
- **Run commands** (tests, scripts, builds) and show outputs
- **Navigate and explain code** — "Where/How is X implemented?"
- **Generate code** from description of what you want
- **Brainstorm approaches** and **research solutions** from the internet

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

> **Demo:** (i) Claude CLI, (ii) Claude App, (iii) VS Code extension

---

# Claude Models — Which to Use

| Model | Strengths | Best for |
|-------|-----------|----------|
| **Opus** | Most capable, deepest reasoning | Complex tasks, multi-file changes, architecture decisions |
| **Sonnet** | Balanced speed and capability | Most everyday work, production tasks |
| **Haiku** | Fastest, most lightweight | Quick questions, simple edits, well-defined tasks |

> **Tip:** For non-coders, Opus is the best choice as it is the most thoughtful about implementation — but it uses limits fastest.

---

<!-- _class: divider -->

# 2. Development Value Chain

## Where Claude fits — and where you do

---

# Shifting Development Value Chain

<table>
<tr><th>Stage</th><th>Human's Role</th><th>Machine's Role</th></tr>
<tr><td><strong>Problem (User)</strong></td><td style="background:#6ee7b7">Define the problem, own the domain</td><td>—</td></tr>
<tr><td><strong>Spec (Product Mgr)</strong></td><td style="background:#6ee7b7">Write requirements, set success criteria</td><td>Brainstorm, clarify, draft specs</td></tr>
<tr><td><strong>Build (Dev)</strong></td><td>Review, guide, approve changes</td><td style="background:#6ee7b7">Write code, create files, run commands</td></tr>
<tr><td><strong>Test (QA)</strong></td><td style="background:#d1fae5">Sanity-check, validate outputs</td><td style="background:#d1fae5">Generate and run tests</td></tr>
<tr><td><strong>Deploy (Ops)</strong></td><td style="background:#d1fae5">Own infrastructure, access controls</td><td style="background:#d1fae5">Generate configs, CI/CD scripts</td></tr>
</table>

> Claude is the **builder**, but you are the **architect, reviewer, and owner**.

---

<!-- _class: divider -->

# 3. Working with Claude Code

## Input, Output, Checks

---

# The Interaction Loop

<svg viewBox="-35 0 735 400" xmlns="http://www.w3.org/2000/svg" style="width:58%;margin:0 auto;display:block;">
  <defs>
    <marker id="ah" markerWidth="8" markerHeight="6" refX="8" refY="3" orient="auto"><path d="M0,0 L8,3 L0,6" fill="#d4a574"/></marker>
  </defs>
  <!-- You prompt → Claude plans (top right) -->
  <path d="M440,50 Q600,50 600,120" fill="none" stroke="#d4a574" stroke-width="2.5" marker-end="url(#ah)"/>
  <!-- Claude plans → You approve plan (right side down) -->
  <path d="M600,180 Q600,230 600,240" fill="none" stroke="#d4a574" stroke-width="2.5" marker-end="url(#ah)"/>
  <!-- You approve plan → Claude builds (bottom right corner) -->
  <path d="M600,300 Q600,347 530,347" fill="none" stroke="#d4a574" stroke-width="2.5" marker-end="url(#ah)"/>
  <!-- Claude builds → You approve code (bottom, right to left) -->
  <path d="M350,347 Q320,347 290,347" fill="none" stroke="#d4a574" stroke-width="2.5" marker-end="url(#ah)"/>
  <!-- You approve code → Claude outputs (bottom left corner) -->
  <path d="M110,347 Q60,347 60,300" fill="none" stroke="#d4a574" stroke-width="2.5" marker-end="url(#ah)"/>
  <!-- Claude outputs → You check (left side up) -->
  <path d="M60,240 Q60,210 60,180" fill="none" stroke="#d4a574" stroke-width="2.5" marker-end="url(#ah)"/>
  <!-- You check → You prompt (top left) -->
  <path d="M60,120 Q60,50 260,50" fill="none" stroke="#d4a574" stroke-width="2.5" marker-end="url(#ah)"/>
  <!-- Boxes -->
  <rect x="260" y="20" width="180" height="55" rx="10" fill="#fef3c7" stroke="#d4a574" stroke-width="2"/>
  <text x="350" y="42" text-anchor="middle" font-size="13" font-weight="600" fill="#1a1a2e">You prompt your</text>
  <text x="350" y="60" text-anchor="middle" font-size="13" font-weight="600" fill="#1a1a2e">requirements</text>
  <rect x="515" y="125" width="170" height="55" rx="10" fill="#f3f4f6" stroke="#d4a574" stroke-width="2"/>
  <text x="600" y="147" text-anchor="middle" font-size="13" font-weight="600" fill="#1a1a2e">Claude plans</text>
  <text x="600" y="165" text-anchor="middle" font-size="13" font-weight="600" fill="#1a1a2e">implementation</text>
  <rect x="515" y="245" width="170" height="55" rx="10" fill="#fef3c7" stroke="#d4a574" stroke-width="2"/>
  <text x="600" y="277" text-anchor="middle" font-size="13" font-weight="600" fill="#1a1a2e">You approve plan</text>
  <rect x="350" y="320" width="180" height="55" rx="10" fill="#f3f4f6" stroke="#d4a574" stroke-width="2"/>
  <text x="440" y="352" text-anchor="middle" font-size="13" font-weight="600" fill="#1a1a2e">Claude builds</text>
  <rect x="110" y="320" width="180" height="55" rx="10" fill="#fef3c7" stroke="#d4a574" stroke-width="2" stroke-dasharray="6,3"/>
  <text x="200" y="352" text-anchor="middle" font-size="13" font-weight="600" fill="#1a1a2e">You approve code</text>
  <rect x="-25" y="245" width="170" height="55" rx="10" fill="#f3f4f6" stroke="#d4a574" stroke-width="2"/>
  <text x="60" y="277" text-anchor="middle" font-size="13" font-weight="600" fill="#1a1a2e">Claude outputs</text>
  <rect x="-25" y="125" width="170" height="55" rx="10" fill="#fef3c7" stroke="#d4a574" stroke-width="2"/>
  <text x="60" y="157" text-anchor="middle" font-size="13" font-weight="600" fill="#1a1a2e">You check</text>
</svg>

It's a **conversation**, not a one-shot prompt.

---

# What Claude Produces

For any non-trivial request, expect:

1. **Inputs** — analyse input files (if any)
2. **An implementation plan** — what it intends to do
3. **Commands to run** — install, run, test
4. **File changes** — edits and new files with explanations
5. **Outputs** — logs, tables, charts + how to interpret them

---

# What You Should Always Check

1. Is the **logic of its implementation** sound? Did it pull the **relevant context**?
2. Did it change the **files you expected**?
3. Did it **run successfully** and do outputs pass basic **sanity checks**?
4. Did it **test its code** and **commit (save)** them?
5. Do you have enough **session/weekly limits** to complete your feature?

### If something looks wrong:

> 1. Press **Esc** to **interrupt** Claude (if still running)
> 2. **State your observation** of what is wrong or what it should be
> 3. Ask Claude to *"**Evaluate** your observation and if the plan is correct"*
> 4. (Get Claude to) **Revert / discard changes** back to last working state if needed

---

# Terminal Survival Kit

<div style="display:flex;gap:40px;font-size:0.75em;">
<div>

**You might use**

| Command | What it does |
|---------|-------------|
| `claude` | Start Claude Code |
| `Ctrl + C` | Stop a running process |
| `ls` | List files in current folder |
| `cd folder_name` | Change directory |
| `cd ..` | Go up one level |
| `cat file.txt` | Display file contents |
| `python script.py` | Run a Python script |
| `↑` (up arrow) | Repeat last command |

</div>
<div>

**Commands Claude often uses**

| Command | What it does |
|---------|-------------|
| `rm -rf *` | **⚠ Delete everything — watch out!** |
| `rm file.txt` | Delete a file |
| `mv old new` | Rename or move a file |
| `grep "text" file` | Search for text in files |
| `curl` | Fetch data from URLs / APIs |
| `npm install` / `pip install` | Install packages |
| `git` / `gh` | Git / GitHub version control |
| `kill` | Stop a background process |

</div>
</div>

---

<!-- _class: divider -->

# 4. Infrastructure Basics

## Hosting and storing data

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

> Claude can deploy locally for you, and guide you through server hosting setup.

---

# Free-ish Starter Options

These are free-tier friendly. Good for learning, personal tools and prototypes.

| Service | Best for |
|---------|---------|
| **Vercel** | Web apps (React, Next.js) |
| **Netlify** | Static sites + simple web apps |
| **Cloudflare Pages** | Static sites + edge functions |
| **Render / Railway** | Simple app hosting (backend) |
| **GitHub Pages** | Static sites (free with GitHub) |

> Claude can recommend the best option based on your project's requirements.

---

# Local vs Server Databases

### Local — Simplest way to store data, runs on your laptop.
- **SQLite** — single file database, no setup needed (⭐ best for simple projects)
- **Local Postgres** — full database as a service on your machine
- **CSV** — spreadsheet-like data in a plain text file (⚠ not scalable)
- **JSON** — structured data format, common for APIs and configs

### Server — Shared data for multi-user / server-hosted apps.
- **Supabase** — hosted Postgres + auth (generous free tier)
- **Managed Postgres/MySQL** — cloud-hosted by AWS, GCP, etc.

> Start with SQLite — upgrade to server when you need shared access.

---

<!-- _class: divider -->

# 5. Version Control Basics

## Git & GitHub

---

# Git & GitHub — What They Are

### Local
**Git** = a manual **"Save"** button (like in Microsoft Word), where you attach notes about your edits.

### Server / Remote repo
**GitHub** = a manual **"Google Drive"** — upload your own backup and share with others.

<svg viewBox="-15 0 730 110" xmlns="http://www.w3.org/2000/svg" style="width:80%;margin:80px auto 0;display:block;">
  <defs>
    <marker id="ga" markerWidth="8" markerHeight="6" refX="8" refY="3" orient="auto"><path d="M0,0 L8,3 L0,6" fill="#d4a574"/></marker>
  </defs>
  <!-- Boxes -->
  <rect x="0" y="25" width="120" height="50" rx="8" fill="#f3f4f6" stroke="#d4a574" stroke-width="2"/>
  <text x="60" y="55" text-anchor="middle" font-size="12" font-weight="600" fill="#1a1a2e">Untracked</text>
  <rect x="180" y="25" width="120" height="50" rx="8" fill="#f3f4f6" stroke="#d4a574" stroke-width="2"/>
  <text x="240" y="55" text-anchor="middle" font-size="12" font-weight="600" fill="#1a1a2e">Staged</text>
  <rect x="360" y="25" width="120" height="50" rx="8" fill="#f3f4f6" stroke="#d4a574" stroke-width="2"/>
  <text x="420" y="55" text-anchor="middle" font-size="12" font-weight="600" fill="#1a1a2e">Committed</text>
  <rect x="540" y="25" width="120" height="50" rx="8" fill="#f3f4f6" stroke="#d4a574" stroke-width="2"/>
  <text x="600" y="55" text-anchor="middle" font-size="12" font-weight="600" fill="#1a1a2e">Pushed</text>
  <!-- Arrows -->
  <path d="M120,50 L172,50" fill="none" stroke="#d4a574" stroke-width="2" marker-end="url(#ga)"/>
  <path d="M300,50 L352,50" fill="none" stroke="#d4a574" stroke-width="2" marker-end="url(#ga)"/>
  <path d="M480,50 L532,50" fill="none" stroke="#d4a574" stroke-width="2" marker-end="url(#ga)"/>
  <!-- Git commands above arrows -->
  <text x="146" y="15" text-anchor="middle" font-size="12" fill="#6b7280" font-style="italic">git add</text>
  <text x="326" y="15" text-anchor="middle" font-size="12" fill="#6b7280" font-style="italic">git commit</text>
  <text x="506" y="15" text-anchor="middle" font-size="12" fill="#6b7280" font-style="italic">git push</text>
  <!-- Analogies below boxes -->
  <text x="60" y="100" text-anchor="middle" font-size="11" fill="#6b7280">New unsaved doc</text>
  <text x="240" y="100" text-anchor="middle" font-size="11" fill="#6b7280">Ready to save</text>
  <text x="420" y="100" text-anchor="middle" font-size="11" fill="#6b7280">Saved locally</text>
  <text x="600" y="100" text-anchor="middle" font-size="11" fill="#6b7280">On GitHub</text>
</svg>

---

# Practical Git Tips

- Tell Claude to use a **private repo** for work-related code
- Remind Claude to **commit and push** after each feature
- For simplicity, tell Claude to **work on** `main` **branch** (branching is a pro feature)
- **Never commit sensitive data** (API/secret keys, passwords, `.env` files, sensitive CSVs)
  - Keep sensitive data in a `.env` file locally
- Use `.gitignore` to prevent committing (or tell Claude which files not to commit):

<div style="width:60%;margin-left:10%;">

```
# Sample .gitignore file
.env           # Environment variables / secrets
*.db           # Local databases
node_modules/  # Installed packages
dist/          # Build outputs
.DS_Store      # macOS junk
data/*.csv     # Sensitive data files
```

</div>

---

<!-- _class: divider -->

# 6. Testing Basics

## Why test and how

---

# Why Test?

Tests **automatically check** that your app works as expected — and that **future changes don't break it**.

| Type | What it tests |
|------|--------------|
| **Unit** | Does each piece work? |
| **Integration** | Do they work together? |
| **End-to-end (E2E)** | Does the whole thing work, starting from user interaction? |

### Example: a test catching a bug

<div style="display:flex;gap:30px;font-size:0.7em;">
<div>

**Buggy code:**
```python
def is_positive(n):
    return n >= 0  # bug: 0 is not positive!
```

</div>
<div>

**Test that catches it:**
```python
def test_zero_is_not_positive():
    assert is_positive(0) == False  # ❌ fails!
```

</div>
</div>

---

# Practical Testing Habits

1. **Build tests for new features** — including edge cases
2. **When fixing a bug** — add a test before or after to prevent recurrence
3. **Run tests before committing** — catch problems early
4. **Watch out** — Claude may ignore failing tests if it thinks they're unrelated to its edits

> You don't need to write tests by hand — Claude Code can generate them for you.

```
> Add tests (including edge cases) for what you built
```

---

<!-- _class: divider -->

# 7. Customising Claude

## Instructions and tool integrations

---

# Customising Workflow with CLAUDE.md

An **instruction file** that guides how Claude behaves in your project. Claude reads it automatically at the start of every session.

| Level | Location | Scope | Example |
|-------|----------|-------|---------|
| **Global** | `~/.claude/CLAUDE.md` | Your personal defaults across all projects | "Always write tests, use git and update project CLAUDE.md" |
| **Local** (repo) | `PROJECT/CLAUDE.md` | Project-specific rules + context (objectives, infrastructure) | "Run with `npm start`, test with `npm test`" |

> Use Claude to help you maintain both global and local CLAUDE.md — tell it to be **succinct** to save tokens.

---

# MCP — Model Context Protocol

MCP lets Claude **connect to external tools and services** — like Slack, databases, or APIs.

- Gives Claude richer context beyond your local files
- Enables actions like searching notes, querying data, or sending messages
- A pathway for future scaling

### Examples

- **OneNote / Notion** — search and reference your notes
- **Slack** — read and send messages
- **Databases** — query live data directly
- **Custom APIs** — connect to internal tools

> These are optional but powerful add-ons to your workflow.

---

# Claude Skills — Reusable Workflows

**Skills** are saved instructions that become `/slash-commands` you can reuse.

- Think of skills as saved recipes — each one teaches Claude a specific workflow
- Claude can also trigger skills automatically based on context

### Example: `/summarise-csv`

```markdown
Read the CSV file provided. Summarise:
- Number of rows and columns
- Column names and data types
- Key statistics (min, max, mean for numeric columns)
- Any missing values
```

> You can create your own skills or install community ones from GitHub.

---

<!-- _class: divider -->

# Wrap-up

## Summary and Q&A

---

# Key Takeaways

1. **Claude builds, you direct** — you own the problem, spec, review, and deployment
2. **Expect to iterate** — prompt, approve, check, repeat until it's right
3. **Always verify** — check logic, outputs, tests, and commits
4. **Know enough** — terminal, git, hosting, databases, and testing basics go a long way
5. **Customise your workflow** — use CLAUDE.md, skills, and MCP to make Claude work your way
6. **Start small, iterate fast** — build a prototype, then improve it one loop at a time

---

<!-- _class: title -->
<!-- _paginate: false -->
<!-- _footer: '' -->

# Questions?

## Let's build something together

Thank you!
