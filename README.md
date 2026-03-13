# NTU Assistant — Agent Skill

NTU 的 AI 助手。透過 [Chrome DevTools MCP](https://github.com/ChromeDevTools/chrome-devtools-mcp) 操作 COOL、myNTU、Mail、ePortfolio，幫你查課程、抓教材、整理作業、看成績、讀信——什麼都能問。

Your AI assistant for NTU. It operates COOL, myNTU, Mail, and ePortfolio through Chrome DevTools MCP — ask it anything about your courses, assignments, grades, or emails.

支援 Claude Code、Codex、OpenCode、Cursor、Copilot 等所有 [skills](https://skills.sh) 相容的 AI agent。

## 功能 / What it does

你可以叫它做的事：

- 查課程資訊、公告、成績
- 下載教材、講義 PDF
- 整理課表、作業截止日期
- 讀 NTU Mail 信件
- 查 ePortfolio 學分進度
- 把資料整理成 Markdown 檔案輸出

需要輸出檔案的時候，它會自動建好資料夾結構：

```
your-project/
├── COURSE_SUMMARY.md      # 課程總覽
├── schedule.md            # 週課表
├── deadlines.md           # 截止日期（按時間排序）
├── Course_Name/
│   ├── Week1/             # 下載的教材
│   └── Homework/
```

## 前置需求 / Prerequisites

1. [Node.js](https://nodejs.org/) v20 以上
2. 任何支援 skills 的 AI agent（Claude Code、Codex、OpenCode、Cursor 等）
3. Chrome DevTools MCP server

裝 Chrome DevTools MCP 只要一行：

```bash
# Claude Code
claude mcp add chrome-devtools -- npx chrome-devtools-mcp@latest

# 或手動加到 MCP 設定
```

<details>
<summary>手動 MCP 設定（JSON）</summary>

在你的 MCP 設定檔加入：

```json
{
  "mcpServers": {
    "chrome-devtools": {
      "command": "npx",
      "args": ["-y", "chrome-devtools-mcp@latest"]
    }
  }
}
```

MCP 啟動後會自動開 Chrome，不需要手動跑 `--remote-debugging-port`。

如果要連到已開啟的 Chrome：

```json
{
  "mcpServers": {
    "chrome-devtools": {
      "command": "npx",
      "args": ["-y", "chrome-devtools-mcp@latest", "--browser-url=http://127.0.0.1:9222"]
    }
  }
}
```

</details>

## 安裝 / Install

```bash
npx skills add YouMingYeh/ntu
```

或手動 clone：

```bash
git clone https://github.com/YouMingYeh/ntu.git ~/.claude/skills/ntu
```

更新：

```bash
npx skills update
```

## 使用 / Usage

在對話中輸入 `/ntu` 加上你想做的事：

```
/ntu 幫我下載所有課程教材
```
```
/ntu 幫我整理課表、近期待辦事項、作業和公告
```
```
/ntu 這週有什麼作業要交？
```
```
/ntu 新學期開始了，幫我同步所有課程資料
```
```
/ntu 把 COOL 上面的成績整理給我看
```

英文也行：

```
/ntu Download all my course materials from COOL
```
```
/ntu What assignments are due this week?
```

第一次用的時候，它會確認 Chrome MCP 有沒有連上，然後幫你登入（你可以直接給帳密，或自己在 Chrome 裡登入）。之後就直接用。

> **安裝提示：** `npx skills add` 過程中會問幾個問題，全部按 Enter 用預設值就好。

## 安全 / Security

- 帳密只用來在 Chrome 登入，不會另外儲存
- 所有資料都在你本機處理，不上傳到任何地方

## 相關資源 / Resources

不知道 skills 是什麼的話，可以先看這些：

- [skills.sh](https://skills.sh/) — skills 搜尋引擎，找找有什麼好用的
- [anthropics/skills](https://github.com/anthropics/skills) — Anthropic 官方 skills，PDF、Word、PPT、Excel 文件處理都有

寫報告或文章的時候，AI 味太重？這兩個 skill 可以幫你修：

- [blader/humanizer](https://github.com/blader/humanizer) — 英文去 AI 味
- [kevintsai1202/Humanizer-zh-TW](https://github.com/kevintsai1202/Humanizer-zh-TW) — 中文去 AI 味

裝法都一樣：

```bash
npx skills add anthropics/skills
npx skills add blader/humanizer
npx skills add kevintsai1202/Humanizer-zh-TW
```

## License

MIT
