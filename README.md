# LPIC-2 Multilingual Training Kit

This repository hosts the LPIC-2 course: 32 lessons (1.5h each), engineer/live lab style. Slides are English-only.

- **Slides:** English-only (links in `docs/slides-links.md`).
- **Labs:** Markdown in `lessons/*` with dual-distro steps (Ubuntu 24.04 LTS & Rocky Linux 9).
- **Midterms:** Two × 30 minutes (not counted in course time).
- **Final Mock:** 60 questions, 90 minutes.

> Answers are kept on a protected branch `for-teachers` under `/answers` (not included here).

## Repos
This repo is part of a trio: `lpic2-course-en`, `lpic2-course-ru`, `lpic2-course-ro`.

## Build PDFs locally
```bash
# Requires pandoc
find lessons -name "*.md" -print0 | xargs -0 -I{} sh -c 'mkdir -p build/pdf/$(dirname {}); pandoc {} -o build/pdf/{}.pdf'
```

## License
CC BY-NC 4.0 for course text; CLI examples are public domain.
