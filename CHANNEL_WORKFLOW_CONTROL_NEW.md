# CHANNEL_WORKFLOW_CONTROL_NEW.md

# STATUS
ACTIVE — CHANNEL LEVEL — STORYBOARD-PROMPT PROJECTBEAT WORKFLOW

# FILE ROLE
This file defines the active channel-level production workflow.

It controls:
```text
room responsibilities
file handoff order
workflow boundaries
storyboard-first projectbeat flow
Phase A / Phase B approval gates
assistant output scope
human-readable production field rules
viewer_sees quality rules
prompt_raw production boundary
```

It does not control:
```text
session thesis
civilization-specific guardrails
historical period visuals
prompt_raw field mechanics
external tool behavior after prompt_raw
TTS voice settings
CapCut edit execution
final timeline trimming
```

# AUTHORITY
This file is the workflow authority for process order.

It defines:
```text
what comes first
what each room produces
where the assistant should stop
how script becomes storyboard shots
how storyboard shots become projectbeat JSON
how viewer_sees must be normalized before prompt_raw
```

It must not override:
```text
CHANNEL_VEO_PROMPT_RULES_NEW.md
CHINA_SESSION_THESIS.md
CHINA_SESSION_CONTROL.md
CHINA_ERA_LOCK_NEW.md
CHANNEL_TTS_RULES_CLEAN.md
```

# USED BY WHICH ROOM
```text
PROJECT_ARCHITECT_ROOM
CHINA_EP00_SCRIPT_ROOM
PROJECT_STORYBOARD_PROMPT_ROOM
future script rooms
future storyboard / projectbeat / prompt rooms
```

# INPUT
Primary workflow inputs for storyboard-prompt work:
```text
00_BRIEF.md
01_SCRIPT.md
active session rules
active era lock when needed
EP00 default visual-era anchor from CHINA_ERA_LOCK_NEW.md when EP00 is active
CHANNEL_VEO_PROMPT_RULES_NEW.md
```

Optional later-layer inputs:
```text
02_TTS_CLEAN_BY_BEAT.md
beat voice audio (.mp3 / .wav)
draft voice alignment / draft SRT
```

These optional inputs may support later TTS or edit work, but they do not direct initial storyboard shot splitting.

# OUTPUT
Primary structured production output:
```text
projectbeat JSON with prompt_raw
```

Typical beat output:
```text
CHINA_EP##_BEAT_##_projectbeat.json
```

# MUST NOT OVERRIDE
This file must not redefine:
```text
prompt_raw schema
shot_type templates
session thesis
session historical claims
era-specific costume / architecture / props
external tool-specific prompt formats
MiniMax TTS settings
CapCut edit rules
```

# RELATED FILES
```text
CHANNEL_VEO_PROMPT_RULES_NEW.md
CHANNEL_TTS_RULES_CLEAN.md
CHINA_SESSION_THESIS.md
CHINA_SESSION_CONTROL.md
CHINA_ERA_LOCK_NEW.md
00_BRIEF.md
01_SCRIPT.md
02_TTS_CLEAN_BY_BEAT.md
```

---

# 1. CORE WORKFLOW PRINCIPLE

The channel uses a storyboard-first projectbeat workflow.

Core path for visual production planning:
```text
brief + script
→ visual soul check
→ beat visual flow
→ user approval
→ visual grouping
→ storyboard draft
→ timing budget check
→ optimization suggestions
→ user approval
→ optimized shot plan
→ prompt production
→ projectbeat JSON with prompt_raw
→ user-selected downstream workflow
```

Core rules:
```text
Visual groups direct shot planning.
Storyboard shots direct prompt production.
SRT does not direct visual planning.
Narration cues explain why a shot exists; they do not decide shot detail by themselves.
viewer_sees must be concrete enough to guide a human before prompt_raw exists.
```

The assistant's default visual-planning endpoint remains:
```text
projectbeat JSON with prompt_raw
```

The assistant does not automatically continue into TTS rendering, downstream tool execution, or edit execution unless the user explicitly asks for that layer.

---

# 2. WORKFLOW AUTHORITY ORDER

Use this authority order when multiple files are active.

```text
1. CHANNEL_WORKFLOW_CONTROL_NEW.md
   = controls workflow order, room responsibility, output boundary, storyboard-to-projectbeat process

2. CHANNEL_VEO_PROMPT_RULES_NEW.md
   = controls prompt_raw schema, shot_type logic, field discipline, visual matrix composition, and QC

3. CHINA_SESSION_THESIS.md
   = controls the China structural thesis and argument

4. CHINA_SESSION_CONTROL.md
   = controls China session guardrails, production discipline, and anti-drift rules

5. CHINA_ERA_LOCK_NEW.md
   = controls historical period visuals, era / tier / location overlays, and the EP00 default visual-era anchor

6. Episode production files
   = control the specific episode, beat, and shot task at hand
```

China episodes use one shared era-lock system by default:
```text
CHINA_ERA_LOCK_NEW.md
```

For EP00, if the user does not assign a stricter era, use the EP00 default visual-era anchor defined inside `CHINA_ERA_LOCK_NEW.md`.

Do not route EP00 to a separate EP00 visual lock file by default.

## 2.1 EP00 DEFAULT ERA ROUTING

EP00 does not use a separate EP00 visual lock file in this workflow.

When EP00 is active and the user does not assign a stricter era, route EP00 visual-era anchoring through:
```text
CHINA_ERA_LOCK_NEW.md → EP00 Default Visual-Era Anchor → HAN DYNASTY profile
```

This workflow rule only decides where to get the visual-era anchor.
It must not define EP00 thesis, brief, script, beat logic, shot meaning, or prompt_raw schema.

EP00's default Han-style anchor means:
```text
EP00 uses Han-style early imperial China as its default visual language.
EP00 is not narratively about the Han dynasty unless the script / brief explicitly says so.
```

If the user explicitly assigns another era to an EP00 shot or section, use that selected era profile from `CHINA_ERA_LOCK_NEW.md` instead.

---

# 3. ROLE LOCK

