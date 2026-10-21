# Indonesia Earthquake Data Analysis

**BIG DATA** | **DATA ANALYTICS** | **PYSPARK & GOOGLE COLAB**

An exploratory data analysis project that processes Indonesian earthquake records using Apache Spark and Spark SQL. The project examines earthquake magnitude distributions, temporal patterns in the Sumbawa region, and the relationship between earthquake magnitude and depth through Python-based data visualizations.

## 01. Project Overview

### Project Description

Indonesia Earthquake Data Analysis is a data processing and visualization project developed to explore earthquake records in Indonesia using PySpark, Spark SQL, Pandas, and Matplotlib.

The analysis focuses on earthquake magnitude frequency, earthquake occurrence over time, and the relationship between magnitude and depth. Particular attention is given to records associated with the Sumbawa region to explore regional earthquake patterns.

### Objectives

- Process earthquake catalog data using Apache Spark.
- Explore dataset structure and summarize relevant variables.
- Identify the most and least frequently recorded earthquake magnitudes.
- Analyze earthquake magnitude distributions in the Sumbawa region.
- Examine monthly earthquake occurrence trends from 2020 to 2024.
- Explore the relationship between earthquake magnitude and depth.
- Present analytical results through clear and informative visualizations.

### Problem Statement

Earthquake catalog datasets contain multiple attributes, including occurrence dates, coordinates, depth, magnitude, and location descriptions. Examining these records individually can make it difficult to identify recurring patterns, compare magnitude frequencies, or observe changes in earthquake occurrence over time.

This project uses data processing, SQL-based aggregation, and visualization to make earthquake records easier to explore and interpret.

### Approach & Solution

The project applies a structured data analysis workflow:

- **Data Processing:** Load and inspect earthquake records using PySpark DataFrames.
- **Data Filtering:** Select relevant columns and filter records based on location, magnitude, and time period.
- **Data Analysis:** Use Spark SQL to group records, count earthquake occurrences, and identify magnitude frequencies.
- **Temporal Analysis:** Aggregate earthquake counts by month for the 2020–2024 period.
- **Data Visualization:** Convert query results into Pandas DataFrames and create charts using Matplotlib.

### Analysis Scope

The project covers three main analytical areas:

1. **Magnitude Distribution:** Examine earthquake frequency by magnitude in the selected Sumbawa region records, focusing on magnitudes up to 5.0.
2. **Temporal Trends:** Examine monthly earthquake counts associated with the Sumbawa region from 2020 to 2024.
3. **Magnitude and Depth:** Explore the distribution of earthquake magnitudes against depth for records with non-null magnitude values and depths of up to 100 km.

### Dataset

The project uses a CSV earthquake catalog named `katalog_gempa.csv`.

| Column | Description |
|---|---|
| `tgl` | Earthquake occurrence date |
| `ot` | Earthquake occurrence time |
| `lat` | Latitude |
| `lon` | Longitude |
| `depth` | Earthquake depth |
| `mag` | Earthquake magnitude |
| `remark` | Earthquake location or regional description |

The dataset is loaded using PySpark with header detection and schema inference. Records are then queried through a temporary Spark SQL view named `EarthquakesData`.

The analysis of the Sumbawa region uses the `remark` column to filter records containing `Sumbawa Region`.

## 02. Tech Stack

| Category | Technology | Purpose |
|---|---|---|
| Programming Language | Python | Data processing and analysis |
| Big Data Processing | Apache Spark / PySpark | Load, select, filter, and process earthquake records |
| Query Language | Spark SQL | Data aggregation, filtering, grouping, and sorting |
| Data Manipulation | Pandas | Convert query results for further analysis |
| Data Manipulation | NumPy | Imported for potential numerical operations |
| Data Visualization | Matplotlib | Create bar charts, line charts, and scatter plots |
| Development Environment | Google Colab / Jupyter Notebook | Execute the analysis notebook |
| Data Format | CSV | Store the earthquake catalog |

