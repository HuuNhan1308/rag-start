# 🚀 RAG Application - Ready to Deploy

Ứng dụng RAG (Retrieval-Augmented Generation) với 3 services độc lập:

## 📦 Cấu Trúc

```
rag-start/
├── 🐍 faiss-vector-storage/    # Python FastAPI - Vector Database
├── 🟢 server-nodejs/            # Node.js Express - Backend API  
├── ⚛️  rag-starter/              # React + Vite - Frontend
└── 📚 [Tài liệu deploy]
```

---

## ⚡ DEPLOY NHANH - 3 BƯỚC

### 🎯 BẮT ĐẦU TỪ ĐÂY

**📄 Đọc ngay:** [BAT-DAU-O-DAY.md](./BAT-DAU-O-DAY.md) hoặc [TOM-TAT.md](./TOM-TAT.md)

### 1️⃣ Push lên GitHub (2 phút)

```bash
git init
git add .
git commit -m "Ready to deploy"
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
git push -u origin main
```

### 2️⃣ Đăng ký Render.com (1 phút)

- Vào: https://render.com
- Đăng nhập bằng GitHub

### 3️⃣ Deploy bằng Blueprint (7 phút)

- Click "New +" → "Blueprint"
- Chọn repository
- Render tự động deploy tất cả!

✅ **Xong trong 10 phút!**

📚 **Hướng dẫn chi tiết:** Xem [INDEX.md](./INDEX.md) để chọn guide phù hợp

---

## 📚 TÀI LIỆU HƯỚNG DẪN (17 FILES)

### 🎯 BẮT ĐẦU

| File | Mô Tả | Thời Gian |
|------|-------|-----------|
| 📄 **[BAT-DAU-O-DAY.md](./BAT-DAU-O-DAY.md)** | **ĐỌC FILE NÀY TRƯỚC!** | 5 phút |
| 📄 **[TOM-TAT.md](./TOM-TAT.md)** | Tóm tắt siêu nhanh | 2 phút |
| 📄 **[INDEX.md](./INDEX.md)** | Mục lục đầy đủ 17 files | Tham khảo |

### 🟢 Cho Người Mới (KHUYẾN NGHỊ)

| File | Mô Tả | Thời Gian |
|------|-------|-----------|
| 📄 **[DEPLOY-GUIDE-SIMPLE.md](./DEPLOY-GUIDE-SIMPLE.md)** | Hướng dẫn đơn giản nhất | 15 phút |
| 📄 **[DEPLOY-GUIDE.md](./DEPLOY-GUIDE.md)** | Hướng dẫn đầy đủ nhất | 30 phút |
| 📄 **[CHECKLIST.md](./CHECKLIST.md)** | Checklist đánh dấu | In ra dùng |
| 📄 **[FINAL-CHECKLIST.md](./FINAL-CHECKLIST.md)** | Kiểm tra trước deploy | 10 phút |

### ⚡ Cho Người Đã Biết Git

| File | Mô Tả | Thời Gian |
|------|-------|-----------|
| 📄 **[QUICK-START.md](./QUICK-START.md)** | Deploy nhanh nhất | 5 phút |
| 📄 **[render.yaml](./render.yaml)** | Config Blueprint | Auto |

### 🐳 Cho Người Biết Docker

| File | Mô Tả | Thời Gian |
|------|-------|-----------|
| 📄 **[DOCKER-GUIDE.md](./DOCKER-GUIDE.md)** | Hướng dẫn Docker | 10 phút |
| 📄 **[docker-compose.yml](./docker-compose.yml)** | Config Docker | Auto |

### 📖 Tài Liệu Tham Khảo

| File | Mô Tả |
|------|-------|
| 📄 **[README-DEPLOY.md](./README-DEPLOY.md)** | Tổng quan deploy |
| 📄 **[DEPLOY-SUMMARY.md](./DEPLOY-SUMMARY.md)** | Tóm tắt với ASCII art |
| 📄 **[ALTERNATIVE-DEPLOY.md](./ALTERNATIVE-DEPLOY.md)** | Các platform khác |
| 📄 **[VIDEO-SCRIPT.md](./VIDEO-SCRIPT.md)** | Script quay video |

---

## 🎯 CHỌN PHƯƠNG ÁN PHÙ HỢP

### Bạn là người mới, chưa biết gì về deploy?
👉 Đọc **[DEPLOY-GUIDE-SIMPLE.md](./DEPLOY-GUIDE-SIMPLE.md)**

### Bạn đã biết Git, muốn nhanh?
👉 Đọc **[QUICK-START.md](./QUICK-START.md)**

### Bạn muốn test local trước?
👉 Đọc **[DOCKER-GUIDE.md](./DOCKER-GUIDE.md)**

