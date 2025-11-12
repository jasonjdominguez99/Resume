# Resume & CV

My professional resume and CV, built with LaTeX and automatically deployed to GitHub Pages.

## Quick Links

- **Live Resume:** [View on GitHub Pages](https://jasonjdominguez99.github.io/Resume/)
- **Source Files:** [`src/`](./src/)
- **Latest Build:** Check the [Actions tab](../../actions) for build status

## Repository Structure

```
/
├── src/                      # LaTeX source files
│   ├── main.tex             # Resume/CV template
│   └── cover_letter.tex     # Cover letter template
├── build/                    # Generated PDFs (git-ignored)
├── .github/workflows/        # CI/CD automation
└── index.html               # GitHub Pages landing page
```

## How It Works

### Automated Deployment

Every push to `master` triggers a GitHub Actions workflow that:
1. Installs LaTeX dependencies
2. Compiles `src/main.tex` → `build/main.pdf`
3. Compiles `src/cover_letter.tex` → `build/cover_letter.pdf`
4. Deploys to GitHub Pages

**No manual PDF generation needed!** Just push your changes and the site updates automatically.

### Local Building

To build PDFs locally:

```bash
# Build resume
cd src && pdflatex -output-directory=../build main.tex && pdflatex -output-directory=../build main.tex && cd ..

# Build cover letter
cd src && pdflatex -output-directory=../build cover_letter.tex && pdflatex -output-directory=../build cover_letter.tex && cd ..

# View
open build/main.pdf  # macOS
```

## Workflow for Job Applications

### Master Branch: Generic CV
Keep your master branch with a generic, up-to-date CV and cover letter template.

### Application Branches: Job-Specific Customizations

For each job application, create a dedicated branch:

```bash
# Create application branch
git checkout -b applications/2025-11-12-company-position

# Customize src/main.tex and src/cover_letter.tex
# Make job-specific edits...

# Build locally
cd src && pdflatex -output-directory=../build main.tex && cd ..

# Commit your changes
git add src/
git commit -m "Customize for [Company] [Position]"

# Push (optional - will trigger build)
git push -u origin applications/2025-11-12-company-position
```

Extract `build/main.pdf` and `build/cover_letter.pdf` to submit with your application.

**Important:** Keep application branches as historical references. Never merge them back to master.

## Cover Letter Variables

The cover letter template supports customization via LaTeX variables:

```latex
\renewcommand{\position}{Software Engineer}
\renewcommand{\company}{Company Name}
\renewcommand{\team}{Team Name}  % Optional
```

Edit these in `src/cover_letter.tex` before building.

## Tech Stack

- **LaTeX:** Document typesetting
- **GitHub Actions:** CI/CD automation
- **GitHub Pages:** Static site hosting
- **pdflatex:** LaTeX compiler

## License

Personal resume repository - not for reuse without permission.
