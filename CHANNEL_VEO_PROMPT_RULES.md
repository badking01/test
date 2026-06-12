# CHANNEL_VEO_PROMPT_RULES.md

## FILE ROLE

This file defines **channel-level prompt rules for `prompt_raw` first**.

The active production workflow for this file is:

```text
01_SCRIPT.md
→ PROJECT_STORYBOARD_PROMPT_ROOM
→ Phase A: Storyboard Planning
→ Optimized Shot Plan
→ Phase B: Prompt Production
→ projectbeat.json / shots[].prompt_raw
```

This file stops at `prompt_raw`.

Downstream use, external AI rewriting, asset generation, clip selection, and editing workflow are controlled by their own rules.

This file controls:

```text
prompt_raw structure
SINGLE_SHOT / SINGLE_SHOT_TRANSITION / SPLIT_SCREEN_MULTIPANEL rules
Veo 3-friendly visual control language
physical concrete prompting
short-clip discipline
camera / framing / movement boundaries
composition/spatial arrangement discipline
material / lighting / color separation
visual constraints preset logic
prompt variation pools
social material hierarchy
prompt_raw QC before JSON output
```

It does **not** control:

```text
episode thesis
narration
TTS
edit plan
civilization-specific visual meaning
country-specific guardrails
era-specific costume, hair, architecture, furniture, tools, weapons, scripts, writing systems, or ritual accuracy
```

Those belong in:

```text
SESSION_THESIS.md
SESSION_CONTROL.md
EP_VISUAL_LOCK.md
ERA_LOCK.md
CHANNEL_WORKFLOW_CONTROL.md
```

---

## AUTHORITY

This file follows:

```text
CHANNEL_IDENTITY.md
CHANNEL_STYLE_LOCK.md
CHANNEL_WORKFLOW_CONTROL.md
```

It must not override:

```text
SESSION_THESIS.md
SESSION_CONTROL.md
EP_VISUAL_LOCK.md
ERA_LOCK.md
```

Conflict rule:

```text
ERA_LOCK.md wins for period accuracy.
EP_VISUAL_LOCK.md wins for episode-specific visual identity.
SESSION_CONTROL.md wins for civilization/session-specific guardrails and visual meaning.
CHANNEL_WORKFLOW_CONTROL.md wins for production workflow and human-readable fields.
CHANNEL_VEO_PROMPT_RULES.md wins only for prompt_raw structure and Veo 3 prompt technique.
```

---

## USED BY WHICH ROOM

Primary use:

```text
[SESSION]_[EPISODE]_PROJECT_STORYBOARD_PROMPT_ROOM
Phase B: Prompt Production
projectbeat JSON generation rooms
```

Also used by:

```text
Veo prompt test / debug rooms
```

This file is the authority for:

```text
shots[].prompt_raw
```

When a room is asked to output valid JSON containing `prompt_raw`, it must follow this file.

Storyboard-to-prompt boundary:

```text
Phase A chooses:
Group
Shot
Visual idea
Layout
Min visual time

This file executes:
prompt_raw template selection
prompt_raw field discipline
Veo technical validation
prompt_raw QC
```

Core rule:

```text
Phase A decides layout.
This file executes layout.
```

---


# 0. QUICK OPERATING CORE

Use this section for normal projectbeat writing.

The full sections below are the rule library for template execution, field discipline, technical validation, debugging, and refinement.

Core scope:

```text
This file controls prompt_raw generation only.
It executes the approved Layout from Phase A: Storyboard Planning.
It does not choose the storyboard shot layout by default.
It does not split or merge shots by itself.
It does not control downstream prompt use, external AI rewriting, asset generation, clip selection, or editing workflow.
```

Upstream input from Optimized Shot Plan:

```text
Group
Shot
Visual idea
Layout
Min visual time
```

Layout-to-prompt_raw mapping:

```text
SINGLE_SHOT
→ prompt_raw.shot_type = SINGLE_SHOT

SPLIT_SCREEN_2
→ prompt_raw.shot_type = SPLIT_SCREEN_MULTIPANEL with 2 panels

SPLIT_SCREEN_3
→ prompt_raw.shot_type = SPLIT_SCREEN_MULTIPANEL with 3 panels

SINGLE_SHOT_TRANSITION
→ prompt_raw.shot_type = SINGLE_SHOT_TRANSITION

MONTAGE_EDIT / MONTAGE_END
→ edit-level layout instruction outside prompt_raw; express as separate production shots or operator_notes when required by the active JSON schema
```

Supported `prompt_raw.shot_type` values:

```text
SINGLE_SHOT
SINGLE_SHOT_TRANSITION
SPLIT_SCREEN_MULTIPANEL
```

Veo short-clip technical validation:

```text
A generated clip should remain technically compatible with a 5–7 second target.
A generated clip must remain under 8 seconds.
One prompt_raw should describe one short visual unit.
```

These rules are validation rules for prompt_raw stability.
They are not storyboard-planning rules.

Shot type execution rule:

```text
SINGLE_SHOT = one scene state, one visual idea.
SINGLE_SHOT_TRANSITION = State 1 → one trigger → State 2.
SPLIT_SCREEN_MULTIPANEL = 2 or 3 simultaneous panels, not time progression.
```

Template rule:

```text
Use the template that matches the approved Layout from Phase A.
Do not switch Layout inside prompt_raw unless the Optimized Shot Plan is revised.
Do not invent extra fields.
```

Field boundary rule:

```text
context = where / what historical-spatial logic
subject = who or what is visible
camera = how the viewer sees it
composition_blocking = where things are placed
action = what moves or holds still
props = what objects must appear
material_textures = what surfaces and materials feel like
lighting_atmosphere = how light and air behave
color_grading = tonal palette and contrast
visual_constraints = Veo-safe physical / optical guardrails
```

Movement boundary:

```text
camera = viewer movement / frame behavior
action = movement inside the frame
transition_trigger = movement that bridges State 1 and State 2
```

Visual style core:

```text
dark
restrained
material
observational
institutional
historically grounded
matte
old optical
non-glossy
```

Written surface rule:

```text
Written surfaces must remain unreadable.
Use blurred ink texture, partial marks, blank worn surfaces, or abstract weathered patterning.
```

Social material rule:

```text
Social hierarchy should read through material quality, access, distance, posture, preservation, and control of space.
High status should feel restrained and protected, not shiny.
Low status should feel exposed to pressure, not theatrically miserable by default.
```

Direct-event rule:

```text
Do not use documents, records, ledgers, or archives as the default image for abstract ideas.
Prefer direct visible events when the idea can be shown through bodies, space, labor, thresholds, objects, or action.
```

Core QC:

```text
maps from Optimized Shot Plan
preserves Group / Shot / Visual idea / Layout intent
concrete
physical
field-clean
short-clip safe
readable without text
historically bounded
non-glossy
free of fantasy / wuxia / costume-drama drift
```

---

# 1. CORE PROMPT_RAW PRINCIPLE

`prompt_raw` is **not** the final Veo prompt.

It is the controlled shot-specific ingredient block that downstream tool or another downstream tool can later interpret into a full Veo 3 prompt.

Core rule:

```text
prompt_raw = structured visual ingredients
downstream prompt = later downstream use
```

Do not write a long finished cinematic paragraph inside `prompt_raw`.

Do not leave key visual decisions for the tool.

The room creating JSON must fill `prompt_raw` clearly enough that:

```text
a human can understand the intended shot
downstream tool can interpret it into a full Veo 3 prompt
Veo 3 can generate a stable short clip
```

---

# 2. VEO 3 SHORT-CLIP DISCIPLINE

Google Veo 3 / Veo 3.1 inside Google Flow is a short-clip video model.

This section validates whether the approved Layout can be executed safely as prompt_raw.
It does not choose the Layout.

A single generated clip should target:

```text
5–7 seconds
```

Hard limit:

```text
under 8 seconds
```

Core validation rule:

```text
One prompt_raw = one short visual unit.
```

Do not treat one prompt like a full scene sequence.

Do not ask one generated clip to perform a long progression, multiple location changes, or multiple temporal turns.

## 2.1 Default Rule — One Prompt, One Scene State

Default to one scene state.

A normal `SINGLE_SHOT` prompt should contain:

```text
one dominant space
one main subject or subject group
one camera behavior
one continuous action or controlled stillness
one readable visual idea
```

This is the safest and most stable Veo 3 behavior.

Use this whenever the shot does not require a visible transition from one state to another.

## 2.2 Golden Limit — Maximum Two Scene States

A single prompt may contain at most two scene states.

This means:

```text
State 1
→ one transition trigger
→ State 2
```

This is the maximum safe temporal progression for Veo 3 / Veo 3.1 inside one prompt.

Never attempt:

```text
State 1 → State 2 → State 3
two separate transitions inside one prompt
a chain of multiple environments, multiple reveals, or multiple action stages inside one generated clip
```

If a prompt contains more than two scene states, Veo is likely to lose temporal logic and produce:

```text
broken or muddy cross-dissolves
object morphing
skipped middle states
unstable continuity
transition collapse
```

Core rule:

```text
Two states are the maximum.
One transition is the maximum.
```

## 2.3 Two-State Transition Rule

Use a two-state prompt only when the transition itself is the visual idea.

A two-state prompt must follow this structure:

```text
State 1 establishes the source space and starting action.
One trigger action causes the transition.
State 2 reveals the destination space and resolves into a readable end state.
```

Recommended time distribution:

```text
State 1: about 55–65%
Transition trigger: brief handoff moment
State 2: about 35–45%
```

Only one transition trigger is allowed.

The trigger is not a third state.

The trigger is a transition device.

## 2.4 Valid Transition Triggers

A valid trigger is a strong physical or camera event that naturally wipes, covers, blurs, or kinetically shifts the frame.

Valid trigger types include:

```text
lens_occlusion
body_crossing_lens
cloth_wipe
sleeve_wipe
door_wipe
gate_wipe
smoke_wipe
dust_wipe
darkness_swallow
whip_pan
motion_blur_wipe
```

Examples:

```text
a sleeve sweeps across the camera lens
a figure passes close to camera and fully occludes the frame
a gate closes across the lens
dust swallows the frame
smoke fills the frame
a fast whip pan creates full-frame motion blur
darkness covers the frame before the new scene appears
```

The trigger must bridge State 1 and State 2.

Do not add a separate visual idea inside the trigger.

## 2.5 When to Use SINGLE_SHOT_TRANSITION

Use `SINGLE_SHOT_TRANSITION` only when:

```text
the transition itself is the point of the shot
the before/after contrast must be felt inside one continuous clip
State 1 and State 2 are both simple enough to read quickly
there is only one transition trigger
the destination state resolves clearly
the whole clip remains under 8 seconds
```

Typical use cases:

```text
conceptual reveal
match-cut transition
kinetic wipe from one institutional space to another
one mechanism visually resolving into another
symbolic before/after transformation
```

Do not use `SINGLE_SHOT_TRANSITION` just because two images are interesting.

Use it only when the transition is meaningful.

## 2.6 When to Split into Multiple Shots

Split into separate `SINGLE_SHOT` prompts when:

```text
the progression contains 3 or more scene states
the clip would require 2 or more transitions
the action has multiple clear stages
the camera must meaningfully travel through multiple spaces
the intermediate state matters and must be read
each state can stand alone for about 3 seconds or longer
the transition is not the main point
editorial cutting would be clearer
```

Core rule:

```text
If the viewer must understand more than one turn, split the shot.
```

## 2.7 Multipanel Is Not a Third-State Workaround

`SPLIT_SCREEN_MULTIPANEL` is for parallel or comparative reading.

It is not a workaround for forcing 3 or more temporal states into one prompt.

Use multipanel when:

```text
several ideas must be understood together at the same time
parallel comparison is the point
separate clips would become too short to read
the relation between panels is more important than temporal progression
```

Do not use multipanel to fake a complex time progression that should have been split into separate clips.

## 2.8 Short Visual Noun Cluster Rule

When narration contains 2–4 short visual nouns or symbolic fragments in sequence, do not automatically create one shot per line.

First check whether each noun has enough screen time to stand as its own readable `SINGLE_SHOT`.

Preferred order:

```text
1. If each noun can hold around 3 seconds or more, split them into separate SINGLE_SHOT clips.

2. If the nouns are parallel symbols of the same idea and the total cluster is too short for separate readable shots, use SPLIT_SCREEN_MULTIPANEL.

3. If the nouns form a visible before/after contrast, use SINGLE_SHOT_TRANSITION only when the transition itself carries meaning.

4. If the nouns form 3 or more temporal steps, split into separate shots.

5. If one noun is visually weak or too short to read, merge it with the nearest visual cluster or remove it as a separate visual unit.
```

Do not use `SPLIT_SCREEN_MULTIPANEL` as the first choice when clean `SINGLE_SHOT` pacing is available.

Use `SPLIT_SCREEN_MULTIPANEL` as a readability fallback when multiple parallel symbols are important but too brief to stand alone.

Example:

```text
“Yellow robes. Palace gates. Great walls.”

If timing allows:
→ three SINGLE_SHOT clips.

If timing is too short:
→ one SPLIT_SCREEN_MULTIPANEL triptych.
```

Reason:

```text
The panel layout preserves simultaneous symbolic readability without fragmenting the edit into unreadable micro-shots.
```

## 2.9 Stability Priority

When in doubt, choose stability over ambition.

Veo 3 performs better with:

```text
one stable visual idea
one simple transition
one resolved destination
restrained camera behavior
clear physical action
```

than with:

```text
layered conceptual progression
multiple space changes
overstuffed 8-second storytelling
symbolic morphing
complex camera choreography
```

## 2.10 Core Summary

Safe default:

```text
SINGLE_SHOT
= one prompt
= one scene state
= one visual unit
```

Advanced exception:

```text
SINGLE_SHOT_TRANSITION
= one prompt
= two scene states maximum
= one trigger maximum
= one under-8-second transition unit
```

Parallel exception:

```text
SPLIT_SCREEN_MULTIPANEL
= one prompt
= 2 or 3 parallel panels
= simultaneous comparison or mechanism reading
```

Never exceed:

```text
two scene states in one prompt
one transition in one prompt
three panels in one multipanel prompt
under 8 seconds per generated clip
```

---

# 3. PROMPT_RAW TEMPLATE STANDARD — MANDATORY

When a room outputs JSON containing `prompt_raw`, it must follow one of the approved templates in this section.

Do not invent alternate `prompt_raw` structures.

Do not output YAML inside JSON.

Keep all shot-level visual guardrails inside `visual_constraints`.

Keep `prompt_raw` visual only.

## 3.1 Approved Shot Types

Use exactly one of:

```text
SINGLE_SHOT
SINGLE_SHOT_TRANSITION
SPLIT_SCREEN_MULTIPANEL
```

The value must match the approved Layout from Phase A through the mapping in section 0.

Core rule:

```text
shot_type executes the approved layout and temporal structure only.
```

Visual style is controlled by:

```text
material_textures
lighting_atmosphere
color_grading
visual_constraints
```

Rough animation uses the same approved `shot_type` templates and is expressed through:

```text
material_textures
lighting_atmosphere
color_grading
visual_constraints
```

## 3.2 Template A — SINGLE_SHOT

Default to `SINGLE_SHOT`.

Use when the narration can be expressed through:

```text
one dominant space
one main subject or subject group
one continuous action or controlled stillness
one clear visual idea
no scene-state transition
```

JSON structure:

```json
"prompt_raw": {
  "shot_type": "SINGLE_SHOT",
  "context": "",
  "subject": "",
  "camera": "",
  "composition_blocking": "",
  "action": "",
  "props": "",
  "material_textures": "",
  "lighting_atmosphere": "",
  "color_grading": "",
  "visual_constraints": ""
}
```

Field logic:

```text
context
= shared shot-level historical / spatial anchor for the single scene.

subject
= main visible subject, subject group, or object focus.

camera
= framing, shot size, angle, lens perspective, camera position, camera movement, and depth of field only.

composition_blocking
= spatial arrangement from foreground → middle ground → deep background; body hierarchy; threshold; distance; placement.

action
= one concrete physical action or controlled stillness.

props
= required physical objects that make the shot readable.

material_textures
= tactile surface materials, class-coded material quality, object condition, clothing surface, architecture material, and physical wear.

lighting_atmosphere
= light source, indoor/outdoor atmosphere, shadow behavior, air quality, and environmental light condition.

color_grading
= palette, saturation, contrast, tonal treatment, and documentary color logic.

visual_constraints
= Veo-friendly physical and optical constraints, including unreadable written surfaces, historical consistency, and anti-drift controls.
```

## 3.3 Template B — SINGLE_SHOT_TRANSITION

Use `SINGLE_SHOT_TRANSITION` only when one generated clip must move from one scene state to another through a single clear trigger.

Maximum structure:

```text
State 1
→ one transition trigger
→ State 2
```

Do not use this template for 3 states.

Do not use this template for 2 separate transitions.

Do not use this template for a full scene sequence.

JSON structure:

```json
"prompt_raw": {
  "shot_type": "SINGLE_SHOT_TRANSITION",
  "context": "",
  "subject": "",
  "camera": "",
  "state_1": {
    "context": "",
    "composition_blocking": "",
    "action": "",
    "props": "",
    "material_textures": ""
  },
  "transition_trigger": {
    "trigger_type": "",
    "trigger_action": "",
    "visual_bridge": ""
  },
  "state_2": {
    "context": "",
    "composition_blocking": "",
    "action": "",
    "props": "",
    "material_textures": ""
  },
  "lighting_atmosphere": "",
  "color_grading": "",
  "visual_constraints": ""
}
```

Top-level field logic:

```text
context
= shared shot-level transition logic. It explains what the whole transition is doing and why State 1 changes into State 2.

subject
= the main subject, subject group, or recurring visual anchor that binds both states when applicable.

camera
= the overall camera behavior across the transition. Keep it simple, controlled, and compatible with the trigger.

lighting_atmosphere
= shared or transitional light/atmosphere logic across both states.

color_grading
= unified tonal treatment so both states belong to the same channel style.

visual_constraints
= shared physical and optical constraints for both states.
```

State field logic:

```text
state_1.context
= concrete source setting.

state_1.composition_blocking
= spatial arrangement before the trigger.

state_1.action
= starting action before the transition.

state_1.props
= required props visible in State 1.

state_1.material_textures
= tactile materials and surfaces specific to State 1.

transition_trigger.trigger_type
= the kind of transition device.

transition_trigger.trigger_action
= the physical or camera action that causes the transition.

transition_trigger.visual_bridge
= how the frame is covered, blurred, wiped, swallowed, or kinetically shifted.

state_2.context
= concrete destination setting.

state_2.composition_blocking
= spatial arrangement after the trigger clears.

state_2.action
= resolved action or controlled stillness after the transition.

state_2.props
= required props visible in State 2.

state_2.material_textures
= tactile materials and surfaces specific to State 2.
```

Valid `trigger_type` examples:

```text
lens_occlusion
body_crossing_lens
cloth_wipe
sleeve_wipe
door_wipe
gate_wipe
smoke_wipe
dust_wipe
darkness_swallow
whip_pan
motion_blur_wipe
```

Core rule:

```text
The trigger is not a third state.
The trigger is the bridge between State 1 and State 2.
```

## 3.4 Template C — SPLIT_SCREEN_MULTIPANEL

Use `SPLIT_SCREEN_MULTIPANEL` only when several ideas must be understood together at the same time.

It is an exception, not the default.

Use it when both are true:

```text
the narration carries multiple parallel ideas, contrasts, or compressed mechanism layers
splitting them into separate clips would create fragments too short to read visually
```

Do not use multipanel only because the narration contains many nouns.

Do not use multipanel when each idea can become a clear standalone clip of about 3 seconds or longer.

Do not use multipanel as a workaround for 3 scene states.

Use 2 panels for:

```text
contrast
comparison
cause-effect pair
two-sided mechanism
```

Use 3 panels for:

```text
clear three-part mechanism
parallel social layers
before / process / result
source / conversion / result
demand / extraction / surplus
```

Never use more than 3 panels.

JSON structure:

```json
"prompt_raw": {
  "shot_type": "SPLIT_SCREEN_MULTIPANEL",
  "context": "",
  "camera": "",
  "composition_blocking": "",
  "shared_material_textures": "",
  "lighting_atmosphere": "",
  "color_grading": "",
  "panel_1_scene": {
    "context": "",
    "subject": "",
    "composition_blocking": "",
    "action": "",
    "props": "",
    "material_textures": ""
  },
  "panel_2_scene": {
    "context": "",
    "subject": "",
    "composition_blocking": "",
    "action": "",
    "props": "",
    "material_textures": ""
  },
  "panel_3_scene": {
    "context": "",
    "subject": "",
    "composition_blocking": "",
    "action": "",
    "props": "",
    "material_textures": ""
  },
  "visual_constraints": ""
}
```

For 2-panel shots:

```text
remove panel_3_scene
```

Top-level field logic:

```text
context
= shared mechanism, comparison, or relationship that binds all panels together.

camera
= locked flat diptych or triptych framing. No independent camera movement inside panels.

composition_blocking
= overall panel arrangement and visual relationship between panels.

shared_material_textures
= shared tactile material logic across panels when needed.

lighting_atmosphere
= unified lighting/atmosphere logic across the entire multipanel layout.

color_grading
= unified tonal treatment across panels.

visual_constraints
= shared physical and optical constraints across all panels.
```

Panel field logic:

```text
panel_x_scene.context
= concrete local setting for that panel.

panel_x_scene.subject
= visible subject or subject group inside that panel.

panel_x_scene.composition_blocking
= spatial arrangement inside that panel.

panel_x_scene.action
= one simple action or controlled stillness inside that panel.

panel_x_scene.props
= required props inside that panel.

panel_x_scene.material_textures
= panel-specific tactile materials and surfaces if different from shared_material_textures.
```

Multipanel camera rule:

```text
locked flat diptych / triptych composition
static framing
no independent camera movement inside panels
no panel-by-panel pan
no panel-by-panel zoom
minimal physical motion only
```

Panel readability rule:

```text
Each panel must be physically readable at a glance.
Do not use readable labels to explain panels.
Do not place unrelated scenes together unless the top-level context clearly defines the relation.
```

---

# 4. PROMPT_RAW FIELD DEFINITIONS

This section defines the meaning and boundary of every approved `prompt_raw` field.

The purpose is to prevent field overlap.

Each field should carry one kind of visual information only.

## 4.1 Universal Field Boundary Rule

Do not collapse all visual information into one long style paragraph.

Each field has a separate job.

Core separation:

```text
context = where / what historical-spatial logic
subject = who or what is visible
camera = how the viewer sees it
composition_blocking = where things are placed
action = what moves or holds still
props = what objects must appear
material_textures = what surfaces and materials feel like
lighting_atmosphere = how light and air behave
color_grading = tonal palette and contrast
visual_constraints = Veo-safe physical / optical guardrails
```

Do not move information into the wrong field.

Examples:

```text
Camera should not contain lighting, color grading, grain, haze, mood, or material texture.

Material_textures should not contain camera language.

Lighting_atmosphere should not contain social-class material hierarchy.

Color_grading should not contain props or action.

Visual_constraints should stay as positive visual-state guidance.
```

## 4.2 context

`context` defines the shot-level historical world, visible space, and specific visual logic.

Every `context` must contain three layers:

```text
[active historical-world anchor] + [visible spatial anchor] + [shot-specific visual logic]
```

### Layer 1 — active historical-world anchor

The first layer anchors the shot inside the active historical world.

It answers:

```text
What civilization, dynasty, era, or historical world does this shot belong to?
```

This layer must be selected from the active project authority files.

Use the active files in this order:

```text
EP_VISUAL_LOCK.md
ERA_LOCK.md
SESSION_CONTROL.md
```

This channel rule only requires the layer to exist.

It does not define the actual anchor value.

Do not hardcode civilization, dynasty, episode, country, or era values inside this channel rule.

Good Layer 1 pattern:

```text
[active historical-world anchor selected from the current session, episode visual lock, or era lock]
```

Avoid using workflow labels, file names, or episode labels as the anchor itself.

The authority file selects the anchor.

The authority file name is not the anchor.

### Layer 2 — visible spatial anchor

The second layer defines the concrete visible space of the shot.

