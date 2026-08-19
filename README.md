# Cross Country Manager

A retro pixel-art cross country **team manager**. You run a club of ten runners, race them as a
ten-leg relay against rival clubs, spend your prize money on training terrain and shoes, train away
your squad's weaknesses, and climb from the village fun run to the national league.

The whole game is one self-contained `index.html` — no build step, no install, no internet needed.

## Play it

Double-click `index.html`, or open it in any modern browser. That's it. Your club saves
automatically to that browser's local storage, so you can close the tab and come back to it.

## How it works

### Your ten runners

Every runner is rated 0–100 in eight attributes:

| | |
|---|---|
| **Fitness** | how long they hold pace before fading |
| **Speed** | flat-out pace on good ground |
| **Sprint** | their kick into the handover |
| **Hills** | climbing strength |
| **Mud** | grip and drive in heavy ground |
| **Long Grass** | lifting the knees through deep grass |
| **Wind** | holding form into a headwind |
| **Uneven** | footing on rough, rutted ground |

Runners are generated with real character — a mudlark who can't sprint, a track speedster who dies
in heavy ground, a grinder with huge fitness and no kick.

### The relay

A race is ten legs. Each runner does one lap of the course loop, then hands the baton on. The course
is a loop split into terrain sections — firm grass, hills, mud, long grass, uneven ground — and some
stretches are exposed to a headwind. A runner's speed on any given stretch comes from the attribute
that stretch tests, how much stamina they have left, their shoes, and their kick at the handover.

**The ground cuts up as the race goes on.** Mud, long grass and rough sections get progressively
heavier on the later legs, so your heavy-ground specialists are worth saving for the back end of the
relay. That's what the running order is for (there's an **Auto Order** button that does it for you).

### Home and away

Every club has its own home ground, and a season's six races are one round hosted by each club — so
one fixture a season is at home and the other five are away, on whatever the opposition runs on. The
courses have real character and get nastier the higher you climb: the village league is parks and
meadows, the national league is bogs that are half mud, fells that are half climbing, and exposed
ridges where four fifths of the loop is into the wind.

**Your home course is built from the terrain you have bought.** Every plot you own puts that ground
into your own loop, so it starts as a bare flat field and turns into a proper technical course as you
invest. And because your squad trains on that exact ground, your facility bonuses count double at
home — the one race a season you should really fancy your chances.

### Finding out what went wrong

After every race the results screen shows **where you lost time** — the seconds your squad gave away
to each attribute, measured as "how much faster would you have been if this attribute were 100".
It also breaks it down leg by leg, with each runner's stamina at the handover and their biggest
weakness on the day, and tells you plainly what to do about it:

> Your squad lost 87s to HILLS and you cannot train it. Buy the HILL CIRCUIT (£850).

### Money, terrain and training

Prize money comes only from racing, and it scales with the league you're in — the village league is
easy to win but pays badly.

You spend it on:

- **Terrain** — a mud pit, a hill circuit, a long grass meadow, an exposed ridge and so on. Buying a
  piece of terrain is what *unlocks training* for that attribute, and gives a small permanent bonus
  straight away. You start with only a cinder track and a fitness trail, so speed and fitness are the
  only things you can train until you start buying ground.
- **Shoes** — mud claws, fell shoes, grass spikes, carbon racers. Each pair has trade-offs (carbon
  racers are quick but hopeless in mud). Pairs go into the kit bag and you assign them per runner.

**Training** is three sessions a week, and each session trains the **whole squad** in one attribute.
Gains shrink as an attribute approaches 100, so you can't just max everything.

### Leagues and seasons

Five tiers: Village Fun Run → District → County → Regional → National. A season is six races against
the five other clubs in your league, scoring 10/8/6/4/2/1 by finishing position. Win the league and
you're promoted with a bonus; finish bottom above the village league and you go down.

**It gets genuinely hard.** Rival clubs improve every season, and the higher the league the harder
they work at it, so standing still means going backwards. The village league is a stroll; the
National League is not somewhere you expect to win. Measured over many simulated careers, a
competent manager wins roughly 96% of village races and about 20% of national ones — reaching the
top tier takes the better part of ten seasons, with real plateaus on the way.

## For anyone poking at the code

`index.html` is organised into commented sections: `UTILITIES`, `DATA`, `GENERATORS`,
`RACE SIMULATION`, `PIXEL RENDERER`, `GAME STATE`, `GAME ACTIONS`, `SAVE/LOAD`, `USER INTERFACE`,
`BOOT`.

A few things worth knowing:

- The rival clubs run through **exactly the same simulation** as you — no cheating AI, no rubber
  banding.
- Speed and fitness apply to every metre of the course, while a terrain attribute only applies on
  its own sections. The speed and fitness ranges are therefore deliberately narrow and the terrain
  range is wide, so that a mud specialist on a muddy course beats someone who is merely fast, and
  buying terrain is worth the money. Those constants are at the top of the `DATA` section.
- The renderer draws to a 400×232 canvas with image smoothing off, then scales up, so everything
  stays crunchy. The HUD font is a hand-encoded 5×7 bitmap and the runners are 5×8 sprites with a
  four-frame run cycle, palette-swapped per club.
- `window.XCM` exposes the internals so you can drive the game headlessly — useful for balance
  testing (`XCM.autoPlayRace()`, `XCM.simulateToEnd()`, `XCM.newGame()`).
