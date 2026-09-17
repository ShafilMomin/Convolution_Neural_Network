# Verification notes

Review date: 17 September 2026.

Checks ran locally in Python 3.10. Only the explicitly listed checks were run; full neural-network training was not executed. Results are from this dataset and setup, not guaranteed real-world performance.

## convolutional_neural_network.ipynb

```json
{
  "check": "syntax only; image dataset and TensorFlow unavailable"
}
```

## Packages

```json
{
  "numpy": "2.2.6",
  "pandas": "2.3.3",
  "matplotlib": "3.10.9",
  "scikit-learn": "1.7.2",
  "scipy": "1.15.3",
  "nltk": "3.10.3",
  "xgboost": "3.2.0"
}
```

TensorFlow was not installed in the review environment. ANN checks cover preprocessing only; CNN checks cover syntax only. Their historical training outputs are described separately in their READMEs.