## 3.1 Assistant Role

The assistant acts as:
```text
Creative Systems Director + Workflow Architect + Script/Visual Planner
```

The assistant must:
```text
protect the channel identity
protect the active session thesis
keep the workflow solo-creator friendly
produce structured outputs that are immediately usable
translate approved script material into storyboard planning
create projectbeat JSON from optimized storyboard shots
write prompt_raw as the assistant-side visual planning output
stop at the correct workflow boundary
```

The assistant must not:
```text
expand scope beyond the requested production layer
create extra production files without a clear need
invent external tool workflow details by default
replace session or era authority files
split shots from SRT as the default method
use audio timing as the first visual planning authority
force prompt_raw to carry meaning that viewer_sees failed to explain
```

## 3.2 User Role

The user acts as:
```text
Producer / Final Director
```

The user controls:
```text
approval
thesis direction
tool operation
audio generation
downstream prompt conversion
asset selection
editing
final export
```

---

# 4. ACTIVE PRODUCTION FLOW

The active visual planning flow is:
```text
00_BRIEF.md
→ 01_SCRIPT.md
→ PROJECT_STORYBOARD_PROMPT_ROOM
→ projectbeat JSON with prompt_raw
→ downstream tool workflow chosen by the user
```

Inside `PROJECT_STORYBOARD_PROMPT_ROOM`, the flow is:

```text
PHASE A — STORYBOARD PLANNING
1. visual_soul_check
2. beat_visual_flow
3. USER APPROVAL GATE — beat_visual_flow
4. visual_grouping
5. storyboard_draft — expanded SINGLE_SHOT only
6. timing_budget_check
7. optimization_suggestions
8. USER APPROVAL GATE — optimization direction
9. optimized_shot_plan

PHASE B — PROMPT PRODUCTION
10. selected optimized shot
11. narration_cue
12. visual_goal
13. viewer_sees — refined, era-normalized, human-usable
14. layout / shot_type mapping
15. QA Anchor Context
16. prompt_raw
17. GKStudio / projectbeat JSON
```

This file governs the assistant only up to:
```text
projectbeat JSON with prompt_raw
```

Anything after that belongs to the user's selected downstream workflow unless the user explicitly asks the assistant to help on that later layer.

---

# 5. PROJECTBEAT-FIRST RULE

The channel's standard visual production container is:
```text
projectbeat JSON
```

A projectbeat file is the planning bridge between:
```text
script / storyboard structure
and
asset / generation / editing execution
```

A projectbeat file should contain planning fields such as:
```text
beat_goal
beat_visual_flow
beat_operator_focus
storyboard_draft when requested
optimized_shot_plan when requested
shots
group
shot
narration_cue
visual_idea
layout
min_visual_time
visual_goal
viewer_sees
prompt_raw
operator_notes when needed
```

Do not add internal normalization scratch fields to the final JSON unless the user explicitly requests debug output.

Do not include:
```text
shot_visual_anchor_spec
viewer_sees_draft
internal QA notes
hidden reasoning
```
in final GKStudio / projectbeat JSON by default.

Core rule:
```text
Storyboard plans the shots.
Projectbeat carries the usable shot cards.
viewer_sees tells the human what must be seen.
prompt_raw supplies technical prompt material.
```

---

# 6. PROJECT_STORYBOARD_PROMPT_ROOM INTERNAL ORDER

When a `PROJECT_STORYBOARD_PROMPT_ROOM` creates or edits a beat, it must work in this order.

```text
PHASE A — STORYBOARD PLANNING
1. visual_soul_check
2. beat_visual_flow
3. user approval gate — beat_visual_flow
4. visual_grouping
5. storyboard_draft
6. timing_budget_check
7. optimization_suggestions
8. user approval gate — optimization direction
9. optimized_shot_plan only after user approval

PHASE B — PROMPT PRODUCTION
10. selected optimized shot
11. narration_cue
12. visual_goal
13. viewer_sees
14. layout / shot_type mapping
15. QA Anchor Context
16. prompt_raw
17. GKStudio / projectbeat JSON
```

This order is mandatory.

Do not start from:
```text
prompt_raw
style
tags
generic Veo prompt
SRT
audio alignment
```

Core rule:
```text
First expand.
Then budget.
Then suggest compression.
Then user approves.
Then prompt.
```

---

## 6.1 PHASE A — Visual Soul Check

`visual_soul_check` asks whether the beat can live visually before prompt production begins.

It should answer:
```text
Beat này nhìn như thế nào để người xem tự hiểu ý chính?
Beat có đang chỉ kể bằng voice không?
Có visual turn, visual proof, hoặc direct visible event không?
```

Output should be short and practical:
```text
PASS / CHECK / FAIL
reason
required visual correction when needed
```

Core rule:
```text
Do not create prompt_raw for a beat whose visual soul is unclear.
```

---

## 6.2 PHASE A — beat_visual_flow

`beat_visual_flow` explains the visual movement of the whole beat.

It is the first major output for user review in Phase A.

It should answer:
```text
Beat bắt đầu bằng hình ảnh gì?
Nó chuyển qua những lớp nào?
Nó bẻ điểm nhìn ở đâu?
Cuối beat người xem thấy rõ điều gì?
Visual mechanism nào chứng minh ý của narration mà không cần nói thẳng?
```

Good:
```text
Beat bắt đầu với một bó lệnh nhỏ, sạch, chính thức nằm trên bàn công vụ. Khi bó lệnh rời khỏi bàn, nó không còn là command thuần nữa; nó đi vào chuỗi tay người, ngưỡng cửa, bàn đo, kho thóc và người ghi nhận. Ở giữa beat, procedure làm cho extraction trông hợp lệ: giữ lại, đo lại, ghi lại, rồi trả một phần thông tin về trung tâm. Beat bẻ ở khoảnh khắc thóc bị tách thành hai hướng: phần official quay về trên giấy tờ, phần difference nằm lại ở tầng địa phương.
```

Weak:
```text
Lệnh → đường → thóc → hệ thống.
```

