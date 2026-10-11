# PhonePe Transaction Analysis Dashboard

An interactive Power BI report that analyses 300,000 digital payment transactions across money transfers, bill payments and recharges, loans and insurance. The report covers payment success, payment failure and user activity, and is backed by a two table data model with DAX measures.

## Objective

Understand how transaction volume and value are distributed across services, how reliable payments are, why payments fail, and how often users transact.

## Dashboard Pages

| Page | Purpose | Main visuals |
|---|---|---|
| Payment Success | Overall volume, value and status mix | KPI cards, payment status donut, amount by service, transactions by service type, monthly transaction trend |
| Payment Fail | Failure volume, value and causes | KPI cards, failed transactions by service and by reason, monthly failure trend |
| User | User reach and activity | KPI cards, users by service, users by month, transactions by service type |

Every page has slicers for Month-Year, Service and Service Type. The Payment Success and User pages also filter on Payment_Status, and the Payment Fail page filters on Reason.

## Data Model

| Table | Rows | Columns |
|---|---|---|
| PhonePe (fact) | 300,000 | Transaction_ID, User_ID, Amount, Service, Service Type, Payment_Status, Reason, Date, Year, Month, Month Number, Month-Year, Day, Day Name |
| All_Users (dimension) | 107,659 | User_ID, Name, Age, Join_Date |

Coverage: transactions from January to December 2024, 4 services and 16 service types.

| Service | Service Types |
|---|---|
| Money_Transfer | To UPI ID, To Self Account, To Mobile Number, To QR Code |
| Loans | Bike Loan, Gold Loan, Mutual Fund, Credit Score |
| Insurance | Term Life, Health, Car, Bike |
| Recharge_Bills | Mobile Recharge, DTH, FASTag Recharge, Cable TV |

## DAX Measures

| Measure | Definition |
|---|---|
| Total Transactions | `DISTINCTCOUNT(PhonePe[Transaction_ID])` |
| Total Amount | `SUM(PhonePe[Amount])` |
| Total Users | `DISTINCTCOUNT(PhonePe[User_ID])` |
| Successful Transactions | Total Transactions where Payment_Status is "Successful" |
| Success Rate | Successful Transactions divided by Total Transactions |
| Failed Transactions | Total Transactions where Payment_Status is "Failed" |
| Failed Amount | Sum of Amount where Payment_Status is "Failed" |
| Avg Failed Transaction Amount | Average Amount where Payment_Status is "Failed" |
| Transactions per User | Total Transactions divided by Total Users |
| Average Transaction Amount | `AVERAGE(PhonePe[Amount])` |

## Key Insights

Figures below are computed from the dataset for the full year.

1. The dataset holds 300,000 transactions worth about 3.47 billion across 100,761 transacting users, with an overall success rate of 96.0%.
2. Money Transfer accounts for half of all transactions (150,000), but Loans generates about 73% of total value, with an average transaction near 50,650 compared with about 2,521 for a transfer.
3. Success rate stays between 95.6% and 96.3% across all 16 service types, so reliability does not vary meaningfully by service.
4. Monthly volume stays between 24,040 and 25,659 transactions, with no strong seasonality.
5. The average user makes about 3 transactions in the year, and only 16% make five or more.
6. The top 10% of users by spend contribute about 37% of total value.


## How to Open

1. Install Power BI Desktop (Windows).
2. Download `Phonepe_Analysis.pbix` from this repository.
3. Open the file. The data is embedded in the report, so no data source setup is needed.

## Tools

Power BI Desktop, DAX.

## Author

Azli Khan
GitHub: [Azli45](https://github.com/Azli45)
LinkedIn: [azli-khan07](https://www.linkedin.com/in/azli-khan07)
