# README


# contoso

Contoso is a synthetic dataset containing sample sales transaction data
for the fictional “Contoso” company. It includes various supporting
tables for business intelligence, such as customer, store, product, and
currency exchange data.

You can either load the datasets directly or use the function
`create_contoso_duckdb()` to create a DuckDB database that contains the
following tables:

- **sales**:
  - Contains information about sales transactions, including the total
    sales amount, customer, store, and product involved.
- **customer**:
  - Contains details about customers, such as customer key, name,
    address, and demographic information.
- **store**:
  - Contains information about stores, including store key, name,
    location, and related details.
- **product**:
  - Contains information about products, such as product key, name,
    category, and price.
- **fx**:
  - Contains foreign exchange rate data, mapping currency pairs to their
    exchange rates on specific dates.
- **date**:
  - Contains date-related information, including date, week, month,
    quarter, and year for use in time-based analysis.
- **order**:
  - Contains information about individual orders, including order key,
    customer key, order date, and store information.
- **orderrows**:
  - Contains detailed line items for each order, including product key,
    quantity, and price for each item in the order.

The Contoso dataset is a fictional set of data created by Microsoft. It
is commonly used for educational and demonstration purposes to showcase
various features of data analysis, business intelligence tools, and data
processing techniques

This dataset is perfect for practicing time series analysis, financial
modeling, or any business intelligence-related tasks.

The data is sourced from the
[sqlbi](https://github.com/sql-bi/Contoso-Data-Generator-V2-Data/releases/tag/ready-to-use-data)
github site

## Dataset overview

![Contoso Overview](fig/contoso_schema.svg)

The relationship keys that join each of the tables are listed below.

| sales         | customer     | product     | store     | order        | orderrows   | fx            |
|---------------|--------------|-------------|-----------|--------------|-------------|---------------|
| order_key     |              |             |           | order_key    | order_key   |               |
| customer_key  | customer_key |             |           | customer_key |             |               |
| store_key     |              |             | store_key | store_key    |             |               |
| product_key   |              | product_key |           |              | product_key |               |
| currency_code |              |             |           |              |             | from_currency |

## Installation

You can install the development version of contoso from
[GitHub](https://github.com/alejandrohagan/contoso) with:

``` r
# install.packages("pak")
pak::pak("alejandrohagan/contoso")
```

## Example

This is a basic example which shows you how to solve a common problem:

``` r
library(contoso)

# Create a DuckDB database containing Contoso datasets
contoso_db <- create_contoso_duckdb(dir = "temp")

# Access the sales dataset from the database
sales_data <- contoso_db$sales
```

## Features

- Realistic Sales Data: Simulates a variety of sales transactions,
  customer details, store locations, and product information.
- Multiple Data Tables: Supports multiple tables like sales, customers,
  store details, product catalog, exchange rates, and time-series
  information.
- Easy-to-Use: Load and use data directly or create a full DuckDB
  database for seamless analysis with create_contoso_database().
