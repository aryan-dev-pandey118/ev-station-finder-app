# Project Description
## Business Description
Although there have been significant developments in the market for electric vehicles (EVs) in Australia, there is still a problem for users in finding charging stations that can be used to recharge their EVs. The apps on the market do not feature up-to-date information or have advanced filtering capabilities or easy navigation. This study is aimed at developing a platform to fill in these gaps in collaboration with the industry partner, Skill Up Labs (Kchaou et al., 2024, p. 2).
## Problem Statement and Objectives
EV users face range anxiety because of partial station information, insufficient search and filter features, and lack of good routing that considers charging stops. The project goals are as follows: (1) design a responsive web app that shows locations of EV charging stations on a map, (2) incorporate real-time data from Open Charge Map API, (3) allow filtering based on connector type, speed, availability, and pricing; (4) offer routing and multi-stop charging route planning; and (5) create a secure MVP in 12 weeks
## Scope
The system allows users to find EV charging stations, provide them with details, filter, and use a map interface to navigate. It can work via the web browsers and depends on external APIs and GPS services to obtain data. The system is not in control of physical charging infrastructure.
## Definitions, Acronyms, and Abbreviations
### Glossary of Terms

| Term  | Definition                          |
| ----- | ----------------------------------- |
| SRS   | Software Requirements Specification |
| API   | Application Programming Interface   |
| GPS   | Global Positioning System           |
| UI/UX | User Interface / User Experience    |
| FR    | Functional Requirement              |
| NFR   | Non-Functional Requirement          |
| OCM   | Open Charge Map                     |
| OSM   | OpenStreetMap                       |


 
 
## Methodology
The current project uses the Scrum methodology, which comprises of six two-week sprints. Scrum was selected for this project due to its iterative approach, provision for feedback, and adaptability.
## Business Requirement
| ID | Requirement                                                                      | Priority |
| -- | -------------------------------------------------------------------------------- | -------- |
| 1  | Provide accurate, real-time charging station information to reduce range anxiety | High     |
| 2  | Enable users to locate a compatible station within 60 seconds                    | High     |
| 3  | Support multiple EV connector types and charging speeds                          | High     |
| 4  | Provide seamless experience across mobile, tablet, and desktop                   | Medium   |
| 5  | Protect user data in compliance with the Australian Privacy Act 1988             | High     |


 

# Team Structure and Work Distribution
The team consist of the five members with clear assigned role. Workload is distributed to ensure each member contribute 20% each.
 
| Member            | Role            | Responsibilities                                                       | Contribution |
| ----------------- | --------------- | ---------------------------------------------------------------------- | ------------ |
| Bikram Gaire      | Project Manager | Project coordination, architecture, sprint management                  | 20%          |
| Aryan Dev Pandey  | Backend         | MongoDB schema, ERD/class diagrams, encryption, API endpoints          | 20%          |
| Saad Aryan        | Frontend        | React UI, Mapbox integration, responsive design, cross-browser testing | 20%          |
| Paban Paudel      | DevOps Engineer | Wireframes, storyboards, test plan, UAT execution                      | 20%          |
| Kamrul Hasan Jiha | QA Engineer     | Requirements, SRS documentation, DFDs, risk analysis, DPIA             | 20%          |


3. Functional Requirements 
## User Registration and Authentication
| ID    | Requirement                                                           | Priority |
| ----- | --------------------------------------------------------------------- | -------- |
| FR-01 | Allow users to register using email and password.                     | High     |
| FR-02 | Allow users to sign in and maintain authenticated sessions.           | High     |
| FR-03 | Allow users to update their profile, including vehicle details.       | High     |
| FR-04 | Support optional multi-factor authentication (MFA) for user accounts. | High     |
| FR-05 | Allow users to reset their password via email verification.           | High     |


 
## Station Discovery and Map
 
| ID    | Requirement                                                                            | Priority |
| ----- | -------------------------------------------------------------------------------------- | -------- |
| FR-06 | Display nearby charging stations on the map.                                           | High     |
| FR-07 | Show real-time availability updates (within 60 seconds).                               | Medium   |
| FR-08 | Search for stations by address or location.                                            | High     |
| FR-09 | Display station indicators (green = available, red = full, grey = offline) on the map. | Medium   |
| FR-10 | Display a detailed station page including connectors, pricing, and operating hours.    | Medium   |

