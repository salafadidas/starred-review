# Starred Review v20260823

> Generated: 2026-08-23 · Live GitHub API data only, no caching
> Total starred: **125**（pagination: page1=100, page2=25, page3=0 → 100+25=125）
> Relevant scored: 125（6 已導入 + 119 未導入全評估，Top 20 見 Part 2B）
> Previous report: `STARRED_REVIEW_v20260622.md`（total starred 96 → 淨增 +29，成長 30.2%）

---

## 專案宇宙概覽

- **Pantheon**：LangGraph multi-agent（FastAPI + LangGraph + Redis + Telegram Bot）· GitNexus code intelligence 已內建 CLAUDE.md 標準流程 · branch `claude/remote-control-Q2YAQ`
- **Aletheia**：FastAPI + LiteLLM(Haiku 4.5 ingest / Sonnet 4.6 query) + Notion ingestion · Karpathy LLM Wiki pattern · REST API 供 Pantheon 呼叫
- **Raphael**：基於 Hermes Agent 的個人全知顧問 AI（只建議、不執行）· `~/.hermes/` 已安裝
- **agent-config**：共用 skills/agents 設定 SSOT（Gstar、eSystem 兩個 reusable skill 的來源 repo）
- **starred-review**：本 repo，稽核與雷達層

⚠️ **專案宇宙變動偵測**：`ecosystem-blueprint` 的 CLAUDE.md 顯示其治理角色已於 2026-08-06 由 Human Project Owner 核准轉為 **Terminal / Complete**，目前唯一 Active Portfolio Item 變更為 `ai-engineering-os`（不在本次 Gstar 追蹤的五個 active project 清單內）。這是專案宇宙層級的真實 pivot，非本次評分調整範圍 — 是否要將 `ai-engineering-os` 併入下次 Gstar 追蹤清單，需 Human 決策（見「未解風險」）。

---

## PART 1 — 已導入 repos（live activity + evidence + fit score + pros/cons）

> **本次分類修正**：`crewAIInc/crewAI`、`anthropics/skills`、`google/skills`、`mattpocock/skills` 四個 repo 在 v20260622 報告中被列為「已導入」，但本次依 SKILL.md Step 4 標準（requirements.txt / .mcp.json / CLAUDE.md 明確引用 / fork 關係）重新檢視 project-pantheon、Aletheia、raphael、agent-config 四個 repo 的 CLAUDE.md 與 requirements.txt，**均未找到直接證據**。已將其移至 PART 2A/2B 重新評估為「未導入」，並在下方各自的評分變化欄位註記。

| Repo | 現況 | ⭐ 當前 | 最後 Push | 契合度 | 證據 |
|------|------|--------|----------|--------|------|
| `langchain-ai/langgraph` | 🟢 已導入 | 40,272 | 今天 | 100/100 | Pantheon `requirements.txt`：langgraph, langgraph-checkpoint-postgres, langchain-core 等 |
| `NousResearch/hermes-agent` | 🟢 已導入 | 234,606 | 今天 | 86/100 | Raphael `CLAUDE.md`：「基於 Hermes Agent 的個人全知顧問 AI」、`~/.hermes/` 安裝路徑 |
| `abhigyanpatwari/GitNexus` | 🟢 已導入 | 45,685 | 2天前 | 76/100 | Pantheon `CLAUDE.md` 內建完整 gitnexus MCP 工作流程區塊；本 session 內 gitnexus-* skill 實際可用 |
| `thedotmack/claude-mem` | 🟢 已導入 | 91,568 | 2天前 | 84/100 | 本 session 可用 skill 清單含 `claude-mem:babysit`/`do`/`mem-search` 等，已從 PoC 候選升級為使用中工具 |
| `upstash/context7` | 🟢 已導入 | 61,101 | 2天前 | 64/100 | 本 session `docs-lookup` agent 與 `docs` skill 均直接呼叫 Context7 MCP |
| `vancelin/openmemory` | ⚪ ⚠️ 建議除役 | 106 | **144天前** | —/100 | 前次報告已列整合但活躍度低落（81天）；本次惡化至144天，且 claude-mem 替代方案已完成並上線 |

### langchain-ai/langgraph — 100/100
- **優點**：官方持續維護、與 AsyncPostgresStore/Saver 原生整合、三模型 ensemble（claude-sonnet/gpt-4o/gemini-2.5-pro）相容、5-node graph（pm_router→researcher→debater→voter→synthesizer）已運作
- **缺點/風險**：API 版本更新快，需持續追蹤 breaking change；與 langmem 的記憶分工需持續協調
- **重要更新**：`langgraph-sdk` 0.4.3(08-19)、`langgraph` 1.2.11(08-11)、`checkpoint-postgres` 3.1.2(08-07) — 三套件均在近兩週內更新
- **評分變化**：99→100（+1，持續活躍 + 官方新版）

### NousResearch/hermes-agent — 86/100
- **優點**：Raphael 直接基底、3-layer memory 原生支援、MCP 原生整合
- **缺點/風險**：`open_issues_count` 高達 **34,923**，規模異常龐大，需評估是否為社群維運負擔或健康度警訊；星數暴增期版本穩定性需觀察
- **重要更新**：v0.20.5(08-21)、v0.20.4(08-18)、v0.20.3(08-17) — 近乎每 1-2 天一版的高頻釋出
- **評分變化**：78→86（+8：星數暴增 199,097→234,606／+35,509 ↑↑ 給 +5；新版釋出 +3）

### abhigyanpatwari/GitNexus — 76/100
- **優點**：零伺服器、瀏覽器端執行、與 GitHub/GitLab/Azure/本地皆相容、Pantheon 已列為 impact analysis 強制工具
- **缺點/風險**：目前為 Release Candidate（rc.211），穩定性仍在快速迭代中
- **重要更新**：v1.6.10-rc.211(08-19) 等連續 RC 版本
- **評分變化**：74→76（+2：星數 42,642→45,685／+3,043 ↑）

