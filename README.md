# NYC Taxi Utilization Analysis 🚖

### **Overview**
This project focuses on analyzing New York City (NYC) taxi ride data to understand patterns, utilization, and borough-level trip characteristics. The analysis integrates temporal and geospatial data, allowing us to enrich the dataset with borough-level insights and calculate utilization metrics for drivers.

The project follows a structured approach to clean the data, enrich it with geospatial information, and conduct meaningful analyses, including driver idle times, trip durations, and borough-level statistics.

---

### **Objectives**
- Enrich the dataset with borough information for pickup and drop-off locations using GeoJSON boundary data.
- Calculate trip durations and filter out invalid or unreasonable trips.
- Compute taxi utilization by calculating idle times between consecutive trips.
- Analyze borough-level statistics, such as trip counts, total trip durations, and average trip durations.

---

### **Datasets**
1. **NYC Taxi Data (CSV)**: Contains ride details such as timestamps, coordinates, and passenger counts.
2. **NYC Borough Boundaries (GeoJSON)**: Defines the geographical boundaries of NYC boroughs.

---

### **Key Steps**

#### 1. **Data Preprocessing**
- Filtered out invalid rows with missing or out-of-bound coordinates.
- Converted `pickup_datetime` and `dropoff_datetime` to a proper `timestamp` format.
- Removed trips with zero passengers and those outside the NYC geographical region.

#### 2. **Enriching Data with Borough Information**
- Used a GeoJSON file to assign `pickup_borough` and `dropoff_borough` columns to each ride.
- Utilized Shapely polygons and Spark UDFs to check if coordinates fell within specific borough boundaries.

#### 3. **Trip Duration Calculation**
- Calculated the trip duration for each ride (in seconds) as the difference between `dropoff_datetime` and `pickup_datetime`.
- Filtered out trips with negative durations or those exceeding 4 hours.

#### 4. **Utilization Analysis**
- Used Spark's Window functions to compute idle times for each taxi by comparing consecutive trips.
- Summed idle times for each driver to calculate total idle time, a key metric for utilization.

#### 5. **Borough-Level Analysis**
- Computed:
  - **Trip counts by borough**: Number of trips starting in each borough.
  - **Total trip duration by borough**: Total time spent on trips originating from each borough.
  - **Average trip duration by borough**: Average time spent per trip in each borough.

---

### **Results**

1. **Trip Distribution by Borough**:
   - Manhattan accounted for the majority of trips due to its high population density and business activity.
   - Outer boroughs like Queens and Brooklyn had fewer trips but longer average durations.

2. **Taxi Utilization**:
   - Idle times varied significantly across drivers, highlighting opportunities for optimization.
   - Drivers servicing Manhattan had shorter idle times due to higher trip demand.

3. **Borough-Level Trip Durations**:
   - Trips originating from Manhattan were shorter on average.
   - Trips from Queens and Brooklyn often spanned longer durations due to greater distances.

---

### **Visualizations**
The project includes visualizations to better understand the results:
1. **Bar Chart**: Trip counts by pickup borough.
2. **Bar Chart**: Total trip duration by pickup borough.
3. **Bar Chart**: Average trip duration by pickup borough.
4. **Histogram**: Distribution of idle times across all drivers.

---

### **Technologies Used**
- **Apache Spark**: Distributed data processing and analysis.
- **Python**: Data manipulation and geospatial processing.
- **Shapely**: Handling geospatial data and polygons.
- **Pandas**: Integration for visualizations.
- **Matplotlib & Seaborn**: Data visualization.

---

### **How to Run**
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/NYC-Taxi-Analysis.git
   cd NYC-Taxi-Analysis
2. **Install Dependencies:** Ensure Python and required libraries are installed**
3. **Run the Notebook:** Open and run the notebook `NYCTaxiAnalysis.ipynb` in a Jupyter or Google Colab environment.
4. **View Visualizations:** After running all cells, refer to the visualization outputs to interpret results.

---

### **Project Structure**
  ```bash
  NYC-Taxi-Analysis/
  │
  ├── Sample NYC Data.csv         # Taxi data (CSV format)
  ├── nyc-boroughs.geojson        # NYC borough boundaries (GeoJSON format)
  ├── NYCTaxi-RezaHOSSEINI-MoslemPirzad.ipynb  # Main analysis notebook
  ├── README.md                   # Project documentation






   
