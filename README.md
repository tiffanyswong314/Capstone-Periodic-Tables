# Capstone: Restaurant Reservation System

## Live application URL
https://periodic-tables-app.onrender.com

## Technology Used
### Frontend
- ReactJS
- CSS
- JSX

### Backend
- Postgres (knex)
- NodeJS
- Express

<br>

## Summary
Periodic Tables is a restaurant schedule management application that allows a restaurant manager to create/read tables and reservations. It provides the ability to search reservations by phone number and sort reservations by those that are booked, seated, and completed.

Users can also create tables and assign capacity to reflect the tables in the restaurant.

<br>

## Installation Instructions

### Frontend
- `cd` into `Thinkful-Final-Capstone/front-end`
  - run `npm install`
  - run `npm start` to start the application

### Backend
- `cd` into `Thinkful-Final-Capstone/back-end`
  - run `npm install`
  - run `npm start` to start the application

<br>

# Features

## Creating A Reservation
Creating a reservations is done by clicking 'New Reservation' on the navigation bar. This requires the customer's first name, last name, reservation date, reservation time, number of guests, and phone number.

![New Reservation](https://github.com/tiffanyswong314/Periodic-Tables-app/assets/137540866/c701ae72-7def-4583-98eb-fae9f2410b9d)


## Managing Reservations
Managing reservations can be done via the dashboard.

The dashboard by default will list the reservations for today. Use the previous and next buttons to look at reservations in the past or future.

![Dashboard](https://github.com/tiffanyswong314/Periodic-Tables-app/assets/137540866/07c5ba82-aaa5-477b-8951-3f7570adc981)


## Searching for a Specific Reservation
Users can search for a particular reservation by the phone number associated with the reservation. This can be done by clicking the 'Search' option in the navigation bar.

![Search](https://github.com/tiffanyswong314/Periodic-Tables-app/assets/137540866/875b82d1-f571-438c-a23b-9a726a20947b)


## Managing Tables
Expanding the restaurant? Create new tables by selecting the 'New Table' option in the navigation bar.

![Create Table](https://github.com/tiffanyswong314/Periodic-Tables-app/assets/137540866/a53615b2-f42f-4883-be4e-d26db8cb730e)



# API

## Create Reservation
**POST** `/reservations`
  - Required body:
    | Param      |  type     |
    | ---------- | ---------- |
    | `first_name` | `str` |
    | `last_name` | `str` |
    | `party` | `int` |
    | `reservation_date` | `date` |
    | `reservation_time` | `str` |
    | `mobile_number` | `str` |




## Get Reservations by Date
**GET** `/reservations?date=<reservation_date>`

Returns reservations for a particular date



## Get Reservations by Id
 `/reservations/:reservation_id`

### Available Methods
- **GET** - Returns a reservation given an existing reservation Id
- **PUT** - Modifies an existing reservation given an existing reservation Id
  - Required params:
    - `reservation_id (int)`
  - Required body:
    | Param      |  type     |
    | ---------- | ---------- |
    | `first_name` | `str` |
    | `last_name` | `str` |
    | `party` | `int` |
    | `reservation_date` | `date` |
    | `reservation_time` | `str` |
    | `mobile_number` | `str` |



## Get Reservation Status
**GET** `/reservations/:reservation_id/status`

Returns a status of [ `booked, seated, finished, cancelled` ] for the particular reservation



## Get Tables
- **GET** `/tables`

Returns the available tables.



## Create Table
- **POST** `/tables`

Creates a table to be listed in the table list.

 - Required body:
    | Param      |  type     |
    | ---------- | ---------- |
    | `table_name` | `str` |
    | `capacity` | `int` |



## Update Table Status
- **PUT** `/tables/:table_id/seat`

Sets table status to 'occupied' and ties a `restaurant_id` to it.

 - Required body:
    | Param      |  type     |
    | ---------- | ---------- |
    | `reservation_id` | `int` |



## Finish Table
- **DELETE** `/tables/:table_id/seat`

Sets the table status to `free` and the accompanying reservation status to `finished`
 - Required body:
    | Param      |  type     |
    | ---------- | ---------- |
    | `reservation_id` | `int` |