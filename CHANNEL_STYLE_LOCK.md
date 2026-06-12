# CHANNEL_STYLE_LOCK.md

## STATUS

ACTIVE — CHANNEL LEVEL

---

## FILE ROLE

This file defines the permanent tonal, narrative, visual-taste, and pacing identity of **Throne In Shadow**.

It answers:

```text
What should the channel feel like?
```

It applies to every session and every episode unless the user explicitly overrides it for a specific task.

This file controls:

```text
tone
mood
narration style
visual taste
pacing feel
aesthetic guardrails
channel identity
viewer experience
```

It does **not** control:

```text
projectbeat JSON structure
prompt_raw templates
Veo prompt syntax
clip duration rules
prompt families
camera/lens prompt templates
visual_constraints field rules
period-specific costumes
period-specific props
period-specific architecture
tool / asset-operator workflow
```

For current production workflow, use:

```text
CHANNEL_WORKFLOW_CONTROL.md
```

For prompt_raw and Veo 3 prompt mechanics, use:

```text
CHANNEL_VEO_PROMPT_RULES.md
```

For period accuracy, use:

```text
ERA_LOCK.md
```

---

## AUTHORITY

This file follows:

```text
CHANNEL_IDENTITY.md
```

This file is followed by:

```text
CHANNEL_WORKFLOW_CONTROL.md
CHANNEL_VEO_PROMPT_RULES.md
SESSION_CONTROL.md
EPISODE FILES
```

If this file conflicts with `CHANNEL_VEO_PROMPT_RULES.md` about technical prompt construction, `CHANNEL_VEO_PROMPT_RULES.md` wins for Veo prompt construction.

If this file conflicts with an ERA LOCK about historical period details, the ERA LOCK wins for costumes, props, architecture, weapons, furniture, and material culture.

---

# 1. CHANNEL STYLE IDENTITY

The channel style is:

```text
cinematic historical documentary
dark atmospheric realism
restrained analytical narration
high-contrast visual language
material and institutional logic
show, don’t tell
voice asks, visual proves
```

The channel should feel like a cold political autopsy of history.

Not a trailer.

Not a classroom lecture.

Not a fantasy epic.

Not nationalist mythology.

Not moral sermonizing.

---

# 2. CORE STYLE PRINCIPLE

```text
Voice = frames the thought.
Visual = proves the thought.
Edit = holds the pressure.
```

Narration should not explain everything.

Visuals must carry part of the information.

Every abstract idea should be translated into something concrete.

The channel prefers evidence-shaped imagery over decorative imagery.

But evidence does not always mean documents.

Use direct visible events when they communicate the idea more clearly than paperwork.

Examples:

```text
tax → grain sacks, measuring baskets, villagers submitting grain, granary storage, counting hands
law → clerks reading aloud, seals pressed into clay, officials at low desks, bodies waiting at thresholds
centralization → roads, census registration, warehouses, county offices, messengers carrying orders
elite reproduction → marriage ritual, children studying, office seating, land boundaries, ancestral hall entry
memory → ancestral halls, tablets, archive rooms, erased names as blurred record texture, bodies outside belonging thresholds
order → queues, measurements, synchronized labor, grain stores, roads, gates, guarded thresholds
dynastic change → burning palace, abandoned throne, fallen ceremonial robe, old banner lowered, new banner raised
```

Avoid using archives, documents, ledgers, books, seals, or record shelves as the default visual metaphor for every historical idea.

Documents are powerful when the subject is records, law, bureaucracy, archives, memory, genealogy, or official history.

For other ideas, use the clearest physical event first.

---

# 3. NARRATION STYLE

Narration should be:

```text
restrained
analytical
cold but not lifeless
curious rather than preachy
precise rather than emotional
haunting without melodrama
interest-aware
structurally suspicious
```

Narration should avoid:

```text
hype
shouting
trailer language
over-explaining
academic stiffness
sentimental character worship
modern political lecturing
moral grandstanding
```

Preferred narration behavior:

```text
ask the deeper question
frame the structure
expose the mechanism
ask who benefits
ask who pays
leave space for visual proof
end beats with pressure
```

Bad direction:

```text
This emperor was evil and cruel.
```

Better direction:

```text
The throne did not need to hate local power.
It only needed to make local power measurable.
```

---

# 4. WESTERN AUDIENCE STYLE

The channel often explains non-Western systems to Western viewers.

Use careful analogies when needed.

Analogies must clarify without flattening differences.

Good:

```text
something like
similar in one crucial sense
not identical
a careful analogy
```

Bad:

```text
X is exactly the same as Y
```

Do not assume the viewer already understands local institutions, rituals, elite titles, or moral systems.

But do not over-explain in narration.

Let the script set the question and let visuals carry concrete proof.

---

# 5. VISUAL TASTE

The channel visual world should feel:

```text
dark
restrained
material
observational
archival
institutional
politically quiet
historically grounded
Western documentary reconstruction
```

Prefer:

```text
matte surfaces
aged wood
worn stone
dust
mud
grain
cloth
roads
rooms
thresholds
records when meaningful
hands doing work
bodies waiting
objects under pressure
```

Avoid:

```text
fantasy glow
wuxia action
magical effects
mythic palace spectacle
glossy costume drama
clean studio beauty lighting
heroic ruler worship
national glory montage
modern music-video color grading
over-saturated palace colors
```

The image should feel like history under pressure, not history as decoration.

---

# 6. STYLE MODES ALLOWED BY THE CHANNEL

The channel can use more than one visual mode.

The two main approved modes are:

```text
REALISTIC DOCUMENTARY RECONSTRUCTION
ROUGH HISTORICAL EXPLAINER ANIMATION
```

## 6.1 Realistic Documentary Reconstruction

Use for:

```text
courts
offices
roads
tax collection
land boundaries
villages
archives
schools
ritual halls
administrative rooms
```

It should feel like:

```text
gritty Western prestige historical documentary
desaturated
matte
low micro-contrast
soft lens rendering
imperfect focus
heavy film grain
underlit
non-glossy
physically grounded
```

## 6.2 Rough Historical Explainer Animation

Use for abstract mechanisms that are difficult to show through realistic footage.

Examples:

```text
extraction logic
conversion loops
elite ecosystem diagrams
moral gatekeeping
absorption loops
parallel cause/effect mechanisms
```

It should feel like:

```text
rough ink sketch
aged parchment
carbon-black linework
dark sepia wash
flat 2D perspective
limited jerky motion
dark documentary humor
archival explainer insert
```

It must not feel like:

```text
anime
cute cartoon
modern corporate infographic
glossy vector animation
3D render
meme comedy
fantasy monster imagery
```

Important distinction:

```text
shot_type is layout.
style_block is visual mode.
```

`SINGLE_SHOT` and `SPLIT_SCREEN_MULTIPANEL` are layout decisions controlled by `CHANNEL_VEO_PROMPT_RULES.md`.

They are not style modes.

---

# 7. PACING FEEL

The channel pacing is:

```text
slow pressure
controlled reveal
measured cuts
visual breathing room
no dopamine editing
```

The edit should not chase constant excitement.

It should build tension through:

```text
contrast
silence
empty rooms
small gestures
symbolic objects
direct visible events
repetition with progression
```

Use documents and archives when meaningful, but do not let every pressure point become paperwork.

Allowed rhythm:

```text
quiet setup
structural turn
visual proof
short pause
next pressure point
```

Avoid:

```text
rapid trailer montage
constant impact cuts
overuse of dramatic music drops
excessive zooms
fast combat choreography
```

---

# 8. SHOW, DON’T TELL STYLE

Core rule:

```text
Voice opens the question.
Visual answers with evidence.
```

The voice may say:

```text
The throne wanted direct command.
```

The visual should show:

```text
census registration
grain taxes
county offices
roads
official seals
villagers being measured, counted, or registered
```

The voice may say:

```text
Elite power survived by changing form.
```

The visual should show:

```text
land boundary
stored grain
child studying indoors
office seat
marriage ritual
ancestral hall entry
elite seating
```

The voice may say:

```text
Dynasties rose and fell.
```

The visual should show:

```text
burning palace
abandoned throne
fallen ceremonial robe
old banner lowered
new banner raised
palace gate changing control
```

Do not force narration to explain every historical mechanism.

Let visuals carry the concrete proof.

