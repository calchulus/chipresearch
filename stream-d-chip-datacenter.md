# Stream D — Datacenter chip research findings (2026-08-16)

## 1. Scope reviewed

All 10 files read in full (paths under `ai-compute-hardware/ai-chip-research/`):

| File | Doc date (per manifest) | Subject |
|---|---|---|
| `datacenter-training/training-chip-market.md` | 2026-06-18 | Training chip landscape, NVIDIA/AMD/Cerebras/TPU/Trainium specs + pricing |
| `datacenter-inference/amd-instinct.md` | 2026-06-18 | MI300/MI325X specs, vs-NVIDIA comparisons, ROCm status |
| `datacenter-inference/cerebras-wafer-scale.md` | 2026-06-18 | WSE-1/2/3, IPO, OpenAI/AWS/Meta deals, financing history |
| `datacenter-inference/emerging-competitors.md` | 2026-06-24 | Tenstorrent, SambaNova, Graphcore, Rain, TPU, Trainium, Maia, MTIA, Etched, Lightelligence |
| `datacenter-inference/groq-lpu.md` | 2026-06-18 | LPU architecture, GroqCloud, NVIDIA $20B licensing deal |
| `datacenter-inference/lightelligence-pace2-analysis.md` | 2026-06-24 | Photonic hybrid PACE2 card specs + comparison table |
| `datacenter-inference/mlcc-capacitor-analysis.md` | 2026-06-23 | MLCC content/cost in AI servers, supply chain (Murata etc.) |
| `datacenter-inference/next-gen-chip-preparation.md` | 2026-06-23 | Preparation strategies for chiplet/SoC/SOI/wafer-scale architectures |
| `datacenter-inference/nvidia-dgx-spark-analysis.md` | 2026-06-24 | DGX Spark TOPS/$ vs edge accelerators |
| `datacenter-inference/tensordyne-logarithmic.md` | 2026-06-18 | Log-math Napier chip, rack claims vs GB300 |

Verification note: one live anchor check succeeded (amd.com confirms MI355X = CDNA 4, FP8 5 PFLOPS dense / 10.1 PFLOPS sparse); a second web check was blocked by permissions, so remaining external anchors rely on established public specs (H100 FP8 dense 1,979 / sparse 3,958 TFLOPS; B100 never shipped as a product).

## 2. Staleness findings

