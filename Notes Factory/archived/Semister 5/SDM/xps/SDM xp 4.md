

### SDM Experiment No. 4

Aim: To implement the modules of the selected project.


#### **1. Identify Project Modules**

Break the project into manageable modules.

| Module No. | Module Name | Description |
| --- | --- | --- |
| 1   | Backend Server Module | FastAPI-based server with connection handling, file transfer APIs, and secure shutdown |
| 2   | File Transfer Module | Chunked/direct upload/download with adaptive sizing and memory-optimized streaming |
| 3   | Security & Encryption Module | AES-256-CBC encryption with PBKDF2, HTTPS-only support, and secure validation mechanisms |
| 4   | Clipboard System Module | Clipboard API for text, images, and file sharing with history tracking and in-memory storage |
| 5   | Frontend Interface Module | Responsive web interface for drag-drop, progress display, QR codes, and real-time tracking |
| 6   | Configuration & Analytics Module | System-wide config management, performance logs, exportable device/session analytics |
| 7   |  Network Discovery Module | LAN discovery, QR-based IP sharing, and protocol auto-detection |

***

#### **2. Perform Practical Implementation for Each Module**

**Module 1: Backend Server**  
• Tech Stack: Python 3.11+, FastAPI  
• Files: `main.py`, `routes.py`  
• Test: Start server and verify LAN & local endpoint visibility

**Module 2: File Transfer**  
• Upload Methods: Direct (HTTP), Chunked (adaptive size: 1–128MB)  
• Download Methods: Direct and chunked with ZIP support  
• Test: Upload/download files of different sizes and measure performance

**Module 3: Security & Encryption**  
• Encryption: AES-256-CBC, PBKDF2 key derivation (100k iterations)  
• Limits: 200MB AES limit per file  
• Test: Transfer an encrypted file via HTTPS and validate successful decryption

**Module 4: Clipboard System**  
• Features: Text, image, and small file transfer (max 10MB)  
• Endpoints: `/api/clipboard/add`, `/list`, `/get`, `/remove`  
• Test: Send/paste text and screenshot, verify retrieval and download

**Module 5: Frontend Interface**  
• Technology: HTML, Vanilla JS (no frameworks)  
• Features: Drag-drop, live progress, mobile support, notifications  
• Test: Open web UI on multiple devices, perform upload/download, and observe responsiveness

**Module 6: Config & Analytics**  
• Config Files: `LANVAN_CONFIG`, `LANVAN_STATE`  
• Metrics: Upload/download tracking, memory usage, speed logs  
• Test: Trigger multiple transfers and export logs

**Module 7 : Network Discovery**  
• Features: QR generation, LAN IP auto-fetching, HTTPS/HTTP toggle  
• Test: Scan QR to access server from other devices on LAN

***

#### **3. Document the Results**

| Module | Screenshot / Output | Result |
| --- | --- | --- |
| 1   | Server started, LAN + local IP visible | Working |
| 2   | File uploaded (chunked/direct), download verified | Working |
| 3   | File encrypted & decrypted securely, HTTPS active | Working |
| 4   | Clipboard item added, listed, and retrieved | Working |
| 5   | Frontend responsive with live progress + notifications | Working |
| 6   | Logs exported, stats tracked | Working |
| 7   | QR scanned, device accessed over LAN | Working  |

***

### **Conclusion:**

Hence, We implemented the modules of the Lanvan project.

