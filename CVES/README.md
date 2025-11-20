# 🛡️ AI Security Vulnerabilities - 2024 & 2025 Combined Analysis

This repository curates detailed documentation for critical AI-related Common Vulnerabilities and Exposures (CVEs) across **2024 và 2025**, dựa trên phân tích từ Fluency Security và các báo cáo công khai khác.

---

## 📊 Combined AI CVE Statistics: By Category

Dữ liệu kết hợp cho thấy **Prompt Injection** và **RCE** là hai mối đe dọa lớn nhất đối với hệ sinh thái AI/ML.

| Vulnerability Category | Count | Examples (Combined 2024 & 2025) |
| :--- | :--- | :--- |
| **Prompt Injection / Logic Abuse** | **6** | CVE-2025-32711, CVE-2024-8309, CVE-2024-5565, CVE-2024-12366, CVE-2025-54132, v.v. |
| **Remote Code Execution (RCE)** | **7** | (Bao gồm RCE từ Prompt Injection, Deserialization, Code Injection, và Container Escape) |
| **Access Control Issues (Auth/IDOR/Escalation)** | **5** | CVE-2025-51867, CVE-2025-5071, CVE-2025-23359, v.v. |
| **File / Path Handling / SSRF** | **2** | CVE-2025-54381 (SSRF), CVE-2025-32018 (Path Traversal) |
| **UI/Script Injection (XSS)** | 1 | CVE-2025-5570 |
| **Denial of Service (DoS)** | 1 | CVE-2025-6398 |

---

## 📋 Complete AI CVE List (2024 & 2025)

| CVE ID | Năm | Product / Vendor | Vulnerability Type |
| :--- | :--- | :--- | :--- |
| **Prompt Injection & Execution** | | | |
| CVE-2025-32711 | 2025 | Microsoft 365 Copilot | AI command/prompt injection (**EchoLeak**) |
| **CVE-2024-8309** | **2024** | **LangChain (GraphCypherQAChain)** | SQL Injection qua Prompt Injection |
| **CVE-2024-5565** | **2024** | **Vanna.AI** | Prompt injection dẫn đến **RCE** |
| **CVE-2024-12366** | **2024** | **PandasAI** | Prompt injection dẫn đến **RCE** |
| CVE-2025-54132 | 2025 | Cursor AI Editor | Embedded prompt injection |
| CVE-2025-32018 | 2025 | Cursor AI Editor | Prompt-influenced path traversal |
| CVE-2025-3248 | 2025 | Langflow | API code injection |
| **Infrastructure & Deserialization RCE** | | | |
| CVE-2025-27520 | 2025 | BentoML (v1.4.2) | Unsafe deserialization / **RCE** |
| CVE-2025-0140 | 2025 | NVIDIA RAPIDS (cuDF/cuML) | Insecure deserialization / **RCE** |
| CVE-2025-23266 | 2025 | NVIDIA Container Toolkit | Container escape / privilege escalation |
| CVE-2025-0132 | 2025 | NVIDIA Toolkit | Container escape bypass |
| CVE-2025-23359 | 2025 | NVIDIA Toolkit | Container escape bypass |
| **Access Control & Web Flaws** | | | |
| CVE-2025-54381 | 2025 | BentoML | **SSRF** via file upload |
| CVE-2025-51867 | 2025 | Deepfiction AI | **IDOR** / cross-account abuse |
| CVE-2025-5071 | 2025 | AI Engine WP plugin | Missing auth / MCP misuse |
| CVE-2025-5570 | 2025 | AI Engine WP plugin | **Stored XSS** in chatbot UI |
| CVE-2025-6398 | 2025 | ASUS AI Suite 3 | Null pointer crash (**DoS**) |

---

## 🚨 Key Trends in AI Security (2024-2025)

### 1. Prompt Injection Thống trị và Leo thang Đặc quyền
Các lỗ hổng Prompt Injection từ năm 2024 (Vanna.AI, PandasAI) đã thiết lập mô hình cho các cuộc tấn công **Ngôn ngữ -> Code Execution**. Xu hướng này tiếp tục vào năm 2025 với các biến thể nguy hiểm hơn như **Zero-click Prompt Injection** (EchoLeak), chứng minh rằng việc thao túng logic ngôn ngữ là vector tấn công hàng đầu.

### 2. Sự Tập trung vào Cơ sở hạ tầng (Infrastructure Focus)
Mặc dù Prompt Injection là lỗi logic, nhưng đa số các CVE còn lại tập trung vào các thành phần **hỗ trợ triển khai AI/ML** (như BentoML, NVIDIA RAPIDS, Container Toolkit). Điều này làm nổi bật tầm quan trọng của việc bảo mật **Chuỗi Cung ứng AI** (AI Supply Chain) và các lỗi bảo mật truyền thống như Deserialization và Container Escape trong môi trường AI.

### 3. Vấn đề "Man-in-the-Prompt"
Sự xuất hiện của các lỗ hổng như **Prompt-influenced path traversal** trong Cursor AI Editor cho thấy các cuộc tấn công đang dịch chuyển sang nhắm vào các giai đoạn **tiền xử lý dữ liệu** và các lớp trung gian (Man-in-the-Prompt), nơi dữ liệu được chuyển đổi trước khi đến mô hình chính.

---

## 💡 Key Insights: Sự Phát triển Nhanh Chóng

* **Tăng cường Mối đe dọa:** Sự xuất hiện của các lỗ hổng **Prompt Injection dẫn đến RCE** và **Zero-click** cho thấy các nhà phát triển AI đang phải đối mặt với các rủi ro hệ thống nghiêm trọng hơn nhiều so với các lỗi ứng dụng thông thường.
* **Bảo mật Toàn bộ Pipeline:** Dữ liệu chứng minh rằng việc chỉ tập trung vào mô hình AI là không đủ; bảo mật phải được áp dụng cho toàn bộ **AI pipeline**—từ thư viện tính toán (`cuML`) đến nền tảng triển khai (`BentoML`) và các công cụ hỗ trợ (`Cursor`).

---

## 🔗 Reference

Based on analysis from [Fluency Security - State of AI Vulnerability 2025](https://blogs.fluencysecurity.com/ai-cves-of-2025/)
```
