# GitHub Starred Repos Review — Gstar
**Version:** v20260605
**Date:** 2026-06-05
**Author:** salafadidas (Vernon)
**Scope:** 58 starred repositories · Live data fetched from GitHub API
**Skill:** Gstar v2 (live check + mandatory Top 20)
**Delta vs v20260605:** No new repos · All 58 repos live-status confirmed

---

## 專案宇宙概覽

| 專案 | 狀態 | 技術棧 |
|------|------|--------|
| **Project Pantheon** | 🚧 Stage 2 Sprint (v4.0) | LangGraph + FastAPI + Redis + GCP Cloud Run + PostgreSQL + Playwright MCP |
| **Aletheia** | 🚧 Active | FastAPI + LiteLLM + Notion SDK + Google Drive + GitHub MCP + Filesystem MCP |

---

## PART 1｜已確認導入的 Starred Repos（Live 確認）

| # | Repo | ⭐ | 狀態 | 導入專案 | 導入證據 | 契合度 | 活躍度警告 |
|---|------|---|------|----------|----------|--------|-----------|
| 1 | **francescofano/langgraph-telegram-bot** | 9 | ⚪ 446天 | Pantheon | Fork 來源；requirements.txt: python-telegram-bot, langgraph | 90/100 | ⚠️ Upstream 停更 446 天，Pantheon 已完全超越，無需追蹤 |
| 2 | **abhigyanpatwari/GitNexus** | 41,380 | 🟢 今天 | Pantheon | AGENTS.md 完整整合；999 symbols, 2292 relationships, 65 flows | 95/100 | ✅ 今天仍更新，穩定 |
| 3 | **vancelin/openmemory** | 101 | ⚪ 65天 | Pantheon | .mcp.json: openmemory http://localhost:8080/mcp | 80/100 | ⚠️ 停更 65 天，評估 claude-mem 作替代 |
| 4 | **Zie619/n8n-workflows** | 54,968 | 🟢 5天 | 獨立 Fork | salafadidas/n8n-workflows fork (2025-08-17) | 85/100 | ✅ 持續更新 |
| 5 | **nashsu/llm_wiki** | 10,481 | 🟢 1天 | Aletheia | CLAUDE.md: "Karpathy LLM Wiki pattern"；wiki/ingest.py | 96/100 | ✅ 昨天更新 |

---

## 更新訊號摘要（v20260605 → v20260605）

| 訊號 | Repo | 變化 | 建議 |
|------|------|------|------|
| ⚠️ 已導入但停更 65 天 | vancelin/openmemory | 無新 commit | 立即評估 claude-mem 作替代記憶層 |
| 🟢 今天仍活躍 | crewAI / GitNexus / paperclip / hermes-agent / agency-agents / agent-threat-rules / doc-cleaner | 0 天 | 評估優先度持續維持 |
| ⚪ 停更 46 天 | multica-ai/andrej-karpathy-skills | 作者轉向 multica-ai/multica | 追蹤新專案；原 CLAUDE.md 仍可用 |
| 📈 快速成長 | mattpocock/skills +18 / Lum1104/Understand-Anything +18 | 持續上升 | 提升優先度 |
| ⚪ 停更 131 天 | mboverell/ai-chief-of-staff | 無維護 | 降出 Top 20，改為觀察 |

---

## PART 2B｜Top 20 未導入 Repos（Live 評估，2026-06-05）

