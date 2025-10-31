# mlops-used-cars-mirror
Used Cars Modeling

## Problem Statement

An automobile dealership in Los Vegas specializes in selling luxury and non-luxury vehicles. They cater to diverse customer preferences with varying vehicle specifications, such as mileage, engine capacity, and seating capacity. However, the dealership faces significant challenges in maintaining consistency and efficiency across its pricing strategy due to reliance on manual processes and disconnected systems. Pricing evaluations are prone to errors, updates are delayed, and scaling operations are difficult as demand grows. These inefficiencies impact revenue and customer trust. Recognizing the need for a reliable and scalable solution, the dealership is seeking to implement a unified system that ensures seamless integration of data-driven pricing decisions, adaptability to changing market conditions, and operational efficiency.

## Objective

The dealership has hired you as an MLOps Engineer to design and implement an MLOps pipeline that automates the pricing workflow. This pipeline will encompass data cleaning, preprocessing, transformation, model building, training, evaluation, and registration with CI/CD capabilities to ensure continuous integration and delivery. Your role is to overcome challenges such as integrating disparate data sources, maintaining consistent model performance, and enabling scalable, automated updates to meet evolving business needs. The expected outcomes are a robust, automated system that improves pricing accuracy, operational efficiency, and scalability, driving increased profitability and customer satisfaction.

## Data Description

- **Segment**: Describes the category of the vehicle, indicating whether it is a luxury or non-luxury segment.
- **Kilometers_Driven**: The total number of kilometers the vehicle has been driven.
- **Mileage**: The fuel efficiency of the vehicle, measured in kilometers per liter (km/l).
- **Engine**: The engine capacity of the vehicle, measured in cubic centimeters (cc).
- **Power**: The power of the vehicle's engine, measured in brake horsepower (BHP).
- **Seats**: The number of seats in the vehicle, can influence the vehicle's classification, usage, and pricing based on customer needs.
- **Price**: The price of the vehicle, listed in lakhs (units of 100,000), represents the cost to the consumer for purchasing the vehicle.
