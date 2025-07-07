# 🅿️ Dynamic Pricing for Urban Parking Lots

**Capstone Project – Summer Analytics 2025**

---

## 🚀 Overview

Urban parking is a limited and valuable resource. Static pricing often leads to underutilization or overcrowding. This project simulates a **real-time dynamic pricing engine** for 14 urban parking lots using a data-driven approach and basic economic theory.

The system adjusts prices dynamically based on occupancy, queue, vehicle type, special events, traffic conditions, and competitive pricing from nearby lots.

---

## 🌟 Objectives

- Develop and compare three models:
  - ✅ Baseline Linear Pricing
  - ✅ Demand-Based Pricing
  - ✅ Competitive Pricing
- Simulate real-time behavior using a streaming framework
- Visualize real-time pricing using Bokeh

---

## 🧱 Architecture Overview

```
+------------------+
|  CSV Input Data  |  <--- Historical + real-time simulation data
+------------------+
         |
         v
+---------------------+
|   Data Preprocessing |
| (timestamp, features)|
+---------------------+
         |
         v
+---------------------+        +------------------------+
|  Pricing Engine     |<------>| Nearby Competitor Lots |
|  (Models 1–3)       |        +------------------------+
+---------------------+
         |
         v
+---------------------+
| Real-Time Simulator |
|   (Pathway)         |
+---------------------+
         |
         v
+---------------------+
|  Visualization (Bokeh) |
+---------------------+

---

## ⚙️ Tech Stack

| Layer                | Technology          |
| -------------------- | ------------------- |
| Data Processing      | Python, Pandas      |
| Math & Modeling      | Numpy               |
| Geo-Calculations     | Geopy               |
| Real-Time Simulation | Pathway (planned)   |
| Visualization        | Bokeh               |
| Deployment (future)  | Pathway / Streamlit |

---

## 📂 Dataset Description

- Sampled over 73 days, 18 time slices/day
- Key fields:
  - `timestamp`
  - `occupancy`, `capacity`
  - `queue`, `vehicle_type`
  - `traffic`, `special_day`
  - `latitude`, `longitude`
- Parking lots identified using synthetic `lot_id` from `(lat, long)`

---

## 📉 Pricing Models

### 1️⃣ Baseline Linear Pricing

```python
price = prev_price + alpha * (occupancy / capacity)

### 2️⃣ Demand-Based Dynamic Pricing

```python
demand = alpha * occ_rate + beta * queue - gamma * traffic + delta * is_special_day + epsilon * vehicle_weight

### 3️⃣ Competitive Pricing Model

- Proximity calculated using geodesic distance (within 1 km)
- Compare with neighboring lots
- Adjust price accordingly:
  - Lower price if competitors are cheaper
  - Raise price if competitors are more expensive

---

## 📊 Visualizations

Built using **Bokeh**:

- Real-time pricing line plots for all lots
- Overlay with competitor prices (dashed red)

Each plot shows:

- Blue line: own lot price
- Red dashed line: avg competitor price nearby

### 📷 Sample Screenshots

#### Real-Time Price vs Competitor (Lot 1)

![Lot 1 Pricing](images/lot1_pricing_plot.png)

#### Real-Time Pricing Overview (All Lots)

![All Lots](images/all_lots_overview.png)

> (Add these images to the `/images/` folder in your repo)

---

## 🔄 Real-Time Simulation

- 10 time ticks at 30-minute intervals
- For each tick:
  - Recalculate prices per lot
  - Fetch competitors in range
  - Update Bokeh plots live

Planned integration with **Pathway** to enable streaming from an external source.

---

