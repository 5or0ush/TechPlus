# CompTIA Tech+

Lightweight browser app for randomized Tech+ practice and exam simulation. Pure HTML/CSS/JS. 

## Live demo (GitHub Pages)

You can run this app straight from GitHub—no build step.

**Enable Pages on your fork:**
1. Fork this repo to your account.
2. In your fork: **Settings → Pages**
3. **Source:** `Deploy from a branch`
4. **Branch:** select the branch that contains `index.html` 
5. **Folder/Path:** `/(root)` (not `/docs`)
6. Save. Wait 1–2 minutes for the first deploy.

**Open your live site:**
- `https://<your-username>.github.io/TechPlus/`

**Requirements / Troubleshooting**
- `index.html` must be at the repository root (same level as `data/`).
- If you see a 404, refresh after a minute or check **Settings → Pages** for the deployed URL.
- Private repos require an eligible plan to publish Pages. Public forks work out of the box.
- Changes to JSON files deploy automatically after you push.

## Features
- Practice mode: choose section and number of questions.
- Exam mode: 75 questions pulled randomly across all sections.
- Instant feedback: correct = green, wrong = red, lock after selection, show explanation.
- Dark theme, mobile-friendly.

## Project layout
```
index.html          # main page
data/
  s1_practice.json  # practice banks by section
  s1_exam.json      # curated exam banks by section
  s2_practice.json
  s2_exam.json
  ...
  s12_practice.json
  s12_exam.json
```

## Question file format
Each JSON file is an array of question objects:
```json
[
  {
    "q": "Question text?",
    "choices": ["A","B","C","D"],
    "answer": 1,                  // 0-based index into choices
    "explain": "Short rationale."
  }
]
```

### File naming
- Practice banks: `data/s<SECTION>_practice.json`  
- Exam banks: `data/s<SECTION>_exam.json`  
Example: `s3_practice.json`, `s3_exam.json`.

## How it works
- Practice mode loads only the selected section’s **practice** file.
- Exam mode loads **all sections’ exam** files, merges, shuffles, and serves 75 items.
- All requests use `fetch()` over HTTP(S). Opening with `file://` will fail.

## Local development
Serve locally:
```bash
cd TechPlus
python3 -m http.server 8000
# then open http://localhost:8000/index.html
```
Or use VS Code **Live Server**.

## Contributing
- Keep every question to 4 choices.
- Use clear, vendor-neutral explanations.
- Validate JSON (no trailing commas).
- Large additions: submit PR per section.

