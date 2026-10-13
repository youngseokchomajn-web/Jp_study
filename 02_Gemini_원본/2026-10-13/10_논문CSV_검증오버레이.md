# 10. 논문 근거 CSV 서지 전수 감사 및 검증 오버레이 보고서

- **조사 기준일:** 2026-10-13
- **감사 대상:** 기존 `02_Gemini_원본/2026-10-13/papers_evidence.csv` (총 9개 데이터 행)
- **감사 기준:** 18차 감사 로그([2026-10-13_논문CSV_서지불일치_감사및_Gemini재검증지시_18차.md](../../01_로그/2026-10-13_논문CSV_서지불일치_감사및_Gemini재검증지시_18차.md)) 및 출판사 공식 Crossref/J-STAGE/Elsevier 메타데이터 직접 대조

---

## 1. 전수 감사 종합 결과 요약

```
[9개 행 전수 대조 결과]
- 서지 및 제목 완전 일치 (MATCH): 3건 (TUAT Yamato 1건, NITech Seki 1건, Kyushu Mori/Inoue 1건)
- 제목 오기 및 수치 외삽 (MISMATCH - REWRITTEN): 1건 (TUT Tajiri 1건)
- 완전한 타 연구 DOI 연결 (MISMATCH - QUARANTINE): 4건 (TUT Tajiri 2건, UTokyo 1건, Kyoto 1건, Nagoya 1건)
- DOI 필드에 프로필 URL 기재 (URL_IS_PROFILE - QUARANTINE): 1건 (TUAT Iwai 1건)
```

**결론:** 기존 `papers_evidence.csv`에 부여되었던 **E3/E4 등급은 즉시 효력을 상실(DISCREDITED)**하며, 공식 원문 초록이 확인된 3건 및 수정본 1건에 대해서만 **E2 (공식 초록 확인)** 등급을 인정합니다. 5건의 불일치/프로필 행은 검증본에서 격리(QUARANTINE) 처리합니다.

---

## 2. 9개 행별 정밀 감사 및 대조 결과

### [Row 1] TUAT — Yamato et al. (2025)
- **DOI:** `10.20965/ijat.2025.p0024`
- **CSV 기재 제목:** Static and Dynamic Measurements of Spindle System During Rotation by Noncontact Electromagnetic Loading System
- **실제 출판사 메타데이터:**
  - 제목: *Static and Dynamic Measurements of Spindle System During Rotation by Noncontact Electromagnetic Loading System*
  - 저자: Shuntaro Yamato, et al.
  - 저널: *International Journal of Automation Technology (IJAT)*, Vol.19, No.1, pp. 24–40, 2025.
- **판정:** **MATCH**
- **조치:** 서지 정보 및 공식 초록 완전 일치. 단, 본문 내 정량 오차표의 직접 열람 전까지는 E3 확정을 보류하고 **E2 (초록 및 개요 확인)**로 하향 조정하여 보존.

---

### [Row 2] TUAT — Iwai, Yamato, Matsubara (2025)
- **기재 URL:** `https://kenkyu-web.tuat.ac.jp/profile/en.16697ed028d11561a2fa89c1675f95c0.html`
- **판정:** **URL_IS_PROFILE_NOT_PAPER**
- **결과:** DOI 식별자 자리에 연구자 프로필 URL이 입력되어 있어 개별 논문의 고유 서지 정보를 독립 검증할 수 없음.
- **조치:** **QUARANTINE (격리)**. 공식 출판 DOI 또는 정식 학회 프리프린트가 확인될 때까지 검증 세트에서 제외.

---

### [Row 3] NITech — Watanabe, Seki et al. (2025)
- **DOI:** `10.20965/ijat.2025.p0499`
- **CSV 기재 제목:** Modeling Machine-Stand Vibration Based on Multibody Dynamics Analysis Considering Contact in Support Mechanisms
- **실제 출판사 메타데이터:**
  - 제목: *Modeling Machine-Stand Vibration Based on Multibody Dynamics Analysis Considering Contact in Support Mechanisms*
  - 저자: Yuya Watanabe, Yuta Mizoguchi, Kenta Seki, Makoto Iwasaki
  - 저널: *IJAT*, Vol.19, No.4, pp. 499–507, 2025.
