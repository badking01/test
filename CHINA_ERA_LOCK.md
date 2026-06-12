# CHINA_ERA_LOCK.md

## FILE ROLE

This file is the **master era lock** for the China Session.

It defines the China-specific visual-period rules for all normal China episodes.

It controls:

```text
historical period visuals
costume / clothing forms
hair / headwear / grooming
architecture / furniture / spatial setting
props / tools / weapons / transport
record materials / writing surfaces
ritual objects / social spaces
China social-role visual embodiment
anti-era-mixing guardrails
```

This file exists because `CHANNEL_VEO_PROMPT_RULES.md` has been cleaned to control **prompt_raw technique only**.

Therefore, China-specific material culture belongs here, not inside channel-level prompt mechanics.

This file is used by:

```text
CHINA_EP##_PROJECT_SHOT_PLANNER
China projectbeat JSON generation rooms
PROJECT_ARCHITECT_ROOM when auditing era consistency
future China episode production rooms
```

This file is **not** a script file.

This file is **not** a prompt_raw schema file.

This file supports:

```text
projectbeat JSON
shots[].prompt_raw
```

by telling the assistant what China-period visual details are historically allowed.

---

## HOW TO USE THIS FILE

Use the era section required by the episode, beat, or shot.

Example:

```text
For this episode, use only:

ERA 01 — ZHOU / SPRING AND AUTUMN / WARRING STATES
```

Do not mix visual details from other eras unless the user explicitly asks for symbolic cross-era compression.

Do not borrow from another era:

```text
costume
hairstyle
headwear
architecture
weapons
furniture
props
color system
ritual objects
social setting
record materials
```

For normal China episodes such as EP01, EP02, and onward, use the relevant section of `CHINA_ERA_LOCK.md` as the active visual-period authority.

Do not create or assume a separate episode visual lock by default.

If no specific era is assigned in a normal China episode, use the broad era range declared in `00_BRIEF.md`, the episode plan, or the projectbeat task, then stay inside the closest matching era section.

Do not invent a generic “ancient China” look.

---

## AUTHORITY

This file follows:

```text
CHANNEL_IDENTITY.md
CHANNEL_STYLE_LOCK.md
CHANNEL_WORKFLOW_CONTROL.md
CHANNEL_VEO_PROMPT_RULES.md
CHINA_SESSION_THESIS.md
CHINA_SESSION_CONTROL.md
```

This file controls China-specific era visuals and social-role embodiment.

It must not override:

```text
China Session thesis
episode script
approved beat meaning
projectbeat timing
channel documentary look
prompt_raw schema
```

Conflict rule:

```text
CHINA_SESSION_THESIS.md wins for China thesis.
CHINA_SESSION_CONTROL.md wins for China session guardrails and visual meaning.
CHANNEL_WORKFLOW_CONTROL.md wins for workflow and human-readable projectbeat fields.
CHANNEL_VEO_PROMPT_RULES.md wins for prompt_raw schema and field mechanics.
CHINA_ERA_LOCK.md wins for period-specific costume, hair, architecture, furniture, props, record materials, weapons, social spaces, and class-role visual embodiment.
```

---

## UNIVERSAL CHINA ANTI-ERROR RULES

These rules apply across the China Session.

### Do not use generic “ancient China” costume drama

Avoid treating all Chinese periods as the same visual world.

Do not use:

```text
generic Ming/Qing palace robes for all eras
generic Qing queue hairstyle outside Qing
fantasy wuxia robes
xianxia / immortal fantasy styling
overly polished palace drama visuals
glowing temple fantasy
modern nationalist imagery
```

### Text and signs

Avoid readable text unless required.

Prefer:

```text
abstract ink marks
unreadable worn strokes
sealed bundles
folded documents
bamboo slips
record texture
```

Avoid:

```text
readable palace plaques
fake AI Chinese characters
modern signs
subtitles
labels
banners with readable text
```

### Furniture

Early periods should not use later furniture by default.

For Spring and Autumn / Warring States / early Han:

```text
people sit or kneel on mats
low tables
floor-level ritual setting
```

Avoid:

```text
high chairs
modern desks
tea tables
gaiwan cups
late imperial furniture
```

### Tone

Even when an era has elite or court visuals, keep the channel look:

