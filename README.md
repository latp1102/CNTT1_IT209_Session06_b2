# Bài 2 - Cấu hình phân quyền Nhóm và sudoers bằng visudo

## 1. Tạo group

sudo groupadd devops-admin

## 2. Tạo user

sudo adduser deployer

## 3. Thêm user vào group

sudo usermod -aG devops-admin deployer

## 4. Kiểm tra group

id deployer

## 5. Cấu hình sudoers

sudo visudo

Cấu hình đã thêm:

%devops-admin ALL=(ALL) NOPASSWD: /usr/bin/systemctl start *, /usr/bin/systemctl stop *, /usr/bin/systemctl restart *, /usr/bin/systemctl status *

## 6. Kiểm tra quyền

su - deployer

sudo -l

## 7. Kiểm tra restart service

sudo systemctl restart cron

sudo systemctl status cron --no-pager

## 8. Kết quả

User deployer thuộc nhóm devops-admin và được phép thực hiện
các lệnh systemctl start, stop, restart, status mà không cần
nhập mật khẩu.

Lệnh restart cron đã thực hiện thành công và dịch vụ cron ở trạng thái
active (running).