### thedotmack/claude-mem — 84/100
- **優點**：與 Claude 原生記憶模型一致、取代 openmemory 的 PoC 已完成並進入使用階段、跨 session context 注入已在本 session 中實際運作
- **缺點/風險**：與 Pantheon 的 langmem 方案分工邊界待釐清；openmemory 舊資料遷移規劃尚未文件化
- **重要更新**：v13.15.3(08-20)
- **評分變化**：78→84（+6：星數 83,590→91,568／+7,978 ↑ 給+3；新版+2；確認導入狀態+1）

### upstash/context7 — 64/100
- **優點**：LLM-ready 文件格式、多語言支援、與 LiteLLM pipeline 相容、docs-lookup agent 已固定使用
- **缺點/風險**：需 API key 管理；部分 SDK 覆蓋率仍不足
- **重要更新**：`@upstash/context7-mcp@4.0.3`(08-21)
- **評分變化**：60→64（+4：星數 57,822→61,101／+3,279 ↑ 給+2；新版+2）

### ⚠️ vancelin/openmemory — 建議正式除役
- **狀況**：144天無 commit（v20260622 報告為81天，本次惡化 +63天）；兩個月內星數僅 102→106（+4），社群關注度停滯
- **建議行動**：claude-mem 已完成替代 PoC 並進入使用階段，**本週內**正式將 openmemory 從 Pantheon/Raphael 工具鏈移除，並在下次 Gstar 報告中不再列入 PART 1

---

## PART 2A — 未導入 repos 全評估（119 repos，依契合度排序）

> 評分方法：Top 20（🏆標記）採人工逐項評估（活躍度、release、星數成長、對五個 active project 的具體價值）；其餘 99 個採統一啟發式（關鍵字相關性 + 活躍度 + 語言 + 中文內容加權），力求涵蓋全部 119 個未導入 starred repos，避免遺漏。契合度 <60 者多為目錄型/教學型/與五個 active project 無直接技術重疊的 repo，標記「觀察中」代表暫無明確導入路徑。

