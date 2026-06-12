# CHANNEL_TTS_RULES.md

## FILE ROLE

This file defines the channel-level rules for preparing narration text for **MiniMax Text-to-Speech**.

It controls:

```text
MiniMax mode
default voice
speed / pitch / volume
beat-based TTS splitting
pause and pacing rules
clean TTS formatting
duration estimation
audio naming
CapCut assembly notes
```

It does **not** control:

```text
episode thesis
script structure
visual map
Veo prompts
edit plan
historical era locks
```

---

## AUTHORITY

This file follows:

```text
CHANNEL_IDENTITY.md
CHANNEL_STYLE_LOCK.md
CHANNEL_WORKFLOW_CONTROL.md
```

It is used when creating:

```text
02_TTS_CLEAN_BY_BEAT.md
```

or any short-form TTS-ready narration file.

If this file conflicts with a locked script, the locked script wins for wording.

This file only controls TTS preparation and delivery settings.

---

## USED BY WHICH ROOM

Use this file in:

```text
SCRIPT_ROOM
TTS preparation tasks
short-form voice preparation tasks
```

Primary output:

```text
02_TTS_CLEAN_BY_BEAT.md
```

or, for short videos:

```text
SHORT_##_TTS_CLEAN.md
```

---

# 1. MINIMAX SETTINGS

## 1.1 Mode

Use:

```text
MiniMax mode: Text-to-Speech
```

Do not use voice cloning or advanced voice design unless the user explicitly asks.

## 1.2 Default Voice

Default voice:

```text
Voice: English_Trustworth_Man
```

Alternative UI display name may appear as:

```text
Trustworthy Man - Warm / English
```

Use the same voice across one episode unless the user explicitly approves a change.

Do not switch voice between beats.

## 1.3 Default Settings

Use:

```text
Pitch: 0
Volume: 1.0
```

Do not change pitch between beats.

Do not change volume between beats unless correcting a technical problem.

Speed may vary slightly by beat type.

---

# 2. SPEED LOGIC

The channel uses restrained documentary narration.

Do not use fast delivery.

## 2.1 Default Explanatory Speed

Use for information-heavy or mechanism-explaining beats:

```text
Speed: 0.92
```

Examples:

```text
core question
The Throne
Elite Ecosystem
conversion loop
Disruptor explanation
structural setup
connective narration
```

## 2.2 Slower Thesis Speed

Use for thesis-heavy, dark, reflective, or closing beats:

```text
Speed: 0.90
```

Examples:

```text
opening hook
absorption paradox
Invisible System
Moral Language
Price of Order / closing
lines that need weight
```

## 2.3 Short-form Voice

For short videos, start with:

```text
Speed: 0.90
Pitch: 0
Volume: 1.0
```

If the rendered voice is good but slightly long, prefer light speed adjustment in CapCut:

```text
CapCut speed: 1.05x–1.08x
```

Do not push too far above:

```text
1.10x
```

because the voice may lose documentary weight.

## 2.4 Avoid

Avoid by default:

```text
Speed: 1.0 or above
```

unless the user wants faster news-like delivery.

Avoid:

```text
Speed below 0.88
```

unless testing a deliberately slow trailer-like passage.

The channel should sound restrained, not sluggish.

---

# 3. BEAT-BASED TTS SPLITTING

Do not create one single long 10–15 minute voice file.

Reason:

```text
Long TTS files are hard to revise.
If one sentence fails, the whole file may need to be regenerated.
Beat-based files are easier to fix, replace, and assemble in CapCut.
```

Default strategy:

```text
1 BEAT = 1 TTS section
```

For long or complex beats, split into sub-sections:

```text
BEAT_08A
BEAT_08B
```

Use sub-splits only when the beat has clear internal structure.

Do not split every sentence into a separate file.

Avoid over-fragmentation.

Recommended range for an 11-minute episode:

```text
9–10 TTS sections
```

For short videos under 90 seconds, a single voice file is acceptable if revision risk is low.

---

# 4. CHINA EP00 DEFAULT TTS SPLIT

For `CHINA EP00`, use:

```text
TTS_01_BEAT_01_OPENING_HOOK
TTS_02_BEAT_02_REAL_QUESTION
TTS_03_BEAT_03_THRONE
TTS_04_BEAT_04_ELITE_ECOSYSTEM
TTS_05_BEAT_05_CONVERTS_POWER
TTS_06_BEAT_06_DISRUPTOR
TTS_07_BEAT_07_ABSORPTION
TTS_08A_BEAT_08_OPERATING_SYSTEM
TTS_08B_BEAT_08_MORAL_LANGUAGE
TTS_09_BEAT_09_PRICE_OF_ORDER
```

Recommended settings:

```text
TTS_01: Speed 0.90 | Pitch 0 | Volume 1.0
TTS_02: Speed 0.92 | Pitch 0 | Volume 1.0
TTS_03: Speed 0.92 | Pitch 0 | Volume 1.0
TTS_04: Speed 0.92 | Pitch 0 | Volume 1.0
TTS_05: Speed 0.92 | Pitch 0 | Volume 1.0
TTS_06: Speed 0.92 | Pitch 0 | Volume 1.0
TTS_07: Speed 0.90 | Pitch 0 | Volume 1.0
TTS_08A: Speed 0.90 | Pitch 0 | Volume 1.0
TTS_08B: Speed 0.90 | Pitch 0 | Volume 1.0
TTS_09: Speed 0.90 | Pitch 0 | Volume 1.0
```

---

# 5. DURATION ESTIMATION

Target time is an estimate only.

Do not treat target time as final timing.

Final timing authority:

```text
1. Rendered MiniMax audio
2. CapCut timeline
3. SRT / auto captions / manual captions
```

Use target estimate only for planning, pacing, and detecting abnormal beat length.

## 5.1 English_Trustworth_Man Approximate Speaking Rates

For voice:

```text
English_Trustworth_Man
```

Use these approximate speaking rates:

```text
Speed 0.90:
- thesis-heavy / short-line narration: ~105–110 WPM
- balanced documentary narration: ~110–115 WPM
- expository narration: ~115–120 WPM

Speed 0.92:
- thesis-heavy / short-line narration: ~108–113 WPM
- balanced documentary narration: ~113–118 WPM
- expository narration: ~118–123 WPM
```

## 5.2 Estimation Formula

Estimated Duration Seconds ≈

```text
(Word Count / Estimated WPM) × 60
+ Explicit Pause Tags
+ Natural punctuation drift
```

Explicit pause tags:

```text
<#0.3#> = +0.3s
<#0.4#> = +0.4s
<#0.5#> = +0.5s
<#0.7#> = +0.7s
<#0.9#> = +0.9s
<#1.0#> = +1.0s
<#1.2#> = +1.2s
<#1.5#> = +1.5s
<#1.8#> = +1.8s
```

Natural punctuation drift is not exact.

Use a loose estimate.

Do not calculate line breaks aggressively.

## 5.3 Target Estimate Header

Each TTS beat header may include:

```text
Target estimate: ~XX–YYs
```

Example:

```text
## TTS_01_BEAT_01_OPENING_HOOK | Target estimate: ~55–65s | Speed: 0.90 | Audio: CHINA_EP00_TTS_01_opening_hook_v01.mp3
```

Do not rewrite narration only to hit target time unless the user asks.

After rendering, the real audio length replaces the estimate.

---

# 6. CLEAN TTS TEXT RULES

When creating a TTS-ready file, use only narration text from `01_SCRIPT.md`.

Remove:

```text
BEAT headers
TIME TARGET
PURPOSE
VISUAL INTENT
VOICEOVER labels
VOICE BLOCK labels
markdown notes
production notes
visual notes
prompt instructions
edit notes
```

Keep:

```text
spoken narration
short lines
sentence punctuation
controlled silence
clean spoken rhythm
```

Do not rewrite narration unless the user explicitly asks.

Do not add new narration.

Do not create Visual Map, Veo prompts, or Edit Plan inside a TTS file.

---

# 7. PAUSE AND PACING RULES

MiniMax Text-to-Speech responds to:

```text
sentence punctuation
ellipsis ...
explicit pause tags like <#0.7#>
```

Line breaks may help readability, but they are not reliable as timing control.

MiniMax may remove blank lines when pasted.

Therefore:

```text
Do not depend on blank lines for pause timing.
Use explicit pause tags for long or important pauses.
```