| 排名 | Repo | ⭐ | 今日變化 | 狀態 | 建議導入專案 | 核心價值 | 契合度 | 優點 | 缺點/風險 | 建議行動 |
|------|------|---|---------|------|------------|----------|--------|------|-----------|---------|
| 🥇 1 | **crewAIInc/crewAI** | 52,868 | +4 | 🟢 今天 | Pantheon Stage 3 | role-based agent 編排；與 Pantheon 角色分工完全吻合 | 93/100 | 文件最完整；v1.14.7a1 迭代中；企業支援 | 與 LangGraph 重疊；遷移成本高 | Stage 3 規劃時評估替代 LangGraph |
| 🥈 2 | **thedotmack/claude-mem** | 80,724 | +4 | 🟢 2天 | Pantheon + Aletheia | 跨 session 記憶；AI 壓縮 context；補充停更的 openmemory | 91/100 | 新增繁中 README；ChromaDB 相容；77k stars | 與 openmemory 功能重疊 | ⭐ 緊急：openmemory 停更，本週評估替代 |
| 🥉 3 | **addyosmani/agent-skills** | 48,334 | +4 | 🟢 3天 | Pantheon | 生產級 skills 直接定義 Pantheon agent skill profile | 87/100 | Google 工程師驗證；44k stars；即插即用 | Shell-based 需轉 Python | 本週：挑 5 個 skills 整合進 AGENTS.md |
| 4 | **Lum1104/Understand-Anything** | 52,301 | +18 | 🟢 1天 | Pantheon | 程式碼知識圖譜；v2.5.0 Dashboard 大改版；已與 GitNexus 差異化 | 88/100 | 昨天更新；52k stars；繁中 README；ELK+lazy containers | 仍有部分與 GitNexus 重疊；TS-Python bridge | ⭐ 本週重新評估：星數暴增已成熟 |
| 5 | **google/skills** | 11,145 | +1 | 🟢 1天 | Pantheon + Aletheia | Google 官方 agent skills；Gmail/Drive 整合直接可用 | 84/100 | Google 官方；Python；昨天 commit | 偏 Google 生態；非通用 orchestration | 本週評估 Gmail/Drive skill 整合進 Aletheia |
| 6 | **rtk-ai/rtk** | 58,970 | +3 | 🟢 2天 | Pantheon + Aletheia | Token 節省 60-90%；多代理人成本控制核心 | 84/100 | Rust 零依賴；59k stars；Apache 2.0；CI 完整 | CLI proxy 架構；LiteLLM 整合待驗證 | Stage 2 前：開發環境先測試 |
| 7 | **paperclipai/paperclip** | 69,142 | +1 | 🟢 今天 | Pantheon | Stage 2 後 agent 管理 UI；多租戶監控儀表板 | 84/100 | 今天更新；69k stars；開源；workplace agent 設計 | 較新；GCP 相容性待確認 | Stage 2 完成後評估整合 |
| 8 | **msitarzewski/agency-agents** | 107,573 | +6 | 🟢 今天 | Pantheon | 完整 AI agency 角色庫；reality checker/wizard 對應 Pantheon | 83/100 | 今天更新；107k stars；附 personality + deliverables | Shell-based 需轉 Python | 本週參考角色定義更新 AGENTS.md |
| 9 | **revfactory/harness** | 6,031 | +9 | 🟢 7天 | Pantheon | meta-skill 自動設計 agent teams；動態生成 Pantheon 角色分工 | 83/100 | 星數+9 成長中；meta-skill 概念創新 | HTML 非 Python；成熟度待觀察 | 評估 harness 作為 Pantheon agent 配置生成器 |
| 10 | **ComposioHQ/awesome-claude-skills** | 63,296 | +5 | 🟢 14天 | Pantheon + Aletheia | Skills 資源庫；MCP + automation 涵蓋廣 | 81/100 | 63k stars；持續更新；MCP 涵蓋廣 | Curated list 需篩選 | 本週瀏覽篩選適用 skills |
| 11 | **mindfold-ai/Trellis** | 9,447 | = | 🟢 3天 | Pantheon | "best agent harness"；Pantheon agent 執行層補充 | 81/100 | 9k stars；3天前更新；agent harness 設計 | 較新；TS-Python bridge 需要 | Stage 2 後評估 Trellis 作為 harness 層 |
| 12 | **Agent-Threat-Rule/agent-threat-rules** | 245 | = | 🟢 今天 | Pantheon | Stage 2 雲端上線安全必備；Prompt injection + MCP security | 80/100 | 今天更新；OWASP 標準；97.1% recall；425 條規則 | 245 stars 成熟度低；規則量大需篩選 | Stage 2 kick-off 前完成 security audit |
| 13 | **multica-ai/andrej-karpathy-skills** | 168,087 | +16 | ⚪ 46天 | Pantheon + Aletheia | CLAUDE.md 即插即用；LLM coding pitfalls 防護 | 82/100 | 168k stars；零整合成本；即插即用 | 停更 46 天；作者轉向 multica-ai/multica | 本週加入 CLAUDE.md；追蹤 multica-ai/multica |
| 14 | **tradecatlabs/vibe-coding-cn** | 14,431 | +3 | 🟢 1天 | Pantheon + Aletheia | AI 結對編程工作流；Prompt/Skill/Workflow 完整指南 | 79/100 | 昨天更新；14k stars；繁中友善 | 教學性質為主；非直接整合工具 | 作為 Pantheon Claude Code 工作流參考 |
| 15 | **ombharatiya/ai-system-design-guide** | 1,660 | +2 | 🟢 今天 | Pantheon | 生產 AI 系統設計指南；Stage 2 架構決策參考 | 77/100 | 今天更新；涵蓋 evals/production AI；實戰導向 | 文件參考性質；非整合工具 | Stage 2 架構設計期閱讀參考 |
| 16 | **mattpocock/skills** | 117,951 | +18 | 🟢 2天 | Pantheon | Real Engineers 生產級 skills；skill 結構設計參考 | 77/100 | 117k stars；2天前更新；Shell-based | 偏 TypeScript；Python 需轉譯 | 下週參考 skill 結構設計 Pantheon agent skills |
| 17 | **upstash/context7** | 56,771 | = | 🟢 1天 | Pantheon + Aletheia | LLM context 文件管理；agents 使用最新 API 文件；MCP-native | 75/100 | 昨天更新；56k stars；MCP-native | 需訂閱 Upstash；token 消耗需控制 | 評估 Aletheia 外部文件來源整合 |
| 18 | **microsoft/ai-agents-for-beginners** | 66,477 | +1 | 🟢 11天 | Pantheon | AutoGen/Semantic Kernel 框架比較；Stage 3 選型參考 | 74/100 | 66k stars；微軟出品；12 lessons | 偏教學；Pantheon 已過初學階段 | Stage 3 框架評估時作為比較基準 |
| 19 | **decolua/9router** | 16,368 | +1 | 🟢 5天 | Pantheon | 多模型 gateway；開發測試降低成本；auto-fallback | 74/100 | 16k stars；5天前更新；40+ providers | 免費服務穩定性；生產不建議 | 開發測試環境使用；生產仍用 LiteLLM |
| 20 | **TauricResearch/TradingAgents** | 83,011 | +6 | 🟢 4天 | Pantheon | multi-agent cross-debate 架構參考；共識機制設計靈感 | 73/100 | 83k stars；4天前更新；cross-debate 機制成熟 | 金融場景；核心邏輯需大量改寫 | Stage 3 架構設計時參考 debate 機制 |