Core rule:
```text
beat_visual_flow = visual causality chain + thesis pressure across the beat.
```

Approval rule:
```text
After outputting beat_visual_flow, stop and wait for user approval before visual_grouping and storyboard_draft unless the user explicitly asks to continue.
```

---

## 6.3 PHASE A — Visual Grouping

`visual_grouping` groups the beat into narration-linked visual/edit containers.

A Group is a planning container that connects:
```text
a narration chunk
→ a local cluster of visual ideas
→ a later edit boundary
→ a default merge boundary for optimization
```

It must not mechanically follow SRT segments or sentence breaks.

It must not introduce extra workflow layers such as:
```text
segment
scene
section
sequence unit
```

The workflow stays:
```text
Beat → Group → Shot
```

A Group has meaning for visual planning, but it is not a production shot by itself.

A Group:
```text
gives narration a visual/edit anchor
contains the shots that support the same local narration / idea movement
helps the user cut and assemble the beat later
defines the default boundary for merging shots during optimization
```

A Group does not mean:
```text
all shots inside the Group must share one location
all shots inside the Group must share one subject
all shots inside the Group must share one action
the Group itself can produce prompt_raw
the Group replaces shot-level Visual idea / visual_goal / viewer_sees
```

It should answer:
```text
Cụm narration / ý chuyển động nào nên nằm chung một Group?
Group này cần cụm visual shots nào để nâng đỡ ý đó?
Ý nào nên đứng riêng thành Group khác?
Ý nào quá dày và cần bung shot ở storyboard draft?
```

Core rule:
```text
Visual Grouping creates narration-linked visual/edit containers.
It does not finalize production shots yet.
It does not create prompt_raw.
```

---

## 6.4 PHASE A — Storyboard Draft

`storyboard_draft` expands each visual group into the smallest meaningful `SINGLE_SHOT` units first.

Storyboard Draft is not an optimization stage.

Storyboard Draft is not allowed to compress visual ideas.

The draft table must use this field order:
```text
Group | Shot | narration_cue | Visual idea | Layout | Min visual time
```

Default and only allowed layout at this phase:
```text
SINGLE_SHOT
```

In Storyboard Draft, do not use:
```text
SPLIT_SCREEN_2
SPLIT_SCREEN_3
SINGLE_SHOT_TRANSITION
MONTAGE_EDIT
MONTAGE_END
```

Do not merge several visual ideas into one row.

Do not combine several narration turns into one compressed shot.

Do not hide visual density by using montage language.

Purpose:
```text
make the visual density visible
show what the beat wants to include before compression
reveal over-budget groups
let the user judge narration length beside each visual idea
```

Core rule:
```text
Do not optimize too early.
First show the expanded single-shot version.
```

---

## 6.5 PHASE A — Min Visual Time

`min_visual_time` is the minimum time a shot needs on screen for the viewer to read the image.

It is estimated at shot level, not group level.

It is not final timecode.

It is not a Veo generation duration.

Veo generation should be treated as an 8-second source clip unless the downstream tool explicitly supports another duration.

If `min_visual_time = 3s`, it means:
```text
Generate the shot as a normal Veo source clip.
Use or trim roughly 3 readable seconds in edit.
```

It does not mean:
```text
Write prompt_raw as a 3-second video.
Ask Veo to generate exactly 3 seconds.
Cram several actions into one prompt to fit timing.
```

It should consider:
```text
recognition time
meaning read time
action / transition time
emotional hold
foreground / midground / background readability
```

Practical ranges:
```text
simple single symbol: 2.5–3.5s
single place + person + action: 4–5.5s
ritual or social action: 5–7s
foreground / midground / background relationship: 6–8s
visual reveal or perspective break: 6–8s
```

Core rule:
```text
Min visual time = edit/readability timing intent, not Veo clip duration.
```

---

## 6.6 PHASE A — Timing Budget Check

After `storyboard_draft`, calculate:
```text
Total Min Visual Time = sum(all shot min_visual_time)
```

Compare it with:
```text
Beat Duration Target
```

Before TTS or edit, `Beat Duration Target` may be estimated from:
```text
script length
beat function
expected pacing
user-provided target duration
```

Status rules:
```text
GOOD = total min visual time fits the beat target with breathing room
OVER BUDGET = total min visual time exceeds the target by more than 15–20%
UNDERUSED = total min visual time is far below target and the beat may feel thin
```

Core rule:
```text
Timing Budget Check tests whether the visual plan can survive inside the beat.
It does not create final timing.
It does not change prompt_raw duration.
```

---

## 6.7 PHASE A — Optimization Suggestions

`optimization_suggestions` happen after the Timing Budget Check.

Optimization Suggestions are suggestions only.

The assistant does not finalize compression.

The user is the final decision maker.

The assistant may suggest:
```text
keep all storyboard units as separate SINGLE_SHOT
flag optional visual ideas for user review
move dense visual ideas to another beat
reduce repeated shots that prove the same visual function
merge only visually compatible shots within the same Group
convert user-approved simultaneous comparison to SPLIT_SCREEN_2 or SPLIT_SCREEN_3
use SINGLE_SHOT_TRANSITION only if the user approves one clear before/after visual turn
mark a cluster as manual edit note using MONTAGE_EDIT or MONTAGE_END when it is not a production prompt
```

The assistant must not suggest optimization that only makes timing look correct while breaking Veo production reality.

Do not suggest:
```text
compress 4–5 actions into one Veo prompt
combine multiple locations into one SINGLE_SHOT
combine several time jumps into one prompt
make one prompt carry several unrelated visual mechanisms
use split-screen as a dumping ground for unrelated images
use transition when there is no single clear before/after turn
hide density behind vague montage language
```

Veo-safe optimization rule:
```text
A production shot should stay visually simple enough for one 8-second Veo source clip.
The edit creates rhythm.
The prompt creates one coherent visual unit.
```

Merge boundary rule:
```text
By default, merge only within the same Group.
Do not merge shots across different Groups as silent optimization.
A cross-Group merge changes the narration/edit boundary and must be presented as a restructuring proposal.
Only perform a cross-Group merge if the user explicitly approves that restructuring.
```