## 7.1 Pause Hierarchy

Approximate behavior for:

```text
Voice: English_Trustworth_Man
Speed: 0.90
Pitch: 0
Volume: 1.0
```

```text
Period .
= normal sentence pause, often ~0.25–0.45s

Single line break
= readability separation, timing not reliable

Blank line
= not reliable because MiniMax may remove it

Ellipsis ...
= suspended / trailing pause, often ~0.5–0.9s but not exact

<#0.3#> to <#0.5#>
= short controlled pause

<#0.7#>
= transition between related ideas

<#0.9#>
= major idea pause

<#1.0#>
= thesis line or strong turn

<#1.2#>
= major beat ending

<#1.5#>
= rare major silence after a central thesis, major reveal, or visual absorption moment

<#1.8#>
= very rare end-of-section or closing-contract silence
```

## 7.2 Pause Tag Discipline

Do not place pause tags after every line.

Do not place pause tags after every sentence.

Use pause tags mainly:

```text
after a strong thesis line
before a major shift
at the end of a section
when a line must land with extra weight
when MiniMax natural punctuation is not enough
```

Default rhythm:

```text
Use punctuation first.
Use explicit tags for controlled pauses.
Do not rely on blank lines.
```

## 7.3 Structural Silence Rule

Use structural silence for thesis-heavy, dark structural, or mechanism-driven narration.

Structural silence is not decoration.

It is used when:

```text
the viewer needs time to understand a mechanism
the visual needs time to prove the sentence
the next line would lose force if spoken too quickly
the episode moves from one layer of power to another
```

Use longer pauses after:

```text
core thesis lines
dark structural reversals
“not X, but Y” turns
lines that reveal who benefits
lines that connect control to extraction
lines that expose absorption, conversion, or reproduction of power
beat-ending pressure lines
closing contract lines
```

Use punctuation first.

Use:

```text
. for normal sentence landing
... for suspended turn, delayed reveal, cold pivot, or trailing thought
explicit pause tags when the silence must be intentional, longer, or structurally important
```

General long-form pause scale:

```text
<#0.3#>–<#0.5#>
= small pause inside one idea

<#0.7#>
= light conceptual turn or transition between related lines

<#0.9#>
= structural turn; viewer needs a moment to connect the mechanism

<#1.0#>–<#1.2#>
= thesis line, dark reversal, or major “not X, but Y” line

<#1.2#>–<#1.5#>
= beat-ending pressure line or visual absorption pause

<#1.5#>–<#1.8#>
= rare major silence after a central episode thesis, major reveal, or closing contract line
```

Use `<#1.5#>` and `<#1.8#>` sparingly.

Do not place long pauses after every short sentence.

For lists, do not pause heavily after every item.

Let the list move, then place the longer pause after the list lands.

Bad:

```text
Land became surplus.
<#1.2#>

Surplus became books.
<#1.2#>

Books became education.
<#1.2#>
```

Better:

```text
Land became surplus.

Surplus became books.

Books became education.

Education became office.
<#0.9#>

Office became prestige.

Prestige became marriage.

Marriage became network.
<#1.2#>
```

Core principle:

```text
Do not lengthen narration only by adding more words.

Lengthen it by giving important ideas enough silence to become visible.
```

```text
Voice delivers the blade.
Pause lets the cut open.
Visual lets the viewer see it.
```

## 7.4 Practical Pause Rule for Shorts

For short-form narration:

```text
Pause under 0.5s:
use punctuation or <#0.25#> to <#0.45#>

Pause 0.5–0.8s:
use <#0.5#> to <#0.8#>

Pause above 0.8s:
use <#0.8#>, <#0.9#>, <#1.0#>, or <#1.2#>
```

For lists, reduce pauses.

Example:

```text
Landowners.
Clans.
Scholars.
Officials.
Merchants.
```

Do not add `<#0.4#>` after every single list item unless the slow listing effect is intentional.

---

# 8. ELLIPSIS RULE

Use ellipsis:

```text
...
```

only for:

```text
suspended turn
delayed reveal
cold narrative pivot
trailing thought
```

Example:

```text
The outsider breaks the gate...
<#0.7#>
only to lock it from the inside.
```

