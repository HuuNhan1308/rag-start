# 🎥 Script Video Hướng Dẫn Deploy

## 📹 Video 1: Giới Thiệu (2 phút)

### Scene 1: Mở đầu (15 giây)
```
[Màn hình]: Logo/Title "Deploy RAG App trong 10 phút"

Lời thoại:
"Chào các bạn! Hôm nay mình sẽ hướng dẫn các bạn deploy một 
ứng dụng RAG với 3 services lên internet hoàn toàn MIỄN PHÍ!"
```

### Scene 2: Demo ứng dụng (30 giây)
```
[Màn hình]: Mở ứng dụng đã deploy, demo các tính năng

Lời thoại:
"Đây là ứng dụng chúng ta sẽ deploy. Nó có thể upload file PDF,
chat với AI dựa trên nội dung file, và hoàn toàn miễn phí!"
```

### Scene 3: Giới thiệu tech stack (30 giây)
```
[Màn hình]: Diagram 3 services

Lời thoại:
"Ứng dụng gồm 3 phần:
- Frontend React để người dùng tương tác
- Backend Node.js xử lý logic
- Vector Storage Python để tìm kiếm thông tin
Nghe có vẻ phức tạp nhưng deploy rất đơn giản!"
```

### Scene 4: Requirements (45 giây)
```
[Màn hình]: Checklist

Lời thoại:
"Bạn chỉ cần:
1. Tài khoản GitHub - miễn phí
2. Tài khoản Render.com - miễn phí
3. 10 phút thời gian
Không cần biết Docker, không cần VPS, không cần credit card!"
```

---

## 📹 Video 2: Hướng Dẫn Chi Tiết (10 phút)

### Scene 1: Push code lên GitHub (2 phút)
```
[Màn hình]: Terminal + GitHub

Lời thoại:
"Bước 1: Đẩy code lên GitHub.
Mở terminal, chạy các lệnh này..."

[Gõ từng lệnh]:
git init
git add .
git commit -m "Ready to deploy"
git remote add origin [URL]
git push -u origin main

"Xong! Code đã lên GitHub."
```

### Scene 2: Đăng ký Render (1 phút)
```
[Màn hình]: Render.com

Lời thoại:
"Bước 2: Vào Render.com, click Get Started,
đăng nhập bằng GitHub. Rất đơn giản!"
```

### Scene 3: Tạo Database (1 phút)
```
[Màn hình]: Render Dashboard

Lời thoại:
"Bước 3: Tạo database. Click New, chọn PostgreSQL,
đặt tên rag-database, chọn Free plan, Create.
Copy URL này, chúng ta sẽ dùng sau."
```

### Scene 4: Deploy Vector Storage (1.5 phút)
```
[Màn hình]: Render Dashboard

Lời thoại:
"Bước 4: Deploy Vector Storage. Click New, Web Service,
chọn repo, điền thông tin như màn hình...
Root directory: faiss-vector-storage
Runtime: Python 3
Build command: pip install -r requirements.txt
Start command: uvicorn main:app --host 0.0.0.0 --port $PORT
Click Create, đợi 5 phút. Copy URL khi xong."
```

### Scene 5: Deploy Backend (2 phút)
```
[Màn hình]: Render Dashboard

Lời thoại:
"Bước 5: Deploy Backend. Tương tự, New, Web Service...
Root directory: server-nodejs
Runtime: Node
Build: npm install && npm run build
Start: npm start

Phần quan trọng: Environment Variables!
Thêm các biến này..."

[Hiển thị từng biến]:
NODE_ENV=production
DATABASE_URL=[paste]
VECTOR_STORAGE_URL=[paste]
JWT_SECRET=[random string]
...

"Click Create, đợi deploy xong, copy URL."
```

### Scene 6: Deploy Frontend (1.5 phút)
```
[Màn hình]: Render Dashboard

Lời thoại:
"Bước 6: Deploy Frontend. New, Static Site...
Root directory: rag-starter
Build: yarn install && yarn build
Publish: dist

Environment variable:
VITE_API_URL=[paste backend URL]

Create, đợi xong, đây là URL ứng dụng của bạn!"
```

### Scene 7: Cập nhật CORS (1 phút)
```
[Màn hình]: Render Dashboard

Lời thoại:
"Bước cuối: Quay lại Backend, sửa CORS_ORIGIN
thành URL của Frontend. Save, đợi restart."
```

---

## 📹 Video 3: Kiểm Tra & Troubleshooting (3 phút)

