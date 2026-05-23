# Skill: GitHub Starred Repos Review

## Purpose
Review all GitHub starred repositories for a user and evaluate their relevance to active projects. Produces a structured report with fit scores, pros/cons, and priority recommendations — then uploads the report to GitHub and optionally syncs to NotebookLM.

## When to Use This Skill
Trigger when user says any of:
- "review my starred repos"
- "幫我看我打星的 GitHub 專案"
- "evaluate my GitHub stars against my projects"
- "starred repos 分析"
- "一鍵 GitHub starred review"

## Prerequisites
- GitHub Personal Access Token (read + write repo scope)
- User's GitHub username
- Context of user's active projects (repo names, tech stack, goals)

## Step-by-Step Execution

### Step 1: Fetch Active Projects
```
GET https://api.github.com/users/{username}/repos?per_page=100
Authorization: token {TOKEN}
```
For each repo: read CLAUDE.md, AGENTS.md, requirements.txt, .mcp.json to understand current tech stack and integrations.

### Step 2: Fetch All Starred Repos
```
GET https://api.github.com/users/{username}/starred?per_page=100&page=1
Authorization: token {TOKEN}
```
Repeat with page=2, 3... until response length < 100.

### Step 3: Identify Already-Integrated Repos
Cross-reference starred repos against:
- requirements.txt / package.json dependencies
- .mcp.json MCP server configs
- Fork relationships (repo.fork == true → check parent)
- CLAUDE.md / AGENTS.md mentions
- Import statements in source files

For each match: assign fit score 0-100, document evidence, list pros/cons.

### Step 4: Evaluate Non-Integrated Repos
For each non-integrated starred repo, evaluate against each active project:
- Relevance to tech stack
- Gap it fills
- Integration complexity
- Community maturity (stars, recent commits)
- Assign fit score 0-100

### Step 5: Generate Report
Report structure (versioned by date):
```
STARRED_REVIEW_v{YYYYMMDD}.md
├── 專案宇宙概覽
├── PART 1: 已導入 repos (with evidence + fit score + pros/cons)
├── PART 2A: 未導入 repos 全評估 (fit score + impact table)
├── PART 2B: Top 5 Priority repos (full recommendation table)
└── 行動建議時程
```

Fit Score Guide:
- 90-100: Critical — integrate immediately
- 80-89: High — plan for current sprint
- 70-79: Medium — evaluate next quarter
- 60-69: Low — monitor, no action needed
- <60: Skip — not relevant to current projects

### Step 6: Upload to GitHub
```
# Create repo if not exists
POST https://api.github.com/user/repos
{"name": "starred-review", "description": "Starred repos review — versioned by date"}

# Upload report
PUT https://api.github.com/repos/{username}/starred-review/contents/STARRED_REVIEW_v{YYYYMMDD}.md
{"message": "feat: add starred repos review v{YYYYMMDD}", "content": "{base64_content}"}
```

### Step 7: Upload SKILL.md to repo
```
PUT https://api.github.com/repos/{username}/starred-review/contents/SKILL.md
{"message": "feat: add skill definition", "content": "{base64_skill_content}"}
```

### Step 8: NotebookLM Sync (if Aletheia available)
If user has Aletheia running:
```bash
# Upload to Google Drive for NotebookLM ingestion
python main.py sync  # Aletheia CLI
```
Otherwise: upload report MD to Google Drive manually, then add as NotebookLM source.

## Output Format

Always produce:
1. **PART 1 table** — integrated repos with evidence column
2. **PART 2A table** — all non-integrated repos, two columns per active project
3. **PART 2B table** — Top 5 priority with action column
4. **Timeline table** — weekly action items

## Notes
- Token should be revoked and regenerated after each session (security)
- Re-run this skill monthly or after starring 5+ new repos
- Version format: v{YYYYMMDD} — allows git history tracking of evaluation evolution
- For users with 100+ starred repos: paginate API calls, batch evaluate by topic cluster first

