# Infosys Financial Statement Analysis (FY2023–FY2026)

An end-to-end financial statement analysis project on **Infosys Limited** covering FY2023 to FY2026. The project uses Python and Pandas for data preparation, Excel for structured financial data, and Power BI with DAX for interactive analysis and visualization.

The objective is to understand the company's financial performance and position across four financial years, identify important movements, and communicate the findings in a clear business context.

---

## Project at a glance

| Item | Details |
|---|---|
| Company | Infosys Limited |
| Period covered | FY2023–FY2026 |
| Financial statements | Income Statement, Balance Sheet and Cash Flow Statement |
| Reporting unit | ₹ crore, except EPS and ratios |
| Data preparation | Python, Pandas and NumPy in Google Colab |
| Reporting and visualization | Microsoft Power BI and DAX |

## Business objectives

- Review revenue, expenses, profit before tax and net profit over the four-year period.
- Measure revenue growth, net profit margin, effective tax rate and earnings per share.
- Examine assets, equity, liabilities, liquidity and working capital.
- Analyze operating, investing and financing cash flows, along with free cash flow.
- Present the results through an interactive Power BI dashboard and summarize the business implications.

## Repository structure

The repository is organized into four working folders:

```text
Infosys-Financial-Statement-Analysis/
│
├── README.md
├── Data/
│   ├── Raw/
│   │   └── Infosys_Raw_Financial_Data.xlsx
│   └── Processed/
│       └── Infosys_Cleaned_Financial_Data.xlsx
│
├── Documents/
│   ├── Project_Process_and_Financial_Analysis.docx
│   └── DAX_Measures_Documentation.docx
│
├── Notebook/
│   └── Infosys_Data_Cleaning.ipynb
│
└── Visuals/
    ├── Executive_Overview.png
    ├── Profitability_Analysis.png
    ├── Financial_Health_Cash_Flow.png
    ├── Expense_Breakdown.png
    └── Infosys_Financial_Analysis.pbix
```

> The names above are suggested filenames. Keep the folder names shown here, and update the filenames or links in this README if your saved files use different names. The `.pbix` file is the Power BI report; the screenshots are preview images.

## Tools and technologies

- **Python** – used to load, inspect and prepare the financial dataset.
- **Google Colab** – notebook environment used for the Python workflow.
- **Pandas** – used to read Excel data, inspect records, clean fields and validate the dataset.
- **NumPy** – used for numerical and missing-value operations.
- **Microsoft Excel** – used to retain the original and cleaned financial data in workbook format.
- **Power BI Desktop** – used to build the interactive financial dashboard.
- **DAX** – used to calculate financial measures and ratios.

## Project workflow

### 1. Data collection and understanding

The source workbook, `Infosys_Raw_Financial_Data.xlsx`, contains separate raw statement sheets and a consolidated `RAW_ALL_DATA` sheet. The consolidated sheet was used for the analysis.

The dataset contains 521 rows and 12 original columns. These include the financial year, statement type, reported section and line item, source note, raw reported value, unit, source PDF, report page and PDF page references, official source URL and data notes.

### 2. Data preparation in Python

The workbook was loaded in Google Colab using Pandas. The consolidated data was read from `RAW_ALL_DATA`, using the fourth row of the worksheet as the header (`header=3`) to skip the introductory metadata rows.

The reported financial values were stored as text. A numeric `Value_Cr` field was created by removing thousands separators, converting parentheses to negative signs, and converting the result to a numeric type. The original reported text field was retained so that the cleaned values could be traced back to the source representation.

Examples of the conversion logic:

| Original text | Numeric value |
|---|---:|
| `146,767` | 146767 |
| `(73)` | -73 |
| `(7,076)` | -7076 |

Data checks performed during preparation included missing-value review, duplicate checks, numeric conversion checks, and record counts by financial year and statement. Four missing section labels were filled in the working DataFrame as `Attribution / comprehensive income`. Sixteen blank line-item labels representing unlabeled subtotals were retained rather than guessed.

### 3. Power BI model and measures

The cleaned workbook was imported into Power BI. The table was named `Sheet1`. DAX measures were created for revenue, profit, profitability ratios, balance-sheet liquidity and cash-flow analysis. Financial-year selection was used to let report users examine individual years and compare trends.

### 4. Dashboard development

The report contains four pages:

| Page | Main analysis |
|---|---|
| **Executive Overview** | Total revenue, net profit, PBT, net profit margin, revenue trend, net profit trend and expenses versus revenue |
| **Profitability Analysis** | Revenue growth, net profit margin, effective tax rate, basic and diluted EPS, and profitability comparison |
| **Financial Health & Cash Flow** | Total assets versus total equity and liabilities, current ratio, working capital, operating cash flow, investing and financing cash flows, and free cash flow |
| **Expense Breakdown** | Donut chart of expense categories with a financial-year slicer synchronized to the Executive Overview page |

## Selected financial results

The following values are taken from the consolidated financial data used in the project. Amounts are in ₹ crore.

