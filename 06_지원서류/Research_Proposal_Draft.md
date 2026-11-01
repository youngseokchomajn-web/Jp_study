# ACADEMIC RESEARCH PROPOSAL (MASTER'S THESIS PROPOSAL DRAFT)

## Title: Physics-Informed Data Assimilation and Dynamic Compliance Evaluation for Machine-Tool Spindle-Bearing Systems Under High-Speed Cutting Conditions
**Japanese Subtitle**: 高速切削条件下における工作機械主軸・軸受系の物理情報に基づくデータ同化と動的コンプライアンス評価に関する研究

**Applicant**: Youngseok Cho (조영석)  
**Intended Degree**: Master of Engineering (M.Eng.)  
**Target Enrollment**: April 2028 (Spring Intake)  
**Primary Research Field**: Mechanical Engineering / Precision Machine Dynamics, Vibration Control, and Structural CAE  
**Target Institutions**: 
- Institute of Science Tokyo — IGP(C), Nakano Laboratory (Assoc. Prof. Yutaka Nakano)
- Tokyo University of Agriculture and Technology (TUAT) — Yamato Research Group (Assoc. Prof. Shuntaro Yamato)
- Kyushu University — Machinery Dynamics Laboratory (Prof. Takumi Inoue / Assist. Prof. Hiroki Mori)
- Hiroshima University — Mechanical Design & Systems Laboratory (Prof. Soichi Ibaraki)

---

## ABSTRACT

In modern precision manufacturing, achieving autonomous machining transformation (MX) and stable high-speed milling requires continuous awareness of the structural dynamic state at the tool-workpiece interface. Conventional finite element analysis (FEA) provides detailed structural predictions but fails in operational environments due to rotational centrifugal ball unloading, thermal expansion, and non-stationary cutting force disturbances. Conversely, purely data-driven black-box models require vast destructive experimental datasets and lack physical interpretability.

This research proposal establishes a **physics-informed data assimilation framework** that synchronizes reduced-order rotor-bearing dynamic models with sparse, non-contact in-situ measurements (e.g., noncontact electromagnetic loading and displacement sensing). By embedding the nonlinear kinematics of angular contact ball bearings (Jones-Harris formulation) into an Ensemble Kalman Filter (EnKF) or Physics-Informed Neural Network (PINN) architecture, the proposed system will estimate time-varying bearing preloads, contact angles, and tool-tip Frequency Response Functions (FRFs) in real time. Building upon the applicant’s four years of industrial CAE and structural dynamics experience, this research will provide the foundational dynamic state estimation necessary for active chatter vibration suppression and autonomous feed-rate optimization in next-generation smart machine tools.

---

## 1. RESEARCH BACKGROUND & PROBLEM FORMULATION

### 1.1 The Industrial Challenge in High-Speed Machine Tools
The machining productivity and surface accuracy of machine tools are fundamentally constrained by **regenerative chatter vibration**, an aggressive self-excited instability arising from the dynamic interaction between the structural compliance of the machine tool and the chip regeneration mechanism (Altintas & Budak, 1995).

In high-speed motorized spindles (spindle speeds $\Omega \ge 15,000\text{ RPM}$), the tool-point dynamic compliance matrix:
$$\mathbf{G}(i\omega) = \frac{\mathbf{X}(i\omega)}{\mathbf{F}(i\omega)}$$
is not stationary. Instead, it undergoes substantial, continuous shifts during operation due to three coupled physical phenomena:
1. **Centrifugal and Gyroscopic Loading**: Centrifugal forces acting on rolling elements induce radial expansion and ball contact angle migration ($\alpha_i \ne \alpha_o$), resulting in a non-linear reduction of bearing radial stiffness by up to $30–40\%$ at maximum RPM.
2. **Thermo-Mechanical Preload Variations**: Thermal expansion of the spindle shaft relative to the water-cooled housing alters internal bearing clearances and preloads.
3. **Dynamic Cutting Force Perturbations**: Heavy intermittent milling forces exert large moment loads, shifting the operating point along the nonlinear Hertzian contact curve ($Q \propto \delta^{3/2}$).

