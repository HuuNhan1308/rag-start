# 📦 Hướng Dẫn Tách 3 Repositories

## 🎯 Tổng Quan

Bạn sẽ tạo 3 repositories riêng biệt:

```
1. rag-vector-storage     (Python FastAPI)
2. rag-backend            (Node.js Express)
3. rag-frontend           (React Vite)
```

---

## 📋 CHECKLIST - Các Files Đã Chuẩn Bị Sẵn

### ✅ Repository 1: rag-vector-storage

Files trong thư mục `faiss-vector-storage/`:
- [x] `README.md` - Hướng dẫn project
- [x] `.gitignore` - Ignore files
- [x] `ENV-SETUP.md` - Hướng dẫn setup env vars
- [x] `Dockerfile` - Docker config (đã có)
- [x] `main.py` - Code chính (đã có)
- [x] `requirements.txt` - Dependencies (đã có)

### ✅ Repository 2: rag-backend

Files trong thư mục `server-nodejs/`:
- [x] `README.md` - Hướng dẫn project
- [x] `.gitignore` - Ignore files
- [x] `ENV-SETUP.md` - Hướng dẫn setup env vars
- [x] `Dockerfile` - Docker config (đã có)
- [x] `package.json` - Dependencies (đã có)
- [x] `src/` - Source code (đã có)

### ✅ Repository 3: rag-frontend

Files trong thư mục `rag-starter/`:
- [x] `README.md` - Hướng dẫn project
- [x] `.gitignore` - Ignore files
- [x] `ENV-SETUP.md` - Hướng dẫn setup env vars
- [x] `package.json` - Dependencies (đã có)
- [x] `src/` - Source code (đã có)

---

## 🚀 BƯỚC 1: Tạo 3 Repositories Trên GitHub

### 1.1. Tạo Repository 1: Vector Storage

1. Vào: https://github.com/new
2. Điền:
   - **Repository name:** `rag-vector-storage`
   - **Description:** `Vector storage service using FAISS for RAG application`
   - **Public** hoặc **Private** (tùy bạn)
   - ❌ **KHÔNG** check "Initialize with README" (đã có sẵn)
3. Click **"Create repository"**
4. **LƯU LẠI URL:** `https://github.com/YOUR_USERNAME/rag-vector-storage.git`

### 1.2. Tạo Repository 2: Backend

1. Vào: https://github.com/new
2. Điền:
   - **Repository name:** `rag-backend`
   - **Description:** `Node.js Express backend for RAG application`
   - **Public** hoặc **Private**
   - ❌ **KHÔNG** check "Initialize with README"
3. Click **"Create repository"**
4. **LƯU LẠI URL:** `https://github.com/YOUR_USERNAME/rag-backend.git`

### 1.3. Tạo Repository 3: Frontend

1. Vào: https://github.com/new
2. Điền:
   - **Repository name:** `rag-frontend`
   - **Description:** `React frontend for RAG chat application`
   - **Public** hoặc **Private**
   - ❌ **KHÔNG** check "Initialize with README"
3. Click **"Create repository"**
4. **LƯU LẠI URL:** `https://github.com/YOUR_USERNAME/rag-frontend.git`

---

## 🚀 BƯỚC 2: Push Code Lên 3 Repositories

### 2.1. Push Vector Storage

```powershell
# Di chuyển vào thư mục vector storage
cd C:\Users\nhanh\OneDrive\Desktop\rag-start\faiss-vector-storage

# Khởi tạo Git
git init

# Add tất cả files
git add .

# Commit
git commit -m "Initial commit: Vector storage service"

# Add remote
git remote add origin https://github.com/YOUR_USERNAME/rag-vector-storage.git

# Push
git branch -M main
git push -u origin main
```

### 2.2. Push Backend

```powershell
# Quay về thư mục gốc
cd ..

# Di chuyển vào thư mục backend
cd server-nodejs

# Khởi tạo Git
git init

# Add tất cả files
git add .

# Commit
git commit -m "Initial commit: Backend service"

# Add remote
git remote add origin https://github.com/YOUR_USERNAME/rag-backend.git

# Push
git branch -M main
git push -u origin main
```

### 2.3. Push Frontend

