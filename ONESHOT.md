# Build ASCII RUSH — a city made of type

Build a complete, replayable endless runner whose game world is rendered entirely through characters. The last train left without you. Run the city after dark, take the roofs, collect the coins and come back for another attempt.

This is an autonomous implementation assignment. Own the decisions, build the game, play it, find what feels wrong and improve it before handing it over. Choose the implementation freely. In an existing checkout, preserve useful code and unrelated work; in an empty checkout, build the whole product from this brief. Do not stop at an architecture document or a title screen.

## The one visual promise

The road, buildings, train roofs, obstacles, runner, pickups and effects resolve into glyphs in the final game image. Internal geometry, lighting or intermediate render targets are implementation choices; the visible world must remain a city made of type, not conventional graphics with a small ASCII overlay.

Make characters carry depth, shape and light. A dark road should be visually quiet, the runner's silhouette unmistakable, obstacles readable before contact, and lamps and signs distinct from collectible coins. Perspective, parallax, shadows and atmosphere should make the city feel substantial. More glyph noise is not more detail.

Aim for a striking night-city composition that remains readable during an ordinary run. Every skin must have a recognizable silhouette. A cinematic screenshot is not success if the player cannot tell a low beam from a jumpable barrier.

## The run

Three lanes with immediate left/right swipes, up to jump and down to slide. Provide the equivalent keyboard controls: arrows or WASD, Space for jump and a pause key. One gesture should produce one intended action rather than accidental chained moves.

The route combines hurdles, low gates, full-height obstacles and trains with ramps leading onto their roofs. Running above street level is a real alternative route, with correct height, support and landing behavior—not a decorative jump animation over an unchanged collider. Jumping and sliding must solve visibly different problems.

Introduce the vocabulary through the first few patterns. Coins suggest a viable line and teach timing without requiring a manual. Escalate by combining learned situations, adding meaningful route choices and increasing pressure. Give the player opportunities to recover between demanding patterns; difficulty should not be indistinguishable from unreadable clutter.

Generate challenges that are reachable at the current speed and with the actual lane-change, jump and slide timings. A free lane is not a fair escape if there is no time to get there. Keep collision shapes and heights consistent with what the glyph renderer shows. Make an eventual loss understandable enough that retrying feels like a new chance, not another roll of the dice.

## Pickups and progression

Magnet, double coins and temporary flight are road pickups. Make activation, remaining duration and expiry readable without covering the track. Flight needs a safe, understandable return to ordinary running; expiry must not drop the player into an unavoidable obstacle.

Track run score, distance and coins separately. Bank collected run coins when an attempt ends or the player deliberately exits through the pause menu. Credit them exactly once. Death does not introduce an unannounced loss of unbanked coins: that was an error in the earlier prompt, not the current game's economy.

The locker offers the original runner, robot and ninja, plus a permanent longer-powerups upgrade. Purchases should visibly change the next run. Show owned, equipped, affordable and unaffordable states clearly. Keep bank, purchases, equipment, best score, best distance and preferences on the device; reopening the page should not charge for something already owned.

Choose sensible prices and progression pacing. Make the first desirable purchase attainable through ordinary play, while leaving a reason to return. The run remains a skill game rather than a shop with a runner attached.

## Complete product flow

Title → immediate run → pause/resume or loss → clear result → quick restart or locker → another run. A pause freezes gameplay and temporary effects. Returning from a hidden tab or a phone lock must not advance a giant frame and kill the player before they can react.

Use phone-safe layouts and large controls without letting HUD panels consume the road. Landscape phone and desktop are important; adapt gracefully to other aspect ratios. Keep the page from scrolling during play and release pointer state correctly when a gesture is cancelled. Include sound with a real mute, reduced-motion treatment, and an understandable notice when local storage is unavailable.

The original fits in one self-contained HTML file. Preserve the benefit—fast access, no account, no unnecessary services, straightforward hosting—without making file count or framework choice the challenge. The shipped game should not need a developer to assemble missing assets before it becomes playable.

## Prove the run, not just the renderer

Exercise lane changes in both directions, jump and slide collisions, ramp entry, rooftop travel, falling or stepping back to the road, and every power-up's expiry. Inspect a demanding late-run pattern at real speed, not only a slowed debug scene. Check generated sequences for practical escape paths.

Finish and exit attempts with known coin totals; verify that restart, title navigation and refresh cannot bank the same attempt twice. Buy and equip every locker item, reload, and confirm persistence and insufficient-funds behavior. Test pause, pointer cancellation, orientation changes and storage failure.

Use the actual rendered game to inspect glyph clarity and input response. Report frame-rate or device claims only for hardware and settings actually tested. Automated runs can expose unreachable patterns; they cannot establish that a thumb gesture feels good.

## Deliver

Leave a directly runnable game, short controls and run instructions, and a factual handoff naming what was tested and what remains unverified. Iterate on readability, rhythm and the first restart before spending effort on peripheral features.

**Finish when the city looks unmistakably like text, plays unmistakably like a runner, and the next attempt is one tap away.**

---

### Repository alignment

Based on `.exidex/content.md` and `index.html`, reviewed 2026-09-19. Source code explicitly states that coins bank when a run finishes or is left; `bank()` guards against duplicate credit. The shop includes Runner, Robot, Ninja and longer power-ups. Fair-pattern, expiry and lifecycle scenarios above strengthen the build requirements and are not a claim that this editing session executed gameplay tests.
