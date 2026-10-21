# BÁO CÁO THỰC HÀNH KIỂM THỬ TỰ ĐỘNG BẰNG SELENIUM

## 1. Giới thiệu

### 1.1. Mục tiêu

Bài thực hành nhằm tìm hiểu và áp dụng Selenium WebDriver để xây dựng các kịch bản kiểm thử tự động cho một website thương mại điện tử. Thông qua bài thực hành, người thực hiện làm quen với việc xác định test case, viết mã kiểm thử bằng Python, thực thi kiểm thử trên trình duyệt Google Chrome và đánh giá kết quả.

### 1.2. Website được kiểm thử

- Tên website: SauceDemo
- Địa chỉ: https://www.saucedemo.com/
- Loại website: Website mô phỏng hoạt động bán hàng trực tuyến.
- Phạm vi kiểm thử: Đăng nhập, kiểm tra danh sách sản phẩm, thêm sản phẩm vào giỏ hàng và đăng xuất.

### 1.3. Công cụ sử dụng

| Công cụ | Mục đích |
|---|---|
| Python | Ngôn ngữ lập trình viết test script |
| Selenium WebDriver | Tự động hóa thao tác trên trình duyệt |
| unittest | Tổ chức và thực thi các test case |
| Google Chrome | Trình duyệt thực hiện kiểm thử |
| Visual Studio Code | Soạn thảo và quản lý mã nguồn |
| Git và GitHub | Quản lý phiên bản và lưu trữ sản phẩm |

## 2. Môi trường kiểm thử

- Hệ điều hành: Windows.
- Ngôn ngữ lập trình: Python.
- Thư viện kiểm thử: Selenium.
- Framework kiểm thử: unittest.
- Trình duyệt: Google Chrome.
- Website mục tiêu: SauceDemo.

Cài đặt Selenium bằng lệnh:

```bash
python -m pip install selenium
```

Kiểm tra phiên bản Selenium:

```bash
python -m pip show selenium
```

## 3. Phương pháp kiểm thử

Bài thực hành sử dụng kiểm thử chức năng tự động (Automated Functional Testing). Các test script mô phỏng thao tác của người dùng trên website, sau đó sử dụng các điều kiện kiểm tra (assertions) để so sánh kết quả thực tế với kết quả mong đợi.

Các thao tác được thực hiện thông qua Selenium WebDriver. Framework unittest quản lý việc khởi tạo trình duyệt, thực thi từng test case và tổng hợp kết quả.

## 4. Danh sách test case

### TC01 – Đăng nhập thành công

- **Mục tiêu:** Kiểm tra chức năng đăng nhập với tài khoản hợp lệ.
- **Tiền điều kiện:** Website truy cập được và người dùng đang ở trang đăng nhập.
- **Dữ liệu kiểm thử:** `standard_user` / `secret_sauce`.
- **Các bước thực hiện:**
  1. Mở trang SauceDemo.
  2. Nhập tên người dùng hợp lệ.
  3. Nhập mật khẩu hợp lệ.
  4. Nhấn nút Login.
- **Kết quả mong đợi:** Website chuyển đến trang danh sách sản phẩm, URL chứa `inventory.html`.
- **Kết quả thực tế:** Cập nhật sau khi chạy kiểm thử.
- **Trạng thái:** Cập nhật PASS hoặc FAIL theo kết quả thực tế.

### TC02 – Đăng nhập thất bại

- **Mục tiêu:** Kiểm tra khả năng xử lý thông tin đăng nhập không hợp lệ.
- **Tiền điều kiện:** Đang ở trang đăng nhập.
- **Dữ liệu kiểm thử:** `wrong_user` / `wrong_pass`.
- **Các bước thực hiện:**
  1. Nhập tên người dùng không hợp lệ.
  2. Nhập mật khẩu không hợp lệ.
  3. Nhấn Login.
- **Kết quả mong đợi:** Website hiển thị thông báo lỗi đăng nhập và không chuyển đến trang danh sách sản phẩm.
- **Kết quả thực tế:** Cập nhật sau khi chạy kiểm thử.
- **Trạng thái:** Cập nhật PASS hoặc FAIL theo kết quả thực tế.

### TC03 – Kiểm tra danh sách sản phẩm

- **Mục tiêu:** Kiểm tra khả năng hiển thị danh sách sản phẩm sau khi đăng nhập.
- **Tiền điều kiện:** Người dùng có thể đăng nhập bằng tài khoản hợp lệ.
- **Các bước thực hiện:**
  1. Đăng nhập.
  2. Chờ danh sách sản phẩm xuất hiện.
  3. Đếm số phần tử sản phẩm trên trang.
- **Kết quả mong đợi:** Danh sách sản phẩm được hiển thị và có ít nhất một sản phẩm.
- **Kết quả thực tế:** Cập nhật sau khi chạy kiểm thử.
- **Trạng thái:** Cập nhật PASS hoặc FAIL theo kết quả thực tế.

### TC04 – Thêm sản phẩm vào giỏ hàng

- **Mục tiêu:** Kiểm tra chức năng thêm sản phẩm vào giỏ hàng.
- **Tiền điều kiện:** Người dùng đã đăng nhập và đang ở trang sản phẩm.
- **Các bước thực hiện:**
  1. Đăng nhập bằng tài khoản hợp lệ.
  2. Tìm sản phẩm Sauce Labs Backpack.
  3. Nhấn nút Add to cart.
  4. Kiểm tra số lượng hiển thị trên biểu tượng giỏ hàng.
