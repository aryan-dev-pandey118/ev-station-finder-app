# Database & API Design

> Capstone Project — EV Charging Station Finder | Week 5 Report

---

## 1. Entities

Six entities were identified from the SRS functional requirements:

| Entity | Collection | Description |
|---|---|---|
| User | `users` | Registered EV drivers and admins. Stores login credentials, vehicle profile, and saved favourite stations. |
| Charging Station | `charging_stations` | Core data object. Stores geospatial location, connector types, pricing, and real-time availability. |
| Route | `routes` | A planned trip from origin to destination with one or more charging stops, distance, duration, and estimated cost. |
| Vehicle | `vehicles` | An EV profile linked to a user. Provides battery capacity and connector type for range and compatibility calculations. |
| Notification | `notifications` | An alert sent to a user when a watched station becomes available or a charging session completes. |
| Search History | `search_history` | A record of a user's past search queries with coordinates, used for personalisation. |

---

## 2. Relationships

- **User → ChargingStation** (many-to-many via favourites): A user can save many stations. Stored as an array of `ObjectId` references on the User document.
- **User → Vehicle** (one-to-many): A user can register multiple EVs. Each Vehicle references its owner by `userId`.
- **User → Route** (one-to-many): A user can plan and save multiple routes. Each Route references the user and vehicle used.
- **Route → ChargingStation** (one-to-many via waypoints): A route embeds an array of waypoints, each referencing a `ChargingStation` by `ObjectId` with planned charging duration.
- **User → Notification** (one-to-many): Each Notification references the user and related station.

> **Embedding decisions:** Connector objects are embedded inside `ChargingStation` (always read together, never queried independently). Route waypoints are embedded inside `Route` so an entire trip is retrieved in a single query.

---

## 3. Database Schema

### 3.1 Users

| Field | Type | Constraints |
|---|---|---|
| `_id` | ObjectId | Auto-generated primary key |
| `email` | String | Required, unique, indexed — validated email format |
| `passwordHash` | String | Required — Bcrypt hash at cost factor 10 |
| `firstName` / `lastName` | String | Required |
| `role` | String | Enum: `"user"` \| `"admin"`. Default: `"user"` |
| `vehicle` | Object | Optional — `{ make, model, year, batteryCapacity_kWh, connectorType }` |
| `favourites` | Array[ObjectId] | References to `charging_stations`. Default: `[]` |
| `mfaEnabled` | Boolean | Default: `false` |
| `createdAt` | Date | Auto-set on creation |

### 3.2 Charging Stations

| Field | Type | Constraints |
|---|---|---|
| `_id` | ObjectId | Auto-generated primary key |
| `stationName` | String | Required |
| `location` | GeoJSON Point | Required — `{ type: "Point", coordinates: [lng, lat] }`. 2dsphere index. |
| `address` | Object | Required — `{ street, suburb, state, postcode, country }` |
| `connectors` | Array[Object] | Required, min 1 — each: `{ type, power_kW, status: "available"\|"occupied"\|"offline" }` |
| `pricing` | Object | Optional — `{ model: "free"\|"per_kWh"\|"session", rate, sessionFee }` |
| `networkProvider` | String | Optional, indexed — e.g. `"Chargefox"`, `"Evie"`, `"Tesla"` |
| `operatingHours` | Object | Optional — `{ open, close, is24Hours }` |
| `isAvailable` | Boolean | Default: `true` — station-level availability flag |
| `source` | String | Required — `"OCM"` (Open Charge Map) or `"manual"` |
| `lastUpdated` | Date | Auto-updated on availability sync |

### 3.3 Routes

| Field | Type | Constraints |
|---|---|---|
| `_id` | ObjectId | Auto-generated primary key |
| `userId` | ObjectId | Required — ref: `users` |
| `vehicleId` | ObjectId | Required — ref: `vehicles` |
| `origin` | GeoJSON Point | Required — departure coordinates |
| `destination` | GeoJSON Point | Required — arrival coordinates |
| `waypoints` | Array[Object] | Embedded — each: `{ stationId, arrivalTime, chargingDuration_min }` |
| `totalDistance_km` | Number | Required |
| `totalDuration_min` | Number | Required — includes travel and charging time |
| `estimatedCost_AUD` | Number | Optional |
| `createdAt` | Date | Auto-set on creation |

### 3.4 Notifications

| Field | Type | Constraints |
|---|---|---|
| `_id` | ObjectId | Auto-generated primary key |
| `userId` | ObjectId | Required — ref: `users` |
| `stationId` | ObjectId | Required — ref: `charging_stations` |
| `type` | String | Enum: `"station_available"` \| `"session_complete"` \| `"system"` |
| `message` | String | Required — notification body text |
| `isRead` | Boolean | Default: `false` |
| `createdAt` | Date | Auto-set on creation |

### 3.5 Indexes

