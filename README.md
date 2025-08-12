# CIFAR-10 Machine Unlearning (Notebook)

Tiny lab to explore **unlearning** by removing one class (airplane) from CIFAR-10.

## Pipeline
- **BASE**: train on retain classes {bird, cat, dog, truck}
- **FULL**: train on retain + airplane (forget class)
- **RETRAIN_BASE**: gold-standard “forgotten” model (retain only)

## We report:
- Forget (airplane) accuracy
- Retain (non-airplane) accuracy
- Unlearning Score: closer to RETRAIN_BASE on forget & closer to FULL on retain (α=0.5)

(Checkpoints & raw metrics JSON are saved under `results/` but git-ignored.)