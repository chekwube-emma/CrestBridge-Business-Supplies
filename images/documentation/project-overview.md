Project Overview
CrestBridge Business Supplies is a fictional Nigerian B2B distribution company operating across Lagos, Abuja and Port Harcourt.
The company supplies business and office-related products including office furniture, office supplies, presentation equipment and technology products to Corporate, SME and Retail customers.
The dataset covered transactions from January to June 2026 and included information on sales, customer payments, products, branches, costs and outstanding balances.
The objective of the project was to develop an end-to-end business intelligence and reporting solution that would give management a clearer view of business performance and support more informed decision-making.
The analysis was designed to answer key management questions including:
How much valid sales revenue had been generated?
How much of that revenue had actually been collected?
How much remained outstanding?
Which branches were performing above or below expectations?
Which branches were meeting their collection targets?
Which products and product categories generated the strongest sales and profitability?
Which customer segments represented the greatest receivables risk?
Which customers required the most urgent collection attention?
How old were outstanding receivables?
How was sales performance changing over time?
The goal was therefore not simply to create a Power BI dashboard.
The project was designed as a complete reporting solution that transformed raw transactional data into structured management information across:
Sales → Collections → Profitability → Customer Risk → Branch Performance → Receivables Ageing → Performance Trends
The project covered the full analytical workflow:
Business Understanding → Data Preparation → Data Modelling → DAX & KPI Development → Business Analysis → Reporting & Storytelling → Deployment & Governance

Business Problem & Reporting Requirements
CrestBridge Business Supplies had transactional data covering sales, collections, customers, products, branches and costs, but the information was not yet structured into a reliable management reporting system.
The raw data also contained several quality issues that could distort reporting if used without validation, including duplicate records, invalid product and customer identifiers, missing customer information, inconsistent branch and status values, zero or negative quantities, negative payments, overpayments and incomplete order-status fields.
Management therefore needed a reporting solution that could do two things:
ensure that only valid and appropriate transactions contributed to financial reporting; and
convert operational data into clear performance information that could support management action.
The reporting solution needed to answer questions across several areas.
Sales Performance
Management needed to understand:
total valid sales generated;
sales performance by branch;
sales performance by product and category;
monthly sales movement and changes in trend.
Collections & Receivables
Management needed visibility into:
total amount collected;
total amount outstanding;
collection rate;
collection performance against branch targets;
customers with the highest outstanding balances;
overdue receivables by ageing category;
customers requiring urgent follow-up.
Profitability
The reporting solution needed to show:
total gross margin;
gross margin percentage;
profitable products and categories;
the difference between high-sales products and high-margin products.
Customer Risk
Management needed to identify:
customer segments with the highest outstanding exposure;
customers contributing most to receivables risk;
the age of outstanding balances;
priority accounts for collection action.
Branch Performance
The solution also needed to compare Lagos, Abuja and Port Harcourt across:
sales;
collections;
outstanding balances;
collection rates;
collection targets;
target attainment.
The central reporting challenge was therefore to transform imperfect transactional data into trusted management information that could help management monitor performance, identify risks and prioritise action.

Data Preparation & Data Quality
The source workbook contained a Raw_Orders transactional table supported by product, customer and branch master tables.
Before analysis, the raw data required validation because several issues could distort sales, collection and profitability reporting.
The data-quality issues identified included:
duplicate records;
invalid Product Codes;
invalid Customer IDs;
missing Customer IDs;
an invalid branch value;
zero and negative quantities;
negative payments;
overpayments;
missing Order Status values;
inconsistent branch names;
inconsistent status formatting.
Rather than overwrite the raw source, I preserved the original dataset and created a separate Clean_Orders table for transformation and reporting.
Validation Approach
Using Power Query, I applied validation rules to identify whether each transaction should be:
Valid
Review
Invalid – Exclude
This allowed questionable records to be separated from transactions considered suitable for reporting.
I also created a separate Financial Reporting Status to control which records were allowed to contribute to financial KPIs.
This was important because a technically complete dataset is not automatically a reporting-ready dataset. Transactions containing invalid references, abnormal quantities or problematic payment values could materially distort management results if included without review.
Transformation Process
The data-preparation process included:
standardising branch and status values;
checking Product Codes against the product master;
checking Customer IDs against the customer master;
identifying missing customer references;
detecting duplicate records;
validating transaction quantities;
reviewing negative and abnormal payment values;
identifying potential overpayments;
separating reportable transactions from records requiring review or exclusion.
The cleaned transactional data was then prepared for integration with the Product, Customer and Branch dimensions.
Reporting Control Principle
A key design decision was to separate:
Raw Data → Data Quality Classification → Financial Reporting Eligibility → Analytical Reporting
This ensured that reported sales, collections, profitability and receivables measures were based on defined business rules rather than simply aggregating every row in the source file.
The result was a more reliable analytical dataset and a clearer audit trail between the original source data and the figures presented in the Power BI reports.


Data Model & Analytical Structure
After cleaning and validating the transactional data, I structured the Power BI model using a star-schema approach.
The model was designed around Clean_Orders as the central fact table, supported by separate dimension tables for:
Products
Customers
Branches
Date
Fact Table
Clean_Orders contained the validated transaction-level data used for analysis.
It included fields related to:
order activity;
quantities;
payments;
reporting status;
customer and product references;
branch information;
receivables and collection-related calculations.
Dimension Tables
The supporting dimension tables were used to provide descriptive business context.
Product Dimension
Included attributes such as:
Product Code
Product Name
Product Category
Unit Price
Unit Cost
Customer Dimension
Included attributes such as:
Customer ID
Customer Name
Customer Segment
Customer Home Branch
Payment Terms
Branch Dimension
Included:
Branch Name
Branch Collection Target
Date Dimension
A dedicated Date table was created to support time-based analysis, including monthly sales trends and Month-on-Month performance calculations.
Why the Model Was Structured This Way
The star-schema design separated transactional data from descriptive business attributes.
This improved:
consistency of analysis;
filtering behaviour;
measure development;
model readability;
scalability of reporting;
maintenance of business logic.
It also reduced the need to repeatedly store descriptive information inside the transactional table.
Relationships between the fact and dimension tables allowed management performance to be analysed by:
time → branch → customer → customer segment → product → product category
The resulting model provided the analytical foundation for the KPI, profitability, collections and receivables reporting developed later in the project.
