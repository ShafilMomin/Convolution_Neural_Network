# Cats vs Dogs: Convolutional Neural Network

A TensorFlow/Keras notebook that learns to classify a picture as a **cat or dog**.

**Python · TensorFlow / Keras · NumPy**

## Dataset: keep it outside GitHub

The image dataset is **not included** because it is large. You can use your existing folders locally or in Google Drive. No GitHub upload is needed.

```text
dataset/
├── training_set/
│   ├── cats/
│   └── dogs/
└── test_set/
    ├── cats/
    └── dogs/
```

Place images inside those class folders. Set `CNN_DATASET_DIR` to the dataset path, or edit `DATASET_DIR` in the notebook. By default, it uses `dataset` locally, or `/content/drive/MyDrive/dataset` after mounting Drive in Colab. It checks for the required folders before training. `.gitignore` excludes the default dataset folder, ZIP archives and saved Keras model files.

The review did not inspect your local images or verify their source/license. Keep training and validation images separate and avoid duplicates across the folders.

## Model and training

```text
64 × 64 RGB image
  → Conv2D(32, 3×3, ReLU) → MaxPool(2×2)
  → Conv2D(32, 3×3, ReLU) → MaxPool(2×2)
  → Flatten → Dense(128, ReLU) → Dense(1, sigmoid)
```

Training images are rescaled to 0–1, with shear, zoom and horizontal-flip augmentation. Validation images are rescaled only. Training uses Adam, binary cross-entropy, batch size 32 and 25 epochs.

The folder named `test_set` is used as **validation data during training**. It is not a separate final test set.

## Single-image prediction

Set `IMAGE_PATH` to an existing image. The prediction cell resizes it to 64 × 64, rescales pixels to 0–1, uses a **0.5 threshold**, and reads class names from the training loader's mapping. The displayed sigmoid score is a model output, not a calibrated guarantee of correctness.

These steps correct the earlier prediction cell, which omitted rescaling and compared its sigmoid output to exactly 1. The model architecture is otherwise preserved. A Drive file-listing cell was removed so the notebook does not publish unrelated folder names.

## Results and verification

Original saved outputs reported **8,016 training images**, **2,000 validation images**, and **80.6% validation accuracy at epoch 25**. These are historical outputs, not newly verified results. The actual image folders were not available during this review.

Updated code passed Python syntax checks; training and real-image inference were **not executed**. Old outputs were cleared. Run the notebook with your dataset before reporting new results. The original environment reported TensorFlow 2.20.0. This tutorial retains the legacy ImageDataGenerator API.

## Run

Open [the notebook](convolutional_neural_network.ipynb) in local Jupyter or Colab. Install the dependencies in a virtual environment for local use:

```bash
python -m pip install tensorflow==2.20.0 numpy notebook
python -m notebook
```

Set the dataset path and run cells in order. Colab's Drive mount is optional; the notebook skips it outside Colab.

[Verification notes](VALIDATION.md) · [TensorFlow image loader documentation](https://www.tensorflow.org/api_docs/python/tf/keras/preprocessing/image/ImageDataGenerator)
