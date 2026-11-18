<!-- Book fixes. Every place the plugin changed after the book printed, with the command that shows it. Commands use the GitHub CLI (gh) against Anthropic's anthropics/knowledge-work-plugins repository. -->
# Book fixes

The book is print, so it stays as it was. The plugin kept moving. This page lists each change that alters what you type or what you can expect, and the files in this repo already carry the fix.

Each entry ends with the command that shows the change and its output, pasted whole from plugin version 1.35.2 (upstream commit `b4c9a4e`). If yours differs, the plugin moved again. You don't need to run these; they need the [GitHub CLI](https://cli.github.com) and a terminal.

## Chapter 2, 4, 6, 7, 11 and Appendix A: removed workflow names, and what to type now

13 of the 31 names the book prints are no longer in the plugin. In Cowork, say the plain-English phrase and the router sends it on.

| The book's name | Still there? | What to type now |
|---|---|---|
| `/month-heads-up` | No | "Cash forecast" or "what does next month look like?" (goes to `cash-flow-snapshot`) |
| `/price-check`, `margin-analyzer` | No | No current skill does unit costs or pricing scenarios. "Should I raise prices?" goes to `content-strategy`, which ranks top sellers and slow movers. |
| `/run-campaign` | No | "What should I promote?" (`content-strategy` writes the brief), then "run this brief" (`canva-creator` makes the Canva posts). For standing posts: "make the content" (`social-content-engine`) |
| `/sales-brief` | No | "Sales brief" goes to `content-strategy`: a 30-day plan of what to push, not a sales report. |
| `/customer-pulse-check`, `customer-pulse` | No | "Pulse check on customers" (goes to `review-reputation`) |
| `/handle-complaint` | No | "A customer is upset" (goes to `ticket-deflector`) |
| `/crm-cleanup`, `crm-maintenance` | No | "Update the CRM" (goes to `crm-autopilot`) |
| `/review-contract` | No | "Review this contract" (goes to `contract-review`) |
| `/friday-brief` | No | "Friday recap" or "how'd we do this week?" (goes to `business-pulse`) |
| `/quarterly-review` | No | No current skill names a quarterly review. Ask in plain words, for example "how did this quarter go?" |

Still there, under the book's name: `/plan-payroll`, `/close-month`, `/tax-prep`, `/call-list`, `/monday-brief`, `business-pulse`, `canva-creator`, `cash-flow-snapshot`, `content-strategy`, `contract-review`, `invoice-chase`, `job-post-builder`, `lead-triage`, `month-end-prep`, `smb-onboard`, `smb-router`, `tax-season-organizer`, `ticket-deflector`. `/plan-payroll` still runs `invoice-chase`, so the book's "chase money through `/plan-payroll`" still holds.

Changed in this repo: the green list in `chapters/11-guardrails/guardrails-policy-example.md`, the Week 3 row of `chapters/12-rollout/30-day-calendar.md`, four cells of `chapters/09-saas-teardown/teardown-book-example.csv`, and the instructions in `chapters/07-growth/README.md`.

The skill list:

```
$ gh api repos/anthropics/knowledge-work-plugins/contents/small-business/skills --jq '.[].name'
ad-manager
ap-processor
brand-style
build-agent
build-connector
business-pulse
call-list
canva-creator
cash-flow-snapshot
close-month
content-strategy
contract-review
crm-autopilot
grant-rfp-writer
grow-pipeline
growth-pulse
hiring-screener
inbox-manager
inventory-planner
invoice-chase
job-post-builder
lead-finder
lead-triage
marketing-monday
monday-brief
month-end-prep
outreach-composer
pay-the-bills
payroll-prep
plan-payroll
proposal-builder
reactivate
report-builder
report-pack
restock
review-reputation
seo-ai-visibility
smb-onboard
smb-router
social-content-engine
speed-to-lead
tax-prep
tax-season-organizer
ticket-deflector
[exit 0]
```

Each mapping above is a line in the router's own file:

```
$ gh api repos/anthropics/knowledge-work-plugins/contents/small-business/skills/smb-router/SKILL.md -H 'Accept: application/vnd.github.raw' | grep -n -E 'Cash forecast|Margins|sales brief|Update the CRM|Pulse check on customers|A customer is upset|Friday recap|Run this brief|Make the content|What should I promote|Review this contract|quote this job|automate this'
44:| "Cash forecast" / "runway" / "what does next month look like?" | `cash-flow-snapshot` (monthly preset) |
51:| "Margins" / "should I raise prices?" | `content-strategy` |
65:| "Write this up" / "quote this job" / "bid" / "proposal" / "RFP" | `proposal-builder` |
69:| "Update the CRM" / "log this call" / "HubSpot is a mess" | `crm-autopilot` (hygiene mode) |
71:| "What should I promote?" / "sales brief" | `content-strategy` |
72:| "Make the content" / "posts" / "assets" / "calendar" | `social-content-engine` |
73:| "Run this brief" / "execute the campaign" — a finished brief in hand | `canva-creator` |
83:| "A customer is upset" / "angry email" | `ticket-deflector` |
85:| "Pulse check on customers" | `review-reputation` |
96:| "Review this contract" / "NDA" / "should I sign?" | `contract-review` |
103:| "Friday recap" / "how'd we do this week?" | `business-pulse` (Friday preset) |
108:| "I do this every week" / "automate this" / "make this a thing" | `build-agent` |
121:| `/monday-brief` — "Monday brief," "start my week," "weekly briefing" | `business-pulse` — "how's the business doing," "snapshot," "daily brief," "Friday recap" |
[exit 0]
```

`/plan-payroll` still chains `invoice-chase`:

