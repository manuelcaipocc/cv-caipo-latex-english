# CV Caipo - LaTeX Resume (ENGLISH version)

Professional CV/resume (English) for **Manuel Caipo** (ML Engineer / Mechanical Engineer), built with
**XeLaTeX** (MiKTeX on Windows). This is an independent git repository; the German version
lives in a separate project (`../cv-caipo-latex`).

The output is a 2-page PDF featuring a decorative topbar with gradient, a QR code
linking to a personal website, hyperlinked certificate references, and a profile photo.

---

## Project Structure

```
cv-caipo-latex-english/             # ENGLISH version (git repo)
├── .claude/                        # Claude Code config & docs (this folder)
├── main.tex                        # Main document — imports all sections
├── topbar_standalone.tex           # Topbar graphic source -> topbar_standalone.pdf
├── qr_standalone.tex               # QR code source -> qr_standalone.pdf
├── 0_personal_data.tex             # Name, contact info, photo, languages
├── 1_profile_summary.tex           # Professional summary paragraph
├── 2_experience.tex                # Work history (PROFESSIONAL EXPERIENCE)
├── 3_tech_skills.tex               # Technical skills (2-column layout)
├── 4_academic.tex                  # Education (Bachelor + Master)
├── 5_rewards.tex                   # Awards & honors
├── 6_recommendation.tex            # Professional references
├── 7_scholarship.tex               # Scholarships & grants
├── 8_courses.tex                   # Additional courses (2-column layout)
├── 9_publications.tex              # Academic publications
├── yaac-icons.sty                  # Custom icon package (FontAwesome social icons)
├── fonts/                          # SourceSansPro OTF files (NOT USED)
├── images/
│   ├── manuelcaipo.jpg             # Profile photo (optimized, ~38 KB)
│   └── manuelcaipo_old.jpg         # Old/previous profile photo
└── cv_links/                       # Supporting documents linked from the CV
```

## Build System

| Component     | Detail                                                    |
|---------------|-----------------------------------------------------------|
| Engine        | XeLaTeX (via MiKTeX on Windows)                           |
| Main font     | TeX Gyre Pagella (loaded via `fontspec`)                  |
| Icons         | FontAwesome (via custom `yaac-icons.sty`)                 |
| Decorations   | Pre-compiled PDFs: `topbar_standalone.pdf`, `qr_standalone.pdf` |
| Page hooks    | `\AddToHook{shipout/background}` for topbar + QR          |
| Structure     | Modular — `main.tex` uses `\input` for 10 section files   |

## Optimizations (also applied to German version)

- Topbar and QR are compiled once as standalone PDFs and embedded via `\includegraphics`
  (no `qrcode` / `shadings` packages in `main.tex` → faster compile, smaller PDF).
- Duplicate package loads removed (`xcolor`, `multirow`, `array`, ...).
- Profile photo compressed (2.3 MB → ~38 KB); final PDF ~85 KB.

## How to Compile

```bash
# Only when the topbar or QR changes:
xelatex -interaction=nonstopmode topbar_standalone.tex
xelatex -interaction=nonstopmode qr_standalone.tex

# CV (run twice to resolve hyperlinks/bookmarks):
xelatex -interaction=nonstopmode main.tex
```
