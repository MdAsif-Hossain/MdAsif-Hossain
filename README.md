# CLAUDE.md

Guidance for Claude Code when working in this directory.

## What this repo is

The source for **Md. Asif Hossain's GitHub profile README** — the file that renders at
`github.com/MdAsif-Hossain`. There is no application code, no build step, and no test
suite. The only deliverable is Markdown that renders correctly on github.com.

| File | Role |
|---|---|
| `readme.md` | **The profile README.** This is the live file — edit this one. |
| `README_RECRUITER.md` | Earlier recruiter-focused draft. Kept as reference for project copy/metrics. Not rendered anywhere. |
| `.github/workflows/snake.yml` | GitHub Action that generates the contribution-snake SVGs into the `output` branch. |
| `CLAUDE.md` | This file. |

> To go live, the file must land in a repo named `MdAsif-Hossain/MdAsif-Hossain` as
> `README.md` at the root. GitHub matches the name case-insensitively, so `readme.md`
> works, but prefer `README.md` when pushing.

## Facts about the owner (do not change without being told)

- **Name:** Md. Asif Hossain — **GitHub:** `MdAsif-Hossain`
- **Title:** AI/ML Engineer — generative AI, LLM/agent systems, RAG, computer vision
- **Education:** B.Sc. Computer Science & Engineering, East West University, Dhaka. Expected **December 2026**.
- **Certifications:** Machine Learning Specialization (DeepLearning.AI / Stanford Online, 2025); Google Data Analytics Professional Certificate (Google, 2024)
- **Languages:** Bengali (native), English (C1), German (A1)
- **Links:** [LinkedIn](https://linkedin.com/in/md-asifhossain20) · <asifhossain8612@gmail.com> · [Kaggle](https://kaggle.com/sabuktagin)
- **Goal:** international AI/ML engineering roles and research collaborations

### Deliberately excluded

**Competitive programming is out.** The owner is inactive on LeetCode, Codeforces,
CodeChef, HackerRank, and HackerEarth. Do not re-add that section or those badges,
even though they appear in git history and in older drafts.

## The four featured projects

Real repos, real numbers. Reuse these figures verbatim — never invent new metrics.

| Project | Repo | Headline facts |
|---|---|---|
| Leo AI Tutor | `Multi-Agent-AI-Tutor` | 4 collaborating CrewAI agents, typed handoffs, 10 automated tests, API-key-free preview |
| BD Knowledge Agent | `BD-Knowledge-Agent` | 3 databases / 86,490 records, SELECT-only SQL guardrails, search fallback |
| BERT Question Answering | `Fine-Tuning-Transformers-for-Question-Answering` | SQuAD v1.1, sliding windows, official EM/F1 |
| People Flow Detection | `People-Flow-Detection-using-Object-Tracking-Heatmap-Visualization` | YOLOv8 + ByteTrack, IN/OUT counting, ~13 FPS on CPU |

## Design system

Keep these constant so the page reads as one thing:

- **Accent gradient:** `#0EA5E9` (sky) → `#6366F1` (indigo) → `#A855F7` (violet)
- **Primary accent text:** `#22D3EE` · **secondary:** `#A78BFA` · **success chip:** `#10B981`
- **Card background:** `#0D1117` · **card text:** `#C9D1D9` · **card theme:** `tokyonight`
- **Fonts in generated SVGs:** `JetBrains+Mono`
- **Badge style:** `for-the-badge` for calls to action, `flat-square` for informational chips

### Animation / dynamic services in use

| Service | Used for |
|---|---|
| `capsule-render.vercel.app` | Waving gradient header and footer banners |
| `readme-typing-svg.demolab.com` | Animated headline typing effect |
| `skillicons.dev` | Tech-stack icon grids (`&perline=` controls wrapping) |
| `github-readme-stats-git-masterrstaa-rickstaa.vercel.app` | Stats + top-languages cards (community mirror — used because the canonical instance rate-limits) |
| `streak-stats.demolab.com` | Contribution streak card |
| `github-readme-activity-graph.vercel.app` | Contribution line graph |
| `komarev.com/ghpvc` | Profile view counter |
| `Platane/snk` (Action) | Contribution snake, published to the `output` branch |

**Known dead:** `github-profile-trophy.vercel.app` returned HTTP 402 (quota exhausted) as of
the last check, so the trophy row was removed. Don't re-add it without curling the URL first.

**Valid shields logo slugs used here:** `linkedin`, `gmail`, `kaggle`, `github`, `googlemaps`,
`handshake`, `minutemailer`, `langchain`, `huggingface`, `pydantic`, `sqlite`, `streamlit`,
`fastapi`, `docker`, `pytorch`, `googlecolab`, `yolo`, `opencv`, `python`. There is **no**
`graduationcap` slug — that badge uses a 🎓 emoji in the label instead.

## Rules when editing

1. **Never fabricate.** No invented metrics, employers, job titles, stars, or repos. Every
   number must trace back to the table above or to something the owner stated.
2. **Both themes must work.** GitHub renders on light and dark. Wrap theme-sensitive images in
   `<picture>` with `prefers-color-scheme` sources, and give every `<img>` a real `alt`.
3. **HTML must stay GitHub-safe.** GitHub's Markdown sanitizer strips `<style>`, `<script>`,
   CSS classes, and inline `style` attributes. Layout comes from `<table>`, `<div align>`,
   `width`/`height` attributes, and `<details>` — nothing else.
4. **Blank line before Markdown inside HTML.** A `<div>` wrapping Markdown needs an empty
   line after the opening tag or the Markdown renders as literal text.
5. **URL-encode capsule-render text.** Spaces → `%20`, `/` → `%2F`, `·` → `%C2%B7`, `&` → `%26`.
6. **Budget the images, and curl before you commit.** Every dynamic SVG is a third-party
   request that can be slow or dead. Stay near the current count; if adding one, consider
   dropping one. Verify any new or changed image URL with
   `curl -s -o /dev/null -w '%{http_code} %{content_type}' -L "<url>"` — expect `200` and an
   image content type. Shields returns `200` even for an unknown `logo=` slug (it just drops
   the icon), so also confirm the SVG body contains an `<image` element.
7. **Recruiter-first ordering.** Who he is → proof of work (projects) → stack → credentials →
   activity stats. Vanity metrics never outrank projects.
8. **Keep it scannable.** A recruiter gives this ~30 seconds. Short lines, strong headings,
   collapse depth into `<details>`.

## Verifying a change

There is nothing to run locally. To check work:

- Paste the file into a GitHub gist or a scratch repo's README and view the rendered result.
- Open each dynamic image URL directly in a browser to confirm it returns an image, not an
  error page.
- Check the render in both GitHub light and dark themes.
