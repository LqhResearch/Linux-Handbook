# Hướng dẫn triển khai website trên Ubuntu sử dụng Docker, Nginx, và MySQL

## 1. Cài Đặt Docker

Trước khi cài đặt Docker, cần cập nhật hệ thống để đảm bảo tất cả các gói phần mềm đang ở phiên bản mới nhất:

```bash
sudo apt update && sudo apt upgrade -y
```

Tiếp theo, tiến hành cài đặt Docker từ kho lưu trữ mặc định của Ubuntu:

```bash
sudo apt install -y docker.io
```

Sau khi cài đặt, kích hoạt Docker để chạy cùng hệ thống và khởi động ngay lập tức:

```bash
sudo systemctl enable --now docker
```

Xác minh Docker đã được cài đặt thành công bằng cách kiểm tra phiên bản:

```bash
docker --version
```

Kiểm tra trạng thái dịch vụ Docker:

```bash
systemctl status docker
```

## 2. Cài Đặt Docker Compose  

Docker Compose là công cụ giúp quản lý và triển khai nhiều container cùng lúc bằng cách sử dụng tệp cấu hình `docker-compose.yml` hoặc `compose.yaml`. Để cài đặt, có hai cách phổ biến: cài đặt qua trình quản lý gói (`apt`) hoặc tải trực tiếp từ GitHub.  

### Cách 1: Cài đặt qua `apt`

Lệnh sau sẽ cài đặt Docker Compose từ kho phần mềm của hệ điều hành.

```bash
sudo apt update
sudo apt install -y docker-compose
```  

Sau khi cài đặt, kiểm tra phiên bản.

```bash
docker-compose --version
```  

> Nhược điểm: Phiên bản Docker Compose có thể cũ hơn so với bản mới nhất trên GitHub.  

### Cách 2: Cài đặt bản mới nhất từ GitHub  

Cách này đảm bảo bạn có phiên bản Docker Compose mới nhất.

```bash
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```  

Cấp quyền thực thi.

```bash
sudo chmod +x /usr/local/bin/docker-compose
```  

Kiểm tra cài đặt thành công.

```bash
docker-compose --version
```  

**Lưu ý:** Nếu sau khi cài đặt, lệnh `docker-compose` không hoạt động, có thể cần di chuyển file vào `/usr/bin/`:  

```bash
sudo mv /usr/local/bin/docker-compose /usr/bin/docker-compose
```  
