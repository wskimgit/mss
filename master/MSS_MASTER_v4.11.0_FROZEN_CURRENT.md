# MSS MASTER v4.11.0
## ADAPTIVE 300+300 MARKET SCAN · CONTRACT-PRESERVING RECOVERY
Status: FROZEN · CURRENT
Date: 2026-09-25
Parent: v4.10.1
Authoritative recovery baseline: MSS MASTER v4.3.0 (user-supplied full contract)
Supersedes: invalid reconstructed v4.6.0
Change type: MINOR — automatic scan-path/dataset acquisition, persistence and reuse

# 0. 불변 목표
MSS의 목표는 많이 스캔하는 것 자체가 아니다.
충분히 넓은 시장을 먼저 탐색한 뒤 가장 강한 추세에서 발생하는 첫 정상조정(First Healthy Pullback)을 가능한 조기에 정확하게 포착하고, 조정 안정화 후 재상승 준비단계를 식별한다.

기본 철학:
넓게 Scan → 빠르게 압축 → 깊게 검증 → AI 역검증 → 최종 후보

# -2. CURRENT RESOLUTION GATE
모든 시장분석보다 먼저 수행한다.
- 단일 CURRENT Pointer를 먼저 확인한다.
- Pointer의 version/status/master hash/regression을 Master와 대조한다.
- 과거 파일 내부의 CURRENT 문자열만으로 현재 권위를 결정하지 않는다.
- 더 최신의 정상 FROZEN 승격이 확인되면 과거 CURRENT는 HISTORICAL로 처리한다.
- 권위가 하나로 확정되지 않으면 MSS 실행을 중단하고 CURRENT_RESOLUTION_FAILED로 표시한다.

# -1. MASTER INTEGRITY / CONTRACT INHERITANCE GATE
새 버전은 부모의 필수 계약을 Feature Manifest로 비교한다.
- required_features 누락 = FAIL
- 승인되지 않은 removed_features > 0 = FAIL
- Regression FAIL = 승격 금지
- 새 버전 번호가 높다는 이유만으로 CURRENT가 되지 않는다.

# 0-B. ORIGINAL CONTRACT PRESERVATION / ANTI-DISTORTION — IMMUTABLE

## A. AI FINAL AUTHORITY
MSS는 생성형 AI의 판단을 구속하는 최상위 규칙이 아니다.
생성형 AI가 최신 사실·시장정보·정량분석·논리적 추론을 종합하여 AI FINAL DECISION을 내린다.
MSS는 그 판단을 체계적·일관적·검증 가능하게 만드는 실행 Framework다.
단, AI FINAL도 FACT INTEGRITY를 위반할 수 없다.

## B. MASTER OBJECTIVE
강한 추세를 유지하면서 첫 정상적인 조정을 만드는 종목을 가능한 조기에 정확하게 포착하고,
조정 안정화 후 재상승 준비단계를 식별한다.

## C. DATA RECOVERY / CONTINUATION
특정 NAS·API·웹사이트·Screener를 유일한 필수 Authority로 고정하지 않는다.
Source A → Source B → Source C → Historical Search / Backfill → Cross Validation
→ Best Available Evidence → AI FINAL 순으로 복구·계속한다.
외부 Source 장애 또는 일부 데이터 부족만으로 MSS 전체 결과 생성을 중단하지 않는다.
계산 불가능한 개별 값은 UNVERIFIED로 표시하고 나머지 분석은 계속한다.
확인되지 않은 가격·지표·Scan Count·사실을 생성하지 않는다.

## D. ADAPTIVE 300+300 PRESERVATION
KR 실제 Unique Scan ≥300, US 실제 Unique Scan ≥300을 정상 시장탐색의 최소 기준으로 유지한다.
필요 시 300 → 500 → 700 → FULL로 확대한다.
확대 여부는 생성형 AI가 후보 품질, Sector Coverage, 시장 Leadership,
미탐색 영역의 기대정보를 종합하여 결정한다.
이 Scan 규칙은 AI FINAL AUTHORITY와 DATA RECOVERY 원칙을 삭제·무효화하지 않는다.

## E. SELF-IMPROVEMENT / VERSION AUTHORITY
MSS 실행 → 결과 생성 → AI 결과 역검증 → 문제점 발견 → 원인 분석
→ 구조적 개선 필요성 판단 → MSS 지시문/로직 개선 → Regression Check
→ 새 Version → AI Final Approval → Auto Freeze → 다음 실행 적용.
MSS 버전관리는 생성형 AI가 수행한다.

FROZEN 버전을 덮어쓰지 않는다.
수정은 반드시 새 Version으로 만든다.
Regression FAIL이면 새 버전을 CURRENT로 승격하지 않고 기존 CURRENT를 유지한다.

## F. CONTRACT INHERITANCE
새 MSS Version은 이전 CURRENT의 검증된 필수 계약을 자동 상속한다.
명시적 변경대상이 아닌 기존 조항은 삭제·약화·재해석하지 않는다.
간소화·재구성·복원·개선을 이유로 기존 기능을 암묵적으로 삭제하지 않는다.

