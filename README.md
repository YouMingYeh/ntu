# NTU Assistant — Agent Skill

每學期開學，你大概都得在 COOL、myNTU、Mail、ePortfolio 四個系統之間反覆跳轉，手動整理課程資訊。這個 skill 幫你用一句話搞定——它透過 Chrome DevTools MCP 直接從各系統抓資料，整理成 Markdown 檔案。

Every semester, NTU students manually hop between COOL, myNTU, Mail, and ePortfolio to piece together their course info. This skill does it for you — it pulls data from each system via [Chrome DevTools MCP](https://github.com/nicolo-nicolo/chrome-devtools-mcp) and organizes everything into Markdown files.

支援 Claude Code、Codex、OpenCode、Cursor、Copilot 等所有 [skills](https://skills.sh) 相容的 AI agent。

## 功能 / What it does

從 NTU COOL 抓課程、公告、教材（走 Canvas API），從 myNTU 拉課表，把所有作業截止日期整理成一份清單。也可以選擇自動下載 PDF 教材。Mail 只抓信件標題和寄件人，不碰內文。ePortfolio 的學分追蹤也有。

最後產出長這樣：

```
your-project/
├── COURSE_SUMMARY.md      # 課程總覽
├── schedule.md            # 週課表
├── deadlines.md           # 截止日期（按時間排序）
├── Course_Name/
│   ├── Week1/             # 下載的教材
│   ├── Week2/
│   └── Homework/
```

## 前置需求 / Prerequisites

1. 任何支援 skills 的 AI agent（Claude Code、Codex、OpenCode、Cursor 等）
2. Chrome DevTools MCP server

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

## 使用 / Usage

開一個對話，直接說：

```
幫我同步 NTU COOL 的課程資料
```

```
Sync my NTU COOL courses
```

它會先確認 Chrome MCP 有連上，然後檢查你有沒有登入（登入永遠是你自己在 Chrome 裡操作，skill 不會碰密碼），接著用 Canvas REST API 抓資料，最後在你的目錄下產生整理好的 Markdown 檔案。

跟 NTU 相關的指令都會觸發這個 skill，像是「課表」「公告」「成績」「作業截止日期」「下載教材」「新學期」之類的。

## 安全 / Security

- 登入都是你自己在 Chrome 裡手動操作，skill 不會自動填密碼
- 資料透過 Canvas REST API 抓取，用的是你瀏覽器的 session
- Mail 只讀標題、寄件人、日期，不讀信件內容
- 所有資料都留在你的電腦上

## License

MIT
