# Sổ tiêm chủng điện tử — bé Đặng Anh Vũ

Ứng dụng web một trang (mobile-first, tiếng Việt) quản lý sổ tiêm chủng cá nhân, xây từ dữ liệu file Word `So_tiem_chung_Dang_Anh_Vu1.docx` (lập ngày 30/08/2026).

## Tính năng

- **Lịch tiêm**: 17 mốc tiêm tiếp theo (Phương án A) với đếm ngược ngày, cảnh báo quá hẹn và hạn chót cứng (Rotarix 26/11/2026), lọc theo Bắt buộc / Đến hẹn.
- **Tích đã tiêm**: bấm nút tròn trên mỗi mũi → xác nhận ngày tiêm thực tế + ghi chú; bỏ tích được (có hỏi lý do).
- **Lịch sử tương tác**: mọi lần tích / bỏ tích được ghi lại kèm thời điểm, không xóa được — đây là nhật ký của sổ.
- **Đã tiêm**: 5 mũi đã hoàn thành (VGB sơ sinh + HBIG, BCG, Rotarix 1, Infanrix Hexa 1, Prevenar 20 mũi 1).
- **Cẩm nang**: chi tiết 11 loại vắc-xin, lưu ý trước/sau tiêm, dấu hiệu đi viện, mũi miễn phí tại trạm y tế xã, bảng chi phí dự kiến.

## Cách lưu dữ liệu

Trang được phát hành dưới dạng Claude Artifact với capability `artifact`: mỗi lần tích tiêm, trang tái tạo toàn bộ tài liệu (từ nguồn chuẩn trong JS, không serialize DOM) với khối state JSON mới rồi `artifact.publish()` — dữ liệu lưu trên máy chủ, đồng bộ giữa các thiết bị cùng mở link. Khi mở ngoài môi trường artifact, trang tự chuyển sang lưu `localStorage` trên thiết bị và hiện banner báo.

`index.html` là toàn bộ ứng dụng: không build, không dependency ngoài Google Fonts (Baloo 2 + Be Vietnam Pro, có fallback hệ thống). File này là bản HTML đầy đủ (`<!doctype>` + `<meta viewport>`) để chạy độc lập qua GitHub Pages/trình duyệt bất kỳ — khác với bản dùng cho Claude Artifact vốn chỉ là đoạn nội dung được khung Artifact tự bọc thêm phần `<head>`.

Bản chạy trực tiếp qua GitHub Pages: nhánh `gh-pages` (root) → https://dagatha9.github.io/deepseek-harness/
