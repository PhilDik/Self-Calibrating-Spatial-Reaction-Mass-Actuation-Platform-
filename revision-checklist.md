# Revision checklist for English edition 0.3

This checklist records which decisions from the discussion are included in the primary technical text `description.md`.

## Core architecture

- The baseline compact prototype uses one steel or ferromagnetic sphere.
- Coils are actuated sequentially according to sphere position; they do not necessarily energize simultaneously.
- The coils and guide are treated as a closed-path tubular linear motor.
- Acceleration, coasting, braking, and limited energy recovery are considered.
- A Hall sensor is not treated as a direct universal sensor for ordinary steel; magnetic markers, inductance measurement, and pauses between power pulses are provided as alternatives.

## Geometry

- A circle or oval remains the simplest embodiment.
- An elongated non-planar path can strengthen selected horizontal directions.
- A spatial figure-eight remains an example rather than a required form.
- At a visible projected crossing, channels are separated in height.
- The spherical interwoven path includes outer arcs, inward concave arcs, chord-like transitions, and controlled junctions.
- A central node with four isolated tubes at different spatial angles is included.
- The center is used primarily for synchronization and cancellation of linear reactions; strong torque is generated on outer arcs with larger lever arms.

## One or multiple spheres

- The "one sphere" rule is limited to a compact shared single-lane path.
- A larger device may use multiple spheres on isolated or reservable routes.
- On a shared one-way path, spheres may temporarily reduce separation but may not overtake each other.
- Counter-directional motion requires separate parallel or spatially separated channels.
- After a strong impulse, phases are restored using a slower compensated action.
- Collisions are prevented by predicting relative braking distance and reserving junction branches.

## Spatial stabilization

- A pair of modules is described as a special case for one plane, not a complete solution.
- For three-axis control, an example with four spheres along non-coplanar, approximately tetrahedral directions is included.
- Compensation is based on impulse and torque vectors, not simply equal traveled distance.
- The fourth control degree of freedom is used for phase alignment, vibration reduction, and collision avoidance.
- Four spheres are not claimed as mandatory; other configurations with full three-axis coverage are permitted.
- A six-dimensional formulation is noted for simultaneous control of three force and three torque components.
- An architecture with two full-axis spherical modules is included; in normal operation they share load and monitor each other's response.
- If one unit fails, the other can programmatically rotate its action direction by selecting arcs and enter full-axis backup mode.
- Each module should have enough force, torque, power, and thermal margin for temporary operation in place of both.
- Compensation limits are stated: a healthy module cannot guarantee cancellation of unlimited spin-up or mechanical destruction of the failed unit.
- Independent power isolation, braking or locking of masses, and a minimum-vibration safe mode are provided.

## Control and learning

- The controller begins with small diagnostic impulses and finds a measurable action threshold.
- The operating baseline is selected slightly below the detected limit.
- Acceleration, braking, sliding, compliance, and settling time are learned separately.
- The controller distinguishes a hard surface, soft support, hand-held state, rolling, sliding, and obstacle blockage from combined sensor data.
- Dedicated sensors in the feet are not required.
- The response map is updated when load, friction, or conditions change.
- Returning to a stored location requires an external reference if the device has been lifted and moved.

## Additional embodiments and applications

- Integration inside a conventional electric motor remains an optional embodiment.
- The auxiliary system will generally require a separate winding or magnetic path.
- Impulse assistance for a suspension, spring, leg, or other compliant support is included.
- The useful impulse is synchronized with the transition of the support from compression to extension.
- Active balancing of washing machines, centrifuges, and rotary tools is included.
- Stabilization and turning of atmospheric and spacecraft vehicles are included.
- For spacecraft, the text explicitly states that there is no reactionless translational thrust and that accumulated angular momentum requires external unloading.
- Rolling noise, impacts, damping, and load transfer into the structural frame are addressed.

## First prototype parameters

- Host body: 5–7 kg.
- Base: approximately 295 × 205 mm.
- One sphere: approximately 40 mm and 0.26 kg.
- Path: approximately 0.75–0.85 m.
- Speed: approximately 1.0–1.5 m/s.
- Approximately 10–12 independently switched coils.
- Microcontroller, power switches, position sensors, IMU, and optional optical odometry.
