# MSS MASTER v5.0.0 — CANDIDATE
## AI-FINAL · ALARM-INHERITED · TIME-BOUNDED OPEN-MARKET SELECTION
Status: CANDIDATE
Date: 2026-09-26
Parent: v4.11.0
Lineage: ALARM MS7-STC DISTRIBUTION v1.0.3 → MSS v4.11.0 → MSS v5.0.0
Change type: MAJOR — authority hierarchy + Alarm inheritance + bounded scan architecture
Reason: Restore AI FINAL as highest decision authority and make market scan a bounded discovery stage rather than the system objective.

# 0. HIGHEST AUTHORITY — AI FINAL AUTHORITY

MSS의 최고 결정권은 생성형 AI의 최종 판단이다.

생성형 AI는 다음을 종합하여 AI FINAL DECISION을 내린다.
- 최신 검증 사실
- 최신 시장정보
- 정량분석
- 추세 지속성
- 가격·거래량·Relative Strength
- First Healthy Pullback / 재가속 구조
- Alarm 계열의 MS7 상태층
- 일봉 STC / 60분 STC 타이밍층
- BUY / SELL 상태머신
- 실적·뉴스·이벤트·리스크
- 데이터 품질과 불확실성
- 논리적 추론
- 독립 자가검증 결과

MSS, Gate, Scan Count, Dataset, Indicator, Threshold, Score, Ranking은 모두 AI FINAL을 지원하는 하위 Framework다.
어떠한 하위 규칙도 AI FINAL AUTHORITY를 대신하거나 기계적으로 덮어쓰지 않는다.

단, AI FINAL도 FACT INTEGRITY를 위반할 수 없다.
FACT INTEGRITY는 별도의 상위 의사결정권이 아니라 AI가 넘어서는 안 되는 사실 경계다.
확인되지 않은 가격·지표·사실·Scan Count를 생성하지 않는다.

권위 순서:
VERIFIED FACT BOUNDARY
→ GENERATIVE AI FINAL AUTHORITY
→ MSS FRAMEWORK
→ ALARM / MS7-STC STATE & TIMING
→ QUANT / GATE / SCORE
→ DATASET / INDICATOR / THRESHOLD

# 1. MASTER OBJECTIVE

MSS의 목적은 많은 종목을 오래 Scan하는 것이 아니다.

열린 시장에서 상승 추세가 지속될 가능성이 높은 종목을 제한된 시간 안에 빠르게 발굴하고,
후보를 단계적으로 압축한 뒤,
Alarm/MS7-STC 상태판단과 심층검증 및 AI 독립 자가검증을 결합하여
가장 유력한 최종 추천 후보를 제시하는 것이 목적이다.

핵심 질문:
"오늘 이용 가능한 시간과 데이터 안에서, 상승 지속 가능성이 가장 높은 종목은 무엇이며,
그 판단은 최신 사실과 Alarm/MSS 상태로 충분히 검증되었는가?"

First Healthy Pullback은 중요한 발굴 기준이지만 MSS 전체 목적 그 자체는 아니다.
최종 목적은 상승 지속 가능성이 높은 종목의 발견·검증·추천이다.

# 2. ALARM LINEAGE — MANDATORY INHERITANCE

MSS는 Alarm MS7-STC의 상위 확장체계다.
Alarm의 핵심 매매·타이밍 철학을 삭제하지 않는다.

계승 필수:
1. MS7 상태층
   - M0 / M1 / M2 / W / S1 / S2 / S3
   - 상태 확정성: CONFIRMED / PROVISIONAL / UNKNOWN / CONFLICT
   - UNKNOWN을 임의로 W로 채우지 않는다.

2. STC 타이밍층
   - 완료 일봉 기준 Slow Stochastic 14,3,3
   - 완료 60분봉 기준 Slow Stochastic 14,3,3
   - Gold 직전/발생/직후
   - Dead 직전/발생/직후
   - 미완성 봉은 확정판정에 사용하지 않는다.

3. BUY 상태머신
   - BUY_WATCH
   - BUY_READY
   - BUY_TRIGGER
   - BUY_CONFIRMED
   - BUY_FAIL/RESET
   - 3거래일 Setup Window 원칙 계승

