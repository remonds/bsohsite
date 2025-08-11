# BSOH Website Blueprint

## Purpose
This document is the single source of truth for the design, build, and deployment of the new BSOH website.  
It records all agreed decisions, the current project baseline, and the rationale behind key choices.  
It ensures continuity over time, even if team members change, and provides a clear reference for both development and governance.

## Objectives
- Maintain a **current baseline** (“What We’ve Agreed So Far”) for quick orientation.
- Keep a **Decision Log** with dates and context, so all changes are traceable.
- Maintain a **Change Log** to see the project’s evolution at a glance.
- Describe the **architecture, workflows, and feature set** in enough detail to guide implementation.
- Record **deployment and hosting** considerations for informed, evidence-based choices.

---

## 1. Current Baseline – What We’ve Agreed So Far
*(This section contains the current confirmed baseline in plain language — updated whenever the baseline changes.)*

---

## 2. Decision Log
| Date       | Decision | Context | Impact |
|------------|----------|---------|--------|
| YYYY-MM-DD | …        | …       | …      |

---

## 3. Change Log
*(Append-only chronological list of changes to the baseline and major plan elements.)*

- YYYY-MM-DD — …

---

## 4. Architecture & Features
*(Detailed plan, workflows, content types, module choices, configuration settings, etc.)*

---

## 5. Git Repository Setup & Initialization

This section documents the exact steps used to create, connect, and initialize the GitHub repository for the BSOH website.  
All commands are executed from the local development environment on `~/proj/bsohsite`.

### Create and link the GitHub repo (with our agreed data)

#### Step 1 – Decide baseline settings
- **GitHub repo name**: `bsohsite` (private)  
- **Local project root**: `~/proj/bsohsite`  
- **Git repo directory**: `~/proj/bsohsite/repo`  
- **DDEV project name (later)**: **bsoh**  
- **TLD**: default `ddev.site`  
- **Blueprint path**: `~/proj/bsohsite/repo/docs/BSOH_Website_Blueprint.md`  
- **`.gitignore` source (now)**: `~/proj/bsohsite/notes/gitassets/Drupal8.gitignore`  

---

#### Step 2 – Create the empty repo on GitHub
1. Open https://github.com/new  
2. Owner: `remonds`  
3. Repository name: `bsohsite`  
4. Description: `Drupal 10 Composer-based site with DDEV configuration for BSOH.`  
5. Visibility: **Private**  
6. **Do NOT check:** “Add a README”, “Add .gitignore”, “Choose a license”  
7. Click **Create repository**

---

#### Step 3 – Repository Initialization & Remote Setup

### Purpose
To set up the local Git repository for the Drupal 10 Composer-based site, link it to the remote GitHub repository, and document the commands and reasoning for future maintainers.

### Steps
```bash
cd ~/proj/bsohsite/repo                # Navigate to local project root
git init                               # Initialize a new Git repository
git branch -m main                     # Rename default branch to 'main'
git remote add origin git@github.com:remonds/bsohsite.git
                                       # Link local repo to remote GitHub repo ('origin')
git remote -v                          # Verify remote configuration
```

### Explanation of Commands
**git init**  
Creates an empty Git repository in the current folder (`.git` directory).

**git branch -m main**  
Renames the current branch to `main` to align with modern Git/GitHub defaults.

**git remote add origin <URL>**  
Links the local repository to the remote GitHub repository.  

`origin` is a Git nickname for this remote repository — commonly used to refer to the primary remote.  

`<URL>` is the SSH address of the GitHub repository.

**git remote -v**  
Lists all remotes linked to this repository, showing both fetch and push URLs.

### Notes
**Why use origin instead of github?**  
`origin` is the widely-used convention in Git for naming the primary remote.  
Using it ensures compatibility with tutorials, scripts, and common workflows.

### Diagram

```
        Local Repository                           Remote Repository (GitHub)
    ┌────────────────────────┐                ┌──────────────────────────────┐
    │   Branch: main         │                │   Branch: main               │
    │   Working Directory    │                │   Hosted on GitHub           │
    │   Staging Area         │                │   URL: git@github.com:...    │
    └──────────┬─────────────┘                └──────────────┬───────────────┘
               │ Push (git push)                             │ Pull (git pull)
               ▼                                             ▲
    ┌────────────────────────┐                ┌──────────────────────────────┐
    │     origin/main        │  <---------->  │     main (default branch)    │
    └────────────────────────┘                └──────────────────────────────┘

```

---

#### Step 4 – Add .gitignore as first commit

```bash
cd ~/proj/bsohsite/repo                # Navigate to local project root
cp ~/proj/bsohsite/notes/gitassets/Drupal8-adapted.gitignore .gitignore
git add .gitignore
git commit -m "Add initial .gitignore (GitHub Drupal template, adapted for Drupal 10 + Composer + DDEV; BSOH notes included)"
git push --set-upstream origin main    # (-u) Push to origin/main and set it as the upstream branch for local 'main'
```

---

#### Step 5 – Add the Blueprint skeleton (second commit)

Create file `~/proj/bsohsite/repo/docs/BSOH_Website_Blueprint.md` (this present file) with the skeleton we prepared earlier, then:

```bash
cd ~/proj/bsohsite/repo                # Navigate to local project root
mv ~/proj/bsohsite/notes/BSOH_Website_Blueprint.md docs/BSOH_Website_Blueprint.md
git add docs/BSOH_Website_Blueprint.md
git commit -m "Add BSOH Website Blueprint skeleton (Purpose, Objectives, Baseline, Decision Log, Change Log)"
git push
```

---

## 6. Deployment & Hosting Notes
*(Current stance, requirements, final choice when decided.)*
