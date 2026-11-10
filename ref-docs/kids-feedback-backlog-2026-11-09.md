# Kids feedback backlog — 9 Nov 2026 (rev 10 Nov)

Source: ~16 min call with Clara & Oskar, plus Adam’s planning notes (10 Nov).

**How to use this doc:** Phases are shippable planning chunks, not “all easy first.” Pick a phase, plan it, ship it. Items inside a phase are still ordered roughly easier → harder within that slice.

**Kids’ area priority (map work):** upstairs → basement → front yard → shed → under the house (as a hidden clubhouse). Attic via laundry called out with upstairs.

**Design gate:** New floors / yards / shed / under-house / attic need a draw.io room map before build. Marked **🗺️ needs draw.io**.

**What they already love (don’t break):** looks like their house; throwing / interacting; **glass** especially (pick up → throw → break = double reaction); throwing at Uncle Adam; Oskar’s Pizza; controls feel fine.

---

## Resource economy (explicit — one job each)

Decide once; keep items from overlapping roles.

| Item | Role | Notes |
|------|------|--------|
| **Leaf coins (🥬)** | **Shop currency only** | Earned from missions, breaks, chaos — *not* from eating lettuce for hearts. Keep the familiar 🥬 icon in the HUD/shop so existing muscle memory stays. |
| **Lettuce** | **Restores hearts only** | Garden / world lettuce heals. Does **not** add shop coins. |
| **Squash** | **Shell-bonk energy only** | Refills the meter that lets Lina tuck into shell and knock Uncle Adam over. Meter drains **very slowly** (gentle, not punishing). Always available at home base; also findable around the house. |
| **Strawberry** | **Sugar rush (speed) only** | Temporary speed boost. |
| **Apple** | **Jump boost only** | Temporary higher jump. (Named here so it isn’t conflated with strawberry/squash/lettuce.) |
| **Special dig food** (TBD name/look) | **Unlocks dig ability** | Mission-gated one-shot (or rare) pickup that starts the dig/cave milestone — not a general power-up. |

**Dropped for now:** wall-climb / sticky power-up; general hunger bar that drains for its own sake.

---

## Mission difficulty — how it works today

There is **no** easy / medium / hard banding in code.

- Always **up to 3 missions open**.
- They are simply the **next 3 unfinished entries** in the fixed `MISSIONS` array (`slice(0, 3)`).
- Finishing one unlocks the next in list order.

So the “easiest of the three” is **not** a sliding difficulty tier that stays “easy forever.” Early open slots are early-list missions (smash vases, disco, rafters…); later open slots are later-list missions (fridge top, bug hunt, drop-on-Adam…), which tend to be harder because the **list was authored that way**, not because a difficulty system is raising the floor.

**Implication for new content:** when we add upstairs / cave / RC missions, place them in the list (or redesign into true E/M/H lanes) deliberately. If we want “always one easy, one medium, one hard,” that would be a **new system** — call it out when planning Phase 5 / progression work; it does not exist yet.

---

## Tonight / near-term focus

1. **🗺️ Draw.io for upstairs** (and note attic access from laundry if it belongs on the same sheet).
2. Sketch **2–3 supporting missions** that only make sense once upstairs exists (explore a room, fetch something from upstairs, attic peek, etc.).
3. Optionally ship **Phase 0** polish in parallel — it doesn’t block the map.

---

## Phase 0 — Polish, pizza, thoughtful throwables

*Listen-and-respond update. No under-house “fix” here — that becomes the clubhouse (Phase 5).*

| ID | Ask | Notes / acceptance | Effort |
|----|-----|--------------------|--------|
| P0-1 | Spell **Oskar with a K** everywhere kids see it | Mission name, toasts, HUD, README if shown. “Oskar’s Pizza”. | XS |
| P0-2 | Add **crust / dough / bread** to Oskar’s Pizza | Extra collectible; bake still needs all ingredients. | S |
| P0-3 | Replace random balls/cubes with **thoughtful props** | Fewer, placed with intent (playroom toys; living-room adult objects). Toys kids want to throw; also books, lamps, TV-adjacent bits, etc. Not scattered junk everywhere. | S–M |
| P0-4 | **Varied break reactions** by object type | Glass → shatter burst; lamp → spark / shade flop; toy → bounce/pieces; screen/TV → crack; books already tumble. Lean into the double reaction they love. | M |
| P0-5 | Make **shop / skins** easier to notice | “I never found that.” Hint after first coins or first mission reward. Full mission-gating of cosmetics lands in Phase 3. | S |
| P0-6 | Confirm / fix **drag-to-look** | Free drag when not on stick/buttons; audit iPad hit targets vs JUMP/GRAB/SHELL. | S |

**Phase 0 exit:** Oskar + crust shipped; house feels full of *good* throwables with distinct break flavours; look/shop less mysterious.

**Moved out:** sealing / “fix fall under house” → **P5-6** (hidden turtle clubhouse).

---

## Phase 1 — Camera: see Lina + room unlock

*High playability. Includes the room-boundary lock Adam hit.*

