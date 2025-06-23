# Shopmate API 🛒

Shopmate API is a modern, scalable, and secure e-commerce backend built with **TypeScript**, **Express.js**, and **Prisma ORM** for PostgreSQL. Designed with modularity and best practices in mind, it provides robust user authentication, session management, and a clean architecture for rapid development and easy maintenance.

---

## ✨ Features

- ⚡ **TypeScript-first:** Type-safe codebase for reliability and maintainability.
- 🚀 **Express.js:** Fast, minimalist web framework for scalable APIs.
- 🗄️ **Prisma ORM:** Type-safe database access with PostgreSQL.
- 🔐 **Authentication:** Secure JWT-based authentication and session management.
- 🧩 **Modular Structure:** Organized by domain (user, authentication, health, etc.).
- ✅ **Validation:** Request validation using [Zod](https://zod.dev/).
- 🛡️ **Security:** Helmet, CORS, HPP, and compression for best practices.
- 📝 **Logging:** Structured logging with [Pino](https://getpino.io/).
- 🧪 **Error Handling:** Centralized and graceful error handling.
- 🧹 **Code Quality:** Enforced with ESLint and Prettier.
- 🔄 **Hot Reload:** Development mode with `nodemon` and `ts-node`.
- 🧬 **Environment Validation:** Uses [envalid](https://github.com/af/envalid) to ensure all required environment variables are set.

---

## 🏆 Achievements

- 🏗️ **Designed a modular, scalable backend** that supports rapid feature development and easy maintenance.
- 🔒 **Implemented robust authentication and session management** using JWT and secure password hashing (argon2).
- 🧩 **Developed a flexible user system** with support for personal details and address management, using Prisma’s relational modeling.
- 🛠️ **Centralized error handling and validation** for consistent API responses and easier debugging.
- 🚦 **Automated environment and code quality checks** with envalid, ESLint, and Prettier.
- 📈 **Optimized for production-readiness** with security best practices and structured logging.
- 🧪 **Ensured reliability** with graceful error handling and clear API documentation.
- 🗃️ **Managed database migrations and schema evolution** using Prisma Migrate.

---

## 🗂️ Project Structure

```
src/
  config/         # Configuration files (env, logger, server modes)
  errors/         # Custom error classes and error handling
  middlewares/    # Express middlewares (auth, validation, error handling)
  modules/        # Feature modules (user, authentication, health, etc.)
  utils/          # Utilities, providers, validators, types
  routes.ts       # Main router
  server.ts       # Express server entrypoint
prisma/
  schema.prisma   # Prisma schema
  migrations/     # Database migrations
.env.example      # Example environment variables
```

---

## 🚀 Getting Started

1. **Clone the Repository**
   ```sh
   git clone https://github.com/mashfiq-rayhan/shop-app.git
   cd shopmate
   ```

2. **Install Dependencies**
   ```sh
   npm install
   ```

3. **Environment Setup**
   - Copy `.env.example` to `.env` and fill in the required variables.
   - Generate RSA key pairs for JWT and add them to your `.env`.

4. **Database Setup**
   - Ensure PostgreSQL is running.
   - Set your `DATABASE_URL` in `.env`.
   - Run Prisma migrations:
     ```sh
     npx prisma migrate dev --name init
     ```

5. **Run the App**
   - Development (hot reload):
     ```sh
     npm run dev
     ```
   - Production:
     ```sh
     npm run build
     npm start
     ```

---

## 📌 API Highlights

- **Health:** `/v/{API_VERSION}/health`
- **Authentication:** `/v/{API_VERSION}/auth/login`, `/v/{API_VERSION}/auth/register`, `/v/{API_VERSION}/auth/logout`
- **User:** `/v/{API_VERSION}/user/`, `/v/{API_VERSION}/user/me`, `/v/{API_VERSION}/user/:slug`

---

## 🧑‍💻 Contributing

1. Fork the repository
2. Create a new branch: `git checkout -b feature/your-feature`
3. Make your changes
4. Run lint and tests
5. Commit and push: `git commit -m "Description"` then `git push origin feature/your-feature`
6. Open a pull request

---

## 📜 License

MIT

---

Shopmate API is built for developers who value clean code, scalability, and security. Whether you're building a new e-commerce platform or looking for a reference implementation, this project is a solid foundation for your next backend adventure. Happy coding! 🎉
