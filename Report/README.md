Dưới đây là so sánh chi tiết và có cấu trúc giữa **CVSS v3.1** và **CVSS v4.0** dưới dạng file Markdown, được trình bày với format đẹp và dễ đọc.

-----

# ⭐ Detailed Comparison: CVSS v3.1 vs. CVSS v4.0

This table provides a systematic comparison between CVSS v3.1 and CVSS v4.0, highlighting the design objectives, components, scoring methodology, and key changes.

## 📊 Summary of Key Differences

| Feature | CVSS v3.1 | CVSS v4.0 (CVSS-B) | Key Change |
| :--- | :--- | :--- | :--- |
| **Release Year** | 2019 | 2023 | v4.0 is a **comprehensive redesign** focusing on modern ecosystems. |
| **Final Score Range** | 0.0 – 10.0 | 0.0 – 10.0 | Score scale remains consistent. |
| **Metric Groups** | 3 Groups: **Base, Temporal, Environmental** | 3 Groups: **Base, Threat, Environmental** | **Threat** metrics replace/expand **Temporal** for practical use. |
| **Scope (S)** | Unchanged (U) / Changed (C) | **Eliminated** | Replaced by a clearer, direct model for **Impact** calculation. |
| **Impact Subscores** | Confidentiality (C), Integrity (I), Availability (A) | C, I, A are more granular (VC/VI/VA, SC/SI/SA). | More detail and precision in measuring system vs. subsequent impact. |
| **New Metrics Added** | N/A | **AT** (Attack Technique), **EUT** (Exploit Utility), **SA** (Safety), **AU** (Automatable), etc. | Better reflects **real-world exploitability** and automated threats. |
| **Alignment** | Widely used | Designed to align with **SBOM, VEX, SSVC** (Software Supply Chain). | Seamless integration into modern risk and vulnerability management. |
| **Vector String** | Starts with `CVSS:3.1/...` | Starts with `CVSS:4.0/...` | Syntax changed to accommodate new metrics. |

-----

## 🔍 I. Detailed Differences by Metric Group

### 1️⃣ Base Metrics

| Metric | CVSS v3.1 | CVSS v4.0 | Rationale for Change |
| :--- | :--- | :--- | :--- |
| **Core** | AV, AC, PR, UI, S, C, I, A | AV, AC, **AT**, PR, UI, **VC**, **VI**, **VA** | **Scope (S)** is removed. **Attack Technique (AT)** is added for complexity. Impact is renamed (Vulnerable System) for clarity. |
| **Separation** | Base Score = Technical Severity | Base Score = Technical Severity | **v4.0** clearly separates the **technical severity** (Base) from the **likelihood of exploitation** (Threat).  |
| **Attack Technique (AT)** | Not present | **Added (AT: Passive/Active)** | Measures the potential for an attacker to modify the vulnerable system's state or data during the attack. |

-----

### 2️⃣ Threat Metrics (New in CVSS v4.0)

CVSS v3.1 included **Temporal Metrics**, which were often ignored in practice. v4.0 redesigns this group into **Threat Metrics** to be more relevant to operational risk.

| Threat Metric | CVSS v4.0 Concept | Purpose |
| :--- | :--- | :--- |
| **Exploit Maturity (EUT)** | Exploit Utility (e.g., Proof-of-Concept, Functional, High) | Reflects the state of publicly available exploit code. |
| **Remediation Progress (RP)** | Remediation Status (e.g., Official Fix, Temporary Fix) | Replaces the v3.1 Remediation Level. |
| **Urgency (UR)** | Provider Urgency | Allows vendors/advisories to immediately communicate the real-world criticality and urgency of a fix. |

**Effect:** These metrics allow organizations to calculate a **Threat Score (CVSS-BT)** that is a much better reflection of **actual exploitation risk** and helps prioritize patching efforts.

-----

### 3️⃣ Environmental Metrics

CVSS v4.0 retains and improves Environmental Metrics:

  * **Clarity:** More explicitly defined for ease of use.
  * **Business Impact:** Allows better adjustment of the score based on **Confidentiality, Integrity, and Availability Requirements (CR, IR, AR)** specific to the business context.
  * **Modern Environments:** Simplified for use in **Cloud, OT (Operational Technology), and IoT** environments.

-----

## 🔍 II. Changes in Impact Calculation

### CVSS v3.1:

The Impact Score is derived from $C, I, A$, where **Scope (S)** acts as a major modifier determining the calculation formula.

### CVSS v4.0:

Impact is broken down into a more granular, multi-dimensional view suitable for complex, interconnected systems:

1.  **Vulnerable System Impact (VC, VI, VA):** The impact on the component directly affected by the vulnerability.
2.  **Subsequent System Impact (SC, SI, SA):** The impact on any component or system **beyond** the vulnerable system.
3.  **Safety Impact (S):** Critical for **OT, IoT, and CPS (Cyber-Physical Systems)**, measuring the impact on physical safety or human life.
4.  **Automatable Impact (AU):** Relevant to automated threats and continuous integration pipelines.

-----

## 🔍 III. Vector String Syntax

The Vector String summarizes all metrics and is critical for automation.

### CVSS v3.1 Example:

```
CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H
```

### CVSS v4.0 Example:

```
CVSS:4.0/AV:N/AC:L/AT:N/PR:N/UI:N/VC:H/VI:H/VA:H/SC:L/SI:L/SA:N
```

**Key Differences:**

  * Uses `CVSS:4.0/...`
  * Replaces $C, I, A$ with $VC, VI, VA$ (Vulnerable Confidentiality, etc.)
  * Adds Subsequent System Impact metrics ($SC, SI, SA$).
  * Eliminates $S$ (Scope).
  * Adds $AT$ (Attack Technique) as a mandatory base metric.

-----

# ⭐ In Summary: Why CVSS v4.0 is Better

| Benefit | Explanation |
| :--- | :--- |
| **Better Reflects Real Risk** | Detailed **Threat metrics** (EUT, UR) allow prioritization based on actual likelihood of exploitation, not just technical severity. |
| **Supports Modern Systems** | Explicitly designed for **Cloud, OT, IoT, and CPS**, using new metrics like Safety (S) and Subsequent Impact ($SC, SI, SA$). |
| **Clearer Scoring Logic** | **Scope is removed**, and Impact is split into two systems, reducing ambiguity and scoring inconsistencies. |
| **Enhanced DevSecOps** | Tighter integration with **SBOM and VEX** standards for automated vulnerability governance. |

-----

Would you like me to generate a new CVE score using the CVSS v4.0 formula based on a set of input metrics?
