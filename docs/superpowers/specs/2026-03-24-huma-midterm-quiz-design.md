# HUMA Midterm Quiz Redesign

## Goal

Replace the repository's existing non-HUMA quiz bank with a HUMA 2831 midterm quiz set aligned to the March 25, 2026 exam scope. The new quiz should help the user drill high-yield distinctions and revisit missed concepts through the app's existing retry flow.

## Scope

- Replace all current problem-bank JSON files in `public/problems/` with HUMA-specific chapter decks.
- Treat each in-syllabus PDF as one chapter.
- Create roughly 15 multiple-choice questions per chapter.
- Keep the current app structure, wrong-answer review flow, and localStorage-based tracking.
- Exclude short essay items.
- Exclude the ontology section from `HUMA2831_Week7_03182026_Slides.pdf` by limiting coverage to slide 11.

## Exam-Aligned Content Strategy

The quiz bank should prioritize the kinds of distinction-based questions most likely to appear on the exam rather than low-yield memorization. Questions should repeatedly test the course's recurring oppositions and movement of thought:

- `phenomena` vs. `noumena`
- `sensibility` vs. `understanding` vs. `reason`
- `intuition` / `sensation` vs. `concept` / `judgment`
- `analytic` vs. `synthetic` judgment
- `a priori` vs. `experience`
- `transcendental` vs. `transcendent`
- `regulative` vs. `constitutive`
- `conditioned` vs. `unconditioned`

Examples from the slides should be used mainly to test which distinction they illustrate. This includes examples such as:

- `triangle`
- `the sun rises in the east`
- `shadow rabbit`
- `mirror image`
- `fire and infant`
- `chipped bowl`
- `knife is absent`

## Chapter Plan

The app should expose these chapter decks:

1. Week 1 - Feb 4
2. Week 2A - Feb 9
3. Week 2B - Feb 11
4. Week 3 - Feb 16
5. Week 4A - Feb 23
6. Week 4B - Feb 25
7. Week 5A - Mar 2
8. Week 5B - Mar 4
9. Week 6A - Mar 9
10. Week 6B - Mar 11
11. Week 7A - Mar 16
12. Week 7B - Mar 18

An `All Chapters` option should remain available.

## Question Design Rules

Each problem should:

- Be written in English, with English explanations.
- Be multiple-choice with four options.
- Include a concise explanation in `related_info`.
- Include a `why_high_yield` field that states the tested distinction or exam pattern.
- Include `source_refs` that point back to the relevant slide deck and topic.
- Use plausible distractors from nearby Kantian terms, not obviously wrong filler.

Each chapter deck should balance:

- definition items
- distinction/comparison items
- example-classification items
- application/scenario items

## Technical Design

The app can keep its current architecture. The rewrite requires:

- New chapter metadata and chapter ids in `src/types.ts` and `src/quizLogic.ts`
- New HUMA chapter titles and file names in `CHAPTER_INFO`
- Removal of the old problem-bank JSON files
- Creation of 12 new problem-bank JSON files under `public/problems/`
- README updates so the project description matches HUMA 2831 instead of the prior course

No behavioral redesign is needed for the quiz engine beyond making chapter selection compatible with the new 12-deck structure.

## Verification

Verification should include:

- JSON validity checks for all new question banks
- a production build via `npm run build`
- spot-checking that chapter loading and `All Chapters` loading still succeed

## Notes

- The existing retry system is part of the value of this tool and should remain intact.
- The most important success criterion is not just volume of questions, but whether the item set trains the user's distinction-mapping for the actual exam.
