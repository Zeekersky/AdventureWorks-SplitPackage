# AdventureWorks-SplitPackage

This repository contains an SSIS package that performs conditional data splitting based on country names. The package processes employee data from the **AdventureWorksDW2017** database and distributes it into separate tables for the United States, United Kingdom, Germany, and others.

## Features
- **Conditional Data Splitting**: Divides data based on the `CountryRegionName` column.
- **ETL Process**: Demonstrates key ETL (Extract, Transform, Load) techniques using SQL Server Integration Services (SSIS).
- **AdventureWorksDW2017 Integration**: Uses the DimEmployee and DimSalesTerritory tables for data transformation.
- **Dynamic Table Population**: Creates and populates new tables for country-specific employee data.

## Requirements
- **SQL Server**: AdventureWorksDW2017 sample database installed.
- **Visual Studio 2019**: With the "SQL Server Integration Services Projects" extension.
- **Environment**: Ensure SSIS and OLE DB connections are properly configured.

## Key Logic
- Employee data in the `DimEmployee` table lacks direct country information.
- A **left join** between `DimEmployee` and `DimSalesTerritory` tables is performed using `SalesTerritoryKey`.
- The merged data is passed through a **Conditional Split** to separate it based on the `CountryRegionName`.

## Process Flow
1. **Data Extraction**:
   - Two OLE DB Source tools fetch data from `DimEmployee` and `DimSalesTerritory` tables.

2. **Data Transformation**:
   - Sort and merge data using the `Merge Join` tool.
   - Split the data conditionally based on the `CountryRegionName` column.

3. **Data Loading**:
   - Populate separate destination tables:
     - `DimEmployee_UnitedStates`
     - `DimEmployee_UnitedKingdom`
     - `DimEmployee_Germany`
     - `DimEmployee_Others`

## Steps to Execute
1. Clone this repository.
   ```bash
   git clone https://github.com/Zeekersky/AdventureWorks-SplitPackage
   ```
2. Open the project in Visual Studio 2019 with the SSIS extension installed.
3. Configure the OLE DB connection to point to your AdventureWorksDW2017 database.
4. Build and execute the SSIS package.
5. Verify the output in the respective destination tables using SQL Server Management Studio (SSMS).

## Output
Upon execution, the employee data will be split into four destination tables based on their `CountryRegionName`:
- **United States**: `DimEmployee_UnitedStates`
- **United Kingdom**: `DimEmployee_UnitedKingdom`
- **Germany**: `DimEmployee_Germany`
- **Others**: `DimEmployee_Others`

## Folder Structure
- **/SSIS_Package**: Contains the SSIS project files.
- **/Documentation**: Includes the detailed project report (PDF).

## Project Report
The detailed project report can be accessed [here](https://github.com/Zeekersky/AdventureWorks-SplitPackage/blob/main/Project%20Report.pdf).

## Screenshots
*Include relevant screenshots of your SSIS package and output tables here.*

## License
This project is open-source and available under the [MIT License](LICENSE).

## Contact
For any queries or suggestions, feel free to reach out:
- **Author**: Akash Pal
- **GitHub**: [Zeekersky](https://github.com/Zeekersky)
