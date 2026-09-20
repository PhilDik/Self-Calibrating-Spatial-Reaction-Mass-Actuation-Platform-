# Self-Calibrating Spatial Reaction-Mass Actuation Platform

**Status:** unvalidated concept; corrected working draft  
**Revision date:** 2026-09-20  
**Author / inventor:** Philipp Dik

The repository contains an earlier English edition recorded on 2026-09-17; the primary draft also carried 2026-09-16. Those historical labels do not establish a new release, verified first public disclosure date or patent priority. This revision incorporates the later four-path scope.

## Abstract

This repository records an unvalidated reaction-mass research proposal. The current candidate uses four independently controlled solid movers in four spatially offset, interwoven, oppositely twisted closed guide paths. Distributed actuation would select where and when each mover accelerates, coasts or brakes. Paired regions are intended to reduce unwanted reactions, while differential actions are intended to create selected host-body moments. The attainable compensation and three-axis torque authority have not been established. The four-path proposal targets attitude-control and stabilization experiments for aircraft or spacecraft.

The earlier one-mover circular or oval guide is retained as a component testbed. A separate ground spherical-robot concept uses three ring guides with one mover per ring; projected crossings require physical clearance. These are distinct embodiments, not a single validated mechanism.

A steel sphere is a convenient test mover, not a requirement of the concept. The current four-path proposal uses solid movers; it does not require liquid or plasma masses, magnetic suspension, a shared central chamber or a central four-channel synchronization node.

The proposed controller would learn a bounded empirical relationship between mover state, actuation and measured host response, then select actions within the available authority. Calibration and reaction-mass control are established methods. No prototype, measured performance dataset or validated simulation is supplied here.

## Preferred electromagnetic embodiment

The earlier one-mover bench embodiment is proposed to contain:

1. A host body or carrier device.
2. A closed guide fixed within it.
3. One freely moving magnetic or ferromagnetic element; a steel sphere is the preferred compact prototype mover.
4. Independently commutated electromagnetic sections distributed along the path.
5. Sensors for mover phase, direction, and speed.
6. Power switches for acceleration and controlled braking.
7. A controller that selects pulse timing and shape.
8. An IMU and, when needed, an optical displacement sensor or external reference.

The coils and magnetic circuit act as the stator of a closed-path tubular linear motor, while the sphere acts as the free moving element. A magnetic-field maximum is created ahead of the sphere and switched before the sphere becomes trapped at the center of an active coil.

For a plain steel mover in a simple unsaturated reluctance model, force scales with current squared and the inductance gradient. Reversing current alone does not reverse attraction. Acceleration and braking require position-dependent commutation; force, sensing accuracy, electrical limits and heating remain to be measured. This is a proposed drive, not a validated motor design.

## Position sensing

Position may be measured with magnetic, inductive, optical, capacitive, or combined sensors. A Hall sensor measures magnetic field rather than ordinary steel directly. It is therefore especially convenient when the sphere is magnetized or contains a magnet. The position of an ordinary steel sphere may instead be determined from perturbation of an auxiliary magnetic field, changes in coil inductance, or the coil's current-voltage response. Measurements taken during short pauses between power pulses reduce interference from the actuation coils.

## Reaction generation

For a point mover in a fixed, nonrotating guide, the incremental dynamic reaction on the host, with gravity excluded from this simplified expression, is:

```text
f_host,i = -m_i [sddot_i t_i + sdot_i^2 kappa_i n_i]
```

Here s is arc length, t is the local tangent, n is the curvature normal, and kappa is curvature. A moving or rotating host requires the full inertial acceleration, including origin acceleration, Coriolis, angular-acceleration and centrifugal terms. Gravity, rolling spin, contact couples, compliance and impacts must be treated consistently. The curvature term already represents the acceleration sustained by the guide constraint.

Simultaneous mover loads are summed at the same time and about a consistently defined reference O:

```text
F(t) = sum_i f_i(t)
torque_O(t) = sum_i [r_i(t) x f_i(t) + contact_couple_i(t)]
J = integral F(t) dt
K_O = integral torque_O(t) dt
```

Actions at different phases occur at different times. Their impulses and the resulting body dynamics must be integrated; they are not an instantaneous sum of forces. Varied tangents and lever arms do not by themselves establish a requested force-and-torque workspace.

## Path geometries

These earlier geometry sketches describe possible test paths, not proven control authority or the final four-path layout. Actual workspace depends on geometry, phase, dynamics and actuator limits.

### Circular or oval path

