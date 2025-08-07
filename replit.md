# Pall Network Crypto Mining App

## Overview

Pall Network is a full-stack, mobile-optimized web application for crypto mining where users can mine "Pall Coin" (PLC) tokens by tapping a "Mine" button once every 24 hours. The app features user authentication, mining mechanics with cooldown timers, wallet functionality, referral systems, and admin capabilities. Built with modern web technologies and designed for optimal mobile experience.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
The client-side is built using React with TypeScript, implementing a modern component-based architecture:

- **UI Framework**: React with TypeScript for type safety and maintainability
- **Styling**: Tailwind CSS with a custom crypto-themed design system and Shadcn/UI components
- **State Management**: TanStack React Query for server state management and caching
- **Routing**: Wouter for lightweight client-side routing
- **Build Tool**: Vite for fast development and optimized production builds

The frontend follows a page-based structure with reusable UI components, implementing responsive design patterns optimized for mobile devices.

### Backend Architecture
The server-side uses Node.js with Express in a RESTful API pattern:

- **Runtime**: Node.js with Express.js framework
- **Language**: TypeScript with ES modules for modern JavaScript features
- **API Design**: RESTful endpoints for authentication, mining, wallet operations, and admin functions
- **File Structure**: Modular separation with dedicated route handlers and business logic

### Authentication System
Implements Replit's OpenID Connect (OIDC) authentication system:

- **Provider**: Replit Auth with OpenID Connect protocol
- **Session Management**: Express sessions with PostgreSQL session store
- **Security**: JWT tokens, secure cookies, and session-based authentication
- **Authorization**: Role-based access control with admin privileges

### Data Storage Architecture
Uses PostgreSQL as the primary database with Drizzle ORM:

- **Database**: PostgreSQL (configured for Neon serverless)
- **ORM**: Drizzle ORM for type-safe database operations
- **Schema Design**: Relational model with users, mining transactions, and sessions tables
- **Connection**: Connection pooling with Neon serverless driver

### Core Database Schema
- **Users Table**: Stores user profiles, mining stats, referral codes, and balance information
- **Mining Transactions Table**: Tracks all mining activities with timestamps and amounts
- **Sessions Table**: Manages user authentication sessions

### Mining System Design
Implements a time-based mining mechanism with cooldown periods:

- **Mining Logic**: Users can mine once per 24-hour period
- **Cooldown System**: Server-side timestamp validation prevents double mining
- **Reward System**: Fixed reward of 1 PLC per mining session
- **Transaction Logging**: All mining activities are recorded for audit trails

### Real-time Features
The application includes countdown timers and real-time status updates:

- **Countdown Timer**: Client-side JavaScript countdown showing time until next mining opportunity
- **Status Polling**: Periodic checks for mining availability
- **Instant Updates**: Optimistic UI updates with server-side validation

## External Dependencies

### Authentication Service
- **Replit Auth**: OpenID Connect provider for secure user authentication
- **Passport.js**: Authentication middleware for Express.js integration

### Database Infrastructure
- **Neon Database**: Serverless PostgreSQL hosting platform
- **Drizzle Kit**: Database migration and schema management tools

### UI and Styling Libraries
- **Shadcn/UI**: Pre-built React component library with Radix UI primitives
- **Tailwind CSS**: Utility-first CSS framework for responsive design
- **Radix UI**: Accessible component primitives for complex UI interactions

### Development and Build Tools
- **TypeScript**: Static type checking for both frontend and backend
- **Vite**: Frontend build tool with hot module replacement
- **ESBuild**: Fast JavaScript bundler for production builds

### Additional Libraries
- **React Hook Form**: Form handling with validation
- **Date-fns**: Date manipulation and formatting utilities
- **Lucide React**: Icon library for consistent iconography
- **Wouter**: Lightweight routing solution for React applications