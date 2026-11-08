# aoba-site-demo — repo website giả lập để thử HIRAKU check

Repo này là website giả lập 青葉市, có lỗi accessibility cài sẵn. Nó dùng để thử plugin HIRAKU bằng Pull Request thật.

- `public/`: trang web (bản sao `portal/demo_site/` của HIRAKU).
- `.github/workflows/a11y.yml`:
  - **Mỗi PR:** gọi HIRAKU, tóm tắt kết quả trong job và tải SARIF lên tab **Security → Code scanning**.
  - **Mỗi lần push vào `main`:** đặt kết quả làm mốc.

Bản xem trước tạm thời là `https://hiraku.synthgora.com/demo-site`, tên miền này đã xác minh trên HIRAKU. Vì vậy HIRAKU quét đúng các **đường dẫn** của tệp đổi trong PR, nhưng trên bản đã deploy sẵn chứ không phải bản của PR. Repo thật của khách sẽ deploy bản xem trước cho từng PR, rồi đưa URL đó vào `preview-url`.

## Thử

1. Sửa `public/news.html` (ví dụ đổi một dòng chữ), tạo nhánh và mở PR.
2. Kết quả mong đợi:
   - Job **HIRAKU accessibility** đỏ, vì 1.4.3 ở `/news.html` là lỗi máy ghi, nên bị chặn.
   - Bảng tóm tắt có "AI nghi không đạt".
   - Tab Code scanning hiện lỗi `JIS-1.4.3`.
3. Merge PR, workflow chạy trên `main` và đặt kết quả làm mốc. PR sau sẽ chỉ báo lỗi **mới**.
