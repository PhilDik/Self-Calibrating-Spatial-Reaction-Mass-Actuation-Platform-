# Self-Calibrating Spatial Reaction-Mass Actuation Platform

**Version:** 0.3 — primary English working draft  
**Disclosure date:** September 16, 2026  
**Author / inventor:** Philip Dik

This English edition is the current primary text translated from the approved Russian working draft.

## Abstract

This document describes a generalized self-calibrating **spatial reaction-mass actuation platform**. One or more constrained internal inertial elements are accelerated, braked, reversed, or otherwise controlled so that their momentum exchange creates a programmable reaction of the host body: force, torque, vibration, attitude response, and modulation of normal force against an external support.

A preferred electromagnetic embodiment uses one freely moving magnetic or ferromagnetic body, conveniently a steel sphere, travelling through a **closed-loop spatial guideway** fixed inside the host. Distributed electromagnetic sections provide **position-dependent, phase-selective actuation**: they determine mover phase and locally accelerate, coast, and brake it. The guide and coils can operate as a closed-path tubular linear motor. The broader architecture is not limited to a spherical mover, spherical host, or this motor topology.

A circular or oval path is the simplest embodiment. Elongated, non-planar, multi-lobed, helical, knotted, spatial figure-eight, or spherical interwoven paths are additional geometries that expand the set of available force directions and torque lever arms. In the spherical embodiment, some arcs may run near a notional outer shell while others pass inward through the volume and connect distant regions. Apparent crossings are separated spatially or implemented as controlled junctions. Short acceleration, braking, or reversal of the sphere on a selected arc creates a temporally localized impulse whose direction and lever arm are determined by the geometry of that arc.

For one compact shared single-lane path, one sphere is preferred: multiple independently accelerated bodies can collide under unequal acceleration or braking. In a larger spatial device, multiple spheres are permitted when isolated channels, bypass branches, controlled junctions, and predictive separation control are provided. Thus, the single-sphere prototype and the multi-channel spherical system are different scales of the same general architecture rather than mutually exclusive solutions.

The controller does not rely only on a calculated model; it experimentally learns the relationship:

```text
(sphere phase and speed, coil command, host-body state)
    -> (reaction, displacement, rotation, vibration, settling time)
```

This allows the system to adapt to payload mass, friction, support compliance, obstacles, and whether the device is on a surface, held in the hand, on wheels, or subject to another external constraint.

The same sensing and control architecture can coordinate related internal masses: a linear shuttle, pendulum, or flywheel. One example is impulse assistance for a compliant support: the controller detects the transition from compression to extension of a suspension, spring, leg, or other compliant element and at that moment brakes or reverses the internal mass so that its reaction adds to the support rebound. This is an application example, not a required feature of the general platform.

## Preferred electromagnetic embodiment

The principal prototype implementation contains:

1. A host body or carrier device.
2. A closed guide fixed within it.
3. One freely moving magnetic or ferromagnetic element; a steel sphere is the preferred compact prototype mover.
4. Independently commutated electromagnetic sections distributed along the path.
5. Sensors for mover phase, direction, and speed.
6. Power switches for acceleration and controlled braking.
7. A controller that selects pulse timing and shape.
8. An IMU and, when needed, an optical displacement sensor or external reference.

The coils and magnetic circuit act as the stator of a closed-path tubular linear motor, while the sphere acts as the free moving element. A magnetic-field maximum is created ahead of the sphere and switched before the sphere becomes trapped at the center of an active coil.

## Position sensing

Position may be measured with magnetic, inductive, optical, capacitive, or combined sensors. A Hall sensor measures magnetic field rather than ordinary steel directly. It is therefore especially convenient when the sphere is magnetized or contains a magnet. The position of an ordinary steel sphere may instead be determined from perturbation of an auxiliary magnetic field, changes in coil inductance, or the coil's current-voltage response. Measurements taken during short pauses between power pulses reduce interference from the actuation coils.

## Reaction generation

For a mass `m` moving at speed `v`, the approximate host-body reaction is:

```text
F_host = -m[(dv/dt)t + v^2 kappa n]
```

Here `t` is the local tangent, `n` is the curvature normal, and `kappa` is the path curvature. Rolling, gravity, guide contact, compliance, and possible impacts add further terms.

At any one point, the direction of action is constrained by the path geometry. As the mover travels around a closed curve, the available directions change. Controlled actions at several phases combine into a required force and torque:

```text
F_result = sum(F_i)
Torque_result = sum((r_i - r_COM) x F_i)
```

The controller therefore treats the path as a set of local impulse sites. For each site it considers the tangent, curvature normal, position relative to the center of mass, allowable sphere speed, and measured host-body response. An impulse may be nearly point-like in time, but the force is transmitted into the structure through the guide supports.

## Path geometries

### Circular or oval path

