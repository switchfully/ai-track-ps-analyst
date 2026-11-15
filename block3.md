## Block 3: Grounding and skills

Last rotation of the day! This block, both pairs are going to connect their AI to a real source document: Meridian's regulatory standards. We serve that document through an MCP server we host ourselves. Once that works, both pairs will take what they learned today and turn it into a skill: a set of instructions the AI only loads when it actually needs them.

What we want you to notice is the difference between an AI that answers from what it was trained on ("this is what energy regulation usually looks like") and an AI that reads Meridian's actual document and quotes it back to you.

One more thing before you start: if you worked in another tool this morning (M365 Copilot, for example), the tool you use now knows nothing about it. That's the price of the connector: it lives in Claude, your work doesn't. So you bring your work with you, in the **context pack** you made at the end of Block 2.

**This block, you write all the prompts yourself.** No hints about wording this time. For every task we only tell you what the result has to look like, and how you check it. You've had a whole day of practice, so now it's up to you.

> Keep adding to your **prompt log** in your team's shared document: the prompt, and one line on whether it worked or what you had to fix.

> Stuck after two tries? Ask your coach for the example prompt for that step. Looking is allowed, just write down what the example does that yours didn't.

> **Watch your tokens.** Agents read your files again on every step, and a long chat gets read again with every message. So name the files in your prompt, and start a **new chat** for each step (keep the plan in your shared document, not in the chat). Your tool says you're out of tokens? Don't wait for it to reset: work on your partner's machine or switch tools, and tell your coach.

**Where things live.** Your work from Blocks 1 and 2 travels with you in the **context pack**. Everything new you make in this block gets one of the names below. Working in the Codespace? Make them files. Working in Claude.ai? Make them sections in your team's shared document, with the same names.

| Name | Made by | In | What it is for |
|---|---|---|---|
| `audit-findings.md` | Pair AD | Step 2 | Every place where your backlog breaks or misses the regulation, with the fixes added in step 3 |
| `review-notes.md` | Pair BC | Step 2 | The traceability and regulation checks |
| `pre-mortem.md` | Pair BC | Step 3 | The six reasons the project failed |
| `steering-committee-review.md` | Pair BC | Step 4 | The review document with a readiness status |
| the skill folder, with `SKILL.md` | Both pairs | The last 25 minutes | The skill you build and swap |
| `prompt-log` | Both pairs | All block | Your prompts, with a one-line verdict each (in the shared document, as before) |

The regulatory standards are a course file too: `meridian-regulatory-standards.md`. You read it through the server, and you use the file to check what the AI quoted.

**How to read this block.** Every step starts with a **Read:** line (what it works with, these exist already) and a **Create:** line (what you make, and where it lives). "The result is good when" is your *done when*. Not sure what to do now? Look at those lines first, then ask your coach.

**Your block at a glance.** This is a rough guide, not a rule. The skill in the last 25 minutes is the part to protect: cut the swap if you must, not the drafting.

| Part | Pair AD | Pair BC |
|---|---|---|
| Setting up | 10 min | 10 min |
| Step 1: feel the difference | 10 min | 10 min |
| Hand over your work | 10 min | 10 min |
| Step 2 | 20 min (the audit) | 15 min (review) |
| Step 3 | 15 min (fix the Critical findings) | 10 min (pre-mortem) |
| Step 4 | none | 10 min (review document) |
| The last 25 minutes | skill | skill |

---

### Setting up (both pairs, about 10 minutes)

* **Read:** nothing yet, the standards come in step 1
* **Create:** the connector in Claude.ai (Option 1), or `.vscode/mcp.json` in your Codespace (Option 2)
* **Done when:** your tool can use `ai-track-standards` (in Copilot, the tools list shows `list_documents` and `read_document`)

Pick one of the two options below. Both work for everything we do in this block.

