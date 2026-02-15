 # Molecular Solubility Prediction

A neural network model coded with PyTorch to predict the solubility of small molecules based on molecular descriptions.

## Results

- RMSE: 0.7436
- MAE:  0.5217
- R²:   0.8820

The model scores well on predictive accuracy benchmarks with the ESOL dataset.

![Predictions_png]

## Dataset

Molecules from the ESOL dataset are analyzed by factoring in 13 molecular descriptors. Molecules are interpreted by SMILES strings through RDKit:
- Molecular weight, LogP, hydrogen bond donors/acceptors
- Topological polar surface area, rotatable bonds
- Ring counts (aromatic, saturated, aliphatic)
- Molar refractivity, Balaban J index, molecular complexity

## Model Architecture

Feedforward neural network with:
- Input: 13 molecular descriptors
- Hidden layers: 256 → 128 → 64 → 32 neurons
- Output: Predicted log(solubility)
- Dropout regularization (0.2) to prevent overfitting
- Total parameters: ~43,000

## Requirements
```
pandas
numpy
torch
scikit-learn
matplotlib
rdkit
```

Install with: `pip install pandas numpy torch scikit-learn matplotlib rdkit`

## Usage

Run the Jupyter notebook or:
```python
python solubility_predictor.ipynb
```

The script trains the model, evaluates on test set, and generates visualization plots.

