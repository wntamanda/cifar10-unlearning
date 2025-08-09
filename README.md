# CIFAR-10 Machine Unlearning

Minimal unlearning MVP:
1) **BASE**: train on {bird, cat, dog, truck}
2) **FULL**: add **airplane** and train
3) **RETRAIN_BASE**: scratch baseline without airplane (gold standard “forgotten” model)

We evaluate on:
- **Overall** (all 10 classes)
- **Forget (airplane)** only
- **Retain (non-airplane)** all other classes

We also compute an **Unlearning Score** for new methods vs:
- **RETRAIN_BASE** (target behavior on airplane)
- **FULL** (target behavior on retain classes)

## Setup
```bash
pip install torch torchvision scikit-learn matplotlib
```

## Run

Open the notebook:

- `cifar10_unlearning.ipynb`

The notebook will produce:
- `splits_train.json`, `splits_test.json`
- checkpoints: `model_base.pt`, `model_full.pt`, `model_retrain.pt`

## Config

Edit `config.json` to tweak:
- Seed
- Epochs
- Learning rate
- Base / forget class IDs
- Samples per class

## Interpreting Results

- After **FULL**, airplane accuracy should be high.
- After **RETRAIN_BASE**, airplane accuracy ≈ 0% and retain accuracy close to BASE.
- An **unlearned** model should:
  - Push airplane accuracy near RETRAIN_BASE (≈ 0%)
  - Keep retain accuracy near FULL

## Next Steps

- Implement Gradient-Ascent Forgetting + Retain CE
- Add EWC / KD regularization
- Compare **Unlearning Score** vs **RETRAIN_BASE** baseline