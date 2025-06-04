# Tableau Project README: Customer Loan Analysis

## 📁 Datasets Used
1. **Branch Data.csv**
2. **Customer Data.csv**
3. **Loan Transactions Data.csv**

## 🔗 Data Relationships Setup in Tableau

### Step 1: Load the Data
- Open Tableau Desktop or Tableau Public
- Load all three CSV files using `Data → New Data Source → Text File`

### Step 2: Define Relationships (Recommended)
- Drag `Loan Transactions Data` to the canvas first
- Drag `Customer Data` on top of it
- Tableau prompts for relationship setup:
  ```
  Customer ID (Loan Transactions) = Customer ID (Customer Data)
  ```
- Drag `Branch Data` on top of `Customer Data` next:
  ```
  Branch ID (Customer Data) = Branch ID (Branch Data)
  ```

✅ These are logical relationships, which Tableau resolves at visualization time. This prevents unnecessary row duplication or loss.

---

## 📊 Charts to Build Using Existing Fields

### 1. Bar Chart: Total Loan Amount by Region
- **X-axis**: `Region` (Branch Data)
- **Y-axis**: `SUM(Loan Amount)` (Loan Data)
- Connection via `Branch ID`

### 2. Line Chart: Loan Applications Over Time
- **X-axis**: `Application Date` (Loan Data)
- **Y-axis**: `COUNT(Transaction ID)` or `SUM(Loan Amount)`
- Use `MONTH()` on `Application Date` for time trend

### 3. Pie Chart: Loan Type Distribution
- **Slice Size**: `SUM(Loan Amount)`
- **Color**: `Type of Loan` (Loan Data)
- Marks Card → Set to `Pie`
- Label → Use `% of Total`

### 4. Scatter Plot: Age vs Loan Amount
- **X-axis**: `Age` (Customer Data)
- **Y-axis**: `Loan Amount` (Loan Data)
- Relationship via `Customer ID`
- Drag `Age` to Columns and `Loan Amount` to Rows

### 5. Heat Map: Risk Level vs Loan Type
- **Rows**: `Risk Level` (Customer Data)
- **Columns**: `Type of Loan` (Loan Data)
- **Color**: `SUM(Loan Amount)`
- Use `Marks → Square` and apply color gradients

---

## 📌 Best Practices

- Prefer **Relationships** over **Joins** to handle data at different levels of granularity.
- Use **filters** like `Risk Level`, `Branch`, or `Loan Type` in dashboards for interactivity.
- Check `Data Type` for fields like dates (convert string to date if needed).
- Use `DATETRUNC()` or `DATEPART()` for time-based grouping in charts.

---

## 🎯 Advanced Enhancements

- Add calculated fields like:
  - `Loan to Age Ratio = [Loan Amount] / [Age]`
  - `Loan Category = IF [Loan Amount] > 500000 THEN 'High' ELSE 'Normal' END`

- Dashboard actions:
  - Filter by Branch
  - Highlight by Risk Level

- Formatting:
  - Clean tooltips
  - Use consistent color palette for dimensions (e.g., Risk Level)

---

## ✅ Result
This setup ensures data is properly related across sources, and enables you to build reliable, interactive dashboards without data loss or distortion.
