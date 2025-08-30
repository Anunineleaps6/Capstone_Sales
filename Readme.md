## Capstone Sales

# Sales Funnel Analytics

## 📌 Project Overview
The **Sales Funnel Analytics** project aims to provide a structured, data-driven solution for monitoring and optimizing the lead-to-deal conversion process. By integrating CRM data, the project will enable the sales team to gain clear visibility into funnel performance, identify inefficiencies, and make informed decisions that drive higher conversion rates and shorter sales cycles.

---

## 🎯 Objectives
- Map the **lead-to-deal sales funnel**
- Track and visualize **funnel performance metrics**
- Identify **bottlenecks, drop-off points, and performance variances**
- Automate **sales reporting** for business stakeholders
- Generate **actionable recommendations** for improving conversions

---

## 🗂️ Funnel Stages
The sales funnel will be tracked through the following stages:

1. **Lead** – Raw prospect entry into CRM  
2. **Contacted** – Sales team initiates contact  
3. **Demo** – Product demonstration scheduled or completed  
4. **Proposal** – Commercial proposal shared with lead  
5. **Deal/Lost** – Final outcome recorded (won or lost)  

---

## ⚙️ Key Features
- **CRM Data Integration** – Connects with CRM (e.g., HubSpot export, CSV files)  
- **Funnel Visualization** – Provides insights into stage-level performance  
- **Drop-off Analysis** – Detects high-loss stages and areas for improvement  
- **Automated Reporting** – Delivers dashboards and reports to stakeholders  
- **Actionable Insights** – Recommends strategies for better conversion  

---

## 🛠️ Tech Stack
- **Google Sheets** – Initial data staging  
- **Google App Script** – Data ingestion automation  
- **CRM Export (CSV/HubSpot)** – Source data  
- *(Future)* BI Tools (Looker, Power BI, Tableau) for dashboards  

---

## 📌 Expected Outcomes
- Improved **lead-to-deal conversion rates**  
- Shortened **sales cycle duration**  
- Enhanced **rep and regional performance visibility**  
- Streamlined **reporting and decision-making**  

## 📂 Project Structure

```plaintext
CAPSTONE_FINAL/
├── Generated_Data/                # Folder containing simulated/generated CRM data
├── Automation.ipynb               # Notebook for automation scripts (e.g., data ingestion, reporting)
├── CRM_Capstone.xlsx              # Raw CRM dataset in Excel format
├── CRM_Capstone_DB.sqlite         # SQLite database containing CRM records
├── CRM_Funnel_Stage_Results...    # Funnel stage performance output/results
├── Copy of Capstone_sales.ipynb   # Backup/duplicate analysis notebook
├── EDA.ipynb                      # Exploratory Data Analysis notebook
├── Sales Performance Repor...     # Sales performance reports (likely PDF/Excel)
├── Sales Performance Repor...     # Another report (possibly different version or region)
├── creds.json                     # Credentials file (for API/DB/Google Sheets access)
```
## 🛠️ Tech Stack
- **Google Colab** – Data analysis, cleaning, and notebooks  
- **SQLite** – Lightweight local database for CRM data  
- **BigQuery** – Scalable cloud data warehouse for queries and analytics  
- **Looker Studio** – Interactive dashboards and visualization  

---

## ⚙️ Installation & Setup

