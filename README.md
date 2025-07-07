# 🅿️ Dynamic Pricing for Urban Parking Lots

A real-time, data-driven pricing engine for urban parking lots, developed as part of the Summer Analytics 2025 Capstone Project. This system simulates dynamic pricing using demand patterns, real-time conditions, and competitive behavior to optimize parking lot utilization.

---

## 🚀 Project Objectives

- Build a **real-time pricing engine** for 14 urban parking lots.
- Develop **three tiers of pricing models**:
  1. **Baseline Linear Model**
  2. **Demand-Based Model**
  3. **Competitive Proximity Model**
- Visualize real-time pricing trends using **Bokeh**.

---

## 📦 Dataset

- 73 days of data sampled at 18 time points per day (8:00 AM to 4:30 PM).
- Features include:
  - `occupancy`, `queue`, `vehicle_type`
  - `traffic`, `special_day`, `latitude`, `longitude`
- **Note**: No `lot_id` provided, so synthetic IDs were generated from `(latitude, longitude)` pairs.

---

## 🧠 Modeling Approach

### 1. Baseline Linear Pricing
> Price increases linearly with occupancy ratio.

```python
new_price = previous_price + α * (occupancy / capacity)
