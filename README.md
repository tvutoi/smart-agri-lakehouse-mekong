# smart-agri-lakehouse-mekong

Kien truc Ho Du lieu Phan tan (Lakehouse) va Toi uu hoa Truy van Du lieu Lon trong Nong nghiep Thong minh Dong bang Song Cuu Long (DBSCL).

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Python: 3.10+](https://img.shields.io/badge/Python-3.10%2B-brightgreen.svg)](https://www.python.org/)
[![Storage: Delta Lake](https://img.shields.io/badge/Storage-Delta%20Lake-00A4E4.svg)](https://delta.io/)
[![Query: Trino](https://img.shields.io/badge/Query-Trino%20%2F%20Presto-FF6B6B.svg)](https://trino.io/)

---

## 1. Gioi thieu de tai

Nghien cuu xay dung kien truc ho du lieu phan tan nham tich hop du lieu da nguon tu cac tram cam bien IoT quan trac xam nhap man, thuy van va thoi tiet tai 13 tinh thanh DBSCL. He thong ket hop tinh nhat quan giao dich ACID voi kha nang truy van da chieu toc do cao, phuc vu canh bao som va dieu tiet thuy loi tu dong.

### Cac dong gop chinh:
- **Kien truc 4 tang**: Thu thap (Kafka) -> Luu tru ACID (Delta Lake tren MinIO) -> Bo nho dem tang toc (Alluxio Tiered Cache) -> Truy van phan tich da chieu (Trino/Presto Photon).
- **Dot pha ky thuat**:
  - Giai quyet lo hong stale read thong qua co che lang nghe nhat ky giao dich tu dong (*Delta Log Listener*).
  - Giam thieu I/O quet bang chi muc lap day khong gian 3D (*Z-Order 3D Clustering*).
- **Ket qua thuc nghiem 500GB**: Tang toc do truy van gap **12.8x**, ti le trung cache dat **82.6%**, giam **78.4%** luu luong shuffle I/O.

---

## 2. Cau truc thu muc

```text
smart-agri-lakehouse-mekong/
|-- data/
|   |-- raw/                  # Du lieu cam bien IoT tho
|   |-- processed/            # Du lieu da chuan hoa Delta Lake/Parquet
|-- src/
|   |-- ingestion/            # Thu thap streaming (Apache Kafka & MQTT)
|   |-- storage/              # Quan tri bang Delta Lake & MinIO
|   |-- query/                # Toi uu hoa truy van Trino / Presto
|-- docs/                     # Tai lieu kien truc va huong dan cai dat
|-- results/
|   |-- benchmarks/           # Log do dac do tre, throughput va shuffle I/O
|-- notebooks/                # Jupyter Notebooks mo hinh hoa va phan tich
|-- CITATION.cff              # Huong dan trich dan chuan Citation File Format
|-- CONTRIBUTING.md           # Quy dinh dong gop ma nguon va quy trinh PR
|-- LICENSE                   # Giay phep ma nguon mo (MIT License)
|-- requirements.txt          # Danh sach cac thu vien phu thuoc
|-- README.md                 # Tai lieu gioi thieu tong quan
```

---

## 3. Huong dan cai dat va chay nhanh (Quickstart)

### Yeu cau he thong:
- Python 3.10 tro len.
- Docker & Docker Compose (phuc vu khoi chay Kafka, MinIO, Alluxio).

### Cac buoc thuc hien:
```bash
# 1. Clone repository
git clone https://github.com/tvutoi/smart-agri-lakehouse-mekong.git
cd smart-agri-lakehouse-mekong

# 2. Tao moi truong ao va cai dat thu vien
python -m venv .venv
source .venv/bin/activate  # Tren Windows: .venv\Scripts\activate
pip install -r requirements.txt

# 3. Chay thu nghiem mo phong luong du lieu
python src/ingestion/kafka_stream.py --topic sensor_salinity_dbscl
```

---

## 4. Trich dan nghien cuu (Citation)

Neu ban su dung ma nguon hoac du lieu tu repository nay trong cac cong bo khoa hoc, vui long trich dan:

```bibtex
@article{tang2026lakehouse,
  author    = {Tang Van Ut Toi},
  title     = {Kien truc Ho Du lieu Phan tan (Lakehouse) va Toi uu hoa Truy van Du lieu Lon trong Nong nghiep Thong minh DBSCL},
  journal   = {Luan van Thac si He thong Thong tin, Dai hoc Can Tho},
  year      = {2026},
  doi       = {10.1145/lakehouse.dbscl.2026.014},
  url       = {https://github.com/tvutoi/smart-agri-lakehouse-mekong}
}
```

---

## 5. Giay phep su dung (License)

Du an nay duoc phan phoi duoi **Giay phep MIT (MIT License)**. Xem tep [LICENSE](LICENSE) de biet them chi tiet ve quyen su dung va mien tru trach nhiem.
