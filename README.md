# Node.js + React Native Learning Roadmap

A structured 18-chapter journey to build full-stack mobile apps with Node.js backend and React Native frontend.

---

## Overview

| Phase | Chapters | Focus |
|-------|----------|-------|
| 1 | 1-5 | Foundations |
| 2 | 6-8 | API Development |
| 3 | 9-11 | Database & Auth |
| 4 | 12-14 | React Native Integration |
| 5 | 15-18 | Production Features |

**Prerequisites:**
- Basic JavaScript knowledge
- Basic React understanding (helpful for Phase 4)

---

## Phase 1: Foundations

### Chapter 1: How the Internet Works
**Topics:**
- Clients, servers, and the network
- HTTP methods (GET, POST, PUT, DELETE)
- URLs, IP addresses, DNS

**Exercise:** Draw a diagram showing how a browser request reaches a server. List all the steps from typing URL to receiving response.

---

### Chapter 2: JavaScript Async Patterns ★ (NEW)
**Topics:**
- Callback functions
- Promises (then/catch)
- async/await syntax
- Event loop basics
- Error handling in async code

**Exercise:** Take code using callbacks and convert it to use async/await. Practice with:
```javascript
// Convert this to async/await
function fetchData(callback) {
  setTimeout(() => callback(null, 'data'), 1000);
}
```

---

### Chapter 3: Node.js Basics
**Topics:**
- Node.js runtime & event loop
- npm & package management
- Module system (require/exports)
- File system operations (fs module)
- process & global objects

**Exercise:** Create a CLI calculator that takes two numbers and an operator as arguments:
```bash
node calc.js add 5 3  # Output: 8
node calc.js multiply 4 2  # Output: 8
```

---

### Chapter 4: Express.js Fundamentals
**Topics:**
- Setting up Express server
- Routes & middleware
- Request/Response objects
- Routing parameters
- Query strings

**Exercise:** Expand your `/api/health` route with:
- `GET /api/health/date` - returns current date
- `GET /api/health/time` - returns current time
- Create a middleware that logs request timestamps

---

### Chapter 5: Docker Fundamentals ★
**Topics:**
- Containers vs Virtual Machines
- Docker images & containers
- Dockerfile basics
- Docker Compose for multi-container setup
- volumes and networking

**Exercise:** 
1. Create a Dockerfile for your Express app
2. Create docker-compose.yml with:
   - Your Express app
   - PostgreSQL database
   - pgAdmin (optional)

---

## Phase 2: API Development

### Chapter 6: RESTful API Design + Postman
**Topics:**
- REST principles
- Resource-based routing
- HTTP status codes
- JSON responses
- Query params & body data
- Postman/Insomnia for testing

**Exercise:** Create `/api/users` route with full CRUD:
- `GET /api/users` - list all users
- `GET /api/users/:id` - get user by ID
- `POST /api/users` - create user (name, email)
- `PUT /api/users/:id` - update user
- `DELETE /api/users/:id` - delete user

Return proper status codes (200, 201, 404, etc.)

---

### Chapter 7: Data Validation & Error Handling
**Topics:**
- Input validation (Joi or express-validator)
- Schema validation
- Custom validation rules
- Global error handler
- Async error handling

**Exercise:**
- Add validation to `POST /api/users`:
  - name: required, min 2 chars
  - email: required, valid email format
- Create global error handling middleware
- Return structured error responses

---

### Chapter 8: Security Basics (CORS, Helmet) ★ (NEW)
**Topics:**
- CORS configuration
- Helmet.js for security headers
- Rate limiting
- Environment variables (.env)
- Security best practices

**Exercise:**
- Configure CORS for specific origins
- Add Helmet middleware
- Add rate limiting
- Use `.env` for all configuration

---

## Phase 3: Database & Auth

### Chapter 9: PostgreSQL + Prisma
**Topics:**
- PostgreSQL basics
- Prisma ORM introduction
- Schema modeling
- Migrations
- CRUD with Prisma Client

**Exercise:**
1. Set up PostgreSQL (local or cloud)
2. Install Prisma and initialize
3. Define User model in schema.prisma
4. Replace in-memory users array with Prisma queries

---

### Chapter 10: Authentication (JWT + bcrypt)
**Topics:**
- Password hashing (bcrypt)
- JWT fundamentals
- Token generation & verification
- Protected routes
- Token refresh strategies

**Exercise:** Add authentication to your API:
- `POST /api/auth/register` - hash password, save user
- `POST /api/auth/login` - verify password, return JWT
- `GET /api/users/profile` - protected route (require JWT)
- Implement JWT middleware for protected routes

---

### Chapter 11: Advanced Queries & Relations
**Topics:**
- One-to-many & many-to-many relations
- Prisma relations (relations, join tables)
- Aggregation & grouping
- Pagination & filtering
- Search functionality

**Exercise:**
1. Create `Post` model linked to User
2. Implement `/api/posts` CRUD
3. Add pagination: `?page=1&limit=10`
4. Add filtering: `?userId=1`

---

## Phase 4: React Native Integration