```
[ Conventional Approach: Disconnected Island ]
  Offline FEA (Static / Linear)  ≠  Physical Machine (Rotational, Thermal, Nonlinear)
           │                                      │
           ▼                                      ▼
  Inaccurate FRF at Speed                  Unpredicted Chatter & Surface Defects

[ Proposed Physics-Informed Data Assimilation ]
  Reduced-Order Model (ROM) ◄── (EnKF / PINN) ──► Sparse Noncontact Sensors
   (Craig-Bampton + Bearing)     Real-Time Feedback  (Noncontact EM Loading/Probes)
                                      │
                                      ▼
             Synchronized Real-Time Tool-Tip Compliance G(iω, t)
                                      │
                                      ▼
            Predictive Feedforward Active Chatter Suppression (TMD / Modulation)
```

### 1.2 Limitations of Current State-of-the-Art
- **Static / Offline FEA Limitations**: Commercial CAE tools (ANSYS, ABAQUS) cannot execute in real time alongside physical machining. Running a full-scale harmonic response analysis for complex casting structures requires minutes to hours, rendering it useless for closed-loop machine control.
- **Purely Data-Driven Black-Box Models**: Deep learning models mapping sensor signals directly to tool chatter lack generalizability across different tool holders, tool lengths, and machine postures.
- **Recent Experimental Breakthroughs in Japan**:
  - *Yamato et al. (IJAT 2025, ASME JMSE 2025)* demonstrated that noncontact electromagnetic loading can measure static/dynamic compliance of rotating spindles up to high RPM without touching the rotating tool. However, converting sparse spindle-shaft sensor signals into full-field tool-point FRFs requires an underlying structural dynamics observer.
  - *Nakano et al. (MSSP 2026)* demonstrated that regenerative chatter can be suppressed by modulating time delays through workpiece dynamic excitation. However, optimal tuning of such active suppression systems depends critically on accurate knowledge of instantaneous structural transfer functions.

This proposal bridges these two frontiers by uniting **industrial-grade structural CAE modeling** with **modern physics-informed data assimilation**.

---

## 2. RESEARCH QUESTIONS & CORE HYPOTHESES

### Research Questions (RQ)
- **RQ1**: How can high-order 3D finite element models of the spindle-bearing-housing assembly be condensed into ultra-low-dimensional state-space representations while preserving nonlinear bearing boundary kinematics?
- **RQ2**: Can sparse, noncontact dynamic measurements (such as electromagnetic coil currents and eddy-current displacements) uniquely identify internal bearing preload states and contact angles under high-speed rotation?
- **RQ3**: How can in-situ identified dynamic compliance functions be seamlessly integrated with active vibration absorbers or workpiece modulation controllers to guarantee unconditional chatter stability?

### Core Hypotheses
1. **Hypothesis 1 (Modal Reduction & Nonlinear Boundary Substructuring)**: A Craig-Bampton substructuring formulation combined with an explicit 5-DOF Jones-Harris nonlinear bearing boundary can reproduce spindle natural frequencies and cross-frequency response peaks with $<3\%$ error, while executing in $<1\text{ ms}$ per time step.
2. **Hypothesis 2 (Bayesian Data Assimilation via EnKF)**: Integrating the reduced-order model as the state transition operator in an Ensemble Kalman Filter (EnKF) will allow accurate reconstruction of hidden bearing stiffnesses from only 2 to 4 displacement probe channels, even in the presence of $10\%$ measurement noise.
3. **Hypothesis 3 (Predictive Stability Expansion)**: Feedforward synthesis of real-time FRFs into stability lobe algorithms will predict impending chatter bifurcation boundaries, enabling active absorbers to expand stable cutting depth by over $150\%$.

---

## 3. PROPOSED METHODOLOGY & WORK PACKAGES (WP)

The proposed research will be executed across four interconnected work packages over a 2-year Master’s program:

