---
name: voice-polish
description: Make text sound like the user wrote it, or write something new that sounds like them, in English or Korean. Use whenever the user pastes text (their own rough draft, an AI draft, someone else's wording, or notes) and wants it fixed, cleaned up, polished, proofread, rewritten, made more professional, or made to "sound like me"; whenever they ask for something written or answered in their voice ("write it the way I would," "reply as me," "in my voice," "내 말투로"); whenever they want English and Korean translated into each other naturally with the right industry or official terms; and whenever they share a reference such as an article and want writing done in that format but in their own words. Trigger even on terse requests like "fix up," "고쳐 줘," or "다듬어 줘" attached to pasted text. Also use when they want to set up or train their voice profile, flag a word as too AI or too advanced, share writing samples, or push back on how an edit changed their wording.
---

# Voice Polish

This skill does three jobs, and all of them have the same finish line: the user reads the result and thinks "that's how I would have written it," not "an AI wrote this."

1. **Rewrite as me.** The user hands over text and wants it to sound like they wrote it.
2. **Write as me.** The user wants something new, such as an answer, reply, email, post, or essay, written the way they would write it.
3. **Translate.** The user wants English turned into Korean or Korean into English, reading as if it were written in that language, with the right terms for the context.

Both jobs run on a voice profile built from the user's own writing. Everything else in this file serves those two jobs.

The skill exists because generic AI writing drifts. It quietly swaps plain words for fancier ones, evens out the rhythm, pads short messages into boilerplate, and fills gaps with made-up details. The result is clean text the user would never actually say.

## Step 0: Make sure there is a profile

Read `references/voice-profile.md`. If its first line still says `STATUS: NOT SET UP`, or it has no exemplars, the skill does not know this user's voice yet. Run **Setup** below before anything else, except for translating text someone else wrote (Job 3), which does not need a profile. If the user only wants a quick fix right now and declines setup, do a careful light-touch edit (mechanics only, their wording kept) and say in one line that it is not tuned to their voice until they add samples.

## Setup: training the profile on their writing

1. **Ask for samples.** Request 3 to 5 pieces they wrote carefully themselves, ideally a mix: essays or papers, plus a few emails or longer messages. Around 1,500 words or more in total gives a good start. Only their own writing: nothing an AI or someone else polished, since that would teach the wrong voice. Quick texts are optional and only teach typo habits. Ask what each piece is (class essay, application essay, work email) so registers can be told apart. Ask which languages they write in: if they write in Korean too, ask for 2 or 3 Korean pieces for the Korean voice section, and if they only write in Korean, the Korean samples are the whole profile.
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
- A request to translate between English and Korean is Job 3.
- Any job can come with a reference document (an article, a sample of the kind of writing they want). Then the reference sets the format; see "Reference documents."
- Korean text or a Korean request follows the same steps; see "Korean."
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

## Job 3: Translate (English ↔ Korean)

The user wants text moved from one language to the other. The goal is text that reads as if it had been written in the target language from the start, by someone who knows the subject, not a word-for-word copy that only reads correctly to the translator.

- **Read the whole thing first** and work out the context: what kind of writing it is (news article, product description, customs or trade document, email, essay), who will read it, and what field it belongs to. The context decides the words.
- **Translate the meaning, sentence by sentence,** then reshape each sentence the way the target language says it: natural word order, natural sentence length, and the connectives and endings that kind of writing uses in that language. Split or merge sentences when the target language needs it, but never drop or add a fact.
- **Use the most common, natural word for that context** in the target language: the word a native writer in that field would reach for. Not the richest or most literary option, and not a literal calque. For terms of art, follow "Terms of art and official names" below.
- **Register follows the target genre.** A Korean article is usually in 한다체; a Korean business email is usually in 합니다체 or 해요체; an English article is plain and direct. If the user shared a reference, it sets the format exactly as in "Reference documents."
- **Voice:** if the user is translating their own writing, the profile's voice for the target language applies. Otherwise, write plain and natural for the genre and do not impose the user's voice on someone else's text.
- **Never translate these:** codes and numbers (HS codes, model numbers, prices, dates, units), proper names of companies, people, and brands unless a standard target-language name exists, and anything the user asks to keep. Convert units or date formats only if asked.
- **After the output,** add a short "Terms to check" list naming any official or technical term you were not certain of, with the original term next to it. Leave the list out when there is nothing to check.

## Reference documents: borrow the format, keep the voice

Sometimes the user shares a reference, such as an article, a blog post, a cover letter, a speech, or a report, and asks for something written or rewritten "in this format," "like this," or "the same way." Different kinds of writing have different shapes, and an article is built differently from a school paragraph. The reference supplies the **form**, the profile supplies the **voice**, and the user supplies the **content**.

Take from the reference (form):
- The kind of writing and its structure: headline, opening hook or lede, subheadings, section order, how it opens and closes
- Paragraph length and count, and overall length
- Point of view and tense (first person, "you," third person)
- How points are set up and supported: where examples, quotes, or numbers sit and how sections hand off to each other
- Formatting: lists, bold, captions, bylines, Q&A blocks
- The register of the genre, as a target on the user's own ladder (see below)

Do not take from the reference (voice and content):
- Its vocabulary, signature phrases, or fancy words. Formality comes from the structure, not from the words. The exception is terms of art: the standard industry or official terms a reference uses for things are the right terms (see "Terms of art and official names")
- Its facts, quotes, numbers, or examples, unless the user says to use them as a source. Then quote and credit them as a source would be quoted
- Punctuation outside the user's inventory

Word choice stays theirs. When a sentence seems to call for a big or AI-looking word, use the plain word the user would actually use. If the genre needs a level above everything on their ladder, write at the top of their own careful register; a reference never licenses words they would not use.

Working rules:
- Read the whole reference first and note its structure before writing. After the output, add one short line naming the format features you borrowed (for example: "Format from the reference: headline, two-sentence hook, three subheaded sections, short closing line"), so the user can correct it.
- If the reference is ambiguous about what to copy (it mixes a news section and an opinion section, say), ask which part they mean.
- It is temporary. The reference applies to this conversation until the user says to stop or shares a new one. Never learn style from it into the voice profile and never add its excerpts to the profile, since it is not the user's own writing.
- Job 1 and Job 2 both work with a reference. Rewriting into a new format is always a rebuild, never the light touch, but every content rule still holds.

## Terms of art and official names

Technical, industry, legal, and government terms are content, not style. For these the rule flips: use the standard term the field actually uses, even if it is formal or not a word the user would use casually. The plain-word rules apply to everything around those terms.

- **Where the right term comes from, in order:** a term the user gives or corrects; the profile's Glossary; a glossary or official source the user shares in the conversation; the term used in a reference document they shared; then the standard term you know for that field.
- **Official names** (customs and HS code product names, government program names, legal terms, regulatory terms): use the official wording, not a paraphrase. If you are not sure the wording is the official one, use your best match and put it in the "Terms to check" list, and suggest checking it against the official source (for Korean customs names, the Korea Customs Service's tariff classification lookup). Never invent an official name, code, or classification, and never change a code the user gave.
- **Product and brand names:** keep the name the company uses in that market. If you do not know the target-market name, keep the original and flag it.
- **The plain-word swap list never overrides a term of art.** "Plain" means plain for that context: in a customs document, the official item name is the plain choice.
- When the user corrects a term ("the official name is X," "in our industry we say Y"), add it to the profile's Glossary so it is used every time after.

## Plain-word swaps

Some words read as AI-written or simply too advanced for how the user talks. Common offenders: utilize, leverage, delve, pivotal, crucial, robust, seamless, foster, bolster, navigate (for "deal with"), landscape, realm, tapestry, multifaceted, showcase, underscore, embark, endeavor, plethora, Moreover, Furthermore, Additionally, In conclusion. Never introduce them, in any job or format, unless the profile shows the user uses that word at that register.

When the user flags a word ("this sounds too AI," "I'd never say that word," "too advanced"), swap it for the plainest word that keeps the meaning, in the profile's vocabulary, and add the pair to the profile's Plain-word swaps list so it never comes back.

## Korean (한국어)

Everything in this skill applies to Korean the same way: both jobs, reference documents, plain-word swaps, the no-made-up-content rule, when to ask, the punctuation inventory, and the final sweep.

- **Language:** work in the language of the text being rewritten. For Job 2, use the language the user asks for, or the one they wrote the request in. Never translate unless asked; when asked, follow Job 3. Keep English words and Konglish the way the user mixes them in.
- **Voice source:** a Korean voice comes from Korean samples, kept in the profile's "Korean voice" section. English samples transfer only general traits: vocabulary level, how often they hedge, sentence-length swing, directness, and humor. Never carry English phrasing over literally.
- **No Korean samples yet:** for Job 1 at the light touch, the pasted Korean text is the style guide, so go ahead. For a rebuild or for Job 2, ask once for 2 or 3 things they wrote in Korean themselves (KakaoTalk messages, emails, school writing) and add them to the Korean voice section the same way as any samples. If they would rather not, write plain, natural Korean at the register the piece needs and say in one line that it is not tuned to their Korean voice yet.
- **Always fixed (Korean mechanics):** 맞춤법 (되/돼, 안/않, 데/대, 로서/로써, 든지/던지, 웬/왠, 금세, 어떡해/어떻게), 띄어쓰기 (dependent nouns such as 것, 수, 때, 만큼, 뿐, 데 are spaced; particles attach to the word before them; 하다 verbs stay joined), particle errors, tense, honorific agreement (the -시- subject honorific and endings that match), and keyboard or 자모 typos.
- **Register is the speech level:** 반말 for close friends and family, 해요체 for everyday polite, 합니다체 for formal speech and formal emails, and 한다체 (plain -다 endings) for essays, reports, and articles. Keep the speech level the user wrote in and never switch it unless asked. A reference article will usually be in 한다체; that is form, so take it from the reference.
- **Korean AI tells to avoid:** stacked connectives (또한, 더불어, 나아가, 아울러, 뿐만 아니라, 이를 통해, 결론적으로); heavy Sino-Korean or abstract words where a plain native word works (활용하다 for 쓰다, 도모하다, 제고하다, 함양하다, 극대화, 시사하는 바가 크다); translationese (~에 있어서, ~을 가지다 for "have," ~에 의해 passives, 되어지다, piling up 그/그녀/그들, sentences ending again and again in ~것이다); and tidy three-part lists. Plain-word swaps work the same way in Korean: flagged words go on the swap list.
- **Texture is voice:** ㅋㅋ, ㅎㅎ, ^^, ~, !!, and trailing ... are part of how many people write in Korean. Keep them where the user uses them, never add them where they do not, and list them in the punctuation inventory once they show up in samples.

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

- Upgraded vocabulary (see Plain-word swaps): "use" to "utilize," "so" to "therefore," "help" to "facilitate," "big" to "significant"
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
3. **The user gives or corrects a term** ("the official name is X," "in our industry we say Y"). Add it to the Glossary with the language pair and the context it applies to.

Keep the whole profile under roughly 150 lines. Merge and condense rather than appending forever.
