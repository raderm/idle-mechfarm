# MechFarmer Prototype Clarification Checklist

Before writing initial prototype pseudocode, clarify these decisions so the first iteration is focused and testable.

## 1) Prototype Scope
- What is the minimum playable loop for v0? (example: plant -> maintain -> harvest -> survive one nightly attack)
- What should be explicitly out-of-scope for v0? (story, cosmetics, weather, multiplayer)
- What is the target session length for a “successful” early run? (10 min / 30 min / 1 hr)

## 2) Core Fantasy and Win/Lose Conditions
- What is the primary fantasy priority for v0: farm optimization, defense strategy, or AI behavior design?
- Is there a run “win condition” (reach day X, earn Y credits, survive Z waves)?
- What ends a run? (HQ destroyed, debt threshold, starvation, time limit)

## 3) Time Model and Game Pace
- How long is one in-game day?
- Does time always run, or can players pause and issue orders?
- How are actions scheduled (tick-based loop, continuous timers, or turn chunks)?
- What events should *always* be active once established (crop growth, upkeep drain, patrol/attacks, market changes)?

## 4) Farm Layout Model
- How many named areas does the starter farm have?
- Are areas fixed zones or expandable tiles?
- What constraints apply per area? (soil quality, defense slots, building cap, power budget)
- Can attacks target specific areas, and can area control be lost/recovered?

## 5) Actors: Player Character and Pawns
- How many controllable workers exist at start?
- Are pawns specialized (farmer/engineer/guard) or fully general?
- How are behavior patterns defined? (priority list, rule conditions, state machine, job queue)
- What happens when two tasks compete? (global priority, area priority, urgency score)

## 6) Economy and Resources
- What are the core currencies/resources in v0? (credits, biomass, power, ammo, parts)
- Which systems consume upkeep continuously versus on use?
- Are resources global or stored per area?
- How is selling/buying handled (static prices, market volatility, contracts)?

## 7) Crops and Production
- How many crop types for v0 (recommend 3–5)?
- What differentiates crops (growth time, yield, upkeep, risk, defensive synergy)?
- What are crop failure modes? (blight, neglect, raid damage, power outage)
- Is there processing/refining in v0, or only raw harvest sales?

## 8) Defense and Tower-Defense Layer
- What enemy types are in v0 and what behaviors do they use?
- How often do attacks occur and how does threat scale?
- Which defense categories exist for v0? (turrets, walls, traps, drones)
- Do defenses need staffing/ammo/power/repairs, and who performs upkeep?

## 9) Upgrade and Progression Structure
- What are the first 10–15 meaningful upgrades?
- Are upgrades permanent meta-progression, run-limited, or both?
- What should unlock new areas/buildings/defenses?
- How quickly should players unlock automation improvements?

## 10) Automation UX
- How do players author behavior patterns? (simple presets first, advanced rules later)
- What level of observability is required to debug automation decisions?
- Which “safety rails” prevent deadlocks or bad loops? (minimum reserve resources, auto-repair thresholds)

## 11) Data and Simulation Design (for pseudocode)
- What are the main entities and relationships? (Farm, Area, Actor, Task, Crop, Defense, Event)
- What update order is canonical each tick? (economy -> AI planning -> movement -> combat -> growth -> UI)
- Which values are deterministic versus randomized?
- What telemetry events should be emitted for charts?

## 12) UI and Analytics Requirements
- Which 3–5 charts are mandatory in v0? (income over time, threat level, labor utilization, upkeep burn, crop throughput)
- What is the critical “at-a-glance” HUD summary?
- How often should charts update and over what time windows?
- Should the prototype include playback/history scrubbing?

## 13) Technical Prototype Constraints
- Are we writing pseudocode in Godot-style architecture from day one? (nodes/scenes/signals)
- Do we target desktop only for prototype?
- What performance target should simulation meet? (entities, ticks/sec)
- What test harness is needed for balancing loops before full engine integration?

## 14) First Milestone Proposal
A practical v0 milestone to align around:
1. 3 farm areas with unique constraints.
2. 3 crops with distinct growth/upkeep profiles.
3. 3 defense options with power/ammo/repair upkeep.
4. 1 player character + 2 pawns using priority-based behavior rules.
5. Day/night loop with one nightly attack wave.
6. 4 core charts (credits, upkeep, harvest throughput, defense incidents).
7. Survive 7 days or hit bankruptcy/loss condition.

## 15) Decision Record Template
For each major decision, capture:
- **Decision**
- **Alternatives considered**
- **Chosen option + rationale**
- **Implications for systems/UI**
- **Open risks**

Using this template now will make the later Godot implementation much smoother.
