# NTU Mail Reference

NTU Mail: `https://ntumail.cc.ntu.edu.tw/`

NTU provides email via Microsoft 365 (Outlook Web App) or a legacy webmail interface.

## URL
- Primary: `https://ntumail.cc.ntu.edu.tw/` (redirects to M365 login or webmail)
- M365 direct: `https://outlook.office365.com/` (if NTU uses M365)

## Authentication
- Uses NTU SSO or Microsoft login
- `take_snapshot` after navigation to check:
  - Login page indicators: "Sign in", "登入", email/password fields
  - Inbox indicators: "Inbox", "收件匣", unread count, email subjects

## Extraction Approach

### Snapshot-based
1. Navigate to inbox
2. `take_snapshot` to get accessibility tree
3. Parse for:
   - Unread email count
   - Recent email subjects (last 10-20)
   - Sender names and dates
   - Email body content (if user requests)

### What to extract
- Total unread count
- List of recent emails: subject, sender, date, read/unread status
- Flagged/important emails if visible
- Email body content when the user asks for it

### Output format
```markdown
## NTU Mail Summary
**Unread:** 5 emails

| Date | From | Subject | Status |
|------|------|---------|--------|
| 2026-03-13 | 廖世偉 | Week 3 作業提醒 | Unread |
| 2026-03-12 | 教務處 | 114-2 選課公告 | Read |
```

## Rules
- Never attempt to send, delete, or modify emails
- All data stays on the user's local machine
