# Veritas — Plagiarism Detection Engine for Academic Submissions

A working web app that screens academic submissions for copied and paraphrased
content, based on the project presentation of the same name.

## Features
- Paste or upload (.txt/.md) a student submission
- Similarity score, originality score, word count and matched-source count
- Per-source breakdown with matched phrases and a score bar
- Annotated submission with matched passages highlighted in place
- Adjustable match length (3–8 word n-grams) to tune sensitivity
- Extendable reference library — upload prior submissions as reference files
- Runs entirely in the browser; no submission data leaves the device

## Detection method
1. Normalise text, remove stop words, build overlapping word n-grams (shingles)
2. Containment: share of submission shingles found in each reference document
3. TF-IDF cosine similarity across the corpus for distinctive shared vocabulary
4. Blended score (75% containment + 25% cosine), matched shingles located back
   in the original text for highlighting

Core logic: `src/lib/plagiarism.ts`. Reference corpus: `src/lib/corpus.ts`.

## Tech stack
React 19, TanStack Start / TanStack Router, TypeScript, Tailwind CSS v4, Vite 7.

## Run locally
```bash
npm install     # or: bun install
npm run dev     # http://localhost:8080
npm run build
```

## Note
A similarity score is evidence, not a verdict. Pair the report with clear
policy, staff training and human review.