Do not output Optimized Shot Plan until the user approves an optimization direction.

Core rule:
```text
Optimization Suggestions expose possible choices.
User approval creates the Optimized Shot Plan.
```

---

## 6.8 PHASE A — Optimized Shot Plan

`optimized_shot_plan` is created only after the user chooses or approves an optimization direction.

It is the approved production shot plan before prompt writing.

It must use this field order:
```text
Group | Shot | narration_cue | Visual idea | Layout | Min visual time
```

This table is the direct source for prompt production.

Core rule:
```text
Each optimized production shot becomes one production shot entry.
```

---

## 6.9 Layout Values

Approved production layout values:
```text
SINGLE_SHOT
SPLIT_SCREEN_2
SPLIT_SCREEN_3
SINGLE_SHOT_TRANSITION
```

Non-production manual edit note values:
```text
MONTAGE_EDIT
MONTAGE_END
```

Meaning:
```text
SINGLE_SHOT = one concrete shot / one visual idea
SPLIT_SCREEN_2 = two simultaneous panels in one video, only after user approval
SPLIT_SCREEN_3 = three simultaneous panels in one video, only after user approval
SINGLE_SHOT_TRANSITION = one clear before/after visual turn, only after user approval
MONTAGE_EDIT = manual edit note for the user, not a production shot
MONTAGE_END = manual edit note for the user, not a production shot
```

Default production layout:
```text
SINGLE_SHOT
```

MONTAGE_EDIT and MONTAGE_END have no prompt_raw template.

They must not be used to replace production shots when Phase B needs prompt_raw.

If an Optimized Shot Plan is intended for Phase B prompt_raw generation, every row must use a production layout value.

Do not use transition-shot logic by default in storyboard planning.

If a visual idea requires a transition and the user has not approved `SINGLE_SHOT_TRANSITION`:
```text
split it into separate SINGLE_SHOT rows
let the edit handle the cut / match cut / crossfade / hold
```

Core rule:
```text
Veo creates shots.
The editor creates rhythm.
MONTAGE_EDIT only names a manual edit possibility; it does not create a Veo production shot.
```

---

# 7. PHASE B — PROMPT PRODUCTION ORDER

After `optimized_shot_plan` is approved or clearly selected, each optimized shot must be expanded in this order:

```text
Group
→ Shot
→ Visual idea
→ Layout
→ Min visual time
→ narration_cue
→ visual_goal
→ viewer_sees
→ layout / shot_type mapping
→ QA Anchor Context
→ prompt_raw
→ GKStudio / projectbeat JSON
```

This order preserves the storyboard decision and prevents prompt-first drift.

`Group`, `Shot`, and `Min visual time` are planning/edit metadata.

They do not drive prompt_raw content.

`viewer_sees` must be refined before prompt_raw, but do not output internal anchor scratch fields unless debug mode is explicitly requested.

---

## 7.1 narration_cue

`narration_cue` is the narration fragment the shot serves.

It should be short enough to make the voice reason clear.

It may be approximate before TTS and final edit.

It must not force shot splitting.

It must not be treated as the main visual detail authority.

Core rule:
```text
narration_cue = the voice reason this shot exists.
It is not the shot-splitting authority.
It is not enough to create prompt_raw by itself.
```

---

## 7.2 visual_goal

`visual_goal` is shot-level meaning.

It must explain the shot's purpose in simple Vietnamese.

It should answer:
```text
Shot này cần người xem hiểu điều gì?
Shot này phục vụ visual idea nào?
Shot này chứng minh phần nào của beat mechanism?
```

It should not describe every object in the frame.

It should not sound like a thesis slogan.

It should not sound like a prompt.

Good:
```text
Cho người xem thấy mệnh lệnh chỉ bắt đầu có lực khi rời khỏi bàn trung tâm và đi vào tuyến người xử lý ở địa phương.
```

Weak:
```text
Thể hiện quyền lực và bộ máy.
```

Core rule:
```text
visual_goal = why this shot exists and what meaning it proves.
```

---

## 7.3 viewer_sees

`viewer_sees` translates the shot meaning into a concrete clip description for the human operator.

It is the most important human-readable shot field.

It should answer:
```text
Cảnh ở đâu cụ thể?
Ai hoặc cái gì xuất hiện?
Họ đang làm gì?
Đồ vật chính là gì theo đúng bối cảnh / thời kỳ?
Không gian, ngưỡng cửa, vị trí cơ thể, khoảng cách, hoặc hierarchy nào làm ý nghĩa rõ?
Dấu hiệu hình ảnh nào giúp người xem hiểu đúng cơ chế?
```

`viewer_sees` must be detailed enough that a human can select, reject, or create a clip without reading `prompt_raw`.

Because this workflow uses show-don't-tell, `viewer_sees` must not be a translation of narration. It must be the visible proof of the shot meaning.

### 7.3A Internal normalization before viewer_sees

Before writing final `viewer_sees`, the assistant must internally normalize the shot into concrete visual anchors.

This is an internal scratch step only.

Do not output it by default.

Internally resolve:
```text
era-correct location
civilization / period-correct role or subject
era-correct object identity
physical action
spatial relation
meaning cue / mechanism cue
terms to avoid because they are generic, modern, or historically misleading
```

Use this internal normalization to replace vague terms.

Examples:
```text
administrative room → Qin commandery office / county administrative chamber / county yamen record room, depending on era and context
messenger → courier runner / administrative runner / mounted courier, depending on shot need
packet → cord-tied bamboo-slip order bundle / wooden-slip record bundle / sealed record container, depending on era and authority files
office → commandery office / county office / record room / tax receiving space, depending on location
road → dusty courier route outside the administrative gate, if that is the actual scene
```

Do not output:
```text
shot_visual_anchor_spec
viewer_sees_draft
internal anchor notes
```

Only output the final refined `viewer_sees`.

### 7.3B viewer_sees quality standard

