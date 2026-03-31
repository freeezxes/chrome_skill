---
name: chrome_skill
description: use for tasks that require interacting with google chrome on macos through the real browser ui, including opening chrome, switching windows or tabs, navigating to sites, reading page content, clicking controls, filling forms, downloading files, checking web app state, or continuing an existing browser session with the user’s signed-in chrome profile on a mac.
---

# Chrome on Mac

Use the existing Google Chrome app on macOS instead of simulated browsing whenever the task depends on the real browser session, visible page state, installed extensions, saved cookies, downloads, or interaction with a live web app.

## Operating rules

- Verify that the environment is a Mac and that Google Chrome is installed before attempting browser work.
- Prefer the user's existing Chrome session and profile.
- Bring Chrome to the foreground before interacting with tabs or page controls.
- Reuse an already-open relevant tab when possible instead of opening duplicates.
- Keep actions minimal and reversible.
- Describe what was observed and what was done after each meaningful step.
- If Chrome is not installed, not accessible, or the environment does not support direct Mac app control, say so plainly and stop.

## Safety and consent

- Never log the user out, clear cookies, close unrelated tabs, or change Chrome settings unless explicitly asked.
- Never submit purchases, financial transactions, destructive account changes, or irreversible actions without explicit user confirmation in the current conversation.
- Never reveal passwords, session tokens, cookies, or hidden credentials.
- Treat email, calendar, admin consoles, banking, production dashboards, and personal accounts as high-sensitivity surfaces. Move slowly and only perform the exact requested action.
- If a page requests a login, prefer the user’s existing session. If manual login is required, pause and let the user complete authentication.
- If a site shows sensitive personal data unrelated to the task, avoid repeating it back unless needed.

## Default workflow

### 1) Confirm readiness

- Check that macOS app control is available.
- Check that Google Chrome is installed.
- Open Chrome if it is not already running.
- Bring Chrome to the front.

### 2) Establish browser context

- Inspect currently open windows and tabs.
- Identify whether the target site is already open.
- Reuse the most relevant tab if it is already in the correct account or workspace.
- Otherwise open a new tab and navigate to the requested URL or search target.

### 3) Interact with the page

- Wait for the page to finish loading before acting.
- Read visible page structure first: title, primary navigation, main content, dialogs, and blocking banners.
- Dismiss cookie banners or popups only when needed to continue.
- Click, type, scroll, and switch tabs deliberately.
- When filling forms, preserve the user’s requested wording exactly unless asked to improve it.

### 4) Verify outcome

- Confirm that the expected page, state, or result is visible.
- Report any errors, blockers, missing permissions, or unexpected redirects.
- Mention downloads, uploads, or drafts created if relevant.

## Interaction preferences

- Prefer direct URLs when the user names a known site.
- Prefer browser search only when the destination is unclear.
- Prefer opening results in a new tab when it helps preserve the user’s current context.
- Prefer reading the current page before navigating away.
- Prefer visible UI actions over hidden shortcuts unless speed clearly matters.

## Handling common browser tasks

### Open a site
- Open Chrome.
- Focus the address bar.
- Navigate directly to the requested URL or destination.
- Confirm the loaded page.

### Continue an existing session
- Inspect open tabs for the named service or workspace.
- Reuse the tab that appears already signed in.
- Confirm account or workspace context from visible page cues.

### Read or inspect a web app
- Summarize the visible page structure first.
- Identify key controls, status badges, tables, filters, or dialogs.
- Answer from the current page before taking extra actions.

### Fill a form
- Read all required fields before typing.
- Fill only the requested fields.
- Re-check entered values before submitting.
- Do not submit without confirmation if submission is consequential.

### Download a file
- Trigger the download.
- Confirm that the download started or completed.
- Report the likely filename and source page.

### Upload a file
- Verify the requested file path or chosen file.
- Use the site’s upload control.
- Confirm that the upload appears complete.

## Robustness rules

- If a click has no visible effect, re-check focus, overlays, disabled states, and load status before retrying.
- If the page changes unexpectedly, describe the new state and continue from there.
- If multiple accounts or workspaces are visible, choose the one most clearly matching the user’s request and say which one was used.
- If the task depends on a popup window, permissions prompt, file picker, or download shelf, handle that native UI explicitly.
- If Chrome crashes or becomes unresponsive, reopen it and restore the task context as closely as possible.

## Output format

For browser tasks, respond with:

1. **Context used** — which tab, site, account, or workspace was used.
2. **Actions taken** — the key browser actions performed.
3. **Result** — what is now visible or completed.
4. **Blockers** — anything preventing completion.
5. **Next choice** — only if the next step is consequential.

## Examples

### Example: open a web app
User: Open Linear in Chrome on my Mac and check my assigned issues.

Behavior:
- Bring Chrome to the foreground.
- Reuse an existing Linear tab if present and signed in.
- Otherwise open Linear in a new tab.
- Navigate to assigned issues.
- Summarize what is visible.

### Example: continue a draft
User: In Chrome, open Gmail and continue the draft to Anna.

Behavior:
- Reuse the signed-in Gmail tab if present.
- Locate the draft list or open draft.
- Stop before sending unless the user explicitly asks to send.

### Example: submit a form carefully
User: Open the vendor portal in Chrome and fill in this application.

Behavior:
- Open or reuse the correct portal tab.
- Read the form structure.
- Fill fields exactly from provided data.
- Re-check values.
- Ask for confirmation only at the final irreversible submit step if submission is consequential.