---

## 行動建議時程

| 時程 | 行動 | 對應 Repo |
|------|------|-----------|
| **⭐ 本週緊急** | openmemory 停更 65 天，立即評估 claude-mem 替代 | thedotmack/claude-mem |
| **本週** | karpathy-skills 加入 CLAUDE.md；追蹤 multica-ai/multica | multica-ai/andrej-karpathy-skills |
| **本週** | 挑 5 個 agent-skills + agency-agents 整合進 AGENTS.md | addyosmani/agent-skills, msitarzewski/agency-agents |
| **本週** | 重新評估 Understand-Anything（v2.5.0 Dashboard） | Lum1104/Understand-Anything |
| **本週** | 瀏覽 google/skills + awesome-claude-skills 篩選適用 skills | google/skills, ComposioHQ/awesome-claude-skills |
| **Stage 2 前** | 開發環境測試 rtk token 節省效果 | rtk-ai/rtk |
| **Stage 2 kick-off 前** | 執行 security audit checklist | Agent-Threat-Rule/agent-threat-rules |
| **Stage 2 完成後** | 評估 paperclip + Trellis agent 管理層 | paperclipai/paperclip, mindfold-ai/Trellis |
| **Stage 3 規劃時** | 評估 crewAI 替代 LangGraph | crewAIInc/crewAI |

---

*Generated by Claude · Gstar Skill v2 · v20260605 · 58 repos · Live API data · 2026-06-05*
