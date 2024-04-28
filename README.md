# Analyzing Model Vehicle Sales
Yeseul Park

## Executive Summary
Our client is a wholesaler that sells scale-model vehicles to businesses. Using both SQL and Python techniques, I investigated several aspects of the company's operations. Important findings include:
- 10 items are on backorder, all of which have over 150 units on backorder
- *Euro+ Shopping Channel and Mini Gifts Distributors Ltd.* are VIP customers
- Overall revenue appears to be increasing
- Holiday spending has been stagnant over the reported data
- No new customers have been acquired in the past 9 months

I used these findings to develop several recommendations for the company moving forward:
- Limit the amount of backordering permitted, to avoid excessive lack of product
- Host private celebratory/marketing events for the two VIP customers
- Increase marketing efforts around the holiday season - perhaps offer holiday discounts or holiday themed products
- Invest in acquiring new customers

## Introduction
In this SQL-based (SQLite) project, I investigate data provided by a wholesaler that purchases scale-model vehicles (motorcycles, airplanes, vehicles, and trains) from manufacturers and sells them to retailers.

### Company structure
Our client is an international wholesalers of scale-model vehicles that has offices in five countries across four contients. They have 23 employees organized into geographically defined sales groups:
- Europe, Middle East, and Africa (EMEA)
- North America (NA)
- Asia Pacific Region (APAC)
- Japan

With the exception of the Japanese group, each group has a sales manager and a team of sales reps. The Japanese team consists of two sales representatives.
The structure of the company is graphically depicted in *figure 1*.

Figure 1: Company employee heirarchy

With the information presented in the database, I infer that the company is a family-based business, due to the presence of three "Pattersons" and two "Firrellis".

### Market Structure and Outlook
There are about 20 major companies operating within this market, including *Mattel Inc., Amalgam Collection, Hamleys of London Ltd.*, and *Welly Die Casting Factor Ltd.* Together, these companies and others represent a scale-model vehicle market estimated at USD 4.2B in 2023 by Technavio. The consumer market is primarily in the US, EU, and Japan, and is expected to grow by about 6% each year through 2028.

## Exploring the Database
The database conssists of 8 tables, as shown in *figure 2*. These gtables are of varying size (*table 1*), with the largest table containing the order details *5 attributes, 2,996 rows) and the smallest table containing information about the product lines (4 attributes, 7 rows).

Figure 2: Database Schema

Table 1: Relative shapes of the individual tables

### Individual Table Descriptions
Each table serves the general purpose described below:
- customers contains customer identifying information and links to the employees, payments, and orders tables
- employees contains employee indentifying information. It contains self-references providing the company heirarchy, and references the offices table as well as the customers table
- offices contains office contact information and only links to the employees table
- orderdetails contains line item detail for each of the orders, including the specific item ordered, the quantity, the unit price, and the order line number. It links to the products and orders table
- orders contains timing-related and identifying information for each of the orders, and it provides a section for free-text comments. It links to the orderdetails and customers tables