| ID | Ask | Notes / acceptance | Effort |
|----|-----|--------------------|--------|
| P1-1 | Fade / hide **occluders** between camera and Lina | Raycast fade so furniture doesn’t eat her. | M |
| P1-2 | Better behaviour in **tight spaces** | Nudge distance / FOV near walls; pairs with occlusion. | M |
| P1-3 | **Investigate + fix room-locked camera** | Today `CAM_ROOMS` + `clipCamera()` keep the camera inside the current room’s AABB. Crossing living → playroom swaps the box, so orbit feels “stuck” / can’t swing the same way. **Investigate:** soft blend across doorways, shared volumes for open plans, allow camera in adjacent rooms with occlusion fade, or pull-in only on solid walls (not room labels). **Suggest a fix in the Phase 1 plan before coding.** | M |

**Phase 1 exit:** Lina stays visible; walking room-to-room doesn’t trap the orbit camera.

---

## Phase 2 — Uncle Adam lives in the house

*Adam can use the whole house from the start — not a late unlock.*

| ID | Ask | Notes / acceptance | Effort |
|----|-----|--------------------|--------|
| P2-1 | Adam **patrols / walks the whole house** | Living, playroom, hall, office, powder, garden access as collision allows. Enclosure remains a **safe zone** (he doesn’t scoop her there). | M |
| P2-2 | Adam **does stuff** when calm | Light ambient activities: cooking in kitchen, watering plants outside, puttering. Readable poses / short loops — not full AI sim. | M–L |
| P2-3 | Adam as **cleanup dad** after chaos | When kids break / scatter things, Adam can fetch a broom (or similar), “clean,” and **restore / replace** the broken prop to its home pose. Turns their favourite chaos into a living reaction loop. | L |

**Phase 2 exit:** Adam feels present everywhere; breaking stuff sometimes summons cleanup; enclosure stays safe.

---

## Phase 3 — Hearts, shell energy, food powers, gated rewards

*Systems + progression gamification. Uses the economy table above.*

| ID | Ask | Notes / acceptance | Effort |
|----|-----|--------------------|--------|
| P3-1 | Context **INTERACT** control | Food → eat; ladder/switch → use; else grab/throw as today. | M |
| P3-2 | **Hearts** start at **3** | Catch = lose a heart. 0 hearts → back to enclosure (not instant every catch). | M |
| P3-3 | **More max hearts via mission progress** | Completing missions raises max hearts (3 → 4 → 5…). | M |
| P3-4 | **Lettuce restores hearts** | Eat lettuce → refill hearts. Not currency. | S–M |
| P3-5 | **Squash = shell-bonk meter** | Meter required (or strongly gated) to shell-bonk Adam. Refill at home-base squash and world squash. Drains **very slowly**. No general hunger bar. | M |
| P3-6 | **Strawberry = sugar rush (speed)** | Temporary. | M |
| P3-7 | **Apple = jump higher** | Temporary. No wall-climb. | M |
| P3-8 | **Mission-gated shop unlocks** | Skins / boosts **visible but locked** until a themed mission (or mission count) unlocks purchase. Still costs leaf coins after unlock. On-theme: mission about disco → disco shell, etc. Gamify progress. | M–L |
| P3-9 | Shop sells **boosts** as well as skins | Jump / speed / shell-related perks that fit the economy. | M |

**Phase 3 exit:** Lives + shell energy + two food boosts feel clear; shop shows locked-on-theme rewards that open with progress.

---

## Phase 4 — Characters & garden vertical (same map)

*Photos / map callouts from Adam still incoming for cats + tree.*

| ID | Ask | Notes / acceptance | Effort |
|----|-----|--------------------|--------|
| P4-1 | Russian tortoise **“Strawberry”** (smaller than Lina) | Companion / NPC; look up real Russian tortoise. | L |
| P4-2 | Cats **Tony & Joey** (personalities) | **Tony:** more scared — Lina can chase him; sometimes he hides, then **pounces and flees**. **Joey:** curious / playful — chases, paws, follows, sniffs. (Reference photos from Adam.) Not just maneki-neko gates — living cat AI. | L |
| P4-3 | Harder routes / timing challenges | Use cats and layout without soft-locking missions. | M |
| P4-4 | **Tree climbing wall + tree house** | Placement from Adam’s map mark. Climb + platform; 1–2 tree missions. | L |
| P4-5 | **Interact ladder** on tree | Pull up/down. Adam climbs only if down. Pull while he’s on it → bonk-equivalent fall. | L |

**Phase 4 exit:** Cats feel like Tony vs Joey; garden has a vertical play space.

---

## Phase 5 — New spaces + supporting missions

*Map first. Upstairs is the priority build after draw.io. Under-house is a **bonus clubhouse**, not a bugfix.*

