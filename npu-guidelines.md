# NPU Thesis Guidelines Reference

This document summarizes the NPU thesis structure and writing requirements used by the `npu-thesis-expert` skill. It is based on the repository's `NwpuThesis` LaTeX template and its README.

> Important: Always prioritize the latest official NPU school/department notices, supervisor requirements, and the actual `nwputhesis` template implementation.

## 1. Template Basis

The repository includes the **NwpuThesis** LaTeX template for Northwestern Polytechnical University.

According to the template README:

- It supports bachelor, master, and PhD theses.
- The graduate thesis format follows the 2025 NPU Graduate School thesis writing guide.
- The bachelor thesis format follows the latest undergraduate graduation design/thesis writing requirements referenced by the template.
- The recommended TeX distribution is TeX Live 2026 or a recent TeX Live version.
- The recommended editor setup is Cursor / VS Code + LaTeX Workshop.
- The template uses XeLaTeX and Biber.

## 2. Entry Files

Choose the correct entry file according to thesis type.

| Thesis type | Entry file | Description |
|---|---|---|
| Bachelor | `bachelor.tex` | 本科毕业设计论文 |
| Master | `master.tex` | 硕士学位论文 |
| PhD | `phd.tex` | 博士学位论文 |

All three entry files load:

```tex
\input{thesis-body}
```

The shared `thesis-body.tex` automatically selects undergraduate or graduate content according to the `degree` option.

## 3. Common Document Options

Options are set in the `\documentclass[...]` block of the selected entry file.

| Option | Values | Notes |
|---|---|---|
| `degree` | `bachelor`, `master`, `phd` | Thesis type |
| `fontset` | `windows`, `local`, `fandol` | Font configuration |
| `academic` | `true`, `false` | Graduate only. `true` for academic degree, `false` for professional degree |
| `blindreview` | `true`, `false` | Whether to hide author, advisor, student number and other identity information |
| `colorcover` | `true`, `false` | Graduate final electronic version may require color cover/back cover |
| `bibstyle` | `2015`, `2025` | GB/T 7714 bibliography style version |
| `lang` / `language` | `chs`, `eng` | Chinese or English version |

Recommended examples:

```tex
\documentclass[
    degree = bachelor,
    fontset = windows,
    blindreview = false,
]{nwputhesis}
```

```tex
\documentclass[
    degree = master,
    fontset = windows,
    academic = true,
    blindreview = false,
    colorcover = true,
]{nwputhesis}
```

```tex
\documentclass[
    degree = phd,
    fontset = windows,
    academic = false,
    blindreview = false,
    colorcover = false,
]{nwputhesis}
```

## 4. Bachelor Thesis Structure

The exact layout is controlled by the template. A typical bachelor thesis contains:

1. Cover and title pages
2. Chinese abstract
3. English abstract
4. Table of contents
5. Main chapters
6. References
7. Acknowledgements
8. Graduation design summary
9. Appendices

Main editable files:

| Content | File |
|---|---|
| Metadata | `content/thesis/undergraduate/info.tex` |
| Chinese and English abstracts | `content/thesis/undergraduate/abstract.tex` |
| Chapter list | `content/thesis/undergraduate/chapters.tex` |
| Chapters | `content/thesis/undergraduate/chapter1.tex` ... `chapter5.tex` |
| References | `content/thesis/undergraduate/reference.bib` |
| Acknowledgements | `content/thesis/undergraduate/acknowledgements.tex` |
| Design summary | `content/thesis/undergraduate/designsummary.tex` |
| Appendix | `content/thesis/undergraduate/appendix.tex` |

## 5. Graduate Thesis Structure

The exact layout is controlled by the template. A typical graduate thesis contains:

1. Cover and title pages
2. Defense committee information
3. Chinese abstract
4. English abstract
5. Table of contents
6. List of figures
7. List of tables
8. Main chapters
9. References
10. Appendices
11. Acknowledgements
12. Research accomplishments during degree study
13. Intellectual property and originality declaration

Main editable files:

| Content | File |
|---|---|
| Metadata | `content/thesis/graduate/info.tex` |
| Defense committee | `content/thesis/graduate/committee.tex` |
| Chinese and English abstracts | `content/thesis/graduate/abstract.tex` |
| Chapter list | `content/thesis/graduate/chapters.tex` |
| Chapters | `content/thesis/graduate/chapter1.tex` ... `chapter6.tex` |
| References | `content/thesis/graduate/reference.bib` |
| Appendix | `content/thesis/graduate/appendix.tex` |
| Acknowledgements | `content/thesis/graduate/acknowledgements.tex` |
| Accomplishments | `content/thesis/graduate/accomplishments.tex` |
| Accomplishment bibliography | `content/thesis/graduate/accomplishments.bib` |
| Signed declaration PDF | `content/figures/研究生学位论文使用授权声明.pdf` |

## 6. Writing Quality Rules

- Use formal academic language.
- Avoid colloquial expressions.
- Keep terminology consistent.
- Define acronyms when first used.
- Use SI units consistently when applicable.
- Do not cite sources that are not actually listed in the bibliography.
- Do not fabricate data, results, tables, figures, or references.
- Ensure each paragraph has a clear topic and logical connection to surrounding paragraphs.
- Make conclusions match the presented evidence.
