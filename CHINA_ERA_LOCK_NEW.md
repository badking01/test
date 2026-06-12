# CHINA_ERA_LOCK_NEW.md

## 1. File Role & Authority

This file is the **China Session visual-era overlay matrix**.

It provides China-specific visual data for:

```text
era / period accuracy
social tier / role embodiment
location / space logic
costume / hair / grooming
architecture / furniture
props / tools / weapons / transport
record materials / writing surfaces
ritual objects / social spaces
material textures
lighting overlays
color-family overlays
anti-era-mixing guardrails
```

This file supports:

```text
projectbeat JSON
shots[].prompt_raw
the 10 prompt fields defined in CHANNEL_VEO_PROMPT_RULES_NEW.md
```

This file is not:

```text
a script file
a TTS file
a prompt_raw schema file
a replacement for CHANNEL_VEO_PROMPT_RULES_NEW.md
a replacement for CHINA_SESSION_CONTROL.md
```

Authority rule:

```text
CHANNEL_VEO_PROMPT_RULES_NEW.md defines field contracts, global visual signature, shot types, prompt_raw mechanics.
CHINA_SESSION_CONTROL.md defines China Session thesis, meaning, and guardrails.
CHINA_ERA_LOCK_NEW.md provides China-specific visual overlays by era, tier, and location.
```

Conflict rule:

```text
For prompt_raw schema and field mechanics → use CHANNEL_VEO_PROMPT_RULES_NEW.md.
For China thesis and narrative meaning → use CHINA_SESSION_CONTROL.md.
For era-specific visual culture → use CHINA_ERA_LOCK_NEW.md.
```

---

## 2. Relationship With CHANNEL_VEO_PROMPT_RULES_NEW

`CHANNEL_VEO_PROMPT_RULES_NEW.md` defines:

```text
the 10 prompt fields
field ownership
global visual signature
field matrix composition model
SINGLE_SHOT as base prompt unit
derived variants
Veo 3 short-clip discipline
```

This file provides external overlay data for those fields:

```text
Layer 3 — China Session Global Overlay
Layer 4 — Era / Period Overlay
Layer 5 — Social Tier / Role Overlay
Layer 6 — Location / Space Overlay
```

Final field composition:

```text
Final prompt_raw field
= CHANNEL field contract
+ CHANNEL global visual signature
+ China Session Global Overlay
+ selected Era Profile
+ selected Tier / Role Overlay
+ selected Location / Space Overlay
+ Shot Intent
```

The final `prompt_raw` must not expose layer names.

---

## 3. China Session Global Overlay

This overlay applies across all China eras unless a specific era profile says otherwise.

### 3.1 context overlay

China Session context should make visible:

```text
court authority
bureaucratic mediation
lineage continuity
ritual legitimacy
landholding
tax extraction
record keeping
education / examination / recruitment
military logistics
road and gate control
local elite access
social hierarchy through space
```

Avoid:

```text
generic ancient China
generic imperial China
generic Asian setting
mystical China
fantasy dynasty
```

### 3.2 subject overlay

Subjects should read through:

```text
social role
rank
access
posture
clothing logic
grooming
body distance from authority
protected vs exposed position
```

### 3.3 camera overlay

Use `CHANNEL_VEO_PROMPT_RULES_NEW.md`.

No China-specific camera override by default.

### 3.4 composition_blocking overlay

China Session blocking should show:

```text
inside vs outside
threshold access
ranked rows
raised vs lowered position
elder vs junior distance
official vs commoner separation
desk / gate / table as mediation point
protected interior vs exposed exterior
```

### 3.5 action overlay

Prefer visible mechanisms:

```text
receiving orders
copying records
sealing packets
measuring grain
carrying tax goods
bowing before elders
entering a household threshold
standing before officials
guarding a gate
moving supplies
teaching / studying
registering names or goods without readable text
```

### 3.6 props overlay

Props should be:

```text
era-compatible
role-compatible
location-compatible
visually necessary
not decorative clutter
```

Written surfaces must stay unreadable.

### 3.7 material_textures overlay

Use:

```text
matte cloth
aged wood
rammed earth
stone / brick when era-appropriate
bamboo / wood / paper records depending on era
bronze / iron / lacquer only when era-compatible
dust, wear, handling marks
```

### 3.8 lighting_atmosphere overlay

Do not override channel global analog-air signature.

China lighting overlays provide:

```text
period lighting technology
tier / role atmosphere
location light behavior
```

Location rule:

```text
INT → indoor side-light logic
EXT → outdoor diffused overcast logic
INT/EXT threshold → controlled mixed-light logic only if both spaces are visible
```

### 3.9 color_grading overlay

Do not override the channel base grade:

```text
deep desaturation
cold slate-greys
deep charcoal
low contrast
```

Era profiles may add restrained material-color accents only when physically present.

### 3.10 visual_constraints overlay

Always protect against:

```text
wrong dynasty costume
wrong hairstyle
wrong furniture height
wrong record material
wrong weapon technology
readable Chinese text
wuxia / xianxia / fantasy drift
modern objects
glossy costume-drama drift
```

---

## 4. Universal China Guardrails

### 4.1 Anti-generic China rule

Use active era anchors from the selected era profile.

Do not use unsupported anchors:

```text
ancient China
old Chinese world
pre-modern Chinese setting
generic imperial China
generic Asian dynasty
```

### 4.2 Anti-readable-text rule

Written surfaces must appear as:

```text
blurred ink texture
abstract marks
blank worn surfaces
partial strokes
weathered patterning
sealed bundles
folded or cord-tied surfaces
out-of-focus record texture
```

Avoid:

```text
readable Chinese characters
fake AI Chinese text
subtitles
labels
readable banners
readable plaques
```

### 4.3 Anti-era-mixing rule

Do not mix:

```text
Warring States robes with Qing queue
Qin/Han bamboo-slip administration with late imperial paper archive furniture
Zhou aristocratic halls with Forbidden City visuals
Tang clothing with Ming/Qing official patches
Song scholar world with early bronze-age ritual props by default
Ming furniture in Qin/Han interiors
Qing queue outside Qing
```

### 4.4 Furniture-height rule

Early eras usually favor:

```text
mats
low tables
floor-level sitting / kneeling
low platforms
```

Later eras may use more developed desks, chairs, cabinets, and archive furniture.

### 4.5 Tone rule

Even elite scenes must follow the channel look:

```text
restrained
aged
documentary
matte
desaturated
material
institutional
non-glossy
```

---

## 5. Era Profile Structure

Each era profile uses this structure:

```text
A. Era Base Overlay
B. Tier / Role Overlays
C. Location / Space Overlays
D. Era Guardrails
```

Default tier set:

```text
Throne / Court Authority
Elite / Local Elite / Lineage Authority
Official / Clerk / Bureaucratic Layer
Scholar / Educated Layer
Society / Commoner / Farmer / Labor Layer
Merchant / Broker Layer
Military / Soldier / Retainer Layer
Women in Family / Marriage / Lineage Scenes
```

