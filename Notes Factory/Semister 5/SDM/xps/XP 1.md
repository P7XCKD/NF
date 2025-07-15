

### **Experiment No. 1**

**Aim**: Define the problem statement for the selected project and write activities for the project with relevant software development model(s).

***

#### 1. Project Title

**Secure LAN-Based File Transfer & Chat System (Web App Version)**

***

#### 2. Problem Statement

In locations with limited or no internet access, sharing files and communicating across devices becomes difficult. Existing tools often rely on cloud services, raising concerns about privacy, compatibility, and internet dependency.

This project aims to create a **secure, browser-based LAN system** that enables **file transfer** and **real-time chat** over **Wi-Fi or mobile hotspot**, without internet. A **Flask server** will run on **Android (via Termux) or PC**, offering features like **QR-based connection**, **AES encryption**, and **cross-platform browser support**.

***

#### 3. Selected Software Development Model

**Iterative Model**

***

#### 4. Justification for Selecting Iterative Model

-   Involves **modular features** (file sharing, chat, QR, encryption) that can be built and tested in cycles.
    
-   Requirements are clear, but **UI and platform behavior may evolve** based on testing.
    
-   Supports **progressive refinement** with each iteration.
    
-   Ideal for **cross-device** and **offline-first** systems needing flexibility.
    

***

#### 5. Project Activities (Phase-Wise)

| **Phase** | **Activity Description** |
| --- | --- |
| Requirement Analysis | Identify core features: LAN transfer, chat, QR, browser access, AES encryption. |
| UI/UX Design | Design responsive browser interfaces using HTML, CSS, JS, and Jinja. |
| Backend Setup | Create Flask routes for file transfer, chat (WebSocket), and QR. |
| Android Integration | Use Termux, MacroDroid, or Widget for server start and browser launch. |
| File Transfer Module | Implement upload/download logic with progress and size control. |
| Chat Module | Build real-time messaging using Flask-SocketIO. |
| QR & Security Layer | Generate QR for connection info; add AES-256 file encryption. |
| Testing & Debugging | Test on PC and Android with different browsers and LAN setups. |
| Deployment & Demo | Finalize setup for real use with auto-start and offline guide. |

***

#### Activities Based on Software Development Life Cycle

| **SDLC Phase** | **Activities** |
| --- | --- |
| Requirement Analysis | Define system purpose: secure offline file transfer and chat. Identify components: Flask, HTML/CSS/JS, WebSockets, Termux, LAN. |
| System Design | Design UI mockups. Plan Flask routes (`/upload`, `/chat`, `/qr`, etc.). Define architecture: Flask server + browser client. |
| Implementation | Build Flask server. Implement file and chat logic. Add QR and encryption. Set up Android automation. |
| Testing | Test file sharing and chat between devices. Validate QR and encryption. Use Wi-Fi/hotspot without internet. |
| Deployment | Deploy on Termux/PC. Provide connection via browser or QR. Ensure stable access in lab or classroom. |
| Maintenance | Monitor server and fix issues. Update code. Add features like encryption or chat logs as needed. |

***


**6. Conclusion**  Hence , we successfully defined the problem statement and activities related to it

***
