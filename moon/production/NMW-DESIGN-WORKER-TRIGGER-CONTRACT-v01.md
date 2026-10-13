# New Moon World｜Design Worker Trigger Contract v01
Date: 2026-10-13
Status: EXECUTABLE CONTRACT / first-wave paths verified where noted
Rule: No Evidence, No PASS

## Verified execution environment
### Node-02 / DESKTOP-O0BQMKS
- Blender: C:\Program Files\Blender Foundation\Blender 4.5\blender.exe  [VERIFIED]
- Python: C:\DAYONG_AI\paper2-crossnode-replication\runtime\python311\python.exe  [VERIFIED]
- Node: C:\DAYONG_AI\tools\node\node-v24.20.0-win-x64\node.exe  [VERIFIED]
- FFmpeg: C:\DAYONG_AI\tools\ffmpeg\ffmpeg-9.0.1-essentials_build\bin\ffmpeg.exe  [VERIFIED]
- Git: C:\DAYONG_AI\tools\git\cmd\git.exe  [VERIFIED]

### Node-01 / DESKTOP-9KDDRT3
- Blender: NOT FOUND in current command/path probe
- Python: C:\Users\user\AppData\Local\Programs\Python\Python312\python.exe [VERIFIED]
- Node: C:\Program Files\nodejs\node.exe [VERIFIED]
- FFmpeg: C:\Users\user\AppData\Local\Microsoft\WinGet\Packages\Gyan.FFmpeg_Microsoft.Winget.Source_8wekyb3d8bbwe\ffmpeg-9.0-full_build\bin\ffmpeg.exe [VERIFIED]
- Git: C:\Program Files\Git\cmd\git.exe [VERIFIED]

First-wave policy:
- 3D creation workers execute on Node-02.
- Web/runtime/code workers may execute on Node-01 or Node-02.
- Material Maker and other GUI-first tools are NOT hard dependencies of Worker v01.
- GUI tools may become optional enrichers after a CLI/API trigger is verified.

---

# Common Task Envelope
Every worker consumes one task JSON:

{
  "task_id": "NMW-...",
  "center": "INTERIOR|ARCHITECTURE|LANDSCAPE|CITY|CHARACTER|ASSET3D|NPC|RUNTIME|QA",
  "scene_id": "Sxxx",
  "project_id": "NEW-MOON-WORLD",
  "input_refs": [],
  "requirements": {},
  "output_dir": "...",
  "acceptance": [],
  "requested_by": "NMW-GAME-DIRECTOR"
}

Worker must create:
- execution.log
- result_manifest.json
- sha256.txt
- status.json

status.json cannot self-declare PASS. Worker may only write:
QUEUED / CLAIMED / RUNNING / READY_FOR_REVIEW / BLOCKED / FAILED

PASS is written only by verifier/QA.

---

# 1. Interior Design Worker
## Trigger
Node-02 Blender headless:

"C:\Program Files\Blender Foundation\Blender 4.5\blender.exe" ^
  -b ^
  --python C:\DAYONG_AI\nmw-workers\interior\worker_entry.py ^
  -- --task <TASK_JSON> --out <OUTPUT_DIR>

## Inputs
- room dimensions / room_id
- style profile
- required furniture
- material IDs
- interaction anchors
- architectural portal coordinates
- optional reference image / asset refs

## Worker actions
1. Read task JSON.
2. Build/open Blender scene.
3. Create/import room geometry and furniture assets.
4. Apply PBR materials available to worker.
5. Create collision/nav helper geometry.
6. Place sit/inspect/door/camera anchors.
7. Set lighting preset.
8. Export GLB.
9. Render one preview PNG.
10. Write manifest + SHA256.

## Outputs
- room_<room_id>.glb
- room_<room_id>.blend (optional source)
- preview.png
- interaction_anchors.json
- material_manifest.json
- collision_manifest.json
- result_manifest.json
- execution.log
- sha256.txt

---

# 2. Architecture Exterior Worker
## Trigger
"C:\Program Files\Blender Foundation\Blender 4.5\blender.exe" ^
  -b ^
  --python C:\DAYONG_AI\nmw-workers\architecture\worker_entry.py ^
  -- --task <TASK_JSON> --out <OUTPUT_DIR>

