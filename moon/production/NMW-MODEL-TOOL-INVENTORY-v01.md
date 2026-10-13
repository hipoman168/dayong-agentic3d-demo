# New Moon World｜各設計中心模型與工具清單 v01
日期：2026-10-13
原則：Evidence First。狀態分為 ACTIVE / VERIFIED / CANDIDATE / RESEARCH / NOT YET CONNECTED。

## 0. 總策劃／總設計／任務分配
### 主模型
- ChatGPT GPT-5.6 Sol：總策劃、Game Director、任務拆解、依賴圖、整合決策、驗收規則。
- D1 / DeepSeek：設計審核與第二意見；不是第二個總策劃。
- Gemini：可作設計評審、視覺概念分析與多模態第二意見；目前應視具體 API/Agent 接線狀態判定是否 ACTIVE。

### 管理／派工工具
- DAYONG AgentOS v0.1：公司級 Agent 溝通／handoff contract，SOURCE-CONTRACT ONLY，尚未部署完成。
- NMW Production OS v01：遊戲製作任務拆解框架。
- NMW Task Queue v01：機器可讀任務佇列。
- GitHub：程式碼與任務／Evidence Source of Truth。
- Google Drive：大型資產、PBR、GLB/GLTF、備份與 Evidence。
- Render：線上測試頁／Playable Build 展示。
- Supabase：公司 Agent／任務／狀態資料平台候選，依現有表與權限接線。
- Desktop Commander：節點執行／檔案／程序控制；非長期唯一通道。

## 1. 建築外觀設計中心
### 模型
- ChatGPT GPT-5.6 Sol：需求拆解、建築語言、規格、權限／ID、技術整合。
- Gemini：外觀概念／視覺方案第二意見（需以實際接線狀態為準）。
- DeepSeek D1：最終設計 Gate。

### 工具
- Blender：建築幾何、GLB/glTF、LOD、Collision、材質掛載（規劃／需正式化流程）。
- Babylon.js：Web 3D runtime、glTF/PBR 載入、場景整合。
- PlayCanvas：Web-first 遊戲引擎候選，與 Babylon.js A/B 評估。
- Three.js：目前既有 NMW demo 使用；偏工程原型，不再作正式 Hero Scene 唯一標準。
- Material Maker / MatLayer：PBR 材質流程。
- GitHub + Google Drive：source / asset handoff。

### 主要交付
GLB/glTF、LOD0/1/2、Collision Proxy、Material IDs、Door/Entrance/Attachment Points、Interior Portals。

## 2. 室內裝修設計中心
### 模型
- ChatGPT GPT-5.6 Sol：空間规划、Room Flow、家具配置、互动点、Lighting preset。
- Gemini：室内风格、多模态视觉评审候选。
- DeepSeek D1：高端一致性审核。

### 工具
- Blender：房间、家具、灯具、空间组合。
- Babylon.js / PlayCanvas：室内 runtime。
- Material Maker / MatLayer：木、石、金属、玻璃、织物 PBR。
- glTF/GLB：正式游戏资产格式。
- PBR Maps：Albedo / Normal / Roughness / Metallic / AO / Emissive。
- Lighting JSON / camera anchors / interaction anchors：游戏交付规范。

### 主要交付
Room GLB、家具资产、Sit/Inspect Anchor、Door/Portal、Nav Surface、Collision、Day/Evening/Rest/Earth View Lighting Preset。

## 3. 庭園景觀設計中心
### 模型
- ChatGPT GPT-5.6 Sol：景观动线、观景点、游戏体验串联。
- Gemini：景观视觉审查候选。
- D1：设计 Gate。

### 工具
- Blender：石材、水景、植栽、桥、灯具等资产。
- Terrain3D：大型地形／LOD／terrain painting 研究与 PoC。
- Material Maker / MatLayer：岩土、石材、水景相关材质。
- Babylon.js / PlayCanvas：动态水面、植栽实例化、场景 runtime。
- NavMesh / Collision：步行路线与 NPC 导航。

### 主要交付
Garden Scene、Path、Water、Plant/Rock Assets、NavMesh、Collision、Earth View Anchor、Fireworks Viewing Anchor。

## 4. 城市规划中心
### 模型
- ChatGPT GPT-5.6 Sol：District、Zoning、Route、Streaming、Low-Density 高端城市规划。
- DeepSeek D1：总体设计审查。

### 工具
- JSON zoning / masterplan：已有 NMW 数据形式。
- Babylon.js / PlayCanvas：城市 runtime。
- Godot / Unreal 官方 World Partition / HLOD：作为大型世界流程学习参考，不代表当前 runtime 已迁移。
- OpenMW / Veloren：大型世界／开放世界架构研究。
- GIS/heightmap/terrain data：作为后续真实地形或月表数据输入。
- Streaming / LOD / HLOD / Instancing：必须纳入正式城市管线。

### 主要交付
District IDs、Zoning、Flight Corridors、Landing Zones、Streaming Cells、Earth View Corridors、Public/Private Mobility Routes。

## 5. 游戏人物・互动体验设计中心
### 模型
- ChatGPT GPT-5.6 Sol：Gameplay Flow、UI/HUD、角色状态、互动逻辑、第三人称体验。
- DeepSeek D1：体验与设计审核。

### 工具
- Three.js Soldier.glb：目前 Sprint 001 第三人称测试角色，仅工程测试资产，不是正式美术。
- Babylon.js / PlayCanvas：正式第三人称 runtime 候选。
- Godot 3D Demos：角色、Camera、Physics、Navigation 学习。
- Chickensoft GameDemo：第三人称、State Machine、Game State、Save/Load 学习。
- Unreal Third Person / Animation State Machine / NavMesh：流程与架构参考。
- Animation State Machine：Idle / Walk / Run / Turn / Sit / Talk / Enter Vehicle。
- Mobile input + Desktop input：正式支持对象。

