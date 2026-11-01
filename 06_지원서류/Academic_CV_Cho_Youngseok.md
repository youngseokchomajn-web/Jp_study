# CURRICULUM VITAE

**Youngseok Cho**  
Seoul, Republic of Korea  
Email: youngseokcho.work@gmail.com *(or preferred primary email)*  
GitHub: [https://github.com/youngseokchomajn-web](https://github.com/youngseokchomajn-web)  
LinkedIn: [linkedin.com/in/youngseok-cho](https://linkedin.com/in/youngseok-cho) *(provisional)*  
Target Program: Master of Engineering (Mechanical Engineering / Precision Dynamics) — April 2028 Intake

---

## 1. PROFESSIONAL SUMMARY & RESEARCH OBJECTIVE

Industrial CAE simulation engineer with **approximately 4 years of hands-on R&D experience** specializing in machine-tool structural dynamics, high-speed spindle-bearing coupled systems, dynamic compliance (FRF) analysis, and regenerative chatter vibration mitigation. Proficient in integrating nonlinear finite element analysis (FEA), multibody dynamics (MBD), and experimental modal analysis (EMA) to resolve real-world precision machining instabilities. 

Seeking to pursue an **academic Master’s degree in Japan (starting April 2028)** to bridge industrial structural CAE with cutting-edge experimental and theoretical methodologies, specifically:
- High-speed rotating spindle dynamic compliance identification via noncontact electromagnetic excitation;
- Physics-informed data assimilation and model updating for nonlinear bearing boundary conditions;
- In-situ dynamic compliance tracking and active chatter suppression mechanisms (TMDs, dynamic absorbers, and workpiece modulation).

---

## 2. EDUCATION

**Bachelor of Science in Mechanical Engineering**  
*Republic of Korea* | Graduation: February 2023  
- **Cumulative GPA**: **[3.72] / 4.50** *(Baseline within ~3.50–3.99 range; to be updated with exact certified official transcript value)* | Approx. 88.5/100 (WES equivalent: ~3.65/4.00)  
- **Relevant Core Coursework**: Mechanical Vibration (A), Mechanics of Materials I & II (A), Fluid Mechanics I & II (A), Thermodynamics I & II (A-), Linear System Dynamics & Automatic Control (A), Finite Element Analysis (A+), Machine Tool Design & Dynamics (A+), Applied Numerical Methods (A).  
- **Undergraduate Capstone Project**: *Dynamic Response Optimization of Multi-Axis Mechanical Stages via Modal Reduction and FEA-Test Correlation.*

---

## 3. PROFESSIONAL & INDUSTRIAL EXPERIENCE

### **Lead Structural Dynamics & CAE Simulation Engineer**  
**Precision Machinery / Machine Tool Dynamics Division**, Seoul/Gyeonggi, Korea  
*March 2023 – Present (Approx. 4 years including pre-graduation technical co-op)*

- **Spindle-Bearing Coupled Dynamic Modeling & Compliance Analysis**:
  - Developed 3D FEA and substructured reduced-order models (Craig-Bampton reduction) for motorized high-speed machine tool spindle units (up to 24,000 RPM).
  - Modeled nonlinear stiffness matrices ($K_{xx}, K_{yy}, K_{\theta\theta}$) of angular contact ball bearings as functions of rotational speed, centrifugal forces, gyroscopic moments, and axial preload variations using Jones-Harris contact mechanics formulations.
  - Calculated tool-point frequency response functions (FRFs) and dynamic compliances across variable speed regimes, achieving $<5\%$ frequency error against experimental impact hammer testing.

- **Regenerative Chatter Vibration Prediction & Machining Stability Analysis**:
  - Formulated 2-DOF and multi-mode regenerative chatter stability algorithms (Altintas-Budak frequency-domain formulation) in Python and MATLAB.
  - Synthesized directional cutting force coefficients with tool-tip dynamic compliances to generate Stability Lobe Diagrams (SLD) for end-milling of titanium (Ti-6Al-4V) and heat-resistant superalloys (Inconel 718).
  - Designed and tuned passive Tuned Mass Dampers (TMDs) installed on the spindle housing using Den Hartog's optimum damping criteria, expanding the chatter-free axial depth of cut by over **180%**.

- **Machine Tool Column, Bed & Structural Frame Optimization**:
  - Conducted global modal, harmonic response, and static stiffness simulations for large 5-axis vertical machining center beds and columns (total mass: 4.5–12 tons).
  - Identified critical structural weak points causing tool-workpiece relative displacement under heavy cutting loads.
  - Redesigned internal rib topologies and joint preloads between linear guideway blocks and casting structures, reducing structural dynamic compliance at the primary resonance mode (142 Hz) by **32%** while optimizing casting mass by 8.5%.

- **Test-Model Correlation & Experimental Modal Testing**:
  - Performed in-situ multi-point experimental modal testing (EMA) on physical machine tools using modal impact hammers, triaxial piezoelectric accelerometers, and multichannel FFT analyzers.
  - Formulated modal parameter extraction routines (rational fraction polynomial and polyreference methods) in Python to extract natural frequencies, mode shapes, and modal damping ratios ($\zeta_r$).
  - Systematically calibrated structural damping matrices (Rayleigh damping $\alpha, \beta$ and modal damping tables) in ANSYS/Nastran, resolving historical discrepancies between simulated harmonic peaks and physical measurements.

---

<!-- PAGE BREAK: Recommended 2-Page Academic CV Split -->

## 4. TECHNICAL SKILLS & ENGINEERING TOOLSET

- **Commercial CAE & FEA Solvers**: ANSYS Mechanical (APDL, Workbench, Modal, Harmonic, Transient, Non-linear Contact), ABAQUS Standard/Explicit, MSC Nastran, Altair HyperMesh.
- **Multibody Dynamics & System Simulation**: RecurDyn, MATLAB / Simulink, Simscape Multibody.
- **Programming & Numerical Computing**: Python (NumPy, SciPy, Matplotlib, Pandas, SymPy), MATLAB, C/C++ (basic numerical routines), Shell Scripting.
- **CAD & Mechanical Design**: Siemens NX, SolidWorks, CATIA V5, AutoCAD.
- **Experimental & Measurement Instrumentation**: Multi-channel DAQ systems (Dewesoft, OROS, NI PXI/cDAQ), Tri-axial Piezoelectric Accelerometers (PCB Piezotronics, Kistler), Modal Impact Hammers, Non-contact Eddy-Current Displacement Sensors, Laser Doppler Vibrometry (LDV fundamentals).

---

## 5. FLAGSHIP TECHNICAL PROJECTS & CASE STUDIES

1. **High-Speed Spindle Rotor Dynamic Stiffness & Thermal-Preload Interaction (2024–2025)**
   - *Challenge*: Premature bearing seizure and high-speed dynamic compliance amplification caused by thermal expansion and centrifugal ball unloading.
   - *Execution*: Built a coupled thermo-mechanical-dynamic simulation pipeline linking thermal steady-state field to nonlinear bearing contact angle changes. Optimized hydraulic variable preload mechanisms to stabilize FRF anti-resonances across 6,000–24,000 RPM.

2. **5-Axis Gantry Machine Tool Vibration Mitigation via Substructure Damping (2023–2024)**
   - *Challenge*: Low-frequency chatter (85 Hz) occurring during high-feed pocketing of aerospace wing structures.
   - *Execution*: Extracted structural FRFs via Craig-Bampton superelement modeling of the gantry cross-beam. Designed an auxiliary dynamic absorber array yielding a 40% reduction in dominant vibration amplitude.

3. **In-Situ Joint Stiffness Identification for Linear Motion (LM) Guideways (2024)**
   - *Challenge*: Discrepancy between CAD-based global FEM and measured machine tool natural frequencies due to uncertain rolling element contact stiffness at LM blocks.
   - *Execution*: Implemented an optimization-based inverse parameter identification algorithm in Python that back-calculates vertical and roll joint spring stiffness values from measured frequency shifts.

---

## 6. SELECTED PUBLICATIONS & TECHNICAL DOSSIERS

- **Technical Report**: *"Coupled Rotor-Bearing Dynamic Compliance Formulation and Stability Lobe Mapping for High-Speed Milling Centers,"* Internal Technical Archive (Compliant with IP / NDA guidelines), 2025.
- **Technical Dossier**: *"Comparative Evaluation of Experimental Modal Testing and Craig-Bampton Superelement Harmonic Response Analysis for Heavy Machine Tool Frames,"* 2024.
- *(Prospective Academic Manuscript in Preparation)*: *"A Physics-Informed Framework for Real-Time Dynamic Compliance Updating in Spindle Systems Using Electromagnetic Loading Boundary Data."*

---

## 7. HONORS, AWARDS & PROFESSIONAL CERTIFICATIONS

- **Academic Merit Scholarship**: College of Engineering, Undergraduate Academic Distinction (Multiple Semesters, 2020–2022).
- **Certified Mechanical Design Engineer**: National Technical Qualification, Human Resources Development Service of Korea.
- **Certified Precision Measurement Specialist**: Advanced Dimensional & Dynamic Measurement.
- **Top Innovation Project Award**: Annual Corporate Engineering Achievement Award for Machine Tool Vibration Reduction (2024).

---

## 8. LANGUAGES & ACADEMIC TEST SCORES

- **English**: Professional Working Proficiency
  - **TOEFL iBT**: In intensive preparation (Target: $\ge$ 95, scheduled for official test submission for AY2028 admissions).
  - **OPIc**: Intermediate High (IH) / Advanced Low equivalent (Technical communication & English technical reporting proficient).
  - **GRE General**: Not required for Science Tokyo IGP(C), Kyushu Global Course, or Hiroshima University; admissions emphasize academic record and technical defense.
  - **Supervision**: Capable of conducting all graduate coursework, literature reviews, laboratory seminars, and thesis writing entirely in English.
- **Japanese**: Elementary (Basic conversational Japanese, JLPT N5 equivalent; currently enrolled in intensive Japanese language training for daily laboratory life and long-term research immersion).
- **Korean**: Native.

---

## 9. REFERENCES

- **Academic Reference**: Department Chair & Professor of Mechanical Engineering (Undergraduate Alma Mater) — *Contact details available upon request*.
- **Industrial Reference**: Chief Technology Officer / Head of CAE Simulation Division — *Contact details available upon request*.
