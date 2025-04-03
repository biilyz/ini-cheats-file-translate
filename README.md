
# Hướng Dẫn Cài Đặt và Sử Dụng Tool Thay Thế Văn Bản

## 1. Cài Đặt Python

Trước khi sử dụng tool, bạn cần đảm bảo rằng Python đã được cài đặt trên hệ thống của bạn. Nếu chưa cài đặt Python, hãy làm theo các bước dưới đây:

### Trên Ubuntu/Debian:

- Mở terminal và chạy lệnh sau để cài đặt Python:

```bash
sudo apt update
sudo apt install python3 python3-pip
```

### Trên macOS:

- Mở Terminal và chạy lệnh sau:

```bash
brew install python
```

Nếu bạn chưa cài Homebrew, bạn có thể cài đặt nó từ [brew.sh](https://brew.sh/).

### Trên Windows:

- Truy cập trang web [Python Official](https://www.python.org/downloads/) và tải xuống phiên bản mới nhất của Python.
- Cài đặt Python và đảm bảo chọn **Add Python to PATH** trong quá trình cài đặt.

### Kiểm tra cài đặt Python:

Sau khi cài đặt Python, bạn có thể kiểm tra lại phiên bản Python đã cài đặt bằng lệnh:

```bash
python3 --version
```

Hoặc trên một số hệ thống Windows có thể là:

```bash
python --version
```

## 2. Chuẩn Bị Tool

Tool này sử dụng Python để thay thế văn bản trong tất cả các file `.ini` trong thư mục chỉ định. Hãy thực hiện các bước dưới đây:

### Bước 1: Tạo file `replace_text.py`

1. Mở terminal và sử dụng editor để tạo file **`replace_text.py`**:
   
   ```bash
   nano replace_text.py
   ```

2. Sao chép và dán nội dung sau vào file **`replace_text.py`**:

```python
import os

# Đường dẫn chứa file .ini
input_folder = "/media/cuong/DATA/translate/cheats"

# Câu cần thay thế
old_text = "Insert coin to start"
new_text = "Nhét xu để bắt đầu"

# Xử lý tất cả các file .ini
for filename in os.listdir(input_folder):
    if filename.endswith(".ini"):
        file_path = os.path.join(input_folder, filename)

        # Đọc nội dung file
        with open(file_path, "r", encoding="utf-8") as f:
            content = f.read()

        # Thay thế nếu có câu cũ
        if old_text in content:
            content = content.replace(old_text, new_text)

            # Ghi lại file đã chỉnh sửa
            with open(file_path, "w", encoding="utf-8") as f:
                f.write(content)

            print(f"✅ Đã thay thế trong: {filename}")

print("🎉 Hoàn tất thay thế!")
```

Lưu và đóng file bằng cách nhấn **Ctrl + X**, sau đó chọn **Y** và **Enter**.

### Bước 2: Thực Thi Tool

Để chạy tool thay thế văn bản, làm theo các bước dưới đây:

1. **Mở terminal** và điều hướng đến thư mục nơi bạn đã tạo file **`replace_text.py`**.
   
2. **Chạy script** bằng lệnh sau:

```bash
python3 replace_text.py
```

Tool sẽ:

- Duyệt qua tất cả các file `.ini` trong thư mục `/media/cuong/DATA/translate/cheats`.
- Thay thế tất cả các câu **"Insert coin to start"** bằng câu **"Nhét xu để bắt đầu"** trong mỗi file `.ini`.
- In thông báo mỗi khi thay thế thành công trong một file, ví dụ: **`✅ Đã thay thế trong: filename.ini`**.

Sau khi chạy xong, bạn sẽ thấy thông báo **`🎉 Hoàn tất thay thế!`** nếu tất cả quá trình đã hoàn tất.

### Bước 3: Kiểm Tra Kết Quả

Sau khi chạy script, bạn có thể kiểm tra lại các file `.ini` trong thư mục `/media/cuong/DATA/translate/cheats` để đảm bảo rằng câu đã được thay thế thành công.

## 3. Chỉnh Sửa Script (Tuỳ Chỉnh)

- **Thay Đổi Địa Chỉ Thư Mục**: Nếu bạn muốn thay đổi thư mục chứa các file `.ini`, chỉ cần thay đổi giá trị của biến `input_folder` trong script:
  
```python
input_folder = "/path/to/your/folder"
```

- **Thay Đổi Câu Cần Thay Thế**: Nếu bạn muốn thay thế một câu khác, chỉ cần thay đổi giá trị của biến `old_text` và `new_text`:
  
```python
old_text = "Câu cũ"
new_text = "Câu mới"
```

## 4. Lưu Ý

- Đảm bảo rằng đường dẫn thư mục **`input_folder`** chính xác và có quyền truy cập vào thư mục chứa các file `.ini` cần thay thế.
- Nếu gặp lỗi về quyền truy cập, bạn có thể cần sử dụng quyền root (sudo) trên hệ thống của mình.
