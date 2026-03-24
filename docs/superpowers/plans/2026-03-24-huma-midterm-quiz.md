# HUMA Midterm Quiz Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Replace the old quiz bank with a 12-chapter HUMA 2831 midterm study deck and keep the app's retry workflow working.

**Architecture:** Keep the existing React/Vite quiz app, but swap the chapter metadata and all question-bank JSON files so the UI loads chapter-specific HUMA decks. Preserve the current quiz engine, review flow, and statistics model while updating type definitions and documentation to reflect the new course scope.

**Tech Stack:** React, TypeScript, Vite, JSON question banks, npm

---

### Task 1: Lock The New Chapter Model

**Files:**
- Modify: `src/types.ts`
- Modify: `src/quizLogic.ts`

- [ ] **Step 1: Update the chapter id model**

Define chapter ids for `all` plus the 12 HUMA chapter decks.

- [ ] **Step 2: Update chapter metadata**

Replace the old `CHAPTER_INFO` entries with week/date-based HUMA labels and matching JSON filenames.

- [ ] **Step 3: Keep quiz selection behavior intact**

Ensure `loadAllProblems()` and `loadProblemsForChapter()` still work with the expanded chapter list.

- [ ] **Step 4: Run a TypeScript-aware build check**

Run: `npm run build`
Expected: build succeeds or reveals any type mismatch caused by the new chapter ids.

### Task 2: Replace The Problem Bank

**Files:**
- Delete: `public/problems/exam1-methods.json`
- Delete: `public/problems/exam1-module1.json`
- Delete: `public/problems/exam1-module2.json`
- Create: `public/problems/huma-week1-0204.json`
- Create: `public/problems/huma-week2-0209.json`
- Create: `public/problems/huma-week2-0211.json`
- Create: `public/problems/huma-week3-0216.json`
- Create: `public/problems/huma-week4-0223.json`
- Create: `public/problems/huma-week4-0225.json`
- Create: `public/problems/huma-week5-0302.json`
- Create: `public/problems/huma-week5-0304.json`
- Create: `public/problems/huma-week6-0309.json`
- Create: `public/problems/huma-week6-0311.json`
- Create: `public/problems/huma-week7-0316.json`
- Create: `public/problems/huma-week7-0318.json`

- [ ] **Step 1: Draft chapter-specific question sets**

Write about 15 multiple-choice items per deck based on the slide content and the user's highlighted exam patterns.

- [ ] **Step 2: Encode metadata consistently**

For every item, include `chapter`, `related_info`, `why_high_yield`, `source_refs`, `incorrect_count`, `concept_id`, and `item_form`.

- [ ] **Step 3: Validate JSON structure**

Run: `python3 - <<'PY' ...`
Expected: all problem files parse successfully and every item has required keys.

### Task 3: Align Surface Copy With The New Course

**Files:**
- Modify: `src/components/Welcome.tsx`
- Modify: `README.md`

- [ ] **Step 1: Update the landing label**

Change the app title string so it no longer says `psychology-quiz`.

- [ ] **Step 2: Refresh project documentation**

Rewrite the README overview and customization notes so they describe the HUMA 2831 deck structure.

### Task 4: Verify End-To-End Behavior

**Files:**
- Modify as needed based on verification results

- [ ] **Step 1: Run JSON validation**

Run a script that parses all `public/problems/*.json` files.
Expected: zero parse errors and consistent required fields.

- [ ] **Step 2: Run production build**

Run: `npm run build`
Expected: exit code 0.

- [ ] **Step 3: Spot-check generated content**

Run a script that counts questions per file and confirms the Mar 18 deck uses only the in-scope material.
Expected: around 15 questions per deck and no ontology-only coverage.
