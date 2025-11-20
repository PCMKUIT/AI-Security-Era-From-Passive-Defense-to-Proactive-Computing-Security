# ⭐ So sánh Chi tiết: CVSS v3.1 và CVSS v4.0

Bảng so sánh này cung cấp cái nhìn hệ thống giữa CVSS v3.1 và CVSS v4.0, tập trung vào mục tiêu thiết kế, các thành phần, phương pháp chấm điểm và những thay đổi quan trọng.

## 📊 Tóm tắt Khác biệt Chính

| Nội dung | CVSS v3.1 | CVSS v4.0 (CVSS-B) | Thay đổi Chính |
| :--- | :--- | :--- | :--- |
| **Năm Ra mắt** | 2019 | 2023 | v4.0 là bản **cải tiến toàn diện**, tập trung vào các hệ thống hiện đại. |
| **Thang điểm** | 0.0 – 10.0 | 0.0 – 10.0 | Thang điểm cuối không thay đổi. |
| **Nhóm Chỉ số** | 3 nhóm: **Base, Temporal, Environmental** | 3 nhóm: **Base, Threat, Environmental** | **Threat metrics** thay thế/mở rộng **Temporal** để phản ánh rủi ro thực tế. |
| **Phạm vi (Scope – S)** | Unchanged (U) / Changed (C) | **Đã loại bỏ** | Thay thế bằng mô hình đánh giá **Tác động (Impact)** trực tiếp và rõ ràng hơn. |
| **Impact Subscores** | C (Confidentiality), I (Integrity), A (Availability) | C, I, A được chia nhỏ (VC/VI/VA, SC/SI/SA). | Chi tiết và chính xác hơn trong việc đo lường tác động lên hệ thống bị ảnh hưởng và các hệ thống kế tiếp. |
| **Chỉ số Mới** | Không có | Thêm **AT** (Attack Technique), **EUT** (Exploit Utility), **SA** (Safety), **AU** (Automatable), v.v. | Phản ánh tốt hơn **mức độ bị khai thác thực tế** và các mối đe dọa tự động hóa. |
| **Liên kết** | Dùng rộng rãi | Thiết kế để gắn chặt với **SBOM, VEX, SSVC** (Chuỗi cung ứng phần mềm). | Thuận tiện hơn trong quản trị rủi ro và chuỗi cung ứng. |
| **Vector String** | Bắt đầu bằng `CVSS:3.1/...` | Bắt đầu bằng `CVSS:4.0/...` | Thay đổi cú pháp để chứa các chỉ số mới. |

-----

## 🔍 I. Khác biệt Chi tiết theo Từng Nhóm Chỉ số

### 1️⃣ Base Metrics

| Chỉ số | CVSS v3.1 | CVSS v4.0 | Lý do Thay đổi |
| :--- | :--- | :--- | :--- |
| **Cốt lõi** | AV, AC, PR, UI, S, C, I, A | AV, AC, **AT**, PR, UI, **VC**, **VI**, **VA** | **Scope (S)** bị loại bỏ. **Attack Technique (AT)** được thêm vào. Tác động (C, I, A) được đổi tên thành **Vulnerable System Impact (VC, VI, VA)** để rõ ràng hơn. |
| **Phân tách** | Base Score = Mức độ Nghiêm trọng Kỹ thuật | Base Score = Mức độ Nghiêm trọng Kỹ thuật | **v4.0** phân tách rõ ràng giữa **nguy cơ khai thác thực tế** (Threat) và **mức độ nghiêm trọng kỹ thuật** (Base). |
| **Kỹ thuật Tấn công (AT)** | Không có | **Thêm vào (AT: Passive/Active)** | Đo lường tiềm năng kẻ tấn công thay đổi trạng thái hoặc dữ liệu của hệ thống dễ bị tổn thương trong quá trình tấn công. |

-----

### 2️⃣ Threat Metrics (Mới trong CVSS v4.0)

CVSS v3.1 có **Temporal Metrics** nhưng ít được sử dụng. Trong v4.0, nhóm này được tái thiết kế thành **Threat Metrics** để thực tế hơn trong đánh giá rủi ro hoạt động.

