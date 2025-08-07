### **Experiment No. 2**

**Aim**: To prepare SRS Document for the selected project


**Project Title:** Secure LAN-Based File Transfer & Chat System
### **1. Introduction**

This Software Requirements Specification (SRS) document describes the functionalities, features, and constraints of the _Secure LAN-Based File Transfer & Chat System_. The system is designed to enable file sharing and communication over a local area network (LAN), functioning without internet access. It ensures fast, secure, and private data transfer between devices using a web-based user interface.

***

#### **1.1 Purpose**

The purpose of this project is to develop a **secure, offline-first file transfer and communication system** that runs on any device (Android or PC) over a local Wi-Fi or hotspot network. It allows users to upload/download files, share clipboard content, and optionally chat, all from within a browser. It is powered by a Python-based backend (FastAPI) and works seamlessly on Android using Termux or on a desktop using a local server.

***

#### **1.2 Scope**

The system is ideal for:

-  file sharing for casual use
    
-   Labs or development teams
    
-   Secure communication in local networks
    
-   Situations where internet is unavailable or restricted
    

The system runs directly on Android (via Termux) or PC, requires no cloud services, and supports cross-platform browser access. Advanced optional features include LAN-based chat, multi-file transfer, encryption, and QR-based smart device pairing.

***

#### **1.3 Intended Audience**

This document is intended for:

-   Users working on network-based utility tools
    
-   Developers and testers designing local web applications
    
-   Evaluators and academic reviewers assessing secure communication systems
    
-   Users seeking portable offline file sharing and chat solutions
    

***

### **2. Overall Description**

#### **2.1 Product Perspective**

The system is a **standalone LAN web application** that runs on a FastAPI backend.  
Key elements include:

-   Backend server with FastAPI (Python)
    
-   Static frontend with HTML/CSS/JS
    
-   LAN connectivity via IP/QR code
    
-   File and clipboard sharing over HTTP
    
-   Optional real-time chat via WebSockets
    
-   Android and PC compatibility (runs via Termux or native Python)
    

***

#### **2.2 Product Features**

-   Offline file upload and download between devices
    
-   Real-time clipboard text sharing
    
-   Local WebSocket-based LAN chat (optional)
    
-   AES-256 encrypted file transfer (optional)
    
-   QR-based smart connection with device info
    
-   Auto-start via MacroDroid or shortcut on Android
    
-   Cross-device browser support (mobile or desktop)
    
-   Lightweight, portable, and cloud-free
    

***

#### **2.3 User Characteristics**

Users are expected to:

-   Have basic knowledge of Wi-Fi networking and browsers
    
-   Be able to connect to a local hotspot or router-based LAN
    
-   Know how to run Python on Android (via Termux) or PC  
    No coding knowledge is required for using the system post-setup.
    

***

#### **2.4 Constraints**

-   Requires LAN connectivity (Wi-Fi or hotspot)
    
-   Does not support public internet or NAT traversal
    
-   Android version requires Termux, permissions, and optional automation app
    
-   No third-party cloud storage integration
    
-   File size limited by available RAM and configured server settings
    
-   Encryption feature optional due to processing limitations on low-end phones
    

***

### **3. Specific Requirements**

#### **3.1 Functional Requirements**

-   The system shall allow file uploads via web interface.
    
-   The system shall serve uploaded files for download to any LAN-connected client.
    
-   The system shall support clipboard text sharing between devices.
    
-   The system shall generate a QR code for LAN IP and port to assist quick connection.
    
-   The system shall run an HTTP server on Android via Termux or PC via Python.
    
-   The system shall auto-start and open browser via MacroDroid (Android only).
    
-   The system may optionally support LAN chat via WebSocket (Phase 3).
    
-   The system may optionally support AES-256 encryption for file transfer.
    

***

#### **3.2 Non-Functional Requirements**

-   The system shall be offline-first and fully functional without internet.
    
-   The system shall load quickly and perform well on low-end devices.
    
-   The web UI shall be responsive and mobile-friendly.
    
-   The backend shall support buffered streaming for large file downloads.
    
-   The system shall use platform-specific production WSGI servers (Waitress on Android, Gunicorn on PC).
    
-   Encryption and chat features shall be optional and toggled via config.
    


***

#### **3.3 Hardware Requirements**

-   Android smartphone with Termux installed (for mobile hosting)
    
-   Windows/Linux PC with Python 3.10+ (for desktop hosting)
    
-   Wi-Fi hotspot or router for LAN access
    
-   Optional: MacroDroid or Shortcut Creator for automation
    
-   USB/battery power supply for Android runtime
    

***

#### **3.4 Software Requirements**

-   Python 3.10+ with FastAPI, Uvicorn, and dependencies
    
-   Termux app with required packages (`python`, `pip`, `openssl`)
    
-   Internet browser (Chrome, Firefox, Edge, etc.) for UI access
    
-   MacroDroid or Termux Widget (Android) for server automation
    
-   QR code scanner (for joining from another device)
    
-   Optional: OpenSSL for HTTPS, `cryptography` package for AES
    

**Conclusion**: Hence , We successfully prepared SRS document for the selected project


