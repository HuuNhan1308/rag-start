# ✅ CHECKLIST DEPLOY - In Ra Và Đánh Dấu

## 📋 GIAI ĐOẠN 1: CHUẨN BỊ

### Code & Testing
- [ ] Tất cả 3 services chạy tốt trên local
- [ ] Frontend kết nối được Backend
- [ ] Backend kết nối được Vector Storage
- [ ] Backend kết nối được Database (local)
- [ ] Đã test upload file
- [ ] Đã test chat với RAG

### Git & GitHub
- [ ] Đã cài Git trên máy
- [ ] Có tài khoản GitHub
- [ ] Đã tạo repository mới trên GitHub
- [ ] Repository là public (hoặc có plan private)

### Environment Variables
- [ ] Có Google API Key (nếu dùng)
- [ ] Đã tạo JWT Secret (chuỗi ngẫu nhiên dài)
- [ ] Biết các env vars cần thiết

### Platform
- [ ] Đã đăng ký Render.com
- [ ] Đã connect GitHub với Render
- [ ] Đã đọc hướng dẫn deploy

---

## 📋 GIAI ĐOẠN 2: PUSH CODE LÊN GITHUB

```bash
# Chạy từng lệnh và đánh dấu
```

- [ ] `git init`
- [ ] `git add .`
- [ ] `git commit -m "Initial commit for deployment"`
- [ ] `git remote add origin https://github.com/USERNAME/REPO.git`
- [ ] `git branch -M main`
- [ ] `git push -u origin main`
- [ ] Kiểm tra code đã lên GitHub

---

## 📋 GIAI ĐOẠN 3: TẠO DATABASE

- [ ] Vào Render Dashboard
- [ ] Click "New +" → "PostgreSQL"
- [ ] Name: `rag-database`
- [ ] Region: Singapore (hoặc gần nhất)
- [ ] Plan: Free
- [ ] Click "Create Database"
- [ ] **Copy Internal Database URL** → Lưu vào notepad

```
DATABASE_URL = ________________________________
```

---

## 📋 GIAI ĐOẠN 4: DEPLOY VECTOR STORAGE

- [ ] Click "New +" → "Web Service"
- [ ] Chọn GitHub repository
- [ ] Name: `vector-storage`
- [ ] Root Directory: `faiss-vector-storage`
- [ ] Runtime: Python 3
- [ ] Build Command: `pip install -r requirements.txt`
- [ ] Start Command: `uvicorn main:app --host 0.0.0.0 --port $PORT`
- [ ] Plan: Free
- [ ] Click "Create Web Service"
- [ ] Đợi deploy xong (5-10 phút)
- [ ] **Copy URL** → Lưu vào notepad

```
VECTOR_STORAGE_URL = ________________________________
```

- [ ] Test URL: Mở `https://[URL]/docs` → Thấy Swagger UI

---

## 📋 GIAI ĐOẠN 5: DEPLOY BACKEND

- [ ] Click "New +" → "Web Service"
- [ ] Chọn GitHub repository
- [ ] Name: `backend`
- [ ] Root Directory: `server-nodejs`
- [ ] Runtime: Node
- [ ] Build Command: `npm install && npm run build`
- [ ] Start Command: `npm start`
- [ ] Plan: Free

### Environment Variables (Thêm từng cái):

- [ ] `NODE_ENV` = `production`
- [ ] `PORT` = `10000`
- [ ] `DATABASE_URL` = `[paste từ bước 3]`
- [ ] `VECTOR_STORAGE_URL` = `[paste từ bước 4]`
- [ ] `JWT_SECRET` = `[chuỗi ngẫu nhiên của bạn]`
- [ ] `JWT_EXPIRES_IN` = `7d`
- [ ] `CORS_ORIGIN` = `*` (sẽ sửa sau)
- [ ] `CORS_METHODS` = `GET,POST,PUT,DELETE,PATCH,OPTIONS`
- [ ] `CORS_ALLOWED_HEADERS` = `Content-Type,Authorization`
- [ ] `GOOGLE_API_KEY` = `[API key của bạn]` (nếu có)

