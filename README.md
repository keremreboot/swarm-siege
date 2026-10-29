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
- Food is eaten in chunks rather than shrinking: round bites come out where the ants are chewing, and the inside of the food shows through.
- Paced for a 2 to 2.5 minute clear: ants bite 0.4 food a second and the clock is 3:00. Eating snacks first clears in about 2:00 played perfectly; throwing every ball at the objectives runs out of time.
- **Level 3, Sweet stacks:** after Ant Swarm's stacked food, on a painted garden table. The objectives are a three-tier layer cake, a tower of eight pancakes and a seven-layer burger, among chocolate-bar towers, sugar-cube pyramids and stacks of donuts and cookies. Every piece is a rigid body (cannon-es physics): ants eat a stack from the top down, or eat its bottom piece from the table, and when a piece goes, whatever it held up drops, tips and tumbles. A stacked objective is done when its last piece is eaten.

Its tuning panel adds bite speed, egg value, the number of egg checkpoints, how fast an idle swarm's search grows, and an optional free ant: when it is on, the colony hatches one ant every 15 seconds and its rim fills toward the next one, so a stuck colony can still throw. Its settings are saved separately from the original.

Everything is in `index.html` (and `v1/index.html`); it loads three.js, Google Fonts and (in v1) cannon-es from CDNs.
