# GrainPalette – A Deep Learning Odyssey in Rice Type Classification

GrainPalette is a deep learning-powered web application that classifies rice grain types using transfer learning. It allows users to upload an image and receive real-time predictions through a clean and modern web interface built with Flask.

---

## 🖼️ Project Preview

<!-- Row 1 -->
<p align="center">
  <img src="static/Screenshot 2025-06-23 191936.png" alt="Home page" width="45%" style="margin: 10px;" />
  <img src="static/Screenshot 2025-06-23 192016.png" alt="Detail page" width="45%" style="margin: 10px;" />
</p>

<!-- Row 2 -->
<p align="center">
  <img src="static/Screenshot 2025-06-23 191959.png" alt="Prediction page" width="75%" style="margin: 10px;" />
</p>

---

##  Live Demo Video

Watch the demo of the GrainPalette app in action!

[![GrainPalette Demo]()](https://youtu.be/1XF4mfGDjLs?feature=shared)

---

## 📌 Features

- 🧠 Built with **Transfer Learning** using Keras/TensorFlow
- 🌾 Classifies rice into 5 types:
  - Basmati
  - Jasmine
  - Arborio
  - Ipsala
  - karacadag
- 🖼️ Upload an image and get predictions instantly
- 📊 Shows prediction with confidence score
- 🧠 Model code available in `model.ipynb`
- 🎨 Modern UI with navbar, background, and animations

---

## 🛠️ Project Development Process

The development of **GrainPalette** followed a structured approach integrating deep learning, data preprocessing, and web application development. Below is a detailed breakdown of the process:

---

### 📁 1. Dataset Collection & Preparation

- The dataset was organized into **five folders**, each representing a rice type: `Basmati`, `Jasmine`, `Arborio`, `Brown`, and `White`.
- Each folder contained multiple rice grain images captured in similar conditions.
- The image directory structure helped in **automatic labeling** using `ImageDataGenerator` or `os.walk()`.

> **Structure:**
> ```
> dataset/
> ├── Basmati/
> ├── Jasmine/
> ├── Arborio/
> ├── Ipsala/
> └── Karacadag/
> ```

---

### 🧹 2. Data Preprocessing

- All images were resized to a consistent size `(224x224)` for compatibility with CNN models.
- Pixel values were normalized by dividing by 255.0.
- Data was split into **training** and **validation** sets with an 80-20 ratio.
- Techniques such as **augmentation** (rotation, zoom, flips) were optionally used to improve generalization.

---

### 🧠 3. Model Building Using Transfer Learning

- A **pre-trained CNN architecture** (e.g., `MobileNetV2`, `VGG16`, or `ResNet50`) was used as a base model.
- The top layers were **customized** to match the 5-class classification task.
- The model was compiled using:
  - `Adam` optimizer
  - `categorical_crossentropy` loss
  - `accuracy` as the evaluation metric

- Training was done using Keras with `model.fit()` and included callbacks like `EarlyStopping` to avoid overfitting.

---

### 📈 4. Model Evaluation

- Accuracy and loss graphs were plotted for training and validation sets.
- A **classification report** was generated to evaluate precision, recall, F1-score.
- Confusion matrix and sample predictions were visualized to understand model behavior.

---

### 💾 5. Model Saving

- Once trained, the model was saved as a `rice.h5` file using:

```python
model.save("rice_model.h5")

---

## ⚙️ Installation & Run Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/GrainPalette.git
cd GrainPalette

conda create -n grainpalette python=3.9
conda activate grainpalette


python app.py

