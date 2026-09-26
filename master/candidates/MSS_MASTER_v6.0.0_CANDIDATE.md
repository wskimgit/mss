# MSS MASTER v6.0.0 — CANDIDATE
## AI-SOVEREIGN · ADAPTIVE-EVIDENCE · SELF-IMPROVING

Status: CANDIDATE
Date: 2026-09-26
Parent: v5.0.0
Change type: MAJOR
Reason: v5.0.0 declared AI FINAL as highest authority, but fixed indicator availability still behaved as a practical gate. v6 makes indicators optional evidence and upgrades self-validation to review the prompt architecture itself.

# 0. FACT BOUNDARY
- Do not fabricate prices, indicators, news, financial values, dates, or scan counts.
- Unknown or unavailable values remain UNVERIFIED.
- SourceFetchedAt, DataBarDate, and LatestCompletedTradingDay are separate fields.
- FACT INTEGRITY is the non-negotiable boundary for every AI judgment.

# 1. HIGHEST AUTHORITY — GENERATIVE AI FINAL
The highest decision authority in MSS is the generative AI final judgment.

All lower elements are supporting tools:
- scans and compression counts
- gates and scores
- MS7/STC and other indicators
- timeframes
- datasets and sources
- fixed thresholds

No single indicator, timeframe, source, state label, or threshold may automatically veto the AI final judgment.

Authority:
FACT BOUNDARY
→ GENERATIVE AI FINAL
→ AI INDEPENDENT REVIEW / SELF-VALIDATION
→ MSS EVIDENCE FRAMEWORK
→ OPTIONAL INDICATORS / SOURCES

If AI overrides a lower rule it must record:
- the lower rule,
- the reason for override,
- contradictory evidence,
- confidence impact.

# 2. MASTER OBJECTIVE
Within a bounded amount of time MSS shall:
1. discover strong candidates from an open market universe,
2. compress candidates efficiently,
3. verify upward-trend sustainability using the most informative available evidence,
4. perform independent AI review,
5. produce a small final research-candidate set with confidence and risks.

The objective is candidate quality, not maximum scan size or completion of every indicator.

# 3. ALARM LINEAGE — CONCEPT PRESERVATION
MSS preserves the original Alarm concepts:
- separate market state from timing,
- track meaningful state changes,
- examine strengthening and weakening evidence,
- never convert unknown data into a false confirmed state,
- preserve the logic of watch/ready/trigger/confirm/fail-reset when useful.

Legacy modules such as MS7, Daily STC, 60m STC, Slow Stochastic 14,3,3 and setup windows are OPTIONAL EVIDENCE MODULES, not mandatory gates.

If a module is unavailable, expensive, stale, or low-value, AI may replace it with more direct evidence.

# 4. ADAPTIVE EVIDENCE ARCHITECTURE
Core evidence priorities:
- trend structure
- multi-horizon returns
- relative strength
- volume and liquidity
- drawdown / pullback
- support / breakout / reacceleration
- sector and market leadership
- volatility / chase risk
- earnings / guidance / material-event risk
- data freshness

Timing evidence is selected only when it improves information value:
- completed daily price structure
- moving-average position and slope
- volatility contraction/expansion
- volume contraction/re-expansion
- RSI / MACD / Stochastic / STC
- intraday structure
- support/resistance and gap behavior

No specific timing indicator is mandatory.

# 5. EVIDENCE SUFFICIENCY
Evaluate four evidence axes:
A. Trend
B. Sustainability
C. Timing / price position
D. Risk

A final AI judgment may be made when at least three axes are supported by reliable current evidence.
Missing STC or intraday data alone does not force rejection.
Positive STC alone does not force selection.

# 6. TIME-BOUNDED OPEN-MARKET FUNNEL
Prefer one bulk-universe acquisition.

OPEN MARKET
→ L1 about 300
→ L2 about 100
→ L3 about 30
→ L4 about 10
→ AI FINAL small candidate set

These are compression targets, not absolute gates.

Do not:
- repeatedly rescan the same full universe,
- expand breadth without information-gain justification,
- apply expensive indicators to every symbol,
- use web search to pad scan counts.

Stop breadth expansion when deep validation has higher expected information value.

# 7. COMPUTE BY INFORMATION VALUE
L1: cheap snapshot / liquidity / momentum / relative-strength proxy / sector.
L2: trend persistence / volatility / volume quality.
L3: historical price series / drawdown / support / pullback / reacceleration.
L4: latest context / event risk / targeted technical or intraday modules only when useful.

# 8. AI INDEPENDENT REVIEW — MANDATORY
After initial candidates are formed, independently challenge them:
- strongest reason to remove each candidate,
- possibility that a stronger candidate was omitted,
- recent surge mistaken for sustainable trend,
- over-reliance on one indicator,
- stale source or bar date mismatch,
- event risk,
- current price-position / chase risk,
- contradictory evidence.

# 9. PROMPT SELF-VALIDATION — MANDATORY
Every run audits BOTH the result and the MSS instruction itself.