4. SELL 상태머신
   - SELL_WATCH
   - SELL_READY
   - SELL_TRIGGER
   - SELL_CONFIRMED
   - SELL_FAIL/RESET
   - BUY와 대칭 구조 계승

5. 역할 분리
   - MS7 = 상태층
   - STC = 타이밍층
   - MSS = Open Market 발견·압축·지속성 검증·AI FINAL 층

기술적 BUY_TRIGGER가 발생해도 MS7이 S1~S3이면 추격위험을 반영하고 AI가 최종 행동을 판단한다.
보유 여부가 확인되지 않으면 SELL 판단은 "보유 시" 조건으로 표현한다.

# 3. OPEN MARKET DISCOVERY

MSS는 고정 Watchlist에만 의존하지 않는다.
KR/US 열린 시장에서 Dynamic Universe를 구성한다.

원칙:
- 가능한 경우 Bulk Dataset으로 전체 적격 Universe를 한 번 취득한다.
- 전체 Universe를 반복 재스캔하지 않는다.
- Source가 전체시장 Snapshot을 제공하면 한 번 정규화·중복제거·저비용 Score 계산 후 압축한다.
- Bulk Dataset이 없을 때만 Budget 안에서 대체 Source를 사용한다.
- Web Search는 Level-1 숫자를 채우기 위한 패딩 수단으로 사용하지 않는다.
- 국가별 Scan은 독립 처리한다.
- 특정 Sector 편향 여부를 확인한다.
- Raw Universe와 실제 처리 수를 분리 기록한다.

# 4. TIME-BOUNDED SCAN — IMMUTABLE

Scan에는 무한정 시간을 할당하지 않는다.

최상위 시간 원칙:
- Scan은 후보 발굴을 위한 전처리 단계다.
- 전체 실행시간의 대부분을 반복 Scan에 소비하지 않는다.
- 추가 Scan의 기대정보가 낮으면 즉시 종료하고 심층검증으로 이동한다.
- 동일 Universe에 대한 반복 300→500→700→FULL 재스캔을 기본 동작으로 금지한다.
- 이미 Bulk Full-Market Dataset을 한 번 처리했다면 추가 breadth scan 대신 후보 검증에 시간을 사용한다.

기본 시간 배분:
- Open Market acquisition + normalization + cheap scoring: 전체 실행 예산의 최대 약 30%
- 후보 압축 및 중간 검증: 약 20%
- Deep validation + Alarm/MS7-STC + 최신 Context: 약 35%
- AI Independent Review + Self-Validation + 결과생성: 약 15%

실행환경 제약으로 절대시간을 고정할 수 없는 경우 위 비율을 논리적 Budget으로 적용한다.

TIME BUDGET STOP:
다음 중 하나이면 breadth 확대를 중지한다.
- 충분한 고품질 후보 확보
- Sector/Leadership coverage 충분
- 추가 탐색의 marginal information gain 낮음
- 남은 시간으로 deep validation 품질이 훼손될 위험
- Source latency/오류가 반복되어 탐색비용이 급증

TIME BUDGET에 도달하면 결과를 중단하지 않는다.
Best Available Evidence로 계속하되 Coverage/Uncertainty를 명시한다.

# 5. PROGRESSIVE COMPRESSION — NO RESCAN

기본 Funnel:
OPEN MARKET / AVAILABLE FULL UNIVERSE
→ LEVEL 1: 최대 약 300 / market
→ LEVEL 2: 최대 약 100 / market
→ LEVEL 3: 최대 약 30 / market
→ LEVEL 4: 최대 약 10 / market
→ AI FINAL: 핵심 3~5 또는 NONE

핵심:
- 위 숫자는 재스캔 횟수가 아니라 "남길 후보 수"의 기본 상한이다.
- Level 1 이후에는 전체시장을 다시 읽지 않고 이전 단계 후보만 더 깊게 계산한다.
- 후보 품질에 따라 AI가 각 단계의 수를 줄이거나 늘릴 수 있다.
- 시장 적격 Universe가 300 미만이면 존재하는 전부를 사용한다.
- 충분한 후보가 일찍 확보되면 300을 억지로 채우지 않는다.
- Bulk full-universe 처리가 저비용으로 가능하면 전체를 한 번 처리한 뒤 Top 300으로 압축한다.