```powershell
# Quay về thư mục gốc
cd ..

# Di chuyển vào thư mục frontend
cd rag-starter

# Khởi tạo Git
git init

# Add tất cả files
git add .

# Commit
git commit -m "Initial commit: Frontend application"

# Add remote
git remote add origin https://github.com/YOUR_USERNAME/rag-frontend.git

# Push
git branch -M main
git push -u origin main
```

---

## ✅ BƯỚC 3: Kiểm Tra

Sau khi push xong, kiểm tra trên GitHub:

### Vector Storage Repository
- [ ] Vào: `https://github.com/YOUR_USERNAME/rag-vector-storage`
- [ ] Có file `README.md` hiển thị đẹp
- [ ] Có file `Dockerfile`
- [ ] Có file `.gitignore`
- [ ] Có file `ENV-SETUP.md`

### Backend Repository
- [ ] Vào: `https://github.com/YOUR_USERNAME/rag-backend`
- [ ] Có file `README.md` hiển thị đẹp
- [ ] Có file `Dockerfile`
- [ ] Có thư mục `src/`
- [ ] Có file `ENV-SETUP.md`

### Frontend Repository
- [ ] Vào: `https://github.com/YOUR_USERNAME/rag-frontend`
- [ ] Có file `README.md` hiển thị đẹp
- [ ] Có thư mục `src/`
- [ ] Có file `ENV-SETUP.md`

---

## 🎉 XONG! Giờ Bạn Có 3 Repositories

```
✅ rag-vector-storage → Railway
✅ rag-backend        → Railway
✅ rag-frontend       → Vercel
```

---

## 🚀 BƯỚC TIẾP THEO: Deploy

Sau khi có 3 repos, deploy theo file:
👉 **`DEPLOY-NO-DATABASE.md`**

### Tóm tắt:

1. **Railway** - Deploy Vector Storage:
   - New Project → Import `rag-vector-storage`
   - Railway auto-detect Dockerfile → Deploy!

2. **Railway** - Deploy Backend:
   - New Service → Import `rag-backend`
   - Add env vars (xem `ENV-SETUP.md`)
   - Deploy!

3. **Vercel** - Deploy Frontend:
   - New Project → Import `rag-frontend`
   - Add `VITE_API_URL` env var
   - Deploy!

4. **Update CORS** trong Backend:
   - Sửa `CORS_ORIGIN` = Frontend URL

---

## 📝 GHI CHÚ QUAN TRỌNG

### Tạo .env Files Cho Local Development

Mỗi project đều có file `ENV-SETUP.md` hướng dẫn tạo `.env`:

**Vector Storage:**
```bash
cd faiss-vector-storage
# Đọc ENV-SETUP.md và tạo .env file
```

**Backend:**
```bash
cd server-nodejs
# Đọc ENV-SETUP.md và tạo .env file
```

**Frontend:**
```bash
cd rag-starter
# Đọc ENV-SETUP.md và tạo .env file
```

### URLs Lưu Lại

Sau khi push, lưu lại 3 URLs:

```
Vector Storage Repo: https://github.com/YOUR_USERNAME/rag-vector-storage
Backend Repo:        https://github.com/YOUR_USERNAME/rag-backend
Frontend Repo:       https://github.com/YOUR_USERNAME/rag-frontend
```

---

## 🆘 Troubleshooting

### Lỗi: "fatal: remote origin already exists"

```bash
git remote remove origin
git remote add origin <YOUR_REPO_URL>
```

### Lỗi: "Permission denied (publickey)"

1. Kiểm tra SSH key: https://github.com/settings/keys
2. Hoặc dùng HTTPS URL thay vì SSH

### Lỗi: Files quá lớn

Kiểm tra `.gitignore` đã ignore:
- `node_modules/`
- `__pycache__/`
- `.venv/`
- `dist/`

---

## 🎯 Checklist Cuối Cùng

Trước khi deploy:

- [ ] Đã tạo 3 repositories trên GitHub
- [ ] Đã push code lên cả 3 repos
- [ ] Kiểm tra README.md hiển thị đẹp trên GitHub
- [ ] Có file `.gitignore` và `ENV-SETUP.md` trong mỗi repo
- [ ] Không có files nhạy cảm (.env, node_modules) bị commit
- [ ] Đã lưu lại 3 URLs

### Nếu TẤT CẢ ✅:

**👉 Tiếp tục với:** `DEPLOY-NO-DATABASE.md`

---

**Chúc bạn thành công! 🚀**

Nếu gặp vấn đề, hỏi tôi nhé! 😊
