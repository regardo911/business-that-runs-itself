<!-- Chapter 8, When the Built-Ins Don't Fit. The book's finished quote-job skill and its design checklist, plus what the plugin added since. Source: ch08.md:66-208 -->
# Chapter 8: your own workflow

`quote-job/SKILL.md` is the book's finished file, exactly as printed. It holds the pool company's rules, not yours. It's plain English: a short header, then instructions. Use it as the model for yours.

## Try the easy way first

The book's rule: before you build anything, ask an existing workflow in plain English and see how close it gets. Since the book printed, the plugin gained two skills that sit right on this chapter:

- `proposal-builder`, for quotes. Its file says to use it for "a quote, bid, estimate, proposal, or SOW", including "put together a quote". Describe the job you just looked at and see what comes back.
- `build-agent`, for a task you repeat. Its file says it "turns a task the owner keeps doing by hand into a named, reusable skill", and triggers on "automate this for me" or "turn this into a workflow". Walk it through the task once.

## Building your own file

1. Answer the seven questions in `design-checklist.md`.
2. Copy `quote-job/SKILL.md`, rename the folder and the `name:` line for your task (lowercase, hyphens), and rewrite the instructions with your rules from your context pack.
3. Easiest now: say "automate this for me" in Cowork and let `build-agent` write the skill with you. The book's route is a GitHub fork, with the new folder inside `small-business/skills/`; neither the book nor the plugin says how a fork then reaches Cowork.
4. Test it on a fake or low-stakes job first. In Claude Code it runs as `/small-business:<your-name>`; in Cowork, ask for it in plain English.

## How you know it worked

The book's checkpoint: "You ran a workflow that handles a task specific to your business that none of the fifteen built-ins covered, and it produced something useful. If level one got you there, great, that counts."
