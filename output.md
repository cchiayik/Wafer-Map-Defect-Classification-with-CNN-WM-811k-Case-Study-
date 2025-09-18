# Wafer Analysis Report

---

## 1. Wafer Index Distribution

<p align="center">
  <img src="https://github.com/user-attachments/assets/60ea0c5f-0a39-4f8d-8623-cc5d5ea70805" width="500" />
  <br>
  <em>Figure 1: Wafer Map Visualisation plot.</em>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/e5fbece9-e653-418f-82aa-31f061b80026" width="400" />
  <br>
  <em>Figure 2: Wafer lot variation.</em>
</p>

From the wafer index distribution plot, the number of wafer maps per index is not consistent.  
This indicates that not all lots have exactly 25 wafer maps, which may be caused by **sensor failure** or other unknown issues.

---

## 2. Pie Chart for Wafer Failure Labelling

<p align="center">
  <img src="https://github.com/user-attachments/assets/c2ddc0a2-ae52-4480-94c3-cc7f9a8b8bf4" width="350" />
  <br>
  <em>Figure 3: Pie chart of wafer failure type labelling.</em>
</p>

From the plotted pie chart, a significant portion of the wafer failure type (**78.7%**) is not labelled.

---

## 3. Wafer Failure Type Distribution

<p align="center">
  <img src="https://github.com/user-attachments/assets/e89a0a9e-d2b6-48d7-be3f-fe73e699c211" width="600" />
  <br>
  <em>Figure 4: Bar chart showing dataset imbalance.</em>
</p>

The dataset is **imbalanced**, with the **Edge-Ring** failure type being dominant.  
Meanwhile, **Donut, Random, Scratch, and Near-Full** are very rare.  
This imbalance may cause the CNN to be biased toward Edge-Ring while neglecting rare failure types.

---

## 4. Model Training and Validation Performance

<p align="center">
  <img src="https://github.com/user-attachments/assets/629ba103-e71b-4be0-bc63-f4ac8749a88f" width="700" />
  <br>
  <em>Figure 5: Training and validation performance curves.</em>
</p>

**Observations**  
- Training accuracy stabilizes above **90%**, validation accuracy around **85%**, indicating good generalization.  
- Both training and validation loss decrease consistently, converging near **0.08–0.10**.  
- Small fluctuations after ~10 epochs reflect data complexity and imbalance.  

---

## 5. Classification Report

<p align="center">
  <img width="572" height="339" alt="Classification Report" src="https://github.com/user-attachments/assets/095fd297-5c3f-489c-9f9d-0ed04820af58" />
  <br>
  <em>Figure 6: Classification report for wafer failure classification.</em>
</p>

### Key Insights

**Strong classes:**  
- *Edge-Ring* (F1 = 0.97) and *Center* (F1 = 0.88) are very well classified.  
- *Random* (F1 = 0.90) also shows high performance.  

**Challenging classes:**  
- *Near-full* has **perfect precision (1.00)** but **low recall (0.57)** → the model is conservative, predicting this class only when very confident, but misses many true cases.  
- *Loc* and *Scratch* show moderate performance (F1 ~ 0.70–0.74), suggesting some confusion with other classes.  
- *Donut* lags slightly behind with F1 = 0.76.  

**Imbalance effect:**  
- Large classes like *Edge-Ring* (1936 samples) dominate the weighted average, boosting overall accuracy.  
- Smaller classes (*Donut, Near-full*) show lower reliability due to fewer training examples.  

📌 **Takeaway**:  
The model achieves **86% accuracy overall** with strong generalization to dominant classes.  
However, further work is needed to improve recall on minority classes (*Near-full, Donut, Scratch, Loc*) to make the classifier more balanced.

---

## 6. Confusion Matrix Analysis

<p align="center">
  <img src="https://github.com/user-attachments/assets/9f97b2a1-9766-485a-a2dd-e3af3cff3e74" width="500" />
  <br>
  <em>Figure 7: Confusion matrix for wafer failure classification.</em>
</p>

**Insights**  
- **High Accuracy Classes**: *Edge-Ring* and *Edge-Loc* show strong results.  
- **Moderate**: *Center* and *Loc* perform well with minor misclassifications.  
- **Challenging**: *Random* and *Scratch* show confusion with others. *Near-Full* is under-represented.  

**Takeaway**:  
Model performs well overall, but minority classes need **data augmentation** or **rebalancing**.

---

## 7. Cross-Validation Performance

<p align="center">
  <img src="https://github.com/user-attachments/assets/f1e4d672-cd57-4c0b-84c6-7fed5e59b62b" width="700" />
  <br>
  <em>Figure 8: Validation Accuracy Plot [left] and Validation Loss Plot [right].</em>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/33509e5e-2127-46e5-818b-918bf67ab339" width="600" />
  <br>
  <em>Figure 9: Validation accuracy and loss across folds.</em>
</p>

**Observations**  
- Validation accuracy trends upward and stabilizes by ~epoch 13–15.  
- Folds 3 and 4 show unstable spikes in validation loss, likely due to noise or imbalance.  
- No major overfitting observed.  

---

## 8. Final Evaluation on Test Set

<p align="center">
  <img width="858" height="145" alt="Final Evaluation" src="https://github.com/user-attachments/assets/76f451e7-3c44-408b-89e7-213f287e2ae1" />
  <br>
  <em>Figure 10: Final evaluation on held-out test set.</em>
</p>

Using the held-out test set, the model was evaluated after completing training and cross-validation.  
The results are as follows:

- **Test Accuracy:** ~85.1%  
- **Test Loss:** ~0.40  

✅ These results are consistent with the validation performance observed across the K-Fold experiments,  
where validation accuracy typically stabilized between **75–85%**.  

⚖️ The close alignment between validation and test performance suggests that the model is **generalizing well**  
without severe overfitting, making it a reliable candidate for downstream use.

---

## 9. Conclusion

- Early stopping (patience ~5) + learning rate scheduling (`ReduceLROnPlateau`) are recommended.  
- Training for ~15 epochs is sufficient to save time without losing performance.  
- The model shows **strong generalization** but requires **data balancing** to better capture minority classes.  
