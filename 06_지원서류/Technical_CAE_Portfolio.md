# TECHNICAL ENGINEERING DOSSIER & CAE PORTFOLIO
## Advanced Structural Dynamics, Spindle-Bearing Coupled Systems, and Regenerative Chatter Analysis in Machine Tools

**Applicant**: Youngseok Cho  
**Field**: Mechanical Engineering / Structural Dynamics & Precision Engineering  
**Experience Level**: ~4 Years Industrial CAE Simulation & Experimental Dynamic Correlation  
**Target Program**: Master of Engineering (April 2028 Intake)

---

> ### **CONFIDENTIALITY & IP COMPLIANCE STATEMENT**
> To protect proprietary commercial intellectual property, exact 3D casting geometries, specific machine-tool product model numbers, and sensitive commercial project identifiers have been sanitized, generalized, and normalized. All governing differential equations, mechanical equilibrium formulations, finite element discretization techniques, numerical algorithms, and scientific findings presented herein reflect the author's original engineering execution and rigorous physical principles.

---

# TABLE OF CONTENTS
1. [Executive Technical Overview](#1-executive-technical-overview)
2. [Case Study 1: Coupled Spindle-Bearing-Housing Dynamic Compliance & FRF Correlation](#2-case-study-1-coupled-spindle-bearing-housing-dynamic-compliance--frf-correlation)
3. [Case Study 2: High-Speed Bearing Nonlinear Stiffness Modeling Under Preload & Centrifugal Loads](#3-case-study-2-high-speed-bearing-nonlinear-stiffness-modeling-under-preload--centrifugal-loads)
4. [Case Study 3: Machine Tool Column Dynamic Compliance Minimization & Regenerative Chatter Mitigation](#4-case-study-3-machine-tool-column-dynamic-compliance-minimization--regenerative-chatter-mitigation)
5. [Case Study 4: In-Situ Joint Parameter Identification & Physics-Informed Model Updating](#5-case-study-4-in-situ-joint-parameter-identification--physics-informed-model-updating)
6. [Experimental Instrumentation & Numerical Computing Arsenal](#6-experimental-instrumentation--numerical-computing-arsenal)
7. [Alignment with Graduate Research in Japan](#7-alignment-with-graduate-research-in-japan)

---

## 1. EXECUTIVE TECHNICAL OVERVIEW

During approximately four years of industrial CAE and experimental dynamics practice, my primary engineering focus has centered on **machine-tool structural dynamics and machining stability**. The core physical challenge in modern high-speed milling is that structural dynamic compliance at the cutting point directly dictates maximum material removal rates (MRR), workpiece surface finish, and tool life.

### Core Engineering Competencies Demonstrated in this Dossier:
- **Coupled Multiphysics Modeling**: Formulating rotor-bearing-housing systems accounting for gyroscopic moments, centrifugal ball loading, and nonlinear Hertzian contact.
- **Substructuring & Dynamic Reduction**: Implementing Craig-Bampton substructuring to couple massive machine casting frames (tons) with micro-scale spindle bearing deflection (microns).
- **Experimental Modal Analysis (EMA)**: Performing multi-point impact hammer and shaker modal testing to extract natural frequencies, mode shapes, and modal damping ratios ($\zeta_r$).
- **Machining Dynamics & Stability**: Formulating 2-DOF and multi-mode regenerative chatter algorithms in Python/MATLAB, synthesizing tool-tip Frequency Response Functions (FRFs) to generate analytical Stability Lobe Diagrams (SLDs).

```
   [ Machine Tool Column & Bed (FEA Substructure) ]
                          ▲
                          │ Nonlinear Joint Boundary (LM Blocks / Bolted Joints)
                          ▼
   [ Spindle Housing & Motor Sleeve (Timoshenko/3D) ]
                          ▲
                          │ 5-DOF Jones-Harris Bearing Stiffness Matrix [K_b(ω, F_p)]
                          ▼
   [ Rotating Spindle Shaft (Timoshenko Beam / Gyroscopic Rotor Dynamics) ]
                          ▲
                          │ Tool-Holder Clamping Interface
                          ▼
   [ Cutting Tool Tip (FRF / Dynamic Compliance H(ω) = x/F) ] ──► [ Altintas-Budak SLD ]
```

### Summary Matrix of Industrial Case Studies

| Case Study | Physical Challenge | Governing Formulations & CAE Method | Experimental Correlation Method | Validated Quantitative Result |
|---|---|---|---|---|
| **Case 1: Spindle-Bearing-Housing Dynamic Compliance** | High-speed tool-point FRF errors ($>25\%$) due to rigid base assumptions | Craig-Bampton CMS substructuring + Timoshenko rotor dynamics ($\Omega \mathbf{G}_r$) | In-situ modal impact hammer testing (PCB hammer/accelerometers) | Natural frequency prediction error $<2.9\%$; compliance peak within $8.5\%$ |
| **Case 2: High-Speed Bearing Nonlinear Stiffness** | Thermal-centrifugal ball unloading causing 34% drop in radial stiffness at 20,000 RPM | 5-DOF Jones-Harris kinematic equilibrium + Newton-Raphson nonlinear solver | Tachometer speed sweep + temperature sensor correlation | Identified contact angle migration ($\alpha_i: 15^\circ \to 21.4^\circ$); optimized variable preload |
| **Case 3: Column Compliance & Regenerative Chatter** | Severe face-milling chatter at $a_p \ge 2.2\text{ mm}$ ($f_c = 142\text{ Hz}$) | Altintas-Budak ZOA stability formulation + Den Hartog TMD tuning formula | Multi-channel microphone / accelerometer cutting chatter trials | Reduced column compliance by $39.4\%$; expanded stable depth of cut by **182%** ($1.7 \to 4.8\text{ mm}$) |
| **Case 4: In-Situ LM Guideway Joint Identification** | Unmodeled micro-slip damping & contact compliance in CAD-based digital twins | Nonlinear parameter optimization ($\min \mathcal{J}$) + Python-ANSYS APDL batch | Multi-point EMA modal test (6 structural modes) | Average MAC increased $0.78 \to 0.96$; frequency discrepancies reduced from $12.4\%$ to $<2.1\%$ |

---

## 2. CASE STUDY 1: COUPLED SPINDLE-BEARING-HOUSING DYNAMIC COMPLIANCE & FRF CORRELATION

### 2.1 Problem Definition
In high-speed vertical machining centers (spindle speeds up to 24,000 RPM), high dynamic compliance at the tool point frequently triggers violent self-excited chatter vibrations during end-milling of titanium and hardened steel. Conventional FEA often treats bearing supports as simple isotropic constant linear springs grounded to a rigid base. This assumption causes large errors ($>25\%$) in natural frequency predictions and completely fails to capture the coupling between spindle modes and structural column modes.

### 2.2 Mathematical Formulation & Governing Equations

#### A. Rotor Dynamics with Gyroscopic Coupling
The rotating spindle shaft is governed by the discretized rotor dynamics equation in the fixed coordinate system:
$$M_r \ddot{\mathbf{q}} + \left( C_r + \Omega G_r \right) \dot{\mathbf{q}} + K_r \mathbf{q} = \mathbf{F}_{ext}(t)$$
where:
- $M_r \in \mathbb{R}^{n \times n}$: Symmetric mass matrix (including translational and rotary inertia),
- $C_r \in \mathbb{R}^{n \times n}$: Structural and internal viscous damping matrix,
- $G_r \in \mathbb{R}^{n \times n}$: Skew-symmetric gyroscopic matrix ($G_r = -G_r^T$), proportional to rotational speed $\Omega$,
- $K_r \in \mathbb{R}^{n \times n}$: Shaft elastic bending and shear stiffness matrix (Timoshenko beam elements),
- $\mathbf{q} = [u, v, w, \theta_x, \theta_y, \theta_z]^T$: Generalized displacement vector.

#### B. Component Mode Synthesis (Craig-Bampton Reduction)
Because modeling the full machine tool frame with millions of solid elements simultaneously with the rotor in harmonic analysis is computationally prohibitive, the stationary housing and column structure is partitioned into boundary degrees of freedom ($\mathbf{q}_b$) and interior degrees of freedom ($\mathbf{q}_i$):
$$\begin{bmatrix} M_{bb} & M_{bi} \\ M_{ib} & M_{ii} \end{bmatrix} \begin{bmatrix} \ddot{\mathbf{q}}_b \\ \ddot{\mathbf{q}}_i \end{bmatrix} + \begin{bmatrix} K_{bb} & K_{bi} \\ K_{ib} & K_{ii} \end{bmatrix} \begin{bmatrix} \mathbf{q}_b \\ \mathbf{q}_i \end{bmatrix} = \begin{bmatrix} \mathbf{f}_b \\ \mathbf{0} \end{bmatrix}$$

The interior DOFs are transformed into a reduced set of Craig-Bampton normal modes:
$$\mathbf{q} = \begin{bmatrix} \mathbf{q}_b \\ \mathbf{q}_i \end{bmatrix} = \begin{bmatrix} \mathbf{I} & \mathbf{0} \\ \boldsymbol{\Psi}_c & \boldsymbol{\Phi}_k \end{bmatrix} \begin{bmatrix} \mathbf{q}_b \\ \boldsymbol{\eta}_k \end{bmatrix} = \mathbf{T}_{CB} \mathbf{p}$$
where $\boldsymbol{\Psi}_c = -K_{ii}^{-1} K_{ib}$ represents static constraint modes, and $\boldsymbol{\Phi}_k$ denotes the first $k$ fixed-interface normal modes ($\left( K_{ii} - \omega^2 M_{ii} \right) \boldsymbol{\phi} = \mathbf{0}$).

### 2.3 Finite Element & Boundary Implementation
1. **Shaft Modeling**: The spindle shaft was discretized using 3D Timoshenko beam elements (shear deformation included) with accurate mass stations representing tool-holder taper (BT40/HSK-A63), motor rotor sleeves, and bearing inner rings.
2. **Housing & Bearings**: Front tandem angular contact ball bearings and rear pair were represented by customized $6 \times 6$ coupled stiffness matrices ($K_{ij}$).
3. **Harmonic Response Simulation**: Swept-frequency harmonic force excitation ($F_x = 1.0\text{ N}, 0 \text{ to } 3,000\text{ Hz}$) was applied at the tool tip to compute the direct Frequency Response Function:
$$H_{xx}(\omega) = \frac{X(\omega)}{F_x(\omega)}$$

### 2.4 Experimental Validation & Test-Model Correlation
- **Experimental Setup**: A calibrated modal impact hammer (PCB 086C03 with vinyl and aluminum tips) was used to excite the tool tip. A triaxial miniature accelerometer (PCB 356A15, mass 4.0 g) measured acceleration. Signals were acquired via an OROS multi-channel FFT analyzer with Hanning/exponential windowing to avoid leakage.
- **Correlation Results**:
  - **Mode 1 (Overhang Bending Mode)**: Predicted: $748\text{ Hz}$ | Measured: $762\text{ Hz}$ (Error: **1.8%**).
  - **Mode 2 (Spindle-Housing Rocking Mode)**: Predicted: $1,180\text{ Hz}$ | Measured: $1,215\text{ Hz}$ (Error: **2.9%**).
  - **Peak Compliance Peak Value**: Within $8.5\%$ of physical test magnitude across $0–2,000\text{ Hz}$.

```
Direct FRF at Tool Tip H_xx (Compliance: m/N)
10^-5 |           FEA Coupled Model:  ───
      |           Impact Hammer Test: ···
10^-6 |                 /\                  /\
      |                /  \                /  \
10^-7 |       /\      /    \              /    \
      |      /  \    /      \            /      \
10^-8 |_____/____\__/________\__________/________\_____
      0          500         1000        1500     2000 (Hz)
                  Mode 1: 762 Hz     Mode 2: 1215 Hz
```

---

## 3. CASE STUDY 2: HIGH-SPEED BEARING NONLINEAR STIFFNESS MODELING UNDER PRELOAD & CENTRIFUGAL LOADS

### 3.1 Problem Definition
At high rotational speeds (e.g., $d_m \cdot N > 1.2 \times 10^6\text{ mm}\cdot\text{RPM}$), centrifugal forces ($F_c$) and gyroscopic moments ($M_g$) acting on the bearing balls induce significant changes in inner and outer ring contact angles ($\alpha_i, \alpha_o$). If the initial axial preload is improperly selected:
- Rigid preload: Excessive thermal expansion induces thermal runaway and bearing seizure.
- Constant spring preload: Centrifugal unloading causes inner-ring ball slip, skewing, and a dramatic drop in spindle radial stiffness.

### 3.2 Mathematical Formulation (Jones-Harris 5-DOF Bearing Kinematics)

For each rolling element (ball $j$, $j=1,\dots,Z$), the centrifugal force $F_{c,j}$ and gyroscopic moment $M_{g,j}$ are:
$$F_{c,j} = \frac{1}{2} m_b d_m \omega_c^2, \quad M_{g,j} = J_b \omega_b \omega_c \sin(\beta)$$
where $m_b$ is ball mass, $d_m$ is bearing pitch diameter, $\omega_c$ is cage orbital velocity, and $J_b$ is ball polar moment of inertia.

The equilibrium equations at each ball contact point satisfy Hertzian contact elasticity ($Q = K_h \delta^{3/2}$):
$$Q_{oj} \cos \alpha_{oj} - Q_{ij} \cos \alpha_{ij} - F_{c,j} = 0$$
$$Q_{oj} \sin \alpha_{oj} - Q_{ij} \sin \alpha_{ij} = 0$$

```
        Outer Ring (Fixed)
           / \
      Q_o /   \ α_o
         /     \
       ( Ball m_b ) ──► F_c (Centrifugal Force)
         \     /
      Q_i \   / α_i
           \ /
        Inner Ring (Rotating with Shaft)
```

The global bearing stiffness matrix is obtained from the Jacobian of the internal equilibrium equations with respect to the 5-DOF relative displacement vector $\mathbf{u} = [\delta_x, \delta_y, \delta_z, \theta_y, \theta_z]^T$:
$$\mathbf{K}_b = \frac{\partial \mathbf{F}_b}{\partial \mathbf{u}} = \sum_{j=1}^Z \left[ \mathbf{T}_j^T \mathbf{K}_{ij} \mathbf{T}_j \right]$$

### 3.3 Computational Algorithm & Implementation
- An iterative **Newton-Raphson nonlinear solver** was coded in Python (NumPy/SciPy).
- The algorithm solved for the contact deformation $\delta_{ij}, \delta_{oj}$ and contact angles $\alpha_{ij}, \alpha_{oj}$ at every azimuth angle $\theta_j$ under combined axial preload ($F_a$), radial cutting load ($F_r$), and speed $\Omega$.
- The resulting speed-dependent stiffness curves ($K_{xx}(\Omega), K_{zz}(\Omega)$) were automatically exported into parametric ANSYS APDL scripts as nonlinear matrix elements (`MATRIX27` / `CBUSH`).

### 3.4 Key Technical Finding
Under fixed-spring preload, as spindle speed escalated from $0$ to $20,000\text{ RPM}$:
- Inner contact angle $\alpha_i$ increased from $15.0^\circ$ to $21.4^\circ$.
- Outer contact angle $\alpha_o$ decreased from $15.0^\circ$ to $9.8^\circ$.
- **Radial dynamic stiffness decreased by 34.2%**, leading to a noticeable forward shift in the spindle's first critical speed and lowering the chatter stability limit.
- **Engineering Solution**: Optimized the pre-load spring rate and introduced a variable hydraulic preload mechanism that switches between "high preload" during low-speed roughing and "low preload" during high-speed finishing.

---

## 4. CASE STUDY 3: MACHINE TOOL COLUMN DYNAMIC COMPLIANCE MINIMIZATION & REGENERATIVE CHATTER MITIGATION

### 4.1 Problem Definition
During heavy face-milling of steel forgings on a vertical machining center, severe regenerative chatter occurred at an axial depth of cut $a_p \ge 2.2\text{ mm}$, accompanied by loud acoustic screams ($>95\text{ dBA}$) and poor surface waviness ($R_a > 6.3\ \mu\text{m}$). The root cause was traced to excessive dynamic compliance of the structural column and headstock slide assembly.

### 4.2 Regenerative Chatter Formulation (Altintas-Budak Analytical Formulation)

The dynamic milling process in orthogonal coordinates $(x, y)$ is governed by:
$$\begin{bmatrix} F_x(t) \\ F_y(t) \end{bmatrix} = \frac{1}{2} a_p K_t \begin{bmatrix} \alpha_{xx}(t) & \alpha_{xy}(t) \\ \alpha_{yx}(t) & \alpha_{yy}(t) \end{bmatrix} \begin{bmatrix} \Delta x(t) \\ \Delta y(t) \end{bmatrix}$$
where $\Delta x(t) = x(t) - x(t - \tau)$ is the regenerative dynamic chip thickness modulation, $\tau = 60 / (N \cdot z)$ is the tooth passing period, and $K_t$ is the tangential cutting force coefficient.

Averaging the directional time-varying coefficients over one tooth pitch transforms the system into the frequency domain:
$$\det \left( \mathbf{I} - \frac{1}{2} K_t a_p \left( 1 - e^{-i \omega_c \tau} \right) \mathbf{A}_0 \mathbf{G}(i \omega_c) \right) = 0$$
where $\mathbf{G}(i \omega_c)$ is the tool-tip transfer function matrix ($[H_{xx}, H_{xy}; H_{yx}, H_{yy}]$).

The critical limiting axial depth of cut ($a_{lim}$) is analytically determined by the real part of the eigenvalues $\Lambda = \Lambda_R + i \Lambda_I$:
$$a_{lim} = -\frac{2 \pi}{N_t K_t} \left( \frac{\Lambda_R^2 + \Lambda_I^2}{\Lambda_R} \right)$$

```
Axial Depth of Cut a_p [mm]
     ▲
 6.0 |            UNSTABLE CHATTER REGIME
     |         /\           /\           /\
 4.0 |________/  \_________/  \_________/  \_________ (After Rib & TMD Optimization: a_lim = 4.8 mm)
     |       /    \       /    \       /    \
 2.0 |------/------\-----/------\-----/------\------- (Baseline Design: a_lim = 1.7 mm)
     |     /        \   /        \   /        \
 0.0 +────┴──────────┴─┴──────────┴─┴──────────┴────► Spindle Speed N [RPM]
               STABLE MACHINING REGIME
```

### 4.3 Structural Optimization & Tuned Mass Damper (TMD) Synthesis
1. **Rib Topology Redesign**:
   - Analyzed strain energy distribution of the column under harmonic cutting loads at the critical chatter frequency ($f_c = 142\text{ Hz}$).
   - Replaced standard horizontal ribs with an optimized **diagonal cross-rib pattern (X-ribbing)** combined with thicker structural wall sections at the guideway mounting surfaces.
   - Reduced direct dynamic compliance peak magnitude $|H_{yy}|$ from $1.85 \times 10^{-6}\text{ m/N}$ to $1.12 \times 10^{-6}\text{ m/N}$ (**39.4% reduction**).
2. **Auxiliary Dynamic Absorber (TMD)**:
   - For residual compliance, a single-DOF Tuned Mass Damper was designed and mounted directly on the spindle housing.
   - Tuned using **Den Hartog’s optimum equal-peak tuning formula**:
$$f_{opt} = \frac{\omega_a}{\omega_n} = \frac{1}{1 + \mu}, \quad \zeta_{opt} = \sqrt{\frac{3 \mu}{8 (1 + \mu)^3}}$$
     where $\mu = m_{TMD} / M_{modal} \approx 0.05$ (absorber mass ratio).
   - In-situ cutting trials demonstrated that the stable depth of cut increased from **$1.7\text{ mm}$ to $4.8\text{ mm}$ (a 182% improvement)** without any chatter instability.

---

## 5. CASE STUDY 4: IN-SITU JOINT PARAMETER IDENTIFICATION & PHYSICS-INFORMED MODEL UPDATING

### 5.1 The Industrial Challenge
In machine-tool digital twin modeling, structural cast iron parts can be modeled with high confidence using continuum solid mechanics ($E, \rho, \nu$). However, rolling-element linear guideway (LM) block joints and bolted interfaces exhibit contact compliance and micro-slip damping that are virtually impossible to predict accurately from nominal CAD drawings alone.

### 5.2 Mathematical Inverse Parameter Identification
The joint interface was parameterized as an equivalent continuous spring-damper boundary layer characterized by normal contact stiffness ($k_n$), tangential shear stiffness ($k_t$), and viscous damping ($c_n, c_t$).

The parameter identification problem was framed as a nonlinear minimization of modal discrepancies:
$$\min_{\boldsymbol{\theta}} \mathcal{J}(\boldsymbol{\theta}) = \sum_{r=1}^M w_r \left( \frac{\omega_{r}^{FEA}(\boldsymbol{\theta}) - \omega_{r}^{EXP}}{\omega_{r}^{EXP}} \right)^2 + \sum_{r=1}^M \left( 1 - \text{MAC}\left( \boldsymbol{\phi}_{r}^{FEA}(\boldsymbol{\theta}), \boldsymbol{\phi}_{r}^{EXP} \right) \right)$$
where:
- $\boldsymbol{\theta} = [k_n, k_t, c_n, c_t]^T$: Parameter vector,
- $\text{MAC}(\boldsymbol{\phi}_1, \boldsymbol{\phi}_2) = \frac{|\boldsymbol{\phi}_1^H \boldsymbol{\phi}_2|^2}{(\boldsymbol{\phi}_1^H \boldsymbol{\phi}_1)(\boldsymbol{\phi}_2^H \boldsymbol{\phi}_2)}$: Modal Assurance Criterion ($0 \le \text{MAC} \le 1$).

### 5.3 Implementation & Results
- Built a parametric model updating pipeline in Python calling ANSYS Batch via APDL commands.
- Leveraged Nelder-Mead simplex and gradient-based Levenberg-Marquardt algorithms.
- **Outcome**: The average MAC value across the first 6 structural modes increased from $0.78$ to **$0.96$**, and frequency discrepancies were reduced from $12.4\%$ to **$< 2.1\%$**.
- This foundational work forms my direct industrial stepping stone toward **real-time data assimilation** in academic research.

---

## 6. EXPERIMENTAL INSTRUMENTATION & NUMERICAL COMPUTING ARSENAL

### Computational & Simulation Tools
| Domain | Software / Environment | Depth of Usage & Implementation |
|---|---|---|
| **Structural FEA** | ANSYS Mechanical (APDL / Workbench) | Macro automation, APDL scripting for parametric bearing matrices, substructuring, harmonic/transient dynamics |
| **Nonlinear FEA** | ABAQUS Standard | Surface-to-surface contact mechanics, pre-tightened bolted joint non-linearities, stress stiffening |
| **Multibody Dynamics** | RecurDyn / Simscape | Flexible-multibody co-simulation, rigid-flexible coupled mechanism analysis |
| **Scientific Computing** | Python (NumPy, SciPy, Matplotlib) | Writing custom solvers: Altintas-Budak chatter lobes, Jones-Harris 5-DOF bearing model, modal parameter extraction |
| **Numerical Mathematics** | MATLAB / Simulink | State-space modeling, control system Bode/Nyquist design, digital signal filtering |
| **CAD & Engineering Design** | Siemens NX / SolidWorks | Parametric 3D solid modeling, defeaturing for CAE meshing, engineering drafting |

### Experimental Testing Equipment & Data Acquisition
- **Excitation**: Modal Impact Hammers (PCB Piezotronics, various tip hardnesses: vinyl, Delrin, aluminum, steel).
- **Sensing**: Triaxial miniature accelerometers (PCB, Kistler, sensitivity: $10–100\text{ mV/g}$), Eddy current non-contact displacement probes (AEC, Keyence).
- **Data Acquisition**: OROS OR36 / Dewesoft Sirius multi-channel high-speed dynamic signal analyzers.
- **Signal Processing**: Fast Fourier Transform (FFT), Power Spectral Density (PSD), H1/H2 Transfer Function estimators, Coherence function analysis ($\gamma^2(\omega) > 0.9$ quality control).

---

## 7. ALIGNMENT WITH GRADUATE RESEARCH IN JAPAN

My four years of industrial CAE and experimental dynamics practice provide a solid foundation for the research themes investigated by leading Japanese laboratories:

1. **Science Tokyo (Nakano Laboratory)**:
   - *Synergy*: Prof. Nakano's breakthrough on workpiece excitation-driven chatter control (*MSSP 2026*) directly complements my industrial experience in stability lobe mapping and dynamic absorber tuning. My FEA substructuring and modal analysis capabilities can accelerate theoretical modeling and experimental validation of active/semi-active chatter control devices.
2. **Tokyo University of Agriculture and Technology (Yamato Research Group)**:
   - *Synergy*: Prof. Yamato’s state-of-the-art noncontact electromagnetic spindle dynamic compliance measurement (*IJAT 2025*) and boundary data assimilation are the natural next-generation evolution of my bearing stiffness and FRF correlation work. I possess the practical knowledge of spindle-bearing mechanics needed to formulate physics-informed state observers and assimilate real-time electromagnetic sensor data.
3. **Kyushu University (Machinery Dynamics Laboratory - Inoue & Mori Lab)**:
   - *Synergy*: Prof. Inoue and Assist. Prof. Mori’s research on rotor self-synchronization (*MSSP 2025*) and non-linear vibration control directly parallels my work on rotor dynamics, gyroscopic coupling, and nonlinear bearing stiffness modeling.
4. **Hiroshima University (Ibaraki Laboratory)**:
   - *Synergy*: Prof. Ibaraki’s pioneering work on dynamic R-test and volumetric error calibration of multi-axis machine tools aligns with my multi-axis structural compliance and joint stiffness parameter identification experience.

---
*End of Technical Portfolio.*
