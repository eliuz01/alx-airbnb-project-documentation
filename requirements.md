**User Authentication**
🔹 API Endpoints

| Method | Endpoint             | Description                                    |
| ------ | -------------------- | ---------------------------------------------- |
| POST   | `/api/auth/register` | Register a new user (guest or host)            |
| POST   | `/api/auth/login`    | Authenticate user credentials and return a JWT |
| GET    | `/api/auth/me`       | Retrieve authenticated user info               |

🔹 Input/Output Specifications
Register Request Payload:

{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "securePassword123",
  "role": "guest"
}
Register Response:

{
  "user": {
    "id": "1234",
    "name": "John Doe",
    "email": "john@example.com",
    "role": "guest"
  },
  "token": "jwt_token_here"
}

🔹 Validation Rules
Email must be unique and valid
Password must be at least 8 characters
Role must be either guest or host

🔹 Performance Criteria
Response time < 300ms under 1,000 concurrent users
JWT tokens must be signed using HMAC SHA-256
Token expiration: 1 hour, with refresh logic

**Property Management**
✅ API Endpoints
| Method | Endpoint              | Description                      |
| ------ | --------------------- | -------------------------------- |
| POST   | `/api/properties`     | Create a new property listing    |
| GET    | `/api/properties`     | List all properties (filterable) |
| GET    | `/api/properties/:id` | Retrieve a specific listing      |
| PUT    | `/api/properties/:id` | Update an existing property      |
| DELETE | `/api/properties/:id` | Delete a property                |

✅ Sample Request: Create Property
{
  "title": "Modern Apartment in Nairobi",
  "location": "Nairobi",
  "price_per_night": 50,
  "amenities": ["WiFi", "Kitchen"],
  "availability": ["2025-07-01", "2025-07-15"],
  "host_id": "7890"
}

✅ Sample Response
{
  "id": "abc123",
  "message": "Property created successfully"
}

🔎 Validation Rules
title, location are required.

price_per_night must be a positive number.

availability must include valid future dates.

host_id must be a verified host account.

🚀 Performance Requirements
Pagination support for 10,000+ listings.

Search and filter queries < 500ms.

Image uploads to use cloud storage (e.g., AWS S3, Cloudinary).

**🗓️ Booking System**
✅ API Endpoints

| Method | Endpoint            | Description              |
| ------ | ------------------- | ------------------------ |
| POST   | `/api/bookings`     | Create a booking         |
| GET    | `/api/bookings/:id` | Retrieve booking details |
| DELETE | `/api/bookings/:id` | Cancel a booking         |

🧾 Sample Request: Create Booking
{
  "property_id": "abc123",
  "guest_id": "guest789",
  "start_date": "2025-07-05",
  "end_date": "2025-07-10"
}

✅ Sample Response
{
  "booking_id": "bk2025",
  "status": "confirmed",
  "total_cost": 250
}
🔎 Validation Rules
start_date must be before end_date.

Check for overlapping dates.

Guests cannot book their own property.

Prevent race conditions on simultaneous bookings.

🚀 Performance Requirements
Transactional logic to avoid double-booking.

Availability check with database indexing.

Response time under 400ms for booking creation.