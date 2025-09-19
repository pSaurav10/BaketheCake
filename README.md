# 📦 Invoice Reader & Reporting System

## 1. Overview
This project is a **fully custom, free system** that:

1. Reads invoices in PDF format.
2. Extracts customer details, product codes, quantities, and prices.
3. Stores the data in a **SQL database** (SQLite).
4. Automatically updates the database when new invoices or customers appear.
5. Allows users to **view historical orders** and **generate analytics reports**.
6. Uses historical data to provide **sales forecasts and trend analysis**.

---

## 2. System Workflow

### Step 1: Invoice Processing
- A new invoice PDF is provided to the system.
- The system extracts:
  - Customer name and contact details
  - Order date
  - Product codes, quantities, and prices

### Step 2: Database Update
- Checks if the customer exists → adds new customer if necessary.
- Checks if the product exists → adds new product if necessary.
- Adds the new order and order items.

### Step 3: Historical Orders
- Users can view past orders per customer, product, or date range.
- Displays quantities, prices, and order details.

### Step 4: Reporting & Analytics
- Summaries and charts for:
  - Total sales per customer, product, or month
  - Top-selling products
  - Monthly or seasonal sales trends
- Generates forecasts for future product demand and sales trends.

---

## 3. Database Design
The system uses a **SQLite database** with four main tables:

- **Customers** → Customer details
- **Products** → Product codes and descriptions
- **Orders** → Orders with customer and date
- **Order Items** → Products within each order, including quantity and price

The database automatically updates whenever a new invoice is processed.

---

## 4. System Features

- **Automatic Updates**: New invoices are parsed and database updated without manual edits.
- **Customer & Product Tracking**: New entries are added automatically; existing entries are reused.
- **Historical Data Access**: View past orders with filtering options.
- **Reporting & Analytics**: Summaries, charts, and forecasts for sales and demand.
- **Interactive Dashboard** (optional): Filter by customer, product, date range, and export reports.

---

## 5. Usage Flow

1. Place a new invoice in the system.
2. Run the ETL pipeline to extract and store data.
3. Use reporting tools to view orders or generate analytics.
4. Dashboard (optional) updates dynamically to reflect new data.

---

## 6. Benefits

- Saves time by eliminating manual entry.
- Maintains a structured historical record of all orders.
- Provides insights into customer behavior and product trends.
- Enables forecasting and data-driven decision-making.
- Fully open-source and customizable to your business needs.

---

## 7. Future Enhancements

- Monitor a folder for new invoices and process automatically.
- Add product recommendation engine (e.g., “customers who bought X also bought Y”).
- Improve parsing for various invoice formats.
- Enhance dashboard with advanced charts, filters, and export options.
- Integrate with email or notification system to alert for new orders.

---

## 8. Suggested Tech Stack

- **Python 3** → Core language for parsing, database, and analysis
- **pdfplumber / pytesseract** → PDF and OCR parsing
- **SQLite** → Free, lightweight database
- **pandas / matplotlib / seaborn** → Data processing and visualization
- **Streamlit** → Interactive dashboard (optional)
- **Prophet / scikit-learn** → Predictions and forecasting

---

It is:
- Capable of tracking customers, products, and orders automatically.
- Equipped with historical data analysis, visualizations, and sales forecasts.
- Ready for expansion with dashboards, alerts, and advanced analytics.

---

invoice_system/
│
├── data/                  # Store invoice PDF files
│
├── db/                    # Database files
│   └── orders.db
│
├── scripts/               # Core Python scripts
│   ├── parse_invoice.py   # Extracts data from invoices
│   ├── db.py              # Database helper functions
│   ├── etl.py             # End-to-end processing pipeline
│   ├── predict.py         # Forecasting & prediction models
│   └── dashboard.py       # Optional Streamlit dashboard
│
├── notebooks/             # Jupyter notebooks for analysis
│
├── requirements.txt       # Python dependencies
│
└── README.md              # Project documentation

---

+-------------------+
          |   Invoice PDF     |
          +-------------------+
                   |
                   v
          +-------------------+
          |   PDF Parsing     |
          | (extract data)    |
          +-------------------+
                   |
                   v
          +-------------------+
          | Database Update   |
          | - Customers       |
          | - Products        |
          | - Orders          |
          | - Order Items     |
          +-------------------+
                   |
         ---------------------
         |                   |
         v                   v
+-------------------+   +-------------------+
| Historical Orders |   | Reporting &       |
| Viewer            |   | Analytics         |
+-------------------+   | - Summaries       |
                        | - Charts          |
                        | - Forecasts       |
                        +-------------------+


---

[New Invoice Folder]
        |
        v
[Folder Monitor Service] (detects new PDFs)
        |
        v
[ETL Pipeline] (parse & update DB)
        |
        +----------------+
        |                |
        v                v
[Dashboard Update]   [Prediction Models]
        |                |
        v                v
[Interactive Reports]   [Demand Forecasts]