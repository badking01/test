# CHANNEL_VEO_PROMPT_RULES.md

## 1. File Role & Authority

This file defines **channel-level prompt rules for `shots[].prompt_raw`**.

It controls:

```text
prompt_raw structure
base SINGLE_SHOT field system
derived prompt variants
Veo 3 short-clip discipline
field ownership and field boundaries
global visual signature
field matrix composition
prompt variation pools
prompt_raw QC before JSON output
```

It does **not** control:

```text
episode thesis
narration
TTS
edit plan
civilization-specific meaning
country-specific guardrails
era-specific costume, hair, architecture, furniture, tools, weapons, scripts, writing systems, ritual accuracy
```

Those belong in:

```text
SESSION_THESIS.md
SESSION_CONTROL.md
EP_VISUAL_LOCK.md
ERA_LOCK.md
CHANNEL_WORKFLOW_CONTROL.md
```

Authority rule:

```text
CHANNEL_VEO_PROMPT_RULES.md wins only for prompt_raw structure and Veo 3 prompt technique.
SESSION_CONTROL.md wins for civilization/session-specific meaning and guardrails.
EP_VISUAL_LOCK.md wins for episode-specific visual identity.
ERA_LOCK.md wins for period accuracy.
CHANNEL_WORKFLOW_CONTROL.md wins for production workflow and human-readable planning fields.
```

Core boundary:

```text
This file defines the reusable prompt system.
Session and era files provide domain-specific overlays.
The final prompt_raw must merge these layers into clean visual fields without exposing the layer names.
```

---

## 2. Workflow Boundary

Active production flow:

```text
01_SCRIPT.md
→ PROJECT_STORYBOARD_PROMPT_ROOM
→ Phase A: Storyboard Planning
→ Optimized Shot Plan
→ Phase B: Prompt Production
→ projectbeat.json / shots[].prompt_raw
```

Phase A decides:

```text
Group
Shot
narration_cue
Visual idea
Layout
Min visual time
```

This file executes:

```text
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

Do not use this file to redesign the storyboard shot unless the user explicitly asks to revise the plan.

---

## 3. Prompt Raw Principle

`prompt_raw` is **not** the final Veo prompt.

It is a controlled shot-specific ingredient block that downstream tools or prompt adapters can later interpret into a full Veo 3 prompt.

```text
prompt_raw = structured visual ingredients
downstream prompt = later full Veo prompt or tool-specific conversion
```

Do not write a long finished cinematic paragraph inside `prompt_raw`.

Do not leave key visual decisions for downstream tools.

A valid `prompt_raw` must be clear enough that:

```text
a human can understand the intended shot
a downstream tool can convert it into a full Veo 3 prompt
Veo can generate a stable short clip
```

---

## 4. Base Prompt Unit: SINGLE_SHOT

`SINGLE_SHOT` is the **core prompt_raw unit**.

The 10 prompt fields are defined for `SINGLE_SHOT` first.

Derived variants inherit these field rules:

```text
SINGLE_SHOT_TRANSITION = SINGLE_SHOT + controlled two-state transition logic
SPLIT_SCREEN_MULTIPANEL = multiple SINGLE_SHOT-like panels in one simultaneous layout
```

Derived variants may add structure, but they must not redefine the meaning of the 10 fields.

Core SINGLE_SHOT rule:

```text
one scene state
one dominant space
one main subject or subject group
one camera behavior
one continuous action or controlled stillness
one readable visual idea
```

Use `SINGLE_SHOT` whenever the shot does not require a visible transition or simultaneous panel comparison.

---

## 5. Veo 3 Short-Clip Discipline

A generated clip should target:

```text
5–7 seconds
```

Hard compatibility limit:

```text
under 8 seconds
```

Core validation rule:

```text
one prompt_raw = one short visual unit
```

Do not treat one prompt like a full scene sequence.

Avoid:

```text
multiple location changes
multiple temporal turns
several sequential actions
complex camera travel through multiple spaces
symbolic morphing chains
```

Stability priority:

```text
one stable visual idea
one controlled camera behavior
one physical action or stillness
one resolved readable image
```

When in doubt, choose stability over ambition.

---

## 6. Approved prompt_raw Shot Types

Use exactly one of:

```text
SINGLE_SHOT
SINGLE_SHOT_TRANSITION
SPLIT_SCREEN_MULTIPANEL
```

Layout-to-prompt_raw mapping:

```text
SINGLE_SHOT → prompt_raw.shot_type = SINGLE_SHOT
SINGLE_SHOT_TRANSITION → prompt_raw.shot_type = SINGLE_SHOT_TRANSITION
SPLIT_SCREEN_2 → prompt_raw.shot_type = SPLIT_SCREEN_MULTIPANEL with 2 panels
SPLIT_SCREEN_3 → prompt_raw.shot_type = SPLIT_SCREEN_MULTIPANEL with 3 panels
MONTAGE_EDIT / MONTAGE_END → edit-level instruction outside prompt_raw
```

Do not invent additional `prompt_raw.shot_type` values.

`MONTAGE_EDIT` and `MONTAGE_END` are not production shot types for `prompt_raw`.

If a montage is needed, use one of these handling modes according to the active JSON schema:

```text
represent the montage as separate production shots
preserve the montage instruction in operator_notes
convert only the selected individual visual unit into prompt_raw
```

---

## 7. The 10 Prompt Fields

These 10 fields define the base `SINGLE_SHOT` unit:

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

Every field must carry only its own kind of information.

Do not collapse all visual information into one long style paragraph.

---

## 8. Field Ownership Map

| Field | Owns | Must not own |
|---|---|---|
| `context` | historical-spatial logic, visible place, shot-specific visual purpose | camera, color, texture, props list |
| `subject` | visible person, group, creature, object focus | lens, lighting, color palette |
| `camera` | viewer viewpoint, framing, lens, angle, movement, optical capture character | subject action, props, haze, color, material texture |
| `composition_blocking` | foreground/midground/background, thresholds, hierarchy, placement | camera movement, action sequence, color |
| `action` | movement or stillness inside the frame | camera movement, color, lighting setup |
| `props` | required visible objects | surface aging, lens behavior, color grade |
| `material_textures` | tactile surfaces, wear, physical material quality | lens, light source, color grade |
| `lighting_atmosphere` | light source, shadow behavior, air, haze, dust, mist, dimness | palette, lens, props, material hierarchy |
| `color_grading` | palette, saturation, contrast, black level, tonal treatment | light source, physical haze, camera, props |
| `visual_constraints` | guardrails that protect the shot from drift | creating the subject, action, thesis, layout, or field content |

Movement boundary:

```text
camera = viewer movement / frame behavior
action = movement inside the frame
transition_trigger = movement that bridges State 1 and State 2
```

Field cleanup rule:

```text
If a field repeats another field, remove the repetition.
If a field tries to do too many jobs, split the information into the correct fields.
If a field contains abstract thesis language, convert it into visible space, body, object, material, action, threshold, distance, camera framing, or social relation.
```

---

## 9. Global Visual Signature

The channel uses an **aged historical-documentary moving-image look**.

This is not a VHS, glitch, damaged tape, or fake retro-filter style.

The global look should feel:

```text
old
optical
matte
restrained
material
observational
historically grounded
slightly time-worn
softened by analog air
physically captured
non-glossy
```

It should not feel:

```text
clean modern AI video
glossy costume drama
fantasy / wuxia spectacle
modern commercial look
music-video stylization
heroic ruler worship
over-saturated palace spectacle
newly rendered CGI
VHS glitch
damaged tape artifact
heavy film scratch overlay
unstable distortion
fake retro filter
```

This global visual signature is distributed across fields.

Do **not** force the entire old-video style into one field.

### 9.1 Global Visual Signature Distribution

| Field | Receives this part of the global visual signature |
|---|---|
| `camera` | anamorphic lens aesthetic, restrained observational framing, subtle lens aberration, soft edge roll-off, controlled movement |
| `material_textures` | worn physical surfaces, dust, fabric wear, tarnished metal, rough handmade material, matte aging |
| `lighting_atmosphere` | vintage analog tape aesthetic expressed as subtle analog air particles that reduce AI sharpness; active location lighting logic only |
| `color_grading` | fixed base grade: deep desaturation, cold slate-greys, deep charcoal, low contrast |
| `visual_constraints` | keep analog softness subtle, realistic, and non-destructive; avoid clean digital sharpness, glossy finish, VHS glitch, heavy filter damage, destructive blur, film scratches, unstable distortion, and fake retro effects |

### 9.2 Global Camera Signature

`camera` carries the channel-level optical capture character.

Default camera signature:

```text
restrained observational framing, anamorphic lens aesthetic, subtle lens aberration, soft edge roll-off, controlled movement
```

`camera` may include:

```text
shot size
framing
camera angle
camera position
lens perspective
depth of field
camera movement
locked or moving frame
anamorphic lens aesthetic
subtle lens aberration
soft edge roll-off
```

`camera` must not include:

```text
subject action
props
light source
haze or dust as atmosphere
color palette
material wear
film grain as color treatment
```

### 9.3 Global Lighting Signature

`lighting_atmosphere` carries the channel-level light and air behavior.

Global channel contribution:

```text
subtle vintage analog tape aesthetic expressed as analog air particles, soft volumetric scattering, and reduced digital sharpness
```

Location lighting is conditional:

```text
INT shot → use indoor side-light logic
EXT shot → use outdoor diffused overcast logic
INT/EXT threshold shot → use controlled mixed-light logic only when both spaces are visibly present
```

Do not include both indoor and outdoor lighting logic by default.

`lighting_atmosphere` may include:

```text
active light source
active location light logic
shadow behavior
dimness
air quality
dust / haze / smoke / mist when physically appropriate
interior / exterior light relationship only when visible in the same frame
environmental brightness
soft analog air particles
```

It must not include:

```text
camera movement
lens distortion
color palette
props
material hierarchy
VHS glitch
tape damage
film scratches
heavy retro filter effects
```

### 9.4 Global Color Signature

`color_grading` carries the channel-level tonal treatment.

Fixed global base grade:

```text
deep desaturation, cold slate-greys, deep charcoal, low contrast
```

`color_grading` may include:

```text
deep desaturation
cold slate-greys
deep charcoal
low contrast
muted tonal range
reduced color intensity
controlled black level
restrained archival tonal treatment
```

It must not include:

```text
light source
physical haze
camera behavior
props
material surfaces
fake retro color bleed
damaged-tape color cast
heavy sepia filter
fake retro color cast
```

---

## 10. Field Matrix Composition Model

Every final `prompt_raw` field may be composed from layered sources.

This model applies to **all 10 fields**, not only `lighting_atmosphere` or `color_grading`.

Composition layers:

```text
Layer 1 — Global Channel Contract
Layer 2 — Global Visual Signature
Layer 3 — Session Domain Overlay
Layer 4 — Era / Period Overlay
Layer 5 — Social Tier / Role Overlay
Layer 6 — Location / Space Overlay
Layer 7 — Mechanism / Concept Overlay
Layer 8 — Shot Intent
```

Core rule:

```text
Layers are selective, not cumulative.
Use only the layers relevant to the active shot.
Do not dump all available layer data into a field.
```

The final field must be written as a clean visual instruction.

Do not expose layer names inside the final `prompt_raw`.

Bad final field:

```text
Layer 1 says old optical; Layer 4 says Qin; Layer 5 says elite; Layer 6 says record room.
```

Good final field:

```text
dim record-room interior with a protected clerical workspace, primitive low illumination, floating dust, and analog-softened air
```

### 10.1 Layer Responsibility

| Layer | Typical source | Role |
|---|---|---|
| Layer 1 — Global Channel Contract | `CHANNEL_VEO_PROMPT_RULES.md` | field meaning, field ownership, short-clip discipline |
| Layer 2 — Global Visual Signature | `CHANNEL_VEO_PROMPT_RULES.md` | channel-level optical, lighting, color, material softness |
| Layer 3 — Session Domain Overlay | `SESSION_CONTROL.md` | civilization/session meaning and guardrails |
| Layer 4 — Era / Period Overlay | `ERA_LOCK.md` | period accuracy, visual culture, materials, technology |
| Layer 5 — Social Tier / Role Overlay | `ERA_LOCK.md` or session tier files | class/role-specific body, access, objects, hierarchy |
| Layer 6 — Location / Space Overlay | `ERA_LOCK.md`, episode visual files, or shot location | architecture, light behavior, spatial logic |
| Layer 7 — Mechanism / Concept Overlay | beat/shot planning | what the shot makes visible |
| Layer 8 — Shot Intent | Optimized Shot Plan / projectbeat | exact subject, action, layout, and visual goal |

### 10.2 Field Source Ownership Matrix

| Field | Global / Channel | Era / Period | Tier / Role | Location / Space | Shot Intent |
|---|---|---|---|---|---|
| `context` | field contract for historical-spatial logic | era/world anchor | optional | required | required |
| `subject` | human/object visibility, realism, natural posture | costume, grooming, period body/object logic | required when social role matters | optional | required |
| `camera` | lens, framing, angle, movement, optical capture | usually none | usually none | optional framing influence | required |
| `composition_blocking` | foreground/midground/background grammar, hierarchy grammar | optional spatial tradition | hierarchy, access, rank | required | required |
| `action` | motion discipline, controlled movement/stillness | period gesture/labor/ritual vocabulary | role-specific behavior | optional | required |
| `props` | meaningful-object discipline | period object pool | access-controlled object pool | location object pool | required |
| `material_textures` | tactile realism, matte aging, anti-AI-smoothness | period material pool | material quality by class | surface identity | required |
| `lighting_atmosphere` | analog air particles, soft volumetric scattering | lighting technology | power/tier atmosphere | active INT/EXT/threshold lighting logic | required |
| `color_grading` | fixed base grade | period color/material family | optional status accent | optional | required |
| `visual_constraints` | Veo-safe guardrails | period guardrails | tier access guardrails | location guardrails | shot-specific risks |

### 10.3 Field Composition Matrix

| Field | Channel Contract | Visual Signature | Era / Period | Tier / Role | Location | Mechanism | Shot Intent |
|---|---|---|---|---|---|---|---|
| `context` | required | no | required | optional | required | required | required |
| `subject` | required | optional | required when period-specific | required when role matters | optional | optional | required |
| `camera` | required | required | usually none | usually none | optional | optional | required |
| `composition_blocking` | required | optional | optional | required when hierarchy matters | required | required | required |
| `action` | required | optional | optional | required when gesture/labor/ritual matters | optional | required | required |
| `props` | required | no | required | required when class/role matters | required | optional | required |
| `material_textures` | required | required | required | optional | required | optional | required |
| `lighting_atmosphere` | required | required | optional | optional | required | optional | required |
| `color_grading` | required | required | optional | optional | optional | optional | required |
| `visual_constraints` | required | required | required | optional | optional | optional | required |

### 10.4 Matrix Merge Rules

When composing a field:

```text
select only the layers that matter for this shot
choose visible specificity over encyclopedic detail
remove conflicting signals
avoid long lists
keep the field readable as one clean instruction
```

A field should feel specific, not crowded.

Do not dump entire pools, era notes, or session notes into a field.

### 10.5 Conditional Layer Rule

Some layers are mutually exclusive.

Example:

```text
INT lighting logic and EXT lighting logic are not both included by default.
```

Use controlled mixed logic only when the frame visibly contains both spaces.

Selection beats accumulation.

---

## 11. Field Contracts

### 11.1 `context`

Purpose:

```text
Defines where the shot exists and what historical-spatial logic it makes visible.
```

Required structure:

```text
context = [active historical-world anchor] + [visible spatial anchor] + [shot-specific visual logic]
```

Layer 1 — active historical-world anchor:

```text
What civilization, dynasty, era, or historical world does this shot belong to?
```

This value must come from:

```text
EP_VISUAL_LOCK.md
ERA_LOCK.md
SESSION_CONTROL.md
```

Do not hardcode civilization, dynasty, country, or era values inside this channel rule.

Layer 2 — visible spatial anchor:

```text
What kind of place are we seeing?
```

Use concrete visible spaces:

```text
court hall
administrative room
county office exterior
tax collection space
rural field
road outside a gate
ancestral hall
school room
granary threshold
fortified wall surface
ritual interior
```

Avoid vague spaces:

```text
ancient world
old society
power system
symbolic space
historical atmosphere
civilization memory
```

Layer 3 — shot-specific visual logic:

```text
What is this shot making visible?
```

The logic must be visible through:

```text
space
body position
object
material
action
threshold
distance
camera framing
social relation
```

### 11.2 `subject`

Purpose:

```text
Defines the main visible subject, subject group, or object focus.
```

The subject must be visible.

It may include:

```text
main person or group
social role
age impression when visually useful
body posture
visible emotional restraint
object focus when no human subject dominates
```

Do not use abstract thesis words as subject.

Bad:

```text
power
elite ecosystem
legitimacy
historical pressure
```

Good:

```text
a seated clerk handling sealed packets at a low work surface
a line of villagers carrying grain sacks toward a collection point
a younger outsider standing lower at the threshold of an elite interior
```

### 11.3 `camera`

Purpose:

```text
Defines how the viewer sees the shot and carries the channel’s global optical capture character.
```

Owns:

```text
shot size
framing
camera angle
camera position
lens perspective
depth of field
camera movement
anamorphic lens aesthetic
subtle lens aberration
soft edge roll-off
```

Does not own:

```text
subject movement
light source
haze / dust in air
palette
material wear
props
```

Default style:

```text
restrained observational framing, controlled movement, anamorphic lens aesthetic, subtle lens aberration, soft edge roll-off
```

### 11.4 `composition_blocking`

Purpose:

```text
Defines where bodies, objects, thresholds, and power relationships are placed inside the frame.
```

May include:

```text
foreground
middle ground
background
inside / outside
threshold
above / below
platform
near / far
center / edge
ranked bodies
blocked access
open passage
```

Blocking should reveal relation, not decorate the scene.

Good:

```text
foreground holds the low work surface; middle ground shows clerks working; deep background holds the distant authority space
```

### 11.5 `action`

Purpose:

```text
Defines what visible subjects, objects, materials, or environment do inside the frame.
```

For `SINGLE_SHOT`, use:

```text
one concrete physical action
or one controlled stillness
```

Good:

```text
hands slowly secure an official packet
grain pours into a measuring basket
a worker lowers a heavy sack onto the ground
the figures remain almost still while only fabric edges shift
dust drifts slowly through side light
```

Do not place camera movement here.

For `SINGLE_SHOT_TRANSITION`, action is split into:

```text
state_1.action
transition_trigger.trigger_action
state_2.action
```

### 11.6 `props`

Purpose:

```text
Defines required physical objects that make the shot readable.
```

Props should support visual meaning, not decorate the frame.

Use only the objects the shot needs.

Do not list every historically possible object.

When the meaning can be shown through direct visible event, do not default to documents.

Good:

```text
grain sacks, measuring basket, low receiving table
sealed packets, low work surface, administrative marker
field boundary stone, measuring rope, muddy field edge
ritual objects, formal cloth, family hall furniture
```

### 11.7 `material_textures`

Purpose:

```text
Defines tactile surface identity, physical age, and material quality.
```

May include:

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
plain functional garments, worn desks, handled administrative surfaces, matte wood
aged fine woven fabric, protected dark wood, carefully maintained stone, restrained inner-room surfaces
```

