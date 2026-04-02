# fine-tune-sms-spam-classifier
SMS Spam Classification using BERT and PyTorch
#  SMS Spam Detection using BERT (Fine-tuning with PyTorch)

This project builds a **binary text classification model** to detect spam SMS messages using a fine-tuned **BERT-base model** with a custom classification head.

---

##  Project Overview

- Backbone model: **BERT-base-uncased**
- Feature extraction: **[CLS] token embedding**
- Classification head: Fully connected neural network
- Task: Binary classification (Spam / Ham)

---

##  Model Architecture

The model uses BERT as a feature extractor and adds a custom classifier on top:
Input Text
   ↓
BERT-base-uncased
   ↓
[CLS] embedding (768-d)
   ↓
Dense (768 → 512)
   ↓
ReLU + Dropout
   ↓
Dense (512 → 2)
   ↓
Softmax


---

##  Training Strategy

- Fine-tuning full BERT + classification head
- Loss function: CrossEntropyLoss
- Optimizer: AdamW
- Early stopping:
  - Training stops if validation loss does not improve for 3 consecutive epochs
- Regularization:
  - Dropout applied in classification head

---

##  Class Imbalance Handling

Dataset is imbalanced (spam class is minority).  
To improve recall for spam detection:

- Decision threshold is adjusted (not strictly 0.5)
- Model is tuned to prioritize **class 1 (spam detection)**

---

##  Evaluation Results

| Class | Precision | Recall | F1-score | Support |
|------|----------|--------|----------|---------|
| 0 (Ham)  | 0.9793 | 0.9793 | 0.9793 | 723 |
| 1 (Spam) | 0.8661 | 0.8661 | 0.8661 | 112 |

### Overall Performance:
- **Accuracy:** 0.9641
- **Macro Avg F1-score:** 0.9227
- **Weighted Avg F1-score:** 0.9641

---

## Key Features

- Fine-tuned **BERT-base-uncased**
- Custom classification head (768 → 512 → 2)
- Early stopping based on validation loss
- Threshold tuning for imbalanced classification
- Strong performance on real SMS spam dataset

---

## Tech Stack

- Python
- PyTorch
- HuggingFace Transformers
- Scikit-learn
- Pandas / NumPy

---

##  Future Improvements

- Try RoBERTa / DistilBERT
- Data augmentation for minority class
- Focal Loss for imbalance handling
- Deploy model with FastAPI

---

##  Author

Built by: *Bui Thi Cam Ngoan*  
