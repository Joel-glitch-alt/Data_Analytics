📦 1. Installation & Setup

Launch Arbutus Analyzer.

Open a project or create a new one.

Import data using File > Open or File > Import (CSV, Excel, text, database).

🔍 2. Data Loading & Inspection

Open a table

OPEN "C:\Data\Transactions.csv";

View first few rows

FIRST 10;

Describe field properties

DESCRIBE ALL;

🧹 3. Data Cleansing

Filter records

BEGINNING
KEEP IF Country = "USA";
END

Convert string to date

COMPUTED Invoice_Date_D = CTOD(Invoice_Date);

Extract substring

COMPUTED State_Code = SUBSTR(State,1,2);

📊 4. Summarization & Reporting

Summarize (Group & Total)

SUMMARIZE ON Merchant_Name Expense_Type
   TOTAL Expense_Amount c_Meal_Limit_Excess
   CLASSIFY Employee_Number;

Summarize with filter

SUMMARIZE ON Agency
   TOTAL Transaction_Amount
   WHERE Country = "USA";

Frequency distribution

FREQUENCY ON State;

🔄 5. Joins & Lookups

Match (Inner Join)

MATCH Transactions TO Customers
    ON Customer_Number = Cust_Num;

Left Join

JOIN Transactions LEFT Customers
    ON Customer_Number = Cust_Num;

📑 6. Reconciliation

Compare two periods

COMPARE CurrPeriod TO PriorPeriod
    ON Invoice_Number;

Summarize differences

SUMMARIZE ON Status
   TOTAL Diff_Amount;

📆 7. Date Functions & Aging

Calculate age in days

COMPUTED Invoice_Age = AGE(Invoice_Date);

Bucket aging

COMPUTED Aging_Bucket = IF(Invoice_Age <= 30, "0-30",
                           IF(Invoice_Age <= 60, "31-60",
                           "Over 60"));

💾 8. Exporting Results

Export to Excel

EXPORT TO "C:\Reports\Summary.xlsx";

Export to CSV

EXPORT TO DELIMITED "C:\Reports\Output.csv";

🚀 9. Automation & Scripting

Macro recording: Use Tools > Record Macro to capture multiple commands.

Batch script: Save commands in a .arb file and run:

arbutus -run MyWorkflow.arb

📖 10. Further Resources

Arbutus Analyzer User Guide
