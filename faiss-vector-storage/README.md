# 🐍 Vector Storage Service

FastAPI service để lưu trữ và tìm kiếm vectors bằng FAISS.

## 🚀 Chạy Local

```bash
# Cài dependencies
pip install -r requirements.txt

# Chạy server
uvicorn main:app --reload --port 8000
```

Truy cập: http://localhost:8000/docs

## 📦 Endpoints

- `POST /add_vector` - Thêm vectors
- `POST /search` - Tìm kiếm vectors
- `GET /debug` - Xem thông tin debug
- `POST /clear` - Xóa tất cả vectors

## 🐳 Docker

```bash
# Build
docker build -t vector-storage .

# Run
docker run -p 8000:8000 vector-storage
```

## 🌐 Deploy

Service này sẽ được deploy tự động khi dùng `render.yaml`.

Xem hướng dẫn deploy trong file gốc:
- `../BAT-DAU-O-DAY.md`
- `../QUICK-START.md`
