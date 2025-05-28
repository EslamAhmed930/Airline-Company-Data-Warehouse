#  Airline Company Data Warehouse (DWH)

This project implements a full Data Warehouse (DWH) solution for an Airline Company, aimed at transforming normalized operational data into an analytical star schema model. It includes ETL process design, dimensional modeling, and performance considerations.

---

##  Project Structure

- `Logical Model.drawio`: ERD representing the high-level logical design.
- `Physical Data Model.xlsx`: Detailed physical schema with tables, datatypes, and relationships.
- `Project Documentation.docx`: Full project overview including goals, assumptions, and data mapping.
- `Report on Index Types in Data Warehousing.docx`: Analysis of indexing strategies to improve performance.
- `README.md`: Project overview and usage instructions.

---

##  Architecture Overview

This DWH follows a **Star Schema** design with clearly separated **dimension** and **fact** tables.

###  Fact Table
- `fact_flight_sales`: Captures ticket purchases, including foreign keys to date, customer, and flight dimensions.

###  Dimension Tables
- `dim_customer`: Passenger demographics and contact info.
- `dim_flight`: Flight details including aircraft, source, and destination.
- `dim_airport`: Airports with city, country, and codes.
- `dim_date`: Prepopulated date dimension.
- `dim_aircraft`: Aircraft type, capacity, and specs.

---

##  ETL Process (via IBM DataStage or SQL)

1. **Extract**: Pull data from OLTP sources (booking systems, CRM).
2. **Transform**:
   - Normalize inconsistent values.
   - Generate surrogate keys for dimensions.
   - Lookup and update slowly changing dimensions (SCD).
3. **Load**:
   - Load dimensions first.
   - Populate fact table via foreign keys from dimensions.

---

##  Technologies Used

- **ETL Tool**: IBM InfoSphere DataStage
- **Database**: Oracle / SQL Server (DWH)
- **Modeling Tools**: draw.io (ERD), Excel (schema definition)
- **Documentation**: Microsoft Word

---

##  Getting Started

1. Clone the repo and open `Logical Model.drawio` and `Physical Data Model.xlsx`.
2. Design your target database using the schema definitions.
3. Implement ETL flows based on `Project Documentation.docx`.
4. Test performance and indexing strategies described in `Report on Index Types.docx`.

---

##  Performance Tips

- Use **bitmap indexes** on low-cardinality dimension keys.
- Apply **surrogate keys** to all dimension tables.
- Partition large fact tables by date or flight ID.
- Avoid joins on transformed fields (e.g., `YEAR(order_date)`).

---



