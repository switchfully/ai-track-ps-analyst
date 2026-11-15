## Block 2: Working with an agent

New pairs! This block, both pairs are going to work with an AI agent. An agent is an AI that reads and edits your files by itself, instead of just answering you in a chat window. That changes your job quite a bit: you're no longer writing prompts that produce text, you're giving instructions, reviewing a plan and checking what it changed.

> There's one rule for this block: you don't edit any file by hand. If the agent gets something wrong, you fix it by giving it another instruction. It will feel slower at times, but this is exactly how you find out where agents go wrong.

**This block, you write the prompts yourself.** This morning you got them ready-made. Now we only tell you the goal, what a good prompt for it needs to contain, and what to check afterwards. How you word it is up to you.

> Keep a **prompt log** in your team's shared document (not in the Codespace, remember: no hand edits there). Every time you write a prompt, paste it in and add one line: did it work, or did you have to fix it, and what did you change? This is the start of your team's prompt library.

> Stuck after two tries? Ask your coach for the example prompt for that step. Looking is allowed, just write down what the example does that yours didn't.

> **Watch your tokens.** Agents read your files again on every step, and a long chat gets read again with every message. So name the files in your prompt, and start a **new chat** for each step (keep the plan in your shared document, not in the chat). Your tool says you're out of tokens? Don't wait for it to reset: work on your partner's machine or switch tools, and tell your coach.

**Where things live.** From now on your work is in files, in a GitHub Codespace (an editor in your browser). These are the files you work with:

| File | What it is | Made in |
|---|---|---|
| `backlog.md` | Your user stories and acceptance criteria | Block 1, moved here in the first task |
| `glossary.md` | The glossary | Block 1, moved here in the first task |
| `decisions.md` | What your team decided | Block 1, moved here in the first task |
| `open-questions.md` | What the client has to answer | Block 1, moved here in the first task |
| `business-rules.md` | Every business rule, with its source and conflicts | Block 1, new file in the first task |
| `.github/copilot-instructions.md` | Your house rules, read by Copilot before every request | Block 1, you paste them in during setup |
| `diagrams/` | Your Mermaid diagrams (pair BD) | This block |
| `flawed-acceptance-criteria.md` | Three criteria with an error in them (pair AC) | Your coach gives it to you |

The prompt log is not in this list. It stays in your team's shared document, because the "no hand edits" rule applies in the Codespace. The brief (`meridian-brief.md`) is in the workspace repo too, because the agent can only read what is in your workspace. Don't see it in the file list? Ask your coach.

**How to read this block.** Every step starts with a **Read:** line (the files it works with, these exist already) and a **Create:** line (the file you make or change, and where it lives). The **Goal** is your *done when*: if the Goal is true, you move on. Not sure what to do now? Look at those lines first, then ask your coach.

**Your block at a glance.** This is a rough guide, not a rule. Setting up and the first task take about 10 minutes, the last 10 minutes are for your context pack and your best and worst prompt.

| Part | Pair AC | Pair BD |
|---|---|---|
| Setting up and the first task | 10 min | 10 min |
| Step 1: plan before you act | 20 min | 15 min |
| Step 2: execute | 25 min | 20 min |
| Step 3 | 15 min (house rules) | 20 min (draw the flows) |
| Step 4: reflect | none | 10 min |
| Context pack and best/worst prompt | 10 min | 10 min |

---

### Setting up (both pairs, about 10 minutes)

* **Read:** your team's shared document from Block 1, and `meridian-brief.md`
* **Create:** a Codespace with Copilot in **Agent** mode, and your instructions in `.github/copilot-instructions.md`
* **Done when:** the Copilot chat says **Agent**, and you can see `meridian-brief.md` in the file list on the left

An agent needs real files to work on, so we'll do this block in a GitHub Codespace. That's basically VS Code running in your browser, nothing to install. One laptop per pair is enough.

* Open the Meridian workspace repo, <https://github.com/switchfully/ai-track-ps-analyst-meridian-starter>, and click **Code** → **Codespaces** → **Create codespace on main**. Sign in with your GitHub account if it asks.
* Open the Copilot chat panel. If Copilot asks you to, enable **GitHub Copilot Free** (no credit card needed). Then switch the chat from **Ask** to **Agent**.
* Paste your team's instructions file from Block 1 into `.github/copilot-instructions.md`. From now on, Copilot reads this file automatically before every request you make in this workspace.

### Your first agent task: move this morning's work into the files

* **Read:** your team's shared document
* **Create:** `backlog.md`, `glossary.md`, `decisions.md`, `open-questions.md` and `business-rules.md` (new file)
* **Done when:** the five files contain this morning's work, word for word the same