## 8.1 Narration Must Not Replace Visual Proof

Narration must write enough meaning for the viewer to understand the structural idea, but it must not say what the visual can prove more strongly.

Core rule:

```text
Write enough meaning.
Do not narrate over visual evidence.
```

Voice should frame the mechanism.

Visuals should prove the mechanism through:

```text
visible action
institutional space
body position
threshold
material burden
ritual cue
social distance
object movement
status change
```

Do not use narration to describe every visible event in the scene.

A narration line should usually do at least one of these jobs:

```text
ask the deeper question
name the structural turn
compress the mechanism
create pressure before the visual proof
explain what the image alone cannot explain
connect one visual proof to the next
```

If a narration line only describes what the viewer can clearly see, cut it, compress it, or turn it into a sharper structural frame.

Weak narration:

```text
A clerk delayed the record.
A messenger waited at the gate.
A landholder hid the field.
Villagers paid more.
```

Stronger narration:

```text
Every step gave someone a chance to touch it.

No one needed to rebel.

The road only had to slow.

That was enough.
```

Then the visual layer can prove the idea through:

```text
clerk pauses
waiting bodies
hidden field boundaries
grain counted again
villagers carrying the burden
a gate that stays half-open
a desk between society and authority
```

Do not cut narration only to make the video shorter.

Cut narration when the image can carry the proof better than the voice.

Core test:

```text
If the viewer can understand the visible event without the narrator naming it,
the narrator should name the deeper mechanism instead.
```

## 8.2 Script-Level Show-Don't-Tell Check

When drafting or revising narration, check every beat before approval:

```text
Which lines frame the thought?
Which lines are only describing future visuals?
Which visual proof can be moved out of voice and into storyboard planning?
Which thesis lines must stay because visuals cannot carry them alone?
```

The preferred script behavior is:

```text
Narration opens space for visual proof.
It does not close that space by explaining everything first.
```

A short narration line may require several visual states later.

A visual sequence may prove more than the narration says.

This is intentional.

Core line:

```text
Voice should leave work for the image.
```

---

# 9. WHAT TO AVOID

Avoid:

```text
fantasy aesthetics
wuxia tropes
glowing dragons
magical effects
mythic palace glow
heroic emperor worship
battle spectacle for its own sake
trailer pacing
sensational conspiracy framing
modern nationalist montage
simplistic villain framing
sentimental character bias
moral sermonizing
generic paperwork montage
```

The channel studies power.

It does not worship power.

It does not reduce power to secret cabals.

It does not turn history into cosplay.

---

# 10. DOCUMENTARY ETHIC

The channel should interpret history through:

```text
power mechanics
class conflict
elite reproduction
bureaucracy
state formation
material constraints
institutional incentives
ritual as legitimacy
moral language as power
memory and archive control
the price of order
```

But the channel must avoid unsupported certainty.

Strong interpretation is allowed.

Conspiracy framing is not.

Preferred language:

```text
structure
incentive
mechanism
condition
reproduction
adaptation
negotiation
mediation
legitimacy
```

Use carefully:

```text
parasite
shadow state
immortal
puppet
secret control
```

These words can become cartoonish if overused.

---

# 11. RELATION TO PROJECTBEAT AND VEO PROMPTING

This file defines the channel’s visual taste.

It should influence `prompt_raw.style_block` through mood and style only.

It should not be used as the technical prompt-format guide.

Technical prompt_raw and Veo 3 prompt rules are controlled by:

```text
CHANNEL_VEO_PROMPT_RULES.md
```

Current workflow rules are controlled by:

```text
CHANNEL_WORKFLOW_CONTROL.md
```

In practice:

```text
CHANNEL_STYLE_LOCK.md = what the image should feel like
CHANNEL_VEO_PROMPT_RULES.md = how prompt_raw and Veo prompts should be structured
CHANNEL_WORKFLOW_CONTROL.md = how the production pipeline works
ERA_LOCK.md = what period details must be correct
SESSION_CONTROL.md = civilization-specific visual and thesis guardrails
```

---

# 12. FINAL STYLE LINE

The channel should feel like this:

```text
history stripped of romance,
power stripped of costume,
order shown through the events, objects, rooms, roads, thresholds, records, and bodies that made it real.
```
