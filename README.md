# Library API – Khoa CNTT

Web API quản lý sách của Thư viện số Khoa CNTT, xây dựng bằng FastAPI. Dữ liệu lưu trong bộ nhớ.

## Cài đặt và chạy

    python3 -m venv .venv
    source .venv/bin/activate
    pip install -r requirements.txt
    uvicorn app.main:app --reload

Mở http://127.0.0.1:8000/docs để xem Swagger UI.

## Danh sách endpoint

| Phương thức | Endpoint | Chức năng | Thành công | Lỗi |
|---|---|---|---|---|
| GET | /books | Danh sách; lọc ?q=, ?author=; phân trang ?skip=, ?limit= | 200 | 422 |
| GET | /books/{id} | Chi tiết một cuốn sách | 200 | 404 |
| POST | /books | Thêm sách mới | 201 | 409, 422 |
| PUT | /books/{id} | Cập nhật toàn bộ | 200 | 404, 409, 422 |
| PATCH | /books/{id} | Cập nhật một phần | 200 | 404, 422 |
| DELETE | /books/{id} | Xóa sách | 204 | 404 |

## Kiểm thử

Import `postman/Library-API.postman_collection.json` và `postman/Library-Local.postman_environment.json` vào Postman, chọn environment Library-Local, khởi động lại server rồi chạy Collection Runner (12 test case TC01–TC12, kết quả 16/16 test passed).

Hoặc chạy bằng Newman:

    npx newman run postman/Library-API.postman_collection.json -e postman/Library-Local.postman_environment.json

## Ảnh minh chứng

![Swagger](docs/swagger.png)

![Postman Runner](docs/postman_runner.png)