Ask:
- Did a lower rule effectively override AI authority?
- Did indicator completion become more important than the objective?
- Did missing indicator or intraday data unnecessarily weaken the judgment?
- Was there duplicated or low-information computation?
- Could a simpler and more direct evidence source replace an expensive rule?
- Did fixed thresholds misfit the current market?
- Did the prompt architecture create avoidable false positives or false negatives?

STRUCTURAL PROBLEM = YES when:
- repeated DATA HOLD blocks useful judgment,
- an indicator costs more than its information value,
- a lower rule mechanically blocks AI authority,
- formal pass conditions dominate actual candidate quality,
- a clearly superior evidence method exists.

If STRUCTURAL PROBLEM = YES:
ROOT CAUSE
→ redesigned evidence rule
→ Candidate Master
→ objective/contract check
→ simulation
→ full regression
→ AI final approval
→ freeze only if PASS
→ current.json updated last
→ pointer re-read verification.

A one-off source failure alone is not structural.
A repeated failure that damages the objective becomes structural.

# 10. SOURCE FLEXIBILITY
Use Source A → B → C → historical/backfill → cross-validation → best available evidence.
If intraday is unavailable:
- seek an alternate source if its information value is high,
- otherwise replace it with daily structure, volume, RS, volatility, or equivalent evidence,
- record the replacement.

# 11. COVERAGE AND CONFIDENCE
Coverage:
FULL / SUFFICIENT / PARTIAL / UNVERIFIED

AI Decision Confidence:
HIGH / MEDIUM / LOW / UNVERIFIED

Specific STC or 60m absence does not automatically imply low confidence.

# 12. RUNTIME PROVENANCE
Record:
- raw universe
- actual unique processed
- funnel counts
- source paths
- SourceFetchedAt / DataBarDate / LatestCompletedTradingDay
- evidence modules used
- evidence modules skipped and reason
- AI override reason
- time-budget stop
- Fabrication = 0

# 13. OUTPUT
1 HEADER
2 MARKET / LEADERSHIP
3 SCAN FUNNEL
4 TOP CANDIDATES
5 EVIDENCE USED
6 AI FINAL + CONFIDENCE
7 DATA INTEGRITY
8 AI SELF-VALIDATION / PROMPT IMPROVEMENT

Keep output concise and non-duplicative.

# 14. VERSION AUTHORITY
current.json alone determines CURRENT.
Frozen masters are immutable.

Promotion:
Candidate
→ objective/contract check
→ simulation
→ full regression
→ AI final approval
→ frozen master
→ current.json updated last
→ pointer/hash re-verified.

# 15. INTENTIONAL v5 REPLACEMENTS
1. Fixed Alarm/STC availability acting as a practical gate
   → replaced by adaptive evidence modules.
2. Result-only self-validation ending at DATA HOLD
   → replaced by mandatory prompt-level structural audit.
3. Final status depending too strongly on fixed timing modules
   → replaced by evidence sufficiency + AI FINAL.

# 16. REGRESSION CONTRACT
01 FACT boundary
02 AI FINAL highest authority
03 no single-indicator veto
04 lower-rule override logging
05 Alarm concept preservation
06 state/timing separation
07 optional MS7
08 optional Daily STC
09 optional 60m STC
10 adaptive evidence
11 trend evidence
12 sustainability evidence
13 timing evidence adaptive
14 risk evidence
15 evidence sufficiency
16 intraday replacement allowed
17 Dynamic Universe
18 KR/US independent
19 one-pass bulk preference
20 no repeated full rescan
21 time budget
22 early stop
23 progressive compression
24 relative strength
25 volume/liquidity
26 drawdown/pullback
27 breakout/reacceleration
28 sector leadership
29 event/fundamental risk
30 chase-risk check
31 completed-bar integrity
32 AI independent review
33 adversarial rejection
34 false-positive check
35 false-negative check
36 prompt self-validation mandatory
37 objective-alignment audit
38 efficiency audit
39 AI-authority audit
40 recurring DATA HOLD structural trigger
41 automatic Candidate Master improvement
42 simulation before freeze
43 full regression
44 AI final approval
45 no fabrication
46 SourceFetchedAt
47 DataBarDate
48 LatestCompletedTradingDay
49 stale mismatch check
50 source flexibility
51 coverage/confidence separation
52 runtime provenance
53 evidence-used logging
54 skipped-evidence logging
55 time-budget output
56 concise output
57 frozen immutable
58 single-current pointer
59 pointer updated last
60 pointer reread
61 historical preservation
62 semantic versioning
63 v5 structural replacement documented
64 self-improvement not reduced to DATA HOLD reporting
65 recurring failure triggers structural review
66 AI judgment allowed without STC when evidence sufficient
67 positive STC does not force AI selection
68 candidate quality over indicator completeness

Any FAIL blocks promotion.

# 17. OFFICIAL EXECUTION
CURRENT resolution
→ freshness/date validation
→ valid asset reuse
→ one-pass open-market scan
→ progressive compression
→ candidate-specific evidence selection
→ latest context/risk review
→ independent AI review
→ AI FINAL + confidence
→ prompt self-validation
→ structural-problem decision
→ automatic improvement if needed
→ output.

STC, 60m, or MS7 unavailability is not itself an execution failure.
