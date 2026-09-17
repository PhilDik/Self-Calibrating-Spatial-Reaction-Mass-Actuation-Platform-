# Preliminary prior-art context

**Search date:** 2026-09-17  
**Status:** non-exhaustive preliminary search; not a legal patentability opinion.

## Closest identified categories

1. **Electromagnetic steel-ball accelerators and magnetic-ball positioning.** Sequentially energized electromagnets are known for accelerating or positioning ferromagnetic or magnetic spheres in a guide. A recent laboratory example is Liu et al., [“Two-dimensional point suspension characteristics of a magnetic robot driven by dual electromagnets within a fluid pipe,” *Mechanical Sciences* 17 (2026)](https://ms.copernicus.org/articles/17/825/2026/ms-17-825-2026.html), which uses electromagnets, camera localization, and Hall sensing to control a magnetic ball inside a pipe. That work addresses magnetic positioning/suspension in a fluid pipe rather than use of the ball as a reaction mass for controlled host-body force and torque. An informal example of sequential acceleration is the [six-coil electromagnetic ball accelerator](https://www.youtube.com/watch?v=R1Dlyg4FFZM).

2. **Fluid-actuated spherical robots with moving masses in circular pipes.** Tafrishi et al., [“Design, Modeling and Motion Analysis of a Novel Fluid Actuated Spherical Rolling Robot,” *Journal of Mechanisms and Robotics* 11(4), 2019, DOI 10.1115/1.4043689](https://doi.org/10.1115/1.4043689), describe spherical moving masses propelled through internal circular fluid-filled pipes to roll a spherical shell. A follow-up study, [“Inverse Dynamics-Based Motion Control of a Fluid-Actuated Rolling Robot”](https://doi.org/10.20537/nd190420), treats motion planning for a spherical mass in a circular pipe fixed to the shell. [CN110979500A](https://patents.google.com/patent/CN110979500A/en) similarly describes a fluid-driven spherical rolling robot with spherical center-of-gravity-adjusting blocks in an annular pipe. These references are close in the use of guided internal spherical masses, but they rely on fluid actuation and center-of-gravity displacement in circular/semi-annular paths rather than a free electromagnetic mover in a distributed, phase-commutated spatial guide used as a programmable reaction-mass actuator.

3. **Closed-path inertial systems.** [WO2018002555A1](https://patents.google.com/patent/WO2018002555A1/en) describes a mass circulating in a closed-cycle guide, controlled braking, electromagnetic motorization as an option, and circular or elliptical embodiments.

4. **Variable-radius rotating masses.** [US20080168862A1](https://patents.google.com/patent/US20080168862A1/en) describes masses connected to telescoping arms and guided along a closed path.

5. **Vibration-induced device movement.** [US9479698B2](https://patents.google.com/patent/US9479698B2/en) describes using an internal vibration motor to rotate an electronic device on a smooth surface.

6. **Impulse torque from internal flywheel braking.** [US10857670](https://patents.google.com/patent/US10857670/en) describes rapid flywheel deceleration producing torque impulses for robotic movement and reconfiguration.

7. **Friction-driven mobile robots.** Experimental vibration-driven robots use eccentric internal rotors, anisotropic friction, wheels, bristles, or clutches. A representative study is [Korendiy and Kachur, Frontiers in Robotics and AI, 2023](https://www.frontiersin.org/journals/robotics-and-ai/articles/10.3389/frobt.2023.1239137/full).

8. **Closed-loop omnidirectional friction control.** [Locomotion and Control of a Friction-Driven Tripedal Robot](https://arxiv.org/html/2011.07370v2) demonstrates model-based multidirectional surface locomotion with feedback, but uses three driven limbs rather than a circulating ball.

9. **Jumping and self-righting by internal momentum exchange.** [The Wheelbot](https://arxiv.org/abs/2207.06988) uses reaction wheels for self-erection, jumping onto its wheels, balancing, and disturbance rejection. Such systems support the general feasibility of timed internal-momentum exchange but do not use the disclosed free mover, closed guide, distributed linear-motor commutation, and learned phase-response map.

10. **Passive ball balancing.** Free balls in annular races are known for passive balancing of rotating machinery. The disclosed actuator differs by actively sensing and electromagnetically commanding the mover to generate selected reactions rather than allowing it to settle passively.

## Terminology used in this disclosure

The literature supports using established terms such as **reaction mass**, **reaction-mass actuator**, **moving mass**, **closed guide / closed-loop guideway**, **distributed electromagnetic actuation**, **phase-selective actuation**, **force/torque map**, and **system identification**. Their use here is descriptive and does not imply that the present architecture is identical to any cited reference.

## Combination not identified in this preliminary search

The search did not identify one reference containing the complete combination of:

- a free rolling ferromagnetic sphere used as an internal inertial mass;
- a closed guide path fixed inside the host body, optionally non-planar or spatially interwoven;
- multiple independently switched coils distributed around the path;
- phase-selective acceleration and braking used to generate translation and rotation of the containing body;
- optional complementary vertical path components used to modulate surface normal force;
- automatic empirical learning of a phase-to-body-motion response map;
- composition of learned impulse primitives for commanded locomotion and return to a stored pose.

Related embodiments additionally coordinate a controlled internal mass with an external compliant mechanism, integrate the actuator into another motor, or use mirrored counter-moving modules to cancel unwanted vibration while retaining a commanded force or moment. These extensions should be assessed separately from the core closed-path single-mover combination.

Patentability cannot be inferred solely from the absence of an identical result. An examiner may combine multiple references when evaluating inventive step or obviousness.
