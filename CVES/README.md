# 🛡️ AI Security Vulnerabilities - 2024 & 2025 Combined Analysis

This repository curates detailed documentation for critical AI-related Common Vulnerabilities and Exposures (CVE) across **2024 and 2025**, based on analysis from Fluency Security and public reports.

-----

## 📊 Combined AI CVE Statistics: By Category

The combined data confirms that **Prompt Injection** and **RCE** are the two biggest and most critical threats to the AI/ML ecosystem.

| Vulnerability Category                           | Count | Examples                                                                             |
| :----------------------------------------------- | :---- | :----------------------------------------------------------------------------------- |
| **Prompt Injection / Logic Abuse** | **6** | CVE-2025-32711, CVE-2024-8309, CVE-2024-5565, CVE-2024-12366, CVE-2025-54132, etc.   |
| **Remote Code Execution (RCE)** | **7** | Includes RCE via prompt injection, deserialization, code injection, container escape |
| **Access Control Issues (Auth/IDOR/Escalation)** | **5** | CVE-2025-51867, CVE-2025-5071, CVE-2025-23359, etc.                                  |
| **File / Path Handling / SSRF** | **2** | CVE-2025-54381 (SSRF), CVE-2025-32018 (Path Traversal)                               |
| **UI/Script Injection (XSS)** | 1     | CVE-2025-5570                                                                        |
| **Denial of Service (DoS)** | 1     | CVE-2025-6398                                                                        |

-----

## 📋 Complete AI CVE List (2024 & 2025)

| CVE ID                                   | Year | Product / Vendor               | Vulnerability Type                         |
| :--------------------------------------- | :--- | :----------------------------- | :----------------------------------------- |
| **Prompt Injection & Execution** |      |                                |                                            |
| CVE-2025-32711                           | 2025 | Microsoft 365 Copilot          | AI command/prompt injection (**EchoLeak**) |
| **CVE-2024-8309** | 2024 | LangChain (GraphCypherQAChain) | SQL Injection via Prompt Injection         |
| **CVE-2024-5565** | 2024 | Vanna.AI                       | Prompt injection → **RCE** |
| **CVE-2024-12366** | 2024 | PandasAI                       | Prompt injection → **RCE** |
| CVE-2025-54132                           | 2025 | Cursor AI Editor               | Embedded prompt injection                  |
| CVE-2025-32018                           | 2025 | Cursor AI Editor               | Prompt-influenced path traversal           |
| CVE-2025-3248                            | 2025 | Langflow                       | API code injection                         |
| **Infrastructure & Deserialization RCE** |      |                                |                                            |
| CVE-2025-27520                           | 2025 | BentoML                        | Unsafe deserialization → **RCE** |
| CVE-2025-0140                            | 2025 | NVIDIA RAPIDS                  | Insecure deserialization → **RCE** |
| CVE-2025-23266                           | 2025 | NVIDIA Container Toolkit       | Container escape / PrivEsc                 |
| CVE-2025-0132                            | 2025 | NVIDIA Toolkit                 | Container escape bypass                    |
| CVE-2025-23359                           | 2025 | NVIDIA Toolkit                 | Container escape bypass                    |
| **Access Control & Web Flaws** |      |                                |                                            |
| CVE-2025-54381                           | 2025 | BentoML                        | SSRF (file-based)                          |
| CVE-2025-51867                           | 2025 | Deepfiction AI                 | IDOR / Account takeover                    |
| CVE-2025-5071                            | 2025 | AI Engine WP plugin            | Missing auth / MCP misuse                  |
| CVE-2025-5570                            | 2025 | AI Engine WP plugin            | Stored XSS                                 |
| CVE-2025-6398                            | 2025 | ASUS AI Suite 3                | Null pointer DoS                           |

-----

## 🚨 Key Trends in AI Security (2024–2025)

### **1. Prompt Injection Dominance**

Prompt Injection evolved from simple logic manipulation (2024) → to **zero-click**, environment-aware, and chained privilege escalation attacks in 2025.

### **2. Infrastructure Attacks Growing Faster Than Model Attacks**

The majority of critical AI CVEs involve:

  * Unsafe deserialization
  * Container escape
  * GPU/ML pipeline exploitation
  * File/IO processing abuse

These reveal systemic weaknesses beyond the model itself.

### **3. The “Man-in-the-Prompt” Layer**

Attacks now target **intermediate stages** like:

  * AI editors (Cursor)
  * Data transformation pipelines
  * LLM-agent orchestration layers

leading to novel issues like **prompt-influenced path traversal**.

-----

## 💡 Key Insights

  * Prompt Injection is no longer a “model flaw” — it's a **full-stack attack surface**.
  * RCE from AI prompts proves that **AI model outputs must be treated as untrusted input**.
  * Securing AI systems demands **full-pipeline visibility** from GPU libraries → orchestration → model → UI.

