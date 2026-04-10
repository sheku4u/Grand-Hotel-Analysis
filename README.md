<p style="font-family: 'Script Bold Italic'; font-size: 40px; font-style: italic; font-weight: bold; color: #9ceafe; margin: 0; text-align:center;">
   Learn About Data
</p>

><p style="font-family:Arial, sans-serif;font-size:16px;color:#white;">This dataset contains 119390 observations for a City Hotel and a Resort Hotel. Each observation represents a hotel booking between the 1st of July 2015 and 31st of August 2017, including booking that effectively arrived and booking that were canceled.</p>
Columns:


* **hotel:** One of the hotels is a resort hotel and the other is a city hotel.
* **is_canceled	lead_time:** Value indicating if the booking was canceled (1) or not (0).
* **arrival_date_year:** Year of arrival date.
* **arrival_date_month:** Month of arrival date with 12 categories: “January” to “December”.
* **arrival_date_week_number:** Week number of the arrival date.
* **arrival_date_day_of_month:** Day of the month of the arrival date.
* **stays_in_weekend_nights:** Number of weekend nights (Saturday or Sunday) the guest stayed or booked to stay at the hotel.
* **stays_in_week_nights:** Number of week nights (Monday to Friday) the guest stayed.
* **adults:** Number of adults
* **children:**	Number of Childern
* **babies:** Number of Babies
* **meal:** BB – Bed & Breakfast
* **country:** Country of origin.
* **market_segment:** Market segment designation. In categories, the term “TA” means “Travel Agents” and “TO” means “Tour Operators”
* **distribution_channel:** Booking distribution channel. The term “TA” means “Travel Agents” and “TO” means “Tour Operators”
* **is_repeated_guest:** Value indicating if the booking name was from a repeated guest (1) or not (0)
* **previous_cancellations:** Number of previous bookings that were cancelled by the customer prior to the current booking
* **previous_bookings_not_canceled:** Number of previous bookings not cancelled by the customer prior to the current booking
* **reserved_room_type:** Code of room type reserved. Code is presented instead of designation for anonymity reasons.
* **assigned_room_type:** Code for the type of room assigned to the booking. Sometimes the assigned room type differs from the reserved room type due to hotel operation reasons (e.g. overbooking) or by customer request. Code is presented instead of designation for anonymity reasons
* **booking_changes:** Number of changes/amendments made to the booking.
* **deposit_type:** No Deposit – no deposit was made; Non Refund – a deposit was made in the value of the total stay cost; Refundable – a deposit was made with a value under the total cost of stay.
* **agent:** ID of the travel agency that made the booking
* **company:** ID of the company/entity that made the booking or responsible for paying the booking. ID is presented instead of designation for anonymity reasons
* **days_in_waiting_list:**  Number of days the booking was in the waiting list before it was confirmed to the customer
* **customer_type:** Group – when the booking is associated to a group; Transient – when the booking is not part of a group or contract, and is not associated to other transient booking; Transient-party – when the booking is transient, but is associated to at least other transient booking
* **adr:**  Average Daily Rate (Calculated by dividing the sum of all lodging transactions by the total number of staying nights)
* **required_car_parking_spaces:**  Number of car parking spaces required by the customer
* **total_of_special_requests:**  Number of special requests made by the customer (e.g. twin bed or high floor)
* **reservation_status:** Check-Out – customer has checked in but already departed; No-Show – customer did not check-in and did inform the hotel of the reason why
* **reservation_status_date:** Date at which the last status was set. This variable can be used in conjunction with the ReservationStatus to understand when was the booking canceled or when did the customer checked-out of the hotel

<p style="font-family: 'Script Bold Italic'; font-size: 40px; font-style: italic; font-weight: bold; color: #009b90; margin: 0; text-align:center;">
   Data Analysis Project: Step-by-Step Guide
</p>

1. **Define the Problem Statement**
   - Clearly articulate the business or analytical problem you aim to solve.
   - Example: "Why are hotel cancellations increasing? What are the key factors driving these cancellations?"

2. **Data Acquisition**
   - Identify and gather the relevant dataset(s) for analysis.
   - Example: Download hotel booking data from sources such as Kaggle or company databases.

3. **Data Exploration & Cleaning**
   - Perform an initial exploration to understand data structure and quality.
     - Inspect columns, data types, and summary statistics.
   - Clean the data:
     - Handle missing values and duplicates.
     - Correct inconsistent data entries.
     - Convert data types if necessary.

