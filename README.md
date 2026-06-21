# Salon Booking Application — Frontend

This is the frontend for the **Salon Booking Application**, built with **React.js**. It provides the user interface for browsing salons, viewing services, booking appointments, making payments, and leaving reviews, communicating with the backend microservices through the API Gateway.

> Looking for the backend? See the [Backend README](./backend-README.md) (or the `backend/` directory).

## Table of Contents

- [Overview](#overview)
- [Tech Stack](#tech-stack)
- [Features](#features)
- [State Management](#state-management)
- [Getting Started](#getting-started)
- [Project Structure](#project-structure)
- [Future Improvements](#future-improvements)

## Overview

The frontend is a single-page React application that consumes REST APIs exposed via the backend's API Gateway. It covers the full user journey — browsing salons by category, viewing available services, booking appointments, making payments, and leaving reviews — with a UI built using Material UI and Tailwind CSS.

## Tech Stack

- **Framework:** React.js
- **Routing:** React Router DOM
- **State Management:** Redux (separate store/slice per backend microservice domain)
- **API Communication:** Axios
- **UI Libraries:** Material UI, Tailwind CSS
- **Image Uploads:** Cloudinary
- **Cross-Cutting:** CORS (secure communication with backend)

## Features

- Browse salons by category
- View salon-specific service offerings
- Book appointments for selected services
- Make secure payments via Razorpay / Stripe (handled through backend Payment Service)
- View booking status notifications
- Leave and view reviews for salon services
- Upload and manage images via Cloudinary (e.g., salon/service images)
- Authenticated user flows (login/signup) integrated with backend Keycloak authentication

## State Management

Redux is used to manage application state, with state organized per microservice domain to mirror the backend's structure:

```
redux/
├── store.js
├── booking/
│   ├── bookingSlice.js
│   └── bookingActions.js
├── salon/
├── category/
├── salonOffering/
├── review/
├── user/
└── payment/
```

This keeps state predictable and makes it easy to trace a piece of UI state back to the backend service that owns it.

## Getting Started

### Prerequisites
- Node.js (LTS recommended)
- npm or yarn
- Backend services running (see [Backend README](./backend-README.md))

### Setup & Run

```bash
# Clone the repository
git clone <repository-url>
cd salon-booking-application/frontend

# Install dependencies
npm install

# Start the development server
npm start
```

The app will run on `http://localhost:3000` by default (or as configured).

### Environment Variables

Create a `.env` file in the frontend root with variables such as:

```
REACT_APP_API_BASE_URL=http://localhost:8080
REACT_APP_CLOUDINARY_CLOUD_NAME=<your-cloudinary-cloud-name>
REACT_APP_CLOUDINARY_UPLOAD_PRESET=<your-upload-preset>
```

> Add a `.env.example` file listing required variables (without actual secrets) for easier onboarding.

## Project Structure

```
frontend/
├── public/
├── src/
│   ├── components/        # Reusable UI components
│   ├── pages/              # Page-level components (routes)
│   ├── redux/               # Redux store, slices, actions per domain
│   ├── services/             # Axios API service calls
│   ├── routes/                # React Router DOM route definitions
│   ├── App.js
│   └── index.js
├── package.json
└── tailwind.config.js
```

## Future Improvements

- Add unit/integration tests (e.g., Jest, React Testing Library)
- Add loading skeletons and improved error boundaries
- Implement code-splitting/lazy loading for better performance
- Add E2E tests (e.g., Cypress/Playwright)
- Improve accessibility (a11y) across components

## License

This project is for educational/portfolio purposes.