| # | File | Claim | Issue | Severity |
|---|---|---|---|---|
| D-1 | amd-instinct.md | MI300X "current flagship"; MI325X "next-gen"; MI400 "expected 2026-2027" | One generation stale: doc omits MI350X/MI355X (CDNA 4, launched mid-2025, shipping >12 months by review date) and MI355X pricing entirely. By 2026-08 the current-gen debate is MI355X vs Blackwell, and MI400/Helios status is the live question. | H |
| D-2 | training-chip-market.md | NVIDIA pricing: A100 $10–15k, H100 $25–35k, H200 $30–40k, B200 $35–45k "(est.)" | Undated estimates. H100/A100 resale prices have fallen sharply since 2024; using these in capex math likely overstates H-series build costs. Most load-bearing numbers in the stream are the weakest-sourced. | H |
| D-3 | training-chip-market.md | "Vera Rubin R100 … 2026, TBD" | Fastest-moving roadmap claim in the stream; Rubin launch/ramp status (and Rubin CPX) will have changed between June and Aug 2026. | H |
| D-4 | tensordyne-logarithmic.md | "Taped out 2026; entering HVM at TSMC" | Pre-production status claim in the highest-risk window (tape-out→HVM); no independent validation; status likely moved. | H |
| D-5 | cerebras-wafer-scale.md | FY2025 financials ($510M rev, $87M NI), IPO pricing ($185, $95B val) | Q2 2026 earnings are likely out by mid-Aug 2026; share price and OpenAI deployment milestones will have moved. | M |
| D-6 | cerebras-wafer-scale.md | OpenAI 750 MW / $10B "through 2028" | Deal mechanics have been reported as fluid; deployment status as of 2026-08 needs re-verification. | M |
| D-7 | groq-lpu.md | "Raising $650M (May 2026)"; LPU v2 "in development, TBD" | Post-NVIDIA-deal trajectory (round closed/abandoned, LPU v2 fate, cloud pivot) is exactly the kind of thing that moves in 2 months. Groq is now effectively semi-captured by NVIDIA — market-structure claim needs refresh. | M |
| D-8 | training-chip-market.md | MI350X FP8 "2,387", MI355X FP8 "2,517 TFLOPS" | Factually wrong as written (not just stale): AMD publishes MI355X FP8 at 5 PFLOPS dense / 10.1 sparse (verified on amd.com). Doc's figures look like FP16-class numbers; understates MI355X by 2–4×. | M |
| D-9 | training-chip-market.md | B100 listed as shipping 2024 product | B100 was superseded by B200 and did not ship as a product; should be removed from the product table. | M |
| D-10 | training-chip-market.md | B300 FP8 = 12,000 TFLOPS | NVIDIA markets GB300-era figures in FP4/sparse terms; 12k FP8 dense per GPU is unverified — likely precision/convention confusion. | M |
| D-11 | emerging-competitors.md | Rain AI "early-stage/stealth"; Etched "stealth"; Graphcore "uncertain" | Company statuses move fast; Rain AI in particular had public distress/wind-down reports — status must be re-verified before citing. | M |
| D-12 | emerging-competitors.md | SambaNova SN50 tok/s claims; "TPU 8i / 8t" as latest TPU lineup | Vendor performance claims + fast-moving Google TPU roadmap, both undated. | M |
| D-13 | mlcc-capacitor-analysis.md | NVL72 = 440k MLCCs; Vera Rubin = 600k; ASPs +68% YoY; lead times 16–24 wks | Time-sensitive supply-chain stats from a single X thread (@demian_ai) + unnamed analyst notes, now ~2 months old. | M |
| D-14 | tensordyne-logarithmic.md | "NVIDIA Rubin ships 2027" | Contradicts training doc's Rubin 2026 and will have moved with NVIDIA announcements. | M |
| D-15 | amd-instinct.md | AMD FY2025 revenue "~$28B" | Actual FY2025 results are now public; figure should be replaced with reported actuals. | L |
| D-16 | amd-instinct.md | MI300X $10–15k, "50% cheaper than H100" | Undated price claim; gap vs NVIDIA shifts with H100 price declines and MI325X/MI355X availability. | M |
| D-17 | nvidia-dgx-spark-analysis.md | "$3,999 discounted price" | Promo pricing moves; low stakes since the device is not DC-relevant. | L |
| D-18 | next-gen-chip-preparation.md | Dated facts inherit cerebras-doc staleness ("Cerebras IPO May 2026 at $95B") | Mostly evergreen strategy content; minimal staleness risk beyond inherited facts. | L |

Pattern: no claim-level timestamps anywhere in the stream; only file mtime dates. Roadmap and pricing claims are indistinguishable from settled facts on the page.

## 3. Internal inconsistencies (cross-doc spec/price conflicts)