4. **Data Analysis & Insight Generation**
   - Conduct exploratory data analysis (EDA) to identify patterns and trends.
   - Apply appropriate statistical or machine learning techniques if needed.
   - Extract actionable insights:
     - Example: "Which months have the highest cancellation rates?"

5. **Data Visualization & Communication**
   - Present findings using clear and impactful visualizations (e.g., bar charts, heatmaps, dashboards).
   - Summarize key insights in a concise report or presentation.
   - Optionally, build a dashboard for interactive exploration.

> **Tip:**  
> For each step, document your process and decisions in markdown. This not only shows your workflow but also demonstrates your communication skills to potential employers.


<p style="font-family: 'Script Bold Italic'; font-size: 40px; font-style: italic; font-weight: bold; color: #66cccc; margin: 0; text-align:center;">
   Business Problem
</p>

In recent years, both **City Hotel** and **Resort Hotel** have experienced high **cancellation rates**. These cancellations have led to several challenges, including reduced revenues and suboptimal utilization of hotel rooms. Lowering the cancellation rate is now a primary goal for both hotels to improve revenue generation and operational efficiency.

This analysis focuses on understanding the drivers behind hotel booking cancellations, as well as examining other factors that may impact business performance and annual revenue generation. The ultimate aim is to provide actionable business recommendations to address these challenges.


###  Assumptions

1. **Data Stability:** No extraordinary events occurred between 2015 and 2017 that significantly impacted the dataset.
2. **Data Relevance:** The data remains relevant for drawing insights and making future plans for the hotels.
3. **Implementation Neutrality:** There are no unforeseen negative consequences associated with implementing the recommended strategies.
4. **Current Practices:** The hotels have not yet adopted any of the proposed solutions.
5. **Primary Impact:** Booking cancellations are the main factor affecting the hotels’ revenue generation effectiveness.
6. **Room Vacancy:** Cancellations directly lead to vacant rooms for the originally booked period.
7. **Booking Timing:** Guests tend to cancel reservations within the same year as their booking.


### Research Questions ❓

1. **What are the key variables influencing hotel reservation cancellations?**
2. **What actionable strategies can be proposed to reduce cancellation rates?**
3. **How can insights from the analysis assist hotels in making effective pricing and promotional decisions?**

> **Tip:**  
> Keeping the business context and assumptions clear at the start of your analysis demonstrates a structured problem-solving approach and sets expectations for stakeholders.

~~~ python
# Importing Essential Libraries for Data Analysis & Visualization

import pandas as pd                         # Data manipulation and analysis
import numpy as np                          # Numerical operations (recommended for any analysis)
import matplotlib.pyplot as plt             # Basic plotting
import seaborn as sns                       # Advanced statistical data visualization

import warnings
warnings.filterwarnings('ignore')           # Suppress warnings for cleaner output

# Set Seaborn and Matplotlib aesthetic parameters globally
sns.set(style='whitegrid', palette='deep', font_scale=1.1)
plt.rcParams['figure.figsize'] = (10, 6)
plt.rcParams['axes.titlesize'] = 16
plt.rcParams['axes.labelsize'] = 14
plt.rcParams['legend.fontsize'] = 12
plt.rcParams['figure.dpi'] = 100

# Optional: Set pandas display options for better table output (optional, but nice for EDA)
pd.set_option('display.max_columns', 50)
pd.set_option('display.width', 1000)


~~~

``` python
# Loading the dataset
df = pd.read_csv('/kaggle/input/hotel-booking-demand/hotel_bookings.csv')
```


<p style="font-family: 'Script Bold Italic'; font-size: 40px; font-style: italic; font-weight: bold; color: #d3ffce; margin: 0; text-align:center;">
   Exploratory Data Analysis (EDA) & Data Cleaning
</p>


#### 1. Data Overview
- Load the dataset and inspect its shape, columns, and basic info.
- Display the first few rows to understand the data structure.

#### 2. Summary Statistics
- Use descriptive statistics to identify the distribution and typical values for each feature.

#### 3. Missing Values & Data Types
- Check for missing values and assess their proportion in each column.
- Review data types to ensure compatibility for analysis.

#### 4. Data Cleaning Steps
- Handle missing values:
  - Impute, fill, or remove as appropriate for each column.
- Address duplicate entries if present.
- Correct inconsistent data (e.g., capitalization, typos).
- Convert columns to correct data types (e.g., dates to datetime).

#### 5. Outlier Detection & Treatment
- Identify potential outliers using visualization or statistical methods.
- Decide on suitable actions: keep, cap, or remove.

### 6. Feature Engineering (Optional)
- Create new features if needed for deeper analysis (e.g., length of stay, booking lead time).