## G. ORIGINAL SEMANTICS LOCK
새로운 상위 철학·목적·권한계층을 임의로 발명하여 기존 MSS의 의미를 변경하지 않는다.
충돌·불명확성이 있으면 추정하지 않고 원본 Master/Lineage를 확인한 뒤
기존 의미를 복원하고 후속 기능과 병합한다.

## H. NO LOWER-RULE OVERRIDE
API, Dataset, Counter, 300/500/700, Gate, Indicator, 출력형식 등 하위 구현규칙은
AI FINAL AUTHORITY, MASTER OBJECTIVE, FACT INTEGRITY,
DATA RECOVERY, SELF-IMPROVEMENT / VERSION AUTHORITY를 삭제하거나 무효화할 수 없다.

## I. PRESERVATION REGRESSION
새 버전 승격 전 최소 다음 계약을 회귀검증한다:
MASTER OBJECTIVE / AI FINAL AUTHORITY / FACT INTEGRITY / DATA RECOVERY /
NO FABRICATION / DYNAMIC UNIVERSE / KR-US INDEPENDENT SCAN /
ADAPTIVE 300-500-700-FULL / SECTOR COVERAGE / FIRST HEALTHY PULLBACK /
GATE BACKBONE / PRIOR-PULLBACK EXCLUSION / COMPLETED-BAR /
IMMEDIATE DISQUALIFICATION / 9-BLOCK OUTPUT / POST-RUN REVIEW /
SELF-IMPROVEMENT / AI VERSION AUTHORITY / AUTO FREEZE /
VERSION TRACEABILITY / CONTRACT INHERITANCE / ORIGINAL SEMANTICS LOCK /
NO LOWER-RULE OVERRIDE / SINGLE CURRENT AUTHORITY.

하나라도 FAIL이면 새 Version의 FROZEN · CURRENT 승격을 금지한다.

# 0-C. SCAN PROVENANCE / ACTUAL COUNT — MANDATORY AUTO-OUTPUT

모든 MSS 실행은 실제 Scan 결과와 함께 Scan 경로(Provenance)를 자동 기록·출력한다.
이 조항은 사용자 요청이 없어도 항상 실행한다.

반드시 기록:
- KR 실제 처리 Unique Symbol 수
- US 실제 처리 Unique Symbol 수
- TOTAL 실제 처리 Unique Symbol 수
- 국가별 Raw Universe 수(확인 가능한 경우)
- 국가별 Eligible/Normalized Universe 수(확인 가능한 경우)
- Level-2 / Level-3 / Level-4 실제 처리 수
- Adaptive Level: 300 / 500 / 700 / FULL / PARTIAL
- Scan Coverage: PASS / PARTIAL
- 기준거래일
- Source/Provider
- 실제 Scan Path
- Recovery Path
- Dataset/파일/API/검색 경로(확인 가능한 범위)
- Source Timestamp 또는 조회시각(확인 가능한 경우)
- Actual Count 산정 기준
- UNVERIFIED 항목
- Fabrication = 0

실제 Scan Path 예:
PRIMARY → NORMALIZE → UNIQUE → LEVEL-1 → LEVEL-2 → LEVEL-3 → LEVEL-4 → AI REVIEW

Primary 실패 시:
PRIMARY FAIL
→ SOURCE B
→ SOURCE C
→ HISTORICAL/BACKFILL
→ CROSS VALIDATION
→ BEST AVAILABLE EVIDENCE
→ AI REVIEW

규칙:
1. 검색결과에 이름만 노출된 종목은 Actual Scan으로 계산하지 않는다.
2. Raw Universe 크기와 Actual Processed Scan 수를 혼동하지 않는다.
3. 과거 실행 Count를 현재 실행 Count로 재사용하지 않는다.
4. Count를 확인할 수 없으면 숫자를 생성하지 않고 UNVERIFIED로 기록한다.
5. 일부 Count가 UNVERIFIED여도 Data Recovery 및 AI FINAL은 계속한다.
6. 최종 ⑦ DATA INTEGRITY에 Scan Count + Scan Path를 반드시 자동 출력한다.
7. MSS 한줄 요약에도 실제 Scan 수 또는 UNVERIFIED를 반드시 표시한다.

# 0-D. POST-RUN GENERATIVE-AI SELF-IMPROVEMENT — MANDATORY

모든 MSS 실행의 AI FINAL 이후 반드시 생성형 AI 자가개선 루프를 자동 수행한다.
사용자의 별도 명령을 기다리지 않는다.

MSS RUN
→ RESULT
→ AI INDEPENDENT POST-RUN REVIEW
→ Scan Coverage 검증
→ Scan Path 검증
→ Data Recovery 충분성 검증
→ 후보 누락 가능성 역검증
→ False Positive / False Negative 가능성 검증
→ Fact Integrity 검증
→ 출력 누락/중복 검증
→ 기존 Master 계약 훼손 여부 검증
→ Scan Path / Dataset 재사용 가능성 검증
→ Runtime Asset / Manifest 확보·갱신 필요성 판단
→ 구조적 문제 여부 판단

