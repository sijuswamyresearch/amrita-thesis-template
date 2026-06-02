# Amrita Vishwa Vidyapeetham — Doctoral Document LaTeX Template

A modular, plug-and-play LaTeX template for **PhD Thesis Proposals, Synopses,
Project Reports, and Final Theses** at Amrita Vishwa Vidyapeetham.

---

## Quick Start

### 1. Edit `doc-info.tex` ← **THE ONLY FILE YOU NEED TO CHANGE FOR PERSONAL INFO**

Open `doc-info.tex` and fill in:
- Your name and registration number
- Thesis title
- Supervisor / Co-supervisor names and designations
- Department, campus, submission month/year
- HOD and Dean names
- Dedication text (leave blank to suppress)

Everything else — title page, certificate, declaration, abstract header — is
**generated automatically** from these macros.

### 2. Choose your document type

| Document            | Use this driver file    |
|---------------------|------------------------|
| Final Thesis        | `main.tex`              |
| Thesis Proposal     | `proposal-main.tex`     |
| Synopsis            | `synopsis-main.tex`  |
| Project Report      | `main.tex` (replace `\newcommand{\DocType}{thesis}` with `\newcommand{\DocType}{report}`)  |

### 3. Write your content

| File | What to edit |
|------|-------------|
| `frontmatter/abstract-body.tex` | Abstract body |
| `frontmatter/acknowledgements.tex` | Acknowledgements |
| `frontmatter/abbreviations.tex` | Your acronyms |
| `chapters/ch01-introduction.tex` | Chapter 1 |
| `chapters/ch02-literature-review.tex` | Chapter 2 |
| `chapters/ch03-methodology.tex` | Chapter 3 |
| `chapters/ch04-results.tex` | Chapter 4 |
| `chapters/ch05-conclusion.tex` | Chapter 5 |
| `backmatter/publications.tex` | Your publications list |
| `backmatter/appendix.tex` | Appendices |
| `references.bib` | BibTeX references |
| `images/` | All figures and logos |

### 4. Compile

```bash
pdflatex main        # or: pdflatex proposal-main
bibtex main
pdflatex main
pdflatex main
```

Or use **latexmk** for one-shot compilation:
```bash
latexmk -pdf main
```

---

## Folder Structure

```
amrita-thesis-template/
│
├── main.tex                   ← Thesis / Synopsis / Report driver
├── proposal-main.tex          ← Thesis Proposal driver
├── synopsis-main.tex          ← synopsis driver
├── form7a-abstract.tex        ← abstract generator as per guidelines (form 7a)
├── doc-info.tex               ← ★ YOUR PERSONAL INFO (edit only this)
├── references.bib             ← BibTeX bibliography
│
├── styles/
│   └── configuration.tex      ← All packages & formatting (do not edit)
│
├── frontmatter/
│   ├── titlepage.tex          ← Auto-generated
│   ├── certificate.tex        ← Auto-generated
│   ├── declaration.tex        ← Auto-generated
│   ├── dedication.tex         ← Auto-generated (suppressed if blank)
│   ├── abstract.body           ← Edit this
│   ├── acknowledgements.tex   ← Edit this
│   └── abbreviations.tex      ← Edit this
│
├── chapters/
│   ├── ch01-introduction.tex
│   ├── ch02-literature-review.tex
│   ├── ch03-methodology.tex
│   ├── ch04-results.tex
│   ├── ch05-conclusion.tex
│   └── proposal-*.tex         ← Proposal-specific sections
|   └── synopsis-*.tex         ← synopsis-specific sections
│
├── backmatter/
│   ├── publications.tex
│   └── appendix.tex
│
└── images/
    ├── README.md
    └── amrita-logo.png        ← Add your images iside this folder
```

---

## Adding More Chapters

1. Create `chapters/ch06-mynewtopic.tex`
2. Add `\input{chapters/ch06-mynewtopic}` to `main.tex` in the correct order.

## Suppressing Optional Sections

| Section | How to suppress |
|---------|----------------|
| Dedication | Leave `\DedicationText{}` empty in `doc-info.tex` |
| Appendix | Comment out `\input{backmatter/appendix}` in `main.tex` |
| List of Figures | Comment out `\listoffigures` in `main.tex` |

---

## Compliance Notes (Amrita Vishwa Vidyapeetham PhD Policy 2024)

- **Font:** Times New Roman 12pt ✓
- **Spacing:** 1.5 line spacing ✓
- **Margins:** Top 1", Bottom 1", Left 1.25", Right 1" ✓
- **Page size:** A4 ✓
- **Certificate format:** As per Engineering/AI faculty template ✓
- **Bibliography style:** plainnat (author-year) ✓
- Chapters follow the standard order required by the policy document.

---

## Troubleshooting

**Logo not showing:** Ensure `images/amrita-logo.png` exists. The template
gracefully shows placeholder text if the file is missing.

**BibTeX not working:** Run the full 4-step compile sequence
(pdflatex → bibtex → pdflatex → pdflatex).

**Missing `ifthen` package:** Add `\usepackage{ifthen}` before loading
`styles/configuration.tex` (already done in both driver files).
