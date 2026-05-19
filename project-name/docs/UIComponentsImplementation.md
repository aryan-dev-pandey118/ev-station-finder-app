# EV Charging Station Finder
## UI Components Implemented

## UI Components Implemented

This section records the user interface features created on the front-end during Sprint 5. All components are designed in a responsive and component-based manner, built with React.js 18+, Tailwind CSS 3.3+ and Mapbox GL JS 2.15+.

## Components Overview

| Component               | Screen / Module      |     Status |
|-------------------------|----------------------|------------|
| Navbar                  |   All Pages          |Implemented |
| Login / Sign-Up Page    | Authentication       |Implemented |
| Interactive Map View    | Map Screen           |Implemented |
|Search Bar & Filter Panel| Map / Search Screen  |Implemented |
|Station Detail Car       | Station View         |Implemented |
| Route Planner Interface | Route Screen         |Implemented |
|Charging Cost Calculator |Route / Station Screen|Implemented |
| User Profile Page       | Profile Screen       |Implemented |
| Favorites Panel         |Profile / Navigation  |Implemented |
| Admin Dashboard         | Admin Panel          |Implemented |
| Notification Interface  | All Pages            |Implemented |
| Responsive Layout       | All Pages            |Implemented |


## Navigation Component (Navbar)

A top navigation bar which is used across all pages and can be reused. It offers links to Map, Search, Route Planner, Favourites and Profile. It displays a guest login/register option and a profile icon with a logout for users that are already logged in. Responsive menu that collapses to hamburger on mobile with Tailwind CSS responsive utilities.

## Authentication Screens
 Login and Registration screens are used for secure user access. Both implement client-side and server-side validation. 
	•	Login: Your email, your password, (show/hide toggle), Remember Me, prompt for MFA if enabled.
	•	 Registration: Name, Email, Password (complexity check), Terms (checkbox), MFA (opt-in) 
	•	The account is locked out after 5 unsuccessful login attempts.

## Interactive Map View
Main screen of the app, designed using Mapbox GL JS. Renders a full-screen map centred on the user's geolocation and displays real-time charging station data from the Open Charge Map API.
	•	 Colour-coded station markers, green (available), red (full), grey (offline) 
	•	Right-click to station popup: name, status, connector type, distance 
	•	The search bar features Mapbox Geocoding with an autocomplete popup, and a GPS re-centre button 
	•	Bottom navigation bar: Map, Search, Favorites, Profile

## Search Bar and Filter Panel
 Enables users to find suitable stations quickly. Filter state is saved in React state and applied dynamically without refreshing the page. 
	•	Location search with autocomplete and radius slider (1–50 km) 
	•	Filter by: Connector Type, Min Charging Speed (kW), Availability toggle, Network Provider, Price Model

## Station Detail Card
This will be visible when the user clicks on a station on the map or search results. Displays the station name, whether it is available, types of connectors, their power, pricing, and hours of operation, as well as a Get Directions button and an Add to favorites toggle button.

## Route Planner Interface
Allows for multi-stop route planning and EV charging stops. Uses the Mapbox Directions API and the backend EV Range Calculator Service. 
	•	Origin and destination inputs with autocomplete; add/remove/swap waypoints 
	•	Auto-suggested charging stops based on vehicle battery range 
	•	Route summary: distance, time, charging stops, estimated cost. 

## Charging Cost Calculator
Included in the Route Planner and Station Detail screens. The user sets the current battery level slider and the target battery level slider and the component calculates the estimated charging time and charging cost in real-time using the charging station's charging speed and the battery capacity of the vehicle.

## User Profile Page
Provides users with control over their account, vehicle information, and preferences. Contains editable Name/Email, Vehicle form (Make, Model, Battery kWh, Connector types), notification toggles, Change Password, MFA toggle, and Account Deletion with confirmation.

## Favorites Panel
 Shows saved charging stations along with their name, location and status. Each entry has a quick Get Directions button and a remove toggle. When there are no favorites saved, an empty-state illustration is displayed.

## Admin Dashboard
Only a user with the admin role can access this. Includes 3 tabs: User Management (search, sort, deactivate users), Station Management (Add Stations, Edit Stations, Remove Stations), and System Analytics (Usage Charts, Popular Stations, Search Trends).

## Notification Interface
Real-time notifications sent through Socket.IO. The unread count badge is indicated by a bell icon in the Navbar. The dropdown panel presents alerts (station available, session complete) with time stamps and Mark as Read / Clear All buttons. The preferences for notifications are controlled from the User Profile page.

## Responsive Design
All components are designed to work for screen sizes between 320px and 2560px (NFR-10) via Tailwind CSS breakpoint utilities. Works on Chrome, Firefox, Safari, Edge and iOS 14+, Android 10+.

| Breakpoint |     Width       |                    Layout                    |
|------------|-----------------|----------------------------------------------|
| Mobile     |320px - 767px    | Single-column; hamburger menu; full-width map|
| Tablet     |768px - 1023px   | Two column; expanded filter panel            |
| Desktop    |1024px+          | Full Navbar; split-view map and station list |


## Design Benefits
	•	Reusability — Common parts (Navbar, Station Card, Filter Panel) minimize code duplication
	•	 Performance — React Virtual DOM reduces re-renders, lazy loading for map, dashboard
	•	 Accessibility — WCAG 2.1 Level AA (using semantic HTML, ARIA labels and keyboard user navigation) 
	•	Maintainability — Separation of UI components and business logic is clear

## Design Constraints
	•	The map needs to be configured with a valid Mapbox API token and internet connection.
	•	To get real-time station data, Open Charge Map API rate limits are required. 
	•	The backend needs to have a persistent WebSocket connection to send Socket.IO notifications.
	•	 Free-tier cloud hosting has a limit on the number of WebSocket connections allowed per site.
## Future Improvements

	•	Switch to dark mode with the Tailwind CSS dark variant classes.
	•	 Progressive Web Apps (PWAs) Offline Map Caching Support 
	•	AI-powered station recommendation widget based on user charging history. 
	•	React Native mobile app development with common component logic.
