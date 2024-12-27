---
title: "Cold Spray Toolbox: World's First Open-Source CAD-to-Product Solution for Cold Spray Additive Manufacturing"
excerpt: "The Complete Cold Spray Toolbox Software is the world's first open-source toolbox designed specifically for Cold Spray Additive Manufacturing (CSAM). It provides a comprehensive solution featuring a user-friendly GUI and various tabs for CAD manipulation, slicing, simulation, and robot tool path generation. <br/><img src='/images/CS_toolbox_software.png'>"
collection: portfolio
---

# Complete Cold Spray Toolbox Software

The **Complete Cold Spray Toolbox Software** is the world's first open-source toolbox designed specifically for **Cold Spray Additive Manufacturing (CSAM)**. It streamlines the entire process—encompassing CAD manipulation, slicing, simulation, and robot tool path generation—into one cohesive platform. By operating at temperatures significantly below the melting point of deposited materials, cold spray avoids many common problems (e.g., oxidation, thermal distortion) often encountered in high-heat additive methods like Laser Metal Deposition (LMD) or Selective Laser Melting (SLM).

---

## What is Cold Spray?

![cold-spray-process-explanation]({{ site.baseurl }}/images/cold-spray-process-explanation.jpg)
<figcaption>Conceptual illustration of the cold spray process.</figcaption>

**Cold Spray** is an innovative additive manufacturing technique developed in the 1980s at the Russian Academy of Sciences. In this process, high-pressure gases (e.g., helium or nitrogen) accelerate micron-sized particles (1–100 µm) through a converging-diverging nozzle at supersonic speeds (300 to 1,200 m/s). Because these particles impact the substrate at high velocity but relatively low temperature (below their melting point), the resulting bonding mechanism is primarily **mechanical interlocking** and **localized metallurgical bonding** due to intense plastic deformation.

This **low-temperature approach** substantially reduces issues like:
- **Oxidation**: Minimal oxide formation compared to high-heat processes.
- **Thermal Stresses**: Reduced or negligible residual stresses since the material never approaches its melt temperature.
- **Microstructural Degradation**: Grain coarsening, phase changes, and decomposition are significantly mitigated.

---

## Key Modules

### 1. CAD Manipulation

**Conceptual Overview**  
![cad-manipulation-concept]({{ site.baseurl }}/images/cad-manipulation-concept.jpg)
<figcaption>High-level illustration of importing and setting up CAD models for Cold Spray AM.</figcaption>

**Software GUI**  
![cad-manipulation-gui]({{ site.baseurl }}/images/cad-manipulation-gui.jpg)
<figcaption>Screenshot of the toolbox GUI during CAD manipulation.</figcaption>

In the **CAD Manipulation** module, users can import native CAD files or 3D scans, select relevant geometries, and assign material properties for cold spray. This ensures precise boundary definitions and alignment for subsequent steps. Users can choose from a variety of powder specifications, substrate references, and parameter templates tailored for different part geometries.

---

### 2. Slicing

**Conceptual Overview**  
![slicing-module-concept]({{ site.baseurl }}/images/slicing-module-concept.jpg)
<figcaption>Layer-by-layer overview of slicing for Cold Spray Additive Manufacturing.</figcaption>

**Software GUI**  
![slicing-module-gui]({{ site.baseurl }}/images/slicing-module-gui.jpg)
<figcaption>A look at the slicing interface, highlighting adjustable layer thickness and fill patterns.</figcaption>

The **Slicing** module allows layer-by-layer preparation of the CAD model for cold spray deposition. Key features include:

- **Material Library**: Choose from a wide range of metals/alloys, each with suggested velocity and temperature ranges.  
- **Fill Patterns**: Configure raster, spiral, or custom fill paths based on part geometry.  
- **Layer Control**: Define layer thickness, overlap, and step distance to optimize mechanical properties, dimensional accuracy, and build time.

---

### 3. Simulation

Before delving into the simulation interface, we present a **mathematical framework** that underpins our cold spray deposition model.

#### Final Deposition Model

By substituting Equations (7) and (8) into Equation (6), we obtain the **material deposition model**:

\[
\frac{\partial |(P_s) \vec{}|}{\partial t}
=
\frac{1}{\rho \cdot h}
\cdot
\frac{ \dot{m}_n }{ \Delta S ( \vec{n}_s \cdot \vec{n}_p ) }
\cdot
\frac{1}{2\pi \sigma_p^2 }
\exp \left[
 -\frac{1}{2}
 \left(\frac{r_n}{\sigma_p}\right)^2
\right]
\tag{14}
\]

