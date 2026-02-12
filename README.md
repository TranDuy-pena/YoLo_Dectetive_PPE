### 👷‍♂️🦺 Construction Site Safety Detection using YOLOv8

## 🚧 AI giám sát an toàn lao động tại công trình xây dựng bằng Computer Vision

# 📌 Giới Thiệu Dự Án

Dự án này sử dụng mô hình YOLOv8 để phát hiện và giám sát việc sử dụng đồ bảo hộ lao động (PPE) tại công trình xây dựng.

🎯 Mục tiêu hệ thống:

👷 Phát hiện công nhân (Person)

🪖 Kiểm tra đội mũ bảo hộ (Hardhat)

🦺 Kiểm tra áo phản quang (Safety Vest)

😷 Kiểm tra khẩu trang (Mask)

🚨 Phát hiện vi phạm an toàn (NO-Hardhat, NO-Safety Vest, NO-Mask)

📊 Hỗ trợ thống kê và cảnh báo thời gian thực

📦 Dataset Sử Dụng

# Dự án sử dụng dataset:

👉 Construction Site Safety Image Dataset Roboflow
Xuất bản trên nền tảng Kaggle

📊 Thông tin dataset

📷 2,801 ảnh

🏷 10 lớp đối tượng

📂 Chia sẵn: train / valid / test

📐 Định dạng: Chuẩn YOLO (bounding box)

🏷 Các lớp (Classes)
ID	Class
0	Hardhat
1	Mask
2	NO-Hardhat
3	NO-Mask
4	NO-Safety Vest
5	Person
6	Safety Cone
7	Safety Vest
8	machinery
9	vehicle

## 🗂 Cấu Trúc Thư Mục
construction-safety-yolo/
│
├── datasets/
│   └── construction_safety/
│       ├── train/
│       ├── valid/
│       ├── test/
│       └── data.yaml
│
├── runs/
│
├── train.py
├── predict.py
├── requirements.txt
└── README.md

## ⚙️ Cài Đặt
# 1️⃣ Clone project
git clone https://github.com/yourname/construction-safety-yolo.git
cd construction-safety-yolo

# 2️⃣ Cài thư viện
pip install ultralytics opencv-python matplotlib


Hoặc:

pip install -r requirements.txt

📥 Tải Dataset
Cách 1: Tải thủ công

Truy cập Kaggle và download dataset → giải nén vào:

datasets/construction_safety/

Cách 2: Dùng Kaggle API
pip install kaggle
kaggle datasets download -d snehilsanyal/construction-site-safety-image-dataset-roboflow -p datasets/construction_safety --unzip

🚀 Huấn Luyện Model
yolo detect train \
data=datasets/construction_safety/data.yaml \
model=yolov8n.pt \
imgsz=640 \
epochs=50 \
batch=16


# 📌 Model tốt nhất:

runs/detect/train/weights/best.pt

🔎 Dự Đoán
🖼 Predict ảnh
yolo detect predict \
model=runs/detect/train/weights/best.pt \
source=image.jpg \
conf=0.4

🎥 Predict video
yolo detect predict \
model=runs/detect/train/weights/best.pt \
source=video.mp4 \
conf=0.4

## 🧠 Logic Cảnh Báo An Toàn (Optional)

# Ví dụ rule:

Nếu phát hiện Person nhưng không có Hardhat → 🚨 Cảnh báo vi phạm

Nếu có NO-Hardhat → 🚨 Vi phạm trực tiếp

Nếu có NO-Safety Vest → 🚨 Không mặc áo phản quang

# Có thể mở rộng:

📊 Thống kê % tuân thủ

📡 Kết nối camera RTSP

📁 Lưu log vi phạm

🌐 Triển Khai Ứng Dụng

# Có thể tích hợp với:

🐍 Flask

⚡ FastAPI

📊 Streamlit

☁ AWS / GCP

📹 Camera IP realtime

| Metric    | Giá trị      |
| --------- | ------------ |
| mAP50     | ~0.90        |
| Precision | ~92%         |
| Recall    | ~89%         |
| Inference | < 30ms (GPU) |

## ⚠️ Lưu Ý

🚧 Hệ thống dùng cho mục đích nghiên cứu và hỗ trợ giám sát.
Không thay thế hoàn toàn trách nhiệm của bộ phận an toàn lao động.

## 👨‍💻 Tác Giả

👤 Lê Trần Duy

🎓 NGUYEN TAT THANH University 

📧 Email: letranduy24503@gmail.com


⭐ Nếu thấy hữu ích

Hãy ⭐ repository để ủng hộ dự án!