Do not put lighting or color grading here.

### 11.8 `lighting_atmosphere`

Purpose:

```text
Defines how light and air behave inside the shot.
```

Owns:

```text
active light source
active location light logic
shadow behavior
air behavior
dust, haze, smoke, mist, humidity when physically appropriate
diffusion
dimness
environmental brightness
soft analog air particles
```

Does not own:

```text
lens distortion
color palette
props
material texture
social-class material hierarchy
VHS glitch
tape damage
film scratches
heavy retro filter effects
```

Layering pattern:

```text
[Layer 1 - Global Channel Atmosphere]
+ [Layer 4 - Era / Period Lighting Logic, if relevant]
+ [Layer 5 - Tier / Role Atmosphere, if relevant]
+ [Layer 6 - Active Location Lighting Logic, required]
+ [Layer 8 - Shot Mood, if needed]
```

Layer 1 global contribution:

```text
subtle vintage analog tape aesthetic expressed as analog air particles, soft volumetric scattering, and reduced digital sharpness
```

Layer 4 and Layer 5 belong to the active `ERA_LOCK.md` or session overlay files.

Layer 6 location selection:

```text
INT shot → indoor side-light logic
EXT shot → outdoor diffused overcast logic
INT/EXT threshold shot → controlled mixed-light logic only if both spaces are visible in one coherent frame
```