| Metric | FY2023 | FY2024 | FY2025 | FY2026 |
|---|---:|---:|---:|---:|
| Revenue from operations | 146,767 | 153,670 | 162,990 | 178,650 |
| Profit before tax | 33,322 | 35,988 | 37,608 | 39,995 |
| Profit for the year | 24,108 | 26,248 | 26,750 | 29,474 |
| Net profit margin | 16.43% | 17.08% | 16.41% | 16.49% |
| Revenue growth | — | 4.71% | 6.07% | 9.61% |
| Effective tax rate | 27.65% | 27.07% | 28.87% | 26.31% |
| Basic EPS (₹ per share) | 57.63 | 63.39 | 64.50 | 71.58 |
| Diluted EPS (₹ per share) | 57.54 | 63.29 | 64.34 | 71.46 |

### Initial observations

- Revenue from operations increased from ₹146,767 crore in FY2023 to ₹178,650 crore in FY2026, an increase of approximately **21.7%**.
- Annual revenue growth accelerated over the period: 4.71% in FY2024, 6.07% in FY2025 and 9.61% in FY2026.
- Net profit increased from ₹24,108 crore to ₹29,474 crore, an increase of approximately **22.3%**.
- Net profit growth was uneven: approximately 8.9% in FY2024, 1.9% in FY2025 and 10.2% in FY2026. FY2025 is therefore a useful year for further investigation.
- Net profit margin peaked at 17.08% in FY2024, fell to 16.41% in FY2025 and was 16.49% in FY2026.
- Basic EPS increased from ₹57.63 in FY2023 to ₹71.58 in FY2026.

These observations describe movements in the financial statements. They do not, by themselves, establish the operational causes behind those movements.

## Financial health and cash flow observations

The dashboard shows a current ratio of approximately 1.81, 2.31, 2.27 and 1.98 from FY2023 to FY2026. Working capital is shown at approximately ₹31,700 crore, ₹50,600 crore, ₹54,200 crore and ₹51,200 crore, respectively.

The dashboard's rounded chart labels indicate operating cash flow of approximately ₹22,000 crore, ₹25,000 crore, ₹36,000 crore and ₹34,000 crore across FY2023–FY2026. Free cash flow is shown at approximately ₹19,900 crore, ₹23,000 crore, ₹33,500 crore and ₹34,000 crore. These cash-flow values are approximate readings from the dashboard labels and should be reconciled to the underlying statement rows before being treated as exact figures.

The current ratio remained above 1 in each year shown, while declining from its FY2024 high to 1.98 in FY2026. Working capital also declined slightly in FY2026 after increasing through FY2025. These movements are worth monitoring, but do not alone establish a liquidity problem.

## Recommendations for further analysis

1. Investigate the FY2025 slowdown in net profit growth by reviewing the movement in operating expenses, other income and tax expense.
2. Monitor employee benefit expenses alongside revenue growth and productivity indicators. Employee costs are a major component of the expense base.
3. Review the FY2026 movement in current ratio and working capital by examining the individual current-asset and current-liability components.
4. Reconcile operating cash flow and free cash flow to the detailed cash-flow statement, including working-capital movements and capital expenditure.
5. Review the detailed investing and financing cash-flow line items before attributing large outflows to specific activities such as acquisitions, dividends, buybacks or repayments.

## Data quality and interpretation notes

The following checks should be completed before using every dashboard visual as a final stakeholder figure:

- **Expense donut:** The screenshot shows a four-year donut total of approximately ₹529.41K, while the four-year Income Statement total expenses sum to ₹509,209 crore. The donut must be filtered to `Statement = Income Statement` and reconciled to the source before its category percentages are treated as final. Similar depreciation labels from different statements can otherwise be counted together.
- **EPS chart:** Confirm that FY2026 appears in the visual. The source data used in this project contains FY2026 basic EPS of ₹71.58 and diluted EPS of ₹71.46.
- **Operating cash flow chart:** Ensure the fiscal years are sorted chronologically (FY2023, FY2024, FY2025, FY2026).
- **Cash-flow values:** Use the underlying unrounded values for final reporting rather than reading rounded chart labels.
- **Balance-sheet comparison:** Total assets should equal total equity and liabilities. This is the accounting identity represented by the comparison chart, not an independent measure of two unrelated totals.

## Documentation

The `Documents` folder is intended to contain:

- **Project Process and Financial Analysis** – workflow, data cleaning, dashboard development, findings and recommendations.
- **DAX Measures Documentation** – measure definitions, formulas, calculation logic and validation.

The `Notebook` folder contains the data-preparation notebook. The `Visuals` folder contains Power BI screenshots and the `.pbix` report file.

## How to use this project

1. Open the notebook in Google Colab or Jupyter to review the data-preparation workflow.
2. Check the raw and processed workbook versions in the `Data` folder.
3. Open the `.pbix` file in Power BI Desktop to explore the dashboard.
4. Use the financial-year slicer to review annual values and trends.
5. Refer to the documents for the methodology, DAX calculations and interpretation.

## Disclaimer

This project is an independent analytical exercise based on the Infosys financial data included with the repository. It is intended for learning, portfolio demonstration and financial-statement analysis. It is not investment advice. Figures and interpretations should be checked against the original annual reports before being used for external financial decisions.

---

## Author

**Project:** Infosys Financial Statement Analysis (FY2023–FY2026)  
**Focus:** Financial analysis, data preparation, Power BI dashboarding and DAX

Add your name, GitHub profile and LinkedIn profile here if you want them displayed in the repository.
