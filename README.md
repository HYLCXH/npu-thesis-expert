# npu-thesis-expert
`npu-thesis-expert`，它用于帮助处理西北工业大学 `nwputhesis` / NPU LaTeX 论文模板和框架相关任务
# NPU Thesis Expert Skill 使用说明

它用于帮助处理西北工业大学 `nwputhesis` / NPU LaTeX 论文模板相关任务，包括论文写作、格式检查、参考文献、图片表格、XeLaTeX/Biber 编译和常见错误排查。

## 1. Skill 文件结构

```text
.cursor/skills/npu-thesis-expert/
├── SKILL.md              # 必需：Cursor 识别 skill 的主文件
├── README.md             # 本说明文件
├── latex-cheatsheet.md   # NwpuThesis 常用路径、命令和写法速查
└── npu-guidelines.md     # NPU 论文结构和写作要求摘要
```

其中 `SKILL.md` 必须存在，并且文件开头需要有 YAML frontmatter：

```markdown
---
name: npu-thesis-expert
description: "西北工业大学本硕博论文 LaTeX 专家。用于 NwpuThesis 模板的项目配置、论文写作、格式检查、参考文献管理和 XeLaTeX/Biber 编译排错。Use when creating or editing an NPU bachelor/master/phd thesis, working with nwputhesis, editing .tex/.bib files, asking about NPU thesis format, or needing LaTeX compilation help."
---
```

## 2. 模板来源说明

当前项目中的 NPU LaTeX 模板参考/基于 `NwpuThesis`：

```text
https://github.com/1195343015/nwputhesis
```

本项目模板说明文件位于：

```text
latex论文格式/README.md
```

其中包含上游仓库、Release、TeX Live、GPL v3 许可证，以及西北工业大学研究生/本科论文规范依据等信息。后续使用 `npu-thesis-expert` 排查模板行为时，应优先以本地 `latex论文格式/` 的实际文件为准；只有在需要核对模板来源、版本变化或上游说明时，再参考 `1195343015/nwputhesis`。

## 3. Cursor 如何加载项目级 Skill

当前 skill 已经放在项目级标准目录：

```text
D:\skills\.cursor\skills\npu-thesis-expert\SKILL.md
```

Cursor 通常会自动扫描当前工作区下的：

```text
.cursor/skills/<skill-name>/SKILL.md
```

因此，只要你在 Cursor 中打开的是 `D:\skills` 这个工作区，后续对 NPU 论文模板、`nwputhesis`、`.tex`、`.bib`、参考文献、Biber、XeLaTeX、论文格式等问题提问时，Cursor 就有机会自动使用这个 skill。

如果没有立刻生效，可以尝试：

1. 保存 `SKILL.md`。
2. 在 Cursor 中执行 `Developer: Reload Window`，或直接重启 Cursor。
3. 重新打开 `D:\skills` 工作区。
4. 在对话中明确说：`使用 npu-thesis-expert skill 帮我检查 NPU 论文模板编译问题`。

## 3. 个人级 Skill 与项目级 Skill 的区别

项目级 skill：

```text
<项目根目录>/.cursor/skills/npu-thesis-expert/SKILL.md
```

特点：

- 只对当前项目生效。
- 可以随项目一起提交和共享。
- 适合本仓库的 NPU 论文模板工作流。

个人级 skill：

```text
C:\Users\26941\.cursor\skills\npu-thesis-expert\SKILL.md
```

特点：

- 对你本机多个 Cursor 项目生效。
- 适合长期复用的个人工作流。
- 不会自动随项目仓库共享。

注意：不要把自定义 skill 放到：

```text
C:\Users\26941\.cursor\skills-cursor\
```

该目录通常是 Cursor 内置 skills 的位置，不建议手动修改。

## 4. 如何触发这个 Skill

推荐提问方式：

```text
使用 npu-thesis-expert skill，帮我检查 bachelor.tex 为什么没有参考文献。
```

```text
帮我排查 nwputhesis 编译失败，日志里有 xdvipdfmx:fatal: Unable to open bachelor.pdf。
```

```text
帮我给本科论文第 1 章增加参考文献引用，并检查 reference.bib。
```

```text
帮我检查 NPU 论文模板的摘要、关键词和章节结构是否规范。
```

如果问题中包含以下关键词，Cursor 更容易自动匹配该 skill：

- NPU / 西北工业大学
- nwputhesis
- bachelor.tex / master.tex / phd.tex
- thesis-body.tex
- reference.bib
- XeLaTeX / Biber / latexmk
- 参考文献不显示
- 引用问号
- 论文格式

