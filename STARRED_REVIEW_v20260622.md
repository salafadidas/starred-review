# Starred Review v20260622

> Generated: 2026-06-22 03:08 UTC  
> Total starred: 96 · Relevant scored: 67 · Top 20 below  
> Previous report: `STARRED_REVIEW_v20260618.md`

---

## 專案宇宙概覽

- **Pantheon**：LangGraph multi-agent · Postgres/pgvector · Telegram bot · Stage 2 Sprint 1 進行中
- **Aletheia**：FastAPI + LiteLLM + Notion · QMD 待裝
- **Raphael**：Hermes Agent 基底 · Phase 1 即將啟動
- **agent-config**：神經系統 · CLAUDE.md governance
- **starred-review / ecosystem-blueprint**：稽核與雷達層

---

## PART 1 — 已導入 repos（live activity）

下列 starred repos 已被生態系直接引用（CLAUDE.md / requirements / .mcp.json）：

- `NousResearch/hermes-agent` · ⭐199,097 · 最後 push 今天 · fit≈78/100
- `abhigyanpatwari/GitNexus` · ⭐42,642 · 最後 push 今天 · fit≈74/100
- `anthropics/skills` · ⭐153,565 · 最後 push 12天前 · fit≈—/100
- `crewAIInc/crewAI` · ⭐54,097 · 最後 push 昨天 · fit≈85/100
- `google/skills` · ⭐14,012 · 最後 push 今天 · fit≈—/100
- `langchain-ai/langgraph` · ⭐35,379 · 最後 push 昨天 · fit≈99/100
- `mattpocock/skills` · ⭐139,994 · 最後 push 3天前 · fit≈—/100
- `thedotmack/claude-mem` · ⭐83,590 · 最後 push 今天 · fit≈78/100
- `upstash/context7` · ⭐57,822 · 最後 push 2天前 · fit≈60/100
- `vancelin/openmemory` · ⭐102 · 最後 push 81天前 · fit≈—/100


⚠️ **注意**：`vancelin/openmemory` 已整合進 Pantheon，但近期更新緩慢 — 已於 Sprint 1 鎖定 `thedotmack/claude-mem` 作為替代候選。

---

## PART 2B — Top 20 Priority Repos

