# 📊✨ MS Power BI PR. 2 Data Modeler

## Overview
- Build a normalized star-schema data model in Power BI. 🚀
- Focus: table relationships, schema design, and Power Query transformations. 🔧
- Not required: DAX measures or calculated columns. Use a Matrix visual for verification only. ✅

## Repository Contents 📂
- [README.md](README.md) — this file
- [summary.txt](summary.txt) — concise project summary and troubleshooting notes �
- [Data/](Data/) — source Excel files:
  - [x] Customer_Dim.xlsx �
  - [x] Product_Dim.xlsx 🛍️
  - [x] Region_Dim.xlsx 🌍
  - [x] Date_Dim.xlsx 📆
  - [x] Sales_Fact.xlsx �
  - [x] Returns_Fact.xlsx �

## Quick Start ▶️
1. Opened Power BI Desktop. 🖥️
2. Get data → Excel → select files from [Data/]. 📁
3. Used Power Query to clean and transform tables, then Close & Apply. �
4. Built relationships in Model View following the Relationship & Modeling Guidelines below. �
5. Used a Matrix visual for verification (no other visuals required). �

## Dataset Summary �
- Sales_Fact.xlsx
  - SalesID (PK), CustomerID (FK), ProductID (FK), RegionID (FK), DateKey (FK), Quantity, Revenue, Discount 💹
- Returns_Fact.xlsx
  - ReturnID (PK), SalesID (FK), ReturnDateKey (FK), Reason 🔎
- Customer_Dim.xlsx
  - CustomerID (PK), FullName, Age, Gender, Segment 🧑‍🤝‍🧑
- Product_Dim.xlsx
  - ProductID (PK), ProductName, Category, Subcategory, Brand 🏷️
- Region_Dim.xlsx
  - RegionID (PK), Country, State, City 🗺️
- Date_Dim.xlsx
  - DateKey (PK), Date, Month, Quarter, Year, Fiscal Year 📅

## Relationship & Modeling Guidelines 🧭
- Schema type: Star Schema centered on Sales_Fact (see [summary.txt](summary.txt)). ⭐
- Relationship pattern: Dimension (1) → Fact (many). ➡️
- Preferred filter direction: single-direction from dimensions → facts. 🔒
- Use inactive relationships (e.g., Returns_Fact → Date_Dim for ReturnDateKey) where needed to avoid ambiguous filter paths. 🧩
- Avoid unnecessary bidirectional filters; enable only when strictly justified. ⚖️

## Power Query & Data Prep 🧰
- Imported via Power Query from [Data/]. �
- Clean steps: removed blank rows, set correct datatypes (ensure Date columns are real dates), trimmed text, normalized categories. 🧼
- Set Data Categories (City, Country) and created hierarchies:
  - Date_Dim: Year > Quarter > Month > Date 🔢
  - Region_Dim: Country > State > City 🏙️
  - Product_Dim: Category > Subcategory > ProductName 🧾

## Verification ✅
- Used a Matrix visual to validate:
  - Sales by Product Category and Region 🧾➡️🌍
  - Return reasons by Fiscal Year 🔁📆
  - Revenue by Customer Segment �👥

## Deliverables 🧾
- One .pbix file including:
  - Transformed tables (Power Query) 🔧
  - Model relationships and hierarchies 🔗
  - Matrix visual for verification ✅
- Short summary (.docx / .txt) describing:
  - Schema type (star/snowflake) ⭐/❄️
  - Relationship rationale and filter flow 🔍
  - Issues encountered and resolutions �️
  - See [summary.txt](summary.txt) for current notes �

## Screenshots 🖼️

### Power Query Editor

#### Query structure
![Power Query Editor - Query Structure](Screenshots/Power%20Query%20Editor/Query%20Structure/image.png)

#### Customer Table

![Power Query Editor - Customer Table](Screenshots/Power%20Query%20Editor/Customer%20Table/image.png)

#### Date Table

![Power Query Editor - Date Table](Screenshots/Power%20Query%20Editor/Date%20Table/image.png)

#### Product Table
![Power Query Editor - Product Table](Screenshots/Power%20Query%20Editor/Product%20Table/image.png)

#### Region Table
![Power Query Editor - Region Table](Screenshots/Power%20Query%20Editor/Region%20Table/image.png)

#### Returns Table
![Power Query Editor - Returns Table](Screenshots/Power%20Query%20Editor/Returns%20Table/image.png)

#### Sales Table
![Power Query Editor - Sales Table](Screenshots/Power%20Query%20Editor/Sales%20Table/image.png)![Power Query Editor - Sales Table](Screenshots/Power%20Query%20Editor/Sales%20Table/image-2.png)

### Model View

#### Data Model Diagram
![Model View - Data Model Diagram](Screenshots/Model%20View/diagram.png)

### Table View

![Model View - Table View](Screenshots/Table%20View/image.gif)

### Report View (Only Matrix Visual)

![Report View - Matrix Visual](Screenshots/Report%20View/image.png)

## All-in-one GIF 🖼️
![All-in-one GIF](Screenshots/all_in_one.gif)

## Checklist ✅
- [x] Import all files via Power Query
- [x] Clean and transform each table
- [x] Create relationships in Model View
- [x] Build hierarchies and set data categories
- [x] Capture Model View + Matrix screenshots

## Common Issues & Troubleshooting ⚠️
- Date parsing: Power BI misreads Excel date serials when Excel column datatype is not Date. Fix in Excel (Short Date) or enforce Date type in Power Query. (See issue noted in [summary.txt](summary.txt).) 🔧📅

