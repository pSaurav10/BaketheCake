# BaketheCake

📘 Project Report: Invoice Reader & Prediction System
1. Objective

The goal of this project is to build a custom system that:

Reads invoices in PDF format.

Extracts customer details and product orders.

Stores the extracted data in a structured SQL database.

Automatically updates the database when new invoices or customers appear.

Uses historical data to provide sales predictions and demand forecasting.

2. System Workflow

Input

A new invoice file in PDF format is provided to the system.

Data Extraction

The system reads the invoice.

It identifies customer information, order date, product codes, quantities, and prices.

Database Update

If the customer already exists in the database → reuse the existing record.

If it is a new customer → add the customer to the database.

If the product already exists → reuse the existing product record.

If it is a new product → add it to the product database.

The order and order items are then saved in the database.

Storage

All information is stored in a SQL database (SQLite for simplicity).

The database holds four types of information:

Customers

Products

Orders

Order Items

Analysis & Predictions

Over time, the stored data builds up a history of customer orders.

The system uses this history to:

Forecast demand for specific products.

Predict customer buying behavior.

Identify sales trends.

3. Database Design

The database contains the following tables:

Customers → Stores customer details.

Products → Stores product codes and descriptions.

Orders → Stores each order, linked to a customer and a date.

Order Items → Stores products within each order, including quantity and price.

4. System Features

Automatic Updates:
Every time a new invoice is processed, the database is automatically updated.

Customer Tracking:
New customers are added automatically, existing ones are reused.

Product Tracking:
New products are added automatically, existing ones are reused.

Data History:
Each invoice adds to the system’s historical record, building a dataset for analysis.

Predictions:
The system can forecast product demand, sales trends, and customer order patterns.

Reporting:
Data can be visualized through notebooks or dashboards for easy interpretation.

5. Usage Flow

Place a new invoice file in the system.

Run the processing pipeline.

The invoice is read and relevant data extracted.

The database is updated with any new customers, products, and orders.

Over time, predictions and reports are generated from the stored data.

6. Future Enhancements

Automate the pipeline so that it monitors a folder for new invoices and updates the database in real time.

Add product recommendation features (e.g., “customers who bought X also bought Y”).

Improve parsing rules for different invoice formats.

Create a user-friendly dashboard with search, filters, and charts.

7. Benefits

Saves time by eliminating manual entry of invoices.

Builds a structured historical record of orders.

Provides valuable insights into customer behavior and sales trends.

Fully custom and free, based entirely on open-source tools.