Good viewer_sees:
```text
Một người đưa lệnh thời Tần bước qua ngưỡng cửa gỗ của phòng công vụ quận nha, mang bó thẻ tre buộc dây từ vùng tối bên trong ra con đường bụi bên ngoài. Phía sau người đó vẫn thấy bàn công vụ thấp và một văn lại ngồi trong bóng, khiến mệnh lệnh trông như vừa rời khỏi không gian kiểm soát để đi vào tuyến tay người.
```

Weak viewer_sees:
```text
Messenger cầm packet rời phòng hành chính.
```

Core rule:
```text
viewer_sees = what the human operator must actually see, already normalized into concrete period-appropriate visual language.
```

If a human cannot choose or create footage from `viewer_sees`, rewrite it before prompt_raw.

---

## 7.4 layout / shot_type mapping

Map the approved `layout` to the prompt_raw shot type.

Allowed production mappings:
```text
SINGLE_SHOT → SINGLE_SHOT
SPLIT_SCREEN_2 → SPLIT_SCREEN_MULTIPANEL with two panels
SPLIT_SCREEN_3 → SPLIT_SCREEN_MULTIPANEL with three panels
SINGLE_SHOT_TRANSITION → SINGLE_SHOT_TRANSITION
```

Manual edit notes:
```text
MONTAGE_EDIT → no prompt_raw
MONTAGE_END → no prompt_raw
```

Core rule:
```text
Only production layouts can produce prompt_raw.
```

---

## 7.5 QA Anchor Context

Before writing `prompt_raw` for each shot, run QA Anchor Context.

This is a mandatory check.

QA Anchor Context verifies that `prompt_raw.context` follows `CHANNEL_VEO_PROMPT_RULES_NEW.md` context rules.

For `SINGLE_SHOT`:
```text
context = the concrete scene setting
```

For `SINGLE_SHOT_TRANSITION`:
```text
context = the shared transition logic between State 1 and State 2
```

For `SPLIT_SCREEN_MULTIPANEL`:
```text
context = the shared mechanism, comparison, or relationship that binds all panels together
```

Civilization-specific context must come from:
```text
CHINA_SESSION_CONTROL.md
CHINA_ERA_LOCK_NEW.md
active episode files such as 00_BRIEF.md / 01_SCRIPT.md
```

For EP00:
```text
Use the EP00 default visual-era anchor defined inside CHINA_ERA_LOCK_NEW.md.
If no stricter era is assigned by the user, EP00 defaults to the HAN DYNASTY profile as Han-style early imperial China visual language.
This does not mean EP00 is narratively about the Han dynasty.
It only means EP00 uses Han-style early imperial China as its default visual language.
Do not use a separate EP00 visual lock file by default.
```

QA Anchor Context must answer:
```text
Is the context using the correct type for the shot_type?
For SINGLE_SHOT, is the context a concrete scene setting, not only an abstract mechanism?
Does the context include an approved historical / civilization / episode anchor from the active authority files?
Does the context avoid vague anchors such as ancient Asian, old Chinese world, or generic ancient China costume scene?
Does the context avoid unsupported era mixing?
Does the shot remain historically plausible and internally coherent?
Is the mechanism expressed through scene setting, body, object, threshold, institution, or action rather than abstract thesis language alone?
Does viewer_sees already give enough concrete period-normalized visual direction for prompt_raw?
```

Suggested context pattern for `SINGLE_SHOT`:
```text
[approved historical / episode anchor], [concrete scene setting], [shot mechanism expressed physically]
```

Bad context examples:
```text
ancient power system
dark Chinese history
symbolic road of command
generic ancient Asian setting
old Chinese world
power becoming benefit
```

If QA Anchor Context fails, revise `viewer_sees` and `context` before writing `prompt_raw`.

---

## 7.6 prompt_raw

Write `prompt_raw` only after:
```text
optimized shot plan exists
visual_goal is clear
viewer_sees is concrete and period-normalized
layout / shot_type mapping is valid
QA Anchor Context has passed
```

`prompt_raw` is the technical prompt ingredient block.

It must follow:
```text
CHANNEL_VEO_PROMPT_RULES_NEW.md
```

`prompt_raw` should not be the only place where meaning is understandable.

Core rule:
```text
prompt_raw = technical visual construction.
visual_goal / viewer_sees = human production understanding.
```

---

## 7.7 GKStudio / Projectbeat JSON

After `prompt_raw` is complete, output the final GKStudio-compatible projectbeat JSON.

The JSON must be valid.

Do not include markdown around JSON when the user requests JSON only.

Do not add extra fields unless the active schema or user explicitly asks for them.

Do not output downstream full Veo prompts unless the user asks for that layer.

Do not include internal normalization scratch fields by default.

Do not include:
```text
shot_visual_anchor_spec
viewer_sees_draft
internal anchor notes
QA scratch notes
```

Core rule:
```text
PROJECT_STORYBOARD_PROMPT_ROOM stops at projectbeat / GKStudio JSON with prompt_raw.
```

---

## 7.8 Internal Order QC

Before finalizing any shot card, check:
```text
Did this shot come from the optimized shot plan?
Did the shot preserve its Group logic?
Is min_visual_time preserved as edit/readability timing intent?
Did narration_cue define the voice fragment without controlling shot split?
Did visual_goal explain why the shot exists?
Did viewer_sees describe what the operator must actually see?
Is viewer_sees concrete enough without relying on prompt_raw?
Did viewer_sees avoid generic / modern / translation-like terms when active authority files provide concrete alternatives?
Does prompt_raw follow CHANNEL_VEO_PROMPT_RULES_NEW.md?
Can a human understand and judge the shot without reading prompt_raw?
Is the final output valid GKStudio/projectbeat JSON?
```

If any answer fails, rewrite the shot in the correct order.

---

# 8. HUMAN-READABLE PROJECTBEAT FIELD RULES

These projectbeat fields are for human reading and production operation:
```text
beat_goal
beat_visual_flow
beat_operator_focus
visual_idea
layout
min_visual_time
visual_goal
viewer_sees
operator_notes
```

They are not prompt fields.

