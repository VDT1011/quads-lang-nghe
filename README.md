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

Góp ý không điền mã theo dõi sẽ không xuất hiện trên trang.

## Sửa trang

Toàn bộ trang nằm trong `index.html`. Link CSV ở hằng `CSV_URL`. Đẩy lên nhánh `main` là GitHub Pages tự cập nhật.
