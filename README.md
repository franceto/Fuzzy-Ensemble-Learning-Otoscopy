# OtoViT Ensemble - Oto-Endoscopic Image Classification

<div align="center">

<!-- Banner hoặc ảnh demo. Có thể thay bằng ảnh trong results/ nếu đã có. -->
<img src="results/confusion_matrix.png" alt="OtoViT Ensemble Result" width="90%" />

<br/>

**Dự án phân loại ảnh nội soi tai bằng 6 Vision Transformer và ensemble với Fuzzy Integral.**

<br/>

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-Deep%20Learning-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)
![timm](https://img.shields.io/badge/timm-Vision%20Transformers-111827?style=for-the-badge)
![Kaggle](https://img.shields.io/badge/Kaggle-Dataset-20BEFF?style=for-the-badge&logo=kaggle&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)

</div>

---

## 1. Project Title & Catchphrase

**OtoViT Ensemble** là dự án phân loại ảnh nội soi tai vào 5 nhóm bệnh lý bằng nhiều mô hình Vision Transformer.

Dự án huấn luyện 6 backbone thị giác, sau đó kết hợp dự đoán bằng các phương pháp ensemble như **Hard Voting**, **Soft Voting**, **Choquet Integral** và **Sugeno Integral**.

> Dự án phục vụ mục đích học tập, nghiên cứu và thử nghiệm mô hình AI. Kết quả dự đoán không thay thế chẩn đoán y khoa.

---

## 2. Quick Demo & Visuals

<div align="center">

[Download Model Weights](https://drive.google.com/file/d/12AoKaKFy1sfNaPvtNEutxHtIc8JKrE6N/view?usp=sharing) ·
[Training Notebook](notebooks/OtoViT.ipynb) ·
[Results Folder](results/)

<br/><br/>

<img src="results/confusion_matrix.png" alt="Confusion Matrix" width="80%" />

</div>


---

## 3. Tính Năng Nổi Bật

- **Phân loại 5 nhóm ảnh nội soi tai:** gồm Acute Otitis Media, Cerumen Impaction, Chronic Otitis Media, Myringosclerosis và Normal.
- **Huấn luyện nhiều Vision Transformer:** sử dụng 6 backbone gồm Swin-T, DeiT-S, CoaT-Lite Small, ViT-B/16, BEiT-B và MaxViT-T.
- **Ensemble nâng cao:** kết hợp mô hình bằng Hard Voting, Soft Voting, Choquet Integral và Sugeno Integral.
- **Tối ưu cho môi trường GPU giới hạn:** thí nghiệm được thực hiện trên RTX 3050 Laptop 4GB VRAM.
- **Tách riêng model weights:** không lưu weights trong repository để tránh dung lượng lớn.

---

## 4. Công Nghệ Sử Dụng

<div align="center">

![Python](https://img.shields.io/badge/Python-Core%20Pipeline-3776AB?style=for-the-badge&logo=python&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-Model%20Training-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)
![timm](https://img.shields.io/badge/timm-ViT%20Backbones-111827?style=for-the-badge)
![torchmetrics](https://img.shields.io/badge/torchmetrics-Evaluation-EE4C2C?style=for-the-badge)
![Albumentations](https://img.shields.io/badge/Albumentations-Augmentation-00A98F?style=for-the-badge)
![scikit-learn](https://img.shields.io/badge/scikit--learn-Metrics-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white)
![OpenCV](https://img.shields.io/badge/OpenCV-Image%20Processing-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Analysis-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![Kaggle](https://img.shields.io/badge/Kaggle-Dataset-20BEFF?style=for-the-badge&logo=kaggle&logoColor=white)

</div>

### Thành phần kỹ thuật

| Nhóm | Công nghệ | Vai trò |
|---|---|---|
| Backbone | Swin-T, DeiT-S, CoaT-Lite Small, ViT-B/16, BEiT-B, MaxViT-T | Trích xuất đặc trưng ảnh nội soi tai |
| Framework | PyTorch | Huấn luyện và inference mô hình |
| Model library | timm | Tải pretrained Vision Transformer backbones |
| Ensemble | Hard Voting, Soft Voting, Choquet, Sugeno | Kết hợp dự đoán từ nhiều mô hình |
| Evaluation | scikit-learn, torchmetrics | Tính metric và tạo confusion matrix |
| Notebook | Jupyter | Chạy pipeline huấn luyện và đánh giá |

---

## 5. Triển Khai Nhanh

**Prerequisites**

- Python 3.10+
- Windows hoặc Linux
- GPU NVIDIA nếu muốn huấn luyện nhanh hơn
- PyTorch CUDA phù hợp với máy đang dùng
- Dataset đặt tại `data/raw/Oto-Endoscopic_Images/`
- Model weights tải riêng nếu chỉ muốn chạy inference hoặc đánh giá lại

```bash
# Clone repository
git clone https://github.com/franceto/OtoViT_Ensemble.git
cd OtoViT_Ensemble

# Tạo và kích hoạt môi trường ảo trên Windows
python -m venv .venv
.venv\Scripts\activate

# Cài PyTorch CUDA 12.1
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121

# Cài thư viện phụ thuộc chính
pip install timm torchmetrics albumentations scikit-learn matplotlib seaborn pandas numpy opencv-python ipykernel jupyter

# Tải models_OtoViT.zip từ Google Drive, sau đó giải nén vào thư mục models
Expand-Archive -Path models_OtoViT.zip -DestinationPath models\

# Mở notebook huấn luyện và đánh giá
cd notebooks
jupyter notebook OtoViT.ipynb
```

---

## 6. Tài Liệu Dự Án

### Bài toán

| Thành phần | Mô tả |
|---|---|
| Input | Ảnh nội soi tai |
| Output | Một trong 5 lớp bệnh lý tai |
| Task | Multi-class image classification |
| Hướng tiếp cận | Huấn luyện nhiều Vision Transformer và ensemble |
| Dữ liệu | Oto-Endoscopic Image Dataset |
| Số ảnh | 3.014 ảnh `.jpg` |
| Số lớp | 5 |
| Split | 80% train / 10% val / 10% test, stratified |

### Các lớp phân loại

```text
Acute Otitis Media
Cerumen Impaction
Chronic Otitis Media
Myringosclerosis
Normal
```

### Dataset

| Hạng mục | Thông tin |
|---|---|
| Dataset | Oto-Endoscopic Image Dataset |
| Nguồn | Kaggle |
| Số ảnh | 3.014 |
| Định dạng ảnh | `.jpg` |
| Số lớp | 5 |
| Vị trí dataset | `data/raw/Oto-Endoscopic_Images/` |

> Link Kaggle trong README gốc chưa có URL cụ thể cho dataset. Hãy cập nhật đường dẫn Kaggle chính xác nếu repository public cần người khác tải lại dữ liệu.

### Models

| Model | Params | Train Time |
|---|---:|---:|
| Swin-T | khoảng 28M | 21 phút |
| DeiT-S | khoảng 22M | 80 phút |
| CoaT-Lite Small | khoảng 20M | 30 phút |
| ViT-B/16 | khoảng 86M | 745 phút |
| BEiT-B | khoảng 86M | 1.556 phút |
| MaxViT-T | khoảng 31M | 3.434 phút |

Tổng thời gian huấn luyện được ghi nhận: khoảng **100 giờ** trên RTX 3050 Laptop 4GB VRAM.

### Model Weights

Weights không được lưu trực tiếp trong repository do dung lượng lớn.

Tải file:

```text
models_OtoViT.zip
```

Link tải:

```text
https://drive.google.com/file/d/12AoKaKFy1sfNaPvtNEutxHtIc8JKrE6N/view?usp=sharing
```

Giải nén vào:

```text
models/
```

Lệnh giải nén trên Windows PowerShell:

```powershell
Expand-Archive -Path models_OtoViT.zip -DestinationPath models\
```

### Kết quả

| Phương pháp | Test Acc |
|---|---:|
| Best Single (Swin-T) | 1.0000 |
| Hard Voting | 1.0000 |
| Soft Voting | 1.0000 |
| Choquet-Init | 1.0000 |
| Choquet-Opt | 1.0000 |
| Choquet-lambda Auto | 1.0000 |
| Sugeno Integral | 1.0000 |

Kết quả và hình ảnh đánh giá được lưu tại:

```text
results/
```

> Kết quả 1.0000 cần được kiểm tra kỹ về cách chia dữ liệu, trùng ảnh, data leakage và tính độc lập giữa train/val/test nếu dùng cho báo cáo học thuật.

### Cấu trúc thư mục

```text
OtoViT_Ensemble/
├── data/
│   └── raw/
│       └── Oto-Endoscopic_Images/     # Đặt dataset vào đây
├── notebooks/
│   └── OtoViT.ipynb                   # Notebook chính
├── models/                            # Đặt file .pth sau khi tải về
├── results/                           # Confusion matrix, loss/acc curves
├── logs/
├── configs/
└── README.md
```

### Gợi ý không commit lên GitHub

```text
.venv/
data/
models/
*.pth
*.pt
*.zip
__pycache__/
.ipynb_checkpoints/
```

### Ghi chú tái lập

- Đặt dataset đúng vào `data/raw/Oto-Endoscopic_Images/`.
- Đặt model weights đã giải nén vào `models/`.
- Chạy notebook `notebooks/OtoViT.ipynb`.
- Kiểm tra lại đường dẫn trong notebook nếu chạy trên máy khác.
- Nếu dùng kết quả cho báo cáo, nên lưu seed, cấu hình transform, batch size, learning rate và phiên bản thư viện.

### Bản quyền

**ANH PHAP TO** — All rights reserved.

### Support

Nếu project hữu ích, hãy cho repository một sao.

Made by **Franceto (ANH PHAP TO)**