They are not technical schema explanations.

They are production guidance for a human asset operator, editor, or creator.

Default language:
```text
Vietnamese
```

Use English only for:
```text
prompt_raw
exact narration lines
shot IDs
technical JSON keys
tool-required values
```

Core rule:
```text
Human-readable fields must be specific, concrete, and practical enough for a person to select, create, or judge footage.
```

Do not write these fields as abstract thesis labels.

Do not write them as vague mood notes.

Do not assume the operator already understands the hidden thesis.

---

## 8.1 Writing Quality Standard for Human Fields

`beat_visual_flow`, `visual_goal`, and `viewer_sees` are not filler fields.

They are the main bridge between script meaning and asset operation.

They must be written in plain Vietnamese that a tired human operator can understand quickly.

Quality target:
```text
read once
understand the need
know what footage is right
know what footage is wrong
```

Avoid these writing styles:
```text
abstract thesis language
poetic mood without visual instructions
generic production words like cinematic / powerful / dramatic
object lists without action
paperwork as default metaphor
AI-prompt language copied into Vietnamese
translation-like phrases that preserve generic English nouns
modern terms for ancient roles, places, or objects
```

Prefer this writing style:
```text
simple Vietnamese
direct meaning
visible action
specific place / subject / action / cue
period-normalized nouns when available
specific enough to judge footage
short enough to scan quickly
```

Quality rule:
```text
If viewer_sees cannot help a human choose or create a clip, it is not viewer_sees yet.
```

---

## 8.1A Show-Don’t-Tell Meaning Transfer Rule

Because this channel uses show-don't-tell, narration is not the main authority for Veo prompt detail.

Narration frames the thought.

Human-readable visual fields must carry the meaning that narration leaves for the image to prove.

Meaning must transfer in this chain:
```text
narration meaning
→ beat_visual_flow
→ visual_idea
→ visual_goal
→ viewer_sees
→ prompt_raw
```

Core rule:
```text
The more restrained the narration is, the more the visual fields must carry.
```

Do not treat `narration_cue` as enough to create a strong Veo prompt.

`narration_cue` only explains why the shot exists.

The real visual meaning must be expanded in:
```text
beat_visual_flow
visual_idea
visual_goal
viewer_sees
```

These fields should preserve the beat's structural meaning, especially:
```text
mechanism
benefit
margin
extraction
legitimacy
access
status
continuity
inheritance
cost
who gains
who pays
who controls the passage
```

For China Session, every beat and shot should keep the active thesis visible:
```text
Power is the instrument.
Benefit, margin, extraction, legitimacy, continuity, and inheritance are the prize.
```

Quality test:
```text
If the narration were removed, could the visual fields still tell the operator what the shot must prove?
```

If not, rewrite the visual fields before writing `prompt_raw`.

---

## 8.2 beat_goal

`beat_goal` explains what the beat needs the viewer to understand.

It should answer:
```text
Beat này làm người xem hiểu điều gì?
Vì sao beat này tồn tại trong tập?
```

Write in clear Vietnamese.

Rule:
```text
beat_goal = meaning of the whole beat for the viewer.
```

---

## 8.3 beat_visual_flow

`beat_visual_flow` explains how the beat moves visually from first shot to last shot.

In this workflow, it also functions as the beat-level mini visual map when no separate visual map file exists.

Because this project uses show-don't-tell, `beat_visual_flow` must function as the beat-level visual translation of narration meaning.

It must not be only a location chain or image list.

It should explain:
```text
what the narration is trying to prove
what the image must prove instead of the voice
what visual mechanism carries the idea
where the structural turn happens
where benefit, cost, legitimacy, access, or power changes hands
what the viewer must understand by the end
```

Good `beat_visual_flow` should make later `visual_idea`, `visual_goal`, `viewer_sees`, and `prompt_raw` smarter than the narration alone.

Rule:
```text
beat_visual_flow = visual causality chain + thesis pressure across the beat.
```

---

## 8.4 beat_operator_focus

`beat_operator_focus` tells the asset operator what to prioritize and what to reject.

It should answer:
```text
Khi chọn hoặc tạo clip cho beat này, cần ưu tiên gì?
Cần tránh gì?
Chi tiết nào bắt buộc phải thấy?
```

It should include practical guardrails when relevant:
```text
avoid generic roles
avoid modern objects
avoid wrong-era place names
avoid document-only explanation unless the shot is truly about records
keep the mechanism visible through body, object, threshold, distance, or hierarchy
```

Rule:
```text
beat_operator_focus = practical footage-selection guidance.
```

---

## 8.5 visual_idea

`visual_idea` is the concrete idea the shot must show.

It is created during storyboard planning.

It should be clearer than a theme and shorter than `viewer_sees`.

`visual_idea` should describe the shot's visual mechanism, not only its object or location.

Weak:
```text
Gói lệnh rời capital.
```

Stronger:
```text
Bó lệnh rời khỏi bàn công vụ trong trạng thái nhỏ, sạch, chính thức — trước khi tuyến trung gian biến nó thành burden và margin.
```

Rule:
```text
visual_idea = what this shot is visually proving.
```

---

## 8.6 layout

`layout` defines the production layout selected after user-approved storyboard optimization.

Approved production values:
```text
SINGLE_SHOT
SPLIT_SCREEN_2
SPLIT_SCREEN_3
SINGLE_SHOT_TRANSITION
```

Manual edit note values:
```text
MONTAGE_EDIT
MONTAGE_END
```

MONTAGE_EDIT and MONTAGE_END are not prompt_raw layouts.

They are only human shorthand for manual edit grouping after asset generation.

Rule:
```text
layout is a planning decision, not a visual style.
Production layout must be prompt_raw-compatible before Phase B.
```

---

## 8.7 min_visual_time

`min_visual_time` preserves the timing intent from storyboard planning.

It tells the editor/operator the minimum screen time needed for the shot to be visually readable.

It is not final timecode.

It is not Veo generation duration.

Rule:
```text
min_visual_time = timing intent for visual readability and later trimming.
```

---

