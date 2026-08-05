# CLAUDE.md

Guidance for Claude Code when working in this directory.

## What this repo is

The source for **Md. Asif Hossain's GitHub profile README** — the file that renders at
`github.com/MdAsif-Hossain`. There is no application code, no build step, and no test
suite. The only deliverable is Markdown that renders correctly on github.com.

| File | Role |
|---|---|
| `readme.md` | **The profile README.** This is the live file — edit this one. |
| `README_RECRUITER.md` | Earlier draft (written by another tool). Kept only as a copy reference. Several of its image URLs are dead — do not copy them forward. |
| `.github/workflows/snake.yml` | GitHub Action that generates the contribution-snake SVGs into the `output` branch. |
| `CLAUDE.md` | This file. |

> To go live, the file must land in a repo named `MdAsif-Hossain/MdAsif-Hossain` as
> `README.md` at the root. GitHub matches the name case-insensitively, so `readme.md`
> works, but prefer `README.md` when pushing.

## Facts about the owner (do not change without being told)

- **Name:** Md. Asif Hossain — **GitHub:** `MdAsif-Hossain`
- **Title:** AI/ML Engineer — LLM & agent systems, RAG, computer vision
- **Education:** B.Sc. Computer Science & Engineering, East West University, Dhaka. Final year, expected **December 2026**.
- **Certifications:** Machine Learning Specialization (DeepLearning.AI / Stanford Online, 2025); Google Data Analytics Professional Certificate (Google, 2024)
- **Languages:** Bengali (native), English (C1), German (A1)
- **Links:** [LinkedIn](https://linkedin.com/in/md-asifhossain20) · <asifhossain8612@gmail.com> · [Kaggle](https://kaggle.com/sabuktagin)
- **Goal:** AI/ML engineering roles, internships, and research collaborations
- **Timezone:** Asia/Dhaka (UTC+6)

### Deliberately excluded

**Competitive programming is out.** The owner is inactive on LeetCode, Codeforces,
CodeChef, HackerRank, and HackerEarth. Do not re-add that section or those badges.

**Named projects are out — for now.** The owner does not want specific repositories
featured yet. The README sells *capabilities* ("What I build") and *engineering
discipline* ("How I work") instead, and links to the repositories tab generically.
Do not add project cards, repo pins, or per-project metrics unless he asks.

<details>
<summary>Project facts on file, for when he does want them shown</summary>

| Project | Repo | Headline facts |
|---|---|---|
| Leo AI Tutor | `Multi-Agent-AI-Tutor` | 4 collaborating CrewAI agents, typed handoffs, 10 automated tests, API-key-free preview |
| BD Knowledge Agent | `BD-Knowledge-Agent` | 3 databases / 86,490 records, SELECT-only SQL guardrails, search fallback |
| BERT Question Answering | `Fine-Tuning-Transformers-for-Question-Answering` | SQuAD v1.1, sliding windows, official EM/F1 |
| People Flow Detection | `People-Flow-Detection-using-Object-Tracking-Heatmap-Visualization` | YOLOv8 + ByteTrack, IN/OUT counting, ~13 FPS on CPU |

These numbers are real. Reuse them verbatim if the section is ever restored — never invent new ones.

</details>

## Design system

Keep these constant so the page reads as one thing:

- **Accent gradient:** `#0EA5E9` (sky) → `#6366F1` (indigo) → `#A855F7` (violet)
- **Primary accent text:** `#22D3EE` · **secondary:** `#A78BFA` · **success chip:** `#10B981`
- **Card background:** `#0D1117` · **card text:** `#C9D1D9` · **card theme:** `tokyonight`
- **Fonts in generated SVGs:** `JetBrains+Mono`
- **Badge style:** `for-the-badge` for calls to action, `flat-square` for informational chips
- **Section rhythm:** gradient `type=rect&height=3` divider between major sections

## ⚠️ Third-party image services: verified status

Every dynamic image is a third-party request. **Most of the popular ones are dead.**
Status below was established by direct probing — re-verify before trusting it again.

### Working (confirmed live, responds to uncached URLs)

| Service | Used for |
|---|---|
| `img.shields.io` | All badges and chips. Rock solid. |
| `capsule-render.vercel.app` | Waving gradient header/footer, `type=rect` dividers |
| `readme-typing-svg.demolab.com` | Animated headline typing effect |
| `skillicons.dev` | Tech-stack icon grids (`&perline=` controls wrapping) |
| `streak-stats.demolab.com` | Contribution streak card — serves fresh, uncached responses |
| `komarev.com/ghpvc` | Profile view counter |
| `Platane/snk` (Action) | Contribution snake → `output` branch |

### Dead — do not use

| Service | Failure |
|---|---|
| `github-readme-stats.vercel.app` | HTTP 503 `DEPLOYMENT_PAUSED` |
| `github-readme-stats-git-masterrstaa-rickstaa.vercel.app` | Deployment removed; returns a 480 KB Vercel HTML page, not an SVG. **This is what was rendering broken in the old READMEs.** |
| `github-profile-summary-cards.vercel.app` | HTTP 500 `FUNCTION_INVOCATION_FAILED` on every card |
| `github-profile-trophy.vercel.app` | HTTP 402 — quota exhausted |
| `github-readme-activity-graph.vercel.app` | **Cache-only.** Serves a previously-cached URL fine, but any URL it hasn't cached returns a 630-byte error card reading "Can't fetch any contribution. Please check your username 😬". Every light theme currently fails. Too fragile to ship. |

### Icon/logo gotchas found by probing

- **`logo=linkedin` no longer exists** in simple-icons (trademark removal). The badge silently
  renders with no icon and a grey `#555` left half. The README works around this with an inline
  base64 `data:image/svg%2Bxml` LinkedIn logo — that URL is ~900 chars, which is expected; don't
  "clean it up". Note `svg+xml` must be written `svg%2Bxml` or the `+` decodes to a space.
- **`logo=graduationcap` and `logo=openai` do not exist.** The graduation chip uses a 🎓 emoji
  in the label instead.
- **skillicons slugs that render as blank squares:** `streamlit`, `kaggle`, `huggingface`,
  `langchain`. Use a shields badge for those instead.
- **Verified-good skillicons slugs:** `python pytorch tensorflow sklearn opencv anaconda fastapi
  django nodejs nestjs react nextjs ts js tailwind postgres mongodb mysql sqlite docker firebase
  git github githubactions linux vscode java c cpp flask redis`

## Rules when editing

1. **Never fabricate.** No invented metrics, employers, job titles, stars, or repos.
2. **Verify every image URL before committing.** This is the whole ballgame — broken cards are
   why the previous versions were rejected. Run the sweep below and require 100% OK.
3. **Both themes must work.** GitHub renders on light and dark. Wrap theme-sensitive images in
   `<picture>` with `prefers-color-scheme` sources, and give every `<img>` a real `alt`.
   If a light-theme variant of a service is broken, drop the whole card — never ship a
   `<picture>` whose light source is an error image.
4. **HTML must stay GitHub-safe.** GitHub's Markdown sanitizer strips `<style>`, `<script>`,
   CSS classes, and inline `style` attributes. Layout comes from `<table>`, `<div align>`,
   `width`/`height` attributes, and `<details>` — nothing else.
5. **Blank line before Markdown inside HTML.** A `<div>` wrapping Markdown needs an empty
   line after the opening tag or the Markdown renders as literal text.
6. **URL-encode capsule-render text.** Spaces → `%20`, `/` → `%2F`, `·` → `%C2%B7`, `&` → `%26`.
7. **`<h2>` gets a border-bottom on GitHub.** Never use `<h2>` inside a table cell or directly
   under a divider — use `<h3>`.
8. **Prefer zero-dependency visuals.** The `█░` bar block and the `yaml` profile block render
   from text alone and can never break. Reach for those before adding another remote SVG.
9. **Recruiter-first ordering.** Positioning → what he can build → how he works → stack →
   credentials → activity → contact.

## Verifying a change

There is nothing to run locally, but **do run this sweep** — it extracts every image URL from
the README, cache-busts it, and fails anything that isn't a real SVG. It caught five dead
services and four blank icons that had shipped in earlier drafts.

```bash
cd "e:/my md" && python - <<'PY'
import io, re, subprocess, sys, os, tempfile
sys.stdout.reconfigure(encoding="utf-8", errors="replace")
s = io.open("readme.md", encoding="utf-8").read()
live = re.sub(r"<!--.*?-->", "", s, flags=re.S)          # skip commented-out blocks
urls  = re.findall(r'(?:src|srcset)="(https?://[^"]+)"', live)
urls += re.findall(r'!\[[^\]]*\]\((https?://[^)]+)\)', live)
seen, out = set(), []
for u in urls:
    if u not in seen: seen.add(u); out.append(u)
tmp = os.path.join(tempfile.gettempdir(), "p.bin"); bad = []
for u in out:
    bust = u + ("&" if "?" in u else "?") + "cbz=91"     # defeat server-side caching
    r = subprocess.run(["curl","-s","-o",tmp,"-w","%{http_code}|%{content_type}",
                        "-L","--max-time","45",bust], capture_output=True, text=True).stdout.strip()
    code, ctype = (r.split("|") + ["",""])[:2]
    size = os.path.getsize(tmp) if os.path.exists(tmp) else 0
    body = open(tmp,"rb").read().decode("utf8","replace") if size else ""
    err  = re.search(r"Can't fetch|went wrong|Error|not found|DEPLOYMENT", body, re.I)
    ok = code=="200" and "image/svg" in ctype and size>400 and "<svg" in body and not err
    if not ok: bad.append(u)
    print(f"{'OK ' if ok else 'BAD'} {code} {size:>7}b  {re.sub(r'^https?://','',u).split('?')[0][:50]}")
print(f"\n=== {len(out)-len(bad)} OK / {len(bad)} BAD ===")
PY
```

To check a shields logo slug actually embeds an icon (shields returns HTTP 200 even for an
unknown slug, silently dropping the icon):

```bash
curl -s "https://img.shields.io/badge/a-b-blue?logo=SLUG" | grep -c "<image"   # 1 = good, 0 = no icon
```

To check a skillicons slug isn't a blank square — a valid icon is well over 400 bytes, a
missing one returns exactly 256:

```bash
curl -s "https://skillicons.dev/icons?i=SLUG" | wc -c
```

Finally, view the render in both GitHub light and dark themes before calling it done.
