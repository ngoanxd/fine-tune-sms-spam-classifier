<h1 align="center">SMS Spam Detection using BERT (Fine-tuning with PyTorch)</h1>

<p align="center">
  Fine-tuning BERT with PyTorch for SMS spam classification
</p>
Dự án xây dựng mô hình phân loại tin nhắn SMS spam bằng cách fine-tune BERT-base-uncased với classification head tùy chỉnh.

---

##  Project Overview
- Backbone model: BERT-base-uncased  
- Feature extraction: [CLS] token embedding (768-d)  
- Classification head: Fully Connected Neural Network  
- Task: Binary classification (Spam / Ham)  

---

##  Model Architecture
<p align="center">
  <img src="https://github.com/user-attachments/assets/dea06d9e-023b-45d2-91d7-f92492492b5a" width="400" />
</p>

---

##  Training Strategy
- Fine-tune toàn bộ BERT + classification head  
- Loss: CrossEntropyLoss  
- Optimizer: AdamW  
- Early Stopping: dừng nếu val loss không cải thiện 3 epoch liên tiếp  
- Dropout trong fully connected layer  

---

##  Class Imbalance Handling
- Dataset bị lệch (spam ít hơn ham)  
- Điều chỉnh decision threshold (không cố định 0.5)  
- Ưu tiên tăng recall cho class Spam (1)  

---

##  Evaluation Results
| Class | Precision | Recall | F1-score | Support |
|------|----------|--------|----------|---------|
| 0 (Ham)  | 0.9793 | 0.9793 | 0.9793 | 723 |
| 1 (Spam) | 0.8661 | 0.8661 | 0.8661 | 112 |

### Overall Performance
- Accuracy: 0.9641  
- Macro F1: 0.9227  
- Weighted F1: 0.9641  

---

##  Key Features
- Fine-tuned BERT-base-uncased  
- Custom classifier (768 → 512 → 2)  
- Early stopping  
- Threshold tuning  
- Handle imbalance hiệu quả  

---

##  Tech Stack
- Python  
- PyTorch  
- HuggingFace Transformers  
- Scikit-learn  
- Pandas / NumPy  

---

##  Future Improvements
- RoBERTa / DistilBERT  
- Data augmentation  
- Focal Loss  
- Deploy FastAPI  

---

##  Author
Bui Thi Cam Ngoan
