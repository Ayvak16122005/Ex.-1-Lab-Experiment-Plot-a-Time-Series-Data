# Ex-01: Plot a Time Series Data

## NAME

Kavya T

## REG NO

2305003004

## Aim

To develop a Python program to plot and visualize time-series data and identify trends such as increasing, decreasing, constant, and seasonal patterns.

## Objectives

- To create time-series data for population, temperature, and commodity prices.
- To store and manage data using Pandas DataFrames.
- To plot time-series data using Matplotlib.
- To identify trends and seasonal patterns from graphs.
- To calculate statistical measures such as mean and standard deviation.
- To apply linear trend analysis and moving averages.

## Technologies Used

- Python
- NumPy
- Pandas
- Matplotlib
- SciPy

## Program

### Annual Population Time Series

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from scipy import stats

# Time-series data
year = np.arange(2015, 2026)
population = np.array([85, 88, 91, 95, 100, 103, 106, 110, 114, 118, 123])

# Create DataFrame
data = pd.DataFrame({
    "Year": year,
    "Population": population
})

print("ANNUAL POPULATION DATA")
print(data)

# Statistical measures
print("\nMean =", round(np.mean(population), 2))
print("Standard Deviation =", round(np.std(population), 2))

# Linear trend using SciPy
slope, intercept, r, p, std_err = stats.linregress(year, population)
trend = intercept + slope * year

print("\nLINEAR TREND")
print("Slope =", round(slope, 2))
print("R-squared =", round(r**2, 4))

# 3-year moving average
data["Smoothed"] = data["Population"].rolling(3).mean()

# Plot
plt.figure(figsize=(9, 5))
plt.plot(year, population, marker="o", label="Original")
plt.plot(year, trend, linestyle="--", label="Trend")
plt.plot(year, data["Smoothed"], marker="o", label="3-Year Moving Average")

plt.title("Annual Population Time Series (2015–2025)")
plt.xlabel("Year")
plt.ylabel("Population (Millions)")
plt.legend()
plt.grid()
plt.show()

print("\nObservation: The series shows an INCREASING TREND.")
```

### Monthly Temperature Time Series

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

# Time-series data
month = np.arange(1, 13)
month_name = ["Jan", "Feb", "Mar", "Apr", "May", "Jun",
              "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"]

temperature = np.array([25, 27, 30, 33, 35, 34,
                        32, 31, 30, 29, 27, 25])

# Create DataFrame
data = pd.DataFrame({
    "Month": month_name,
    "Temperature": temperature
})

print("MONTHLY TEMPERATURE DATA")
print(data)

# Statistical measures
print("\nMean =", round(np.mean(temperature), 2))
print("Standard Deviation =", round(np.std(temperature), 2))

# 3-month moving average
data["Smoothed"] = pd.Series(temperature).rolling(3).mean()

# Plot
plt.figure(figsize=(9, 5))
plt.plot(month_name, temperature, marker="o", label="Original")
plt.plot(month_name, data["Smoothed"], marker="o",
         label="3-Month Moving Average")

plt.title("Monthly Temperature Time Series")
plt.xlabel("Month")
plt.ylabel("Temperature (°C)")
plt.legend()
plt.grid()
plt.show()

print("\nObservation: The series shows a SEASONAL PATTERN.")
```

### Monthly Commodity Price Time Series

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from scipy import stats

# Time-series data
month = np.arange(1, 13)
month_name = ["Jan", "Feb", "Mar", "Apr", "May", "Jun",
              "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"]

price = np.array([4200, 4350, 4280, 4500, 4650, 4800,
                  4750, 4900, 5050, 5100, 5250, 5400])

# Create DataFrame
data = pd.DataFrame({
    "Month": month_name,
    "Price": price
})

print("MONTHLY COMMODITY PRICE DATA")
print(data)

# Statistical measures
print("\nMean =", round(np.mean(price), 2))
print("Standard Deviation =", round(np.std(price), 2))

# Linear trend using SciPy
slope, intercept, r, p, std_err = stats.linregress(month, price)
trend = intercept + slope * month

print("\nLINEAR TREND")
print("Slope =", round(slope, 2))
print("R-squared =", round(r**2, 4))

# 3-month moving average
data["Smoothed"] = pd.Series(price).rolling(3).mean()

# Plot
plt.figure(figsize=(9, 5))
plt.plot(month_name, price, marker="o", label="Original")
plt.plot(month_name, trend, linestyle="--", label="Trend")
plt.plot(month_name, data["Smoothed"], marker="o",
         label="3-Month Moving Average")

plt.title("Monthly Commodity Price Time Series")
plt.xlabel("Month")
plt.ylabel("Price")
plt.legend()
plt.grid()
plt.show()

print("\nObservation: The series shows an INCREASING TREND with some fluctuations.")
```

## Observations

### Population Data

The annual population data shows an increasing trend from 2015 to 2025.
<img width="757" height="767" alt="image" src="https://github.com/user-attachments/assets/bbc62267-cfb1-4391-9b1c-cbde01a98bca" />

### Temperature Data

The monthly temperature data shows a seasonal pattern. The temperature increases toward the middle of the year and decreases afterward.
<img width="762" height="777" alt="image" src="https://github.com/user-attachments/assets/77b58af2-a86a-48cc-9f9d-2ce3f4267f71" />

### Commodity Price Data

The commodity price data shows an overall increasing trend with some fluctuations.
<img width="762" height="772" alt="image" src="https://github.com/user-attachments/assets/9f78abcc-afcc-45e1-86b6-a7839cb57417" />



## Result

Thus, time-series data for annual population, monthly temperature, and monthly commodity prices were successfully created, stored using Pandas, and visualized using Matplotlib. The population and commodity price graphs show an overall increasing trend, while the temperature graph shows a seasonal pattern, with temperatures increasing toward the middle of the year and decreasing afterward.

