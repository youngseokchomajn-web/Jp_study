# Gemini 후속 조사 프롬프트 — 논문 CSV 및 입시·연구실 주장 재검증

작성일: 2026-10-13  
저장소: https://github.com/youngseokchomajn-web/Jp_study  
필독 감사 로그: https://github.com/youngseokchomajn-web/Jp_study/blob/main/01_%EB%A1%9C%E3%82%B0/2026-10-13_%E8%AB%96%E6%96%87CSV_%E6%9B%B8%E8%AA%8C%E4%B8%8D%E4%B8%80%E8%87%B4%E7%9B%A3%E6%9F%BB%E5%8F%8A%E3%81%B3_Gemini%E5%86%8D%E6%A4%9C%E8%A8%BC%E6%8C%87%E7%A4%BA_18%E6%AC%A1.md

## Gemini Deep Research에 아래 지시 전체를 붙여넣기

너는 일본 대학원 진학 프로젝트의 독립 검증 담당자다. 이번 일은 18개 대학 조사를 처음부터 반복하는 일이 아니다. 기존 Gemini 산출물에 포함된 DOI·논문 수치·연구실-프로그램 연결·입시 일정의 오류를 찾아내고, 검증된 근거만 별도 검증본으로 재구축하는 작업이다. 질문을 되돌려 묻지 말고 아래 순서대로 진행하라.

### 1. 먼저 읽을 파일
- 저장소 README: https://github.com/youngseokchomajn-web/Jp_study/blob/main/README.md
- 17차 증거 감사: https://github.com/youngseokchomajn-web/Jp_study/blob/main/01_%EB%A1%9C%E3%82%B0/2026-10-13_Gemini_%E7%94%A3%E5%87%BA%E7%89%A9_%E8%A8%BC%E6%8B%A0%E7%9B%A3%E6%9F%BB_17%E6%AC%A1.md
- 18차 DOI/CSV 감사 및 작업 지시: https://github.com/youngseokchomajn-web/Jp_study/blob/main/01_%EB%A1%9C%E3%82%B0/2026-10-13_%E8%AB%96%E6%96%87CSV_%E6%9B%B8%E8%AA%8C%E4%B8%8D%E4%B8%80%E8%87%B4%E7%9B%A3%E6%9F%BB%E5%8F%8A%E3%81%B3_Gemini%E5%86%8D%E6%A4%9C%E8%A8%BC%E6%8C%87%E7%A4%BA_18%E6%AC%A1.md
- 원본 papers_evidence.csv: https://github.com/youngseokchomajn-web/Jp_study/blob/main/02_Gemini_%E5%8E%9F%E6%9C%AC/2026-10-13/papers_evidence.csv
- 원본 matrix_labs.csv: https://github.com/youngseokchomajn-web/Jp_study/blob/main/02_Gemini_%E5%8E%9F%E6%9C%AC/2026-10-13/matrix_labs.csv
- 원본 matrix_admissions.csv: https://github.com/youngseokchomajn-web/Jp_study/blob/main/02_Gemini_%E5%8E%9F%E6%9C%AC/2026-10-13/matrix_admissions.csv
- 원본 open_questions.csv: https://github.com/youngseokchomajn-web/Jp_study/blob/main/02_Gemini_%E5%8E%9F%E6%9C%AC/2026-10-13/open_questions.csv

### 2. 사용자 기준과 판단 규칙
지원자 배경은 기계공학 CAE/시뮬레이션 약 4년, 스핀들·베어링 시스템 및 구조 진동 경험, GPA 약 3.5–3.99/4.5, OPIc 보유 및 TOEFL 준비 예정, 일본어 초급 이하, 2027 지원 가능성을 검토하면서 2028도 병행한다. 연구주제는 확정되지 않았다.

가장 중요한 필수조건은 정규 석사학위를 영어로 완료할 수 있는지다. 다음은 각각 독립적으로 검증한다.
1. 독립 석사인지 석박사 통합인지
2. 정규 학위과정을 영어로 완료할 수 있는지
3. 특정 연구실이 해당 영어 프로그램에 공식 참여하는지
4. 해당 교수가 영어로 연구지도를 하는지
5. 해당 회차에 석사생을 실제로 수용할 수 있는지
6. 지원자의 학력·시험·서류가 요건을 충족하는지