Do not combine indoor and outdoor lighting logic by default.

Good INT pattern:

```text
directional side-light from a narrow opening, deep interior shadows, weak practical illumination at the focal workspace, floating dust softened by analog air particles
```

Good EXT pattern:

```text
diffused overcast daylight, soft shadow edges, subdued environmental brightness, outdoor haze softened by analog air particles
```

Good threshold pattern:

```text
dark interior foreground with controlled exterior spill at the doorway, both spaces unified by subtle analog air particles
```

### 11.9 `color_grading`

Purpose:

```text
Defines the final tonal treatment of the image.
```

Owns:

```text
palette
saturation
contrast
black level
shadow tone
warmth / coldness
archival tonal treatment
```

Does not own:

```text
light source
physical haze
camera behavior
props
material surfaces
action
fake retro color bleed
damaged-tape color cast
heavy sepia filter
fake retro color cast
```

Layering pattern:

```text
[Layer 1 - Global Fixed Base Grade]
+ [Layer 4 - Period Color / Material Family, if relevant]
+ [Layer 5 - Optional Tier / Status Accent, if relevant]
+ [Layer 8 - Shot Tonal Emphasis, if needed]
```

Layer 1 fixed global base grade:

```text
deep desaturation, cold slate-greys, deep charcoal, low contrast
```

Layer 4 and Layer 5 belong to the active `ERA_LOCK.md` or session overlay files.

Good base pattern:

```text
deep desaturation, cold slate-greys, deep charcoal shadows, low contrast, restrained archival tonal treatment
```

Good layered pattern:

```text
deep desaturation, cold slate-greys, deep charcoal shadows, low contrast, with only restrained period-specific material accents from the active era lock
```

### 11.10 `visual_constraints`

Purpose:

```text
Defines Veo-safe physical and optical guardrails.
```

`visual_constraints` protects the shot.

It does not create the shot.

Use positive visual-state language.

Good:

```text
written surfaces remain unreadable, reduced to blurred ink texture, partial marks, blank worn surfaces, or abstract weathered patterning
clothing, grooming, objects, architecture, tools, furniture, and materials remain historically consistent with the active session, episode visual lock, or era lock
all materials remain matte, aged, tactile, and non-glossy
```

Avoid simple negative-list style:

```text
no text, no logo, no modern objects, no fantasy, no bad anatomy
```

Better:

```text
all signboards are plain weathered surfaces without visible writing; all materials remain matte, aged, and non-glossy; all objects belong to the active historical context
```

Keep this field compact and risk-focused.

---

## 12. SINGLE_SHOT Template

Use when the approved Layout is:

```text
SINGLE_SHOT
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

Validation:

```text
one scene state
one dominant space
one main subject or subject group
one camera behavior
one continuous action or controlled stillness
one readable visual idea
all 10 fields field-clean
under-8-second compatible
```

---

## 13. Derived Prompt Variant: SINGLE_SHOT_TRANSITION

`SINGLE_SHOT_TRANSITION` is a derived variant of `SINGLE_SHOT`.

Use it only when one generated clip must move from one scene state to another through one clear trigger.

Maximum structure:

```text
State 1 → one transition trigger → State 2
```

Use only when:

```text
the transition itself is the visual idea
the before/after contrast must be felt inside one continuous clip
State 1 and State 2 are both simple enough to read quickly
there is only one transition trigger
the destination state resolves clearly
the whole clip remains under 8 seconds
```

Do not use it for:

```text
three or more scene states
two separate transitions
full scene progression
decorative transition with no meaning
```

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

Top-level fields:

```text
context = shared transition logic
subject = recurring visible anchor when applicable
camera = overall camera behavior across the transition
lighting_atmosphere = shared or transitional light/atmosphere logic
color_grading = unified tonal treatment
visual_constraints = shared guardrails
```

State fields:

```text
state_1.context = source setting + source visual logic
state_1.composition_blocking = spatial arrangement before trigger
state_1.action = starting action
state_1.props = required props in State 1
state_1.material_textures = surfaces specific to State 1

transition_trigger.trigger_type = transition device
transition_trigger.trigger_action = physical or camera action causing the transition
transition_trigger.visual_bridge = how the frame is covered, blurred, wiped, swallowed, or shifted

state_2.context = destination setting + resolved visual logic
state_2.composition_blocking = spatial arrangement after trigger
state_2.action = resolved action or controlled stillness
state_2.props = required props in State 2
state_2.material_textures = surfaces specific to State 2
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
material_match_cut
```

Core rule:

```text
The trigger is not a third state.
The trigger is the bridge between State 1 and State 2.
```

---

## 14. Derived Prompt Variant: SPLIT_SCREEN_MULTIPANEL

`SPLIT_SCREEN_MULTIPANEL` is a derived layout variant of `SINGLE_SHOT`.

Use it only when several ideas must be understood together at the same time.

It is for:

```text
simultaneous comparison
parallel social layers
compressed mechanism reading
cause-effect pair
two-sided contrast
three-part mechanism
```

It is not for:

```text
time progression
montage edit
three sequential scene states
panel-by-panel hidden sequences
```

Panel count:

```text
SPLIT_SCREEN_2 → 2 panels
SPLIT_SCREEN_3 → 3 panels
never more than 3 panels
```

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

For 2-panel shots, remove:

```text
panel_3_scene
```

Top-level fields:

```text
context = shared mechanism, comparison, or relationship
camera = locked flat diptych or triptych framing
composition_blocking = overall panel arrangement
shared_material_textures = shared tactile logic across panels when useful
lighting_atmosphere = unified lighting/atmosphere across all panels
color_grading = unified tonal treatment across all panels
visual_constraints = shared guardrails
```

Panel fields:

```text
panel_x_scene.context = concrete local setting + panel-specific visual logic
panel_x_scene.subject = visible subject or subject group
panel_x_scene.composition_blocking = spatial arrangement inside panel
panel_x_scene.action = one simple action or controlled stillness
panel_x_scene.props = required props inside panel
panel_x_scene.material_textures = panel-specific surfaces if different from shared material logic
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

## 15. Prompt Variation Pools

Prompt variation pools are reusable option banks.

They help avoid repetitive camera, spatial arrangement, action, material, transition, and multipanel choices while keeping every shot coherent.

Pools are not JSON schemas.

Pools are not output fields.

When writing `prompt_raw`:

```text
1. Identify the shot_type.
2. Identify the visual job of the shot.
3. Choose one suitable option from each relevant pool.
4. Adapt the option to the shot.
5. Write only the adapted final choice into the correct prompt_raw field.
6. Do not include unused pool options.
```

Core rule:

```text
Pools provide controlled variation.
prompt_raw records the final selected choice.
```

Do not dump a full pool into a shot.

### 15.1 Pool-to-field mapping

```text
Camera Pools → camera
Spatial Arrangement Pools → composition_blocking
Action / Micro-Motion Pools → action
Material Texture Pools → material_textures or shared_material_textures
Transition Trigger Pools → transition_trigger
Multipanel Arrangement Pools → composition_blocking for SPLIT_SCREEN_MULTIPANEL
```

Do not mix fields.

### 15.2 Camera Pools

Camera pools answer:

```text
How does the viewer see the shot?
```

They must not answer:

```text
What does the subject do?
What is the lighting?
What is the color grade?
What materials appear?
```

Indoor authority / institutional space:

```text
locked medium-wide observational frame from a straight formal axis, anamorphic lens aesthetic, subtle lens aberration, soft edge roll-off
static frontal composition from slightly below eye level, controlled depth of field, soft optical edge falloff
slow controlled push-in from a wide frame toward the main subject, vintage lens softness
side-angle frame through a doorway or threshold, shallow depth of field, restrained optical distortion
fixed wide frame with foreground, middle ground, and deep background clearly separated
```

Outdoor road / field / public space:

```text
wide observational frame with distant figures moving through the landscape, soft edge roll-off
locked wide frame from road level, with long lateral depth across the scene
slow controlled lateral track following one direction of movement, restrained and non-flashy
medium-wide roadside frame with the subject crossing from foreground to middle ground
static long-lens observational frame compressing distance between people and terrain
```

Macro / material detail:

```text
macro close-up on hands and object contact, shallow depth of field, old optical softness
fixed close-up on one material surface with minimal movement
tight observational frame on a single repeated gesture
close detail shot from a low side angle
static insert frame isolating one object against a simple background
```

Ritual / formal body arrangement:

```text
symmetrical wide frame centered on the main ritual axis
static medium-wide frame with ranked bodies arranged by distance
low frontal frame emphasizing elevated or seated authority
side-angle frame showing one figure lower, farther, or outside the threshold
locked wide frame preserving formal spacing between groups
```

Transition-compatible camera:

```text
locked frame until the trigger enters the lens
static composition interrupted by one full-frame occlusion
single sudden whip-pan movement used only as the transition trigger
slow push-in ending at the moment the trigger covers the frame
fixed side frame where a passing body or object wipes the lens
```