For increased accuracy, the projected discretized surface area \(\Delta S\) must be adjusted to account for the angle of incidence \(\theta\), described as:

\[
\Delta S^* = \cos(\theta) \, \Delta S
\]

Furthermore, the **scalar deposition** (\(P_s\)) can be expressed in terms of the partial derivative of the vector magnitude:

\[
\frac{\partial P_s}{\partial t}
=
\frac{\partial |(P_s) \vec{}|}{\partial t}
\,
(\vec{n}_p)
\tag{15}
\]

Below is a conceptual **visualization of the deposition process** (Figure 21) based on the above equations:

![deposition-process-diagram]({{ site.baseurl }}/images/deposition-process-diagram.jpg)
<figcaption>Figure 21: Visualization of how particles accumulate on the substrate as described by Equations (14) and (15).</figcaption>

---

**Simulation Interface**  
![simulation-gui]({{ site.baseurl }}/images/simulation-gui.jpg)
<figcaption>A real-time simulation of layer growth and particle trajectories in the toolbox.</figcaption>

With **up to 90% accuracy** relative to experimental data, the Simulation module:

- **Predicts Deposit Thickness**: Continuously updates build height maps based on user-defined parameters.  
- **Analyzes Particle Velocities**: Evaluates the effect of gas pressure, nozzle diameter, and stand-off distance.  
- **Optimizes Parameters**: Allows iterative tuning of spray angles, traverse speed, and feed rate to reduce trial-and-error in actual builds.

---

### 4. Robot Tool Path Generation

**Conceptual Overview**  
![robot-toolpath-concept]({{ site.baseurl }}/images/robot-toolpath-concept.jpg)
<figcaption>Conceptual overview of offline programming for robotic cold spray.</figcaption>

**Digital Twin Environment**  
![robot-toolpath-digital-twin]({{ site.baseurl }}/images/robot-toolpath-digital-twin.jpg)
<figcaption>Simulation showing a robotic arm following a predefined toolpath in a digital twin environment.</figcaption>

The **Robot Tool Path Generation** module automatically calculates collision-free trajectories for your chosen robot (e.g., ABB, Fanuc, KUKA). Key advantages include:

- **Offline Programming**: Visualize nozzle angles, standoff distances, and motion sequences in a virtual environment before physical setup.  
- **Collision Detection**: Identify potential clearance issues and refine path planning to avoid expensive hardware damage.  
- **Integrated Export**: Seamlessly convert simulation outputs to robot-native instructions, accelerating transition to real-world deposition.

---

## Results

In this section, we showcase **real-world outcomes** from using the Cold Spray Toolbox, highlighting consistency between simulated and actual builds.

### 1. CAD Model vs. Final Printed Part

![cad-to-printed-part]({{ site.baseurl }}/images/cad-to-printed-part.jpg)
<figcaption>A comparison of the initial CAD model and the final cold-sprayed component.</figcaption>

- **Observation**: Layer thickness, part contours, and overall dimensional accuracy show strong correlation with the simulated build.

### 2. Wrench Example

![wrench-cad]({{ site.baseurl }}/images/wrench-cad.jpg)
<figcaption>CAD model of a specialized wrench designed for cold spray AM.</figcaption>

![wrench-printed-machined]({{ site.baseurl }}/images/wrench-printed-machined.jpg)
<figcaption>Finished cold-sprayed wrench after minimal post-process machining.</figcaption>

- **Highlights**: Demonstrates the flexibility of cold spray for complex geometries and the final part’s uniform material properties. Machining requirements were minimal, confirming near-net shape capability.

---

## Conclusion

The **Complete Cold Spray Toolbox Software** delivers a **holistic solution** for **Cold Spray Additive Manufacturing**—from CAD imports and slicing to advanced numerical simulations and robot tool path generation. By leveraging **low-temperature deposition**, the process preserves critical material properties and ensures robust mechanical interlocking without the common drawbacks of high-heat additive methods.

---

## References

- [1] **Your Thesis Link Here** – For an in-depth understanding of the governing equations, experimental validations, and advanced cold spray methodologies, please refer to the author’s thesis.
- [2] **Additional Reference (If Needed)**

---

