# TSS Sales Rep: changes from upstream

Based on [zubair-trabzada/ai-sales-team-claude](https://github.com/zubair-trabzada/ai-sales-team-claude) at commit `efef8b8` (MIT license, kept in `LICENSE`).

## Fixes
- **TLS verification turned back on**: `scripts/analyze_prospect.py` and `scripts/contact_finder.py` had `check_hostname = False` and `CERT_NONE`, which removed HTTPS certificate checks when scraping prospect sites.
- **Skill and agent headers**: none of the 14 `SKILL.md` files or the 5 agent files had the YAML frontmatter (`name`, `description`) Claude Code uses to discover them. Added it to all of them.
- **Installer**:
  - No longer clones the upstream repo when piped from curl. It installs only from this local copy, so you get the fixed files.
  - New `--project DIR` option installs into `DIR/.claude/` instead of `~/.claude/`.
  - Installs `reportlab` and `beautifulsoup4` from `requirements.txt` (user-level) when they're missing, instead of only warning.

## Install
```bash
git clone <this repo> && cd <this repo>
./install.sh                       # for your user (~/.claude)
./install.sh --project ~/work/tss  # or just for one project folder
```

## Still to do for TSS
- Build the TSS ideal customer profile (`/sales icp`) and bake it into the scoring.
- Rewrite `templates/` (outreach, proposal, objections, meeting prep) for Total Stream Systems' offer, pricing, and proof points.
