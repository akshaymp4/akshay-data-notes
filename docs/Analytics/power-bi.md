<div class="powerbi-hero">
  <div class="powerbi-chip">Analytics | BI Development | Reporting</div>
  <h1>Microsoft Power BI</h1>
  <p>
    Power BI is a business intelligence platform used to connect data, clean and transform it,
    model relationships, build interactive dashboards, and publish reports for decision-making.
    These notes are structured from basic to advanced level for analytics, BI, and developer-oriented work.
  </p>
</div>

## 1. Power BI Overview { .powerbi-h2 }

### 1.1 What Is Power BI? { .powerbi-h3 }

Microsoft Power BI is a BI and data visualization platform used to:

- connect data from many sources
- transform and clean data
- model tables and relationships
- create reports and dashboards
- publish and share insights

It is widely used by:

- data analysts
- business analysts
- analytics engineers
- reporting developers
- data teams working with Microsoft ecosystems

### 1.2 Why Power BI Is Important { .powerbi-h3 }

Power BI is popular because it combines data preparation, modeling, DAX calculations, visualization, and cloud sharing in one ecosystem.

For analytics roles, it helps you:

- build business reports quickly
- combine data from multiple systems
- create reusable metrics
- support decision-making with dashboards
- publish reports through Power BI Service

### 1.3 File Types and Interface Basics { .powerbi-h3 }

Common file extensions:

- `.pbix`: Power BI Desktop report file
- `.pbit`: Power BI template file
- `.twbx`: Tableau packaged workbook, not a Power BI file, but useful to remember when comparing tools

Main tabs in Power BI Desktop:

- File
- Home
- Insert
- Modeling
- View
- Help

Features inside these tabs are called ribbons, similar to Microsoft Excel.

Useful note:

- Power BI is updated frequently
- you can check the current installed version through `Help > About`

### 1.4 Pages vs Sheets { .powerbi-h3 }

In Excel, you work with sheets.

In Power BI, you work with report pages such as:

- Page 1
- Page 2
- Summary
- Sales Dashboard

## 2. Core Architecture of Power BI { .powerbi-h2 }

### 2.1 Three Main Components { .powerbi-h3 }

Power BI is commonly understood through three core working areas:

1. Power Query
2. Power Pivot
3. Power View

### 2.2 Power Query { .powerbi-h3 }

Power Query is used for:

- data extraction
- transforming data
- cleaning data
- reshaping columns and rows
- combining multiple sources

Analysts often spend a large portion of their project time here.

### 2.3 Power Pivot { .powerbi-h3 }

Power Pivot is used for:

- data modeling
- organizing tables
- creating relationships
- writing DAX
- building measures and calculated columns

### 2.4 Power View { .powerbi-h3 }

Power View is the reporting and presentation layer where you:

- analyze data
- build visuals
- create dashboard pages
- present insights to users

### 2.5 Time Split in Real Projects { .powerbi-h3 }

A practical rule often seen in analytics work:

- around 80% of the time goes into Power Query and Power Pivot
- around 20% goes into Power View

This is because data cleaning, modeling, and business logic usually take more effort than drawing visuals.

## 3. Data Connections and Import Best Practices { .powerbi-h2 }

### 3.1 Data Sources { .powerbi-h3 }

Power BI can import data from many sources, including:

- Excel
- SQL Server
- Azure sources
- CSV files
- web APIs
- SharePoint
- Oracle
- PostgreSQL
- MySQL

### 3.2 Excel Best Practice { .powerbi-h3 }

When importing from Excel, always convert the source range into a proper Excel table first.

Why this helps:

- refresh becomes easier
- new rows are included automatically
- structure is more reliable
- data range issues are reduced

This should become a regular habit.

### 3.3 Import vs Transform Data { .powerbi-h3 }

When loading data into Power BI, you will usually choose one of these options:

- Load: bring the data directly into the model
- Transform Data: open Power Query to clean and reshape before loading

For most serious projects, `Transform Data` is the better option.