### 15.3 Spatial Arrangement Pools

Authority distance:

```text
foreground holds working objects while authority sits distant in deep background
main authority figure is elevated while others stand lower in ordered ranks
viewer looks through layers of officials before reaching the central authority
subject remains far from the raised platform, blocked by desks and attendants
frame separates command space above from laboring space below
```

Threshold exclusion:

```text
one figure stands outside the threshold while accepted figures occupy the inner room
doorway divides exposed exterior space from protected institutional interior
blocked subject remains at the edge of frame while the center belongs to insiders
closed gate or door separates the subject from the room of decision
```

Administrative layering:

```text
foreground shows administrative objects, middle ground shows clerks working, background holds authority or storage
low work surface anchors the frame while bodies gather around it in controlled hierarchy
working desk sits between society and authority as visual barrier or channel
documents and tools remain supporting props while body position shows the mechanism
```

Labor / extraction arrangement:

```text
laboring bodies occupy the foreground while officials or record keepers sit farther back
grain or goods move from exposed public space toward controlled institutional space
workers stand low and crowded while measuring tools occupy the center
burdened subject bends while the receiving side remains upright
route of movement leads from field or road into office, gate, or storage
```

Ritual / social incorporation:

```text
elders occupy the deep interior while the entering figure remains lower near the threshold
two groups face one another across ritual objects in the center
younger figure is positioned below or behind senior figures in formal order
composition moves from outsider edge toward inner-room belonging
formal spacing shows who is accepted, who witnesses, and who waits
```

### 15.4 Action / Micro-Motion Pools

Controlled stillness:

```text
figures remain almost still while only small fabric edges shift
hands pause above the object before completing the gesture
bodies hold formal posture while the room stays quiet
one person waits without moving as others continue the procedure
scene holds in controlled silence with only minimal environmental movement
```

Administrative micro-action:

```text
hands slowly secure an official packet
clerk moves one object across a low work surface
administrative marker is placed beside a record object
messenger presents a sealed item to a seated official
record object is passed from one hand to another through the office
```

Labor / extraction micro-action:

```text
grain pours slowly into a measuring basket
worker lowers a heavy sack onto the ground
hands lift a loaded basket toward a receiving table
cart wheel turns slowly through mud
villagers move in a slow line toward the collection point
```

Ritual / social status micro-action:

```text
younger figure bows once before seated elders
hands arrange ritual objects with slow restraint
figure steps from the threshold into the inner room
elders remain seated while the newcomer waits lower before them
two groups hold formal posture across ritual objects
```

Environmental motion:

```text
dust drifts slowly through the room
cloth edges barely shift in the air
smoke or steam moves gently across the background
loose straw or road dust moves across the ground
hanging object sways slightly while people remain still
```

### 15.5 Material Texture Pools

These are channel-level social-material patterns.

Civilization-specific props, costumes, grooming, architecture, ritual objects, and record materials belong in:

```text
SESSION_CONTROL.md
EP_VISUAL_LOCK.md
ERA_LOCK.md
```

Laboring / poor / displaced class:

```text
coarse natural cloth, worn hems, rough wood, mud, work-marked hands, crowded exposed space
patched fabric, damp ground, weathered tools, rough baskets, unstable footing
worn outer garments, simple carrying objects, exposed road or field materials
rough fibers, cracked wood, wet earth, heavy sacks, unprotected hands
```

Administrative / clerical / institutional class:

```text
plain functional garments, worn desks, handled administrative surfaces, matte wood, orderly storage
muted practical cloth, aged work surfaces, institutional furniture, restrained working space
simple official materials, handled record objects, worn storage surfaces, formal working posture
aged timber, low work surfaces, corded or sealed objects where historically appropriate
```

Privileged / landed / educated class:

```text
aged fine woven fabric, preserved furniture, controlled empty space, dark maintained interior surfaces
finer matte textiles, worn but protected wood, formal seating distance, restrained household order
old wealth expressed through material preservation, inner-room access, slower posture, and social distance
carefully maintained stone or wood, protected shelves, formal cloth, restrained elite surfaces
```

Court / ruling / ceremonial class:

```text
matte ceremonial textiles, raised position, formal spatial order, worn stone or timber surfaces
large institutional architecture, ranked arrangement, controlled distance, restrained ceremonial material
elevated placement, deep interior axis, disciplined body hierarchy, aged high-status surfaces
formal cloth, old polished-by-use wood, heavy institutional floor materials, controlled ceremonial spacing
```

Religious / ritual / scholarly authority:

```text
aged ritual surfaces, simple formal textiles, handled teaching objects, preserved interior space
matte ceremonial objects, worn wooden interiors, restrained seating order, quiet scholarly materials
protected shelves, ritual table surfaces, aged paper or record textures where historically appropriate
dark interior wood, disciplined object placement, formal cloth, quiet institutional surfaces
```

Military / command class:

```text
worn leather, matte metal, rough command surfaces, transport materials, disciplined storage
weathered armor surfaces, practical cloth, hard road materials, handled weapons or command objects where historically appropriate
heavy carts, rope, wood, mud, metal fittings, supply objects, functional military order
restrained command materials, practical belts, worn footwear, rough campaign surfaces
```

### 15.6 Transition Trigger Pools

Use only for `SINGLE_SHOT_TRANSITION`.

Lens occlusion / body wipe:

```text
a figure passes close to the camera and fully occludes the frame before the destination appears
a sleeve or cloth sweeps directly across the lens and wipes the source scene away
a large object crosses the foreground until the frame is fully covered
a door or gate surface passes across the lens and reveals the new state after clearing
```

Motion blur / whip pan:

```text
one sudden whip-pan creates full-frame motion blur before landing on the destination state
camera snaps sideways once, using motion blur as the only transition bridge
fast lateral camera sweep wipes the source space into the destination space
```

Smoke / dust / darkness:

