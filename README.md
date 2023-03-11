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

### Data Introduction:

The dataset we are using is sourced from Kaggle Datasets([Source](https://www.kaggle.com/datasets/ahsan81/hotel-reservations-classification-dataset "source")) and includes information on hotel reservations made between 2017 and 2018 for a hotel in Algarve, Portugal, whose name wants to remain confidential for protection of customers' information. There are 19 columns and 36275 rows in the dataset, one of which is the target variable `booking_status`, indicating whether a reservation was cancelled or confirmed. Our goal is to develop a model that accurately predicts this outcome using information from the other columns.

Descriptions on attributes of the data are contained in the data dictionary that follows:

### Data Dictionary:
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

## Modeling / Evaluation

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

`Decision Tree`, `Random Forest` and `XGBoost` have surpassed both the average value on accuracy and precision. We will use these three models to create our ensemble models. We will try `Stacking Classifier`, `Voting Classifier` and `Gradient Boost` and pick the one that works best based on their performance metrics.

<p float="left">
  <img src="https://user-images.githubusercontent.com/122312679/224465243-c2cefa1e-0e3e-4f37-a2e3-2b73c4dc881f.png" width="400" />
  <img src="https://user-images.githubusercontent.com/122312679/224465263-f342ff64-abd2-4b57-b048-114c143b9126.png" width="400" />
</p>

All three ensemble models work better than any of the individual models. `Stacking Classifier` does best in both accuracy and precision. Therefore we will choose this as our final model. However, difference in performances are subtle and `Voting Classifier` was the second best performer at much quicker pace. If the stakeholder wants a quick and economic computation, then this model could be a good alternative.

We will now dig deeper into our final model.
We noticed some important features are:
- Month of Arrival
- Reservation Segment Type
- Lead Time
- Average Price Per Night
- Number of Special Requests

We also noticed some less important features:
- Meal Plan Types
- Number of Previous Cancellations
- Room Types


Now we will dig dipper into the features that impact our final model by making their visualizations and using them to make recommendations to Hilton.

## Conclusion
In this part, we will make meaningful recommendations to Hilton and emphasize any noteworthy discoveries.

### Recommendation 1: Focus on strategies to improve summer reservations.
![image](https://user-images.githubusercontent.com/122312679/224465648-d948e98a-0654-46f1-997e-796982c8bc7e.png)
- January reservation confirmation is off the chart.
- Winter time reservation confirmations are more reliable than other times of the year.
- Summer time, especially near peak vacation times, there are too many cancellations.
- We believe there needs to be more focus and strategic approaches in dealing with reservations made for summer visits.

### Recommendation 2: Make business people come. Enhance their experiences.
![image](https://user-images.githubusercontent.com/122312679/224465694-bc2861a0-b9e4-4d0b-b1e8-064aee6fce5a.png)
- Free rooms are never cancelled.
- Business travelers are three times less likely to cancel their reservations compared to people who make their reservations through other segment type.
- We believe that Hilton should develope strategies on satisfying needs of business travelers, hopefully even offerring opportunities for business conventions.

### Recommendation 3: Price rooms just before steep increase in cancellation rate.
![image](https://user-images.githubusercontent.com/122312679/224465714-f8821c00-ce8a-4921-83c6-71f7bc671ba3.png)
- Reservations for room price below $40 are kept 98% of the times.
- Once a neighborhood for pricing is determined, choose specifically a price point right before a sharp increase in cancellation rate. We do not want to expose ourselves to much greater cancellation chances at the cost of couple extra bucks.

### Discovery 1: Reservations made 5 months prior are recipe for cancellations.
![image](https://user-images.githubusercontent.com/122312679/224465733-d0dcdb63-4872-4408-9f86-41f62f7d8329.png)
- Considering that reservations are twice more likey to be kept, the inflection point near at 5-month mark suggests an important warning.
- Reservations made five months prior or even earlier are very likely to be cancelled.

### Discovery 2: Special requests are welcome!
![image](https://user-images.githubusercontent.com/122312679/224465746-4972a7fd-dc90-4bee-8410-2a02ae2e4dae.png)
- Any customer-specific requests are not welcome to the businesses.
- However, in this specific case of dealing with cancellations, higher number of special requests guarantee non-cancellations. It could be possible that specific plans and expectations of customers equate to reservation confirmations.

## Next Steps
<b>For better correctness:</b>
- To increase the correctness of my model, I can search for more data which contains more person-specific information about person the reservation such as:
  - Person's 'Loyalty Program' status
  - Person's demographic information
  - Geographic location where reservation was made
  - Time it took for reservation to be made from the start (for online reservations)
  
- Maybe different ensemble methods can be used to enhance performance. This project will continue to be updated for hyperparameter tuning on ensemble. 

<b>For better generalizations:</b>
- This model was built based only on data generated from a single hotel. It could be overfitting to this specific hotel. To be generalized for predictions all across the globe, data from different hotels from different countries can help a lot.




