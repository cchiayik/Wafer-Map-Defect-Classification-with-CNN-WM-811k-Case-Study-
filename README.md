# 🧠 Wafer Map Defect Classification with CNN (WM-811k Case Study)
# 📌 Project Overview

This project explores the use of Convolutional Neural Networks (CNNs) for semiconductor wafer defect pattern classification using the WM-811k dataset.

Defect pattern recognition is critical in semiconductor manufacturing for improving yield analysis and fault detection. By leveraging deep learning, we aim to automatically classify wafer maps into multiple defect categories, reducing reliance on manual inspection.

##⚡ Key Features

Built with TensorFlow/Keras in Python (experimented on Kaggle).

Implemented two experimental pipelines:

Standard Train/Validation split

K-Fold Cross Validation for robustness

Applied class balancing strategies (weighted loss, smoothing) to address dataset imbalance.

Achieved ~85% validation accuracy with strong generalization performance.

## 🔑 Key Highlights

- **Dataset**: WM-811k (semiconductor wafer map defect dataset)  
- **Approach**: Convolutional Neural Network (CNN) implemented in Keras/TensorFlow  
- **Pipelines**:  
  - Hold-out validation (train/test split)  
  - 5-Fold Cross Validation for robustness  
- **Techniques Used**:  
  - Class balancing with smoothed weights  
  - Data augmentation for generalization  
  - Early stopping to prevent overfitting  
- **Performance**:  
  - ~85% accuracy across folds  
  - Strong classification on majority classes  
  - Improved stability on minority defect classes  
- **Evaluation Tools**: Accuracy/Loss curves, confusion matrices, and classification reports  

## 🚀 How to Run / Usage

## ⚠️ Full implementation is not shared due to dataset and IP sensitivity.
Instead, the workflow is summarized below:

Data Preparation

Extract wafer maps and resize to a consistent shape (e.g., 64×64).

Normalize pixel intensities.

Encode defect categories as integer labels.

Model Architecture

CNN with stacked Conv2D → BatchNorm → Pooling layers.

Dense layers with dropout for generalization.

Softmax output for multi-class classification.

# (Pseudocode)
model = Sequential([
    Conv2D(...), BatchNormalization(), MaxPooling2D(...),
    Conv2D(...), BatchNormalization(), GlobalAveragePooling2D(),
    Dense(..., activation="relu"), Dropout(0.5),
    Dense(num_classes, activation="softmax")
])

## Training Strategy

Baseline: Train/Validation split with data augmentation.

Robust: Stratified K-Fold Cross Validation.

Optimizer: Adam (tuned LR).

Loss: Categorical cross-entropy with class weights to handle imbalance.

EarlyStopping + ModelCheckpoint for best model retention.

Evaluation

Monitor training/validation accuracy & loss.

Generate classification report & confusion matrix.

Compare fold results for stability and generalization.

## 📊 Results & Insights
Training Curves

Training accuracy steadily improves, with validation accuracy stabilizing around 85%.

Loss convergence shows no severe overfitting, demonstrating good model stability.

Confusion Matrix

Strong performance on major classes such as Edge-Ring, Edge-Loc, and Center.

Minor classes like Random, Scratch, and Near-Full show higher misclassification due to class imbalance.

Future work: Data augmentation and rebalancing techniques may further improve rare class recognition.

## 🛠 Tech Stack

Languages: Python

Frameworks: TensorFlow, Keras

Libraries: NumPy, Pandas, Scikit-learn, Matplotlib, Seaborn

Environment: Kaggle GPU runtime

## 📈 Recommendations

Data Augmentation: Improve representation of rare defect types.

Advanced Architectures: Experiment with ResNet/EfficientNet for feature robustness.

Deployment Potential: This pipeline could be extended into a real-time wafer inspection system in an industrial setting.

## 📌 Disclaimer

This project is a case study for learning and demonstration purposes only.

The dataset originates from the publicly available WM-811k dataset.

Full code is not released due to industrial sensitivity and potential IP considerations.

## ✍️ Author

Developed by Chew Chia Yik — Chemical Engineering graduate exploring Machine Learning applications in semiconductor manufacturing.
