# 🐾 PawConnect: Pet Welfare and Care System

> *Because every pet deserves love and care.*

PawConnect is a full-stack web application that brings pet care, veterinary discovery, emergency help, animal rescue, lost-and-found, adoption, donations and volunteering into one platform. It serves pet owners, rescuers, vets, shelters, donors, volunteers and adopters.

**Course:** SEL-311 Software Construction, Lab Group Project
**Institution:** Bahria University, H11 Campus Islamabad, Department of Software Engineering
**Instructor:** Engr. Saad Mazhar Khan

---

## Table of Contents

1. [Problem Statement](#problem-statement)
2. [Features](#features)
3. [User Roles](#user-roles)
4. [Technology Stack](#technology-stack)
5. [System Design](#system-design)
6. [Project Structure](#project-structure)
7. [Getting Started](#getting-started)
8. [Database Setup](#database-setup)
9. [Testing](#testing)
10. [Git Workflow](#git-workflow)
11. [Project Status](#project-status)
12. [Team](#team)

---

## Problem Statement

Pet owners and animal welfare organisations face several everyday problems:

- Owners forget vaccinations, medicines, grooming and vet visits.
- Finding a suitable vet or an emergency clinic for a specific pet type is hard.
- Injured, abandoned or stray animals are not reported quickly or accurately to nearby rescuers.
- Lost pets are hard to reunite with owners because reports are scattered across social media and local groups.
- Adopters do not know which pet suits their home, lifestyle and available time.
- Rescue organisations depend on donations, foster homes and volunteers, but have no single place to ask for them.

PawConnect solves these problems with one integrated platform that applies real rules (status tracking, matching, scoring and role-based access), not just pages that display stored data.

## Features

### Open to everyone (no account needed)

- Browse adoptable pets and read full details for each one
- Read rescue cases and see how much has been raised
- Search for vets, then call them or get directions (emergency help never needs an account)
- View lost and found reports
- Read pet care guides and first-aid tips
- Donate as a guest (name and email only)
- See volunteer roles and what each one involves

### For registered users

- **Pet profiles and care planner:** multi-pet profiles, reminders for feeding, vaccination and medicine, overdue tracking and a wellness score
- **Rescue reporting:** report a stray or injured animal with photo, location and urgency, then track it through a status timeline (Reported → Rescuer Assigned → Transported → At Veterinary Clinic → Recovering → Ready for Adoption → Resolved)
- **Lost and found matching:** posts are compared by species, breed, colour, size, area, date and marks, with a possible-match percentage
- **Adoption and foster:** a preference form with a compatibility score for each pet
- **Donations:** campaign progress, remaining amount, donor count and simulated payments
- **Volunteering:** open requests, availability and contribution history
- **Admin tools:** verify vets and shelters, moderate reports and view analytics

## User Roles

| Role | What they can do |
|---|---|
| Guest | Browse, search and donate without an account |
| Pet owner | Manage pet profiles, care plans and emergency information |
| Adopter | Apply to adopt or foster and see compatibility scores |
| Rescuer / Volunteer | View rescue cases, update their status, offer help or foster care |
| Vet / Clinic | Manage the clinic profile, doctors and appointment requests (requires verification) |
| Shelter | Post adoption listings, campaigns and volunteer needs (requires verification) |
| Donor | Donate to campaigns and sponsor treatment |
| Administrator | Verify listings, moderate content and view statistics (created manually, never through sign-up) |

A user can hold more than one role. Roles are stored on the account and enforced by the server, never chosen at login.

## Technology Stack

| Layer | Technology |
|---|---|
| Frontend | React.js |
| Backend | Node.js with Express.js |
| Database | MongoDB with Mongoose |
| Authentication | JSON Web Tokens (JWT), bcrypt password hashing |
| Image upload | Cloudinary or Firebase Storage |
| Maps | Leaflet with OpenStreetMap |
| Testing | Jest and Supertest |
| Version control | Git and GitHub |

## System Design

The backend follows a layered architecture with one responsibility per layer:

```
Client (React)  →  Routes  →  Controllers  →  Services  →  Models  →  MongoDB
```

- **Models:** data and validation, with internal data hidden behind methods
- **Services:** business rules such as the compatibility score, match percentage and status transitions
- **Controllers:** handle requests and responses only
- **Middleware:** authentication, role checks and centralised error handling

**Object-oriented concepts used** (class and file names will be listed here as they are built):

| Concept | Where |
|---|---|
| Encapsulation | *to be added* |
| Inheritance and polymorphism | *to be added* |
| Collections and iteration | *to be added* |
| Error handling | *to be added* |

The full architecture diagram, class diagram and ER diagram are in the SDS inside the `docs/` folder.

## Project Structure

```
pawconnect-pet-welfare-system/
├── client/                 # React frontend
│   ├── public/
│   └── src/
│       ├── components/     # Reusable UI components
│       ├── pages/          # Home, Login, Sign up, dashboards ...
│       ├── services/       # API calls
│       └── context/        # Auth and app state
├── server/                 # Node.js + Express backend
│   ├── src/
│   │   ├── config/         # Database and environment setup
│   │   ├── models/         # Mongoose models
│   │   ├── services/       # Business logic
│   │   ├── controllers/    # Request handlers
│   │   ├── routes/         # API routes
│   │   ├── middleware/     # Auth, roles, error handling
│   │   └── utils/
│   ├── tests/              # Automated tests
│   └── seed/               # Sample data scripts
├── docs/                   # SRS, SDS, prototypes, report, screenshots
├── PROGRESS_LOG.md         # Weekly progress record
├── .gitignore
└── README.md
```

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) 18 or later
- [MongoDB](https://www.mongodb.com/try/download/community) running locally, or a free MongoDB Atlas cluster
- [Git](https://git-scm.com/)

### 1. Clone the repository

```bash
git clone https://github.com/aiman015/pawconnect-pet-welfare-system.git
cd pawconnect-pet-welfare-system
```

### 2. Set up the backend

```bash
cd server
npm install
cp .env.example .env
```

Open `.env` and fill in your own values. **Never commit this file.**

```env
PORT=5000
MONGO_URI=mongodb://localhost:27017/pawconnect
JWT_SECRET=replace_with_a_long_random_string
JWT_EXPIRES_IN=7d
CLIENT_URL=http://localhost:5173
```

Start the server:

```bash
npm run dev
```

The API runs at `http://localhost:5000`.

### 3. Set up the frontend

Open a second terminal:

```bash
cd client
npm install
npm run dev
```

The app opens at `http://localhost:5173`.

## Database Setup

1. Make sure MongoDB is running, or put your Atlas connection string in `MONGO_URI`.
2. The database and collections are created automatically on first run.
3. Load sample data (pets, rescue cases, clinics, campaigns and test users):

```bash
cd server
npm run seed
```

The seed script creates test accounts for each role. The credentials are listed in `server/seed/README.md` and are for development only.

## Testing

```bash
cd server
npm test
```

The test table (input, expected, actual) and the bug log are in `docs/`.

## Git Workflow

- `main` always contains working code.
- Every feature is built on its own branch, for example `feature/rescue-status-tracker`.
- Branches are merged through a **pull request reviewed by another team member**.
- Commit messages describe what changed, for example `Add status transition validation for rescue cases`.
- Progress is recorded weekly in [`PROGRESS_LOG.md`](PROGRESS_LOG.md).
- The final submitted version is tagged `v1.0`.

## Project Status

🚧 In development.

## Team

| Name | Enrollment |
|---|---|
| Aiman Farooq | 09-131242-015 |
| Arhama Tariq | 09-131242-019 |
| Rohab Israr | 09-131242-077 |

---

*Developed as the SEL-311 Software Construction Lab Group Project at Bahria University, Islamabad.*
