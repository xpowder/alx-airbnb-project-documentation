# alx-airbnb-project-documentation

# Airbnb Clone – Backend Requirement Specifications

This document provides **technical and functional requirements** for key backend features of the Airbnb Clone system.  
It includes API endpoints, input/output specifications, validation rules, and performance criteria.

---

## 1. User Authentication

### Description
Handles user registration, login, and profile management for guests and hosts.

### API Endpoints
| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/users/register` | POST | Register a new user |
| `/api/users/login` | POST | Authenticate user credentials |
| `/api/users/profile` | GET/PUT | Retrieve or update user profile |

### Input/Output Specifications
- **Register/Login**
  - Input: `{ "username": string, "email": string, "password": string }`
  - Output: `{ "user_id": int, "token": string, "username": string, "email": string }`
- **Profile Update**
  - Input: `{ "username": string, "email": string, "password": string (optional) }`
  - Output: `{ "user_id": int, "username": string, "email": string }`

### Validation Rules
- Email must be valid format.  
- Password must be ≥ 8 characters, include letters and numbers.  
- Username must be unique and 3–30 characters.  

### Performance Criteria
- Registration/Login responses < 500ms under 100 concurrent users.  
- Token-based authentication using JWT with 1-hour expiry.

---

## 2. Property Management

### Description
Allows hosts to add, update, delete, and list property details.

### API Endpoints
| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/properties` | POST | Add a new property |
| `/api/properties/{id}` | GET | Retrieve property details |
| `/api/properties/{id}` | PUT | Update property information |
| `/api/properties/{id}` | DELETE | Remove property |

### Input/Output Specifications
- Input:  
```json
{
  "title": "Cozy Apartment",
  "description": "2-bedroom apartment in downtown",
  "location": "City Center",
  "price_per_night": 120,
  "availability": ["2025-09-01", "2025-09-15"]
}