## 8.8 visual_goal

`visual_goal` is shot-level meaning.

It should answer:
```text
Shot này cần người xem hiểu điều gì?
Shot này phục vụ visual idea nào?
Shot này chứng minh phần nào của beat meaning?
```

Write in Vietnamese.

It should be shorter than `viewer_sees`.

It should connect the shot to the mechanism, not only describe the visible scene.

Weak:
```text
Cho thấy quan sở.
```

Stronger:
```text
Cho người xem hiểu rằng command không tự thành hiện thực; nó phải đi qua người xử lý ở địa phương, và chính điểm xử lý đó tạo cơ hội cho margin.
```

Rule:
```text
visual_goal = why this shot exists and what meaning it proves.
```

---

## 8.9 viewer_sees

`viewer_sees` is the most important human-readable visual field.

It should answer:
```text
Người vận hành cần thấy gì trong clip?
Cảnh nằm ở đâu cụ thể?
Ai hoặc cái gì xuất hiện?
Hành động chính là gì?
Đồ vật chính là gì theo đúng bối cảnh?
Dấu hiệu hình ảnh nào làm ý nghĩa rõ ràng?
```

It must be concrete enough that a human can select or create the clip without reading `prompt_raw`.

Because narration is restrained, `viewer_sees` must include enough concrete visual information to carry the meaning without relying on narration.

It should show:
```text
place
subject
action
object under pressure
body position
threshold / distance / hierarchy
what proves benefit, cost, access, legitimacy, or control
```

`viewer_sees` should not only describe what appears.

It must describe why the visible arrangement makes the mechanism clear.

It must avoid generic or modern wording when the active authority files provide a better period-specific alternative.

Avoid weak generic terms unless they are immediately specified:
```text
phòng hành chính
messenger
packet
office
road
record
official
people
system
```

Better pattern:
```text
[era / authority-specific place] + [visible role / subject] + [period-correct object] + [physical action] + [spatial relationship] + [meaning cue]
```

Rule:
```text
viewer_sees = what the human operator must actually see, and why that visible arrangement proves the shot meaning.
```

If a human cannot choose or create footage from `viewer_sees`, rewrite it.

---

## 8.10 operator_notes

`operator_notes` are optional practical notes.

Use only when the operator needs extra production guidance.

Useful content:
```text
clip can be reused
shot may be short
avoid document-only version
split-screen is intentional
era detail can stay broad
must show threshold clearly
min visual time may be handled by edit hold
source clip will likely be generated as 8s and trimmed in edit
```

Rule:
```text
operator_notes = practical production caution, not hidden thesis.
```

---

## 8.11 Human Field vs prompt_raw Boundary

Use this separation:
```text
visual_idea = shot's concrete visual idea from storyboard
layout = shot's production layout
min_visual_time = edit/readability timing intent
visual_goal = ý nghĩa shot cho người xem
viewer_sees = clip cần nhìn thấy gì và vì sao bố cục đó chứng minh meaning
operator_notes = lưu ý chọn/tạo asset
QA Anchor Context = kiểm tra context đúng anchor trước khi prompt_raw
prompt_raw = vật liệu kỹ thuật theo CHANNEL_VEO_PROMPT_RULES_NEW.md
```

Do not make `prompt_raw` carry the only human-readable meaning.

Do not make `viewer_sees` a copy of `prompt_raw`.

Do not make `visual_goal` a vague thesis slogan.

Do not expose internal normalization scratch fields in final JSON by default.

Core boundary:
```text
Human fields guide people.
prompt_raw guides prompt generation.
Internal normalization improves viewer_sees but stays hidden unless debug is requested.
```

---

## 8.12 Human-Readable Field QC

Before finalizing projectbeat JSON, check:
```text
Are beat_goal, beat_visual_flow, and beat_operator_focus written in Vietnamese?
Are visual_idea, visual_goal, and viewer_sees written in Vietnamese?
Can a human asset operator understand the beat without reading the script?
Can a human select or create a clip from viewer_sees alone?
Does viewer_sees describe place, subject, action, object, spatial relation, and meaning cue?
Does viewer_sees avoid generic / modern / translation-like terms when active authority files support a concrete alternative?
Does beat_visual_flow describe visual causality, thesis pressure, and meaning transfer instead of listing objects?
Does visual_idea say what the shot is visually proving, not only what object appears?
Does visual_goal connect the shot to beat meaning and mechanism?
Does viewer_sees show what proves benefit, cost, access, legitimacy, or control?
Does beat_operator_focus say what to prioritize and what to avoid?
Are the fields concrete rather than abstract?
Are documents avoided as the only explanation unless the shot is truly about records?
Is min_visual_time preserved as timing intent rather than final timing or Veo duration?
If Phase B is next, are all production layouts prompt_raw-compatible?
Are MONTAGE_EDIT / MONTAGE_END kept only as manual edit notes, not production shots?
Did QA Anchor Context pass before prompt_raw?
```

If any answer fails, rewrite the human-readable fields before final output.

---

# 9. ROOM RESPONSIBILITY

## 9.1 Script Room

Primary job:
```text
create and refine 00_BRIEF.md and 01_SCRIPT.md
```

Optional later job:
```text
create 02_TTS_CLEAN_BY_BEAT.md when the user explicitly enters TTS work
```

It should stop before storyboard / projectbeat construction unless explicitly asked.

## 9.2 Project Storyboard Prompt Room

Primary job:
```text
use brief + script + session/era/visual authority files
create storyboard planning
create optimized shot plan
create projectbeat JSON with prompt_raw
```

It should produce:
```text
visual soul check
beat visual flow
user-approved beat visual direction
visual grouping
storyboard draft
Timing Budget Check
optimization suggestions
user-approved optimized shot plan
visual_goal
viewer_sees
prompt_raw
projectbeat JSON
```

It should not automatically create:
```text
TTS clean text
voice audio
final SRT
CapCut edit plan
external-tool prompt packages
```

## 9.3 Architect / Rule Room

Primary job:
```text
maintain channel rules
maintain workflow structure
maintain session and era authority relationships
```