```text
restrained historical documentary
muted desaturated palette
material textures
dust
wood
stone
cloth
bronze
records
institutional pressure
```

Avoid:

```text
romantic court spectacle
wuxia beauty lighting
overly glossy silk drama
heroic emperor worship
```

---


### Historical Anchor Discipline

Do not use vague anchors that cause generic Chinese costume-drama drift.

Avoid unsupported anchors such as:

```text
pre-modern Chinese
old Chinese world
ancient Asian setting
generic imperial China
generic Chinese dynasty
```

Use era-compatible anchors from the active era section.

Each era section should guide:

```text
court anchors
office anchors
rural anchors
ritual anchors
record / archive anchors
military anchors
architecture anchors
```

If a normal episode is broad but still period-based, use the broad era range declared in the episode brief or projectbeat task.

If a shot is era-specific, the era lock wins.

### Era-Compatible Role Appearance

Every visible person should match the active era and social role.

Check:

```text
ruler / court figure
official / clerk
scholar / service man
commoner / farmer / laborer
merchant / broker
soldier
elder / ritual authority
women in family or ritual scenes
```

Do not let a later role costume leak into earlier periods.

Avoid:

```text
Ming/Qing official hats in Warring States or Han scenes
Qing queue hairstyles outside Qing
Song scholar-gentry look in early ARC_01 unless explicitly symbolic
late imperial formal furniture in early aristocratic settings
fantasy armor or wuxia robes in administrative scenes
```

### Hair / Headwear / Grooming by Era

Hair, headwear, and grooming are era-sensitive.

For every era, prompts should use the approved hair/headwear guidance from that era section.

Baseline negative risk:

```text
modern short hair
buzz cuts
fade haircuts
contemporary hairstyles
modern grooming
modern fashion silhouettes
```

If no specific era is assigned in a normal China episode, use the broad era range declared in the episode brief or projectbeat task.

Do not invent a hairstyle because it "looks ancient."

### Costume / Textile by Era

Costume should be controlled by period, social role, and material realism.

Avoid:

```text
generic silky palace robes across all periods
overly glossy red-and-gold costume drama
fantasy embroidery
modern tailoring
court attire used for every social class
```

Use restrained materials:

```text
matte cloth
rough woven textile
aged ceremonial fabric
coarse commoner clothing
period-appropriate official clothing
muted dyes
worn hems
```

Exact clothing forms belong to the active era section.

### Architecture / Furniture / Props by Era

Architecture and furniture must not silently drift into later dynasty aesthetics.

Check the active era for:

```text
palace / court architecture
county office or administrative room
rural road / gate / wall
ancestral or ritual space
school or study space
furniture height
desk / mat / seating style
lighting objects
transport / carts
tools
weapons
seals
record containers
```

Do not mix obvious eras inside one shot.

Core rule:

```text
One shot should feel historically coherent before it feels cinematic.
```

### Record Material by Era

Use era-compatible record materials.

Do not use late imperial paper archive visuals for every period.

Possible record materials by era may include:

```text
bamboo slips
wooden tablets
silk manuscripts
folded paper records
cord-tied bundles
sealed packets
clay seal impressions
official seal boxes
ledger books
archive shelves
```

The active era decides which materials are appropriate.

Channel-level anti-readable-text rules still apply.

This file decides what kind of record material belongs to the era.

`CHANNEL_VEO_PROMPT_RULES.md` decides how to make the written marks unreadable, blurred, abstract, or visually neutralized.

### Anti-Era-Mixing Rule

Do not mix visually incompatible details inside one shot.

Examples of bad mixing:

```text
Warring States service men with Ming/Qing official caps
early bamboo-slip administration with late imperial paper libraries
Zhou aristocratic world with Song scholar-gentry costume logic
Qin-Han administrative rooms with Qing queue hairstyles
ancient clan ritual space with modern printed books
late imperial furniture inside early aristocratic halls
```

If a prompt needs symbolic compression across eras, it must be declared as a concept montage or EP-level symbolic visual, not treated as literal era reconstruction.

### Broad-Episode / Symbolic Compression Rule

Some China episodes may cover a broad period or compare multiple periods.

Broad does not mean random.

If the episode is not locked to a single dynasty, define the broad active era range from the brief or projectbeat task, then use only compatible visual details from that range.