1. **MI300X FP8: 1,307 TFLOPS (training doc) vs 2,615 TFLOPS (amd-instinct).** Both numbers exist in reality but correspond to different conventions (dense vs with-sparsity); neither doc labels the convention, so the two comparison regimes are silently inconsistent.
2. **H100/H200 FP8: 1,979 (training doc) vs 3,958 (amd-instinct comparison tables).** Same dense/sparse conflation. The amd-doc conclusion "H100 +51% FP8" is only valid within its own sparse convention; the training doc's numbers imply a different competitive gap. This matters: it's the basis for "NVIDIA still leads on raw FP8."
3. **CDNA 4 attribution conflict.** Training doc: MI350X/MI355X = CDNA 4 (correct, confirmed on amd.com). amd-instinct: "CDNA 3 (MI300) / CDNA 4 (MI400)" and omits the MI350 series entirely. Direct contradiction between the two docs.
4. **Rubin timing: 2026 vs 2027.** Training doc places Vera Rubin in 2026; tensordyne doc says "NVIDIA Rubin ships 2027, same timeline [as Napier HVM]." One of the two timeline anchors for Tensordyne's competitive window is wrong.
5. **Tensordyne rack power: 120 kW vs 86 kW.** System spec says 120 kW/rack; the GB300 comparison table says "Total rack power 86kW" for both Tensordyne and GB300. The 86 kW figures are chip-only power (288×300W; 72×1.2kW) presented as rack power, contradicting the doc's own spec and flattering the "equal power" framing.
6. **Cerebras WSE-3 mangled in lightelligence comparison table**: "2,500+ TOPS, FP16/32, 20kW+, ~$3M." The 2,500 figure is the tokens/sec number from the Cerebras doc converted into fake TOPS; power is 25 kW in both other docs. Cross-doc unit conflation.
7. **AMD discount magnitude:** "30–50% cheaper" (training doc) vs "50% cheaper" (vs H100) and "60% cheaper" (vs H200) in amd-instinct tables. Minor tension, same direction.
8. **TPU table units mixed (training doc):** v5e pod listed as "393 TFLOPS" alongside v4's "1.1 ExaFLOPS" and Ironwood's "42.5 ExaFLOPS" — 393 TFLOPS is a per-chip-class figure, not a pod figure.
9. **Cerebras die size self-conflict:** overview says "(215mm²)"; the comparison table correctly says 215mm × 215mm (~46,225 mm²).
10. **Consistency checks that PASS** (worth recording): Cerebras WSE-3 transistors/cores/SRAM (4T/900k/44GB) consistent across both docs; CG-3 aggregates arithmetic checks out (192×44GB = 8.4TB, 192×4T = 768T); MI325X "same compute as MI300X" consistent; Cerebras node "$3M+ / 25 kW" consistent across cerebras/amd/lightelligence docs; edge-accelerator table (Axelera 214 TOPS €179, DeepX 25/$85, Hailo 26/$90) identical in dgx-spark and lightelligence docs; Groq total funding ~$1B consistent.

## 4. Speculation vs fact flags

- **Tensordyne (highest risk).** Every performance number (13× tok/s, 17× tok/MW, 608 PFLOPS/rack, 2,730 tok/s, "$33M additional annual revenue per rack") is a CEO/vendor claim about pre-production, simulation-grade silicon from a company with no named customers and no disclosed funding. The doc partially labels this ("Key Claims (from CEO…)", a caveat noting ~3.3× real per-chip advantage, a risk table marking benchmarks "simulation … real-world TBD") — better than average — but the GB300 comparison table presents claimed numbers in spec-table format without a "claimed" marker. Cross-doc handling is better: cerebras doc says "2,730 tok/s (claimed)", amd doc says "None announced" customers.
- **Lightelligence.** Vendor spec sheet with price and power listed as TBD — the two fields a buyer needs are missing. "10–100× efficiency" is properly labeled theoretical. Comparison table contains the mangled Cerebras row (see §3.6).
- **MLCC doc.** MLCC counts per board/rack, ASP +68% YoY, and Murata share (40%/70%) are presented as fact but trace to a single X thread and unnamed analyst notes. Should carry a sourcing label.
- **Groq.** "$500M (2025)" revenue is likely a projection; "3M+ developers" is a vendor metric. The $20B NVIDIA licensing deal itself is dated and corroborated across docs.
- **Cerebras.** Inference speed records (Llama 4 Maverick 2,500 tok/s, "15–30× faster") are vendor benchmarks presented as fact; "$10B" OpenAI value is reported, not contract-disclosed. Customer-concentration figures (MBZUAI+G42 = 86%) appear S-1-derived — good.
- **Training doc.** Trainium customer list "Apple (AI services)" and "OpenAI (compute capacity)" mixes reported deals with rumor; needs sourcing. Market-size table (~$50–60B, shares) is unsourced.
- **Emerging competitors.** SambaNova tok/s figures and Tenstorrent "industry-leading benchmarks" are vendor claims presented without labels.

## 5. Relevance notes (mlcc, next-gen-prep)