### Chapter 12: React Native Fundamentals ★ (NEW)
**Topics:**
- Expo vs React Native CLI
- Component structure
- Navigation (React Navigation)
- Styling basics
- State management (useState, useEffect)

**Exercise:**
1. Create a new Expo project
2. Build a simple screen with:
   - Text input
   - Button
   - Display area
3. Set up React Navigation with 2-3 screens

---

### Chapter 13: API Consumption from RN
**Topics:**
- Fetch API / Axios
- React Native networking
- Handling loading states
- Pull-to-refresh
- Error handling UI

**Exercise:**
1. Install Axios in your RN app
2. Create a service file for API calls
3. Fetch users from your `/api/users` endpoint
4. Display users in a FlatList with:
   - Loading indicator
   - Pull-to-refresh
   - Error message display

---

### Chapter 14: Auth State & Protected Screens
**Topics:**
- Context API for auth state
- AsyncStorage for token persistence
- Protected route navigation
- Auto-login on app restart
- Logout functionality

**Exercise:**
1. Create `AuthContext` for login/logout state
2. Store JWT in AsyncStorage
3. Create a Login screen
4. Implement protected routes:
   - Show Login if not authenticated
   - Show home screen if authenticated
5. Handle logout with state clear

---

## Phase 5: Production Features

### Chapter 15: File Uploads
**Topics:**
- Multer for file handling
- Image processing
- Storage solutions (local/Cloudinary/S3)
- File type validation
- Frontend file upload handling

**Exercise:**
- Add `POST /api/users/avatar` endpoint using Multer
- Accept image files only (jpg, png)
- Store in `/uploads` folder
- Return image URL in response
- Update RN app to select and upload image

---

### Chapter 16: Docker + Docker Compose ★
**Topics:**
- Multi-container Docker Compose
- Production Dockerfiles
- Environment variables in Docker
- Health checks
- Volume management

**Exercise:**
1. Create production Dockerfile (multi-stage build)
2. Update docker-compose.yml for production:
   - App container
   - PostgreSQL
   - Nginx (optional reverse proxy)
3. Add health checks to containers

---

### Chapter 17: Testing (Jest) ★ (NEW)
**Topics:**
- Unit testing fundamentals
- Jest setup
- Testing Express routes (supertest)
- Mocking
- Code coverage

**Exercise:**
1. Set up Jest in your project
2. Write unit tests for:
   - Validation functions
   - Helper utilities
3. Write integration tests for:
   - `GET /api/users`
   - `POST /api/users`
4. Achieve 70%+ code coverage

---

### Chapter 18: Deployment
**Topics:**
- Render / Railway / Koyeb / Vercel
- Environment configuration
- Database provisioning
- CI/CD basics
- Health check endpoints

**Exercise:**
1. Deploy your API to Render (free tier)
2. Configure environment variables
3. Connect PostgreSQL database
4. Deploy your React Native app (or connect to localhost)
5. Test all endpoints in production

---

## Progress Tracker

### Phase 1: Foundations
- [ ] Chapter 1: How the Internet Works
- [ ] Chapter 2: JavaScript Async Patterns ★
- [ ] Chapter 3: Node.js Basics
- [ ] Chapter 4: Express.js Fundamentals
- [ ] Chapter 5: Docker Fundamentals ★

### Phase 2: API Development
- [ ] Chapter 6: RESTful API Design + Postman
- [ ] Chapter 7: Data Validation & Error Handling
- [ ] Chapter 8: Security Basics (CORS, Helmet) ★

### Phase 3: Database & Auth
- [ ] Chapter 9: PostgreSQL + Prisma
- [ ] Chapter 10: Authentication (JWT + bcrypt)
- [ ] Chapter 11: Advanced Queries & Relations

### Phase 4: React Native Integration
- [ ] Chapter 12: React Native Fundamentals ★
- [ ] Chapter 13: API Consumption from RN
- [ ] Chapter 14: Auth State & Protected Screens

### Phase 5: Production Features
- [ ] Chapter 15: File Uploads
- [ ] Chapter 16: Docker + Docker Compose ★
- [ ] Chapter 17: Testing (Jest) ★
- [ ] Chapter 18: Deployment

---

## Quick Reference

### Recommended Tech Stack
| Layer | Technology |
|-------|------------|
| Backend | Node.js + Express |
| Database | PostgreSQL + Prisma |
| Auth | JWT + bcrypt |
| Docker | Docker + Docker Compose |
| Testing | Jest + Supertest |
| Frontend | React Native (Expo) |
| Deployment | Render / Railway |

### Project Structure
```
rn-backend-api/
├── src/
│   ├── controllers/
│   ├── routes/
│   ├── middleware/
│   ├── services/
│   ├── config/
│   └── app.js
├── prisma/
│   └── schema.prisma
├── tests/
├── Dockerfile
├── docker-compose.yml
└── package.json
```

---

## Tips for Success

1. **Practice daily** - Even 30 minutes helps
2. **Build something real** - Apply concepts to your actual project
3. **Test everything** - Use Postman to verify your API works
4. **Debug properly** - Learn to read error messages
5. **Don't skip Docker** - It will save you headaches later

---

*Last updated: April 2026*
