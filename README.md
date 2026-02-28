# News Portal

A full-stack news portal application built with React and Node.js that allows users to read, create, and manage news articles.

## Tech Stack

### Frontend
- **React 18** - UI library
- **Vite** - Build tool and dev server
- **React Router DOM** - Client-side routing
- **Axios** - HTTP client
- **JWT Decode** - Token handling

### Backend
- **Node.js** - Runtime environment
- **Express 5** - Web framework
- **Sequelize** - ORM for database operations
- **MySQL** - Database
- **JWT** - Authentication
- **bcryptjs** - Password hashing
- **express-validator** - Input validation

## Features

- User authentication (register/login)
- JWT-based authorization
- News article CRUD operations
- Role-based access control (admin, editor, reader)
- Protected routes for authenticated users
- Input validation and error handling

## Project Structure

```
NewsPortal-new/
├── backend/
│   ├── config/          # Database configuration
│   ├── controllers/     # Route controllers
│   ├── middleware/      # Auth and validation middleware
│   ├── migrations/      # Sequelize migrations
│   ├── models/          # Sequelize models (User, News)
│   ├── routes/          # API routes
│   ├── seeders/         # Demo data seeders
│   └── server.js        # Entry point
├── frontend/
│   ├── public/          # Static assets
│   └── src/
│       ├── components/  # Reusable components
│       ├── context/     # React context (Auth)
│       ├── pages/       # Page components
│       ├── services/    # API service layer
│       └── App.jsx      # Main app component
└── data/
    └── data.sql         # Database schema
```

## Prerequisites

- Node.js (v18 or higher)
- MySQL Server
- npm or yarn

## Installation

### 1. Clone the repository

```bash
git clone <repository-url>
cd NewsPortal-new
```

### 2. Set up the database

```bash
mysql -u root -p < data/data.sql
```

Or create the database manually:
```sql
CREATE DATABASE news_portal_db;
```

### 3. Configure environment variables

Create a `.env` file in the `backend` directory:

```env
PORT=5000
DB_HOST=127.0.0.1
DB_USER=root
DB_PASSWORD=your_password
DB_NAME=news_portal_db
DB_DIALECT=mysql
JWT_SECRET=your_jwt_secret_key
```

### 4. Install dependencies

**Backend:**
```bash
cd backend
npm install
```

**Frontend:**
```bash
cd frontend
npm install
```

### 5. Run database migrations and seeders (optional)

```bash
cd backend
npx sequelize-cli db:migrate
npx sequelize-cli db:seed:all
```

## Running the Application

### Development Mode

**Start the backend server:**
```bash
cd backend
npm run dev
```
The API will be available at `http://localhost:5000`

**Start the frontend development server:**
```bash
cd frontend
npm run dev
```
The app will be available at `http://localhost:5173`

### Production Mode

**Backend:**
```bash
cd backend
npm start
```

**Frontend:**
```bash
cd frontend
npm run build
npm run preview
```

## API Endpoints

### Authentication
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/auth/register` | Register a new user |
| POST | `/api/auth/login` | Login user |

### News
| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| GET | `/api/news` | Get all news articles | No |
| GET | `/api/news/:id` | Get a single article | No |
| POST | `/api/news` | Create a news article | Yes |
| PUT | `/api/news/:id` | Update a news article | Yes |
| DELETE | `/api/news/:id` | Delete a news article | Yes |

## Frontend Routes

| Path | Component | Description |
|------|-----------|-------------|
| `/` | Home | Display all news articles |
| `/news/:id` | NewsDetail | View single article |
| `/login` | Login | User login page |
| `/register` | Register | User registration page |
| `/dashboard` | Dashboard | User dashboard (protected) |

## License

ISC