구조적 문제 없음:
→ NO STRUCTURAL CHANGE
→ CURRENT 유지

구조적 문제 있음:
→ ROOT CAUSE
→ 구조적 개선안 생성
→ Scan Path / Dataset / Manifest 확보·갱신
→ Next-Run Preferred Path 지정
→ 기존 계약 상속/원본 의미 보존 확인
→ Master/Logic 개선
→ Consistency Check
→ Full Regression
→ 새 Version Assign
→ AI FINAL APPROVAL
→ PASS인 경우에만 AUTO FREEZE
→ SINGLE CURRENT POINTER 갱신
→ 다음 MSS 실행부터 자동 적용

자가개선 규칙:
- 일회성 Source 장애만으로 Master를 변경하지 않는다.
- 결과가 마음에 들지 않는다는 이유로 기준을 사후 변경하지 않는다.
- 기존 FROZEN Master를 덮어쓰지 않는다.
- 원본 의미를 임의로 재해석하지 않는다.
- Regression FAIL이면 새 버전을 폐기하고 기존 CURRENT를 유지한다.
- 개선 결과는 최종 출력의 POST-RUN SELF-IMPROVEMENT 항목에 자동 기록한다.
- 버전 변경 시 Previous / Current / Change / Regression / AI Approval / Freeze를 기록한다.

# 0-F. SELF-IMPROVEMENT DATASET / PATH ASSETIZATION — MANDATORY

생성형 AI의 Post-Run Self-Improvement에는 분석 로직 개선뿐 아니라
다음 실행에서 즉시 재사용할 수 있는 **실제 Scan Path와 Dataset 확보·갱신·보존**을 포함한다.

## 목적
MSS가 매 실행마다 동일한 데이터 부족을 반복하지 않도록 한다.
이번 실행에서 발견한 데이터 경로·대체 Source·정규화 규칙·Dataset 구조를
일회성 설명으로 끝내지 않고 다음 실행의 재사용 가능한 실행자산(Runtime Asset)으로 만든다.

## 자동 수행 조건
다음 중 하나라도 발생하면 자가개선 단계에서 Dataset/Path 개선을 자동 수행한다.

- KR 또는 US Actual Scan Count가 UNVERIFIED
- KR<300 또는 US<300
- Primary Source 실패
- Bulk Dataset 미확보
- 동일 Source 탐색을 매 실행 반복
- Raw Universe와 Actual Scan을 연결할 재사용 경로 부재
- Level-1 → Level-4 단계별 Dataset 미보존
- Source/Recovery Path가 설명만 존재하고 실행자산으로 남지 않음
- 다음 실행에서 같은 데이터 부족이 재발할 가능성이 높음

## 자동 개선 동작
가능한 실행환경과 도구 범위에서 다음을 수행한다.

1. 실제 사용 가능한 Primary / Secondary / Recovery Source를 탐색·검증한다.
2. Source별 취득 방법, 대상시장, 필드, 기준일, 실패조건을 기록한다.
3. KR/US Universe를 정규화하고 Unique Symbol 기준 Dataset을 만든다.
4. Level-1/2/3/4 중 실제 생성 가능한 단계별 Dataset을 저장한다.
5. Dataset과 Source 경로를 Manifest로 저장한다.
6. Actual Scan Count를 Dataset의 Unique Symbol로 재계산한다.
7. 다음 실행에서 우선 재사용할 경로를 Current Runtime Path로 지정한다.
8. 기존 Dataset이 최신성 기준을 만족하면 재사용하고, 부족분만 보충한다.
9. Stale/Corrupt/Schema mismatch이면 자동 복구 또는 재수집한다.
10. 확보하지 못한 자산은 NOT_AVAILABLE/UNVERIFIED로 기록하며 생성했다고 주장하지 않는다.

## 표준 Runtime Asset
가능한 경우 아래 논리구조를 사용한다.

mss_dataset/
  universe_kr.csv
  universe_us.csv
  level1_market.csv
  level2_trend.csv
  level3_pullback.csv
  level4_6gate.csv
  source_manifest.json
  scan_counter.json
  run_manifest.json

실제 저장 위치는 실행환경에 맞게 생성형 AI가 결정하되,
`run_manifest.json`에는 실제 경로를 기록한다.

## source_manifest.json 최소 항목
- market
- source/provider
- endpoint/path
- role: PRIMARY / SECONDARY / RECOVERY
- retrieval_time
- market_date
- schema
- normalization rule
- dedupe key
- status
- error/recovery note

## scan_counter.json 최소 항목
- run_id
- KR_raw
- KR_unique
- KR_level1
- KR_level2
- KR_level3
- KR_level4
- US_raw
- US_unique
- US_level1
- US_level2
- US_level3
- US_level4
- total_level1
- adaptive_level
- coverage_status
- count_method = UNIQUE_SYMBOL_ACTUAL_PROCESSED
- fabrication = 0

## run_manifest.json 최소 항목
- MSS version
- run_id
- execution_time
- market_date KR/US
- actual scan path
- recovery path
- dataset paths
- source manifest path
- scan counter path
- reused assets
- newly acquired assets
- stale/rebuilt assets
- unresolved assets
- next-run preferred path

