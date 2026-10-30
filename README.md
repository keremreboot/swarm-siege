# Swarm Siege

A phone-portrait browser prototype that mixes Ant Swarm 3D and Base Demolish.

Tap the level to launch a glass ball of ants. Each swarm eats anything at or below its size, every bite flies to the colony, and the colony hatches new ants into the next ball. Swarms that meet merge. Ants only live about 15 seconds once they land, so keep feeding the colony. Eat the three red objectives before the 60-second timer runs out.

- **Level 1, Army base:** Radar (12 ants), Tank (30), HQ (50)
- **Level 2, Picnic:** Burger (15), Melon (35), Cake (60)

The tuning panel (beside the game on desktop, behind the sliders button on a phone) changes the time limit, hatch cost, bite rate, walk speed, sight range, lifespan, starting ants and size gates. Press R to restart.

## Version 1

A rules variant lives at [/v1/](https://keremreboot.github.io/swarm-siege/v1/), with the same two levels plus a third:
- Ants never die. A swarm with nothing nearby slowly looks further out until it finds food.
- Any swarm can eat anything. More ants eat it faster. A small swarm eats whatever it lands nearest and never leaves food it has started on, so one ant thrown on the HQ chews the HQ; a colony can get stuck that way.
- Every object is worth a set number of eggs, laid in batches at checkpoints as it is eaten. The eggs pop out, then fly to the colony and hatch into the next ball.
- Nothing is written on the objects. The objective chips at the top show how much of each objective has been eaten.
- The objectives are bigger (Radar 100 bites, Tank 240, HQ 400; Burger 120, Melon 260, Cake 400), so growing the colony before going for them pays off.
- Framed after Ant Swarm: each level is an island (grass top, orange soil sides) on flat calm water, with nothing else in the world, so everything on screen is food. The camera is steep (63 degrees) so little hides behind tall stacks, with the island's front edge 70% of the way down the screen. The launcher is a small Base Demolish style cannon (an iron mortar with gold bands on a wooden carriage, drawn with its glass ball at 60%) in the water at the bottom of the screen; the next ball sits in its mouth, and it swings toward the aim and kicks back with a puff of smoke when it fires. All food is drawn 35% larger than it is built, there are a third fewer loose snacks, and every level is respaced so no two pieces of food touch. Surfaces are near-flat colours: plain sand, big soft gingham, seam-only planks.
- Food is eaten in chunks rather than shrinking: round bites come out where the ants are chewing, and the inside of the food shows through.
- Paced for a 2 to 2.5 minute clear: ants bite 0.4 food a second and the clock is 3:00. Eating snacks first clears in about 2:00 played perfectly; throwing every ball at the objectives runs out of time.
- **Level 3, Sweet stacks:** after Ant Swarm's stacked food, on a painted plank board. The objectives are a three-tier cake, a tower of eight pancakes and a seven-layer burger, among chocolate-bar towers, sugar-cube pyramids and stacks of donuts and cookies. Every piece is a rigid body (cannon-es physics): ants eat a stack from the top down, or eat its bottom piece from the table, and when a piece goes, whatever it held up drops, tips and tumbles. A stacked objective is done when its last piece is eaten.

Its tuning panel adds bite speed, egg value, the number of egg checkpoints, how fast an idle swarm's search grows, and an optional free ant: when it is on, the colony hatches one ant every 15 seconds and its rim fills toward the next one, so a stuck colony can still throw. Its settings are saved separately from the original.

## Carry version (the `carry` branch)

On this branch, `v1/index.html` is an alternate of version 1 where food is carried home instead of eaten. Same three levels, same island, camera and cannon:
- Every level has ant holes along its front edge: two on the Army base, one on the Picnic, three on Sweet stacks.
- Every piece of food takes a number of ants to lift. Food that takes three or more shows the number over it, green once the next ball has that many. Objectives show their name and number: Radar 18, Tank 36, HQ 60; Burger 15, Melon 30, Cake 50. In Sweet stacks the cake's tiers take 12, 20 and 30, and a stack is carried off a piece at a time from the top. The chips at the top show how many ants each objective takes right now, and turn green when the next ball has enough.
- A swarm only goes for food it has the ants for, and sends exactly that many; the rest look for more. Swarms with nothing to do merge when they meet.
- Carriers haul their food to the nearest hole at 0.8 m/s, round anything taller than a snack (big pieces are wider than any gap, so they go straight over). Down the hole it goes: the carriers fly back into the cannon with the new ants it hatches. A snack doubles its one carrier; bigger food gives a little less per carrier, but more at once.
- Ants never die. A swarm with nothing it can lift nearby waits 2.5 seconds, then walks to a hole and rejoins the ball.
- No eating, bites or eggs.
- Paced for a clear in about 2:05 to 2:15 played well on each level, on the 3:00 clock. Throwing every ball at random food still clears the Picnic in about 2:40.
- Sweet stacks uses cannon-es's naive broadphase. With sweep-and-prune, the cake's tiers fell through each other as soon as they woke, and the bottom tier was thrown into the air (version 1 on `main` has the same fix).

The tuning panel swaps bite speed, egg value and checkpoints for carry speed, ants per food and ants needed, and search growth for the wait before heading home. Its settings are saved apart from version 1.

Everything is in `index.html` (and `v1/index.html`); it loads three.js, Google Fonts and (in v1) cannon-es from CDNs.
