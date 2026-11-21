# Huong dan Dong gop (Contributing Guidelines)

Cam on ban da quan tam den du an **smart-agri-lakehouse-mekong**. Du an rat hoan nghenh cac dong gop tu cong dong nghien cuu va lap trinh vien.

---

## 1. Quy trinh dong gop ma nguon (Workflow)

1. **Fork** repository ve tai khoan ca nhan cua ban tren GitHub.
2. Clone repository ve may cuc bo:
   ```bash
   git clone https://github.com/<your-username>/smart-agri-lakehouse-mekong.git
   cd smart-agri-lakehouse-mekong
   ```
3. Tao nhanh tinh nang moi (Feature Branch):
   ```bash
   git checkout -b feature/ten-tinh-nang
   ```
4. Thuc hien cac thay doi, dam bao ma nguon chay on dinh va vuot qua kiem thu:
   ```bash
   pytest tests/
   flake8 src/
   ```
5. Commit thay doi theo quy chuan commit:
   ```bash
   git commit -m "feat(storage): bo sung co che doc ghi streaming Delta Lake"
   ```
6. Push nhanh len fork cua ban:
   ```bash
   git push origin feature/ten-tinh-nang
   ```
7. Mo mot **Pull Request (PR)** den nhanh `main` cua repository goc.

---

## 2. Quy uoc Commit (Conventional Commits)

Vui long su dung cac tien to chuan sau:
- `feat:` Tinh nang moi cho he thong.
- `fix:` Sua loi trong ma nguon.
- `docs:` Cap nhat tai lieu hoac README.
- `perf:` Cai tien hieu nang truy van hoac cache.
- `test:` Bo sung hoac sua doi ca kiem thu.
- `refactor:` Tai cau truc ma nguon ma khong lam thay doi hanh vi.

---

## 3. Lien he ho tro

Neu gap loi hoac co thac mac ve kien truc nghien cuu, vui long mo mot **Issue** tren GitHub hoac lien he qua email: `toim2526014@gstudent.ctu.edu.vn`.
