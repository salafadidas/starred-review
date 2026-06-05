# Skill: Gstar

## Purpose
Review all GitHub starred repositories for a user and evaluate their relevance to active projects. Produces a structured live report with fit scores, pros/cons, and priority recommendations — then uploads the report to GitHub and optionally syncs to NotebookLM.

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
For every starred repo, fetch current metadata:
```
GET https://api.github.com/repos/{owner}/{repo}
GET https://api.github.com/repos/{owner}/{repo}/releases?per_page=3
Authorization: token {GITHUB_TOKEN}
```
Capture for each repo:
- `stargazers_count` — current star count → compute delta vs previous report
- `pushed_at` — last commit date → compute days_ago → 🟢 active (≤30d) / ⚪ inactive (>30d)
- Latest 3 release tags + dates + names
- Description changes indicating pivot or deprecation

Score adjustment rules (applied in Step 5):
- Inactive >60 days → score -5 to -10
- Star surge (>+1000 since last report) → score +2 to +5
- Author pivot to new project → flag + score -3 to -5
- Major new release since last report → score +2 to +3

**This step is MANDATORY on every Gstar run. Never skip live status checks.**

### Step 4: Identify Already-Integrated Repos
Cross-reference starred repos against:
- requirements.txt / package.json dependencies
- .mcp.json MCP server configs
- Fork relationships (repo.fork == true → check parent via /repos/{owner}/{repo})
- CLAUDE.md / AGENTS.md mentions
- Import statements in source files

For each match: assign fit score 0-100, document evidence, list pros/cons.
**Flag if integrated repo has gone inactive (>60 days no push) — evaluate replacement.**

### Step 5: Evaluate Non-Integrated Repos
For each non-integrated starred repo, evaluate against each active project:
- Relevance to tech stack and current project stage
- Gap it fills (what problem does it solve right now)
- Integration complexity (immediate / sprint / stage / long-term)
- Community maturity (live star count + last push from Step 3)
- Assign fit score 0-100, adjusted per live data rules in Step 3

### Step 6: Generate Report
```
STARRED_REVIEW_v{YYYYMMDD}.md
├── 專案宇宙概覽
├── PART 1: 已導入 repos (evidence + fit score + pros/cons + live activity)
├── PART 2A: 未導入 repos 全評估
├── PART 2B: Top 20 Priority repos (FULL table — reordered columns, see Step 7)
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
**After every Gstar run, render the complete Top 20 table directly in chat.**
Never require user to open the GitHub report.
Never use a simplified/summary table — always use the FULL column set in the exact order below.

**MANDATORY COLUMN ORDER (14 columns — reading flow: identity → activity → relevance → evidence → action):**

| 排名 | 狀態 | Repo | 當前 Stars | 星數成長 | 最後 Push | 建議導入專案 | 核心價值 | 契合度 | 優點 | 缺點/風險 | 重要更新內容 | 評分變化 | 建議行動 |
|------|------|------|-----------|---------|----------|-------------|----------|--------|------|-----------|------------|---------|---------|

**Column reading flow rationale:**
1. 排名        — 定位錨點，第一眼
2. 狀態        — 🟢/⚪ 緊接排名，即時活躍警示
3. Repo        — 識別對象
4. 當前 Stars  — 規模與可信度，緊接 Repo
5. 星數成長    — 趨勢動能，緊接 Stars
6. 最後 Push   — 活躍度細節，完成時間三角
7. 建議導入專案 — 對哪個專案有用
8. 核心價值    — 為什麼有用（主論述）
9. 契合度      — 量化評分
10. 優點       — 支撐評分的正面證據
11. 缺點/風險  — 平衡判斷的負面證據
12. 重要更新內容— 最新變化，影響當下決策
13. 評分變化   — 歷史趨勢（previous → current，附原因）
14. 建議行動   — 最後落地：做什麼、何時做

**Column content requirements:**
- **排名**: number with 🥇🥈🥉 for top 3
- **狀態**: 🟢 (pushed ≤30 days) or ⚪ (pushed >30 days)
- **Repo**: full repo name in bold (owner/repo)
- **當前 Stars**: live star count with comma formatting
- **星數成長**: delta vs previous report with arrows (e.g. +18 ↑↑ / +4 ↑ / = / -3 ↓)
- **最後 Push**: YYYY-MM-DD（relative, e.g. 今天 / 2天前 / 46天前）
- **建議導入專案**: which active project(s) (Pantheon / Aletheia / Pantheon + Aletheia / Stage N)
- **核心價值**: 1-2 sentences explaining value for this user's specific project context
- **契合度**: X/100 (live-adjusted per Step 3 rules)
- **優點**: 3-4 specific pros relevant to user's stack
- **缺點/風險**: 2-3 specific cons or risks
- **重要更新內容**: specific version numbers, feature changes, notable events since last report
- **評分變化**: "prev/100 → curr/100（±N，reason）" or "X/100 → X/100（持平，reason）"
- **建議行動**: concrete action + timing keyword (本週 / 下週 / Stage 2 前 / Stage 2 後 / Stage 3)

This full table must appear in EVERY Gstar output, including update-only runs.

### Step 8: Upload Report to GitHub
```
PUT https://api.github.com/repos/{username}/starred-review/contents/STARRED_REVIEW_v{YYYYMMDD}.md
{"message": "feat: Gstar v{YYYYMMDD}", "content": "{base64_content}"}
```
Use suffix (e.g. v20260605b) for same-day reruns. Never overwrite — always new versioned file.
Also update README.md to point to latest version.

### Step 9: Upload Updated SKILL.md
```
PUT https://api.github.com/repos/{username}/starred-review/contents/SKILL.md
{"message": "feat: update Gstar skill", "content": "{base64_content}", "sha": "{existing_sha}"}
```

### Step 10: NotebookLM Sync (if Aletheia available)
```bash
python main.py full
```
Otherwise: upload report MD to Google Drive manually, add as NotebookLM source.

---

## Output Format (Every Run — Non-Negotiable)

1. **Run summary** — total repos, new since last run, status changes, today's date
2. **⚠️ Key alerts** — inactive integrated repos, author pivots, major new releases
3. **PART 1 table** — integrated repos with live activity status
4. **PART 2B Top 20 FULL table** — all 14 columns in prescribed order, always in chat
5. **行動建議時程** — weekly action items

---

## Security Note
- GITHUB_TOKEN must be stored in .env (never hardcoded or pasted in chat)
- .env must be listed in .gitignore
- Regenerate token after any accidental exposure
- Minimum required scopes: repo (read+write), read:user

---

## Notes
- Re-run monthly or after starring 5+ new repos
- Version format: v{YYYYMMDD} + suffix for same-day reruns
- Previous report versions are always preserved — never overwrite
- Live GitHub API data always takes precedence over memory or cached data
- Score adjustments are cumulative across versions — track 評分變化 column for trend