```text
dense dust fills the frame and clears into the destination state
smoke swallows the source scene before thinning into the new space
frame falls into darkness for a brief moment before the destination appears
steam or powder covers the lens and resolves into the second state
```

Material match cut:

```text
dark cloth surface fills the frame and clears into another dark surface in the destination
rough wooden surface passes across the lens and resolves into a different wooden structure
stone surface fills the frame before revealing another stone environment
close material texture becomes the visual bridge between two institutional spaces
```

### 15.7 Multipanel Arrangement Pools

Two-panel contrast / cause-effect:

```text
locked diptych with left panel showing source condition and right panel showing consequence
locked diptych with one panel showing authority and the other showing social cost
locked diptych with one panel showing command and the other showing extraction
locked diptych with one panel showing privilege and the other showing exclusion
```

Three-panel mechanism:

```text
locked triptych showing source, conversion process, and result
locked triptych showing demand, extraction, and surplus
locked triptych showing land, education, and office as connected social stages
locked triptych showing outsider, incorporation, and new elite position
```

Parallel social layers:

```text
locked triptych showing court, office, and village as simultaneous layers
locked triptych showing family, school, and bureaucracy as connected institutions
locked triptych showing ritual, record, and office as parallel forms of authority
```

---

## 16. Visual Preset Library

Visual presets are channel-level defaults for reusable image treatment.

They must not include civilization-specific props, era costume, architecture, grooming, weapons, rituals, or writing systems.

### 16.1 Realistic Documentary Lighting

Indoor:

```text
vintage analog haze, weak side light entering from a small opening, deep natural shadows, dim interior air, restrained observational stillness
```

Outdoor:

```text
heavy overcast exterior light, soft shadow edges, subdued environmental brightness, restrained air movement, no direct heroic sunlight
```

Mixed indoor / outdoor:

```text
dim interior side light and overcast exterior light unified by low-contrast documentary atmosphere, restrained shadow behavior, and consistent visual stillness
```

### 16.2 Realistic Documentary Color

Default dark earth:

```text
desaturated muddy browns, cold slate-grays, dark charcoal earth tones, restrained bronze shadows, low contrast, faded archival tone
```

Cold institutional gray:

```text
desaturated gray-brown palette, cold ash-gray midtones, charcoal shadows, muted wood and stone tones, restrained contrast
```

### 16.3 Rough Historical Explainer Animation

Use rough animation for abstract mechanisms that are difficult to show through realistic footage.

Allowed shot types:

```text
SINGLE_SHOT
SPLIT_SCREEN_MULTIPANEL
```

Do not create a separate animation `shot_type`.

Rough animation style:

```text
minimalist 2D ink sketch
aged parchment surface
carbon-black linework
dark sepia wash
flat graphic perspective
limited jerky motion
archival explainer insert
```

Rough animation must not look like:

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

Rough animation routes style through:

```text
material_textures
lighting_atmosphere
color_grading
visual_constraints
```

---

## 17. Social Material Hierarchy Rule

Social position must be readable through:

```text
material quality
spatial access
body position
distance from authority
posture
preservation
control of space
```

Do not give every class the same poor, muddy, rough texture language.

Dark documentary style does not mean every subject must look poor.

Higher-status spaces can remain:

```text
dark
aged
matte
restrained
historically grounded
```

while still reading as higher status.

### 17.1 Social hierarchy affects these fields

```text
subject
composition_blocking
props
material_textures
action
```

It should usually affect lighting or color only after the above fields already show hierarchy.

### 17.2 Status patterns

Poor / laboring / displaced:

```text
exposed
worn
crowded
burdened
physically marked by work
waiting outside
blocked from protected space
```

Administrative / clerical / institutional:

```text
plain
functional
ordered
handled
procedural
positioned between authority and society
```

Privileged / landed / educated:

```text
preserved
protected
spacious
controlled
slow
inner-room access
others approach them
```

Court / ruling / ceremonial:

```text
elevated
ranked
distant
ceremonial
institutional
approached through layers
```

Religious / ritual / scholarly authority:

```text
ordered
restrained
preserved
formal
interpretive
teacher or elder deeper inside
```

Military / command:

```text
functional
hard-worn
disciplined
logistical
controlled
ranked readiness
```

### 17.3 Higher status rule

High status should feel:

```text
old
restrained
protected
controlled
preserved
```

Not:

```text
shiny
glossy
romantic
fantasy-luxury
```

### 17.4 Low status rule

Low status should feel:

```text
exposed to pressure
burdened
blocked
crowded
physically constrained
```

Not theatrically miserable by default.

### 17.5 Session and era boundary

This section is channel-level.

It defines reusable social-material reading.

It does not define specific historical costumes, hairstyles, architecture, props, weapons, rituals, or record materials.

Those belong in:

```text
SESSION_CONTROL.md
EP_VISUAL_LOCK.md
ERA_LOCK.md
```

---

## 18. Document / Record Discipline

Documents, records, books, ledgers, seals, and archives should not become the default solution for every abstract idea.

Use direct visible events first when possible.

Direct visual examples:

