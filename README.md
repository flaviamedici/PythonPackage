# Invoice Generator

A lightweight Python package that converts Excel invoice files (`.xlsx`) into professionally formatted PDF invoices.

Whether you're automating invoice generation for a small business or learning how to package Python libraries, this project demonstrates how to process Excel files, generate PDFs, and distribute a reusable Python package.

---

## Features

* 📄 Convert Excel invoices into PDF invoices
* 📁 Process multiple invoices in a single run
* 🧾 Automatically calculate invoice totals
* 🏷️ Display invoice number and invoice date
* 📦 Generate product tables from Excel data
* 🖼️ Add company branding with a logo
* 📂 Automatically create the output directory
* 📚 Can be used as a standalone application or installed as a Python package

---

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
├── setup.py
└── README.md
```

---

## Requirements

* Python 3.8+
* pandas
* openpyxl
* fpdf

Install the dependencies:

```bash
pip install pandas openpyxl fpdf
```

or install directly from the package after publishing:

```bash
pip install invoicing
```

---

## Excel File Format

The application expects invoice files inside an `invoices` directory.

Each filename should follow the format:

```text
invoiceNumber-date.xlsx
```

Example:

```text
10001-2025.07.15.xlsx
```

The workbook must contain a worksheet named:

```text
Sheet 1
```

### Required Columns

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

---

# Using the Project

Run the application:

```bash
python main.py
```

The application calls:

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

---

## Function Parameters

The `generate()` function accepts the following parameters:

| Parameter          | Description                           |
| ------------------ | ------------------------------------- |
| `invoices_path`    | Directory containing Excel invoices   |
| `pdfs_path`        | Output directory for generated PDFs   |
| `image_path`       | Company logo displayed on the invoice |
| `product_id`       | Excel column containing product IDs   |
| `product_name`     | Excel column containing product names |
| `amount_purchased` | Excel column containing quantities    |
| `price_per_unit`   | Excel column containing unit prices   |
| `total_price`      | Excel column containing total prices  |

---

## Example Output

Each generated PDF contains:

* Invoice number
* Invoice date
* Product table
* Total invoice amount
* Company name
* Company logo

The PDFs are automatically saved inside the output directory.

---

## How It Works

The package performs the following steps:

1. Searches the invoice directory for all Excel files.
2. Reads each invoice using **pandas**.
3. Creates a new PDF using **FPDF**.
4. Builds a formatted invoice table.
5. Calculates the invoice total.
6. Adds company branding.
7. Exports the invoice as a PDF.

---

## Dependencies

| Library  | Purpose                     |
| -------- | --------------------------- |
| pandas   | Read Excel spreadsheets     |
| openpyxl | Excel engine used by pandas |
| FPDF     | Generate PDF documents      |
| glob     | Locate invoice files        |
| pathlib  | Handle file paths           |
| os       | Create output directories   |

---

# Packaging for PyPI

This project is structured as a reusable Python package and can be published to PyPI.

## Before Publishing

Remove the following files and folders from the package:

* `invoices/`
* `output/`
* `main.py`
* `pythonhow.png`

These files are only needed for the example application.

---

## Create a PyPI Account

Create an account at:

https://pypi.org/

---

## Build the Package

Install setuptools if needed:

```bash
pip install setuptools
```

Build the distribution:

```bash
python setup.py sdist
```

A `dist/` folder will be created containing the source distribution.

---

## Upload to PyPI

Install Twine:

```bash
pip install twine
```

Upload the package:

```bash
twine upload --skip-existing dist/*
```

You'll be prompted for your PyPI username and password.

---

## Install Your Package

Once published, anyone can install the package using:

```bash
pip install <package-name>
```

Example:

```bash
pip install invoicing
```

---

## Supported Python Versions

According to the package configuration, this library supports:

* Python 3.8
* Python 3.9
* Python 3.10
* Python 3.11

---

## Future Improvements

* Support multiple worksheet names
* Currency formatting
* Multiple page invoices
* Customer and billing information
* Invoice templates
* Automatic invoice numbering
* Email generated invoices
* QR code support
* Barcode support
* Custom fonts and themes
* Export to additional file formats

---

## License

This project is licensed under the **MIT License**.

See the `LICENSE` file for more information.