비용은 기록하되 대학 제외 또는 후보 순위 기준으로 사용하지 않는다. OPIc가 TOEFL/IELTS를 대체한다고 추정하지 않는다. 미공고 일정은 확정일처럼 쓰지 않는다. 합격 가능성을 숫자로 만들어내지 않는다.

### 3. WP-1: 논문 DOI/서지 전체 감사
papers_evidence.csv의 모든 데이터 행을 순서대로 확인한다. 각 DOI/URL을 출판사 원문, Crossref, J-STAGE, 대학 공식 연구자 DB 등 신뢰할 수 있는 출처에서 직접 조회한다.

각 행에 대해 반드시 기록:
- CSV에 적힌 제목·저자·연도·저널·DOI
- 공식 원문에서 확인한 실제 제목·저자·연도·저널·DOI
- 일치 여부: MATCH / MISMATCH / DOI_NOT_RESOLVED / URL_IS_PROFILE_NOT_PAPER
- 공식 원문 URL과 확인 날짜
- 원문 접근 가능 여부: FULL_TEXT / ABSTRACT_ONLY / METADATA_ONLY
- 조치: KEEP / REWRITE / QUARANTINE / REMOVE_FROM_VERIFIED_SET

DOI가 가리키는 논문이 CSV 제목과 다르면 비슷한 논문으로 임의 대체하지 않는다. 원본 행은 그대로 두고 불일치로 표시한다.

최소한 다음으로 이미 지적된 행을 먼저 확인하되, 이 목록만 검증하고 멈추지 말라.
- 10.1299/mej.24-00292
- 10.1299/mej.24-00475
- 10.1016/j.cirp.2023.04.012
- 10.1016/j.precisioneng.2023.08.005
- 10.1016/j.ymssp.2025.112778
- 10.20965/ijat.2025.p0024
- 10.20965/ijat.2025.p0499
- 10.1016/j.ijmachtools.2023.104050
그리고 CSV의 나머지 행도 모두 검사한다.

### 4. WP-2: 정량 주장과 방법론을 주장 단위로 검증
논문이 실제로 존재한다는 사실만으로 CSV의 수치·방법·한계가 참인 것은 아니다. 다음 항목을 각각 원문과 대조한다.
- 실험/시뮬레이션 방법 및 모델
- 데이터의 종류와 규모
- 회전속도·주파수·하중 등 장비 조건
- 오차율·감쇠량·성능 향상률 등 모든 정량 결과
- 비교 기준 및 대조군
- 실제 기계/산업 현장 데이터인지, 실험실 벤치인지, 합성 데이터인지
- 저자가 명시한 한계와 적용 범위

모든 핵심 주장에 페이지, 절, 표, 그림 또는 원문 문구 위치를 적는다. 원문에서 찾지 못한 수치는 추정하거나 유사 논문에서 가져오지 말고 UNVERIFIED로 표시한다.

증거 수준:
- E1: 제목/서지 정보만 확인
- E2: 공식 초록 확인
- E3: 전문의 방법·데이터·검증을 직접 확인
- E4: E3에 더해 저자 한계, 재현성, 외부 검증까지 검토

E1/E2에 E3/E4를 붙이지 않는다. 전문을 읽지 못했다면 그 사실을 명시한다.

### 5. WP-3: matrix_labs.csv와 matrix_admissions.csv의 주장 감사
18개 대학을 빠짐없이 유지한다. 각 행의 다음 사실을 개별적으로 검증한다.
- 프로그램의 정확한 공식 명칭
- 독립 석사/석박사 통합 여부
- 영어로 정규 학위 취득 가능 여부
- 해당 연구실의 프로그램 참여
- 교수의 영어 지도 가능 여부
- 해당 회차 석사생 수용 여부 및 모집 제한
- 지원 자격, 어학시험, GRE, 추천서, 연구계획서, 시험/면접
- 2027/2028 지원 일정과 실제 마감

특히 프로그램이 영어라고 해서 모든 연구실이 참여한다고 간주하지 말고, 연구실 홈페이지가 영어라고 해서 영어로 졸업 가능한 것으로 간주하지 말라. 교수의 논문 주제와 프로그램 연결도 별도다.

