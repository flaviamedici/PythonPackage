# Invoice Generator

A Python application that automatically converts Excel invoice files into professionally formatted PDF invoices.

## Overview

This project reads invoice data from Excel (`.xlsx`) files, formats the information into a clean PDF layout, calculates the invoice total, and adds a company logo to each generated invoice.

It is useful for automating invoice creation and eliminating the need to manually create PDF invoices.

## Features

* Converts Excel invoices into PDF format
* Automatically processes multiple Excel files in a folder
* Displays:

  * Invoice number
  * Invoice date
  * Product details
  * Quantity purchased
  * Price per unit
  * Total price
* Calculates the total invoice amount automatically
* Adds a company logo to the invoice
* Creates the output directory automatically if it doesn't exist

## Project Structure

```text
project/
│
├── invoices/
│   ├── 10001-2025.01.01.xlsx
│   ├── 10002-2025.01.02.xlsx
│   └── ...
│
├── output/
│   └── Generated PDF invoices
│
├── invoicing/
│   ├── __init__.py
│   └── invoice.py
│
├── pythonhow.png
├── main.py
└── README.md
```

## Requirements

* Python 3.9+
* pandas
* openpyxl
* fpdf

Install the required packages:

```bash
pip install pandas openpyxl fpdf
```

## Excel File Format

Each invoice should be stored as an Excel file inside the `invoices` folder.

The filename should follow this format:

```text
invoiceNumber-date.xlsx
```

Example:

```text
10001-2025.07.15.xlsx
```

The workbook should contain a worksheet named:

```text
Sheet 1
```

The worksheet must contain the following columns:

| Column           |
| ---------------- |
| product_id       |
| product_name     |
| amount_purchased |
| price_per_unit   |
| total_price      |

Example:

| product_id | product_name | amount_purchased | price_per_unit | total_price |
| ---------- | ------------ | ---------------- | -------------- | ----------- |
| 101        | Keyboard     | 2                | 45             | 90          |
| 102        | Mouse        | 1                | 25             | 25          |

## Usage

Run the application:

```bash
python main.py
```

`main.py` calls the invoice generator:

```python
from invoicing import invoice

invoice.generate(
    "invoices",
    "output",
    "pythonhow.png",
    "product_id",
    "product_name",
    "amount_purchased",
    "price_per_unit",
    "total_price"
)
```

The script will:

1. Search the `invoices` folder for all Excel files.
2. Read each invoice.
3. Generate a formatted PDF.
4. Save the PDF inside the `output` directory.

## Generated PDF

Each PDF contains:

* Invoice number
* Invoice date
* Product table
* Total amount
* Company name
* Company logo

## How It Works

The `generate()` function performs the following steps:

1. Finds every Excel invoice using `glob`.
2. Reads invoice data with **pandas**.
3. Creates a PDF using **FPDF**.
4. Builds a table from the Excel data.
5. Calculates the invoice total.
6. Adds branding (company name and logo).
7. Saves the completed PDF in the output folder.

## Dependencies

* **pandas** – Reads Excel files.
* **openpyxl** – Excel engine used by pandas.
* **FPDF** – Creates PDF documents.
* **glob** – Locates invoice files.
* **pathlib** – Handles file paths.
* **os** – Creates output directories.

## Future Improvements

* Support multiple worksheet names
* Add currency formatting
* Customize fonts and colors
* Email generated invoices automatically
* Add customer information section
* Generate invoice summaries
* Support multiple company logos
* Export to additional formats

## License

This project is available for educational and personal use.
