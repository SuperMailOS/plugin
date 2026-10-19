# SuperMailOS

Work your SuperMailOS business email from a conversation: catch up on what's unread, find any email or attachment, draft replies in your voice, track who owes you an answer, and send from your company address when you say so.

SuperMailOS is managed business email on your own domains. This plugin connects to your SuperMailOS mailboxes and adds skills that teach the assistant how to use them well.

## What's inside

- **SuperMailOS connector**: the hosted SuperMailOS MCP server at `https://supermailos.com/mcp`. You sign in to SuperMailOS and approve what it may do (read mail; organize mail and save drafts; send mail). You can tick fewer permissions than it asks for.
- **Skills**
  - `getting-started`: shows which mailboxes are connected and what this connection may do.
  - `inbox-triage`: sorts unread mail into "needs a reply", "needs a look" and "low priority", then offers to mark read, archive or label, only after you confirm.
  - `mail-search`: finds conversations and attachments with search operators such as `from:`, `subject:`, `has:attachment` and date ranges.
  - `reply-drafting`: writes replies as drafts by default; sends only when you explicitly ask.
  - `follow-ups`: lists conversations where you're waiting on someone and ones where someone is waiting on you.

## Requirements

A SuperMailOS account (https://supermailos.com). The connection acts as you, with your current access: you see the mailboxes you can open in SuperMailOS, nothing more. Workspace owners and admins can reach every mailbox in their workspace.

## Install

- **Claude** (web, desktop, mobile): add SuperMailOS from the Claude directory.
- **Claude Code**: `/plugin marketplace add SuperMailOS/plugin`, then `/plugin install supermailos@supermailos`.
- **GitHub Copilot CLI**: `copilot plugin marketplace add SuperMailOS/plugin`, then `copilot plugin install supermailos@supermailos`.
- **Gemini CLI**: `gemini extensions install https://github.com/SuperMailOS/plugin`.
- **Cursor**: this repository is a Cursor plugin (`.cursor-plugin/plugin.json`).
- **Any other MCP client**: connect to `https://supermailos.com/mcp` (Streamable HTTP). Clients with OAuth sign in to SuperMailOS in the browser; others send a SuperMailOS API key as `Authorization: Bearer smk_...`. Setup for each app: https://supermailos.com/docs/mcp. Step-by-step for an assistant installing it: [llms-install.md](llms-install.md).

## Use it

After installing, connect SuperMailOS and approve the sign-in. Then try:

- "What needs my attention in my inbox today?"
- "Find the last invoice from Acme and tell me the total."
- "Draft a reply to Priya saying Thursday at 3pm works."
- "Who hasn't replied to me this week?"

Reading mail never marks it as read. Replies are saved as drafts in SuperMailOS for you to review; mail is sent only when you clearly ask, because a sent email can't be recalled.

## Data and privacy

This plugin contains only instructions (skills) and the address of the SuperMailOS server. It runs no code on your computer and stores nothing itself.

When the assistant calls a SuperMailOS tool, the request goes to `supermailos.com` over HTTPS, signed in as you. SuperMailOS returns the mail you asked for (subjects, senders and recipients, dates, message text and, when you open one, an attachment) to the assistant you connected. From there it is processed by that assistant under your agreement with its provider. Bcc recipients are shown only to the person who sent the message or was Bcc'd.

SuperMailOS stores a record of the connection (which app, the permissions you approved, when it was last used) and one-way hashes of its tokens. You can disconnect at any time in SuperMailOS under Settings, Connected apps.

- Privacy policy: https://supermailos.com/privacy
- Terms: https://supermailos.com/terms
- Documentation: https://supermailos.com/docs/mcp
- Support: https://supermailos.com/contact (hello@supermailos.com)

## Safety

Emails are written by other people and can contain text meant to manipulate an assistant. The skills treat email content as information to report, never as instructions to follow, and the send tools are separate from the read tools so your assistant can ask before anything leaves your mailbox. To be strictest, connect without the "send mail" permission: the assistant can then only save drafts.

## License

MIT. See [LICENSE](LICENSE).
