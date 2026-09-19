# ASCII RUSH: GPT-6 one-shot build

You are GPT-6, responsible for the complete game, its renderer and its visual identity. Build a polished endless runner through a night city rendered entirely as characters. Deliver a complete playable product: title, run, loss, restart, locker, progression and settings. A striking still image is not enough.

Make ordinary decisions autonomously and continue through implementation, playing, visual refinement and fixes without incremental approval requests. Use suitable tools. Preserve working systems and unrelated work in an existing checkout; in an empty project, this document is the whole-game brief. The compact, self-contained experience matters more than a particular file count or graphics API.

## 1. The promise

The last train left without you. Run the city after dark. Dodge the street obstacles, climb the ramps, run along train roofs and bank enough coins to return in another silhouette.

The game is three-lane, immediate and thumb-driven. Its defining visual rule is equally simple: **the final game world is made of glyphs**. Roads, runner, trains, obstacles, buildings, lights and effects must resolve into characters. Geometry and lighting may exist underneath, as they already do in the source; an ordinary 3D game with a small text overlay does not satisfy the brief.

It should look like a city made of type, not a terminal filled with random symbols.

## 2. Build a deliberate ASCII image

**Composition and depth.** Use a coherent chase perspective with a strong vanishing point and the runner clearly separated in the near foreground. Three usable lanes must remain apparent. Curbs, streetlamps, façades, elevated train roofs and distant towers provide different depth layers and rates of motion. A roof should visibly sit above the street, and its ramp should read as a climb before the player reaches it.

Keep the immediate road quiet. Concentrate architectural detail into the middle distance and sides: projecting awnings, recessed storefronts, window grids with selective lighting, cornices, rooftop equipment, signs and lamp arms. Vary building mass and height while keeping a believable street rhythm. Do not let random tall noise replace authored silhouette. The city should feel dense beyond the route without covering the lane entrances.

**Glyph treatment.** Choose a consistent character family and intentional relationships between sparse marks, middle-density forms and dense highlights. Preserve clear local contrast: the sky and road can use sparse or dark marks; lit windows and edges can carry stronger glyphs. Characters should remain sharp rather than being stretched into fuzzy rectangular pixels. Their density must describe form and illumination, not fluctuate arbitrarily on every frame.

A runner, hurdle, low gate, wall, train and coin must each survive the character conversion as a distinct silhouette. Check the smallest gameplay representation, not only a close-up before the post-process. Give hazardous edges enough contrast and thickness to remain legible in motion. A technically complete glyph shader that erases the difference between jump and slide is a failed renderer.

**Color and light.** Build around blue-black and slate streets, muted teal architecture, selective cyan/magenta signage and warm gold collectible highlights. The source's warm title/button color can carry through coins and rewards. Use spatially coherent light pools and dark sides to give objects volume. Highlight windows selectively; an entire façade uniformly glowing is not a richer city.

Weather changes may introduce rain streaks, haze or stronger road reflections, but all remain expressed through the glyph image and leave obstacles readable. Fog should reduce distant detail, not remove necessary reaction distance. Rain must not resemble falling collectible coins. Avoid a full-screen neon wash that makes every material the same luminous surface.

**Motion clarity.** Keep character sampling stable enough to prevent distracting crawl and shimmer. Preserve the runner's head, torso and legs through running, jumping and sliding. Use parallax and coherent travel speed to produce momentum rather than smearing the image with blur. Landing can produce a compact impact and brief pose compression. Lateral movement should lean or shift decisively, then settle; it should not look like a static icon being dragged sideways.

The default Runner, Robot and Ninja need distinct readable forms. Robot can emphasize an angular head and mechanical stride; Ninja a different head/torso silhouette and a restrained trailing shape. They must remain identifiable after glyph conversion, not only in the shop preview. These are visual treatments of the existing skins, not extra character classes.

## 3. Make the street teach its actions

Swipe left/right for one lane change, up to jump and down to slide. Support arrows/WASD, Space and pause on desktop. One gesture produces one intentional action, with clean pointer cancellation and no page scrolling during play.

Hurdles ask for a jump, gates for a slide, full-height walls for a lane change. Trains provide ramps and a physically higher running surface. Roof entry, roof travel, stepping off, airborne movement and return to ground must agree with the visible geometry. Do not simulate a roof merely by lifting the sprite while keeping the street collider.

Use a few generous opening patterns to teach the vocabulary, then combine it into more demanding sequences. Coins trace useful paths and arcs. A coin line should not quietly guide a learner into an impossible jump. Mix focused sequences with quiet connectors, rather than filling every moment with obstacles.

Generate patterns reachable with the actual lane-change duration, speed, jump arc and slide window. An open lane is not a viable escape when it takes longer to reach than the remaining reaction time. Difficulty can increase with speed and combinations, but the image must still provide enough information to respond. Avoid inventing extra obstacle types before the existing four are visually and mechanically distinct.

