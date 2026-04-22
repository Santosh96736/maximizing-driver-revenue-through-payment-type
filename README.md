# Maximizing Driver Revenue Through Payment Type

## Table of Contents
- [Project Overview](#project-overview)
- [Business Problem](#business-problem)
- [Dataset](#dataset)
- [Technical Approach](#technical-approach)
- [Statistical Testing](#statistical-testing)
- [Key Findings](#key-findings)
- [Business Recommendation](#business-recommendation)
- [Skills Demonstrated](#skills-demonstrated)
- [Contact](#contact)


# Project Overview
This project analyzes NYC Yellow Taxi trip data to determine whether payment type (Card vs Cash) significantly impacts driver revenue per trip.

Using statistical analysis and hypothesis testing, we evaluate whether encouraging digital payments can increase driver earnings.

# Business Problem
Taxi drivers receive payments via multiple methods.
However, it is unclear whether:

- Card payments generate higher revenue than cash

- The difference is statistically significant

- Payment behavior impacts earnings

This project aims to answer:

Does payment type significantly affect driver revenue?

# Dataset
- Source: NYC Yellow Taxi Trip Data (2023)

- Time Period Used: January–February 2023

- Size: Multi-million trip records

- Processing Method: Chunk-based loading for memory efficiency

> ⚠️ Note: The original dataset is not included in this repository due to its large size. However, it is publicly available on data.gov.

## Selected Columns
| Column           | Description                           |
| ---------------- | ------------------------------------- |
| pickup_datetime  | Trip start time                       |
| dropoff_datetime | Trip end time                         |
| passenger_count  | Number of passengers                  |
| trip_distance    | Distance traveled (miles)             |
| payment_type     | Types of payment (Card, Cash)         |
| fare_amount      | Revenue per trip                      |


# Technical Approach 

## Large-Scale Data Handling
- Used chunksize=1_000_000

- Filtered specific months

- Wrote processed subset to a new CSV

- Ensured reproducibility (file deletion before append)

## Data Cleaning

- Removed missing values

- Removed duplicates

- Filtered unrealistic records:

   - Duration > 0

   - Distance > 0

   - Fare > 0

- Restricted to:

   - Passenger count 1–5

   - Payment types: Card & Cash only

   - Outlier removal using IQR method

## Feature Engineering

Created:  

- Trip duration (minutes)

This helped validate realistic trip behavior.

## Exploratory Data Analysis

Analyzed:

- Fare distribution by payment type

- Trip distance distribution

- Payment preference distribution

- Passenger count segmentation

Key observation:

- Card payments dominate usage

- Card trips show higher average fares
![Fare and Distance Distribution By Payment Type](https://github.com/Santosh96736/Maximizing-Driver-Revenue-Through-Payment-Type/blob/main/fare_%26_distance_distribution_by_payment_type.png)

## Statistical Testing
Hypothesis

- H₀: Payment type has no effect on average fare
- H₁: Payment type significantly affects average fare

Test Used  

- Welch’s t-test (unequal variance assumption)  
```st.ttest_ind(card_sample, cash_sample, equal_var=False)```

Result

- p-value < 0.05

- Null hypothesis rejected

Conclusion:

- Payment type significantly impacts driver revenue per trip.

> ⚠️ Note: While the t-test confirms statistical significance, further analysis controlling for trip distance and duration would help isolate whether payment type independently impacts revenue.

## Key Findings

- Card payments have higher average fare than cash.

- Revenue difference is statistically significant.

- Card transactions show lower variability than cash.

## Business Recommendation

Encouraging digital payments can improve both revenue and predictability for drivers. Ride-hailing platforms can introduce incentives such as cashback or discounts to promote card usage. Additionally, understanding that card users tend to generate higher fares can help in designing targeted pricing strategies and improving overall revenue optimization.

## Skills Demonstrated

- Large-scale data processing

- Data cleaning & validation

- Feature engineering

- EDA & visualization

- Hypothesis testing

- Business interpretation

## Contact
If you would like to discuss this project or collaborate:

-  📧 EMAIL : [Santosh Kumar Sahu](santosh96736@gmail.com)
-  🔗 LINKEDIN : [Santosh Kumar Sahu](https://www.linkedin.com/in/santosh-kumar-sahu-data-analyst)
