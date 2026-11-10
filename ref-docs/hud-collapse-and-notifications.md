# HUD collapse & notifications — I Am Lina

Reference for progressive disclosure on the play HUD and for transient feedback. Use this when adding menus, collapsing panels, or toast-style messages so the UI stays consistent on iPad Safari (and desktop).

**Audience:** kids on a large touch screen. Prefer big targets, few words, and a clear playfield over dense chrome.

---

## Core idea

| Layer | Attention | What belongs there |
|-------|-----------|--------------------|
| **Playfield** | Eyes on Lina | 3D world, markers, action buttons (JUMP / GRAB / SHELL / stick) |
| **Always-on HUD** | Glance | Coins, mission progress count, timer while a timed task runs |
| **One tap away** | Disclosure | Active mission details, secondary tools (View, Shop, Missions, Tell us, Name) |
| **Full-screen panel** | Pause | Shop, mission board, feedback — pause the game while open |
| **Notification** | Peripheral | Short status (“Got cheese!”) or celebration (“DONE: …”) — never a decision |

Menus can hold choices and words. The HUD must be readable in a split second. Rank by urgency: always show what ends the run or tracks the session; tuck the rest behind a disclosure. ([Partii game UI](https://partii.games/docs/build/game-ui))

---

## Pattern A — Disclosure (collapse / expand)

Use the W3C **disclosure** pattern (show/hide), not a fake accordion of unrelated pages. ([WAI-ARIA APG Disclosure](https://www.w3.org/WAI/ARIA/apg/patterns/disclosure/), [WebAIM disclosures](https://webaim.org/techniques/disclosures/), [Apple HIG disclosure controls](https://developer.apple.com/design/human-interface-guidelines/disclosure-controls))

### Rules for this project

1. **One visible trigger** with a clear label of what opens (“Menu”, “Missions”, “Done missions”).
2. **Trigger is a `<button>`** (not a bare `<div>`). Activate with Enter/Space when focused.
3. **`aria-expanded="true|false"`** always matches visibility. Prefer `aria-controls` pointing at the panel id.
4. **Collapsed content is not focusable** — use `hidden`, or `visibility` + remove from tab order. Do not leave Shop/Missions focusable while visually hidden.
5. **Chevron / triangle** points to the open direction (▶ collapsed → ▼ expanded is fine for vertical stacks; ▶ / ◀ for a right rail).
6. **Most-used stuff stays at the top of the hierarchy** — coins + “N open” stay visible; full descriptions hide by default.
7. **Remember state lightly** — session memory is enough for “missions expanded”; default to **collapsed** on a fresh load so the house is visible.
8. **Touch size** ≥ ~44×44 CSS px for the toggle (Apple game-control guidance). Leave gaps so a thumb doesn’t hit JUMP by accident.
9. **Do not nest disclosures more than one level deep** on the play HUD. Deep trees are for rare settings, not for every session.

### Where we use it

| Control | Default | Notes |
|---------|---------|--------|
| **Menu rail** (top-right) | Collapsed | Holds View, Shop, Missions, Tell us, Name. One ☰ / Menu chip when closed. |
| **Mission strip** (top-left HUD) | Collapsed | Always show `🥬 coins` + `📜 done/total`. Expand for the three open missions + short desc. |
| **Mission board sections** | Open = expanded; Locked & Done = collapsed | Full list is long — kids should see “what’s open” first. |

### Interaction details

- Opening a **full-screen panel** (Shop / Missions / Feedback / name gate) should **collapse the menu rail** so chrome doesn’t sit on top of the modal.
- Closing a panel returns to play with the rail still collapsed (predictable).
- A **badge or pulse** on the collapsed Menu (or Shop) is how we surface “new coins / open shop” without forcing the rail open forever.
- Camera look-drag must ignore the rail and HUD toggles (same `LOOK_SKIP` idea as today’s buttons).

---

## Pattern B — Notifications (toasts)

Distinguish **status** feedback from **critical** decisions.

| Kind | Example | UI | Duration | Stacking |
|------|---------|----|----------|----------|
| **Status** | “Got mozzarella!”, “Yum! 3/8” | Toast / snackbar | ~2–4 s | One at a time; queue or replace |
| **Celebrate** | “DONE: Vase Smasher! +7” | Larger toast | ~3–5 s | Replace or short queue; don’t pile |
| **Critical / choice** | “Pick a face first”, name gate | Modal / inline — **not** auto-dismiss toast | Until dismissed | N/A |

### Adopted standards (adapted for kids + play)

From [Material 3 Snackbar](https://m3.material.io/components/snackbar/guidelines), [BuiltUX toast anti-patterns (2026)](https://builtux.com/toast-notifications-snackbars-production-ux-anti-patterns-2026/), and game HUD feedback notes:

1. **Non-blocking** — toasts must not steal focus or cover JUMP / GRAB / SHELL / stick.
2. **One visible at a time** — never stack 5 overlapping messages. Queue extras, or replace with the newest if it supersedes (e.g. progress “3/8” → “4/8”).
3. **Cap the queue** (e.g. max 3 waiting) so a chaos spree doesn’t backlog for a minute.
4. **Auto-dismiss** for status/celebrate only. Rough windows: short **~2.5 s**, long **~4–5 s**. Interactive/error copy stays until the kid acts.
5. **`role="status"` + `aria-live="polite"`** on the toast region. Do not use `assertive` for routine pickups.
6. **Readable over the scene** — strong text shadow or a soft pill behind the words; check over bright sky and busy rooms.
7. **Placement for I Am Lina**
   - **Celebrate / mission** — upper-middle (current habit), large type, short.
   - **Status** — same region is OK for consistency on iPad; keep opacity transition snappy (~0.2–0.3 s).
   - Avoid bottom-center if it would sit on the stick/action cluster.
8. **Dedupe / coalesce** — rapid repeats of the same stem (e.g. many “POP!”) should update one toast, not enqueue ten.
9. **Pair toast with HUD** when it matters — mission complete also bumps `📜 done/total` so the message isn’t only ephemeral (Material’s “also communicate inline” idea).
10. **Never** put irreversible or “you must choose” content only in an auto-dismiss toast.

### Toast API shape (project convention)

Keep a single helper so call sites stay simple:

```text
toast(message, { kind: 'status' | 'celebrate', replace?: boolean })
```

- Default `kind: 'status'`.
- Mission complete / all-clear → `celebrate`.
- `replace: true` (default for same-kind updates) swaps the current toast and clears the short queue for that burst.
- Game loop ticks down the visible toast; when it ends, show the next queued item if any.

---

## Pattern C — Full-screen panels vs disclosures

| | Disclosure | Full-screen panel |
|--|------------|-------------------|
| Play continues? | Yes | No — set `paused` |
| Use for | Mission strip, menu rail | Shop, mission board, feedback, name |
| Back behaviour | Toggle collapses | Explicit “Back to the game” |
| Depth | One level | Flat list / sectioned list inside |

Do not turn Shop into a side drawer that leaves physics running. Kids need pause while buying shells.

---

## Visual / motion budget

- **Motion** = state change (rail open/close, toast fade), not decoration.
- Honour `prefers-reduced-motion: reduce` — instant show/hide, no bounce.
- Collapsed Menu and Mission strip share the same chrome language: translucent dark pill, white border, heavy weight type (match existing buttons).
- Phone layout (`html.phone`): keep collapsed by default; mission descriptions only when the strip is expanded (today phones hide `.obj` always — expansion is the way to show them).

---

## Checklist before shipping a HUD change

- [ ] Playfield centre and action buttons stay clear in the default (collapsed) state.
- [ ] Disclosure button has `aria-expanded` and a real `<button>`.
- [ ] Collapsed controls are not hit-testable / not in the look-drag skip list as ghosts.
- [ ] Opening Shop / Missions / Feedback / gate collapses the menu rail.
- [ ] Toasts: one visible, queued or replaced, `aria-live="polite"`, not over action buttons.
- [ ] Celebrate messages still update the always-on coin / mission counters.
- [ ] iPad + phone: toggles ≥ ~44px (phone can scale down labels but keep hit area).
- [ ] No new always-on paragraphs over gameplay.

---

## Sources

- [WAI-ARIA APG — Disclosure (Show/Hide)](https://www.w3.org/WAI/ARIA/apg/patterns/disclosure/)
- [WebAIM — Disclosures and Accordions](https://webaim.org/techniques/disclosures/)
- [Apple HIG — Disclosure controls](https://developer.apple.com/design/human-interface-guidelines/disclosure-controls)
- [Partii — Game UI: HUDs, menus and screens](https://partii.games/docs/build/game-ui)
- [Material Design 3 — Snackbar guidelines](https://m3.material.io/components/snackbar/guidelines)
- [BuiltUX — Toast notifications UX anti-patterns (2026)](https://builtux.com/toast-notifications-snackbars-production-ux-anti-patterns-2026/)
- [GameDesign.gg — Mobile game UX (two-tap / progressive disclosure)](https://gamedesign.gg/articles/mobile-game-ux-design/)

---

## Changelog

| Date | Note |
|------|------|
| 10 Nov 2026 | First draft; menu rail + mission strip + toast queue landed in `index.html`. |
