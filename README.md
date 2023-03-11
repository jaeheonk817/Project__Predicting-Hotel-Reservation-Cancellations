![image](https://user-images.githubusercontent.com/122312679/224463306-25ef0c20-006a-49f7-bb80-1553a6b01af4.png)

# Predicting Hotel Reservation Cancellations
Authored by Jae Heon Kim
## Overview
With the advent of the post-pandemic world, traditional travel industries are facing sharp increase in reservation cancellations. Given the economic uncertainties and rising wages, Hilton is aiming to optimize its resources by correctly identifying instances of reservation cancellations.
## Business Understanding
Hilton is a prominent hospitality brand in the hotel industry that faces stiff competition from non-traditional rivals like Airbnb in the tech-oriented post-pandemic world. Hilton is confronting challenges of accurately predicting its reservation cancellations as it holds the key to optimal allocation of resources without falling short of customers' expectations. 


So we are creating a machine-learning prediction model that predicts whether a reservation will be cancelled. This model can make two types of mistakes:
- Predicted cancellation was wrong: This is not a problem as our stakeholders will still make business.
- Predicted non-cancellation was wrong. This is a huge problem as there are lost expected revenue and increased spending on overstaffing.

We want to build a prediction model that minimizes both of these errors, but with greater emphasis on reducing the second type of error.

## Data Introduction:

The dataset we are using is sourced from Kaggle Datasets([Source](https://www.kaggle.com/datasets/ahsan81/hotel-reservations-classification-dataset "source")) and includes information on hotel reservations made between 2017 and 2018 for a hotel in Algarve, Portugal, whose name wants to remain confidential for protection of customers' information. There are 19 columns and 36275 rows in the dataset, one of which is the target variable `booking_status`, indicating whether a reservation was cancelled or confirmed. Our goal is to develop a model that accurately predicts this outcome using information from the other columns.

Descriptions on attributes of the data are contained in the data dictionary that follows:

## Data Dictionary:
<details>
  <summary><strong>Click to view</strong></summary>
  
`Booking_ID`: unique identifier of each booking

`no_of_adults`: Number of adults

`no_of_children`: Number of Children

`no_of_weekend_nights`: Number of weekend nights (Saturday or Sunday) the guest stayed or booked to stay at the hotel

`no_of_week_nights`: Number of week nights (Monday to Friday) the guest stayed or booked to stay at the hotel

`type_of_meal_plan`: Type of meal plan booked by the customer:

`required_car_parking_space`: Does the customer require a car parking space? (0 - No, 1- Yes)

`room_type_reserved`: Type of room reserved by the customer. The values are ciphered (encoded) by INN Hotels.

`lead_time`: Number of days between the date of booking and the arrival date

`arrival_year`: Year of arrival date

`arrival_month`: Month of arrival date

`arrival_date`: Date of the month

`market_segment_type`: Market segment designation.

`repeated_guest`: Is the customer a repeated guest? (0 - No, 1- Yes)

`no_of_previous_cancellations`: Number of previous bookings that were canceled by the customer prior to the current booking

`no_of_previous_bookings_not_canceled`: Number of previous bookings not canceled by the customer prior to the current booking

`avg_price_per_room`: Average price per day of the reservation; prices of the rooms are dynamic. (in euros)

`no_of_special_requests`: Total number of special requests made by the customer (e.g. high floor, view from the room, etc)

`booking_status`: Flag indicating if the booking was canceled or not.

</details>

# Modeling / Evaluation

![image](https://user-images.githubusercontent.com/122312679/224463819-288f133c-796a-402e-a1f7-6601fb15d295.png)

This graph shows that every one out of three cancellations are canceled in our dataset. In other words, if we guessed that every reservation is kept, then we would correctly predict the outcome 2 out of 3 times. We are going to try different machine learning classification models that perform better than this, hopefully a lot better.

We will go on to make:
- Logistic Regression
- Decision Tree
- K-Nearest Neighbors
- Bayes Classification
- Random Forest
- XG Boost

models and visualize which ones work best.

<table>
  <tr>
    <td align="center"><img src="https://user-images.githubusercontent.com/122312679/224464305-df7dd192-72ec-468a-9757-27c34bdd0000.png" width="400px"></td>
    <td align="center"><img src="https://user-images.githubusercontent.com/122312679/224464314-69245ce2-77ef-47fb-85c5-326787d30a2e.png" width="400px"></td>
  </tr>
</table>

