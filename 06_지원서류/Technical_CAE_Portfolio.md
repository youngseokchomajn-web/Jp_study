# Technical CAE Portfolio — Evidence-Controlled Working Draft

**Applicant:** Youngseok Cho  
**Research direction:** Machine-tool structural dynamics and spindle–bearing systems  
**Intended intake:** April 2028 (subject to each programme's published admission route)

> **Status: WORKING DRAFT — not an evidence-verified portfolio.** The earlier version contained unsupported numerical outcomes, experimental work, solver/tool claims and detailed case histories. Those claims are intentionally removed here. This version defines the technically defensible portfolio structure; case-specific details must be supplied from the applicant's own work records and cleared for disclosure.

## 1. Engineering background
The applicant has approximately four years of professional experience in CAE / simulation work related to machine-tool structural vibration. The work context includes machine-tool structures, spindle and bearing systems, and the influence of structural dynamics on system behaviour.

The applicant's current technical interests include:
- Structural dynamic behaviour of machine-tool frames, heads and spindle housings.
- Coupling between spindle, bearing supports and surrounding structures.
- Bearing stiffness changes associated with preload and contact angle.
- Frequency-response functions (FRFs), modal behaviour and dynamic compliance.
- Improving the physical consistency of simulation models and their boundary conditions.

This summary is based on the applicant's described work areas. It does not imply that every method below has already been independently implemented or experimentally validated.

## 2. Portfolio case-study template
Each real project should be documented using this template. Create one copy per project.

### Case [N] — [Anonymized engineering problem]
**Context:** [Machine/system class; remove customer, model and confidential identifiers]  
**Applicant's role:** [What you personally owned and executed]  
**Question:** [One engineering question, stated without marketing language]

**Model and assumptions**
- Geometry / idealization: [What was modeled]
- Materials and joints: [Verified inputs]
- Boundary conditions: [How supports, interfaces and loads were represented]
- Solver and analysis type: [Exact tool/module and analysis]
- Bearing representation: [Linear/nonlinear; source of stiffness data; preload/contact-angle assumptions]

**Execution**
1. [Actual step performed]
2. [Actual step performed]
3. [Actual step performed]

**Verification**
- Comparison target: [Measurement, analytical solution, previous model or independent calculation]
- Metric: [Define frequency error, MAC, FRF magnitude/phase error, etc. only if actually calculated]
- Evidence: [Approved plot/report or reproducible calculation]
- Limitations: [Unmeasured parameters, model uncertainty, boundary-condition sensitivity]

**Outcome**
- Qualitative conclusion: [Only if supported]
- Quantitative result: [Value + unit + baseline + method + source; otherwise omit]
- Personal learning: [What changed in your engineering judgement]

**Disclosure review:** [Approved / anonymized further / not for external use]

## 3. Candidate technical themes (not claims of completed work)

### A. Spindle–bearing–housing dynamic coupling
Potential research question: How do bearing-support stiffness assumptions and housing flexibility affect the predicted dynamic response of a machine-tool spindle system?

Possible methods, subject to programme and laboratory resources:
- Establish a baseline structural model and clearly defined interfaces.
- Compare rigid-support, linear-support and parameterized bearing-support models.
- Examine natural frequencies and tool-point / spindle response through FRFs.
- Conduct sensitivity analysis for bearing stiffness, preload and support conditions.
- Validate against an available measurement or a separately justified reference model.

### B. Bearing stiffness, preload and contact angle
Potential research question: How sensitive are system-level dynamic predictions to the bearing stiffness model and its operating assumptions?

Possible methods:
- Document the source and validity range of bearing parameters.
- Distinguish catalog values, analytical estimates, supplier data and measured values.
- Evaluate sensitivity to preload, contact angle and operating condition.
- Avoid claiming a nonlinear bearing model unless its governing equations, inputs and implementation can be explained.

### C. Structural FRF and model calibration
Potential research question: Which uncertain support or joint parameters dominate the mismatch between a numerical model and an observed frequency response?

Possible methods:
- Define measurable response quantities and excitation/measurement locations.
- Separate frequency, amplitude, phase and mode-shape comparisons.
- Identify parameters only when the available measurements make them observable.
- Report uncertainty and non-uniqueness rather than presenting one fitted parameter set as uniquely correct.

## 4. Technical principles to defend in an interview
- An FRF is a complex, frequency-dependent input–output relationship. Its real and imaginary parts are orthogonal components of the complex response; the imaginary part alone is not a direct measure of damping.
- Damping is inferred through an appropriate dynamic model or modal parameter-estimation procedure, with assumptions and fit quality reported.
- Half-power bandwidth estimation has assumptions (including an adequately isolated, lightly damped resonance); it is not universally reliable for closely spaced modes or strongly coupled responses.
- A good numerical fit does not prove that the model parameters are physically unique.
- Model validation requires an independent comparison target and an explicit account of uncertainty.

## 5. Evidence register
| Claim / artifact | Evidence required | Status |
|---|---|---|
| Approx. four years of CAE work | Employment records / applicant confirmation | Applicant to verify exact dates |
| Machine-tool structural vibration work | Anonymized work description and approved artifact | Described by applicant; project evidence pending |
| Spindle / bearing system work | Model scope, parameter source and personal contribution | Described by applicant; details pending |
| FRF / dynamic compliance work | Actual plots, model setup and interpretation | Scope and depth to verify |
| Experimental modal testing | Test plan, acquisition files and personal role | Do not claim unless verified |
| Chatter / TMD outcomes | Analysis or test records, baseline and method | Do not claim unless verified |
| Numerical improvement percentages | Traceable raw data and calculation | Excluded pending evidence |

## 6. Assembly plan
1. Select two projects that best represent the applicant's actual work.
2. Create an evidence folder for each project with redacted, employer-approved artifacts.
3. Draft a 1-page case study per project using the template above.
4. Ask a technically knowledgeable reviewer to challenge assumptions and calculations.
5. Remove any detail that cannot be defended orally or disclosed lawfully.
6. Produce a concise 4–6 page portfolio only after the evidence review is complete.