If a shot uses one era-specific visual cue, do not mix it with incompatible details from another era unless the shot is explicitly designed as a symbolic montage.

Symbolic montage must be clearly declared as symbolic.

---


# CHINA SOCIAL ROLE / CLASS VISUAL TRANSLATION LOCK

This section controls China-specific social-role embodiment across eras.

Use it together with the active era section.

The active era decides the exact clothing form, hair, headwear, furniture, architecture, record material, and props.

This section decides how different social positions should read visually through:

```text
posture
spatial access
material quality
surface preservation
body position
object family
social distance
ritual or administrative placement
```

Core rule:

```text
Do not make every China subject look like the same poor villager, the same palace official, or the same generic scholar.
```

Status should be readable without text.

Privilege should look protected, preserved, and spatially controlled.

Poverty or labor should look exposed to material pressure, not theatrically miserable by default.

---

## Imperial / Court Authority

Function:

```text
visible state authority
ritual sovereignty
central command
court hierarchy
```

Visual signs:

```text
elevated platform
deep formal axis
ranked officials
controlled distance
ceremonial textile
large institutional scale
restricted access
```

Material logic:

```text
matte ceremonial cloth
aged high-status wood or stone
formal but worn court surfaces
restrained ornament
protected inner space
```

Avoid:

```text
heroic emperor worship
glossy dragon spectacle
beauty-lit ruler portrait
fantasy throne glow
Ming/Qing court clothing used for every era
```

Era section decides the exact robe, cap, platform, architecture, and ceremonial object.

---

## Officials / Clerks / Bureaucratic Layer

Function:

```text
turn command into records, taxes, law, registration, and procedure
mediate between throne and society
```

Visual signs:

```text
low or formal work desks depending on era
seals or sealed packets where appropriate
record containers
measuring tools
counting rods or ledgers depending on era
clerks placed between authority and commoners
```

Material logic:

```text
plain functional garments
handled desk surfaces
worn administrative tools
matte wood
orderly storage
practical headwear according to era
```

Spatial logic:

```text
bureaucratic figures often sit or stand behind the table, gate, desk, or threshold
commoners often approach from exposed foreground or exterior space
```

Avoid:

```text
modern office posture
modern desk props
generic scholar robes for every clerk
late imperial paper office visuals in early eras
```

---

## Scholar / Literati / Educated Layer

Function:

```text
education
moral interpretation
examination or recruitment access
family investment becoming public authority
```

Visual signs:

```text
books or study materials appropriate to era
brushes and inkstones where appropriate
school or study space
teacher-student hierarchy
quiet indoor access
slower posture
```

Material logic:

```text
finer but matte cloth
protected study surfaces
controlled interior space
worn scholarly tools
restrained colors
```

Avoid:

```text
turning all educated men into late Song/Ming/Qing scholars
projecting examination culture into eras before it is mature
overly clean scholar fantasy
modern classroom layout
```

Era section decides whether the figure is early Shi, Han official, Tang scholar, Song literati, Ming/Qing gentry, or another period-specific form.

---

## Local Elite / Landed Household / Clan Authority

Function:

```text
land control
family continuity
local reputation
marriage value
lineage memory
ritual authority
```

Visual signs:

```text
inner-room access
ancestral hall or clan courtyard when relevant
elders seated deeper inside
younger or lower-status figures nearer the threshold
land records or genealogy bundles as supporting props
controlled empty space
preserved household surfaces
```

Material logic:

```text
aged fine woven fabric
protected dark wood
maintained stone or brick
formal seating distance
old household objects
reserved interior light
```

Social reading:

```text
elite status should read through access, distance, posture, preservation, and control of space — not through shiny luxury.
```

Avoid:

```text
making local elites look like impoverished peasants
making them look like palace royalty by default
generic villain council imagery
conspiracy-room silhouettes
```

---

## Merchant / Broker Layer

Function:

```text
exchange
credit
transport
price mediation
marriage or local network brokerage
movement between official and local worlds
```

Visual signs:

```text
weighing tools
goods bundles
market edge
transport carts
accounting objects appropriate to era
negotiation posture
standing between two groups
```

Material logic:

```text
practical but better-kept garments than laborers
handled goods
wooden boxes
cloth bundles
scales or counting tools where era-appropriate
road / market / office threshold spaces
```