It answers:

```text
What kind of place are we seeing?
```

Good visible spatial anchors:

```text
court council hall
administrative room
county office exterior
tax collection room
rural field
rural road outside a county gate
ancestral hall interior
lineage school room
fortified wall surface
monastic courtyard
granary threshold
```

Avoid vague spatial anchors:

```text
ancient world
old society
power system
symbolic space
historical atmosphere
civilization memory
```

### Layer 3 — shot-specific visual logic

The third layer explains what this shot is doing visually.

It answers:

```text
What is this shot making visible?
```

Good shot-specific visual logic:

```text
imperial authority appearing as familiar surface power
imperial authority becoming visually insufficient as administrative work fills the foreground
command leaving the office and entering the road toward society
law becoming real through a reader before waiting villagers
grain tax moving from villagers into administrative measurement
land, education, and office shown as simultaneous channels of elite reproduction
```

Avoid abstract thesis language:

```text
power system
elite reproduction
historical pressure
the invisible machine
civilization logic
```

Convert abstract ideas into visible space, body position, object, material, action, threshold, distance, camera framing, or social relation.

### Core context formula

Use this structure:

```text
context = active historical-world anchor + visible spatial anchor + shot-specific visual logic
```

Examples:

```text
[active historical-world anchor] + court council hall + imperial authority appearing as familiar surface power
```

```text
[active historical-world anchor] + tax collection room + grain tax moving from villagers into administrative measurement
```

```text
[active historical-world anchor] + rural field + state extraction reaching village labor through measurement and command
```

```text
[active historical-world anchor] + monastic tax collection room + religious institution converting obligation into recorded surplus
```

### SINGLE_SHOT context

For `SINGLE_SHOT`:

```text
context = [active historical-world anchor] + [visible spatial anchor] + [single scene visual logic]
```

Example:

```text
[active historical-world anchor] + administrative room + law becoming real through a reader before waiting villagers
```

### SINGLE_SHOT_TRANSITION context

For `SINGLE_SHOT_TRANSITION`:

```text
context = [active historical-world anchor] + [shared visible world or transition corridor] + [shared transition logic between State 1 and State 2]
```

Example:

```text
[active historical-world anchor] + administrative gate and rural road corridor + command moving from office space into the road toward society
```

For `SINGLE_SHOT_TRANSITION`, `state_1.context` and `state_2.context` must also use the same layered principle:

```text
state_1.context = [active historical-world anchor] + [source spatial anchor] + [source scene logic]
state_2.context = [active historical-world anchor] + [destination spatial anchor] + [destination scene logic]
```

Example:

```text
state_1.context = [active historical-world anchor] + administrative room + sealed command prepared inside office space
state_2.context = [active historical-world anchor] + rural road outside a county gate + command moving toward society
```

### SPLIT_SCREEN_MULTIPANEL context

For `SPLIT_SCREEN_MULTIPANEL`:

```text
context = [active historical-world anchor] + [shared spatial or institutional world] + [shared comparison or mechanism across panels]
```

Example:

```text
[active historical-world anchor] + institutional society across land, school, and office spaces + land, education, and office shown as simultaneous channels of elite reproduction
```

For `SPLIT_SCREEN_MULTIPANEL`, each `panel_x_scene.context` must also use:

```text
panel_x_scene.context = [active historical-world anchor] + [panel spatial anchor] + [panel-specific visual logic]
```

Example:

```text
panel_1_scene.context = [active historical-world anchor] + rural landholding space + field boundary as material control
panel_2_scene.context = [active historical-world anchor] + lineage school interior + education as access gate
panel_3_scene.context = [active historical-world anchor] + administrative office interior + office access as institutional status
```

### Authority boundary

This channel rule defines the required `context` structure.

It does not define the actual active historical-world anchor.

The active historical-world anchor must come from:

```text
EP_VISUAL_LOCK.md
ERA_LOCK.md
SESSION_CONTROL.md
```

Channel-level rules must not hardcode civilization, dynasty, episode, country, or era values.

### Final context test

Before accepting `context`, ask:

```text
Does it begin with the active historical-world anchor?
Does it include a visible spatial anchor?
Does it include shot-specific visual logic?
Can the downstream tool understand the historical world, the place, and the visual purpose?
Is the historical-world anchor selected from the active session, episode visual lock, or era lock?
Is the wording concrete rather than abstract thesis?
```

If any answer is unclear, rewrite `context`.

## 4.3 subject

`subject` defines the main visible subject, subject group, or object focus.

It should describe what must appear on screen.

Good:

```text
a lone clerk seated at a low desk beside sealed administrative packets
villagers carrying grain sacks toward a county gate
a younger outsider standing at the threshold of an elite family hall
```

Avoid abstract thesis words:

```text
power
the elite ecosystem
legitimacy
dynastic memory
historical pressure
```

The subject must be visible.

## 4.4 camera

`camera` defines how the viewer sees the shot.

It may include:

```text
shot size
framing
camera angle
camera position
lens perspective
depth of field
camera movement
locked or moving frame
```

Camera movement means the movement of the camera, not the movement of the subject.

Good camera language:

```text
locked medium-wide observational frame
static frontal composition
slow controlled push-in
slow controlled lateral track
fixed low-angle frame
macro close-up with shallow depth of field
```

Bad camera language:

```text
the clerk walks across the room
villagers carry grain toward the gate
the official lifts a document
a sleeve covers the lens
dust moves through the room
```

Those belong to `action` or `transition_trigger`.

Camera should answer:

```text
How does the viewer see the shot?
```

Camera should not answer:

```text
What does the subject do?
What moves inside the frame?
What event happens?
```

## 4.5 composition_blocking

`composition_blocking` defines the spatial arrangement inside the frame.

It should explain where bodies, objects, thresholds, and power relationships sit.

Use:

```text
foreground
middle ground
background
inside / outside threshold
above / below platform
near / far from authority
center / edge of frame
ranked bodies
blocked entry
open passage
```

Good:

```text
foreground holds a low desk and sealed packets; middle ground shows clerks working; deep background shows the distant raised court platform
```

Good:

```text
the outsider stands lower and closer to the threshold while seated elders occupy the deeper interior space
```

Avoid:

```text
beautiful composition
dramatic scene
symbolic hierarchy
cinematic power
```

Blocking should reveal relation, not decorate the scene.

## 4.6 action

`action` defines what the visible subject, object, material, or environment does inside the frame.

It does not define camera movement.

For normal `SINGLE_SHOT`, use one continuous action.

Good action language:

```text
hands slowly tie a sealed packet
grain pours slowly into a measuring basket
a villager lowers a heavy sack onto wet ground
dust drifts through the side light
the figures remain still while one sleeve edge barely shifts
```

Bad action language:

```text
slow push-in
wide observational shot
static frontal frame
macro close-up
lateral tracking movement
```

Those belong to `camera`.

For `SINGLE_SHOT_TRANSITION`, action is split into:

```text
state_1.action
transition_trigger.trigger_action
state_2.action
```

Do not place the full transition chain into one generic `action` sentence.

## 4.7 props

`props` defines required physical objects that make the shot readable.

Props should not be decorative filler.

Good:

```text
grain sacks, measuring basket, low work table
field boundary stone, measuring rope, muddy field edge
sealed packets, low desk, administrative marking tool
marriage gifts, red cloth, ritual vessels, family hall objects
```

Avoid long prop lists.

Do not include every possible object.

Choose only what the shot needs.

If the meaning can be shown through a direct visible event, do not default to documents.

## 4.8 material_textures

`material_textures` defines tactile surface identity.

It may include:

```text
cloth quality
wood condition
stone wear
metal age
paper or record surface condition
mud / dust / grain / skin texture
class-coded material quality
architecture material
object wear
```

Good:

```text
coarse natural cloth, worn hems, rough wood, mud, work-marked hands
```

Good:

```text
aged fine woven fabric, protected dark wood, carefully maintained stone, restrained inner-room surfaces
```

Good:

```text
plain functional garments, worn desks, handled administrative surfaces, matte wood, orderly storage
```

Do not put lighting or color grading here.

Bad:

```text
low side light, heavy shadows, desaturated color, cinematic gloom
```

Those belong to:

```text
lighting_atmosphere
color_grading
```

## 4.9 lighting_atmosphere

`lighting_atmosphere` defines light behavior and environmental atmosphere.

It may include:

```text
indoor / outdoor light source
side light
overcast light
shadow behavior
dimness
air quality
smoke / dust / mist if used as atmosphere
interior / exterior light relationship
```

Good:

```text
weak side light entering from a small opening, deep natural shadows, still interior air
```

Good:

```text
heavy overcast exterior light with soft shadow edges and restrained environmental stillness
```

Good for mixed space:

```text
dim interior side light and overcast exterior light are unified by low-contrast documentary atmosphere
```

Do not put camera movement, props, social-class material hierarchy, or color palette here.

## 4.10 color_grading

`color_grading` defines palette, saturation, contrast, and tonal treatment.

It may include:

```text
desaturation
earth tones
ash-gray palette
dark bronze shadows
muted contrast
monochrome sepia
paper-beige animation tone
```

Good:

```text
desaturated muddy browns, ash-grays, dark charcoal earth tones, restrained bronze shadows, low micro-contrast
```

Good:

```text
monochrome carbon-black ink, dark sepia washes, aged parchment beige, no vibrant saturation
```

Do not place lighting source, camera movement, props, or material hierarchy here.

## 4.11 visual_constraints

`visual_constraints` defines Veo-safe visual guardrails.

It should describe how risky elements appear physically.

Use positive visual-state language.

Good:

```text
written surfaces remain unreadable, reduced to blurred ink texture, partial marks, blank worn surfaces, or abstract weathered patterning
```

Good:

```text
all clothing, grooming, objects, architecture, and materials remain historically consistent with the active era or visual lock
```

Avoid negative-list style:

```text
no text, no modern objects, no glossy look, no bad anatomy
```

Better:

```text
all signboards are plain weathered surfaces without visible writing; all materials remain matte, aged, and non-glossy; all objects belong to the active historical context
```

`visual_constraints` should stay compact and risk-focused.

It should control risk.

## 4.12 Transition-Specific Fields

These fields apply only to `SINGLE_SHOT_TRANSITION`.

### state_1

`state_1` defines the source scene.

It contains:

```text
context
composition_blocking
action
props
material_textures
```

It should establish the starting state quickly and clearly.

### transition_trigger

`transition_trigger` defines the one allowed bridge between State 1 and State 2.

It contains:

```text
trigger_type
trigger_action
visual_bridge
```

`trigger_type` names the device.

Examples:

```text
cloth_wipe
sleeve_wipe
whip_pan
smoke_wipe
dust_wipe
door_wipe
gate_wipe
lens_occlusion
motion_blur_wipe
darkness_swallow
```

`trigger_action` describes the physical or camera action.

`visual_bridge` describes how the frame is covered, blurred, wiped, swallowed, or shifted.

The trigger is not a third state.

### state_2

`state_2` defines the destination scene.

It contains:

```text
context
composition_blocking
action
props
material_textures
```

It should resolve into a readable end state.

Do not add another transition after State 2.

## 4.13 Multipanel-Specific Fields

These fields apply only to `SPLIT_SCREEN_MULTIPANEL`.

### shared_material_textures

Use this when all panels need a shared tactile material logic.

Example:

```text
matte aged materials, restrained institutional surfaces, worn wood, coarse cloth, weathered stone
```

If panels differ by class or location, use panel-specific `material_textures` as well.

### panel_x_scene

Each panel must contain:

```text
context
subject
composition_blocking
action
props
material_textures
```

Each panel must be physically readable at a glance.

Do not use readable labels to explain panels.

Do not place multiple unrelated scenes inside one panel.

### top-level composition_blocking

For multipanel, top-level `composition_blocking` defines the panel arrangement.

Good:

```text
locked triptych layout with the left panel showing land, the center panel showing education, and the right panel showing office access
```

Avoid:

```text
cool panel effect
three symbolic images
dynamic panel energy
```

Multipanel is for simultaneous reading, not temporal progression.

## 4.14 Camera Movement vs Subject Action Boundary

Camera movement and subject action must not be confused.

`camera` describes the movement or stillness of the viewer's viewpoint.

