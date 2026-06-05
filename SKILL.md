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

### Step 3: Fetch Live Status for ALL Starred Repos (NEW — mandatory)
For every starred repo, fetch current metadata via:
```
GET https://api.github.com/repos/{owner}/{repo}
Authorization: token {GITHUB_TOKEN}
```
Capture for each repo:
- `stargazers_count` — current star count
- `pushed_at` — last commit date
- `updated_at` — last metadata update
- `description` — may have changed
- Latest release tag + date (via /releases?per_page=1)

Compare against previous report version to detect:
- Star count delta (growth signals relevance momentum)
- Last push recency (🟢 active = pushed within 30 days / ⚪ inactive = >30 days)
- New releases or major version bumps
- README/description changes indicating pivot or deprecation

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
- Relevance to tech stack
- Gap it fills
- Integration complexity
- Community maturity (live star count + last push date from Step 3)
- Assign fit score 0-100

Adjust scores based on live data:
- Active repo with star surge → score up
- Inactive repo (>60 days) → score down by 5-10 points
- Author pivoting to new project → flag and score down

### Step 6: Generate Report
Report structure (versioned by date):
```
STARRED_REVIEW_v{YYYYMMDD}.md
├── 專案宇宙概覽
├── PART 1: 已導入 repos (evidence + fit score + pros/cons + activity status)
├── PART 2A: 未導入 repos 全評估 (live stars + last push + fit score + impact)
├── PART 2B: Top 20 Priority repos (full recommendation table)
├── 更新訊號摘要 (star surges, new releases, inactive warnings)
└── 行動建議時程
```

Fit Score Guide:
- 90-100: Critical — integrate immediately
- 80-89: High — plan for current sprint
- 70-79: Medium — evaluate next quarter
- 60-69: Low — monitor, no action needed
- <60: Skip — not relevant to current projects

**PART 2B must always list Top 20 non-integrated repos** ranked by fit score, each with:
- Repo name + current live star count
- Recommended target project
- Core value statement
- Fit score (0-100) — adjusted from live data
- Pros (2-3 points)
- Cons/risks (2-3 points)
- Activity status (🟢 active / ⚪ inactive)
- Recommended action with timing

### Step 7: Always Output Top 20 Table in Chat (MANDATORY)
**After every Gstar run, always render the Top 20 table directly in the chat response.**
Do not require user to open the GitHub report to see the ranking.
Format:

| 排名 | Repo | ⭐ | 建議導入專案 | 核心價值 | 契合度 | 優點 | 缺點/風險 | 狀態 | 建議行動 |
|------|------|---|-------------|----------|--------|------|-----------|------|---------|
| 1 | ... | ... | ... | ... | .../100 | ... | ... | 🟢/⚪ | ... |

This table must appear in EVERY Gstar output, even for partial runs or update-only runs.

### Step 8: Upload Report to GitHub
```
# Create repo if not exists
POST https://api.github.com/user/repos
{"name": "starred-review", "description": "Starred repos review — versioned by date"}

# Upload new versioned report
PUT https://api.github.com/repos/{username}/starred-review/contents/STARRED_REVIEW_v{YYYYMMDD}.md
{"message": "feat: Gstar v{YYYYMMDD}", "content": "{base64_content}"}

# Update README to point to latest version
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

1. **Run summary** — total repos checked, new repos since last run, repos with status changes
2. **PART 1 table** — integrated repos with live activity status
3. **PART 2A table** — all non-integrated repos with live stars + last push
4. **⚠️ Update signals** — star surges, new releases, inactive warnings, author pivots
5. **PART 2B Top 20 table** — ALWAYS rendered in chat, ranked by live-adjusted fit score
6. **Timeline table** — weekly action items

---

## Security Note
- GITHUB_TOKEN must be stored in .env (never hardcoded or pasted in chat)
- .env must be listed in .gitignore
- Regenerate token after any accidental exposure
- Minimum required scopes: repo (read+write), read:user

---

## Notes
- Re-run this skill monthly or after starring 5+ new repos
- Version format: v{YYYYMMDD} — allows git history tracking of evaluation evolution
- For users with 100+ starred repos: paginate API calls, batch evaluate by topic cluster first
- Previous report versions are preserved in GitHub — never overwrite, always create new versioned file
- Live data from GitHub API always takes precedence over memory or previous report data