## Contributors & Contact 🤝
- Assigned by Business Analyst Manager (see [summary.txt](summary.txt)). �
- For questions, attach sample screenshots and a short summary of steps taken. �

## License 📜
- This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details. 🏷️

## References 🔗
- Project notes: [summary.txt](summary.txt) �
- Source data: [Data/](Data/) 📂

## **Data Dictionary** 🗂️
- **Sales_Fact**: SalesID (PK), CustomerID (FK), ProductID (FK), RegionID (FK), DateKey (FK), Quantity, Revenue, Discount — transactional sales values.
- **Returns_Fact**: ReturnID (PK), SalesID (FK), ReturnDateKey (FK), Reason — returns linked to sales.
- **Customer_Dim**: CustomerID (PK), FullName, Age, Gender, Segment — descriptive customer attributes.
- **Product_Dim**: ProductID (PK), ProductName, Category, Subcategory, Brand — product catalog details.
- **Region_Dim**: RegionID (PK), Country, State, City — geographic hierarchy.
- **Date_Dim**: DateKey (PK), Date, Month, Quarter, Year, Fiscal Year — calendar attributes used for time intelligence.

## **Modeling Decisions** 🧭
- Schema: Star schema centered on `Sales_Fact`. This reduces complexity and improves query performance for common analytics.
- Filter direction: Single-direction from dimensions → facts to keep filter flow predictable and to avoid performance issues from many-to-many propagation.
- Returns: Modeled as a separate fact table and linked to `Sales_Fact` via `SalesID` to preserve transactional integrity; use an inactive relationship to `Date_Dim` for `ReturnDateKey` when needed.
- Hierarchies: Build Year → Quarter → Month → Date (Date_Dim) and Country → State → City (Region_Dim) to enable efficient drilling in visuals.

## **How to Reproduce / Run** ▶️
1. Open Power BI Desktop (version recommended: latest stable). 🖥️
2. Use `Get data` → `Folder` or `Excel` and point to the `Data/` folder. 📁
3. In Power Query Editor: apply the transformations recorded in each query (remove blanks, set datatypes, trim, deduplicate where applicable). 🔁
4. Close & Apply to load tables to the model. 🔄
5. In Model View: create relationships as per the diagram in `Screenshots/Model View/diagram.png`. 🔗
6. Verify with the Matrix visual shown in `Screenshots/Report View/image.png`. ✅

## **How to Review / QA Checklist** 🔎
- Confirm row counts: Source file vs Power Query preview (after transformations). ✔️
- Confirm datatypes: Date columns are Date, numeric columns are Decimal/Whole Number. 🔢
- Confirm relationships: Cardinalities are correct and filter directions are as documented. 🔗
- Validate a few sample queries in Report View (Revenue by Category & Region, Returns by Fiscal Year). 📊
- Performance sanity: Refresh takes reasonable time; avoid unnecessary computed columns. ⏱️

## **Contribution Guidelines** 
- Open an issue describing the change before making major updates.
- Keep Power BI `.pbix` files under `releases/` (if included) and large assets under `Data/` or `Screenshots/` only.
- For changes to queries or model, include a short note in `summary.txt` describing intent and effect. 📝

## **FAQ / Troubleshooting** ❓
- Q: Power BI shows wrong dates after import — A: Ensure Excel source column is typed as Date or cast in Power Query using `Date.From`. 📅
- Q: Duplicate keys in dimension — A: Remove duplicates in Power Query or create a surrogate key when necessary. 🔑
- Q: Filters not applying — A: Check relationship direction and inactive relationships; consider using DAX only where necessary. 🧩

## **Changelog** 🧾
- 2025-11-24: Expanded README with Data Dictionary, Modeling Decisions, Reproduction steps, QA, Contribution Guidelines, FAQ, and Glossary. ✨

## **Contact & Support** 📬
- Owner: `Prath Udhnawala` — Email: (add-your-email@example.com) — for data access requests or scope questions. 📧
- For technical issues, create a GitHub Issue including screenshots and steps-to-reproduce. 🐞

## **Glossary** 📚
- Star Schema: A data modeling pattern with a central fact table connected to dimension tables (1→many). ⭐
- Fact Table: Table containing transactional metrics (revenue, quantity). 💰
- Dimension Table: Descriptive attributes used for slicing and dicing (product, customer, date). 🧾

## **Tips & Best Practices** ✅
- Prefer Power Query transformations over DAX for cleaning and shaping data — it keeps the model lean. 🧼
- Avoid calculated columns where a query transformation will do the job. ➖
- Use hierarchies and data categories to improve report usability and locale-aware formatting. 🌐
- Document any deviations from the standard model in `summary.txt`. 📝

## **Badges (optional)** 🏷️
- Status: ![Status](https://img.shields.io/badge/status-complete-brightgreen?logo=starship)
- License: ![GitHub License](https://img.shields.io/github/license/Prath-Digital/MS_Power_BI_PR.-2-Data-Modeler?logo=github&logoColor=%23ffffff&label=License)
- Power BI: ![Power BI](https://img.shields.io/badge/Power%20BI-Microsoft%20Power%20BI-F2C811?logo=microsoft-power-bi&logoColor=black)
- Contributors: ![Contributors](https://img.shields.io/github/contributors/Prath-Digital/MS_Power_BI_PR.-2-Data-Modeler?logo=github&logoColor=%23ffffff)