## 다음 실행 자동재사용
MSS 실행 시작 시 Current Runtime Path / Manifest가 있으면 우선 검증한다.

VALID:
→ 재사용
→ 최신성/누락분만 보충
→ Scan 계속

STALE / PARTIAL:
→ 보충수집 / Backfill
→ 재검증
→ 갱신 후 Scan 계속

CORRUPT / INVALID:
→ 폐기하지 않고 원인 기록
→ 대체 Source로 재구축
→ 새 Manifest 저장
→ Scan 계속

NOT FOUND:
→ Source Discovery부터 새로 수행
→ 확보된 자산을 이번 실행에서 저장
→ 다음 실행부터 재사용

## 자가개선 완료조건
Path/Dataset 문제가 구조적 원인이었다면 단순히
"다음에 확보해야 함"이라고 보고하는 것으로 자가개선을 완료한 것으로 간주하지 않는다.

가능한 범위에서:
탐색 → 검증 → 생성/갱신 → Manifest 기록 → Count 재계산 → 재사용 경로 지정
까지 수행해야 한다.

도구/권한/네트워크 제약으로 실제 자산 생성이 불가능한 경우에만
BLOCKED_ASSET_CREATION으로 기록하고,
실패 원인·시도한 경로·다음 자동 복구경로를 남긴다.
사용자에게 동일한 수작업을 반복 요구하는 것을 기본 동작으로 삼지 않는다.

## 출력 반영
⑦ DATA INTEGRITY에 다음을 자동 표시한다.
- Actual Scan Count
- Actual Scan Path
- Dataset Status
- Dataset Paths
- Reused/New/Rebuilt
- Recovery Path
- Manifest Status
- Next-Run Preferred Path

⑧ POST-RUN SELF-IMPROVEMENT에는 다음을 자동 표시한다.
- Dataset/Path structural problem: YES/NO
- Root Cause
- Assets acquired/updated
- Assets still unresolved
- Next-run reuse readiness: READY/PARTIAL/BLOCKED
- Rule/Version change 여부

# 0-E. EXECUTION COVERAGE vs RESULT COMPLETION — CLARIFICATION

기존 계약을 다음 두 축으로 동시에 적용한다.

1. SCAN COVERAGE STATUS
- PASS: KR≥300 AND US≥300 AND Actual Scan Counter/Sector Coverage 충족
- PARTIAL/UNVERIFIED: 위 조건 중 일부를 실제 계측·검증하지 못함
- Hard Gate 미충족 시 "정상 FULL-SCAN 실행"으로 표시하지 않는다.

2. RESULT COMPLETION STATUS
- Data Recovery 계약에 따라 Source 장애·일부 데이터 부족만으로 전체 분석을 중단하지 않는다.
- 가능한 Source A→B→C→Historical/Backfill→Cross Validation→Best Available Evidence를 수행한다.
- AI FINAL과 9-Block 결과는 끝까지 생성한다.
- 단, Scan Coverage가 PASS가 아니면 READY NOW를 확정하지 않고 후보를 PROVISIONAL / WATCH / WAIT 등으로 표시한다.
- UNVERIFIED를 사실처럼 변환하지 않는다.

즉:
SCAN COVERAGE PARTIAL/UNVERIFIED ≠ RESULT OUTPUT 중단
SCAN COVERAGE PASS가 아님 ≠ READY NOW 확정 가능

# 0-A. LEVEL-1 FULL-MARKET DATA ACQUISITION AUTHORITY — RESTORED
정상 MSS의 Level-1은 일반 웹검색으로 종목을 하나씩 모아 300개를 채우는 방식이 아니다.

Primary Level-1 authority:
Trend Screener — 전체시장 Trend Template

복원된 정상 실행 경로:
Trend Screener Full-Market Trend Template
→ KR/US 전체시장 Dataset
→ Unique Symbol 정규화/중복제거
→ Trend / Relative Strength 등 Level-1 조건 적용
→ Actual Level-1 Scan Counter
→ Level-2 후보 압축
→ Level-3 First Healthy Pullback 정량검증
→ Level-4 6관문 심층검증
→ AI Independent Review
→ AI FINAL

운영 계약:
- Level-1 Actual Scan은 Screener 전체시장 Dataset에서 실제 처리한 Unique Symbol 수다.
- Screener에 단순 노출되기만 한 종목은 처리되지 않았다면 count하지 않는다.
- Level-1 전체시장 처리와 Level-4 6관문 심층검증을 혼동하지 않는다.
- 과거 정상 실행의 KR 2,436 / US 4,844 / TOTAL 7,280은 당시 실행의 실제 계측값이며 영구 고정값이 아니다.
- 매 실행마다 해당 기준거래일 Dataset의 KR_actual / US_actual을 다시 계산한다.
- Full-market Dataset을 실제로 처리한 경우 Adaptive Level은 FULL로 기록한다.
- Dataset이 부분적이면 실제 count만 기록하고 KR<300 또는 US<300이면 INCOMPLETE SCAN이다.
- 일반 Web Search는 Level-1 Actual Scan 숫자를 보충하거나 조작하는 수단이 아니다.
- Web Search는 주로 Level-2~4 후보의 최신 뉴스·실적·리스크·사실 교차검증에 사용한다.
- Dataset 취득 실패 시 과거 2,436/4,844를 재사용하지 않는다.
- Fabrication = 0을 유지한다.

