## Block 1: Prompting well

This morning is all about the basics. How do you give AI the right context, how do you get the format you actually need, and how do you make it tell you what it found in the brief versus what it simply guessed? You can use any AI chat tool you like for this block (check out `ai-cheat-sheets/copilot-chat.md` if you're not sure which one). No files, no setup, just a chat window.

One thing we want you to do after every single prompt: check two or three things by hand against the brief. Each prompt below tells you what to look at. We kept the brief short on purpose, so this takes you a couple of minutes, not an hour. If you skip it, you're not really testing the AI anymore, you're just trusting it.

**What this block is for.** You learn to give an AI the source, the task, the format and the rules it needs, and to check what comes back. By the end of the block your team has a first backlog, a glossary, business rules, a domain model and a short instructions file. Everything you make goes into one shared place, and in Block 2 we move it into files.

**Set up your team's shared place (5 minutes, both pairs together).**

* **Read:** nothing yet
* **Create:** one shared place for your team's work: a Word document, a OneNote page, a Teams chat, whatever works for you. Give it four sections: **Backlog**, **Glossary**, **Decisions** and **Open questions**
* **Done when:** all four of you can open it and type in it

You add three more sections during the morning when you need them: **Business rules**, **Diagrams** and **Instructions**. This is also where `prompt-log` lives from Block 2 on.

**How to read an exercise.** Every prompt below starts with the same three lines, so you always know where you stand:

* **Read:** what the prompt works with. This exists already, you don't make it.
* **Create:** what you make or change, and in which section of your shared place. If it says *nothing*, no section changes in this step.
* **Done when:** what has to be true before you go to the next prompt.

Not sure what to do now? Look at these three lines first. Still not sure after that? Ask your coach. It means the exercise isn't clear enough, not that you're doing it wrong.

**Where things live.** The course files (`meridian-brief.md` and the cheat sheets) are shared by your coach. Everything you create today goes in your team's shared place. You rotate partners every block, and Block 2 builds on what you made in Block 1, so everybody in the team has to be able to find it. Your sections:

| Section | Made by | In | What it is for |
|---|---|---|---|
| Open questions | Pair AB | Prompt 1 | Everything the client has to answer, not you |
| Decisions | Pair AB | Prompt 1 | Everything your team decides itself, and why |
| Backlog | Pair AB | Prompts 2 to 4 | User stories with source quotes and acceptance criteria |
| Glossary | Pair CD | Prompts 1 and 2 | One definition per term |
| Business rules | Pair CD | Prompt 3 | Every rule the system must enforce, with its source and conflicts |
| Diagrams | Pair CD | Prompt 4 | The domain model in Mermaid |
| Instructions | Your whole team | The last 15 minutes | Your house rules for the AI |

**Your block at a glance.** This is a rough guide, not a rule. The block is 90 minutes: about 5 for the shared place, about 65 for your prompts, 15 for the instructions file and a few minutes of room.

| Part | Pair AB | Pair CD |
|---|---|---|
| Prompt 1 | 15 min | 15 min |
| Prompt 2 | 20 min | 15 min |
| Prompt 3 | 20 min | 20 min |
| Prompt 4 | 10 min | 15 min |
| Left over | Prepare questions for the client | A few minutes to share with pair AB |

---

## Pair AB: understanding the brief and writing user stories

### Prompt 1: understand before you build

* **Read:** `meridian-brief.md`
* **Create:** your contradictions and gaps, sorted into the **Decisions** and **Open questions** sections of your shared place
* **Done when:** you checked two quotes against the brief, and you and your partner decided for every contradiction whether it is *ours to decide* (Decisions) or *the client's to answer* (Open questions)

* Paste the full Meridian brief into your chat (or attach the file) and send the following prompt:

```
I'm a functional analyst joining a requirements engagement for a Complaint Management
System. Here is all the source material we have:

[paste or attach meridian-brief.md]

1. Explain the domain to me in 10 lines, as if I'm a new analyst on the team.
2. List every contradiction or gap you find between the three documents. For each one,
   quote the conflicting statements and say who said what.

Use only what is in these documents. If you infer something that is not stated, label it
explicitly as an inference.
```

* Pick two of the contradictions it found and look up the quotes in the brief yourself. Are they quoted correctly? Did it attribute them to the right person?
* Look for the auto-close conflict between Sarah on one side and Marc and Priya on the other. Is it in the list? If the AI treats it as something that's already settled, you just found the biggest risk of the day.
* Discuss with your partner which of these you can decide yourselves (they go under decisions) and which ones need an answer from the client (they go under open questions).

### Prompt 2: the user story backlog

* **Read:** `meridian-brief.md` and your contradictions from Prompt 1
* **Create:** the stories in the **Backlog** section, grouped by epic. Gaps go in **Open questions**, not in the backlog
* **Done when:** every story has a source quote, and you checked at least three of them in the brief. A story whose quote you can't find is removed or flagged

```
Based on this source material, propose a user story backlog for the Complaint Management
System, organised into epics. Use the format:

As a [role], I want to [action], so that [benefit].

For each story, add:
- Source: which document it comes from, with a short quote
- Stated or inferred: say explicitly which

Do not invent functionality that the source material doesn't support. If you think
something is missing, list it separately as a gap, not as a story.
```

* Pick three stories at random and find their quote in the brief. Can't find it? Then that story is a candidate for removal.
* Is there a story for regulatory complaints (Marc and Priya both talk about it)? And is there a story that closes complaints automatically? If so, who decided it should be in there, you or the AI?

### Prompt 3: acceptance criteria for the core flow

* **Read:** your stories for submission, acknowledgement and resolution
* **Create:** acceptance criteria under those three stories in the **Backlog** section
* **Done when:** each of the three stories has Given/When/Then criteria with the right timeframes, and you can explain to your partner how a tester verifies two of them

Don't try to do the whole backlog here, there's no time for that. Pick the stories for submission, acknowledgement and resolution.

```
Write acceptance criteria for these user stories:

[paste the stories]

Rules:
- Use Given/When/Then
- Every criterion must be testable: a tester can read it and know exactly how to verify it
- No vague language like "promptly" or "user-friendly"
- Use the exact numbers and timeframes from the source material
```

* Compare every timeframe with the brief. Acknowledgement is 2 working days, resolution is 5 working days (internal target) and 8 weeks (the regulation). Did the AI keep the 5 days and the 8 weeks apart, or did it mash them into one number?
* Take two criteria and explain to your partner how a tester would verify them. If you can't, rewrite them.

### Prompt 4: interrogate the output

* **Read:** your **Backlog** section, with the acceptance criteria
* **Create:** fixes in the **Backlog** section, and a line in **Decisions** for everything you changed
* **Done when:** for each of the five facts below, you opened the story the AI points to and saw that the fact is really in it. A fact that isn't, you add or you flag as a gap

This is the most important prompt of the block, so please don't skip it.

```
Review the backlog and acceptance criteria you generated against these facts from the
source material. For each fact, tell me whether it is covered, where exactly (which story),
and what a development team would build wrong if it were missing.

- Acknowledgement within 2 working days is a regulatory requirement
- Resolution has a 5-day internal target AND an 8-week regulatory obligation
- Regulatory complaints must be escalated to compliance within 2 working days
- All complaint records are retained for 5 years
- Auto-closing on customer non-response is rejected by both Marc and Priya
```

* For every fact the AI claims is covered, open the story it points to. Is it really in there?

### Got some time left? Prepare questions for the client

* **Read:** your **Open questions** section
* **Create:** the questions for each stakeholder, under the matching entry in **Open questions**
* **Done when:** every open question has a stakeholder and neutral questions, and none of them is a leading question

```
Here is our open-questions list: [paste it]

For each question, name the stakeholder who has to answer it (Sarah, Marc, Priya, or the
commercial team). Then write 1 open question, 2 to 3 probing questions and 1 closed question
to ask them. Do not suggest what the answer probably is.
```

> Keep an eye out for leading questions. "Would 7 days be acceptable for auto-close?" sounds harmless, but it already picks Sarah's side. Rewrite those into neutral questions.

---

## Pair CD: terminology, glossary and business rules

### Prompt 1: audit the terminology

* **Read:** `meridian-brief.md`
* **Create:** the audit as rough notes at the top of the **Glossary** section
* **Done when:** you have the three lists (different words for the same thing, the same word with different meanings, undefined terms), each with the exact quote and who said it

```
Here is the source material for a Complaint Management System:

[paste or attach meridian-brief.md]

Audit the terminology:
1. Where do stakeholders use different words for the same thing?
2. Where does the same word mean different things to different people?
3. Which terms are used without ever being defined?

Quote the exact words and who used them. Use only what is in the documents.
```

* Look at the word "escalation". Sarah uses it for a missed 5-day deadline that goes to the team leader. Priya uses it for a regulatory complaint that goes to compliance. Those are two completely different things. Did the AI notice?

### Prompt 2: build the glossary

* **Read:** your terminology audit
* **Create:** the glossary in the **Glossary** section
* **Done when:** all ten terms from the prompt are defined, you checked three definitions against the brief, and pair AB has a copy

```
Based on the terminology audit, write a glossary. For each term: one precise definition,
the document(s) it comes from, and any conflicting usage you resolved and how.

Include at least: complaint, complaint category, complaints handler, team leader,
acknowledgement, resolution, escalation, extension, regulatory complaint, business customer.
```

* Pick three definitions and check them against the brief yourself.
* Share the glossary with pair AB as soon as it's more or less stable. Their stories should use the same words as your glossary.

### Prompt 3: extract the business rules

* **Read:** `meridian-brief.md` and your glossary
* **Create:** a new section **Business rules** in your shared place
* **Done when:** every rule has a source and a speaker, conflicts are flagged and not resolved, and the timeframes in your list match the ones you counted in the brief

```
Extract every business rule from the source material. A business rule is something the
system must enforce: a timeframe, a condition, a mandatory step, a prohibition.

For each rule:
1. State it in one sentence
2. Quote the source and who said it
3. Flag any conflict with another rule

Do not resolve conflicts. Only surface them.
```

* Count the timeframes in the brief yourself (there are only a handful of them). Did the AI find all of them, with the right numbers?
* The auto-close rule should show up as a conflict, not as "the system closes complaints after 7 days". Is it flagged?

Hang on to this list, we'll need it again in Block 2.

### Prompt 4: a domain model diagram

* **Read:** your glossary and `meridian-brief.md`
* **Create:** a new section **Diagrams** in your shared place, with the Mermaid code of the domain model
* **Done when:** the diagram renders in mermaid.live, and you know whether a regulatory complaint is its own thing in the model or just a value in a list

```
Based on the source material and our glossary, propose a domain model as a Mermaid class
diagram. Include the main entities (complaint, category, handler, team leader, customer,
extension request, escalation), their key attributes and their relationships with
cardinality.
```

* Paste the result into [mermaid.live](https://mermaid.live). Does it render? AI-generated Mermaid often has a small syntax error somewhere. If it does, don't start fixing it yourself: paste the error back into the chat and let the AI fix it.
* Is a regulatory complaint something different from a standard complaint in the model, or is it just another value in a list?

---

## The last 15 minutes, with your whole team: write your house rules

By now you've probably typed "use only the source", "quote it" and "label inferences" about five times. That's annoying, and it's easy to forget one of them. So let's write them down once.

* **Read:** your two or three best prompts of this morning
* **Create:** a new section **Instructions** in your shared place (10 to 20 lines)
* **Done when:** you ran one of your earlier prompts again in a new chat without the extra rules, and the answer still follows them

Together with the other pair, write a short instructions file for this engagement (10 to 20 lines). Use the lines from your prompts that made the biggest difference. You can let the AI draft it, but do edit it yourselves afterwards:

```
Based on the prompts we used this morning [paste 2 or 3 of your best prompts], write a short
set of standing instructions for an AI assistant working on this requirements engagement.
Cover: our role, the output formats we use, how to handle the source material, how to
handle contradictions, and our glossary terms. Keep it under 20 lines.
```

* Save it in your team's shared document under the new section **Instructions**.
* Try it out. In M365 Copilot, paste it into Settings → Personalization → Custom instructions (or in the instructions of a Copilot Notebook). In Claude.ai, create a Project and paste it into the project instructions. Using GitHub Copilot? Hold on to it, that one comes in Block 2.
* Start a new chat and run one of your earlier prompts again, but this time without all the extra rules. Does the answer still follow them?

> Want to know what each tool supports exactly? Take a look at `ai-cheat-sheets/working-efficiently.md`.

---

### Done?

Before Retro 1 at 11:00, your team should have:

* An open-questions list with real entries in it, the auto-close conflict being one of them
* A first backlog, with a source quote for every story
* Acceptance criteria for the core flow, with the right timeframes
* A glossary with the 10 core terms, and a list of business rules with the conflicts flagged
* A domain model that renders in mermaid.live
* Your team's instructions file, which you tried at least once

What you learned in this block:
* How to build a prompt that gives AI the source, the task, the format and the rules it needs
* How to make AI quote its source and label its guesses, so you can actually check it
* How to spot-check AI output against the brief in a couple of minutes
* How to stop retyping the same rules by turning them into custom instructions
