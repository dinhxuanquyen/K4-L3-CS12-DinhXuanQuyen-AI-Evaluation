# Báo cáo chi tiết kết quả bài tập CS12 · Nhóm 03

## Đề tài: Đánh giá trợ lý đổi trả Mộc Store
- Hình thức: **Thực hiện cá nhân**
- Học viên: **Đinh Xuân Quyền** (Nhóm 03 theo danh sách lớp)
- File dữ liệu: [`Nhom03_CS12.xlsx`](./Nhom03_CS12.xlsx) / [`DinhXuanQuyen_CS12.xlsx`](./DinhXuanQuyen_CS12.xlsx)

---

### Chi tiết các phần bài tập Xưởng (10 điểm)

#### X1. Đơn vị công việc AI (1.0 điểm)
- **Câu chuẩn:** *"Đọc 1 tin nhắn yêu cầu đổi trả của khách và dữ liệu đơn hàng trong hệ thống → soạn câu phản hồi theo đúng chính sách CS-1 đến CS-6 kèm bước hành động tiếp theo, thời gian phản hồi dưới 2 giây; chuyển nhân viên khi khách yêu cầu gặp người hoặc khiếu nại hàng lỗi."*
- **Tiêu chuẩn đạt:** Đủ đầu vào, đầu ra kiểm được, ràng buộc số (< 2 giây), nói rõ ca chuyển người (CS-3, CS-6).

#### X2. Chiều và phễu (1.0 điểm)
- **3 chiều qua phép thử:**
  1. *Ý định yêu cầu:* 4 giá trị (Đổi hàng, Trả hàng, Tra cứu đơn, Cần làm rõ) $\rightarrow$ đổi nhánh xử lý, công cụ gọi khác nhau.
  2. *Thời gian nhận hàng & tình trạng:* 3 giá trị (trong 7 ngày, quá 7 ngày, hàng lỗi trong 30 ngày) $\rightarrow$ đổi từ chấp nhận sang từ chối hoặc chuyển người.
  3. *Mức độ cung cấp thông tin mã đơn:* 3 giá trị (có mã, chỉ có SĐT, không có thông tin) $\rightarrow$ đổi từ tra cứu sang hỏi thông tin.
- **Phễu:** $4 \times 3 \times 3 = 36$ tổ hợp $\rightarrow$ loại 12 phi lý $\rightarrow$ còn 24 $\rightarrow$ chọn 15 tình huống $\times$ 3 cách diễn đạt = **45 ca** (nằm chuẩn trong khoảng 40–50 ca).

#### X3. Ngân hàng 8 tình huống (2.0 điểm)
- Đủ 3 loại: 3 Đại diện (ca 1, 2, 8), 4 Thử thách (ca 3, 4, 5, 6), 1 Hồi quy nghiêm trọng (ca 7: đơn 15 ngày đòi trả tiền).
- Mọi tình huống đều dẫn chuẩn mã chính sách `CS-1` đến `CS-6`.

#### X4. Đọc 3 vết thực thi mới (1.5 điểm)
- **Vết W1:** Bước 3 | Mã lỗi: `missing_lookup` | Giải pháp: Bắt buộc gọi `tra_cuu_don` trước khi tạo yêu cầu.
- **Vết W2:** Bước 2 | Mã lỗi: `wrong_intent` | Giải pháp: Khi nhiều đơn hoặc mơ hồ phải gán `Cần làm rõ` và hỏi lại.
- **Vết W3:** Bước 4 | Mã lỗi: `missing_escalation` | Giải pháp: Khi hàng lỗi (CS-3) hoặc đòi gặp người (CS-6), bắt buộc gọi `chuyen_nhan_vien`.

#### X5. 4 tiêu chí nhị phân (2.0 điểm)
1. **TC1:** Tra cứu trước khi xác nhận (Mã lệnh, ngưỡng 100%)
2. **TC2:** Chuyển nhân viên khi hàng lỗi (Mã lệnh, ngưỡng 100%)
3. **TC3:** Ghi nhận cảm xúc trước khi xử lý (Giám khảo AI, ngưỡng $\ge 85\%$)
4. **TC4:** Không bịa thông tin đơn (Mã lệnh, ngưỡng 100%)
- Không chứa từ ngữ mơ hồ; ví dụ sát ranh 2 phía rõ ràng.

#### X6. Hiệu chỉnh giám khảo (1.0 điểm)
- Ma trận nhầm lẫn: Cả hai Đạt = 12 | Chặn nhầm = 2 | Cho qua lỗi = 0 | Cả hai Không đạt = 6.
- TPR = 85.7% (dưới ngưỡng 90%) | TNR = 100% (đạt ngưỡng 90%).
- Kết luận: Chọn **B** (thêm ví dụ Đạt sát ranh và mục không bắt buộc để giảm chặn nhầm).

#### X7. Kết luận có răng (1.5 điểm)
- Quyết định: **Phát hành** (Đạt mọi tiêu chí, độ sụt 2 điểm của TC3 chỉ là nhiễu thống kê trên 50 ca).
- Kế hoạch theo dõi sau phát hành:
  + Tỷ lệ mẫu: 5% tin thực tế/ngày (~15 tin/ngày).
  + 3 tín hiệu trôi: Tỷ lệ dislike, tỷ lệ đòi gặp người, tỷ lệ trôi phân loại ý định.
  + Ngưỡng cảnh báo: Dislike > 15%, độ chính xác tụt > 3 điểm, đòi gặp người > 10%.
  + Phân công: Chị Ngân kiểm tra hàng ngày; AI PM & Tech lead họp rà soát hàng tuần.
- 3 câu số liệu: Tỷ lệ nền = **75%**, Số ca chống tái phát = **50**, Tỷ lệ khớp = **84%**.