## Inputs
- building_id
- footprint / dimensions
- architectural family (EX-01 etc.)
- entrance coordinates
- landing-pad attachment requirement
- material IDs
- LOD budget

## Actions
- create/import exterior shell
- create door/entrance/portal anchors
- generate collision proxy
- generate/export LOD variants when requested
- attach material IDs
- export GLB + preview

## Outputs
- building_<id>_LOD0.glb
- optional LOD1/LOD2.glb
- collision.glb
- attachment_points.json
- material_manifest.json
- preview.png
- result_manifest.json
- execution.log
- sha256.txt

---

# 3. Landscape Worker
## Trigger
"C:\Program Files\Blender Foundation\Blender 4.5\blender.exe" ^
  -b ^
  --python C:\DAYONG_AI\nmw-workers\landscape\worker_entry.py ^
  -- --task <TASK_JSON> --out <OUTPUT_DIR>

## Inputs
- site boundary
- entrance/landing coordinates
- path endpoints
- landscape theme
- Earth-view / fireworks anchors
- asset refs

## Actions
- terrain/path block and smoothing
- import/place rock/plant/water/bridge/light assets
- generate walkable surface/collision helpers
- place viewing anchors
- export game-ready scene GLB

## Outputs
- landscape_<id>.glb
- nav_surface.glb/json
- anchors.json
- asset_manifest.json
- preview.png
- result_manifest.json
- execution.log
- sha256.txt

Note: Terrain3D can be added later as a terrain-generation adapter; it is not required for first real delivery.

---

# 4. City Planning Worker
## Trigger
Python, no Blender required for core planning:

"C:\DAYONG_AI\paper2-crossnode-replication\runtime\python311\python.exe" ^
  C:\DAYONG_AI\nmw-workers\city\worker_entry.py ^
  --task <TASK_JSON> --out <OUTPUT_DIR>

Optional blockout export may call Blender as subprocess.

## Inputs
- district requirements
- zoning doctrine
- NLU/land-unit rules
- population-density limits
- flight corridor constraints
- Earth-view corridor
- estate/building inputs

## Actions
- solve zone/district layout
- allocate persistent IDs
- produce walk/flight/public routes
- produce streaming cells and boundaries
- optionally generate blockout GLB via Blender

## Outputs
- masterplan.json
- zoning.json
- routes.json
- streaming_cells.json
- placement_contract.json
- optional city_blockout.glb
- result_manifest.json
- execution.log
- sha256.txt

---

# 5. Character / Gameplay Worker
## Trigger
Node.js:

"C:\DAYONG_AI\tools\node\node-v24.20.0-win-x64\node.exe" ^
  C:\DAYONG_AI\nmw-workers\gameplay\worker_entry.mjs ^
  --task <TASK_JSON> --out <OUTPUT_DIR>

or Node-01:
"C:\Program Files\nodejs\node.exe" ...

## Inputs
- scene_id
- player start/end state
- input scheme
- character asset ref
- animation clip map
- collision/nav refs
- interaction targets

## Actions
- generate/update controller module
- camera follow/collision config
- animation state mapping
- interaction trigger definitions
- desktop/mobile input mapping
- test harness page

## Outputs
- controller.js/mjs
- camera_config.json
- animation_state_machine.json
- interaction_registry.json
- test_page.html
- result_manifest.json
- execution.log
- sha256.txt

---

# 6. 3D Asset / Material Worker
## Trigger
Blender headless for first-wave automation:

"C:\Program Files\Blender Foundation\Blender 4.5\blender.exe" ^
  -b ^
  --python C:\DAYONG_AI\nmw-workers\asset3d\worker_entry.py ^
  -- --task <TASK_JSON> --out <OUTPUT_DIR>

## Inputs
- source asset or generation parameters
- Persistent Asset ID
- target poly budget
- texture budget
- material profile
- LOD requirements

## Actions
- import/clean asset
- normalize transforms/scale
- assign or bake available PBR maps
- generate collision proxy
- generate LOD where supported
- export GLB
- inspect missing textures

## Outputs
- <asset_id>.glb
- optional LODs
- collision.glb
- pbr_manifest.json
- asset_manifest.json
- preview.png
- result_manifest.json
- execution.log
- sha256.txt

Material Maker / MatLayer:
- optional adapters after CLI/headless behavior is independently verified.
- not required for Worker v01 delivery.

---

