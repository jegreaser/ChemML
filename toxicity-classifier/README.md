# Antioxidant Response Toxicity Classification

Binary classifier to predict if molecules activate the antioxidant response pathway (SR-ARE), an important indicator of oxidative stress toxicity.

## Results

**Test Set Performance:**
- Accuracy: 76.2%
- Precision: 37.6%
- Recall: 72.3%
- F1 Score: 49.5%

![Confusion Matrix](confusion_matrix.png)

The model correctly identifies 72% of toxic molecules, which is the priority metric for toxicity screening where missing dangerous compounds is more costly than false alarms.

## Dataset

Uses the Tox21 dataset focused on the SR-ARE (Stress Response - Antioxidant Response Element) assay.
- Total molecules: 5,825
- Class distribution: 84% non-toxic, 16% toxic
- Features: 13 molecular descriptors computed from SMILES (molecular weight, LogP, hydrogen bond donors/acceptors, TPSA, ring counts, etc.)

## Model

Feedforward neural network:
- Architecture: 128 → 64 → 32 → 2 (binary output)
- Dropout: 0.2-0.3 for regularization
- Total parameters: ~12,000
- Loss function: CrossEntropyLoss with class weighting

## Class Imbalance Challenge

Initial results showed 85% accuracy but only 40% recall - the model was biased toward predicting "non-toxic" due to class imbalance. Applied class weighting (5:1 ratio) to prioritize detecting toxic molecules, improving recall to 72% at the cost of lower precision. This tradeoff is appropriate for drug safety applications.

![
