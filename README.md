# Question Paper Builder

**Live app:** https://rifat299.github.io/question-paper-builder/

A free browser tool for Bangladeshi educators to build and export SSC/HSC exam papers. No installation. Runs entirely in your browser.

---

## What it does

You type in the questions. The app formats them into an A4 paper — two-column layout, board-standard font sizes, section dividers, proper header with school name and exam info. Then you print it to PDF.

It also reads question papers from photos. Upload a picture of an existing paper, and Mistral AI pulls out all the questions and drops them into the editor.

---

## Question types

**MCQ (বহুনির্বাচনি)** — stem with four options. Choose ক/খ/গ/ঘ or a/b/c/d labels in Settings. Mark the correct answer for an answer key, and toggle whether the preview shows it. Any MCQ can have an optional figure attached.

**Creative Question (সৃজনশীল)** — উদ্দীপক (stimulus) followed by four sub-questions: knowledge, comprehension, application, higher-order. Standard 10-mark CQ format, with the 1+2+3+4 split for regular subjects. If you leave the higher-order field blank, the app recognizes it as a math CQ and shows the 2+4+4 split instead. Diagrams supported in the stimulus.

**Short Question** — open-ended, configurable marks.

---

## Features

### Paper header
School name, exam title, subject, subject code, time, total marks, set, year, instructions (Bangla and English, edited separately). All appear in the preview with the correct size and weight hierarchy.

### Live preview
Right panel updates as you type. The column layout fills left-first, the same way board papers print. What you see in the preview is what comes out on paper. On phones, an Edit/Preview tab switcher swaps between the two so you're not squinting at a split screen.

### Math
Wrap equations in `$...$` for inline or `$$...$$` for a display block. KaTeX renders them in real time.

```
$a^2 + b^2 = c^2$
$$\frac{-b \pm \sqrt{b^2-4ac}}{2a}$$
```

### AI image extraction
Upload or paste a photo of any question paper and Mistral reads it in two passes — first an OCR-style transcript of the page, then a pass that turns that transcript into structured MCQ/CQ/SQ entries. It picks up Bangla text, math, MCQ options, and CQ structure. Requires a free API key from Mistral (see setup).

### English version
Each question card has a **Translate with AI** button at the bottom. One click sends the question to Mistral and gets back an English translation — the LaTeX inside `$...$` is left untouched so equations don't break. The translation is editable. Switch the toolbar to **📄EN** and the preview shows the English version. Two papers from one session.

### Diagrams
MCQ and CQ questions both accept images. Drag a file, click to browse, or click the paste box and press Ctrl+V to grab from clipboard. Images scale to fit the column.

### Reorder
Drag the ⠿ handle on any card to move it. Preview updates instantly.

### Export
**Print** — opens the browser's print dialog, formatted for A4. Save as PDF from there or send straight to a printer.

### Clear all
One button wipes the current paper — header and questions both — with a confirmation prompt first.

---

## Setup

The app works immediately at https://rifat299.github.io/question-paper-builder/ for everything except AI features.

### Mistral API key (needed for image extraction and translation)

1. Go to [console.mistral.ai](https://console.mistral.ai/api-keys), sign in
2. Create an API key and copy it
3. In the app: click **⚙️** → paste the key → **Test Key** → **Save Settings**

The key is stored in your browser's `localStorage`. It never goes to any server except Mistral's API.

Extraction uses `pixtral-12b-2409` for reading the image, and `mistral-small-latest` for both structuring the result and translating questions. Check Mistral's console for current free-tier limits.

---

## How to use

**Build a paper from scratch**
1. Fill in the header fields
2. Click **+ MCQ**, **+ সৃজনশীল**, or **+ Short Q**
3. Type your questions. Use `$math$` for equations
4. Preview updates on the right as you work
5. Click **Print** when done and save as PDF

**Extract questions from a photo**
1. Add your Mistral API key in ⚙️ Settings
2. In **AI Image Extraction**, drag a photo in, click to browse, or click the paste box and press Ctrl+V
3. Click **Extract with Mistral**
4. Review the extracted questions, click **Import**

**Generate an English version**
1. Expand any question card
2. Scroll to the bottom — click **✨ Translate with AI**
3. Edit the translation if anything looks off
4. Click **📄EN** in the toolbar
5. Print the English version

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
- Better print page-break handling for long papers
- Print CSS refinements

---

## Tech used

| | |
|---|---|
| React 18 | UI |
| Babel Standalone | JSX without a build step |
| KaTeX | Math rendering |
| Browser print | PDF export |
| Mistral Pixtral 12B + Mistral Small | AI extraction and translation |
| Noto Serif Bengali, Hind Siliguri, Inter | Fonts |

---

## License

MIT. Use it, fork it, modify it.
