
## Exp No : 06

### Aim

To estimate cost of the project using constructive cost model (COCOMO) approach for the selected project.

***

### Theory

Since **Lanvan** is a LAN-based file transfer system with:

-   FastAPI backend + WebSocket
    
-   AES-256 encryption + mDNS/QR integration
    
-   Chunked uploads/downloads, clipboard sync, and P2P features
    

This places it in the **Organic Mode** of COCOMO (small team, simple requirements, <50 KLOC).

***

#### Step 1: Estimate KLOC (Thousand Lines of Code)

Lanvan consists of:

-   Backend (FastAPI, validation, encryption, WebSocket)
    
-   Frontend (vanilla JS, HTML, QR handling, logs, GUI)
    
-   Features (chunking, clipboard, P2P prep)
    

**Total Lines of Code:** ~17,132  
**Effective KLOC:** ~12.2 KLOC

***

#### Step 2: Apply COCOMO Organic Model Formulas

**Formulas:**

-   Effort (PM) = 2.4 × (KLOC)^1.05
    
-   Development Time (TDEV in months) = 2.5 × (Effort)^0.38
    
-   Cost = Effort × Cost per Person-Month
    

**Calculation:**

-   Effort = 2.4 × (12.2)^1.05  
    ≈ 2.4 × 13.62  
    ≈ **32.7 Person-Months**
    
-   Development Time = 2.5 × (32.7)^0.38  
    ≈ 2.5 × 2.84  
    ≈ **7.1 months**
    
-   Team Size = Effort / Time = 32.7 / 7.1 ≈ **5 developers**
    

***

#### Step 3: Cost Estimation

Average cost per developer per month (India, mix of junior/mid/senior devs): ≈ **₹75,000 – ₹1,00,000**.  
Taking blended cost from role distribution: **₹54,55,000 total**.

***

### Final COCOMO Estimate for Lanvan Project

-   Effort: ~32.7 Person-Months
    
-   Development Time: ~7.1 months
    
-   Team Size: ~5 developers
    
-   Estimated Cost: ~₹54.55 Lakhs
    

***

### Conclusion

Hence, we have estimated the cost of the project using constructive cost model (COCOMO) approach for the selected project.