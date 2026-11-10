# I Am Lina

A tortoise chaos game for Adam's niece and nephew. Three.js and cannon-es, no build step, runs in Safari on an iPad.

You are Lina, a tortoise loose in a cartoon house: open kitchen, dining and living room, a playroom with her tortoise home, a hall, an office and a powder room, plus the garden. Upstairs and the basement are locked for now.

- Left thumb: walk. Right side: JUMP, GRAB/THROW and SHELL (tuck in and roll like a bowling ball for 3 seconds). Drag the world to look around.
- Knock over side tables, break vases and lamps for coins, bonk Uncle Adam (cartoon slapstick: he spins into the air and lands dizzy).
- Uncle Adam wanders around calmly. Bonk him and he turns red and chases Lina for 25 seconds. If he catches Lina out of her shell, she is carried back to the start. In shell mode he cannot touch her.
- Hop up the wooden steps (JUMP) to the rafters. Pick up small things with GRAB and THROW them. The garden is through the east door: lettuce, a T-rex and a droid.
- Coin shop (Shop button): shell colours (brown by default) and shell patterns. Coins and unlocks are saved on this device.
- 19 missions (Missions button), three open at a time, finishing one opens the next, inspired by I Am Cat: vases, disco radio, rafters, pick and throw, bonking Uncle Adam, lettuce feast, domino books, balloons, dino friend, paintings, droid bump, tables, fridge top, bug hunt, hiding in the box, dropping things on Uncle Adam.
- View button (or V): third person, first person, from above, from the side, from the front.

Run locally: `python3 -m http.server` in this folder, open http://localhost:8000 (WASD or arrows, space for shell).
Live: https://abroniewski.github.io/i-am-lena-game/

## Analytics

PostHog (EU, project **the-lab**) with `site: i-am-lena`. No autocapture, no session replay, and feedback **text** is never sent (mood only). Disabled on localhost.

### Players (required)

Every launch asks **What is your name?** (free text — anyone can play). The last name is pre-filled so the same kid can tap **Let’s play!** quickly.

- **Identity = device.** Each browser/iPad gets a stable `device_id` in localStorage. PostHog `identify`s as `i-am-lena:device:{device_id}`, so two iPads stay two people even if both type “Oskar”.
- **Name = label.** Every event also carries `player` (slug) and `player_name` (as typed), so you can filter “Oskar’s iPad” vs “Clara’s iPad” in analytics. Changing the name updates the label on that device; it does not create a new person.
- Also on every event: `play_id` (one play stretch). Change mid-session with the **👤 Name** button, or open with `?player=YourName`.

### Session model

Each play stretch gets a `play_id`. Events:

| Event | When |
|-------|------|
| `session_started` | Player selected, tab becomes visible again, or load with a saved player |
| `play_heartbeat` | Every 60s while the tab is visible — includes running action counts + `duration_s` |
| `session_ended` | Tab hidden / page unload — full summary: jumps, shells, grabs, throws, catches, bonks, breaks, coins earned, missions completed, `duration_s` |

### Gameplay events

| Event | Notes |
|-------|--------|
| `$pageview` | Load |
| `player_selected` | Gate / switch / `?player=` |
| `mission_complete` | `mission`, `done`, `total`, `reward` |
| `all_missions_done` | Full clear |
| `missions_opened` | Mission board |
| `shop_opened` / `shop_purchase` | Purchase includes `kind`, `item`, `price` |
| `view_changed` | Camera mode name |
| `control_used` | `shell`, `grab`, `throw` (jumps are counted in session summaries only) |
| `prop_broken` | `kind` (vase / lamp / …) |
| `adam_bonked` | `how` shell\|throw, `from_rafters` |
| `adam_chase_started` / `adam_chase_ended` | Mad chase window |
| `caught_by_adam` / `returned_to_start` | Scoop + reset |
| `garden_entered` | First time into the garden this load |
| `food_eaten` | e.g. lettuce |
| `bug_hunt_started` / `bug_hunt_finished` | `result` won\|timeout |
| `feedback_opened` / `feedback_mood_picked` / `feedback_sent` / `feedback_dismissed` / `feedback_share_result` | Mood only; note body never sent |

Every custom event also gets `device_id`, `player`, `player_name`, `play_id`, `coins`, `missions_done`, `missions_total`, and `active_missions` when the game has started.

**How to read it:** break down by `device_id` (or PostHog person) for true per-iPad history; use `player_name` to see which kid that device usually belongs to. Same name on two devices stays two people. Clearing site data on an iPad creates a new `device_id`. Localhost sends nothing.