- **판정:** **MATCH** (저자 머리글자 T. Watanabe 오기를 Yuya Watanabe로 정정)
- **조치:** 서지 정보 및 초록 일치. 기계 스탠드 레벨링 볼트의 Hertz 접촉 비선형 MBD 모델링 확인. 등급을 **E2**로 보정하여 보존.

---

### [Row 4] Toyohashi Tech (TUT) — Tajiri, Kawamura (2024)
- **DOI:** `10.1299/mej.24-00292`
- **CSV 기재 제목:** Parameter identification of nonlinear vibratory systems using physics-informed/grey-box neural networks
- **실제 J-STAGE 메타데이터:**
  - 공식 제목: *Proposal of a parameter identification method for single-degree-of-freedom nonlinear systems using neural networks*
  - 저자: Daiki TAJIRI, Shozo KAWAMURA
  - 저널: *Mechanical Engineering Journal (JSME)*, Vol.11, No.6, p. 24-00292, 2024.
- **판정:** **MISMATCH (REWRITTEN)**
- **결과:** 실제 논문 제목은 '단자유도(single-degree-of-freedom) 비선형 시스템'에 대한 신경망 파라미터 식별 제안임. 원본 CSV의 'grey-box/physics-informed' 표현 및 '1~3% 오차'는 초록 수준에서 명시적 수치로 확인되지 않음.
- **조치:** 공식 제목 및 저자로 재작성하고, 수치 주장을 검증 보류로 낮추어 **E2** 등급으로 보존.

---

### [Row 5] Toyohashi Tech (TUT) — Tajiri, Kawamura (2025)
- **DOI:** `10.1299/mej.24-00475`
- **CSV 기재 제목:** Vibration suppression of layered structural systems with additional dynamic absorbers (12 dB 진동 억제)
- **실제 J-STAGE 메타데이터:**
  - 공식 제목: *Simple abnormality diagnosis of layered structures using an additional vibratory system*
  - 저자: Daiki TAJIRI, Shozo KAWAMURA
  - 저널: *Mechanical Engineering Journal*, Vol.12, No.2, p. 24-00475, 2025.
- **판정:** **MISMATCH (DISCREDITED / QUARANTINE)**
- **결과:** 실제 논문은 부가 진동계를 이용한 다층 구조물의 '간이 이상 진단(Abnormality Diagnosis)' 연구임. 원본 CSV에 적힌 '동흡진기를 통한 12 dB 진동 억제'는 전혀 다른 연구의 주장이 잘못 합성된 것임.
- **조치:** **QUARANTINE**. 검증된 논문 목록에서 완전히 격리.

---

### [Row 6] Kyushu University — Mori, Inoue et al. (2025)
- **DOI:** `10.1016/j.ymssp.2025.112778`
- **CSV 기재 제목:** Energy-based analysis and experiment for self-synchronization of two rotors installed in two-DOF translational system
- **실제 Elsevier 메타데이터:**
  - 제목: *Energy-based analysis and experiment for self-synchronization of two rotors installed in two-DOF translational system*
  - 저자: H. Mori, T. Inoue, et al.
  - 저널: *Mechanical Systems and Signal Processing (MSSP)*, Vol.234, 112778, 2025.
- **판정:** **MATCH**
- **조치:** 제목 및 저자 완전 일치. 초록상 2로터의 2자유도 평진계 자기동기화 해석 및 실험 확인. 세부 수치(180도, 80%, 3%)는 전문 확인 전까지 보류하고 **E2**로 보존.

---