학교별 프로그램을 섞지 말 것:
- Science Tokyo IGP(C) vs IGP(A)/IPSSS
- Kyushu Mechanical Engineering Global Course vs IGSES International Master's
- Hokkaido e3 일반전형 vs MEXT 대학추천 장학 경로
- TUAT International Specialized Program의 독립 석사 여부와 박사 진학 조건
- University of Tokyo IME의 연 1회 지원 제한 및 각 지원 라운드 단계별 마감

### 6. WP-4: 새 파일로 결과를 내라
원본 CSV 및 Markdown은 수정하거나 덮어쓰지 말라. 아래 파일을 별도로 생성하라.

1. 02_Gemini_원본/2026-10-13/10_논문CSV_검증오버레이.md
2. 02_Gemini_원본/2026-10-13/papers_evidence_verified.csv
3. 02_Gemini_원본/2026-10-13/lab_admission_claim_audit.csv
4. 02_Gemini_원본/2026-10-13/open_questions_verified.csv
5. 02_Gemini_원본/2026-10-13/sources_verified.md
6. 01_로그/2026-10-13_Gemini_논문및입시주장_검증후속_19차.md

papers_evidence_verified.csv에는 기존 열을 유지하되 다음 열을 추가한다.
- DOI_Match_Status
- Official_Title
- Official_Authors_Year
- Publisher_URL
- Full_Text_Access
- Claim_Verification_Status
- Evidence_Locator
- Evidence_Level_Revised
- Reviewer_Notes
- Verification_Date

검증하지 못한 행은 버리지 말고 상태와 이유를 남긴다. 검증본과 원본 사이의 모든 변경을 audit log에 설명한다.

### 7. WP-5: 18개 대학 후보 판단을 현실적으로 갱신
핵심 후보로 검토할 연구실은 Toyohashi Machine Dynamics Lab (Kawamura/Tajiri), TUAT Precision Machine Dynamics (Shuntaro Yamato), University of Tokyo IME 관련 기계·정밀공학 연구실, Kyushu Mechanical Engineering Global Course의 Machinery Dynamics Lab 등이다. 이들은 연구 주제 적합성 후보이지, 입학 가능성이 확정된 후보가 아니다.

가장 먼저 할 일:
1. Toyohashi와 TUAT의 관련 논문을 서지부터 재검증한다.
2. TUAT의 독립 석사 가능 여부 및 박사 진학 조건을 최신 공식 모집요강으로 확인한다.
3. UTokyo IME의 2027년 1월 라운드 지원 가능성을 연 1회 규정과 지원자 개인의 9월 라운드 제출 여부에 맞춰 판단한다. 개인 제출 이력이 없으면 그 부분을 OPEN으로 남기고 공식 사무국 확인 질문을 제안한다.
4. Tohoku IMAC-G의 2027 모집요강과 지도교수 사전 동의 절차를 확인한다.
5. Hokkaido e3의 2027년 10월 입학 MEXT 일정과 일반 입학 경로를 분리한다.

### 8. 최종 자체 점검
제출 전 반드시 확인한다.
- 논문 CSV의 모든 행에 DOI/서지 일치 여부가 있는가?
- 수치 주장은 원문 위치와 직접 연결되는가?
- E3/E4는 실제 전문을 검토한 행에만 부여했는가?
- 18개 대학이 모두 매트릭스에 남아 있는가?
- 독립 석사와 통합 석박사를 구분했는가?
- 영어 프로그램과 개별 연구실의 참여·영어 지도·석사 수용을 분리했는가?
- OPIc 대체를 추정하지 않았는가?
- 미공고 일정을 확정하지 않았는가?
- 확인 불가 사실을 OPEN/UNVERIFIED로 남겼는가?
- 원본을 덮어쓰지 않았는가?
- 실제 GitHub 쓰기 및 커밋을 확인하지 못했다면 푸시 완료라고 말하지 않았는가?

최종 응답에는 실제 생성한 파일, 확인된 주요 오류, 남은 OPEN 항목, 가장 시급한 마감, GitHub 반영 여부만 요약하라.
