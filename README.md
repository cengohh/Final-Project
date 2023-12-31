# Delivery Duration Prediction

This data project has been used as a take-home assignment in the recruitment process for the data science positions at DoorDash.<br>

Assignment<br>
When a consumer places an order on DoorDash, we show the expected time of delivery. It is very important for DoorDash to get this right, as it has a big impact on consumer experience. In this exercise, you will build a model to predict the estimated time taken for a delivery.<br>

Concretely, for a given delivery you must predict the total delivery duration seconds , i.e., the time taken from<br>
Start: the time consumer submits the order (created_at) to<br>
End: when the order will be delivered to the consumer (actual_delivery_time)<br>

Data Description<br>
The attached file historical_data.csv contains a subset of deliveries received at DoorDash in early 2015 in a subset of the cities. Each row in this file corresponds to one unique delivery. We have added noise to the dataset to obfuscate certain business details. Each column corresponds to a feature as explained below. Note all money (dollar) values given in the data are in cents and all time duration values given are in seconds<br>

The target value to predict here is the total seconds value between created_at and actual_delivery_time.<br>

Columns in historical_data.csv<br>

Time features<br>

market_id: A city/region in which DoorDash operates, e.g., Los Angeles, given in the data as an id<br>
created_at: Timestamp in UTC when the order was submitted by the consumer to DoorDash. (Note this timestamp is in UTC, but in case you need it, the actual timezone of the region was US/Pacific)<br>
actual_delivery_time: Timestamp in UTC when the order was delivered to the consumer<br>

Store features<br>

store_id: an id representing the restaurant the order was submitted for<br>
store_primary_category: cuisine category of the restaurant, e.g., italian, asian<br>
order_protocol: a store can receive orders from DoorDash through many modes. This field represents an id denoting the protocol<br>

Order features<br>

total_items: total number of items in the order<br>
subtotal: total value of the order submitted (in cents)<br>
num_distinct_items: number of distinct items included in the order<br>
min_item_price: price of the item with the least cost in the order (in cents)<br>
max_item_price: price of the item with the highest cost in the order (in cents)<br>

Market features<br>

DoorDash being a marketplace, we have information on the state of marketplace when the order is placed, that can be used to estimate delivery time. The following features are values at the time of created_at (order submission time):<br>

total_onshift_dashers: Number of available dashers who are within 10 miles of the store at the time of order creation<br>
total_busy_dashers: Subset of above total_onshift_dashers who are currently working on an order<br>
total_outstanding_orders: Number of orders within 10 miles of this order that are currently being processed.<br>

Predictions from other models<br>

We have predictions from other models for various stages of delivery process that we can use:<br>

estimated_order_place_duration: Estimated time for the restaurant to receive the order from DoorDash (in seconds)<br>
estimated_store_to_consumer_driving_duration: Estimated travel time between store and consumer (in seconds)<br>