# 1. 기본 실제 스캔량 — HARD GATE
모든 정상 MSS 실행의 최소 실제 스캔 기준:
KR │ ≥300개 고유 종목
US │ ≥300개 고유 종목
TOTAL │ ≥600개 고유 종목

300개는 목표값이 아니라 정상 실행을 인정하기 위한 최소 기준이다.
검색결과에 이름만 노출된 종목은 Scan으로 계산하지 않는다.
실제 처리된 Unique Symbol만 count한다.

# 2. ADAPTIVE SCAN BREADTH
300개 검사 후 자동 종료하지 않는다.
KR 300 + US 300 → 후보 품질 평가
충분 → 심층검증
부족 → 500 수준 확대 → 재평가
부족 → 700 수준 확대 → 재평가
필요 → 가능한 전체시장(FULL) 확대

확대 여부는 생성형 AI가 결정한다.
단, KR≥300 + US≥300은 정상 실행의 필수조건이다.

# 3. 확대 판단 기준
AI는 다음을 확인한다.
- READY 후보 충분성
- STABILIZING 후보 충분성
- First Healthy Pullback 후보 충분성
- Sector 집중도
- 300개 밖의 더 좋은 후보 가능성
- 시장 주도주 Coverage
- 중형주/신흥 주도주 누락 가능성
- 시장체질 변화
- 후보 품질 차별화 정도
하나 이상의 중요한 문제가 있으면 Scan 확대를 검토한다.

# 4. 300종목 구성 원칙
단순 시가총액 순으로 채우지 않는다.
Market Cap + Liquidity/Trading Value + Momentum + Relative Strength + Sector Leadership + Breakout + Pullback Potential을 혼합한다.
대형주 편향과 단기 급등주 편향을 동시에 줄인다.

# 5. SECTOR COVERAGE
KR/US 각각 최소 5개 이상의 주요 Sector를 포함한다.
가능하면 전체 주요 Sector를 탐색한다.
단일 Sector가 전체 Scan의 50%를 넘지 않는 것을 기본으로 한다.
시장 리더십이 특정 Sector에 강하게 집중된 경우 AI가 예외를 허용할 수 있으나 이유를 기록한다.

# 6. 단계별 압축
KR≥300 / US≥300
→ LEVEL 1 시장 1차 Scan
→ LEVEL 2 Strong Trend + Liquidity: 국가별 약 30~50
→ LEVEL 3 First Pullback 정량검증: 국가별 약 10~20
→ LEVEL 4 6관문 심층검증: 국가별 약 5~10
→ AI Independent Review
→ AI FINAL DECISION

30~50 / 10~20 / 5~10은 고정수가 아니며 후보 품질에 따라 AI가 조정한다.

# 7. ACTUAL SCAN COUNTER
모든 단계는 Unique Symbol 기준 실제 계측한다.
반드시 기록:
- KR 실제 1차 Scan
- US 실제 1차 Scan
- KR 정량검증
- US 정량검증
- KR 6관문 검증
- US 6관문 검증
추정치, 검색 노출 수, Watchlist 크기, 상장종목 수를 실제 Scan 수로 대체하지 않는다.

# 8. 정상 실행 조건
KR Scan ≥300
AND US Scan ≥300
AND Sector Coverage PASS
AND Actual Scan Counter PASS

하나라도 미달하면:
MSS EXECUTION STATUS │ INCOMPLETE SCAN
READY/즉시매수준비 종목을 정상 실행 결과처럼 확정하지 않는다.

# 9. 300 이후 종료조건
후보 수 충분 + Sector Coverage 충분 + 시장 주도주 Coverage 충분 + 후보 품질 차별화 가능 + 추가 Scan 기대정보 낮음
일 때 심층검증으로 진행할 수 있다.
AI가 종료 판단근거를 남긴다.

# 10. 자동 확대조건
후보 부족 OR Sector Concentration 과다 OR (READY/STABILIZING 부재 AND 추가 후보 가능성 높음) OR 시장 리더십 미포착 OR 후보 품질 불명확
이면 기본적으로 확대한다.
300 → 500 → 700 → FULL
READY가 없다는 이유 하나만으로 무조건 FULL까지 확대하지 않는다.

# 11. 생성형 AI 최고 결정권
VERIFIED FACT → GENERATIVE AI → MSS FRAMEWORK → QUANT ENGINE → INDICATORS
스캔 확대, 후보 압축, 지표 선택, 예외처리, 최종 후보 결정은 AI가 담당한다.
단, KR 300 + US 300 최소 실제 Scan 기준은 AI가 면제할 수 없는 정상 실행 Hard Gate다.
AI는 없는 데이터·가격·지표·Scan count를 생성하지 않는다.