`action` describes the movement or stillness of visible subjects, objects, materials, or environment inside the frame.

Use this test:

```text
If the viewer's viewpoint moves, write it in camera.
If something inside the frame moves, write it in action.
If the movement causes a transition between State 1 and State 2, write it in transition_trigger.
```

Examples:

```text
slow push-in
→ camera

locked wide frame
→ camera

villagers carry grain
→ action

hands tie a record bundle
→ action

dust drifts through light
→ action or lighting_atmosphere depending on use

sleeve sweeps across the lens to reveal a new scene
→ transition_trigger

whip pan wipes the scene into another scene
→ transition_trigger, with camera describing the overall camera behavior
```

Core rule:

```text
camera = viewer movement / frame behavior.
action = subject or environment movement inside the frame.
transition_trigger = movement that bridges State 1 and State 2.
```

## 4.15 Final Field Rule

Every field must help the final downstream prompt become more stable.

If a field repeats another field, remove the repetition.

If a field contains abstract thesis language, convert it into visible space, body, object, material, action, or camera logic.

If a field tries to do too many jobs, split the information into the correct fields.

---

# 5. PROMPT VARIATION POOLS

Prompt variation pools are reusable Markdown option banks.

They help the room avoid repetitive camera, spatial arrangement, action, material, transition, and multipanel choices while keeping every shot coherent.

Pools are not JSON schemas.

Pools are not output fields.

When writing `prompt_raw`, choose one suitable option from the relevant pool, adapt it to the shot, and write only the final selected choice into the correct `prompt_raw` field.

Core rule:

```text
Pools provide controlled variation.
Prompt_raw records the final selected choice.
```

Do not dump the full pool into each shot.

## 5.1 Pool Principle

Use pools to create variety without breaking:

```text
channel tone
short-clip stability
historical plausibility
field boundaries
session-specific visual guardrails
era-specific accuracy
```

Pool options may be adapted.

Do not copy a pool option blindly if it does not fit the shot.

A pool option is only valid when it matches:

```text
shot_type
narration cue
visual_goal
viewer_sees
active session control
active episode visual lock
active era lock if assigned
```

Do not use pools to override civilization-specific or era-specific rules.

## 5.2 How to Use Pools

When creating `prompt_raw`, follow this process:

```text
1. Identify the shot_type.
2. Identify the visual job of the shot.
3. Choose one suitable option from each relevant pool.
4. Adapt the option to the shot.
5. Write the adapted result into the correct prompt_raw field.
6. Do not include unused pool options.
```

Field mapping:

```text
Camera Pools → camera
Spatial Arrangement Pools → composition_blocking
Action / Micro-Motion Pools → action
Material Texture Pools → material_textures or shared_material_textures
Transition Trigger Pools → transition_trigger
Multipanel Arrangement Pools → composition_blocking for SPLIT_SCREEN_MULTIPANEL
```

Do not mix fields.

Camera pools must not contain lighting, color, grain, haze, material texture, or props.

Action pools must not contain camera movement.

Material pools must not contain camera or lighting behavior.

Lighting and color presets belong to the Visual Preset Library, not this pool section.

## 5.3 Camera Pools

Use camera pools to vary framing, angle, lens perspective, camera position, camera movement, and depth of field.

Camera options should answer:

```text
How does the viewer see the shot?
```

Camera options should not answer:

```text
What does the subject do?
What is the lighting?
What is the color grade?
What materials appear?
```

### Indoor Authority / Institutional Space

Use for courts, offices, archives, ritual halls, administrative interiors, and controlled formal rooms.

Options:

```text
locked medium-wide observational frame from a straight formal axis
static frontal composition from slightly below eye level
slow controlled push-in from a wide frame toward the main subject
side-angle frame through a doorway or threshold, shallow depth of field
fixed wide frame with foreground, middle ground, and deep background clearly separated
```

### Outdoor Road / Field / Public Space

Use for roads, fields, village edges, labor routes, exterior movement, and open public space.

Options:

```text
wide observational frame with distant figures moving through the landscape
locked wide frame from road level, with long lateral depth across the scene
slow controlled lateral track following one direction of movement
medium-wide roadside frame with the subject crossing from foreground to middle ground
static long-lens observational frame compressing distance between people and terrain
```

### Macro / Material Detail

Use for hands, tools, grain, surfaces, clothing edges, ritual objects, and small physical evidence.

Options:

```text
macro close-up on hands and object contact, shallow depth of field
fixed close-up on one material surface with minimal movement
tight observational frame on a single repeated gesture
close detail shot from a low side angle
static insert frame isolating one object against a simple background
```

### Ritual / Formal Body Arrangement

Use for ceremonies, status hierarchy, teaching, judgment, oath, lineage, religious, or formal social scenes.

Options:

```text
symmetrical wide frame centered on the main ritual axis
static medium-wide frame with ranked bodies arranged by distance
low frontal frame emphasizing elevated or seated authority
side-angle frame showing one figure lower, farther, or outside the threshold
locked wide frame preserving formal spacing between groups
```

### Transition-Compatible Camera

Use only for `SINGLE_SHOT_TRANSITION`.

Options:

```text
locked frame until the trigger enters the lens
static composition interrupted by one full-frame occlusion
single sudden whip-pan movement used only as the transition trigger
slow push-in ending at the moment the trigger covers the frame
fixed side frame where a passing body or object wipes the lens
```

## 5.4 Spatial Arrangement Pools

Use spatial arrangement pools to vary spatial relationships, body hierarchy, thresholds, and visual power structure.

Spatial arrangement should answer:

```text
Where are bodies, objects, and spaces placed in relation to one another?
```

### Authority Distance

Use when power is visible through distance, height, rank, or controlled access.

Options:

```text
foreground holds working objects while authority sits distant in the deep background
the main authority figure is elevated while others stand lower in ordered ranks
the viewer looks through layers of officials before reaching the central authority
the subject remains far from the raised platform, blocked by desks and attendants
the frame separates command space above from laboring space below
```

### Threshold Exclusion

Use when the shot shows access, exclusion, blocked entry, or social boundary.

Options:

```text
one figure stands outside the threshold while accepted figures occupy the inner room
the doorway divides exposed exterior space from protected institutional interior
the blocked subject remains at the edge of the frame while the center belongs to insiders
a closed gate or door separates the subject from the room of decision
the composition places belonging in the background and exclusion in the foreground
```

### Administrative Layering

Use for offices, records, law, clerks, commands, and state procedure.

Options:

```text
foreground shows administrative objects, middle ground shows clerks working, background holds authority or storage
a low work surface anchors the frame while bodies gather around it in controlled hierarchy
sealed objects move across the frame from one hand to another through institutional layers
the working desk sits between society and authority as the visual barrier
documents and tools remain supporting props while body position shows the mechanism
```

### Labor / Extraction Arrangement

Use for tax, grain, labor duty, measurement, roads, and visible burden.

Options:

```text
laboring bodies occupy the foreground while officials or record keepers sit farther back
grain or goods move from exposed public space toward controlled institutional space
workers stand low and crowded while measuring tools occupy the center of the frame
the burdened subject bends or lowers the object while the receiving side remains upright
a route of movement leads from field or road into office, gate, or storage
```

### Ritual / Social Incorporation

Use for marriage, lineage, belonging, education, oath, moral authority, or status absorption.

Options:

```text
elders occupy the deep interior while the entering figure remains lower near the threshold
two family groups face one another across ritual objects in the center
a younger figure is positioned below or behind senior figures in formal order
the composition moves from outsider edge toward inner-room belonging
formal spacing shows who is accepted, who witnesses, and who waits
```

## 5.5 Action / Micro-Motion Pools

Use action pools to vary subject, object, material, or environmental movement inside the frame.

Action options should answer:

```text
What happens inside the frame?
```

Action options should not describe camera movement.

### Controlled Stillness

Use when the shot should feel restrained, institutional, or observational.

Options:

```text
the figures remain almost still while only small fabric edges shift
hands pause above the object before completing the gesture
bodies hold formal posture while the room stays quiet
one person waits without moving as others continue the procedure
the scene holds in controlled silence with only minimal environmental movement
```

### Administrative Micro-Action

Use for records, offices, state procedure, bureaucratic processing, and command transmission.

Options:

```text
hands slowly secure an official packet
a clerk moves one object across a low work surface
an administrative marker is placed beside a record object
a messenger presents a sealed item to a seated official
a record object is passed from one hand to another through the office
```

### Labor / Extraction Micro-Action

Use for tax, grain, labor, transport, measurement, or visible burden.

Options:

```text
grain pours slowly into a measuring basket
a worker lowers a heavy sack onto the ground
hands lift a loaded basket toward a receiving table
a cart wheel turns slowly through mud
villagers move in a slow line toward the collection point
```

### Ritual / Social Status Micro-Action

Use for belonging, marriage, lineage, education, oath, religious order, or hierarchy.

Options:

```text
a younger figure bows once before seated elders
hands arrange ritual objects with slow restraint
a figure steps from the threshold into the inner room
elders remain seated while the newcomer waits lower before them
two family groups hold formal posture across ritual objects
```

### Environmental Motion

Use when the scene needs movement without adding a new action stage.

Options:

```text
dust drifts slowly through the room
cloth edges barely shift in the air
smoke or steam moves gently across the background
loose straw or road dust moves across the ground
a hanging object sways slightly while the people remain still
```

## 5.6 Material Texture Pools

Use material texture pools to prevent all social positions from sharing the same surface language.

Material texture options should answer:

```text
What do the surfaces, clothing, objects, and spaces physically feel like?
```

They should not answer:

```text
How is the shot lit?
How is the image graded?
How does the camera move?
```

Civilization-specific props, costumes, grooming, architecture, ritual objects, and record materials belong in:

```text
SESSION_CONTROL.md
EP_VISUAL_LOCK.md
ERA_LOCK.md
```

### Laboring / Poor / Displaced Class

Use for bodily labor, tax burden, exposure, poverty, displacement, or low social position.

Options:

```text
coarse natural cloth, worn hems, rough wood, mud, work-marked hands, crowded exposed space
patched fabric, damp ground, weathered tools, rough baskets, unstable footing
worn outer garments, bare functional surfaces, simple carrying objects, exposed road or field materials
rough fibers, cracked wood, wet earth, heavy sacks, unprotected hands
```

### Administrative / Clerical / Institutional Class

Use for offices, clerks, bureaucratic work, institutional processing, and state procedure.

Options:

```text
plain functional garments, worn desks, handled administrative surfaces, matte wood, orderly storage
muted practical cloth, aged work surfaces, institutional furniture, restrained working space
simple official materials, handled record objects, worn storage surfaces, formal working posture
aged timber, low work surfaces, corded or sealed objects where historically appropriate
```

### Privileged / Landed / Educated Class

Use for old wealth, education, landed status, family continuity, or elite interior space.

Options:

```text
aged fine woven fabric, preserved furniture, controlled empty space, dark maintained interior surfaces
finer matte textiles, worn but protected wood, formal seating distance, restrained household order
old wealth expressed through material preservation, inner-room access, slower posture, and social distance
carefully maintained stone or wood, protected shelves, formal cloth, restrained elite surfaces
```

### Court / Ruling / Ceremonial Class

Use for ruling authority, court ritual, formal power, or institutional scale.

Options:

```text
matte ceremonial textiles, raised position, formal spatial order, worn stone or timber surfaces
large institutional architecture, ranked arrangement, controlled distance, restrained ceremonial material
elevated placement, deep interior axis, disciplined body hierarchy, aged high-status surfaces
formal cloth, old polished-by-use wood, heavy institutional floor materials, controlled ceremonial spacing
```

### Religious / Ritual / Scholarly Authority

Use for moral authority, teaching, ritual hierarchy, lineage, religious office, or scholarly legitimacy.

Options:

```text
aged ritual surfaces, simple formal textiles, handled teaching objects, preserved interior space
matte ceremonial objects, worn wooden interiors, restrained seating order, quiet scholarly materials
protected shelves, ritual table surfaces, aged paper or record textures where historically appropriate
dark interior wood, disciplined object placement, formal cloth, quiet institutional surfaces
```

### Military / Command Class

Use for military administration, command, logistics, discipline, and organized force.

Options:

