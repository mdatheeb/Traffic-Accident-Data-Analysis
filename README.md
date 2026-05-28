# Public Safety Analytics: UK Traffic Accident Data Analysis

This repository contains a comprehensive data analytics project exploring public road safety by identifying high-risk times, primary contributing factors, and critical geographical accident patterns within the United Kingdom. 

📊 Public Safety Analytics: Traffic Accident Data Analysis & Geospatial Hotspot Visualization
An end-to-end automated data science pipeline and spatial analytics engine engineered to monitor, evaluate, and map systematic road safety and localized collision catalysts across the United Kingdom.

This project handles everything programmatically—from dataset retrieval and rigorous feature engineering to interactive visualization layers.

🚀 Key Features
⚡ Automated Asset Pipeline: Programmatic data ingestion via kaggle API with fallback error-prevention logic.

🧹 Robust Cleaning Pipeline: Complete structural mitigation dropping non-mappable markers and imputing fragmented categories.

🌤️ Environmental Risk Analysis: Identifies core weather factors heavily correlated with frequent accidents.

⚖️ Normalized Temporal Metrics: Breaks through calendar baseline imbalances (5 weekdays vs. 2 weekend days) to calculate genuine average daily risks.

🗺️ Interactive Spatial Clustering: Compiles dense coordinate sets into interactive geographic browser maps powered by Leaflet marker-clustering engines.

🛠️ Architecture Workflow
Code snippet
graph TD
    A[Kaggle Hub API Data Ingestion] --> B[Dynamic File Discovery & Loading]
    B --> C[Data Cleaning & Imputation Protocol]
    C --> D[Feature Engineering: Datetime Splitters]
    D --> E1[Analytical Stage 1: Environmental Analytics]
    D --> E2[Analytical Stage 2: Calendar Regularization]
    D --> E3[Analytical Stage 3: Interactive Geospatial Mapping]
    E1 --> F1[top_3_causes.png]
    E2 --> F2[weekday_vs_weekend.png]
    E3 --> F3[traffic_accident_hotspots.html]
📦 System Dependencies & Stack
Component	Library / Driver	Version Profile	Operational Role
🐍 Runtime	Python	3.10+	Core computation environment
🐼 Data Core	Pandas	2.x+	DataFrame manipulations and temporal transformations
🔢 Array Math	NumPy	1.26+	Vectorized evaluations and missing data flags
🎨 Stat Plots	Seaborn	0.13+	Statistical distribution plots and horizontal bar designs
📊 Engine Plots	Matplotlib	3.8+	Subplot array framing and image asset outputs
🗺️ Geospatial	Folium	0.15+	Leaflet.js map compiling and script injection
☁️ API Ingest	KaggleHub	Latest	Secure programmatic database synchronization
📊 Dataset Profile
Repository Source: Department for Transport (United Kingdom)

Database Shape: 1,504,150 Records × 33 Features

Target Metrics Tracked: Geographic Coordinates, Environmental Flags, Spatial Conditions, Speed Limits, Severity Levels.

Core Explored Fields Table
Feature Key	Data Classification	Imputation Strategy / Transformation Applied
Latitude / Longitude	Geographic Float	Rows dropped if null (critical coordinate integrity)
Date / Time	Chronological / Object	Converted into native machine-readable Datetime properties
Weather_Conditions	Categorical String	Preserved for frequency extraction layers
Junction_Control	Categorical String	Filled missing data blocks explicitly with 'Unknown'
Pedestrian_Crossing-*	Infrastructure Metric	Defaulted structural nulls to 0 indicating no infrastructure asset
⚙️ Cleaning & Engineering Transformations
Raw public infrastructure records are notoriously fragmented. The pipeline mitigates defects through a strict data transformation sequence:

Spatial Sanitization: Safely discards row subsets lacking Latitude, Longitude, or Time properties, preventing geographic plotting distortion.

