# 📘 RESTful-Booker API Documentation

This document provides full technical documentation for the publicly available **Restful-Booker API**, including all available endpoints, request/response formats, parameters, and usage examples.

---

## 🔐 Authentication

**POST** `/auth` — Create Auth Token  
Creates a new authentication token to be used with secured endpoints like PUT, PATCH, and DELETE.

- **URL**: `https://restful-booker.herokuapp.com/auth`
- **Headers**:
  - `Content-Type: application/json`
- **Request Body**:
```json
{
  "username": "admin",
  "password": "password123"
}
Success Response:

json
Copy
Edit
{
  "token": "abc123"
}
📋 Booking Endpoints
GET /booking — Get Booking IDs
Returns all booking IDs. Supports optional filters.

URL: https://restful-booker.herokuapp.com/booking

Optional Query Parameters:

firstname: string

lastname: string

checkin: date (YYYY-MM-DD)

checkout: date (YYYY-MM-DD)

Success Response:

json
Copy
Edit
[
  { "bookingid": 1 },
  { "bookingid": 2 },
  { "bookingid": 3 }
]
GET /booking/:id — Get Booking by ID
Returns the booking details for a given ID.

URL Example: https://restful-booker.herokuapp.com/booking/1

Headers:

Accept: application/json

Success Response:

json
Copy
Edit
{
  "firstname": "Sally",
  "lastname": "Brown",
  "totalprice": 111,
  "depositpaid": true,
  "bookingdates": {
    "checkin": "2013-02-23",
    "checkout": "2014-10-23"
  },
  "additionalneeds": "Breakfast"
}
POST /booking — Create Booking
Creates a new booking.

URL: https://restful-booker.herokuapp.com/booking

Headers:

Content-Type: application/json

Accept: application/json

Request Body:

json
Copy
Edit
{
  "firstname": "Jim",
  "lastname": "Brown",
  "totalprice": 111,
  "depositpaid": true,
  "bookingdates": {
    "checkin": "2018-01-01",
    "checkout": "2019-01-01"
  },
  "additionalneeds": "Breakfast"
}
Success Response:

json
Copy
Edit
{
  "bookingid": 1,
  "booking": {
    "firstname": "Jim",
    "lastname": "Brown",
    "totalprice": 111,
    "depositpaid": true,
    "bookingdates": {
      "checkin": "2018-01-01",
      "checkout": "2019-01-01"
    },
    "additionalneeds": "Breakfast"
  }
}
PUT /booking/:id — Update Entire Booking
Fully updates an existing booking.

URL: https://restful-booker.herokuapp.com/booking/1

Headers:

Content-Type: application/json

Accept: application/json

Cookie: token=abc123

Request Body:

json
Copy
Edit
{
  "firstname": "James",
  "lastname": "Brown",
  "totalprice": 111,
  "depositpaid": true,
  "bookingdates": {
    "checkin": "2018-01-01",
    "checkout": "2019-01-01"
  },
  "additionalneeds": "Breakfast"
}
Success Response: Same structure as request.

PATCH /booking/:id — Partial Update Booking
Partially updates a booking (e.g., just firstname).

URL: https://restful-booker.herokuapp.com/booking/1

Headers:

Content-Type: application/json

Cookie: token=abc123

Example Request Body:

json
Copy
Edit
{
  "firstname": "James"
}
Success Response: Returns updated booking with modified fields.

DELETE /booking/:id — Delete Booking
Deletes a booking. Requires authorization.

URL: https://restful-booker.herokuapp.com/booking/1

Headers (one of the following):

Cookie: token=abc123

Authorization: Basic YWRtaW46cGFzc3dvcmQxMjM=

Success Response:

h
Copy
Edit
HTTP/1.1 201 Created
🛡️ Authorization Methods
You must provide a valid token or Basic Auth to access secure endpoints (PUT, PATCH, DELETE).

Basic Auth Header (Base64 encoded):

makefile
Copy
Edit
Authorization: Basic YWRtaW46cGFzc3dvcmQxMjM=
Cookie Header:

makefile
Copy
Edit
Cookie: token=abc123
🗓️ Date Format
All date fields such as checkin and checkout follow the ISO format:

css
Copy
Edit
YYYY-MM-DD
🔗 Base URL
arduino
Copy
Edit
https://restful-booker.herokuapp.com
👨‍💻 Maintainer
Ahmed ElDamshity
📧 ahmed.eldamshity25@gmail.com
