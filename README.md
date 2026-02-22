[TARS Solar System Simulation](https://tuohimetsa.github.io/TARS/tars_solar_system.html) — *Click to run*

# TARS Solar System Visualization

Orbital mechanics simulation and 3D visualization of the **TARS** (Torqued Accelerator using Radiation from the Sun) concept from:

**Kipping, D. & Lampo, K.** *Torqued Accelerator using Radiation from the Sun (TARS) for Interstellar Payloads.* [arXiv:2507.17615](https://arxiv.org/abs/2507.17615) (2025).

TARS spins up by solar radiation pressure on two surfaces with different reflectivities (α reflective, β absorbing), then releases a payload at high tangential speed. The simulation includes the Sun and planets, TARS spin-up and payload release, and optional asteroids.

---

## Running the project

Serve the project over HTTP (required for ES modules):

```bash
cd /path/to/TARS
python3 -m http.server
```

Then open [http://localhost:8000/tars_solar_system.html](http://localhost:8000/tars_solar_system.html) in a browser.

---

## Physics formulations and references

All references are to the paper above (arXiv:2507.17615). The simulation uses a **single disc** with one half α (reflective/white) and one half β (absorbing/black); the paper describes **two paddles** with α on one side and β on the other. Symbol mapping: **S** = solar irradiance, **θ** = spin phase (paper phase angle), **R_α**, **R_β** = reflectivities, **F_R** = net torque force, **δ** = lever arm, **I** = moment of inertia.

### Orbital dynamics

- **Gravity:** Newtonian point-mass gravity. Sun–planet orbits use Keplerian two-body (Velocity–Verlet). TARS, payloads, and asteroids use **n-body** acceleration from the Sun plus optional planetary perturbations.
- **Units:** Distances in AU, time in years; μ⊙ chosen so that 1 AU, 1 year satisfies Kepler’s third law (μ⊙ = 4π² AU³/yr²).

### Solar irradiance (flux)

Incident power per unit area at heliocentric distance *r*:

| **S** = **L⊙** / (4π *r*²) |

- **L⊙** = 3.828×10²⁶ W (solar luminosity). Same as paper’s flux definition leading to Eq. (1).

### Sail forces and net torque force

In the **zero-transmission limit** (opaque paddle), the normal radiation force on each surface (paper Eq. 6, thermal terms omitted here) is:

| **F**⊥,**α** = (*A*/*c*)(1 + **R**α)**S** cos²**θ** |  
| **F**⊥,**β** = (*A*/*c*)(1 + **R**β)**S** cos²**θ** |

- *A* = paddle area (one face), *c* = speed of light, **θ** = phase angle (disc tilt to Sun).  
- Net torque-producing force (paper Eq. 7):

| **F**_R_ = **F**⊥,**α** − **F**⊥,**β** |

The simulation uses **|cos θ|** to modulate force by face tilt; **θ** is the spin phase.

### Torque and spin-up

Torque **τ** = **F**_R_ × **δ**, with **δ** the lever arm. For a **semicircle**, the centre of pressure lies at distance **4*R*/(3π)** from the disc centre (paper Eq. 11 uses **δ**; here **δ** = 4*R*/(3π) with *R* = disc radius):

| **τ** = **F**_R_ · **δ**  ,  **δ** = 4*R*/(3π) |

Angular acceleration (paper Eq. 11):

| **ω̇** = **τ** / *I* |

*I* is a simplified moment of inertia (point masses at radius *R*). Spin **ω** is integrated in time; **θ** advances as **ω** *t* for the sail view and torque modulation.

### Structural failure (tether)

The paper (Section 9) treats a **uniform ribbon**: tension at midpoint, **v**_crit_ = √(2**σ**/**ρ**). This simulation uses a **tether + payload** model instead:

- Centripetal force on payload: *F* = *m* **ω**² *R*.
- Tether tensile stress: **σ**_tether_ = *F* / (cross-sectional area).
- If **σ**_tether_ > **σ** (tensile strength), the structure “fails” and the payload is released.

So the formulation is **tether tensile limit** rather than the paper’s ribbon **v**_crit_.

### Payload release

At release, the payload gets a tangential velocity **v** = **ω** *R* (plus the craft’s orbital velocity). It then propagates under gravity only (n-body from Sun and optional planets). No ongoing thrust or sail on the payload.

### Simplifications vs paper

- **No transmission** *T*∠(**θ**): paddles taken as opaque.  
- **No thermal asymmetry** *Q*α: no thermal re-emission terms (paper Eq. 6).  
- **Geometry:** One disc, half α / half β, instead of two paddles.  
- **Failure criterion:** Tether tensile stress vs **σ**, not ribbon midpoint tension and **v**_crit_ = √(2**σ**/**ρ**).

---

## Disclaimer

This is a work in progress. The simulation is not a complete or certified representation of the paper’s model. Physics and numerics may be refined over time. Largely built with AI assistance.
