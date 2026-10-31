 Key DAX Measures

This file contains selected DAX measures used in the CrestBridge Business Supplies Power BI project.

The measures were designed to translate validated transaction data into management information across sales, collections, profitability, branch performance and performance trends.



1. Valid Gross Sales

Purpose
Calculates total gross sales using only transactions approved for financial reporting.

DAX


Valid Gross Sales = 
CALCULATE(
    SUM(Clean_Orders[Gross Sales]),
    Clean_Orders[Financial Reporting Status] = "Include"
)

Business Use
Provides a controlled sales figure that excludes transactions that do not meet the defined financial reporting rules.

This helps ensure that management sales KPIs are based on validated and reportable transactions rather than every record in the source dataset.

2. Collection Rate
Purpose
Measures the proportion of valid gross sales that has been collected from customers.

DAX

Collection Rate = 
DIVIDE(
    [Amount Collected],
    [Valid Gross Sales],
    0
)

Business Use
Helps management evaluate how effectively sales are being converted into cash.

The measure can also be analysed by branch, customer segment and other dimensions to identify areas with weak collection performance.

3. Total Outstanding Balance

Purpose
Calculates the total unpaid balance relating only to transactions included in financial reporting.

DAX
Total Outstanding Balance = 
CALCULATE(
    SUM(Clean_Orders[Outstanding Balance]),
    Clean_Orders[Financial Reporting Status] = "Include"
)

Business Use
Provides management with visibility into total receivables exposure and supports further analysis of overdue balances, ageing and collection priorities.


4. Overall Gross Margin %

Purpose
Measures gross margin as a percentage of valid gross sales.

DAX
Overall Gross Margin % = 
DIVIDE(
    [Total Gross Margin],
    [Valid Gross Sales],
    0
)

Business Use
Shows profitability efficiency and allows management to compare products, categories or other business segments beyond sales value alone.

This helps distinguish between products generating high revenue and products generating stronger margins.


5. Collection Rate Variance vs Target

Purpose
Measures the difference between actual collection performance and the applicable branch collection target.

DAX
Collection Rate Variance vs Target = 
VAR TargetValue = [Branch Collection Target]
RETURN
IF(
    ISBLANK(TargetValue),
    BLANK(),
    [Collection Rate] - TargetValue
)

Business Use
Shows whether a branch is performing above or below its collection target.

A negative result indicates that actual collection performance is below target, while a positive result indicates performance above target.

This measure helped identify Port Harcourt as the branch requiring the greatest collection attention.


6. Month-on-Month Sales Change

Purpose
Measures the absolute difference between current valid gross sales and the previous month's valid gross sales.

DAX
Month-on-Month Change = 
VAR PreviousValue = [Previous Month Gross Sales]
RETURN
IF(
    ISBLANK(PreviousValue),
    BLANK(),
    [Valid Gross Sales] - PreviousValue
)

Business Use
Shows the absolute increase or decrease in sales compared with the previous month.

It helps management identify significant movements in sales performance and determine which periods may require deeper investigation.

A positive value indicates an increase from the previous month, while a negative value indicates a decline.

Month-on-Month % Change

Measures the percentage increase or decrease in valid gross sales compared with the previous month.

Month-on-Month % Change = 
DIVIDE(
    [Month-on-Month Change],
    [Previous Month Gross Sales],
    BLANK()
)

Makes it easier to compare the scale of monthly performance changes, even when sales values differ significantly between periods.
