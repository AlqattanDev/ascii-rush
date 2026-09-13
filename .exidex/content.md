## The city after dark

ASCII RUSH is an endless runner where every frame is text. The road, the towers, the neon, the train roofs and the runner are all characters drawn to a canvas, projected with a real camera so the city has depth, lighting and shadow instead of reading as a wall of letters. The last train left without you. Run.

## Three lanes, one thumb

Swipe left and right to change lanes, up to jump, down to slide. Ride the ramps onto the train roofs. Coins line the safe path, so following them is the tutorial. On a keyboard it is WASD or the arrows, Space to jump and P to pause. The whole game fits a landscape phone and runs at full speed there.

## Locker and bank

Coins you survive with are banked. The locker sells skins (a runner, a robot, a ninja) and upgrades; the magnet, double coins and flight are power-ups you pick up on the road. Best distance, bank and purchases save on the device.

## How it is built

One HTML file with no dependencies, no build step and no assets: the renderer, the procedural obstacle generator, the shop, the audio and the persistence are all inside it. The visual pass was the work: quiet road texture, stronger light and shadow separation, and a runner and HUD silhouette that stay readable at speed.