| # | Repo | ⭐ | 狀態 | 最後Push | 建議專案 | 契合度 | 備註 |
|---|------|----|----|---------|---------|--------|------|
| 1 | **nashsu/llm_wiki** 🏆 | 16,684 | 🟢 | 2026-08-21 | Aletheia | 94/100 | 中文知識庫桌面應用，活躍度與星數雙升 |
| 2 | **Egonex-AI/Understand-Anything** 🏆 | 80,178 | 🟢 | 2026-08-11 | Aletheia+Pantheon | 88/100 | 程式碼知識圖譜，星數大幅成長 |
| 3 | **crewAIInc/crewAI** 🏆 | 57,497 | 🟢 | 2026-08-22 | Pantheon | 87/100 | 多 agent 框架，Stage 3 對照組（本次重新分類為未導入） |
| 4 | **TauricResearch/TradingAgents** 🏆 | 99,360 | ⚪ | 2026-07-18 | Pantheon | 86/100 | 星數大漲但轉為不活躍，需觀察 |
| 5 | **msitarzewski/agency-agents** 🏆 | 147,476 | 🟢 | 2026-08-06 | Raphael | 83/100 | 星數暴增，sub-agent 人格化模式參考 |
| 6 | **Graphify-Labs/graphify** 🏆 | 109,684 | 🟢 | 2026-08-20 | Aletheia | 78/100 | 程式碼/文件/SQL 知識圖譜化，補 GitNexus 之外的資料源 |
| 7 | **rohitg00/agentmemory** 🏆 | 27,296 | 🟢 | 2026-08-17 | Pantheon | 77/100 | Memory layer 基準測試對照 langmem |
| 8 | **NVIDIA/SkillSpector** 🏆 | 14,890 | 🟢 | 2026-08-22 | agent-config | 76/100 | Skill 安全掃描，直接呼應 security.md 治理需求 |
| 9 | **headroomlabs-ai/headroom** 🏆 | 67,241 | 🟢 | 2026-08-22 | Pantheon+Aletheia | 74/100 | 壓縮 LLM 輸入 token，降低 LiteLLM 呼叫成本 |
| 10 | **rtk-ai/rtk** 🏆 | 77,125 | 🟢 | 2026-08-22 | Pantheon+Aletheia | 72/100 | CLI 層級 token 節流，補 headroom 之外場景 |
| 11 | **comet-ml/opik** 🏆 | 21,547 | 🟢 | 2026-08-23 | Pantheon | 70/100 | LLM 應用追蹤/評估平台，補目前僅 structlog 的可觀測性缺口 |
| 12 | **THU-MAIC/OpenMAIC** 🏆 | 20,860 | 🟢 | 2026-08-23 | Pantheon | 70/100 | 多 agent 互動課堂實作參考 |
| 13 | **Panniantong/Agent-Reach** 🏆 | 74,313 | 🟢 | 2026-08-12 | Raphael | 68/100 | 多平台資訊蒐集 CLI，Raphael 顧問層輸入來源 |
| 14 | **ComposioHQ/awesome-claude-skills** 🏆 | 73,073 | 🟢 | 2026-08-10 | agent-config | 68/100 | Skill 目錄，活躍度回升（30天前→13天前） |
| 15 | **obra/superpowers** 🏆 | 276,488 | 🟢 | 2026-08-19 | agent-config | 66/100 | Skill 框架方法論，星數持續暴增 |
| 16 | **mateaix/mateclaw** | 1,036 | 🟢 | 2026-08-22 | Raphael | 65/100 | 第二大腦，Multi-Agent Orchestration + MCP + Memory |
| 17 | **MemTensor/memmy-agent** | 920 | 🟢 | 2026-08-21 | Raphael | 65/100 | 個人 AI agent 共享記憶庫，支援 Hermes Agent |
| 18 | **browser-use/browser-use** | 110,205 | 🟢 | 2026-08-22 | Pantheon | 64/100 | 60→64（+4，星數+10,244 ↑↑，release 0.13.8） |
| 19 | **santifer/career-ops** | 67,873 | 🟢 | 2026-08-23 | agent-config | 64/100 | 60→64（+4，星數+12,800 ↑↑，持續 release） |
| 20 | **n8n-io/n8n** | 202,048 | 🟢 | 2026-08-23 | 觀察中 | 63/100 | 60→63（+3，星數+8,513 ↑，持續 release） |
| 21 | **punkpeye/awesome-mcp-servers** | 92,710 | 🟢 | 2026-08-17 | 觀察中 | 62/100 | 60→62（+2，星數+3,145 ↑） |
| 22 | **microsoft/ai-agents-for-beginners** | 73,046 | 🟢 | 2026-08-18 | Pantheon | 62/100 | 60→62（+2，星數+5,363 ↑） |
| 23 | **alirezarezvani/claude-skills** | 24,833 | 🟢 | 2026-08-21 | agent-config | 62/100 | 60→62（+2，星數+6,101 ↑，release 已停滯於 05-28） |
| 24 | **coreyhaines31/marketingskills** | 45,333 | 🟢 | 2026-08-22 | agent-config | 61/100 | Marketing skills for Claude Code and AI agents |
| 25 | **nexu-io/html-anything** | 8,420 | 🟢 | 2026-08-23 | agent-config | 61/100 | Agentic HTML editor，75 skills × 9 surfaces |
| 26 | **Imbad0202/academic-research-skills** | 43,395 | 🟢 | 2026-08-20 | agent-config | 58/100 | Academic Research Skills for Claude Code |
| 27 | **Weizhena/Deep-Research-skills** | 2,001 | 🟢 | 2026-08-23 | agent-config | 58/100 | Structured deep research skill |
| 28 | **tinyhumansai/openhuman** | 36,520 | 🟢 | 2026-08-23 | Raphael | 56/100 | Personal AI，local-first memory + agent fleet |
| 29 | **luongnv89/claude-howto** | 41,161 | 🟢 | 2026-08-19 | Pantheon | 55/100 | Claude Code 視覺化教學指南 |
| 30 | **virgiliojr94/book-to-skill** | 24,328 | 🟢 | 2026-08-19 | agent-config | 54/100 | 技術書 PDF 轉 Claude Code skill |
| 31 | **tt-a1i/archify** | 15,112 | 🟢 | 2026-08-22 | agent-config | 52/100 | 架構圖/流程圖 skill |
| 32 | **Nutlope/hallmark** | 26,692 | 🟢 | 2026-08-06 | agent-config | 51/100 | Anti-AI-slop 設計 skill |
| 33 | **nidhinjs/prompt-master** | 11,632 | ⚪ | 2026-06-10 | Raphael | 51/100 | Prompt 撰寫 skill（不活躍） |
| 34 | **aqua5230/usage** | 297 | 🟢 | 2026-08-23 | 觀察中 | 51/100 | Claude Code/Codex 用量追蹤 menu bar app |
| 35 | **anthropics/skills** | 171,107 | 🟢 | 2026-08-21 | agent-config | 50/100 | 官方 Agent Skills repo（本次重新分類為未導入） |
| 36 | **vercel-labs/skills** | 29,501 | 🟢 | 2026-08-18 | agent-config | 50/100 | Open agent skills 工具 |
| 37 | **google/skills** | 18,622 | 🟢 | 2026-08-22 | agent-config | 50/100 | Google 官方 Agent Skills（本次重新分類為未導入） |
| 38 | **anysearch-ai/anysearch-skill** | 5,857 | 🟢 | 2026-08-21 | agent-config | 50/100 | 統一即時搜尋引擎 skill |
| 39 | **tradecatlabs/vibe-coding-cn**（fork of EnzeD/vibe-coding） | 15,961 | 🟢 | 2026-08-04 | Aletheia | 49/100 | 中文 Vibe Coding 教程 |
| 40 | **mattpocock/skills** | 233,171 | 🟢 | 2026-08-21 | agent-config | 47/100 | Skill 目錄，星數暴增（本次重新分類為未導入） |
| 41 | **addyosmani/agent-skills** | 89,201 | 🟢 | 2026-08-21 | agent-config | 47/100 | Production-grade engineering skills |
| 42 | **op7418/guizang-ppt-skill** | 24,663 | 🟢 | 2026-08-07 | agent-config | 47/100 | HTML 簡報生成 skill |
| 43 | **revfactory/harness** | 8,819 | 🟢 | 2026-07-24 | agent-config | 47/100 | Meta-skill，設計 domain-specific agent team |
| 44 | **Agent-Threat-Rule/agent-threat-rules** | 373 | 🟢 | 2026-08-23 | agent-config | 47/100 | AI agent 安全威脅偵測規則標準 |
| 45 | **Raymondhou0917/claude-code-resources** | 281 | 🟢 | 2026-08-22 | 觀察中 | 46/100 | 中文 Claude Code 學習資源 |
| 46 | **kelvinschen/acpus** | 39 | 🟢 | 2026-08-20 | Pantheon | 46/100 | ACP agent 編排，crash-survive workflow |
| 47 | **Alishahryar1/free-claude-code** | 47,577 | 🟢 | 2026-08-23 | 觀察中 | 45/100 | 免費 Claude Code/Codex 額度工具 |
| 48 | **NYCU-Chung/cc-statusline** | 263 | ⚪ | 2026-05-22 | Pantheon | 45/100 | Claude Code statusline dashboard |
| 49 | **shengyanlin/claude-overlay** | 87 | 🟢 | 2026-08-23 | 觀察中 | 45/100 | Windows 螢幕感知 Claude Code chat |
| 50 | **S40911120/recensa** | 69 | 🟢 | 2026-08-16 | 觀察中 | 45/100 | Claude Code session transcript 檢視器 |
| 51 | **op7418/guizang-social-card-skill** | 6,552 | ⚪ | 2026-07-01 | Aletheia | 44/100 | 小紅書/公眾號封面生成 skill（不活躍） |
| 52 | **imraywang/wewrite** | 3,156 | 🟢 | 2026-08-17 | Aletheia | 44/100 | 公眾號內容全流程 skill |
| 53 | **decolua/9router** | 26,114 | 🟢 | 2026-08-14 | 觀察中 | 42/100 | 免費 AI coding provider 路由 |
| 54 | **VoltAgent/awesome-claude-code-subagents** | 24,563 | 🟢 | 2026-08-12 | Pantheon | 42/100 | 100+ 專用 subagent 集合 |
| 55 | **zakirkun/deep-eye** | 2,180 | 🟢 | 2026-08-21 | agent-config | 42/100 | AI 驅動漏洞掃描與合規報告 |
| 56 | **paperclipai/paperclip** | 79,215 | 🟢 | 2026-08-23 | Pantheon | 41/100 | Agent 管理 app |
| 57 | **stablyai/orca** | 51,526 | 🟢 | 2026-08-23 | Pantheon | 41/100 | 平行 agent fleet ADE |
| 58 | **HKUDS/CLI-Anything** | 47,981 | 🟢 | 2026-08-21 | Pantheon | 41/100 | CLI Agent-Native 化框架 |
| 59 | **mindfold-ai/Trellis** | 14,164 | 🟢 | 2026-08-21 | Pantheon | 41/100 | Agent harness |
| 60 | **worldwonderer/oh-story-claudecode** | 5,966 | 🟢 | 2026-08-22 | Aletheia | 41/100 | 網文寫作 skill 包 |
| 61 | **hardness1020/awesome-agent-architecture** | 618 | 🟢 | 2026-08-21 | Pantheon | 41/100 | AI agent 架構學習資源 |
| 62 | **criptogus/HermesOffice** | 518 | 🟢 | 2026-08-13 | Pantheon | 41/100 | Hermes Agent 驅動的 AI 原生辦公套件 |
| 63 | **op7418/Humanizer-zh** | 15,887 | ⚪ | 2026-01-19 | Aletheia | 39/100 | 中文去 AI 味 skill（不活躍） |
| 64 | **DietrichGebert/ponytail** | 108,521 | 🟢 | 2026-08-07 | Pantheon | 38/100 | Agent「少寫程式碼」哲學 skill |
| 65 | **JCodesMore/ai-website-cloner-template** | 32,866 | 🟢 | 2026-08-14 | Pantheon | 38/100 | 一鍵網站複製工具 |
| 66 | **xai-org/grok-build** | 25,915 | 🟢 | 2026-08-23 | Pantheon | 38/100 | Coding agent harness/TUI |
| 67 | **joeseesun/qiaomu-anything-to-notebooklm** | 5,783 | ⚪ | 2026-04-28 | agent-config | 38/100 | 多來源內容轉 NotebookLM（不活躍） |
| 68 | **linuxhsj/openclaw-zero-token** | 5,150 | 🟢 | 2026-08-17 | 觀察中 | 37/100 | 免 Token 使用各大模型 |
| 69 | **alchaincyf/nuwa-skill** | 31,181 | 🟢 | 2026-07-27 | 觀察中 | 35/100 | 思維模式蒸餾 skill |
| 70 | **mengxi-ream/read-frog** | 9,315 | 🟢 | 2026-08-23 | 觀察中 | 35/100 | 語言學習與翻譯瀏覽器擴充 |
| 71 | **Thysrael/Horizon** | 8,999 | 🟢 | 2026-08-23 | 觀察中 | 35/100 | AI 新聞雷達每日簡報 |
| 72 | **freestylefly/CodexGuide** | 3,245 | 🟢 | 2026-08-20 | 觀察中 | 35/100 | Codex 中文實踐指南 |
| 73 | **notoriouslab/doc-cleaner** | 310 | 🟢 | 2026-08-20 | Aletheia | 35/100 | 文件轉 Markdown（16種格式） |
| 74 | **mathruffian-dot/claude-code-lazy-packs** | 243 | ⚪ | 2026-06-12 | 觀察中 | 33/100 | Claude Code 懶人包（不活躍） |
| 75 | **lbjlaq/Antigravity-Manager** | 30,629 | 🟢 | 2026-08-23 | 觀察中 | 32/100 | 帳號管理切換工具 |
| 76 | **freestylefly/awesome-gpt-image-2** | 12,403 | 🟢 | 2026-08-23 | Aletheia | 32/100 | GPT-Image2 提示詞工程模板庫 |
| 77 | **bozhouDev/codex-orange-book** | 3,264 | 🟢 | 2026-08-14 | 觀察中 | 32/100 | Codex 橙皮書使用指南 |
| 78 | **voidful/hung-yi-lee-skill** | 973 | 🟢 | 2026-08-11 | Aletheia | 32/100 | 李宏毅老師教學蒸餾 skill |
| 79 | **OpenHands/OpenHands** | 84,836 | 🟢 | 2026-08-23 | 觀察中 | 31/100 | AI-driven development 框架 |
| 80 | **jamiepine/voicebox** | 51,181 | 🟢 | 2026-08-09 | 觀察中 | 31/100 | AI 語音工作室 |
| 81 | **soxoj/maigret** | 36,972 | 🟢 | 2026-08-23 | 觀察中 | 31/100 | 使用者名稱跨站調查工具 |
| 82 | **openai/codex-plugin-cc** | 32,210 | ⚪ | 2026-07-08 | 觀察中 | 31/100 | Claude Code 內呼叫 Codex（不活躍） |
| 83 | **companion-inc/feynman** | 8,538 | 🟢 | 2026-08-23 | 觀察中 | 31/100 | （無公開描述） |
| 84 | **mcncarl/yichen-skills** | 1,924 | 🟢 | 2026-08-20 | 觀察中 | 31/100 | （無公開描述） |
| 85 | **godotengine/godot** | 116,022 | 🟢 | 2026-08-21 | 觀察中 | 28/100 | 遊戲引擎（與五個 active project 無重疊） |
| 86 | **apple/container** | 49,251 | 🟢 | 2026-08-20 | 觀察中 | 28/100 | macOS 輕量虛擬機容器工具 |
| 87 | **AlexsJones/llmfit** | 33,658 | 🟢 | 2026-08-23 | 觀察中 | 28/100 | 硬體可跑模型比對工具 |
| 88 | **tw93/Kami** | 10,866 | 🟢 | 2026-08-08 | 觀察中 | 28/100 | 內容排版工具 |
| 89 | **Finb/Bark** | 8,934 | 🟢 | 2026-08-18 | 觀察中 | 28/100 | iOS 推播通知 app |
| 90 | **zhongerxin/Cowart** | 5,644 | 🟢 | 2026-08-23 | 觀察中 | 28/100 | （無公開描述） |
| 91 | **ombharatiya/ai-system-design-guide** | 2,719 | 🟢 | 2026-08-15 | 觀察中 | 28/100 | AI 系統設計指南 |
| 92 | **ggwhite/4x** | 33 | 🟢 | 2026-08-23 | Pantheon | 28/100 | Design/Code/Review/Test 隔離角色開發迴圈 |
| 93 | **notoriouslab/browser-mcp-lite** | 42 | ⚪ | 2026-04-02 | 觀察中 | 27/100 | 輕量瀏覽器 MCP server（不活躍） |
| 94 | **multica-ai/andrej-karpathy-skills** | 205,578 | ⚪ | 2026-04-20 | 觀察中 | 26/100 | Karpathy CLAUDE.md 行為改善單檔（不活躍） |
| 95 | **Zie619/n8n-workflows** | 56,232 | ⚪ | 2026-06-24 | 觀察中 | 25/100 | n8n workflow 收集（不活躍，另有整合中的 fork） |
| 96 | **cloudflare/agentic-inbox** | 6,922 | ⚪ | 2026-04-23 | Pantheon | 25/100 | 自架 AI email client（不活躍） |
| 97 | **zakirkun/guardian-cli** | 1,855 | ⚪ | 2026-06-27 | 觀察中 | 25/100 | 滲透測試自動化 CLI（不活躍） |
| 98 | **alchaincyf/elon-musk-skill** | 489 | ⚪ | 2026-05-28 | Aletheia | 25/100 | 人物思維蒸餾 skill（不活躍） |
| 99 | **jinggreen15/ai-design-team** | 189 | ⚪ | 2026-03-29 | agent-config | 25/100 | 多角色設計團隊 skill（不活躍） |
| 100 | **tanweai/pua** | 19,476 | ⚪ | 2026-07-16 | Aletheia | 24/100 | 高能動性中文 skill（不活躍） |
| 101 | **myyang19770915/Hybride_pageindex_RAG** | 47 | ⚪ | 2026-06-25 | Aletheia | 24/100 | 混合搜尋 RAG 專案（不活躍） |
| 102 | **mboverell/ai-chief-of-staff** | 17 | ⚪ | 2026-01-25 | Pantheon | 22/100 | 會議筆記轉洞見系統（不活躍） |
| 103 | **ai-twinkle/rlhf-book-zh-tw** | 177 | ⚪ | 2026-07-10 | 觀察中 | 21/100 | RLHF 繁中譯本（不活躍） |
| 104 | **arxhr007/Aliens_eye** | 3,463 | ⚪ | 2026-07-16 | 觀察中 | 20/100 | 社群帳號搜尋工具（不活躍） |
| 105 | **poccii/Faceting-Diagram-viewer** | 2 | ⚪ | 2026-07-14 | 觀察中 | 20/100 | 切割圖檢視器（不活躍） |
| 106 | **salafadidas/Aletheia**（自有 repo） | 1 | ⚪ | 2026-06-27 | — | 20/100 | 自星標自有 repo，非外部候選 |
| 107 | **salafadidas/project-pantheon**（自有 repo，fork of francescofano/langgraph-telegram-bot） | 1 | ⚪ | 2026-06-27 | — | 20/100 | 自星標自有 repo，非外部候選 |
| 108 | **notoriouslab/gmail-statement-fetcher** | 19 | ⚪ | 2026-04-02 | 觀察中 | 19/100 | Gmail 帳單下載工具（不活躍） |
| 109 | **ai-twinkle/Hub** | 186 | ⚪ | 2026-07-13 | 觀察中 | 17/100 | 社群回饋平台（不活躍） |
| 110 | **mli/paper-reading** | 33,726 | ⚪ | 2025-03-22 | 觀察中 | 16/100 | 論文精讀（518天前，長期不活躍） |
| 111 | **NousResearch/autoreason** | 599 | ⚪ | 2026-04-12 | 觀察中 | 16/100 | 主觀領域自動研究（不活躍） |
| 112 | **Aider-AI/aider** | 48,415 | ⚪ | 2026-05-22 | 觀察中 | 15/100 | 終端 AI 結對編程（92天前不活躍） |
| 113 | **op7418/Youtube-clipper-skill** | 2,154 | ⚪ | 2026-01-22 | 觀察中 | 15/100 | YouTube 剪輯 skill（不活躍） |
| 114 | **fatwang2/siri-ultra**（fork of Sh4yy/personal-ai） | 1,206 | ⚪ | 2026-06-05 | 觀察中 | 15/100 | LLM 驅動 Siri（不活躍） |
| 115 | **wellwind/claude-code-from-source-zh-tw** | 124 | ⚪ | 2026-04-14 | 觀察中 | 15/100 | 中文原始碼導讀（不活躍） |
| 116 | **mukiwu/claude-code-tips** | 40 | ⚪ | 2026-04-19 | 觀察中 | 15/100 | Claude Code 使用技巧（不活躍） |
| 117 | **doggy8088/gpt4o-tokenizer** | 18 | ⚪ | 2026-05-31 | 觀察中 | 15/100 | Tokenizer 工具（不活躍） |
| 118 | **salafadidas/SeongJinWoo**（自有 repo） | 1 | ⚪ | 2026-06-14 | — | 15/100 | 自星標自有 repo，非外部候選 |
| 119 | **salafadidas/Garden-Party**（自有 repo） | 1 | ⚪ | 2026-06-14 | — | 15/100 | 自星標自有 repo，非外部候選 |