This is the simplest geometry and the preferred geometry for a first prototype. It is suitable for continuous sphere motion, directional vibration, periodic impulses, active imbalance, and angular-momentum exchange.

### Elongated and non-planar path

An elongated shape strengthens selected action axes. Smooth changes in elevation add vertical components. Paired sections can provide similar horizontal but different vertical reactions, allowing normal-force components to be added or cancelled.

### Figure-eight and multi-lobed forms

A spatial figure-eight is only one possible embodiment and does not define the overall system. Its loops provide different lever arms relative to the center of mass, while branches at a projected crossing are separated vertically. Helical, knotted, and multi-lobed forms are appropriate when the expanded force-and-torque workspace justifies added mechanical complexity.

### Spherical interwoven path

An approximately spherical path may be a single continuous spatial curve interwoven through a three-dimensional volume. Some arcs lie near a notional spherical surface, while concave arcs and chord-like transitions pass inward and connect distant regions. As a result, the tangents, curvature normals, and impulse lever arms span a substantially broader set of three-dimensional directions than those of a planar ring.

An apparent crossing of arcs may be implemented in three ways:

- spatial separation as an overpass and underpass;
- a smooth connection forming part of one continuous route;
- an electromagnetically controlled junction selecting one of several closed subroutes.

The controller selects a suitable outer or inner arc and accelerates, brakes, or reverses the sphere near it. This creates a short reaction in the required direction and a moment about the center of the device. Several nearby actions may be combined to obtain the required angle more precisely. The actual force-and-torque workspace is refined through self-calibration rather than geometric calculation alone.

### Central four-channel node

In one embodiment, the central region of the sphere contains four isolated tubular channels passing near the center of the structure at different spatial angles. Their directions may approximately follow vectors from the center toward the vertices of a tetrahedron, thereby covering three-dimensional space relatively uniformly.

The channels should not open into one common chamber if simultaneous passage of spheres is intended. They are implemented as a compact spatial bundle:

- each channel has its own continuous wall;
- channel axes are slightly offset from the exact geometric center;
- passages may be arranged at different levels;
- spheres pass through the central region simultaneously without contact;
- after the central node, the channels diverge toward the outer and inner arcs of the sphere.

Synchronous passage through the central node is used as a phase reference and for mutual cancellation of linear reactions. Because the force lever arm near the center of mass is small, strong turning moments are formed primarily on the outer arcs. If the central channels are curved or offset, the node itself can also generate a limited moment.

![Central four-channel node](../figures/central-four-channel-node.svg)

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

In a related embodiment, an internal pendulum, linear mass, flywheel, or suitable segment of the closed path is synchronized with a suspension, spring, leg, wheel, flexible support, or other compliant mechanism:

1. a user command enables the sequence;
2. sensors detect increasing compression;
3. the internal mass may increase preload;
4. near the transition from compression to extension, the mass is braked or reversed;
5. its reaction adds to the rebound of the compliant support;
6. subsequent recovery is shaped so that it does not cancel the useful impulse.

Maximum effectiveness is achieved immediately after the lowest point, while the external contact is still loaded, rather than after complete extension. The external support supplies the net impulse to the combined system. In free flight, internal motion can change relative motion of components and host orientation, but not the trajectory of the combined center of mass.

### Paired and counter-moving modules

One continuously circulating mass produces periodic reactions even when only one component is desired. Two or more mirrored modules may therefore be phase-synchronized. Their motion directions, speeds, and impulse timing are selected so that parasitic oscillations, torque ripple, and stored angular momentum cancel each other while the requested force or turning moment adds.

For example, two mirrored spheres move in opposite directions at the same baseline speed. Synchronous correction preserves cancellation, while differential acceleration or braking temporarily creates the required moment. The controller measures residual vibration and continuously adjusts phase and speed because manufacturing tolerances, load, and wear prevent reliance on ideal open-loop cancellation.

A single module is physically possible. A paired arrangement is useful for compensation in one selected plane, but by itself does not provide complete independent stabilization about all three axes.

### Four spheres and three-axis compensation

For spatial stabilization, the system must independently generate roll, pitch, and yaw moments. One embodiment contains four independently controlled spheres distributed along four non-coplanar directions within a shared spherical structure. Geometrically, these directions may approximate a tetrahedral arrangement.

In a symmetric mode, the impulses and angular momenta of the four elements are selected so that their vector sum is close to zero:

```text
H1 + H2 + H3 + H4 ≈ 0
```

During a maneuver, the controller temporarily breaks the symmetry. Some spheres accelerate or brake on selected arcs, while the others compensate unwanted components. The control system solves two coupled objectives:

```text
sum of unwanted forces ≈ 0
sum of moments = required host-body moment
```

Four independently controlled directions can cover three rotational axes, while the remaining control degree of freedom can be used to prevent collisions, restore sphere distribution, reduce vibration, or redistribute accumulated internal angular momentum.

