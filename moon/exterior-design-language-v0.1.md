# New Moon World — Exterior Design Language Library v0.1

Status: BASELINE / ADJUSTABLE
Purpose: Convert architectural reference material into reusable AI design constraints. Do not copy protected reference images or proprietary plans; extract design grammar, proportion, material, lighting, and spatial principles.

## Core rule

AI-generated buildings must remain unique while staying inside:
1. Parcel / Estate Build Envelope
2. Zoning / FAR / BCR / height / setback rules
3. Earth View corridor rules
4. Structural plausibility class
5. Persistent Building ID and version history

The AI may vary form, facade, material, lighting, landscape, entrance, balcony, roof, and glazing, but may not exceed the registered spatial authority.

## Exterior style families

### EX-01 Japanese Courtyard Modern
Design grammar:
- sheltered entry sequence
- framed garden view at arrival
- courtyard / tsuboniwa as organizing element
- warm timber + stone + plaster
- controlled openings rather than all-glass facade
- deep eaves / layered thresholds
- indoor-outdoor visual continuity
- Earth View framed as a deliberate focal view

Best for:
- villas
- low-rise residences
- boutique guesthouses

### EX-02 Contemporary Luxury Villa
Design grammar:
- layered setbacks
- cantilevered volumes
- strong horizontal and vertical composition
- large glazing at primary view facade
- natural stone / fair-faced concrete / metal panels / louvers
- restrained palette
- architectural lighting integrated into facade

Best for:
- R2 / R3 premium residential
- Earth View villas
- show homes

### EX-03 Sculptural Signature Residence
Design grammar:
- one dominant geometric idea
- curved / faceted / carved volume
- identifiable silhouette from district distance
- limited material palette
- entrance and balcony geometry tied to the main concept
- no arbitrary decorative noise

Best for:
- premium parcel owners
- landmark homes
- collector residences

### EX-04 Urban Mixed-Use Residential
Design grammar:
- strong podium / base
- residential tower above
- first-floor shopfront modules where zoning overlay permits
- separate residential and retail access
- facade rhythm aligned with unit grid
- balconies / bay windows / vertical fins for identity
- night lighting emphasizes podium and entrance

Best for:
- R3 / R4 with R_SHOP_1F overlay
- C1 mixed-use streets

### EX-05 Corporate / Office Landmark
Design grammar:
- facade derived from company identity or industry story
- brand motif translated into geometry, not pasted decoration
- lobby as major spatial marker
- daylight and transparency at public levels
- roof / crown allowed as brand signature within height limit

Best for:
- C1-C3 office / headquarters

### EX-06 Celestial Futurism
Design grammar:
- low-gravity-inspired cantilevers within structural plausibility
- pressure-shell references
- metallic / ceramic / glass composite palette
- integrated illumination
- Earth-facing observation elements
- landscape designed as a protected artificial oasis overlay

Best for:
- New Moon / New Mars signature architecture

## Facade parameter set

Every AI facade proposal must output:
- massing_family
- silhouette_signature
- podium_ratio
- setback_profile
- cantilever_depth
- facade_grid
- glazing_ratio
- earth_view_glazing_ratio
- roof_type
- entrance_type
- balcony_type
- material_palette[3..5]
- accent_material
- lighting_strategy
- landscape_strategy
- street_interface
- retail_frontage_if_allowed
- uniqueness_signature

## Material palette rules

Preferred premium material vocabulary:
- natural stone
- textured / fair-faced concrete
- dark anodized or brushed metal
- timber / engineered timber appearance
- high-performance glazing
- vertical louvers / screens
- ceramic / composite panels

Avoid:
- flat untextured boxes
- one-material facades
- repetitive identical balcony stacks without articulation
- uncontrolled glass boxes
- random decorative motifs without design logic

## Lighting design rules

### Exterior
- concealed linear lighting for edges / recesses
- wall-wash lighting on stone / textured surfaces
- entry focal lighting
- landscape path lighting
- avoid uniformly bright facades
- default residential warm-white target: 2700K–3200K visual intent

### Interior
Each room must have:
- ambient layer
- task layer
- accent layer
- indirect layer where appropriate
- scene presets: Day / Evening / Entertain / Rest / Earth View

## Visitor presentation modes

Every completed building should expose:
1. Hero Exterior
2. Front / Left / Right / Rear
3. Aerial / Site Context
4. Floor Plan
5. Dollhouse / Cutaway
6. Walkthrough
7. Interior Effect Views
8. Earth View scene(s)
9. Night Lighting scene
10. Design / Material board

## Uniqueness requirement

Before commit, AI must compare the proposal against the district's existing Building Signature Index.
Reject or regenerate if:
- silhouette similarity too high
- facade grid similarity too high
- same material + massing + roof combination repeats excessively
- Earth View solution duplicates a nearby signature building

## Reference-derived principles

- Contemporary luxury housing: proportion, layered massing, setbacks, cantilevers, large openings, stone / concrete / metal / glass, and night lighting should be designed as one system.
- Japanese residential precedent: courtyard, framed views, controlled circulation, natural light and quiet transition sequences can organize both facade and interior experience.
- Mixed-use precedent: facade design must integrate ground-floor shop function and separate access rather than treating retail signage as an afterthought.
- Corporate precedent: architecture can translate brand / industry identity into a recognizable geometric language.

## Product rule

New Moon World sells design freedom inside governed spatial limits:
“Every building may be unique. No building may ignore its parcel, zoning, view rights, or authority.”