Default location set:

```text
INT. Court / Great Hall
INT. Record Room / Administrative Chamber
INT. Clan Hall / Ancestral Hall
INT. Study / School / Examination Space
EXT. Gate / Road / Courier Route
EXT. Village / Tax Collection / Field
EXT. Market / Dock / Commercial Edge
EXT. Frontier / Military Camp
```

---

# 6. Era Profiles

---

## 6.1 ERA 01 — ZHOU / SPRING AND AUTUMN / WARRING STATES

Approx:

```text
770–221 BCE
```

Use for:

```text
Eastern Zhou
Spring and Autumn
Warring States
pre-Qin aristocratic order
regional courts
lineage aristocracy
early service men / Shi
state formation before Qin unification
bronze ritual order
```

### A. Era Base Overlay

#### A.1 Era Identity

The world should feel:

```text
aristocratic
ritual-heavy
fragmented
regional
lineage-based
bronze-age to early iron-age transition
politically unstable
materially rough
not imperial-unified yet
```

Prefer:

```text
rammed earth platforms
dark timber halls
straight rooflines
bronze ritual vessels
bamboo slips
wooden tablets
low court mats
rough silk
hemp
jute
leather
bronze weapons
dusty roads
regional court compounds
```

Avoid:

```text
unified imperial bureaucracy look
grand Forbidden City visuals
Tang luxury
Song scholar-gentry tea culture
Ming/Qing robes
Qing queue
high chairs
gaiwan cups
fantasy armor
```

#### A.2 Field Overlays

context:

```text
regional court world, lineage authority, ritual legitimacy, aristocratic houses, early state formation, land and grain obligations, city-state gates, early records
```

subject:

```text
formal restrained bodies, tied hair or topknot-like arrangements, rank shown through posture, seating, distance, and access
```

composition_blocking:

```text
low platforms, mats, ranked bodies, ritual center, bronze vessels, elders deeper inside, lower figures near thresholds
```

action:

```text
placing ritual objects, bowing, receiving command token, passing bound records, carrying grain tribute, measuring boundaries, messenger crossing gate threshold
```

props:

```text
bronze ritual vessels, ding/gui forms, jade discs or ornaments, wooden offering tables, bamboo or wooden slips, cord-tied record bundles, grain baskets, measuring containers, simple weapons, ceremonial mats
```

material_textures:

```text
aged bronze patina, dark timber, rammed earth, packed earth floors, rough woven hemp, coarse linen, matte silk for high rank, bamboo/wood slip surfaces, cord fibers, mud, weathered stone
```

lighting_atmosphere:

```text
pre-electric low illumination, narrow opening side-light, weak primitive lamp in interiors when useful, dust above low surfaces, ritual smoke only when supported, diffused overcast outdoors
```

color_grading:

```text
global base grade with restrained aged bronze green, dark timber black-brown, rammed earth beige-gray, muted clay red, dull jade green, weathered hemp beige
```

visual_constraints:

```text
avoid Qing queue, Ming/Qing official hats, Tang glamour, Song tea-house look, Forbidden City architecture, high chairs, late imperial paper office visuals, readable writing
```

### B. Tier / Role Overlays

#### B.1 Throne / Royal / Ruling House

subject:

```text
formal aristocratic figure, restrained expression, layered robe silhouette, rank shown through stillness and distance
```

composition_blocking:

```text
ruling figure deeper inside or slightly elevated, protected by attendants, ritual objects, and court spacing
```

action:

```text
remaining still while others approach, receiving ritual offering, observing oath, accepting tribute
```

props:

```text
bronze ritual vessels, low ceremonial table, jade ornament, ceremonial mat, court token
```

material_textures:

```text
matte silk, preserved dark wood, aged bronze patina, muted jade, worn ceremonial surfaces
```

lighting_atmosphere:

```text
dim ritual side-light, deep protected shadows, heavy still air, dust or smoke only in ritual context
```

#### B.2 Elite / Aristocratic / Lineage

subject:

```text
older lineage figures or elite household members with composed posture, controlled gestures, carefully arranged garments
```

composition_blocking:

```text
elders deeper inside; younger, lower, or outsider figures near threshold; ritual or family objects between groups
```

action:

```text
witnessing, receiving, seating, arranging ritual objects, accepting a newcomer
```

props:

```text
ritual vessels, formal mats, family objects, offering table, cord-tied records, jade ornament
```

material_textures:

```text
aged inner-room timber, preserved matte fabric, handled ritual surfaces, dust in protected corners
```

#### B.3 Official / Scribe / Early Administrative

subject:

```text
plain ordered clerical figure, tied hair, restrained face, procedural posture, hands focused on record objects
```

composition_blocking:

```text
work surface separates clerk from messenger or commoner; records sit between authority and society
```

action:

```text
sorting slips, tying bundles, receiving command token, counting goods, registering tribute
```

props:

```text
bamboo or wooden slips, cord-tied bundles, low work table, seal or token object, measuring container
```

material_textures:

```text
handled wood, bamboo slip edges, cord fibers, matte administrative tools, dusty work surface
```

lighting_atmosphere:

```text
focused weak practical light on work surface, side-light from narrow opening, dark room edges, floating dust
```

#### B.4 Society / Commoner / Farmer / Labor

subject:

```text
weathered working bodies, coarse garments, practical tied hair or rough head covering, bent posture under burden when appropriate
```

composition_blocking:

```text
figures lower in frame, exposed outdoors, crowded near collection point, facing controlled receiver
```

action:

```text
carrying grain, lowering baskets, waiting in line, crossing muddy ground, presenting tribute
```

props:

```text
grain baskets, woven sacks, hemp rope, simple pottery, wooden cart, measuring container
```

material_textures:

```text
coarse hemp, frayed rope, muddy ground, rough baskets, dust, work-marked hands, worn sandals
```

#### B.5 Military / Retainer / Soldier

subject:

```text
disciplined practical body, worn protective gear where suitable, restrained readiness
```

composition_blocking:

```text
soldiers at gate, wall, road, or command threshold; ranked by access and duty
```

action:

```text
holding position, receiving orders, guarding gate, escorting messenger, moving supply
```

props:

```text
bronze or early iron weapons, shields, carts, rope, supply objects, command token when suitable
```

material_textures:

```text
worn leather, matte metal, rough wood, road dust, mud, practical cloth
```

### C. Location / Space Overlays

#### C.1 INT. Ritual Hall / Ancestral Hall

context:

```text
protected ritual interior where lineage, ancestry, and political legitimacy are visible
```

composition_blocking:

```text
ritual object or offering surface at center; elders/rulers deeper inside; lower figures near threshold
```

props:

```text
bronze ritual vessels, low offering table, ceremonial mats, jade object when suitable
```

material_textures:

```text
aged bronze, dark timber, packed earth or worn floor, matte cloth, dust in corners
```