```
┌──────────────────────────────────────────────────────────────────────────────┐
│  WP1: High-Fidelity Reduced-Order Modeling (ROM) & Nonlinear Bearing Model   │
│  - Craig-Bampton reduction of spindle frame & housing                        │
│  - 5-DOF Jones-Harris kinematics: centrifugal & gyroscopic coupling          │
└──────────────────────────────────────┬───────────────────────────────────────┘
                                       │
                                       ▼
┌──────────────────────────────────────────────────────────────────────────────┐
│  WP2: Noncontact Dynamic Sensing & Experimental Setup Integration            │
│  - Noncontact electromagnetic exciter integration (spindle shaft loading)    │
│  - Multi-channel eddy-current and piezoelectric acceleration acquisition     │
└──────────────────────────────────────┬───────────────────────────────────────┘
                                       │
                                       ▼
┌──────────────────────────────────────────────────────────────────────────────┐
│  WP3: Physics-Informed Sequential Data Assimilation (EnKF / PINN)             │
│  - State estimation: Preload F_p(t), contact angles α_i, α_o, joint damping  │
│  - Sub-millisecond recursive state update & real-time FRF reconstruction     │
└──────────────────────────────────────┬───────────────────────────────────────┘
                                       │
                                       ▼
┌──────────────────────────────────────────────────────────────────────────────┐
│  WP4: In-Situ Dynamic Compliance Tracking & Active Chatter Mitigation        │
│  - Analytical Altintas-Budak SLD generation from synchronized FRFs           │
│  - Active workpiece modulation / Tuned Mass Damper (TMD) closed-loop control │
└──────────────────────────────────────────────────────────────────────────────┘
```

### WP1: High-Fidelity Reduced-Order Modeling (ROM) of the Spindle System
1. **Substructuring**: Partition the stationary structural frame and spindle housing into boundary DOFs ($\mathbf{q}_b$) and interior DOFs ($\mathbf{q}_i$) using Craig-Bampton reduction:
   $$\mathbf{q} = \begin{bmatrix} \mathbf{I} & \mathbf{0} \\ -K_{ii}^{-1} K_{ib} & \boldsymbol{\Phi}_k \end{bmatrix} \begin{bmatrix} \mathbf{q}_b \\ \boldsymbol{\eta}_k \end{bmatrix}$$
2. **Rotor & Bearing Formulation**: Model the rotating spindle shaft using Timoshenko beam theory, incorporating gyroscopic matrix $\Omega \mathbf{G}_r$. Couple the shaft to the housing via a 5-DOF nonlinear spring-damper bearing model:
   $$\mathbf{F}_{bearing} = \mathbf{f}\left( \Delta \mathbf{u}, \Omega, F_{preload}, T \right)$$
   where internal equilibrium at each ball incorporates centrifugal force $F_c = \frac{1}{2} m_b d_m \omega_c^2$ and gyroscopic moment $M_g = J_b \omega_b \omega_c \sin \beta$.

### WP2: Noncontact Dynamic Sensing & Experimental Integration
1. **Electromagnetic Excitation Rig**: Adopt noncontact magnetic bearing coils or electromagnetic exciters positioned at the front spindle nose (following Yamato et al., 2025).
2. **Measurement Strategy**: Measure dynamic excitation current $I(t)$ and radial displacements $X(t), Y(t)$ using eddy-current sensors. Eliminate the need for bulky rotating force dynamometers by calibrating coil electromagnetic force characteristics:
   $$F_{mag} \approx k_i I - k_s x$$
3. **Modal Verification**: Benchmark experimental FRFs at standstill ($0\text{ RPM}$) using traditional modal impact hammers to establish baseline ground-truth modal parameters.

### WP3: Physics-Informed Sequential Data Assimilation
1. **State-Space Formulation**: Construct the augmented state vector $\mathbf{z}_k = [\mathbf{x}_k^T, \dot{\mathbf{x}}_k^T, \boldsymbol{\theta}_k^T]^T$, where $\boldsymbol{\theta}_k = [F_{preload}, \alpha_i, k_{joint}, c_{modal}]^T$ represents time-varying physical parameters.
2. **Ensemble Kalman Filtering (EnKF)**:
   - Forecast step: Propagate an ensemble of structural states through the nonlinear reduced-order dynamics:
     $$\mathbf{z}_{k|k-1}^{(j)} = \mathcal{M}\left( \mathbf{z}_{k-1|k-1}^{(j)} \right) + \mathbf{w}_k^{(j)}$$
   - Analysis (Update) step: Update ensemble states using sparse displacement measurements $\mathbf{y}_k$:
     $$\mathbf{z}_{k|k}^{(j)} = \mathbf{z}_{k|k-1}^{(j)} + \mathbf{K}_k \left( \mathbf{y}_k - \mathcal{H}\left( \mathbf{z}_{k|k-1}^{(j)} \right) + \mathbf{v}_k^{(j)} \right)$$