---

## PART 2B — Top 20 Priority Repos

| 排名 | 狀態 | Repo | 當前 Stars | 星數成長 | 最後 Push | 建議導入專案 | 核心價值 | 契合度 | 優點 | 缺點/風險 | 重要更新內容 | 評分變化 | 建議行動 |
|------|------|------|-----------|---------|----------|-------------|----------|--------|------|-----------|------------|---------|---------|
| 🥇 1 | 🟢 | **langchain-ai/langgraph** | 40,272 | +4,893 ↑ | 今天 | ✅已導入 / Pantheon | Pantheon 多 agent 編排骨幹，5-node graph 已運作，官方持續維護 | 100/100 | 官方支援 · 與 AsyncPostgresStore 原生整合 · 三模型 ensemble 相容 · 文件齊全 | API 版本更新快 · 與 langmem 分工需持續協調 | langgraph-sdk 0.4.3(08-19)、langgraph 1.2.11(08-11)、checkpoint-postgres 3.1.2(08-07) | 99→100（+1，持續活躍+新版） | 追蹤 1.2.x changelog，確認無 breaking change |
| 🥈 2 | 🟢 | **nashsu/llm_wiki** | 16,684 | +4,320 ↑ | 2天前 | Aletheia | 中文桌面知識庫應用，持久化 wiki 取代傳統 RAG 每次重檢索 | 94/100 | 活躍度上升 · 星數穩定成長 · 與 Aletheia 中文語料需求高度契合 | 需評估桌面應用 vs API 整合方式 · 版本相容需確認 | v0.6.10(08-21) | 92→94（+2，星數+4,320↑，release） | Aletheia 下個 Sprint 評估桌面/API 整合路徑 |
| 🥉 3 | 🟢 | **Egonex-AI/Understand-Anything** | 80,178 | +14,701 ↑↑ | 12天前 | Aletheia+Pantheon | 多模態程式碼知識圖譜，含 Figma 設計圖譜；Aletheia 後期擴充可用 | 88/100 | 星數大幅成長 · 支援 Claude Code/Codex/Cursor 多平台 · 圖譜視覺化完整 | 12天無新 push，動能略降溫 · 需評估與 GitNexus 的功能重疊 | v2.9.0(07-10) — Figma design graphs + .ua directory | 85→88（+3，星數+14,701↑↑） | Aletheia QMD 後接入，評估與 GitNexus 分工 |
| 4 | 🟢 | **crewAIInc/crewAI** | 57,497 | +3,400 ↑ | 1天前 | Pantheon（Stage 3對照） | 另一條多 agent 路線；Pantheon Stage 3 架構決策的對照組 | 87/100 | 簡潔 API · 範本豐富 · 持續活躍 · 適合架構比較 | 與 LangGraph 雙軌維護成本高 · **本次確認未在 requirements.txt/CLAUDE.md 中找到整合證據，重新分類為未導入** | 1.15.17(08-20) | 85→87（+2，星數成長；分類修正：由「已導入」→「未導入」） | Stage 3 架構決策時對照評估，非本週急件 |
| 5 | 🟢 | **NousResearch/hermes-agent** | 234,606 | +35,509 ↑↑ | 今天 | ✅已導入 / Raphael | Raphael Phase 1 直接基底；3-layer memory 與 MCP 原生支援 | 86/100 | Raphael 直接套用 · 內建 MCP+memory · 高頻釋出節奏 | **open_issues 高達34,923，規模異常，需評估維運健康度** · 暴增期穩定性待觀察 | v0.20.5(08-21)、v0.20.4(08-18)、v0.20.3(08-17) | 78→86（+8，星數暴增+5，新版+3） | Raphael Phase 1 持續採用，觀察 issue backlog 趨勢 |
| 6 | ⚪ | **TauricResearch/TradingAgents** | 99,360 | +11,510 ↑↑ | **36天前** | Pantheon | 多 agent + 領域知識完整實作範本；Stage 3 設計可參考 | 86/100 | 星數大幅成長 · 完整領域案例 | **由 baseline 的「今天 push」轉為 36天不活躍，動能明顯降溫，需觀察是否停止維護** | v0.3.1(07-05) | 85→86（+1，星數成長抵銷活躍度下滑疑慮） | 觀察下次 push，若持續不活躍則降低優先序 |
| 7 | 🟢 | **thedotmack/claude-mem** | 91,568 | +7,978 ↑ | 2天前 | ✅已導入 / Raphael+agent-config | 跨 session context 記憶；已從 PoC 候選升級為本 session 實際使用中工具 | 84/100 | 與 Claude 原生記憶模型一致 · PoC 已完成 · 本 session 內確認在用 | 與 langmem 分工邊界待釐清 · openmemory 遷移規劃未文件化 | v13.15.3(08-20) | 78→84（+6，星數+3，新版+2，確認導入+1） | 正式文件化 openmemory→claude-mem 遷移計畫 |
| 8 | 🟢 | **msitarzewski/agency-agents** | 147,476 | +32,526 ↑↑ | 17天前 | Raphael | Agency 模式對 Raphael 多 sub-agent 架構有直接參考價值 | 83/100 | 星數暴增 · 人格化 sub-agent 範本豐富 | 17天未 push，動能趨緩 · 尚無正式 release | （無 release） | 78→83（+5，星數暴增） | Raphael sub-agent 人格化設計參考，本季瀏覽 |
| 9 | 🟢 | **Graphify-Labs/graphify** | 109,684 | 首次追蹤 | 3天前 | Aletheia | 把 codebase/docs/SQL/PDF 轉成可查詢知識圖譜，local deterministic AST parsing | 78/100 | 星數高（10萬+）· 持續高頻 release · 支援 Claude Code/Cursor/Codex/Gemini CLI | 新進榜，長期穩定性待觀察 · 與現有 GitNexus 功能有重疊 | v0.9.48(08-20) | 新進榜 → 78 | Aletheia 評估與 GitNexus 分工（GitNexus 管程式碼，graphify 管文件/SQL） |
| 10 | 🟢 | **rohitg00/agentmemory** | 27,296 | +3,668 ↑ | 6天前 | Pantheon | Memory layer 比較參考；對照目前 langmem 方案優缺點 | 77/100 | 活躍 · benchmark 導向 · 與生態系契合 | 整合工作量需評估 | v0.9.29(08-16) | 74→77（+3，星數+3,668↑，release） | 監控 release，作為 langmem 基準對照 |
| 11 | 🟢 | **NVIDIA/SkillSpector** | 14,890 | 首次追蹤 | 1天前 | agent-config | Skill 安全掃描，偵測 Claude Code/Codex/MCP skill 的漏洞、惡意模式、prompt injection、供應鏈風險 | 76/100 | NVIDIA 出品可信度高 · 直接呼應 security.md 治理需求 · 高頻 release | 新進榜，尚未實測 | v2.9.6(08-18) | 新進榜 → 76 | agent-config 本季導入，作為新增 skill 上線前的安全掃描關卡 |
| 12 | 🟢 | **abhigyanpatwari/GitNexus** | 45,685 | +3,043 ↑ | 2天前 | ✅已導入 / Pantheon | 把 repo 轉成 knowledge graph；本 session 內 MCP 工具實際使用中 | 76/100 | 已導入且驗證有效 · 零伺服器 · 與 GitHub API 一致 | 仍為 RC 版本（rc.211），穩定性待觀察 | v1.6.10-rc.211(08-19) | 74→76（+2，星數穩定成長） | 持續使用，觀察正式版釋出時程 |
| 13 | 🟢 | **headroomlabs-ai/headroom** | 67,241 | 首次追蹤 | 1天前 | Pantheon+Aletheia | 壓縮 tool outputs/logs/RAG chunks 再送進 LLM，token 降低 20-95% | 74/100 | 直接降低 LiteLLM 呼叫成本 · Library/proxy/MCP server 三種形式 · 每日 release | 新進榜，需驗證壓縮後答案品質 | v0.36.5(08-22) | 新進榜 → 74 | Pantheon/Aletheia 各挑一條 pipeline 做 PoC，驗證成本節省幅度 |
| 14 | 🟢 | **rtk-ai/rtk** | 77,125 | 首次追蹤 | 1天前 | Pantheon+Aletheia | CLI proxy 降低常見開發指令 60-90% token 消耗，單一 Rust binary 零依賴 | 72/100 | 部署簡單（單 binary）· 與 headroom 互補（CLI層 vs API層）· 持續高頻 release | 新進榜，開發階段版號（dev-0.45.1-rc）顯示仍不穩定 | dev-0.45.1-rc.362(08-20) | 新進榜 → 72 | 待 headroom PoC 後一併評估，非本週急件 |
| 15 | 🟢 | **THU-MAIC/OpenMAIC** | 20,860 | +2,108 ↑ | 今天 | Pantheon | 多 agent 開源實作；可比對 Pantheon 目前 LangGraph 設計 | 70/100 | 活躍 · 持續 release · 教學情境完整 | 整合工作量需評估 | v0.3.2(08-14) | 67→70（+3，星數+2,108↑，release） | 監控 release，作為多 agent 互動設計參考 |
| 16 | 🟢 | **comet-ml/opik** | 21,547 | 首次追蹤 | 今天 | Pantheon | LLM 應用 debug/評估/監控，補目前 Pantheon 僅有 structlog 的可觀測性缺口 | 70/100 | 完整 tracing+eval+dashboard · production-ready · 每日 release | 新進榜，需評估自架成本 vs SaaS 版 | 2.2.36(08-21) | 新進榜 → 70 | Pantheon Stage 3 前評估導入，補齊 observability |
| 17 | 🟢 | **ComposioHQ/awesome-claude-skills** | 73,073 | +7,622 ↑ | 13天前 | agent-config | Skill 生態系參考來源；餵入 agent-config 的 skill templates | 68/100 | 範本豐富 · **活躍度回升**（由baseline的30天不活躍→13天前） | 目錄型 repo，需自篩 | （無 release） | 64→68（+4，星數+7,622↑，活躍度回升+2） | 本週瀏覽，摘錄 skill 模板進 agent-config |
| 18 | 🟢 | **Panniantong/Agent-Reach** | 74,313 | 首次追蹤 | 11天前 | Raphael | 讓 AI agent 讀取/搜尋 Twitter/Reddit/YouTube/GitHub 等，零 API 費用 | 68/100 | 一站式 CLI · 零 API 費用 · Raphael 顧問層資訊蒐集直接可用 | 11天未 push，release 已停滯於 06-11（動能降溫） | v1.5.0(06-11) | 新進榜 → 68 | Raphael 資訊蒐集層 PoC，觀察後續維護節奏 |
| 19 | 🟢 | **obra/superpowers** | 276,488 | +41,366 ↑↑ | 4天前 | agent-config | Skill 生態系方法論參考來源；餵入 agent-config skill templates | 66/100 | **星數暴增**（235,122→276,488，本次追蹤中最大絕對成長）· 活躍 · 持續 release | 目錄/方法論型 repo，需自篩 | v6.3.0(08-12) | 60→66（+6，星數暴增+41,366↑↑ 給+5，release+1） | 本週瀏覽，摘錄方法論進 agent-config |
| 20 | 🟢 | **upstash/context7** | 61,101 | +3,279 ↑ | 2天前 | ✅已導入 / Aletheia | 為 Aletheia 提供 LLM-ready library docs；docs-lookup agent 已固定使用 | 64/100 | 已導入且驗證有效 · LLM-ready docs · 多語言支援 | 需 API key 管理 · SDK 覆蓋率仍不足 | @upstash/context7-mcp@4.0.3(08-21) | 60→64（+4，星數+3,279↑，release+2） | 持續使用，觀察 SDK 覆蓋率是否提升 |

