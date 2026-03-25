🦻 OtoViT Ensemble — Oto-Endoscopic Image Classification
Huấn luyện 6 Vision Transformer trên dataset nội soi tai, kết hợp Fuzzy Integral (Choquet & Sugeno) để ensemble.

📋 Bài toán
Phân loại 5 bệnh lý tai qua ảnh nội soi:
Acute Otitis Media · Cerumen Impaction · Chronic Otitis Media · Myringosclerosis · Normal

📂 Dữ liệu

Dataset: Oto-Endoscopic Image Dataset — 3,014 ảnh .jpg, 5 class
Split: 80% Train / 10% Val / 10% Test (stratified)
Đặt dataset vào: data/raw/Oto-Endoscopic_Images/

🤖 Models
ModelParamsTrain TimeSwin-T~28M21 phútDeiT-S~22M80 phútCoaT-Lite Small~20M30 phútViT-B/16~86M745 phútBEiT-B~86M1,556 phútMaxViT-T~31M3,434 phút

⏱️ Tổng thời gian huấn luyện: ~100 giờ trên RTX 3050 Laptop 4GB VRAM

🚀 Cài đặt
bashgit clone https://github.com/<your-username>/OtoViT_Ensemble.git
cd OtoViT_Ensemble
python -m venv .venv
.venv\Scripts\activate # Windows
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121
pip install timm torchmetrics albumentations scikit-learn matplotlib seaborn pandas numpy opencv-python ipykernel jupyter

📓 Chạy notebook
bashcd notebooks
jupyter notebook OtoViT.ipynb

📁 Cấu trúc thư mục
OtoViT_Ensemble/
├── data/raw/ ← đặt dataset vào đây
├── notebooks/OtoViT.ipynb ← notebook chính
├── models/ ← file .pth đã train (public)
├── results/ ← confusion matrix, loss/acc curves
├── logs/
└── configs/

📊 Kết quả
Phương pháp Test Acc
Best Single (Swin-T) 1.0000
Hard Voting 1.0000
Soft Voting 1.0000
Choquet-Init 1.0000
Choquet-Opt 1.0000
Choquet-λ Auto 1.0000
Sugeno Integral 1.0000

Kết quả lưu tại results/

🔓 Model Weights
Pretrained .pth weights được public tại thư mục models/ — tự do sử dụng cho mục đích nghiên cứu.

© Bản quyền
ANH PHAP TO — All rights reserved.

⭐ If you find this repository helpful, please give me a star to show your support for my research!
