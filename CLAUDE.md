# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This repository contains LaTeX-based summary notes for the Advanced Machine Learning lecture at ETH Zurich. The notes aim to restructure and internalize complex ML concepts by organizing them into a coherent narrative with detailed explanations, intuition, and explicit assumptions.

**Key characteristics:**
- Academic writing style with LaTeX mathematical notation
- Focus on detailed derivations and conceptual explanations (not just results)
- Each chapter is a standalone `.tex` file in the `chapters/` directory
- Main document (`main.tex`) includes all chapters via `\include` directives

## Build Commands

### Build the PDF
```bash
latexmk -pdf main.tex
```

This generates `main.pdf` along with auxiliary files (`.aux`, `.log`, `.out`, `.toc`, etc.).

### Clean build artifacts
```bash
latexmk -c main.tex  # Remove most auxiliary files
latexmk -C main.tex  # Remove all generated files including PDF
```

## Project Structure

```
main.tex                    # Main document with preamble, includes all chapters
chapters/
  00 Math Preliminaries.tex
  01 Conceptual Foundation.tex
  02 Fundamentals of Machine Learning.tex
  03 Regression.tex
  ...                       # 18 chapters total (some still TODO)
images/                     # Figures and diagrams
sample.bib                  # Bibliography (currently not used)
```

**Chapter naming convention:** Files are prefixed with two-digit numbers (e.g., `00`, `01`, ..., `18`) to maintain ordering. Chapter titles follow after the number.

**Document structure:**
- `main.tex`: Defines the document class, packages, custom environments, and includes all chapters
- Each chapter file starts with `\section{...}` and contains `\subsection` elements
- Custom environments: `derivation` and `notebox` (shaded boxes for proofs and notes)
- Math: Heavy use of `align*`, `equation`, inline math with `$...$`

## LaTeX Style Guidelines

**Critical rules from `.github/copilot-instructions.md`:**

1. **No package changes**: Keep the current `article` class, geometry settings, spacing (`\parskip`, no `\parindent`), and loaded packages unchanged unless explicitly requested

2. **Math formatting**:
   - Use display environments (`equation`, `align*`) for multi-line expressions
   - **ASCII-only macros**: Never use Unicode math symbols in LaTeX source—stick to ASCII macros like `\alpha`, `\mathbb{R}`, `\times`, etc.

3. **Content structure**:
   - Prefer `\section`/`\subsection` and lists for organization
   - Use concise academic tone
   - Add new content to relevant chapter files; only add `\include{...}` in `main.tex` when creating a new chapter

4. **Figures**:
   - Keep all figures in `images/` directory
   - Use `\label{...}` and `\ref{...}` for cross-references
   - Match existing sizing and placement patterns

5. **Bibliography**: Currently commented out in `main.tex`. If citing is needed, use `sample.bib` and add new entries there

6. **No placeholders**: Mark TODOs explicitly if information is missing; never use speculative or placeholder text

7. **Custom environments**:
   - `\begin{derivation}...\end{derivation}`: For mathematical derivations (shaded box with "Derivation." prefix)
   - `\begin{notebox}...\end{notebox}`: For important notes (shaded box with "Note." prefix)
   - `\begin{definition}...\end{definition}`: Theorem-style definition environment

## Content Guidelines

When writing or editing chapters:

1. **Narrative structure**: Create a coherent flow with clear connections between concepts (avoid slide-like disconnected points)

2. **Detailed explanations**: Don't just state results—explain why they hold, provide intuition, and make implicit assumptions explicit

3. **Derivations**: Include full mathematical derivations in `derivation` environments, especially when results are typically given without proof

4. **No slide references**: The notes should stand alone; don't mention "the slides" or lecture-specific context

5. **Cross-references**: Use `\label` and `\ref` to connect related concepts (e.g., `\label{sec:cond-gaussian}` in section on conditional Gaussians, referenced elsewhere)

## Current TODO Items (from README)

- [ ] Write chapter 10 Neural Networks
- [ ] Write chapter 11 Transformers
- [ ] Write chapter 12 Graph Neural Networks
- [ ] Write chapter 14 Reinforcement Learning

Note: Some chapter files already exist for these topics but may need expansion or completion.

## Working with This Repository

**Typical workflow:**
1. Identify which chapter file needs modification
2. Read the relevant chapter file(s) to understand existing style and content
3. Make changes following the style guidelines above
4. Build the PDF with `latexmk -pdf main.tex` to verify compilation
5. Check the generated PDF for formatting, math rendering, and overall appearance

**When adding a new chapter:**
1. Create file in `chapters/` with pattern `NN Chapter Title.tex`
2. Start with `\section{Chapter Title}`
3. Add `\include{chapters/NN Chapter Title}` to `main.tex` in the appropriate position
4. Build to verify

**Common issues:**
- If LaTeX compilation fails, check for unescaped special characters (`_`, `%`, `&`, `#`, etc.)
- Math errors often come from mismatched delimiters or undefined commands
- Missing figures: ensure paths in `\includegraphics` match files in `images/`