### Bạn muốn so sánh các platform?
👉 Đọc **[ALTERNATIVE-DEPLOY.md](./ALTERNATIVE-DEPLOY.md)**

---

## 🛠️ CHẠY LOCAL

### Không dùng Docker:

```bash
# Terminal 1: Database (cần cài PostgreSQL)
# Tạo database: rag_db

# Terminal 2: Vector Storage
cd faiss-vector-storage
pip install -r requirements.txt
uvicorn main:app --reload

# Terminal 3: Backend
cd server-nodejs
npm install
# Tạo file .env (xem ENV-EXAMPLE.md)
npm run dev

# Terminal 4: Frontend
cd rag-starter
yarn install
# Tạo file .env (xem ENV-EXAMPLE.md)
yarn dev
```

### Dùng Docker (Đơn giản hơn):

```bash
docker-compose up -d
```

Truy cập:
- Frontend: http://localhost:5173
- Backend: http://localhost:3000
- Vector Storage: http://localhost:8000/docs

---

## 📋 REQUIREMENTS

### Để Deploy:
- ✅ Tài khoản GitHub
- ✅ Tài khoản Render.com (hoặc platform khác)
- ✅ Google API Key (nếu dùng Gemini)

### Để Chạy Local:
- ✅ Node.js 20+
- ✅ Python 3.11+
- ✅ PostgreSQL 15+
- ✅ Yarn hoặc npm

---

## 🌐 TECH STACK

### Frontend
- ⚛️ React 19
- 🎨 Vite
- 📡 Axios
- 🧭 React Router

### Backend
- 🟢 Node.js + Express
- 📘 TypeScript
- 🗄️ PostgreSQL + Sequelize
- 🔐 JWT Authentication
- 🤖 Google Generative AI

### Vector Storage
- 🐍 Python + FastAPI
- 🔍 FAISS (Facebook AI Similarity Search)
- 📊 NumPy

---

## 💰 CHI PHÍ DEPLOY

### Miễn Phí (Free Tier)
- ✅ Render.com: 750 giờ/tháng/service
- ✅ PostgreSQL: 90 ngày, 256MB
- ⚠️ Services "ngủ" sau 15 phút không dùng
- ⚠️ Khởi động lại mất 30-60 giây

### Trả Phí (Production)
- 💵 Render: $7/tháng/service
- 💵 Database: $7/tháng
- 💵 **Tổng**: ~$28/tháng

---

## 🎉 FEATURES

- 📤 Upload PDF/TXT files
- 🔍 Vector search với FAISS
- 💬 Chat với RAG (Retrieval-Augmented Generation)
- 🤖 Tích hợp Google Gemini AI
- 🔐 Authentication với JWT
- 📱 Responsive UI

---

## 🆘 CẦN TRỢ GIÚP?

### Bước 1: Đọc Tài Liệu
- Tất cả hướng dẫn đã có trong các file `.md`
- Đọc phần Troubleshooting trong mỗi guide

### Bước 2: Kiểm Tra Logs
- **Render**: Dashboard → Service → Tab "Logs"
- **Docker**: `docker-compose logs -f [service]`
- **Local**: Xem terminal output

### Bước 3: Tìm Kiếm
- Google: "render.com [tên lỗi]"
- ChatGPT/Claude: Paste logs và hỏi
- Render Docs: https://render.com/docs

---

## 🤝 CONTRIBUTING

Nếu bạn muốn đóng góp:
1. Fork repository
2. Tạo branch mới
3. Commit changes
4. Push và tạo Pull Request

---

## 📝 LICENSE

MIT License - Tự do sử dụng cho mọi mục đích

---

## 🎓 HỌC THÊM

### DevOps Basics
- Git & GitHub
- Environment Variables
- CI/CD
- Docker

### Platform Docs
- [Render](https://render.com/docs)
- [Vercel](https://vercel.com/docs)
- [Railway](https://docs.railway.app)
- [Docker](https://docs.docker.com)

---

## 📞 LIÊN HỆ

Nếu có câu hỏi hoặc cần hỗ trợ, vui lòng:
- 🐛 Tạo Issue trên GitHub
- 💬 Hỏi trong Discussions
- 📧 Email: [your-email]

---

## ⭐ NẾU DỰ ÁN HỮU ÍCH

Đừng quên:
- ⭐ Star repository này
- 🔀 Fork để tự customize
- 📢 Chia sẻ với bạn bè

---

## 🗺️ ROADMAP

- [ ] Thêm support cho nhiều loại file hơn
- [ ] Tích hợp thêm AI models
- [ ] Cải thiện UI/UX
- [ ] Thêm analytics dashboard
- [ ] Multi-language support
- [ ] Mobile app

---

**Chúc bạn deploy thành công! 🚀**

Made with ❤️ for the community