Compensation is not calculated from equal traveled distances. Two spheres traversing equal path lengths may create different reactions because of differences in speed, acceleration, curvature, and lever arm. The controller matches measured changes in linear and angular momentum while accounting for local route geometry.

Four spheres are an example, not a mandatory count. Other configurations are possible: three independent loops without redundancy, four spatially separated modules, three counter-moving pairs, or another configuration whose control-action matrix spans all three axes. If simultaneous control of three linear-force components is also required, the system is treated as a six-dimensional force-and-torque actuator.

### Collision prevention and phase recovery

On one continuous one-way route, the ordering of spheres does not change. A strong impulse may temporarily reduce their separation but must not result in an actual overtake. The controller predicts relative motion and preserves a braking margin:

```text
free distance > relative-motion braking distance + safety clearance
```

After a rapid impulse, symmetry is restored with a weaker and more extended action, preferably on sections whose reactions mutually cancel. Counter-directional motion requires separate parallel or spatially separated channels. At junctions, the controller reserves a branch in advance and prevents simultaneous entry by conflicting spheres.

### Two redundant spherical modules

A large device may contain two full-axis spherical modules located in different parts of the load-bearing structure. In normal operation they share the load, mutually reduce residual vibration, and cross-check each other's response using a common IMU and local telemetry. Each module has a local controller, while a supervisory layer compares commanded and actual action.

If one module loses some coils, sensors, or channels, the healthy module enters a degraded backup mode. It estimates the residual force and torque of the failed unit and generates an opposing reaction, or independently assumes three-axis attitude control. For this purpose, each module must provide a full three-axis control range and sufficient force, torque, power, and thermal margin for temporary operation in place of both modules.

A spherical module does not necessarily need to be mechanically rotated toward the failed unit. Its action direction can be changed by programmatically selecting inner and outer arcs—effectively rotating the working coordinate system inside a stationary housing. An additional gimbal is permissible if the intrinsic directional range is insufficient, but it adds separate mechanical failure points.

The failed module is first placed in a safe state: its power stages are isolated, and free masses are braked or locked where possible. The healthy module can compensate center-of-mass shift, residual imbalance, and a limited parasitic moment, but it is not required to stabilize the device against unlimited spin-up or mechanical destruction of the second unit. Independent power isolation, passive sphere retention, mechanically robust channels, and a defined limit for compensable fault reaction are therefore provided.

Fault tolerance may operate at several levels:

- failure of one coil is compensated by neighboring sections of the same route;
- sensor failure is compensated by position estimation from other sensors and coil electrical parameters;
- failure of one sphere or channel redistributes the task among the remaining spheres in the module;
- failure of an entire module switches the second module into full-axis backup mode;
- when reserve capacity is insufficient, the system enters a minimum-vibration mode while maintaining a stable orientation as far as available authority permits.

## Self-calibration

For selected phases and current profiles, the system records:

- sphere phase, direction, and speed;
- current, voltage, pulse duration, and temperature;
- host-body acceleration and rotation;
- actual displacement and heading change;
- vibration and settling time;
- state of contact or compliant support;
- onset of sliding, actuator saturation, or obstacle constraint.

Small diagnostic impulses are applied first. If the IMU and relative-displacement sensor indicate that the host body remains stationary, the system gradually increases baseline speed or action amplitude until a reliably measurable response appears. The detected threshold is reduced slightly and stored as the operating starting point. The controller then separately estimates accelerating and braking effects, sliding threshold, support compliance, and settling time.

Dedicated sensors in the feet are not required. States such as "on a hard surface," "held in the hand," "on a soft support," "rolling," "sliding," or "blocked by an obstacle" may be estimated probabilistically from a combination of IMU data, optical displacement, sphere phase, and measured response to test impulses. The response map is continuously refined when load or environment changes.

After calibration, the controller composes the required motion, rotation, vibration, balancing action, or impulse from learned control primitives. For continued motion, a useful push may be combined with precomputed braking before the next active section when both reactions direct the host body toward the same desired direction.

## Localization and return

A surface-facing optical sensor measures short displacements, while the IMU measures rapid acceleration and rotation. A visual, infrared, magnetic, or radio marker, or a docking station, removes accumulated error and allows return to a stored position.

If the device is lifted and moved, IMU and optical odometry alone are insufficient; it must be re-referenced to an external landmark.

## Integration into a motor or machine

The actuator may be located inside the housing of a conventional electric motor, joint, wheel module, tool, household appliance, or sealed machine as an additional controlled degree of freedom. The main motor rotates a shaft, while the internal mass independently creates a balancing action, compensates vibration, generates haptic feedback, smooths transient torque, or provides diagnostic excitation.