- **Kết quả mong đợi:** Số lượng trên biểu tượng giỏ hàng hiển thị là 1.
- **Kết quả thực tế:** Cập nhật sau khi chạy kiểm thử.
- **Trạng thái:** Cập nhật PASS hoặc FAIL theo kết quả thực tế.

### TC05 – Đăng xuất

- **Mục tiêu:** Kiểm tra chức năng đăng xuất khỏi hệ thống.
- **Tiền điều kiện:** Người dùng đã đăng nhập thành công.
- **Các bước thực hiện:**
  1. Đăng nhập vào SauceDemo.
  2. Nhấn nút mở menu điều hướng.
  3. Chọn Logout.
  4. Kiểm tra trang sau khi đăng xuất.
- **Kết quả mong đợi:** Website quay về trang đăng nhập, nút Login hiển thị và danh sách sản phẩm không còn xuất hiện.
- **Kết quả thực tế:** Cập nhật sau khi chạy kiểm thử.
- **Trạng thái:** Cập nhật PASS hoặc FAIL theo kết quả thực tế.

## 5. Cấu trúc chương trình kiểm thử

Chương trình được xây dựng trong file `test_saucedemo.py` và sử dụng lớp `SauceDemoTests`, kế thừa từ `unittest.TestCase`.

Các thành phần chính:

- `setUp()`: Khởi tạo trình duyệt Chrome, thiết lập thời gian chờ và mở website.
- `tearDown()`: Đóng trình duyệt sau khi mỗi test case hoàn thành.
- `login()`: Hàm hỗ trợ đăng nhập, được tái sử dụng trong nhiều test case.
- `WebDriverWait`: Chờ phần tử hoặc điều kiện cần thiết trước khi thao tác.
- `assertIn()`, `assertTrue()`, `assertFalse()`, `assertEqual()` và `assertGreater()`: Kiểm tra kết quả thực tế so với điều kiện mong đợi.

Việc tái sử dụng hàm đăng nhập giúp giảm mã lặp và làm cho chương trình dễ đọc, dễ bảo trì hơn.

## 6. Thực thi kiểm thử

Mở Terminal tại thư mục dự án và chạy:

```bash
python -m unittest -v test_saucedemo
```

Lệnh trên thực thi các test case có tên bắt đầu bằng `test_` trong module `test_saucedemo`.

### Kết quả kiểm thử

Cập nhật bảng dưới đây theo kết quả chạy thực tế:

| Test case | Chức năng | Kết quả |
|---|---|---|
| TC01 | Đăng nhập thành công | Chưa cập nhật |
| TC02 | Đăng nhập thất bại | Chưa cập nhật |
| TC03 | Danh sách sản phẩm | Chưa cập nhật |
| TC04 | Thêm vào giỏ hàng | Chưa cập nhật |
| TC05 | Đăng xuất | Chưa cập nhật |

Tổng số test case: 5.

Tổng số PASS: Cập nhật sau khi chạy.

Tổng số FAIL/ERROR: Cập nhật sau khi chạy.

## 7. Hình ảnh minh chứng

Bổ sung ảnh chụp thực tế vào thư mục `screenshots/` và hiển thị ảnh bằng Markdown.

### Hình 1. Mã nguồn kiểm thử

<img width="1366" height="678" alt="image" src="https://github.com/user-attachments/assets/a6609aa7-f8c3-4bc3-b64c-fd51f8716375" />


### Hình 2. Kết quả chạy các test case

<img width="719" height="390" alt="image" src="https://github.com/user-attachments/assets/97366265-62cc-488f-9dce-80780df02da7" />


### Hình 3. Kiểm thử đăng nhập

<img width="1354" height="351" alt="image" src="https://github.com/user-attachments/assets/48174ffa-9f8a-407b-a4cd-a3185b8a3716" />


### Hình 4. Danh sách sản phẩm

<img width="1345" height="511" alt="image" src="https://github.com/user-attachments/assets/94aed0cf-4f94-40fe-ab51-8b3c49525dc1" />


### Hình 5. Thêm sản phẩm vào giỏ hàng

<img width="1366" height="625" alt="image" src="https://github.com/user-attachments/assets/a1e915ef-8837-4fc3-87e0-9fc6ed0b6a6e" />

### Hình 6. Kiểm thử đăng xuất

<img width="1354" height="351" alt="image" src="https://github.com/user-attachments/assets/9dfa9c72-7d18-4fe2-a625-cc4d7a083fe4" />



## 8. Đánh giá và kết luận

Qua bài thực hành, người thực hiện đã áp dụng Selenium WebDriver kết hợp với Python unittest để xây dựng năm kịch bản kiểm thử chức năng cho website SauceDemo.

Các kịch bản bao gồm đăng nhập thành công, đăng nhập thất bại, kiểm tra danh sách sản phẩm, thêm sản phẩm vào giỏ hàng và đăng xuất. Việc sử dụng WebDriverWait giúp chương trình chờ các điều kiện giao diện cần thiết trước khi thực hiện thao tác, hạn chế lỗi do thời gian tải trang.

Kết quả cuối cùng cần được đánh giá dựa trên log thực tế của chương trình. Những test case chưa đạt cần được phân tích nguyên nhân, sửa lỗi và chạy lại trước khi đưa ra kết luận về mức độ thành công của bài kiểm thử.

Bài thực hành giúp củng cố kiến thức về kiểm thử chức năng tự động, tổ chức test case, sử dụng assertion và quản lý mã nguồn bằng GitHub.

## 9. Thông tin nộp bài

- Họ và tên: Vũ Mai Quỳnh
- Mã sinh viên: 23010223
- Lớp: [Điền lớp]
- GitHub Repository: [Dán link repository sau khi tạo]
