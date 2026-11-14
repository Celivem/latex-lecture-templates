# 中文理工講義與習題詳解 LaTeX 版型 · LaTeX Lecture Templates

兩套 XeLaTeX 版型，給繁體中文的理工科講義與習題詳解使用：A4、Noto Sans TC、深藍標題、淺橘重點結果框，定義、定理、推導、例題共用一組編號。

Two XeLaTeX templates for Traditional Chinese science and engineering course materials: one for lecture notes (definition / theorem / derivation / example blocks with shared numbering, key-result boxes), one for worked solutions (English problem statement in a serif box, Chinese solution, result boxes).

| 講義 `codex_notes.tex` | 詳解 `codex_solutions.tex` |
|---|---|
| ![講義範例](docs/notes_preview.png) | ![詳解範例](docs/solutions_preview.png) |

## 需要什麼

- XeLaTeX（TeX Live 2023 以上；用到 `fontspec`、`xeCJK`、`tcolorbox`、`pgfplots`、`titlesec` 等常見套件）
- Noto Sans TC 字型：見 [fonts/README.md](fonts/README.md)

## 快速開始

1. 下載 Noto Sans TC，把 `NotoSansTC-Regular.ttf`、`NotoSansTC-Bold.ttf` 放進 `fonts/`。
2. 編譯範例：

   ```bash
   cd examples
   latexmk -xelatex notes_example.tex
   latexmk -xelatex solutions_example.tex
   ```

範例檔 [notes_example.tex](examples/notes_example.tex)、[solutions_example.tex](examples/solutions_example.tex) 用到了大部分的功能，可以直接複製來改。

## 講義版型 `styles/codex_notes.tex`

主檔用 `\documentclass[10pt,a4paper]{article}`，在載入版型前定義 `\coursename`（頁首左側），然後 `\input` 版型：

```latex
\providecommand{\codexfontpath}{../fonts/}   % 字型資料夾
\newcommand{\coursename}{數學物理講義}
\input{../styles/codex_notes.tex}
\setuplecture{1}{高斯積分}   % 章號、章名：節號 1-1、式號 (1.1)、頁首 L01
\coursekeepblocks            % 讓節標題不落在頁底
```

| 指令／環境 | 用途 |
|---|---|
| `\lecturehead{小字}{章名}` | 章首標頭（取代 `\maketitle`） |
| `\booksection{中文}{English}` | 節標題，英文副標放同一行 |
| `\plainsection{標題}` | 不編號的節（引導、總結） |
| `\chaptergoal{...}` | 章首問題框 |
| `definition`、`theorem` | 定義、定理框，可加 `[標題]` |
| `derivation`、`example` | 推導、例題（左側細線），可加 `[標題]` |
| `solution` | 例題的解，接在 `example` 之後 |
| `note`、`extension` | 注意框、延伸補充 |
| `\keyresult{數學式}` | 淺橘底的重點結果 |
| `\dd`、`\e`、`\avg{}`、`\Order` | 微分 d、e、期望值括號、大 O |

可選參數（在 `\input` 之前定義）：`\codexsecsep`（節號分隔符，預設 `-`）、`\codexlecturetag`（頁首章號格式，預設 `L01`）、`\codextoclabelwidth`（目錄節號寬度）。

## 詳解版型 `styles/codex_solutions.tex`

字型設定讀同資料夾的 `fonts.tex`（範例見 [examples/fonts.tex](examples/fonts.tex)），英文題目框使用 TeX Live 內建的 TeX Gyre Termes。

| 指令／環境 | 用途 |
|---|---|
| `\courseheader{左}{右}` | 頁首文字 |
| `\chapterhead{CHAPTER 1}{第 1 章　章名}` | 章首標頭（另起一頁） |
| `chapterintro` | 章首說明（灰字） |
| `\problem{題號}{中文題名}` | 題目標題，自動加入目錄 |
| `statement` | 英文原題框，跨頁時標「（續）」 |
| `resultbox`、`\keyresult{...}` | 結果框；`\keyresult` 在數學模式裡改成橘色底 |
| `notebox` | 提醒或補充 |

詳解內的小標用 `\subsection*{思路}` 這類不編號的形式，目錄只列章與題目。

## 授權

版型與範例以 [MIT License](LICENSE) 釋出。Noto Sans TC 採 SIL Open Font License，需另外下載。