3. **PINN Complement**: Evaluate a Physics-Informed Neural Network architecture running on edge GPUs to estimate continuous field variables where real-time Matrix inversion is constrained.

### WP4: In-Situ Compliance Tracking & Active Chatter Vibration Control
1. **Real-Time Dynamic Compliance Synthesis**: Extract the direct tool-point transfer function $H_{xx}(i\omega, t)$ and cross-transfer function $H_{xy}(i\omega, t)$ from the updated state observer.
2. **Chatter Stability Boundary Prediction**: Calculate instantaneous stability lobes via Altintas-Budak analytical formulation:
   $$a_{lim}(t) = -\frac{2\pi}{N_t K_t} \frac{\Lambda_R(t)^2 + \Lambda_I(t)^2}{\Lambda_R(t)}$$
3. **Active Control Integration**:
   - Link with Nakano Lab's active workpiece vibration excitation or smart dynamic absorber concepts.
   - Adjust active damping controller gains in real time as the spindle compliance shifts, eliminating chatter before vibration amplitudes exceed tolerance limits.

---

## 4. SYNERGIES WITH TARGET LABORATORIES IN JAPAN

### 4.1 Institute of Science Tokyo — Nakano Laboratory (Assoc. Prof. Yutaka Nakano)
- **Direct Research Convergence**: Prof. Nakano's recent pioneer paper (*MSSP 2026*, DOI: `10.1016/j.ymssp.2026.114043`) proposes controlling end-milling chatter by workpiece excitation-driven time-delay variation. 
- **Applicant’s Contribution**: The effectiveness of time-delay variation depends on the dynamic modal characteristics of the combined tool-workpiece system. My proposed physics-informed state observer can supply the real-time compliance matrices required to optimize Nakano Lab’s excitation parameters dynamically during high-speed cutting.

### 4.2 Tokyo University of Agriculture and Technology (TUAT) — Yamato Research Group (Assoc. Prof. Shuntaro Yamato)
- **Direct Research Convergence**: Prof. Yamato is the leading authority on noncontact electromagnetic spindle compliance measurement (*IJAT 2025*, DOI: `10.20965/ijat.2025.p0024`) and boundary condition data assimilation.
- **Applicant’s Contribution**: While Yamato Lab excels at experimental noncontact electromagnetic hardware and inverse algorithms, my four years of industrial FEA/MBD experience in modeling 3D machine structures, bearings, and casting frames provides the structural mechanics backbone needed to scale from experimental test rigs to full-scale multi-axis industrial machine tools.

### 4.3 Kyushu University — Machinery Dynamics Laboratory (Prof. Takumi Inoue & Assist. Prof. Hiroki Mori)
- **Direct Research Convergence**: Prof. Inoue and Assist. Prof. Mori’s expertise in rotor self-synchronization (*MSSP 2025*, DOI: `10.1016/j.ymssp.2025.112778`) and nonlinear vibration control offers an ideal theoretical environment to study gyroscopic nonlinearities and modal interactions in high-speed spinning rotors.

### 4.4 Hiroshima University — Mechanical Design & Systems Laboratory (Prof. Soichi Ibaraki)
- **Direct Research Convergence**: Prof. Ibaraki’s international prominence in 5-axis machine tool volumetric error calibration and dynamic R-test trajectory tracking provides an opportunity to extend this compliance evaluation framework from tool-point vibration to multi-axis spatial geometric accuracy.

---

## 5. TWO-YEAR MASTER'S RESEARCH TIMELINE (2028.04 – 2030.03)

