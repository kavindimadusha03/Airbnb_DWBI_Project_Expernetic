# NYC Airbnb Market Analysis & Data Engineering Pipeline

## 📝 Project Description
This project provides an end-to-end Data Engineering and Business Intelligence (BI) analysis of the New York City short-term rental market, using public data from Inside Airbnb. 

The primary objective is to transform raw, web-scraped data into a production-ready analytical architecture. The pipeline automates the extraction, cleaning, and normalization of complex datasets, ultimately constructing a relational **Star Schema** within an SQLite database. The project concludes with a comprehensive Exploratory Data Analysis (EDA) that uncovers key market dynamics, including:
* **Geospatial Pricing Gradients:** How proximity to Manhattan’s center dictates price premiums.
* **Seasonal Cyclicality:** Analysis of demand spikes and their impact on pricing and minimum-stay policies.
* **Hosting Dynamics:** Identifying the power-law distribution between casual and commercial hosts.
* **Platform Quality Metrics:** Evaluating the statistical reality of "review inflation" in short-term rental ratings.

---

## 🚀 Reproducibility Instructions (Google Colab Setup)

This project is designed to be executed in a cloud-based Python environment. Follow these steps to reproduce the analysis.

### Step 1: Environment & Dependencies
1. Open your [Google Colab](https://colab.research.google.com/) account.
2. Upload the `Airbnb_DWBI_Project.ipynb` file from this repository to your Colab workspace.
3. The notebook requires the following standard data science libraries, which are pre-installed in Google Colab:
   * `pandas`, `numpy`, `matplotlib`, `seaborn`, `folium`, `sqlite3`

### Step 2: Data Download
The notebook is configured to automatically fetch the latest raw datasets from the [Inside Airbnb](http://insideairbnb.com/get-the-data.html) servers. You do not need to download these files manually. When you run the first code cell, the pipeline will:
1. Create a `raw_data/` directory in your Colab environment.
2. Download the latest `listings.csv.gz`, `calendar.csv.gz`, and `reviews.csv` files directly to that folder.
3. But you have to mannually upload the neighbourhoods.geojson and neighbourhoods.csv to the raw_data folder.

### Step 3: Execution Order
To ensure the pipeline constructs the database and generates visualizations correctly, run the notebook cells in the following logical order:

1. **Section 02 (Dataset Familiarization):** Executes the automated download, initial data profiling, and handling of missing values.
2. **Section 03 (Data Engineering):** * Runs the ETL pipeline to clean currency strings and standardize dates.
    * Generates business-critical features (Annual Revenue, Occupancy Rates).
    * Builds the **Star Schema** and populates the `airbnb_analytics.db` SQLite database.
3. **Section 04 (Exploratory Data Analysis):** * Executes the data visualization suite to generate price distributions, seasonal line charts, and host tenure trendlines.
    * Generates the interactive `folium` geospatial heatmap.

---

## 📊 Key Pipeline Features
* **Auditability:** Every step of the ETL process is logged using Python’s `logging` library to ensure data integrity.
* **Dimensional Modeling:** By implementing a Star Schema, the project demonstrates advanced data warehousing concepts, separating fact logs from descriptive dimensions.
* **Visual Storytelling:** The EDA section uses a professional design language to provide actionable insights for stakeholders, including real-estate investors and platform managers.

---
