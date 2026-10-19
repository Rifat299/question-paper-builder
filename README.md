# Question Paper Builder

**Live app:** https://rifat299.github.io/question-paper-builder/

A free browser tool for Bangladeshi educators to build and export SSC/HSC exam papers. No installation, no account, no API keys. Runs entirely in your browser.

---

## What it does

You type in the questions. The app formats them into an A4 paper — two-column layout, board-standard font sizes, section dividers, proper header with school name and exam info. Then you print it to PDF.

It works with AI **manually**: the app gives you ready-made prompts, you run them in the AI of your choice (Claude, Gemini, ChatGPT), and you paste the JSON reply back. The app itself makes no AI calls and needs no API key.

---

## Question types

**MCQ (বহুনির্বাচনি)** — stem with four options. Choose ক/খ/গ/ঘ or a/b/c/d labels in Settings. Mark the correct answer for an answer key, and toggle whether the preview shows it. Any MCQ can have an optional figure attached.

**Creative Question (সৃজনশীল)** — উদ্দীপক (stimulus) followed by four sub-questions: knowledge, comprehension, application, higher-order. Standard 10-mark CQ format, with the 1+2+3+4 split for regular subjects. If you leave the higher-order field blank, the app recognizes it as a math CQ and shows the 2+4+4 split instead. Figures supported in the stimulus.

**Short Question** — open-ended, configurable marks.

---

## Features

### Paper header
School name, exam title, subject, subject code, time, total marks, set, year, instructions (Bangla and English, edited separately). All appear in the preview with the correct size and weight hierarchy.

### Live preview
Right panel updates as you type. The column layout fills left-first, the same way board papers print. What you see in the preview is what comes out on paper. On phones, an Edit/Preview tab switcher swaps between the two so you're not squinting at a split screen.

### Math
Wrap equations in `$...$` for inline or `$$...$$` for a display block. KaTeX renders them in real time. Equations written as `\( ... \)` or `\[ ... \]` (common in AI replies) are converted automatically.

```
$a^2 + b^2 = c^2$
$$\frac{-b \pm \sqrt{b^2-4ac}}{2a}$$
```

### Import questions with AI (no API key)
1. Click **Copy Extraction Prompt**.
2. Open Claude, Gemini or ChatGPT, attach a photo of a question paper, and paste the prompt.
3. Paste the JSON reply into the import box, click **Parse JSON**, review the list, then click **Import**.

The importer is forgiving: it strips code fences and surrounding chatter, repairs stray backslashes in LaTeX, and accepts a single question, a list, or `{"questions": [...]}`.

### English version (manual translation)
- Each question card has **Copy Bangla Q + AI prompt**. It copies the Bangla question plus instructions for the AI: translate naturally, leave everything inside `$...$` untouched, reply with JSON only.
- Paste the AI's reply into the JSON box on the card and click **Apply to English fields**. The English fields stay editable, and you can also type the translation by hand.
- **Translate all** (above the question list) builds one prompt for every question — or only those without English yet — and applies the reply question by question using the `no` values.
- Switch the toolbar to **📄EN** and the preview and printed paper show the English version. Two papers from one session.

### Diagrams: image or TikZ
Every figure slot (MCQ figure, CQ stimulus figure) has an **Image / TikZ** switch.

- **Image** — drag a file, click to browse, or click the paste box and press Ctrl+V. Images scale to fit the column. Use this for figures with Bangla labels.
- **TikZ** — paste TikZ code and the figure is drawn in the browser with a live preview, stored as vector SVG with the question, so it stays crisp in print. Set a max height per figure. **Copy TikZ prompt for AI** gives you instructions to use with a photo of the figure.

TikZ notes:
- Rendering uses [TikZJax](https://github.com/rod2ik/tikzjax) (loaded from the jsDelivr CDN). The first diagram downloads the TeX engine and can take 10–30 seconds; you need an internet connection for rendering new TikZ code.
- Labels must be Latin letters, digits or math like `$A$` — the engine cannot typeset Bangla text.
- Put any `\usetikzlibrary{...}` line before `\begin{tikzpicture}`. Only common TikZ libraries are supported.

### Copy and paste questions as JSON
- **📋 JSON** on any question card copies that question.
- **📥 Paste JSON** adds a copied question (or a list) as new questions at the end — in the same paper or a different one.
- **Copy all as JSON** copies every question.
- TikZ code and its SVG are included in the copied JSON. Uploaded images are not (they are too large) — re-attach them.

### Autosave, Save and Load
Your paper is autosaved in the browser as you work. **Save** downloads the whole paper (header, questions, figures, paper language) as a `.qpb.json` progress file; **Load** restores it later or on another computer.

### Reorder
Drag the ⠿ handle on any card to move it. Preview updates instantly.

### Export
**Print** — opens the browser's print dialog, formatted for A4. Save as PDF from there or send straight to a printer.

### Clear all
One button wipes the current paper — header and questions both — with a confirmation prompt first.

---

## How to use

**Build a paper from scratch**
1. Fill in the header fields
2. Click **+ MCQ**, **+ সৃজনশীল**, or **+ Short Q**
3. Type your questions. Use `$math$` for equations
4. Preview updates on the right as you work
5. Click **Print** when done and save as PDF

**Extract questions from a photo**
1. In **Import Questions from AI**, click **Copy Extraction Prompt**
2. Run it in Claude / Gemini / ChatGPT with your photo attached
3. Paste the JSON reply, click **Parse JSON**, review, then **Import**

**Generate an English version**
1. On a question card, click **Copy Bangla Q + AI prompt** (or use **Translate all** for the whole paper)
2. Run it in your AI and copy the JSON reply
3. Paste it into the JSON box and click **Apply**; edit the wording if needed
4. Click **📄EN** in the toolbar and print

**Add a diagram**
1. Expand any MCQ or CQ card
2. Choose **🖼️ Image** (drag, browse, or Ctrl+V) or **📐 TikZ** (paste code, check the preview)

**Reuse a question**
1. Click **📋 JSON** on the question
2. In any paper, click **📥 Paste JSON** and paste

---

## Contributing on GitHub

The entire app is one HTML file. No build step, no npm, no framework setup.

### Fork and edit

1. Fork the repo: https://github.com/rifat299/question-paper-builder
2. Edit `index.html`
3. Open `index.html` locally in any browser to test — it just works
4. Submit a pull request

### Report a bug or request a feature

Open an issue: https://github.com/rifat299/question-paper-builder/issues

Include what you expected, what happened, your browser and OS, and a screenshot if it helps.

### Things worth contributing

- More question types (fill-in-the-blank, matching)
- Better print page-break handling for long papers
- Print CSS refinements
- Offline TikZ rendering (bundle the TeX engine)

---

## Tech used

| | |
|---|---|
| React 18 | UI |
| Babel Standalone | JSX without a build step |
| KaTeX | Math rendering |
| TikZJax | TikZ diagrams rendered to SVG in the browser |
| Browser print | PDF export |
| Noto Serif Bengali, Hind Siliguri, Inter | Fonts |

---

## License

MIT. Use it, fork it, modify it.