Ellipsis creates tone, not precise timing.

If the pause length matters, pair ellipsis with an explicit tag.

Do not overuse ellipsis.

Too many ellipses can make narration feel melodramatic or trailer-like.

---

# 9. OUTPUT FORMAT

Use one global settings block at the top.

```text
## GLOBAL MINIMAX SETTINGS

Mode: Text-to-Speech
Voice: English_Trustworth_Man
Pitch: 0
Volume: 1.0

Speed is set per beat.
Do not paste this settings block into the MiniMax narration box.
```

Do not repeat Voice / Pitch / Volume inside every beat.

Each beat header must include:

```text
TTS_##_BEAT_##_NAME | Target estimate: ~XX–YYs | Speed: X.XX | Audio: filename.mp3
```

Under each beat header, include only clean narration.

The user should copy only the narration text into MiniMax, not the settings block or beat header.

Do not use `SEGMENT` terminology for TTS outputs.

Use:

```text
TTS
BEAT
```

---

# 10. SHORT-FORM TTS FORMAT

For short videos, use:

```text
# SHORT_##_TTS_CLEAN

## GLOBAL MINIMAX SETTINGS

Mode: Text-to-Speech
Voice: English_Trustworth_Man
Speed: 0.90
Pitch: 0
Volume: 1.0

Do not paste this settings block into the MiniMax narration box.

---

## TTS_SHORT_01 | Target estimate: ~60–75s | Audio: SHORT_##_TTS_01_v01.mp3

[narration only]
```

Short-form TTS may remain one file if the narration is under 90 seconds.

If revision becomes difficult, split into:

```text
TTS_SHORT_01A
TTS_SHORT_01B
TTS_SHORT_01C
```

---

# 11. AUDIO NAMING

Use clear exported audio filenames.

For China EP00:

```text
CHINA_EP00_TTS_01_opening_hook_v01.mp3
CHINA_EP00_TTS_02_real_question_v01.mp3
CHINA_EP00_TTS_03_throne_v01.mp3
CHINA_EP00_TTS_04_elite_ecosystem_v01.mp3
CHINA_EP00_TTS_05_converts_power_v01.mp3
CHINA_EP00_TTS_06_disruptor_v01.mp3
CHINA_EP00_TTS_07_absorption_v01.mp3
CHINA_EP00_TTS_08A_operating_system_v01.mp3
CHINA_EP00_TTS_08B_moral_language_v01.mp3
CHINA_EP00_TTS_09_price_of_order_v01.mp3
```

For shorts:

```text
SHORT_01_TTS_main_v01.mp3
SHORT_01_TTS_main_speed_x_1_07_v01.mp3
```

If a voice section is regenerated, increment version:

```text
_v01
_v02
_v03
```

Do not overwrite old audio until the new version is approved.

---

# 12. TESTING RULE

Before rendering all long-form voice sections, test at least two sections:

```text
TTS_01
TTS_08B
```

Reason:

```text
TTS_01 tests hook, tone, pacing, and first impression.
TTS_08B tests complex abstract material and moral-language clarity.
```

If both pass, continue rendering the remaining sections.

For shorts, render one full test first.

Then check:

```text
total duration
pause length
list pacing
thesis line impact
whether CapCut 1.05x–1.08x speed-up would help
```

---

# 13. CAPCUT ASSEMBLY NOTE

When assembling beat-based voice files in CapCut:

```text
Place audio files in order.
Keep transitions between beat files natural.
Use 0.3–0.8 seconds of silence between beats if needed.
Do not create obvious audio gaps unless the beat needs a pause.
Normalize volume lightly if needed.
Do not change voice character per beat.
```

Voice is the timeline spine.

Visuals and music must follow voice timing.

If using CapCut speed adjustment:

```text
1.05x–1.08x = safe light tightening
1.10x = upper caution zone
above 1.10x = usually too fast for this channel
```

---

# 14. FINAL TTS PRINCIPLE

The channel voice should feel:

```text
controlled
trustworthy
restrained
analytical
dark but not theatrical
serious but not robotic
```

The voice should not feel:

```text
news anchor hype
movie trailer voice
emotional sermon
academic lecture
AI monotone
```

Core principle:

```text
Let the sentence land.
Do not overperform it.
```