## 4. The guard, pickups and scoring

Preserve the source's two kinds of loss. A direct major collision ends the attempt. A glancing lane-change collision can cause a stumble: the runner slows briefly and the guard is close for five seconds. Stay clean to recover; stumble again in that window and the guard catches up. Give recovery a visible and audible beginning and end. This is not a hidden multi-hit health bar.

The guard's increased pressure should read from a restrained approaching silhouette, cue and warning, without obscuring the next obstacle. A crash and a catch receive different short ending beats. The player should understand which error ended the attempt.

Road pickups are **Magnet, Double and Jetpack**. Magnet pulls reachable coins toward the runner. Jetpack visibly lifts them above the track, permits lane changes and creates an airborne collection opportunity. Its expiry gives the existing safe-landing grace period and clear feedback so the return is understandable rather than an unavoidable crash. Pickup duration is six seconds before the permanent two-second extension. Show remaining duration compactly.

For this brief, label Double accurately as **Double Score**: the current implementation doubles distance-score gain and coin-score value, while each collected coin still adds one coin to the bank. It is not a bank-currency multiplier. Keep UI, instructions and behavior consistent.

Track score, run distance, collected coins, best score and best distance separately. Bank the attempt's coins when it ends or when the player deliberately leaves through the pause/title path. Credit the attempt exactly once. Death does not erase those coins. The source economy is not an extraction game.

## 5. The presentation outside the run

**Title.** A real ASCII wordmark, a composed live city view and one obvious start action. The background can show a quiet section of the real rendered route, not a promotional image implying graphics the game cannot deliver. Keep the message short and the playable world visible. Use monospaced typography with a deliberate hierarchy rather than making every label the same size.

**HUD.** Score, coins, distance, temporary power state and pause in a compact arrangement. Dark-backed readouts can protect contrast, but must not occupy the reaction corridor. Keep the first obstacle, runner and active warning visible together. Avoid large opaque panels drifting over the middle lane.

**Locker.** Show all three silhouettes through clear character previews and obvious owned/equipped/affordable states. Preserve the original free Runner, Robot at 50 coins, Ninja at 100, and the 100-coin longer-powerups upgrade as the initial economy. A purchase visibly affects the next run. No fake purchase-success message when the bank is insufficient.

**Results.** A concise scorecard with the real ending cause, score, distance, collected/banked coins and records. Restart is immediate and prominent. A new record earns restrained emphasis, not a celebration that delays the next attempt. Pause genuinely freezes gameplay and temporary effects; resume restores control without an accidental swipe.

Use synthesized or properly sourced sound that belongs to this compact arcade night: rhythmic footsteps, jump/slide/landing, crisp pickups, distinctive power activation, guard pressure and crash. Avoid a high-volume identical beep for every event. Include mute and reduced motion. Persist bank, ownership, equipped skin, records and settings; explain unavailable storage without falsely promising permanence.

## 6. What completion requires

Play the complete title/run/pause/loss/restart/locker loop. Exercise every obstacle, rooftop transition and pickup, a first stumble, five-second recovery, a second stumble catch, a crash and safe Jetpack expiry. Check banking after both loss and deliberate quit, repeated result navigation, purchasing, reloading and storage failure. Hidden-tab return or a phone lock must not advance an enormous frame into instant death.

Inspect actual rendered frames from an opening street, a dense late-run pattern, the top of a train, each skin, active flight and the result screen. At normal speed and actual display size, identify the runner, next threat and usable response without squinting. Check glyph sharpness, color hierarchy, sampling stability and weather readability. A slower diagnostic scene does not prove late-run visibility.

Optimize the renderer's decorative cost before shortening warning distance or changing collision rules. Report performance for tested hardware, settings and rendering mode only. Desktop measurements are not phone measurements.

Deliver a self-contained runnable game, short startup/control instructions and factual verification notes. Use real input paths as well as deterministic diagnostics. Do not claim a generated pattern is fun merely because a bot survived it.

**The standard: a sharp city made of type, a runner with readable movement, fair mistakes and a next attempt that is one tap away.**

---

### Source basis and target distinction

Grounded in `index.html`, including its glyph renderer, pattern generator, `stumble`, `activate`, `tick`, `bank` and result flow, plus `.exidex/content.md`. The source code establishes five-second stumble recovery, six/eight-second pickups, two-second landing protection and banking on both crash/catch and exit. Marketing calls the multiplier “double coins,” but `tick` doubles score rather than `runCoins`; this brief explicitly preserves that executable behavior and names it accurately. Detailed model, lighting and motion treatment above is the new visual target, not a claim of runtime inspection in this rewrite.