## 5. 后续是否还需要 `@latex论文格式`？

一般情况下：**不一定需要每次都 `@latex论文格式`**。

原因是 skill 已经记录了本仓库的模板位置和常用路径，例如：

```text
latex论文格式/
latex论文格式/bachelor.tex
latex论文格式/content/thesis/undergraduate/reference.bib
latex论文格式/content/thesis/graduate/reference.bib
```

但在以下情况，建议继续使用 `@latex论文格式` 或直接 `@` 具体文件：

1. 你希望 Cursor 明确把整个模板目录作为上下文。
2. 你刚刚新增、移动或重命名了模板目录。
3. 你同时有多个 LaTeX 模板目录，担心 Cursor 选错。
4. 你要让 Cursor 修改某个具体文件，例如：
   - `@latex论文格式/content/thesis/undergraduate/chapter1.tex`
   - `@latex论文格式/content/thesis/undergraduate/reference.bib`
   - `@latex论文格式/thesis-body.tex`
5. 你询问 PDF 当前显示内容、日志片段或某个具体报错时，最好同时 `@` 日志文件或终端输出。

推荐习惯：

- 普通问题：不用 `@latex论文格式`，直接问即可。
- 涉及修改文件：最好 `@` 具体文件。
- 涉及全局结构/编译排查：可以 `@latex论文格式`。

## 6. 参考文献不显示的标准排查流程

当 PDF 中没有“参考文献”章节时，按以下顺序排查：

1. 确认当前编译入口：
   - 本科：`bachelor.tex`
   - 硕士：`master.tex`
   - 博士：`phd.tex`
2. 确认 `thesis-body.tex` 中加载了正确的 `.bib`：
   - 本科：`content/thesis/undergraduate/reference.bib`
   - 研究生：`content/thesis/graduate/reference.bib`
3. 确认正文中有引用命令，例如：

```tex
已有研究表明该方法具有较好的鲁棒性\cite{mitra2007gesture}。
```

4. 如果正文没有任何 `\cite{...}`，参考文献通常不会显示。可以：
   - 在正文中加入真实引用；或
   - 明确需要列出全部 `.bib` 条目时，在 `\printbibliography` 前加入 `\nocite{*}`。
5. 使用完整编译：

```bash
latexmk -xelatex bachelor.tex
```

6. 日志中出现以下内容，说明 Biber 已经参与处理：

```text
Latexmk: Using biber to make bibliography file(s).
Latexmk: Bibliography file(s) from .bcf file:
  content/thesis/undergraduate/reference.bib
```

## 7. Windows 下 PDF 被占用的处理流程

如果日志出现：

```text
xdvipdfmx:fatal: Unable to open "bachelor.pdf".
No output PDF file written.
```

说明最终 PDF 没有成功写出，常见原因是 `bachelor.pdf` 正在被 Cursor PDF 预览器或外部 PDF 阅读器占用。

处理步骤：

1. 关闭 Cursor/VS Code 中打开的 `bachelor.pdf` 预览标签页。
2. 关闭外部 PDF 阅读器中打开的 `bachelor.pdf`。
3. 删除旧的 `bachelor.pdf`。
4. 清理并重新编译：

```bash
latexmk -C bachelor.tex
latexmk -xelatex bachelor.tex
```

如果 `latexmk` 提示：

```text
Latexmk: Nothing to do for 'bachelor.tex'.
Collected error summary:
  xdvipdfmx: gave an error in previous invocation of latexmk.
```

通常是上一次失败状态被记录了。清理后重新编译即可。

临时替代方案是换一个输出名：

```bash
xelatex -jobname=bachelor-new bachelor.tex
biber bachelor-new
xelatex -jobname=bachelor-new bachelor.tex
xelatex -jobname=bachelor-new bachelor.tex
```

## 8. 建议的日常使用方式

写作修改：

```text
使用 npu-thesis-expert，帮我润色本科论文第 2 章，保持学术表达，不编造实验结果。
```

参考文献：

```text
使用 npu-thesis-expert，检查我的 reference.bib 和正文 cite 是否一致。
```

编译排错：

```text
使用 npu-thesis-expert，根据这个日志判断为什么 bachelor.pdf 没更新。
```

格式检查：

```text
使用 npu-thesis-expert，检查我的摘要、关键词、章节标题是否符合 NPU 论文写作习惯。
```
