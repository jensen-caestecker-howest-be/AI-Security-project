# AI-Security-project

## Project Goals
The goal of this project is to evaluate the robustness of various deep learning models (VGG16 and ResNet20) against adversarial attacks using the **Adversarial Robustness Toolbox (ART)**. Additionally, we implement defensive techniques such as **Adversarial Training** to improve the models' robustness against these attacks.

## Dataset Details
### Dataset: CIFAR-10
- **CIFAR-10** is a dataset containing 60,000 32x32 color images in 10 classes. The dataset is split into 50,000 training images and 10,000 testing images.
- **Classes:** airplane, automobile, bird, cat, deer, dog, frog, horse, ship, and truck.
- **Preprocessing:** 
    - Images are normalized using the following mean and standard deviation:
        - Mean: [0.4914, 0.4822, 0.4465]
        - Std: [0.2470, 0.2435, 0.2616]

## Attack Methods Used
The following adversarial attack methods were applied:
1. **FGSM (Fast Gradient Sign Method):** A first-order gradient-based attack.
2. **PGD (Projected Gradient Descent):** An iterative attack that refines the adversarial examples.
3. **Carlini & Wagner (C&W):** A powerful attack based on optimization.

## Adversarial Defense Techniques
To improve robustness, **Adversarial Training** was employed. This method involves training the model with both clean and adversarially perturbed examples.

## Results Summary

### 1. **ResNet20 Performance**
- **Clean Accuracy:** 91.70%
- **FGSM Accuracy:** 18.90%
- **PGD Accuracy:** 4.30%
- **C&W Accuracy:** 29.50%

#### Adversarially Trained ResNet20:
- **Clean Accuracy (Adversarially Trained):** 71.80%
- **FGSM Accuracy (Adversarially Trained):** 56.70%
- **PGD Accuracy (Adversarially Trained):** 34.70%
- **C&W Accuracy (Adversarially Trained):** 71.40%

### 2. **VGG16 Performance**
- **Clean Accuracy:** 92.80%
- **FGSM Accuracy:** 45.00%
- **PGD Accuracy:** 4.10%
- **C&W Accuracy:** 69.40%

#### Adversarially Trained VGG16:
- **Clean Accuracy (Adversarially Trained):** 71.80%
- **FGSM Accuracy (Adversarially Trained):** 56.70%
- **PGD Accuracy (Adversarially Trained):** 34.70%
- **C&W Accuracy (Adversarially Trained):** 71.40%

## Comparison of Model Performance

| Model             | Clean Accuracy (%) | FGSM Accuracy (%) | PGD Accuracy (%) | C&W Accuracy (%) |
|-------------------|--------------------|-------------------|------------------|------------------|
| **ResNet20**      | 91.70              | 18.90             | 4.30             | 29.50            |
| **VGG16**         | 92.80              | 45.00             | 4.10             | 69.40            |

### Attack Success Rates:

| Attack Method   | ResNet20 Success Rate (%) | VGG16 Success Rate (%) |
|-----------------|---------------------------|------------------------|
| **FGSM**        | 81.10                     | 55.00                  |
| **PGD**         | 95.70                     | 95.90                  |
| **C&W**         | 70.50                     | 30.60                  |

### Defense Mechanism Performance (Adversarial Training):

| Model                     | Clean Accuracy (%) | FGSM Accuracy (%) | PGD Accuracy (%) | C&W Accuracy (%) |
|---------------------------|--------------------|-------------------|------------------|------------------|
| **ResNet20 (Adversarially Trained)** | 57.40               | 44.10             | 22.50            | 56.20            |
| **VGG16 (Adversarially Trained)**   | 71.80               | 56.70             | 34.70            | 71.40            |

## Classification Reports for Adversarial Examples

### VGG16 - FGSM Adversarial Examples:
```plaintext
              precision    recall  f1-score   support

    airplane       0.26      0.50      0.34        14
  automobile       0.92      0.53      0.68        43
        bird       0.67      0.72      0.69       117
         cat       0.89      0.65      0.75       171
        deer       0.81      0.53      0.64        91
        frog       0.61      0.94      0.74       139
       horse       0.97      0.76      0.86       102
        ship       0.76      0.97      0.85       157
       truck       0.86      0.75      0.80       166

    accuracy                           0.76      1000
   macro avg       0.75      0.71      0.71      1000
weighted avg       0.79      0.76      0.76      1000
```