### Scene 1: Test ứng dụng (1 phút)
```
[Màn hình]: Mở ứng dụng

Lời thoại:
"Giờ test thử! Mở Frontend URL...
Upload file... Chat với AI... Hoạt động hoàn hảo!"
```

### Scene 2: Các lỗi thường gặp (1.5 phút)
```
[Màn hình]: Split screen - lỗi và cách fix

Lời thoại:
"Nếu gặp lỗi:

1. Frontend không kết nối Backend
   → Kiểm tra VITE_API_URL và CORS_ORIGIN

2. Backend không start
   → Xem logs, thường là thiếu env vars

3. Service 'ngủ'
   → Đây là bình thường với free tier,
      lần đầu truy cập đợi 30 giây"
```

### Scene 3: Next steps (30 giây)
```
[Màn hình]: Checklist

Lời thoại:
"Vậy là xong! Bạn đã có ứng dụng live trên internet!
Chia sẻ link cho bạn bè, khách hàng để demo.
Muốn cập nhật? Chỉ cần git push, Render tự động deploy!"
```

---

## 📹 Video 4: Advanced (5 phút) - Optional

### Scene 1: Docker local (2 phút)
```
[Màn hình]: Terminal + Docker Desktop

Lời thoại:
"Nếu muốn test local trước khi deploy,
dùng Docker Compose rất đơn giản..."

docker-compose up -d

"Tất cả services chạy ngay!"
```

### Scene 2: Alternative platforms (2 phút)
```
[Màn hình]: So sánh bảng

Lời thoại:
"Ngoài Render, bạn có thể dùng:
- Vercel cho frontend - rất nhanh
- Railway - giao diện đẹp
- AWS - cho dự án lớn
Nhưng Render là dễ nhất cho người mới!"
```

### Scene 3: Production tips (1 phút)
```
[Màn hình]: Dashboard

Lời thoại:
"Khi dự án phát triển:
- Upgrade lên paid plan: $28/tháng
- Không còn cold start
- Database không giới hạn
- Phù hợp cho production thật sự!"
```

---

## 🎬 OUTRO (30 giây)

```
[Màn hình]: Kết thúc + CTA

Lời thoại:
"Vậy là xong! Hy vọng video hữu ích.
Đừng quên like, subscribe, và share!
Link tài liệu đầy đủ ở description.
Hẹn gặp lại các bạn video sau!"

[Text trên màn hình]:
📚 Tài liệu: [GitHub link]
💬 Hỏi đáp: [Discord/Telegram]
⭐ Star repo nếu hữu ích!
```

---

## 📝 NOTES CHO NGƯỜI QUAY

### Chuẩn bị:
- [ ] Code đã chạy tốt local
- [ ] Đã deploy thử 1 lần để biết flow
- [ ] Chuẩn bị 2 tài khoản: 1 để demo, 1 backup
- [ ] Screen recording software (OBS, Camtasia)
- [ ] Mic tốt

### Khi quay:
- Nói chậm, rõ ràng
- Zoom in khi cần (Ctrl + Mouse wheel)
- Highlight cursor khi click
- Pause giữa các bước để người xem theo kịp
- Nếu lỗi → giữ lại, giải thích cách fix

### Editing:
- Thêm text annotation cho các bước quan trọng
- Thêm timestamps trong description
- Thêm chapters trong YouTube
- Background music nhẹ nhàng
- Speed up phần đợi deploy (5-10 phút → 30 giây)

### Description:
```
🚀 Deploy RAG Application lên Internet MIỄN PHÍ trong 10 phút!

📚 Tài liệu đầy đủ: [GitHub link]
⏰ Timestamps:
0:00 - Giới thiệu
2:00 - Push code lên GitHub
4:00 - Tạo Database
5:00 - Deploy Vector Storage
7:00 - Deploy Backend
9:00 - Deploy Frontend
10:00 - Kiểm tra

🔗 Links:
- Render.com: https://render.com
- GitHub Repo: [link]
- Tài liệu chi tiết: [link]

💬 Hỏi đáp: [Discord/Telegram link]
```

---

## 🎯 TIPS

### Để video viral:
- Thumbnail bắt mắt: "Deploy trong 10 phút"
- Title SEO: "Hướng dẫn Deploy RAG App | Miễn phí | Không cần Docker"
- Tags: deploy, rag, ai, chatbot, free hosting, render, tutorial
- Post trên: Facebook groups, Reddit, Dev.to, LinkedIn

### Tạo series:
1. Video này: Deploy cơ bản
2. Video 2: Customize UI/UX
3. Video 3: Thêm features
4. Video 4: Scale lên production
5. Video 5: Monitoring & Analytics

---

**Chúc bạn quay video thành công! 🎬**
