👕 MensWear Shop – n8n AI Automation Workflow

This project demonstrates an AI-powered automation workflow built using n8n to manage and streamline communication for a menswear e-commerce store.
The workflow integrates Google Sheets as a customer data source and automates email notifications based on each customer’s order status.

🚀 Overview

The MensWear Shop Automation Workflow simplifies order management by automatically reading order details from a Google Sheet and sending customers the appropriate email updates according to their order status.
Delivered orders are skipped, while customers with other statuses (such as Processing, Returned, Cancelled, or Refund Request) receive automated email updates.

🧩 Workflow Structure

The automation is created using n8n, and it follows this logical flow:

Trigger:
The workflow starts manually by clicking "Execute Workflow" in n8n.

Read Data from Google Sheet:
The Google Sheets node reads customer information including:

Customer ID

Customer Name

Email

Phone Number

Order Status

Date

Product

Filter Node:
The workflow filters out all rows where the order status is “Delivered” to ensure only pending or actionable statuses are processed.

Switch Node:
The Switch node routes the remaining orders based on their Order Status, allowing for specific actions and delays for each type:

Order Returned → Wait 10s → Send Email

Order Cancelled → Wait 3s → Send Email

Refund Request → Wait 6s → Send Email

Order Processing → Wait 15s → Send Email

Email Notifications:
Each email is sent through a Gmail Node using customized templates that correspond to each order status.

🗂️ Google Sheet Data

The Google Sheet serves as the workflow’s data source.
Below are the key columns used:

Column	Description
Customer ID	Unique ID for each customer
Customer Name	Name of the customer
Email	Customer email address
Phone	Customer contact number
Order Status	Current order stage (Processing, Returned, Cancelled, Refund, Delivered)
Date	Order date
Product	Product name and variant

📊 Example Google Sheet:
(See attached screenshot MensWear Shop Sheet)

⚙️ Workflow Diagram

Below is the visual representation of the workflow in n8n:

When clicking ‘Execute Workflow’

Get rows from Google Sheet

Filter (Exclude Delivered)

Switch (Based on Order Status)

Wait Nodes (Delay before sending email)

Gmail Nodes (Send Status-Based Emails)

📸 Example Workflow:
(See attached screenshot MensWear Shop Workflow)

🧠 Logic Summary

✅ Skip all Delivered orders.

✉️ Automatically send personalized emails for:

Processing

Order Cancelled

Order Returned

Refund Request

🕓 Include wait times before sending each email to ensure proper sequencing.

🧰 Tools & Technologies

n8n – Workflow Automation Platform

Google Sheets – Customer Data Source

Gmail API – Email Sending Integration

Google Cloud – Authentication for Sheets and Gmail

Custom Filters and Switch Nodes – For order-based routing logic

📈 Use Case

This automation can be integrated into any e-commerce workflow where order updates are managed via Google Sheets. It saves time, ensures timely customer communication, and reduces manual tracking.

📸 Screenshots

Workflow in n8n:


Google Sheet Data:


🧑‍💻 Author

Hamza Zafar

WordPress & Web Automation Developer

Founder at XpertsWP

💼 Expertise: WordPress, Elementor, Divi, and Automation Workflows

💡 Future Enhancements

Add dynamic email templates with customer names and products.

Integrate automatic order updates from WooCommerce or Shopify.

Include SMS notifications using Twilio or WhatsApp API.

🏁 How to Use

Clone the repository.

Import the workflow JSON file into n8n.

Connect your Google Sheets and Gmail credentials.

Update the Sheet ID and email templates.

Execute the workflow manually or schedule it with Cron.
