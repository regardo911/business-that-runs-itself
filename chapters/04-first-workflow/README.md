<!-- Chapter 4, Your First Workflow in 30 Minutes. Install, "set me up", first read-only run, the troubleshooting lines and the 8-line checklist. Source: ch04.md:9-147 -->
# Chapter 4: your first workflow

Set a 30-minute timer. You leave with one real brief on your own business, and nothing sent, paid or changed.

**1. Install Cowork.** It's the Claude desktop app for Mac or Windows. Sign in with your paid Claude account. The plugin runs there, in the desktop app, and not in the browser.

**2. Add the Small Business plugin.** In Cowork: from claude.com/plugins, find Small Business, click to add it. In Claude Code, if you live in a terminal, the book's two lines, exactly:

```bash
claude plugin marketplace add anthropics/knowledge-work-plugins
claude plugin install small-business@knowledge-work-plugins
```

**3. Say `set me up`.** Answer its questions from your chapter 3 files. Connect your money tool first (for most owners, QuickBooks). Then point it at your `My Business Context` folder, or paste the four files in. "Get me started" works too.

**4. Type `/monday-brief`** or say "what should I focus on this week?" In Claude Code the same command is `/small-business:monday-brief`.

**5. Gut check.** Pick one number and one customer name in the brief and look them up in the real tool. Write down anything that's off.

## If it doesn't go smoothly

| What you see | What the book says to do |
|---|---|
| "I can't find the small-business anything." | You're in the browser. Open the Cowork desktop app. Still missing? Add the plugin from claude.com/plugins. |
| The connection won't finish, or logged you out. | Run the sign-in again and approve it. |
| The brief came back empty or obviously wrong. | Nothing's connected yet (run `set me up`, connect QuickBooks), or the context pack didn't make it in (hand it the four files again). |
| Claude Code threw an install error. | Switch to Cowork. |

## Before you leave this chapter

Copy this list into your notes and tick each line:

- [ ] Cowork desktop app opens on your work computer (not the browser, not your phone).
- [ ] The Small Business plugin is installed.
- [ ] "Set me up" ran start to finish.
- [ ] Your context pack from Chapter 3 got added or pasted in.
- [ ] At least one real tool (probably QuickBooks) is connected.
- [ ] `/monday-brief` returned actual output, not an empty or generic page.
- [ ] You checked at least one number or customer name in that brief against the real source.
- [ ] You wrote down one gap, a wrong number, a missing customer, a tool not yet connected, to fix later.

## Done when

> "You ran a real workflow on your real business data and got back a snapshot that's mostly or completely right, and you did it without sending, paying, or changing anything."

For the rest of week one, run the brief every morning and note what it gets wrong. That's your list of context-pack fixes.
