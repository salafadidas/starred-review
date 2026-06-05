# Skill: Gstar

## Purpose
Review all GitHub starred repositories for a user and evaluate their relevance to active projects. Produces a structured report with fit scores, pros/cons, and priority recommendations — then uploads the report to GitHub and optionally syncs to NotebookLM.

## When to Use This Skill
Trigger when user says any of:
- "gstar"
- "run gstar"
- "gstar 分析"
- "review my starred repos"
- "幫我看我打星的 GitHub 專案"
- "evaluate my GitHub stars against my projects"

## Prerequisites
- GitHub Personal Access Token (stored in .env as GITHUB_TOKEN)
- User's GitHub username
- Context of user's active projects (repo names, tech stack, goals)

---

## Step-by-Step Execution

### Step 1: Fetch Active Projects (LIVE — every run)
```
GET https://api.github.com/users/{username}/repos?per_page=100
Authorization: token {GITHUB_TOKEN}
```
For each repo: read CLAUDE.md, AGENTS.md, requirements.txt, .mcp.json to understand current tech stack and integrations.
**Do NOT rely on cached or memory data — always fetch live from GitHub API.**

### Step 2: Fetch All Starred Repos (LIVE — every run)
```
GET https://api.github.com/users/{username}/starred?per_page=100&page=1
Authorization: token {GITHUB_TOKEN}
```
Repeat with page=2, 3... until response length < 100.
**Always paginate fully. Total count must match GitHub profile starred count.**

### Step 3: Fetch Live Status for ALL Starred Repos (MANDATORY — every run)
For every starred repo, fetch current metadata via:
```
GET https://api.github.com/repos/{owner}/{repo}
Authorization: token {GITHUB_TOKEN}
```
Capture for each repo:
- `stargazers_count` — current star count
- `pushed_at` — last commit date → compute days_ago → 🟢 active (≤30 days) / ⚪ inactive (>30 days)
- Latest release tag + date (via /releases?per_page=3)
- README/description changes indicating pivot or deprecation

Compare against previous report version to compute:
- Star count delta (growth signals relevance momentum)
- Score adjustment: active🟢 = base score; inactive >60 days = -5 to -10; star surge >+1000 = +2 to +5
- Flag: newly integrated, newly inactive, author pivot, major new release

**This step is MANDATORY on every Gstar run. Never skip live status checks.**

### Step 4: Identify Already-Integrated Repos
Cross-reference starred repos against:
- requirements.txt / package.json dependencies
- .mcp.json MCP server configs
- Fork relationships (repo.fork == true → check parent via /repos/{owner}/{repo})
- CLAUDE.md / AGENTS.md mentions
- Import statements in source files

For each match: assign fit score 0-100, document evidence, list pros/cons.
**Also flag if integrated repo has gone inactive (>60 days no push) — evaluate replacement.**

### Step 5: Evaluate Non-Integrated Repos
For each non-integrated starred repo, evaluate against each active project:
- Relevance to tech stack and current project stage
- Gap it fills (what problem does it solve right now)
- Integration complexity (immediate / sprint / stage / long-term)
- Community maturity (live star count + last push date from Step 3)
- Assign fit score 0-100, adjusted from live data

### Step 6: Generate Report
Report structure (versioned by date):
```
STARRED_REVIEW_v{YYYYMMDD}.md
├── 專案宇宙概覽
├── PART 1: 已導入 repos (evidence + fit score + pros/cons + live activity status)
├── PART 2A: 未導入 repos 全評估 (live stars + last push + fit score + impact)
├── PART 2B: Top 20 Priority repos (FULL table — all columns, see spec below)
├── 更新訊號摘要 (star surges, new releases, inactive warnings, author pivots)
└── 行動建議時程
```

Fit Score Guide:
- 90-100: Critical — integrate immediately
- 80-89: High — plan for current sprint
- 70-79: Medium — evaluate next quarter
- 60-69: Low — monitor, no action needed
- <60: Skip — not relevant to current projects