## Filtering and Search
| ID    | Requirement                                                                                              | Priority |
| ----- | -------------------------------------------------------------------------------------------------------- | -------- |
| FR-01 | System shall allow users to register using a unique email and password with validation rules applied.    | High     |
| FR-02 | System shall authenticate users via email/password and maintain a secure session using token-based auth. | High     |
| FR-03 | System shall allow users to update their profile, including vehicle type, connector type, and model.     | High     |
| FR-04 | System shall support optional multi-factor authentication (MFA) via email or authenticator app.          | High     |
| FR-05 | System shall allow users to reset their password via a secure email verification link with expiry.       | High     |

 
## Notifications
| ID    | Requirement                                                                                       | Priority |
| ----- | ------------------------------------------------------------------------------------------------- | -------- |
| FR-19 | System shall notify users when a previously unavailable charging station becomes available.       | Medium   |
| FR-20 | System shall send alerts to users upon completion of a charging session.                          | Low      |
| FR-21 | System shall allow users to configure and control their notification preferences in app settings. | Low      |


 
# Non-Functional Requirements
 
| ID     | Category    | Requirement                                                                                         | Priority |
| ------ | ----------- | --------------------------------------------------------------------------------------------------- | -------- |
| NFR-01 | Performance | System shall load station data and map tiles within 3 seconds on a 4G network.                      | High     |
| NFR-02 | Performance | System shall support up to 1,000 concurrent users and scale horizontally.                           | High     |
| NFR-03 | Performance | System shall maintain API response times under 1 second under normal load conditions.               | High     |
| NFR-04 | Reliability | System shall handle API errors gracefully and return informative error messages.                    | High     |
| NFR-05 | Reliability | System shall perform automated database backups at least every 6 hours.                             | Medium   |
| NFR-06 | Security    | System shall encrypt all data in transit using HTTPS (TLS 1.2 or higher).                           | High     |
| NFR-07 | Security    | System shall hash user passwords using bcrypt with a minimum cost factor of 8.                      | High     |
| NFR-08 | Security    | System shall store API keys securely in environment variables and never expose them in client code. | High     |
| NFR-09 | Security    | System shall limit each IP to a maximum of 100 requests per 15 minutes.                             | Medium   |
| NFR-10 | Usability   | System shall provide a fully responsive UI for screen widths from 320px to 2560px.                  | High     |
| NFR-11 | Usability   | System shall comply with WCAG 2.1 Level AA accessibility standards.                                 | High     |
| NFR-12 | Usability   | System shall enable users to locate a desired station within 60 seconds without external guidance.  | Medium   |
| NFR-13 | Scalability | System shall use a stateless backend architecture to support horizontal scaling.                    | Low      |


 
# Hardware and Software configuration
| Component       | Specification                                                                                |
| --------------- | -------------------------------------------------------------------------------------------- |
| Server Hardware | Cloud VM (2 vCPUs, 4 GB RAM) or local development machine (Intel i5 or equivalent, 8 GB RAM) |
| Client Hardware | Desktop/laptop (minimum 1024×768 resolution), mobile/tablet (iOS 14+ / Android 10+) with GPS |
| Server OS       | Ubuntu 22.04 LTS, Node.js v18+, MongoDB v6.0+, Redis v7.0+                                   |
| Frontend Stack  | React.js 18+, React Router v6, Tailwind CSS 3.3+, Mapbox GL JS 2.15+                         |


6. Use Case Diagram
The use case diagram (Figure 1) illustrates three actors: Guest Users (view map, search stations, view details); Registered EV Drivers (additionally: login, save favorites, plan routes, manage notifications); and Administrators (manage users, moderate stations, view analytics). The diagram uses <<include>> for mandatory processes (e.g., authentication) and <<extend>> for optional behaviors (e.g., add to favorites).
                                      
