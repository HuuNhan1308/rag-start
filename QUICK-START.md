# ⚡ Quick Start - Deploy trong 5 Phút

## 🎯 Cách Nhanh Nhất (Dùng Render Blueprint)

### Bước 1: Push code lên GitHub

```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
git push -u origin main
```

### Bước 2: Deploy bằng 1 click

1. Đăng nhập Render.com bằng GitHub
2. Click nút này: **"New +"** → **"Blueprint"**
3. Chọn repository của bạn
4. Render sẽ tự động đọc file `render.yaml` và deploy TẤT CẢ!

### Bước 3: Đợi 5-10 phút

Render sẽ tự động:
- ✅ Tạo PostgreSQL database
- ✅ Deploy Vector Storage (Python)
- ✅ Deploy Backend (Node.js)
- ✅ Deploy Frontend (React)
- ✅ Kết nối tất cả với nhau

### Bước 4: Xong!

Vào Dashboard, click vào `rag-frontend` service để lấy URL!

---

## 🔧 Nếu Cần Thêm Environment Variables

Sau khi deploy xong, vào từng service và thêm:

### Backend:
- `GOOGLE_API_KEY`: API key của Google AI
- `PINECONE_API_KEY`: Nếu dùng Pinecone

### Frontend:
- Không cần thêm gì, đã tự động!

---

## 🎉 Đơn Giản Vậy Thôi!

Nếu gặp lỗi, xem file `DEPLOY-GUIDE.md` để troubleshoot.

---

## 📝 Lưu Ý

File `render.yaml` đã cấu hình sẵn:
- ✅ Tự động kết nối database
- ✅ Tự động kết nối giữa các services
- ✅ Tự động generate JWT secret
- ✅ Tự động config CORS

Bạn chỉ cần push code và click deploy! 🚀
