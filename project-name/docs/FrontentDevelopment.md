# 6.3 Frontend Development

The frontend of the EV Charging Finder system was developed using **React.js** and **Tailwind CSS**. React.js was selected because it supports component-based development, which makes the code reusable, organized, and easier to maintain. It also uses a Virtual DOM, which improves performance by updating only the required parts of the user interface.

Tailwind CSS was used to create a clean, responsive, and modern interface. It helped the team design pages quickly and maintain a consistent layout across different screen sizes.

## Frontend Features

The main frontend features include:

- **Interactive Map:** Displays EV charging stations using **Mapbox**.
- **Login Page:** Allows users to securely access the system.
- **Route Planner:** Helps users plan routes to selected charging stations.
- **Responsive Design:** Supports desktop, tablet, and mobile devices.

---

# 6.4 API Gateway Layer

The backend API layer was developed using **Express.js**. This layer connects the frontend interface with the backend services and external APIs. It handles user requests, authentication, security, and data communication.

The API gateway layer includes:

- **JWT Authentication Middleware:** Provides secure login and protects private routes.
- **CORS and Helmet Security:** Protects the system from common web security risks.
- **REST API Endpoints:** Allows communication between frontend and backend.
- **Socket.IO Communication:** Supports real-time updates such as charger availability.

---

# 6.5 External APIs

The EV Charging Finder system uses external APIs to provide map and charging station information.

## Open Charge Map API

The **Open Charge Map API** is used to collect information about EV charging stations, including location, charger type, and station details.

## Mapbox API

The **Mapbox API** is used to display interactive maps, show station markers, and support route planning features. It helps users view charging locations clearly and navigate to their selected charging station.

---

# Visual Representation

The system architecture can be shown using an architecture diagram.

**Architecture Flow:**

```text
User Interface
      ↓
React.js Frontend
      ↓
Express.js API Gateway
      ↓
Database / External APIs
      ↓
Mapbox API + Open Charge Map API