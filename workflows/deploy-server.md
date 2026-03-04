---
description: Triển khai code lên Server Production (DevOps / IT)
---

# Deploy Server Tự Động

// turbo-all

Quy trình Zero-Touch Deployment:

1. Terminal khởi động, di chuyển vào thư mục project frontend/backend theo đường dẫn Sếp chỉ định.
2. Đồng bộ Git: `git checkout main && git pull origin main`. Nếu có conflict → báo cáo và DỪNG.
3. Dọn dẹp: `rm -rf node_modules && npm install --silent`.
4. Build production: `npm run build`. Nếu build fail → in lỗi và DỪNG.
5. Chuyển file: `scp -r ./build [user]@[server_ip]:[deploy_path]/` (dùng key SSH nếu có).
6. Khởi động lại web server: `ssh [user]@[server_ip] "systemctl reload nginx"`.
7. Health check: Gửi `curl -s -o /dev/null -w "%{http_code}" https://[domain]`. Nếu 200 OK → Báo cáo thành công ✅. Nếu khác → Báo động đỏ 🔴.
