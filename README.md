# Topic: Deep Learning for Automated Thyroid Nodule Delineation
# Streamlit App Link: https://thyro-ai-ap.streamlit.app/

This repository contains the project on automated thyroid nodule segmentation using deep learning. The project develops, trains, and compares three state-of-the-art architectures (U-Net, SegNet, and Residual U-Net) to build a robust decision-support system.

# 1. Project Overview & Problem Statement
This project addresses a critical gap in rural and underserved healthcare systems where patients often face significant delays in consulting with a specialist after receiving a thyroid imaging report.

Information Gap: Patients lack immediate specialist interpretation, leading to anxiety and uncertainty.

Diagnostic Delay: This "time-to-diagnosis" gap can postpone urgent care for potentially serious conditions.

The Goal: To create an automated decision-support tool that provides an instant, preliminary analysis of thyroid images. The system segments (delineates) nodules, providing a foundational step for future classification and bridging the gap between receiving a report and consulting a doctor.

# 2. Methodology
The project follows a comprehensive pipeline from data acquisition to model comparison.

Data Collection: The project uses the Thyroid Dataset (tg3k), a public dataset containing 2D ultrasound images and their corresponding pixel-level ground truth segmentation masks.

Data Pre-processing:

A clean directory structure (Train/, Test/) was created.

The dataset was randomly split into a 70% training set and a 30% testing set.

All images and masks were resized to a uniform 256x256 pixels.

Images were converted to PyTorch Tensors and normalized for training.

Model Implementation: Three key architectures were implemented from scratch in PyTorch:

U-Net: The baseline model, using skip connections to preserve fine-grained details.

SegNet: An efficiency-focused model, using max-pooling indices for upsampling to reduce memory usage.

Residual U-Net: An advanced model using residual blocks to enable deeper, more powerful, and stable training.

# 3.Training:

All models were trained on a GPU-enabled environment.

Optimizer: Adam (lr=1e-4)

Loss Function: Binary Cross-Entropy Loss (nn.BCELoss), suitable for binary (nodule vs. background) segmentation.

Evaluation & Model Selection:

Models were evaluated on the unseen test set at the end of each epoch.

The primary evaluation metric was the Dice Coefficient, which measures the spatial overlap between the predicted mask and the ground truth mask.

The best-performing version of each model (based on the highest Dice score) was saved for a final comparison.

# 4. Results & Conclusion
Comparative Analysis: All three models were successfully trained. The Residual U-Net achieved the highest Dice Coefficient, confirming its superior ability to learn complex features and accurately delineate irregular nodule boundaries.

Visual Proof: The final visualizations show that the Residual U-Net's predicted masks are visually closer to the ground truth masks compared to U-Net and SegNet.

Final Impact: This project successfully demonstrates that an automated deep learning system is a feasible and reliable solution for thyroid nodule analysis. It provides a strong foundation for a future deployable application that can make medical diagnostics more accessible and efficient.
