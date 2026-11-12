# Báo cáo thực hành Day 3 — Image Segmentation

- **Mã học viên theo lớp:** 03052 *(kiểm tra lại với thông tin trên LMS trước khi nộp)*
- **Ngày thực hành:** 11–12/11/2026
- **Môi trường thực hiện:** CVAT.ai (bản trực tuyến), Google Colab hỗ trợ tạo mask nháp cho Easy Semantic
- **Công cụ đã dùng để vẽ/chỉnh sửa mask trong CVAT:** [HỌC VIÊN XÁC NHẬN: Brush / Polygon / công cụ khác]

## 1. Bài đã nộp

Theo thông tin học viên cung cấp, đã hoàn thành ba phần chính và có ba file ZIP xuất từ CVAT. Việc tải lên GitHub, nội dung ZIP và chất lượng mask cần kiểm tra lại trước khi nộp LMS.

| Task | File ZIP dự kiến đặt trong `submissions/` | Hoàn thành mấy ảnh (học viên xác nhận) | Điểm tối đa (coach chấm sau) |
| --- | --- | ---: | ---: |
| easy_semantic | `easy_semantic.zip` | 3 / 3 | 20 |
| medium_instance | `medium_instance.zip` | 3 / 3 | 32 |
| hard_panoptic | `hard_panoptic.zip` | 2 / 2 | 30 |
| cp1_holes | Chưa có | 0 / 1 | 3 |
| cp2_slice | Chưa có | 0 / 1 | 3 |
| cp5_occlusion | Chưa có | 0 / 1 | 3 |
| cp3_thin | Chưa có | 0 / 1 | 3 |
| cp4_curb | Chưa có | 0 / 1 | 3 |
| cp6_coverage | Chưa có | 0 / 1 | 3 |
| **Tổng tối đa** | | | **100** |

**Tình trạng hiện tại:** Ba ZIP Easy, Medium, Hard đã được học viên xác nhận là có. Sáu checkpoint chưa được xác nhận hoàn thành; không tạo ZIP rỗng. Không tự ghi điểm đạt được.

## 2. Một quyết định trước khi dùng gợi ý

*Phần này phải ghi đúng đối tượng đầu tiên bạn **tự vẽ** trong `medium_instance`, trước khi sử dụng gợi ý tự động. Không thể điền thay nếu chưa biết bạn đã vẽ vật nào.*

- **Ảnh, vị trí và object Medium đầu tiên tự vẽ:** [ĐIỀN TÊN ẢNH, VỊ TRÍ VÀ VẬT THỰC TẾ].
- **Class và quy tắc chọn biên:** [ĐIỀN CLASS THỰC TẾ; mô tả phần nhìn thấy và lý do chọn đường biên].
- **Nếu đã dùng gợi ý sau đó:** [GHI GỢI Ý NÀO ĐÚNG/SAI, ĐÃ SỬA HAY GIỮ VÀ LÝ DO].
- **Nếu không dùng gợi ý:** Ghi “Không dùng” và giải thích một quyết định gán nhãn thực tế.

## 3. Một lỗi tôi tìm thấy và sửa

**Lỗi thực tế đã gặp trong quá trình tạo nhãn (lỗi kỹ thuật, không phải lỗi chất lượng mask):**

- **Task/ảnh/vùng:** `hard_panoptic` — phần cấu hình Labels → Raw trước khi vẽ ảnh.
- **Loại lỗi:** Khác — JSON nhãn không được CVAT chấp nhận.
- **Bằng chứng quan sát:** CVAT hiển thị `Unexpected non-whitespace character after JSON at position 2 (line 1 column 3)`.
- **Hành động xử lý:** Sau lỗi này, task Hard đã có thể tiếp tục thực hiện. [HỌC VIÊN XÁC NHẬN CÁCH ĐÃ SỬA: xóa toàn bộ nội dung Raw và dán lại JSON / thêm nhãn bằng Constructor / cách khác].
- **Đã Save và export lại chưa?** Học viên xác nhận có file `hard_panoptic.zip`; cần kiểm tra ZIP có đủ hai ảnh và các mask hay chưa.
- **Kết quả tự đánh giá GitHub Actions:** Chưa có kết quả được cung cấp; không tự ghi điểm.

> **Lưu ý:** Nếu giảng viên yêu cầu một *lỗi mask thực tế đã phát hiện và sửa*, hãy thay toàn bộ mục 3 bằng lỗi đúng từ ảnh đã tô (tên ảnh, vị trí, lỗi, thao tác sửa, Save/export). Không mô tả một lỗi mask chưa từng quan sát.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

Chỉ ghi các trường hợp thực sự đã gặp hoặc đã cân nhắc; không dùng ví dụ giả làm quan sát.

| Ảnh/vị trí | Hai cách hiểu có thể | Quy tắc/chứng cứ | Quyết định hoặc câu hỏi cho coach |
| --- | --- | --- | --- |
| Easy Semantic — đoạn mặt đường có ô tô; [BỔ SUNG TÊN ẢNH/VỊ TRÍ] | Tô `road` cả phần bị ô tô che, hoặc chỉ tô mặt đường nhìn thấy | Quy tắc chỉ gán mask cho pixel nhìn thấy; ô tô không thuộc năm class Easy | [XÁC NHẬN BẠN ĐÃ TÔ QUANH XE, KHÔNG TÔ LÊN XE; HOẶC GHI CÂU HỎI THỰC TẾ] |
| [ĐIỀN ẢNH/VÙNG THỰC TẾ 2] | [CÁCH HIỂU A] / [CÁCH HIỂU B] | [DẤU HIỆU NHÌN THẤY VÀ QUY TẮC ÁP DỤNG] | [QUYẾT ĐỊNH HOẶC CÂU HỎI] |
| [ĐIỀN ẢNH/VÙNG THỰC TẾ 3] | [CÁCH HIỂU A] / [CÁCH HIỂU B] | [DẤU HIỆU NHÌN THẤY VÀ QUY TẮC ÁP DỤNG] | [QUYẾT ĐỊNH HOẶC CÂU HỎI] |