## 4. Power Query and M Language { .powerbi-h2 }

### 4.1 What Power Query Does { .powerbi-h3 }

Power Query is the ETL layer inside Power BI.

Typical tasks:

- remove nulls
- rename columns
- change data types
- split columns
- merge tables
- append tables
- filter records
- pivot and unpivot data

### 4.2 M Language { .powerbi-h3 }

M Language, also called Power Query M Formula Language, is the language used behind Power Query steps.

It is mainly used to:

- transform source data
- define repeatable cleaning steps
- manipulate tables before loading to the model

You do not need to write M manually at the beginning, but it becomes useful as you move to advanced work.

### 4.3 Append vs Merge { .powerbi-h3 }

These are two very important concepts.

Append:

- stacks one table below another
- used when tables have similar columns
- similar to `UNION ALL` in SQL

Merge:

- joins two tables side by side
- used when tables have related keys
- similar to `JOIN` in SQL

### 4.4 Example: Data Consolidation Using Append { .powerbi-h3 }

If you have two sales tables from two sheets:

1. import both tables
2. open `Transform Data`
3. select one query from the left panel
4. go to `Home > Append Queries`
5. choose the other table to append
6. rename the final combined query
7. disable load for intermediate queries if they are no longer needed

This helps keep the model clean.

## 5. Data Modeling { .powerbi-h2 }

### 5.1 What Is Data Modeling? { .powerbi-h3 }

The process of linking multiple tables to generate insight through analysis and visualizations is called data modeling.

Power BI data modeling helps you:

- connect fact and dimension tables
- reduce duplicate logic
- improve report performance
- create reusable business calculations

### 5.2 Model View { .powerbi-h3 }

Model View shows the relationships between tables like an ER diagram.

This is where you can:

- see connected tables
- manage relationships
- understand cardinality
- inspect schema structure

### 5.3 Auto-Detected Relationships { .powerbi-h3 }

By default, Power BI may automatically create relationships.

Important note:

- do not rely on this blindly
- it may be correct or incorrect
- always validate relationship columns, cardinality, and filter direction

You can also create relationships manually using drag and drop.

### 5.4 Relationship Types { .powerbi-h3 }

Power BI commonly uses:

- one-to-many
- many-to-one
- one-to-one
- many-to-many

The symbols `1` and `*` indicate a one-to-many relationship.

Example:

- `Customers[CustomerID]` -> `Sales[CustomerID]`
- one customer can have many sales records

### 5.5 Fact Table vs Dimension Table { .powerbi-h3 }

Fact table:

- contains measurable and transactional data
- usually includes sales amount, quantity, cost, profit, order count

Dimension table:

- contains descriptive attributes
- usually includes customer, product, region, date, category

Example:

Fact table:

| OrderID | ProductID | CustomerID | SalesAmount |
|---------|-----------|------------|-------------|
| 101 | P1 | C7 | 500 |
| 102 | P2 | C3 | 900 |

Dimension table:

| ProductID | ProductName | Category |
|-----------|-------------|----------|
| P1 | Laptop | Electronics |
| P2 | Phone | Electronics |

### 5.6 Star Schema { .powerbi-h3 }

Star schema is the preferred model design in many Power BI solutions.

It has:

- one fact table in the center
- multiple dimension tables around it

Benefits:

- easier to understand
- better performance
- simpler DAX
- cleaner report design

### 5.7 Snowflake Schema { .powerbi-h3 }

Snowflake schema is an extension of star schema where dimensions are further normalized into sub-dimensions.

Example:

- `Sales` connected to `Product`
- `Product` connected to `Category`

This can be useful, but in Power BI, star schema is often preferred for simplicity.

## 6. Views in Power BI Desktop { .powerbi-h2 }

### 6.1 Report View { .powerbi-h3 }

This is where you build visuals such as:

- cards
- slicers
- tables
- pie charts
- maps
- line charts
- bar charts

### 6.2 Table View { .powerbi-h3 }

This is where you inspect table data and create calculations such as:

