# Anomaly Detection Playground

**Live Demo:** [[GitHub Page Link Here](https://chrishawnm.github.io/anomaly_detection/)]

This project is an interactive visualization tool designed to demonstrate the differences between **Standard Z-Score** and **Modified Z-Score** (Median/MAD) when detecting anomalies in time-series data.

## 🎯 Overview

In data analytics, correctly identifying outliers is critical. However, the method you choose matters. This playground uses a random dataset generator to simulate real-world server CPU loads or transaction data, allowing users to manipulate variables like growth trends, outlier magnitude, and time windows to see how different statistical methods react.

## 🧮 The Concept: Mean vs. Median

The core purpose of this tool is to visualize the **"Masking Effect"** caused by large outliers.

### 1. The Standard Z-Score (Fragile)
* **Formula:** `(Value - Average) / Standard Deviation`
* **The Problem:** The Mean (Average) and Standard Deviation are highly sensitive to extreme values. If you have one massive outlier (a "Whale"), it pulls the average up and inflates the standard deviation. This "squashes" the Z-scores of smaller anomalies, effectively hiding them from detection.

### 2. The Modified Z-Score (Robust)
* **Formula:** `(Value - Median) / MAD`
* **The Solution:** This method uses the Median and Median Absolute Deviation (MAD). These metrics are robust, meaning they are not easily influenced by extreme outliers. By isolating the "Whales," this method ensures that the baseline remains stable, allowing you to successfully detect smaller, more subtle anomalies.

## 🛠 Features & Controls

Here is a breakdown of the interactive controls available in the playground:

### 📈 Yearly Growth Trend
* **What it does:** Simulates "Data Drift" (e.g., business growth or increased server load over time).
* **Why it matters:** Comparing data from 3 years ago to today is often inaccurate because the baseline has changed. A 40% CPU load might have been an anomaly in Year 1, but normal in Year 3.

### 🐋 Number & Size of Anomalies
* **What it does:** Injects random anomalies into the dataset. The "Size" slider acts as a multiplier to create "Whales."
* **Why it matters:** This allows you to test the breaking point of the Standard Z-Score. By creating massive outliers, you can observe how the Standard Z-Score fails to flag smaller anomalies while the Modified Z-Score catches them.

### 🚨 Alert Threshold
* **What it does:** Sets the sensitivity of the red "Alert" dots.
* **Why it matters:** In real-world distributed systems, not every statistical anomaly is a business problem. This mimics the "Alert Fatigue" problem, allowing engineers to tune out noise and focus only on critical issues.

### 📅 Date Field Slider (Contextual Analysis)
* **What it does:** Filters the date range and recalculates statistics based on the view.
* **Why it matters:** This is the most powerful feature. It recalculates the Z-Scores based only on the visible time window. This simulates "Contextual Anomaly Detection," where a data point is evaluated against its immediate neighbors rather than a global historical average.

## 🚀 How to Test

1.  **Generate Data:** Start with the default settings.
2.  **Create a "Whale":** Increase the Anomaly Size slider to the maximum (20x).
3.  **Compare Methods:**
    * **Switch to Standard Z-Score:** Notice how the smaller anomalies often turn blue (undetected) because the "Whale" has skewed the math.
    * **Switch to Modified Z-Score:** Notice how the smaller anomalies turn red (detected) because the Median remains stable.
4.  **Test Context:** Use the Date Slider to zoom in on a specific cluster of data to see how the anomalies update in real-time based on the local context.

## 💻 Tech Stack

* HTML5/JavaScript
* Chart.js (Data Visualization)
* noUiSlider (Range Selection)
* Tailwind CSS (Styling)

--
