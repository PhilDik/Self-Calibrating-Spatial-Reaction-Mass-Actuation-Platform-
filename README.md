# Self-Calibrating Spatial Reaction-Mass Actuation Platform

**Version:** 0.4 — English GitHub edition  
**Disclosure date:** 2026-09-17  
**Inventor / author:** Philip Dik

> Primary technical disclosure: [`docs/description.md`](docs/description.md). The repository has been translated and normalized for English-language publication on GitHub.

## Abstract

This disclosure describes a generalized **self-calibrating spatial reaction-mass actuation platform**. One or more controlled internal inertial elements move through guides or related constrained trajectories fixed to a host body. Their acceleration, braking, reversal, and momentum exchange are scheduled to create programmed host-body force, torque, vibration, attitude response, and normal-force modulation.

A preferred electromagnetic embodiment uses a freely moving magnetic or ferromagnetic mover in a closed spatial guideway with distributed electromagnetic sections. A steel sphere is especially convenient for a compact prototype, but the general architecture is not limited to a spherical mover, a spherical host body, or a single guide geometry.

A circular or oval guide is the simplest embodiment. Non-planar, elongated, multi-lobed, helical, knotted, figure-eight, or approximately spherical interwoven guides are optional geometries when a broader set of reaction directions and moment arms is useful. In a spherical interwoven embodiment, some arcs may follow the outer volume while others pass through its interior. Projected crossings are physically separated or implemented as controlled junctions. Short acceleration, braking, or reversal at a selected arc produces a temporally localized impulse with a direction and lever arm determined by that arc.

One mover is preferred in a shared compact guide because independently controlled movers can collide during unequal acceleration or braking unless additional separation and phase-locking measures are provided.

The controller learns an empirical response model rather than relying only on nominal mechanics:

```text
(mover phase, speed, coil action, measured body state)
    -> (force response, displacement, rotation, vibration, settling)
```

It uses mover-position sensing, coil-current measurement, an IMU, and optionally surface optical flow or an external reference. The learned model can compensate for payload, support compliance, friction, obstruction, and whether the host is held, resting, sliding, rolling, or otherwise externally constrained.

The same control architecture may coordinate related internal inertial elements, including a guided reciprocating mass, pendulum, or flywheel, with an external compliant mechanism. One example is impulse assistance: the controller preloads a compliant support, detects reversal from compression to extension, then brakes or reverses an internal mass so that its reaction adds to the support rebound. This is an application example, not a requirement of the general reaction-mass architecture.

![System overview](figures/system-overview.svg)

## Featured demonstrator: spherical mobile robot with hop capability

A particularly intuitive prototype places the spatial reaction-mass system inside a rolling spherical shell. An optional externally mounted, magnetically coupled head-like module can remain visually upright while the main body rolls, giving the demonstrator a form factor reminiscent of familiar spherical character robots such as Sphero's BB-8 toy. The resemblance is only an external demonstration format; the internal actuation architecture described here is different.

The demonstrator can be used to show rolling, steering, attitude correction, rocking, vibration, and rapid impulse response. With sufficient internal momentum change and correctly timed surface contact, selected reaction-mass actions may also increase the upward ground-reaction impulse and produce a **short hop** or hop-assisted obstacle traversal. This is a prototype objective rather than a guaranteed performance claim. In free flight, internal masses can redistribute attitude and angular momentum but cannot accelerate the isolated system's center of mass.

The same platform concept also applies to non-spherical hosts, linear shuttles, capsules, pendula, flywheels, multiple isolated movers, and hybrid mechanisms. The spherical robot is therefore a high-visibility example, not the definition of the invention.

## 1. Technical field

The system relates to electromagnetic actuation, inertial and vibration control, surface-coupled locomotion, haptics, active balancing, motor integration, programmable reaction masses, and self-calibrating robotic devices.

## 2. Preferred electromagnetic embodiment

The principal prototype embodiment contains:

1. A host body.
2. A closed guide fixed to the host.
3. One freely moving magnetic or ferromagnetic inertial element; a steel sphere is the preferred compact prototype mover.
4. Independently controllable electromagnetic sections distributed along the guide.
5. Sensors estimating mover phase, direction, and speed.
6. Power stages that apply local acceleration and controlled braking.
7. A controller that schedules those actions from a desired body response.
8. Body-state sensing, preferably an IMU and, when relevant, optical flow or another displacement reference.

The moving sphere is the translator of a closed-path tubular linear reluctance motor. The coils and magnetic circuit form its stator. A travelling field maximum is commutated ahead of the sphere for acceleration and removed or shifted before the sphere reaches a trapping field centre.

## 3. Position sensing

Position may be measured by magnetic, inductive, optical, capacitive, or combined sensors. A Hall sensor directly measures magnetic field, not ordinary steel itself. Hall sensing is straightforward when the mover is magnetized or contains a magnet. With a plain steel sphere, position may instead be inferred from perturbation of a biased magnetic field, from coil inductance, or from current/voltage response. Measurements may be taken during coil-current off-windows to reduce interference from the actuation field.

