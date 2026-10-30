# Voice Polish

A Claude skill that makes writing sound like you. It does three things:

1. **Rewrite as me:** paste text (your rough draft, an AI draft, anything) and get it back sounding like you wrote it.
2. **Write as me:** ask Claude to write or answer something, and it writes it the way you would.
3. **Translate (English ↔ Korean):** paste text and say "translate this to Korean" (or English). It reads the context and uses the most natural, common words for that kind of writing, plus the right industry and official terms, like customs (HS code) item names and product names. It keeps codes and numbers exactly as they are, and lists any official term it isn't sure of so you can check it. Translation works right away, even before you set up your voice profile.

It learns your voice from your own essays and emails. It never makes up stories or facts about you, and it asks when it needs details.

It also does:

- **Match a format:** share an article (or any example) and say "write this in the same format." It copies the shape, like the headline, sections, and paragraph length, but keeps your own words.
- **Remember your terms:** tell it "the official name is X" or "in our industry we say Y," and it saves the term to a glossary and uses it every time. You can also share a glossary or an official term list.
- **Swap fancy words:** say "this word sounds too AI" or "too advanced," and it swaps in the word you'd actually use and remembers not to use it again.
- **Korean (한국어):** everything works in Korean too. Share a few things you wrote in Korean so it learns your Korean voice, including how you use 반말 or 존댓말 and things like ㅎㅎ or ^^.

## Install

Download `voice-polish.zip` from the [latest release](https://github.com/smelvintime/voice-polish/releases/latest).

**On claude.ai or the Claude app:** open Customize, then Skills, then Add, then Upload skill, and choose `voice-polish.zip`.

**In Claude Code:** unzip it into your skills folder, so the result is `~/.claude/skills/voice-polish/SKILL.md`.

## Train it on your writing

Start a chat and say **"set up my voice profile."** Then paste 3 to 5 things you wrote yourself, such as essays, papers, and a few emails. Around 1,500 words or more works well. Use writing nobody else (and no AI) polished. If you write in Korean, include 2 or 3 Korean pieces too. You can also start in Korean: **"내 말투 프로필 만들어 줘."**

Claude builds your profile, shows you a short summary to check, and saves it:

- **Claude Code:** it saves automatically.
- **claude.ai:** Claude gives you a `voice-profile.md` file. Open Customize, then Skills, then voice-polish, and replace `references/voice-profile.md` with it. Until you do, the profile only lasts for that one chat.

To add more writing later, say "add this to my voice profile" and paste it in. If Claude ever changes something you'd never write, tell it ("I would never say that"), and it records the rule.

## Privacy

Your filled-in profile contains quotes from your own writing. Share the blank skill freely, but keep your trained copy to yourself.
