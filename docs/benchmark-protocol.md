# Benchmark protocol

## Why the splits are used this way

BETH's training and validation splits are reported to contain no attacks; `evil` events appear only in the
test split. That shapes the protocol. Verify with `python -m triage describe` on each file first.

| Split | Role | What we measure |
|---|---|---|
| Train | Fit the baseline (what is routine). No labels used. | Nothing |
| Validation | Attack-free, so every Medium/High alert is a false alarm. Tune `rules.yaml` here. | False-alarm rate |
| Test | Frozen settings, run once. | Precision, recall, F1 against `evil`; analyst workload |

Do not tune anything on test. If a result on test prompts a rule change, say so in the report and
re-validate; do not present the post-change number as a clean held-out result.

## Metrics

- **Detection vs. `evil`:** precision, recall, F1 at Medium+ (score >= 40) and High (>= 70), at the action-group level (a group is positive if any event is `evil`) and at the event level (each event inherits its group's tier).
- **Workload:** share of groups auto-logged (Low) and share needing review. This is the framework's stated goal.
- **False alarms:** Medium+ and High alert rates on validation.
- **Label disagreements:** groups labeled malicious but scored Low, and groups scored High but labeled benign. These are written to `artifacts/review_queue.csv`. Read them by hand and pick a few to discuss in the report; the sshd case is the model.

## Baselines

1. **`sus` flag:** predict `evil` whenever `sus` is set. Shows what the dataset's own flag buys you.
2. **Isolation Forest:** unsupervised, single-event features, fit on train. Its alert threshold is set so its alert rate on validation equals the framework's, so both methods spend the same false-alarm budget.

If the framework does not beat these, report that honestly and use the review queue to explain why.

## Reporting rules

- Report test numbers from one frozen run, with the `rules.yaml` version (git commit hash) that produced them.
- Never report numbers from `data/sample`. Those prove the pipeline runs and nothing else.
- State the limits: one test host, honeypot traffic, and rules written by the team (so some tuning to this data is unavoidable).
