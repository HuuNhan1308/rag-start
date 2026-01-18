# 🚀 Hướng Dẫn Deploy Dự Án RAG

## 📁 Cấu Trúc Dự Án

```
rag-start/
├── faiss-vector-storage/    # Python FastAPI - Vector Database
├── server-nodejs/            # Node.js Express - Backend API
├── rag-starter/              # React - Frontend
└── [Các file deploy]
```

---

## 🎯 CHỌN PHƯƠNG ÁN DEPLOY

### 🌟 Dành Cho Người Mới (KHUYẾN NGHỊ)

**📄 Đọc file:** `DEPLOY-GUIDE-SIMPLE.md`

- ✅ Đơn giản nhất
- ✅ Miễn phí
- ✅ 10 phút setup
- ✅ Không cần biết Docker
- 🎯 Platform: **Render.com**

### ⚡ Deploy Siêu Nhanh (1 Click)

**📄 Đọc file:** `QUICK-START.md`

- ✅ Deploy tất cả trong 1 lần
- ✅ Dùng file `render.yaml`
- ✅ Tự động kết nối các services
- 🎯 Platform: **Render.com Blueprint**

### 🐳 Chạy Trên Máy Local Bằng Docker

**📄 Đọc file:** `DOCKER-GUIDE.md`

- ✅ Test trước khi deploy
- ✅ Chạy tất cả services cùng lúc
- ✅ Giống y hệt production
- 🎯 Tool: **Docker Compose**

### 🎓 Các Phương Án Khác

**📄 Đọc file:** `ALTERNATIVE-DEPLOY.md`

- Vercel + Railway + Supabase
- Heroku
- DigitalOcean
- AWS / Google Cloud
- VPS tự quản lý

---

## 📋 CHECKLIST TRƯỚC KHI DEPLOY

### ✅ Code

- [ ] Tất cả services chạy tốt trên local
- [ ] Đã test kết nối giữa frontend ↔ backend ↔ vector storage
- [ ] Không có lỗi linter/build

### ✅ Environment Variables

- [ ] Đã tạo file `.env` cho từng project (xem `ENV-EXAMPLE.md`)
- [ ] Có Google API Key (nếu dùng)
- [ ] Có JWT Secret (tự tạo chuỗi ngẫu nhiên)

### ✅ Git & GitHub

- [ ] Đã cài Git
- [ ] Có tài khoản GitHub
- [ ] Code đã push lên GitHub

### ✅ Platform

- [ ] Đã đăng ký Render.com (hoặc platform khác)
- [ ] Đã connect GitHub với platform

---

## 🎯 HƯỚNG DẪN THEO CẤP ĐỘ

### 🟢 Cấp Độ 1: Người Mới Hoàn Toàn

1. Đọc `DEPLOY-GUIDE-SIMPLE.md`
2. Làm theo từng bước
3. Hỏi khi gặp khó khăn

**Thời gian:** 15-20 phút

### 🟡 Cấp Độ 2: Đã Biết Git & GitHub

1. Đọc `QUICK-START.md`
2. Push code lên GitHub
3. Deploy bằng Render Blueprint

**Thời gian:** 5-10 phút

### 🔴 Cấp Độ 3: Biết Docker

1. Đọc `DOCKER-GUIDE.md`
2. Chạy `docker-compose up`
3. Deploy lên Railway/Cloud Run

**Thời gian:** 10 phút

---

## 📚 TÀI LIỆU CHI TIẾT

| File | Mô Tả | Độ Khó | Thời Gian |
|------|-------|--------|-----------|
| `DEPLOY-GUIDE-SIMPLE.md` | Hướng dẫn chi tiết từng bước | ⭐ Dễ | 15 phút |
| `DEPLOY-GUIDE.md` | Hướng dẫn đầy đủ, giải thích kỹ | ⭐ Dễ | 30 phút |
| `QUICK-START.md` | Deploy nhanh bằng Blueprint | ⭐⭐ TB | 5 phút |
| `DOCKER-GUIDE.md` | Chạy bằng Docker | ⭐⭐⭐ Khó | 10 phút |
| `ALTERNATIVE-DEPLOY.md` | Các phương án khác | ⭐⭐ TB | Đọc thôi |