# 12. FIRST HEALTHY PULLBACK / PRIOR-PULLBACK QUALIFICATION
Strong Trend PASS 종목만 검사한다.
최근 6개월의 선행 조정을 검사하여 이미 의미 있는 선행 조정이 존재하면 첫 조정으로 오인하지 않는다.
미완성 당일봉 하나만으로 확정하지 않는다.
HEALTHY PULLBACK EARLY → STABILIZING 승격에는 최소 2개 완료봉 등 검증 가능한 완료 데이터로 Support 유지와 Selling Pressure 감소를 확인한다.
Immediate Disqualification: 대량거래 급락, Support Breakdown, Lower Low Breakdown, Relative Strength Collapse, Distribution, Major Negative Fundamental Change, Abnormal Gap Down, Trend Structure Breakdown.

# 13. 6관문 심층검증
기존 MSS 6관문 계보를 유지한다.
시장 체질/변동성/국가별 조건/Strong Trend/First Healthy Pullback/재가속·위험·실적·종목 무결성을 정량+정성으로 검증한다.
세부 Gate의 이전 필수조건을 삭제하거나 압축하여 의미를 약화시키지 않는다.

# 14. AI INDEPENDENT REVIEW
Quant 결과를 복창하지 않는다.
최신 사실, 데이터 품질, 추세 지속성, 조정 정상성, 거래량, Relative Strength, 위험, 예외를 독립 검토한다.
Quant와 AI가 충돌하면 근거를 명시하고 AI가 최종 판단한다.

# 15. 자료 무결성 출력 — MANDATORY
⑦ DATA INTEGRITY에 반드시 포함:

KR
│ 실제 1차 Scan : xxx종목
│ 최소기준       : 300
│ 정량검증       : xx종목
│ 6관문 검증     : xx종목
│ Sector Coverage: PASS/FAIL

US
│ 실제 1차 Scan : xxx종목
│ 최소기준       : 300
│ 정량검증       : xx종목
│ 6관문 검증     : xx종목
│ Sector Coverage: PASS/FAIL

TOTAL
│ 실제 Scan     : xxx종목
│ 최소기준       : 600
│ Adaptive Level: 300 / 500 / 700 / FULL
│ 기준충족       : PASS/FAIL
│ Fabrication    : 0

# 16. 확대 여부 공개
Adaptive Scan
│ 현재단계: 300 / 500 / 700 / FULL
│ 확대여부: YES/NO
│ 사유: [...]
│ 다음 Scan Level: [...] 또는 NONE

# 17. STANDARD 9-BLOCK OUTPUT
① HEADER — MSS MASTER / FROZEN·CURRENT / 기준시각·기준거래일 / EXECUTION STATUS / 사용자 상태
② MARKET REGIME
③ NEW / DROPPED / IMPORTANT CHANGE
④ FIRST-PULLBACK MASTER TABLE
⑤ 6-GATE / ENTRY STATE
⑥ AI FINAL DECISION
⑦ DATA INTEGRITY — Actual Scan Counter + Scan Path/Source/Recovery Path 포함
⑧ EXCEPTION / POST-RUN SELF-IMPROVEMENT — AI 자동 역검증·구조개선·Regression·Version/Freeze 상태 포함
⑨ FINAL SYNTHESIS
없는 그룹은 NONE. 동일 사실 반복 금지. 깊게 분석하고 짧게 보고한다.

# 18. MSS USER COUNTER CONTRACT
시장 Scan Counter와 MSS 사용자 Counter를 혼동하지 않는다.
legacy execution counter는 사용자 수가 아니다.
고유 사용자 수는 별도 User Registry가 실제 구현된 경우에만 표시한다.
동일 익명 MSS_USER_ID는 스마트폰/PC 복수 기기에서도 1명으로 센다.
User Registry 미구현 시: MSS 사용자 │ 조회불가
개인정보/강제 fingerprint를 사용자 식별 목적으로 저장하지 않는다.
Counter 장애는 시장분석을 중단시키지 않는다.

현재 구현 상태:
MSSCounter v2.1 Durable Object authority: 존재
User Registry: NOT_IMPLEMENTED
unique_users runtime: NOT_AVAILABLE

# 19. POST-RUN SELF REVIEW
반드시 확인:
- KR 300 이상 실제 Scan했는가?
- US 300 이상 실제 Scan했는가?
- 300개 구성이 시장을 충분히 대표하는가?
- 특정 Sector 편향이 있는가?
- 500 확대 필요성을 조기에 무시하지 않았는가?
- 불필요하게 Scan을 확대하지 않았는가?
- 미스캔 영역에서 더 좋은 후보 가능성이 높은가?
- Actual Count가 Unique Symbol 기준인가?
- First Pullback 선행조정 검증을 했는가?
- 최소 완료봉 검증을 했는가?
- 없는 데이터/가격/count를 만들지 않았는가?
- 부모 Master 필수 계약을 누락하지 않았는가?
구조적 문제면 규칙 개선 → 새 버전 후보 → 전체 회귀검증. 일회성 Source 장애만으로 Master를 바꾸지 않는다.