-----

# ➕ Appendix: CVSS Scoring Algorithms (Specification)

This section extends the README with **official CVSS v3.1 and v4.0 equations**, helping analysts understand how severity scores were derived for each CVE.

-----

## **1. CVSS v3.1 Scoring Algorithm (Simplified & Formal Specification)**

The Base Score depends on **Impact** and **Exploitability**:

### **Base Score**

```
If Impact <= 0: 
    Base = 0
Else If Scope = Unchanged:
    Base = RoundUp( min(Impact + Exploitability, 10) )
Else If Scope = Changed:
    Base = RoundUp( min(1.08 × (Impact + Exploitability), 10) )
```

-----

### **Impact Sub-Score (ISC)**

```
ISC_Base = 1 - ((1 - C) × (1 - I) × (1 - A))

If Scope = Unchanged:
    Impact = 6.42 × ISC_Base
Else:
    Impact = 7.52 × (ISC_Base - 0.029) 
             - 3.25 × (ISC_Base - 0.02)^15
```

-----

### **Exploitability Sub-Score**

```
Exploitability = 8.22 × AV × AC × PR × UI
```

-----

## **2. Temporal Score (v3.1)**

```
Temporal = RoundUp(
    Base × ExploitCodeMaturity × RemediationLevel × ReportConfidence
)
```

-----

## **3. Environmental Score (v3.1)**

Environmental Score recalculates the Base Score using modified metrics.

```
If Modified Impact <= 0:
    Environmental = 0

Else If Modified Scope = Unchanged:
    Environmental = RoundUp(
        RoundUp(min(M.Impact + M.Exploitability, 10))
        × E × RL × RC
    )

Else If Modified Scope = Changed:
    Environmental = RoundUp(
        RoundUp(min(1.08 × (M.Impact + M.Exploitability), 10))
        × E × RL × RC
    )
```

-----

### **Modified ISC (v3.1)**

```
ISC_Modified = min(
    1 - ((1 - M_C×CR) × (1 - M_I×IR) × (1 - M_A×AR)),
    0.915
)
```

### **Modified Exploitability (v3.1)**

```
M.Exploitability = 8.22 × M_AV × M_AC × M_PR × M_UI
```

-----

4. CVSS v4.0 (CVSS-B) Scoring Algorithm 🚀CVSS v4.0 simplifies the structure by combining Temporal and Environmental concepts into the Threat and Supplemental groups, and introducing new Impact metrics.Base Score (CVSS-B)The Base Score is determined by the Base Equation (BE) and the Impact Subscore (IS), similar to v3.1, but using new impact variables (VC, VI, VA, SC, SI, SA).$$\text{CVSS-B} = \text{RoundUp}(\text{Min}(\text{BE} \times 10, 10))$$Trong đó:$$\text{BE} = \text{Min}(\text{IS} \times 1.176, \text{Exploitability}) + \text{IS}$$Exploitability Sub-Score (E)Giống như v3.1, nhưng sử dụng các biến $AV$, $AC$, $AT$, $PR$, $UI$.$$\text{Exploitability} = 0.55 \times (8.58 \times \text{AV} \times \text{AC} \times \text{AT} \times \text{PR} \times \text{UI})$$Impact Sub-Score (IS)Impact Sub-Score là trung bình có trọng số của hai nhóm ảnh hưởng: Vulnerable System (VC, VI, VA) và Subsequent System (SC, SI, SA).$$\text{IS} = 1 - \Big( (1-\text{VC} \times \text{VCI}) \times (1-\text{VI} \times \text{VII}) \times (1-\text{VA} \times \text{VAI}) \Big) \times \Big( (1-\text{SC} \times \text{SCI}) \times (1-\text{SI} \times \text{SII}) \times (1-\text{SA} \times \text{SAI}) \Big)$$Threat Score (CVSS-BT)Threat Score là sự kết hợp của Base Score và các yếu tố thời gian (Threat).$$\text{CVSS-BT} = \text{RoundUp}(\text{CVSS-B} \times \text{EUT} \times \text{RP} \times \text{UR})$$MetricÝ nghĩaEUTExploit Utility (Độ hữu dụng của khai thác)RPRemediation Progress (Tiến trình khắc phục)URUrgency (Tính cấp bách)Supplemental Score (CVSS-BTE)Supplemental Score bổ sung các yếu tố về Auto (Tự động hóa) và Safety (An toàn).$\text{CVSS-BTE} = \text{CVSS-BT} \quad \text{+ (Auto: High/Low, Safety: Present/Not Present)}$(Lưu ý: Công thức này chỉ là chỉ định khái niệm, giá trị số cụ thể phụ thuộc vào chuẩn CVSS v4.0 chính thức.)RoundUp Rule (v3.1 & v4.0)RoundUp(x) = smallest number (1 decimal) ≥ x  
Example: RoundUp(4.01) = 4.1