- **mlcc-capacitor-analysis.md** — covers MLCC counts per AI server board/rack (GB200: 6.5k; NVL72: 440k; Vera Rubin: 600k), capacitor cost in BOM (~$3k→~$12k/cabinet), why AI chips need them (low-voltage/high-current transients), workarounds (IVR, chiplet power delivery, Cerebras wafer-scale), and MLCC supply chain (Murata/TDK/Taiyo Yuden/Yageo tickers, lead times, ASP inflation). **Verdict: tangential for this stream.** It's a component/supply-chain BOM analysis — relevant to GPU pricing/lead-time context, but it answers "who supplies the capacitor layer," not "what should a 3–15 MW DC buy." Belongs in a supply-chain stream or should be flagged as context-only.
- **next-gen-chip-preparation.md** — covers preparation strategies for chiplet/SoC/SOI/wafer-scale architectures, aimed at hardware companies (EDA tools, UCIe), software companies, researchers, and investors, with a 2026–2035 phase timeline. **Verdict: tangential.** It is chip-industry strategy content with almost nothing actionable for a datacenter builder; the few concrete facts it carries (Cerebras IPO valuation) are inherited from other docs. Belongs in a chip-investment/supply-chain stream, not DC hardware procurement.

## 6. Load-bearing claims for the DC thesis

Docs that matter for "what should a 3–15 MW GPU datacenter buy": **training-chip-market.md** (NVIDIA pricing table), **amd-instinct.md** (AMD price/perf for inference fleets), **cerebras-wafer-scale.md** (node cost/power for inference-DC design), **groq-lpu.md** (inference market structure post-NVIDIA-deal), and **tensordyne-logarithmic.md** (rack-level power/perf scenario only). DGX Spark, Lightelligence, MLCC, and next-gen-prep are non-core.

Top 5 hardware-pricing claims:

| Claim | File | Sourced? | Assessment |
|---|---|---|---|
| NVIDIA B200 ~$35–45k, 1,000W | training-chip-market.md | No ("est.") | The central capex input for a new 3–15 MW build. Order-of-magnitude plausible vs public reporting, but unsourced; must be refreshed with 2026 contract/street pricing before any capex math. |
| H100 ~$25–35k / H200 ~$30–40k | training-chip-market.md | No ("est.") | Likely stale-high given resale-market declines; would overstate capex for H-series builds. Verify against current resale quotes — cheapest way to change the thesis math. |
| AMD MI300X ~$10–15k; "30–50%/50–60% cheaper than NVIDIA" | amd-instinct.md, training doc | No | Directionally consistent with historical ASPs, but the doc has no price for the actually-current MI355X — the AMD cost-advantage pillar of the thesis is currently unpriced in the repo. |
| Cerebras node $3M+ at 25 kW | cerebras-wafer-scale.md | Partial (company/reported) | Consistent across 3 docs; implies ~$120k/kW compute — key for any inference-focused DC design. Should be re-checked against post-IPO disclosures. |
| Tensordyne 120 kW/rack, "$33M additional annual revenue per rack" | tensordyne-logarithmic.md | No — vendor claim | Unusable as a planning input pre-production; keep only as a scenario with an explicit "claimed" tag. (DGX Spark $3,999/1 PFLOP FP4 is a verified product spec but not DC-scale relevant.) |

## 7. Stream summary

The ten docs form a coherent June-2026 snapshot of training and inference silicon, but the snapshot is decaying exactly where the investment thesis lives. **Worst staleness** is in amd-instinct.md (a full generation behind — MI300X still "flagship," MI355X omitted), the NVIDIA pricing table (undated estimates, H-series likely overstated), the Rubin roadmap line (2026, TBD), and Tensordyne's HVM status. The most consequential **cross-doc conflict** is the dense-vs-sparse FP8 convention mix-up: MI300X is 1,307 TFLOPS in one doc and 2,615 in another, and H100 is 1,979 vs 3,958 — the same chips, two different competitive narratives — plus a direct CDNA-4 attribution contradiction (MI350 series vs MI400) and Rubin 2026-vs-2027. **Speculation handling is mixed**: Tensordyne's doc is admirably caveated in prose but presents vendor claims in spec-table format; Lightelligence omits price/power entirely; the MLCC doc presents single-source X-thread data as fact. For the 3–15 MW thesis, only four or five docs are load-bearing, and the core weakness is that **every GPU unit price in the repo is an unsourced estimate** — the single most decision-relevant input is the least verifiable. Recommended fixes: adopt one FP8 convention (label dense vs sparse) across all docs, refresh NVIDIA/AMD pricing with dated sources, correct MI350/MI355X specs and CDNA-4 attribution, tag Tensordyne/Lightelligence/SambaNova tables as vendor claims, and relocate MLCC + next-gen-prep to a supply-chain/industry stream.