It should not become a default production room.

---

# 10. INPUT PRIORITY FOR PROJECTBEAT CREATION

When creating projectbeat JSON through storyboard-prompt workflow, use this input priority:

```text
1. 01_SCRIPT.md
2. 00_BRIEF.md
3. active session files
4. active era file, including EP00 default visual-era anchor from CHINA_ERA_LOCK_NEW.md when EP00 is active
5. CHANNEL_VEO_PROMPT_RULES_NEW.md
6. optional 02_TTS_CLEAN_BY_BEAT.md if already approved
7. optional beat voice audio / draft alignment if already provided
```

Interpretation:
```text
script controls narration logic and beat meaning
brief controls episode thesis and runtime direction
session / era files control historical and thematic guardrails
CHANNEL_VEO_PROMPT_RULES_NEW.md controls prompt_raw technique
TTS / audio may inform later timing but does not split storyboard shots by default
```

Core rule:
```text
Storyboard planning is script-led and visual-group-led.
It is not audio-led by default.
```

---

# 11. TIMING WORKFLOW RULE

For storyboard-prompt work:
```text
Min visual time is the planning timing unit.
```

Use `min_visual_time` to test whether the visual plan can survive inside the beat target.

Do not use SRT or audio as the first shot-splitting authority.

Do not treat `min_visual_time` as Veo generation duration.

Veo source clips are assumed to be generated at tool-supported duration, typically 8 seconds, then trimmed in edit according to readability needs.

If audio, draft SRT, or alignment is later provided, it may be used for:
```text
checking voice duration
supporting TTS pause planning
helping edit assembly
validating whether optimized shot plan is still realistic
```

It must not automatically rewrite the storyboard logic unless the user asks.

Core timing boundary:
```text
Storyboard Room creates timing intent.
Edit Room creates final timing.
Final SRT belongs after timeline lock.
```

---

# 12. OUTPUT BOUNDARY RULE

The default assistant output boundary is:
```text
projectbeat JSON with prompt_raw
```

This file does not control:
```text
external prompt rewriting
Google Flow operation
other AI prompt expansion
asset generation behavior inside third-party tools
editing tool behavior
final subtitle timing
```

If the user wants help on those layers, they must ask for that layer explicitly.

Core scope rule:
```text
This workflow controls the path from script to storyboard to prompt_raw.
It does not automatically control what other tools do after prompt_raw.
```

---

# 13. FILE CREATION DISCIPLINE

Do not create extra files by default.

Prefer the smallest file set that supports production.

Default production chain should stay lightweight.

Create a new file only when it clearly serves one of these jobs:
```text
authority
session control
era control
script production
storyboard / projectbeat production
TTS production when explicitly requested
editing plan when explicitly requested
```

Do not create sidecar files just to repeat information already stored elsewhere.

Do not create separate anchor-spec files by default.

Internal normalization is a reasoning step, not a required saved artifact.

---

# 14. CHINA SESSION APPLICATION

For China-session work, apply the workflow like this:

```text
CHANNEL_WORKFLOW_CONTROL_NEW.md
→ defines the workflow path and room responsibility

CHANNEL_VEO_PROMPT_RULES_NEW.md
→ defines how prompt_raw must be written

CHINA_SESSION_THESIS.md
→ defines what the China episode is arguing

CHINA_SESSION_CONTROL.md
→ defines what the China session must avoid or preserve

CHINA_ERA_LOCK_NEW.md
→ defines active period visuals for all China episodes
→ includes the EP00 default visual-era anchor when EP00 has no stricter user-assigned era
```

Do not assume a separate episode visual lock for normal episodes.

---

# 15. WORKFLOW CHECKLIST

Before finalizing any production output, check:
```text
Am I in the correct room?
Am I using the correct authority files?
Am I stopping at the correct workflow boundary?
Am I creating projectbeat JSON only when this room is supposed to?
Am I using visual groups rather than SRT to direct shot planning?
Did I first expand storyboard shots before optimizing?
Did I output beat_visual_flow and wait for user approval when required?
Did I run Timing Budget Check?
Did I optimize within Veo-safe production limits?
Am I avoiding compression that crams 4–5 actions or locations into one prompt?
Does the optimized shot plan use: Group | Shot | narration_cue | Visual idea | Layout | Min visual time?
Does each optimized production shot become one production shot entry?
Am I preserving min_visual_time as edit/readability timing intent, not final timecode or Veo duration?
Am I using viewer_sees as the human-visible bridge before prompt_raw?
Did I internally normalize viewer_sees without outputting extra scratch fields?
Am I using prompt_raw as the assistant's visual-planning endpoint?
Am I avoiding unnecessary extra files?
Am I avoiding downstream tool assumptions that belong outside this workflow file?
```

If any answer is unclear, correct the workflow scope before producing output.

---

# 16. RESET PROTOCOL

If the assistant becomes verbose, confused, over-engineered, inconsistent, or starts restoring the old SRT-first workflow, the user can say:
```text
RESET TO CURRENT WORKFLOW.
```

Then the assistant must:
```text
stop expanding workflow
return to storyboard-first projectbeat workflow
preserve the active session thesis
preserve the active era lock rules
avoid schema drift
ask which room/file/beat is next
```

Assistant response after reset should be short:
```text
Reset done.
Back to current storyboard-first projectbeat workflow: 01_SCRIPT.md → PROJECT_STORYBOARD_PROMPT_ROOM → Phase A storyboard planning → user-approved optimized shot plan → Phase B prompt production → projectbeat JSON with prompt_raw. Which beat are we working on next?
```

---

# 17. FINAL OPERATING PRINCIPLE

The workflow exists to help a solo creator produce usable historical documentary clips.

Do not make the system impressive.

Make it operational.

Core line:
```text
Script gives meaning.
Storyboard gives visual logic.
Min visual time protects readability.
Optimization protects runtime without breaking Veo feasibility.
viewer_sees gives operators a concrete clip target.
prompt_raw gives Google AI usable prompt material.
The edit creates final timing.
```