```text
worn leather, matte metal, rough command surfaces, transport materials, disciplined storage
weathered armor surfaces, practical cloth, hard road materials, handled weapons or command objects where historically appropriate
heavy carts, rope, wood, mud, metal fittings, supply objects, functional military order
restrained command materials, practical belts, worn boots or footwear, rough campaign surfaces
```

## 5.7 Transition Trigger Pools

Use transition trigger pools only for `SINGLE_SHOT_TRANSITION`.

The trigger must bridge State 1 and State 2.

The trigger is not a third state.

### Lens Occlusion / Body Wipe

Use when a figure or object physically covers the lens.

Options:

```text
a figure passes close to the camera and fully occludes the frame before the destination scene appears
a sleeve or cloth sweeps directly across the lens and wipes the source scene away
a large object crosses the foreground until the frame is fully covered
a door or gate surface passes across the lens and reveals the new state after clearing
```

### Motion Blur / Whip Pan

Use when the transition is driven by camera acceleration.

Options:

```text
one sudden whip-pan creates full-frame motion blur before landing on the destination state
the camera snaps sideways once, using motion blur as the only transition bridge
a fast lateral camera sweep wipes the source space into the destination space
```

### Smoke / Dust / Darkness

Use when atmosphere covers the frame.

Options:

```text
a dense wave of dust fills the frame and clears into the destination state
smoke swallows the source scene before thinning into the new space
the frame falls into darkness for a brief moment before the destination appears
a cloud of steam or powder covers the lens and resolves into the second state
```

### Material Match Cut

Use when a similar surface bridges two spaces.

Options:

```text
a dark cloth surface fills the frame and clears into another dark surface in the destination space
a rough wooden surface passes across the lens and resolves into a different wooden structure
a stone surface fills the frame before revealing another stone environment
a close material texture becomes the visual bridge between two institutional spaces
```

## 5.8 Multipanel Arrangement Pools

Use multipanel arrangement pools only for `SPLIT_SCREEN_MULTIPANEL`.

Multipanel is for simultaneous reading, not temporal progression.

### Two-Panel Contrast / Cause-Effect

Options:

```text
locked diptych with left panel showing source condition and right panel showing consequence
locked diptych with one panel showing authority and the other showing social cost
locked diptych with one panel showing command and the other showing extraction
locked diptych with one panel showing privilege and the other showing exclusion
```

### Three-Panel Mechanism

Options:

```text
locked triptych showing source, conversion process, and result
locked triptych showing demand, extraction, and surplus
locked triptych showing land, education, and office as connected social stages
locked triptych showing outsider, incorporation, and new elite position
```

### Parallel Social Layers

Options:

```text
locked triptych showing court, office, and village as simultaneous layers
locked triptych showing family, school, and bureaucracy as connected institutions
locked triptych showing ritual, record, and office as parallel forms of authority
```

Panel rule:

```text
Each panel must remain simple.
Each panel must be readable at a glance.
Do not place multiple unrelated actions inside one panel.
Do not use readable labels to explain panels.
```

## 5.9 Pool Downstream use Rule

Pools are interpretable over time.

When adding new pool options, follow these rules:

```text
Add only options that preserve channel tone.
Add only options that remain short-clip friendly.
Add only options that respect field boundaries.
Add only options that can be adapted across civilizations.
Do not add civilization-specific props or era-specific costume details to channel-level pools.
Do not add options that encourage fantasy, glossy spectacle, trailer action, or over-complex camera behavior.
```

Before adding a new pool option, ask:

```text
Does this option belong at channel level?
Or should it belong in SESSION_CONTROL.md, EP_VISUAL_LOCK.md, or ERA_LOCK.md?
```

Core rule:

```text
Channel-level pools define reusable visual grammar.
Session and era files define historical specificity.
```

---

# 6. VISUAL PRESET LIBRARY

This section defines reusable channel-level visual presets for the new `prompt_raw` fields.

These presets define reusable visual treatment for the current schema.

Do not collapse camera, material, lighting, color, constraints, and mood into one large paragraph.

Use the correct field:

```text
material_textures = tactile surfaces and material quality
lighting_atmosphere = light and air behavior
color_grading = palette, saturation, contrast, tonal treatment
visual_constraints = Veo-safe physical and optical guardrails
```

This library is channel-level.

Do not place civilization-specific props, era-specific costume, architecture, grooming, weapons, ritual details, or record materials here.

Those belong in:

```text
SESSION_CONTROL.md
EP_VISUAL_LOCK.md
ERA_LOCK.md
```

## 6.1 Preset Principle

Visual presets should preserve the channel’s documentary identity:

```text
dark
restrained
material
observational
institutional
historically grounded
non-glossy
old optical
```

Presets should not make the image feel:

```text
fantasy
wuxia
glossy costume drama
modern commercial
music-video
heroic ruler worship
over-saturated palace spectacle
clean digital AI render
```

A preset is a reusable base.

It may be adapted to the active shot, session, episode visual lock, or era lock.

Do not use presets to override historical specificity.

## 6.2 Lighting Atmosphere Presets

`lighting_atmosphere` defines light source, shadow behavior, interior/exterior atmosphere, and environmental air.

It should not define camera, material hierarchy, props, or color grading.

### 6.2.1 Indoor Documentary Lighting

Use for realistic indoor documentary reconstruction:

```text
weak side light entering from a small opening, deep natural shadows, dim interior air, restrained observational stillness, no beauty lighting
```

Use for:

```text
courts
offices
archives
ritual halls
schools
family interiors
administrative rooms
interior threshold scenes
```

### 6.2.2 Outdoor Documentary Lighting

Use for realistic outdoor documentary reconstruction:

```text
heavy overcast exterior light, soft shadow edges, subdued environmental brightness, restrained air movement, no direct heroic sunlight
```

Use for:

```text
roads
fields
village edges
labor routes
tax collection points
public gates
frontier surfaces
exterior processions
```

### 6.2.3 Mixed Space / Multipanel Lighting

Use for split-screen, transition, or shots that combine indoor and outdoor logic:

```text
dim interior side light and overcast exterior light are unified by low-contrast documentary atmosphere, restrained shadow behavior, and consistent visual stillness across all spaces
```

Use when:

```text
one panel is indoor and another is outdoor
State 1 and State 2 use different spaces
the shot needs both institutional interior and social exterior
the composition must feel visually unified despite multiple spaces
```

Do not let each panel or state feel like a different film.

### 6.2.4 Rough Animation Lighting

Use for rough historical explainer animation:

```text
flat paper-like illumination with no realistic studio lighting, no glossy highlights, no dramatic cinematic beams, and no 3D light modeling
```

Use when the shot uses:

```text
rough historical explainer animation
hand-inked archival diagram
satirical mechanism sketch
aged parchment visual explanation
```

## 6.3 Color Grading Presets

`color_grading` defines palette, saturation, contrast, and tonal treatment.

It should not define lighting source, camera behavior, props, or material hierarchy.

### 6.3.1 Realistic Documentary Dark Earth

Default for realistic documentary reconstruction:

```text
desaturated muddy browns, ash-grays, dark charcoal earth tones, restrained bronze shadows, low micro-contrast, muted saturation, no glossy digital color
```

Use for:

```text
most realistic historical documentary shots
institutional interiors
roads
grain
offices
courts
ritual halls
social hierarchy scenes
```

### 6.3.2 Cold Institutional Gray

Use when the shot needs a colder bureaucratic or archival feeling:

```text
desaturated gray-brown palette, cold ash-gray midtones, charcoal shadows, muted wood and stone tones, restrained contrast, no warm romantic glow
```

Use for:

```text
records
archives
administrative rooms
law processing
empty institutional spaces
bureaucratic stillness
```

### 6.3.3 Rough Animation Monochrome Sepia

Use for rough historical explainer animation:

```text
monochrome carbon-black ink, dark sepia washes, aged parchment beige, low saturation, flat tonal contrast, no vibrant modern color
```

Use for:

```text
mechanism diagrams
conversion loops
parallel social layers
rough symbolic explanation
satirical historical inserts
```

## 6.4 Old Optical Capture Rule

The channel should not look like clean modern AI video.

Realistic shots should feel optically captured, aged, imperfect, and documentary-like.

Preferred optical qualities:

```text
soft aged lens rendering
softened optical resolution
mild focus falloff
softened edges
muted shadow detail
subtle halation only when natural
uneven exposure
low micro-contrast
visible historical film grain
slight atmospheric softness
old documentary lens feel
slightly degraded optical capture
```

Core rule:

```text
The footage should feel old, optical, matte, imperfect, and physically captured.
It should not feel clean, crisp, glossy, hyper-detailed, or newly rendered.
```

Do not overuse optical language inside `camera`.

Camera may define lens perspective and framing.

Old optical qualities should mainly appear through:

```text
color_grading
lighting_atmosphere
visual_constraints
```

## 6.5 Rough Historical Explainer Animation Mode

Rough animation uses the same approved `shot_type` templates.

It can be used with:

```text
SINGLE_SHOT
SPLIT_SCREEN_MULTIPANEL
```

Use rough animation for abstract mechanisms that are difficult to show through realistic footage.

Examples:

```text
extraction logic
conversion loops
elite reproduction
moral gatekeeping
absorption loop
parallel institutional layers
```

The rough animation look should be:

```text
minimalist 2D ink sketch
aged parchment surface
carbon-black linework
dark sepia wash
flat graphic perspective
limited jerky motion
archival explainer insert
dark documentary humor when appropriate
```

It must not look like:

```text
anime
cute cartoon
modern corporate infographic
glossy vector animation
3D render
meme comedy
fantasy creature design
smooth digital CGI
```

When using rough animation, route the style through:

```text
material_textures
lighting_atmosphere
color_grading
visual_constraints
```

Do not create a separate animation `shot_type`.

## 6.6 Preset Selection Rule

Use these defaults unless the active session, episode visual lock, or era lock requires a different treatment.

For realistic indoor shots:

```text
lighting_atmosphere = Indoor Documentary Lighting
color_grading = Realistic Documentary Dark Earth or Cold Institutional Gray
```

For realistic outdoor shots:

```text
lighting_atmosphere = Outdoor Documentary Lighting
color_grading = Realistic Documentary Dark Earth
```

For mixed indoor / outdoor shots:

```text
lighting_atmosphere = Mixed Space / Multipanel Lighting
color_grading = one unified realistic documentary grading across all states or panels
```

For rough animation:

```text
lighting_atmosphere = Rough Animation Lighting
color_grading = Rough Animation Monochrome Sepia
```

For `SINGLE_SHOT_TRANSITION`:

```text
use one unified lighting_atmosphere and color_grading unless the contrast between State 1 and State 2 is the explicit point
```

For `SPLIT_SCREEN_MULTIPANEL`:

```text
use one unified lighting_atmosphere and color_grading across all panels
```

Do not make each panel look like a different visual universe.

## 6.7 Preset Boundary Rule

Do not place these elements in the Visual Preset Library:

```text
specific China props
specific era costume
specific dynasty architecture
specific hair or headwear
specific ritual objects
specific weapon types
specific writing system materials
shot-specific subject action
camera movement pools
social-class material hierarchy
```

They belong elsewhere.

Channel-level visual presets define reusable atmosphere and image treatment.

Session and era files define historical specificity.

---

# 7. VISUAL CONSTRAINTS PRESET LIBRARY

`visual_constraints` defines Veo-safe physical and optical guardrails.

It should be written as positive visual-state guidance.

It should describe how risky elements appear visually, physically, or optically inside the image.

Use positive visual-state language.

Bad:

```text
no text, no logos, no modern objects, no glossy look
```

Better:

```text
written surfaces remain unreadable, reduced to blurred ink texture, blank worn surfaces, partial marks, or abstract weathered patterning; all materials remain matte, aged, historically consistent, and non-glossy
```

Do not leave `visual_constraints` empty.

## 7.1 Constraint Principle

Use `visual_constraints` to control:

```text
unreadable written surfaces
historical consistency
modern-object drift
glossy digital drift
costume-drama drift
fantasy drift
optical softness
material realism
animation-style discipline
```

Do not use `visual_constraints` to explain the thesis.

Do not use it to replace:

```text
context
subject
props
material_textures
lighting_atmosphere
color_grading
```

