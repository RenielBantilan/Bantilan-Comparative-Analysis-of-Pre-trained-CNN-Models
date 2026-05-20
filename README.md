# Bantilan-Comparative-Analysis-of-Pre-trained-CNN-Models

## Google colab link: https://drive.google.com/file/d/1boqXMK9G2C_ZgGBa72NXdV-rN4oQpmKP/view?usp=drive_link

## Model Link: https://drive.google.com/drive/folders/1dtUobXWtuUS6aPkx_Qf7FwRxE9OIXcuS?usp=sharing


## A. Model Performance

1. Which pre-trained model achieved the highest accuracy? Why?
EfficientNetB0 achieved the highest accuracy.
Why? EfficientNetB0 uses a compound scaling method that balances depth, width, and resolution, leading to better feature extraction without excessive computational cost. It is optimized for both accuracy and efficiency.

2. Which model had the lowest performance? What could be the reason?
NASNetMobile had the lowest performance.
Reason: NASNetMobile is designed for extreme lightweight applications, which may limit its capacity to learn complex patterns in a dataset with 20 classes. It may underfit if the dataset has fine-grained visual differences.

3. How did loss values compare across models?
EfficientNetB0 had the lowest validation loss, indicating better generalization.
MobileNetV2 had moderate loss, balancing speed and accuracy.
NASNetMobile showed higher loss, suggesting underfitting or insufficient representational power.

## B. Evaluation Metrics

4. Why is accuracy not enough to evaluate a model?
Accuracy can be misleading when classes are imbalanced. A model could guess the majority class and still achieve high accuracy but perform poorly on minority classes. Precision, recall, and F1-score provide a more complete picture.

5. Which model had the best F1-score? What does it indicate?
EfficientNetB0 had the best F1-score.
Indicates: It maintains a good balance between precision and recall, meaning it avoids both many false positives and false negatives.

6. How did Precision and Recall differ across models?
EfficientNetB0: High precision and recall → reliable predictions.
MobileNetV2: Slightly lower recall → more false negatives.
NASNetMobile: Lower precision → more false positives.

## C. Confusion Matrix Analysis

7. Which classes were frequently misclassified?
Classes with similar visual features (e.g., different dog breeds, types of vehicles, or fruits with similar color/texture) were frequently misclassified.

8. What patterns did you observe in the confusion matrix?
Most misclassifications occurred between visually similar classes. The diagonal dominance was strongest for EfficientNetB0, while NASNetMobile showed more off-diagonal errors.

## D. ROC and AUC

9. Which model had the highest AUC score?
EfficientNetB0 had the highest AUC (closest to 1.0).

10. What does AUC tell us about model performance?
AUC measures the model’s ability to distinguish between classes. A higher AUC means the model is better at ranking positive classes higher than negative ones, even if the absolute probability calibration is off.

## E. Explainability (Grad-CAM)

11. What did Grad-CAM reveal about model decision-making?
Grad-CAM showed that models focused on relevant foreground objects (e.g., the face of an animal, the wheels of a car) rather than background noise.

12. Did the model focus on relevant image regions?
Yes, especially for EfficientNetB0 and MobileNetV2. NASNetMobile sometimes focused on smaller or less discriminative regions.

13. Which model produced the most meaningful heatmaps?
EfficientNetB0 produced the most precise and class-discriminative heatmaps, highlighting the exact parts of the image that matched the predicted class.

## F. Model Comparison & Improvement

14. Which model would you recommend for deployment? Why?
MobileNetV2 – if deployment is on mobile or edge devices.
EfficientNetB0 – if deployed on cloud or powerful servers.
MobileNetV2 offers a good trade-off between accuracy and speed for real-time applications.

15. How can you further improve your best-performing model?
Fine-tune the top layers (set base_model.trainable = True after initial training).
Use data augmentation (rotation, zoom, flip, brightness).
Increase training epochs with early stopping.
Apply label smoothing to reduce overconfidence.

## G. Real-World Application

16. How can your model be applied in real-world scenarios?
Example: A 20-class waste sorting system (plastic, paper, glass, metal, etc.) deployed in recycling facilities or smart bins to automatically classify waste types.

17. What are the risks of deploying an inaccurate model?
Misclassification could cause contamination in recycling streams.
In medical or safety-critical applications, it could lead to harmful decisions.
Loss of user trust if the model frequently makes errors.

18. How can this system be integrated into a mobile/web app?
Convert the model to TensorFlow Lite for mobile or TensorFlow.js for web.
Use Flask/FastAPI backend to serve the model via REST API.
Deploy on Google Cloud Run or AWS Lambda for scalability.
Capture image from camera → preprocess → send to API → display result.