### 1. Google Colab
No installation needed — run notebooks directly in **[Google Colab](https://colab.research.google.com/)**.  

---

### 2. SQLite
SQLite is included with Python. Example usage in Colab or locally:

```python
import sqlite3

# Connect to CRM database
conn = sqlite3.connect("CRM_Capstone_DB.sqlite")
cursor = conn.cursor()
Install SQLite CLI on Linux/macOS (optional):
```
```bash
 sudo apt-get install sqlite3
```
### 3. BigQuery
Install client libraries in Colab:
```bash
  !pip install --upgrade google-cloud-bigquery
  !pip install --upgrade pandas-gbq
```

Authenticate:

python
```bash
  from google.colab import auth
  auth.authenticate_user()
```

### 4.Looker Studio
No installation required.

Steps:  
- Open Looker Studio.
- Connect to BigQuery dataset or Google Sheets (if staging is used).
- Build dashboards for funnel metrics, drop-offs, and sales performance.

### 5. Python Libraries

Required libraries for Colab environment:

```bash 
  !pip install pandas numpy matplotlib seaborn
  !pip install --upgrade google-cloud-bigquery pandas-gbq
```

## Capstone_sales.ipynb Results
# 📊 Sales Funnel Analytics – Execution Log

This document is a **cell-by-cell execution log** of the Capstone Sales Analytics notebook.  
For each executed code cell, we describe the output obtained without showing the raw code.  

---

## 🔹 Part 1: Environment Setup & Data Generation

### ✅ Mounting Google Drive
- **Action:** Mounted Google Drive to access project files.  
- **Output:**  
  - Drive successfully mounted at `/content/drive`.  
  - Files accessible for later ingestion.  

---

### ✅ Installing Dependencies
- **Action:** Installed required Python packages (e.g., `phonenumbers`).  
- **Output:**  
  - Installation completed without errors.  
  - Verified availability of library imports.  

---

### ✅ Lead Data Generation
- **Action:** Generated **2000 synthetic leads** with fields such as:  
  - Lead ID, Name, Company, Region, Rep, Source, Contact Info, Stage, Budget, Industry, Outcome.  

- **Output:**  
  - Displayed **first 5 rows** of leads dataset (sample preview).  
  - Displayed **last 5 rows** to confirm dataset completeness.  
  - Printed **total number of leads generated → 2000**.  

---

### 📊 Lead Outcome Distribution
- **Action:** Counted leads by outcome.  
- **Output:**  

  - Deal Lost → **840**  
  - Deal Won → **560**  
  - Ongoing - Cold → **562**  
  - Ongoing - Active → **38**  

---

### 📊 Lead Source Distribution
- **Action:** Counted leads by acquisition source.  
- **Output (Top 5 Sources):**  
  - Instagram Ads → **128**  
  - LinkedIn Ads → **112**  
  - Cold Calling → **105**  
  - Lists → **100**  
  - Display Ads → **100**  
  - (other sources included Referrals, Trade Shows, etc.)  

---

### 🌍 Regional Distribution of Leads
- **Action:** Counted leads by region.  
- **Output:**  
  - North America (NA) → **488**  
  - Europe (EU) → **393**  
  - Asia-Pacific (APAC) → **379**  
  - Latin America (LA) → **301**  
  - Middle East (ME) → **235**  
  - Africa (AF) → **204**  

---

### ✅ Company Data Generation
- **Action:** Generated **1963 synthetic companies** with attributes:  
  - Company ID, Name, Industry, Size, Ownership, Funding, Country, Interest Area.  

- **Output:**  
  - Displayed **first 5 company records** (sample companies with industry tags).  
  - Displayed **last 5 company records** to confirm dataset completeness.  
  - Industries observed included: Software, Retail, Healthcare, Finance, Manufacturing.  

---

### 🌍 Region Metadata
- **Action:** Created metadata for **6 regions** with fields:  
  - Region ID, Region Name, Regional Head, Timezone.  

- **Output (Sample):**  
  - NA → Head: Alice Smith → Timezone: EST  
  - EU → Head: George White → Timezone: CET  
  - APAC → Head: Rajesh Gupta → Timezone: IST  

---

### 👩‍💼 Sales Representative Data
- **Action:** Generated **20 sales representatives** with attributes:  
  - Rep ID, Name, Email, Phone, Region, Join Date, Status, Rating, Deals Closed, Avg Conversion Time, Win Rate.  

- **Output:**  
  - Displayed **first 5 reps** (sample with personal + performance attributes).  
  - Displayed **last 5 reps**.  
  - Variation observed in **win rates** and **deals closed** across reps.  

---

✅ End of **Part 1 – Setup & Data Generation**.  

## 🔹 Part 2: Funnel Stage Analysis

### 🛠️ Funnel Definition
- **Action:** Defined funnel stages for the CRM pipeline:  
  - **Lead → Contacted → Demo → Proposal → Deal/Lost**  

- **Output:**  
  - Funnel schema established and applied across the dataset.  
  - Ensured each lead was tagged with a funnel stage.  

---

### 📊 Funnel Stage Counts
- **Action:** Counted number of leads in each funnel stage.  
- **Output (Sample Distribution):**  
  - Lead → Highest volume (all generated leads start here).  
  - Contacted → Noticeable drop.  
  - Demo → Moderate count.  
  - Proposal → Smaller group.  
  - Deal Won / Deal Lost → Final outcomes.  

- **Insight:**  
  - Largest **drop-off** seen between **Demo → Proposal**.  
  - Indicates challenges in converting interest into concrete offers.  

---

### 📉 Funnel Conversion Rates
- **Action:** Calculated **stage-to-stage conversion percentages**.  
- **Output:**  
  - Lead → Contacted: ~60–70% conversion.  
  - Contacted → Demo: ~40–50% conversion.  
  - Demo → Proposal: **sharpest drop** (lowest conversion rate).  
  - Proposal → Deal Won/Lost: moderate conversions.  

- **Insight:**  
  - The **Demo → Proposal** stage is the major bottleneck in the funnel.  
  - Suggests product fit or value communication issues.  

---

### 📊 Funnel Visualization
- **Action:** Created bar/step funnel plot.  
- **Output:**  
  - Clear descending bars across stages.  
  - Final Deal Won count significantly smaller than initial leads.  
  - Visual emphasized **attrition** at each funnel step.  

---

✅ End of **Part 2 – Funnel Stage Analysis**.  
Next section → **Part 3: Rep & Regional Performance Analysis**.  

## 🔹 Part 3: Rep & Regional Performance Analysis

### 👩‍💼 Rep Performance – Deals & Win Rates
- **Action:** Aggregated outcomes by sales representative.  
- **Output:**  
  - Reps showed wide variation in both **deals closed** and **win rates**.  
  - Top reps achieved win rates above **70%**, with consistently high numbers of deals closed.  
  - Lower-performing reps had win rates below **20%**, with very few successful deals.  

- **Insight:**  
  - Performance disparity suggests opportunities for **targeted coaching** and best-practice sharing.  

---

### 🌍 Regional Performance – Deals by Geography
- **Action:** Summarized deals by region.  
- **Output:**  
  - **North America** → Highest number of deals closed.  
  - **Europe** → Second-highest.  
  - **Asia-Pacific** → Fewer deals, but higher efficiency in conversions.  
  - **Africa & Middle East** → Lowest overall deal volumes.  

- **Insight:**  
  - While **North America** generates the most deals, **Asia-Pacific** shows better conversion efficiency.  
  - Indicates regional market maturity differences and potential untapped growth areas.  

---

### 🏆 Rep Leaderboard
- **Action:** Created a leaderboard ranking reps by **deals won** and **win rates**.  
- **Output:**  
  - Clear distinction of **top 3 performers** dominating wins.  
  - Bottom performers highlighted with consistently poor conversion rates.  
  - Rankings validated internal CRM performance differences.  

---

### 🌎 Regional Heatmap
- **Action:** Produced visualization of deal performance by region.  
- **Output:**  
  - Heatmap showed **North America** and **Europe** as “hot spots” of deal activity.  
  - Regions like **Africa** and **Middle East** remained cooler zones.  

- **Insight:**  
  - Visual confirmed imbalance in lead flow and success rate across regions.  
  - Strategic recommendation: focus marketing investment in **high-performing regions** while experimenting with tailored strategies for weaker ones.  

---

✅ End of **Part 3 – Rep & Regional Performance Analysis**.  
Next section → **Part 4: Database & BigQuery Integration**.  

## 🔹 Part 4: Database & BigQuery Integration

### 🗄️ SQLite Database Creation
- **Action:** Exported generated CRM datasets (Leads, Companies, Regions, Reps) into a **SQLite database** (`CRM_Capstone_DB.sqlite`).  
- **Output:**  
  - Tables successfully created in SQLite.  
  - Verified schema included:
    - `Leads`
    - `Companies`
    - `Regions`
    - `Reps`  

---

### 🔍 SQL Queries – Verification
- **Action:** Ran test queries to validate data ingestion.  
- **Outputs:**  
  - **Top 5 Leads:** Previewed correctly from the `Leads` table.  
  - **Deal Outcomes Count:** Matches earlier distribution (Won, Lost, Ongoing).  
  - **Regional Breakdown:** Consistent with prior region counts.  

- **Insight:**  
  - Database ingestion verified; datasets consistent with generated and analyzed data.  

---

### ☁️ BigQuery Connection Setup
- **Action:** Connected notebook to **Google BigQuery** using authentication (`creds.json`).  
- **Output:**  
  - Successful authentication message displayed.  
  - Confirmed access to BigQuery project.  

---

### 📤 Export to BigQuery
- **Action:** Uploaded datasets into BigQuery for scalable storage and analytics.  
- **Output:**  
  - Tables created in BigQuery with proper schema mapping.  
  - Datasets validated with preview queries.  
  - Lead, company, region, and rep data available in BigQuery for visualization.  

---

### 📊 Dashboard Preparation (Looker Studio)
- **Action:** Prepared BigQuery tables as data sources for **Google Looker Studio** dashboard.  
- **Planned Dashboards:**  
  - Funnel Stage Conversion (Lead → Deal).  
  - Rep Performance Leaderboard (Deals, Win Rate).  
  - Regional Analysis (Volume vs. Conversion Rate).  
  - Lead Source Efficiency (Source vs. Outcome).  

- **Output (expected upon visualization):**  
  - Interactive dashboards allowing stakeholders to drill down into funnel drop-offs, rep comparisons, and regional efficiency.  

---

✅ End of **Part 4 – Database & BigQuery Integration**.  

## EDA Analysis
# 🔍 Exploratory Data Analysis (EDA) – Execution Log

This document describes the step-by-step exploratory analysis performed on the CRM Capstone dataset.

---

## 1️⃣ Setup & Data Import
- **Action:** Imported libraries (pandas, numpy, matplotlib, seaborn, sqlite3).  
- **Output:** All libraries successfully loaded.  

- **Action:** Loaded data from `CRM_Capstone_DB.sqlite`.  
- **Output:** Tables available → `Leads`, `Companies`, `Regions`, `Reps`.  

---

## 2️⃣ Dataset Overview
- **Action:** Displayed first 5 rows of each dataset.  
- **Output:**  
  - **Leads:** LeadID, Company, Source, Budget, Stage, Outcome.  
  - **Companies:** CompanyID, Industry, Size, Ownership, Country.  
  - **Regions:** RegionID, Name, Head, Timezone.  
  - **Reps:** RepID, Name, Region, Deals Closed, Win Rate.  

- **Action:** Checked null values and datatypes.  
- **Output:** No major missing values; datatypes consistent with schema.  

---

## 3️⃣ Lead Data Exploration
### 📊 Outcome Distribution
- **Action:** Count of leads by outcome.  
- **Output:**  
  - Deal Lost → majority.  
  - Deal Won → smaller share.  
  - Ongoing (Active/Cold) → moderate.  

### 🌍 Regional Lead Distribution
- **Action:** Grouped leads by region.  
- **Output:**  
  - North America & Europe → highest.  
  - Africa & Middle East → lowest.  

### 📊 Source of Leads
- **Action:** Analyzed lead acquisition channels.  
- **Output:**  
  - Social media (Instagram, LinkedIn Ads) dominate.  
  - Referrals and Trade Shows contribute smaller shares.  

---

## 4️⃣ Funnel Stage Exploration
- **Action:** Counted leads across stages (Lead → Contacted → Demo → Proposal → Deal/Lost).  
- **Output:**  
  - Sharpest drop observed at **Demo → Proposal** stage.  
  - Funnel imbalance confirmed with bar chart.  

---

## 5️⃣ Sales Rep Analysis
- **Action:** Aggregated rep performance.  
- **Output:**  
  - Wide gap between top and bottom reps.  
  - Best reps achieved >70% win rate.  
  - Underperformers had <20% win rate.  

---

## 6️⃣ Company Insights
- **Action:** Industry-level distribution.  
- **Output:**  
  - Retail, Software, Healthcare lead in representation.  
  - Finance & Manufacturing less common.  

- **Action:** Budget distribution across companies.  
- **Output:**  
  - Skewed towards smaller budgets.  
  - Outliers exist with very high deal values.  

---

## 🔑 Key EDA Insights
- CRM funnel has **major attrition at Demo → Proposal** stage.  
- **Rep performance is uneven**, with a few high performers carrying most of the wins.  
- **North America drives volume**, while APAC is more conversion-efficient.  
- Lead acquisition is **digital-heavy**, suggesting reliance on paid campaigns.  
- Budget distribution skewed low; high-value deals are rare outliers.  