The positive visual description must already make the shot understandable.

Constraints only protect the shot from drifting.

## 7.2 Realistic Documentary Visual Constraints

Use for realistic documentary reconstruction shots.

```text
Written surfaces remain unreadable, reduced to blurred ink texture, partial marks, blank worn surfaces, or abstract weathered patterning. Clothing, grooming, objects, architecture, tools, furniture, and materials remain historically consistent with the active session, episode visual lock, or era lock. All surfaces remain matte, aged, worn, tactile, and non-glossy. The image keeps softened optical resolution, old documentary lens rendering, visible grain, slight atmospheric softness, muted shadow detail, and low micro-contrast. Contemporary objects, modern styling, readable signage, subtitles, logos, clean digital sharpness, fantasy effects, and glossy costume-drama finish are kept out of the visual world.
```

## 7.3 Rough Animation Visual Constraints

Use for rough historical explainer animation.

```text
All written, mapped, diagrammed, labeled, or symbolic surfaces appear only as unreadable ink strokes, blank shapes, rough marks, or abstract chart-like patterning. The animation remains flat, hand-inked, paper-textured, monochrome-sepia, and archival. Motion stays slow, minimal, jagged, and puppet-like, with limited frame-by-frame shifts on a static aged parchment surface. The image avoids 3D shading, glossy vector smoothness, vibrant cartoon color, clean corporate infographic style, modern subtitles, logos, readable labels, and smooth digital CGI movement.
```

## 7.4 Transition Visual Constraints

Use for `SINGLE_SHOT_TRANSITION` when the shot moves from State 1 to State 2.

```text
The transition remains a single clear visual bridge between two scene states. The frame is covered, blurred, wiped, swallowed, or kinetically shifted by one physical or camera trigger only. State 1 and State 2 remain readable as two distinct states. The trigger does not become a third scene. No additional hidden transition, morphing chain, symbolic transformation, or extra environment appears between the two states.
```

Use this together with either:

```text
Realistic Documentary Visual Constraints
```

or:

```text
Rough Animation Visual Constraints
```

depending on the shot treatment.

## 7.5 Multipanel Visual Constraints

Use for `SPLIT_SCREEN_MULTIPANEL`.

```text
All panels remain visually simple, readable at a glance, and unified by the same channel-level visual treatment. Panel boundaries stay clean and stable. No readable labels, subtitles, arrows, logos, or written explanations appear inside the panels. Each panel contains one simple visual idea only. No panel contains a hidden sequence of multiple temporal states. The multipanel layout remains static, controlled, and non-chaotic.
```

Use this together with either:

```text
Realistic Documentary Visual Constraints
```

or:

```text
Rough Animation Visual Constraints
```

depending on the shot treatment.

## 7.6 Written Surface Rule

When any shot includes:

```text
books
documents
records
ledgers
scrolls
tablets
maps
walls
plaques
signboards
banners
stone surfaces
official packets
genealogy surfaces
administrative marks
```

the written or marked areas must remain visually unreadable.

Use:

```text
blurred ink texture
abstract faded marks
blank worn surfaces
partial non-linguistic strokes
weathered surface patterning
out-of-focus record texture
sealed bundles
folded or cord-tied surfaces
```

Avoid relying on generated readable text.

Core rule:

```text
Written surfaces can carry texture, age, and institutional weight.
They must not carry readable information.
```

## 7.7 Historical Consistency Rule

`visual_constraints` must protect the active historical world.

For channel-level use, write:

```text
clothing, grooming, objects, architecture, tools, furniture, and materials remain historically consistent with the active session, episode visual lock, or era lock
```

Do not invent specific era details inside channel-level constraints.

Era-specific accuracy belongs to:

```text
ERA_LOCK.md
```

Civilization-specific visual rules belong to:

```text
SESSION_CONTROL.md
EP_VISUAL_LOCK.md
```

If a specific era is assigned, the era lock wins.

## 7.8 Constraint Selection Rule

For realistic documentary shots, use:

```text
Realistic Documentary Visual Constraints
```

For rough historical explainer animation, use:

```text
Rough Animation Visual Constraints
```

For transition shots, add:

```text
Transition Visual Constraints
```

For multipanel shots, add:

```text
Multipanel Visual Constraints
```

Do not overload the field with too many repeated warnings.

Keep `visual_constraints` compact, visual, and physical.

## 7.9 Constraint Boundary Rule

`visual_constraints` should not do the job of other fields.

Do not use `visual_constraints` to define:

```text
main subject
main action
camera framing
panel structure
transition logic
social material hierarchy
lighting preset
color grading preset
historical thesis
```

Those belong in their own fields.

Core rule:

```text
visual_constraints protects the shot.
It does not create the shot.
```

---

# 8. FIELD WRITING DISCIPLINE

This section defines how each `prompt_raw` field should be written in practice.

The goal is to keep every field:

```text
concrete
physical
short-clip friendly
field-specific
Veo-stable
visually readable
```

Do not write abstract thesis language inside technical prompt fields.

Convert abstract ideas into:

```text
space
body position
object
material
action
threshold
distance
camera framing
visible social relation
```

## 8.1 General Writing Rule

Every field should help Veo generate a stable short clip.

Good prompt_raw writing is:

```text
specific but not overloaded
visual but not decorative
historical but not over-detailed
cinematic but not trailer-like
physical but not literal-minded
```

Avoid:

```text
symbolic abstraction
full atmospheric paragraphs
multiple actions in one field
uncontrolled camera movement
unreadable-text dependency
generic historical atmosphere
fantasy or costume-drama language
```

## 8.2 context Writing Discipline

`context` should anchor the shot in a concrete visual world.

Good:

```text
imperial administrative command passing from an office toward rural society
a formal court interior where authority sits behind layers of officials
a rural tax collection route between village road and administrative gate
a compressed mechanism showing land, education, and office as connected forms of elite reproduction
```

Avoid:

```text
power system scene
ancient atmosphere
civilization memory
symbolic elite network
history under pressure
```

Rule:

```text
context should tell the downstream tool what kind of world the shot belongs to.
It should not become narration.
```

## 8.3 subject Writing Discipline

`subject` should describe the visible subject.

Good:

```text
a seated clerk handling sealed administrative packets at a low work surface
a line of villagers carrying grain sacks toward a collection point
a younger outsider standing lower at the threshold of an elite interior
a group of elders seated deeper inside a formal family hall
```

Avoid:

```text
the throne's contradiction
elite reproduction
the invisible system
social legitimacy
historical power
```

Rule:

```text
If the subject cannot be seen, rewrite it.
```

## 8.4 camera Writing Discipline

`camera` should describe the viewer’s viewpoint.

Good:

```text
locked medium-wide observational frame from a straight formal axis
static frontal composition from slightly below eye level
slow controlled push-in from a wide frame toward the main subject
macro close-up on hands and object contact, shallow depth of field
locked flat triptych composition, static framing
```

Avoid:

```text
villagers carry grain
a clerk ties a packet
dust drifts through side light
low bronze shadows
aged wood and coarse cloth
```

Those belong to other fields.

Rule:

```text
camera = how the viewer sees the shot.
action = what happens inside the shot.
```

Do not put lighting, color, grain, haze, material texture, props, or subject action inside `camera`.

## 8.5 composition_blocking Writing Discipline

`composition_blocking` should explain spatial relationship.

Good:

```text
foreground holds the low work surface and sealed objects; middle ground shows clerks working; deep background holds the distant authority space
```

Good:

```text
the outsider remains near the threshold while accepted figures occupy the protected inner room
```

Good:

```text
laboring bodies occupy the foreground while officials sit farther back behind the receiving table
```

Avoid:

```text
dramatic composition
symbolic power arrangement
beautiful cinematic arrangement
dark historical framing
```

Rule:

```text
Blocking should reveal relation.
It should not decorate the shot.
```

## 8.6 action Writing Discipline

`action` should contain one physical action or controlled stillness.

Good:

```text
hands slowly secure an official packet
grain pours into a measuring basket
a worker lowers a heavy sack onto the ground
a younger figure bows once before seated elders
the figures remain almost still while only fabric edges shift
```

Avoid:

```text
the clerk writes, stands, walks, seals the record, and hands it to another official
the dynasty collapses and a new order rises
the village transforms into bureaucracy
the camera slowly pushes in
```

Rule:

```text
One shot should not contain a full scene progression.
One action is safer than many actions.
```

Camera movement belongs in `camera`.

Transition-causing movement belongs in `transition_trigger`.

## 8.7 props Writing Discipline

`props` should list only objects that make the shot readable.

Good:

```text
grain sacks, measuring basket, low receiving table
sealed packets, low work surface, administrative marker
field boundary stone, measuring rope, muddy field edge
marriage gifts, red cloth, ritual objects, family hall furniture
```

Avoid:

```text
every possible historical object in the room
decorative props unrelated to the shot
generic documents as the only proof of meaning
large readable signs or labels
```

Rule:

```text
Props support visual meaning.
They should not replace visible action or social relation.
```

## 8.8 material_textures Writing Discipline

`material_textures` should describe tactile surfaces and material quality.

Good:

```text
coarse natural cloth, worn hems, rough wood, mud, work-marked hands
```

Good:

```text
plain functional garments, worn desks, handled administrative surfaces, matte wood, orderly storage
```

Good:

```text
aged fine woven fabric, protected dark wood, carefully maintained stone, restrained inner-room surfaces
```

Avoid:

```text
weak side light
overcast gloom
desaturated palette
slow push-in
wide shot
```

Rule:

```text
material_textures = surface and material.
lighting_atmosphere = light and air.
color_grading = palette and tone.
```

## 8.9 lighting_atmosphere Writing Discipline

`lighting_atmosphere` should describe light and air behavior.

Good:

```text
weak side light entering from a small opening, deep natural shadows, dim interior air
```

Good:

```text
heavy overcast exterior light, soft shadow edges, subdued environmental brightness
```

Good:

```text
dim interior side light and overcast exterior light unified by low-contrast documentary atmosphere
```

Avoid:

```text
coarse cloth and old wood
villagers carrying grain
locked medium-wide frame
ash-gray and dark bronze palette
```

Rule:

```text
lighting_atmosphere controls light behavior.
It should not carry material hierarchy, props, or camera framing.
```

## 8.10 color_grading Writing Discipline

`color_grading` should describe palette, saturation, contrast, and tonal treatment.

Good:

```text
desaturated muddy browns, ash-grays, dark charcoal earth tones, restrained bronze shadows, low micro-contrast
```

Good:

```text
cold gray-brown palette, ash-gray midtones, charcoal shadows, muted wood and stone tones
```

Good:

```text
monochrome carbon-black ink, dark sepia washes, aged parchment beige, low saturation
```

Avoid:

```text
side light entering a room
grain sacks and measuring baskets
slow controlled push-in
coarse cloth and worn hems
```

Rule:

```text
color_grading controls tonal treatment.
It should not carry action, props, camera, or material hierarchy.
```

## 8.11 visual_constraints Writing Discipline

`visual_constraints` should protect the shot from Veo drift.

Good:

```text
written surfaces remain unreadable, reduced to blurred ink texture, partial marks, blank worn surfaces, or abstract weathered patterning
```

Good:

```text
clothing, grooming, objects, architecture, tools, furniture, and materials remain historically consistent with the active session, episode visual lock, or era lock
```

Avoid:

```text
no text, no logo, no modern objects, no fantasy, no bad anatomy, no blur problem
```

Rule:

```text
visual_constraints protects the shot.
It does not create the shot.
```

Do not use `visual_constraints` to explain the thesis or replace missing visual description.

## 8.12 transition_trigger Writing Discipline

`transition_trigger` is used only in `SINGLE_SHOT_TRANSITION`.

It should describe one bridge between State 1 and State 2.

Good:

```text
trigger_type: sleeve_wipe
trigger_action: the official's sleeve sweeps directly across the lens
visual_bridge: dark cloth fully occludes the frame before clearing into the destination state
```

Good:

```text
trigger_type: whip_pan
trigger_action: the camera whips sharply once from the administrative desk toward the dark wall edge
visual_bridge: full-frame motion blur wipes the source scene into the destination scene
```

Avoid:

```text
the room dissolves into a road, then into a wall, then into a battlefield
the scene symbolically transforms across several eras
the camera flies through history
```