## Search for Station
| Element    | Description                                                                                                                                                                                                                  |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Actors     | Guest User, Registered EV Driver                                                                                                                                                                                             |
| Conditions | Active internet connection; location permissions granted for GPS-based search                                                                                                                                                |
| Flow       | 1. User views the map → 2. User enters a location or taps the GPS button → 3. System queries the Open Charge Map API → 4. System displays stations as color-coded markers → 5. User selects a marker to view station details |
| Result     | Relevant charging stations are displayed on the map with availability indicators                                                                                                                                             |


 
## Plan Route Charging Stop
| Element        | Description                                                                                                                                                                                                                            |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Actors         | Registered EV Driver                                                                                                                                                                                                                   |
| Conditions     | User is logged in; vehicle details (e.g., range, connector type) are saved in the profile                                                                                                                                              |
| Main Flow      | 1. User enters destination → 2. System calculates route via Mapbox → 3. System suggests charging stops based on vehicle range → 4. User selects preferred stops → 5. System displays total distance, estimated time, and charging cost |
| Alternate Flow | 3a. If no stations are available along the route, system suggests nearby alternative stations → 5a. User can remove or swap suggested charging stops                                                                                   |
| Result         | Optimized route with charging stops is displayed, including navigation directions and station details                                                                                                                                  |


# Database Design
Why MongoDB?
Excellent support for GeoJSON location queries (important for "find nearby stations") also flexible document structure for arrays (e.g., connectors, favorites) and works well with the MERN stack. MongoDB (NoSQL database) and Mongoose ODM were chosen since the EV Charging Station Finder performs geospatial queries (locating charging stations nearby) very well and provides flexible schemas to enhance it in the future.
 
## Data Collection
### User Collection

| Field        | Type            | Constraints                           | Description                                     |
| ------------ | --------------- | ------------------------------------- | ----------------------------------------------- |
| _id          | ObjectId        | Auto-generated                        | Primary key                                     |
| email        | String          | Required, Unique, Indexed             | Login email (validated format)                  |
| passwordHash | String          | Required                              | Bcrypt hash (cost factor 10)                    |
| role         | String          | Default: 'user', Enum: 'user','admin' | User role                                       |
| vehicle      | Object          | Optional                              | { make, model, batteryCapacity, connectorType } |
| favorites    | Array[ObjectId] | Default: []                           | References ChargingStation documents            |

---

### ChargingStation Collection

| Field       | Type            | Constraints              | Description                                |
| ----------- | --------------- | ------------------------ | ------------------------------------------ |
| _id         | ObjectId        | Auto-generated           | Primary key                                |
| stationName | String          | Required                 | Display name                               |
| location    | GeoJSON Point   | Required, 2dsphere index | { type: 'Point', coordinates: [lng, lat] } |
| connectors  | Array of Object | Required, min: 1         | { type, power_kW, status }                 |
| pricing     | Object          | Optional                 | { model, rate_per_kWh, sessionFee }        |
| isAvailable | Boolean         | Default: true            | Station availability flag                  |


 
Additional collections include Routes (planned trips with waypoints, distance, duration, cost, accessibility), Vehicles (linked to users for range calculations), Notifications (alerts with read status), and SearchHistory (recent queries with coordinates).
## Entity Relation Diagram
The ER diagram demonstrates the key data structures of the EV Charging Station Finder system, such as Users, Charging Stations, Routes, and other data. It demonstrates the way users add favorites, route planning and communication with the charging stations. The design facilitates effective storage of data and system operations.



## Class Diagram
The Class Diagram illustrate main data entities (classes) and their relationships:
• A User can have many Favorites (ChargingStations) and plans many Routes
• A Route uses one Vehicle and stops at multiple ChargingStations
• ChargingStation includes methods like findNearby () to support map-based searches
 

 

 
 
 
## Data Flow Diagram
The Level 0 DFD (Figure 4) models the system as a single process interacting with EV Users, Admins, External APIs (Mapbox/Open Charge Map), and Notification Services. The Level 1 DFD (Figure 5) decomposes this into six processes: User Authentication, Station Discovery, Search and Filtering, Route Planning, Notifications, and Admin Management.
 


 
## Data Encryption and Anonymization
Encryption at rest is provided by MongoDB Atlas using AES-256. All client-server and API communications use HTTPS (TLS 1.2+). Passwords are hashed with crypt (cost factor 10), and JWT tokens are signed with HMAC-SHA256 (Rana et al., 2023, p. 4412).

 
# System Architecture
The EV Charging Station Finder application employs a contemporary MERN stack architecture with clear topic division.