*同分排序原則：已導入 repos（✅標記）優先於分數相同的未導入 repos，因其已產生驗證過的實際價值。*

---

## 更新訊號摘要

### 🚀 星數暴增（Top 5 絕對成長，本次追蹤範圍內）
1. `mattpocock/skills`：139,994 → 233,171（**+93,177**，未進 Top20 因目錄型 repo 契合度受限）
2. `obra/superpowers`：235,122 → 276,488（+41,366）
3. `NousResearch/hermes-agent`：199,097 → 234,606（+35,509）
4. `msitarzewski/agency-agents`：114,950 → 147,476（+32,526）
5. `Egonex-AI/Understand-Anything`：65,477 → 80,178（+14,701）

> 整體觀察：AI agent/skill 生態系在 2026-06-22 至 2026-08-23 這兩個月間呈現全面性星數暴增，幾乎所有追蹤中的大型 repo 成長皆超過 +1,000 star 門檻，屬於市場級趨勢而非個別 repo 訊號，已依 SKILL.md 星數成長規則統一套用調分。

### ⚠️ 不活躍警告
- `TauricResearch/TradingAgents`：由 baseline「今天 push」轉為 **36天前**，Top20 中唯一從活躍轉為不活躍者，需觀察下次是否恢復
- `vancelin/openmemory`：**144天**無 commit（baseline為81天，惡化+63天），已有確認可行替代方案（claude-mem），**建議本週正式除役**

