# Huấn Luyện Học Tăng Cường Cho Robot Humanoid HU_D03

Dự án phát triển chính thức các chính sách điều khiển (Locomotion) và bắt chước chuyển động (Mimic) tối ưu cho dòng robot Humanoid 31 bậc tự do (31 DOF) **HU_D03**. Dự án được xây dựng và tối ưu hóa trên nền tảng **mjlab** hỗ trợ mô phỏng vật lý MuJoCo tốc độ cao song song hóa cực đại qua NVIDIA Warp (CUDA).

---

## 📌 Các Tính Năng Nổi Bật

* **Hỗ Trợ Tối Đa 31 DOF:** Cấu hình chuẩn khớp toàn thân bao gồm cả chân nâng cao (achilles joints), hông, eo (waist), tay (shoulder/elbow/wrist) và đầu.
* **Nhóm Tác Vụ Khoa Học:** 
  1. **Locomotion (Điều khiển di chuyển):** Học đi bộ đa hướng linh hoạt trên địa hình phẳng và địa hình gồ ghề phức tạp.
  2. **Mimic (Bắt chước chuyển động mẫu):** Học cách tái hiện mượt mà các chuỗi hành động mẫu phức tạp từ tệp dữ liệu chuyển động (như nhảy múa, chạy, cử chỉ).

---

## 📁 Cấu Trúc Thư Mục Dự Án

```text
Vin/ 
├── HU_D03_03/                  # Thư mục dự án huấn luyện chính (31 DOF)
│   ├── assets/                 # Tài nguyên 3D meshes và file mô hình XML robot
│   │   ├── motions/            # Nơi lưu trữ dữ liệu chuyển động mẫu (.npz) cho Mimic
│   │   └── robots/hu_d03/      # File mô hình XML chính thức của robot HU_D03
│   ├── configs/                # Các file cấu hình hệ thống
│   ├── scripts/                # Scripts chạy huấn luyện (train.py, play.py, csv_to_npz.py)
│   ├── src/hu_d03_03/          # Mã nguồn lõi (tasks/velocity, tasks/mimic)
│   └── pyproject.toml          # Quản lý dependency và cấu hình gói dự án
├── mjlab/                      # Framework mô phỏng MuJoCo + Warp lõi của dự án
│   └── mjlab-main/             # Mã nguồn thư viện mô phỏng song song
├── humanoid-description/       # Thư mục lưu trữ mô tả URDF/MJCF của các dòng robot
└── README.md                   # Tài liệu hướng dẫn sử dụng chính của workspace
```

---

## 🚀 Hướng Dẫn Huấn Luyện

Đảm bảo bạn đã kích hoạt môi trường ảo (ví dụ: `conda activate Vin`).

### 1. Huấn luyện Locomotion (Đi bộ mặt phẳng)
Tác vụ đi bộ trên mặt phẳng phẳng (`plane`), giúp robot nhanh chóng hội tụ dáng đi cơ bản:
```bash
python scripts/train.py Mjlab-Velocity-Flat-HuD03
```

### 2. Huấn luyện Locomotion (Đi bộ địa hình gồ ghề)
Tác vụ nâng cao di chuyển trên địa hình gồ ghề phức tạp có sinh địa hình tự động tăng dần độ khó:
```bash
python scripts/train.py Mjlab-Velocity-Rough-HuD03
```

### 3. Huấn luyện Mimic (Bắt chước chuyển động mẫu)
Học tái hiện tệp chuyển động mục tiêu (cần tệp `hu_d03_motion.npz` tại `assets/motions/`):
```bash
python scripts/train.py Mjlab-Mimic-Flat-HuD03
```




