# NTU Mail Reference

NTU Mail uses Roundcube webmail.

## URL
- `wmail1.cc.ntu.edu.tw/rc/index.php`
- `ntumail.cc.ntu.edu.tw` redirects here

## Authentication
- **Separate from NTU SSO** — needs its own login
- Username: student ID (e.g., `r14944035`, no @domain)
- Password: NTU password
- Login form has two text inputs + LOGIN button
- If user is already logged in, snapshot will show inbox

## Extraction
1. Navigate to `wmail1.cc.ntu.edu.tw`
2. `take_snapshot` — check for LOGIN button (not logged in) vs inbox content (logged in)
3. If not logged in: ask user for credentials or to log in manually
4. Once in inbox, `take_snapshot` to read emails
5. Click on individual emails to read full content if needed

## Rules
- Never attempt to send, delete, or modify emails
- All data stays on the user's local machine