> **Tip:**  
> Document each step with code and markdown explanations. This shows your process and reasoning, making your project clear and compelling to reviewers.

``` python
# Display the first and last 5 rows to get a sense of the data
display(df.head())   # First 5 rows
display(df.tail())   # Last 5 rows
```

``` python
# Show the shape of the data (rows, columns)
print(f"Dataset contains {df.shape[0]:,} rows and {df.shape[1]} columns.\n")
```

``` python
# List all column names
print("Column names:")
print(df.columns.tolist())
print()
```

``` python
# Get info on data types and missing values
print("\nDataFrame Info:")
df.info()
print()
```

``` python
# Convert reservation_status_date to datetime for time-based analysis
df['reservation_status_date'] = pd.to_datetime(df['reservation_status_date'])
```

``` python
# Describe object (categorical) columns
print("\nSummary Statistics for Categorical Columns:")
display(df.describe(include='object'))
```

``` python
for col in df.describe(include = 'object').columns:
    print(col)
    print(df[col].unique())
    print('`'*50)
```

``` python
# Show unique values for each categorical column for better understanding
print("Unique values in each categorical column:")
for col in df.select_dtypes(include='object').columns:
    print(f"\n{col}:")
    print(df[col].unique())
    print('-'*50)
```

<p style="font-family: 'Script Bold Italic'; font-size: 40px; font-style: italic; font-weight: bold; color: #ffede2; margin: 0; text-align:center;">
    Data Pre-processing
</p>

Data pre-processing is a crucial step to ensure data quality and reliability for analysis. The following tasks are typically performed:

#### 1. Handling Missing Values
- Identify columns with missing values and decide on an appropriate strategy (e.g., removal, imputation, or replacement with statistical measures).

#### 2. Removing Duplicates
- Check for and remove any duplicate records that may skew the analysis.

#### 3. Data Type Conversion
- Ensure all columns have the correct data types (e.g., dates as `datetime`, categorical variables as `category`).

#### 4. Standardizing Categorical Values
- Normalize textual/categorical data for consistency (e.g., converting to lower case, correcting typos, standardizing labels).

#### 5. Feature Engineering
- Create new features or transform existing ones to better capture the underlying patterns (e.g., length of stay, lead time).

#### 6. Outlier Treatment
- Detect and address outliers that may distort the analysis.

> **Tip:**  
> Always document your pre-processing steps and reasoning. This transparency increases the trustworthiness and reproducibility of your analysis.

``` python 
# Check for missing values in each column
print("Missing values per column:")
print(df.isnull().sum())
print()
```

``` python
# Drop columns with excessive missing values or limited analytical value
cols_to_drop = ['agent', 'company']
df.drop(cols_to_drop, axis=1, inplace=True)
print(f"Dropped columns: {cols_to_drop}")
```

``` python
# Drop any remaining rows with missing values
df.dropna(inplace=True)
print(f"Data shape after dropping NA: {df.shape}")
```

``` python
# Summary statistics for numerical columns
print("\nSummary statistics for numerical columns:")
display(df.describe())
```

``` python
# Outlier detection for 'adr' (Average Daily Rate)
plt.figure(figsize=(8, 4))
sns.boxplot(x=df['adr'], color='skyblue')
plt.title('Box Plot of Average Daily Rate (adr)')
plt.xlabel('Average Daily Rate (adr)')
plt.show()
```

``` python
# Remove extreme outliers in 'adr' for cleaner analysis
outlier_threshold = 5000
df = df[df['adr'] < outlier_threshold]
print(f"Data shape after removing adr outliers (adr < {outlier_threshold}): {df.shape}")
```

<p style="font-family: 'Script Bold Italic'; font-size: 40px; font-style: italic; font-weight: bold; color: #34481a; margin: 0; text-align:center;">
   Data Analysis & Visualizations
</p>

In this section, we’ll analyze the cleaned hotel booking dataset to uncover key insights and trends. Visualizations are used to communicate findings clearly and effectively.


#### 1. Univariate Analysis

- **Objective:** Understand the distribution of individual features.
- **Example Visualizations:**
  - **Hotel Type Distribution:** Countplot of bookings by hotel type.
  - **Cancellation Rate:** Pie chart or bar plot of canceled vs non-canceled bookings.
  - **Lead Time:** Histogram of lead time (days between booking and arrival).
  - **Customer Country:** Top 10 countries by number of bookings.


#### 2. Bivariate Analysis

- **Objective:** Explore relationships between two variables.
- **Example Visualizations:**
  - **Cancellation Rate by Hotel Type:** Compare cancellation rates between city and resort hotels.
  - **Lead Time vs. Cancellation:** Boxplot of lead time grouped by cancellation status.
  - **Monthly Booking Trends:** Line plot of bookings per month by hotel type.


#### 3. Multivariate Analysis

- **Objective:** Investigate interactions between multiple variables.
- **Example Visualizations:**
  - **Cancellation Rate by Market Segment and Hotel:** Heatmap or grouped bar chart.
  - **ADR Trends by Month and Hotel:** Line plot showing average daily rate trends.


#### 4. Visualization Best Practices

- Use clear titles, axes labels, and legends.
- Choose appropriate color palettes for clarity and aesthetics.
- Highlight key findings using annotations or color emphasis.
- Keep plots clean and avoid clutter.


> **Tip:**  
> After each plot, add a short markdown summary explaining the main insight or observation. This demonstrates both analytical and communication skills.

``` python
# Calculate the percentage of canceled and not canceled reservations
cancelled_perc = df['is_canceled'].value_counts(normalize=True) * 100
print("Reservation Status Percentage:\n", cancelled_perc)

