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

### Race tactics

Before each race you brief every runner on how to race their leg:

| Tactic | What it does |
|---|---|
| **Even Pace** | Steady and sensible. Almost never goes wrong. |
| **Front Run** | Go hard from the gun and try to break them. Brutal on the legs. |
| **Sit And Kick** | Tuck in, save everything, unleash it late. |
| **Negative Split** | Start within yourself and wind it up all the way home. |
| **Hold The Inside** | Fight for the shortest line — quickest route, but that is where the traffic is. |
| **Stay Wide** | Run in clean air out of the trouble. Safe, but it is the long way round. |

They will *try*. Each tactic leans on an attribute — front running needs fitness, a kick needs
sprint, holding the inside needs sure footing — and a runner who isn't built for it can get it
wrong, pay the price and get nothing back. The results screen tells you who nailed it and who
didn't.

Runners pick their own line through the race, drift across the track, and swing out to pass when
somebody is in their way. **The inside is the shortest way round, so it is quicker — but it is also
the line everybody runs, so it churns up worst and it is where you get boxed in.** On firm ground
the inside wins; on a muddy course the fresher ground out wide is often faster. There is no single
right answer, which is the point. **Suggest Tactics** reads the course and briefs the squad for you
if you would rather not micro-manage.

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
  piece of terrain is what *unlocks training* for that attribute. **Buy the same ground again** and
  you get more of it in your home course and better sessions on it (+14% per extra piece); the flat
  attribute bonus goes up too, but with sharp diminishing returns so stacking terrain can't simply
  buy you away wins.
- **Shoes** — mud claws, fell shoes, grass spikes, carbon racers. Each pair has trade-offs (carbon
  racers are quick but hopeless in mud). Pairs go into the kit bag and you assign them per runner.

### Building the ground

Everything on the ground can be bought **over and over** — each one costs more than the last, and the
point is to keep making the place bigger.

| | What it does |
|---|---|
| **Grandstand** | +2% to your runners at home *each*, and sells tickets — the takings vary every race day |
| **Food Truck Pitch** | They pay you for the pitch. A bit every race week, treble on home race day |
| **Club Gift Shop** | Ticks over all week, roaring trade at home |
| **Live Band** | +18% ticket sales each — people come for the day out, not just the running |
| **Social Media Team** | Mid-priced and earns very well every week |
| **Big Screen** | Slow to pay for itself, but worth **+40% more every season** you own it |
| **Camera Crew & Rig** | Brutally expensive, and poor value in the village league — but TV money climbs steeply with your division. About £1,400 a season at the bottom, nearly £10,000 at the top |

Ticket money and pitch fees are rolled fresh every race day, so no two are the same. Everything you
build appears on your home course: stands ring the loop with a crowd in them, food trucks and the
gift shop line the finishing straight, big screens and camera towers go up around it.

### Home advantage

You race at home once a season, and it is worth turning up for:

- **+8%** on your runners' attributes simply for being on your own ground
- **+2% per stand** you have built, with the crowd behind them
- your facility bonuses count double
- the course is the one built from the terrain you bought, which is the ground you train on
- gate receipts and a bumper day in the gift shop

Both percentages lift your runners' *attributes*, not their raw speed — the whole speed attribute,
0 to 100, is only worth a 16% swing, so a flat 8% on speed would decide the race on its own. Even
applied to attributes it is a big edge, and it grows every time you build another stand: a developed
ground makes the home fixture close to a certainty. That is deliberate — it is the race you build
towards all season. The constants are `HOME_BOOST` and `STAND_BOOST` near the top of the `DATA`
section if you want a tighter contest.

**Training** is three sessions a week, and each session trains the **whole squad** in one attribute.
Gains shrink as an attribute approaches 100, so you can't just max everything — your weakest runners
improve fastest.

You don't just click a button: the squad goes out onto the ground you're training on and you watch
them work it. A mud session runs in the mud pit, hill work goes round the hill circuit, wind work is
out on the exposed ridge, and the improvements pop up over each runner's head as they earn them.
Afterwards you get the full before-and-after for all ten.

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