- new column
- new measure
- quick measure
- new table

These options are found under `Table Tools` or `Modeling`, depending on context.

### 6.3 Model View { .powerbi-h3 }

This is the relationship and schema design area.

## 7. Visuals and Report Design { .powerbi-h2 }

### 7.1 Common Visuals { .powerbi-h3 }

Frequently used visuals:

- Card
- Slicer
- Table
- Pie chart
- Map
- Line graph
- Bar chart
- Matrix
- KPI
- Gauge
- Decomposition Tree

### 7.2 Choose the Right Chart { .powerbi-h3 }

Use chart types intentionally:

- bar chart for comparisons
- line chart for trends over time
- card for a single KPI
- table or matrix for detailed reporting
- map for geographic analysis
- slicer for interactive filtering

### 7.3 Drill Down and Grouping { .powerbi-h3 }

For additional drill-down in a line graph:

1. right-click on a date field
2. choose `New group`
3. create bins or number groups as needed

This is useful when you want to group values into ranges.

### 7.4 AI Features in Power BI { .powerbi-h3 }

Power BI includes built-in AI-assisted explanations.

Example:

If there is a dip in sales in a line chart:

1. right-click on the data point
2. choose `Analyze`
3. use `Explain the decrease` or `Explain the increase`

This helps discover possible drivers behind the change.

### 7.5 Working with Images from Links { .powerbi-h3 }

To convert a URL column into images:

1. go to table view
2. select the column with links
3. open `Column tools`
4. set `Data category` to `Image URL`

This is useful for product catalogs and profile-based reports.

## 8. DAX Fundamentals { .powerbi-h2 }

### 8.1 What Is DAX? { .powerbi-h3 }

DAX stands for Data Analysis Expressions.

It is the formula language used in Power BI for:

- aggregations
- filtering
- business logic
- time intelligence
- ranking
- calculated columns
- measures

It is one of the most important interview topics in Power BI.

### 8.2 Why DAX Matters { .powerbi-h3 }

A large number of Power BI interview questions come from:

- DAX
- data modeling

Power BI contains more than 200 DAX functions.

### 8.3 New Column vs New Measure vs New Table { .powerbi-h3 }

New Column:

- creates a new calculated column
- evaluates row by row
- stored in the model
- increases memory usage

New Measure:

- does not create a physical column
- calculates results dynamically
- appears in the fields list
- is usually better for aggregations
- generally requires less memory than a calculated column

New Table:

- creates a new table using DAX
- can be used for helper tables, manual entry, or calculations

Quick Measure:

- helps create measures through a guided interface
- useful for beginners and standard patterns

### 8.4 Implicit vs Explicit Measures { .powerbi-h3 }

Implicit measure:

- created automatically when you drag a numeric field into a visual and Power BI applies `Sum`, `Count`, or similar aggregation

Explicit measure:

- created manually using `New Measure`
- recommended for reusable business logic

### 8.5 Naming Rules { .powerbi-h3 }

Important naming behavior:

- a new measure name must be unique across the entire model
- you cannot use the same measure name as a column in another table
- a new column name must be unique only within the same table
- the same column name can exist in a different table

### 8.6 Basic DAX Examples { .powerbi-h3 }

New column example:

```DAX
Full Name = Customers[FirstName] & " " & Customers[LastName]
```

New measure example:

```DAX
Total Sales = SUM(Sales[SalesAmount])
```

Conditional measure:

```DAX
High Sales Flag =
IF([Total Sales] > 100000, "High", "Normal")
```

Safe division:

```DAX
Profit Margin = DIVIDE([Total Profit], [Total Sales], 0)
```

## 9. Common DAX Function Categories { .powerbi-h2 }

### 9.1 Aggregation Functions { .powerbi-h3 }

- `SUM()`: adds values in a column
- `AVERAGE()`: returns the mean
- `MIN()`: returns the smallest value
- `MAX()`: returns the largest value

Example:

```DAX
Average Sales = AVERAGE(Sales[SalesAmount])
```

