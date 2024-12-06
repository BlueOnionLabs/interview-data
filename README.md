# Blue Onion Labs Data Engineering Take Home Assignment

Thank you for your interest in Blue Onion!

This assignment is designed to give you an opportunity to demonstrate your data engineering skills in a practical format similar to what you would be doing as a member of our team. We primarily use Python and modern data tools, so we encourage you to use Python + DBT (or similar transformation tool) for this assignment.

## Background

In our hypothetical scenario, we have a client who needs to process and analyze their financial transaction data from multiple sources to generate accurate accounting reports. The client receives daily transaction files from various payment processors and needs to consolidate this data into a reliable analytical database that powers their accounting system.

## Data Sources

The repository contains sample data files in the `/data` directory:
- `processor_a_transactions.csv`: Main payment processor transactions
- `processor_b_transactions.json`: Secondary payment processor transactions
- `tax_rates.csv`: Reference table for tax rates by region
- `exchange_rates.csv`: Daily currency conversion rates to USD

Each processor has different schemas and conventions for representing similar information.

## Product Requirements

We need to generate monthly accounting reports that track money flowing in and out. Each month's report should:
1. Sum up all transactions for that month
2. Show the money customers owe us (orders, shipping, and taxes)
3. Show the money we received from customers
4. Follow this format:

### Monthly Report Format
Example for a month with $20,000 in orders:
```csv
Account,Debit,Credit,Description
Accounts Receivable,20000.00,,Cash expected for orders
Revenue,,20000.00,Revenue for orders

Accounts Receivable,1500.00,,Cash expected for shipping
Shipping Revenue,,1500.00,Revenue for shipping

Accounts Receivable,750.00,,Cash expected for taxes
Sales Tax Payable,,750.00,Cash to be paid for sales tax

Cash,22250.00,,Cash received
Accounts Receivable,,22250.00,Clears out what customers owed
```

### How to Calculate Each Amount
1. Order amount: Transaction amount (minus bundle discount if exists)
2. Shipping: From transaction data (not affected by bundle discount)
3. Tax: Order amount × tax rate (shipping is not taxed)
4. Convert all amounts to USD using exchange_rates.csv for the transaction date

See example_journal_entries.csv for more examples.

### Technical Requirements

1. **Data Ingestion**
   - Process processor_a_transactions.csv and processor_b_transactions.json
   - Validate required fields: transaction_id, date, amount, currency, status
   - Check regions exist in tax_rates.csv

2. **Data Model**
   - transactions (normalized data from both processors)
   - tax_rates (from tax_rates.csv)
   - monthly_journal_entries (output)

3. **Infrastructure**
   - Use a database you feel comfortable with for local development (DuckDB or SQLite are suggested as options)
   - Implement error handling and logging
   - Optional: If you have access, you may use Snowflake/BigQuery/etc.
   - Optional but suggested: Use a tool to perform modular transformations (DBT is one such option)
   - Bonus: Create incremental processing capability
   - Bonus: Implementation of data quality monitoring
   - Bonus: CI/CD configuration

4. **Documentation**
   - Provide a README with setup instructions
   - Document any assumptions made about the data

## Submission

Please provide a link to a repository containing your code

We recognize this assignment is comprehensive and appreciate your time. It's totally OK to opt out of certain implementation details. If you choose not to implement certain aspects of the exercise, just explain your prioritization decisions.

Good luck!
