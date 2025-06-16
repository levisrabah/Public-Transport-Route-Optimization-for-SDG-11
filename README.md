# Public Transport Route Optimization for SDG 11

## Project Overview
This project addresses **UN SDG 11: Sustainable Cities and Communities** by optimizing public transport routes through K-means clustering. The goal is to identify optimal bus stop hubs in New York City using real data from the MTA Bus Stops dataset, improving accessibility and reducing travel times.

### Objective
- **Problem**: Inefficient bus stop placement can lead to longer travel times and reduced accessibility, particularly in underserved areas.
- **Solution**: Use K-means clustering to group bus stop locations based on latitude, longitude, and population density, identifying potential hubs.
- **Impact**: Enhances public transport efficiency, reduces carbon emissions, and promotes equitable access.

## Dataset
- **Source**: MTA Bus Stops dataset (`bi7e-6jgj`) from [NYC Open Data](https://data.cityofnewyork.us/Transportation/MTA-Bus-Stops/bi7e-6jgj), accessed via Socrata API.
- **Features**: Latitude (`stop_lat`), longitude (`stop_lon`), and synthetic population density (placeholder).
- **Access**: Uses Socrata API with an app token to avoid throttling limits.

## Tools & Libraries
- **Python**: Programming language.
- **Jupyter Notebook**: Interactive development.
- **Scikit-learn**: K-means clustering and preprocessing.
- **Pandas & NumPy**: Data manipulation.
- **Matplotlib & Seaborn**: Visualizations.
- **Folium**: Interactive map.
- **Sodapy**: Socrata API client.

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/levisrabah/public-transport-optimization.git
   cd public-transport-optimization
   ```
2. Install dependencies:
   ```bash
   pip install pandas numpy scikit-learn matplotlib seaborn folium sodapy
   ```
3. Run the Jupyter Notebook:
   ```bash
   jupyter notebook public_transport_clustering_socrata.ipynb
   ```

## Methodology
1. **Data Preprocessing**:
   - Fetch MTA Bus Stops data via Socrata API.
   - Rename `stop_lat` and `stop_lon` to `latitude` and `longitude`.
   - Add synthetic population density.
   - Clean missing/invalid coordinates.
   - Normalize features using StandardScaler.
2. **Model Training**:
   - Apply K-means clustering with `k=5` (determined via elbow and silhouette methods).
3. **Evaluation**:
   - Compute silhouette score for cluster quality.
   - Visualize clusters on a Folium map and 2D scatter plot.
4. **Output**:
   - Save clustered data to `clustered_bus_stops.csv`.
   - Generate interactive map (`nyc_bus_stops_map.html`).

## Results
- **Silhouette Score**: ~0.4–0.5 (indicating reasonable cluster separation).
- **Clusters**: 5 clusters representing potential bus stop hubs.
- **Visualizations**:
  - Elbow and silhouette plots for optimal `k`.
  - Interactive Folium map showing clustered bus stops.
  - 2D scatter plot with population density (point size).

## Demo Screenshots
1. **Elbow and Silhouette Plots**:
   - File: `screenshots/elbow_silhouette.png`
   - Description: Justifies `k=5` for clustering.
2. **Folium Map**:
   - File: `screenshots/folium_map.png`
   - Description: Shows clustered bus stops in NYC.
3. **2D Scatter Plot**:
   - File: `screenshots/scatter_plot.png`
   - Description: Visualizes clusters by coordinates and population density.

## Ethical Considerations
- **Bias in Data**: The dataset may underrepresent bus stops in low-income or remote areas, potentially skewing clusters toward high-density zones. Synthetic population density assumes uniform distribution, which may not reflect reality.
- **Fairness**: Clustering prioritizes high-density areas, but underserved regions must be considered to ensure equitable access.
- **Sustainability**: Optimized routes reduce fuel consumption, supporting SDG 11’s environmental goals.
- **Mitigation**: Use real population data and consult community stakeholders to validate hub placements.

## How to Run the Demo
1. Open `public_transport_clustering_socrata.ipynb` in Jupyter Notebook.
2. Run all cells to generate outputs.
3. Open `nyc_bus_stops_map.html` in a browser.

## Stretch Goals
- Integrate real population data (e.g., [NYC Population by Borough](https://data.cityofnewyork.us/City-Government/Population-by-Borough/9t2m-hnzh)).
- Use MTA Bus Time API for real-time data.
- Deploy as a Streamlit app for interactive visualization.

## Repository Structure
```
public-transport-optimization/
├── public_transport_clustering_socrata.ipynb
├── nyc_bus_stops_map.html
├── clustered_bus_stops.csv
├── README.md
├── report.pdf
└── screenshots/
    ├── elbow_silhouette.png
    ├── folium_map.png
    ├── scatter_plot.png
```

## References
- [UN SDG 11](https://sdgs.un.org/goals/goal11)
- [NYC Open Data: MTA Bus Stops](https://data.cityofnewyork.us/Transportation/MTA-Bus-Stops/bi7e-6jgj)
- [Scikit-learn: K-means](https://scikit-learn.org/stable/modules/clustering.html)
- [Socrata API](https://dev.socrata.com/)
```