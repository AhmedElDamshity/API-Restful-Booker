# 📘 RESTful-Booker API Documentation

This document provides full technical documentation for the publicly available **Restful-Booker API**, including all available endpoints, request/response formats, parameters, and usage examples.

---

## 🔐 Authentication

### ✅ POST `/auth` – Create Auth Token

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
```

- **Success Response (200 OK)**:

```json
{
  "token": "abc123"
}
```

---

## 📋 Booking Endpoints

---

### 📄 GET `/booking` – Get Booking IDs

Returns all booking IDs. Supports optional filters.

- **URL**: `https://restful-booker.herokuapp.com/booking`
- **Optional Query Parameters**:
  - `firstname`: string
  - `lastname`: string
  - `checkin`: date (YYYY-MM-DD)
  - `checkout`: date (YYYY-MM-DD)
- **Success Response (200 OK)**:

```json
[
  { "bookingid": 1 },
  { "bookingid": 2 }
]
```

---

### 📄 GET `/booking/:id` – Get Booking by ID

Returns booking details for a specific booking ID.

- **URL Example**: `https://restful-booker.herokuapp.com/booking/1`
- **Headers**:
  - `Accept: application/json`
- **Success Response (200 OK)**:

```json
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
```

---

### 📝 POST `/booking` – Create New Booking

Creates a new booking record.

- **URL**: `https://restful-booker.herokuapp.com/booking`
- **Headers**:
  - `Content-Type: application/json`
  - `Accept: application/json`
- **Request Body**:

```json
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
```

- **Success Response (200 OK)**:

```json
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
```

---

### ✏️ PUT `/booking/:id` – Update Entire Booking

Fully updates an existing booking.

- **URL**: `https://restful-booker.herokuapp.com/booking/1`
- **Headers**:
  - `Content-Type: application/json`
  - `Accept: application/json`
  - `Cookie: token=abc123`
- **Request Body**:

```json
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
```

- **Success Response (200 OK)**: Same structure as above.

---

### ✏️ PATCH `/booking/:id` – Partial Update Booking

Updates only specified fields of a booking.

- **URL**: `https://restful-booker.herokuapp.com/booking/1`
- **Headers**:
  - `Content-Type: application/json`
  - `Cookie: token=abc123`
- **Example Request Body**:

```json
{
  "firstname": "James"
}
```

- **Success Response (200 OK)**: Returns the updated fields in the booking.

---

### ❌ DELETE `/booking/:id` – Delete Booking

Deletes a booking using token or basic auth.

- **URL**: `https://restful-booker.herokuapp.com/booking/1`
- **Headers (one of the following)**:
  - `Cookie: token=abc123`
  - `Authorization: Basic YWRtaW46cGFzc3dvcmQxMjM=`

- **Success Response**:

```http
HTTP/1.1 201 Created
```

---

## 🔐 Auth Methods

| Header Type     | Description                                       |
|------------------|---------------------------------------------------|
| Cookie           | `token=abc123` used in PUT, PATCH, DELETE         |
| Authorization    | Basic auth: `admin:password123` (Base64 encoded)  |

---

## 📆 Date Format

All dates must be in the ISO format:

```
YYYY-MM-DD
```

---

## 🌐 Base URL

```
https://restful-booker.herokuapp.com
```

---

## 👨‍💻 Maintainer

**Ahmed ElDamshity**  
📧 ahmed.eldamshity25@gmail.com