# Enhanced: Plot the reservation status count with Seaborn for aesthetics
plt.figure(figsize=(6, 4))
sns.set_palette('pastel')
ax = sns.countplot(
    x=df['is_canceled'].map({0: 'Not Canceled', 1: 'Canceled'}),
    order=['Not Canceled', 'Canceled'],
    edgecolor='black'
)

# Add percentage annotations on bars
for p in ax.patches:
    height = p.get_height()
    percentage = height / df.shape[0] * 100
    ax.annotate(f'{percentage:.1f}%', (p.get_x() + p.get_width() / 2., height),
                ha='center', va='bottom', fontsize=12, color='black', weight='bold')

plt.title('Reservation Status Count', fontsize=15)
plt.xlabel('Reservation Status', fontsize=12)
plt.ylabel('Number of Bookings', fontsize=12)
sns.despine()
plt.tight_layout()
plt.show()
```

``` python 
plt.figure(figsize=(8, 4))
ax1 = sns.countplot(
    x='hotel',
    hue='is_canceled',
    data=df,
    palette='Blues'
)

# Set legend outside the plot for clarity
ax1.legend_.set_bbox_to_anchor((1, 1))
plt.title('Reservation Status in Different Hotels', fontsize=18)
plt.xlabel('Hotel', fontsize=14)
plt.ylabel('Number of Reservations', fontsize=14)
plt.xticks(fontsize=12)
plt.yticks(fontsize=12)
plt.legend(['Not Canceled', 'Canceled'], title='Status', bbox_to_anchor=(1, 1))
plt.tight_layout()
plt.show()
```

``` python
# Calculate cancellation percentage for Resort Hotel
resort_hotel = df[df['hotel'] == "Resort Hotel"]
resort_cancelled_perc = resort_hotel['is_canceled'].value_counts(normalize=True) * 100
print("Resort Hotel - Reservation Status Percentage:")
print(resort_cancelled_perc)
print('-'*40)

# Calculate cancellation percentage for City Hotel
city_hotel = df[df['hotel'] == "City Hotel"]
city_cancelled_perc = city_hotel['is_canceled'].value_counts(normalize=True) * 100
print("City Hotel - Reservation Status Percentage:")
print(city_cancelled_perc)
print('-'*40)
```

``` python
# Separate data for each hotel type
resort_hotel = df[df['hotel'] == "Resort Hotel"]
city_hotel = df[df['hotel'] == "City Hotel"]

# Group by reservation date and calculate mean ADR (Average Daily Rate)
resort_hotel_grouped = resort_hotel.groupby('reservation_status_date')['adr'].mean()
city_hotel_grouped = city_hotel.groupby('reservation_status_date')['adr'].mean()

# Plot ADR trends for both hotels
plt.figure(figsize=(20, 8))
plt.title('Average Daily Rate Over Time: City Hotel vs Resort Hotel', fontsize=28)
plt.plot(resort_hotel_grouped.index, resort_hotel_grouped.values, label='Resort Hotel', color='royalblue')
plt.plot(city_hotel_grouped.index, city_hotel_grouped.values, label='City Hotel', color='orangered')
plt.xlabel('Reservation Status Date', fontsize=20)
plt.ylabel('Average Daily Rate (ADR)', fontsize=20)
plt.legend(fontsize=20)
plt.xticks(fontsize=16)
plt.yticks(fontsize=16)
plt.tight_layout()
plt.show()
```

``` python
import calendar
# Extract month from reservation_status_date
df['month'] = df['reservation_status_date'].dt.month

