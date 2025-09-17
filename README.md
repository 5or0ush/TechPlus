# Tech+

# Tech+ Practice (CompTIA Tech+)

Lightweight browser app for randomized Tech+ practice and exam simulation. Pure HTML/CSS/JS. No build, no backend.

## Live demo (GitHub Pages)
1. Fork this repo.
2. In your fork: **Settings → Pages** → Source: `Deploy from a branch` → Branch: choose your branch (e.g., `app`) and **/(root)**.
3. Open:
   - `https://<your-username>.github.io/TechPlus/App.html`  
     or if you rename `App.html` to `index.html`:
   - `https://<your-username>.github.io/TechPlus/`

## Features
- Practice mode: choose section and number of questions.
- Exam mode: 75 questions pulled randomly across all sections.
- Instant feedback: correct = green, wrong = red, lock after selection, show explanation.
- Dark theme, mobile-friendly.

## Project layout
```
App.html            # main page (or rename to index.html)
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
# then open http://localhost:8000/App.html
```
Or use VS Code **Live Server**.

## Contributing
- Keep every question to 4 choices.
- Use clear, vendor-neutral explanations.
- Validate JSON (no trailing commas).
- Large additions: submit PR per section.

## License
MIT for code. Question content © contributors; provide proper attribution if importing third‑party material.
# Tech+ Practice (CompTIA Tech+)

Lightweight browser app for randomized Tech+ practice and exam simulation. Pure HTML/CSS/JS. No build, no backend.

## Live demo (GitHub Pages)
1. Fork this repo.
2. In your fork: **Settings → Pages** → Source: `Deploy from a branch` → Branch: choose your branch (e.g., `app`) and **/(root)**.
3. Open:
   - `https://<your-username>.github.io/TechPlus/App.html`  
     or if you rename `App.html` to `index.html`:
   - `https://<your-username>.github.io/TechPlus/`

## Features
- **Practice mode**: pick any section and choose number of questions (10, 20, 30, or All).
- **Exam mode**: fixed 75 questions pulled randomly from all sections.
- **Instant feedback**: correct = green, wrong = red, selection locked after answering, correct answer + explanation displayed.
- **Scoreboard (Exam mode only)**: live stats for answered, correct, wrong, and percentage score.
- Dark theme, responsive design, mobile-friendly.

## Project layout
```
index.html          # main page (was App.html)
data/
  s1_practice.json  # practice banks by section
  s1_exam.json      # curated exam banks by section
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
    "answer": 1,
    "explain": "Short rationale."
  }
]
```
- `answer` uses a 0-based index into `choices`.

### File naming
- Practice banks: `data/s<SECTION>_practice.json`
- Exam banks: `data/s<SECTION>_exam.json`
Example: `s3_practice.json`, `s3_exam.json`.

## How it works
- Practice mode loads only the selected section’s practice file and lets you choose 10/20/30/All questions.
- Exam mode loads all exam files, merges, shuffles, and serves 75 items with live scoring.
- All requests use `fetch()` over HTTP(S). Opening with `file://` will fail.

## Local development
Serve locally:
```bash
cd TechPlus
python3 -m http.server 8000
# then open http://localhost:8000/index.html
```

