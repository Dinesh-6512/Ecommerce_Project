# Coding Standards & Structure

## Backend (FastAPI)
The backend is organized into simple, single-purpose files:
- `main.py`: Contains all API routes (endpoints).
- `models.py`: Defines the PostgreSQL database tables.
- `schemas.py`: Defines the data formats expected in requests and responses (Pydantic).
- `database.py`: Manages the database connection and sessions.
- `auth.py`: Handles password hashing, verification, and token generation.

## Frontend (ReactJS)
The frontend is built with React and Vite. It is organized as follows:
- `src/App.jsx`: Main routing configuration using `react-router-dom`.
- `src/index.css`: Global design system and premium CSS styles.
- `src/components/`: Reusable UI elements (Header, Footer, ProductCards).
- `src/pages/`: Full screen views (Login, Register, Profile, Home, Cart).

## General Rules
- Keep the implementation simple and easy to read.
- Do not over-engineer; build only what is required for the current task.
- Ensure API endpoints have clear names (e.g., `/api/register`).
- Return clear HTTP status codes (e.g., 200 for OK, 400 for Bad Request, 404 for Not Found).