구 v4.x의 "KR≥300, US≥300 절대 Hard Gate"와 "300→500→700→FULL 반복 확대"는
AI FINAL과 Time-Bounded 철학에 맞게 본 버전에서 명시적으로 대체한다.

새 정상성 기준:
- Coverage가 최종판단에 충분한가?
- 핵심 시장 리더십이 포함되었는가?
- 후보 품질이 구별 가능한가?
- Deep validation이 충분한가?
- AI가 불확실성을 정직하게 표시했는가?

# 6. LEVEL DEFINITIONS

## LEVEL 0 — Universe Acquisition
목표: 열린 시장에서 가능한 넓은 적격 Universe를 한 번 확보.
작업: Source 취득 → schema 확인 → normalization → unique dedupe → data date 확인.

## LEVEL 1 — Cheap Market Selection
대상: Available Universe 전체 또는 Budget 내 최대 범위.
저비용 기준:
- Liquidity / Trading Value
- Market Cap
- Momentum
- Relative Strength proxy
- Sector Leadership
- Breakout / Pullback Potential
- abnormal data 제거

산출: 최대 약 300 / market.
이 단계에서는 고비용 Web/OHLCV deep-history 조회를 최소화한다.

## LEVEL 2 — Trend Sustainability
대상: Level 1 후보만.
검증:
- Strong Trend
- multi-horizon return
- trend structure
- volume quality
- liquidity durability
- sector leadership persistence
- excessive spike / chase risk
- fundamental/event red flags where cheaply available

산출: 최대 약 100 / market.

## LEVEL 3 — Pullback / Reacceleration
대상: Level 2 후보만.
검증:
- First Healthy Pullback
- prior meaningful pullback
- support maintenance
- selling pressure reduction
- completed bars
- relative strength maintenance
- reacceleration preparation

산출: 최대 약 30 / market.

## LEVEL 4 — Deep Verification
대상: Level 3 핵심 후보.
검증:
- 최신 완료 일봉
- 필요 시 60분 완료봉
- MS7
- STC Daily/60m
- BUY/SELL state machine
- latest news/earnings/event risk
- abnormal gap / distribution / support breakdown
- cross-validation / best available evidence

산출: 최대 약 10 / market.

# 6-A. SIX-GATE BACKBONE — PRESERVED

Level 4 심층검증은 기존 MSS 6-Gate 계보를 유지한다.
세부 구현은 시장상황과 데이터 가용성에 따라 AI가 조정할 수 있으나 다음 6개 검증축은 삭제하지 않는다.

G1 MARKET / REGIME
- 시장 체질, 변동성, 국가별 조건, Sector leadership

G2 STRONG TREND
- 중기 추세, Relative Strength, liquidity, trend structure

G3 HEALTHY PULLBACK
- First Healthy Pullback, prior-pullback exclusion, support 유지, selling pressure

G4 TIMING / ALARM
- MS7 상태층, Daily STC, 60m STC, BUY/SELL state

G5 REACCELERATION / RISK
- 재가속 가능성, volume confirmation, gap/distribution, event/fundamental risk

G6 FACT / INTEGRITY
- completed bars, source date, cross-validation, fabrication=0, contradiction check

Gate는 AI FINAL을 기계적으로 대신하지 않는다.
그러나 Gate FAIL 또는 UNVERIFIED는 AI FINAL에서 반드시 근거와 함께 반영한다.

# 7. SUSTAINABILITY-FIRST SELECTION

최우선 후보는 단기 급등률이 가장 높은 종목이 아니다.

다음을 종합한다:
- 강한 중기 상승구조
- 상승 추세 지속 가능성
- 과도한 추격위험 부재
- 정상조정 또는 건강한 안정화
- Relative Strength 유지
- 거래량 구조 건전성
- Sector/Industry Leadership
- 실적·이벤트 리스크
- 재가속 가능성
- Alarm/MS7-STC 타이밍 적합성

First Healthy Pullback은 높은 우선순위를 갖지만,
추세 지속성이 더 높은 다른 구조가 존재하면 AI가 근거를 제시하고 최종후보에 포함할 수 있다.

# 8. IMMEDIATE DISQUALIFICATION

다음은 강한 감점 또는 제외 사유:
- Trend Structure Breakdown
- Support Breakdown
- Lower Low Breakdown
- Relative Strength Collapse
- 대량거래 급락 / Distribution
- Abnormal Gap Down
- Major Negative Fundamental Change
- 확인되지 않은 급등 이벤트 의존
- 데이터 정합성 파손
- 추격위험이 기대수익보다 현저히 큰 경우

