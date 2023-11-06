# Startupheroes Route Optimization Case Study #

This document provides the instructions for the assignment, including how to get started and submit your solution.


## Introduction

We deliver orders from stores to customers daily, considering specific time constraints and route optimization. Orders are picked up from stores by couriers and delivered afterward. Our goal is to optimize the couriers' routes while meeting delivery deadlines as closely as possible.

## Problem Description

Given the descriptions of orders and couriers, optimize the delivery schedule of couriers to deliver orders on time with optimal routes. We aim to minimize the total time spent on the road and maximize the number of orders delivered within their deadlines.

* All couriers start idle with no assigned orders.
* Assume all orders are ready for pickup at any time, and ignore service times at stores and customer addresses.
* Couriers travel on a grid map. Each edge traversal takes 1 minute.
  Example: Going from (0,0) to (0,1) takes 1 minute.
  Example: Going from (1,1) to (2,3) takes 3 minutes.
* All orders have a standard volume of 1 unit, and couriers have a limited carrying capacity.
* Each courier's route should contain only one cycle: visit the store once and then deliver orders.
* Late deliveries are allowed but not preferred.
* You can use as many vehicles as needed. The cost of additional vehicles is negligible.

## Input and Output Data Patterns

Input file starts with courier data at each line and then continues with order data after one empty line. 
Each courier has a unique couirerId, order capacity, current latitude, current longitude.
Each order has a unique orderId, delivery deadline (in minutes), pickup store latitude, pickup store longitude, destination latitude, destination longitude. 

For example, in the below sample input data, there are 3 couriers having package capacity of 2,3 and 3 respectively and couriers 1 and 2 are at position (10, 10), while courier number 3 is at position (10, 11). Then after one empty line, there are 4 orders having delivery deadlines of 8,12,10 and 10 minutes respectively with pick up and destination locations given afterwards. 
 
```
1,2,10,10
2,3,10,10
3,3,10,11

11,8,10,10,15,12
12,12,10,10,18,15
13,10,10,10,6,7
14,10,10,10,9,7
```

For this sample input, the ideal solution could be as follows. 

```
1, p11 -> p12 -> d11 -> d12, 13
2, p13 -> p14 -> d14 -> d13, 7
3, , 0
```

Each line provides the route of one courier and the total time spent on the road. In this solution, the total time spent by all couriers is 20 minutes, with 1 minute of late delivery for order 12.

## Optimization Goals

1.) Minimize Total Travel Time: Shorten the routes of couriers as much as possible. <br />
2.) Meet Delivery Deadlines: Deliver orders within their specified deadlines to the extent possible. 

Balancing these constraints is up to your discretion. Aim to provide a well-reasoned approach and solution.


## Solution Proposal

* This is a VRPTW problem (Vehicle Routing Problem With Time Window) including pickup and delivery constraint. You are expected to use OR-Tools in your solution. You can find detailed instructions about how to install OR-Tools in https://developers.google.com/optimization/install
* You can use any programming language, but using Java is preferable. 
* It does not matter if you read the input data from the file or if you put it directly into your code. Also, you can print the solution to the console or to a file, which does not matter too. What matters is how you approach to the problem and emphasize your reasoning. 
* Push your solution to `origin/<your-branch-name>`, and create a pull request. Please do not merge your pull request.
* Explaining your reasoning within code comments and PR description would be appreciated.