Option 1, Claude.ai in your browser (a free account is fine):
* Sign in at [claude.ai](https://claude.ai).
* Go to **Customize** → **Connectors** → **Add custom connector**. Call it `ai-track-standards` and paste this URL: `https://ai-track-ps-production.up.railway.app/mcp`. There's no login.
* Start a new chat, click **+** → **Connectors** and switch `ai-track-standards` on.
* For the skill at the end of the block, go to **Settings** → **Capabilities** and switch on **Code execution and file creation**. Skills don't work without it.

Option 2, GitHub Copilot in your Codespace from Block 2:
* Create a file called `.vscode/mcp.json` with the following content:

```json
{
  "servers": {
    "ai-track-standards": {
      "type": "http",
      "url": "https://ai-track-ps-production.up.railway.app/mcp"
    }
  }
}
```

* A small **Start** link appears above the server name in that file. Click it.
* In the chat panel (still in Agent mode), take a look at the tools list. You should see `list_documents` and `read_document` in there.

> Curious about what you're actually connecting to? `ai-cheat-sheets/what-is-mcp-for-analysts.md` explains it.

**What you need to know to talk to the server:** it's called `ai-track-standards`, it has two tools (`list_documents` and `read_document`), and the document we need has the id `meridian-regulatory`. An AI only reads that document when you tell it to, it won't do it by itself.

---

### Both pairs, step 1: feel the difference

* **Read:** `meridian-regulatory-standards.md`, to check what the AI quotes
* **Create:** nothing. Note what you saw in your prompt log
* **Done when:** you can say what is different between the answer without and the answer with the connector

You're going to ask the same question twice: first in a chat without the connector, then in one with the connector. For this one, we give you the question, so both runs are comparable:

```
What are Meridian Energy's rules for extending the internal 5-day resolution target, and
what happens if a team leader doesn't respond to an extension request?
```

For the second run, you write the extra sentence that makes the AI use the server and quote the document. Add it at the end of the question.

* Without the connector, the AI has never seen Meridian's rules. Did it tell you that, or did it come up with something that sounds plausible?
* With the connector, take a look at `meridian-regulatory-standards.md` and look up the clause it quoted. Does it exist? Is it quoted correctly?

---

### Both pairs: hand over your work

* **Read:** your context pack from the end of Block 2
* **Create:** a new chat that has your context pack in it, and the connector on if you're in Claude.ai
* **Done when:** the AI listed every part it received, the number of stories matches your own count, and nothing is cut off

Open a **new** chat (with the connector on, if you're in Claude.ai) and attach or paste your context pack. Before you ask it to do anything with it, check what actually arrived. You write that prompt yourself.

The result is good when the AI:
* lists every part it received (backlog, open questions, prompt log)
* tells you how many stories it sees in the backlog

Then check it:
* Count the stories in your own backlog. Does the number match? Is anything cut off at the end?
* Something missing or cut off? Fix it now, not halfway through the audit.
* Is the AI telling you what it received, or what it assumes is in there?

Use this same chat for your audit or review, so you don't have to hand over your work twice. Start a new chat for the skill at the end, and bring only the prompts that worked best. Still in your Codespace from Block 2? Your files are already there, but do the check anyway: ask the AI which files it can see.

---

## Pair AD: auditing the backlog against the regulation

### Step 2: the audit

* **Read:** your backlog from the context pack, and the regulatory standards through the MCP server
* **Create:** `audit-findings.md` (new). Don't change any story yet

**Your mandate:** find out where your requirements backlog violates the regulatory standards, or misses something the standards require.

The result is good when:
* Every finding names the story it's about
* Every finding quotes the clause it violates or misses
* Every finding explains why it matters
* Every finding comes with corrected requirement language
* The findings are sorted by severity: Critical, Major, Minor

Then check it:
* Take three findings and find the quoted clause in the document. Can't find a clause? Then the AI made it up. Write it down, it's great material for Retro 3.
* Look at §4 (no automatic closure) and §2.3 (5 days versus 8 weeks) in particular. Is there still anything in your backlog that those sections don't allow?

### Step 3: fix the critical findings

* **Read:** `audit-findings.md`
* **Create:** the rewritten stories and criteria in your backlog, and a "Fixes" section in `audit-findings.md` with what was wrong and which clause it's based on

**Your mandate:** rewrite every story and acceptance criterion that has a Critical finding.

The result is good when every Critical finding has a rewritten story or criterion, and every change comes with a note on what was wrong and which clause it's based on.

* Paste the fixes into your team's shared document.

---

## Pair BC: reviewing the package for the steering committee

You're the senior analyst who reviews the package before the client gets to see it. The AI will find real issues, but it will also invent a few that aren't there. It's up to you to tell them apart.

### Step 2: traceability and regulation in one review

* **Read:** your backlog, acceptance criteria and open questions from the context pack, `meridian-brief.md` and the regulatory standards through the MCP server
* **Create:** `review-notes.md` (new), with a section "Traceability" and a section "Regulation"

**Your mandate:** review the requirements package (backlog, acceptance criteria and open questions) before it goes to the client. You need two checks, using `meridian-brief.md` and the regulatory document.

The result is good when:
* For every story, you can see the sentence in the brief it comes from, and stories without one are flagged as possibly invented
* Every regulatory obligation in the standards document is marked as covered, partly covered or missing in the backlog, with the clause quoted

Then check it:
* The satisfaction survey and the dashboards each get one sentence in Sarah's email. Did they grow into big features that nobody actually asked for?
* Pick two of the "missing" findings and check them yourself. Are they really missing?

### Step 3: the pre-mortem

* **Read:** your backlog, `review-notes.md` and the regulatory standards
* **Create:** `pre-mortem.md` (new), with six reasons

**Your mandate:** make the AI play a red team. It's one year from now, the system was built exactly from this package, and the project failed. Why?

The result is good when:
* There are 6 distinct reasons, spread over technical, organisational and legal/regulatory
* Every reason points to a story or a missing requirement in your package
* Every reason either quotes a source that shows the risk was knowable today, or says clearly that it's speculation

Then check it:
* Sort the 6 reasons into three piles: real (there's a source behind it), speculative and invented. Chances are you'll have something in every pile.

### Step 4: the review document

* **Read:** `review-notes.md` and `pre-mortem.md`
* **Create:** `steering-committee-review.md` (new)

**Your mandate:** combine the review and the pre-mortem into one document for the steering committee.

The result is good when it has:
* A summary of 3 sentences
* The critical issues (must fix before the checkpoint)
* The other issues
* What's done well (at least 3 things)
* The open questions that need a client decision
* A readiness status: NOT READY / READY WITH CAVEATS / READY

Then check it:
* Do you agree with the readiness status it gave? You'll have to defend it during the showcase.

---

## Both pairs, the last 25 minutes: build a skill

You've written a lot of instructions for the same kind of check by now. A skill saves you that work. It's a folder with a `SKILL.md` file in it, which tells the AI how to do one specific task. The AI only reads the short description of each skill it has, and loads the full instructions when your request matches that description.

> How is this different from the instructions file you made this morning? That file is read before every request. A skill is only read when it's relevant. `ai-cheat-sheets/working-efficiently.md` explains it in a bit more detail.

Pair AD builds `regulatory-check`, a skill that checks any requirement against Meridian's regulation. Pair BC builds `requirements-review`, a skill that reviews stories for traceability and testability.

### Step 5: draft the skill

* **Read:** your prompt log and the prompts that worked best in this block
* **Create:** a folder with the name of your skill, and in it `SKILL.md` (new). In Copilot: `.github/skills/<skill-name>/SKILL.md`. In Claude.ai: a folder you zip and upload
* **Done when:** the skill exists, it is under 40 lines, and its description says when to use it

A `SKILL.md` file always looks like this. That's the format, the AI doesn't know it by heart:

```
---
name: the-name-in-lowercase-with-hyphens
description: One or two sentences. What the skill does and when to use it.
---
The instructions: the steps to follow, what to check, what sources to use, the exact
output format, and what never to do.
```

**Your mandate:** have the AI write the `SKILL.md` for the task you just did, based on the prompts that worked best for you in this block (your prompt log is useful here).

The result is good when:
* It follows the format above
* It's short: under 40 lines
* The instructions are specific enough that someone else could follow them without asking you anything

Then read what it wrote and edit it yourselves. Spend most of your time on the description: that's what the AI uses to decide whether to load your skill or not.

### Install it and swap

* **Read:** the skill of the other pair in your group
* **Create:** one piece of feedback for the other pair, in your prompt log
* **Done when:** you ran their skill in a new chat on one of your own stories, without explaining what it does, and gave them your feedback

* Using Claude.ai? Put `SKILL.md` in a folder with the same name as the skill, zip that folder and upload it under **Customize** → **Skills** (the **+** button). Don't forget to switch it on.
* Using GitHub Copilot? Ask the agent to save it as `.github/skills/<skill-name>/SKILL.md`. Copilot picks it up by itself, and you can also start it with `/<skill-name>` in the chat.
* Now swap with the other pair in your group. Try their skill on one of your stories, in a new chat, without explaining what it does. Did the AI pick it up on its own? Did it do what the other pair had in mind? Give them one piece of feedback.

---

### Finished early? Wireframe the customer view

* **Read:** your backlog
* **Create:** `status-page.html` (new)
* **Done when:** it opens in your browser, and under the wireframe is a list of everything on the page that your stories don't cover

**Your mandate:** Sarah wants customers to see where their complaint is. Make a low-fidelity wireframe of the customer's complaint status page, based on your stories.

The result is good when:
* It's a single HTML file with grey boxes and plain text only
* Below the wireframe, there's a list of everything on the page that is NOT covered by your stories

Save it as `status-page.html` and open it in your browser, then check it:
* Does anything on it depend on the current portal? IT told us it's being replaced, so the requirement can't depend on it.
* What does a customer see while their complaint is "awaiting customer info"?

---

### Done?

* Both pairs saw the difference between an answer with and without the connector
* Your work made it across to the new tool, and you checked what arrived
* Pair AD did the audit, fixed the Critical findings and wrote down any invented clauses
* Pair BC has a review document with a readiness status they can defend
* Both pairs have a working skill that the other pair tested
* Your prompt log is complete, and you know which of your prompts you'd reuse on a real engagement

What you learned in this block:
* What grounding is, and why an answer from the real document beats an answer from training data
* What MCP is and how it connects an AI tool to a source
* How to check whether a quoted clause actually exists
* What a skill is, how it differs from instructions, and why the description matters so much
* How to brief an AI when all you have is the result you want
* What it takes to move your work from one AI tool to another, and why files beat chats