AI는 예외를 허용할 수 있으나 근거와 리스크를 명시해야 한다.

# 9. AI INDEPENDENT REVIEW

Quant 결과를 복창하지 않는다.

Execution AI와 Independent Review AI의 논리 역할을 분리한다.
물리적으로 같은 생성형 AI가 수행하더라도 역할 기준은 분리한다.

Independent Review는 최소 다음을 수행한다.
- Top 후보를 일부러 기각하려는 반대검증
- 후보 누락 가능성
- False Positive
- False Negative
- 추세 지속성 과대평가
- Pullback 오인
- completed-bar 오류
- stale source / date mismatch
- event risk 누락
- sector concentration
- 데이터와 결론의 불일치

Quant와 AI가 충돌하면:
근거 기록 → AI FINAL.
불확실성이 해소되지 않으면 READY를 강행하지 않고 STABILIZING/WATCH/UNVERIFIED로 낮춘다.

# 10. AI SELF-VALIDATION — MANDATORY

모든 MSS AI FINAL 이후 자동 수행한다.
사용자에게 검증을 떠넘기지 않는다.

논리 역할:
1. EXECUTION AI
2. INDEPENDENT REVIEW AI
3. REGRESSION AI
4. FINAL APPROVAL AI

자가검증 항목:
- 최신 데이터인가?
- SourceFetchedAt과 DataBarDate를 혼동하지 않았는가?
- LatestCompletedTradingDay가 맞는가?
- 미완성 봉을 확정에 사용하지 않았는가?
- 후보 누락 가능성을 검토했는가?
- 상승 지속성 근거가 충분한가?
- Alarm/MS7-STC가 최종판단과 모순되지 않는가?
- False Positive/Negative를 검토했는가?
- 없는 수치·사실을 만들지 않았는가?
- Scan에 과도한 시간을 사용하지 않았는가?
- 더 Scan할 정보이득보다 deep validation 가치가 큰 시점에 멈췄는가?
- 기존 계약을 승인 없이 훼손하지 않았는가?

# 11. DATA RECOVERY / CONTINUATION

특정 NAS·API·웹사이트·Screener를 단일 Authority로 고정하지 않는다.

Source A
→ Source B
→ Source C
→ Historical Search / Backfill
→ Cross Validation
→ Best Available Evidence
→ AI FINAL

외부 Source 일부 실패만으로 전체 결과 생성을 중단하지 않는다.
계산 불가능한 개별 값은 UNVERIFIED.
Fabrication = 0.

Source metadata는 반드시 분리 기록:
- SourceFetchedAt
- DataBarDate
- LatestCompletedTradingDay
- Provider
- Path/Endpoint
- Status
- RecoveryNote

조회시각이 최신이라고 가격봉까지 최신이라고 간주하지 않는다.

# 12. RUNTIME ASSETIZATION

가능하면 다음 자산을 재사용한다.

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

VALID → 재사용 + 최신성 검증
STALE/PARTIAL → 필요한 부분만 보충
CORRUPT/INVALID → 원인 기록 후 재구축
NOT FOUND → 새로 확보 후 저장

이전 버전 Runtime Asset도 schema와 date가 검증되면 INPUT으로 재사용 가능하다.
단, 이전 run_manifest를 새 버전 실행 결과라고 위장하지 않는다.

# 13. SCAN COUNTER / PROVENANCE

매 실행 기록:
- KR Raw Universe
- US Raw Universe
- KR Actual Unique Processed
- US Actual Unique Processed
- Level1/2/3/4 처리 수
- Final reviewed count
- Sector coverage
- SourceFetchedAt
- DataBarDate
- LatestCompletedTradingDay
- Actual Scan Path
- Recovery Path
- Time Budget Stop 여부
- Unverified fields
- Fabrication = 0

과거 Count를 현재 Count로 재사용하지 않는다.
검색결과에 이름만 노출된 종목은 Scan Count에 넣지 않는다.

# 13-A. USER COUNTER / FAILURE ISOLATION — PRESERVED

