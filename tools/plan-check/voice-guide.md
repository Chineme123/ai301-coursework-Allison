# Voice guide: how I talk upstream

<!--
THIS IS THE PART YOU WRITE (new this week). Live mode reads this file
before any comment of yours goes out the door; eval mode ignores it
entirely, because your voice is yours and carries no gold labels.

This is not etiquette. "Be polite and concise" is advice for everyone
and therefore rules for no one. Write rules YOU need, in your own
words, each one concrete enough that the skill can hold a draft
against it and say which rule it breaks.

Three sections. Fill all three.
-->

## Who I am in threads

<!-- 2-3 lines. Who is talking when you comment on an issue: your
experience level stated plainly, what you are doing in this repo, what
readers can expect from you. This is the register your rules protect. -->

I am a student developer making my first open-source contribution. I
work mainly with JavaScript, Python, and C#, and I am especially
interested in backend work. My natural professional voice is
conversational and practical: I give concrete context, explain what I
tried, and say clearly what I need or plan to do next.

## Rules I write by

<!-- 3-5 rules, drafted from the lecture's slide-12 moment. Each rule
needs a wrong/right pair from your own hand: one line you might
actually have written that breaks the rule, and the line you would
post instead. The pair is what makes a rule executable; a rule without
one is a wish.

Format each rule like this:

### Rule: <short name>

<The rule, one or two sentences.>

- Wrong: "<a line that breaks it>"
- Right: "<the line to post instead>"
-->

### Rule: Brief greeting, then context

A short greeting is natural for me, but the next sentence should state
the issue or status directly. Do not spend a paragraph being enthusiastic
or formal before reaching the point.

- Wrong: "Hello everyone! I am very excited for this wonderful opportunity to contribute to the project."
- Right: "Hi, I'd like to investigate why failed tool-call results do not reach the review output."

### Rule: Explain what I tried

Give relevant actions in a practical order so the reader does not suggest
the same steps again. Keep concrete details and remove unrelated narration.

- Wrong: "I tried many things, but nothing worked and I am stuck."
- Right: "I ran the review flow three times. Each run recorded the failure in `tool_results`, but the final review omitted it."

### Rule: State evidence and uncertainty separately

Say what I observed, then use plain language such as "I believe" or "I
have not confirmed" for my interpretation. Do not turn a reasonable guess
into a fact.

- Wrong: "The review service is definitely dropping the result."
- Right: "The result leaves the orchestrator successfully, so I believe the review service may be involved. I have not confirmed where it is dropped yet."

### Rule: Be practical and open to another view

When I suggest an approach or disagree, explain the immediate benefit and
risk. State my preference directly while leaving room for information I
may be missing.

- Wrong: "A rewrite makes no sense. We should just change the variable."
- Right: "I believe a smaller change could resolve the immediate error with less risk. I am open to understanding why a full rewrite may still be necessary."

### Rule: End with the request or next step

Finish by saying what I need from the reader or what I will do next. For
a claim, promise the investigation and report, never a fix or deadline.

- Wrong: "I'll fix this by tomorrow and open a pull request."
- Right: "I'll trace the result through the orchestrator and review service, then report what I find."

## Things I never post

<!-- A short list. Promises you cannot keep, tones you refuse,
shortcuts you know you reach for when tired. The skill quotes this
list back at you when a draft crosses it. -->

- Long introductions, decorative prose, or filler before the point.
- Formal wording I would not naturally use when plain language is clearer.
- A promise to fix the issue or finish by a particular date.
- Certainty that is stronger than the evidence.
- "Same as above" or a copied conclusion without my own reproduction evidence.
- An unexplained screenshot, log, or error dump with no connection to the issue.
- Credentials, tokens, secrets, or private environment values.
