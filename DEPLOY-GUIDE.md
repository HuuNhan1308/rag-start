# 🚀 Hướng Dẫn Deploy RAG Application - Dành Cho Người Mới

## 📋 Tổng Quan

Bạn có 3 services cần deploy:
1. **Frontend (React)** - Giao diện người dùng
2. **Backend (Node.js)** - API server
3. **Vector Storage (Python FastAPI)** - Vector database

## 🎯 Phương Án Deploy Đơn Giản Nhất

Chúng ta sẽ sử dụng **Render.com** - một platform miễn phí và rất dễ sử dụng cho người mới.

### ✅ Ưu điểm:
- ✨ Miễn phí cho các dự án nhỏ
- 🎮 Giao diện đơn giản, không cần biết Docker
- 🔄 Tự động deploy khi bạn push code lên GitHub
- 📦 Hỗ trợ PostgreSQL database miễn phí
- 🌐 Tự động có HTTPS

---

## 📝 BƯỚC 1: CHUẨN BỊ CODE

### 1.1. Cài đặt Git (nếu chưa có)

Tải và cài đặt Git từ: https://git-scm.com/download/win

### 1.2. Đẩy code lên GitHub

Mở PowerShell trong thư mục dự án và chạy:

```bash
# Khởi tạo git repository
git init

# Thêm tất cả files
git add .

# Commit
git commit -m "Initial commit for deployment"

# Tạo repo mới trên GitHub (đi đến github.com và tạo repository mới)
# Sau đó liên kết và đẩy code lên
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
git branch -M main
git push -u origin main
```

**Lưu ý:** Thay `YOUR_USERNAME` và `YOUR_REPO_NAME` bằng thông tin của bạn.

---

## 🌐 BƯỚC 2: ĐĂNG KÝ RENDER.COM

1. Truy cập: https://render.com
2. Click "Get Started" và đăng ký bằng GitHub account
3. Cho phép Render truy cập vào repositories của bạn

---

## 🗄️ BƯỚC 3: TẠO DATABASE (PostgreSQL)

1. Trong Render Dashboard, click **"New +"** → chọn **"PostgreSQL"**
2. Điền thông tin:
   - **Name**: `rag-database`
   - **Database**: `rag_db`
   - **User**: `rag_user` (tự động tạo)
   - **Region**: Chọn region gần bạn nhất
   - **Plan**: Chọn **"Free"**
3. Click **"Create Database"**
4. **LƯU LẠI** các thông tin sau (Render sẽ hiển thị):
   - Internal Database URL (dùng cho backend)
   - External Database URL (nếu muốn connect từ máy local)

---

## 🐍 BƯỚC 4: DEPLOY VECTOR STORAGE (Python FastAPI)

### 4.1. Trong Render Dashboard:

1. Click **"New +"** → chọn **"Web Service"**
2. Connect đến GitHub repository của bạn
3. Điền thông tin:
   - **Name**: `rag-vector-storage`
   - **Region**: Chọn region gần bạn
   - **Root Directory**: `faiss-vector-storage`
   - **Runtime**: **"Python 3"**
   - **Build Command**: `pip install -r requirements.txt`
   - **Start Command**: `uvicorn main:app --host 0.0.0.0 --port $PORT`
   - **Plan**: Chọn **"Free"**

4. Click **"Create Web Service"**

5. Sau khi deploy xong, **LƯU LẠI URL** (dạng: `https://rag-vector-storage.onrender.com`)

---

## 🟢 BƯỚC 5: DEPLOY BACKEND (Node.js)

### 5.1. Tạo file cấu hình môi trường

Trong Render Dashboard:

1. Click **"New +"** → chọn **"Web Service"**
2. Connect đến GitHub repository
3. Điền thông tin:
   - **Name**: `rag-backend`
   - **Region**: Chọn region giống với database
   - **Root Directory**: `server-nodejs`
   - **Runtime**: **"Node"**
   - **Build Command**: `npm install && npm run build`
   - **Start Command**: `npm start`
   - **Plan**: Chọn **"Free"**

### 5.2. Thêm Environment Variables

Trong phần **"Environment"**, thêm các biến sau:

```
NODE_ENV=production
PORT=10000

# Database (lấy từ PostgreSQL bạn tạo ở bước 3)
DATABASE_URL=<Internal_Database_URL_từ_bước_3>

# Vector Storage (lấy từ bước 4)
VECTOR_STORAGE_URL=https://rag-vector-storage.onrender.com

# JWT Secret (tự tạo một chuỗi ngẫu nhiên phức tạp)
JWT_SECRET=your_super_secret_jwt_key_here_change_this
JWT_EXPIRES_IN=7d

# Google AI API Key (nếu bạn đang dùng)
GOOGLE_API_KEY=your_google_api_key_here

# CORS Origin (sẽ cập nhật sau khi deploy frontend)
CORS_ORIGIN=*
```