Imputation Safety Nets: Instead of dropping high-volume categorical missing blocks (such as site conditions or junction controllers), rows are preserved and safely labeled as 'Unknown' to retain secondary dimensions.

Chronological Extractor: Coerces object dates to pd.to_datetime formats. Days are explicitly derived into literal strings (e.g., 'Monday') and mapped to logical weekend trackers to counteract volumetric reporting imbalances.

Python
# Core Imputation Snippet from Pipeline
df_cleaned = df.dropna(subset=['Latitude', 'Longitude', 'Time']).copy()
fill_unknown = ['Junction_Control', 'Special_Conditions_at_Site', 'Carriageway_Hazards', 'LSOA_of_Accident_Location']
df_cleaned[fill_unknown] = df_cleaned[fill_unknown].fillna('Unknown')
df_cleaned['Date'] = pd.to_datetime(df_cleaned['Date'], errors='coerce')
📈 Deep-Dive Visual Analytics
⛅ 1. Environmental Weather Catalysts
Extracts and isolates the top 3 high-volume weather profiles present during active road collisions.

Target Visualization Asset: top_3_causes.png

Analytical Insight: Data metrics show that clear/fine weather conditions paradoxically dominate reporting volume. This strongly suggests traffic density scaling, clear-day velocity acceleration, and driver complacency play a heavier role than active inclement weather.

📅 2. Regularized Temporal Risk Modeling
Compares crash frequency based on days of the week, avoiding chronological data traps.

Target Visualization Asset: weekday_vs_weekend.png

Analytical Insight: Raw metrics mistakenly indicate weekends are safer due to lower cumulative accident numbers. However, dividing raw sums by respective day profiles (5 vs. 2) to calculate the true daily average accident rate proves that road hazards remain consistently dangerous throughout the entire week.

🗺️ 3. Interactive Marker-Cluster Hotmaps
Constructs a localized, dense leaflet cluster mapping layout.

Target Visualization Asset: traffic_accident_hotspots.html

Analytical Insight: Avoids rendering heavy, unoptimized asset points by packaging coordinates inside interactive nodes. Zooming down automatically splits regional nodes into individual color-coded hazard markers containing embedded popup HTML specs (such as local Speed limits and Severity rankings).

🏁 Quick Start & Deployment Guide
📂 Repository File Architecture
Plaintext
├── public_saftey_analysis.ipynb     # Interactive Data Science Notebook
├── README.md                        # Production Portfolio Documentation
├── top_3_causes.png                 # Exported Weather Drivers Bar Plot
├── weekday_vs_weekend.png           # Exported Temporal Normalization Bar Plot
└── traffic_accident_hotspots.html   # Deployable Interactive Hotspot Map Asset
⌨️ Environment Initialization
Install the required analytical and geospatial mapping assets directly using pip:

Bash
pip install pandas numpy matplotlib seaborn folium kagglehub
💻 Local Pipeline Execution
Run the complete automated notebook flow or compile the code segment directly using your favorite interactive python runner:

Bash
# Execute within a local runtime or Google Colab environment to generate assets
jupyter notebook public_saftey_analysis.ipynb
🔮 Roadmap & Future Extensions
📡 Real-Time Dispatch Streams: Connect the data ingestion structure to live transport APIs or emergency services radio logging streams.

🤖 Predictive Risk Forecasting: Train classification structures (e.g., XGBoost or Random Forests) to calculate localized accident probabilities based on real-time weather forecasts.

👥 Demographic Normalization: Integrate local population baselines and daily vehicle miles traveled (VMT) to compute absolute incident rates per capita.

🏫 Project Metadata & Team
Academic Year Profile: 2026

Academic Institution: Department of Computer Science and Engineering

Project Contributors: * Tanushree Jain - RTU24101CS044

Md Atheeb - RTU24101CS028

Source Control Repository: Traffic-Accident-Data-Analysis On GitHub