### 主要交付
Player Controller、Camera、Animation State Machine、Interaction IDs、HUD、Mobile Controls、Gameplay Flow。

## 6. 3D 資產・材質中心
### 模型
- ChatGPT GPT-5.6 Sol：资产规范、Persistent Asset ID、质量门槛、LOD/PBR 标准。
- 图像／3D 生成模型：尚未固定单一正式模型，不得宣称已定型。
- Gemini 图像／视觉模型：可作为概念／检查输入，依 API 状态。
- 未来可评估开放 3D 生成模型，但需 License / topology / game-ready 验证。

### 工具
- Blender
- Material Maker 1.7
- MatLayer
- Terrain3D
- Babylon.js loaders
- glTF/GLB
- PBR pipeline
- mesh optimization / LOD / collision proxy
- Poly Haven CC0：现有部分 PBR / asset 来源
- Khronos / Three.js / Babylon sample assets：仅 PoC / pipeline 验证，不是正式美术。

### 主要交付
Game-ready GLB/glTF、PBR Maps、LOD、Collision Proxy、Asset Manifest、Persistent Asset ID、poly/texture budget。

## 7. AI Agent / NPC 行為中心
### 模型
- DeepSeek API：低成本 LLM 推理／NPC 对话候选主力之一。
- Gemini API：多模态／视觉／Agent 能力补充。
- ChatGPT / OpenAI Agents SDK：Agent 编排、handoff、tool use 候选。
- 本地小型 LLM：Qwen3-8B GGUF / llama.cpp，适合部分本地 NPC／低成本推理研究。

### 工具
- DAYONG AgentOS
- OpenAI Agents SDK
- Microsoft Agent Framework
- Supabase：状态／用户／权限／记忆／任务数据层候选
- NavMesh / Interaction IDs / Permission Hooks
- TTS：Kokoro 0.9.4，中文 zf_xiaobei 已有本地基准。
- Voice API：后续实时语音 NPC。

### 主要交付
Concierge、Security、Merchant、Resident Behavior、Dialogue Hook、Permission-aware Interaction、State Persistence。

## 8. 飞船／交通系统
### 模型
- ChatGPT GPT-5.6 Sol：交互、路线、权限、Gameplay 设计。
- D1：高级设计审查。

### 工具
- Blender：飞船模型、舱门、座椅、动画。
- Babylon.js / PlayCanvas：Vehicle controller、camera、FX。
- Animation / State Machine：Call → Arrive → Door Open → Board → Seat → Flight → Land → Exit。
- City Route / Flight Corridor data。
- Audio/VFX：引擎声、推进器、导航灯、landing FX。

### 主要交付
Private Spacecraft、Public Shuttle、Logistics Drone、Vehicle IDs、Seat/Entry Anchors、Flight Controller、Route、Landing Logic。

## 9. 程式／Runtime 工程中心
### 模型
- ChatGPT GPT-5.6 Sol：主要代码设计、review、debug、集成。
- DeepSeek：代码／架构第二意见、低成本执行候选。
- Gemini：代码／多模态问题辅助候选。

### 工具
- JavaScript / TypeScript
- Babylon.js
- PlayCanvas Engine
- Three.js（既有 PoC）
- Node.js
- npm
- Git / GitHub
- Render
- Supabase
- FFmpeg
- PowerShell / Python
- GitHub Actions
- WebGL2 / WebGPU
- glTF / GLB loaders

### 主要交付
Runtime、Scene Graph、Asset Loader、Streaming、Save/Load、Interaction Registry、Web/Mobile Build、QA instrumentation。

## 10. 整合／QA／Evidence 中心
### 模型
- ChatGPT GPT-5.6 Sol：整合判断、Evidence 审核、问题定位。
- D1：最终设计 Review。
- D2 阿凯：论文／研究线 review；若协助 NMW，只应作为工程／流程监督，不改变 D2 原本论文角色边界。

### 工具
- GitHub commit SHA
- Render deploy ID / live status
- Playable URL
- Browser screenshot / gameplay capture
- FFmpeg
- SHA256 / Evidence Freeze
- FPS / frame time / memory / loading metrics
- Google Drive Evidence archive
- DAYONG AgentOS handoff / task ledger

### PASS 规则
任何“完成”必须至少有对应 commit / asset / deploy / runtime evidence；视觉通过与技术通过分开；D1 Review 在内部 QA PASS 后才触发。

## 11. 目前建议的主技术路线
### Web-first
- Runtime：Babylon.js 与 PlayCanvas 首轮 A/B，尚未最终定版。
- Asset：Blender → GLB/glTF
- Material：Material Maker / MatLayer → PBR Maps
- World：District / Estate / Building / Room 分层
- Character：第三人称 Controller + Animation State Machine + NavMesh
- AI/NPC：DeepSeek / Gemini / OpenAI Agent layer + Supabase state
- Storage：Google Drive 大资产；GitHub 代码；Render 测试／展示

## 12. CEO / Dispatcher 需要的 Capability Tags
可将每个中心的能力注册成：
- GAME_DIRECTOR
- ARCHITECTURE
- INTERIOR
- LANDSCAPE
- CITY_PLANNING
- CHARACTER_GAMEPLAY
- ASSET_3D
- MATERIAL_PBR
- NPC_AGENT
- VEHICLE_SPACECRAFT
- RUNTIME_ENGINEERING
- QA_EVIDENCE
- D1_DESIGN_REVIEW

每个 Task 必须声明：
required_capabilities[]
preferred_models[]
required_tools[]
input_assets[]
deliverables[]
acceptance_gates[]
evidence_required[]
