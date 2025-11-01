Retail Sales Data Analysis and Visualization Using Pandas
Submitted by: Avinash Kumar Singh
Date: October 30, 2025
This project is a hands-on exercise in using Pandas, a popular Python tool for handling data, to analyze and visualize fake retail sales data. Imagine you're a store manager looking at sales records to spot trends—like which products sell best in different areas or how payments affect totals. We start by setting up the tools, create a sample dataset, explore it, run some quick checks, filter for insights, group data for summaries, make a summary table, and end with charts to make everything visual and easy to understand.
1. Setting Up the Tools
First, we quietly install the needed Python packages: Pandas for data handling, Matplotlib and Seaborn for charts, and OpenPyXL for reading Excel files if needed. Then, we import them:

Pandas as "pd" (for data frames, like spreadsheets).
NumPy as "np" (for random numbers and math).
Matplotlib's pyplot as "plt" (for basic plots).
Seaborn as "sns" (for fancier charts).
We also set up inline plotting so charts show right in the notebook and apply a clean grid style for better looks.

2. Building a Fake Sales Dataset (100 Rows)
To practice without real data, we create a simple sales log with 100 made-up orders. We set a random seed (999) so the results are the same every time we run it.
Key details in the dataset:

Products: Randomly picked from Laptop, Mouse, Keyboard, Monitor, or Headset.
Regions: North, South, East, or West.
Payments: Cash, Card, or UPI.

The data includes:

Order ID: Numbers from 1001 to 1100.
Product: Random choice from the list above.
Region: Random from the regions.
Quantity: Random integers from 1 to 10 per order.
Unit Price: Random prices between 150 and 2500 (rounded to 2 decimals).
Payment: Random from the payment options.
Order Date: Dates starting January 1, 2024, spread over 100 days.

We turn this into a Pandas DataFrame (like a table) called "df" and add a new column "Total" by multiplying Quantity times Unit Price for each row. Finally, we peek at the first few rows with df.head() to see it looks right.
3. Getting to Know the Data
To understand our dataset:

df.head(10) shows the top 10 rows.
df.tail() shows the last 5 rows.
df.info() gives basics like data types and missing values.
df.describe().round(2) summarizes numbers: averages, min/max, etc., rounded nicely.
We print the shape (100 rows, 8 columns) and list all column names: ['OrderID', 'Product', 'Region', 'Quantity', 'UnitPrice', 'Payment', 'OrderDate', 'Total'].

4. Counting Common Items
Quick counts to see what's popular:

df['Product'].value_counts(): How many orders for each product (e.g., Laptops might top the list).
df['Region'].value_counts(): Orders per region (roughly even since it's random).

5. Narrowing Down the Data
Filtering lets us zoom in:

High-value orders: high_val = df[df['Total'] > 10_000] grabs rows where total exceeds 10,000, then high_val.head() shows the top ones (big spends on pricey items like laptops).
East region orders: df[df['Region'] == 'East'].shape tells us how many (about 25, since random).

6. Grouping and Summarizing
Group data to find patterns:

By region: df.groupby('Region')['Total'].agg(['mean','sum','count']).round(2)—average, total, and count of sales per region.
By product: df.groupby('Product')['Quantity'].mean().round(2)—average quantity sold per product type.

7. Creating a Summary Table
A pivot table is like a customizable spreadsheet summary: df.pivot_table(values='Total', index='Region', columns='Payment', aggfunc='sum', fill_value=0).round(2). This shows total sales by region (rows) and payment type (columns), filling empty spots with 0.
8. Making Charts for Easy Insights
Visuals turn numbers into pictures:

Bar Chart: Total Sales by Region
Sum totals per region, plot as bars in teal color. Title: "Total Sales by Region". Labels: Revenue on y-axis. No rotation on x-labels. This shows which area brings in the most money.
Histogram: Quantity Distribution
Shows how often different quantities (1-10) appear, in salmon color with black edges. Title: "Distribution of Order Quantities". X: Quantity, Y: Frequency. Great for seeing if most orders are small (e.g., 1-3 items).
Scatter Plot: Unit Price vs. Total
Dots for each order's price vs. total, semi-transparent purple. Title: "Unit Price vs Order Total". X: Unit Price, Y: Total. Spots clusters—like high-price items driving big totals.
Box Plot: Total by Payment Method
Using Seaborn: Boxes show revenue spread (medians, outliers) for Cash/Card/UPI. Palette: Set2 colors. Title: "Total Revenue by Payment Method". Reveals if one method leads to bigger spends.
Line Chart: Monthly Sales Trend
Resample totals by month from OrderDate, plot as line with orange dots. Title: "Monthly Sales Trend". Y: Revenue. Tracks if sales grow or dip over the year.

Wrapping Up
This practical covers all the basics: viewing data (head/tail/info/describe), counting (value_counts), selecting (filtering), summarizing (groupby), and tabling (pivot_table). We used a fresh, random dataset and created clean, ready-to-share charts. It's a solid start for anyone analyzing sales—like spotting East region's potential or pushing card payments for higher totals!
