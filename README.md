# Voice Polish

A Claude skill that makes writing sound like you. It does two things:

1. **Rewrite as me:** paste text (your rough draft, an AI draft, anything) and get it back sounding like you wrote it.
2. **Write as me:** ask Claude to write or answer something, and it writes it the way you would.

It learns your voice from your own essays and emails. It never makes up stories or facts about you, and it asks when it needs details.

## Install

Download `voice-polish.zip` from the [latest release](https://github.com/smelvintime/voice-polish/releases/latest).

**On claude.ai or the Claude app:** open Customize, then Skills, then Add, then Upload skill, and choose `voice-polish.zip`.

**In Claude Code:** unzip it into your skills folder, so the result is `~/.claude/skills/voice-polish/SKILL.md`.

## Train it on your writing

Start a chat and say **"set up my voice profile."** Then paste 3 to 5 things you wrote yourself, such as essays, papers, and a few emails. Around 1,500 words or more works well. Use writing nobody else (and no AI) polished.

Claude builds your profile, shows you a short summary to check, and saves it:

- **Claude Code:** it saves automatically.
- **claude.ai:** Claude gives you a `voice-profile.md` file. Open Customize, then Skills, then voice-polish, and replace `references/voice-profile.md` with it. Until you do, the profile only lasts for that one chat.

To add more writing later, say "add this to my voice profile" and paste it in. If Claude ever changes something you'd never write, tell it ("I would never say that"), and it records the rule.

## Privacy

Your filled-in profile contains quotes from your own writing. Share the blank skill freely, but keep your trained copy to yourself.
