<h1 align="center">Application YOLO for Personal Protective Equipment (PPE) Detection in Industrial Environments</h1>

YOLO detector training was carried out in the standard detection task formulation using bounding boxes and class labels The CNN based on pretrained ResNet18 was trained in a multiclass classification setup using Focal Loss and WeightedRandomSampler to compensate for class imbalance For the SNN, positive and negative image pairs were formed, enabling metric learning based on contrastive loss function.
The YOLO-based model was trained for 25 epochs. The training demonstrated stable convergence: all loss components showed monotonic decrease to values of 1.30, 0.94, and 1.07, respectively, by the final epoch.

**Figure 1** (see `results/correlation_matrix.png`) presents the correlation matrix of training metrics. Strong positive correlations (r > 0.94) were observed among all performance metrics (Precision, Recall and F1-Score), indicating their synchronized improvement. Localization loss (box loss) demonstrated strong negative correlations with Recall (r = -0.971) and mAP50-95 (r = -0.969), confirming that bounding box localization accuracy is the primary determinant of model performance.

The F1-confidence curve (**Figure 2**, `results/f1-confidence_Curve.png`) illustrates the trade-off between precision and recall. The model achieved an optimal F1-score of 0.66 at a confidence threshold of 0.306 for all classes combined. Class-specific analysis revealed significant performance variation: well-represented classes such as "Hardhat" (8623 instances), "NO-Hardhat" (2905 instances), and "Safety Cone" (2739 instances) demonstrated F1-scores exceeding 0.75-0.85 at their optimal thresholds, while underrepresented classes such as "Fall-Detected" (89 instances) and "Ladder" (226 instances) showed considerably lower performance. This imbalance highlights the importance of dataset balancing for practical deployment in industrial safety systems.

**Figure 3** (`results/confusion_matrix.png`) shows the normalized confusion matrix, revealing class-specific detection patterns and common misclassification errors between similar PPE categories.

**Figure 4** (`results/results.png`) demonstrates the training dynamics across 25 epochs, showing the convergence of box loss, class loss, precision, recall, and mAP metrics.

As a result, the model achieved Precision = 0.662, Recall = 0.689, F1-Score = 0.675 and Accuracy = 0.573, demonstrating balanced detection performance for PPE recognition in industrial environments.