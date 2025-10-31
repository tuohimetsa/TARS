[TARS](https://tuohimetsa.github.io/TARS/tars_solar_system.html) <- Click here

# TARS Solar System Visualization

This is an orbital mechanics simulation and a visualization of the TARS (Torqued Accelerator using Radiation from the Sun) concept, based on the paper "[Torqued Accelerator using Radiation from the Sun (TARS) for Interstellar Payloads](https://arxiv.org/abs/2507.17615)".

## Features

### Solar System Simulation
*   The simulation displays a simplified model of the solar system, including the Sun and the planets from Mercury to Neptune.
*   Planetary orbits are calculated based on Kepler's laws, with an option to enable N-body gravitational interactions between planets.

### TARS Spacecraft
*   The TARS spacecraft is simulated, with its spin accelerating due to solar radiation pressure.
*   The simulation models the physics of the TARS concept, including the forces on the sails and the resulting torque.

### Payload Launching
*   Users can launch payloads from the TARS spacecraft.
*   The launch direction can be controlled using a 3D vector or an interactive aim ball.
*   The trajectory of the payload is simulated under the gravitational influence of the Sun and other celestial bodies.

### Trajectory Preview
*   A trajectory preview line shows the expected path of the payload before launch.
*   The preview takes into account the gravitational forces of the Sun and planets.
*   Closest approach information to celestial bodies is displayed.

### Asteroid Simulation
*   The simulation includes a feature to spawn asteroids with customizable mass, radius, and intercept velocity.
*   Asteroids are spawned at random positions in the outer solar system and their trajectories are simulated.

## User Interface

The user interface consists of a heads-up display (HUD) with several tabs to control the simulation.

### HUD
The main HUD displays real-time data about the simulation, including:
*   Real and simulated time.
*   TARS spacecraft status (position, velocity, spin, etc.).
*   Payload information.

### Controls Tab
*   **Time Controls:** Start, pause, and stop the simulation. Control the simulation speed.
*   **Focus Control:** Select which object the camera should follow (TARS, Sun, planets, or payloads).
*   **View Controls:** Toggle the visibility of orbits, starfield, labels, and trails.

### Physics Tab
*   Adjust the physical parameters of the simulation, such as:
    *   Gravitational constant (`muSun`).
    *   TARS sail area, lever arm, and reflectivity.
    *   Payload mass and tether properties.
    *   Enable or disable N-body gravitational interactions.

### Graphics Tab
*   Control the graphical settings of the simulation, such as:
    *   Sun and ambient light intensity.
    *   Star size and orbit opacity.
    *   Background color.
    *   Toggle true-to-scale planet sizes.

### Payload Tab
*   **Launch Controls:** Launch a payload from the TARS spacecraft.
*   **Aiming Controls:**
    *   Set the launch direction using a 3D vector.
    *   Use the Azimuth and Elevation inputs to aim.
    *   An interactive 2D aim ball to visually select the launch direction.
*   **Trajectory Preview:** Enable and configure the trajectory preview.

### Targets Tab
*   **Asteroid Controls:**
    *   Set the mass, radius, and intercept velocity of asteroids.
    *   Spawn new asteroids into the simulation.
*   **Impact Pulse:** Displays the calculated impact pulse of the asteroid.

## Disclaimer

This is a work in progress. The simulation is not yet a complete or fully accurate representation. The physics modeling is currently under construction.