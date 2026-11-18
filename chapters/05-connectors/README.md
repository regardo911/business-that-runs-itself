<!-- Chapter 5, The Connector Spine. Connect, test, verify, one tool at a time, with a written log. Source: ch05.md:31-142 -->
# Chapter 5: connectors

Two files. `test-questions.md` gives you the one question to ask each tool. `connection-log.md` is where you write down that the answer matched.

For each tool, in this order (QuickBooks first, then the way you take payments, then your inbox, then HubSpot if you use it):

1. **Connect.** In Cowork, tell Claude to connect the tool. Sign in, approve.
2. **Test.** Ask that tool's row from `test-questions.md`.
3. **Verify.** Open the real tool and compare. Mismatch or error: reconnect and ask again.
4. **Log it.** Fill in one block of `connection-log.md`.

Then push it once: "summarize last month's invoices", and check the count against what you know you sent. A short count means a partial pull. Ask for the full month again.

Connect the rest (Canva, Calendar, DocuSign, Slack, Drive) the day a workflow needs them, with the same four steps.

## When the spine is live

In the book's words: "Claude pulled real data from one of your real systems, and you confirmed against the actual tool that the data is correct."

The book lists twelve connectors; the plugin lists 35 now. [BOOK-FIXES.md](../../BOOK-FIXES.md) has the list, and `test-questions.md` adds Slack and DocuSign rows.