Avoid:

```text
modern shopkeeper look
overly comic merchant caricature
anachronistic coins, books, or account ledgers outside era fit
```

---

## Commoner / Farmer / Labor Layer

Function:

```text
tax burden
labor duty
grain production
transport
exposure to extraction
visible cost of order
```

Visual signs:

```text
grain sacks
baskets
muddy road
field edge
worn tools
bent or burden-bearing posture
waiting lines
exposed exterior space
```

Material logic:

```text
coarse natural cloth
worn hems
rough fibers
mud
wet earth
weathered wood
work-marked hands
simple tied hair or cloth headwraps according to era
```

Avoid:

```text
turning all commoners into famine victims unless the narration requires it
modern peasant clothing
clean costume-drama villagers
generic misery montage without mechanism
```

---

## Soldier / Military Layer

Function:

```text
organized force
frontier logistics
state coercion
command execution
military administration
```

Visual signs:

```text
formation discipline
weapons appropriate to era
armor appropriate to era
supply carts
command objects
camp or gate space
```

Material logic:

```text
worn leather
matte metal
rough command surfaces
transport materials
weathered armor
practical belts and bindings
```

Avoid:

```text
fantasy armor
wuxia sword hero framing
samurai-like armor
Ming/Qing firearms in earlier eras
gunpowder weapons before appropriate periods
```

---

## Ritual Elder / Lineage Authority

Function:

```text
belonging
ancestral legitimacy
moral hierarchy
family discipline
ritual gatekeeping
```

Visual signs:

```text
ancestral tablets
altar table
ritual vessels
lineage shelf
elder seated deeper inside
junior figure lower or nearer the threshold
formal bowing
family groups arranged by rank
```

Material logic:

```text
aged ritual wood
matte ceremonial objects
preserved interior surfaces
formal cloth
quiet dusted light
protected ancestral space
```

Avoid:

```text
glowing temple fantasy
heavy mystical smoke
religious spectacle detached from family hierarchy
generic archive room replacing lineage space
```

---

## Women in Family / Marriage / Lineage Scenes

Function:

```text
marriage alliance
kinship absorption
family continuity
ritual belonging
status conversion
```

Visual signs:

```text
bridal procession when era-appropriate
red betrothal gifts when culturally appropriate to the period and scene
family elders witnessing
two family groups facing each other
ancestral tablets or family hall background
threshold movement into household or lineage space
```

Material logic:

```text
formal but era-appropriate garments
restrained textile quality
family-space placement
ritual objects as supporting props
controlled body posture
```

Avoid:

```text
romantic palace-drama framing
modern wedding staging
beauty commercial styling
marriage shown only as signed paperwork
```

Era section decides the exact clothing, hairstyle, ritual object, interior layout, and color logic.

---

## Social Role QC

Before writing projectbeat `viewer_sees` or `prompt_raw`, check:

```text
Can the viewer tell who has access and who is exposed?
Can the viewer tell who works, who waits, who records, who receives, who witnesses, and who decides?
Do the costume, hair, props, furniture, and architecture match the active era?
Does elite status read through protected space and material preservation, not shiny luxury?
Does commoner status read through labor, exposure, and material pressure, not generic misery?
Do clerks and officials look like administrative operators, not generic scholars?
Do lineage scenes show belonging and threshold, not just paperwork?
Does the shot avoid mixing visually incompatible dynasties?
```

If the answer fails, revise the shot using the active era section and this social-role lock.

---


# ERA 01 — ZHOU / SPRING AND AUTUMN / WARRING STATES  
## Approx. 770–221 BCE

Use this section for episodes about:

```text
Eastern Zhou
Spring and Autumn
Warring States
pre-Qin aristocratic order
early service men / Shi
regional courts
lineage aristocracy
state formation before Qin unification
```

---