plt.figure(figsize=(16, 8))
ax1 = sns.countplot(
    x='month',
    hue='is_canceled',
    data=df,
    palette='bright'
)

# Set legend and labels for clarity
legend_labels, _ = ax1.get_legend_handles_labels()
ax1.legend(legend_labels, ['Not Canceled', 'Canceled'], title='Status')
ax1.set_title('Reservation Status per Month', fontsize=20)
ax1.set_xlabel('Month', fontsize=14)
ax1.set_ylabel('Number of Reservations', fontsize=14)
ax1.set_xticklabels([calendar.month_abbr[m] for m in sorted(df['month'].unique())], fontsize=12)
plt.tight_layout()
plt.show()
```

``` python
plt.figure(figsize=(15, 8))
plt.title('Total ADR from Canceled Bookings per Month', fontsize=30)

# Group canceled bookings by month and sum ADR
monthly_adr_canceled = df[df['is_canceled'] == 1].groupby('month')[['adr']].sum().reset_index()

# Barplot
sns.barplot(
    x='month',
    y='adr',
    data=monthly_adr_canceled,
    palette='coolwarm'
)

# Set x-axis labels to month abbreviations
plt.xticks(
    ticks=range(len(monthly_adr_canceled['month'])),
    labels=[calendar.month_abbr[m] for m in monthly_adr_canceled['month']],
    fontsize=14
)
plt.xlabel('Month', fontsize=18)
plt.ylabel('Total ADR (Canceled Bookings)', fontsize=18)
plt.legend(['Monthly Income from Canceled Bookings'])
plt.tight_layout()
plt.show()
```

``` python
# Filter for canceled reservations
cancelled_data = df[df['is_canceled'] == 1]

# Get top 10 countries by number of cancellations
top_10_country = cancelled_data['country'].value_counts().head(10)

plt.figure(figsize=(8, 8))
plt.title('Top 10 Countries with Reservation Cancellations', fontsize=18)

# Pie chart
plt.pie(
    top_10_country,
    autopct='%.2f%%',
    labels=top_10_country.index,
    startangle=140,
    textprops={'fontsize': 12}
)

plt.tight_layout()
plt.show()
```

``` python
# Absolute counts per market segment
market_segment_counts = df['market_segment'].value_counts()
print("Market Segment Counts:\n", market_segment_counts)
print('-' * 40)

# Proportion (percentage) per market segment
market_segment_perc = df['market_segment'].value_counts(normalize=True) * 100
print("Market Segment Percentage:\n", market_segment_perc)
print('-' * 40)
```

``` python
# Compute ADR time series for cancelled reservations
cancelled_data = df[df['is_canceled'] == 1]
cancelled_df_adr = cancelled_data.groupby('reservation_status_date')[['adr']].mean()
cancelled_df_adr.reset_index(inplace=True)
cancelled_df_adr.sort_values('reservation_status_date', inplace=True)

# Compute ADR time series for not cancelled reservations
not_cancelled_data = df[df['is_canceled'] == 0]
not_cancelled_df_adr = not_cancelled_data.groupby('reservation_status_date')[['adr']].mean()
not_cancelled_df_adr.reset_index(inplace=True)
not_cancelled_df_adr.sort_values('reservation_status_date', inplace=True)

# Plot the ADR trends
plt.figure(figsize=(20, 6))
plt.title('Average Daily Rate: Cancelled vs Not Cancelled Reservations', color="Black", fontsize=20)
plt.plot(not_cancelled_df_adr['reservation_status_date'], not_cancelled_df_adr['adr'], label='Not Cancelled', color='royalblue')
plt.plot(cancelled_df_adr['reservation_status_date'], cancelled_df_adr['adr'], label='Cancelled', color='crimson')
plt.xlabel('Reservation Status Date', fontsize=14)
plt.ylabel('Average Daily Rate (ADR)', fontsize=14)
plt.legend(fontsize=14)
plt.tight_layout()
plt.show()
```

``` python 
# Filter for reservation_status_date between '2016-01-01' and '2017-09-01'
cancelled_df_adr = cancelled_df_adr[
    (cancelled_df_adr['reservation_status_date'] > '2016-01-01') &
    (cancelled_df_adr['reservation_status_date'] < '2017-09-01')
]

not_cancelled_df_adr = not_cancelled_df_adr[
    (not_cancelled_df_adr['reservation_status_date'] > '2016-01-01') &
    (not_cancelled_df_adr['reservation_status_date'] < '2017-09-01')
]
```
