# Bài 4: Quản lý tệp tin bỏ qua (.gitignore) và Sửa lịch sử (Amend)

## 1. Mục tiêu

* Cấu hình `.gitignore` để Git bỏ qua các file chứa thông tin nhạy cảm.
* Gỡ file `credentials.txt` khỏi Git nhưng không xóa file vật lý trên máy.
* Sử dụng `git commit --amend` để sửa commit gần nhất.

## 2. Tạo file credentials.txt

Tạo file `credentials.txt` để mô phỏng file chứa thông tin bảo mật.

Ví dụ:

```text
username=admin
password=123456
api_key=example-secret-key
```

Sau đó commit nhầm file:

```bash
git add credentials.txt
git commit -m "add credentials file"
```

## 3. Tạo file .gitignore

Tạo file `.gitignore` với nội dung:

```gitignore
credentials.txt
```

File `credentials.txt` sẽ được Git bỏ qua trong những lần commit tiếp theo.

## 4. Gỡ credentials.txt khỏi Git

Sử dụng lệnh:

```bash
git rm --cached credentials.txt
```

Tham số `--cached` chỉ xóa file khỏi Git Index, không xóa file vật lý trên máy tính.

Sau khi thực hiện lệnh, file `credentials.txt` vẫn tồn tại trong thư mục làm việc nhưng Git không còn theo dõi file này.

## 5. Commit thay đổi

Thêm file `.gitignore`:

```bash
git add .gitignore
```

Sau đó sử dụng `--amend` để sửa commit gần nhất:

```bash
git commit --amend -m "add gitignore and remove sensitive credentials"
```

Lệnh `--amend` thay thế commit gần nhất bằng một commit mới có nội dung và thông điệp đã được cập nhật.

## 6. Kiểm tra trạng thái

Sử dụng:

```bash
git status
```

Kết quả mong đợi:

```text
nothing to commit, working tree clean
```

Kiểm tra `.gitignore`:

```bash
git check-ignore -v credentials.txt
```

Kết quả cho thấy `credentials.txt` đang được `.gitignore` bỏ qua.

## 7. Kiểm tra lịch sử commit

Sử dụng:

```bash
git log -n 1
```

Kết quả mong đợi:

```text
commit <commit-id>
Author: ...
Date: ...

    add gitignore and remove sensitive credentials
```

Commit message đã được sửa thành công bằng `git commit --amend`.

## 8. Kết luận

Sau khi hoàn thành:

* `credentials.txt` vẫn tồn tại trên máy tính.
* `credentials.txt` không còn được Git theo dõi.
* `.gitignore` được cấu hình để bỏ qua `credentials.txt` trong tương lai.
* Commit gần nhất đã được sửa thông điệp bằng `git commit --amend`.