lighting_atmosphere:

```text
dim side-light from narrow opening, deep protected shadows, suspended dust or ritual smoke only when supported
```

#### C.2 INT. Court Room / Aristocratic Hall

context:

```text
ranked political interior where aristocratic command, witness, or reception is staged through distance
```

composition_blocking:

```text
central authority deeper or slightly elevated; attendants/scribes off-axis; messenger/visitor near entrance
```

props:

```text
low tables, mats, ceremonial objects, record bundles, command token, ritual bronze when relevant
```

material_textures:

```text
dark timber, matte fabrics, packed earth or stone-like floor, aged bronze, handled wood
```

lighting_atmosphere:

```text
directional side-light, deep shadow pockets, restrained interior stillness, analog-softened air
```

#### C.3 INT. Record Room / Administrative Chamber

context:

```text
early administrative interior where command becomes record, procedure, and control
```

composition_blocking:

```text
work surface deeper inside; record bundles arranged around edges; messenger/commoner lower or near threshold
```

props:

```text
bamboo or wooden slips, cord-tied record bundles, low work table, storage rack, seal/token object
```

material_textures:

```text
handled wood, bamboo edges, cord fibers, dust, matte administrative surfaces, worn floor
```

lighting_atmosphere:

```text
indoor side-light logic, weak practical lamp on focal workspace when suitable, dark corners, floating dust
```

#### C.4 EXT. Village / Tax Collection / Field

context:

```text
exposed public space where grain, labor, tax, and social burden become visible
```

composition_blocking:

```text
commoners and goods in foreground; measuring/receiving point at center; official receiver farther back
```

props:

```text
grain baskets, woven sacks, measuring containers, rope, carts, simple pottery, field tools
```

material_textures:

```text
mud, dust, coarse hemp, frayed rope, rough wicker, grain, worn sandals
```

lighting_atmosphere:

```text
diffused overcast daylight, bleak mist or road dust, soft shadow edges, subdued exterior brightness
```

#### C.5 EXT. Gate / Walled City / Road Threshold

context:

```text
controlled passage where authority filters movement, goods, messengers, or military access
```

composition_blocking:

```text
gate or wall dominates background; crossing figure at threshold; guards/officials control passage
```

props:

```text
wooden gate, wall surface, cart, rope, command token, supply objects, simple weapons when appropriate
```

material_textures:

```text
rammed earth wall, weathered timber gate, road dust, worn cart wood, rope fibers, muddy ground
```

lighting_atmosphere:

```text
diffused exterior light, dusty air near ground, muted sky brightness, low-contrast atmosphere
```

### D. Era Guardrails

Do not use:

```text
Qing queue
Ming/Qing official hats
Tang luxury
Song tea-house scholar look by default
Forbidden City palace style
yellow glazed imperial roof tiles
high chairs
gaiwan tea cups
late imperial paper office visuals
fantasy weapons
readable writing
```

---

## 6.2 ERA 02 — QIN IMPERIAL / EARLY UNIFICATION

Approx:

```text
221–206 BCE
```

Use for:

```text
Qin unification
centralized command
standardization
military administration
legalist state machinery
imperial extraction
early empire formation
```

### A. Era Base Overlay

#### A.1 Era Identity

The world should feel:

```text
austere
hard-edged
centralized
militarized
disciplined
black-toned
bureaucratic
standardizing
```

Prefer:

```text
black and dark blue-black clothing
square plate armor
lamellar armor
rammed earth walls
military roads
standardized records
seal impressions
crossbows
cold administrative spaces
low tables
bamboo / wooden records
seal boxes
law tablets
```

Avoid:

```text
soft court romance
ornate Tang luxury
Ming/Qing palace richness
wuxia elegance
glowing emperor mythology
```

#### A.2 Field Overlays

context:

```text
early centralized imperial state, law, military command, standardized offices, roads, commanderies, record control, extraction machinery
```

subject:

```text
strict posture, functional dark garments, tightly bound hair/topknot, minimal ornament, practical official or military body
```

composition_blocking:

```text
rigid axes, desks or low work surfaces as command filters, gates and walls as control points, ranked military/administrative order
```

action:

```text
registering, sealing, counting, measuring, receiving command, moving orders, guarding gates, carrying supply, inspecting goods
```

props:

```text
bamboo/wood records, seal boxes, law tablets, command tallies, measuring blocks, crossbows, military supply carts, low work tables
```

material_textures:

```text
rammed earth, dark timber, matte black/blue-black cloth, leather ties, plate armor, bamboo/wood records, cord fibers, clay seal impressions
```

lighting_atmosphere:

```text
pre-electric low illumination, sharp interior side-light, weak practical lamp at focal workspace, cold administrative shadow, overcast exteriors
```

color_grading:

```text
global base grade with restrained black, dark blue-black, cold clay gray, muted earth, dull red/clay accents when physically present
```

visual_constraints:

```text
avoid Tang/Ming/Qing clothing, Qing queue, ornate throne spectacle, modern paper documents, late imperial furniture, gunpowder weapons, readable text
```

### B. Tier / Role Overlays

#### B.1 Throne / Imperial Command

subject:

```text
austere ruling authority, controlled stillness, dark formal garments, minimal ornament, command expressed through distance and rigidity
```

composition_blocking:

```text
ruler or command center placed on formal axis, surrounded by ranked officials or military order, protected by space
```

action:

```text
receiving report, issuing command through token/seal, observing rigid procedure
```

props:

```text
seal object, command tally, low table, standardized records, dark court surfaces
```

#### B.2 Official / Clerk / Legal-Administrative

subject:

```text
plain dark official or clerk, strict hair binding, procedural posture, hands centered on records or seal objects
```

composition_blocking:

```text
clerk behind work surface; messenger/commoner positioned lower or at threshold
```

action:

```text
sealing, counting, registering, sorting record bundles, receiving command
```

props:

```text
bamboo/wood slips, seal box, law tablet, command tally, measuring block, low desk
```

material_textures:

```text
handled dark wood, cord-tied records, clay seal texture, rough administrative tools
```

lighting_atmosphere:

```text
INT side-light, weak single-point practical lamp, dark corners, floating dust, cold bureaucratic hush
```

#### B.3 Military / Soldier / Supply

subject:

```text
disciplined soldier, practical armor, functional bindings, no heroic pose
```

composition_blocking:

```text
soldiers arranged by rank at gate, road, barrack, or supply point
```

action:

```text
guarding, receiving orders, checking goods, moving supplies, holding crossbow, escorting messenger
```

props:

```text
crossbow, spear, armor plates, supply cart, command tally, rope, crates or grain sacks
```

#### B.4 Society / Labor / Tax-bearing Commoners

subject:

```text
burdened working bodies, coarse practical garments, exposed posture, dusty or muddy surfaces
```

composition_blocking:

```text
commoners approach controlled receiving point; officials remain protected or higher in frame
```

action:

```text
carrying goods, presenting grain, waiting at gate, lowering sacks, crossing dusty road
```

props:

```text
grain sacks, baskets, measuring containers, carts, rope, simple tools
```

### C. Location / Space Overlays

#### C.1 INT. Commandery Office / Administrative Room

context:

```text
austere Qin interior where orders become registration, law, and extraction
```

composition_blocking:

```text
protected work surface deeper inside; records and seals close to clerk; messenger/commoner near threshold
```

props:

```text
bamboo/wood records, seal box, command tally, law tablet, measuring block, low table
```

material_textures:

```text
dark handled wood, cord-tied slips, clay seal surfaces, rammed-earth wall, dust
```

lighting_atmosphere:

```text
moody directional side-light from narrow opening, weak primitive practical lamp on focal workspace, deep corners, analog-softened dust
```

#### C.2 EXT. Road / Gate / Checkpoint

context:

```text
state-controlled movement point where goods, soldiers, orders, or commoners are filtered
```

composition_blocking:

```text
gate/wall as control background; guards/clerks at threshold; travelers/goods in exposed foreground
```

props:

```text
wooden gate, command tally, crossbow rack, supply cart, rope, goods bundles
```

material_textures:

```text
rammed earth, weathered timber, road dust, worn leather, coarse cloth
```

lighting_atmosphere:

```text
diffused overcast exterior light, dusty air, muted sky brightness, low contrast
```

#### C.3 EXT. Granary / Tax Collection Point

context:

```text
Qin extraction space where grain and registration become state control
```

composition_blocking:

```text
grain in foreground; measuring point at center; clerk/official separated from carriers
```

props:

```text
grain sacks, measuring containers, bamboo/wood records, seal object, carts
```

material_textures:

```text
grain dust, coarse sacks, wood, rope fibers, dry mud, handled records
```

lighting_atmosphere:

```text
overcast exterior or dim granary side-light depending on interior/exterior framing
```

### D. Era Guardrails

Do not use:

```text
Tang putou hats
Ming buzi patches
Qing queue
ornate dragon throne spectacle
late imperial furniture
modern paper documents
gunpowder weapons
fantasy armor
readable writing
```

---

## 6.3 ERA 03 — HAN DYNASTY

Approx:

```text
206 BCE–220 CE
```

Use for:

```text
Han bureaucracy
early imperial expansion
Confucian institutionalization
frontier logistics
granaries
household registration
imperial administration
```

### A. Era Base Overlay

#### A.1 Era Identity

The world should feel:

```text
broad imperial
expanding
administrative
earth-and-brick
early bureaucratic
more mature than Qin but not late imperial
```

Prefer:

```text
grey brick watchtowers
que towers at gates
rammed earth walls
tile ends with ancient motifs
courtyard offices
granaries
frontier posts
low furniture / mats
bamboo slips
wooden tablets
sealed documents
counting rods
household registers
```

Avoid:

```text
Forbidden City visuals
dramatically curved late imperial eaves
Tang glazed luxury
Ming/Qing palace interiors
Qing queue
late imperial bookcases
```

#### A.2 Field Overlays

context:

```text
maturing imperial administration, frontier expansion, household registration, granary storage, Confucian institutional growth, court-office-road system
```

subject:

```text
cross-collar layered robes, controlled sleeves, official caps when appropriate, restrained bureaucratic posture
```

composition_blocking:

```text
courtyard office hierarchy, clerk/work surface between authority and society, gate towers and granaries as state presence
```

action:

```text
registering households, handling tax/grain records, checking supply carts, frontier command, teaching or advising when period-appropriate
```

props:

```text
bamboo slips, wooden tablets, sealed documents, counting rods, granary ledgers, tax records, low desks, carts, crossbows/spears for military scenes
```

material_textures:

```text
grey brick, rammed earth, dark wood, bamboo/wood records, muted red accents, clay, worn cloth, early imperial tile texture
```

lighting_atmosphere:

```text
low office light, courtyard overcast diffusion, frontier dust, granary dimness, restrained institutional air
```

color_grading:

```text
global base grade with black, muted red, clay earth, lime white, grey brick, dark wood accents
```

visual_constraints:

```text
avoid Tang fashion, Ming/Qing official patches, Qing queue, late imperial furniture, Forbidden City look, modern paper libraries
```

### B. Tier / Role Overlays

#### B.1 Court / Imperial Administration

subject:

```text
formal Han court or official figure, layered cross-collar robe, controlled sleeves, period-appropriate cap
```

composition_blocking:

```text
ranked officials along court or office axis; ruler/authority deeper or elevated
```

action:

```text
receiving reports, observing procedure, holding court order, directing officials
```

props:

```text
sealed records, official objects, low table or court surface, bamboo/wood documents
```

#### B.2 Official / Clerk / Register Keeper

subject:

```text
plain bureaucratic figure, practical robe, official cap when appropriate, focused hands
```

composition_blocking:

```text
desk or low table separates clerk from commoner; records and counting tools define workspace
```

action:

```text
counting, registering, storing, receiving grain records, checking household registration
```

props:

```text
bamboo slips, wooden tablets, counting rods, sealed documents, granary ledgers
```

#### B.3 Scholar / Educated / Confucian Institutional Layer

subject:

```text
restrained educated figure, plain layered robe, controlled posture, teacher or advisor body language
```

composition_blocking:

```text
teacher/advisor deeper in room; student/junior lower or nearer entry
```

action:

```text
teaching, reading unreadable records, presenting advice, guiding junior figure
```

props:

```text
era-compatible records, writing tools, teaching objects, low study surfaces
```

#### B.4 Society / Farmer / Labor

subject:

```text
working household figures, coarse garments, tied hair/head covering, exposed posture
```

composition_blocking:

```text
workers at field/granary edge; officials/clerks protected near receiving point
```

action:

```text
carrying grain, unloading cart, standing in registration line, presenting goods
```

props:

```text
grain sacks, baskets, carts, ropes, measuring containers
```

#### B.5 Frontier / Military

subject:

```text
disciplined soldier or frontier courier, practical armor or military dress, no fantasy hero pose
```

composition_blocking:

```text
watchtower/gate/camp frames state frontier control
```

action:

```text
guarding, moving supply, receiving orders, escorting carts, watching road
```

props:

```text
crossbows, spears, supply carts, military registers, frontier equipment
```

### C. Location / Space Overlays

#### C.1 INT. County Office / Administrative Room

context:

```text
Han bureaucratic interior where registration, tax, and imperial order become procedure
```

composition_blocking:

```text
clerk/official behind work surface; commoner or messenger in lower approach position
```

props:

```text
bamboo slips, wooden tablets, counting rods, sealed documents, low desk
```

material_textures:

```text
grey brick or earth wall, worn wood, handled records, clay floor, muted cloth
```

lighting_atmosphere:

```text
indoor side-light, dim institutional shadow, dust above workspace, restrained office air
```

