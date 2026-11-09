# Tally
I built Tally to manage dozens of codebases and physical projects across dual-boot Linux and Windows using Git-tracked Markdown files backed by an ephemeral SQLite cache for instant CLI speed.

Every task manager, app, and cloud tool I tried either got in the way, broke across dual-boot partitions, or forced me into a proprietary database trap. If you're managing a massive number of projects—codebases, physical builds, creative pipelines, and life—across multiple operating systems, standard to-do apps fall apart. You end up with lists everywhere and execute on nothing.

Tally is a local-first, zero-bloat task engine designed around one hard rule: Plain text is the only permanent state.


## The Core Idea

Markdown is the Source of Truth: Your projects live as flat .md files with YAML frontmatter in a Git-tracked registry (~/projects/registry/). They hold your notes, your lore, your specs, and your tasks (- [ ]). Because they're just text, Git handles synchronization seamlessly across Windows, Linux, and laptops without binary merge conflicts.

SQLite is Disposable: Parsing 200+ markdown files on every CLI query is slow. Tally uses an ephemeral, git-ignored SQLite database (.index.sqlite) purely as a read cache. If the index ever gets out of sync, corrupted, or you pull changes from another machine, you just delete it and Tally rebuilds it from the markdown files in milliseconds.

AI-Native: Because tasks and project notes live natively in flat Markdown files, local LLMs and RAG pipelines can read your project state and append tasks without wrappers or APIs.

## How It Works in Practice

Every project gets a single markdown file:
```Markdown

---
id: beaumont-lore
status: active
context: gamedev
---

# Notes on Léon's Purse
Historical vegetable-tanned cowhide collet with supple pork lining.

## Tasks
- [ ] Finalize physical prototype patterns
- [ ] Draft lyrics for Gentleman's Winter
- [x] Select leather weight```
