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
- `product_catalog.csv`: Product information including categories and pricing

Each processor has different schemas and conventions for representing similar information.

## Product Requirements

Build a data pipeline that processes these various data sources and creates a transformed dataset suitable for accounting analysis. The final output should enable the generation of monthly journal entries (similar to the current example but focusing on the data processing aspects).

### Features
- Data Ingestion
  - Create ingestion processes for both CSV and JSON data sources
  - Implement basic data quality checks
  - Handle common data issues (duplicates, missing values, etc.)

- Data Transformation
  - Normalize transaction data from different sources into a consistent format
  - Calculate derived fields (e.g., total sales, tax amounts)
  - Create dimension tables for products, regions, and time periods
  - Implement proper handling of historical data changes

- Data Modeling
  - Design an efficient schema that supports:
    - Fast query performance for common accounting queries
    - Easy maintenance and updates
    - Clear audit trail of transformations
    - Flexible reporting capabilities

### Required Calculations
- Transaction amount normalization (handling different currency formats)
- Tax calculations based on regional rates
- Monthly aggregations for:
  - Gross sales by product category
  - Net revenue after returns
  - Tax liability by jurisdiction
  - Payment reconciliation

## Technical Requirements

### Infrastructure
- Use DuckDB or SQLite for local development
- Optionally: If you have access, you may use Snowflake/BigQuery/etc.
- Implement data quality tests
- Include proper documentation of data lineage

### Data Pipeline
- Build modular transformation logic using DBT (or similar tool)
- Include proper testing and documentation
- Implement error handling and logging
- Create incremental processing capability

### Documentation
- Provide a README with setup instructions
- Include data dictionary for final models
- Document any assumptions made about the data
- Explain your choices in data modeling and transformation logic

### Bonus Points
- Implementation of data quality monitoring
- Performance optimization techniques
- CI/CD configuration
- Data visualization examples

## Submission

Please provide a link to a repository containing your code. Include:
- Source code for all transformations
- DDL for required tables
- Documentation of your solution
- Any scripts needed to run the pipeline

We recognize this assignment is comprehensive and appreciate your time. If you choose not to implement certain aspects, please explain your prioritization decisions.

Good luck!