### 🔄 分類修正（非 repo 本身 pivot，屬本次報告方法論修正）
- `crewAIInc/crewAI`、`anthropics/skills`、`google/skills`、`mattpocock/skills`：v20260622 報告列為「已導入」，本次依 requirements.txt/CLAUDE.md/.mcp.json 重新查證未找到直接證據，改列「未導入」評估

### 📦 新版釋出（近一週內，Top20 相關）
- `langchain-ai/langgraph`：langgraph-sdk 0.4.3 (08-19)
- `NousResearch/hermes-agent`：v0.20.5 (08-21)
- `thedotmack/claude-mem`：v13.15.3 (08-20)
- `abhigyanpatwari/GitNexus`：v1.6.10-rc.211 (08-19)
- `upstash/context7`：context7-mcp@4.0.3 (08-21)
- `headroomlabs-ai/headroom`：v0.36.5 (08-22，每日高頻)

### 🌐 專案宇宙 pivot（見上方「專案宇宙概覽」）
- `ecosystem-blueprint` 治理角色轉為 Terminal/Complete，新 Active Portfolio Item 為 `ai-engineering-os`（不在 Gstar 追蹤清單內）

---

## 行動建議時程

| 時程 | 動作 |
|------|------|
| 本週 | `vancelin/openmemory` 正式除役；`NVIDIA/SkillSpector` 導入 agent-config 作為 skill 上線前安全掃描關卡 |
| 下週 | `headroomlabs-ai/headroom` 於 Pantheon 或 Aletheia 挑一條 pipeline 做 token 壓縮 PoC |
| Sprint 內 | `nashsu/llm_wiki` 評估桌面/API 整合路徑；`Graphify-Labs/graphify` 與 GitNexus 分工評估 |
| Stage 3 前 | `comet-ml/opik` 導入 Pantheon 補齊 observability；`crewAIInc/crewAI` vs LangGraph 架構對照 |
| Stage 3 後 | `rtk-ai/rtk` 併同 headroom PoC 結果一併評估 |
| 持續觀察 | `TauricResearch/TradingAgents` 活躍度是否恢復；`NousResearch/hermes-agent` open_issues 趨勢 |
| 待 Human 決策 | 是否將 `ai-engineering-os` 併入下次 Gstar 追蹤的 active project 清單 |

---

*Generated by Gstar skill · live GitHub API data · no caching · SKILL.md blob `70f3a0e81dd0b66e237ca32e422ffc16fd3bff32`（未修改，本次執行未發現需修正之處）*
