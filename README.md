# CIFAR-10 Unlearning Scratchpad

Tiny notebook that experiments with removing the **airplane** class from CIFAR-10.

## What it does 

1. **Reference models**
   * **BASE** : trained on 4 classes: bird, cat, dog, truck  
   * **FULL** : same 4 classes **+ airplane**  
   * **RETRAIN_BASE** : fresh run on the 4 classes (ideal “forgotten” model)

2. **Unlearning variants** : start from **FULL** and apply:
   * GAR (uniform-KL + CE)
   * optional EWC diagonal penalty
   * optional masked knowledge-distillation

3. **Metrics**
   * *Forget accuracy* : performance on airplane images
   * *Retain accuracy* : performance on everything else
   * *Unlearning score* : 1 if it matches RETRAIN_BASE on forget and FULL on retain, 0 if it fails both.

## Disclaimer 

This repo is a learning sandbox, not a polished reproduction of any paper.  
Expect shortcuts, rough edges, and room for improvement :)