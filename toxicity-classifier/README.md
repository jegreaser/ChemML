# Antioxidant Response Toxicity Classification

Binary classifier to predict if molecules activate the antioxidant response pathway (SR-ARE), an important indicator of oxidative stress toxicity.

## Results

**Test Set Performance:**
- Accuracy: 75.29%
- Precision: 43.93%
- Recall: 74.47%
- F1 Score: 49.30% 

![Confusion Matrix](confusion_matrix.png)

The model correctly identifies ~70% of toxic molecules, which is the priority in a setting where missing toxic molecules is far more costly than missing non-toxic molecules.

## Dataset

The model uses the Tox21 dataset to train molecules that are toxic along the SR-ARE (Stress Response - Antioxidant Response Element) assay.
- Total molecules: 5,825
- Class distribution: 84% non-toxic, 16% toxic
- Features: 13 molecular descriptors computed from SMILES (molecular weight, LogP, hydrogen bond donors/acceptors, TPSA, ring counts, etc.)

## Model

Feedforward neural network:
- Architecture: 128 → 64 → 32 → 2
- Dropout: 0.2
- Total parameters: ~12,000
- Loss function: CrossEntropyLoss with class weighting

## Class Imbalance Challenge

Initial results had 85% accuracy, due to the large class imbalance heavily skewed towards non-toxic molecules. Applying class weighting (5:1 ratio) to prioritize detecting toxic molecules, improved recall to 74% at the cost of lower precision.