### 9.2 Filter Functions { .powerbi-h3 }

- `FILTER()`: returns a filtered table
- `ALL()`: removes filters
- `CALCULATE()`: changes filter context and evaluates an expression

Example:

```DAX
West Region Sales =
CALCULATE(
    SUM(Sales[SalesAmount]),
    Sales[Region] = "West"
)
```

### 9.3 Logical Functions { .powerbi-h3 }

- `IF()`: conditional logic
- `SWITCH()`: cleaner multi-condition logic
- `AND()`: multiple conditions
- `OR()`: multiple conditions
- `||`: OR operator

Example:

```DAX
Sales Category =
SWITCH(
    TRUE(),
    [Total Sales] >= 100000, "Excellent",
    [Total Sales] >= 50000, "Good",
    "Needs Attention"
)
```

### 9.4 Time Intelligence Functions { .powerbi-h3 }

- `TODAY()`
- `NOW()`
- `DATESYTD()`
- `PREVIOUSMONTH()`

Example:

```DAX
YTD Sales =
CALCULATE(
    [Total Sales],
    DATESYTD('Date'[Date])
)
```

Important:

- time intelligence works best with a proper date table

### 9.5 Ranking Functions { .powerbi-h3 }

- `RANKX()`
- `TOPN()`

Example:

```DAX
Product Rank =
RANKX(
    ALL(Products[ProductName]),
    [Total Sales]
)
```

### 9.6 Text Functions { .powerbi-h3 }

- `CONCATENATE()`
- `LEFT()`
- `RIGHT()`

Example:

```DAX
State Code = LEFT(Customers[StateName], 2)
```

### 9.7 Mathematical Functions { .powerbi-h3 }

- `ROUND()`
- `DIVIDE()`

Example:

```DAX
Rounded Sales = ROUND([Total Sales], 2)
```

## 10. Filter Context and Row Context { .powerbi-h2 }

### 10.1 Row Context { .powerbi-h3 }

Row context means a calculation is evaluated one row at a time.

Common in:

- calculated columns
- iterators like `SUMX()`

### 10.2 Filter Context { .powerbi-h3 }

Filter context means the calculation result changes based on active filters from:

- slicers
- visuals
- page filters
- report filters
- `CALCULATE()`

This is one of the most important DAX concepts to understand deeply.

### 10.3 Practical Example { .powerbi-h3 }

If a card shows `Total Sales`, the result can change based on:

- selected year
- selected region
- selected product category

That happens because of filter context.

## 11. Power BI Service { .powerbi-h2 }

### 11.1 What Is Power BI Service? { .powerbi-h3 }

Power BI Service is the cloud platform used for:

- publishing reports
- sharing dashboards
- collaboration
- scheduling refresh
- workspace-based access

You usually build reports in Power BI Desktop and publish them to Power BI Service.

### 11.2 Why It Matters { .powerbi-h3 }

Power BI Service is important because reports are rarely useful if they stay only on a local laptop.

This is where teams:

- consume reports
- collaborate on dashboards
- control access
- distribute content to business users

### 11.3 Typical Flow { .powerbi-h3 }

1. build report in Power BI Desktop
2. validate data and visuals
3. publish to Power BI Service
4. share with workspace users or app users
5. manage refresh and permissions

## 12. Power BI vs Tableau { .powerbi-h2 }

### 12.1 Functional Equivalents { .powerbi-h3 }

| Power BI | Tableau Equivalent | Use |
|----------|--------------------|-----|
| New Measure | Aggregated Calculated Field | dynamic aggregated calculations |
| New Column | Row-Level Calculated Field | row-level computation |
| New Table | LOD or Joins based approach | no exact direct equivalent |
| Quick Measure | Pre-built table calculations | standard calculation patterns |
| Slicer | Quick Filter | interactive filtering |
| Bookmark | Story or saved states concept | guided report views |
| Power BI Service | Tableau Server / Tableau Public | sharing and publishing |