## Architecture Layers
### Client Layer (Frontend)

Built using React.js and Tailwind CSS.

Responsible for:

* Interactive Map (Mapbox GL JS)
* User dashboard and profile management
* Search and filtering interface
* Notification UI (in-app alerts)

---

### API Gateway Layer

Implemented using Express.js.

Responsible for:

* JWT-based authentication middleware
* Rate limiting for API protection
* Security middleware (CORS, Helmet)
* REST API endpoints
* Real-time communication via Socket.IO

---

### Service Layer (Business Logic)

Contains core application logic separated into modular services:

* **Auth Service**: JWT generation/validation, bcrypt password hashing, role-based access control
* **Route Service**: Integration with Mapbox Directions API and charging stop optimization logic
* **EV Range Service**: Battery consumption estimation, travel time calculation, and cost estimation

---

### Data Layer

* MongoDB (with Mongoose ODM): Stores Users, Charging Stations, Routes, Vehicles, Favorites, Notifications
* Redis: Used for session caching, API response caching, and rate-limit optimization

---

### External APIs & Integrations

* Open Charge Map API: Charging station data source
* Mapbox API: Map rendering, geocoding, and routing
* Nodemailer + Socket.IO: Email notifications and real-time user alerts

 
# User Interface Design
## Story Board
### Application Screens

| Screen             | Description                                                                                                                                                                                               |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Landing / Map View | Full-screen interactive map centered on user location. Includes search bar (top), color-coded charging station markers, and bottom navigation (Map, Search, Favorites, Profile).                          |
| Search Results     | Map zooms to selected location. Displays station markers with summary cards (name, distance, availability status). Supports toggle between map and list view.                                             |
| Route Planner      | Allows destination input and displays suggested charging stops based on vehicle range. Users can add/remove/swap stops. Shows route summary including distance, time, charging stops, and estimated cost. |
| User Profile       | Allows users to update personal details, vehicle information, notification settings, favourites, password, MFA settings, and account deletion.                                                            |
| Admin Dashboard    | Contains tabs for User Management, Station Management, and System Analytics (usage statistics, popular stations, search trends).                                                                          |


 
## Input Data Forms
### Registration Form

| Fields                                                                   | Validation                                                                                                      |
| ------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------- |
| First Name, Last Name, Email, Password, Confirm Password, Terms Checkbox | Real-time client + server validation; email must be unique; password minimum 8 characters with complexity rules |

---

### Login Form

| Fields                       | Validation                                                     |
| ---------------------------- | -------------------------------------------------------------- |
| Email, Password, Remember Me | Account lockout after 5 failed attempts; MFA prompt if enabled |

---

### Vehicle Profile Form

| Fields                                                                          | Validation                                                    |
| ------------------------------------------------------------------------------- | ------------------------------------------------------------- |
| Make (dropdown), Model, Year, Battery kWh, Compatible Connectors (multi-select) | Optional fields; used for range estimation and route planning |

---

### Search Function

| Fields                                                           | Validation                                                      |
| ---------------------------------------------------------------- | --------------------------------------------------------------- |
| Location (text with autocomplete / GPS), Radius (1–50 km slider) | Mapbox Geocoding autocomplete; GPS requires location permission |

---

### Filter System

| Fields                                                                             | Validation                                       |
| ---------------------------------------------------------------------------------- | ------------------------------------------------ |
| Connector types, Minimum charging speed, Availability toggle, Price model, Network | Dynamic filtering with session state persistence |

---

### Route Planner

| Fields                                                                | Validation                                          |
| --------------------------------------------------------------------- | --------------------------------------------------- |
| Origin (text/GPS), Destination, Vehicle selection, Preferred Networks | Addresses must be geocoded before route calculation |

