# Computational Analysis of Readability in CEFR-Graded English Reading Materials

## Overview

This project investigates whether traditional readability indices reflect the intended proficiency progression (A1–C1) built into a single ELT textbook series's reading passages. It combines corpus preparation, NLTK-based tokenization, and eight `textstat`-computed readability formulas to test how well automated readability measures track CEFR-graded material.

## Research Question

To what extent do traditional readability indices (Flesch Reading Ease, Flesch-Kincaid Grade Level, SMOG, Dale-Chall, Coleman-Liau Index, Automated Readability Index, Gunning Fog, Linsear Write Formula) reflect the intended progression of reading passages across CEFR proficiency levels within a single ELT textbook series?

## Corpus

- Source: *English File* series (Oxford University Press)
- 5 passages, one per CEFR level (A1, A2, B1, B2, C1)
- Word counts: A1 (853), A2 (877), B1 (1091), B2 (791), C1 (862)
- A1 and A2 consist of several short, complete texts (dialogues, personal profiles, short narratives) compiled to a comparable length, reflecting how beginner-level material is structured in this series. B1–C1 are longer, more continuous passages.

**The raw corpus text is not included in this repository**, since it consists of excerpts from a commercially copyrighted textbook. The `data/` folder explains this and describes the corpus structure only. Anyone wishing to reproduce this study should source equivalent excerpts from the same or a comparable series.

## Methodology

1. Corpus cleaning: correcting OCR/transcription artifacts (verified against the source where possible) while preserving original punctuation style
2. Quote normalization: standardizing curly quotes to straight quotes for consistent tokenization
3. Tokenization: NLTK `word_tokenize` / `sent_tokenize` (via the `punkt` / `punkt_tab` models)
4. Readability scoring: all eight formulas computed via `textstat` for each passage
5. Aggregation: results compiled into a pandas DataFrame, ordered by CEFR level
6. Visualization: per-formula bar charts and a cross-formula comparison chart (matplotlib)

## Key Findings

- Six of eight formulas (Flesch Reading Ease, Flesch-Kincaid, SMOG, Coleman-Liau, ARI, Gunning Fog) showed a fully consistent progression from A1 to C1, with no reversals — strong convergent evidence that this series' CEFR grading is linguistically well-calibrated.
- Two formulas broke pattern: **Dale-Chall** dipped slightly between A1 and A2, plausibly due to its fixed familiar-word list penalizing the high density of personal names in the A1 text rather than genuine difficulty. **Linsear Write** reversed twice, consistent with its relatively coarse, small-sample design and more limited validation in the general ELT literature.
- A full discussion of these findings, together with methodological limitations, is provided in the accompanying report (see `/report`, forthcoming).

## Repository Structure

notebook/ → Full analysis notebook (Google Colab / Jupyter)
results/ → Output data table and chart images
data/ → Corpus description only (raw text excluded — see above)

## Reproducing This Analysis

1. Open `notebook/readability_analysis.ipynb` in Google Colab
2. Source your own 5 passages (or use the same series) and upload them as `A1.txt`, `A2.txt`, `B1.txt`, `B2.txt`, `C1.txt`
3. Run all cells in order

## Tools Used

Python, NLTK, pandas, textstat, matplotlib — all run in Google Colab.

## A Note on AI Assistance

Code in this project was developed through AI-assisted pair programming (Claude, Anthropic) as part of a self-directed learning process. Study design, corpus construction and cleaning decisions, formula selection, and interpretation of results are my own.

## License

Code in this repository is shared under the MIT License. The corpus source material (*English File*, Oxford University Press) is not included and remains the copyright of its publisher.
