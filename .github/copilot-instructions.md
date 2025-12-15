# Copilot Instructions

## Repository purpose

- AML course summary written in LaTeX (`main.tex` includes chapter files like `00 Math Preliminaries.tex`).

## Style & formatting

- Use LaTeX only; keep the current `article` class, geometry, spacing (`\parskip`, no paragraph indent), and loaded packages unchanged unless asked.
- Prefer `\section`/`\subsection`/lists for structure; keep concise academic tone and fix obvious typos while editing.
- For math, use display environments (`equation`, `align*`) for multi-line expressions; avoid Unicode math symbols—stick to ASCII macros.
- Keep figures in `images/`, with `\label`/`\ref`; match existing sizing/placement patterns.
- Avoid adding new packages or altering `main.tex` layout unless explicitly requested.

## Content placement

- Add new content to the relevant chapter file; only add a new `\include{...}` in `main.tex` when creating a new chapter file.
- Leave the bibliography commented unless asked; if citing, prefer entries from `sample.bib` and add new ones there if needed.

## Safety/other

- No placeholder or speculative text—mark TODOs explicitly if information is missing.
- Preserve ASCII-only text unless the document already uses specific symbols and they are required.