## 4. Force generation

For a mover of mass `m` travelling at speed `v` along a path parameterized by arc length, the approximate reaction applied to the host is:

```text
F_host = -m[(dv/dt)t + v^2 kappa n]
```

where `t` is the local tangent, `n` is the curvature normal, and `kappa` is path curvature. Rolling inertia, gravity, guide contact, compliance, and impact add further terms.

At one phase, the immediate reaction is constrained by local path geometry. Across a curved or non-planar guide, the available directions change. Timed actions at several phases can synthesize a resultant force and torque:

```text
F_result = sum(F_i)
Torque_result = sum((r_i - r_COM) x F_i)
```

The useful control object is therefore not only the global path shape but a catalogue of local impulse sites. Each site has a tangent, curvature normal, position relative to the host centre of mass, usable mover-speed range, and measured body response. A short pulse is approximately localized in time, while its force and torque are distributed through the guide supports into the host structure.

## 5. Guide geometries

### 5.1 Circular or oval guide

The simplest embodiment is a smooth closed loop. It is suitable for circulation, vibration, periodic impulse generation, active imbalance, and torque exchange. It is also the preferred geometry for an initial prototype.

### 5.2 Non-planar and elongated guide

A stretched or non-planar loop prioritizes selected axes while retaining out-of-plane control. Smooth elevation changes can provide paired phases with similar horizontal and different vertical reactions, allowing the controller to add or cancel normal-force modulation.

### 5.3 Multi-lobed or figure-eight guide

A figure-eight is one optional implementation, not the defining geometry. Its lobes provide separated lever arms and its projected crossing can be vertically separated. More general helical, knotted, or multi-lobed paths may be used when the desired force-and-torque workspace justifies additional mechanical complexity.

### 5.4 Spherical interwoven guide

An approximately spherical guide may be formed as a single continuous spatial curve woven through a three-dimensional volume. Some arcs may lie near the notional sphere surface, while inward-curving arcs or chord-like transitions pass through the interior and reconnect remote regions. This produces impulse sites whose tangents, curvature normals, and lever arms cover a wider three-dimensional set than a planar loop.

Apparent intersections do not require the mover to collide with another path segment. They may be:

- separated spatially as overpasses and underpasses;
- connected by smooth transitions belonging to one continuous route; or
- built as electromagnetically switched junctions that select one of several closed subroutes.

The controller may accelerate, brake, or reverse the mover near a selected interior or surface arc. This creates a short, directionally selected reaction and a corresponding moment about the host centre. Several nearby actions can be composed to refine the effective direction. The achievable force-and-torque workspace is determined experimentally and need not be inferred from ideal geometry alone.

![Guide geometry variants](figures/guide-geometry-variants.svg)

## 6. Control modes

### 6.1 Continuous circulation

The mover maintains a nonzero baseline speed. Small speed changes around that baseline create controllable reactions without repeatedly starting from rest.

### 6.2 Impulse generation

The mover is slowed before a selected phase, accelerated through it, and then recovered with a lower-amplitude or differently timed action. Acceleration and braking are both usable control actions.

### 6.3 Distributed vibration or balancing

Actions are spread across several guide sections to create a requested vibration spectrum, counter an observed disturbance, change apparent imbalance, or smooth transient torque.

### 6.4 Surface-coupled locomotion

When the host contacts a surface, vertical reaction may unload or reload the contact while a horizontal reaction is applied. Asymmetric cycles can produce stick-slip translation or rotation.

### 6.5 Compliant-support impulse assistance

In a related embodiment, an internal pendulum, linear shuttle, flywheel, or selected segment of the closed-path mover is coordinated with a spring, suspension, flexure, leg, wheel, or other compliant support:

1. an enable command arms the sequence;
2. the controller detects increasing compression;
3. internal-mass motion may increase preload;
4. near the compression-to-extension reversal, the mass is braked or reversed;
5. its reaction is aligned with support rebound;
6. later recovery is shaped to avoid cancelling the useful impulse.

The external contact supplies the net impulse to the combined system. Once isolated in free flight, internal motion can redistribute attitude and momentum between components but cannot accelerate the combined centre of mass.

### 6.6 Paired and counter-moving modules

A continuously circulating mover produces periodic reaction components even when only one component is desired. Two or more mirrored actuator modules may therefore be phase-locked and driven in common or differential modes. Their paths, mover directions, speeds, and pulse timing are selected so that unwanted periodic forces, torque ripple, and stored angular momentum cancel, while a selected force or turning moment adds.

For example, two mirrored movers may circulate in opposite directions at equal baseline speed. Symmetric correction changes preserve cancellation; differential acceleration or braking temporarily creates a commanded moment. The controller measures residual vibration and continuously trims phase and speed because manufacturing tolerance, payload, and wear prevent perfect open-loop cancellation.

One module is not physically impossible, but a paired arrangement is preferable when low vibration, stable attitude, or clean rotational impulses are primary requirements.

