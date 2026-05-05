# Architecture Design Report

## 4.1 System Architecture Overview

The EV Charging Station Finder is built with the **MERN stack** (MongoDB, Express.js, React, Node.js).

The system uses a **layered architecture** which divides the system into distinct functional layers for improved organisation, scalability, and maintainability. This enables efficient processing of real-time data, user interactions, and API calls.

---

## 4.2 Architecture Layers

```
┌─────────────────────────────────────────────┐
│              Client Layer (Frontend)         │
│         React.js · Tailwind CSS · Mapbox     │
└───────────────────┬─────────────────────────┘
                    │ HTTP / REST
┌───────────────────▼─────────────────────────┐
│             API Gateway Layer                │
│          Express.js · JWT · CORS             │
└───────────────────┬─────────────────────────┘
                    │
┌───────────────────▼─────────────────────────┐
│           Service Layer (Business Logic)     │
│  Auth · Station Data · Routes · EV Range    │
└───────────────────┬─────────────────────────┘
                    │
┌───────────────────▼─────────────────────────┐
│               Data Layer                     │
│        MongoDB (Mongoose) · Redis Cache      │
└─────────────────────────────────────────────┘
```

### A) Client Layer (Frontend)

The GUI/Frontend is built with **React.js** and **Tailwind CSS**.

Responsibilities:
- Displaying the interactive map (Mapbox)
- Handling user actions (search, filters)
- Station detail view and navigation

### B) API Gateway Layer

Written in **Express.js**, this layer handles:
- Communication between frontend and backend
- Authentication using JWT
- Security: rate limiting and CORS

### C) Service Layer (Business Logic)

Implements core system functionality. Main services include:

| Service | Responsibility |
|---|---|
| Authentication Service | User login, signup, JWT management |
| Station Data Service | Fetching and processing station info |
| Route Planning Service | Calculating optimal charging routes |
| EV Range Calculation | Estimating vehicle range per charge |

### D) Data Layer

Uses **MongoDB** via Mongoose ODM, with **Redis** for caching.

Stores:
- User data
- Charging station data
- Routes and history

Caching with Redis minimises repeated API requests and speeds up response times.

---

## 4.3 External Integrations

| Service | Purpose |
|---|---|
| **Mapbox API** | Map rendering and navigation |
| **Open Charge Map API** | Charging station data |
| **Geolocation API** | User location detection |

These integrations enable real-time, up-to-date, and precise data across the application.

---

## 4.4 Data Flow Overview

```
User Action (search / filter)
        │
        ▼
  Frontend (React)
        │  HTTP Request
        ▼
  API Gateway (Express.js)
        │
        ▼
  Service Layer (Business Logic)
        │              │
        ▼              ▼
  MongoDB          External APIs
  (Mongoose)       (Mapbox / OCM)
        │
        ▼
  Response to Frontend
        │
        ▼
  Results displayed to User
```

---

## 4.5 Architecture Design Benefits

| Benefit | Detail |
|---|---|
| **Scalability** | Handles growing users and data volumes |
| **Flexibility** | Easy to extend or swap individual layers |
| **Performance** | Redis caching for fast responses |
| **Security** | Multiple protection layers (JWT, CORS, rate limiting) |
| **Maintainability** | Clear separation of concerns across layers |

---

## 4.6 Design Constraints

- Reliance on third-party APIs (Mapbox, Open Charge Map)
- Internet connectivity required at all times
- API rate limits on external services
- Limited free-tier cloud resources

---

## 4.7 Future Improvements

- **Microservices architecture** — decouple services for independent scaling
- **AI-based route optimisation** — smarter charging stop suggestions
- **Mobile app integration** — native iOS/Android support
- **Advanced caching strategies** — reduce latency further with edge caching