## ERA 01 VISUAL IDENTITY

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
Qing queue hairstyles
high chairs
gaiwan tea cups
fantasy armor
```

---

## ERA 01 COSTUME

### General aristocratic / service class

Use:

```text
deep robes / shenyi-like layered robes
cross-collar robes
moderate wide sleeves
rough silk
hemp
jute
muted earth tones
undyed cloth
dark browns
black-green
faded ochre
dusty grey
```

For men:

```text
topknot
cloth head covering
small wood or bronze cap
natural beard
simple belt
plain shoes
```

Avoid:

```text
Ming round-collar official robes
Qing queue hairstyle
Tang putou hats
Song scholar caps unless period-specific
overly flowing wuxia robes
bright satin costume-drama fabric
```

---

## ERA 01 QIN STATE SUB-LOCK

Use this when the visual state is specifically Qin or proto-Qin.

Visual identity:

```text
austere
disciplined
militarized
practical
minimal ornament
black and dark blue-black preference
```

Hair:

```text
asymmetric topknot
right-side topknot
tightly bound back hair
functional military hair binding
```

Clothing:

```text
black or blue-black practical garments
compact robe design
less ornament
square-plate armor
armor protecting neck and shoulders
```

Weapons:

```text
long Qin sword
bronze / early iron weapon look
crossbow
spear
military tally
```

Avoid:

```text
soft court luxury
bright embroidered robes
Tang / Ming / Qing styling
wuxia sword fantasy
```

---

## ERA 01 ARCHITECTURE

Use:

```text
wooden halls on rammed earth platforms
high platform court buildings
straight sloped rooflines
no dramatic upturned eaves
timber columns
earth walls
bronze fittings
painted but weathered details
cloud and phoenix motifs in restrained form
regional compounds
```

Avoid:

```text
Forbidden City architecture
highly curved flying eaves
yellow glazed imperial tiles
late imperial red walls
overly ornate palace corridors
```

---

## ERA 01 WEAPONS / MILITARY

Use:

```text
bronze jian
bronze spear
long spear
wooden shields with leather covering
painted shield patterns
crossbow for Qin contexts
chariots if appropriate
leather armor
lamellar or square plate armor for Qin
```

Avoid:

```text
gunpowder weapons
cannons
Ming/Qing firearms
fantasy oversized swords
samurai-style armor
modern military gear
```

---

## ERA 01 DOCUMENTS / ADMINISTRATION

Use:

```text
bamboo slips
wooden tablets
cord-tied records
clay seals
bronze seals
counting rods
low desks
floor mats
scribes kneeling or sitting low
```

Avoid:

```text
modern bound books
modern paper libraries
printing press look
late imperial desk furniture
modern office props
```

---

## ERA 01 SOCIAL SETTING

Useful visual spaces:

```text
regional court hall
ancestral ritual space
lineage archive
military planning tent
low administrative room
road checkpoint
grain storage area
aristocratic compound
service-man threshold
```

Key interactions:

```text
kneeling on mats
bowing in ritual order
hands unrolling bamboo slips
seal pressed into clay
messenger kneeling with command
service man waiting at threshold
officials debating around low table
```

---

## ERA 01 ANTI-ERROR RULES

Do not use:

```text
high chairs
gaiwan tea cups
Qing queue hairstyle
Ming/Qing official robes
Forbidden City palace style
yellow glazed tile imperial palace
Tang luxury hair and gowns
Song literati tea-house look
modern paper stacks
readable modern-looking characters
```

---

# ERA 02 — QIN IMPERIAL / EARLY UNIFICATION  
## Approx. 221–206 BCE

Use this section for:

```text
Qin unification
centralized command
standardization
military administration
legalist state machinery
imperial extraction
early empire formation
```

---

## ERA 02 VISUAL IDENTITY

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
rammed earth walls
military roads
standardized records
seal impressions
crossbows
cold administrative spaces
```

Avoid:

```text
soft court romance
ornate Tang luxury
Ming/Qing palace richness
wuxia elegance
glowing emperor mythology
```

---

## ERA 02 COSTUME / HAIR

Use:

```text
dark practical robes
black / blue-black palette
functional belts
tight topknots
asymmetric or practical military hair binding
minimal ornament
```

Armor:

```text
square armor plates
lamellar armor
neck and shoulder protection
rough leather ties
```

Avoid:

```text
flowing fantasy robes
colorful silk spectacle
Qing queue
Ming buzi official patches
Tang putou hats
```

---

## ERA 02 ARCHITECTURE / OBJECTS

Use:

```text
rammed earth fortifications
austere court interiors
military barracks
standardized office spaces
low tables
bamboo records
wooden administrative boards
seal boxes
law tablets
crossbow racks
```