## 03. Screenshots / Results

This section presents the data processing workflow, analytical query results, and visualizations generated from the earthquake catalog. Each analysis highlights the insights that can be obtained from historical earthquake records and how these insights may support further analysis and decision-making.

### 3.1 Data Loading & Exploration

The earthquake catalog is loaded from a CSV file into a PySpark DataFrame. The dataset schema, sample records, selected columns, and descriptive summaries are examined to understand the structure and characteristics of the available data.

**Workflow:**

`CSV Dataset → PySpark DataFrame → Schema Inspection → Column Selection → Descriptive Summary`

**Key Activities:**
- Load the earthquake catalog using PySpark.
- Inspect column names, data types, and sample records.
- Select relevant attributes, including date, time, coordinates, depth, magnitude, and location description.
- Generate descriptive summaries to examine the dataset.

**Insights & Practical Applications:**

- Understand the available earthquake attributes and their suitability for further analysis.
- Identify potential data quality issues, such as missing values or inconsistent date formats, that may require additional preprocessing.
- Establish a foundation for filtering, aggregating, and visualizing earthquake records.

This stage helps ensure that subsequent analyses are based on an understanding of the dataset's structure and limitations.

**Screenshot:**

<img width="822" height="466" alt="image" src="https://github.com/user-attachments/assets/edf4c382-0085-4a69-89fa-395085b8e336" />


### 3.2 Earthquake Magnitude Frequency Analysis

Spark SQL is used to group earthquake records by magnitude and count their occurrences. The queries identify the most and least frequently recorded magnitude values in the overall dataset and examine magnitude frequencies in records associated with the Sumbawa region.

Additional queries separate Sumbawa records into magnitude categories at or above 5.0 and at or below 5.0.

**Workflow:**

`Earthquake Records → Spark SQL GROUP BY → COUNT(*) → Frequency Comparison`

**Analysis Method:**
- Group records by `mag`.
- Count earthquake records using `COUNT(*)`.
- Sort the results to identify the most and least frequently recorded magnitude values.
- Filter records associated with the Sumbawa region for regional analysis.
- Examine magnitude frequencies using the 5.0 threshold.

**Insights & Practical Applications:**

- Identify which magnitude values appear most and least frequently in the available earthquake catalog.
- Compare the frequency distribution of recorded magnitudes between the overall dataset and the selected Sumbawa records.
- Support exploratory analysis of historical seismic activity and help identify patterns that may warrant further investigation.
- Provide descriptive information that can complement geological studies, seismic hazard assessments, and disaster preparedness planning.

The results describe the frequency of recorded historical events. They do not independently establish the probability of a future earthquake or predict when one will occur.

**Screenshot:**

<img width="332" height="435" alt="image" src="https://github.com/user-attachments/assets/9112e530-3d52-4fb3-94cd-35cae8bad8ae" />

<img width="218" height="354" alt="image" src="https://github.com/user-attachments/assets/7aaca2d0-1314-4ddb-a297-cd89958bc8d1" />

<img width="218" height="471" alt="image" src="https://github.com/user-attachments/assets/910a7c0c-7861-44ce-8f06-788ec3728dad" />


### 3.3 Earthquake Magnitude Distribution in Sumbawa

A bar chart displays the number of recorded earthquakes for each magnitude value in the selected Sumbawa region records with magnitudes at or below 5.0.

**Analysis Method:**
- Filter records using `remark LIKE '%Sumbawa Region%'`.
- Select records with `mag <= 5.0`.
- Group records by `mag`.
- Count earthquake occurrences for each magnitude.
- Visualize the aggregated results using a Matplotlib bar chart.

**Purpose:**

Compare earthquake frequencies across recorded magnitude values and identify which values appear more frequently in the selected dataset.

**Insights & Practical Applications:**

