# 🚀 Hướng Dẫn Deploy Nhanh - 10 Phút

## Phương án đơn giản nhất cho người mới: RENDER.COM

---

## ✅ CHECKLIST TRƯỚC KHI BẮT ĐẦU

- [ ] Code đang chạy tốt trên máy local
- [ ] Có tài khoản GitHub
- [ ] Có tài khoản Google (để đăng ký Render)

---

## 🎯 CÁC BƯỚC (SIÊU ĐƠN GIẢN)

### BƯỚC 1: Đẩy code lên GitHub (5 phút)

```bash
cd C:\Users\nhanh\OneDrive\Desktop\rag-start

# Khởi tạo Git
git init
git add .
git commit -m "Ready for deployment"

# Tạo repo mới trên GitHub.com, sau đó:
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
git branch -M main
git push -u origin main
```

---

### BƯỚC 2: Đăng ký Render.com (1 phút)

1. Vào: https://render.com
2. Click "Get Started for Free"
3. Đăng nhập bằng GitHub

---

### BƯỚC 3: Tạo Database (2 phút)

1. Click **"New +"** → **"PostgreSQL"**
2. Điền:
   - Name: `rag-database`
   - Region: `Singapore` (gần VN nhất)
   - Plan: **Free**
3. Click "Create Database"
4. ✏️ **Copy URL** (có dạng: `postgresql://...`)

---

### BƯỚC 4: Deploy Vector Storage - Python (2 phút)

1. Click **"New +"** → **"Web Service"**
2. Chọn repo GitHub của bạn
3. Điền:
   - Name: `vector-storage`
   - Root Directory: `faiss-vector-storage`
   - Runtime: `Python 3`
   - Build: `pip install -r requirements.txt`
   - Start: `uvicorn main:app --host 0.0.0.0 --port $PORT`
   - Plan: **Free**
4. Click "Create Web Service"
5. ✏️ **Copy URL** khi deploy xong

---

### BƯỚC 5: Deploy Backend - Node.js (3 phút)

1. Click **"New +"** → **"Web Service"**
2. Chọn repo GitHub
3. Điền:
   - Name: `backend`
   - Root Directory: `server-nodejs`
   - Runtime: `Node`
   - Build: `npm install && npm run build`
   - Start: `npm start`
   - Plan: **Free**

4. **Thêm Environment Variables** (click "Add Environment Variable"):
   ```
   NODE_ENV=production
   PORT=10000
   DATABASE_URL=<paste_url_từ_bước_3>
   VECTOR_STORAGE_URL=<paste_url_từ_bước_4>
   JWT_SECRET=my_super_secret_key_12345
   CORS_ORIGIN=*
   ```

5. Click "Create Web Service"
6. ✏️ **Copy URL** khi deploy xong

---

### BƯỚC 6: Deploy Frontend - React (2 phút)

1. Click **"New +"** → **"Static Site"**
2. Chọn repo GitHub
3. Điền:
   - Name: `frontend`
   - Root Directory: `rag-starter`
   - Build: `yarn install && yarn build`
   - Publish: `dist`

4. **Thêm Environment Variable**:
   ```
   VITE_API_URL=<paste_url_từ_bước_5>
   ```

5. Click "Create Static Site"
6. ✏️ **Copy URL** → Đây là link ứng dụng của bạn! 🎉

---

### BƯỚC 7: Cập nhật CORS (1 phút)

1. Quay lại **Backend service**
2. Vào tab "Environment"
3. Sửa `CORS_ORIGIN`:
   ```
   CORS_ORIGIN=<paste_frontend_url_từ_bước_6>
   ```
4. Click "Save Changes"

---

## 🎉 XONG RỒI!

Mở **Frontend URL** và test thôi!

---

## ⚠️ LƯU Ý

- **Free tier**: Services sẽ "ngủ" sau 15 phút không dùng
- **Lần đầu truy cập**: Đợi 30-60 giây cho service "thức dậy"
- **Database miễn phí**: 90 ngày, 256MB

---

## 🔄 Cập nhật Code Sau Này

```bash
# Chỉnh sửa code, sau đó:
git add .
git commit -m "Update something"
git push
```

Render tự động deploy lại! ✨

---

## 🆘 Gặp Lỗi?

1. Vào Render Dashboard
2. Click vào service bị lỗi
3. Click tab **"Logs"**
4. Đọc lỗi → Google hoặc hỏi ChatGPT

---

## 💰 Chi Phí

- **Miễn phí hoàn toàn** cho testing
- **Nếu muốn upgrade**: ~$21/tháng cho 3 services + database

---

## 🎓 Phương Án Khác (Nâng Cao)

### Vercel (Frontend) + Railway (Backend + Vector) + Supabase (DB)

**Ưu điểm:**
- Vercel: Deploy frontend cực nhanh
- Railway: Giao diện đẹp, dễ dùng
- Supabase: PostgreSQL miễn phí tốt hơn

**Nhược điểm:**
- Phức tạp hơn (3 platforms khác nhau)
- Phải quản lý nhiều tài khoản

---

## 📞 Cần Giúp Đỡ?

Nếu bị kẹt ở bước nào, check file `DEPLOY-GUIDE.md` để xem hướng dẫn chi tiết hơn!

Chúc bạn deploy thành công! 🚀
