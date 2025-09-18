#  Pseudocode: Wafer Defect Detection using CNN

---

## 1. Problem Statement
Classify semiconductor wafer maps into predefined defect categories to support:  
- **Yield improvement**  
- **Smart manufacturing (IR4.0) quality control**

---

## 2. Data Preparation
**Input:** Wafer map dataset (images + defect labels)  

**Process:**
- Normalize pixel values → `[0, 1]` range  
- Handle class imbalance → oversampling / class weighting  
- Train-test split → 80/20, stratified by defect type  

**Output:** Balanced training and test sets

---

## 3. Model Design
**Model:** Convolutional Neural Network (CNN)  

**Architecture:**
1. `Conv2D` → `ReLU` → `MaxPooling`  
2. `Conv2D` → `ReLU` → `MaxPooling`  
3. `Flatten`  
4. `Dense` (fully connected) → `Dropout`  
5. `Dense(num_classes, activation="softmax")`  

---

## 4. Training
**Input:** `X_train`, `y_train`  

**Process:**
- Compile model  
  - Optimizer: `Adam`  
  - Loss: `CategoricalCrossentropy`  
- Train for *N* epochs with **EarlyStopping**  
- Use validation set to monitor overfitting  

**Output:** Trained model → `wafer_cnn_final.h5`

---

## 5. Evaluation
**Input:** `X_test`, `y_test`  

**Process:**
- Predict wafer defect class (`model.predict`)  
- Generate **classification report**:  
  - Accuracy  
  - Precision, Recall, F1-score  
- Plot **confusion matrix**  

**Output:** Performance metrics + visual validation

---

## 6. Results
- Achieved **~82% test accuracy**  
- Balanced performance across defect categories  
- Visualization of sample wafer map predictions:  


## 7. Note
⚠️ Full dataset and production code are not shared due to confidentiality.  
This pseudocode and results are provided as a demonstration of **methodology** and **outcomes**.
