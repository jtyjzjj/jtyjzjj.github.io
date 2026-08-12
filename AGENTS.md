# AGENTS.md

## Cursor Cloud specific instructions

### What this repo is

This repository is the **pre-built (generated) output of a Hexo blog** using the NexT.Muse theme (v5.1.4), i.e. the static site that gets deployed to GitHub Pages. It is **not** the Hexo source project: there is no `package.json`, `_config.yml`, `source/` markdown, or `themes/` directory here. Everything is already-rendered HTML/CSS/JS.

Implications:
- There is **nothing to build or install** — no package manager, no runtime dependencies, no backend, and no database.
- You **cannot** regenerate the site with `hexo generate`/`hexo server` here, because the Hexo source is absent. Edit the rendered files directly if you must change content/markup.

### Running the site (development)

Serve the repo root as web root with any static file server. The pages use absolute root paths (`/css/main.css`, `/lib/...`, `/js/...`), so the server **must** be rooted at the repo root, not a subfolder:

```bash
python3 -m http.server 8080   # then open http://localhost:8080/
```

Key routes: `/` (home), `/2018/01/21/hello-world/` (the one blog post), `/archives/`, `/tags/{maven,POM,项目管理}/`.

### Notes / gotchas

- Opening `index.html` via `file://` renders incompletely because of the absolute asset paths — always serve over HTTP.
- Some referenced third-party scripts (Baidu Analytics `hm.baidu.com`, Duoshuo comments, Algolia search) require internet/CDN access and/or unset config; they are inert and do not affect core rendering. The site renders fully offline without them.
- Content is Chinese (`lang="zh-Hans"`); Chrome may show a translate prompt — that is expected browser behavior, not a site issue.