- Determine which recorded magnitude values are most common within the selected data.
- Understand how earthquake counts are distributed across the magnitude range being analyzed.
- Help researchers and students explore the characteristics of historical earthquakes in the Sumbawa region.
- Provide an initial descriptive reference for further regional seismic analysis and risk assessment when combined with additional geological and historical information.

**Limitation:** The chart includes only records matching the regional filter and `mag <= 5.0`. It cannot describe the complete magnitude distribution of all earthquakes in the region, and its results depend on the coverage and completeness of the dataset.

**Screenshot:**

<img width="989" height="590" alt="image" src="https://github.com/user-attachments/assets/d2f1d741-88fb-48d8-a64b-1583dc57abd4" />


### 3.4 Monthly Earthquake Trends (2020–2023)

A line chart illustrates monthly earthquake counts for records associated with the Sumbawa region between 2020 and 2023.

The date field is converted into a year-month format, and records are grouped by month before visualization.

**Analysis Method:**
- Filter records associated with the Sumbawa region.
- Restrict the analysis to dates from 2020 through 2023.
- Convert the date field into a year-month representation.
- Count earthquake records for each month.
- Visualize monthly counts using a Matplotlib line chart.

**Purpose:**

Observe changes in recorded earthquake frequency over time and identify months with relatively higher or lower counts.

**Insights & Practical Applications:**

- Identify periods with higher or lower numbers of recorded earthquakes in the selected historical dataset.
- Examine how recorded earthquake frequency changes across the five-year observation period.
- Help researchers explore temporal patterns and determine whether additional investigation of particular periods is warranted.
- Support historical reporting and provide contextual information for seismic monitoring and disaster preparedness activities.

**Limitation:** Changes in monthly earthquake counts do not necessarily indicate a predictable cycle or an upcoming earthquake. The visualization describes past records and does not forecast future seismic events.

**Screenshot:**

<img width="1387" height="590" alt="image" src="https://github.com/user-attachments/assets/b93c2a92-fd78-4b05-8d2e-83328039cb36" />


### 3.5 Relationship Between Earthquake Magnitude and Depth

A scatter plot explores the distribution of earthquake magnitude against earthquake depth for records with non-null magnitude values and depths of up to 100 km.

**Chart Configuration:**
- **X-axis:** Earthquake depth (`depth`), measured in kilometers.
- **Y-axis:** Earthquake magnitude (`mag`).
- **Filter:** `mag IS NOT NULL` and `depth <= 100`.

**Purpose:**

Examine how recorded earthquake magnitudes are distributed across different depths and identify potential patterns or outliers in the selected records.

**Insights & Practical Applications:**

- Observe the range of magnitudes recorded at different earthquake depths.
- Explore whether the selected records suggest any association between depth and magnitude.
- Identify unusual observations that may warrant further investigation.
- Provide an exploratory starting point for more detailed seismic analysis involving depth, magnitude, geographic location, and other geological variables.

**Limitation:** A scatter plot alone cannot establish causation, quantify a statistically significant relationship, or predict future earthquake magnitude. Additional statistical analysis and geological context would be required to support those conclusions.

**Screenshot:**

<img width="989" height="590" alt="image" src="https://github.com/user-attachments/assets/c32742e4-9b8c-4032-9c50-49025ac66a67" />


### Results Summary

| Analysis | Visualization / Output | Insights & Practical Applications |
|---|---|---|
| Data Loading & Exploration | Schema, sample records, and descriptive summary | Understand dataset structure and identify potential data quality issues. |
| Magnitude Frequency Analysis | SQL query results | Identify frequently recorded magnitude values and compare overall and regional distributions. |
| Sumbawa Magnitude Distribution | Bar chart | Explore the frequency of recorded magnitudes up to 5.0 in the selected regional data. |
| Monthly Earthquake Trends | Line chart | Examine historical changes in monthly earthquake counts from 2020 to 26 Januari 2023. |
| Magnitude vs. Depth | Scatter plot | Explore the distribution of magnitude values across earthquake depths and identify observations for further study. |