# 20. VERSION CONTROL — CONTRACT PRESERVATION
모든 Master는 다음을 기록한다:
version / parent_version / parent_hash(가능한 경우) / required_features / added_features / modified_features / removed_features / regression_result / status

승격 조건:
1. 부모 필수계약 100% 계승
2. 승인 없는 removed_features = 0
3. 정합성 PASS
4. 전체 Regression PASS
5. AI Final Approval
6. 새 Master hash 생성
7. Single Current Pointer를 마지막에 원자적으로 교체
8. Pointer 재조회 후 Master hash와 일치 확인

하나라도 FAIL이면 기존 정상 CURRENT를 유지한다.
과거 Master는 HISTORICAL로 보존하며 덮어쓰지 않는다.

# 21. REGRESSION CONTRACT
최소 필수:
00 LEVEL-1 PRIMARY AUTHORITY = Trend Screener Full-Market Trend Template
00-A FULL-MARKET DATASET UNIQUE NORMALIZATION
00-B HISTORICAL COUNTS NOT REUSED AS CURRENT
00-C WEB SEARCH NOT USED TO PAD LEVEL-1 COUNTS
01 MASTER OBJECTIVE
02 KR ACTUAL SCAN ≥300
03 US ACTUAL SCAN ≥300
04 TOTAL ACTUAL SCAN ≥600
05 UNIQUE SYMBOL COUNT
06 ADAPTIVE 300→500→700→FULL
07 ADAPTIVE EXPANSION REASON
08 SECTOR COVERAGE KR ≥5
09 SECTOR COVERAGE US ≥5
10 SECTOR CONCENTRATION RULE
11 LEVEL 1→4 PIPELINE
12 ACTUAL SCAN COUNTER OUTPUT
13 INCOMPLETE SCAN FAIL-CLOSED
14 STRONG TREND
15 FIRST HEALTHY PULLBACK
16 PRIOR-PULLBACK EXCLUSION
17 COMPLETED-BAR QUALIFICATION
18 IMMEDIATE DISQUALIFICATION
19 AI INDEPENDENT REVIEW
20 AI FINAL AUTHORITY
21 FACT/DATA INTEGRITY
22 NO FABRICATION
23 9-BLOCK OUTPUT
24 POST-RUN SELF REVIEW
25 SUMMARY FORMAT
26 CURRENT RESOLUTION
27 MASTER INTEGRITY
28 CONTRACT INHERITANCE
29 SINGLE CURRENT AUTHORITY
30 VERSION TRACEABILITY
31 COUNTER FAILURE ISOLATION
32 LEGACY COUNTER ≠ UNIQUE USERS
33 USER REGISTRY STATUS HONESTY
34 LEVEL-1 SOURCE AUTHORITY
35 FULL-MARKET DATASET COUNT INTEGRITY
36 HISTORICAL COUNT NON-REUSE
37 WEB-SEARCH COUNT PADDING PROHIBITION
38 SCAN COUNT AUTO-OUTPUT
39 SCAN PATH PROVENANCE AUTO-OUTPUT
40 RAW VS ACTUAL COUNT SEPARATION
41 RECOVERY PATH AUTO-OUTPUT
42 POST-RUN AI SELF-IMPROVEMENT
43 ROOT-CAUSE BEFORE MASTER CHANGE
44 AUTO VERSION ASSIGNMENT BY GENERATIVE AI
45 AUTO FREEZE ONLY AFTER REGRESSION PASS
46 DATASET/PATH ASSETIZATION
47 RUNTIME ASSET MANIFEST
48 NEXT-RUN PATH REUSE
49 DATASET STALE/PARTIAL/CORRUPT RECOVERY
50 ACTUAL COUNT RECALC FROM DATASET
51 ASSET CREATION HONESTY / NO FALSE CLAIM
52 SOURCE MANIFEST PERSISTENCE
53 SCAN COUNTER PERSISTENCE
54 RUN MANIFEST PERSISTENCE

하나라도 FAIL이면 FROZEN/CURRENT 승격 금지.

# 22. OFFICIAL EXECUTION COMMAND
사용자가 "MSS 지시문을 수행하라."라고 하면 하나의 실행으로:
CURRENT RESOLUTION
→ MASTER INTEGRITY / CONTRACT INHERITANCE
→ 최신 시장상태 및 기준거래일
→ Trend Screener 전체시장 Trend Template Dataset 취득
→ KR/US Unique Symbol 정규화·중복제거
→ Level-1 Actual Scan Counter 계측
→ Scan Path / Source / Recovery Path 자동 기록
→ 기존 Runtime Manifest/Path 검증 및 재사용
→ 필요한 Dataset 자동 취득·보충·Backfill
→ universe/level1~4/source_manifest/scan_counter/run_manifest 생성·갱신
→ Actual Count를 Dataset Unique Symbol 기준 재계산
→ KR 실제 Unique Scan ≥300
→ US 실제 Unique Scan ≥300
→ Sector Coverage
→ Adaptive 확대판단(300/500/700/FULL)
→ Level 2 Strong Trend+Liquidity
→ Level 3 First Pullback 정량검증
→ Level 4 6관문 심층검증
→ Prior-Pullback / Completed-Bar / Immediate Disqualification
→ AI Independent Review
→ AI Final
→ User Counter 상태(실패 격리)
→ 9-Block 출력
→ Post-Run AI Self-Improvement
→ Dataset/Path 구조문제 및 Next-Run Reuse Readiness 검증
→ 가능한 경우 Runtime Asset 자동 생성·갱신
→ Root Cause / Structural Change 판단
→ Regression
→ 필요 시 새 버전
→ PASS 시에만 Freeze + Pointer 교체
→ Pointer 재검증
→ 지정된 MSS 한줄 요약

