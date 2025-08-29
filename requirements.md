# Requirements - Airbnb Clone Backend

## 1. User Authentication
### Endpoints
- POST /api/auth/register
  - Input: { name, email, password, role: guest|host }
  - Output: 201 Created { userId, token }
  - Validation: Unique email, valid format, password ≥ 8 chars

- POST /api/auth/login
  - Input: { email, password }
  - Output: 200 OK { token, user }

- GET /api/auth/profile
  - Auth: JWT
  - Output: 200 OK { user profile }

## 2. Property Management
- POST /api/properties
  - Role: host
  - Input: { title, description, location, price, amenities[], availability[] }

- GET /api/properties
  - Query params: location, priceRange, guests, amenities, page, limit

- PUT /api/properties/:id
  - Role: host (owner) or admin

- DELETE /api/properties/:id
  - Role: host (owner) or admin

## 3. Booking System
- POST /api/bookings
  - Input: { propertyId, startDate, endDate, guests }
  - Validation: Prevent double booking

- PATCH /api/bookings/:id/cancel
  - Role: guest or host

- GET /api/bookings
  - Role: guest/host/admin

## Performance & Security
- DB: PostgreSQL or MySQL
- Caching: Redis for search results
- File storage: AWS S3 or Cloudinary
- Payment: Stripe or PayPal (multi-currency)
