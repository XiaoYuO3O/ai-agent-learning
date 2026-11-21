# Antigravity 專案工作藍圖

> 本文件用於記錄「ai agent學習ai agent」專案的目標、架構設計、開發階段與進度追蹤，同時作為與 AI Agent 協作時的核心參考上下文。

---

## 1. 專案概述

- **專案名稱**：ai agent學習ai agent
- **建立日期**：2026-11-22
- **專案定位**：以 AI Agent 學習 AI Agent，建置 Antigravity 全域工作流設定，並透過 `@sensebar`（三師爸）YouTube 頻道字幕建立三層式知識庫（Second Brain）。
- **核心目標**：
  - [x] 目標一：建立專案工作藍圖 `Antigravity.md` 與 Antigravity 全域規則 `GEMINI.md`
  - [x] 目標二：建立三個全域工作流 Skills（`init-project`、`start-work`、`end-work`）
  - [x] 目標三：複製並執行 `sensebar-agent-knowledge-vault-builder`，完成 `@sensebar` AI 相關影片清單與字幕逐字稿抓取
  - [ ] 目標四：整理 `Clipping/` 逐字稿，在 `知識庫/` 建立結構化主題筆記、總索引（`Index`）與紀錄（`Log`）

---

## 2. 上次進度與下一步

### 上次進度（2026-11-22）
1. **專案與全域規則建置**：
   - 建立專案工作藍圖 `Antigravity.md` 與 `.gitignore`，並初始化 Git 版本控制。
   - 建立全域規則檔 `/Users/carol/Downloads/ai agent/GEMINI.md`（透過 `~/.gemini/GEMINI.md` 符號連結套用至全機），設定語言偏好為**繁體中文**、GitHub 帳號為 `XiaoYuO3O`。
2. **全域 Skills 建立**（存放於 `~/.gemini/config/skills/`）：
   - `init-project`（觸發詞：初始化專案／專案初始化）
   - `start-work`（觸發詞：開工／我來了／上次做到哪／我們繼續／接下來）
   - `end-work`（觸發詞：收工／下班／同步／換電腦繼續做）
3. **三師爸 AI Agent 知識庫建置（`sensebar-agent-knowledge-vault-builder/`）**：
   - 執行 `extract_videos.py`：掃描 `@sensebar` 頻道共 551 支影片／直播，篩選出 **113 支** AI Agent 相關影片，更新 `sensebar_ai_videos.md`、`sensebar_all_videos.md` 與 `sensebar_ai_urls.txt`。
   - 執行 `download_all_subs.py`（使用 `uv` Python 3.12 + 最新 `yt-dlp`）：完成 `Clipping/` 共 **113 份** `.md` 逐字稿（新下載並清理 20 份、已存在跳過 88 份、無字幕佔位 5 份）。

### 下一步待辦（Next Steps）
1. **知識庫結構化整理**：掃描 `sensebar-agent-knowledge-vault-builder/Clipping/` 內的 113 份逐字稿，提取摘要、關鍵字與主題，寫入 `知識庫/`（包含 `Index.md` 與 `Log.md`）。
2. **設定 GitHub 遠端倉庫**：在 GitHub（帳號 `XiaoYuO3O`）建立對應遠端 repo 並綁定 `git remote add origin`，完成首次遠端推送。
3. **運用知識庫學習與實作**：透過整理好的三師爸 AI Agent 知識庫，進行後續 AI Agent 專案實作。

---

## 3. 技術選型與系統架構

- **AI Agent 平台**：Google Antigravity
- **程式語言與環境**：Python 3.12（透過 `uv` 執行）、`yt-dlp`
- **知識庫架構（三層式 Obsidian Vault）**：
  - `Clipping/`：YouTube 字幕原始逐字稿（只讀不修改）
  - `創作庫/`：自訂教材、講義、腳本（只讀不修改）
  - `知識庫/`：由 Agent 維護的結構化知識、主題分類、索引與紀錄

---

## 4. 專案目錄結構

```text
ai agent學習ai agent/
├── Antigravity.md                              # 專案工作藍圖與進度紀錄
├── .gitignore                                  # Git 忽略規則
└── sensebar-agent-knowledge-vault-builder/     # 三師爸 AI Agent 影片字幕知識庫
    ├── CLAUDE.md / agents.md / README.md       # Agent 知識庫規則與操作說明
    ├── extract_videos.py                       # 頻道影片掃描與關鍵字過濾腳本
    ├── download_all_subs.py                    # 字幕下載與 VTT 去重清理腳本
    ├── sensebar_ai_urls.txt                    # 篩選出的 113 支 AI 影片網址
    ├── sensebar_ai_videos.md                   # AI 相關影片清單表格
    ├── sensebar_all_videos.md                  # 頻道全部 551 支影片清單
    ├── Clipping/                               # 113 份清理後的影片逐字稿 (.md)
    ├── 創作庫/                                  # 自訂教材與文稿區
    └── 知識庫/                                  # Agent 整理的結構化知識區
```

---

## 5. 工作階段與里程碑（Roadmap）

### Phase 1：專案初始化與全域環境建置
- [x] 建立 `Antigravity.md` 專案工作藍圖
- [x] 建立全域規則 `GEMINI.md`（繁體中文、GitHub 帳號 `XiaoYuO3O`）
- [x] 建立三個全域工作流 Skills（`init-project`、`start-work`、`end-work`）
- [x] 初始化專案 Git 與 `.gitignore`

### Phase 2：知識庫資料擷取（Data Ingestion）
- [x] 複製 `sensebar-agent-knowledge-vault-builder`
- [x] 執行 `extract_videos.py` 取得最新 113 支 AI 相關影片清單
- [x] 執行 `download_all_subs.py` 補齊所有最新影片字幕逐字稿至 `Clipping/`

### Phase 3：知識庫結構化與應用
- [ ] 消化 `Clipping/` 逐字稿，於 `知識庫/` 建立主題分類筆記、`Index.md` 與 `Log.md`
- [ ] 設定 GitHub 遠端倉庫（`XiaoYuO3O`）並同步推送
- [ ] 結合知識庫內容進行 AI Agent 實戰練習

---

## 6. AI Agent 協作規範

- **語言偏好**：文件、註解、Commit 訊息與回覆預設使用繁體中文。
- **知識庫規則**：回答三師爸觀點或 `@sensebar` 影片內容前，必須先查閱 `Clipping/` 逐字稿，且絕不修改或刪除 `Clipping/` 與 `創作庫/` 內的原始檔案。
- **更新原則**：每次「收工」時同步更新本文件的進度、下一步與變更紀錄。

---

## 7. 決策與變更紀錄

| 日期 | 類型 | 說明 |
| :--- | :--- | :--- |
| 2026-11-22 | 初始化 | 建立 `Antigravity.md` 工作藍圖初稿 |
| 2026-11-22 | 全域設定 | 將全域 `GEMINI.md` 移至 `/Users/carol/Downloads/ai agent/GEMINI.md`（保留 `~/.gemini/GEMINI.md` 符號連結），新增繁體中文與 GitHub `XiaoYuO3O` 設定，並建立 `init-project`、`start-work`、`end-work` 三個全域 Skills |
| 2026-11-22 | 知識庫更新 | 複製並執行 `sensebar-agent-knowledge-vault-builder`，掃描 551 支影片、篩選 113 支 AI 影片，新下載 20 份字幕逐字稿至 `Clipping/` |
| 2026-11-22 | 收工盤點 | 更新 `Antigravity.md` 進度與下一步，完成本地 Git 初始化與版本提交 |