## 7. Self-calibration and adaptive control

For selected path phases and current profiles, the controller records:

- mover phase, direction, and speed;
- coil current, voltage, timing, and temperature;
- host acceleration and angular velocity;
- measured displacement and heading change;
- vibration and settling time;
- contact or suspension state when available;
- whether static friction, compliance, saturation, or an obstruction limited the response.

The controller builds and continuously updates a response map. It may begin with low-energy identification pulses, estimate the current operating envelope, retain a conservative baseline, and then select combinations of learned actions for translation, rotation, vibration, balancing, impulse assistance, or disturbance rejection.

## 8. Localization and return behavior

An optical-flow sensor facing the support may estimate short-range planar motion. An IMU estimates rapid movement and attitude. Visual features, an infrared or magnetic marker, a radio beacon, or a physical dock can remove accumulated drift and allow return to a stored pose.

If the host is lifted and manually relocated, IMU and optical-flow dead reckoning alone do not provide absolute recovery. Environmental re-localization is required.

## 9. Integration into another motor or machine

The actuator may be integrated into the housing of a conventional electric motor, joint, wheel module, tool, appliance, or sealed machine as an additional controlled degree of freedom. The main motor produces shaft torque; the internal mover provides independently timed reaction, balancing, vibration cancellation, haptic output, transient-torque shaping, or diagnostic excitation.

The auxiliary actuator may share a housing and controller with the main motor while using a separate winding or magnetic-flux path. Reusing the same winding is possible only when the competing torque and mover-control requirements are magnetically and thermally compatible.

## 10. Example applications

Non-limiting examples include:

- programmable directional vibration and haptic feedback;
- sealed or externally wheel-free surface motion;
- short-range self-positioning and return to a stored location;
- active balancing and compensation of changing payload;
- active imbalance cancellation in washing machines, centrifuges, rotating tools, and other appliances;
- vibration cancellation and structural excitation;
- transient torque smoothing in motors and joints;
- deliberate normal-force modulation at a contact;
- impulse assistance coordinated with suspension, springs, legs, flexures, or compliant mounts;
- three-dimensional reaction and attitude-control experiments using a spherical interwoven guide;
- paired counter-moving modules for vibration suppression and attitude control in aircraft or spacecraft;
- controlled attitude exchange in free flight, without a claim of reactionless propulsion;
- system identification by applying known internal impulses and observing the host response.



## 11. Distinguishing combination

The principal disclosed combination includes:

- one free magnetic or ferromagnetic mover in a shared closed guide;
- distributed electromagnetic acceleration and controlled braking;
- phase-selective generation of reaction force and torque;
- optional non-planar or spherical interwoven geometry for additional reaction directions;
- empirical learning of the relationship between mover action and host response;
- adaptation to changing payload, friction, compliance, and constraints;
- composition of learned response primitives for a requested effect;
- optional integration with localization, a conventional motor, or a compliant external mechanism;
- optional mirrored pairing that cancels parasitic reaction while retaining a commanded force or moment.

Individual coil accelerators, passive ball balancers, vibration robots, flywheels, reaction masses, homing systems, and jumping mechanisms are known. This disclosure concerns the stated mechanical, sensing, commutation, and adaptive-control combination.

## 12. Physical limitations

The actuator does not produce reactionless thrust. Persistent translation requires exchange with an external surface, fluid, field, expelled mass, tether, or other environment. Internal motion alone can create temporary host reactions, attitude exchange, vibration, and redistribution of momentum, but cannot translate the combined centre of mass of an isolated system.

## 13. Example prototype envelope

One non-limiting surface-coupled prototype may use:

- host mass: approximately 5–7 kg;
- available base envelope: approximately 295 × 205 mm;
- one bearing-steel sphere: approximately 40 mm diameter and 0.26 kg;
- closed guide length: approximately 0.75–0.85 m;
- mover speed: approximately 1.0–1.5 m/s;
- independently switched elongated coils: approximately 10–12;
- microcontroller, coil drivers, mover sensors, IMU, and optional optical flow.

These figures illustrate one test platform and do not limit the broader principle.

## 14. Prior-art context and publication purpose

See [docs/prior-art.md](docs/prior-art.md). The search is preliminary and is not a legal patentability opinion. This document is intended as a clear, dated technical disclosure. Public disclosure does not itself grant exclusive rights and may affect later patent protection. Obtain jurisdiction-specific legal advice before publication if patent protection is desired.

## Related work and terminology

The design uses established engineering terminology including **reaction mass**, **closed-loop guideway**, **distributed electromagnetic actuation**, **phase-selective actuation**, **system identification**, and **force/torque response map**. Related systems include fluid-actuated spherical robots with guided internal moving masses and electromagnetic magnetic-ball positioning systems; the closest references and explicit distinctions are summarized in [`docs/prior-art.md`](docs/prior-art.md).

## Citation

Citation metadata is provided in [`CITATION.cff`](CITATION.cff). Replace all author and repository placeholders before publishing.