```text
tax burden → grain submitted, measured, carried, stored
land control → boundary stone, measuring rope, people standing on field edge
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

Written surfaces must remain unreadable.

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

Core rule:

```text
Written surfaces can carry texture, age, and institutional weight.
They must not carry readable information.
```

---

## 19. Visual Constraints Presets

Use `visual_constraints` to protect:

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

Do not use `visual_constraints` to explain the thesis or replace missing fields.

### 19.1 Realistic Documentary Visual Constraints

```text
Written surfaces remain unreadable, reduced to blurred ink texture, partial marks, blank worn surfaces, or abstract weathered patterning. Clothing, grooming, objects, architecture, tools, furniture, and materials remain historically consistent with the active session, episode visual lock, or era lock. All surfaces remain matte, aged, worn, tactile, and non-glossy. The image keeps subtle old-video imperfections, softened optical resolution, vintage lens rendering, slight atmospheric softness, muted shadow detail, and low contrast without heavy fake retro filter effects.
```

### 19.2 Rough Animation Visual Constraints

```text
All written, mapped, diagrammed, labeled, or symbolic surfaces appear only as unreadable ink strokes, blank shapes, rough marks, or abstract chart-like patterning. The animation remains flat, hand-inked, paper-textured, monochrome-sepia, and archival. Motion stays slow, minimal, jagged, and puppet-like, with limited frame-by-frame shifts on a static aged parchment surface.
```

### 19.3 Transition Visual Constraints

Use together with realistic or rough animation constraints:

```text
The transition remains a single clear visual bridge between two scene states. The frame is covered, blurred, wiped, swallowed, or kinetically shifted by one physical or camera trigger only. State 1 and State 2 remain readable as two distinct states. The trigger does not become a third scene. No additional hidden transition, morphing chain, symbolic transformation, or extra environment appears between the two states.
```

### 19.4 Multipanel Visual Constraints

Use together with realistic or rough animation constraints:

```text
All panels remain visually simple, readable at a glance, and unified by the same channel-level visual treatment. Panel boundaries stay clean and stable. No readable labels, subtitles, arrows, logos, or written explanations appear inside the panels. Each panel contains one simple visual idea only. The multipanel layout remains static, controlled, and non-chaotic.
```

---

## 20. Layout Technical Validation

This section validates the approved Layout from Phase A.

It does not perform storyboard splitting, merging, or layout selection by default.

### 20.1 SINGLE_SHOT validation

Check:

```text
one scene state
one dominant space
one main subject or subject group
one camera behavior
one continuous action or controlled stillness
one readable visual idea
```

If the approved shot requires multiple spaces, several action stages, or a temporal chain, the prompt_raw is overloaded.

### 20.2 SINGLE_SHOT_TRANSITION validation

Check:

```text
State 1 → one transition trigger → State 2
one source state
one destination state
one physical or optical trigger
one resolved destination
under-8-second compatibility
```

The trigger must not become a third state.

There must be no second transition.

### 20.3 SPLIT_SCREEN_MULTIPANEL validation

Check:

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

It does not validate hidden time progression.

### 20.4 Overload check

Overload signs:

```text
one prompt_raw describes three or more locations
one prompt_raw contains multiple temporal turns
one prompt_raw asks for several sequential actions
one panel contains a hidden sequence
one transition contains more than one trigger
one SINGLE_SHOT tries to behave like a montage
```

If overloaded, do not solve the problem by adding more text.

Use one of these responses:

```text
simplify the prompt_raw to match the approved Layout
ask to revise the Optimized Shot Plan
split into separate production shots when Phase A is revised
move montage behavior to operator_notes when the schema allows it
```

---

## 21. Prompt Raw QC Checklist

Before outputting any projectbeat JSON containing `prompt_raw`, check every shot.

### 21.1 Storyboard mapping

```text
Does the shot come from an approved Optimized Shot Plan row?
Does it preserve Group identity?
Does it preserve Shot identity?
Does it preserve the approved narration_cue?
Does it preserve the approved Visual idea?
Does it follow the approved Layout?
Does prompt_raw avoid creating new shot splits?
Does prompt_raw avoid merging shots across groups?
```

### 21.2 Schema

```text
Does prompt_raw use one approved shot_type only?
Does it use the correct template for that shot_type?
Are all required fields present?
Does it use only fields defined by the selected template?
Is prompt_raw structured visual source material, not a finished cinematic paragraph?
```

### 21.3 Short-clip safety

```text
Is the generated clip under-8-second compatible?
Does it target about 5–7 seconds when possible?
Is it one short visual unit?
Does it avoid full scene progression?
Does it avoid multiple location changes?
Does it avoid multiple temporal turns?
```

### 21.4 Field boundary

```text
Does camera contain only viewer viewpoint, framing, lens perspective, optical capture character, and camera movement?
Does action contain only subject, object, material, or environmental movement inside the frame?
Is transition-causing movement placed in transition_trigger?
Does material_textures describe surfaces and material quality only?
Does lighting_atmosphere describe light and air only?
Does color_grading describe palette, saturation, contrast, and tonal treatment only?
Does visual_constraints protect the shot instead of creating it?
```

### 21.5 Physical readability

```text
Can the viewer understand the shot without readable text?
Is the subject visible?
Is the action visible?
Are props meaningful rather than decorative?
Does composition show relation, hierarchy, access, or exclusion?
Does the shot avoid abstract thesis language inside technical fields?
```

### 21.6 Social material hierarchy

```text
Can the viewer tell who has more access?
Can the viewer tell who waits and who is received?
Can the viewer tell who works and who commands?
Can the viewer tell who is exposed and who is protected?
Can the viewer tell who belongs inside and who remains outside?
Does higher status remain restrained instead of glossy?
Does low status remain material instead of melodramatic?
```

If hierarchy is unclear, revise first:

```text
subject
composition_blocking
props
material_textures
action
```

before changing lighting or color.

### 21.7 Historical authority

```text
Does the shot follow the active SESSION_CONTROL.md?
Does it follow the active EP_VISUAL_LOCK.md?
If an era is assigned, does it follow ERA_LOCK.md?
Does it avoid civilization-specific details not supported by active files?
Does it avoid mixing incompatible eras inside one shot?
```

### 21.8 Visual style

```text
Does the image preserve the aged historical-documentary visual signature?
Does camera carry optical capture character without stealing lighting or color jobs?
Does lighting_atmosphere carry light and air without stealing color grading?
Does color_grading carry palette and contrast without stealing lighting?
Does realistic footage avoid clean modern AI video and glossy costume drama?
Does rough animation remain flat, hand-inked, parchment-based, and non-corporate?
```

### 21.9 Final pass

```text
Does this prompt_raw map from the approved Optimized Shot Plan row?
Is this shot concrete?
Is it physical?
Is it short-clip safe?
Is it visually readable?
Is it historically bounded?
Is it field-clean?
Is it non-glossy?
Is it free of readable text dependency?
Does it serve the narration_cue without over-explaining it?
```

If not, revise before output.
