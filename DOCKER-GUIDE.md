# 🐳 Hướng Dẫn Chạy Bằng Docker

## 📋 Yêu Cầu

- Docker Desktop đã cài đặt
- 4GB RAM trở lên

## 🚀 Cách Chạy

### Bước 1: Cài Docker Desktop

Tải về tại: https://www.docker.com/products/docker-desktop/

### Bước 2: Chạy tất cả services

```bash
# Mở PowerShell trong thư mục dự án
cd C:\Users\nhanh\OneDrive\Desktop\rag-start

# Chạy tất cả
docker-compose up -d
```

### Bước 3: Đợi services khởi động

```bash
# Xem logs
docker-compose logs -f

# Kiểm tra status
docker-compose ps
```

### Bước 4: Truy cập

- **Frontend**: http://localhost:5173
- **Backend**: http://localhost:3000
- **Vector Storage**: http://localhost:8000/docs
- **Database**: localhost:5432

---

## 🛑 Dừng Services

```bash
# Dừng tất cả
docker-compose down

# Dừng và xóa data
docker-compose down -v
```

---

## 🔍 Debug

### Xem logs của một service cụ thể:

```bash
docker-compose logs -f backend
docker-compose logs -f vector-storage
docker-compose logs -f frontend
```

### Restart một service:

```bash
docker-compose restart backend
```

### Vào bên trong container:

```bash
docker-compose exec backend sh
docker-compose exec vector-storage sh
```

---

## 📝 Lưu Ý

- **Lần đầu chạy**: Sẽ mất 5-10 phút để build images
- **Sau đó**: Chỉ mất 30 giây để start
- **Data**: Lưu trong Docker volumes, không mất khi restart

---

## 🎯 Deploy Lên Production

Nếu muốn deploy bằng Docker:

### Railway.app (Khuyến nghị)

1. Tạo tài khoản tại: https://railway.app
2. Connect GitHub repository
3. Railway tự động detect Dockerfile và deploy!

### Google Cloud Run

1. Build images:
```bash
docker build -t gcr.io/YOUR_PROJECT/backend ./server-nodejs
docker build -t gcr.io/YOUR_PROJECT/vector-storage ./faiss-vector-storage
```

2. Push lên Google Container Registry:
```bash
docker push gcr.io/YOUR_PROJECT/backend
docker push gcr.io/YOUR_PROJECT/vector-storage
```

3. Deploy trên Cloud Run console

---

## 🆘 Troubleshooting

### Port đã được sử dụng?

Sửa ports trong `docker-compose.yml`:
```yaml
ports:
  - "3001:3000"  # Thay 3000 thành port khác
```

### Out of memory?

Tăng memory cho Docker Desktop:
- Settings → Resources → Memory → Tăng lên 4GB+

### Build lỗi?

```bash
# Xóa cache và build lại
docker-compose build --no-cache
docker-compose up -d
```

---

Chúc bạn thành công! 🚀