### 12.2 Tableau Reference Notes { .powerbi-h3 }

Useful Tableau comparisons:

- Tableau Desktop: for creating visualizations
- Tableau Server: for sharing and collaborating
- Tableau Prep: for data preparation and cleaning

In Tableau:

- Dimensions are categorical columns
- Measures are numerical columns

### 12.3 Strength Comparison { .powerbi-h3 }

Tableau is often seen as stronger in advanced and statistical charts such as:

- Gantt chart
- Box plot
- motion-style analysis

Power BI is often stronger in business-focused visuals such as:

- KPI
- Decomposition Tree
- Gauge chart

## 13. Important Developer and Analyst Best Practices { .powerbi-h2 }

### 13.1 Modeling Best Practices { .powerbi-h3 }

- prefer star schema where possible
- keep dimensions clean and descriptive
- avoid unnecessary many-to-many relationships
- validate relationships manually
- create reusable explicit measures

### 13.2 Report Design Best Practices { .powerbi-h3 }

- choose visuals intentionally
- avoid cluttered dashboards
- maintain consistent colors and labels
- use slicers carefully
- highlight the most important KPIs first

### 13.3 Performance Best Practices { .powerbi-h3 }

- prefer measures over too many calculated columns
- reduce unnecessary columns in the model
- disable load for staging queries when appropriate
- use proper data types
- keep the model simple

### 13.4 Refresh Best Practices { .powerbi-h3 }

- use clean source tables
- define stable keys
- structure Excel sources as tables
- document business definitions of measures
- test refresh after every important model change

## 14. Interview-Focused Topics { .powerbi-h2 }

### 14.1 Most Important Topics { .powerbi-h3 }

If you are preparing for interviews, focus strongly on:

- DAX
- data modeling
- star schema
- fact vs dimension
- implicit vs explicit measures
- Power Query transformations
- Power BI Service
- report performance basics

### 14.2 Common Interview Questions { .powerbi-h3 }

- What is the difference between a calculated column and a measure?
- What is star schema and why is it preferred?
- What is the difference between fact and dimension tables?
- What is `CALCULATE()` used for?
- What is filter context?
- When would you use append vs merge?
- What is the purpose of Power BI Service?
- Why are measures preferred over too many calculated columns?

## 15. End-to-End Example Workflow { .powerbi-h2 }

### 15.1 Sales Dashboard Example { .powerbi-h3 }

Suppose you are building a sales dashboard for a company.

Step 1: Import data

- sales data from Excel
- product data from SQL
- target data from CSV

Step 2: Clean data in Power Query

- fix data types
- remove null rows
- standardize column names
- append monthly files if needed

Step 3: Build data model

- `Sales` as fact table
- `Products`, `Customers`, `Date`, `Region` as dimension tables
- create one-to-many relationships

Step 4: Create DAX measures

- `Total Sales`
- `Total Profit`
- `Profit Margin`
- `YTD Sales`

Step 5: Build report pages

- executive summary page
- product analysis page
- regional performance page

Step 6: Publish to Power BI Service

- schedule refresh
- share with business users
- manage access

## 16. Quick Revision Notes { .powerbi-h2 }

- Power Query is for extraction, cleaning, and transformation
- Power Pivot is for modeling and DAX
- Power View is for reporting and visualization
- DAX and data modeling are the most important interview areas
- always validate relationships manually
- measures are generally better than calculated columns for reusable aggregations
- Power BI Service is used for publishing and collaboration
- star schema is usually the preferred model pattern
- append stacks tables, merge joins tables
- choose visuals based on the business question

## 17. Final Summary { .powerbi-h2 }

Power BI is not just a charting tool. It is a complete BI development platform that covers:

- data connection
- ETL through Power Query
- modeling through relationships and schema design
- business logic with DAX
- dashboarding through report visuals
- sharing through Power BI Service

For developer and analyst roles, strong Power BI skills usually come from mastering three things:

1. clean data preparation
2. solid data modeling
3. reusable DAX measures
