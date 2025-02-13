# E-WasteX

This is a MERN stack-based platform for e-waste recycling, allowing users to buy, sell, donate, and bid on e-waste. The platform also features a rewards system where users earn coins for their contributions, which can be exchanged for cryptocurrency.

## Table of Contents
- [Website](#website)
- [Installation](#installation)
- [API Endpoints](#api-endpoints)
  - [E-Waste Management](#e-waste-management)
    - [Create E-Waste](#create-e-waste)
    - [Get All E-Waste Items](#get-all-e-waste-items)
    - [Get E-Waste by ID](#get-e-waste-by-id)
    - [Place a Bid](#place-a-bid)
    - [Update E-Waste Status](#update-e-waste-status)
    - [Delete E-Waste](#delete-e-waste)
- [Schema Definitions](#schema-definitions)
  - [User Schema](#user-schema)
  - [E-Waste Schema](#e-waste-schema)
  - [Bid Schema](#bid-schema)
  - [Reward Schema](#reward-schema)

## Website 
Link - https://ewaste-x.netlify.app/

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/Anuj5504/EWaste-X.git
   ```
2. Install dependencies:
   ```bash
   cd ewastex
   npm install
   ```

3. Start the server:
   ```bash
   cd backend
   npm run dev
   cd ..
   ```
4. Start the Frontend:
   ```bash
   cd frontend
   npm run dev
   ```


## API Endpoints
### E-Waste Management

#### 1. Create E-Waste
**Endpoint:** `POST /api/ewaste/create`

**Description:** Creates a new e-waste item with details such as category, condition, location, and pricing information.

**Request Headers:**
```json
{
  "Authorization": "Bearer <your-token>"
}
```

**Request Body:**
```json
{
  "itemName": "Old Laptop",
  "category": "Electronics",
  "condition": "Used",
  "weight": 2.5,
  "quantity": 1,
  "location": "Pune, India",
  "donationOrSale": "sell",
  "price": 100,
  "biddingEnabled": true,
  "biddingEndTime": "2025-03-01T12:00:00Z"
}
```

**Response:**
```json
{
  "message": "E-Waste created successfully",
  "ewaste": {
    "_id": "12345",
    "itemName": "Old Laptop",
    "category": "Electronics",
    "condition": "Used",
    "location": "Pune, India"
  }
}
```

---

#### 2. Get All E-Waste Items
**Endpoint:** `GET /api/ewaste/all`

**Description:** Retrieves a list of all available e-waste items.

**Response:**
```json
[
  {
    "_id": "123",
    "itemName": "Old Laptop",
    "category": "Electronics",
    "condition": "Used"
  }
]
```

---

#### 3. Get E-Waste by ID
**Endpoint:** `GET /api/ewaste/:id`

**Description:** Retrieves detailed information about a specific e-waste item.

**Response:**
```json
{
  "_id": "123",
  "itemName": "Old Laptop",
  "category": "Electronics",
  "condition": "Used"
}
```

---

#### 4. Place a Bid
**Endpoint:** `POST /api/bids/:ewasteId`

**Description:** Allows users to place a bid on an e-waste item with bidding enabled.

**Request Body:**
```json
{
  "user": "user_id",
  "amount": 50
}
```

**Response:**
```json
{
  "message": "Bid placed successfully",
  "bid": {
    "_id": "98765",
    "user": "user_id",
    "amount": 50,
    "ewasteId": "12345"
  }
}
```

---

#### 5. Update E-Waste Status
**Endpoint:** `PATCH /api/ewaste/:id/status`

**Description:** Updates the status of an e-waste item (e.g., from "available" to "sold").

**Request Body:**
```json
{
  "status": "sold"
}
```

**Response:**
```json
{
  "message": "E-Waste status updated successfully",
  "ewaste": {
    "_id": "12345",
    "status": "sold"
  }
}
```

---

#### 6. Delete E-Waste
**Endpoint:** `DELETE /api/ewaste/:id`

**Description:** Deletes an e-waste item permanently from the system.

**Response:**
```json
{
  "message": "E-Waste item deleted successfully"
}
```

---

### Schema Definitions

#### User Schema
Defines user-related information, including name, email, wallet address, and recycling activity.

#### E-Waste Schema
Represents e-waste items, including their condition, location, and pricing details.

#### Bid Schema
Defines bidding-related details, including bid amounts and associated e-waste items.


