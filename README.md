🧠 Wafer Map Defect Classification with CNN (WM-811k Case Study)
📌 Project Overview

This project explores the use of Convolutional Neural Networks (CNNs) for semiconductor wafer defect pattern classification using the WM-811k dataset.

Defect pattern recognition is critical in semiconductor manufacturing for improving yield analysis and fault detection. By leveraging deep learning, we aim to automatically classify wafer maps into multiple defect categories, reducing reliance on manual inspection.

⚡ Key Features

Built with TensorFlow/Keras in Python (experimented on Kaggle).

Implemented two experimental pipelines:

Standard Train/Validation split

K-Fold Cross Validation for robustness

Applied class balancing strategies (weighted loss, smoothing) to address dataset imbalance.

Achieved ~85% validation accuracy with strong generalization performance.

📊 Results & Insights
Training Curves

Training accuracy steadily improves, with validation accuracy stabilizing around 85%.

Loss convergence shows no severe overfitting, demonstrating good model stability.

Confusion Matrix

Strong performance on major classes such as Edge-Ring, Edge-Loc, and Center.

Minor classes like Random, Scratch, and Near-Full show higher misclassification due to class imbalance.

Future work: Data augmentation and rebalancing techniques may further improve rare class recognition.

🛠 Tech Stack

Languages: Python

Frameworks: TensorFlow, Keras

Libraries: NumPy, Pandas, Scikit-learn, Matplotlib, Seaborn

Environment: Kaggle GPU runtime

📈 Recommendations

Data Augmentation: Improve representation of rare defect types.

Advanced Architectures: Experiment with ResNet/EfficientNet for feature robustness.

Deployment Potential: This pipeline could be extended into a real-time wafer inspection system in an industrial setting.

📌 Disclaimer

This project is a case study for learning and demonstration purposes only.

The dataset originates from the publicly available WM-811k dataset.

Full code is not released due to industrial sensitivity and potential IP considerations.

✍️ Author

Developed by [Your Name] — Chemical Engineering graduate exploring Machine Learning applications in semiconductor manufacturing.