시장 Scan Counter와 MSS 사용자 Counter를 혼동하지 않는다.
legacy execution counter는 고유 사용자 수가 아니다.
고유 사용자 수는 별도 User Registry가 실제 구현된 경우에만 표시한다.
User Registry 미구현 시: MSS 사용자 │ 조회불가.
사용자 수를 추정하거나 강제 fingerprint로 보충하지 않는다.
Counter 장애는 시장분석·후보선정·AI FINAL을 중단시키지 않는다.

현재 계승 상태:
- MSSCounter Durable Object authority: 존재할 수 있음
- User Registry: 실제 구현 여부 확인 후 표시
- unique_users runtime: 확인 불가 시 NOT_AVAILABLE

# 13-B. COVERAGE vs RESULT COMPLETION

Scan Coverage와 Recommendation Confidence는 별도 축이다.

SCAN COVERAGE:
- FULL / SUFFICIENT / PARTIAL / UNVERIFIED

RECOMMENDATION CONFIDENCE:
- HIGH / MEDIUM / LOW / UNVERIFIED

Raw Scan Count 하나만으로 추천 가능/불가를 자동 결정하지 않는다.
반대로 Coverage가 부족한데 Confidence를 과장하지도 않는다.
AI는 탐색범위, 후보대표성, deep validation, data freshness를 함께 평가한다.

# 14. FINAL RECOMMENDATION STATES

AI FINAL은 다음 상태를 사용한다.

- READY NOW
  상승 지속성 + 데이터 + 타이밍 + 리스크가 충분히 검증된 핵심 후보.

- STABILIZING
  추세는 유효하나 정상조정/안정화 또는 Trigger 완성을 기다리는 후보.

- WATCH
  구조는 관심대상이지만 데이터/타이밍/품질 검증이 부족한 후보.

- WAIT FOR FIRST PULLBACK
  상승구조는 강하나 추격위험 때문에 정상조정을 기다리는 후보.

- DROPPED / AVOID
  구조 훼손, prior pullback 불합격, 리스크 증가, 데이터 무결성 실패 등.

READY NOW가 없으면 NONE을 허용한다.
추천 수를 채우기 위해 품질기준을 낮추지 않는다.

# 15. STANDARD 9-BLOCK OUTPUT

① HEADER
- MSS Version / CURRENT
- 실행시각
- Latest Completed Trading Day KR/US
- Execution Status

② MARKET REGIME
- KR / US 시장체질과 Leadership

③ SCAN & COMPRESSION
- Universe → L1 → L2 → L3 → L4
- 실제 Count
- Time Budget Stop
- 주요 New/Dropped

④ SUSTAINABILITY MASTER TABLE
- 핵심 후보
- Trend
- Pullback/Reacceleration
- RS/Volume
- 주요 Risk

⑤ ALARM / MS7-STC STATE
- MS7
- Daily STC
- 60m STC
- BUY/SELL State
- 다음 상태조건

⑥ AI FINAL RECOMMENDATION
- READY NOW
- STABILIZING
- WATCH
- WAIT
- DROPPED/AVOID

⑦ DATA INTEGRITY
- Source
- SourceFetchedAt
- DataBarDate
- LatestCompletedTradingDay
- Scan Count
- Scan Path
- Recovery
- Unverified
- Fabrication=0

⑧ POST-RUN SELF-VALIDATION / SELF-IMPROVEMENT
- Independent Review
- Structural Problem YES/NO
- Root Cause
- Rule Change YES/NO
- Regression
- Version/Freeze

⑨ FINAL SYNTHESIS
- 최종 핵심 후보
- 핵심 근거
- 다음 승격/실패 조건

원칙: 깊게 분석하고 짧게 보고한다. 동일 사실 반복 금지.

# 16. SELF-IMPROVEMENT / VERSION AUTHORITY

매 실행:
MSS RUN
→ RESULT
→ AI INDEPENDENT REVIEW
→ AI SELF-VALIDATION
→ STRUCTURAL PROBLEM DECISION

구조적 문제 없음:
→ NO STRUCTURAL CHANGE
→ CURRENT 유지

구조적 문제 있음:
→ ROOT CAUSE
→ 개선안
→ Candidate Master
→ Contract Inheritance Check
→ Consistency Check
→ Full Regression
→ AI Final Approval
→ PASS인 경우에만 Freeze
→ Single Current Pointer 마지막 교체
→ Pointer 재조회
→ 다음 실행 적용

