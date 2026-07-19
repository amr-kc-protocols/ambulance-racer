# 🚑 Ambulance Racer

A retro pseudo-3D arcade racer in the style of SNES-era *Top Gear 2* — except you're
driving an ambulance through Auckland. Single self-contained HTML file, no
dependencies, works on desktop and mobile.

**Play it:** open `index.html` in any browser.

## Gameplay

- **5 laps** around a procedurally-shaped circuit against **7 rival racers** with
  rubber-band AI — your live race position is tracked on the HUD and minimap,
  overtakes are announced, and the pack gets a little faster every lap.
- **Siren mechanic:** flip on the lights and sirens and civilian traffic pulls over
  to the shoulder and slows down. Passing a yielded car with the siren running
  earns a *Right of Way* score bonus.
- **Nitro** boost with a regenerating gauge, **drafting** behind cars for a slipstream
  speed bonus, **damage** that saps your top speed past 70%, and **fuel** that refills
  each lap (run dry and you limp).
- Lap times are called out as you cross the line (with your last lap kept on the
  HUD), and best lap + high score persist in `localStorage`.

## Controls

| Input | Action |
|---|---|
| `←` `→` / `A` `D` | steer |
| `↑` / `W` | accelerate |
| `↓` | brake |
| `Space` | nitro |
| `S` | siren on/off |
| `P` | pause |
| `M` | mute |
| `R` | restart |

Touch controls (steer, gas, brake, nitro, siren) appear automatically on
mobile devices.

## Tech notes

- 320×224 canvas (SNES resolution) upscaled with `image-rendering: pixelated`.
- Classic pseudo-3D road: per-frame screen rows with screen-space curve
  accumulation, hills from a height function, painter's-algorithm rendering
  with distance fog.
- The minimap outline is traced from the actual track curvature function, and
  rival positions are plotted on it live.
- Sound is generated with the Web Audio API: engine pitch follows RPM within the
  current gear (idling on the grid during the countdown), a hi-lo two-tone siren,
  looped-noise off-road rumble, noise-burst crashes, and countdown beeps.
