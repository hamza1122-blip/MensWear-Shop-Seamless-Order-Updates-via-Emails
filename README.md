# 👕 MensWear Shop – n8n AI Automation Workflow  

> **Automating Customer Communication with Smart Workflow Intelligence**  

---

## 🚀 Overview  

The **MensWear Shop Automation Workflow** simplifies order management by automatically reading order details from a **Google Sheet** and sending customers the appropriate email updates according to their order status.  
Delivered orders are skipped, while customers with other statuses (such as *Processing, Returned, Cancelled,* or *Refund Request*) receive automated email updates.  

---

## 🧩 Workflow Structure  

The automation is created using **n8n**, and it follows this logical flow:

1. **Trigger:**  
   The workflow starts manually by clicking **"Execute Workflow"** in n8n.

2. **Read Data from Google Sheet:**  
   The Google Sheets node reads customer information including:
   - Customer ID  
   - Customer Name  
   - Email  
   - Phone Number  
   - Order Status  
   - Date  
   - Product  

3. **Filter Node:**  
   The workflow filters out all rows where the order status is **“Delivered”** to ensure only pending or actionable statuses are processed.

4. **Switch Node:**  
   The Switch node routes the remaining orders based on their **Order Status**, allowing for specific actions and delays for each type:
   - **Order Returned** → Wait 10s → Send Email  
   - **Order Cancelled** → Wait 3s → Send Email  
   - **Refund Request** → Wait 6s → Send Email  
   - **Order Processing** → Wait 15s → Send Email  

5. **Email Notifications:**  
   Each email is sent through a **Gmail Node** using customized templates that correspond to each order status.  

---

## 🗂️ Google Sheet Data  

The Google Sheet serves as the workflow’s data source.  
Below are the key columns used:

| Column | Description |
|--------|-------------|
| Customer ID | Unique ID for each customer |
| Customer Name | Name of the customer |
| Email | Customer email address |
| Phone | Customer contact number |
| Order Status | Current order stage (Processing, Returned, Cancelled, Refund, Delivered) |
| Date | Order date |
| Product | Product name and variant |

📊 Example Google Sheet:  
*(See attached screenshot `MensWear Shop Sheet`)*  

---

## ⚙️ Workflow Diagram  

Below is the visual representation of the workflow in n8n:

1. **When clicking ‘Execute Workflow’**  
2. **Get rows from Google Sheet**  
3. **Filter (Exclude Delivered)**  
4. **Switch (Based on Order Status)**  
5. **Wait Nodes (Delay before sending email)**  
6. **Gmail Nodes (Send Status-Based Emails)**  

📸 Example Workflow:  
*(See attached screenshot `MensWear Shop Workflow`)*  

---

## 🧠 Logic Summary  

- ✅ Skip all **Delivered** orders  
- ✉️ Automatically send personalized emails for:  
  - Processing  
  - Order Cancelled  
  - Order Returned  
  - Refund Request  
- 🕓 Include wait times before sending each email to ensure proper sequencing  

---

## 🧰 Tools & Technologies  

- **n8n** – Workflow Automation Platform  
- **Google Sheets** – Customer Data Source  
- **Gmail API** – Email Sending Integration  
- **Google Cloud** – Authentication for Sheets and Gmail  
- **Custom Filters and Switch Nodes** – For order-based routing logic  

---

## 📈 Use Case  

This automation can be integrated into any **e-commerce workflow** where order updates are managed via Google Sheets. It saves time, ensures timely customer communication, and reduces manual tracking.  

---

## 💬 Tagline Options  

- **Automating Customer Communication with Smart Workflow Intelligence**  
- **Seamless Order Updates — Powered by n8n Automation**  
- **AI-Driven Order Management for Modern E-Commerce**  
- **From Google Sheets to Smart Email Automation**  
- **Automate. Inform. Engage. — Smarter Order Tracking Made Simple**  
- **Smart Automation for Effortless Order Status Updates**  
- **Turn Your Customer Data into Automated Communication**

---

## 🧑‍💻 Author  

**Hamza Zafar**  
- WordPress & Web Automation Developer  
- Founder at **XpertsWP**  
- 💼 Expertise: WordPress, Elementor, Divi, and Automation Workflows  

---

## 💡 Future Enhancements  

- Add dynamic email templates with customer names and products  
- Integrate automatic order updates from WooCommerce or Shopify  
- Include SMS notifications using Twilio or WhatsApp API  

---

## 🏁 How to Use  

1. Clone the repository  
2. Import the workflow JSON file into n8n  
3. Connect your Google Sheets and Gmail credentials  
4. Update the Sheet ID and email templates  
5. Execute the workflow manually or schedule it with Cron  

---