### VGG16 - PGD Adversarial Examples:
```plaintext
           precision    recall  f1-score   support

    airplane       0.14      0.36      0.20        14
  automobile       0.44      0.16      0.24        43
        bird       0.44      0.34      0.38       117
         cat       0.63      0.42      0.50       171
        deer       0.34      0.21      0.26        91
        frog       0.34      0.90      0.50       139
       horse       0.62      0.29      0.40       102
        ship       0.72      0.68      0.70       157
       truck       0.72      0.55      0.63       166

    accuracy                           0.49      1000
   macro avg       0.49      0.43      0.42      1000
weighted avg       0.55      0.49      0.49      1000
```

### VGG16 - C&W Adversarial Examples:
```plaintext
              precision    recall  f1-score   support

    airplane       0.87      0.93      0.90        14
  automobile       1.00      0.98      0.99        43
        bird       0.98      0.97      0.98       117
         cat       0.98      0.99      0.99       171
        deer       0.98      0.96      0.97        91
        frog       0.99      0.99      0.99       139
       horse       0.97      0.99      0.98       102
        ship       1.00      0.98      0.99       157
       truck       0.99      1.00      0.99       166

    accuracy                           0.98      1000
   macro avg       0.97      0.98      0.97      1000
weighted avg       0.98      0.98      0.98      1000
```

### ResNet20 - FGSM Adversarial Examples:
```plaintext
              precision    recall  f1-score   support

    airplane       0.29      0.50      0.36        12
  automobile       0.86      0.51      0.64       185
        bird       0.18      0.28      0.22        32
         cat       0.57      0.10      0.17       230
        deer       0.23      0.33      0.27        48
         dog       0.10      0.14      0.11        14
        frog       0.18      0.99      0.31        76
       horse       0.92      0.18      0.30       190
        ship       0.58      0.78      0.67        68
       truck       0.60      0.62      0.61       145

    accuracy                           0.40      1000
   macro avg       0.45      0.44      0.37      1000
weighted avg       0.63      0.40      0.40      1000
```

### ResNet20 - PGD Adversarial Examples:
```plaintext
              precision    recall  f1-score   support

    airplane       0.08      0.07      0.07        12
  automobile       0.61      0.09      0.16       185
        bird       0.31      0.47      0.37        32
         cat       0.75      0.12      0.21       230
        deer       0.20      0.18      0.19        48
         dog       0.22      0.29      0.25        14
        frog       0.28      0.99      0.44        76
       horse       0.94      0.03      0.05       190
        ship       0.45      0.56      0.50        68
       truck       0.52      0.44      0.48       145

    accuracy                           0.26      1000
   macro avg       0.44      0.43      0.35      1000
weighted avg       0.57      0.26      0.28      1000
```

### ResNet20 - C&W Adversarial Examples:
```plaintext
              precision    recall  f1-score   support

    airplane       0.92      0.92      0.92        12
  automobile       0.98      0.97      0.98       185
        bird       0.91      0.91      0.91        32
         cat       0.95      0.97      0.96       230
        deer       0.96      0.94      0.95        48
         dog       0.93      0.93      0.93        14
        frog       0.96      0.89      0.93        76
       horse       0.96      0.98      0.97       190
        ship       0.94      0.97      0.96        68
       truck       0.97      0.97      0.97       145

    accuracy                           0.96      1000
   macro avg       0.95      0.94      0.95      1000
weighted avg       0.96      0.96      0.96      1000
```

## Installation and Setup
1. Clone the repository:
    ```bash
    git clone https://github.com/yourusername/adversarial-robustness.git
    ```
2. Install dependencies:
    ```bash
    pip install -r requirements.txt
    ```
3. Run the training and evaluation:
    ```bash
    python train.py
    ```

## Usage Instructions
To evaluate the models:
1. **Training:**
    - Train models using clean images and adversarial examples for adversarial training.
    ```bash
    python train.py --adversarial_training --epochs 3
    ```

2. **Evaluate the models:**
    - Evaluate clean and adversarial performance.
    ```bash
    python evaluate.py --model vgg16 --attack fgsm
    python evaluate.py --model resnet20 --attack pgd
    ```