| Threat Metric | Khái niệm CVSS v4.0 | Mục đích |
| :--- | :--- | :--- |
| **Exploit Utility (EUT)** | Mức độ phát triển của mã khai thác (ví dụ: Proof-of-Concept, Functional, High) | Phản ánh trạng thái của mã khai thác có sẵn công khai. |
| **Remediation Progress (RP)** | Tình trạng Khắc phục (ví dụ: Official Fix, Temporary Fix) | Thay thế cho Remediation Level trong v3.1. |
| **Urgency (UR)** | Mức độ Khẩn cấp từ Nhà cung cấp | Cho phép nhà cung cấp/tổ chức tư vấn truyền đạt ngay lập tức mức độ quan trọng và khẩn cấp thực tế của bản vá. |

**Tác dụng:** Các chỉ số này cho phép các tổ chức tính toán **Threat Score (CVSS-BT)** phản ánh tốt hơn **nguy cơ khai thác thực tế** và giúp ưu tiên việc vá lỗi.

-----

### 3️⃣ Environmental Metrics

CVSS v4.0 giữ lại Environmental Metrics nhưng cải tiến:

  * **Rõ ràng hơn:** Các tiêu chí được định nghĩa rõ ràng hơn.
  * **Tác động Kinh doanh:** Cho phép điều chỉnh điểm dựa trên **Yêu cầu về Bảo mật, Toàn vẹn và Sẵn sàng (CR, IR, AR)** cụ thể của bối cảnh kinh doanh.
  * **Môi trường Hiện đại:** Đơn giản hóa để sử dụng trong các môi trường phân tán như **Cloud, OT (Công nghệ Vận hành), và IoT**.

-----

## 🔍 II. Thay đổi trong Cách tính Tác động (Impact)

### CVSS v3.1:

Impact Score được tính từ $C + I + A$, và **Scope (S)** ảnh hưởng lớn đến công thức tính toán.

### CVSS v4.0:

Impact được phân tách chi tiết hơn thành các khía cạnh đa chiều, phù hợp với các hệ thống phức tạp, liên kết:

1.  **System Impact (VC, VI, VA):** Tác động lên thành phần trực tiếp bị lỗ hổng ảnh hưởng.
2.  **Subsequent System Impact (SC, SI, SA):** Tác động lên bất kỳ thành phần hoặc hệ thống nào **ngoài** hệ thống dễ bị tổn thương ban đầu (giống như "Changed Scope" nhưng chi tiết hơn).
3.  **Safety Impact (S):** Quan trọng đối với **OT, IoT, và CPS (Hệ thống Vật lý-Điều khiển)**, đo lường tác động lên an toàn vật lý hoặc tính mạng con người.
4.  **Automation Impact (AU):** Liên quan đến các mối đe dọa tự động hóa.

-----

## 🔍 III. Vector String

Vector String tóm tắt tất cả các chỉ số.

### CVSS v3.1 Ví dụ:

```
CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H
```

### CVSS v4.0 Ví dụ:

```
CVSS:4.0/AV:N/AC:L/AT:N/PR:N/UI:N/VC:H/VI:H/VA:H/SC:L/SI:L/SA:N
```

**Khác biệt chính:**

  * Sử dụng `CVSS:4.0/...`
  * Thay thế $C, I, A$ bằng $VC, VI, VA$ (Vulnerable Confidentiality, v.v.)
  * Thêm các chỉ số Tác động Hệ thống Kế tiếp ($SC, SI, SA$).
  * Loại bỏ $S$ (Scope).
  * Thêm $AT$ (Attack Technique) là một chỉ số cơ bản bắt buộc.

-----

# ⭐ Tóm tắt Ngắn gọn: CVSS v4.0 Đã Cải tiến những gì?

| Lợi ích | Giải thích |
| :--- | :--- |
| **Phản ánh Nguy cơ Thực tế Tốt hơn** | **Threat metrics** chi tiết cho phép ưu tiên vá lỗi dựa trên khả năng khai thác thực tế. |
| **Phù hợp Hệ thống Hiện đại** | Thiết kế rõ ràng cho **Cloud, OT, IoT, và CPS** (Hệ thống Vật lý-Điều khiển). |
| **Vector Rõ ràng hơn** | **Bỏ Scope**, cải tiến Impact thành hai nhóm hệ thống (Vulnerable và Subsequent) giúp giảm sự mơ hồ. |
| **Hỗ trợ SBOM, VEX** | Tích hợp tốt vào quy trình **DevSecOps** và quản lý chuỗi cung ứng phần mềm. |
