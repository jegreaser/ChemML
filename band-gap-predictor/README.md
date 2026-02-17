# 🔬 Band Gap Predictor

A machine learning model for predicting the electronic band gap (eV) of materials from structural and compositional features.

## Model Performance

Test Set Results:

RMSE: 0.7274 eV
MAE: 0.4610 eV
R²: 0.7926

The model explains ~79% of the variance in band gap values, with a MAE of 0.4610 which puts it in the range of top models for this task.

<img width="2372" height="2371" alt="predictions" src="https://github.com/user-attachments/assets/937aa1e7-4c49-4cf3-b012-cae4e242452d" />

> This scatter plot demonstrates the models predictions vs actual values. Points along the red line represent perfect predictions. The model becomes less successful at about 6 eV due to a smaller sample pool in that range.

## Dataset

The model is trained on a dataset of inorganic materials with DFT-computed band gaps from matliner.

Train set: 74321 samples
Validation set: 15875 samples
Test set: 15917 samples

## 🔍 Known Limitations

- **High band gap materials (> 6 eV):** There are less samples in this regime, so predictions show high variance.
- **Negative predictions:** A few band gap predictions fall below zero. In practice, these predictions would be clipped to zero for maximum accuracy.
- **Out-of-distribution materials:** Some poor predictions can be attributed to various material families that are underrepresented in the dataset.
