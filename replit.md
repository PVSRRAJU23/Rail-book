# RailBook - Indian Railway Ticket Booking Application

## Overview

RailBook is a web-based Indian railway ticket booking application that allows users to search for trains, select seats from a visual coach map, and complete bookings. The application draws inspiration from IRCTC and BookMyShow's seat selection interface, focusing on clear visual hierarchy and intuitive seat selection with color-coded seat states (available, booked, selected).

The application follows a progressive disclosure pattern: search → results → seats → booking, with support for different travel classes (Sleeper, AC 3-Tier, AC 2-Tier, AC First Class) and passenger categories (General, Senior Citizen, Tatkal, Premium Tatkal).

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Routing**: Wouter (lightweight React router)
- **State Management**: TanStack React Query for server state
- **UI Components**: shadcn/ui component library built on Radix UI primitives
- **Styling**: Tailwind CSS with custom design tokens for railway-specific colors (railway-blue #1565C0, primary orange #FF5722)
- **Forms**: React Hook Form with Zod validation
- **Build Tool**: Vite with custom plugins for Replit integration

### Backend Architecture
- **Runtime**: Node.js with Express.js
- **Language**: TypeScript with ESM modules
- **API Pattern**: RESTful endpoints under `/api` prefix
- **Authentication**: Replit Auth integration using OpenID Connect with Passport.js
- **Session Management**: express-session with PostgreSQL session store (connect-pg-simple)

### Data Storage
- **Database**: PostgreSQL
- **ORM**: Drizzle ORM with Zod schema integration (drizzle-zod)
- **Schema Location**: `shared/schema.ts` exports all models
- **Migrations**: Drizzle Kit for schema push (`npm run db:push`)

### Authentication System
- Replit Auth via OpenID Connect
- Session-based authentication stored in PostgreSQL `sessions` table
- User data stored in `users` table with OAuth profile sync
- Auth routes: `/api/login`, `/api/logout`, `/api/auth/user`

### Project Structure
```
client/           # React frontend
  src/
    components/   # UI components (TrainSearch, SeatMap, PassengerForm, etc.)
    hooks/        # Custom hooks (use-auth, use-toast)
    lib/          # Utilities and query client
    pages/        # Page components
server/           # Express backend
  replit_integrations/auth/  # Authentication module
shared/           # Shared types and schemas
  models/         # Drizzle schema definitions
  schema.ts       # Schema exports
```

### Design System
- Typography: Roboto (primary), Open Sans (body)
- Color palette defined in CSS variables with light/dark mode support
- Component theming through shadcn/ui's New York style
- Base-12px spacing system following Tailwind conventions

## External Dependencies

### Database
- PostgreSQL via `DATABASE_URL` environment variable
- Session storage in PostgreSQL using connect-pg-simple

### Authentication
- Replit Auth (OpenID Connect)
- Required environment variables: `REPL_ID`, `ISSUER_URL`, `SESSION_SECRET`

### Third-Party Services
- Google Fonts (Roboto, Open Sans, DM Sans, Geist Mono, Fira Code)

### Key NPM Packages
- `drizzle-orm` / `drizzle-kit` - Database ORM and migrations
- `@tanstack/react-query` - Server state management
- `@radix-ui/*` - Accessible UI primitives
- `openid-client` - OIDC authentication
- `passport` / `passport-local` - Authentication middleware
- `zod` - Schema validation
- `react-hook-form` - Form handling