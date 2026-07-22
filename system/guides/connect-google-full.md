# Level up Google — edit Sheets & Docs (advanced, optional)

> ⚠️ **This is the advanced path.** The one-click Connectors you set up during onboarding let the
> assistant **read** your Drive, Docs, and Sheets. To let it **create and edit** Sheets & Docs, you
> connect a small local "MCP server" called **workspace-mcp**. This one **does** need a terminal, a
> runtime (Python or Node), and a free Google Cloud project. Plan ~30 minutes. It's more fiddly on
> Windows. You don't need this for everyday use — do it only if you specifically want editing.
>
> The assistant will walk you through it if you say **"level up google"**. If a step looks
> different or errors, paste a screenshot and ask "what next?".
>
> The most up-to-date, official steps live at **https://workspacemcp.com/quick-start** — if this
> guide and that page ever disagree, trust the website.

---

## 🇬🇧 English

**What you'll do:** create a free Google Cloud project → turn on the Google APIs → make an OAuth
"Desktop" credential → run the workspace-mcp server → connect it to Claude → test an edit.

**Before you start:** you need either **Python 3.11+** (with `uvx`) **or** **Node.js 22+** (with
`npx`). If you have neither, install Python from [python.org/downloads](https://www.python.org/downloads/)
(tick "Add python.exe to PATH" on Windows), then reopen your terminal.

1. **Create a Google Cloud project.** Go to
   [console.cloud.google.com](https://console.cloud.google.com/) → sign in → top bar → **New
   Project** → name it (e.g. "My Claude Workspace") → **Create**.
2. **Enable the APIs.** In the search bar enable each of: **Google Drive API**, **Google Docs API**,
   **Google Sheets API**, and (optional) **Gmail API**, **Google Calendar API**. (APIs & Services →
   Library → search → Enable.)
3. **Set up the OAuth consent screen.** APIs & Services → **OAuth consent screen** → choose
   **External** → fill the app name + your email → add yourself as a **Test user** → save.
4. **Create the credential.** APIs & Services → **Credentials** → **Create credentials** → **OAuth
   client ID** → application type **Desktop app** → **Create** → **Download JSON**. Save it somewhere
   you'll remember (e.g. this kit folder) as `client_secret.json`.
5. **Run the server** (in a terminal, from a folder that can see your `client_secret.json`):
   - Python: `uvx workspace-mcp --transport streamable-http`
   - or Node: `npx @workspace-mcp/server --transport streamable-http`
   It should say it's listening on `http://localhost:8000`. Leave this window open.
6. **Connect it to Claude** (new terminal window):
   `claude mcp add --transport http workspacemcp http://localhost:8000/mcp`
   The first time you use a Google tool, a browser opens — **sign in and Allow**.
7. **Test it.** Back in Claude, say: *"Create a Google Sheet called 'Test' and put my name in A1."*
   If a real Sheet appears in your Drive, you're done. To see the tools, run `claude mcp list`.

**Heads-up (Windows):** `uvx`/Python paths trip people up; if `uvx` isn't found, close and reopen the
terminal after installing Python, or use the Node option. **Security:** this gives an AI **write**
access to your Google — only do it on your own account, and you can remove it any time with
`claude mcp remove workspacemcp` and by deleting the credential in Google Cloud.

---

## 🇷🇺 Русский

**Что сделаем:** создадим бесплатный проект Google Cloud → включим нужные Google API → создадим
OAuth-ключ типа «Desktop» → запустим сервер workspace-mcp → подключим его к Claude → проверим
редактирование.

**Перед началом:** нужен либо **Python 3.11+** (с `uvx`), либо **Node.js 22+** (с `npx`). Если нет
ни того ни другого — поставь Python с [python.org/downloads](https://www.python.org/downloads/) (на
Windows отметь «Add python.exe to PATH»), затем переоткрой терминал.

1. **Создай проект Google Cloud.** [console.cloud.google.com](https://console.cloud.google.com/) →
   войди → сверху **New Project** → назови (например, «My Claude Workspace») → **Create**.
2. **Включи API.** В поиске включи по очереди: **Google Drive API**, **Google Docs API**,
   **Google Sheets API** и (по желанию) **Gmail API**, **Google Calendar API**. (APIs & Services →
   Library → найти → Enable.)
3. **Настрой окно согласия OAuth.** APIs & Services → **OAuth consent screen** → **External** →
   впиши название приложения и свою почту → добавь себя в **Test users** → сохрани.
4. **Создай ключ.** APIs & Services → **Credentials** → **Create credentials** → **OAuth client ID**
   → тип **Desktop app** → **Create** → **Download JSON**. Сохрани как `client_secret.json` в удобном
   месте (например, в папке этого кита).
5. **Запусти сервер** (в терминале, из папки, где лежит `client_secret.json`):
   - Python: `uvx workspace-mcp --transport streamable-http`
   - или Node: `npx @workspace-mcp/server --transport streamable-http`
   Должна появиться строка про `http://localhost:8000`. Не закрывай это окно.
6. **Подключи к Claude** (новое окно терминала):
   `claude mcp add --transport http workspacemcp http://localhost:8000/mcp`
   При первом использовании откроется браузер — **войди и нажми Allow**.
7. **Проверь.** В Claude скажи: *«Создай Google-таблицу "Test" и впиши моё имя в A1.»* Если в твоём
   Диске появилась настоящая таблица — готово. Список инструментов: `claude mcp list`.

**Важно (Windows):** часто спотыкаются на путях `uvx`/Python; если `uvx` не находится — переоткрой
терминал после установки Python или используй вариант с Node. **Безопасность:** так ИИ получает право
**изменять** твой Google — делай это только на своём аккаунте. Убрать можно в любой момент:
`claude mcp remove workspacemcp` и удалив ключ в Google Cloud.

---

*Официальные и самые свежие шаги: https://workspacemcp.com/quick-start*
