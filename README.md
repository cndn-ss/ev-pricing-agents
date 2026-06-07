
# Dynamic Tariff Intelligence for EV Charging Networks 
### A Three-Agent Autonomous Pricing Framework

**Open Project 2026 | Society of Business**

## 📖 Overview
EV charging infrastructure in most markets currently operates on a flat ₹/kWh rate. While administratively simple, this causes two simultaneous structural failures:
1. **Peak-hour congestion:** Identical tariffs during high demand create queues, stranded vehicles, and grid strain.
2. **Off-peak underutilization:** Stations sit idle during late nights or early mornings, tying up capital without generating revenue.

This repository contains a reproducible, **end-to-end Agentic AI pricing engine** built to autonomously resolve these inefficiencies. By forecasting grid utilization and adjusting per-kWh tariffs dynamically, the framework smooths demand, maximizes operational efficiency, and improves overall network profitability.

##  Agentic Architecture
The framework is structured around three cooperating agents:

1. **Demand Prediction Agent:** Forecasts hourly grid utilization using temporal, infrastructure, and historical lag features. Evaluates Random Forest and Gradient Boosting models to output congestion probabilities and expected charging loads.
2. **Tariff Pricing Agent:** Translates demand forecasts into real-time tariff recommendations. Applies "surge" pricing during high-congestion hours (>80% utilization) and offers selective "discounts" during idle periods (<10–20% utilization).
3. **Monitoring & Learning Agent:** Simulates customer response using a transparent price-elasticity assumption (ε = −0.30) and evaluates each pricing decision against core KPIs (Revenue, Queue Proxy, Utilization Change, Pricing Efficiency). 

##  Datasets
This pipeline requires two official datasets (to be uploaded as ZIP files):
* **ACN-Data (`ACN Data.zip`):** Caltech session-level behavioral insights to evaluate session times, delivered energy, duration, and idle times.
* **UrbanEV (`UrbanEV.zip`):** Shenzhen city-scale dataset providing high-frequency demand signals for forecasting, utilization tracking, and congestion proxying.

##  Prerequisites & Setup
The project is optimized to run seamlessly in **Google Colab**. 

### Dependencies
No strict local environment setup is required if using Colab, but the notebook relies on standard data science libraries:
* `pandas`, `numpy` (Data manipulation)
* `scikit-learn` (Predictive modeling: Random Forest, Gradient Boosting)
* `matplotlib`, `seaborn` (Data visualization)

##  How to Run the Pipeline

1. **Open the Notebook:** Open `EV_Socbiz_Final.ipynb` in Google Colab or your local Jupyter environment.
2. **Upload Datasets:** Run the first cell. An upload widget will appear. Upload both `ACN Data.zip` and `UrbanEV.zip` directly into the environment. 
3. **Automatic Extraction:** The notebook will automatically extract, structure, and locate the necessary Excel (`.xlsx`) and CSV files.
4. **Execute Pipeline:** Run the remaining cells sequentially. The notebook will automatically:
   - Clean and reshape ACN data into hourly intervals.
   - Aggregate UrbanEV spatial-temporal matrices.
   - Train the Demand Prediction Agent.
   - Run the simulated pricing and customer response loops.
   - Generate all comparative visualizations.

##  Expected Outputs
Upon successful execution, the script generates an `outputs/` directory containing:
* **Evaluation Metrics Table:** Coverage of 9 core KPIs tracking the before-and-after performance of the pricing framework.
* **Annotated Visualizations:** 7 high-quality charts demonstrating EDA insights, demand shifts, revenue improvements, and elasticity curves (saved to `outputs/figures/`).
* **Final Submission Archive:** An automatically generated `.zip` file (`final_submission_outputs.zip`) containing all output CSVs and saved figures for easy downloading.

##  License & Acknowledgments
Developed for the Open Project 2026 | Society of Business. Datasets belong to their respective creators (Caltech ACN-Data and UrbanEV).