#### C.2 EXT. Granary / Courtyard Office

context:

```text
state storage and extraction space where grain becomes administrative record
```

composition_blocking:

```text
granary/storage behind receiving point; carriers foreground; clerk or official positioned at control point
```

props:

```text
grain sacks, baskets, carts, records, measuring tools
```

material_textures:

```text
grain dust, rough wood, rammed earth, grey brick, coarse cloth
```

lighting_atmosphere:

```text
diffused exterior light or dim storage side-light, subdued brightness, floating grain dust
```

#### C.3 EXT. Frontier Post / Gate / Road

context:

```text
imperial edge where military logistics, messengers, and frontier control become visible
```

composition_blocking:

```text
watchtower or gate background; soldiers/couriers at threshold; carts or road line foreground
```

props:

```text
crossbows, spears, carts, supply bundles, command records
```

material_textures:

```text
grey brick, rammed earth, dust, leather, worn wood, muted armor surfaces
```

lighting_atmosphere:

```text
overcast exterior, dusty road air, muted horizon, low contrast
```

### D. Era Guardrails

Do not use:

```text
Tang high-chest fashion
Ming buzi patches
Qing queue
Forbidden City architecture
late imperial furniture by default
gaiwan tea culture
modern paper libraries
readable text
```

---

## 6.4 ERA 04 — TANG DYNASTY

Approx:

```text
618–907 CE
```

Use for:

```text
Tang court
Silk Road cosmopolitanism
imperial capital
elite display
frontier administration
Buddhist-influenced spaces when required
```

### A. Era Base Overlay

#### A.1 Era Identity

The world should feel:

```text
prosperous
cosmopolitan
broad open
multi-cultural
more colorful than earlier eras
```

For this channel, keep it:

```text
restrained
desaturated
aged
dusty
worn silk
aged lacquer
muted red columns
faded gold
non-glossy
```

Prefer:

```text
round-collar robes
putou headwear
large dougong brackets
red-painted columns
grey or greenish glazed roof tiles
broad wooden halls
urban market streets
official belts
horse gear
trade goods
paper documents where appropriate
```

Avoid:

```text
Qing queue
Ming buzi patches
overly glossy Tang romance visuals
fantasy immortal robes
flying sleeves
excessive glowing gold
```

#### A.2 Field Overlays

context:

```text
imperial capital, cosmopolitan court, frontier administration, trade routes, official bureaucracy, market exchange, religious/ritual spaces when relevant
```

subject:

```text
round-collar robes for men, putou headwear, high-waisted ruqun or shawl/pibo for elite women when appropriate, restrained body language
```

composition_blocking:

```text
broad halls, urban depth, market layers, court rows, administrative desks, frontier/capital contrast
```

action:

```text
receiving official order, moving trade goods, recording documents, formal court procedure, frontier supply, market exchange
```

props:

```text
paper documents, official belts, worn silk, lacquer, ceramic vessels, horse gear, trade goods, market baskets, official records
```

material_textures:

```text
worn silk, aged lacquer, dusty red-painted wood, ceramic, paper fibers, horse gear leather, weathered market wood
```

lighting_atmosphere:

```text
diffused capital light, dim administrative interiors with lamp pools, softened silk-filtered side-light only when physically present, dusty market air
```

color_grading:

```text
global base grade with restrained faded red, worn lacquer brown, muted jade/green roof tones, aged gold accents only when physically present
```

visual_constraints:

```text
avoid glossy Tang drama color, xianxia/wuxia styling, Qing queue, Ming official patches, modern tea/costume tourism look
```

### B. Tier / Role Overlays

#### B.1 Throne / Court

subject:

```text
formal Tang court figure, round-collar or ceremonial robe form as appropriate, restrained elite posture
```

composition_blocking:

```text
large hall depth, ranked officials, ruler/authority protected by distance and scale
```

action:

```text
receiving tribute/report, formal audience, issuing order through officials
```

props:

```text
official records, ceremonial objects, worn silk, lacquered surfaces, court mats or furniture as period-appropriate
```

#### B.2 Elite / Court Official / Administrative

subject:

```text
official in restrained round-collar robe and putou-like headwear where appropriate, composed procedural posture
```

composition_blocking:

```text
administrative table/desk or official row separates state procedure from petitioners/messengers
```

action:

```text
recording, receiving papers, reviewing reports, handing over orders
```

props:

```text
paper documents, brushes, inkstone, official belt, storage shelves, administrative boxes
```

material_textures:

```text
paper fibers, dark shelves, worn lacquer, matte official cloth, handled desk surface
```

#### B.3 Society / Market / Labor

subject:

```text
market workers, boat/dock laborers, farmers, or porters in faded practical garments, hair wraps or simple bindings
```

composition_blocking:

```text
goods and labor foreground; officials/merchants or receiving points farther back
```

action:

```text
carrying goods, weighing, loading carts/boats, exchanging bundles, waiting at market edge
```

props:

```text
market baskets, cloth bundles, scales, ceramic vessels, carts, dock goods
```

#### B.4 Merchant / Broker / Silk Road Edge

subject:

```text
practical but better-kept trader or broker, positioned between goods and official/local receiver
```

composition_blocking:

```text
goods between groups, broker at threshold of official and market spaces
```

action:

```text
weighing, negotiating, presenting goods, moving bundles
```

props:

```text
scales, goods bundles, transport objects, accounting tools appropriate to era
```

### C. Location / Space Overlays

#### C.1 INT. Court / Palace Hall

context:

```text
Tang imperial or elite hall where scale and ranked access show authority
```

composition_blocking:

```text
large hall axis, ranked figures, protected authority depth, controlled approach
```

props:

```text
court objects, official records, worn ceremonial textiles, lacquered surfaces
```

material_textures:

```text
aged lacquer, dusty red columns, worn silk, matte wood, stone or tile floor
```

lighting_atmosphere:

```text
controlled side-light or diffused hall light, dusty air, restrained shadow, analog softness
```

#### C.2 INT. Administrative Archive / Office

context:

```text
Tang administrative interior where paper records and official procedure are visible
```

composition_blocking:

```text
shelves or record stacks at edges, official workspace central/deep, messenger/petitioner lower or nearer threshold
```

props:

```text
paper records, brushes, inkstones, boxes, shelves, official belt/objects
```

material_textures:

```text
paper fibers, worn shelves, dark wood, matte lacquer, thick ink as unreadable texture
```

lighting_atmosphere:

```text
warm lamp pools or side-light where appropriate, shadowed shelves, floating dust
```

#### C.3 EXT. Market / Dock / Urban Street

context:

```text
cosmopolitan commercial space where goods, exchange, and social movement become visible
```

composition_blocking:

```text
goods foreground, traders and labor midground, official/elite access or road flow in background
```

props:

```text
market stalls, baskets, goods bundles, ceramic vessels, scales, carts, boat/dock items when relevant
```

material_textures:

```text
wooden stalls, rough cloth, ceramic, road dust, rope, worn goods
```

lighting_atmosphere:

```text
diffused overcast exterior light, dusty market air, subdued brightness, low contrast
```

### D. Era Guardrails

Do not use:

```text
Qing queue
Ming buzi patches
hyper-saturated Tang romance colors
fantasy immortal robes
wuxia flying sleeves
modern tourism palace styling
readable text
```

---

## 6.5 ERA 05 — SONG DYNASTY

Approx:

```text
960–1279 CE
```

Use for:

```text
mature bureaucracy
examination culture
scholar-officials
urban commercial life
printing and paper culture
lineage expansion
administrative refinement
```

### A. Era Base Overlay

#### A.1 Era Identity

The world should feel:

```text
bureaucratic
scholarly
urban
commercial
paper-heavy
refined but restrained
institutionally mature
```

Prefer:

```text
paper documents
printed books
examination papers
brushes
inkstones
official files
lineage records
tax ledgers
woodblock printing when appropriate
county offices
bookshops
lineage halls
bridges
canals
wooden urban interiors
```

Avoid:

```text
Qing queue
Ming/Qing official patches unless explicitly later transition
Tang elite fashion by default
ancient bronze-only document systems
wuxia sect architecture
```

#### A.2 Field Overlays

context:

```text
mature civil bureaucracy, examination culture, paper records, urban commerce, lineage consolidation, scholar-official order
```

subject:

```text
scholar-officials, clerks, gentry, merchants, students, teachers; restrained garments and posture
```

composition_blocking:

```text
study/office hierarchy, examination rows, desks/shelves, teacher-student distance, urban commercial depth
```

action:

```text
studying, copying, examining papers, filing records, teaching, trading, weighing goods, managing lineage records
```

props:

```text
paper documents, printed books, brushes, inkstones, official files, lineage records, tax ledgers, abacus/counting tools where appropriate
```

material_textures:

```text
paper fibers, ink-black surfaces, worn wood, muted cloth, urban dust, book edges, cabinet surfaces
```

lighting_atmosphere:

```text
dim study side-light, soft paper-room shadows, overcast urban light, quiet interior air
```

color_grading:

```text
global base grade with ink black, paper beige, muted brown, soft grey, washed-out green, weathered wood accents
```

visual_constraints:

```text
avoid Qing queue, Ming patches by default, Tang court fashion, bamboo-slip-only administration, modern classroom layout, readable writing
```

### B. Tier / Role Overlays

#### B.1 Scholar-Official / Literati

subject:

```text
restrained educated figure, quiet posture, period-appropriate robe/hat, controlled hand movement
```

composition_blocking:

```text
teacher/official deeper inside; students/juniors/petitioners lower or near entry
```

action:

```text
reviewing papers, teaching, writing unreadable marks, reading printed material as texture
```

props:

```text
paper documents, books, brush, inkstone, desk, shelves, lineage or official records
```

#### B.2 Official / Clerk / Examination Bureaucracy

subject:

```text
functional bureaucratic figure, focused posture, plain restrained clothing
```

composition_blocking:

```text
files/desks mediate between state and petitioners/students
```

action:

```text
filing, checking, registering, distributing papers, examining records
```

props:

```text
official files, paper bundles, inkstone, brush, cabinets, ledgers
```

#### B.3 Local Elite / Lineage / Gentry

subject:

```text
protected household or lineage figure, elder or educated family member with controlled access to inner space
```

composition_blocking:

```text
elders deeper in lineage hall; juniors/commoners near threshold; records or ritual objects between groups
```

action:

```text
witnessing, teaching, arranging lineage records, receiving visitor, presiding over family ritual
```

props:

```text
lineage records, paper bundles, ritual table, household objects, books
```

#### B.4 Merchant / Urban Commercial

subject:

```text
better-kept practical merchant or broker, positioned among goods and account objects
```

composition_blocking:

```text
goods, scales, and accounts mediate between buyer/seller/official
```

action:

```text
weighing, counting, recording, moving goods, negotiating
```

props:

```text
scales, goods bundles, paper account objects, baskets, boxes, urban stall surfaces
```

### C. Location / Space Overlays

#### C.1 INT. Study / School / Examination Space

context:

```text
education or examination space where knowledge becomes office access
```

composition_blocking:

```text
rows of desks or study surfaces, teacher/examiner deeper, students lower or repeated in orderly rows
```

props:

```text
paper, books, brushes, inkstones, desks, shelves
```

material_textures:

```text
paper fibers, worn wood, ink texture, muted cloth, dust
```

lighting_atmosphere:

```text
soft side-light, dim study air, paper-room quiet, analog-softened dust
```

#### C.2 INT. County Office / Archive

context:

```text
mature paper bureaucracy where documents, files, and officials mediate power
```

composition_blocking:

```text
files/cabinets at edges; official/clerk at work surface; petitioner lower or near threshold
```

props:

```text
paper files, ledgers, brush, inkstone, cabinet, document boxes
```

material_textures:

```text
paper stacks, worn cabinets, dark wood, ink, muted fabric
```

lighting_atmosphere:

```text
dim side-light, shadowed shelves, quiet institutional air
```

#### C.3 INT. Lineage Hall

context:

```text
family/lineage space where records, ritual, and social hierarchy preserve local power
```

composition_blocking:

```text
elders deeper inside, juniors or outsiders near threshold, records/ritual table between groups
```

props:

```text
lineage records, ritual table, household objects, paper bundles
```

material_textures:

```text
aged wood, paper, cloth, dust, preserved household surfaces
```

lighting_atmosphere:

```text
restrained interior side-light, dim protected background, analog-softened dust
```

#### C.4 EXT. Urban Market / Bridge / Canal / Dock

context:

```text
commercial space where urban life, exchange, and paperwork-mediated order are visible
```

composition_blocking:

```text
goods and workers foreground; merchants/brokers midground; road/bridge/canal depth background
```

props:

```text
goods bundles, scales, baskets, boxes, boats/carts when relevant
```

material_textures:

```text
wood, rope, paper scraps, wet stone, canal/dock surfaces, worn cloth
```

lighting_atmosphere:

```text
diffused overcast urban light, damp air, low-contrast exterior atmosphere
```

### D. Era Guardrails

Do not use:

```text
Qing queue
Ming/Qing official patches by default
Tang high-chest fashion
Warring States deep-robes as default
bamboo-slip-only bureaucracy
modern classroom layout
readable documents
wuxia academy look
```

---

## 6.6 ERA 06 — MING DYNASTY

Approx:

```text
1368–1644 CE
```

Use for:

```text
Ming state
late imperial bureaucracy
Forbidden City context
official robes
gentry society
lineage institutions
maritime / taxation / examination contexts
```

### A. Era Base Overlay

#### A.1 Era Identity

The world should feel:

```text
late imperial
formal
bureaucratic
ritualized
architecturally monumental
```

For channel tone, keep it:

```text
desaturated
aged
dusty
documentary
less glossy than costume drama
```

Prefer:

```text
round-collar robes with metal buttons
official buzi rank badge patch when relevant
stiff winged official hat
formal court robe
gentry robes
red walls / yellow glazed roof tiles only when relevant
formal courtyards
late imperial offices
ancestral halls
paper registers
official files
wooden cabinets
brushes
inkstones
lineage documents
tax ledgers
```

Avoid:

```text
Qing queue
Manchu changshan
Tang putou hats
Warring States deep robe default
bronze weapons as default military look
overly pristine palace drama lighting
```

#### A.2 Field Overlays

context:

```text
late imperial bureaucracy, examination/gentry order, lineage institutions, monumental court, taxation and official documentation
```

subject:

```text
Ming officials, gentry, clerks, commoners; period-appropriate hats/robes and social posture
```

composition_blocking:

```text
formal courtyards, ranked offices, cabinets/desks, official hierarchy, ancestral hall distance
```

action:

```text
reviewing files, receiving reports, taking petitions, managing tax ledgers, lineage ritual, examination-related procedure
```

props:

```text
paper registers, official files, wooden cabinets, brushes, inkstones, lineage documents, tax ledgers, rank badges where subject requires
```

material_textures:

```text
faded red paint, worn stone, dusty wood, paper files, matte cloth, aged lacquer, official surfaces
```

lighting_atmosphere:

```text
dim office side-light, courtyard overcast diffusion, dusty palace/office air, restrained late-imperial atmosphere
```

color_grading:

```text
global base grade with faded red, aged ochre, dusty yellow glaze only when physically present, dark wood, paper beige
```

visual_constraints:

```text
avoid Qing queue/Manchu clothing, Tang headwear, early bamboo-slip administration, glossy palace tourism look, readable documents
```

### B. Tier / Role Overlays

#### B.1 Court / Imperial Authority

subject:

```text
formal late imperial court figure or official presence, Ming-specific attire when relevant, restrained institutional posture
```

composition_blocking:

```text
large courtyard/hall axis, ranked officials, authority protected by gates and distance
```

action:

```text
receiving report, formal audience, controlled ceremonial movement
```

props:

```text
official files, court objects, formal desks or surfaces, ceremonial textiles if relevant
```

#### B.2 Official / Clerk / Bureaucratic

subject:

```text
Ming official or clerk, period-appropriate robe/hat when relevant, procedural posture
```

composition_blocking:

```text
desk/cabinet/file surface mediates between state and petitioner
```

action:

```text
reviewing files, stamping/sealing, receiving petitions, sorting registers, recording taxes
```

props:

```text
paper files, registers, brush, inkstone, cabinets, seal objects
```

#### B.3 Gentry / Local Elite / Lineage

subject:

```text
protected gentry or lineage elder, restrained clothing, controlled inner-room posture
```

composition_blocking:

```text
elders deeper in ancestral hall; juniors/petitioners lower or near threshold; records/ritual objects mediate
```

action:

```text
presiding, witnessing, reading lineage records, arranging family ritual, receiving visitors
```

props:

```text
lineage documents, ritual table, paper records, household objects
```

#### B.4 Society / Tax / Labor

subject:

```text
commoners, carriers, farmers, or laborers in worn late-imperial practical garments
```

composition_blocking:

```text
labor/goods foreground; official receiver at protected point
```

action:

```text
carrying grain, submitting tax, waiting at office/gate, unloading goods
```

props:

```text
grain sacks, baskets, carts, tax ledgers near official side, measuring tools
```

### C. Location / Space Overlays

#### C.1 INT./EXT. Court / Formal Courtyard

context:

```text
late imperial state space where monumental architecture organizes hierarchy
```

composition_blocking:

```text
gate/courtyard/hall axis, ranked figures, protected authority, officials in formal rows
```

props:

```text
formal court objects, official files, ceremonial surfaces when relevant
```

material_textures:

```text
faded red walls, worn stone, aged paint, matte cloth, dusty surfaces
```

lighting_atmosphere:

```text
diffused courtyard light or dim hall side-light, dusty air, low contrast
```

#### C.2 INT. Office / Archive

context:

```text
late imperial paper bureaucracy where files, cabinets, and officials mediate power
```

composition_blocking:

```text
file cabinets/shelves at edges, official at desk, petitioner/commoner lower or near threshold
```

props:

```text
paper registers, files, cabinets, brushes, inkstones, seals
```

material_textures:

```text
paper, worn cabinets, dark wood, ink, faded cloth
```

lighting_atmosphere:

```text
indoor side-light, shadowed cabinets, dusty file-room air
```

#### C.3 INT. Ancestral / Lineage Hall

context:

```text
gentry lineage space where family memory, property, and ritual authority are maintained
```

composition_blocking:

```text
elders deeper inside, juniors/outsiders lower, ritual or record surface between groups
```

props:

```text
lineage documents, ritual table, household objects, paper bundles
```

material_textures:

```text
aged wood, paper, matte cloth, dust, preserved household surfaces
```

lighting_atmosphere:

```text
dim protected interior, side-light, deep corners, analog-softened dust
```

#### C.4 EXT. Market / Dock / Tax Point

context:

```text
late imperial commercial or extraction space where goods, tax, and bureaucracy meet
```

composition_blocking:

```text
goods/workers foreground, merchant/official receiver midground, road/dock/office background
```

props:

```text
goods bundles, boxes, scales, carts, account papers, tax objects
```

material_textures:

```text
rope, cloth, paper, worn wood, stone/dirt ground, dust or damp air
```

lighting_atmosphere:

```text
diffused overcast exterior, subdued brightness, muted market/dock air
```

### D. Era Guardrails

Do not use:

```text
Qing queue
Manchu changshan/magua
Tang putou
Warring States robes as default
bronze-age administration
overly pristine palace drama
readable documents
```

---

## 6.7 ERA 07 — QING DYNASTY

Approx:

```text
1644–1912 CE
```

Use for:

```text
Qing state
Manchu rule
late imperial court
queue hairstyle
banner institutions
late imperial bureaucracy
```

### A. Era Base Overlay

#### A.1 Era Identity

The world should feel:

```text
late imperial
Manchu-influenced
ornate but controlled
bureaucratic
ritualized
multi-ethnic imperial
```

For channel tone:

```text
aged ornament
faded lacquer
dusty halls
worn textiles
bureaucratic records
restrained court ritual
non-glossy
```

Prefer:

```text
queue hairstyle
front half shaved / long braid for men when appropriate
changshan / long robe
magua short jacket
high stiff collars
Manchu-influenced court robes
late imperial palace complexes
ornate carving
red walls / glazed roofs when relevant
paper records
official memorials
wooden cabinets
court documents
seals
```

Avoid:

```text
queue outside Qing
Ming winged official hat
Tang robes
Warring States deep robes
ancient bamboo-slip bureaucracy
bronze sword era visuals by default
modern republican clothing unless late transition is explicit
```

