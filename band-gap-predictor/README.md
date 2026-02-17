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

| Split      | Size |
|------------|------|
| Train      | —    |
| Validation | —    |
| Test       | —    |


---

## ⚙️ Training

To retrain the model from scratch:

```bash
python train.py --config configs/default.yaml
```

Key hyperparameters are defined in `configs/default.yaml`. Results and checkpoints will be saved to `outputs/`.

---

## 📈 Evaluation

To reproduce the test set evaluation:

```bash
python evaluate.py --model model/best_model.pkl --data data/processed/test.csv
```

This will print metrics and regenerate the `predictions.png` scatter plot.

---

## 🔍 Known Limitations

- **High band gap materials (> 6 eV):** Predictions show higher variance, likely due to sparse training data in this regime.
- **Negative predictions:** A small number of predictions fall slightly below zero. These should be clipped to 0 eV in practice, as negative band gaps are unphysical for the targeted material class.
- **Out-of-distribution materials:** Performance may degrade for material families underrepresented in the training set.

---

## 🤝 Contributing

Contributions are welcome! Please open an issue or submit a pull request. For major changes, open an issue first to discuss what you'd like to change.

---

## 📄 License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

---

## 📬 Contact

For questions or feedback, open an issue on GitHub or reach out at `your-email@example.com`.