**Goal:** the backlog ends up in `backlog.md`, the glossary in `glossary.md`, the decisions in `decisions.md`, the open questions in `open-questions.md` and the business rules in a new file `business-rules.md`. The content itself doesn't change, it only moves.

A good prompt for this:
* Names every file the content has to end up in
* Says clearly what the agent is not allowed to do (hint: touch the content)
* Contains your team's shared document, so the agent has something to work with

Now open the **Source Control** panel on the left. Every file the agent touched is listed there, and when you click one, you see exactly what changed. You'll be using this view all block long, because this is how you check what an agent did.

* Pick one story in `backlog.md` and compare it with your shared document. Is it still word for word the same?

> This Codespace is your pair's own scratch space. Please don't push anything back to the repo. At the end of the block, you simply copy your results back into your team's shared document.

---

## Pair AC: filling the gaps in the backlog

Most teams miss the same things: regulatory complaints, extensions and escalations. You're going to let the agent add those. On top of that, a "previous session" left behind three acceptance criteria that aren't quite right, and you'll let the agent fix those too.

About 60 minutes: step 1 takes 20, step 2 takes 25 and step 3 takes 15.

Before you start, ask your coach for `flawed-acceptance-criteria.md` and let the agent save it in the workspace.

### Step 1: plan before you act

* **Read:** `backlog.md`, `business-rules.md`, `meridian-brief.md` and `flawed-acceptance-criteria.md`
* **Create:** nothing in the workspace. Paste the plan in your prompt log, you need it in step 2

Never let an agent start changing files before you've seen its plan. That's the habit of this block.

**Goal:** a plan, and no changed files yet, for three things:
1. User stories with acceptance criteria for regulatory complaints (escalation to compliance within 2 working days)
2. Stories for the extension flow (a handler asks for more time with a reason, the team leader approves) and for a missed deadline without an extension
3. The factual error in each of the three flawed acceptance criteria, compared to `meridian-brief.md`, and how to fix it

A good prompt for this:
* Tells the agent which files to read first
* Says in so many words that nothing may be changed yet
* Asks for a plan per part, not one long list
* Asks for the file and the source quote behind every planned change
* Says what to do when the brief doesn't give an answer (hint: flag it, don't decide it)

After you got the plan:
* Read it before you let it do anything. Look at the three flawed criteria: do you agree with the error it found? Check each one in the brief yourself.
* Did it plan the business customer question as a story? It shouldn't, that one is still an open question. Tell the agent.

### Step 2: execute it, one step at a time

* **Read:** your plan and the files from step 1
* **Create:** the new stories in `backlog.md` (regulatory complaints, extensions, missed deadline) and the three corrected criteria, in `backlog.md` under the heading "Corrected criteria"

**Goal:** the agent carries out the plan, one part at a time, and you check after each part. When it's done, all three parts of the plan are in `backlog.md`, and you checked each part in the Source Control panel.

A good prompt for this:
* Points to the plan, so you don't have to repeat it
* Says the agent has to stop after each part and list what it changed
* Sets limits: nothing gets removed without asking you, and no invented source quotes

After each part, open the changed files in the Source Control panel.
* Does the regulatory escalation go to compliance within 2 working days? Not 5 days, and not to the team leader?
* Does the missed-deadline flow treat a missed 5-day target differently from a missed 8-week deadline? Only the 8-week one requires a letter to the customer.

### Step 3: did it follow your house rules?

* **Read:** `.github/copilot-instructions.md` and the stories the agent added in step 2
* **Create:** the list of broken rules in your prompt log. If a rule is unclear, an improved `.github/copilot-instructions.md` and a line in `decisions.md` about what you changed

**Goal:** a list of every place where what the agent added breaks the rules in your instructions file.

A good prompt for this:
* Points to the file with the rules
* Asks for every place where a rule wasn't followed, not for a verdict like "looks fine"

> If the agent keeps breaking the same rule, chances are the rule isn't clear enough. Improve your instructions file (that's the one file you may ask the agent to edit for this) and remember what you changed, we'll ask you about it in Retro 2.

---

## Pair BD: restructuring the backlog and drawing the flows

You're going to let the agent clean up the entire backlog in one go, and then turn it into process diagrams.

About 65 minutes: step 1 takes 15, step 2 takes 20, step 3 takes 20 and step 4 takes 10.

### Step 1: plan before you act

* **Read:** `backlog.md`, `glossary.md` and `meridian-brief.md`
* **Create:** nothing in the workspace. Paste the plan in your prompt log, you need it in step 2