#### A.2 Field Overlays

context:

```text
Qing late imperial bureaucracy, Manchu court order, banner institutions, memorial system, palace/office ritual, late imperial household and social hierarchy
```

subject:

```text
Qing-specific grooming and clothing when male/official context requires it; queue hairstyle for men; Manchu-influenced court or official forms when relevant
```

composition_blocking:

```text
late imperial court/office hierarchy, cabinets/files, memorial desks, palace gates, banner or bureaucratic order
```

action:

```text
handling memorials, receiving official documents, court ritual, filing records, gate/office control, late imperial household ritual
```

props:

```text
paper records, official memorials, wooden cabinets, seals, court documents, late imperial office objects
```

material_textures:

```text
faded lacquer, dusty halls, worn textiles, paper files, aged wood, restrained ornament, red wall paint when relevant
```

lighting_atmosphere:

```text
dim palace/office side-light, dusty file-room air, diffused courtyard light, restrained ornate interiors
```

color_grading:

```text
global base grade with faded lacquer red, dark wood, worn textile tones, muted yellow/green roof accents only when physically present
```

visual_constraints:

```text
use queue only in Qing contexts; avoid Ming/Tang/Zhou/Han costume bleed; avoid tourism-gloss palace styling; written surfaces unreadable
```

### B. Tier / Role Overlays

#### B.1 Court / Imperial / Banner Authority

subject:

```text
Qing court or banner authority figure, Manchu-influenced robe forms when relevant, queue for male figures, controlled ritual posture
```

composition_blocking:

```text
palace/office axis, ranked officials, authority protected by gates, screens, desks, and distance
```

action:

```text
receiving memorial, formal court procedure, controlled ceremonial movement
```

props:

```text
court documents, seals, official memorials, palace/office objects
```

#### B.2 Official / Clerk / Memorial Bureaucracy

subject:

```text
Qing official or clerk, queue for male figures, period-appropriate robe/jacket, procedural posture
```

composition_blocking:

```text
desk/cabinet/file surface mediates between official procedure and petitioners/messengers
```

action:

```text
sorting files, handling memorials, sealing, receiving documents, recording
```

props:

```text
paper files, memorials, cabinets, brushes, inkstones, seals
```

#### B.3 Gentry / Local Elite / Household

subject:

```text
late imperial elite household or gentry figure, Qing-period grooming/clothing where appropriate, protected inner-room posture
```

composition_blocking:

```text
elders or elites deeper inside, others near threshold, records/ritual objects between groups
```

action:

```text
receiving visitor, arranging records, witnessing ritual, controlling household access
```

props:

```text
paper records, ritual table, household objects, cabinets, seals if relevant
```

#### B.4 Society / Commoner / Labor

subject:

```text
Qing-period commoner or laborer, worn practical garments, queue for male figures when appropriate, exposed posture
```

composition_blocking:

```text
commoners/goods foreground; office/gate/receiver deeper or protected
```

action:

```text
waiting, carrying goods, submitting documents or tax goods, unloading, crossing gate
```

props:

```text
baskets, carts, goods bundles, paper document on official side, tools
```

### C. Location / Space Overlays

#### C.1 INT./EXT. Palace / Court / Formal Gate

context:

```text
Qing imperial or late imperial formal space where ritual and bureaucracy reinforce authority
```

composition_blocking:

```text
gates/courtyards/halls arranged in formal axis; officials ranked by access and distance
```

props:

```text
court documents, seals, ceremonial/office objects, screens or cabinets when relevant
```

material_textures:

```text
faded lacquer, dusty red walls, aged painted detail, worn textiles, stone/tile surfaces
```

lighting_atmosphere:

```text
diffused courtyard light or dim side-lit interior, restrained dust, low contrast
```

#### C.2 INT. Office / Memorial Archive

context:

```text
late imperial office where paper memorials and files channel state power
```

composition_blocking:

```text
cabinets/files at edges, official/clerk at desk, messenger/petitioner lower or near threshold
```

props:

```text
paper memorials, files, cabinets, brushes, inkstones, seals
```

material_textures:

```text
paper, dark wood, faded lacquer, ink, dust, matte cloth
```

lighting_atmosphere:

```text
indoor side-light, shadowed cabinets, dusty file-room air, analog-softened particles
```

#### C.3 INT. Household / Lineage Hall

context:

```text
late imperial household or lineage space where family hierarchy and record memory are visible
```

composition_blocking:

```text
elders deeper inside, juniors or outsiders near threshold, ritual/record surface between groups
```

props:

```text
paper records, family objects, ritual table, cabinets
```

material_textures:

```text
aged wood, worn textiles, paper, dust, preserved household surfaces
```

lighting_atmosphere:

```text
dim protected interior, side-light, deep corners, restrained stillness
```

#### C.4 EXT. Market / Gate / Road

context:

```text
late imperial public movement space where goods, documents, and authority meet
```

composition_blocking:

```text
goods/people foreground, gate/office/official receiver background, movement controlled by access
```

props:

```text
goods bundles, carts, boxes, papers on official side, scales
```

material_textures:

```text
worn cloth, paper, wood, stone/dirt road, rope, dust
```

lighting_atmosphere:

```text
diffused overcast exterior, subdued brightness, low contrast public air
```

### D. Era Guardrails

Do not use:

```text
queue hairstyle outside Qing
Ming winged official hats in Qing scenes
Tang putou
Zhou/Han/Qin deep robes as default
ancient bamboo-slip bureaucracy
bronze Jian as default visual symbol
modern republican clothing unless explicitly late transition
readable documents
tourism-gloss palace styling
```

---

# 7. Final Era QC Checklist

Before writing `viewer_sees` or `prompt_raw`, check:

```text
Is the active era explicitly selected?
Does the scene use only the selected era profile?
Does the subject match the selected era and tier?
Does hair/headwear match the selected era?
Does costume match the selected era and role?
Does the furniture height match the era?
Do record materials match the era?
Do props/tools/weapons match the era?
Does architecture match the era?
Does the location overlay match the shot location?
Does the tier overlay match the visible social role?
Does lighting use only the active location logic?
Does color grading keep the channel global base grade?
Are written surfaces unreadable?
Does the image avoid wuxia/xianxia/fantasy drift?
Does elite status read through protected space and material preservation, not shiny luxury?
Does commoner status read through labor, exposure, and material pressure, not generic misery?
Does the shot avoid mixing visually incompatible dynasties?
```

If any answer fails, revise the shot before generating `prompt_raw`.

---

# 8. Development Notes For Future Expansion

This file is V1 foundation.

Future improvements should add deeper data inside each era profile:

```text
more exact costume variants
more precise hairstyle/headwear by role
more accurate furniture evolution
more location-specific prop sets
more period-specific lighting technology
more period-specific color-material families
more anti-error examples per era
```

Do not expand by adding generic China details.

Expand by improving the active era profile.