### Step 7: Always Output Full Top 20 Table in Chat (MANDATORY)
**After every Gstar run, always render the complete Top 20 table directly in the chat response.**
Do NOT require user to open the GitHub report to see the ranking.
Do NOT output a simplified/summary table — always use the FULL column set below.

**MANDATORY FULL TABLE FORMAT:**

| 排名 | Repo | 建議導入專案 | 核心價值 | 契合度 | 優點 | 缺點/風險 | 建議行動 | 當前 Stars | 星數成長 | 最後 Push | 重要更新內容 | 評分變化 | 狀態 |
|------|------|-------------|----------|--------|------|-----------|---------|-----------|---------|----------|------------|---------|------|

Column definitions:
- **排名**: rank number with medal emoji for top 3
- **Repo**: full repo name in bold
- **建議導入專案**: which active project(s) to integrate into
- **核心價值**: 1-2 sentences explaining the key value proposition for this user's specific project context
- **契合度**: fit score X/100 (live-adjusted)
- **優點**: 3-4 specific pros relevant to this user's stack
- **缺點/風險**: 3 specific cons or risks
- **建議行動**: concrete action with timing (本週 / Stage 2 前 / Stage 2 後 / Stage 3)
- **當前 Stars**: live star count with comma formatting
- **星數成長**: delta vs previous report with arrow (e.g. +18 ↑↑ / = / -3 ↓)
- **最後 Push**: date + relative (e.g. 2026-06-05（今天）/ 2026-04-20（46天前）)
- **重要更新內容**: specific version numbers, feature changes, or notable events since last report
- **評分變化**: previous score → current score with reason (e.g. 78/100 → 88/100（+10，星數暴增+34k + v2.5 大改版）)
- **狀態**: 🟢 (active ≤30 days) or ⚪ (inactive >30 days)

This full table must appear in EVERY Gstar output, including update-only runs.
Never abbreviate or simplify — users rely on this table for decision-making.

### Step 8: Upload Report to GitHub
```
# Create repo if not exists
POST https://api.github.com/user/repos
{"name": "starred-review", "description": "Starred repos review — versioned by date"}

# Upload new versioned report (never overwrite, always new version)
PUT https://api.github.com/repos/{username}/starred-review/contents/STARRED_REVIEW_v{YYYYMMDD}.md
{"message": "feat: Gstar v{YYYYMMDD}", "content": "{base64_content}"}

# Update README to point to latest
PUT https://api.github.com/repos/{username}/starred-review/contents/README.md
{"message": "docs: update README to v{YYYYMMDD}", "content": "{base64_content}", "sha": "{existing_sha}"}
```

### Step 9: Upload Updated SKILL.md
```
PUT https://api.github.com/repos/{username}/starred-review/contents/SKILL.md
{"message": "feat: update Gstar skill", "content": "{base64_content}", "sha": "{existing_sha}"}
```

### Step 10: NotebookLM Sync (if Aletheia available)
If user has Aletheia running:
```bash
python main.py full   # Aletheia CLI: sync Notion + ingest + push to Google Drive
```
Otherwise: upload report MD to Google Drive manually, then add as NotebookLM source.

---

## Output Format (Every Run — Non-Negotiable)

Every Gstar run MUST produce ALL of the following in the chat response:

1. **Run summary header** — total repos checked, new repos since last run, repos with status changes, today's date
2. **⚠️ Key alerts** — openmemory-style warnings, author pivots, major new releases
3. **PART 1 table** — integrated repos with live activity status
4. **PART 2B Top 20 FULL table** — ALL 14 columns, always rendered in chat
5. **行動建議時程** — weekly action items

---

## Security Note
- GITHUB_TOKEN must be stored in .env (never hardcoded or pasted in chat)
- .env must be listed in .gitignore
- Regenerate token after any accidental exposure
- Minimum required scopes: repo (read+write), read:user

---

## Notes
- Re-run this skill monthly or after starring 5+ new repos
- Version format: v{YYYYMMDD} + suffix (e.g. v20260605b) for same-day reruns
- Previous report versions are preserved in GitHub — never overwrite, always create new versioned file
- Live data from GitHub API always takes precedence over memory or previous report data
- Score adjustments are cumulative across versions — track score_change column for trend