---

### Station Summary Card

| Fields                                                          | Validation                          |
| --------------------------------------------------------------- | ----------------------------------- |
| Name, Distance, Availability, Connector icons, Pricing, Actions | Color-coded availability indicators |

---

### Station Detail Page

| Fields                                                                       | Validation                                          |
| ---------------------------------------------------------------------------- | --------------------------------------------------- |
| Full address, Map pin, Connector list, Pricing table, Hours, Ratings, Photos | Data loaded from station API with fallback handling |

---

### Route Summary

| Fields                                                                             | Validation                               |
| ---------------------------------------------------------------------------------- | ---------------------------------------- |
| Route map, Waypoints, Distance, Travel time, Charging time, Total cost, Directions | Calculated using Mapbox + EV range logic |

---

### Admin Analytics Dashboard

| Fields                                                                               | Validation                                 |
| ------------------------------------------------------------------------------------ | ------------------------------------------ |
| User count, Active users (line chart), Popular stations (bar chart), Search heat map | Aggregated from backend analytics pipeline |

## Output Form
### Station Summary Card

* Name of station
* Distance from user location
* Availability status (color-coded indicator)
* Connector type icons
* Pricing summary
* Action buttons (View Details / Navigate / Save)

---

### Station Detail Page

* Full station address
* Map pin location
* Connector list with individual availability status
* Detailed pricing table
* Operating hours
* User ratings and reviews
* Photo gallery of station

---

### Route Summary

* Route displayed on interactive map
* List of waypoints (including charging stops)
* Total distance
* Estimated travel time
* Estimated charging time per stop
* Total trip cost estimation
* Turn-by-turn navigation directions

---

### Admin Analytics Dashboard

* Total registered users count
* Daily active users (line chart visualization)
* Most popular charging stations (bar chart)
* Search activity heat map


 
# Test Plan
The testing approach, test cases, and acceptance criteria for the EV Charging Station Finder are described in this section. All functional and non-functional criteria are confirmed and validated prior to deployment thanks to the test strategy.

10.1 Testing Strategy
The project uses a multi-level, structured testing method to ensure that the system functions as intended and fulfils user requirements. There are four main categories of testing in it. The fully built application is subjected to system testing to make sure all parts work together seamlessly and that user tasks, including finding and displaying charging station information, are completed without any problems. In User Acceptance Testing (UAT), actual or representative users test the system to make sure it satisfies business needs and is useful and simple to use in real-world scenarios.

## Test Cases
### Test Cases

| ID    | Test Case                         | Req    | Input / Action                                                       | Expected Result                                                           | Level              |
| ----- | --------------------------------- | ------ | -------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------ |
| TC-01 | User Registration                 | FR-01  | Submit valid registration form with name, email, and strong password | Account created successfully, confirmation message displayed, JWT issued  | Unit / Integration |
| TC-02 | User Registration - Invalid Email | FR-01  | Submit registration form with invalid email format                   | Validation error: "Please enter a valid email address"                    | Unit               |
| TC-03 | User Login                        | FR-02  | Submit login form with valid credentials                             | User authenticated, redirected to map view, JWT stored in session         | Integration        |
| TC-04 | User Login - Wrong Password       | FR-02  | Submit login form with correct email but wrong password              | Error message displayed; login attempt counter incremented                | Unit               |
| TC-05 | Map Display                       | FR-06  | Open application with GPS enabled                                    | Map loads within 3 seconds, centered on user location, stations displayed | System             |
| TC-06 | Station Search                    | FR-08  | Search "Sydney CBD"                                                  | Map pans to location, relevant stations displayed                         | Integration        |
| TC-07 | Filter by Connector Type          | FR-10  | Select Type 2 and CCS filters                                        | Only matching stations displayed                                          | Integration        |
| TC-08 | Station Details                   | FR-09  | Click station marker                                                 | Station details shown (name, address, connectors, pricing, hours)         | System             |
| TC-09 | Favourite Station                 | FR-16  | Click "Add to Favourites"                                            | Station added to favourites, UI updated, confirmation shown               | Integration        |
| TC-10 | Password Reset                    | FR-05  | Request reset using registered email                                 | Reset email sent with time-limited secure link                            | Integration        |
| TC-11 | Performance - Page Load           | NFR-01 | Load map page on 4G connection                                       | Page interactive within 3 seconds                                         | System             |
| TC-12 | Security - HTTPS                  | NFR-06 | Access via HTTP                                                      | Redirect to HTTPS, no insecure data transmission                          | System             |
| TC-13 | Responsive Design                 | NFR-11 | Test on 320px, 768px, 1024px, 1920px                                 | UI adapts correctly with no layout break                                  | System / UAT       |



 

 

 

 
​​​​​
# Project Constraints
The most important limitations for this project are: a 12-week development phase, which was set based on the goals of the WIL program; the need to use third-party API services like Mapbox and Open Charge Map, which could have rate limits and downtime issues; the cloud service, MongoDB Atlas M0, which limits how much data can be included in the application; the inability to use anything other than the MERN stack of technologies; and the fact that the application cannot work without an Internet connection.