This is the simplest geometry and the preferred geometry for a first prototype. It is suitable for continuous sphere motion, directional vibration, periodic impulses, active imbalance, and angular-momentum exchange.

### Elongated and non-planar path

An elongated shape changes the available tangents and lever arms. Smooth changes in elevation add vertical components. Paired sections can provide similar horizontal but different vertical reactions, allowing normal-force components to be added or cancelled.

### Figure-eight and multi-lobed forms

A spatial figure-eight is only one possible embodiment and does not define the overall system. Its loops provide different lever arms relative to the center of mass, while branches at a projected crossing are separated vertically. Helical, knotted, and multi-lobed forms are appropriate when the expanded force-and-torque workspace justifies added mechanical complexity.

### Spherical interwoven path

An approximately spherical path may be a single continuous spatial curve interwoven through a three-dimensional volume. Some arcs lie near a notional spherical surface, while concave arcs and chord-like transitions pass inward and connect distant regions. As a result, the tangents, curvature normals, and impulse lever arms span a substantially broader set of three-dimensional directions than those of a planar ring.

An apparent crossing of arcs may be implemented in three ways:

- spatial separation as an overpass and underpass;
- a smooth connection forming part of one continuous route;
- an electromagnetically controlled junction selecting one of several closed subroutes.

The controller would select feasible actions at particular phases. The combined model and measurements must establish the attainable workspace; neither non-planarity nor calibration guarantees an arbitrary reaction direction.

### Current four-path scope

The later proposal uses four spatially shifted, interwoven, oppositely twisted closed paths, each with its own solid mover. Paired regions are intended for coordinated circulation and differential acceleration/braking. The earlier central four-channel synchronization node is superseded.

No dimensioned four-path geometry is supplied. Physical separation, mover clearance and achievable compensation remain to be verified. The earlier switched-junction and single-route sketches are optional historical alternatives; they are not requirements of the current four separate paths.

## Control modes

### Continuous motion

The sphere maintains a nonzero average speed. Short accelerations and braking actions around that speed create reactions without repeatedly starting from rest.

### Impulse mode

Before a selected section, the sphere is slowed and then rapidly accelerated through it. Speed recovery is performed with a weaker, more extended, or differently directed action. Braking is as much a control action as acceleration; some energy may be recovered, although the amount is limited by losses and the power-stage architecture.

### Vibration and balancing

Actions are distributed among several sections to form a requested vibration spectrum, counter an external disturbance, change imbalance, or smooth a transient torque.

### Surface locomotion

Vertical reaction changes normal force while horizontal reaction is applied at a selected friction level. An asymmetric cycle produces sliding, rotation, or stick-slip motion.

### Compliant-support impulse assistance

An earlier related application coordinates a guided mass, pendulum or flywheel with a spring, suspension, leg or other compliant support. The proposed sequence senses compression and schedules acceleration, braking or reversal around the rebound. Whether this increases the useful external impulse depends on the coupled dynamics, actuator limits and contact timing. No universal optimum immediately after the lowest point is asserted.

Recovery reactions must be included in the full contact cycle. Internal actuation alone cannot change the combined centre-of-mass trajectory during isolated flight.

### Paired and counter-moving modules

Paired or counter-moving modules are proposed to reduce selected unwanted periodic reactions. Cancellation depends on mover mass, path geometry, phase, speed, acceleration and lever arm. Equal opposite speeds or zero summed angular momentum alone do not establish cancellation of force and torque.

Differential acceleration or braking can alter the host reaction, but the attainable command and residual vibration must be calculated and measured. Restoring phase or speed also produces reaction and must be included in the complete motion cycle.

### Four-mover control limits

The current candidate has four separately guided movers with independently commanded acceleration and braking. Three-axis attitude authority is a design objective, not an established result.

At fixed mover phases and speeds, a point-mass model can write the instantaneous wrench as w = d + B u, with four scalar tangential-acceleration inputs. The 6-by-4 matrix B has rank at most four. Its torque submatrix must have rank three, with feasible bounded commands, before local three-axis torque control can be claimed. Additional force-cancellation constraints can consume the remaining input freedom; a fourth actuator is not automatically a spare degree of freedom for arbitrary phase recovery, collision avoidance or vibration suppression.

A six-component force-and-torque representation does not imply six independently controllable outputs. Special geometry or finite-time control may change the feasible task set, but both require analysis of the actual paths and limits. Tetrahedral travel directions alone are not a proof because moment arms also matter.

Internal redistribution may rebalance individual mover momentum and available control margin. It cannot change the isolated system's total angular momentum. External disturbance momentum requires external unloading where needed.

