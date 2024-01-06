# hotel-demand-eda-and-prediction
This is an unofficial project solely intended for personal learning and research. The project is based on the [Hotel booking demand dataset from Kaggle](https://www.kaggle.com/datasets/jessemostipak/hotel-booking-demand). The project is a collaboration between Wei Kuo and Aknur Kassym.

## 1. Introduction

### Problem Statement

Our project focuses on leveraging predictive analytics to forecast future booking patterns. By analyzing historical data, we aim to analyze customer patterns and create models that predict booking trends. These insights will empower hotels to make informed decisions, optimize resource allocation, and tailor services to meet guest expectations. Without these predictive capabilities, hotels risk revenue loss due to misjudged demand or unmet guest needs. Thus, our emphasis on data-driven strategies aims to mitigate these risks and enhance guest satisfaction.

### Project Goal

The project’s goal is to offer a detailed understanding of booking patterns and behaviors within 2 hotels in Portugal - City Hotel and Resort Hotel. The analysis aims to cover client origins, peak demand days, seasonal pricing variations, booking patterns, and cancellation trends over time. Additionally, based on historical booking information prediction models like linear regression, logistic regression, and kNN will be developed to forecast future potential cancellations.

## 2. Description of the Dataset

### Overview

The Hotel Booking Demand dataset from Kaggle utilized in this project was initially published in Data in Brief in 2019 (Antonio, Almeida, & Nunes, 2019). This dataset, originally assembled by Nuno Antonio, Ana Almeida, and Luis Nunes, was curated and cleaned by Thomas Mock and Antoine Bichat for the #TidyTuesday initiative in February 2020. The dataset used in this project comprises booking details for two hotels in Portugal - City Hotel and Resort Hotel.

### Technical Details

#### Part 0 - Exploratory Data Analysis & Variable Selection

In part 0 of the project, we included 8 questions to gain a deeper understanding of the dataset we are going to handle. They are as follows:
- Where do the guests come from?
- How much do guests pay for a room per night?
- How does the price per night vary over the year?
- Which are the most busy months?
- What are the bookings in each market segment?
- How long do people stay at the hotels?
- How many bookings were canceled?
- Which month has the highest number of guests?

Initially, all 30 variables in the dataset are considered. To narrow them down, correlation analysis with the target variable ('is_cancelled') is performed after encoding categorical variables using LabelEncoder(). This results in the selection of 10 variables with the highest correlation with 'is_cancelled'.

#### Part 1 - Classification Models

**Normalization:** The selected variables are normalized using StandardScaler() to standardize their values and bring them to a common scale.
**Model Selection:** Three classification models are used: logistic regression, decision tree, and k-nearest neighbors (KNN).
**Training and Testing:** The dataset is split into a 70-30 ratio for training and testing, respectively, using a train-test split.

#### Part 2 - Neural Network Model

**Neural Network Architecture:** A three-layer neural network is constructed with layer dimensions of (10, 200), (200, 200), and (200, 2), incorporating ReLU activation functions for each layer.
**Loss Function and Optimizer:** Cross-entropy loss is employed as the chosen loss function, and the Adam optimizer is utilized for updating network weights.
**Hyperparameter Tuning:** Two hyperparameters are tested: batch size (16, 64) and learning rate (0.1, 0.5).

## 3. Results

### Exploratory Data Analysis

The analysis of the dataset revealed intriguing insights into customer demographics and booking behaviors. Notably, approximately one-third of the guests hail from Portugal, with the remaining half predominantly originating from Britain, France, Spain, and Germany (Figure 1). Room pricing displayed a notable variance based on room type, ranging from approximately $87 to $180 (Figure 2). A substantial surge in prices during the summer months was indicative of heightened demand, with rates reaching $142 in August compared to $67 in January (Figure 4).

Moreover, our examination revealed that nearly half of all bookings—specifically 47.5%—were made through online channels (Figure 3). Seasonality played a pivotal role, with summer emerging as the peak season for bookings (Figure 5). Interestingly, the City hotel exhibited higher demand compared to the Resort hotel (Figure 4), aligning with the trend observed in cancellations. It was evident that the volume of cancellations correlated proportionally with the overall booking volume, with the City hotel experiencing a higher cancellation rate than the Resort hotel (Figure 7). These findings underscore the impact of seasonality, online booking preferences, and the differing demand dynamics between the two hotel types.

### Cancellation Prediction Model

Our cancellation prediction model underwent rigorous evaluation, scrutinizing numerous parameters based on their correlation to the 'is_cancelled' variable. From this analysis, we curated a selection of ten influential parameters, including lead_time, country, total_of_special_requests, required_car_parking_spaces, assigned_room_type, distribution_channel, reservation_status_date, booking_changes, hotel, and previous_cancellations.

Among the hyperparameters we selected, there is not a significant difference between different combinations of learning rates and batch size. Regardless, learning rate = 0.1 and batch size = 16 produced the highest accuracy of 62, 95%. The results for our three-layer neural network are not as good as we initially predicted, and this is probably due to our inexperience in fine-tuning hyperparameters. However, on the other hand, the other three distinct models we selected all yielded promising results: Logistic Regression achieved a commendable accuracy of 75.57%, while both the Decision Tree and k-Nearest Neighbors models outperformed, showcasing impressive accuracy rates of 85.10% and 85.00%, respectively. These outcomes underscore the efficacy of our model selection, particularly highlighting the robust predictive capability of the Decision Tree and k-nearest Neighbors algorithms in foreseeing cancellations within the hotel bookings dataset.

| Model Type           | Accuracy     |
|----------------------|--------------|
| Neural Networks      | 62,95%       |
| Logistic Regression  | 75,57%       |
| Decision Tree        | 85,10%       |
| k-Nearest Neighbors  | 85,00%       |

## 4. Conclusion

Our project aimed to leverage historical data for predictive analysis in the hospitality sector, specifically focusing on booking trends within two Portuguese hotels. We conducted an in-depth exploration, unraveling customer demographics, pricing dynamics, market segmentation, stay durations, guest volumes, and cancellation trends. This extensive analysis provided comprehensive insights into booking behaviors.

Our primary achievement was the development and evaluation of predictive models—three-layered neural networks, logistic regression, kNN, and decision tree model. The decision tree model emerged as the most accurate, achieving an 85.10% cancellation prediction rate. This model empowers hotels to anticipate cancellations and optimize strategies.

Looking ahead, the groundwork laid in this project could pave the way for an overarching customer demand prediction model. Such a model, combining various predictive elements, could offer holistic insights into booking behaviors, aiding hotels in proactive resource management and tailored guest services.

By surpassing our initial goals, we've equipped hotels with valuable tools to anticipate future booking trends. This predictive capability ensures better resource allocation and services tailored to guest needs, mitigating revenue loss risks. Our journey signifies a step forward in enhancing operational efficiency and guest satisfaction within the hospitality industry.
