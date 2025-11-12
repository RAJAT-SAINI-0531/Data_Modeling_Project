# Global Super Store Data Modeling & Analysis Project

![MySQL](https://img.shields.io/badge/mysql-4479A1.svg?style=for-the-badge&logo=mysql&logoColor=white)
![Tableau](https://img.shields.io/badge/Tableau-E97627?style=for-the-badge&logo=Tableau&logoColor=white)
![Microsoft Excel](https://img.shields.io/badge/Microsoft_Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)

## 📋 Project Overview

This comprehensive data modeling project transforms Global Super Store's business operations data from a flat Excel structure into a robust, normalized MySQL database system. The project encompasses complete database design, implementation, dimensional modeling, and advanced business intelligence analytics using Tableau.

### 🎯 Business Objectives
- **Database Modernization**: Convert legacy Excel-based data storage to a professional MySQL RDBMS
- **Data Normalization**: Design normalized database schema following 3NF principles
- **Dimensional Modeling**: Create star and snowflake schemas for analytical processing
- **Business Intelligence**: Develop interactive dashboards and visualizations for strategic decision-making
- **Performance Analytics**: Enable comprehensive sales, profit, and trend analysis

## 🔍 Project Scope & Dataset Analysis

### 📊 Raw Data Specifications
- **Data Source**: `Excel File.xlsx` (7.67 MB)
- **Total Records**: 51,290 orders
- **Data Columns**: 24 comprehensive attributes
- **Geographic Coverage**: Global operations with detailed regional breakdowns
- **Time Span**: Multi-year transaction history
- **Data Quality**: High-quality dataset with minimal null values (only 19.5% missing postal codes)

### 📈 Data Schema Overview

| Attribute | Data Type | Description | Business Context |
|-----------|-----------|-------------|------------------|
| `Row ID` | Integer | Unique record identifier | Primary indexing |
| `Order ID` | String | Business order reference | Transaction tracking |
| `Order Date` | Date | Order placement timestamp | Temporal analysis |
| `Ship Date` | Date | Order fulfillment date | Logistics performance |
| `Ship Mode` | String | Delivery method | Shipping optimization |
| `Customer ID` | String | Customer unique identifier | CRM integration |
| `Customer Name` | String | Customer full name | Personalization |
| `Segment` | String | Customer classification | Market segmentation |
| `City` | String | Customer city location | Geographic targeting |
| `State` | String | Customer state/province | Regional analysis |
| `Country` | String | Customer country | International operations |
| `Postal Code` | Float | ZIP/postal code | Demographic analysis |
| `Market` | String | Market region classification | Strategic planning |
| `Region` | String | Geographic region | Territory management |
| `Product ID` | String | Product unique identifier | Inventory management |
| `Category` | String | Product primary category | Portfolio analysis |
| `Sub-Category` | String | Product sub-classification | Detailed segmentation |
| `Product Name` | String | Complete product description | Catalog management |
| `Sales` | Float | Revenue amount (USD) | Financial performance |
| `Quantity` | Integer | Units sold | Volume analysis |
| `Discount` | Float | Applied discount rate | Pricing strategy |
| `Profit` | Float | Profit margin (USD) | Profitability analysis |
| `Shipping Cost` | Float | Logistics expense (USD) | Cost optimization |
| `Order Priority` | String | Business priority level | Service level management |

## 🏗️ Database Architecture & Design

### 1️⃣ Normalized Database Schema (OLTP)

#### **Entity-Relationship Design**
- **File**: `ER_Diagram_Global_Super_Store.mwb` (11.67 KB)
- **Backup**: `ER_Diagram_Global_Super_Store.mwb.bak` (11.67 KB)
- **Visual Reference**: `ER - Global Super Store.png`

#### **Normalization Principles**
- **First Normal Form (1NF)**: Eliminated repeating groups and ensured atomic values
- **Second Normal Form (2NF)**: Removed partial dependencies on composite keys
- **Third Normal Form (3NF)**: Eliminated transitive dependencies

#### **Key Entity Tables**
1. **Customers Table**
   - Primary Key: Customer_ID
   - Attributes: Name, Segment, Geographic details
   
2. **Products Table**
   - Primary Key: Product_ID
   - Attributes: Name, Category, Sub-Category
   
3. **Orders Table**
   - Primary Key: Order_ID
   - Foreign Keys: Customer_ID, Product_ID
   - Attributes: Dates, Priority, Quantities
   
4. **Geography Table**
   - Primary Key: Location_ID
   - Attributes: City, State, Country, Region, Market
   
5. **Transactions Table**
   - Composite Key: Order_ID + Product_ID
   - Financial metrics: Sales, Profit, Discount, Shipping Cost

#### **Database Implementation**
- **Implementation Method**: MySQL Workbench Forward Engineering
- **Visual Documentation**: `Forward Engineer - Global Super.png`
- **Server Deployment**: Automated schema creation and table generation

### 2️⃣ Dimensional Data Models (OLAP)

#### **Star Schema Architecture**
- **File Reference**: `Star Schema Global Super.jpg`
- **Design Purpose**: Optimized for analytical queries and reporting
- **Structure**: Central fact table surrounded by dimension tables

**Fact Table**: Sales_Fact
- Measures: Sales, Profit, Quantity, Discount, Shipping_Cost
- Foreign Keys: Time_Key, Product_Key, Customer_Key, Geography_Key

**Dimension Tables**:
- **Time_Dimension**: Date hierarchies (Year, Quarter, Month, Day)
- **Product_Dimension**: Product catalog information
- **Customer_Dimension**: Customer demographics and segmentation
- **Geography_Dimension**: Location hierarchies and regional data

#### **Snowflake Schema Architecture**
- **File Reference**: `Snowflake Schema Global Super.jpg`
- **Design Purpose**: Normalized dimensional model for storage optimization
- **Structure**: Normalized dimension tables with sub-dimensions

**Enhanced Features**:
- **Product Hierarchy**: Category → Sub-Category → Product
- **Geographic Hierarchy**: Country → Region → State → City
- **Time Hierarchy**: Year → Quarter → Month → Week → Day
- **Customer Hierarchy**: Market → Segment → Individual Customer

## 📊 Business Intelligence & Analytics

### 🎨 Tableau Workbook Analysis
- **Primary File**: `Tableau Global Super Store.twbx` (1.69 MB)
- **Comprehensive Dashboard**: `Sales & Profits in USA.png`

### 📍 Geographic Sales Analysis (Map Visualization)

**Visualization Features**:
- **Interactive US State Map**: Color-coded by sales performance
- **Hover Functionality**: State name and sales figures display
- **Geographic Insights**: Regional performance identification
- **Business Value**: Territory optimization and resource allocation

### 🔵 Profitability Analysis (Bubble Chart)

**Chart Specifications**:
- **Title**: "Profits in USA"
- **Bubble Size**: Represents profit magnitude
- **Interactive Elements**: 
  - State identification
  - Quantity sold metrics
  - Profit values
  - Shipping cost analysis
- **Business Applications**: Profitability assessment and cost optimization

### 📈 Sales Trend Analysis (Line Chart)

**Analytical Parameters**:
- **Title**: "Sales Trend in the USA"
- **Time Period**: 4-year historical analysis
- **Filter Criteria**: States with sales > $40,000
- **Trend Identification**: Growth patterns and seasonal variations
- **Strategic Value**: Forecasting and capacity planning

### 🖥️ Interactive Executive Dashboard

**Dashboard Components**:
- **Name**: "Sales and Profits in the USA"
- **Integration**: Combined map, bubble, and line visualizations
- **Interactivity**: Click-through state filtering
- **Real-time Updates**: Dynamic data refresh capabilities
- **Executive Reporting**: KPI monitoring and performance tracking

## 📁 Project File Structure

```
Data_Modeling_Project/
├── 📊 Data Sources/
│   └── Excel File.xlsx                          # Raw business data (51,290 records)
├── 🗄️ Database Models/
│   ├── ER_Diagram_Global_Super_Store.mwb       # MySQL Workbench model
│   ├── ER_Diagram_Global_Super_Store.mwb.bak   # Model backup
│   └── ER - Global Super Store.png             # ER diagram visualization
├── 📈 Dimensional Models/
│   ├── Star Schema Global Super.jpg            # Star schema design
│   └── Snowflake Schema Global Super.jpg       # Snowflake schema design
├── 📊 Business Intelligence/
│   ├── Tableau Global Super Store.twbx         # Complete Tableau workbook
│   └── Sales & Profits in USA.png              # Dashboard screenshot
├── 🔧 Implementation/
│   └── Forward Engineer - Global Super.png     # MySQL implementation process
└── 📖 Documentation/
    └── README.md                                # Project documentation
```

## 🛠️ Technical Implementation

### **Database Technologies**
- **RDBMS**: MySQL Server
- **Modeling Tool**: MySQL Workbench 8.0+
- **Data Source**: Microsoft Excel 2016+
- **File Format**: .xlsx with UTF-8 encoding

### **Analytics Technologies**
- **BI Platform**: Tableau Desktop/Server
- **Visualization Types**: Geographic maps, bubble charts, line graphs
- **Dashboard Framework**: Interactive multi-chart layouts
- **Data Connectivity**: Direct Excel integration

### **Design Methodologies**
- **Database Design**: Entity-Relationship Modeling (ERM)
- **Normalization**: Boyce-Codd Normal Form (BCNF) compliance
- **Dimensional Modeling**: Kimball methodology
- **Data Warehousing**: Star and Snowflake schema patterns

## 📋 Implementation Workflow

### **Phase 1: Data Analysis & Requirements**
1. **Excel Data Profiling**: Analyzed 51,290 records across 24 attributes
2. **Business Requirements**: Identified OLTP and OLAP needs
3. **Data Quality Assessment**: Evaluated completeness and consistency
4. **Stakeholder Interviews**: Gathered reporting requirements

### **Phase 2: Database Design**
1. **Conceptual Modeling**: Created high-level entity relationships
2. **Logical Design**: Developed normalized table structures
3. **Physical Implementation**: MySQL Workbench forward engineering
4. **Validation Testing**: Verified schema integrity and constraints

### **Phase 3: Dimensional Modeling**
1. **Star Schema**: Designed fact and dimension tables
2. **Snowflake Schema**: Created normalized dimensional hierarchies
3. **Performance Optimization**: Implemented indexing strategies
4. **Data Mart Creation**: Specialized subject area models

### **Phase 4: Business Intelligence Development**
1. **Data Connection**: Established Tableau-Excel integration
2. **Visualization Design**: Created interactive charts and maps
3. **Dashboard Assembly**: Combined visualizations into cohesive interface
4. **User Acceptance Testing**: Validated with business stakeholders

## 🎯 Business Impact & Outcomes

### **Operational Improvements**
- **Data Integrity**: Eliminated redundancy through normalization
- **Query Performance**: Optimized structure for analytical processing
- **Scalability**: Designed for future data volume growth
- **Maintenance**: Reduced data management complexity

### **Analytical Capabilities**
- **Geographic Insights**: State-level sales performance analysis
- **Profitability Analysis**: Multi-dimensional profit evaluation
- **Trend Identification**: Historical pattern recognition
- **Interactive Reporting**: Self-service analytics for stakeholders

### **Strategic Advantages**
- **Decision Support**: Data-driven strategic planning
- **Market Intelligence**: Regional performance optimization
- **Resource Allocation**: Evidence-based investment decisions
- **Competitive Advantage**: Advanced analytics capabilities

## 🔍 Key Performance Indicators (KPIs)

### **Sales Metrics**
- **Total Revenue**: Multi-million dollar transaction volume
- **Geographic Distribution**: Comprehensive US state coverage
- **Product Performance**: Category and sub-category analysis
- **Seasonal Trends**: Time-based pattern identification

### **Profitability Metrics**
- **Gross Profit Margins**: Product-line profitability analysis
- **Regional Profitability**: Geographic profit distribution
- **Customer Profitability**: Segment-based profit evaluation
- **Cost Analysis**: Shipping and discount impact assessment

### **Operational Metrics**
- **Order Processing**: Fulfillment time analysis
- **Shipping Efficiency**: Mode and cost optimization
- **Customer Segmentation**: Behavioral pattern analysis
- **Inventory Performance**: Product velocity tracking

## 📚 Technical Documentation

### **Database Schema Scripts**
Generated through MySQL Workbench Forward Engineering:
- Table creation statements with proper constraints
- Index definitions for performance optimization
- Foreign key relationships for data integrity
- View definitions for common query patterns

### **Data Dictionary**
Complete attribute documentation including:
- Data types and constraints
- Business rules and validation logic
- Relationship mappings
- Performance considerations

### **Tableau Workbook Structure**
- Data source connections and refresh schedules
- Calculated field definitions and formulas
- Dashboard action configurations
- Filter and parameter specifications

## 🔄 Future Enhancement Opportunities

### **Technical Improvements**
- **Real-time Integration**: ETL pipeline for live data updates
- **Cloud Migration**: AWS/Azure database hosting
- **API Development**: RESTful services for data access
- **Mobile Analytics**: Responsive dashboard design

### **Analytical Enhancements**
- **Predictive Modeling**: Machine learning integration
- **Advanced Segmentation**: Customer lifetime value analysis
- **Market Basket Analysis**: Cross-selling optimization
- **Forecasting Models**: Demand prediction algorithms

### **Business Intelligence Expansion**
- **Executive Scorecards**: KPI monitoring dashboards
- **Operational Dashboards**: Real-time performance tracking
- **Self-Service Analytics**: User-friendly report builders
- **Automated Alerting**: Exception-based notifications

## 🏆 Project Success Metrics

### **Technical Achievements**
- ✅ Successfully normalized 51,290 records into 3NF-compliant schema
- ✅ Implemented both OLTP and OLAP data models
- ✅ Created interactive business intelligence platform
- ✅ Delivered comprehensive documentation and visualizations

### **Business Value Delivered**
- ✅ Enabled data-driven decision making across organization
- ✅ Provided geographic sales insights for territorial planning
- ✅ Delivered profitability analysis for strategic optimization
- ✅ Created scalable foundation for future analytics expansion

---
<div align="center">

---

### 🛠️  Developed by **Rajat Saini**

---
</div> 
<br><br>

**Step 1: Create an ER diagram**

- Your first task is to use the visual data modeling tool in MySQL Workbench to create a suitable ER diagram for the Global Super Store. 
- Make use of the data fields within the company Excel file as stated in the scenario. Feel free to add more entities and attributes if required. Make sure that your tables are normalized to conform with the three fundamental normal forms.
- The following ER diagram illustrates an adequate relational schema for Global Super Store’s database :

![image](ER_GlobalSuperStore.png)


**Step 2: Implement the data model**
- Use MySQL Workbench’s forward engineer feature to implement the Global Super Store data model inside the MySQL server.
- You need to select that Database tab, then select the forward engineer method in MySQL Workbench to implement Global Super Store’s data model inside the MySQL server as shown below.

![image](https://github.com/himanshu1295/Data_Modeling_Project/assets/106751126/cdc7b908-69b4-4b65-a523-8e5ac1c45587)

- Once you have completed the required steps using the wizard, you need to carry out the final Commit Progress step to confirm that each task was executed.
- Click Close to close the wizard. The new database schema should now be created in the MySQL server as shown below :
![image](https://github.com/himanshu1295/Data_Modeling_Project/assets/106751126/f4e877bc-169b-4592-ac55-26a338079a64)

**Step 3: Create a Star and Snowflake Schema**

- The marketing department at the Global Super Store Company wants to build a campaign to promote the company’s products within the USA. 
- First, they need to understand the company’s performance in this market by analyzing their sales data. They are interested in data related to products, locations and times only. 
- Help them out by creating a Star schema that includes relevant fact and dimensions tables with relevant attributes and data types.
- The following ER diagram illustrates an adequate Star schema for a Global Super Store dimensional data model :

![Star Schema Global Super](https://github.com/himanshu1295/Data_Modeling_Project/assets/106751126/8d6a74d5-ddfe-477f-84bd-8535252c650c)

- The following ER diagram illustrates an adequate Snowflake schema for a Global Super Store dimensional data model :

![Snowflake Schema Global Super](https://github.com/himanshu1295/Data_Modeling_Project/assets/106751126/0db49d19-cc17-4317-8bec-794c4b9a392e)

**Step 4: Create a map chart**

- Use Tableau to investigate Global Super Store’s sales in the USA. Create a map chart that shows sales in different states within the USA. 

- If you roll over a state, then you should be able to view the state name and sales figure as shown below :

![image](https://github.com/himanshu1295/Data_Modeling_Project/assets/106751126/044b8eb4-f22c-4af0-8d4d-85aa2924c297)

**Step 5: Create a bubble chart**

The Global Super Store needs to check its profits within the USA. To help them out, create a bubble chart in Tableau. Call it “Profits in USA”. 

If you roll over a bubble, you should be able to view the following information, as shown in the screenshot below:
- State name,
- Quantity sold,
- Profits,
- and shipping cost.

Your chart should look similar to the following example:

![image](https://github.com/himanshu1295/Data_Modeling_Project/assets/106751126/15b3d78f-dbc4-49f5-9e7e-252a0ff2316d)

**Step 6: Create a line chart**

- The Global Super Store wants to view sales trends in the USA over the last 4 years. Create a line chart in Tableau for states with Sales of more than $40000. Call it “Sales Trend in the USA”, as shown below :

![image](https://github.com/himanshu1295/Data_Modeling_Project/assets/106751126/3ed6d663-b85c-418b-b8c3-603c0f46e19d)

**Step 7: Create an interactive dashboard**

- Create an interactive dashboard that includes the charts produced in tasks 4, 5 and 6. Name it ‘Sales and Profits in the USA’. If you click on a state, you should be able to view relevant sales and profits information as shown below :

![image](https://github.com/himanshu1295/Data_Modeling_Project/assets/106751126/eb86b61f-84b7-4fd0-8251-6e5342dbbe2e)

## Conclusion

I have created an ER diagram for Global Super Store and used MySQL Workbench’s Forward Engineer feature to implement the ER diagram in a MySQL database. I have also developed a dimensional data model for the Global Super Store. I have also analyzed data with relevant charts using Tableau and built an interactive dashboard.
<br><br>
