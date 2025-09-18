## Pseudocode: Wafer Defect Detection using CNN

## 1 Problem Statement
Classify semiconductor wafer maps into defect categories to support **yield improvement**  
and **smart manufacturing (IR4.0)** quality control.

---

## 2 Data Preparation
Input: Wafer map dataset (images + defect labels)
Process:
- Normalize pixel values (0-1)
- Handle class imbalance (oversampling / class weighting)
- Train-test split (80/20, stratified)
Output: Balanced training and test sets

---

## 3 Model Design
Model: Convolutional Neural Network (CNN)
Architecture:
- Conv2D → ReLU → MaxPooling
- Conv2D → ReLU → MaxPooling
- Flatten
- Dense (fully connected) → Dropout
- Output Layer (Softmax for defect classification)

---

## 4 Training
Input: X_train, y_train
Process:
- Compile model (optimizer = Adam, loss = categorical crossentropy)
- Train for N epochs with early stopping
- Use validation set to monitor overfitting
Output: Trained CNN model (wafer_cnn_final.h5)

---

## 5 Evaluation
Input: X_test, y_test
Process:
- Predict defect class for each wafer map
- Generate classification report:
* Accuracy
* Precision, Recall, F1-score
- Plot confusion matrix
Output: Performance metrics + visual validation

---

## 6 Results
- Achieved **~91% test accuracy**  
- Balanced performance across defect classes  
- Visualization of sample wafer map predictions:  

![sample wafer map](results/wafermap_example.png)

---

## 7 Industry 4.0 Relevance
- ✅ **Smart Quality Control** – Automated defect detection replaces manual inspection  
- ✅ **Predictive Maintenance** – Detects systematic issues before yield loss  
- ✅ **Big Data & AI** – Applies CNNs to large-scale semiconductor datasets  
- ✅ **Scalability** – Framework adaptable to other manufacturing analytics  

---

## 8 Note
⚠️ Full dataset and production code are not shared due to confidentiality.  
This pseudocode and results are provided for demonstration of **methodology** and **outcomes**