4. Click **"Create Web Service"**
5. Sau khi deploy xong, **LƯU LẠI URL** (dạng: `https://rag-backend.onrender.com`)

---

## ⚛️ BƯỚC 6: DEPLOY FRONTEND (React)

### 6.1. Render Static Site:

1. Click **"New +"** → chọn **"Static Site"**
2. Connect đến GitHub repository
3. Điền thông tin:
   - **Name**: `rag-frontend`
   - **Root Directory**: `rag-starter`
   - **Build Command**: `yarn install && yarn build`
   - **Publish Directory**: `dist`

### 6.2. Thêm Environment Variables

Trong phần **"Environment"**, thêm:

```
VITE_API_URL=https://rag-backend.onrender.com
```

4. Click **"Create Static Site"**
5. Sau khi deploy xong, bạn sẽ có URL frontend (dạng: `https://rag-frontend.onrender.com`)

---

## 🔄 BƯỚC 7: CẬP NHẬT CORS

### 7.1. Quay lại Backend Service

1. Vào Backend service trong Render Dashboard
2. Vào **"Environment"**
3. Sửa biến `CORS_ORIGIN`:
   ```
   CORS_ORIGIN=https://rag-frontend.onrender.com
   ```
4. Click **"Save Changes"** - Backend sẽ tự động restart

---

## ✅ BƯỚC 8: KIỂM TRA

### 8.1. Test từng service:

1. **Vector Storage**: 
   - Mở: `https://rag-vector-storage.onrender.com/docs`
   - Bạn sẽ thấy Swagger UI

2. **Backend**:
   - Mở: `https://rag-backend.onrender.com`
   - Nếu hiển thị JSON response → OK

3. **Frontend**:
   - Mở: `https://rag-frontend.onrender.com`
   - Ứng dụng của bạn sẽ xuất hiện!

---

## 🎉 HOÀN TẤT!

Giờ ứng dụng của bạn đã live trên internet! 

### 📌 URLs Quan Trọng:

- **Ứng dụng của bạn**: `https://rag-frontend.onrender.com`
- **Backend API**: `https://rag-backend.onrender.com`
- **Vector Storage**: `https://rag-vector-storage.onrender.com`

---

## 🚨 LƯU Ý QUAN TRỌNG

### ⚠️ Free Tier Limitations:

1. **Services sẽ "ngủ" sau 15 phút không hoạt động**
   - Lần đầu truy cập sẽ mất 30-60 giây để "thức dậy"
   - Đây là bình thường với Free tier

2. **Database có giới hạn**:
   - 90 ngày sử dụng miễn phí
   - 256MB storage
   - Đủ cho testing và demo

3. **750 giờ/tháng** cho mỗi service miễn phí

### 💡 Nếu muốn upgrade sau này:

- **Render**: $7/tháng cho mỗi service (không sleep)
- **Database**: $7/tháng (không giới hạn thời gian)

---

## 🔧 CẬP NHẬT CODE SAU NÀY

Khi bạn muốn cập nhật code:

```bash
# Chỉnh sửa code của bạn
# Sau đó:
git add .
git commit -m "Mô tả thay đổi"
git push
```

Render sẽ **tự động** phát hiện và deploy lại! 🎉

---

## 🆘 TROUBLESHOOTING

### Nếu Frontend không kết nối được Backend:

1. Kiểm tra `VITE_API_URL` trong Frontend environment variables
2. Kiểm tra `CORS_ORIGIN` trong Backend environment variables
3. Xem logs trong Render Dashboard → chọn service → tab "Logs"

### Nếu Backend không kết nối được Database:

1. Kiểm tra `DATABASE_URL` có đúng không
2. Xem logs của Backend service

### Nếu Service không start được:

1. Vào service trong Render Dashboard
2. Click tab **"Logs"**
3. Xem lỗi gì và google/hỏi AI

---

## 🎓 TÀI LIỆU THAM KHẢO

- Render Docs: https://render.com/docs
- Deploy FastAPI: https://render.com/docs/deploy-fastapi
- Deploy Node.js: https://render.com/docs/deploy-node-express-app
- Deploy React: https://render.com/docs/deploy-create-react-app

---

## 📞 CẦN TRỢ GIÚP?

Nếu gặp vấn đề, hãy:
1. Đọc kỹ phần Troubleshooting
2. Kiểm tra Logs trong Render Dashboard
3. Google với từ khóa: "render.com deploy [tên lỗi]"

Chúc bạn deploy thành công! 🚀