금지:
- 일회성 Source 장애만으로 Master 변경
- 결과가 마음에 들지 않는다는 이유로 기준 사후 변경
- 기존 FROZEN 덮어쓰기
- Regression FAIL 버전 승격
- Candidate를 CURRENT처럼 사용

# 16-A. CONTRACT INHERITANCE / ORIGINAL SEMANTICS LOCK

새 버전은 부모의 검증된 필수계약을 상속한다.
명시적 변경대상이 아닌 기존 필수기능은 삭제·약화하지 않는다.
핵심 의미가 충돌하거나 불명확하면 Alarm lineage와 직전 정상 CURRENT를 우선 확인한다.

본 v5.0.0의 의도적 변경은 다음 두 v4.x scan 규칙에 한정된다.
- absolute KR≥300 / US≥300 recommendation gate
- sequential 300→500→700→FULL breadth expansion

위 두 규칙은 사용자 지시에 따라 AI FINAL / Time-Bounded / Progressive Compression 체계로 대체한다.
그 외 검증된 기능은 유지한다.

NO LOWER-RULE OVERRIDE:
Dataset, API, Counter, Indicator, Threshold, Gate, 출력형식은
AI FINAL AUTHORITY / FACT INTEGRITY / MASTER OBJECTIVE / SELF-VALIDATION을 무효화할 수 없다.

# 17. SINGLE CURRENT AUTHORITY

CURRENT 권위는 오직 master/current.json이 결정한다.

우선순위:
current.json pointer
→ pointer가 지정한 frozen master identity/hash
→ regression result
→ AI Final Approval
→ version number

파일명이나 문서 내부의 CURRENT 문자열만으로 권위를 결정하지 않는다.

상태:
- CANDIDATE
- REGRESSION_PASS
- FROZEN_CURRENT
- HISTORICAL
- INVALID

FROZEN_CURRENT는 하나만 존재해야 한다.

# 18. VERSIONING

Semantic versioning:
- PATCH: 비기능/문구/메타데이터 수정
- MINOR: 기능·Gate·출력 확장, 핵심철학 유지
- MAJOR: 최고권위·목표·Scan Architecture·핵심 상태체계 변경

v5.0.0은 다음 의도적 변경을 승인한다.
- v4.x의 300→500→700→FULL 반복 확대를 폐기하고 one-pass + progressive compression으로 대체.
- KR≥300/US≥300을 AI보다 위의 절대 Hard Gate로 두지 않는다.
- 300은 기본 L1 후보 상한/목표이며 성공조건 그 자체가 아니다.
- Scan Coverage와 Recommendation Confidence를 분리한다.
- Alarm/MS7-STC를 MSS 최종판단 계보에 명시적으로 복원한다.
- Time Budget / Early Stop / Marginal Information Gain을 최상위 실행원칙으로 추가한다.
- SourceFetchedAt / DataBarDate / LatestCompletedTradingDay를 분리한다.

# 19. REQUIRED FEATURES — v5.0.0

필수 상속/유지:
- AI FINAL AUTHORITY
- FACT INTEGRITY / NO FABRICATION
- Dynamic Universe
- KR/US independent handling
- Sector Coverage
- Strong Trend
- First Healthy Pullback
- Prior-Pullback exclusion
- Completed-bar qualification
- Immediate Disqualification
- AI Independent Review
- Data Recovery
- Scan provenance / actual count
- Runtime assetization
- Post-run self-improvement
- Contract inheritance
- Single Current authority
- Version traceability
- Auto Freeze only after regression PASS
- 9-block output
- Counter failure isolation
- user registry honesty

Alarm lineage required:
- MS7 state layer
- Daily STC
- 60m STC
- BUY/SELL state machines
- Setup Window concept
- UNKNOWN/CONFLICT honesty
- state change emphasis

새 필수:
- AI highest authority explicitly at top
- bounded scan time
- no repeated full-universe rescan
- progressive compression 300→100→30→10 default
- sustainability-first selection
- logical-role-separated self-validation
- source date semantics separation
- recommendation confidence independent from scan count

# 20. REGRESSION CONTRACT — v5

승격 전 최소 검사:

01 AI FINAL highest authority
02 FACT INTEGRITY boundary
03 no lower-rule override
04 Alarm lineage documented
05 MS7 preserved
06 Daily STC preserved
07 60m STC preserved
08 BUY state machine preserved
09 SELL state machine preserved
10 Setup Window preserved
11 Dynamic Universe
12 KR/US independent
13 open-market discovery
14 one-pass bulk preference
15 no repeated universe rescan
16 time budget
17 early stop
18 marginal information gain
19 progressive compression
20 L1 max ~300
21 L2 max ~100
22 L3 max ~30
23 L4 max ~10
24 AI Final 3~5 or NONE
25 Strong Trend
26 sustainability-first
27 First Healthy Pullback
28 prior-pullback exclusion
29 completed-bar
30 immediate disqualification
31 RS/volume
32 sector coverage
33 event/fundamental risk
34 AI independent review
35 adversarial candidate rejection
36 false positive check
37 false negative check
38 self-validation mandatory
39 Execution/Review/Regression/Approval role separation
40 data recovery
41 no fabrication
42 SourceFetchedAt
43 DataBarDate
44 LatestCompletedTradingDay
45 stale date mismatch check
46 scan counter
47 raw vs actual
48 scan provenance
49 time budget stop output
50 runtime assets
51 manifest reuse
52 stale/partial recovery
53 corrupt recovery
54 prior counts not reused
55 web search not used to pad counts
56 9-block output
57 concise nonduplicate output
58 post-run structural problem gate
59 root cause before rule change
60 candidate before freeze
61 full regression before freeze
62 AI Final Approval
63 frozen master immutable
64 single current pointer
65 pointer updated last
66 pointer re-read verification
67 historical preservation
68 semantic versioning
69 intentional v4 scan-gate replacement documented
70 recommendation confidence independent from raw scan count
71 Counter failure isolation
72 User Registry honesty

하나라도 FAIL이면 v5.0.0 FROZEN_CURRENT 승격 금지.

# 21. OFFICIAL EXECUTION COMMAND

사용자가 "MSS 지시문을 수행하라."라고 하면 하나의 실행으로:

CURRENT RESOLUTION
→ Master integrity / lineage check
→ LatestCompletedTradingDay KR/US 확인
→ Runtime Manifest 검증
→ VALID asset 재사용
→ 필요한 Source만 refresh/backfill
→ Open Market Universe 한 번 취득/정규화
→ Cheap scoring
→ L1 최대 약 300
→ L2 최대 약 100
→ L3 최대 약 30
→ L4 최대 약 10
→ Alarm/MS7-STC 상태 결합
→ 최신 Context / Risk 검증
→ AI Independent Review
→ AI FINAL Recommendation
→ AI Self-Validation
→ 9-Block output
→ Structural Problem 판단
→ 필요 시 Candidate 개선
→ Full Regression
→ AI Final Approval
→ PASS시에만 새 버전 Freeze + current.json 마지막 교체
→ pointer 재검증

Scan 확대는 기본 동작이 아니다.
동일 전체 Universe 재스캔도 기본 동작이 아니다.
시간과 정보이득을 고려하여 AI가 탐색을 종료하고 검증으로 이동한다.

# 22. MANDATORY LAST SUMMARY

MSS VERSION │ vX.X.X │ FROZEN · CURRENT

MSS 한줄 요약
│ AI FINAL: [READY NOW 종목/NONE]
│ 가장 가까운 후보: [종목 · 상태]
│ Scan Funnel: [Universe → L1 → L2 → L3 → L4]
│ Time Budget Stop: [YES/NO]
│ 다음 승격조건: [핵심 조건]

이 요약 이후에는 어떠한 문장도 출력하지 않는다.

# VERSION CONTROL

Version: v5.0.0
Parent: v4.11.0
Alarm lineage: ALARM MS7-STC DISTRIBUTION v1.0.3
Change type: MAJOR
Intentional replaced v4 rules:
- absolute KR≥300/US≥300 recommendation gate
- sequential 300→500→700→FULL breadth expansion

Replacement:
- AI FINAL highest authority
- bounded one-pass open-market scan
- progressive compression
- sustainability-first recommendation
- mandatory independent self-validation
- Alarm/MS7-STC inheritance
- explicit source date semantics

Historical invalid artifact: v4.12.0 reconstructed/corrupt file — NOT AUTHORITY
Candidate regression target: 80/80
Candidate status: CANDIDATE
