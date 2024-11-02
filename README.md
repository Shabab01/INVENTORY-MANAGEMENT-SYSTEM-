# Inventory Management System

![WhatsApp Image 2024-11-02 at 20 08 09_5435a983](https://github.com/user-attachments/assets/607f880f-fd87-4698-9e21-feed7c4224b2)

A comprehensive SQL-based inventory management system that organizes, manages, and analyzes inventory and sales data. The project includes structured tables for categories, products, and sales data, and provides valuable insights on sales performance across different product categories.

## Project Overview

The **Inventory Management System** database was designed to streamline inventory tracking and sales performance analysis. This system is suitable for retail businesses or warehouses looking to maintain organized data on products, their categories, and sales history. Key features include the ability to track total sales, analyze product performance by category, and support decision-making with insights derived from SQL queries.

## Database Schema

The database consists of three main tables:
1. **Categories**: Stores information on different product categories.
2. **Product**: Contains details on individual products, their prices, and category associations.
3. **Sales**: Tracks transactions including quantity sold, sale dates, and product IDs.

## Key Features

- **Category-based Sales Reports**: Calculates the total quantity sold and sales revenue for each product category.
- **Product Price and Quantity Tracking**: Provides current price and quantity available for each product.
- **Sales Data Analysis**: Facilitates analysis of sales performance over time, identifying high-performing categories and products.
  
## Table Details

### Categories Table

| Column           | Data Type | Description                         |
|------------------|-----------|-------------------------------------|
| `Category_id`    | INT       | Primary key for category           |
| `Category_Name`  | VARCHAR   | Name of the category               |

### Product Table

| Column           | Data Type | Description                         |
|------------------|-----------|-------------------------------------|
| `Product_id`     | INT       | Primary key for product            |
| `Category_id`    | INT       | Foreign key linked to Categories   |
| `Product_Name`   | VARCHAR   | Name of the product                |
| `Unit_Price`     | DECIMAL   | Price per unit                     |

### Sales Table

| Column           | Data Type | Description                         |
|------------------|-----------|-------------------------------------|
| `Sale_id`        | INT       | Primary key for sale               |
| `Product_id`     | INT       | Foreign key linked to Product      |
| `QuantitySold`   | INT       | Number of units sold               |
| `Sale_Date`      | DATE      | Date of the sale transaction       |

## Setup and Usage

1. **Clone the repository**:
   ```bash
   git clone https://github.com/yourusername/inventory-management-system.git
   ```

2. **Import the SQL file**: Use a MySQL or PostgreSQL client to execute `Inventory_management_db.sql` and create the database tables.

3. **Run Example Queries**: Once the database is set up, try running some of the example queries below.

## Example Queries

Here are some example queries to help you get started:

1. **Total Quantity Sold and Sales Value by Category**
   ```sql
   SELECT 
       Categories.Category_Name,
       SUM(Sales.QuantitySold) AS Total_Quantity_Sold,
       SUM(Sales.QuantitySold * Product.Unit_Price) AS Total_Sales_Value
   FROM 
       Sales
       JOIN Product ON Sales.Product_id = Product.Product_id
       JOIN Categories ON Product.Category_id = Categories.Category_id
   GROUP BY 
       Categories.Category_Name;
   ```

2. **Top 5 Best-Selling Products**
   ```sql
   SELECT 
       Product.Product_Name,
       SUM(Sales.QuantitySold) AS Total_Quantity_Sold
   FROM 
       Sales
       JOIN Product ON Sales.Product_id = Product.Product_id
   GROUP BY 
       Product.Product_Name
   ORDER BY 
       Total_Quantity_Sold DESC
   LIMIT 5;
   ```

## Future Enhancements

- **User Access Controls**: Implement role-based access for data security.
- **Inventory Alerts**: Add automated alerts for low-stock items.
- **Data Visualization**: Integrate visual reporting tools like Power BI or Tableau.

## Contributing

Feel free to fork this repository, create new branches for features or fixes, and submit a pull request with your improvements.
