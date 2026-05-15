# NwpuThesis LaTeX Cheatsheet

Quick reference for using the NPU `nwputhesis` template in this repository.

## 1. Template Root

In this repository, the template root is:

```text
latex论文格式/
```

Run build commands from this directory unless the user has copied the template elsewhere.

## 2. Entry Files

Choose one entry file according to the thesis type:

| Thesis type | Entry file |
|---|---|
| Bachelor | `bachelor.tex` |
| Master | `master.tex` |
| PhD | `phd.tex` |

All entry files load:

```tex
\input{thesis-body}
```

## 3. Document Options

Options are set in the selected entry file.

### Bachelor

```tex
\documentclass[
    degree = bachelor,
    fontset = windows,
    blindreview = false,
]{nwputhesis}
```

### Master

```tex
\documentclass[
    degree = master,
    fontset = windows,
    academic = true,
    blindreview = false,
    colorcover = true,
]{nwputhesis}
```

### PhD

```tex
\documentclass[
    degree = phd,
    fontset = windows,
    academic = false,
    blindreview = false,
    colorcover = false,
]{nwputhesis}
```

Common options:

| Option | Values | Meaning |
|---|---|---|
| `degree` | `bachelor`, `master`, `phd` | Thesis type |
| `fontset` | `windows`, `local`, `fandol` | Font setup |
| `academic` | `true`, `false` | Graduate academic/professional degree |
| `blindreview` | `true`, `false` | Blind review version |
| `colorcover` | `true`, `false` | Color cover/back cover for graduate final PDF |
| `bibstyle` | `2015`, `2025` | GB/T 7714 bibliography style version |
| `lang` / `language` | `chs`, `eng` | Chinese or English thesis version |

## 4. Project Structure

```text
latex论文格式/
├── bachelor.tex
├── master.tex
├── phd.tex
├── thesis-body.tex
├── nwputhesis.cls
├── nwputhesis/
├── content/
│   ├── figures/
│   └── thesis/
│       ├── undergraduate/
│       │   ├── info.tex
│       │   ├── abstract.tex
│       │   ├── chapters.tex
│       │   ├── chapter1.tex ... chapter5.tex
│       │   ├── reference.bib
│       │   ├── acknowledgements.tex
│       │   ├── designsummary.tex
│       │   └── appendix.tex
│       └── graduate/
│           ├── info.tex
│           ├── committee.tex
│           ├── abstract.tex
│           ├── chapters.tex
│           ├── chapter1.tex ... chapter6.tex
│           ├── reference.bib
│           ├── appendix.tex
│           ├── acknowledgements.tex
│           ├── accomplishments.tex
│           └── accomplishments.bib
├── .vscode/settings.json
├── .latexmkrc
└── Makefile
```

## 5. Metadata

Metadata is configured with `\nwputhesissetup{...}`.

### Bachelor metadata

File:

```text
content/thesis/undergraduate/info.tex
```

Example:

```tex
\nwputhesissetup{
    title = {论文中文题名},
    author = {作者姓名},
    year = {2026},
    month = {7},
    major = {专业名称},
    advisor = {导师姓名},
}
```

### Graduate metadata

File:

```text
content/thesis/graduate/info.tex
```

Example:

```tex
\nwputhesissetup{
    class-number = {TP311.1},
    student-number = {2023123456},
    title = {论文中文题名},
    title* = {English Thesis Title},
    author = {作者姓名},
    author* = {Author Name},
    year = {2026},
    month = {3},
    school = {学院名称},
    major = {专业名称},
    major* = {Major in English},
    advisor = {导师姓名},
    advisor* = {Advisor Name},
    advisor-rank = {教授},
    advisor-rank* = {Professor},
}
```

## 6. Abstract and Keywords

Abstract files:

```text
content/thesis/undergraduate/abstract.tex
content/thesis/graduate/abstract.tex
```

Chinese keywords:

```tex
\keywordslist{关键词1, 关键词2, 关键词3}
```

English keywords:

```tex
\engkeywordslist{keyword 1, keyword 2, keyword 3}
```

Keep the Chinese and English abstracts consistent in content.
