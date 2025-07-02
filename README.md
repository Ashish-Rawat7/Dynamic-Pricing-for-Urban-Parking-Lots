# Dynamic Pricing for Urban Parking Lots

## 🚗 Background and Motivation

Urban parking spaces are a scarce and highly demanded resource. Static pricing often leads to inefficiencies—either overcrowding or underutilization. To maximize utilization, dynamic pricing that adapts to real-time demand, competition, and environmental factors is essential.

This project simulates such a system. It builds an intelligent, data-driven pricing engine for 14 parking spaces using real-time data streams, economic theory, and machine learning models built from scratch (using only `numpy` and `pandas`). The code is designed for real-time streaming with [Pathway](https://pathway.com/) and visualization with [Bokeh](https://bokeh.org/).

---

## 🗂️ Data Description

The dataset covers 14 urban parking spaces over 73 days, sampled 18 times per day (every 30 minutes from 8:00 AM to 4:30 PM).  
Each record includes:

- **Location Information**
  - Latitude and Longitude (for proximity/competition calculations)

- **Parking Lot Features**
  - Capacity (maximum vehicles)
  - Occupancy (current vehicles)
  - Queue length (vehicles waiting)

- **Vehicle Information**
  - Incoming vehicle type: `car`, `bike`, or `truck`

- **Environmental Conditions**
  - Nearby traffic congestion level
  - Special day indicator (holidays, events)

---

## 🎯 Project Objective

Build a dynamic pricing model for each parking lot such that:

- Price updates in real time based on:
  - Historical occupancy patterns
  - Queue length
  - Nearby traffic
  - Special events
  - Vehicle type
  - Competitor prices
- Starts from a base price of $10
- Price variation is smooth and explainable
- (Optional) Suggests rerouting vehicles if a lot is overburdened

---

## 📈 Model Stages

### **Model 1: Baseline Linear Model**

- Linear price increase as occupancy increases  
  `Price_{t+1} = Price_t + α * (Occupancy / Capacity)`

### **Model 2: Demand-Based Price Function**

- Demand function considers occupancy, queue, traffic, special days, and vehicle type  
  Example:  
  `Demand = α*(Occupancy/Capacity) + β*QueueLength − γ*Traffic + δ*IsSpecialDay + ε*VehicleTypeWeight`  
  `Price_t = BasePrice * (1 + λ * NormalizedDemand)`  
- Demand is normalized, and price is bounded (0.5x to 2x of base)

### **Model 3: Competitive Pricing Model (Optional)**

- Adds location intelligence and competition:
  - Uses geographic proximity to find competitors
  - Factors in competitor prices
  - If full & competitors are cheaper → suggest reroute or reduce price
  - If competitors are more expensive → can increase price

---

## 🏃 Real-Time Simulation

- Uses [Pathway](https://pathway.com/) for streaming data ingestion and real-time processing
- Real-time Bokeh visualizations:
  - Pricing history for each parking lot
  - Competitor price comparisons

---

## 🛠️ Tech Stack

- Python (Google Colab)
- Pandas, Numpy (all models from scratch)
- Pathway (for streaming and real-time simulation)
- Bokeh (for real-time visualizations)

---

## 📊 Visualization

- Real-time price line plots for each parking lot
- Comparison plots with competitor prices

---

## 📄 How to Run

1. Clone this repo
2. Open the notebook in Google Colab
3. Install dependencies (see `requirements.txt` if provided)
4. Upload `dataset.csv`
5. Run all cells to simulate and visualize real-time dynamic pricing

---

## 📝 Report & Explanation

- **Demand Function:**  
  Described in the notebook and report, with coefficients and rationale for each feature.

- **Assumptions:**  
  Explained in detail (see notebook/report).

- **Price Adjustment:**  
  Logic for price updates and competition described step-by-step.

- **Visualizations:**  
  All Bokeh plots are embedded in the notebook and included in the report.

---

