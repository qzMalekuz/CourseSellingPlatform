# 🎓 CourseLelo.io

![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)
![Express](https://img.shields.io/badge/Express.js-000000?style=for-the-badge&logo=express&logoColor=white)
![Prisma](https://img.shields.io/badge/Prisma-3982CE?style=for-the-badge&logo=Prisma&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)
![Bun](https://img.shields.io/badge/Bun-000000?style=for-the-badge&logo=bun&logoColor=white)

A modern, robust backend for a complete course selling platform built with Express, Prisma, and PostgreSQL. 

**CourseLelo.io** features role-based access control, secure authentication, and a full suite of APIs for managing courses, lessons, and purchases.

---

## ⚡️ Tech Stack

- **Runtime**: [Bun](https://bun.sh/)
- **Framework**: [Express.js](https://expressjs.com/)
- **Language**: [TypeScript](https://www.typescriptlang.org/)
- **Database**: [PostgreSQL](https://www.postgresql.org/)
- **ORM**: [Prisma](https://www.prisma.io/)
- **Security**: JWT + bcrypt
- **Validation**: Zod

---

## 🚀 Getting Started

### Prerequisites

- [Bun](https://bun.sh/) runtime installed
- PostgreSQL database up and running

### Installation

1. **Install dependencies:**
   ```bash
   bun install
   ```

2. **Configure environment variables:**  
   Create a `.env` file in the root directory:
   ```env
   PORT=3000
   JWT_SECRET=your-super-secret-key
   SALT_ROUNDS=10
   DATABASE_URL=postgresql://user:password@localhost:5432/course_selling
   ```

3. **Run database migrations:**
   ```bash
   bun prisma migrate dev
   ```

4. **Start the server:**
   ```bash
   bun run dev
   # or
   bun run src/index.ts
   ```

---

## 📡 API Endpoints

### 🔐 Authentication (`/auth`)
- `POST /auth/signup` - Register a new user (Student or Instructor)
- `POST /auth/login` - Login and receive a JWT token

### 📚 Courses (`/courses`)
- `POST /courses` - Create a new course *(Instructor only)*
- `GET /courses` - Browse all available courses
- `GET /courses/:id` - Fetch details of a specific course *(Instructor only)*
- `PATCH /courses/:id` - Update course information *(Instructor only)*
- `DELETE /courses/:id` - Remove a course *(Instructor only)*

### 📖 Lessons (`/lessons`)
- `POST /lessons` - Add a lesson to a course *(Instructor only)*
- `GET /lessons` - Get all lessons for a course
- `PATCH /lessons/:id` - Update a lesson *(Instructor only)*
- `DELETE /lessons/:id` - Remove a lesson *(Instructor only)*

### 🛒 Purchases (`/purchases`)
- `POST /purchases` - Enroll in / purchase a course *(Student only)*
- `GET /purchases/my-courses` - View purchased courses *(Student only)*

---

## 🗄️ Database Models

- **User**: Stores user details and roles (`STUDENT` or `INSTRUCTOR`).
- **Course**: Contains course metadata (title, description, price) created by instructors.
- **Lesson**: Individual curriculum items within courses.
- **Purchase**: Records of courses bought by students.

---

## 🛡️ Authentication

API endpoints under role-based access require a valid JWT token in the `Authorization` header:

```http
Authorization: Bearer <your_jwt_token_here>
```

---
*Built with ❤️ for CourseLelo.io*