Avoid:

```text
Forbidden City style
late imperial furniture
lavish palace halls
decorative palace plaques
```

---

## ERA 02 ANTI-ERROR RULES

Do not use:

```text
high Tang color palette
Ming/Qing official robes
Qing queue hair
gunpowder weapons
modern maps
modern paper documents
ornate dragon throne spectacle
```

---

# ERA 03 — HAN DYNASTY  
## Approx. 206 BCE–220 CE

Use this section for:

```text
Han bureaucracy
early imperial expansion
state offices
Confucian institutionalization
frontier logistics
granaries
household registration
imperial administration
```

---

## ERA 03 VISUAL IDENTITY

The world should feel:

```text
broad
imperial
expanding
administrative
earth-and-brick
early bureaucratic
more mature than Qin but not late imperial
```

Palette:

```text
black with red accents
earth clay
lime white
grey brick
muted red
dark wood
```

---

## ERA 03 COSTUME

Use:

```text
cross-collar layered robes
overlapping collars
multiple layers
wide but controlled sleeves
rectangular official caps
Jinxian-style cap / forward-peaked official cap where appropriate
dark robes with red accents
plain bureaucratic garments
```

For women:

```text
high but moderate waist skirts
layered robes
restrained fabric
```

Avoid:

```text
Tang high-chest ruqun
Ming buzi official patches
Qing queue hairstyle
late imperial collar shapes
wuxia robes
```

---

## ERA 03 ARCHITECTURE

Use:

```text
grey brick
watchtowers / que towers at gates
rammed earth walls
tile ends with ancient motifs
courtyard offices
granaries
frontier posts
low furniture
mats
early imperial administrative halls
```

Avoid:

```text
Forbidden City walls
dramatically curved eaves
Tang glazed luxury
Ming/Qing palace interiors
high chairs for early Han contexts
```

---

## ERA 03 WEAPONS / MILITARY

Use:

```text
steel jian
single-edged Han dao
crossbows
spears
horse armor chest pieces
frontier supply carts
military registers
```

Avoid:

```text
bronze-only weapon look for late Han military
gunpowder
Ming/Qing firearms
fantasy swords
```

---

## ERA 03 DOCUMENTS / ADMINISTRATION

Use:

```text
bamboo slips
wooden tablets
sealed documents
counting rods
household registers
granary ledgers
tax records
low office desks
clerks on mats or low seating
```

Avoid:

```text
modern paper libraries
late imperial bookcases
Song examination halls unless explicitly later
gaiwan tea culture
```

---

## ERA 03 ANTI-ERROR RULES

Do not use:

```text
high chairs by default
gaiwan cups
Tang fashion
Ming/Qing official robes
Qing queue hairstyle
Forbidden City architecture
modern calligraphy scroll decor
```

---

# ERA 04 — TANG DYNASTY  
## Approx. 618–907 CE

Use this section for:

```text
Tang court
Silk Road cosmopolitanism
imperial capital
elite display
frontier administration
Buddhist-influenced spaces when required
```

---

## ERA 04 VISUAL IDENTITY

The world should feel:

```text
prosperous
cosmopolitan
broad
open
multi-cultural
more colorful than earlier eras
```

But for this channel, keep the look restrained:

```text
desaturated Tang color
worn silk
aged lacquer
dusty red columns
muted jade
faded gold
not glossy fantasy
```

---

## ERA 04 COSTUME

Men:

```text
round-collar robes
side slits
leather belts with modest fittings
putou headwear
soft wing-like hat forms
```

Women:

```text
high-waisted ruqun
shawl / pibo if appropriate
high elaborate hair buns for elite women
hairpins used with restraint
```

Avoid:

```text
Qing queue
Ming official patches
Song scholar-gentry simplicity if not appropriate
hyper-saturated Tang drama colors
fantasy immortal robes
```

---

## ERA 04 ARCHITECTURE

Use:

```text
large dougong brackets
red-painted columns
grey or greenish glazed roof tiles
slightly upturned eaves
broad palace or capital architecture
large wooden halls
urban market streets
Silk Road goods when appropriate
```

Avoid:

```text
Forbidden City-style Ming layout as default
Qing ornate carving
modern Chinese palace tourism look
```

---

## ERA 04 MATERIALS / PROPS