- [ ] Click "Create Web Service"
- [ ] Đợi deploy xong (5-10 phút)
- [ ] **Copy URL** → Lưu vào notepad

```
BACKEND_URL = ________________________________
```

- [ ] Test URL: Mở `https://[URL]` → Thấy JSON response

---

## 📋 GIAI ĐOẠN 6: DEPLOY FRONTEND

- [ ] Click "New +" → "Static Site"
- [ ] Chọn GitHub repository
- [ ] Name: `frontend`
- [ ] Root Directory: `rag-starter`
- [ ] Build Command: `yarn install && yarn build`
- [ ] Publish Directory: `dist`

### Environment Variables:

- [ ] `VITE_API_URL` = `[paste BACKEND_URL từ bước 5]`

- [ ] Click "Create Static Site"
- [ ] Đợi deploy xong (5-10 phút)
- [ ] **Copy URL** → Đây là link ứng dụng!

```
FRONTEND_URL = ________________________________
```

---

## 📋 GIAI ĐOẠN 7: CẬP NHẬT CORS

- [ ] Quay lại Backend service
- [ ] Click tab "Environment"
- [ ] Tìm biến `CORS_ORIGIN`
- [ ] Sửa từ `*` thành `[FRONTEND_URL từ bước 6]`
- [ ] Click "Save Changes"
- [ ] Đợi backend restart (1-2 phút)

---

## 📋 GIAI ĐOẠN 8: KIỂM TRA

### Vector Storage
- [ ] Mở: `[VECTOR_STORAGE_URL]/docs`
- [ ] Thấy Swagger UI
- [ ] Test endpoint `/debug`

### Backend
- [ ] Mở: `[BACKEND_URL]`
- [ ] Thấy JSON: `{"msg": "Server is up.."}`
- [ ] Test endpoint `/api/v1/...` (nếu có)

### Frontend
- [ ] Mở: `[FRONTEND_URL]`
- [ ] Trang web hiển thị đúng
- [ ] Không có lỗi trong Console (F12)

### Tích Hợp
- [ ] Upload file từ frontend
- [ ] Chat với RAG
- [ ] Kiểm tra response có đúng không

---

## 📋 GIAI ĐOẠN 9: HOÀN TẤT

- [ ] Tất cả services đều chạy
- [ ] Không có lỗi trong logs
- [ ] Ứng dụng hoạt động end-to-end
- [ ] Đã lưu lại tất cả URLs

### Lưu Thông Tin Quan Trọng:

```
=== THÔNG TIN DEPLOY ===

Frontend URL: ________________________________
Backend URL: ________________________________
Vector Storage URL: ________________________________
Database URL: ________________________________

JWT Secret: ________________________________
Google API Key: ________________________________

Ngày Deploy: ____/____/______
Platform: Render.com
Plan: Free Tier

=========================
```

---

## 📋 SAU KHI DEPLOY

### Chia Sẻ
- [ ] Gửi Frontend URL cho bạn bè/khách hàng
- [ ] Hướng dẫn cách sử dụng

### Monitoring
- [ ] Bookmark Render Dashboard
- [ ] Kiểm tra logs thường xuyên
- [ ] Theo dõi usage (để không vượt free tier)

### Backup
- [ ] Lưu file `CHECKLIST.md` này với thông tin đã điền
- [ ] Lưu tất cả env vars vào nơi an toàn
- [ ] Backup database (nếu có data quan trọng)

---

## 🎉 HOÀN THÀNH!

Chúc mừng bạn đã deploy thành công! 🚀

### Bước Tiếp Theo:

1. **Test kỹ**: Dùng thử tất cả chức năng
2. **Monitor**: Theo dõi logs trong vài ngày đầu
3. **Optimize**: Cải thiện performance nếu cần
4. **Scale**: Nâng cấp lên paid plan khi cần

### Nếu Gặp Lỗi:

- [ ] Đọc logs trong Render Dashboard
- [ ] Kiểm tra lại checklist này
- [ ] Xem file `DEPLOY-GUIDE.md` phần Troubleshooting
- [ ] Google hoặc hỏi AI

---

**Lưu file này lại để tham khảo sau! 📌**
