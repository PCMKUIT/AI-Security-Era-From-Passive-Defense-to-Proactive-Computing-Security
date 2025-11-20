# 🛡️ AI Security Vulnerabilities - 2024 & 2025 Combined Analysis

This repository curates detailed documentation for critical AI-related Common Vulnerabilities and Exposures (CVEs) across **2024 and 2025**, based on analysis from Fluency Security and other public reports.

---

## 📊 Combined AI CVE Statistics: By Category

The combined data confirms that **Prompt Injection** and **RCE** are the two biggest and most critical threats to the AI/ML ecosystem.

| Vulnerability Category | Count | Examples (Combined 2024 & 2025) |
| :--- | :--- | :--- |
| **Prompt Injection / Logic Abuse** | **6** | CVE-2025-32711, CVE-2024-8309, CVE-2024-5565, CVE-2024-12366, CVE-2025-54132, etc. |
| **Remote Code Execution (RCE)** | **7** | (Includes RCE from Prompt Injection, Deserialization, Code Injection, and Container Escape) |
| **Access Control Issues (Auth/IDOR/Escalation)** | **5** | CVE-2025-51867, CVE-2025-5071, CVE-2025-23359, etc. |
| **File / Path Handling / SSRF** | **2** | CVE-2025-54381 (SSRF), CVE-2025-32018 (Path Traversal) |
| **UI/Script Injection (XSS)** | 1 | CVE-2025-5570 |
| **Denial of Service (DoS)** | 1 | CVE-2025-6398 |

---

## 📋 Complete AI CVE List (2024 & 2025)

| CVE ID | Year | Product / Vendor | Vulnerability Type |
| :--- | :--- | :--- | :--- |
| **Prompt Injection & Execution** | | | |
| CVE-2025-32711 | 2025 | Microsoft 365 Copilot | AI command/prompt injection (**EchoLeak**) |
| **CVE-2024-8309** | **2024** | **LangChain (GraphCypherQAChain)** | SQL Injection via Prompt Injection |
| **CVE-2024-5565** | **2024** | **Vanna.AI** | Prompt injection leading to **RCE** |
| **CVE-2024-12366** | **2024** | **PandasAI** | Prompt injection leading to **RCE** |
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

### 1. Prompt Injection Dominance and Privilege Escalation
Prompt Injection vulnerabilities from 2024 (Vanna.AI, PandasAI) established the pattern for **Language-to-Code Execution** attacks. This trend escalated in 2025 with highly sophisticated variants like **Zero-click Prompt Injection** (EchoLeak), proving that manipulating AI's linguistic logic remains a critical attack vector.

### 2. Focus on Infrastructure Over Models
While Prompt Injection is a logic flaw, a majority of other CVEs target the **supporting infrastructure for AI/ML deployment** (e.g., BentoML, NVIDIA RAPIDS, Container Toolkit). This highlights the crucial importance of securing the entire **AI Supply Chain** and tackling traditional security flaws like Deserialization and Container Escape within AI environments.

### 3. The "Man-in-the-Prompt" Challenge
The emergence of flaws like **Prompt-influenced path traversal** in Cursor AI Editor shows that attacks are moving to target the **data preprocessing stages** and intermediate layers (Man-in-the-Prompt), where data is transformed before reaching the core model.

---

## 💡 Key Insights: Rapid Threat Evolution

* **Systemic Risk:** The confirmed instances of **Prompt Injection leading to RCE** and **Zero-click** vulnerabilities indicate that AI developers are facing far more serious systemic risks compared to typical application flaws.
* **Full Pipeline Security:** The data confirms that focusing solely on the AI model is insufficient; security must be applied to the entire **AI pipeline**—from computation libraries (`cuML`) to deployment platforms (`BentoML`) and development tools (`Cursor`).

---

## 🔗 Reference

Based on analysis from [Fluency Security - State of AI Vulnerability 2025](https://blogs.fluencysecurity.com/ai-cves-of-2025/)
