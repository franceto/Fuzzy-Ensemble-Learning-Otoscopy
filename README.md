# 🦻 OtoViT Ensemble — Oto-Endoscopic Image Classification

Huấn luyện 6 Vision Transformer trên dataset nội soi tai, kết hợp Fuzzy Integral (Choquet & Sugeno) để ensemble.

---

## 📋 Bài toán

Phân loại 5 bệnh lý tai qua ảnh nội soi:
`Acute Otitis Media` · `Cerumen Impaction` · `Chronic Otitis Media` · `Myringosclerosis` · `Normal`

---

## 📂 Dữ liệu

- **Dataset:** [Oto-Endoscopic Image Dataset](https://www.kaggle.com/datasets/) — 3,014 ảnh `.jpg`, 5 class
- **Split:** 80% Train / 10% Val / 10% Test (stratified)
- Đặt dataset vào: `data/raw/Oto-Endoscopic_Images/`

---

## 🤖 Models

| Model           | Params | Train Time |
| --------------- | ------ | ---------- |
| Swin-T          | ~28M   | 21 phút    |
| DeiT-S          | ~22M   | 80 phút    |
| CoaT-Lite Small | ~20M   | 30 phút    |
| ViT-B/16        | ~86M   | 745 phút   |
| BEiT-B          | ~86M   | 1,556 phút |
| MaxViT-T        | ~31M   | 3,434 phút |

> ⏱️ Tổng thời gian huấn luyện: **~100 giờ** trên RTX 3050 Laptop 4GB VRAM

---

## 🚀 Cài đặt

```bash
git clone https://github.com/franceto/OtoViT_Ensemble.git
cd OtoViT_Ensemble
python -m venv .venv
.venv\Scripts\activate        # Windows
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121
pip install timm torchmetrics albumentations scikit-learn matplotlib seaborn pandas numpy opencv-python ipykernel jupyter
```

---

## 📥 Tải Model Weights

Weights không lưu trong repo do dung lượng lớn. Tải `models_OtoViT.zip` tại Google Drive, giải nén vào `models/`:

👉 **[Download models_OtoViT.zip](https://drive.google.com/file/d/12AoKaKFy1sfNaPvtNEutxHtIc8JKrE6N/view?usp=sharing)**

```powershell
Expand-Archive -Path models_OtoViT.zip -DestinationPath models\
```

---

## 📓 Chạy notebook

```bash
cd notebooks
jupyter notebook OtoViT.ipynb
```

---

## 📁 Cấu trúc thư mục

```
OtoViT_Ensemble/
├── data/raw/                  ← đặt dataset vào đây
├── notebooks/OtoViT.ipynb     ← notebook chính
├── models/                    ← đặt file .pth sau khi tải về
├── results/                   ← confusion matrix, loss/acc curves
├── logs/
└── configs/
```

---

## 📊 Kết quả

| Phương pháp          | Test Acc |
| -------------------- | -------- |
| Best Single (Swin-T) | 1.0000   |
| Hard Voting          | 1.0000   |
| Soft Voting          | 1.0000   |
| Choquet-Init         | 1.0000   |
| Choquet-Opt          | 1.0000   |
| Choquet-λ Auto       | 1.0000   |
| Sugeno Integral      | 1.0000   |

> Kết quả lưu tại `results/`

---

## © Bản quyền

**ANH PHAP TO** — All rights reserved.

---

⭐ Nếu thấy repo này bổ ích, hãy cho tôi 1 sao để ủng hộ công sức nghiên cứu!