# Future Enhancements
Future improvements include:
• AI route optimization
• Payment integration
• Mobile apps
• Admin analytics
• Charging reservations
# Project Milestones
### Project Milestones and Timeline

| Milestone              | Target Week | Deliverables                                                |
| ---------------------- | ----------- | ----------------------------------------------------------- |
| Requirements Complete  | Week 2      | Requirements document, team charter, project plan           |
| SRS Submitted          | Week 3      | Final Software Requirements Specification (SRS) report      |
| Architecture Finalized | Week 4      | System architecture diagrams, development environment setup |
| Backend MVP            | Week 6      | MongoDB schema, core APIs, authentication system            |
| Frontend Complete      | Week 9      | React UI, Mapbox integration, search and filter features    |
| Integration & Testing  | Week 11     | Full system integration, test execution, bug fixes          |
| Final Delivery         | Week 12     | Deployed application, documentation, and presentation       |

 
# Project Budget
### Estimated Budget Allocation (EV Charging Station Finder Project)

| Budget Item                                | Estimated Cost (AUD) |
| ------------------------------------------ | -------------------- |
| Research and Planning                      | $130                 |
| SRS Documentation and Design               | $90                  |
| UI/UX Design                               | $220                 |
| Database Design and Setup                  | $200                 |
| Backend Development                        | $380                 |
| Frontend Development                       | $380                 |
| API Integration (Mapbox / Open Charge Map) | $50                  |
| Testing and Debugging                      | $200                 |
| Hosting, Deployment, Tools                 | $220                 |
| Final Documentation and Presentation       | $80                  |
| Contingency Reserve                        | $120                 |
| **Total Estimated Budget**                 | **$2070**            |

# Risk Analysis
### Risk Management Table

| Risk                          | Impact | Likelihood | Mitigation Strategy                                                                             |
| ----------------------------- | ------ | ---------- | ----------------------------------------------------------------------------------------------- |
| API downtime or rate limiting | High   | Medium     | Implement Redis caching, fallback cached station data, and API usage monitoring with alerts     |
| Scope creep                   | Medium | High       | Use Agile sprints with strict MoSCoW prioritisation and Product Owner approval for changes      |
| Team member unavailability    | Medium | Medium     | Cross-training, shared Git repository, and proper documentation of all modules                  |
| Inaccurate station data       | Medium | Medium     | Validate using multiple data sources, enable user reporting, and schedule periodic data refresh |
| Security vulnerabilities      | High   | Low        | Apply input sanitisation, HTTPS enforcement, Helmet.js middleware, and regular npm audit checks |
| Timeline insufficiency        | Medium | High       | Prioritise MVP features first and defer non-essential features to later phases                  |

# Conclusion
The EV Charging Station Finder is a user-friendly and scalable web application to ease the task of searching and finding their way to electric vehicle charging stations. Real-time APIs, geolocation, and an interactive map interface will enable the system to efficiently discover stations, filter, and plan routes. On balance, the system offers a solid ground to increase the accessibility of EVs and facilitates the shift to the more efficient and sustainable transportation.