### Collision prevention and phase recovery

The following shared-lane and junction constraints concern earlier multi-mover alternatives. The current four-path proposal uses separate guide paths and still requires clearance, retention and bounded control.

On one continuous one-way route, the ordering of spheres does not change. A strong impulse may temporarily reduce their separation but must not result in an actual overtake. The controller predicts relative motion and preserves a braking margin:

```text
free distance > relative-motion braking distance + safety clearance
```

After a rapid impulse, restoring phase or speed produces a further reaction. Any proposed compensated recovery must be evaluated over the complete motion cycle. Counter-directional motion requires separate parallel or spatially separated channels. At junctions, the controller reserves a branch in advance and prevents simultaneous entry by conflicting spheres.

### Optional two-module redundancy

An earlier optional arrangement uses two spatial modules with local controllers and supervisory monitoring. Full-axis backup is a requirement to be demonstrated for each module, not a consequence of using two modules.

Any backup function depends on remaining torque authority, sensing, electrical and thermal margins, and bounded fault reactions. A failed coil, sensor or guide may reduce controllability or observability; neighbouring actuators and the other module are not guaranteed to compensate. A common IMU or shared power path is a common failure dependency.

The proposal includes isolation and retention of a failed mover where possible. No healthy module can guarantee cancellation of unlimited spin-up or structural failure. Safe-state behaviour, failure energy and degraded control must be validated before fault-tolerant operation is claimed.

## Self-calibration

For selected phases and current profiles, the system records:

- sphere phase, direction, and speed;
- current, voltage, pulse duration, and temperature;
- host-body acceleration and rotation;
- actual displacement and heading change;
- vibration and settling time;
- state of contact or compliant support;
- onset of sliding, actuator saturation, or obstacle constraint.

Identification would begin with small actions within independently established current, temperature, speed, contact-load and mechanical limits. A detectable-motion or sliding threshold is a measured response property, not a safety limit. Command amplitude must not be increased without those limits merely because no body movement is observed.

Support state may be estimated probabilistically from IMU data, optical displacement, mover phase and response to bounded test actions. Distinct contact conditions can produce similar measurements. Sensor sufficiency and state identifiability must be validated; the present proposal does not establish that dedicated contact sensing is unnecessary.

Calibration is intended to support selection of feasible measured response primitives. It cannot create missing actuator authority or guarantee an arbitrary requested motion. Acceleration, braking and recovery must be evaluated together with the host and contact dynamics.

## Localization and return

A surface-facing optical sensor measures short displacements, while the IMU measures rapid acceleration and rotation. A visual, infrared, magnetic, or radio marker, or a docking station, removes accumulated error and allows return to a stored position.

If the device is lifted and moved, IMU and optical odometry alone are insufficient; it must be re-referenced to an external landmark.

## Integration into a motor or machine

The actuator may be located inside the housing of a conventional electric motor, joint, wheel module, tool, household appliance, or sealed machine as an additional controlled degree of freedom. The main motor rotates a shaft, while the internal mass independently creates a balancing action, compensates vibration, generates haptic feedback, smooths transient torque, or provides diagnostic excitation.

The main motor and auxiliary actuator may share the housing and controller, but a separate winding or magnetic path is generally more practical for the auxiliary mass. A single winding is suitable only when the requirements for main torque and internal-mass motion are compatible in magnetic flux, heating, and commutation timing.

## Example applications

The following are proposed applications, not demonstrated capabilities of this device. Each requires sufficient measured authority, bandwidth and operating margin.

- programmable directional vibration and haptic feedback;
- movement of a sealed enclosure without an external wheel drive;
- short-range self-positioning and return to a stored location;
- active balancing under changing load;
- suppression of imbalance in a washing machine, centrifuge, rotary tool, or other device;
- vibration compensation and controlled structural excitation;
- smoothing of transient torque in a motor or joint;
- control of normal force at an external contact point;
- impulse assistance for a suspension, spring, leg, flexible support, or other compliant mechanism;
- three-dimensional impulses and attitude control using a spherical interwoven path;
- paired counter-moving modules for stabilization and turning of an atmospheric or spacecraft vehicle;
- two full-axis spherical modules with mutual monitoring and redundancy in the event of partial or complete failure of one module;
- attitude control in free flight without any claim of reactionless translational thrust;
- identification of device and environmental properties from response to known internal impulses.

For an atmospheric vehicle, the internal modules may operate together with aerodynamic surfaces, propellers, or other external forces. In a spacecraft they can change attitude through angular-momentum exchange, but sustained operation requires unloading accumulated momentum through an external actuator, such as a magnetic torquer or attitude-control thruster.