**Goal:** a restructuring plan, and no changed files yet, for these problems:
1. Stories that don't follow "As a ... I want ... so that ..."
2. Stories without a source quote from `meridian-brief.md`
3. Terms that don't match `glossary.md`
4. Acceptance criteria that can't be tested

A good prompt for this:
* Tells the agent which files to read
* Says that nothing may be changed yet
* Asks for every story that needs to change, with the reason why, per problem

After you got the plan:
* Compare it with what you see in the backlog. Did it flag things that aren't actually a problem? Did it miss things that are?

### Step 2: execute the restructure

* **Read:** your plan, `backlog.md` and `glossary.md`
* **Create:** the restructured `backlog.md`

**Goal:** the backlog is cleaned up, without losing what it says.

A good prompt for this:
* Says in which order to work (hint: terminology first, testability last) and to stop after each step and list what changed
* Protects the meaning: an acceptance criterion may become clearer, but it can't say something else
* Doesn't allow removing a story without asking you
* Forbids invented source quotes: if a story has no source, the agent flags it

After the restructure:
* Open `backlog.md` in the Source Control panel and go through the changes.
* Pick three stories it changed. Do they still say what they said before?
* Did it invent a source quote anywhere? Search for it in the brief.

### Step 3: draw the flows

* **Read:** the restructured `backlog.md`, `business-rules.md` and `meridian-brief.md`
* **Create:** `diagrams/main-flow.md` and `diagrams/extension-flow.md` (new files), and a reference to the right diagram in every story in `backlog.md` it covers

**Goal:** two Mermaid diagrams, each in its own file in a `diagrams/` folder, and a reference to the right diagram in every story it covers:
1. `main-flow.md`: the complaint from submission to closure, with every decision point
2. `extension-flow.md`: what happens when a handler needs more time

A good prompt for this:
* Names the files and the folder
* Says what the diagrams have to be based on
* Asks for the references in the stories as part of the same task

After the agent is done:
* Open one of the diagram files and click the preview icon in the top right. Does it render?
* Look at how a complaint gets closed in the main flow. Do you see the two reminders, the 14-day letter and the manual sign-off? Or does the diagram just close it automatically?

### Step 4: reflect

* **Read:** your prompt log and the changes in the Source Control panel
* **Create:** your answers in `decisions.md`, through the agent (so one more prompt for your log)
* **Done when:** all three questions below are answered, in your own words

This one isn't a prompt for the agent, it's a conversation with your partner. Write your answers in `decisions.md` (through the agent, of course, so this is one more prompt for your log).

* What did the agent do that you didn't expect?
* At what point did you stop trusting it, and why?
* What would you want to have in place before you let an agent loose on a real client's documents?

---

### The last 10 minutes, both pairs

* **Read:** your files in the workspace and your prompt log
* **Create:** the context pack: one new document with three headings: backlog, open questions and prompt log
* **Done when:** the pack holds the final backlog, the open questions and the prompt log, nothing else, and you picked your best and your worst prompt

* Ask the agent to show you the final content of each file and paste it back into your team's shared document.
* Now build your **context pack**: one short document with three parts, each under its own heading: the backlog, the open questions and your prompt log. Leave the rest in your shared document. The smaller the pack, the less your next tool has to read.
* Why? In Block 3 you'll work in a different tool (most of you in Claude.ai), and that tool knows nothing about today. Your work doesn't live in a chat, it lives in files, and the context pack is how it travels with you.
* Pick your **best** and your **worst** prompt from your log. You'll be asked for them in Retro 2.

### Done?

Pair AC:
* Regulatory complaint stories exist, with escalation to compliance within 2 working days
* Extension and missed-deadline stories exist, with the 5 days and the 8 weeks kept apart
* The three flawed criteria are corrected, each one with a source quote
* The business customer question is still an open question

Pair BD:
* The backlog is restructured, without any invented source quotes
* Both diagrams render, and the main flow doesn't close complaints automatically
* Your reflection is in `decisions.md`

Both pairs:
* Your instructions file is better than it was this morning
* Everything is back in your team's shared document
* Your context pack is ready: backlog, open questions and prompt log, nothing else
* Your prompt log has every prompt you wrote, each with a one-line verdict
* You picked your best and your worst prompt

What you learned in this block:
* What the difference is between chatting with AI and letting an agent work on your files
* Why you always let an agent make a plan before it starts changing things
* How to check what an agent really did, by reading the changes instead of its summary
* How an instructions file in the project gives an agent your team's rules
* What a prompt needs to contain to keep an agent on a leash
* Why your work has to live in files you can carry to another tool, and not in one chat
