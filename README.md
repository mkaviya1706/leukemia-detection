# Explainable Agentic AI-Based Leukemia Detection from Blood-Smear Images

An AI-assisted leukemia screening framework that combines deep feature extraction, metaheuristic feature selection, machine learning, explainable AI, and agent-based analysis to classify blood-smear images as **Healthy Hematological Cells (HEM)** or **Acute Lymphoblastic Leukemia (ALL)**.

## Overview

Leukemia detection from blood-smear images requires careful examination of cellular characteristics. This project proposes an automated image-classification framework that extracts meaningful features from blood-smear images, selects informative features, and classifies them using machine-learning algorithms.

The system also incorporates explainability and agentic AI components to provide visual explanations, feature-level interpretations, model-based risk information, and a structured AI-assisted screening report.

## Key Features

- Blood-smear image preprocessing and augmentation.
- Deep feature extraction using Vision Transformer (ViT), EfficientNet-B3, and DenseNet121.
- Feature selection using six metaheuristic optimization methods.
- Evaluation of seven machine-learning classifiers.
- ViT Grad-CAM and attention-based visual explanations.
- SHAP-based feature contribution analysis.
- Risk assessment using a dedicated AI agent.
- Structured screening report generation using a dedicated AI agent.

## System Architecture

```text
C-NMC Blood-Smear Dataset
           |
           v
 Image Preprocessing
           |
           v
 Deep Feature Extraction
 ViT / EfficientNet-B3 / DenseNet121
           |
           v
 Metaheuristic Feature Selection
 CDMO / EBARO / IRSA / RSO-BERSOC / PSO / HHO
           |
           v
 Machine Learning Classification
 SVM / XGBoost / Random Forest / MLP
 KNN / Logistic Regression / Decision Tree
           |
           v
      HEM / ALL Prediction
           |
           v
       Explainability
       Grad-CAM + SHAP
           |
           v
   Risk Assessment Agent
           |
           v
   Report Generation Agent
           |
           v
 Final AI-Assisted Screening Report
```

## Dataset

The project uses the **C-NMC leukemia dataset** for binary classification.

| Attribute | Description |
|---|---|
| Dataset | C-NMC Leukemia |
| Classes | HEM and ALL |
| Total images | 10,661 |
| HEM images | 3,389 |
| ALL images | 7,272 |
| Training images | 9,594 |
| Validation images | 1,067 |
| Input image size | 224 × 224 pixels |
| Split strategy | 90:10 stratified split |

**Note:** Obtain the dataset from its authorized source. The dataset is not included in this repository.

## Methodology

### 1. Image Preprocessing

The blood-smear images are resized to 224 × 224 pixels and normalized before feature extraction. Data augmentation techniques such as flipping, rotation, brightness and contrast adjustment, and noise addition are used during training to introduce image variation.

### 2. Deep Feature Extraction

Three deep-learning architectures are evaluated to obtain feature representations from the input images.

| Model | Feature Dimension |
|---|---:|
| Vision Transformer (ViT) | 768 |
| EfficientNet-B3 | 1,536 |
| DenseNet121 | 1,024 |

ViT provides the feature representation selected for the final classification pipeline based on the experimental comparison.

### 3. Feature Selection

Six metaheuristic optimization methods are evaluated:

- Chaotic Dwarf Mongoose Optimization (CDMO)
- Enhanced Binary Artificial Rabbits Optimization (EBARO)
- Improved Reptile Search Algorithm (IRSA)
- Reptile Search Optimization / Binary Enhanced RSO (RSO/BERSOC)
- Particle Swarm Optimization (PSO)
- Harris Hawks Optimization (HHO)

HHO reduces the original ViT feature representation from **768 to 300 selected features** for the final classification pipeline.

### 4. Machine Learning Classification

Seven classifiers are compared using the selected feature representations:

- Support Vector Machine (SVM)
- XGBoost
- Random Forest
- Multi-Layer Perceptron (MLP)
- K-Nearest Neighbors (KNN)
- Logistic Regression
- Decision Tree

The experiments comprise six feature-selection methods combined with seven classifiers, resulting in **42 experimental combinations**.

### 5. Explainable AI

The system uses two complementary explanation techniques:

- **ViT Grad-CAM:** Highlights image regions that contribute to the model prediction.
- **SHAP:** Estimates the contribution of selected numerical features to the prediction.

Together, these techniques provide visual and feature-level interpretations of the classification output.

### 6. Agentic AI Framework

The framework contains three agents:

**Explainability Agent**  
Organizes Grad-CAM and SHAP results to provide visual and feature-level explanations.

**Risk Assessment Agent**  
Processes the predicted class and confidence information to generate a model-based risk category.

**Report Generation Agent**  
Combines the prediction, confidence, explanation, and risk information into a structured AI-assisted screening report.

## Experimental Results

The final classification configuration is **ViT + HHO + SVM**.

| Metric | Result |
|---|---:|
| Accuracy | 95.60% |
| Precision | 96.58% |
| Recall | 96.98% |
| F1-score | 96.78% |
| Original ViT features | 768 |
| Selected HHO features | 300 |

These values represent the recorded experimental results for the final configuration. Performance should be interpreted in the context of the dataset and evaluation procedure used.

## Technology Stack

- **Programming language:** Python
- **Deep learning:** PyTorch, Torchvision, Transformers
- **Image processing:** OpenCV, Pillow
- **Machine learning:** Scikit-learn, XGBoost
- **Numerical processing:** NumPy, Pandas
- **Visualization:** Matplotlib
- **Explainable AI:** SHAP
- **Development environment:** Kaggle Notebook




### Execution

1. Download the C-NMC dataset from its authorized source.
2. Configure the dataset paths in the notebooks.
3. Run the preprocessing and feature extraction stages.
4. Execute feature selection and classifier evaluation.
5. Evaluate the final ViT-HHO-SVM configuration.
6. Generate Grad-CAM, SHAP, risk assessment, and screening report outputs.

Run the notebooks in the required order, ensuring that the intermediate feature files and trained models are available to subsequent stages.

### Limitations

- The current classification task focuses on HEM and ALL.
- Results depend on the dataset, preprocessing procedure, and evaluation setup.
- The model-based risk category is a screening-support output, not a clinically validated risk score.
- Further external validation is required before considering real-world clinical use.

### Future Enhancements

- Extend the framework to additional leukemia classes.
- Evaluate performance on independent external datasets.
- Improve feature-selection efficiency and model generalization.
- Enhance visual explanations and structured report generation.
- Develop a user-friendly application after appropriate validation.

,,,
