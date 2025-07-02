# 🌱 Soil Classification Using EfficientNet

This project involves classifying soil images into four categories using deep learning and transfer learning techniques. It was developed as part of the **Soil Image Classification Challenge (annam.ai)**.

## 🧠 Model Overview

- **Base Model**: EfficientNetB3 (pretrained on ImageNet)
- **Custom Head**: GlobalAveragePooling + Dense Layers
- **Optimizer**: Adam
- **Loss**: Categorical Crossentropy
- **Input Shape**: 384 x 384 x 3

## 📁 Dataset

The dataset contains soil images labeled into the following classes:

- **Alluvial Soil**
- **Black Soil**
- **Clay Soil**
- **Red Soil**

The original dataset formats:
- `train/`: Image directory
- `train_labels.csv`: Image IDs and their corresponding `soil_type`
- `test/`: Test image directory
- `test_ids.csv`: List of test image IDs

## 🔄 Preprocessing

- All images converted to `.jpg` format
- Image augmentation using `ImageDataGenerator`
- Train-validation split (80/20 stratified)
- Rescaling pixel values between [0, 1]

## ⚙️ Training Pipeline

1. **Transfer Learning Phase**: Freeze EfficientNet base, train head layers
2. **Callbacks**:
   - ModelCheckpoint
   - EarlyStopping
   - ReduceLROnPlateau

## 📊 Evaluation

Model is evaluated on validation data using:
- Accuracy
- Classification report (Precision, Recall, F1-score)

Also identifies the **worst-performing class** based on F1-score.

## 🧪 Inference

- Predictions generated on the test set.
- Output saved to `submission.csv` containing:
  - `image_id`
  - `soil_type`

## 🖼️ Sample Output

Class-wise F1-scores:

Alluvial soil &nbsp;:   0.990476 <br>
Black Soil  &nbsp;&nbsp;&nbsp; :   0.978723 <br>
Clay soil  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;   :   1.000000 <br>
Red soil    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  :   1.000000 <br>

---

## 👥 Contributors

- **Shubham Kumar Das** (Model Optimization)
- **Chataniya Dhanai** (Primary Developer)

---

## 📦 Dependencies

- TensorFlow ≥ 2.8
- Pandas
- scikit-learn
- PIL
- Matplotlib
- EfficientNet

## 🚀 How to Run

1. Upload dataset to Kaggle (or local system)
2. Run the notebook end-to-end in a GPU environment
3. The final submission file will be saved as `submission.csv`