```
$ gh api repos/anthropics/knowledge-work-plugins/contents/small-business/skills/plan-payroll/SKILL.md -H 'Accept: application/vnd.github.raw' | grep -n -o 'ranks and drafts overdue-invoice reminders with invoice-chase'
3:ranks and drafts overdue-invoice reminders with invoice-chase
[exit 0]
```

The email half of the old `/run-campaign` now hands you the copy to send yourself:

```
$ gh api repos/anthropics/knowledge-work-plugins/contents/small-business/skills/canva-creator/SKILL.md -H 'Accept: application/vnd.github.raw' | grep -n -E 'email content|their own tool'
7:  for social posts only (Instagram, Facebook, X, LinkedIn) — email content
9:  their own tool. Every step requires explicit owner approval. This is the
375:4. **Surface email content for handoff.** For each email row, present the
[exit 0]
```

## Chapter 2, Chapter 8 and Appendix A1: how many skills

The book prints "15 building-block skills, 15 ready-to-use workflows, and a router", 31 folders. The plugin now has 44 skill folders, and its README says eleven of them are workflows. The 44 folders include the router, so by the book's own way of counting it's 32 skills, 11 workflows and 1 router.

```
$ gh api repos/anthropics/knowledge-work-plugins/contents/small-business/skills --jq 'length'
44
[exit 0]
```

```
$ gh api repos/anthropics/knowledge-work-plugins/contents/small-business/README.md -H 'Accept: application/vnd.github.raw' | grep -n -E '44 skills|Eleven of these|get me started'
6:business: 44 skills spanning finance, sales, marketing, operations, and
29:2. Say **"get me started"** — a 15-minute setup connects your first two
76:## The 44 skills
100:Eleven of these (like close-month and plan-payroll) are workflows that chain
[exit 0]
```

## Chapter 8: the plugin folder has a fifth item

Chapter 8's folder tree shows `.claude-plugin/`, `.mcp.json`, `README.md` and `skills/`. There's now a `shared/` folder too. Your custom skill still goes in `skills/`.

```
$ gh api repos/anthropics/knowledge-work-plugins/contents/small-business --jq '.[].name'
.claude-plugin
.mcp.json
README.md
shared
skills
[exit 0]
```

## Chapter 5 and Appendix A2: the connector list

The book lists twelve connectors, Microsoft 365 among them. The plugin's connector file now lists 35, with no Microsoft 365 entry. Some skills still say they read Microsoft 365 mail and files. All eleven other connectors from the book are still there.

The book's test-question table also says it has "one for each connector in the box" but prints eight rows, with no row for Slack or DocuSign. `chapters/05-connectors/test-questions.md` adds those two rows in the book's own pattern.

```
$ gh api repos/anthropics/knowledge-work-plugins/contents/small-business/.mcp.json -H 'Accept: application/vnd.github.raw' | jq -r '.mcpServers | keys[]'
airwallex
apollo-io
atlassian
canva
clay
docusign
emergent
expensify
gmail
google-calendar
google-drive
gusto
hubspot
intuit-mailchimp
intuit-quickbooks
monday-com
myob
notion
paypal
ramp
ringex-chat
shopify
slack
square
stripe
tiktok
trello
wix
xero
zapier
zoho-books
zoho-crm
zoho-desk
zoho-projects
zoom
[exit 0]
```

```
$ gh api repos/anthropics/knowledge-work-plugins/contents/small-business/.mcp.json -H 'Accept: application/vnd.github.raw' | grep -c -i -E 'microsoft|m365|outlook'
0
[exit 1]
```

## Chapter 3 and 4: "set me up"

Still works. The plugin's README now uses "get me started" for the same setup, and the setup skill answers to both.

```
$ gh api repos/anthropics/knowledge-work-plugins/contents/small-business/skills/smb-onboard/SKILL.md -H 'Accept: application/vnd.github.raw' | grep -n -E 'set me up|get me started'
8:  cadence. Use when the owner is getting started or says any of: "set me up,"
21:User: "get me started"
[exit 0]
```

## Chapter 8: two new skills for quotes and custom workflows

The book says no built-in covers quoting, and has you fork the repository to build `quote-job`. Two skills now sit on that job. `proposal-builder` takes quotes and estimates. `build-agent` turns a task you walk it through into a named skill and adds it to the router.

The book doesn't say how a forked copy gets into Cowork, and neither does the plugin's README or `build-agent` file. The fork route in the book is unchanged; `build-agent` is the other way in. `chapters/08-custom-workflow/README.md` lists both.

```
$ gh api repos/anthropics/knowledge-work-plugins/contents/small-business/skills/proposal-builder/SKILL.md -H 'Accept: application/vnd.github.raw' | grep -n -E 'quote, bid|put together a quote'
10:  owner can send themselves. Use this whenever a quote, bid, estimate, proposal,
12:  "put together a quote," "I need to bid this job," "turn my notes into a
[exit 0]
```

```
$ gh api repos/anthropics/knowledge-work-plugins/contents/small-business/skills/build-agent/SKILL.md -H 'Accept: application/vnd.github.raw' | grep -n -E 'Turns a task|automate this for me|Add it to'
4:  Turns a task the owner keeps doing by hand into a named, reusable skill they
12:  ask for," "build me an agent," "automate this for me," "turn this into a
78:Add it to `smb-router` so plain-English requests reach it, and record the trigger phrases the owner actually uses.
[exit 0]
```

## Chapter 9: the hours math

The book says $300 a week "is about $1,200 a month, which is roughly $14,000 a year". A year has 52 weeks, so $300 a week is $15,600 a year. Use your own hours and rate. The sheet here has no hours column.

```
$ echo $((300 * 52)) $((1200 * 12))
15600 14400
[exit 0]
```