# 23. MSS 한줄 요약 — MANDATORY LAST OUTPUT
MSS VERSION │ vX.X.X │ FROZEN · CURRENT

MSS 한줄 요약
│ 즉시매수준비: [종목/NONE]
│ 가장 가까운 후보: [종목 · 상태]
│ 실제 스캔: KR xxx종목 · US xxx종목 · 총 xxx종목
│ Adaptive Scan: 300 / 500 / 700 / FULL
│ 다음 승격조건: [...]

이 요약 이후에는 어떠한 문장도 출력하지 않는다.

# VERSION CONTROL
Previous                                 │ v4.10.1
Historical authoritative scan baseline   │ v4.3.0
Invalid reconstruction superseded        │ v4.6.0
Current                                  │ v4.11.0
Change Type                              │ MINOR — Automatic Dataset/Path Assetization + Next-Run Reuse
Core Preserved                           │ ADAPTIVE 300+300 MARKET SCAN
Expansion                                │ 300 → 500 → 700 → FULL
Actual Scan Hard Gate                    │ KR≥300 AND US≥300 AND TOTAL≥600
Regression                               │ PASS (54/54 contract checks)
AI Approval                              │ APPROVED
Status                                   │ FROZEN · CURRENT

# v4.9.0 FINAL APPROVAL / FREEZE
Original Contract Restoration          │ PASS
AI FINAL AUTHORITY                     │ PASS
MASTER OBJECTIVE                       │ PASS
FACT INTEGRITY                         │ PASS
DATA RECOVERY                          │ PASS
Adaptive 300→500→700→FULL             │ PASS
KR/US Independent Scan                │ PASS
Self-Improvement                       │ PASS
AI Version Authority                  │ PASS
Contract Inheritance                  │ PASS
Original Semantics Lock               │ PASS
No Lower-Rule Override                │ PASS
9-Block Output                         │ PASS
Version Traceability                  │ PASS
Regression                            │ PASS
AI Final Approval                     │ APPROVED
Auto Freeze                           │ COMPLETE
Status                                │ FROZEN · CURRENT

# v4.10.0 FINAL APPROVAL / FREEZE
Original Contract Preservation          │ PASS
AI FINAL AUTHORITY                     │ PASS
FACT INTEGRITY                         │ PASS
DATA RECOVERY                          │ PASS
Adaptive 300→500→700→FULL             │ PASS
Actual Scan Count Auto-Output          │ PASS
Scan Path Provenance Auto-Output       │ PASS
Raw vs Actual Count Separation         │ PASS
Recovery Path Auto-Output              │ PASS
Post-Run Generative-AI Self-Improvement│ PASS
Root-Cause Gate                        │ PASS
AI Version Authority                  │ PASS
Regression                               │ PASS (54/54 contract checks)
AI Final Approval                     │ APPROVED
Auto Freeze                           │ COMPLETE
Status                                │ FROZEN · CURRENT

# v4.10.1 PATCH VALIDATION
Core Regression                         │ 45/45 PASS
Header Metadata Consistency             │ PASS
Coverage/Result Status Reconciliation   │ PASS
AI FINAL AUTHORITY Preservation         │ PASS
DATA RECOVERY Preservation              │ PASS
300+300 Hard Gate Preservation          │ PASS
Original Semantics Lock                 │ PASS
AI Final Approval                       │ APPROVED
Auto Freeze                             │ COMPLETE
Status                                  │ FROZEN · CURRENT

# v4.11.0 FINAL APPROVAL / FREEZE
Original Contract Preservation           │ PASS
AI FINAL AUTHORITY                      │ PASS
FACT INTEGRITY                          │ PASS
DATA RECOVERY                           │ PASS
Adaptive 300→500→700→FULL              │ PASS
Scan Count Auto-Output                  │ PASS
Scan Path Provenance                    │ PASS
Post-Run Generative-AI Self-Improvement │ PASS
Dataset/Path Assetization               │ PASS
Runtime Asset Manifest                  │ PASS
Next-Run Automatic Reuse                │ PASS
Stale/Partial/Corrupt Recovery           │ PASS
Actual Count Recalc from Dataset        │ PASS
No False Asset Claim                    │ PASS
Regression                              │ PASS (54/54)
AI Final Approval                       │ APPROVED
Auto Freeze                             │ COMPLETE
Status                                  │ FROZEN · CURRENT