| Collection | Index | Purpose |
|---|---|---|
| `charging_stations` | `location` (2dsphere) | Powers `$geoNear` query for nearby station discovery |
| `charging_stations` | `isAvailable` | Fast filtering of available stations on the map |
| `charging_stations` | `networkProvider` | Supports the network provider filter |
| `users` | `email` (unique) | Fast login lookup and uniqueness enforcement on registration |
| `notifications` | `userId + isRead` (compound) | Retrieves unread notifications per user efficiently |
| `search_history` | `userId + createdAt` (compound) | Paginated retrieval of a user's recent searches |

---

## 4. REST API Design

All endpoints are served under `/api/v1`. Protected routes require a **JWT Bearer token** in the `Authorization` header. All responses use the envelope `{ success, data, message }`.

### Authentication

| Method | Endpoint | Auth | Description |
|---|---|---|---|
| `POST` | `/auth/register` | Public | Create a new account. Returns JWT. |
| `POST` | `/auth/login` | Public | Authenticate user. Returns JWT and profile. |
| `POST` | `/auth/logout` | JWT | Invalidate the current session. |
| `POST` | `/auth/forgot-password` | Public | Send a password reset link to the user's email. |
| `POST` | `/auth/reset-password` | Token | Set a new password using the emailed token. |
| `GET` | `/auth/me` | JWT | Return the currently authenticated user's profile. |

### Users

| Method | Endpoint | Auth | Description |
|---|---|---|---|
| `PUT` | `/users/profile` | JWT | Update name or vehicle details. |
| `GET` | `/users/favourites` | JWT | List saved favourite stations. |
| `POST` | `/users/favourites/:stationId` | JWT | Add a station to favourites. |
| `DELETE` | `/users/favourites/:stationId` | JWT | Remove a station from favourites. |
| `DELETE` | `/users/account` | JWT | Permanently delete the account. |

### Charging Stations

| Method | Endpoint | Auth | Description |
|---|---|---|---|
| `GET` | `/stations/nearby` | Public | Find stations within a radius. Accepts: `lat`, `lng`, `radius_km`, `connectorType`, `minSpeed_kW`, `availability`, `pricing`, `network`. |
| `GET` | `/stations/search` | Public | Address or text search via Mapbox Geocoding. |
| `GET` | `/stations/:id` | Public | Full station detail — connectors, pricing, hours, availability. |
| `POST` | `/stations` | Admin | Manually add a new station. |
| `PUT` | `/stations/:id` | Admin | Update station details or availability. |
| `DELETE` | `/stations/:id` | Admin | Remove a station record. |
| `POST` | `/stations/sync` | Admin | Trigger a manual sync with the Open Charge Map API. |

### Route Planning

| Method | Endpoint | Auth | Description |
|---|---|---|---|
| `POST` | `/routes/plan` | JWT | Plan a route. Returns suggested charging stops, distance, time, and cost. |
| `GET` | `/routes` | JWT | List all saved routes for the user. |
| `GET` | `/routes/:id` | JWT | Get a specific saved route with full waypoint details. |
| `DELETE` | `/routes/:id` | JWT | Delete a saved route. |

### Notifications

| Method | Endpoint | Auth | Description |
|---|---|---|---|
| `GET` | `/notifications` | JWT | Get all notifications. Supports `?unreadOnly=true`. |
| `PATCH` | `/notifications/:id/read` | JWT | Mark a notification as read. |
| `DELETE` | `/notifications/:id` | JWT | Delete a notification. |
| `POST` | `/notifications/subscribe/:stationId` | JWT | Subscribe to availability alerts for a station. |

---

## 5. Validation Rules

All inputs are validated at the Express middleware layer using `express-validator` before reaching any business logic. Failed validation returns a `400` with a descriptive message.

| Field | Rule | Error Returned |
|---|---|---|
| `email` | Must pass `isEmail()` format check. Checked for uniqueness on registration. | `"Please enter a valid email address"` |
| `password` | Minimum 8 characters. Must include at least one uppercase letter and one number. | `"Password must be at least 8 characters with one uppercase and one number"` |
| `lat` / `lng` | Valid floats within geographic bounds (`-90` to `90` / `-180` to `180`). | `"Invalid coordinates provided"` |
| `radius_km` | Integer between `1` and `50`. | `"Radius must be between 1 and 50 km"` |
| `connectorType` | One of: `Type 1`, `Type 2`, `CCS`, `CHAdeMO`, `Tesla`. | `"Invalid connector type specified"` |
| `minSpeed_kW` | Float between `1.4` and `350`. | `"Charging speed must be between 1.4 kW and 350 kW"` |
| `pricing` | One of: `free`, `per_kWh`, `session`. | `"Invalid pricing model"` |
| `stationName` | Required string, non-empty, max 100 characters. | `"Station name is required"` |