In a washing machine, centrifuge, or rotary tool, sensors measure vibration and the controller would estimate imbalance and command masses to seek an opposing reaction. Unlike a passive ball balancer, the position and speed of the masses are actively commanded and corrected from measured vibration.


## Featured demonstrator embodiment: spherical mobile robot

A high-visibility, non-limiting prototype may place the spatial guideway inside a spherical mobile shell and add an optional magnetically coupled external head-like module for visual orientation and public demonstration. The resulting form factor can resemble familiar consumer spherical character robots, including the Sphero BB-8 toy, but the reference is only to the external demonstration format; the internal actuation method remains the distributed electromagnetic reaction-mass system disclosed here.

The separate ground demonstrator proposes three ring guides with one mover per ring and physical clearance at projected crossings. Experiments would assess rolling, steering, attitude response, rocking, vibration and contact impulses. Because selected guide arcs can produce reaction components with substantial vertical components, the controller may also schedule an upward ground-reaction impulse by accelerating, braking, or reversing a mover at an appropriate phase while the shell is in contact with the support. If the attainable momentum change, contact timing, traction, structural strength, and available stroke are sufficient, this may produce a short hop or assist traversal over a small obstacle.

The hop is a surface-coupled manoeuvre, not reactionless propulsion. The supporting surface supplies the external impulse to the complete device. During free flight, internal mass motion may alter attitude and redistribute angular momentum but cannot change the translational momentum of the isolated combined system.

The external head-like module is optional and may be retained by magnetic attraction or another low-friction coupling so that it remains visually upright while the main sphere rolls. It is not required for the core actuator and need not participate in force generation.

## Noise, impacts, and load transfer

A rolling steel sphere, guide joints, and rapid magnetic braking can generate audible structure-borne noise. It can be reduced by using a continuous smooth guide, avoiding abrupt joints, applying anticipatory magnetic braking, using compliant external mounts, and adding a local damping layer. The soft layer must not be so compliant that it substantially absorbs the useful impulse or disrupts coil-gap accuracy.

Reaction loads should be transmitted to the common rigid guide frame rather than to a decorative outer shell. In the current four-path proposal, the separated guides and their supports form part of the load-bearing structure.

## Proposed architecture and prior-art limits

The specific proposal under investigation is the four-path arrangement described above and its phase-dependent actuation policy. Generic internal masses, reaction wheels, acceleration/braking, adaptive response maps and paired compensation are not claimed as new.

Earlier patent disclosures already include four coordinated eccentric masses with adaptive compensation and tetrahedral multi-actuator layouts. Curved reaction-mass actuators with response characterization are also known. These are material prior art even though they do not establish the exact four interwoven non-planar guides proposed here. See [the prior-art review](prior-art.md).

No conclusion of novelty, inventive step, freedom to operate or demonstrated performance is asserted. The absence of an identified exact equivalent is not evidence of novelty.

## Physical limitations

The complete host-plus-mover system obeys external linear- and angular-momentum balance. Internal actuation cannot change the inertial trajectory of an isolated system's centre of mass. It can move the host relative to its internal masses and can change attitude; no reactionless translational thrust is claimed.

Surface locomotion and hopping require external support interaction. Slow or differently timed recovery does not remove the compensating internal reaction; the complete actuation and contact cycle must be analysed. A magnetorquer can unload spacecraft momentum only where a suitable external magnetic field is available; other missions require another external torque source.

## Example prototype parameters

- host-body mass: approximately 5–7 kg;
- available base: approximately 295 × 205 mm;
- one bearing-steel sphere: approximately 40 mm diameter and 0.26 kg;
- closed-path length: approximately 0.75–0.85 m;
- sphere speed: approximately 1.0–1.5 m/s;
- independently switched elongated coils: approximately 10–12;
- microcontroller, power switches, sphere sensors, IMU, and optional optical sensor.

These are unvalidated illustrative targets for the earlier one-mover bench concept, not a built prototype and not specifications of the four-path module.

## Purpose of publication

This document is intended as a clear, dated disclosure of the technical concept. A preliminary prior-art review is provided in `docs/prior-art.md` and is not a legal opinion on patentability. Public disclosure does not by itself create exclusive rights and may limit later patenting opportunities: depending on the jurisdiction and circumstances, disclosed information may become part of the prior art.


## Rights and publication status

Copyright © 2026 Philipp Dik. All rights reserved. No open-source or open-content license is granted by this repository unless a later version explicitly states otherwise.

