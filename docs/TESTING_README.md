# Testing Documentation for SaveAndSound Project

## Documents Overview

### 📋 TEST_PLAN.md
The test plan includes:
- Objectives and scope of testing
- Test strategy and approaches
- Test items and quality attributes
- Risk assessment and mitigation
- Test tools and methodologies

### 📊 TEST_RESULTS.md
Contains detailed results of executed test cases:
- Pass / Fail metrics
- Test execution per component
- Defect tracking and analysis
- Notes on performance, reliability, and security

### 📝 TESTING_SUMMARY.md
Provides a high-level overview:
- Key findings from functional and non-functional testing
- Identified defects
- Recommendations and conclusions

## Quick Start Guide

### Running Tests

**Start Backend Services**

```bash
cd SaveAndSound
./gradlew bootRun
```

## Quick Start

### Start Frontend

```bash
cd frontend
npm install
npm start
```

## Access Applications

- **Backend API**: http://localhost:8080
- **Frontend**: http://localhost:3000

## Test Environment Setup

- **Java**: 17+
- **Node.js**: 18+
- **PostgreSQL**: 15+
- **Gradle** for backend build
- **JUnit 5** for unit testing
- **Postman / REST Assured** for API testing

## Test Categories

### Functional Testing
✅ User Management (Registration, Login, Authentication)  
✅ Sound Management (CRUD for sounds, Upload, Edit, Delete)  
✅ Playlist Management (CRUD for playlists, Add/Remove sounds)  
✅ Favorites Management (Like sounds, Favorite playlist)  
✅ Artist View (View artist and their songs)  

### Integration Testing
✅ API Integration (Controllers ↔ Services ↔ Database)  
✅ Database Integrity  
✅ Authentication & Authorization Integration  

### Non-Functional Testing
✅ Performance Testing (API response < 1s)  
✅ Reliability & Fault Tolerance  
✅ Security Testing (Authentication & Authorization)  
✅ Usability Testing (User-friendly UI and messages)

# Test Case Example

| ID | Name | Scenario / Instructions | Expected Result | Actual Result | Pass/Fail |
|----|------|------------------------|-----------------|---------------|-----------|
| TC001 | Register New User | 1. Open registration form 2. Enter valid data 3. Submit | User successfully registered | User successfully registered | Pass |
| TC002 | Upload Sound | 1. Login as Creator 2. Upload sound file with details 3. Submit | Sound uploaded successfully | Sound uploaded | Pass |
| TC003 | Create Playlist | 1. Login as User 2. Create playlist with name and description 3. Submit | Playlist created | Playlist created | Pass |
| TC004 | Like Sound | 1. Login as User 2. View sound 3. Click like button | Sound liked, button changes to Unlike | Sound liked | Pass |
| TC005 | Invalid Registration (Empty Email) | 1. Open registration 2. Leave email empty 3. Submit | Error "Email is required" | Error displayed | Pass |

More detailed test cases can be found in TEST_RESULTS.md.

## Known Issues / Risks

- Race conditions when multiple users like the same sound
- Data loss during database connection failures
- Form validation errors (e.g., invalid sound file format)
- Data integrity violations when deleting linked entities (sounds in playlists)

## Test Metrics

| Metric | Value |
|--------|-------|
| Total Test Cases | 30+ |
| Passed | 28+ |
| Failed | 2 |
| Critical Issues | 0 |
| High Priority Issues | 1 |
| Medium Priority Issues | 1 |

## Next Steps

### Fix Identified Issues
- Resolve validation edge cases
- Address concurrent like issues

### Complete Remaining Tests
- End-to-end UI testing
- Full performance and security testing

### Update Documentation
- Add new test results
- Document testing methodology and environment

## Contact

For questions or issues regarding testing, contact the development team or your lab instructor.
