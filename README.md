# Location-based-Analysis

## Description
This ML Model provides a comprehensive analysis of restaurant data by focusing on key geographic and performance metrics. It utilizes data visualization techniques to present meaningful insights into restaurant distribution, concentration, and performance across different cities. Here’s a detailed overview of the process:

1. **Data Loading and Cleaning**
   - Import necessary libraries: `pandas` for data manipulation and `matplotlib` for plotting.
   - Load the dataset and handle missing values for critical location-based attributes like latitude and longitude.

2. **Geographic Visualization**
   - Visualize the distribution of restaurants on a geographic map using scatter plots.
   - Plot longitude and latitude to illustrate restaurant locations, highlighting the spread and density.

3. **City-Based Analysis**
   - Group the dataset by city to count the number of restaurants in each city.
   - Use bar charts to depict the concentration of restaurants, allowing for easy comparison across different cities.

4. **Performance Metrics by City**
   - Calculate average ratings and price ranges for restaurants in each city.
   - Merge the average rating and price range data into a single DataFrame for comprehensive analysis.

5. **Visualizing Ratings and Price Ranges**
   - Create combined visualizations to display average ratings and price ranges by city.
   - Use bar plots and line plots to provide a clear comparative view of how cities fare in terms of restaurant quality and affordability.

Sure, here are the sections for usage, algorithms used, installation, and license:

## 🖥️ Usage
To use this script for analyzing restaurant data, follow these steps:

1. **Load the Dataset**
   ```python
   import pandas as pd

   df = pd.read_csv('Dataset.csv')
   ```

2. **Handle Missing Values**
   ```python
   # Drop rows with missing values in latitude and longitude
   df = df.dropna(subset=['Latitude', 'Longitude'])
   ```

3. **Visualize Restaurant Distribution**
   ```python
   import matplotlib.pyplot as plt

   plt.figure(figsize=(10, 6))
   plt.scatter(df['Longitude'], df['Latitude'], alpha=0.5, c='blue')
   plt.xlabel('Longitude')
   plt.ylabel('Latitude')
   plt.title('Distribution of Restaurants')
   plt.show()
   ```

4. **Analyze Restaurant Concentration by City**
   ```python
   city_group = df.groupby('City').size().reset_index(name='Count')

   plt.figure(figsize=(12, 8))
   plt.barh(city_group['City'], city_group['Count'])
   plt.xlabel('Number of Restaurants')
   plt.ylabel('City')
   plt.title('Concentration of Restaurants by City')
   plt.show()
   ```

5. **Calculate and Visualize Average Ratings and Price Range**
   ```python
   avg_rating_city = df.groupby('City')['Aggregate rating'].mean().reset_index(name='Average Rating')
   avg_price_city = df.groupby('City')['Price range'].mean().reset_index(name='Average Price Range')
   city_stats = pd.merge(avg_rating_city, avg_price_city, on='City')

   fig, ax1 = plt.subplots(figsize=(12, 8))
   ax1.barh(city_stats['City'], city_stats['Average Rating'], color='blue', alpha=0.6, label='Average Rating')
   ax1.set_xlabel('Average Rating')
   ax1.set_ylabel('City')

   ax2 = ax1.twiny()
   ax2.plot(city_stats['Average Price Range'], city_stats['City'], color='red', marker='o', label='Average Price Range')
   ax2.set_xlabel('Average Price Range')

   plt.title('Average Rating and Price Range by City')
   plt.show()
   ```

## 📊 Algorithms Used
- **Data Cleaning**: Handle missing values by dropping rows with missing latitude and longitude.
- **Data Grouping**: Group data by city to count the number of restaurants.
- **Descriptive Statistics**: Calculate average ratings and price ranges for restaurants by city.
- **Data Visualization**: Use scatter plots, bar charts, and combined bar/line plots to visualize data distribution, concentration, and performance metrics.

## 🔧 Installation
To install and set up the project, follow these steps:

1. **Create and activate a virtual environment**
   ```bash
   python -m venv restaurant_env
   ```

   - For Windows:
     ```bash
     restaurant_env\Scripts\activate
     ```
   - For macOS/Linux:
     ```bash
     source restaurant_env/bin/activate
     ```

2. **Install required packages**
   ```bash
   pip install pandas matplotlib seaborn
   ```

## 📝 License
This project is licensed under the MIT License. See the LICENSE file for more details.