Use:

```text
worn silk
lacquer
ceramic vessels
wooden market stalls
paper documents
official belts
horse gear
trade goods
```

Avoid:

```text
gunpowder handheld weapons
Qing queue
Ming buzi patches
excessive glowing gold
wuxia flying sleeves
```

---

## ERA 04 ANTI-ERROR RULES

Do not use:

```text
Qing queue hairstyle
hand cannons
Ming/Qing robes
modern tea gaiwan as default
overly glossy Tang romance visuals
```

---

# ERA 05 — SONG DYNASTY  
## Approx. 960–1279 CE

Use this section for:

```text
mature bureaucracy
examination culture
scholar-officials
urban commercial life
printing and paper culture
lineage expansion
administrative refinement
```

---

## ERA 05 VISUAL IDENTITY

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

Palette:

```text
ink black
paper beige
muted brown
soft grey
weathered wood
washed-out green
low natural light
```

---

## ERA 05 COSTUME

Use:

```text
scholar robes
official robes with period-appropriate hats
simple layered garments
restrained fabric
muted colors
```

Avoid:

```text
Qing queue
Ming buzi patch robes unless late transition explicitly
Tang high-chest gowns
Warring States deep robes as default
```

---

## ERA 05 ARCHITECTURE / SPACES

Use:

```text
examination halls
urban streets
bookshops
lineage halls
paper archives
county offices
bridges
canals
wooden urban interiors
tea shops if period-appropriate
```

Avoid:

```text
gaiwan Qing-style tea as default
Forbidden City imperial visual dominance
wuxia sect architecture
```

---

## ERA 05 DOCUMENTS / ADMINISTRATION

Use:

```text
paper documents
printed books
examination papers
brushes
inkstones
official files
lineage records
tax ledgers
woodblock printing if appropriate
```

Avoid:

```text
bamboo-slip-only administration as default
bronze weapon emphasis
Qing visual elements
```

---

## ERA 05 ANTI-ERROR RULES

Do not use:

```text
Qing queue hair
Ming/Qing official patches unless explicitly later
Tang elite fashion
ancient bronze-only document systems
```

---

# ERA 06 — MING DYNASTY  
## Approx. 1368–1644 CE

Use this section for:

```text
Ming state
late imperial bureaucracy
Forbidden City context
official robes
gentry society
lineage institutions
maritime / taxation / examination contexts
```

---

## ERA 06 VISUAL IDENTITY

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

---

## ERA 06 COSTUME

Use:

```text
round-collar robes with metal buttons
official buzi rank badge patch
stiff winged official hat
formal court robe
gentry robes
```

Avoid:

```text
Qing queue hairstyle
Manchu changshan
Tang putou hats
Warring States deep robe default
```

---

## ERA 06 ARCHITECTURE

Use:

```text
Forbidden City-style architecture when relevant
red walls
yellow glazed roof tiles
highly curved eaves
monumental gates
formal courtyards
late imperial offices
ancestral halls
```

For documentary tone:

```text
aged paint
worn stone
dust
faded red
not glossy tourism color
```

---

## ERA 06 DOCUMENTS / PROPS

Use:

```text
paper registers
official files
wooden cabinets
rank badges
brushes
inkstones
lineage documents
tax ledgers
```

Avoid:

```text
bronze weapons as default military look
Qing queue
modern paper folders
fantasy palace props
```

---

## ERA 06 ANTI-ERROR RULES

Do not use:

```text
Qing queue hairstyle
Manchu clothing
Tang headwear
bronze Jian as default
overly pristine palace drama lighting
```

---

# ERA 07 — QING DYNASTY  
## Approx. 1644–1912 CE

Use this section for:

```text
Qing state
Manchu rule
late imperial court
queue hairstyle
banner institutions
late imperial bureaucracy
```

---

## ERA 07 VISUAL IDENTITY

The world should feel:

```text
late imperial
Manchu-influenced
ornate but controlled
bureaucratic
ritualized
multi-ethnic imperial
```

For channel tone, avoid making it overly decorative.

Prefer:

```text
aged ornament
faded lacquer
dusty halls
worn textiles
bureaucratic records
restrained court ritual
```

---

## ERA 07 HAIR

Use:

```text
queue hairstyle
front half shaved
long braid at back
```