Rule:

```text
The trigger is not a third state.
It is one bridge only.
```

## 8.13 state_1 / state_2 Writing Discipline

For `SINGLE_SHOT_TRANSITION`, both states must remain simple.

State 1 should quickly establish the source.

State 2 should resolve clearly into the destination.

Good:

```text
state_1 = a dim administrative room with one clear action
trigger = one sleeve wipe across the lens
state_2 = a fortified wall surface revealed in stillness
```

Avoid:

```text
state_1 contains multiple actions
state_2 adds another transition
state_2 introduces a new complex sequence
the trigger becomes a separate symbolic scene
```

Rule:

```text
State 1 and State 2 must be readable within one under-8-second clip.
```

## 8.14 panel_x_scene Writing Discipline

For `SPLIT_SCREEN_MULTIPANEL`, each panel must be simple.

Good:

```text
panel 1: land boundary with owners and workers
panel 2: school interior with child studying
panel 3: administrative office with official seating
```

Avoid:

```text
each panel has multiple locations
each panel has multiple action stages
panels require readable labels to understand
panels become three temporal states instead of parallel ideas
```

Rule:

```text
Each panel = one simple visual idea.
Multipanel = simultaneous reading, not time progression.
```

## 8.15 Document / Record Discipline

Documents, records, books, ledgers, seals, and archives should not become the default solution for every abstract idea.

Use direct visible events first when possible.

Good direct visuals:

```text
tax burden → grain submitted, measured, carried, stored
land control → boundary stone, measuring rope, people standing on the field
marriage alliance → bride entering, gifts, elders witnessing, ritual space
absorption → outsider entering inner room, receiving office, children studying, marriage alliance, elite seating
dynasty change → abandoned throne, fallen ceremonial garment, old banner lowered, gate changing control
```

Use documents mainly when the narration is about:

```text
law
records
archives
bureaucracy
genealogy
memory storage
documentation
official history
```

Rule:

```text
Documents may support meaning.
They should not carry the whole meaning unless the shot is about documents.
```

## 8.16 Final Writing Test

Before accepting any `prompt_raw`, ask:

```text
Can the viewer understand the shot without readable text?
Does each field do only its own job?
Is the shot under-8-second compatible?
Is there only one action or one controlled transition?
Are camera movement and subject action separated?
Are material, lighting, and color separated?
Does the shot avoid generic document dependence?
Does the shot follow session, episode, and era guardrails?
```

If any answer is unclear, rewrite the field before output.

---

# 9. SOCIAL MATERIAL HIERARCHY RULE

Social position must be readable through material, space, body placement, and access.

Do not give every class the same poor, muddy, rough texture language.

Dark documentary style does not mean every subject must look poor.

Higher-status spaces can remain dark, aged, matte, restrained, and historically grounded while still reading as higher status.

Core rule:

```text
Social hierarchy should be visible through material quality, spatial access, body position, distance from authority, posture, preservation, and control of space.
```

Do not use brightness, gloss, fantasy luxury, or costume-drama spectacle to show status.

Show status through controlled physical evidence.

## 9.1 What Social Material Hierarchy Controls

This rule controls how `material_textures`, `composition_blocking`, `props`, and `subject` communicate social position.

It should affect:

```text
clothing condition
fabric quality
surface preservation
furniture quality
room access
body height
body distance
threshold position
object control
tool quality
ritual position
administrative position
public vs inner space
exposed vs protected space
```

It should not override:

```text
SESSION_CONTROL.md
EP_VISUAL_LOCK.md
ERA_LOCK.md
```

Civilization-specific costume, hair, architecture, weapons, ritual objects, and record materials belong in those files.

## 9.2 Status Should Not Depend on Cleanliness Alone

Avoid this mistake:

```text
poor = dirty
elite = clean
court = shiny
```

This is too simple and can drift into glossy costume drama.

Better:

```text
poor / laboring = exposed, worn, crowded, burdened, physically marked by work
administrative = plain, functional, ordered, handled, procedural
privileged = preserved, protected, spacious, controlled, slow, interior
court / ruling = elevated, ranked, distant, ceremonial, institutional
ritual / scholarly authority = ordered, restrained, preserved, formal, interpretive
military / command = functional, hard-worn, disciplined, logistical, controlled
```

All levels can remain matte, aged, desaturated, and old-optical.

## 9.3 Laboring / Poor / Displaced Class

Use when the shot shows:

```text
manual labor
tax burden
transport
field work
displacement
public exposure
low social position
physical cost of order
```

Material cues:

```text
coarse natural cloth
worn hems
patched fabric
rough wood
mud
damp ground
weathered tools
heavy carrying objects
work-marked hands
simple functional surfaces
```

Spatial cues:

```text
exposed exterior space
crowded foreground
low body position
waiting lines
blocked thresholds
distance from protected interior
burdened movement toward authority
```

Body cues:

```text
bent posture
hands carrying weight
waiting outside
lowered head or body
crowded movement
slow physical strain
```

Avoid:

```text
making poverty look theatrical
overdoing misery
using famine/refugee imagery unless the narration requires it
turning commoners into decorative suffering
```

## 9.4 Administrative / Clerical / Institutional Class

Use when the shot shows:

```text
clerks
offices
records
procedure
bureaucracy
law processing
tax administration
state transmission
institutional labor
```

Material cues:

```text
plain functional garments
worn desks
handled administrative surfaces
matte wood
orderly storage
sealed or secured objects where historically appropriate
simple work tools
repeated procedural objects
```

Spatial cues:

```text
controlled office stillness
low work surfaces
objects arranged by procedure
workers positioned between authority and society
desks acting as barriers or channels
storage behind working bodies
```

Body cues:

```text
seated work posture
hands processing objects
controlled repeated gestures
formal stillness
faces secondary to procedure
```

Avoid:

```text
turning clerks into modern office workers
making bureaucracy look clean and digital
using records as the only meaning when social action is needed
```

## 9.5 Privileged / Landed / Educated Class

Use when the shot shows:

```text
old wealth
landed status
education access
elite interior space
family continuity
marriage value
social preservation
local authority
```

Material cues:

```text
aged fine woven fabric
finer matte textiles
preserved furniture
protected dark wood
carefully maintained stone
restrained household surfaces
formal cloth
objects preserved through continuity
```

Spatial cues:

```text
inner-room access
controlled empty space
protected interior
formal seating distance
others waiting lower or farther away
thresholds controlled by insiders
slower movement inside protected space
```

Body cues:

```text
seated authority
slower posture
witnessing rather than carrying
receiving rather than waiting
being approached rather than approaching
occupying the deeper interior
```

Avoid:

```text
glossy silk spectacle
romantic elite glamour
clean costume-drama luxury
making elites look poor just because the channel is dark
```

Core note:

```text
Privilege should read through preservation, access, distance, and control — not through shine.
```

## 9.6 Court / Ruling / Ceremonial Class

Use when the shot shows:

```text
ruling authority
court ritual
formal power
state ceremony
institutional scale
ranked hierarchy
visible command
```

Material cues:

```text
matte ceremonial textiles
aged high-status surfaces
large institutional architecture
heavy floor materials
dark timber or stone where appropriate
restrained ceremonial objects
formal cloth
worn but maintained surfaces
```

Spatial cues:

```text
raised position
deep interior axis
ranked arrangement
formal distance
controlled approach
large empty space
bodies arranged by status
authority separated by height, depth, or layers
```

Body cues:

```text
stillness
ranked standing or kneeling
ritual posture
slow formal gestures
many bodies oriented toward one authority point
```

Avoid:

```text
heroic emperor worship
overdesigned palace spectacle
glowing throne fantasy
national glory montage
bright romantic court drama
```

## 9.7 Religious / Ritual / Scholarly Authority

Use when the shot shows:

```text
moral authority
ritual order
teaching
scholarly interpretation
religious office
lineage legitimacy
memory institutions
education gatekeeping
```

Material cues:

```text
aged ritual surfaces
simple formal textiles
handled teaching objects
preserved interior space
matte ceremonial objects
worn wooden interiors
protected shelves
quiet scholarly materials
```

Spatial cues:

```text
teacher or elder placed deeper inside
students or juniors lower or farther forward
ritual objects centered between bodies
threshold defining belonging or exclusion
formal order around memory or teaching
```

Body cues:

```text
seated instruction
formal listening
bowing
waiting for recognition
controlled ritual gestures
younger bodies placed lower than senior bodies
```

Avoid:

```text
glowing temple atmosphere
mystical fantasy aura
generic sacred light
modern classroom look unless historically justified
```

## 9.8 Military / Command Class

Use when the shot shows:

```text
organized force
logistics
command
military administration
frontier control
discipline
campaign supply
state violence
```

Material cues:

```text
worn leather
matte metal
rough command surfaces
transport materials
disciplined storage
functional belts
hard road materials
supply objects
weathered armor surfaces where historically appropriate
```

Spatial cues:

```text
ordered formation
supply route
command object at center
bodies aligned by rank
transport objects moving in controlled direction
weapon or supply storage kept disciplined
```

Body cues:

```text
upright readiness
carrying supply
waiting for command
ranked posture
controlled movement
disciplined stillness
```

Avoid:

```text
battle spectacle as default
hero combat
wuxia choreography
fantasy armor
modern tactical posing
```

## 9.9 Higher Status in a Dark Documentary Style

Higher status does not require brighter lighting or glossy surfaces.

Use:

```text
better preserved materials
more controlled space
greater distance from labor
inner-room access
slower posture
formal seating
ranked bodies
fewer crowded objects
objects handled by others
ritual or administrative authority
```

Avoid:

```text
bright luxury
polished fantasy surfaces
glowing gold
clean costume-drama fabric
romantic palace lighting
```

Core rule:

```text
High status should feel old, restrained, protected, and controlled.
Not shiny.
```

## 9.10 Low Status in a Dark Documentary Style

Low status does not require melodrama.

Use:

```text
exposure
burden
crowding
waiting
rough tools
worn surfaces
low body position
blocked access
physical labor
distance from protected rooms
```

Avoid:

```text
turning every commoner shot into famine
overusing suffering faces
making poverty decorative
using misery when the narration is about normal extraction or social position
```

Core rule:

```text
Low status should feel exposed to pressure.
Not theatrically miserable by default.
```

## 9.11 Session and Era Boundary

This section is channel-level.

It defines reusable social-material logic.

It does not define specific historical costumes, hairstyles, architecture, props, weapons, rituals, or record materials.

For civilization-specific details, follow:

```text
SESSION_CONTROL.md
EP_VISUAL_LOCK.md
```

For period-specific details, follow:

```text
ERA_LOCK.md
```

Example:

```text
This file can say:
privileged class should use preserved interior surfaces and controlled empty space.

It should not say:
use Ming official robes, Qing queue hairstyle, bamboo slips, or Roman senatorial toga.
```

Core rule:

```text
Channel-level hierarchy defines social reading.
Session and era files define historical form.
```

## 9.12 Final Social Hierarchy Test

Before accepting `prompt_raw`, ask:

```text
Can the viewer tell who has more access?
Can the viewer tell who waits and who is received?
Can the viewer tell who works and who commands?
Can the viewer tell who is exposed and who is protected?
Can the viewer tell who belongs inside and who remains outside?
Can the viewer tell social position without readable text?
Does the scene avoid making every class look equally poor?
Does higher status remain restrained instead of glossy?
Does low status remain material instead of melodramatic?
```

If social hierarchy is unclear, revise:

```text
subject
composition_blocking
props
material_textures
action
```

before changing lighting or color.

---

# 10. LAYOUT TECHNICAL VALIDATION

This section validates the approved Layout from Phase A: Storyboard Planning.

It does not perform storyboard splitting, merging, or layout selection by default.

Phase A decides:

```text
Group
Shot
Visual idea
Layout
Min visual time
```

This file validates:

```text
whether the selected Layout can be executed safely in prompt_raw
whether the selected template is filled correctly
whether the prompt_raw remains under-8-second compatible
whether the visual idea is overloaded for the selected Layout
```

Core rule:

```text
Storyboard Planning chooses the shot.
Veo Prompt Rules builds and validates the prompt_raw.
```

## 10.1 SINGLE_SHOT Validation