---

## 🔧 FILES CẤU HÌNH

### Cho Render.com
- `render.yaml` - Blueprint deploy tự động

### Cho Docker
- `docker-compose.yml` - Chạy tất cả services
- `server-nodejs/Dockerfile` - Backend container
- `faiss-vector-storage/Dockerfile` - Vector storage container
- `rag-starter/Dockerfile.dev` - Frontend dev container

### Environment Variables
- `server-nodejs/ENV-EXAMPLE.md` - Backend env vars
- `rag-starter/ENV-EXAMPLE.md` - Frontend env vars

---

## 🎉 SAU KHI DEPLOY XONG

### Kiểm Tra

1. **Vector Storage**: Mở `/docs` để xem Swagger UI
2. **Backend**: Mở root URL, xem JSON response
3. **Frontend**: Mở và test các chức năng

### Chia Sẻ

- URL Frontend: Đây là link ứng dụng của bạn!
- Gửi cho bạn bè, khách hàng để demo

### Cập Nhật Sau Này

```bash
# Chỉnh sửa code
git add .
git commit -m "Update feature X"
git push
```

Platform sẽ tự động deploy lại! ✨

---

## 🆘 GẶP VẤN ĐỀ?

### Bước 1: Kiểm Tra Logs

- Render: Dashboard → Service → Tab "Logs"
- Docker: `docker-compose logs -f [service_name]`

### Bước 2: Các Lỗi Thường Gặp

#### Frontend không kết nối Backend
- ✅ Kiểm tra `VITE_API_URL` có đúng không
- ✅ Kiểm tra `CORS_ORIGIN` trong backend

#### Backend không kết nối Database
- ✅ Kiểm tra `DATABASE_URL`
- ✅ Xem logs của database service

#### Service không start
- ✅ Xem logs để biết lỗi cụ thể
- ✅ Kiểm tra build command có đúng không

### Bước 3: Tìm Trợ Giúp

1. Google: "render.com [tên lỗi]"
2. Render Docs: https://render.com/docs
3. Hỏi ChatGPT/Claude với logs lỗi

---

## 💰 CHI PHÍ DỰ KIẾN

### Miễn Phí (Free Tier)

- ✅ Render.com: 750 giờ/tháng mỗi service
- ✅ Database: 90 ngày, 256MB
- ⚠️ Services sẽ "ngủ" sau 15 phút không dùng

### Trả Phí (Nếu Cần)

- **Render**: $7/tháng/service
- **Database**: $7/tháng
- **Tổng**: ~$28/tháng cho production

---

## 🎓 HỌC THÊM

### DevOps Cơ Bản

- Git & GitHub
- Environment Variables
- CI/CD basics
- Docker basics

### Nâng Cao

- Kubernetes
- AWS/GCP
- Monitoring & Logging
- Security best practices

---

## 📞 LIÊN HỆ & HỖ TRỢ

Nếu cần hỗ trợ:
1. Đọc kỹ tài liệu
2. Kiểm tra logs
3. Google/ChatGPT
4. Hỏi cộng đồng

---

## 🎯 KHUYẾN NGHỊ CUỐI CÙNG

### Cho Demo/Testing:
👉 **Render Free Tier** (`DEPLOY-GUIDE-SIMPLE.md`)

### Cho Production Nhỏ:
👉 **Render Paid** ($28/tháng)

### Cho Production Lớn:
👉 **AWS/GCP** (cần học thêm)

---

**Chúc bạn deploy thành công! 🚀**

Nếu thành công, đừng quên star repo và chia sẻ với bạn bè nhé! ⭐
