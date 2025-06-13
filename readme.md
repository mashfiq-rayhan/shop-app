# Shop APP

Shopmate API is a modern, scalable, and secure e-commerce backend built with **TypeScript**, **Express.js**, and **Prisma ORM** for PostgreSQL. It provides robust user authentication, modular architecture, and best practices for maintainability and extensibility.

---

## Features

- **TypeScript-first**: Type-safe codebase for reliability and maintainability.
- **Express.js**: Fast, unopinionated, and minimalist web framework.
- **Prisma ORM**: Type-safe database access with PostgreSQL.
- **Authentication**: Secure JWT-based authentication and session management.
- **Modular Structure**: Organized by domain (user, authentication, health, etc.).
- **Validation**: Request validation using [Zod](https://zod.dev/).
- **Error Handling**: Centralized and graceful error handling.
- **Logging**: Structured logging with [Pino](https://getpino.io/).
- **Environment Validation**: Uses [envalid](https://github.com/af/envalid) to ensure all required environment variables are set.
- **Security**: Includes security best practices (Helmet, CORS, HPP, compression).
- **Code Quality**: Enforced with ESLint and Prettier.
- **Hot Reload**: Development mode with `nodemon` and `ts-node`.

---

## Prerequisites

- **Node.js**: `v20.16.0`
- **npm**: `>=10.8.2`
- **PostgreSQL**: Running instance for database

---

## Getting Started

### 1. Clone the Repository

```sh
git clone https://github.com/ShaNaim/shopmate.git
cd shopmate
```

### 2. Install Dependencies

```sh
npm install
```

### 3. Environment Setup

- Copy `.env.example` to `.env` and fill in the required variables:

```sh
cp .env.example .env
```

- Required variables include:
  - `PORT`
  - `HOSTNAME`
  - `NODE_ENV`
  - `LOG_LEVEL`
  - `API_VERSION`
  - `DATABASE_URL`
  - JWT keys (see below)

- **JWT Keys**: Generate RSA key pairs for access and refresh tokens. Add them to your `.env` as:
  - `ACCESS_TOKEN_PUBLIC_KEY`
  - `ACCESS_TOKEN_PRIVATE_KEY`
  - `REFRESH_TOKEN_PUBLIC_KEY`
  - `REFRESH_TOKEN_PRIVATE_KEY`

### 4. Database Setup

- Ensure PostgreSQL is running.
- Set your `DATABASE_URL` in `.env` (e.g., `postgresql://user:password@localhost:5432/shopmate`).
- Run Prisma migrations:

```sh
npx prisma migrate dev --name init
```

- (Optional) Format your Prisma schema:

```sh
npm run format-db
```

### 5. Build and Run

#### Development (with hot reload):

```sh
npm run dev
```

#### Production:

```sh
npm run build
npm start
```

---

## Project Structure

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

## Scripts

| Command           | Description                                 |
|-------------------|---------------------------------------------|
| `npm run dev`     | Start server in development mode (hot reload)|
| `npm run build`   | Compile TypeScript to JavaScript            |
| `npm start`       | Start server from compiled code             |
| `npm run lint`    | Run ESLint on codebase                      |
| `npm run format`  | Format code with Prettier                   |
| `npm run clean`   | Remove `dist` directory                     |
| `npm run format-db` | Format Prisma schema                      |

---

## API Endpoints

### Health

- `GET /v/{API_VERSION}/health` — Health check
- `GET /v/{API_VERSION}/health/system` — System info (auth required)

### Authentication

- `POST /v/{API_VERSION}/auth/login` — Login (email, password)
- `POST /v/{API_VERSION}/auth/register` — Register new user
- `GET /v/{API_VERSION}/auth/logout` — Logout (auth required)
- `PUT /v/{API_VERSION}/auth/block/:slug` — Block/unblock user (auth required)

### User

- `GET /v/{API_VERSION}/user/health` — User system health (auth required)
- `GET /v/{API_VERSION}/user/` — List all users (auth required)
- `POST /v/{API_VERSION}/user/` — Create user (auth required)
- `PUT /v/{API_VERSION}/user/:slug` — Update user (auth required)
- `GET /v/{API_VERSION}/user/me` — Get authenticated user info (auth required)
- `GET /v/{API_VERSION}/user/:slug` — Get user by slug (auth required)

---

## Code Quality

- **Linting**: `npm run lint`
- **Formatting**: `npm run format`
- **Pre-commit**: Uses `lint-staged` for staged files

---

## Contributing

1. Fork the repository
2. Create a new branch: `git checkout -b feature/your-feature`
3. Make your changes
4. Run lint and tests
5. Commit and push: `git commit -m "Description"` then `git push origin feature/your-feature`
6. Open a pull request

---

## Troubleshooting

- Ensure Node.js version matches `.nvmrc` (`v20.16.0`). Use `nvm use 20.16.0`.
- Ensure `.env` is properly configured.
- Database connection issues: check `DATABASE_URL` and PostgreSQL status.
- For Prisma errors, see logs and [src/errors/prisma.error.ts](src/errors/prisma.error.ts).

---

## License

MIT

---

## Acknowledgements

- [Express.js](https://expressjs.com/)
- [Prisma ORM](https://www.prisma.io/)
- [Zod](https://zod.dev/)
- [Pino](https://getpino.io/)
