# Wafer Analysis Report

---

## Wafer Index Distribution

<p align="center">
  <img src="https://github.com/user-attachments/assets/60ea0c5f-0a39-4f8d-8623-cc5d5ea70805" width="500" />
  <br>
  <em>Figure 1: Wafer Index distribution plot.</em>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/e5fbece9-e653-418f-82aa-31f061b80026" width="400" />
  <br>
  <em>Figure 2: Wafer lot variation.</em>
</p>

From this wafer index distribution plot, the number of wafer maps per index is not the same.  
This indicates that not all lots have exactly 25 wafer maps, which may be caused by sensor failure or other unknown problems.

---

## Pie Chart for Labelling Portion of Wafer Failure Type

<p align="center">
  <img src="https://github.com/user-attachments/assets/c2ddc0a2-ae52-4480-94c3-cc7f9a8b8bf4" width="350" />
  <br>
  <em>Figure 3: Pie chart of wafer failure type labelling.</em>
</p>

From the plotted pie chart, a significant portion of the wafer failure type (**78.7%**) is not labelled.

---

## Wafer Failure Type Distribution

<p align="center">
  <img src="https://github.com/user-attachments/assets/e89a0a9e-d2b6-48d7-be3f-fe73e699c211" width="600" />
  <br>
  <em>Figure 4: Bar chart showing dataset imbalance.</em>
</p>

This dataset is imbalanced, with the **Edge-Ring** failure type being dominant.  
Meanwhile, **Donut, Random, Scratch, and Near-Full** are very rare.  
This imbalance may cause the CNN to be biased toward Edge-Ring while neglecting rare failure types.

---

## Model Training and Validation Performance

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

## Confusion Matrix Analysis

<p align="center">
  <img src="https://github.com/user-attachments/assets/9f97b2a1-9766-485a-a2dd-e3af3cff3e74" width="500" />
  <br>
  <em>Figure 6: Confusion matrix for wafer failure classification.</em>
</p>

**Insights**  
- **High Accuracy Classes**: Edge-Ring and Edge-Loc show strong results.  
- **Moderate**: Center and Loc perform well with minor misclassifications.  
- **Challenging**: Random and Scratch show confusion with others. Near-Full is under-represented.  

**Takeaway**: Model performs well overall, but minor classes need **data augmentation** or **rebalancing**.

---

## Cross-Validation Performance

<p align="center">
  <img src="https://github.com/user-attachments/assets/f1e4d672-cd57-4c0b-84c6-7fed5e59b62b" width="700" />
  <br>
  <em>Figure 7: Validation accuracy across folds.</em>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/33509e5e-2127-46e5-818b-918bf67ab339" width="600" />
  <br>
  <em>Figure 8: Validation loss across folds.</em>
</p>

**Observations**  
- Validation accuracy trends upward and stabilizes by ~epoch 13–15.  
- Folds 3 and 4 show unstable spikes in validation loss, likely due to noise or imbalance.  
- No major overfitting observed.  

✅ **Conclusion**:  
- Early stopping (patience ~5) + learning rate scheduling (e.g., `ReduceLROnPlateau`) recommended.  
- Training for ~15 epochs is sufficient to save time without losing performance.  
