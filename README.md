# প্রশ্নপত্র বিল্ডার — Question Paper Builder
**SSC & HSC Exam Paper Builder for Bangladeshi Curriculum**

A fully static, single-file web app. No backend. No build step. Host free on GitHub Pages.

---

## ✨ Features

| Feature | Detail |
|---|---|
| **MCQ** | 4-option (ক/খ/গ/ঘ or a/b/c/d), marks, correct answer marker |
| **Creative Q (সৃজনশীল)** | Stimulus + 4 sub-questions (1+2+3+4 = 10 marks) |
| **Short Questions** | Open-ended, configurable marks |
| **AI Image Extraction** | Upload a photo → Gemini parses all questions automatically |
| **LaTeX Math** | `$x^2$` inline, `$$\frac{a}{b}$$` block — renders via KaTeX |
| **Bangla + English** | Full UTF-8, Hind Siliguri + Noto Serif Bengali fonts |
| **Live Preview** | Side-by-side A4 preview, updates instantly |
| **PDF Export** | jsPDF + html2canvas → print-ready A4 PDF |
| **Drag & Drop Reorder** | Reorder questions by dragging |
| **Mobile Friendly** | Tab-based editor/preview on mobile |

---

## 🚀 Deploy to GitHub Pages (3 steps)

```bash
# 1. Create a new repo on GitHub, then:
git init
git add index.html README.md .nojekyll
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/question-paper-builder.git
git push -u origin main

# 2. In GitHub repo → Settings → Pages → Source: "Deploy from branch" → main → / (root)
# 3. Your app is live at: https://YOUR_USERNAME.github.io/question-paper-builder/
```

That's it. The `.nojekyll` file tells GitHub Pages to skip Jekyll processing.

---

## 🔑 Setting up Gemini API (for AI image extraction)

1. Go to [aistudio.google.com](https://aistudio.google.com)
2. Sign in with Google → click **Get API key** → Create API key (free tier: 15 req/min)
3. In the app: click **⚙️ Settings** → paste your key → **Test Key** → **Save**

Your key is stored only in `localStorage` — never transmitted to any server other than Google's API directly from your browser.

---

## 📐 Math Syntax (KaTeX)

| What | Syntax | Result |
|---|---|---|
| Inline math | `$x^2 + y^2$` | x² + y² |
| Block math | `$$\frac{a}{b}$$` | fraction display |
| Square root | `$\sqrt{x}$` | √x |
| Fraction | `$\frac{p}{q}$` | p/q |
| Matrix | `$$\begin{pmatrix} a & b \\ c & d \end{pmatrix}$$` | matrix |
| Subscript | `$H_2O$` | H₂O |
| Greek | `$\alpha, \beta, \lambda$` | α, β, λ |

---

## 🛠️ Local Usage (no install needed)

Just open `index.html` in any modern browser. For AI extraction to work, you need an internet connection (Gemini API call from browser). Everything else works fully offline.

---

## 📁 File Structure

```
index.html          ← The entire app (single file, ~54KB)
README.md           ← This file
.nojekyll           ← Disables Jekyll on GitHub Pages
```

---

## 🏗️ Tech Stack

- **React 18** (via CDN, no build needed)
- **Babel Standalone** (JSX transpilation in browser)
- **KaTeX 0.16** (math rendering)
- **jsPDF 2.5 + html2canvas 1.4** (PDF export)
- **Google Gemini 1.5 Flash** (AI image OCR — free tier)
- **Google Fonts** (Hind Siliguri, Noto Serif Bengali, Inter)

---

## 📄 License
MIT — free to use, modify, and deploy.
