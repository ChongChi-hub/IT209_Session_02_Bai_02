# Bài 2: Khởi tạo User thường và thiết lập đặc quyền quản trị

### 1. Tạo user `devops` và cấp quyền sudo
Sau khi SSH vào Droplet bằng user `root`, chạy các lệnh sau:
```bash
adduser devops
usermod -aG sudo devops
```

### 2. Sao chép cấu hình SSH Key sang user `devops`
Để tài khoản mới có thể SSH vào bằng khóa đã cấu hình:
```bash
sudo rsync --archive --chown=devops:devops ~/.ssh /home/devops/
```
*(Lệnh `rsync` này sẽ sao chép toàn bộ thư mục `.ssh` từ root sang home của devops, đồng thời cập nhật đúng owner là devops)*

### 3. Kiểm tra đăng nhập và quyền sudo
Đăng xuất và đăng nhập lại bằng user `devops` từ máy cá nhân:
```bash
ssh -i ~/.ssh/id_ed25519_do_ss2 devops@<IP_ADDRESS_DROPLET>
```

Kiểm tra đặc quyền:
```bash
sudo whoami
```

*Lưu ý: Vì thẻ visa của em bị khoá nên không thể tạo droplet để chạy thử nghiệm các lệnh này.*
