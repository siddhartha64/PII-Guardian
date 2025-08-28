# PII-Defense-Flixkart
*A robust Personal Identifiable Information (PII) detection and redaction system for e-commerce applications*  

Author: **Pagilla Siddhartha Reddy**

---

##  Overview
This project is designed to detect and mask sensitive information in real-time.  
It helps prevent leakage of Personally Identifiable Information (PII) like phone numbers, Aadhaar, UPI IDs, emails, and more.  

The system uses a combination of regex patterns and masking strategies to ensure data privacy while keeping logs useful for analysis.

---

##  Features
- **Multi-format Detection**: Supports phone numbers, Aadhaar, passport, UPI, emails, addresses, and IPs  
- **Intelligent Masking**: Context-aware redaction that preserves utility  
- **Combinatorial Analysis**: Flags risky PII combinations  
- **Real-time Processing**: Works efficiently with CSV + JSON input  
- **Comprehensive Logging**: Tracks detections and redactions  

---

##  Supported PII Types

| PII Type  | Detection Pattern | Masking Strategy      |
|-----------|------------------|------------------------|
| Phone     | 10-digit number  | `12XXXXXX89`           |
| Aadhaar   | 12-digit number  | `1234XXXX5678`         |
| Passport  | A + 7 digits     | `AXXXXXXX9`            |
| UPI ID    | user@domain      | `userXXX@domain`       |
| Email     | Standard format  | `us.XXX@domain.com`    |
| Address   | Contains PIN     | `[REDACTED_ADDRESS]`   |
| IP Addr   | IPv4 format      | `192.168.1.XXX`        |
| Names     | Full names       | `SaXXXXX NaXXXXx`      |

---

## Quick Start

### 1. Requirements
- Python **3.6+**
- Standard libraries: `csv`, `json`, `re`, `sys`

### 2\. Run the Detector



```
python detector_Pagilla_Siddhartha_Reddy.py iscp_pii_dataset.csv
```

 Input Format
---------------

CSV file should look like:


```
record_id,json_data
1,"{""name"": ""John Doe"", ""phone"": ""1234567890"", ""email"": ""john@example.com""}"
2,"{""first_name"": ""Jane"", ""last_name"": ""Smith"", ""aadhar"": ""123456789012""}"
```

 Output
---------

The script generates `redacted_output_Pagilla_Siddhartha_Reddy.csv` with the following columns:

-   **record_id** → Original ID
-   **redacted_data_json** → Masked JSON
-   **is_pii** → Boolean flag

 Architecture
---------------

-   **Standalone Detection** → Directly masks sensitive fields
-   **Combinatorial Detection** → Flags risky identity leaks when multiple PII types appear together

### Flow:

```
Input data → Detector
PII detected → Masked inline
Logs/cleaned data → Output file or downstream system
```

 Project Structure
--------------------

```
Assignment/
├── detector_Pagilla_Siddhartha_Reddy.py          # Main detection script
├── iscp_pii_dataset.csv                          # Sample dataset
├── redacted_output_Pagilla_Siddhartha_Reddy.csv  # Masked output
├── README.md                                     # Project documentation
```