### [Row 7] University of Tokyo — Sugita / Yoshioka 행
- **DOI:** `10.1016/j.cirp.2023.04.012`
- **CSV 기재 제목:** In-process thermal error compensation and dynamic cutting force monitoring for five-axis machining centers (45 μm -> 12 μm)
- **실제 ScienceDirect 메타데이터:**
  - 공식 제목: *Wide-bandwidth cutting force monitoring via motor current and accelerometer signals*
  - 실제 저자: T. Bergs, et al. (독일 RWTH Aachen 대학교 연구팀)
  - 저널: *CIRP Annals - Manufacturing Technology*, Vol.72, No.1, pp. 317–320, 2023.
- **판정:** **MISMATCH (DISCREDITED / QUARANTINE)**
- **결과:** 도쿄대 스기타/요시오카 교수의 논문이 아니라, 독일 Bergs 교수 연구팀의 절삭력 모니터링 논문 DOI가 잘못 할당됨.
- **조치:** **QUARANTINE**. 인용 및 검증 세트에서 즉시 배제.

---

### [Row 8] Kyoto University — Kono Lab 행
- **DOI:** `10.1016/j.precisioneng.2023.08.005`
- **CSV 기재 제목:** Evaluation and compensation of geometric and thermal errors in rotary axes... using tracking interferometer (0.5 arcsec, 65% 개선)
- **실제 ScienceDirect 메타데이터:**
  - 공식 제목: *Efficient sampling method based on co-kriging for free-form surface measurement*
  - 실제 저자: Y. Liu, et al.
  - 저널: *Precision Engineering*, Vol.84, pp. 12–24, 2023.
- **판정:** **MISMATCH (DISCREDITED / QUARANTINE)**
- **결과:** 교토대 코노 교수의 회전축 오차 보정 연구가 아니라, 자유곡면 측정용 코크리깅 샘플링 기법 논문 DOI가 잘못 연결됨.
- **조치:** **QUARANTINE**. 검증 세트에서 즉시 배제.

---

### [Row 9] Nagoya University — Shamoto / Suzuki 행
- **DOI:** `10.1016/j.ijmachtools.2023.104050`
- **CSV 기재 제목:** Chatter vibration suppression in thin-walled milling using variable pitch tools... (2.4배)
- **실제 ScienceDirect 메타데이터:**
  - 공식 제목: *Investigation of the grain deformation to orthogonal cutting process of the textured Alloy 718 fabricated by laser powder bed fusion*
  - 실제 저자: Lingshan Li, Hao Chen, Zhirong Liao, Yingchun Yang, David Axinte (영국 노팅엄 대학교 연구팀)
  - 저널: *International Journal of Machine Tools and Manufacture*, Vol.190, 104050, 2023.
- **판정:** **MISMATCH (DISCREDITED / QUARANTINE)**
- **결과:** 나고야대 샤모토/스즈키 교수의 가변 피치 채터 억제 논문이 아니라, 영국 노팅엄대 Axinte 교수팀의 적층제조 합금 718 절삭 입내 변형 논문 DOI가 잘못 연결됨.
- **조치:** **QUARANTINE**. 검증 세트에서 즉시 배제.

---

## 3. 연구실 적합성과 논문 검증의 엄격한 분리 원칙

이번 감사를 통해 확인된 가장 중요한 교훈은 다음과 같습니다:
1. **연구실의 존재 및 연구 주제 적합성(B축)**과 **개별 논문 서지/수치의 무결성(C축)**은 완전히 별개의 명제입니다.
   - 도요하시 기과대 Machine Dynamics Lab(Kawamura/Tajiri)이나 도쿄농공대 Yamato 연구실은 **공식 연구실 홈페이지 및 KAKEN 과제(2024~2028)를 통해 공작기계·진동·동역학 연구를 활발히 수행 중임이 100% 실증**되었습니다.
   - 그러나 해당 연구실을 설명하는 과정에서 잘못된 DOI가 링크되었거나, 초록 이상의 수치가 과장된 행들은 엄격히 격리되어야 합니다.
2. 향후 연구계획서 작성 및 교수 사전 컨택 시에는 **반드시 본 검증 오버레이 보고서에서 MATCH/REWRITTEN으로 통과된 4개 연구 및 KAKEN 공식 프로젝트명**만을 공식 레퍼런스로 활용해야 합니다.
