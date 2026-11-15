# Setup Unleashed

A suspension and setup simulator that runs in the browser. A full car with a double wishbone suspension at every corner drives around a circuit; you change springs, dampers, anti-roll bars, alignment, tire pressures and brake bias, and see what that does to the balance, the grip and the lap time.

Everything is in one file, `index.html`. Open it in a browser, or publish the repository with GitHub Pages.

## What it does

**The car**
- Ride model with heave, pitch and roll, four unsprung masses, coil springs through a motion ratio, 2-way dampers (bump and rebound), bump stops and an anti-roll bar per axle.
- Double wishbone kinematics at every corner: camber gain, caster, bump steer and Ackermann steering.
- Tires with load sensitivity, camber sensitivity, tire pressure (stiffness, response and peak grip), and combined slip: each wheel spins on its own, so wheels can lock under braking and spin under power.
- Rear-wheel drive, adjustable brake bias.

**On track**
- Two circuits: a flowing club circuit, and a handling track built to test balance (sweeper, esses, hairpin, crest, bumpy braking zone, off-camber corner).
- Hills, rough patches, raised kerbs, grass, skid marks.
- Drive yourself (keyboard or touch, with optional ABS and traction help) or let the autopilot drive:
  - **Follows line**: follows the racing line and its speed plan blindly; setup flaws show plainly.
  - **Catches slides**: also countersteers on oversteer and lifts on understeer.
  - **Learns track**: finds the car's limit lap by lap, separately for cornering and braking, until the lap times settle.
- Planned braking with trail-braking, traction-limited throttle, threshold braking at the slip limit.

**Analysis**
- Lap and sector timing, a live delta, a lap table and a lap history plot.
- A ghost car replaying the fastest lap on each track.
- Live telemetry (body angles, driver inputs), a balance gauge, a g-g diagram with grip-use summary, tire cards with grip circles.
- Setups A and B, with side-by-side fast runs that compare them sector by sector.
- A setup optimizer (CMA-ES) and a one-setting scan, running off-screen in Web Workers, much faster than real time.

**Test rig**
- The car on a rolling road with set road profiles, and simulated cornering and braking forces, for looking at the suspension without driving.

## Running it

Open `index.html` in a current desktop or mobile browser. It loads three.js from cdnjs and the fonts from Google Fonts, so it needs an internet connection; there is no build step.

To host it: in the repository settings, enable **Pages** with the `main` branch as the source. The simulator is then served at `https://<user>.github.io/setup-unleashed/`.

Driving yourself: arrow keys or W A S D; on touch screens, the buttons on the 3D view. Rest the pointer on any control for a short description.

## Notes on the model

The physics is a teaching model, not a validated vehicle model. Not modelled: a limited-slip differential, aerodynamics, camber thrust, kingpin inclination, tire temperature. The roll and pitch centres sit at ground level. The autopilot's limit is the limit for this autopilot, not for a perfect driver, and the optimizer finds what this model rewards; treat extreme results as a question, not an answer.

## Design

The interface follows the Racing Unleashed brand guidelines (colours, Bai Jamjuree and IBM Plex typography). No logos are included.

## Licence

All rights reserved. No licence is granted for reuse.
