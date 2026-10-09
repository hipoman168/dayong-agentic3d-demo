# New Moon World｜Sprint 001 Kickoff
## Goal
Deliver the first playable 3rd-person entry experience.

## Scope
S000 Login → S010 Spawn / Welcome → S020 First Walk

## Player flow
1. Open New Moon World.
2. See premium lunar civilization entry screen.
3. Enter World.
4. Player avatar spawns in Welcome Pavilion.
5. Camera locks to third-person mode.
6. Player can Idle / Walk / Run / Turn / Stop.
7. Collision prevents walking through architecture.
8. Concierge NPC is visible at arrival point.
9. Player walks from spawn point to Mobility Court trigger.
10. Trigger S020_COMPLETE and unlock S030 Call Spacecraft.

## Team orders

### Experience Team
Deliver:
- login/enter flow
- player spawn
- third-person controller
- follow camera + camera collision
- keyboard/mobile input
- locomotion animation state machine
- S020 completion trigger

### City Team
Deliver:
- Welcome Pavilion district coordinates
- spawn point
- walk route
- Mobility Court destination
- nav/collision boundary
- streaming cell IDs

### Architecture Team
Deliver:
- Welcome Pavilion game-ready shell
- entrance/open area
- collision proxy
- camera-safe geometry
- LOD definition
- material IDs

### 3D Asset Team
Deliver:
- one production-quality humanoid avatar base
- one concierge NPC base
- game-ready GLB/glTF
- PBR textures
- animation clips or compatible rig
- persistent asset IDs

### NPC/Agent Team
Deliver:
- concierge idle state
- greeting trigger contract
- talk anchor
- nav anchor
- no autonomous roaming yet

### Integration Team
Deliver:
- runtime scene assembly
- actual playable URL
- input test
- collision test
- animation state test
- mobile load test
- evidence pack

## Runtime decision
Sprint 001 uses a controlled A/B gate:
- Babylon.js implementation candidate
- PlayCanvas implementation candidate

Decision is based on:
- third-person controller quality
- animation integration
- glTF pipeline
- mobile FPS
- loading behavior
- developer complexity

No engine is declared PASS until the same S000-S020 flow is proven.

## Acceptance Gate
Sprint 001 is PASS only when:
- real avatar is visible
- player input moves avatar
- camera follows avatar
- collision works
- locomotion animation transitions work
- player reaches destination trigger
- URL is playable on mobile
- commit/run/evidence exists

## Forbidden shortcuts
- no free-fly camera counted as player movement
- no screenshot/image counted as scene
- no Box/Sphere hero assets
- no "planned" or "started" status without evidence
- no self-approved team PASS
