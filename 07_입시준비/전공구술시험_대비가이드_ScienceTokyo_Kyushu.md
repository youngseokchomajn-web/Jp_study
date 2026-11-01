# 일본 국립대 기계공학 영어 석사 전공 구술시험(Oral Exam) 대비 마스터 가이드
## Science Tokyo IGP(C) 5대 기초 전공 & 규슈대·히로시마대 전공 심층 대비

**대상 학교**: 
- **Institute of Science Tokyo (Science Tokyo, 구 도쿄공업대학)** — IGP(C) 기계계열 구술면접 (5대 전공 필수)
- **규슈대학교 (Kyushu University)** — 기계공학 글로벌 코스 1월 전공 구술시험 (Rotor Dynamics & 15분 발표)
- **히로시마대학교 (Hiroshima University)** — 첨단이공학연구과 해외특별선발 온라인 전형 (공작기계 정밀도 및 R-test)

**지원자 프로필**: 기계공학 학사, 기계 CAE 실무 약 4년 (공작기계 구조동역학, 스핀들-베어링, FRF, 채터 진동)  
**시험 언어**: 100% 영어 (English Technical Defense)

---

# 목 차
1. [전공 구술시험 개요 및 평가 프로세스](#1-전공-구술시험-개요-및-평가-프로세스)
2. [Science Tokyo 기계공학 5대 전공 심층 대비 (핵심 이론 & 빈출 문답)](#2-science-tokyo-기계공학-5대-전공-심층-대비)
   - [2.1 기계진동학 (Mechanical Vibration)](#21-기계진동학-mechanical-vibration)
   - [2.2 재료역학 (Mechanics of Materials)](#22-재료역학-mechanics-of-materials)
   - [2.3 선형제어공학 (Linear Control Systems)](#23-선형제어공학-linear-control-systems)
   - [2.4 유체역학 (Fluid Mechanics)](#24-유체역학-fluid-mechanics)
   - [2.5 열역학 (Thermodynamics)](#25-열역학-thermodynamics)
3. [규슈대학교 글로벌 코스 구술시험 특화 전략 (Inoue & Mori 연구실)](#3-규슈대학교-글로벌-코스-구술시험-특화-전략)
4. [히로시마대학교 특별선발 면접 특화 전략 (Ibaraki 연구실)](#4-히로시마대학교-특별선발-면접-특화-전략)
5. [CAE 실무 엔지니어 전용 방어 논리 (First-Principles Physics)](#5-cae-실무-엔지니어-전용-방어-논리)
6. [영문 필수 전문용어 및 수식 구술 핸드북](#6-영문-필수-전문용어-및-수식-구술-핸드북)

---

## 1. 전공 구술시험 개요 및 평가 프로세스

### 1.1 구술시험의 본질과 면접관의 평가 관점
일본 국립대학원 영어 독립 석사과정(IGP 등)의 구술시험은 단순 인성 면접이 아닌, **"학부 4년간의 기계공학 핵심 역학 원리를 온전히 체화하고 있는가"**와 **"연구계획서를 학술적·수학적으로 방어할 수 있는가"**를 테스트하는 **심층 테크니컬 구술고사(Technical Oral Defense)**입니다.

- **심사위원단**: 지도교수 지망자 1명 + 분과 교수 2~3명 (총 3~4명의 면접관).
- **진행 방식**: 화상 회의(Zoom/Webex)로 20~30분 진행.
  - 전반부 (5~10분): 지원자 자기소개, 실무/학부 연구 요약, 지원 연구계획서 발표 (슬라이드 화면 공유 또는 구술).
  - 중반부 (10~15분): 기계공학 기초 전공 질문 (기초 역학 5개 분야 무작위 질문).
  - 후반부 (5분): 연구계획서 세부 기술 질문 및 영어 소통 능력, 향후 진로.

---

## 2. SCIENCE TOKYO 기계공학 5대 전공 심층 대비

### 2.1 기계진동학 (Mechanical Vibration) — [최우선 핵심 분야]

#### A. 핵심 이론 압축
1. **1자유도 자유진동/강제진동 방정식**:
   $$m \ddot{x} + c \dot{x} + k x = F_0 \cos(\omega t)$$
   - 고유진동수: $\omega_n = \sqrt{k/m}$, 감쇠비: $\zeta = \frac{c}{2\sqrt{km}} = \frac{c}{2m\omega_n}$
   - 감쇠 고유진동수: $\omega_d = \omega_n \sqrt{1 - \zeta^2}$
   - 감쇠 진동의 분류:
     * 미감쇠(Underdamped, $\zeta < 1$): 진폭이 지수함수적으로 감쇠하며 주기적 진동 지속.
     * 임계감쇠(Critically damped, $\zeta = 1$): 진동 없이 가장 빠른 속도로 평형점 복귀 ($x(t) = (C_1 + C_2 t)e^{-\omega_n t}$).
     * 과감쇠(Overdamped, $\zeta > 1$): 진동 없이 느린 감쇠 복귀.
   - 대수감소율(Logarithmic Decrement, $\delta$):
     $$\delta = \ln\left(\frac{x_1}{x_2}\right) = \frac{2\pi \zeta}{\sqrt{1 - \zeta^2}} \approx 2\pi \zeta \quad (\zeta \ll 1)$$
   - 조화진동 정상상태 응답: $X = \frac{F_0/k}{\sqrt{(1 - r^2)^2 + (2\zeta r)^2}}$ (여기서 주파수비 $r = \omega/\omega_n$)
   - 공진(Resonance) 시 동적 증폭계수(Dynamic Magnification Factor): $Q \approx \frac{1}{2\zeta}$ (소감쇠 시 $r \approx 1$).

2. **다자유도 진동 및 모달 해석 (Modal Analysis)**:
   $$\mathbf{M} \ddot{\mathbf{x}} + \mathbf{C} \dot{\mathbf{x}} + \mathbf{K} \mathbf{x} = \mathbf{F}(t)$$
   - 고유치 문제 (Undamped): $(\mathbf{K} - \omega_r^2 \mathbf{M}) \boldsymbol{\phi}_r = \mathbf{0}$
   - 모드 직교성 (Orthogonality):
     $$\boldsymbol{\phi}_r^T \mathbf{M} \boldsymbol{\phi}_s = \delta_{rs} M_r, \quad \boldsymbol{\phi}_r^T \mathbf{K} \boldsymbol{\phi}_s = \delta_{rs} K_r = \delta_{rs} \omega_r^2 M_r$$
   - 모달 좌표 변환: $\mathbf{x}(t) = \boldsymbol{\Phi} \boldsymbol{\eta}(t)$를 통해 비연성된 $n$개의 단자유도 방정식으로 분해.

3. **동흡진기 (Tuned Mass Damper - TMD) 와 Den Hartog 최적 조율**:
   - 주 진동계($M, K$)에 보조 진동계($m, k, c$)를 부착하여 공진 진폭 억제.
   - 질량비 $\mu = m/M$.
   - Den Hartog 최적 고유진동수비: $g_{opt} = \frac{\omega_a}{\omega_n} = \frac{1}{1 + \mu}$
   - Den Hartog 최적 감쇠비: $\zeta_{opt} = \sqrt{\frac{3\mu}{8(1+\mu)^3}}$

4. **재생 채터 진동 (Regenerative Chatter) vs. 강제 진동 (Forced Vibration)**:
   - **강제 진동**: 외부 외력(모터 불평형, 절삭 공구 회전수 $\times$ 날 수)의 가진 주파수가 구조 고유진동수와 일치하여 발생. 진동을 제거하려면 외부 가진원 주파수를 변경.
   - **자성(재생) 진동**: 외부 가진력 없이, 이전 날이 남긴 가공면 파형과 현재 날의 진동 간 위상차(Phase shift)에 의해 절삭 저항의 변동이 발생하고, 이 변동력이 다시 구조 진동을 증폭시키는 닫힌 루프(Closed-loop) 불안정성 현상. 주파수는 공구 통과 주파수가 아니라 구조물의 지배적 고유진동수 부근에서 발생.

---

#### B. 예상 구술 질문 및 모범 영문 답변 (Q&A)

**Q1. Explain the physical difference between forced vibration and self-excited vibration (such as machining chatter).**
> **Model Answer (English)**:  
> "In forced vibration, the system is driven by an external periodic excitation force that exists independently of the system's own motion, such as mass unbalance or tooth-passing frequency. If the machine stops cutting, the excitation stops. The response occurs precisely at the excitation frequency.  
> In contrast, self-excited vibration—such as regenerative chatter—does not possess an external periodic force. The excitation mechanism is created and modulated by the motion of the structure itself. In milling, relative vibration between the tool and workpiece leaves a wavy surface. The subsequent cutting tooth encounters a modulated dynamic chip thickness, causing a periodic cutting force variation. If there is a phase lag between the inner and outer modulations, energy is continuously pumped into the structural mode. Consequently, the vibration grows exponentially at a frequency near the natural frequency of the structure, independent of the spindle rotational speed."

**Q2. How do you mathematically derive the orthogonality of mode shapes, and why is it essential in structural FEA?**
> **Model Answer (English)**:  
> "For a linear undamped system, consider two distinct natural modes: $(\mathbf{K} - \omega_r^2 \mathbf{M})\boldsymbol{\phi}_r = \mathbf{0}$ and $(\mathbf{K} - \omega_s^2 \mathbf{M})\boldsymbol{\phi}_s = \mathbf{0}$. Pre-multiplying the first equation by $\boldsymbol{\phi}_s^T$ and taking the transpose, utilizing the symmetry of mass matrix $\mathbf{M} = \mathbf{M}^T$ and stiffness matrix $\mathbf{K} = \mathbf{K}^T$, and subtracting the two scalar equations yields:  
> $(\omega_r^2 - \omega_s^2) \boldsymbol{\phi}_s^T \mathbf{M} \boldsymbol{\phi}_r = 0$.  
> Since $\omega_r \ne \omega_s$ for distinct modes, it follows that $\boldsymbol{\phi}_s^T \mathbf{M} \boldsymbol{\phi}_r = 0$ and consequently $\boldsymbol{\phi}_s^T \mathbf{K} \boldsymbol{\phi}_r = 0$.  
> In structural FEA and CAE, orthogonality allows us to diagonalize the mass and stiffness matrices through modal transformation $\mathbf{x} = \boldsymbol{\Phi} \boldsymbol{\eta}$. This decouples an $N$-degree-of-freedom coupled system into $N$ independent single-DOF equations, dramatically accelerating harmonic and transient dynamic calculations from hours to seconds."

**Q3. What is a Frequency Response Function (FRF), and how do you interpret its real and imaginary parts in terms of stability?**
> **Model Answer (English)**:  
> "A Frequency Response Function (FRF), denoted as $H(\omega) = X(\omega)/F(\omega)$, represents the steady-state dynamic output of a linear system per unit harmonic input force as a function of frequency. In receptance format (displacement over force), it represents dynamic compliance.  
> The real part, $\text{Re}[H(\omega)]$, represents the in-phase compliance response with the force. In regenerative chatter theory (Altintas-Budak formulation), the critical axial depth of cut $a_{lim}$ is inversely proportional to the minimum negative real part of the oriented transfer function: $a_{lim} \propto -1 / \text{Re}[G]$.  
> The imaginary part, $\text{Im}[H(\omega)]$, represents the $90^\circ$ out-of-phase quadrature response, directly corresponding to energy dissipation or damping. The peak of the imaginary part defines the exact resonance frequency and allows extraction of the modal damping ratio via the half-power bandwidth method."

**Q4. How do you experimentally estimate the modal damping ratio $\zeta$ from an impulse response and from an FRF?**
> **Model Answer (English)**:  
> "In the time domain, we use the logarithmic decrement method from an impulse ring-down signal: measuring two successive peak amplitudes $x_n$ and $x_{n+m}$, we compute $\delta = \frac{1}{m} \ln(x_n / x_{n+m}) \approx 2\pi\zeta$, from which $\zeta \approx \delta / (2\pi)$.  
> In the frequency domain, we use the half-power bandwidth method on the FRF magnitude curve. At the resonance peak $\omega_n$ with maximum amplitude $X_{max}$, we locate the two frequencies $\omega_1$ and $\omega_2$ where the amplitude drops to $X_{max} / \sqrt{2}$ (the $-3\text{ dB}$ points). The damping ratio is then calculated directly as $\zeta = \frac{\omega_2 - \omega_1}{2\omega_n}$."

---

### 2.2 재료역학 (Mechanics of Materials)

#### A. 핵심 이론 압축
1. **응력-변형률 텐서, 주응력 및 모어 원 (Mohr's Circle)**:
   - 2차원 평면응력 상태 $(\sigma_x, \sigma_y, \tau_{xy})$:
     * 모어 원 중심: $C = \left( \frac{\sigma_x + \sigma_y}{2}, 0 \right)$
     * 모어 원 반지름: $R = \sqrt{\left(\frac{\sigma_x - \sigma_y}{2}\right)^2 + \tau_{xy}^2}$
     * 주응력: $\sigma_{1,2} = \frac{\sigma_x + \sigma_y}{2} \pm R$
     * 최대 평면 전단응력: $\tau_{max} = R = \frac{\sigma_1 - \sigma_2}{2}$
   - 3차원 주응력: $\sigma_1 \ge \sigma_2 \ge \sigma_3$, 절대 최대 전단응력: $\tau_{max,abs} = \frac{\sigma_1 - \sigma_3}{2}$.

2. **항복 조건 (Yield Criteria)**:
   - **Tresca (최대 전단응력설)**: $\tau_{max} = \frac{\sigma_1 - \sigma_3}{2} = \frac{\sigma_Y}{2} \implies \sigma_1 - \sigma_3 = \sigma_Y$.
   - **von Mises (전단변형에너지설, $J_2$ theory)**:
     $$\sigma_v = \sqrt{\frac{1}{2}\left[ (\sigma_1 - \sigma_2)^2 + (\sigma_2 - \sigma_3)^2 + (\sigma_3 - \sigma_1)^2 \right]} = \sigma_Y$$
     - 물리적 의미: 체적 변화(정수압 응력)를 제외하고 형상 왜곡(Distortion)을 유발하는 편차 응력(Deviatoric stress tensor $s_{ij}$)의 제2 불변량 $J_2$가 한계치에 도달할 때 연성 재료가 항복.

3. **원형 축의 비틀림 (Torsion of Circular Shafts)**:
   $$\tau = \frac{T r}{J}, \quad \theta = \frac{T L}{G J}$$
   - $J$: 극관성모멘트. 중실축(Solid): $J = \frac{\pi d^4}{32}$, 중공축(Hollow spindle): $J = \frac{\pi (d_o^4 - d_i^4)}{32}$.
   - 비틀림 강성: $K_\theta = \frac{G J}{L}$.

4. **보 굽힘 이론: 오일러-베르누이 vs. 티모셴코 (Euler-Bernoulli vs. Timoshenko Beam)**:
   - **오일러-베르누이(Euler-Bernoulli)** 가정: 변형 전 단면은 변형 후에도 평면을 유지하고 중립축에 수직이다 ($\gamma_{xz} = 0$, 전단변형 무시). $L/h > 10$인 가늘고 긴 보에 적합.
     $$EI \frac{d^4 w}{dx^4} = q(x)$$
   - **티모셴코(Timoshenko)**: 전단변형각 $\phi$와 회전 관성(Rotary inertia)을 반영. 단면이 중립축에 수직하지 않음. $L/h < 5$인 두꺼운 보 또는 고주파 스핀들 축 진동 해석에 필수.

5. **기둥의 좌굴 (Buckling) 과 오일러 임계 하중**:
   $$P_{cr} = \frac{\pi^2 E I}{(K L)^2}$$
   - $K$: 유효길이계수 (양단 힌지 $K=1$, 양단 고정 $K=0.5$, 일단 고정-일단 자유 $K=2$, 일단 고정-일단 힌지 $K\approx 0.7$).

---

#### B. 예상 구술 질문 및 모범 영문 답변 (Q&A)

**Q1. What is the physical justification for using von Mises yield criterion rather than Tresca for ductile metals like steel?**
> **Model Answer (English)**:  
> "The von Mises yield criterion is based on the distortion strain energy density—the energy associated solely with shape distortion, completely independent of hydrostatic pressure $\sigma_m = (\sigma_1+\sigma_2+\sigma_3)/3$. Since experimental tests prove that isotropic hydrostatic compression or tension does not cause plastic slip in metals, yield depends only on the deviatoric stress tensor $J_2$.  
> Mathematically, the von Mises yield surface forms a smooth cylinder in Haigh-Westergaard principal stress space, whereas Tresca forms a hexagonal prism. Von Mises accounts for the intermediate principal stress $\sigma_2$, which Tresca completely neglects. Experimental data for steel and aluminum align closer to the von Mises ellipse by approximately $15\%$ under pure shear conditions."

**Q2. When simulating a high-speed machine tool spindle shaft, why must we switch from Euler-Bernoulli beam theory to Timoshenko beam theory?**
> **Model Answer (English)**:  
> "A typical machine-tool spindle shaft is short, hollow, and thick, characterized by a low length-to-diameter aspect ratio ($L/D < 5$), and it operates at high vibrational frequencies up to several thousand Hertz.  
> Euler-Bernoulli theory assumes that plane cross-sections remain perpendicular to the neutral axis, totally neglecting transverse shear deformation and rotary inertia. For thick shafts and high-frequency bending modes where the wavelength is comparable to the shaft diameter, shear deformation contributes significantly to total compliance. Neglecting shear overestimates the shaft stiffness, leading to an over-prediction of natural frequencies by up to $15–20\%$. Timoshenko beam theory accounts for both transverse shear strain and rotary inertia, providing accurate dynamic compliance predictions."

**Q3. How do you construct Mohr's circle for a combined bending moment $M$ and torque $T$ on a circular shaft?**
> **Model Answer (English)**:  
> "On the outer surface of a circular shaft subjected to bending $M$ and torsion $T$, the longitudinal normal stress is $\sigma_x = \frac{M y}{I} = \frac{32 M}{\pi d^3}$, the transverse stress is $\sigma_y = 0$, and the torsional shear stress is $\tau_{xy} = \frac{T r}{J} = \frac{16 T}{\pi d^3}$.  
> On the Mohr's circle plane $(\sigma, \tau)$, the center is located at $C = (\sigma_x / 2, 0) = \left( \frac{16 M}{\pi d^3}, 0 \right)$, and the radius is $R = \sqrt{(\sigma_x / 2)^2 + \tau_{xy}^2} = \frac{16}{\pi d^3}\sqrt{M^2 + T^2}$.  
> The maximum principal stress is $\sigma_1 = \frac{16}{\pi d^3}\left( M + \sqrt{M^2 + T^2} \right)$, and the maximum shear stress is $\tau_{max} = R = \frac{16}{\pi d^3}\sqrt{M^2 + T^2}$."

---

### 2.3 선형제어공학 (Linear Control Systems)

#### A. 핵심 이론 압축
1. **상태공간 표현 (State-Space Representation) 및 전달함수 변환**:
   $$\dot{\mathbf{x}}(t) = \mathbf{A} \mathbf{x}(t) + \mathbf{B} \mathbf{u}(t), \quad \mathbf{y}(t) = \mathbf{C} \mathbf{x}(t) + \mathbf{D} \mathbf{u}(t)$$
   - 전달함수(Transfer Function): $G(s) = \mathbf{C} (s\mathbf{I} - \mathbf{A})^{-1} \mathbf{B} + \mathbf{D}$
   - 시스템 극점(Poles): $\det(s\mathbf{I} - \mathbf{A}) = 0$ (행렬 $\mathbf{A}$의 고유치).

2. **PID 제어기의 물리적 작용과 한계**:
   $$u(t) = K_p e(t) + K_i \int_0^t e(\tau) d\tau + K_d \frac{de(t)}{dt}$$
   - 비례(P): 현재 오차에 비례하여 응답 속도를 높이나 정상상태 오차(Offset)를 완전히 제거하지 못함.
   - 적분(I): 과거 누적 오차를 반영하여 정상상태 오차를 0으로 제거($e_{ss} \to 0$). 단, 위상 지연(Phase lag)을 유발하여 시스템 안정성을 저하시키고 액추에이터 포화 시 와인드업(Integrator Windup) 위험 발생.
   - 미분(D): 오차의 변화율을 감지하여 미래 거동을 예측, 위상 여유(Phase lead) 및 감쇠를 부가하여 오버슈트 억제. 단, 고주파 측정 노이즈 증폭 위험.

3. **안정도 판별법 (Stability Criteria)**:
   - **나이퀴스트 안정도 판별법 (Nyquist Criterion)**:
     $$Z = N + P$$
     ($Z$: 폐루프 RHP 극점 수, $N$: $(-1, j0)$점을 시계방향으로 감싼 횟수, $P$: 개루프 RHP 극점 수).
   - **이득 여유(Gain Margin) & 위상 여유(Phase Margin)**:
     - GM: 위상이 $-180^\circ$가 되는 주파수($\omega_{pc}$)에서 이득의 여유 ($1/|G(j\omega)|$).
     - PM: 이득이 $0\text{ dB}$ ($|G(j\omega)| = 1$)가 되는 주파수($\omega_{gc}$)에서 위상과 $-180^\circ$ 간의 차이 ($180^\circ + \angle G(j\omega_{gc})$).

4. **가제어성(Controllability) 및 가관측성(Observability)**:
   - 가제어성 행렬: $\mathcal{C} = \begin{bmatrix} \mathbf{B} & \mathbf{A}\mathbf{B} & \mathbf{A}^2\mathbf{B} & \dots & \mathbf{A}^{n-1}\mathbf{B} \end{bmatrix} \implies \text{rank}(\mathcal{C}) = n$
   - 가관측성 행렬: $\mathcal{O} = \begin{bmatrix} \mathbf{C} \\ \mathbf{C}\mathbf{A} \\ \mathbf{C}\mathbf{A}^2 \\ \vdots \\ \mathbf{C}\mathbf{A}^{n-1} \end{bmatrix} \implies \text{rank}(\mathcal{O}) = n$

---

#### B. 예상 구술 질문 및 모범 영문 답변 (Q&A)

**Q1. What is the physical significance of Gain Margin and Phase Margin, and what typical values are required for machine tool servo drives?**
> **Model Answer (English)**:  
> "Gain Margin (GM) and Phase Margin (PM) quantify the robustness of a feedback control system against modeling uncertainties, time delays, and parameter drifts before reaching instability.  
> Phase Margin indicates how much additional phase lag (such as computational delay or physical communication delay) can be tolerated at the gain crossover frequency before oscillation occurs. Gain Margin indicates how much the open-loop gain can be increased at the phase crossover frequency (where phase lag reaches $-180^\circ$) before instability.  
> For high-precision machine tool servo drives and active vibration absorbers, typical target values are a Phase Margin between $45^\circ$ and $60^\circ$ and a Gain Margin of at least $6\text{ dB}$ (a factor of 2) to ensure well-damped transient response without excessive overshoot."

**Q2. Explain the Separation Principle in state-space modern control theory.**
> **Model Answer (English)**:  
> "The Separation Principle states that for a linear time-invariant system, the design of a state-feedback controller ($\mathbf{u} = -\mathbf{K}\hat{\mathbf{x}}$) and the design of a state observer (such as a Luenberger observer $\dot{\hat{\mathbf{x}}} = \mathbf{A}\hat{\mathbf{x}} + \mathbf{B}\mathbf{u} + \mathbf{L}(\mathbf{y} - \mathbf{C}\hat{\mathbf{x}})$) can be carried out completely independently.  
> The eigenvalues of the combined closed-loop observer-controller system are simply the union of the eigenvalues of $(\mathbf{A} - \mathbf{B}\mathbf{K})$ and the eigenvalues of $(\mathbf{A} - \mathbf{L}\mathbf{C})$. Therefore, one can design the feedback gain $\mathbf{K}$ to meet control performance requirements, and independently design the observer gain $\mathbf{L}$—typically placing observer poles 3 to 5 times faster than controller poles—without altering the controller's closed-loop poles."

**Q3. What is Integrator Windup in machine tool position control, and how do you prevent it?**
> **Model Answer (English)**:  
> "Integrator Windup occurs when a large setpoint step or sustained load disturbance drives the motor amplifier into actuator saturation (voltage or current limit). While the actuator is saturated, the control error cannot be cleared immediately, causing the integral term $\int e(\tau) d\tau$ to accumulate to an excessively large value. When the system finally reaches the target, the saturated integrator takes a long time to unwind, producing huge overshoot and prolonged settling times.  
> We prevent windup using anti-windup algorithms: clamping the integrator state when the actuator hits its limit, using back-calculation anti-windup to bleed off excess integrator charge, or conditionally disabling integration when the error exceeds a predefined threshold."

---

### 2.4 유체역학 (Fluid Mechanics)

#### A. 핵심 이론 압축
1. **질량 보존(연속방정식) 및 나비에-스토크스 방정식**:
   - 연속방정식 (Continuity Equation):
     $$\frac{\partial \rho}{\partial t} + \nabla \cdot (\rho \mathbf{u}) = 0 \quad \xrightarrow{\text{비압축성}} \quad \nabla \cdot \mathbf{u} = \frac{\partial u}{\partial x} + \frac{\partial v}{\partial y} + \frac{\partial w}{\partial z} = 0$$
   - 운동량 보존 (Navier-Stokes Equations, 비압축성 뉴턴 유체):
     $$\rho \left( \frac{\partial \mathbf{u}}{\partial t} + (\mathbf{u} \cdot \nabla)\mathbf{u} \right) = -\nabla p + \mu \nabla^2 \mathbf{u} + \rho \mathbf{g}$$

2. **베르누이 방정식 (Bernoulli's Equation) 과 적용 5대 한계**:
   $$p + \frac{1}{2} \rho v^2 + \rho g z = \text{constant}$$
   - **5대 가정**: ① 비점성 유동(Inviscid, $\mu = 0$), ② 정상 유동(Steady state), ③ 비압축성 유동(Incompressible, $Ma < 0.3$), ④ 유선(Streamline)을 따른 적용, ⑤ 일/열교환 없음.

3. **관내 유동 손실 (Pipe Flow) 과 다르시-바이스바흐 방정식**:
   $$h_f = f \frac{L}{D} \frac{v^2}{2g}$$
   - 층류 ($Re < 2,300$): $f = \frac{64}{Re}$ (조도 $\epsilon/D$와 무관).
   - 난류 ($Re > 4,000$): 무디 선도(Moody Chart) 또는 Colebrook 방정식을 통해 상대조도와 레이놀즈수로부터 마찰계수 $f$ 결정.

4. **경계층 이론 및 유동 박리 (Boundary Layer Separation)**:
   - 평판 층류 경계층 두께: $\delta(x) \approx \frac{5.0 x}{\sqrt{Re_x}}$.
   - 역압력 구배 ($dp/dx > 0$) 환경에서 벽면 전단응력 $\tau_w = \mu \left. \frac{\partial u}{\partial y} \right|_{y=0} = 0$이 되는 지점에서 경계층 박리 발생.

---

#### B. 예상 구술 질문 및 모범 영문 답변 (Q&A)

**Q1. State the fundamental assumptions required to apply Bernoulli's equation, and explain when it fails.**
> **Model Answer (English)**:  
> "Bernoulli’s equation relies on five fundamental assumptions:  
> 1. Inviscid flow (friction and shear stresses are negligible);  
> 2. Incompressible flow (density $\rho$ remains constant, typically Mach number $< 0.3$);  
> 3. Steady flow ($\partial / \partial t = 0$);  
> 4. Application along a single streamline (unless the flow is irrotational everywhere);  
> 5. No energy addition or extraction (no pumps, turbines, or heat transfer).  
> Bernoulli’s equation fails inside viscous boundary layers near solid walls, across shock waves where strong compressibility and entropy generation occur, in separated turbulent wake flows, and in regions where fluid passes through rotating machinery like turbines or pumps."

**Q2. Explain the physical meaning of the Reynolds number, and why pipe friction factor becomes independent of Reynolds number at high turbulent flows.**
> **Model Answer (English)**:  
> "The Reynolds number, $Re = \frac{\rho U D}{\mu}$, represents the ratio of dynamic convective inertia forces to viscous shear forces. At low $Re$, viscous forces dominate and damp out velocity perturbations, maintaining smooth laminar streamlines.  
> In fully rough turbulent pipe flow (the right-hand horizontal region of the Moody diagram), the laminar viscous sublayer becomes so thin that surface roughness asperities protrude directly into the turbulent core. Consequently, momentum loss is governed entirely by form drag over roughness elements rather than viscous shear. Therefore, the friction factor $f$ becomes purely a function of relative roughness $\epsilon/D$, completely independent of $Re$."

---

### 2.5 열역학 (Thermodynamics)

#### A. 핵심 이론 압축
1. **열역학 제1법칙, 내부에너지와 엔탈피**:
   - 제1법칙: $dE = \delta Q - \delta W$.
   - **엔탈피(Enthalpy)**: $h = u + Pv$.
     * 물리적 의미: 유동 유체가 시스템 경계를 통과할 때 보유하는 고유 내부에너지($u$)와 유체를 밀어 넣는 데 필요한 유동일(Flow work $Pv$)의 합.
   - 개방계 정상유동 에너지 방정식 (SFEE):
     $$\dot{Q} - \dot{W}_s = \dot{m} \left[ \left( h_2 - h_1 \right) + \frac{v_2^2 - v_1^2}{2} + g(z_2 - z_1) \right]$$

2. **열역학 제2법칙 및 엔트로피 생성 (Entropy Generation)**:
   - 클라우지우스 부등식: $\oint \frac{\delta Q}{T} \le 0$.
   - 고립계 엔트로피 증가 원리: $dS_{total} = dS_{sys} + dS_{surr} = S_{gen} \ge 0$.
   - 구이-스토돌라 정리(Gouy-Stodola Theorem): 비가역 손실일(Destroyed exergy) $\dot{I} = T_0 \dot{S}_{gen}$.

3. **열역학 사이클 비교 (Thermodynamic Cycles)**:
   - **카르노 사이클 (Carnot)**: 등온팽창 $\to$ 단열팽창 $\to$ 등온압축 $\to$ 단열압축. 최고 이론 효율 $\eta_{Carnot} = 1 - T_L / T_H$.
   - **오토 사이클 (Otto)**: 가솔린 엔진. 등엔트로피 압축 $\to$ **정적 가열** $\to$ 등엔트로피 팽창 $\to$ **정적 방열**. $\eta = 1 - \frac{1}{r_c^{k-1}}$.
   - **디젤 사이클 (Diesel)**: 압축착화 엔진. 등엔트로피 압축 $\to$ **정압 가열** $\to$ 등엔트로피 팽창 $\to$ **정적 방열**.
   - **브레이턴 사이클 (Brayton)**: 가스터빈 추진/발전. 등엔트로피 압축 $\to$ **정압 가열** $\to$ 등엔트로피 팽창 $\to$ **정압 방열**.

---

#### B. 예상 구술 질문 및 모범 영문 답변 (Q&A)

**Q1. Why can no practical heat engine exceed the Carnot efficiency, and what causes irreversibility in mechanical systems?**
> **Model Answer (English)**:  
> "The Carnot efficiency, $\eta = 1 - T_L/T_H$, represents the thermodynamic upper bound derived from the Second Law of Thermodynamics, operating via totally reversible processes where total entropy generation is zero ($S_{gen} = 0$).  
> According to the Clausius inequality, for any real cyclic process, $\oint \delta Q / T \le 0$. Any real mechanical engine incurs irreversibilities, which generate positive entropy ($S_{gen} > 0$). In mechanical engineering systems, primary sources of irreversibility include mechanical friction between moving surfaces, fluid viscous dissipation, unconstrained fluid expansion, and heat transfer across a finite temperature difference ($\Delta T > 0$). These mechanisms irreversibly degrade available work (exergy) into thermal dissipation."

**Q2. Explain the physical difference between internal energy $u$ and enthalpy $h$. Why is enthalpy preferred for open-system heat exchangers?**
> **Model Answer (English)**:  
> "Internal energy $u$ represents the microscopic kinetic and potential energy stored within molecules (translational, vibrational, and chemical bonding). It is the natural thermodynamic property for closed, rigid systems where boundaries do not move ($\delta W = 0$).  
> Enthalpy, defined as $h = u + Pv$, combines the internal energy with the flow work $Pv$ required to push fluid across a control surface against surrounding pressure. In open-system devices such as spindle cooling jackets or heat exchangers, fluid continuously enters and leaves under pressure. Using enthalpy allows us to express the first law simply as $\dot{Q} - \dot{W}_s = \dot{m}\Delta h$, eliminating the need to explicitly compute boundary flow work."

---

## 3. 규슈대학교 글로벌 코스 구술시험 특화 전략 (Inoue & Mori 연구실)

규슈대학교 기계공학 글로벌 코스(1월 전공 구술시험)는 **Machinery Dynamics Laboratory (Prof. Takumi Inoue & Assist. Prof. Hiroki Mori)**의 연구 분야인 **로터 동역학(Rotor Dynamics), 비선형 진동 및 자기동기화(Self-Synchronization, MSSP 2025)**에 집중됩니다.

### 3.1 15분 발표 슬라이드 최적 구성안 (총 10장)
1. **Slide 1**: Title, Name, Industrial Experience Summary, Target Laboratory (Machinery Dynamics Lab).
2. **Slide 2**: Professional Engineering Overview (~4 years CAE simulation in machine tool dynamics).
3. **Slide 3**: Problem Statement: Machining instability in high-speed spindle-bearing systems.
4. **Slide 4**: Mathematical Modeling: Rotor-bearing coupled dynamics & 5-DOF Jones-Harris nonlinear kinematics.
5. **Slide 5**: Finite Element Substructuring (Craig-Bampton CMS) & Dynamic Compliance Formulation.
6. **Slide 6**: Experimental Test-Model Correlation: Multi-point modal hammer test vs. FEA harmonic peaks.
7. **Slide 7**: Engineering Countermeasure: Column rib optimization & Tuned Mass Damper (TMD) yielding 182% depth-of-cut expansion.
8. **Slide 8**: Proposed Master’s Research: Real-time physics-informed data assimilation for rotating spindles.
9. **Slide 9**: Synergies with Inoue/Mori Lab (Rotor non-linear dynamics, gyroscopic coupling & self-synchronization).
10. **Slide 10**: Summary, Expected Contributions & 2-Year Milestone Roadmap.

### 3.2 로터 동역학 특화 예상 Q&A

**Q1. Formulate the Jeffcott rotor model with internal and external damping, and explain the physical cause of rotordynamic instability.**
> **Model Answer (English)**:  
> "A Jeffcott rotor consists of a point mass $m$ on a flexible shaft with stiffness $k$, rotating at spin speed $\Omega$. In the complex coordinate $z = x + iy$, the equation of motion is:  
> $m \ddot{z} + (c_e + c_i)\dot{z} - i \Omega c_i z + k z = m e \Omega^2 e^{i\Omega t}$,  
> where $c_e$ is stationary external viscous damping, and $c_i$ is rotating internal shaft material damping.  
> The term $-i \Omega c_i z$ acts as a skew-symmetric non-conservative circulatory force. When the rotational speed exceeds the first critical speed ($\Omega > \omega_n (1 + c_e/c_i)$), internal shaft damping ceases to dissipate energy and instead pumps rotational kinetic energy into lateral forward whirl vibration, triggering catastrophic rotor self-excited whirl instability."

**Q2. What is the Sommerfeld Effect in rotating machinery?**
> **Model Answer (English)**:  
> "The Sommerfeld Effect is a classic non-ideal resonance phenomenon observed when an unbalance rotor is driven by a non-ideal power source (a torque-limited electric motor). As the rotor speed accelerates toward its critical resonance frequency $\omega_n$, large lateral vibration amplitudes develop. This severe lateral vibration extracts enormous energy from the drive motor. If motor torque is insufficient, the rotational speed becomes trapped or stagnates just below the resonance frequency, while motor power is consumed entirely by lateral vibration. Once motor torque exceeds the critical barrier, the rotor abruptly jumps to a much higher speed with a sudden drop in vibration amplitude."

---

## 4. 히로시마대학교 특별선발 면접 특화 전략 (Ibaraki 연구실)

히로시마대학교 첨단이공학연구과 해외특별선발은 **Prof. Soichi Ibaraki (Mechanical Design and Systems Lab)**의 세계적인 연구 분야인 **5축 공작기계 공간오차(Volumetric Errors) 및 동적 R-test(Dynamic R-test, ISO 10791-6)**에 맞추어집니다.

### 4.1 공작기계 정밀도 및 계측 특화 예상 Q&A

**Q1. What is the difference between Position-Independent Geometric Errors (PIGBs) and Position-Dependent Geometric Errors (PDGEs) in 5-axis machine tools?**
> **Model Answer (English)**:  
> "In multi-axis machine tools:  
> - **Position-Independent Geometric Errors (PIGBs)** represent kinematic location and orientation misalignments of the rotary axes relative to the linear axes (such as squareness errors between axes and rotary axis pivot point offsets). They remain constant regardless of axis position and contribute 8 location error parameters in a typical five-axis machine.  
> - **Position-Dependent Geometric Errors (PDGEs)** are component errors that vary as a function of the axis travel position, such as pitch, yaw, roll, straightness, and linear positioning errors of linear guides, or radial/axial runout and wobble of rotary tables (6 error components per axis).  
> In structural CAE, PIGBs relate to static assembly alignments, whereas PDGEs are strongly influenced by structural frame deflection and guideway waviness."

**Q2. Explain the measurement principle of the Dynamic R-test.**
> **Model Answer (English)**:  
> "The Dynamic R-test measures the relative dynamic displacement between the tool and the workpiece table during simultaneous multi-axis motion (such as synchronous motion of the $X, Y, Z$ linear axes and $B, C$ rotary axes).  
> A precision spherical target artifact is mounted on the machine tool spindle, and a sensor nest containing three or four non-contact displacement sensors (eddy-current or capacitive probes) is clamped to the rotary table. By executing synchronized circular or tool-orientation trajectories and recording 3D probe deflections, the dynamic R-test directly evaluates dynamic trajectory synchronization errors, servo tracking lag, and structural compliance deflections under dynamic motion conditions."

---

## 5. CAE 실무 엔지니어 전용 방어 논리 (First-Principles Physics)

일본 국립대 교수들은 실무 출신 지원자에게 흔히 다음 의구심을 품습니다:  
*"상용 소프트웨어(ANSYS) 버튼만 누른 것 아닌가? 지배 방정식과 수치해석 기초를 정말 이해하고 있는가?"*  
이를 완벽히 불식시키는 필수 방어 논리입니다:

### 5.1 "ANSYS 버튼 클리커" 의심에 대한 결정적 반격
> **Interviewer**: *"You have used commercial CAE tools for 4 years. Did you simply use the built-in GUI solvers, or do you understand what happens at the mathematical solver level?"*  
> **Strong Defense**:  
> "I treat commercial solvers strictly as numerical assemblers of the governing differential equations. For instance, in our spindle-bearing simulations, commercial FEA cannot natively model the speed-dependent nonlinear stiffness reduction of angular contact ball bearings due to centrifugal and gyroscopic ball loading.  
> To overcome this, I personally derived the 5-DOF Jones-Harris nonlinear kinematic equilibrium equations and coded a Newton-Raphson nonlinear solver in Python. I then integrated these computed non-linear stiffness matrices directly into ANSYS via APDL matrix elements (`MATRIX27`/`CBUSH`).  
> Furthermore, in modal and harmonic analysis, I verify mesh convergence using the Richardson Extrapolation and Grid Convergence Index (GCI), ensuring that numerical discretization errors do not contaminate our dynamic compliance transfer functions."

### 5.2 접촉 비선형성 수렴 실패 시 대처법
> **Interviewer**: *"When contact non-linearity does not converge in FEA, what physical and mathematical steps do you take?"*  
> **Strong Defense**:  
> "Non-convergence in contact problems typically arises from abrupt changes in the contact status (chattering between open and closed status) or severe ill-conditioning of the tangent stiffness matrix $\mathbf{K}_T$.  
> Mathematically, I check whether the penalty stiffness factor is excessively high, which causes numerical stiffness and round-off error, or too low, which permits non-physical penetration. I employ the Augmented Lagrange formulation to decouple normal penetration from numerical stiffness. If severe geometric non-linearity exists, I activate line search algorithms and reduce the automated load-stepping increments ($\Delta t$). Physically, I inspect rigid body modes and apply weak stabilizing spring dampers to prevent numerical singularities."

---

## 6. 영문 필수 전문용어 및 수식 구술 핸드북

| 한글 용어 | English Academic Term | 구술 발음 및 핵심 표현 |
|---|---|---|
| 고유진동수 / 고유모드 | Natural Frequency / Mode Shape | "Eigenvalue $\omega_r$ and Eigenvector $\boldsymbol{\phi}_r$" |
| 주파수응답함수 | Frequency Response Function (FRF) | "Complex dynamic compliance $H(\omega) = X(\omega)/F(\omega)$" |
| 재생 채터 진동 | Regenerative Chatter Vibration | "Self-excited instability caused by phase lag in dynamic chip thickness" |
| 동흡진기 | Tuned Mass Damper (TMD) | "Passive auxiliary oscillator tuned via Den Hartog's optimum criterion" |
| 자이로스코프 효과 | Gyroscopic Effect / Matrix | "Speed-proportional skew-symmetric matrix $\Omega \mathbf{G}$ causing mode splitting" |
| 헤르츠 접촉 이론 | Hertzian Contact Mechanics | "Nonlinear load-deflection relationship $Q = K_h \delta^{3/2}$" |
| 성분모드합성법 | Component Mode Synthesis (CMS) | "Craig-Bampton reduction using constraint modes and normal modes" |
| 상태공간방정식 | State-Space Representation | "First-order matrix differential system $\dot{\mathbf{x}} = \mathbf{A}\mathbf{x} + \mathbf{B}\mathbf{u}$" |
| 가제어성 / 가관측성 | Controllability / Observability | "Full rank condition of the controllability matrix $[B, AB, \dots]$" |
| 폰 미세스 항복조건 | von Mises Yield Criterion | "Distortion energy density reaching critical threshold $J_2 = k^2$" |
| 모어 원 | Mohr's Circle | "Graphical representation of transformed 2D/3D stress state to find principal stresses" |
| 엔탈피 | Enthalpy | "Thermodynamic energy property $h = u + Pv$ accounting for internal energy and flow work" |
| 경계층 박리 | Boundary Layer Separation | "Adverse pressure gradient $dp/dx > 0$ causing zero wall shear stress" |
| 엔트로피 생성 | Entropy Generation / Exergy Destruction | "Irreversibility principle governed by Gouy-Stodola theorem $I = T_0 S_{gen}$" |
| 조머펠트 현상 | Sommerfeld Effect | "Rotordynamic power-capture phenomenon causing motor speed trapping near resonance" |
| 동적 R-test | Dynamic R-test | "Synchronous multi-axis kinematic trajectory evaluation using spherical target and displacement sensors" |

---
*End of Oral Exam Preparation Guide.*