The main motor and auxiliary actuator may share the housing and controller, but a separate winding or magnetic path is generally more practical for the auxiliary mass. A single winding is suitable only when the requirements for main torque and internal-mass motion are compatible in magnetic flux, heating, and commutation timing.

## Example applications

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

In a washing machine, centrifuge, or rotary tool, multiple masses can continuously measure imbalance and move so as to generate an opposing reaction. Unlike a passive ball balancer, the position and speed of the masses are actively commanded and corrected from measured vibration.


## Featured demonstrator embodiment: spherical mobile robot

A high-visibility, non-limiting prototype may place the spatial guideway inside a spherical mobile shell and add an optional magnetically coupled external head-like module for visual orientation and public demonstration. The resulting form factor can resemble familiar consumer spherical character robots, including the Sphero BB-8 toy, but the reference is only to the external demonstration format; the internal actuation method remains the distributed electromagnetic reaction-mass system disclosed here.

The spherical demonstrator may execute rolling locomotion, steering, rapid attitude correction, rocking, vibration, and impulse-assisted contact manoeuvres. Because selected guide arcs can produce reaction components with substantial vertical components, the controller may also schedule an upward ground-reaction impulse by accelerating, braking, or reversing a mover at an appropriate phase while the shell is in contact with the support. If the attainable momentum change, contact timing, traction, structural strength, and available stroke are sufficient, this may produce a short hop or assist traversal over a small obstacle.

The hop is a surface-coupled manoeuvre, not reactionless propulsion. The supporting surface supplies the external impulse to the complete device. During free flight, internal mass motion may alter attitude and redistribute angular momentum but cannot change the translational momentum of the isolated combined system.

The external head-like module is optional and may be retained by magnetic attraction or another low-friction coupling so that it remains visually upright while the main sphere rolls. It is not required for the core actuator and need not participate in force generation.

## Noise, impacts, and load transfer

A rolling steel sphere, guide joints, and rapid magnetic braking can generate audible structure-borne noise. It can be reduced by using a continuous smooth guide, avoiding abrupt joints, applying anticipatory magnetic braking, using compliant external mounts, and adding a local damping layer. The soft layer must not be so compliant that it substantially absorbs the useful impulse or disrupts coil-gap accuracy.

Reaction loads should be transmitted to the common rigid guide frame rather than to a decorative outer shell. In a large multi-channel system, the central node and outer arcs form part of the load-bearing structure of the host body.

## Distinctive combination

The principal disclosed combination includes:

1. One freely moving magnetic or ferromagnetic element in a shared closed guide.
2. Distributed electromagnetic acceleration and controlled braking.
3. Phase-selective generation of host-body reaction and torque.
4. Optional spatial or spherical interwoven geometry for additional action directions.
5. Experimental learning of the relationship between command and actual response.
6. Adaptation to load, friction, compliance, and external constraints.
7. Composition of a requested effect from learned control primitives.
8. Optional integration with navigation, a conventional motor, or an external compliant mechanism.
9. Optional mirrored pairing of modules to cancel parasitic reaction while retaining a commanded force or moment.
10. A scalable embodiment with multiple independently controlled spheres and full three-axis torque control.
11. A central spatial node with multiple isolated channels permitting simultaneous passage of masses without collision.
12. The option to combine two full-axis modules with mutual monitoring, control redistribution, and compensation of a bounded fault reaction.

Metal-ball accelerators, passive ball balancers, vibration-driven robots, flywheels, reaction masses, return-to-position systems, and jumping mechanisms are individually known. This disclosure records the stated combination of mechanics, sensing, commutation, and adaptive control.

## Physical limitations

The system does not create reactionless thrust. Sustained translational locomotion requires momentum exchange with a surface, liquid, gas, external field, expelled mass, tether, or another environment. In an isolated system, internal motion can create temporary reaction, vibration, and attitude change, but cannot translate the combined center of mass.

## Example prototype parameters

- host-body mass: approximately 5–7 kg;
- available base: approximately 295 × 205 mm;
- one bearing-steel sphere: approximately 40 mm diameter and 0.26 kg;
- closed-path length: approximately 0.75–0.85 m;
- sphere speed: approximately 1.0–1.5 m/s;
- independently switched elongated coils: approximately 10–12;
- microcontroller, power switches, sphere sensors, IMU, and optional optical sensor.

These numbers describe only one experimental prototype and do not limit the general principle.

## Purpose of publication

This document is intended as a clear, dated disclosure of the technical concept. A preliminary prior-art review is provided in `docs/prior-art.md` and is not a legal opinion on patentability. Public disclosure does not by itself create exclusive rights and may limit later patenting opportunities: depending on the jurisdiction and circumstances, disclosed information may become part of the prior art.


## Rights and publication status

Copyright © 2026 Philip Dik. All rights reserved. No open-source or open-content license is granted by this repository unless a later version explicitly states otherwise.
