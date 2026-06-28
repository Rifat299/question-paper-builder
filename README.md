# Question Paper Builder

**Live app:** https://rifat299.github.io/question-paper-builder/

A free browser tool for Bangladeshi educators to build and export SSC/HSC exam papers. No installation. Runs entirely in your browser.

---

## What it does

You type in the questions. The app formats them into an A4 paper — two-column layout, board-standard font sizes, section dividers, proper header with school name and exam info. Then you export to PDF.

It also reads question papers from photos. Upload a picture of an existing paper, and Gemini AI pulls out all the questions and drops them into the editor.

---

## Question types

**MCQ (বহুনির্বাচনি)** — stem with four options (ক/খ/গ/ঘ or a/b/c/d). You can mark the correct answer for an answer key. Any MCQ can have an optional figure attached.

**Creative Question (সৃজনশীল)** — উদ্দীপক (stimulus) followed by four sub-questions at 1, 2, 3, and 4 marks. Standard 10-mark CQ format. Diagrams supported in the stimulus.

**Short Question** — open-ended, configurable marks.

---

## Features

### Paper header
School name, exam title, subject, subject code, time, total marks, set, year, instructions. All appear in the preview with the correct size and weight hierarchy.

### Live preview
Right panel updates as you type. The column layout fills left-first, the same way board papers print. What you see in the preview is what comes out of the PDF export.

### Math
Wrap equations in `$...$` for inline or `$$...$$` for a display block. KaTeX renders them in real time.

```
$a^2 + b^2 = c^2$
$$\frac{-b \pm \sqrt{b^2-4ac}}{2a}$$
```

### AI image extraction
Upload a photo of any question paper — Gemini reads it and fills the editor fields. Picks up Bangla text, math, MCQ options, CQ structure. Requires a free API key (see setup). Free tier is 250 images per day.

### English version
Each question card has a **Translate with AI** button at the bottom. One click sends the question to Gemini and gets back an English translation. The translation is editable. Switch the toolbar to **📄EN** and the preview and PDF show the English version. Two papers from one session.

### Diagrams
MCQ and CQ questions both accept images. Drag a file, click to browse, or click the paste box and press Ctrl+V to grab from clipboard. Images scale to fit the column.

### Reorder
Drag the ⠿ handle on any card to move it. Preview updates instantly.

### Export
**Export PDF** — renders the preview at 2x resolution and saves an A4 PDF.
**Print** — opens the browser print dialog.

---

## Setup

The app works immediately at https://rifat299.github.io/question-paper-builder/ for everything except AI features.

### Gemini API key (needed for image extraction and translation)

1. Go to [aistudio.google.com](https://aistudio.google.com), sign in with Google
2. Click **Get API key** → **Create API key** → copy it
3. In the app: click **⚙️** → paste the key → **Test Key** → **Save Settings**

The key is stored in your browser's `localStorage`. It never goes to any server except Google's API.

Free tier: 250 requests/day, 10/minute, using `gemini-2.5-flash`.

---

## How to use

**Build a paper from scratch**
1. Fill in the header fields
2. Click **+ MCQ**, **+ সৃজনশীল**, or **+ Short Q**
3. Type your questions. Use `$math$` for equations
4. Preview updates on the right as you work
5. **Export PDF** when done

**Extract questions from a photo**
1. Add your Gemini API key in ⚙️ Settings
2. In **AI Image Extraction**, drag a photo in, click to browse, or click the paste box and press Ctrl+V
3. Click **Extract with Gemini**
4. Review the extracted questions, click **Import**

**Generate an English version**
1. Expand any question card
2. Scroll to the bottom — click **✨ Translate with AI**
3. Edit the translation if anything looks off
4. Click **📄EN** in the toolbar
5. Export the English PDF

**Add a diagram**
1. Expand any MCQ or CQ card
2. Find **📐 Add Diagram**
3. Drag an image in, click to browse, or click the paste box and press Ctrl+V

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

- Save/load paper as JSON
- More question types (fill-in-the-blank, matching)
- Better PDF page-break handling for long papers
- Print CSS refinements

---

## Tech used

| | |
|---|---|
| React 18 | UI |
| Babel Standalone | JSX without a build step |
| KaTeX | Math rendering |
| jsPDF + html2canvas | PDF export |
| Gemini 2.5 Flash | AI extraction and translation |
| Noto Serif Bengali | Bangla font |

---

## License

MIT. Use it, fork it, modify it.
