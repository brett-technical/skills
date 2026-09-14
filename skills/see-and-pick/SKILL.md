---
name: see-and-pick
description: "Use when the user must choose among real options and needs to see them — screenshots, live links, toggles — not a prose list. Trigger on: 'show me examples', 'I need to see it', 'where are my toggles', 'I want to pick', 'copy my pick', a decision with more than two artifacts to compare. Do NOT use for a single yes/no, for writing the final artifact, or for a plan dashboard. Do NOT use to dump two competing pastes in chat."
version: 1.0.0
license: MIT
---

# See and pick

Turn a set of options into one local HTML board the user can see, toggle, and copy a pick from. The board is the decision surface. Chat stays short.

This skill does not study a field and does not build the product. It ends when the user pastes a pick string.

## When to use

- The user has to choose among things that look different in the real world.
- They say they do not know what an item is, or they need a link to visit it.
- A prior list in chat was too abstract.

Do not use when there is one binary choice, or when they already named the pick.

## Output

One HTML file, self-contained CSS, next to the work it serves. Open it in the user's browser as a tab in the current window. No new window.

Sticky bar: current pick string, Copy pick, Reset to recommendation.

Done when: every option has a live URL, toggles work, need items start on, skip items start off, killed items cannot turn on, Copy pick writes a token string the next step can parse.

## Procedure

1. **Inventory the options.** One row per thing the user might add, skip, or choose among. Done when each row has a name, what it is in one sentence, and whether it is need, skip, killed, either-or, or stack.

2. **Kill before you draw.** Drop anything that:
   - leaks private infrastructure, a hidden library, machine paths, or accounts
   - needs a service or account the user does not have
   - is costume (looks busy, does not change the product)
   Done when killed items are listed with one-line why, and they never appear in the pick string.

3. **One live example per row.** A URL the user can open and see the thing (a repo README, a file, a screenshot of the real page). If they cannot visit it, the row is not ready. Screenshot the real artifact when look or layout is the point. Save images next to the HTML. Done when every visible row has a working link.

4. **Either-or vs stack.** Either-or = radio, pick exactly one (license, README frame, look). Stack = checkbox, any mix. Locked-on = need that is format law or leak-prevention. Locked-off = killed. Done when two radios in the same group cannot both be on.

5. **Write the board.** Dark, dense, one page. Each card: toggle, short name, one sentence, live link. Need section on by default. Skip section off by default. Killed section visible, disabled. Look section is screenshots plus radios. Do not replace toggles with static verdicts. If you rewrite the page, restore the toggles in the same pass. Done when a click changes the pick string.

6. **Recommend, do not trap.** Reset sets need-on / skip-off. The user can flip skip items on. Chat names only kills and the one question still open (usually look). Done when chat is shorter than the board.

7. **Wait for the pick string.** Parse it. Do not build until it exists. Token shape: `look:<id> <either-or ids> <stack ids>` (example: `look:matt 5 22 1 2 3`). Done when the next step can run from that string alone.

## Pick string

- Stable integer or slug ids, not titles.
- Locked-on ids always included even if the checkbox is disabled.
- Locked-off ids never included.
- `look:none` means no hero.

## Pitfalls

1. **Chat as the board.** A bullet list is not seeing. If they ask what something looks like, the board failed. Add a link and a screenshot, do not explain harder.
2. **Dropping toggles on rewrite.** A reassessment pass that removes checkboxes is a defect. Keep the toggles. Change defaults and labels.
3. **Advertising private context.** Positioning like "from my private set" is a kill, not a feature.
4. **Counters and accounts.** A badge that needs a registry account, or that shows zero, is skip or kill unless the user asked for it.
5. **Diagram without a URL.** "ASCII lifecycle" with no link is not an example. Link the real README and say where to scroll.
6. **Building from a recommendation.** The recommendation is the default, not the pick. Wait.
7. **file:// audio/video.** Serve those boards over localhost HTTP. Plain screenshots and links work from `file://`.
8. **Opening a new browser window.** Current window. Do not force a new window.

## Verification

- [ ] Board opened in the current browser window
- [ ] Every non-killed row has a live URL
- [ ] Either-or groups are radios
- [ ] Copy pick produces a parseable string
- [ ] Killed rows cannot appear in that string
- [ ] A rewrite still has toggles