### Overall Insights & Project Impact

This project transforms raw earthquake catalog records into structured analytical results and visualizations that make historical seismic data easier to explore and interpret.

The analysis can help users:
- Understand the distribution of recorded earthquake magnitudes.
- Explore historical changes in earthquake frequency over time.
- Examine how earthquake magnitude values are distributed across different depths.
- Identify patterns and observations that may guide further research.
- Provide descriptive evidence that can complement seismic hazard assessments and disaster preparedness planning.

The project is an exploratory data analysis workflow, not an earthquake prediction system. Predicting the time, location, or magnitude of future earthquakes would require a separate research methodology, appropriate predictive models, additional validation, and evidence that the models perform reliably.

## 04. Installation & Usage

### Prerequisites

Before running the project, prepare the following:

- A Google account to access Google Colab.
- The earthquake catalog CSV file, `katalog_gempa.csv`.
- Basic knowledge of Python and SQL.
- An internet connection for accessing Google Colab and installing dependencies when necessary.

### Project Structure

The following is a recommended repository structure for organizing the notebook, dataset, and screenshots.

```text
indonesia-earthquake-data-analysis/
├── notebook/
│   └── earthquake_analysis.ipynb
├── data/
│   └── katalog_gempa.csv
├── screenshots/
│   ├── data-exploration.png
│   ├── magnitude-frequency.png
│   ├── magnitude-distribution.png
│   ├── monthly-earthquake-trends.png
│   └── magnitude-vs-depth.png
└── README.md
```

The folder and filenames are recommendations. Adjust them to match the files actually available in the repository.

### Installation

**1. Open the notebook**

Open `earthquake_analysis.ipynb` in Google Colab.

**2. Prepare the dataset**

Upload `katalog_gempa.csv` to the Colab session, or modify the file path if the dataset is stored in Google Drive.

**3. Install PySpark**

Run the following command in a notebook cell if PySpark is not already installed:

```python
!pip install pyspark
```

**4. Import the required libraries**

```python
import psutil
import pyspark
from pyspark.sql import SparkSession
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
```

The code imports `psutil` to inspect CPU utilization and imports NumPy, although neither is essential to the main visualizations shown in the provided code.

### Configuration

Initialize the Spark session and specify the dataset location:

```python
from pyspark.sql import SparkSession

spark = (
    SparkSession.builder
    .appName("Earthquakes In Indonesia")
    .getOrCreate()
)

csv_file = "katalog_gempa.csv"

df = spark.read.csv(
    csv_file,
    header=True,
    inferSchema=True
)
```

Make sure that the CSV path matches the actual location of the dataset.

### Running the Analysis

1. Run the notebook cells in order.
2. Load the earthquake catalog into a PySpark DataFrame.
3. Inspect the schema and select the relevant columns.
4. Create the `EarthquakesData` temporary SQL view.
5. Execute the Spark SQL queries for magnitude frequency and regional filtering.
6. Run the visualization cells to generate the bar chart, line chart, and scatter plot.
7. Review the resulting tables and charts.

### Expected Outputs

When the notebook runs successfully with a compatible dataset, it generates:

- Dataset schema and sample records.
- Descriptive summary results.
- SQL query results for earthquake magnitude frequencies.
- A bar chart of Sumbawa region earthquake magnitude distribution.
- A line chart of monthly earthquake counts for 2020–2024.
- A scatter plot showing earthquake depth against magnitude.

### Notes

- The CSV must contain the columns referenced in the notebook.
- Regional filtering depends on the location descriptions stored in `remark`.
- The monthly trend query expects dates that can be parsed using the format `yyyy/MM/dd`.
- The results depend on the contents and date range of the dataset.
- The project is an exploratory data analysis workflow, not a real-time earthquake monitoring or prediction system.

--- 
