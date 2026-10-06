# Quads Lắng Nghe – Tra cứu trạng thái góp ý

Trang tĩnh (GitHub Pages) để người gửi góp ý ẩn danh tra cứu trạng thái theo **mã theo dõi** họ tự đặt trong form
[Quads Lắng Nghe](https://forms.gle/uvyjx1a3smVC96w89).

## Luồng dữ liệu

```
Google Form ──► Sheet "Câu trả lời biểu mẫu 1" (riêng tư, chứa nội dung góp ý)
                   │  Ban lãnh đạo chọn "Trạng thái", ghi "Lý do / Phản hồi" (cột L, M)
                   ▼
                Tab "Công khai" (công thức FILTER: chỉ Mã, Trạng thái, Lý do, Ngày gửi)
                   │  Tệp › Chia sẻ › Công bố lên web – CHỈ tab này, định dạng CSV
                   ▼
                index.html đọc CSV và hiển thị
```

Trang **không bao giờ** nhận được nội dung góp ý: chỉ tab "Công khai" được công bố.

## Cập nhật trạng thái (Ban lãnh đạo)

1. Mở Sheet câu trả lời, chọn ô cột **Trạng thái** của dòng cần xử lý:
   `Chưa tiếp nhận` · `Đã tiếp nhận` · `Đã giải quyết` · `Không tiếp nhận`.
   Để trống cũng được hiểu là *Chưa tiếp nhận*.
2. Ghi **Lý do / Phản hồi**. Bắt buộc khi *Không tiếp nhận*. Nội dung này hiển thị **công khai**,
   nên không nhắc chi tiết có thể lộ danh tính người gửi.
3. Trang tự cập nhật sau vài phút (Google làm mới bản công bố khoảng 5 phút/lần).

Góp ý không điền mã theo dõi vẫn hiện trong bảng với nhãn *Không có mã* nhưng không tra cứu riêng được.
Vì vậy, điều kiện của công thức FILTER ở tab "Công khai" phải là cột A (Dấu thời gian) khác rỗng, không dùng cột mã.

## Ảnh đính kèm

Người gửi có thể gửi thêm ảnh cho góp ý của mình ở khung *Gửi ảnh kèm góp ý*, kèm mã theo dõi.
Ảnh được thu nhỏ, nén JPEG và xoá EXIF (vị trí, thiết bị) ngay trên trình duyệt, rồi gửi tới một
Web App Apps Script. Địa chỉ Web App nằm ở hằng `UPLOAD_URL` trong `index.html`; để trống thì khung này ẩn đi.

- Ảnh lưu trong thư mục Drive riêng tư *Quads Lắng Nghe – Ảnh đính kèm* của người triển khai Web App.
- Mỗi ảnh ghi một dòng vào tab *Ảnh đính kèm* của Sheet câu trả lời (thời gian, mã, link ảnh). Tab này không được công bố.
- Chỉ nhận ảnh cho mã đã có trong Sheet: tối đa 5 ảnh mỗi lần, 20 ảnh mỗi mã, 300 ảnh mỗi ngày.
- Mã nguồn Web App không nằm trong repo này vì có chứa ID của Sheet.

## Sửa trang

Toàn bộ trang nằm trong `index.html`. Link CSV ở hằng `CSV_URL`. Đẩy lên nhánh `main` là GitHub Pages tự cập nhật.