This is Qing-specific.

Do not use queue hairstyle outside Qing unless the episode explicitly concerns Qing or post-Qing legacy.

---

## ERA 07 COSTUME

Use:

```text
changshan / long robe
magua short jacket
high stiff collars
Manchu-influenced court robes
early qipao / Manchu changsam for women when appropriate
horse-hoof shoes for Manchu women if relevant
```

Avoid:

```text
Tang putou
Ming winged official hat
Warring States deep robes
Han official caps
```

---

## ERA 07 ARCHITECTURE

Use:

```text
late imperial palace complexes
ornate carving
multi-color painted details
red walls
glazed roofs
bureaucratic offices
banner spaces
```

For channel tone:

```text
desaturate colors
show age and dust
avoid tourist-postcard gloss
```

---

## ERA 07 DOCUMENTS / PROPS

Use:

```text
paper records
official memorials
wooden cabinets
Manchu-Chinese bureaucratic setting when appropriate
court documents
seals
```

Avoid:

```text
bronze sword era visuals
Warring States armor
Tang fashion
modern republican clothing unless late transition is explicit
```

---

## ERA 07 ANTI-ERROR RULES

Do not use:

```text
queue hairstyle outside Qing
Ming official hat
Tang robes
bronze Jian as default
ancient bamboo-slip bureaucracy
```

---

# CONTENT GROUP BANK — CHINA SESSION

These are optional scene families for China Session visual planning.

Use them only when they fit the episode.

Do not turn them into generic costume drama.

---

## GROUP 01 — GREAT HALL POLITICS

Use for:

```text
court discussion
state deliberation
ruler-official tension
formal political space
```

Visual ingredients:

```text
large wooden hall
columns
low court mats for early periods
officials in ranked space
dim candle or oil light
sealed documents
ritual distance
```

Era caution:

```text
Spring and Autumn / Han: kneeling or low seating
Tang / Ming: standing or more formal court posture when appropriate
```

Avoid:

```text
heroic emperor pose
ornate spectacle
readable plaques
fantasy glow
```

---

## GROUP 02 — STRATEGIC WAR ROOM

Use for:

```text
planning
frontier tension
map consultation
military reform
logistics before battle
```

Visual ingredients:

```text
military tent
dark study room
period-appropriate map
sand table
tally sticks
supply records
sword or command object
```

Era caution:

```text
early periods: bamboo or wooden maps / rough maps
later periods: paper maps
```

Avoid:

```text
modern maps
fantasy battle planning
dramatic trailer table glow
```

---

## GROUP 03 — BATTLEFIELD LOGISTICS

Use for:

```text
marching
grain transport
supply lines
camp organization
state extraction through war
```

Visual ingredients:

```text
rough roads
carts
grain sacks
disciplined soldiers
campfires
dust
mud
mountain roads
```

Avoid:

```text
battle spectacle as default
slow-motion hero combat
wuxia choreography
```

---

## GROUP 04 — SCHOLAR / LITERATI RESERVE

Use for:

```text
study
writing
education
withdrawal from court
elite cultivation
moral language
```

Visual ingredients:

```text
brush
inkstone
paper
books
simple study room
bamboo grove only when appropriate
rough wine jar
plain desk
```

Avoid:

```text
romantic immortal scholar fantasy
overly scenic poetry montage
floating robes
```

---

## GROUP 05 — ANCIENT MARKET / COMMON LIFE

Use for:

```text
tax burden
commercial life
common people
labor
village economy
public registration
```

Visual ingredients:

```text
rough cloth
brown and grey garments
dusty road
market stall
food smoke
manual labor
baskets
carrying poles
mud
```

Avoid:

```text
tourist market postcard
bright lantern fantasy
modern street food look
```

---

## GROUP 06 — INNER PALACE MELODRAMA

Status:

```text
Use with caution.
Not part of default channel visual language.
```

Can be used only when the episode specifically requires:

```text
inner palace politics
elite household ritual
court women
succession crisis
palace domestic space
```

Avoid by default because it can push prompts toward:

```text
costume drama
romance
palace intrigue melodrama
silk glamour
perfumed smoke
beauty-shot framing
```

If used, apply:

```text
restrained documentary framing
desaturated palette
institutional pressure
no seductive framing
no glamorous melodrama
```
