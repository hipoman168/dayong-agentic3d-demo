# New Moon World Production OS v01

## Command model
- Executive Producer / Game Director: ChatGPT 總設計中心
- Design Review Gate: D1 (DeepSeek)
- Source of Truth: GitHub repo + Google Drive asset cloud
- Runtime target: Web-first 3D game; engine decision gate Babylon.js vs PlayCanvas
- Rule: No Evidence, No PASS.

## Team lanes
1. GAME-DESIGN / EXPERIENCE — player flow, controls, camera, interaction, UI/HUD, animation states
2. CITY — district layout, routes, landing zones, commercial/public spaces, streaming boundaries
3. ARCHITECTURE — building exteriors, entrances, attachment points, collision, LOD
4. INTERIOR — room scenes, furniture, lighting anchors, interaction anchors
5. LANDSCAPE — garden paths, water, planting, viewing points, fireworks viewing space
6. 3D-ASSET — game-ready GLB/glTF, PBR, LOD, collision proxies, asset manifest
7. AI-AGENT / NPC — concierge, security, merchants, resident behavior and dialogue hooks
8. INTEGRATION / QA — scene assembly, runtime integration, FPS/VRAM/loading/navigation/evidence
9. D1 — design review only; approve/reject against NMW design constitution.

## Production unit
Every production unit is a Scene Card with:
- scene_id
- purpose
- player_start_state
- player_end_state
- camera
- character actions
- world assets
- NPCs
- interactions
- audio/VFX
- dependencies
- required deliverables
- acceptance criteria
- evidence links

## Vertical Slice 001 — First playable journey
### S000 LOGIN
Player sees premium lunar civilization identity, signs in / enters world.
End state: session authenticated, avatar/profile loaded.

### S010 SPAWN / WELCOME
Avatar spawns in premium lunar welcome pavilion.
Actions: idle -> orient camera -> first movement.
NPC: concierge makes first greeting.

### S020 GUIDED WALK
Player walks from welcome pavilion to private mobility court.
Systems: third-person controller, camera collision, locomotion state machine, navmesh, ambient NPCs.

### S030 CALL SPACECRAFT
Player interacts with call point.
System resolves vehicle ownership/permission and spawns assigned craft.

### S040 BOARD SPACECRAFT
Door animation, walk-to-seat, enter vehicle state, camera transition.

### S050 FLIGHT
Player rides/flys from Welcome District to Estate District.
World streaming: origin unload / destination preload.
Audio/VFX: restrained premium spacecraft motion.

### S060 LAND / DISEMBARK
Landing pad approach, docking, exit animation.
NPC/service staff receives player.

### S070 GARDEN APPROACH
Walk through premium landscape sequence toward residence entrance.
Garden, water, lighting, Earth View framing.

### S080 ENTER RESIDENCE
Door interaction + permission check.
Exterior -> interior streaming transition.

### S090 LIVING
Player freely walks inside living/dining zone.
Interactions: sit, inspect objects, talk to concierge, lighting scene.

### S100 PRIVATE ROOM
Master suite / Earth View.
End of Vertical Slice 001.

## Expansion backlog after Slice 001
- Fireworks event / public viewing district
- Shops, browsing, purchase/ownership
- Visiting other residents' homes with permission
- Restaurants/hotels/cultural events
- Public shuttle network
- Resident social interactions
- Commerce inventory/economy
- Festival/event scheduling

## Hard production gates
1. Design Gate — NMW premium civilization doctrine
2. Game-ready Asset Gate — no hero primitives
3. Runtime Gate — actual playable scene
4. Interaction Gate — actions work, not decorative buttons
5. Navigation Gate — character/NPC can traverse valid paths
6. Performance Gate — measured FPS/memory/loading
7. Evidence Gate — reproducible evidence before PASS
8. D1 Review — only after integration passes internal gates
