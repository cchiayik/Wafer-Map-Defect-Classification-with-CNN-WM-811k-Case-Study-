<img width="1500" height="1500" alt="download" src="https://github.com/user-attachments/assets/60ea0c5f-0a39-4f8d-8623-cc5d5ea70805" />
<img width="589" height="455" alt="download" src="https://github.com/user-attachments/assets/e5fbece9-e653-418f-82aa-31f061b80026" />
## Wafer Index Distribution
From this Wafer Index distribution plot, the number of wafer map as of Wafer Index is not the same. 
Indicate not all lot has exact 25 wafer maps which may caused by sensor failure or other unknown problems.
<p align="center">
  <img width="419" height="415" alt="download" src="https://github.com/user-attachments/assets/c2ddc0a2-ae52-4480-94c3-cc7f9a8b8bf4" />
## Pie Chart for Labelling Portion of Wafer Failure Type
From the plotted pie chart, a significant portion of the wafer failure type (78.7%) is not labelled.

<img width="855" height="451" alt="download" src="https://github.com/user-attachments/assets/e89a0a9e-d2b6-48d7-be3f-fe73e699c211" />


From this bar chart, it is clear this dataset is imbalanced, with the most failure type being the edge-ring. While Donut, Random, Scratch and Near-full (most rare) are significantly small portions. This imbalanced dataset might cause inaccuracy in the model, and the CNN will be biased toward the most common data (Edge-Ring) while neglecting the less common failure type (such as Near-full).


<img width="1001" height="375" alt="download" src="https://github.com/user-attachments/assets/629ba103-e71b-4be0-bc63-f4ac8749a88f" />
<img width="797" height="701" alt="download" src="https://github.com/user-attachments/assets/9f97b2a1-9766-485a-a2dd-e3af3cff3e74" />
## Confusion Matrix Analysis

The confusion matrix provides deeper insight into class-level performance:

High Accuracy Classes:

Edge-Ring and Edge-Loc show strong classification results, with the majority of samples correctly identified.

Center and Loc classes also perform well, though some misclassifications occur.

Challenging Cases:

Random and Scratch classes exhibit confusion with other categories, likely due to visual similarities in wafer defect patterns.

The Near-Full category has very few samples, making it prone to misclassification and under-representation.

Key Takeaway: While the model performs well overall, minor classes with fewer samples are more error-prone. Future work could explore data augmentation or class rebalancing techniques to further enhance classification robustness.

<img width="1156" height="470" alt="download" src="https://github.com/user-attachments/assets/f1e4d672-cd57-4c0b-84c6-7fed5e59b62b" />
<img width="1189" height="1490" alt="download" src="https://github.com/user-attachments/assets/33509e5e-2127-46e5-818b-918bf67ab339" />

