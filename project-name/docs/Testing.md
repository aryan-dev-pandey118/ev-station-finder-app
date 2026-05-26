# Week 10 — Testing

## EV Charging Finder

### Expected Deliverable

Ensure system quality and verify that all system functions operate correctly through testing and validation.

---

## Activities

During Week 10, testing activities were performed to validate system functionality, integration, security, and user interface performance.

Testing activities included:

- Unit testing of frontend and backend modules
- Integration testing between React.js frontend and Express.js backend
- API testing using Postman
- Manual testing of user workflows
- UI testing for responsive design
- Authentication testing using JWT
- Testing Mapbox integration and route planner functionality
- Validation of Open Charge Map API responses
- Error handling and bug fixing
- User acceptance testing preparation

---

# 9.1 Requirement Validation

All functional and non-functional requirements were tested to ensure the EV Charging Finder system meets project objectives and user requirements.

### Functional Requirements Validated

- User registration and login functionality
- EV charging station search
- Mapbox map integration
- Route planning functionality
- Station details display
- Filter functionality
- API communication
- Authentication system

### Non-Functional Requirements Validated

- System responsiveness
- Performance and loading speed
- User interface usability
- Data security and authentication
- System reliability

---

# 9.2 Version Control and Iteration Evidence

GitHub was used throughout development for project management and tracking.

GitHub activities included:

- Commit history tracking
- Branch management
- Collaboration monitoring
- Sprint-based development

Version control helped maintain development history and supported teamwork during project implementation.

---

# 9.3 Testing Conducted

| Test Type | Status |
|-----------|---------|
| Unit Testing | Completed |
| Integration Testing | Completed |
| UI Testing | Completed |
| User Acceptance Testing | In Progress |

### Testing Tools Used

- Postman
- Browser Developer Tools
- MongoDB Compass
- Manual Testing

### Postman API Testing Conducted

API testing was performed using Postman to validate:

- User authentication endpoints
- Login and registration APIs
- Charging station retrieval APIs
- Map and route APIs
- Backend response validation
- Error handling responses

---

## Questions

### What are the most critical test cases?

**TC1 – User Login Validation**
- Verify users can register and log in successfully.
- Expected Result: User authentication completed and JWT token generated.

**TC2 – Charging Station Search**
- Verify users can search nearby charging stations.
- Expected Result: Charging stations displayed correctly.

**TC3 – Mapbox Integration**
- Verify stations appear on interactive map.
- Expected Result: Markers load correctly without errors.

**TC4 – Route Planner**
- Verify users receive route navigation to selected stations.
- Expected Result: Route displayed correctly.

**TC5 – Filter Function**
- Verify charger filtering by type, distance, and availability.
- Expected Result: Filtered results displayed accurately.

**TC6 – API Communication**
- Verify frontend communicates correctly with backend.
- Expected Result: Data retrieved successfully.

---

### What bugs exist?

| Issue | Solution |
|--------|----------|
| Map loading delay | Optimized API calls |
| Authentication errors | Added validation |
| UI responsiveness issues | Improved Tailwind CSS |

---

# 9.4 Bug Fixes and Improvements

Several improvements were made after testing:

- Reduced map loading delay by optimizing API requests
- Improved authentication validation using JWT middleware
- Enhanced UI responsiveness using Tailwind CSS
- Fixed frontend-backend integration issues
- Improved error handling for API failures

---

## Deliverable: Test Plan and Test Reports

The Week 10 deliverable includes:

- Requirement validation report
- Unit testing report
- Integration testing report
- UI testing report
- API testing evidence using Postman
- Bug tracking and fixes report
- GitHub iteration evidence
- User acceptance testing progress

This testing phase confirms that the EV Charging Finder MVP is stable and ready for final improvements and deployment.