| ID | Ask | Notes / acceptance | Effort |
|----|-----|--------------------|--------|
| P5-0 | **🗺️ draw.io** per space (upstairs tonight) | Same workflow as ground floor. | Design |
| P5-1 | **🗺️ Upstairs** + **supporting missions** | Unlock stairs; rooms at real scale. Ship with missions that require going up (milestone feel). | XL |
| P5-2 | **🗺️ Attic** via laundry entrance | Big space; good future spawn / hideout hook. | XL |
| P5-3 | **🗺️ Basement** | Kids’ #2. | XL |
| P5-4 | **🗺️ Front yard** | Distinct from current garden. | XL |
| P5-5 | **🗺️ Shed interior** | Enter the existing shed shell. | L–XL |
| P5-6 | **🗺️ Under-house turtle clubhouse** | Soften / hide the obvious fall-through so it isn’t a trap. Falling in (when they find it) drops into a **bonus turtle party clubhouse** — celebration space, not a void. | L–XL |

**Build order after maps:** upstairs (+ missions) → attic → basement → front yard → shed → clubhouse.

**Phase 5 exit:** Upstairs playable with new missions; clubhouse designed as intentional secret.

---

## Phase 6 — Dig caves as milestone missions (GTA-garage hideouts)

*Each new cave is a mission milestone, not a free dig-anywhere sandbox.*

| ID | Ask | Notes / acceptance | Effort |
|----|-----|--------------------|--------|
| P6-1 | **Mission: find special food → unlock dig** | Milestone mission: get the dig food, then dig the marked hotspot. | L |
| P6-2 | **Hotspots** on the map | Dig sites look different once opened. Mission can highlight “find the spot.” | M |
| P6-3 | Cave = **virtual interior** (GTA garage style) | Entering the hotspot opens a larger cave space **not** bound to the wall thickness — stash / hangout / spawn. | L–XL |
| P6-4 | Cave **utility** | Lettuce for hearts; occasional special power-up spawn so kids revisit. Also **spawn points**. | M |
| P6-5 | **Spawn picker** | On heart-out: choose enclosure / Cave 1 / Cave 2… (pictures / names). | M–L |
| P6-6 | **Decor / rewards inside caves** | Unlock furniture & flair as missions complete; place in hideouts. New cave always tied to exploring a new map part or milestone mission. | XL |

**Phase 6 exit:** At least one dig mission → virtual cave → spawn + revisit loop.

---

## Phase 7 — Vehicles & moonshots

| ID | Ask | Notes / acceptance | Effort |
|----|-----|--------------------|--------|
| P7-1 | **RC car** (scoped) | Mostly visual mount: Lina + car moves **faster**, **no jump**, can ride off stairs. **Battery drains**; recharge / swap batteries (caves are a good source). Introduced with a **mission** that needs the car — e.g. backyard ramp jump **over Uncle Adam**, who sits/lies down in the yard for that mission until it’s done. | XL |
| P7-2 | **Drone** picks Lina up | Still ambitious; park after RC car learnings. | XL |
| P7-3 | **RC boat** | Needs water volume. | XL |
| P7-4 | **Build with Lego** | Multi-object snap; after solid INTERACT. | XL+ |
| P7-5 | **Another whole house** | Only after current house expansions settle. | XXL |

**Phase 7 exit:** N/A as one ship — RC car is the first moonshot to plan when caves/missions can support battery + intro mission.

---

## Suggested planning cadence (mixed difficulty)

| Order | Slice | Why |
|-------|--------|-----|
| Now | **🗺️ Upstairs draw.io** + mission sketch | Unblocks the kids’ #1 ask; can plan tonight. |
| A | **Phase 0** | Fast “we heard you” ship; improves throw/break fantasy. |
| B | **Phase 1** | Camera frustration (occlusion + room lock) before more rooms. |
| C | **Phase 3 foundation** (hearts + economy + gated shop) *or* **Phase 2** Adam | Either systems or Adam presence — both amplify chaos they love. |
| D | **Phase 5 upstairs build** + missions | After map exists. |
| E | **Phase 4** cats / tree | Same-map content; photos/map marks help. |
| F | **Phase 6** caves | Needs hearts/spawns + preferably more map. |
| G | **Phase 7** RC car | Needs caves (batteries) + mission framework. |

---

## Traceability

| Theme | Backlog IDs |
|-------|-------------|
| Oskar spelling; pizza crust | P0-1, P0-2 |
| Thoughtful toys / adult props; varied breaks | P0-3, P0-4 |
| Shop discoverability → later gating | P0-5, P3-8, P3-9 |
| Drag look | P0-6 |
| Occlusion; room-locked camera | P1-1–P1-3 |
| Adam everywhere; activities; cleanup | P2-1–P2-3 |
| Hearts, squash shell meter, strawberry/apple | P3-* + economy table |
| Strawberry tortoise; Tony/Joey personalities; tree | P4-* |
| Upstairs first; under-house clubhouse | P5-* |
| Dig mission → GTA-style caves; spawn; decor | P6-* |
| RC car + battery + intro mission | P7-1 |
| Distinct food roles | Economy table |

---

## Out of scope / parked

- Disney account chatter.
- Wall-climb / sticky squash.
- General hunger bar (replaced by squash shell meter only).
- True E/M/H mission lanes — not built yet; redesign separately if desired.
