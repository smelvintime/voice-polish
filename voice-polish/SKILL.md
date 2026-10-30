---
name: voice-polish
description: Make text sound like the user wrote it, or write something new that sounds like them, using a voice profile trained on their own essays and emails. Use this whenever the user pastes text (their own rough draft, an AI draft, someone else's wording, or notes) and wants it fixed, fixed up, cleaned up, polished, proofread, rewritten, made more readable or more professional, or made to "sound like me." Also use whenever they ask for something new written or answered in their voice ("write it the way I would," "reply as me," "answer this like I would," "in my voice"), including emails, messages, discussion posts, and essays. Trigger even on terse requests like "fix up" attached to pasted text. Also use when the user wants to set up or train their voice profile, shares essays or writing samples to teach their style, or pushes back on how an edit or draft changed their wording.
---

# Voice Polish

This skill does two jobs, and both have the same finish line: the user reads the result and thinks "that's how I would have written it," not "an AI wrote this."

1. **Rewrite as me.** The user hands over text and wants it to sound like they wrote it.
2. **Write as me.** The user wants something new, such as an answer, reply, email, post, or essay, written the way they would write it.

Both jobs run on a voice profile built from the user's own writing. Everything else in this file serves those two jobs.

The skill exists because generic AI writing drifts. It quietly swaps plain words for fancier ones, evens out the rhythm, pads short messages into boilerplate, and fills gaps with made-up details. The result is clean text the user would never actually say.

## Step 0: Make sure there is a profile

Read `references/voice-profile.md`. If its first line still says `STATUS: NOT SET UP`, or it has no exemplars, the skill does not know this user's voice yet. Run **Setup** below before anything else. If the user only wants a quick fix right now and declines setup, do a careful light-touch edit (mechanics only, their wording kept) and say in one line that it is not tuned to their voice until they add samples.

## Setup: training the profile on their writing

1. **Ask for samples.** Request 3 to 5 pieces they wrote carefully themselves, ideally a mix: essays or papers, plus a few emails or longer messages. Around 1,500 words or more in total gives a good start. Only their own writing: nothing an AI or someone else polished, since that would teach the wrong voice. Quick texts are optional and only teach typo habits. Ask what each piece is (class essay, application essay, work email) so registers can be told apart.
2. **Build the profile.** Fill in every section of the template from the samples alone, with short verbatim quotes as evidence. Record patterns, not one-off quirks. Where the samples show nothing for a section, write "not enough samples yet" rather than guessing.
   - **Punctuation inventory:** list the marks they actually use. A mark that never appears across the samples is foreign. Ask them to confirm the list, since it is enforced strictly.
   - **Personal stories on record:** list only stories that appear in the samples, with only the details given there.
   - **Exemplars:** 5 to 8 short verbatim excerpts that best show the voice.
3. **Check with them.** Show a short summary (a few lines on how they write) and ask if anything is off. Fix what they correct and log it in the Corrections log.
4. **Save it.** Replace the whole template with the finished profile, and change the first line to `STATUS: SET UP`.
   - In Claude Code, write `references/voice-profile.md` directly.
   - On claude.ai, chat cannot change a skill's files. Give them the finished `voice-profile.md` as a file and tell them to open Customize, then Skills, then voice-polish, and replace `references/voice-profile.md` with it (edit and paste, or re-upload the skill folder with the new file in it). Until they do, the profile only lasts for this conversation.

Run the same steps, merged into the existing profile, whenever they share more writing later.

## Step 1: Read the voice profile

Read the profile before writing anything, for both jobs. It records how the user writes when writing carefully, their register ladder, their punctuation inventory, their typo habits, their personal stories on record, and the corrections they have given on past work. When the profile conflicts with what you would normally "improve," the profile wins, and entries in its Corrections log outrank everything else in the file.

## Step 2: Work out the job, and what is missing

- Pasted text plus any fix, polish, rewrite, or "sound like me" request is Job 1.
- A question to answer, a message to reply to, or a piece to write, with a signal that it should sound like them, is Job 2. A plain "write me an email about X" with no voice signal is an ordinary drafting request, and this skill should not hijack it.
- Before writing, check that you have what the piece needs. If something important is missing, see "When to ask."

## Job 1: Rewrite as me

How much to change depends on how far the text already is from the user's voice. Read the input against the profile first.

- **Already theirs, just rough** (their own draft with typos, tangles, or half-gibberish): the pasted text is the style guide. Fix the mechanics, untangle only what a reader would misread, and leave the wording, rhythm, hedges, contractions, and formatting alone. Every output sentence should be traceable to an input sentence. This is the most common case, and "improving" their own words to sound more like them is the classic failure.
- **Not in their voice** (an AI draft, someone else's wording, or the user says it came out wrong or weird): the input supplies the content and the profile supplies the voice. Rebuild the sentences from the profile's documented parts: their connectives, their vocabulary level, their sentence shapes, their punctuation. The test is that it reads like the same person on a day when the sentences came out right, not like a different and better writer.
- **Mixed:** judge it sentence by sentence.
- **"Just fix the spelling," "proofread this":** mechanics only, whatever the wording.

When it is unclear which depth fits, default to the light touch and add one line saying a fuller rewrite is available.

Content rules at every depth: keep every fact, claim, number, date, name, quotation, and hedge exactly as given. Rewriting changes how it sounds, never what it asserts or how sure it is. Never add an example, story, opinion, or closing summary the user did not write, and keep the length close to the original unless they ask for expansion.

**Always fixed (mechanics):** absolute, in every register, with no exceptions for rhythm or for how characteristic the mistake is. An authentic mistake is still a mistake.
- Spelling and typos, including every known habit in the profile
- Missing, doubled, or run-together words
- Wrong homophones and autocorrect casualties
- Subject-verb agreement, tense consistency, article and plural use
- Capitalization and basic punctuation (missing periods, fused sentences, stray commas)
- Punctuation outside the profile's inventory, converted per the section below

**Fixed only when clarity genuinely suffers:**
- A sentence tangled enough that a reader could misread it: untangle it with the smallest edit, reusing their own words
- A run-on that is actually hard to follow: split it at the natural seam. A long sentence that reads fine stays long
- A genuinely ambiguous pronoun or reference

**Their voice, protected:** in the light touch these stay exactly as written; in a rebuild they are the target, taken from the profile.
- Word choice and vocabulary level. If they wrote "big," do not write "significant"
- The mix of short and long sentences
- Casual connectives, softeners, and hedges. Hedging is content: it encodes how sure they are, so never strengthen or weaken a claim
- Contractions or full forms, as they wrote them
- Deliberate fragments, line breaks, and paragraph breaks
- Humor, asides, and personality

The line between fixed and protected is correctness, not formality. Informal-but-correct choices are voice and stay.

## Job 2: Write as me

The user and the request supply the content; the profile supplies only the voice.

- Reread two or three exemplars of the same kind before drafting: email exemplars for an email, essay exemplars for an essay.
- Draft in two passes: first write the piece for substance in plain neutral wording, then translate it sentence by sentence into their voice with the profile open. Voice applied in a deliberate second pass lands at their natural rate; voice generated on the fly tends to overshoot, piling on hedges and quirks, or undershoot.
- Follow the profile's documented shapes: how their emails open and close, how long they run, how their essays open and carry their points. Match length to what they would actually write.
- Copy the variance, not just the vocabulary. Most people's writing swings between long and short sentences; match the swing shown in the exemplars. Evenly sized sentences throughout read as AI-written.
- Connect sentences the way they do, using the connectives and openers the profile records, and use contractions at the rate their samples show.
- Hedge at their real rate with their own hedges, skip balanced maxims and tidy parallel lists, and never go chattier or fancier than their careful writing.
- **No made-up content.** Never invent facts, names, dates, numbers, quotes, citations, commitments, or opinions they did not give. A personal story or example is usable only if it is listed in the profile's stories on record, or the user gives it in this conversation. If none fits, there is no story to use: write the point without one, leave a [bracketed placeholder], or ask.
- The test: set it next to the profile's exemplars and it should read like their sibling, something the user could have typed on a good day.

## When to ask

Asking for direction is welcome; guessing on things that matter is not. Ask in one short round, batching the questions and using AskUserQuestion where it is available, when:

- A fact the piece needs is missing: a name, date, number, commitment, or what they actually want to say.
- The purpose, audience, or length is unclear enough to change the register (a professor or a friend, a discussion post or an application essay).
- The piece seems to call for a personal story and none is on record.
- A garbled passage has two plausible readings that change what it says.

Do not ask about what the request or profile already answers, and never ask twice about the same text. If the session looks unattended, take the safest reading, use [placeholders] for missing specifics, and flag what you assumed.

## Register

Match the register to the piece using the profile's ladder. Everyday careful is the default. Any higher register the profile records (application essays, for example) is used only when the user explicitly asks for that level.

- **More formal:** "make it more professional" raises the register within their own careful range, never into corporate speak, and never makes it longer.
- **Tighter:** "tighten this up" cuts redundancy and repetition, still in their words.

## Punctuation inventory

The profile's Punctuation section is an inventory, not a description of tendencies. A mark the user does not use is foreign in their sentences even when correct. Foreign marks are converted in every job, including a pass that otherwise changes nothing.

- Convert to the nearest mark they do use, keeping the wording intact, following any conversions the profile lists. Typical: a mid-sentence colon becomes a comma, a semicolon becomes a comma or a sentence break, an em dash becomes a comma or whatever dash they actually type. A colon introducing an actual list stays.
- Never convert in the other direction, and never add a mark outside the inventory.
- Quotations from a source keep the author's punctuation unless the Corrections log says otherwise, and any altered quotation gets a one-line flag.

## The failure mode to avoid

These are the tells of AI-smoothed text. Never introduce them, in either job:

- Upgraded vocabulary: "use" to "utilize," "so" to "therefore," "help" to "facilitate," "big" to "significant"
- Added transitions the user does not use: "Moreover," "Furthermore," "Additionally," "In conclusion"
- Restructuring into topic-sentence essay form, or merging their short lines and paragraphs
- Any mark outside the punctuation inventory
- Evening out sentence lengths, or padding with context, examples, pleasantries, or a closing summary they did not write
- Editing the message's intent: do not soften a complaint, warm up a cold note, or add enthusiasm that is not there
- Filling a gap with an invented detail instead of a placeholder or a question

## Gibberish and ambiguity

When a passage is garbled but context makes the intent clear, repair it confidently and silently. When it is genuinely ambiguous, pick the most likely reading and add a brief flag after the output quoting the original fragment and the reading you chose, or ask first if the detail is meaning-critical (names, numbers, dates, negations, who did what to whom).

Negation typos (a "not" where the text clearly means "now," a dropped "no") get fixed from context but always with a one-line flag. Language is yours to fix while content is not: if the text seems to contain a factual or terminology error, leave it as written and mention it in a brief flag.

## Final sweep

Before presenting anything, re-read the text once purely for mechanics: check it against the always-fixed list and the profile's typo habits item by item. Then scan the punctuation alone, mark by mark, against the inventory. Finally confirm nothing of yours crept in: no added transitions, no vocabulary upgrades, no invented details.

## Output format

Default: the text only, cleanly separated so it is easy to copy, with at most a few words of lead-in. No change list and no commentary about preserving their voice. Add a short flag only when the ambiguity rule requires it, when a quotation was altered, when you used a placeholder or an assumption, or when the user asks what changed. For long pieces, put the result in a file or artifact if the surface supports it.

Be accurate about what you did. Call a light fix a fix and a rebuild a rewrite, and never claim the output sounds like the user as though that had been verified.

## Maintaining the voice profile

Update the profile in two situations, saving it the same way as in Setup step 4:

1. **The user shares more samples.** Merge what they show into the existing sections. Only learn style from careful writing; rushed text may only update typo habits. Add at most 2 or 3 excerpts to Exemplars per update, and add any personal stories the samples contain to stories on record. Text they asked to have rewritten is not a style sample. Never widen the punctuation inventory from a sample; only the user saying they use a mark can add one.
2. **The user corrects an edit or draft** ("I would never say that," "keep the X"). Record the inferred rule in the Corrections log with a date. These entries become the highest authority in the profile.

Keep the whole profile under roughly 150 lines. Merge and condense rather than appending forever.
