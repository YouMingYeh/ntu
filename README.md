# NTU Assistant — Agent Skill

NTU 的 AI 助手。幫你查課程、抓教材、整理作業、看成績、讀信，什麼都能問。它會自己操作 Chrome 去 COOL、myNTU、Mail、ePortfolio 幫你把資料抓回來。

Your AI assistant for NTU. It controls Chrome to pull data from COOL, myNTU, Mail, and ePortfolio — ask it anything about your courses, assignments, grades, or emails.

## 功能 / What it does

- 查課程資訊、公告、成績
- 下載講義、簡報、PDF
- 整理課表、作業截止日期
- 讀 NTU Mail 信件
- 查學分進度
- 做成一頁式課程總覽網頁

## 事前準備 / Before you start

1. 裝好 [Node.js](https://nodejs.org/)（v20 以上）
2. 裝好一個支援 skills 的 AI 工具（[Claude Code](https://claude.com/claude-code)、Codex、Cursor 等都行）
3. 讓 AI 工具可以操作 Chrome — 在終端機貼上這行：

```bash
claude mcp add chrome-devtools -- npx chrome-devtools-mcp@latest
```

這會讓 AI 工具在需要時自動打開 Chrome 幫你操作，不用自己手動開。

<details>
<summary>其他 AI 工具的設定方式</summary>

找到你的 AI 工具的 MCP 設定檔，加入：

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

</details>

## 安裝 / Install

在終端機輸入：

```bash
npx skills add YouMingYeh/ntu
```

安裝過程會問你幾個問題，**全部按 Enter 就好。**

更新到最新版：

```bash
npx skills update
```

<details>
<summary>手動安裝</summary>

```bash
git clone https://github.com/YouMingYeh/ntu.git ~/.claude/skills/ntu
```

</details>

## 怎麼用 / Usage

打開 AI 工具，輸入 `/ntu` 就好。什麼都不加，它會列出所有能幫你做的事讓你選。也可以直接加上你想做的事：

```
/ntu
```
```
/ntu 幫我下載所有課程教材
```
```
/ntu 整理課表和近期作業
```
```
/ntu 這週有什麼作業要交？
```
```
/ntu 新學期，幫我同步所有課程
```
```
/ntu 幫我看成績
```

英文也行：

```
/ntu Download all course materials
```
```
/ntu What's due this week?
```

第一次用的時候，它會自動打開 Chrome，然後問你要不要給帳密幫你登入 NTU，或你自己先在 Chrome 登入好再告訴它。登入一次之後，各個 NTU 系統就都通了。

## 安全 / Security

- 帳密只用來當場在 Chrome 填入登入，不會存在任何地方
- 所有資料都在你自己的電腦上處理

## 推薦搭配 / Recommended skills

不知道 skills 是什麼？可以先看 [skills.sh](https://skills.sh/)。

其他好用的 skills：

- [anthropics/skills](https://github.com/anthropics/skills) — 處理 PDF、Word、PPT、Excel
- [blader/humanizer](https://github.com/blader/humanizer) — 英文文章去 AI 味
- [kevintsai1202/Humanizer-zh-TW](https://github.com/kevintsai1202/Humanizer-zh-TW) — 中文文章去 AI 味

裝法都一樣：

```bash
npx skills add anthropics/skills
npx skills add blader/humanizer
npx skills add kevintsai1202/Humanizer-zh-TW
```

## License

MIT