For approved Layout:

```text
SINGLE_SHOT
```

Use:

```text
prompt_raw.shot_type = SINGLE_SHOT
```

Validate that the prompt_raw contains:

```text
one scene state
one dominant space
one main subject or subject group
one camera behavior
one continuous action or controlled stillness
one readable visual idea
```

If the approved shot requires multiple spaces, several action stages, or a temporal chain, the prompt_raw is overloaded.
Return to the Optimized Shot Plan or simplify the prompt_raw.

## 10.2 SPLIT_SCREEN_2 / SPLIT_SCREEN_3 Validation

For approved Layout:

```text
SPLIT_SCREEN_2
SPLIT_SCREEN_3
```

Use:

```text
prompt_raw.shot_type = SPLIT_SCREEN_MULTIPANEL
```

Validate that the prompt_raw contains:

```text
2 panels for SPLIT_SCREEN_2
3 panels for SPLIT_SCREEN_3
one simple visual idea per panel
locked flat diptych or triptych composition
static framing
simultaneous reading
unified lighting_atmosphere and color_grading
no readable labels, arrows, subtitles, or panel text
```

Multipanel validates parallel or comparative reading.
It does not validate a hidden time progression.

## 10.3 SINGLE_SHOT_TRANSITION Validation

For approved Layout:

```text
SINGLE_SHOT_TRANSITION
```

Use:

```text
prompt_raw.shot_type = SINGLE_SHOT_TRANSITION
```

Validate that the prompt_raw contains:

```text
State 1
→ one transition trigger
→ State 2
```

The transition must have:

```text
one source state
one destination state
one physical or optical trigger
one resolved destination
under-8-second compatibility
```

The trigger must not become a third state.
There must be no second transition.

## 10.4 MONTAGE_EDIT / MONTAGE_END Handling

For approved Layout:

```text
MONTAGE_EDIT
MONTAGE_END
```

Do not invent a new prompt_raw shot_type.

Use one of these handling modes according to the active JSON schema or user request:

```text
represent the montage as separate production shots
preserve the montage instruction in operator_notes
convert only the selected individual visual unit into prompt_raw
```

Core rule:

```text
MONTAGE_EDIT and MONTAGE_END are edit-level layout instructions, not prompt_raw templates.
```

## 10.5 Overload Check

Before accepting any prompt_raw, check whether it exceeds the approved Layout.

Overload signs:

```text
one prompt_raw describes three or more locations
one prompt_raw contains multiple temporal turns
one prompt_raw asks for several sequential actions
one panel contains a hidden sequence
one transition contains more than one trigger
one SINGLE_SHOT tries to behave like a montage
```

If overloaded, do not solve the problem by adding more text into prompt_raw.

Use one of these responses:

```text
simplify the prompt_raw to match the approved Layout
ask to revise the Optimized Shot Plan
split into separate production shots when Phase A is revised
move montage behavior to operator_notes when the schema allows it
```

## 10.6 Duration Validation

Use these timing rules only as technical validation:

```text
5–7 seconds = ideal generated clip range
under 8 seconds = hard Veo-compatible limit
about 3 seconds = normal minimum for standalone visual reading
about 2 seconds = rare exception for very simple inserts
under 2 seconds = usually not worth a generated standalone shot
```

`Min visual time` belongs to the upstream Optimized Shot Plan.
It is preserved as timing intent outside prompt_raw when the active JSON schema includes it.

Core rule:

```text
Min visual time guides production timing.
It does not change the prompt_raw template.
```

## 10.7 Layout Compliance Checklist

Before writing or accepting prompt_raw, ask:

```text
Does this shot come from an Optimized Shot Plan row?
Does it preserve Group and Shot identity?
Does it preserve the approved Visual idea?
Does it follow the approved Layout?
Does it respect Min visual time as timing intent outside prompt_raw?
Does prompt_raw avoid inventing extra scene states?
Does prompt_raw avoid merging across groups?
Is the selected template technically safe for Veo?
Can the viewer understand the shot without readable text?
```

Decision output:

```text
approved SINGLE_SHOT → execute Template A
approved SINGLE_SHOT_TRANSITION → execute Template B
approved SPLIT_SCREEN_2 / SPLIT_SCREEN_3 → execute Template C
approved MONTAGE_EDIT / MONTAGE_END → handle outside prompt_raw or as separate production shots
```

---

# 11. PROMPT_RAW QC CHECKLIST

Before outputting any projectbeat JSON containing `prompt_raw`, check every shot against this list.

If a shot fails QC, revise the `prompt_raw` before final output.

## 11.0 Storyboard Mapping QC

Check:

```text
Does the shot come from an approved Optimized Shot Plan row?
Does it preserve Group identity?
Does it preserve Shot identity?
Does it preserve the approved Visual idea?
Does it follow the approved Layout?
Is Min visual time preserved as timing intent outside prompt_raw when the schema includes it?
Does prompt_raw avoid creating new shot splits?
Does prompt_raw avoid merging shots across groups?
```

Core rule:

```text
prompt_raw executes the approved storyboard shot.
It does not redesign the storyboard shot.
```

## 11.1 Schema QC

Check:

```text
Does prompt_raw use one approved shot_type only?
Does it use the correct template for that shot_type?
Are all required fields present?
Does it use only the fields defined by the selected template?
Is prompt_raw written as structured visual source material, not a finished cinematic paragraph?
```

Approved `shot_type` values:

```text
SINGLE_SHOT
SINGLE_SHOT_TRANSITION
SPLIT_SCREEN_MULTIPANEL
```

Core rule:

```text
Follow the selected shot_type template exactly.
Do not invent extra fields.
```

## 11.2 Veo 3 Short-Clip QC

Check:

```text
Is the generated clip under-8-second compatible?
Does the shot target about 5–7 seconds when possible?
Is the shot one short visual unit?
Does it avoid full scene progression?
Does it avoid multiple location changes?
Does it avoid multiple temporal turns?
```

Validation rule:

```text
approved SINGLE_SHOT → one scene state
approved SINGLE_SHOT_TRANSITION → two states with one meaningful trigger
approved SPLIT_SCREEN_MULTIPANEL → 2 or 3 simultaneous panels
approved MONTAGE_EDIT / MONTAGE_END → edit-level handling outside prompt_raw or separate production shots
```

## 11.3 Shot Type QC

### SINGLE_SHOT

Check:

```text
one scene state only
one dominant space
one main subject or subject group
one camera behavior
one action or controlled stillness
one readable visual idea
```

### SINGLE_SHOT_TRANSITION

Check:

```text
State 1 is clear
State 2 is clear
there is exactly one transition trigger
the trigger is not a third state
there is no second transition
the destination resolves clearly
the whole transition remains under-8-second compatible
```

### SPLIT_SCREEN_MULTIPANEL

Check:

```text
2 or 3 panels only
no more than 3 panels
one simple visual idea per panel
static locked multipanel layout
no independent camera movement inside panels
no readable labels or arrows
simultaneous comparison, not temporal progression
```

## 11.4 Field Boundary QC

Check:

```text
Does camera contain only viewer viewpoint, framing, lens perspective, and camera movement?
Does action contain only subject, object, material, or environmental movement inside the frame?
Is transition-causing movement placed in transition_trigger?
Does material_textures describe surfaces and material quality only?
Does lighting_atmosphere describe light and air only?
Does color_grading describe palette, saturation, contrast, and tonal treatment only?
Does visual_constraints protect the shot instead of creating the shot?
```

Core boundary:

```text
camera = viewer movement / frame behavior
action = movement inside the frame
transition_trigger = movement that bridges State 1 and State 2
```

## 11.5 Physical Readability QC

Check:

```text
Can the viewer understand the shot without readable text?
Is the subject visible?
Is the action visible?
Are props meaningful rather than decorative?
Does composition show relation, hierarchy, access, or exclusion?
Does the shot avoid abstract thesis language inside technical fields?
```

If the viewer needs readable text to understand the shot, revise the visual idea.

## 11.6 Document / Record QC

Check:

```text
Are documents, records, ledgers, books, seals, and archives used only when meaningful?
Can the idea be shown through a direct visible event instead?
Do written surfaces remain unreadable?
Are written surfaces treated as texture, age, or material evidence rather than readable information?
```

Direct event test:

```text
tax → grain submitted, measured, carried, stored
land → boundary stone, measuring rope, visible field relation
marriage → bride entering, gifts, elders witnessing, ritual space
absorption → outsider enters inner room, receives office, joins alliance, gains elite seating
dynastic change → abandoned throne, fallen ceremonial garment, old banner lowered, gate changing control
```

## 11.7 Social Material Hierarchy QC

Check:

```text
Can the viewer tell who has more access?
Can the viewer tell who waits and who is received?
Can the viewer tell who works and who commands?
Can the viewer tell who is exposed and who is protected?
Can the viewer tell who belongs inside and who remains outside?
Does the scene avoid making every class look equally poor?
Does higher status remain restrained instead of glossy?
Does low status remain material instead of melodramatic?
```

If hierarchy is unclear, revise:

```text
subject
composition_blocking
props
material_textures
action
```

before changing lighting or color.

## 11.8 Historical Authority QC

Check:

```text
Does the shot follow the active SESSION_CONTROL.md?
Does it follow the active EP_VISUAL_LOCK.md?
If an era is assigned, does it follow ERA_LOCK.md?
Does it avoid civilization-specific details not supported by the active files?
Does it avoid mixing incompatible eras inside one shot?
```

Authority rule:

```text
CHANNEL_VEO_PROMPT_RULES.md controls prompt_raw technique.
SESSION_CONTROL.md controls civilization-specific meaning.
EP_VISUAL_LOCK.md controls episode-specific visual identity.
ERA_LOCK.md controls period accuracy.
```

## 11.9 Visual Style QC

Check:

```text
Does the image remain dark, restrained, material, observational, institutional, and historically grounded?
Does it avoid fantasy, wuxia, anime, glossy costume drama, modern commercial look, heroic ruler worship, and national glory montage?
Does realistic footage keep old optical capture qualities?
Does rough animation remain flat, hand-inked, parchment-based, and non-corporate?
```

Old optical check:

```text
softened optical resolution
old documentary lens rendering
visible grain
slight atmospheric softness
muted shadow detail
low micro-contrast
matte non-glossy surfaces
```

## 11.10 Visual Constraints QC

Check:

```text
Is visual_constraints written as positive visual-state language?
Does it avoid simple negative-prompt listing?
Does it keep written surfaces unreadable?
Does it protect historical consistency?
Does it prevent modern-object drift, glossy drift, fantasy drift, and clean AI-render drift?
Is it compact enough to avoid repeated warnings?
```

Core rule:

```text
visual_constraints protects the shot.
It does not create the shot.
```

## 11.11 Transition QC

For `SINGLE_SHOT_TRANSITION`, check:

```text
Does context define the shared transition logic?
Does state_1 establish the source clearly?
Does transition_trigger contain one trigger_type, one trigger_action, and one visual_bridge?
Does state_2 resolve into a clear destination?
Is the trigger physically or optically plausible?
Does the trigger bridge the two states without becoming a third state?
Is there no symbolic morphing chain?
Is there no second transition?
```

If the transition is only decorative, use a normal cut or separate shots instead.

## 11.12 Multipanel QC

For `SPLIT_SCREEN_MULTIPANEL`, check:

```text
Does context define the shared mechanism or comparison?
Is panel count limited to 2 or 3?
Does top-level composition_blocking define the panel arrangement?
Does each panel contain one simple visual idea?
Are panels readable without labels?
Is the camera locked and static?
Is lighting_atmosphere unified across panels?
Is color_grading unified across panels?
Is multipanel used for simultaneous relation, not time progression?
```

If panels represent temporal steps that need viewer breathing room, split into separate shots.


## 11.13 Final Pass

Before finalizing, ask:

```text
Does this prompt_raw map from the approved Optimized Shot Plan row?
Does it preserve the approved Group / Shot / Visual idea / Layout?
Is this shot concrete?
Is it physical?
Is it short-clip safe?
Is it visually readable?
Is it historically bounded?
Is it field-clean?
Is it non-glossy?
Is it free of readable text dependency?
Does it serve the narration cue without over-explaining it?
```

If not, revise before output.