# 7. NPC / Agent Behavior Worker
## Trigger
Python or Node wrapper. Model provider is selected by task policy, not hard-coded into worker.

Example:
python C:\DAYONG_AI\nmw-workers\npc\worker_entry.py --task <TASK_JSON> --out <OUTPUT_DIR>

## Inputs
- npc_id
- role/persona
- scene/interaction IDs
- allowed actions/tools
- dialogue policy
- permission rules
- model routing policy (DeepSeek / Gemini / OpenAI / local)

## Actions
- call configured LLM adapter when needed
- generate behavior/state contract
- generate dialogue intent set
- bind interaction/nav IDs
- never expose API keys in outputs

## Outputs
- behavior_state_machine.json
- dialogue_contract.json
- tool_permissions.json
- interaction_bindings.json
- result_manifest.json
- execution.log
- sha256.txt

Important:
Model adapters must read keys from environment/secret store. Keys never enter task JSON.

---

# 8. Runtime Integration Worker
## Trigger
Node.js:

node C:\DAYONG_AI\nmw-workers\runtime\worker_entry.mjs --task <TASK_JSON> --out <OUTPUT_DIR>

## Inputs
- validated GLB/assets
- scene manifests
- gameplay modules
- interaction registry
- world/city streaming metadata

## Actions
- assemble runtime scene
- copy/bundle assets
- generate loader/scene graph
- wire interactions
- build playable web output
- emit deploy package

## Outputs
- dist/
- index/test HTML
- runtime_manifest.json
- asset_load_report.json
- integration_report.json
- execution.log
- sha256.txt

Deployment is a separate controlled step (GitHub -> Render), not silently performed by the worker unless task explicitly authorizes deploy.

---

# 9. QA / Evidence Worker
## Trigger
Python + FFmpeg:

python C:\DAYONG_AI\nmw-workers\qa\worker_entry.py --task <TASK_JSON> --out <OUTPUT_DIR>

FFmpeg path on Node-02:
C:\DAYONG_AI\tools\ffmpeg\ffmpeg-9.0.1-essentials_build\bin\ffmpeg.exe

## Inputs
- expected deliverables
- runtime URL/build path
- commit SHA/deploy ID
- acceptance gates

## Actions
- verify files exist/non-zero
- recompute SHA256
- validate manifests and IDs
- check GLB/load report
- gather performance evidence when instrumentation exists
- verify gameplay capture corresponds to build/commit
- mark REVIEW result, never fabricate PASS

## Outputs
- verification_report.json
- sha256_recomputed.txt
- evidence_manifest.json
- gameplay_capture.mp4 (only if actual capture mechanism is available and executed)
- status.json

---

# First Real Delivery Contract
## Task ID
NMW-REAL-INT-0001

## Center
INTERIOR

## Purpose
Produce the first non-synthetic game-ready room asset through the real Worker -> Tool -> Artifact -> SHA256 chain.

## Scope
Estate 001 / Living Room v01

## Minimum input
{
  "task_id": "NMW-REAL-INT-0001",
  "center": "INTERIOR",
  "scene_id": "S090",
  "project_id": "NEW-MOON-WORLD",
  "requirements": {
    "room_id": "ROOM-LIVING-001",
    "style": "premium interstellar residential / Japanese-modern restrained luxury",
    "dimensions_m": [8, 6, 3.2],
    "must_have": ["sofa","coffee_table","rug","earth_view_window","warm_lighting"],
    "interaction_anchors": ["SIT-001","INSPECT-TABLE-001"],
    "export": "GLB"
  }
}

## Required evidence
1. Real Task ID: NMW-REAL-INT-0001
2. Worker execution.log with start/end/command
3. Actual GLB file
4. preview.png
5. result_manifest.json
6. SHA256 independently recomputable
7. verifier identity/status
8. no TEST-/synthetic marker

## PASS definition
Only after QA independently recomputes SHA256 and successfully loads/checks the generated GLB.

---

# Worker Adapter Interface v01
All center adapters SHALL expose:

execute(task_json_path, output_dir) -> exit_code

Exit code:
0 = completed work and READY_FOR_REVIEW
10 = invalid task
20 = missing dependency/tool
30 = generation failed
40 = output validation failed

stdout/stderr must be captured into execution.log.

This interface is sufficient for CEO/D2 to implement Worker production skeleton without knowing internal artistic decisions.
