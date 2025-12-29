## Exercise B — Run-to-Run Variance & Stability Analysis

### What did I build?
I built a deterministic framework to measure run-to-run instability in LLM outputs without canonical labels. The system aligns extracted semantic items across multiple runs using evidence-text overlap and computes safety-critical stability metrics.

### Key assumptions
- Evidence grounding is the strongest signal for semantic identity
- Polarity changes are high-risk and unacceptable
- Bucket drift is acceptable only within bounded ranges
- Stability is evaluated per journal independently

### System breakdown
- Loader: reads LLM run outputs
- Matcher: aligns items via evidence overlap
- Metrics: agreement rate, polarity flip rate, bucket drift rate
- Report: per-journal stability summary

### Determinism & safety controls
- Evidence-first deterministic matching
- Explicit polarity flip detection
- No hallucinated merges
- Abstains when evidence is insufficient

### Evaluation strategy
Measured stability across runs using:
- Agreement rate
- Polarity flip rate
- Bucket drift rate (intensity, arousal, time)

### Edge cases & limitations
- Token overlap may underperform on very short spans
- Does not resolve implicit or cross-sentence evidence
- Bucket boundaries are heuristic

### Future improvements
- Learned similarity thresholds
- Confidence-weighted aggregation
- Production monitoring dashboards
