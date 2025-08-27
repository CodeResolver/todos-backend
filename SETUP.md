# Todo List Backend Setup

This is the Express.js backend for the Todo List App using Prisma with **Zod validation** and support for both MySQL and SQLite databases.

## 🚀 Features

- **TypeScript** with full type safety
- **Zod validation** for runtime type checking and better error messages
- **Dual database support** - MySQL (production) and SQLite (development)
- **Express.js** with clean architecture
- **Prisma ORM** for database management
- **CORS** configured for frontend integration

## Prerequisites

- Node.js (v18 or higher)
- npm or yarn package manager
- MySQL server (for production) - optional for development

## Quick Start

### 1. Install Dependencies

```bash
npm install
```

### 2. Choose Your Database

#### Option A: SQLite (Recommended for Development)
```bash
npm run db:sqlite
```

#### Option B: MySQL (Production Ready)
```bash
npm run db:mysql
```

The server will automatically start after database setup!

## Manual Setup

### 1. Install Dependencies

```bash
npm install
```

### 2. Database Configuration

#### For SQLite (Development)
```bash
cp .env.sqlite .env
npm run db:generate
npm run db:push
```

#### For MySQL (Production)
```bash
cp .env.mysql .env
# Edit .env with your MySQL connection string
npm run db:generate
npm run db:push
```

### 3. Start the Development Server

```bash
npm run dev
```

The server will start on `http://localhost:3001`

## API Endpoints

- `GET /tasks` - Get all tasks
- `POST /tasks` - Create a new task
- `PUT /tasks/:id` - Update a task
- `DELETE /tasks/:id` - Delete a task
- `GET /health` - Health check

## Task Schema

```typescript
{
  id: number;
  title: string;
  color: string; // 'red', 'blue', 'green', 'yellow', 'purple', 'orange', 'pink', 'gray'
  completed: boolean;
  createdAt: Date;
  updatedAt: Date;
}
```

## Example API Usage

### Create a Task
```bash
curl -X POST http://localhost:3001/tasks \
  -H "Content-Type: application/json" \
  -d '{"title": "Learn TypeScript", "color": "blue"}'
```

### Get All Tasks
```bash
curl http://localhost:3001/tasks
```

### Update a Task
```bash
curl -X PUT http://localhost:3001/tasks/1 \
  -H "Content-Type: application/json" \
  -d '{"completed": true}'
```

### Delete a Task
```bash
curl -X DELETE http://localhost:3001/tasks/1
```

## Development Commands

- `npm run dev` - Start development server with hot reload
- `npm run build` - Build for production
- `npm run start` - Start production server
- `npm run db:generate` - Generate Prisma client
- `npm run db:push` - Push schema to database
- `npm run db:migrate` - Run database migrations
- `npm run db:studio` - Open Prisma Studio

## Project Structure

```
src/
├── controllers/     # Request handlers
├── middleware/      # Express middleware
├── routes/         # Route definitions
├── types/          # TypeScript type definitions
└── index.ts        # Main application file
```