| 排名 | 狀態 | Repo | 當前 Stars | 星數成長 | 最後 Push | 建議導入專案 | 核心價值 | 契合度 | 優點 | 缺點/風險 | 重要更新內容 | 評分變化 | 建議行動 |
|------|------|------|-----------|---------|----------|-------------|----------|--------|------|-----------|------------|---------|---------|
| 🥇 1 | 🟢 | **langchain-ai/langgraph** | 35,379 | — | 2026-06-21（昨天） | ✅已導入 / Pantheon | Pantheon 多 agent 編排骨幹；最新版本與 AsyncPostgresStore/Saver 直接相容。 | 99/100 | 官方支援 · 與 langmem/Postgres 整合佳 · 文件齊全 · 活躍社群 | API 變動快 · 學習曲線陡 | 近 3 日內活躍 · ⭐35,379 | 新進榜 → 99 | 持續追蹤 release · S1-NS-1 前 review changelog |
| 🥈 2 | 🟢 | **nashsu/llm_wiki** | 12,364 | — | 2026-06-18（3天前） | Aletheia | 中文 LLM 知識庫；可作為 Aletheia 中文語料補充。 | 92/100 | 活躍社群 · 與生態系契合 · 文件齊全 | 整合工作量需評估 · 版本相容需確認 | 近 3 日內活躍 · ⭐12,364 | 新進榜 → 92 | 監控 release · 下次 Gstar 再評 |
| 🥉 3 | 🟢 | **Egonex-AI/Understand-Anything** | 65,477 | — | 2026-06-20（昨天） | Aletheia | 多模態 RAG 框架；Aletheia 後期擴充 image/PDF 理解時可採用。 | 85/100 | 活躍社群 · 與生態系契合 · 文件齊全 | 整合工作量需評估 · 版本相容需確認 | 近 3 日內活躍 · ⭐65,477 | 93 → 85（-8） | 監控 release · 下次 Gstar 再評 |
| 4 | 🟢 | **TauricResearch/TradingAgents** | 87,850 | — | 2026-06-22（今天） | Pantheon | 多 agent + 領域知識的完整實作範本；Stage 3 設計可參考。 | 85/100 | 活躍社群 · 與生態系契合 · 文件齊全 | 整合工作量需評估 · 版本相容需確認 | 今日仍有 push · ⭐87,850 | 新進榜 → 85 | 監控 release · 下次 Gstar 再評 |
| 5 | 🟢 | **crewAIInc/crewAI** | 54,097 | — | 2026-06-20（昨天） | ✅已導入 / Pantheon | LangGraph 之外另一條多 agent 路線；Stage 3 架構決策的對照組。 | 85/100 | 簡潔 API · 範本豐富 · 適合做架構比較 | 與 LangGraph 雙軌維護成本高 | 近 3 日內活躍 · ⭐54,097 | 82 → 85（+3） | Stage 3 架構決策時對照 · 不急 |
| 6 | 🟢 | **NousResearch/hermes-agent** | 199,097 | — | 2026-06-22（今天） | ✅已導入 / Raphael | Raphael Phase 1 直接基底；3-layer memory 與 MCP 原生支援。 | 78/100 | Raphael 直接套用 · 內建 MCP+memory · 部署簡單 | 相依套件多 · 部署資源吃緊 | 今日仍有 push · ⭐199,097 | 99 → 78（-21） | Raphael Phase 1 直接採用 · 本週開 issue |
| 7 | 🟢 | **msitarzewski/agency-agents** | 114,950 | — | 2026-06-21（今天） | Raphael | Agency 模式對 Raphael 多 sub-agent 架構有直接參考價值。 | 78/100 | 活躍社群 · 與生態系契合 · 文件齊全 | 整合工作量需評估 · 版本相容需確認 | 今日仍有 push · ⭐114,950 | 84 → 78（-6） | 監控 release · 下次 Gstar 再評 |
| 8 | 🟢 | **thedotmack/claude-mem** | 83,590 | — | 2026-06-21（今天） | ✅已導入 / Raphael | Sprint 1 已鎖定取代 openmemory 的候選；memory + context 跨會話保持。 | 78/100 | 與 Claude 原生記憶模型一致 · 取代 openmemory 阻力低 · Stage 1 已點名 | 需 migration 規劃 · langmem 共存策略未定 | 今日仍有 push · ⭐83,590 | 100 → 78（-22） | Sprint 1 結尾啟動 PoC（取代 openmemory） |
| 9 | 🟢 | **rohitg00/agentmemory** | 23,628 | — | 2026-06-15（6天前） | Pantheon | Memory layer 比較參考；對照目前 langmem 方案的優缺點。 | 74/100 | 活躍社群 · 與生態系契合 · 文件齊全 | 整合工作量需評估 · 版本相容需確認 | 6 天內活躍 · ⭐23,628 | 85 → 74（-11） | 監控 release · 下次 Gstar 再評 |
| 10 | 🟢 | **abhigyanpatwari/GitNexus** | 42,642 | — | 2026-06-21（今天） | ✅已導入 / Aletheia | 把 GitHub repo 轉成 knowledge graph；Aletheia 個人技術知識圖譜核心。 | 74/100 | 可視化 repo 依賴 · 適合個人 ecosystem · 與 GitHub API 一致 | 尚屬早期 · 中文文件少 | 今日仍有 push · ⭐42,642 | 96 → 74（-22） | Aletheia QMD 後接入 · Stage 2 後段 |
| 11 | 🟢 | **THU-MAIC/OpenMAIC** | 18,752 | — | 2026-06-22（今天） | Pantheon | 多 agent 開源實作；可比對 Pantheon 目前 LangGraph 設計。 | 67/100 | 活躍社群 · 與生態系契合 · 文件齊全 | 整合工作量需評估 · 版本相容需確認 | 今日仍有 push · ⭐18,752 | 新進榜 → 67 | 監控 release · 下次 Gstar 再評 |
| 12 | 🟢 | **ComposioHQ/awesome-claude-skills** | 65,451 | — | 2026-05-22（30天前） | agent-config | Skill 生態系參考來源；可以餵入 agent-config 的 skill templates。 | 64/100 | 範本豐富 · 社群活躍 · 直接借鑑 SKILL.md 結構 | 目錄型 repo · 需自篩 | 30 天內活躍 · ⭐65,451 | 新進榜 → 64 | 本週瀏覽 · 摘錄 skill 模板進 agent-config |
| 13 | 🟢 | **alirezarezvani/claude-skills** | 18,732 | — | 2026-06-20（昨天） | Raphael | Skill 生態系參考來源；可以餵入 agent-config 的 skill templates。 | 60/100 | 範本豐富 · 社群活躍 · 直接借鑑 SKILL.md 結構 | 整合工作量需評估 · 版本相容需確認 | 近 3 日內活躍 · ⭐18,732 | 新進榜 → 60 | 本週瀏覽 · 摘錄 skill 模板進 agent-config |
| 14 | 🟢 | **punkpeye/awesome-mcp-servers** | 89,565 | — | 2026-06-19（2天前） | Pantheon | MCP server 目錄；用來補 Raphael / Pantheon 缺的連線。 | 60/100 | 範本豐富 · 社群活躍 · 直接借鑑 SKILL.md 結構 | 目錄型 repo · 需自篩 | 近 3 日內活躍 · ⭐89,565 | 86 → 60（-26） | 本週瀏覽 · 摘錄 skill 模板進 agent-config |
| 15 | 🟢 | **browser-use/browser-use** | 99,961 | — | 2026-06-20（昨天） | Pantheon | Pantheon agent 取得瀏覽器操作能力，補齊 web 抓取／自動化缺口。 | 60/100 | Python 原生 · LLM-driven · 補 web 自動化缺口 | 瀏覽器資源密集 · GCP 部署需另外處理 | 近 3 日內活躍 · ⭐99,961 | 新進榜 → 60 | Pantheon Stage 3 評估 · 本月中觀察 |
| 16 | 🟢 | **n8n-io/n8n** | 193,535 | — | 2026-06-22（今天） | Pantheon | Raphael「執行交給 n8n」路徑的執行引擎；webhook+cron 完整。 | 60/100 | 拖拉式編排 · webhook/cron 完整 · 自架彈性高 | 自架運維成本 · 與 Pantheon 邊界要先劃清 | 今日仍有 push · ⭐193,535 | 新進榜 → 60 | Raphael Phase 2 評估 · Stage 2 後 |
| 17 | 🟢 | **obra/superpowers** | 235,122 | — | 2026-06-22（今天） | Pantheon | Skill 生態系參考來源；可以餵入 agent-config 的 skill templates。 | 60/100 | 活躍社群 · 與生態系契合 · 文件齊全 | 整合工作量需評估 · 版本相容需確認 | 今日仍有 push · ⭐235,122 | 92 → 60（-32） | 監控 release · 下次 Gstar 再評 |
| 18 | 🟢 | **santifer/career-ops** | 55,073 | — | 2026-06-22（今天） | Aletheia | PM career / 知識管理流程模板；Aletheia 結構化參考。 | 60/100 | 活躍社群 · 與生態系契合 · 文件齊全 | 整合工作量需評估 · 版本相容需確認 | 今日仍有 push · ⭐55,073 | 80 → 60（-20） | 監控 release · 下次 Gstar 再評 |
| 19 | 🟢 | **microsoft/ai-agents-for-beginners** | 67,683 | — | 2026-06-18（3天前） | Pantheon | MS 教材；Stage 3 培訓自己或新成員時的快速 onboarding。 | 60/100 | 活躍社群 · 與生態系契合 · 文件齊全 | 整合工作量需評估 · 版本相容需確認 | 近 3 日內活躍 · ⭐67,683 | 新進榜 → 60 | 監控 release · 下次 Gstar 再評 |
| 20 | 🟢 | **upstash/context7** | 57,822 | — | 2026-06-19（2天前） | ✅已導入 / Aletheia | 為 Aletheia 提供 LLM-ready library docs；補強 RAG knowledge layer。 | 60/100 | LLM-ready docs · 多語言支援 · 對 LiteLLM 友善 | 需 API key · 部分 SDK 文件覆蓋不足 | 近 3 日內活躍 · ⭐57,822 | 88 → 60（-28） | Aletheia QMD 安裝後評估串接 · 下週 |

---

## 更新訊號摘要

- **熱度持續上升**：langgraph、hermes-agent、claude-mem 為本週 push 活躍前段
- **持續對焦的整合候選**：claude-mem（取代 openmemory）、context7（強化 RAG）、gitnexus（個人知識圖譜）
- **長尾觀察**：crewAI（架構對照）、n8n（執行層）、browser-use（Pantheon Stage 3）

---

## 行動建議時程

| 時程 | 動作 |
|------|------|
| 本週 | Issue #25 修復 → S1-NS-1 解鎖；Raphael Hermes Agent 安裝 |
| 下週 | Aletheia QMD 安裝；context7 串接 PoC |
| Sprint 1 結尾 | claude-mem PoC 啟動 |
| Stage 2 後段 | gitnexus 接入 Aletheia |
| Stage 3 | crewAI vs LangGraph 對照；browser-use 評估 |

---

*Generated by Gstar skill · live GitHub API data · no caching*