| Period | Milestone & Work Content | Expected Deliverable |
|---|---|---|
| **M1 – M6**<br>*(2028.04 – 2028.09)* | - Advanced coursework in Continuum Mechanics, Advanced Vibration, and System Control.<br>- Comprehensive literature review of physics-informed data assimilation in structural mechanics.<br>- Detailed formulation of the Craig-Bampton reduced-order spindle model in Python/C++. | Mathematical formulation report; validated baseline ROM code. |
| **M7 – M12**<br>*(2028.10 – 2029.03)* | - Integration of 5-DOF Jones-Harris nonlinear bearing stiffness model.<br>- Interfacing with laboratory noncontact electromagnetic excitation rig.<br>- Standstill and low-speed experimental calibration against impact hammer modal testing. | Intermediate Progress Report; conference presentation at JSME (Japan Society of Mechanical Engineers). |
| **M13 – M18**<br>*(2029.04 – 2029.09)* | - Development and tuning of the Ensemble Kalman Filter (EnKF) for real-time state estimation.<br>- High-speed spindle rotation trials ($10,000–24,000\text{ RPM}$) under varying preload and thermal conditions.<br>- In-situ dynamic compliance tracking validation. | Peer-reviewed journal manuscript submission (e.g., *Precision Engineering* or *MSSP*). |
| **M19 – M24**<br>*(2029.10 – 2030.03)* | - Closed-loop integration with active chatter suppression / workpiece modulation.<br>- End-milling cutting validation trials demonstrating chatter-free depth of cut expansion.<br>- Master’s Thesis defense and final manuscript publication. | Master's Thesis; 2nd peer-reviewed journal paper (e.g., *IJAT* or *CIRP Annals*). |

---

## 6. EXPECTED CONTRIBUTIONS & SCIENTIFIC MERIT

1. **Academic Contribution**: Establishes a rigorous bridge between computational solid mechanics (FEA/ROM) and sequential data assimilation (Bayesian filtering) tailored for rotating precision machinery, overcoming the trade-off between physical fidelity and computational speed.
2. **Industrial Impact**: Enables autonomous machine tools to self-diagnose their dynamic stability boundaries during cutting, eliminating catastrophic chatter marks, preventing spindle bearing seizure, and maximizing machining throughput in critical aerospace and automotive components.
3. **Personal Trajectory**: Equips the applicant with advanced academic research methodologies, positioning him to lead cutting-edge CAE-digital twin developments in precision manufacturing upon completion of the Master's degree.

---

## 7. REFERENCES

1. **Nakano, Y.**, et al. (2026). "Chatter control in end-milling process using time-delay variation driven by workpiece excitation." *Mechanical Systems and Signal Processing*, Vol. 249, Article 114043. DOI: `10.1016/j.ymssp.2026.114043`.
2. **Yamato, S.**, et al. (2025). "Static and Dynamic Measurements of Spindle System During Rotation by Noncontact Electromagnetic Loading System." *International Journal of Automation Technology*, Vol. 19, No. 1, pp. 24–40. DOI: `10.20965/ijat.2025.p0024`.
3. **Yamato, S.**, et al. (2025). "A Simplified Estimation of Spindle Dynamic Compliance From Current Measurement for Contactless Electromagnetic Excitation." *ASME Journal of Manufacturing Science and Engineering*, Vol. 147, No. 1. DOI: `10.1115/1.4067175`.
4. **Altintas, Y., and Budak, E.** (1995). "Analytical Prediction of Chatter Stability Conditions in Milling." *CIRP Annals - Manufacturing Technology*, Vol. 44, No. 1, pp. 357–362.
5. **Inoue, T., Mori, H.**, et al. (2025). "Energy-based analysis and experiment for self-synchronization of two rotors installed in two-DOF translational system." *Mechanical Systems and Signal Processing*, Vol. 234, Article 112778. DOI: `10.1016/j.ymssp.2025.112778`.
6. **Iwasaki, M., Seki, K.**, et al. (2025). "Modeling Machine-Stand Vibration Based on Multibody Dynamics Analysis Considering Contact in Support Mechanisms." *International Journal of Automation Technology*, Vol. 19, No. 4, pp. 499–507. DOI: `10.20965/ijat.2025.p0499`.
7. **Craig, R. R., and Bampton, M. C.** (1968). "Coupling of substructures for dynamic analyses." *AIAA Journal*, Vol. 6, No. 7, pp. 1313–1319.
8. **Harris, T. A., and Kotzalas, M. N.** (2006). *Rolling Bearing Analysis: Essential Concepts of Bearing Technology*, CRC Press.
9. **Evensen, G.** (2009). *Data Assimilation: The Ensemble Kalman Filter*, Springer.
10. **Raissi, M., Perdikaris, P., and Karniadakis, G. E.** (2019). "Physics-informed neural networks: A deep learning framework for solving forward and inverse problems involving nonlinear partial differential equations." *Journal of Computational Physics*, Vol. 378, pp. 686–707.

---
*End of Research Proposal Draft.*
