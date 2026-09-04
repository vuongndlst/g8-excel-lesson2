# Thám tử số liệu – Làm sạch dữ liệu và thống kê cơ bản

Website tĩnh dành cho GitHub Pages. Bài 2 của chuỗi Excel & Phân tích dữ liệu, khối 8.

## Đưa lên GitHub Pages
1. Tạo một repository mới trên GitHub.
2. Upload `index.html` vào thư mục gốc của repository.
3. Vào **Settings → Pages**.
4. Chọn **Deploy from a branch**.
5. Chọn nhánh **main** và thư mục **/(root)**.
6. Lưu và chờ GitHub tạo đường dẫn website.

## Điều kiện sử dụng
Học sinh cần mở song song file **LSTS_KhaoSat_K8_2026_AnDanh_Cleaned.xlsx** (chia sẻ trên Canvas).
File có 3 sheet: `Data` (dữ liệu gốc còn lỗi), `Clean_Data` (đã làm sạch), `Cleaning_Log` (nhật ký xử lý).
Từ chặng 3 trở đi, học sinh **tính trên Excel rồi gõ kết quả vào web**; sai thì chặng sau không mở.

## Nội dung
- Chặng 1: Bốn thủ phạm làm bẩn dữ liệu (ô trống, số lưu dạng văn bản, giá trị vô lý, bản ghi nghi trùng)
- Chặng 2: Ba mảnh ghép của một công thức (dấu `=`, vùng `B3:B300`, tên hàm)
- Chặng 3: COUNT và COUNTA – tính trên Excel
- Chặng 4: SUM, AVERAGE, MAX, MIN – tính trên cả hai sheet `Data` và `Clean_Data`
- Chặng 5: MEDIAN và AVERAGE – phát hiện ngoại lệ kéo lệch trung bình
- Kiểm tra cuối: 10 câu ngẫu nhiên rút từ ngân hàng 20 câu, đạt 8/10 để tải minh chứng PNG/PDF

## Đáp án các chặng (dành cho giáo viên)

Vùng dữ liệu: hàng 3 → hàng 300 (298 phản hồi).

| Chặng | Công thức | Sheet | Kết quả |
|---|---|---|---|
| 3 | `=COUNTA(A3:A300)` | Clean_Data | 298 |
| 3 | `=COUNT(A3:A300)` | Clean_Data | 0 |
| 3 | `=COUNT(F3:F300)` | Clean_Data | 291 |
| 3 | `=COUNT(B3:B300)` | Clean_Data | 293 |
| 4 | `=SUM(G3:G300)` | Clean_Data | 1 952 348 |
| 4 | `=AVERAGE(B3:B300)` | Clean_Data | 7,21 |
| 4 | `=MAX(H3:H300)` | Data | 87 |
| 4 | `=MAX(B3:B300)` | Data | 25 |
| 5 | `=AVERAGE(G3:G300)` | Data | 7 061,57 |
| 5 | `=MEDIAN(G3:G300)` | Data | 6 606 |
| 5 | `=AVERAGE(G3:G300)` | Clean_Data | 6 573,56 |
| 5 | `=MEDIAN(G3:G300)` | Clean_Data | 6 602 |

Phát hiện trọng tâm của bài: một ô nhập nhầm 152 000 bước làm **AVERAGE lệch 488 bước**, trong khi **MEDIAN chỉ lệch 4 bước**.

## Lưu ý kỹ thuật
- Phần nhiệm vụ **không in sẵn công thức**. Học sinh làm sai ô nào thì ô đó tô đỏ và chỉ ô đó hiện gợi ý công thức; câu chọn sai cũng tô đỏ riêng.
- Website không cần backend. Họ tên và lớp lưu trong `localStorage` (khóa `excelClean2Student`).
- PDF tạo từ ảnh minh chứng bằng jsPDF tải từ CDN; nếu mạng chặn CDN, học sinh vẫn tải được bản PNG.
- Ô nhập kết quả chấp nhận cả dấu phẩy và dấu chấm thập phân, có hoặc không có dấu phân cách hàng nghìn (`6573,56`, `6573.56`, `1.952.348`, `1952348` đều được chấp nhận).
- Các phương án trong ô chọn được xáo trộn ngẫu nhiên mỗi lần tải trang.
