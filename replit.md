# FastPic Transfer - File Upload & Sharing Application

## Overview

FastPic Transfer is a modern web application for uploading and sharing photos/files with support for large file uploads (up to 100GB), real-time progress tracking, and shareable links. The application features a clean, responsive interface built with React and shadcn/ui components.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Build Tool**: Vite for fast development and optimized builds
- **UI Library**: shadcn/ui components built on Radix UI primitives
- **Styling**: Tailwind CSS with CSS variables for theming
- **State Management**: TanStack Query for server state management
- **Routing**: Wouter for lightweight client-side routing
- **File Handling**: React Dropzone for drag-and-drop file uploads

### Backend Architecture
- **Runtime**: Node.js with Express.js
- **Language**: TypeScript with ES modules
- **File Uploads**: Multer middleware for handling multipart/form-data
- **Real-time Communication**: WebSockets for upload progress updates
- **Session Management**: Express sessions with PostgreSQL store

### Database Architecture
- **Primary Database**: PostgreSQL via Neon serverless
- **ORM**: Drizzle ORM with type-safe queries
- **Schema**: Two main tables - `uploads` and `files` with proper relationships
- **Migrations**: Drizzle Kit for schema management

## Key Components

### Upload System
- **Chunked Uploads**: Support for large file uploads with chunking
- **Progress Tracking**: Real-time progress updates via WebSockets
- **File Validation**: Client-side validation for supported file types
- **Concurrent Uploads**: Multiple file upload support with queue management

### Sharing System
- **Unique Share IDs**: Short, shareable identifiers for upload collections
- **Access Controls**: Optional password protection and download permissions
- **Expiration**: Configurable expiration dates for shared links
- **Download Management**: Individual file downloads with proper MIME types

### Storage Management
- **Local File Storage**: Files stored in `uploads/` directory
- **Storage Tracking**: Real-time storage usage monitoring
- **File Organization**: Organized by upload ID with original filename preservation

## Data Flow

1. **Upload Initiation**: Client creates upload session, receives unique upload ID
2. **File Processing**: Files are validated and uploaded via chunked transfer
3. **Progress Updates**: WebSocket connection provides real-time progress
4. **Storage**: Files saved to local filesystem with metadata in database
5. **Sharing**: Share link generated with configurable access controls
6. **Download**: Recipients access files via share ID with download tracking

## External Dependencies

### Core Dependencies
- **@neondatabase/serverless**: PostgreSQL connection for Neon database
- **drizzle-orm**: Type-safe database ORM
- **multer**: File upload handling middleware
- **ws**: WebSocket server for real-time communication
- **nanoid**: Unique ID generation for uploads and shares

### UI Dependencies
- **@radix-ui/***: Comprehensive set of accessible UI primitives
- **@tanstack/react-query**: Server state management and caching
- **react-dropzone**: File drag-and-drop functionality
- **tailwindcss**: Utility-first CSS framework
- **class-variance-authority**: Type-safe variant styling
- **lucide-react**: Icon library

### Development Dependencies
- **vite**: Fast build tool and dev server
- **tsx**: TypeScript execution for development
- **esbuild**: Fast JavaScript bundler for production

## Deployment Strategy

### Development Environment
- **Hot Reloading**: Vite dev server with HMR support
- **Real-time Debugging**: WebSocket connection monitoring
- **Database Sync**: Drizzle push for schema synchronization

### Production Deployment
- **Build Process**: Vite builds client, esbuild bundles server
- **Static Assets**: Client files served from `dist/public`
- **Environment Variables**: DATABASE_URL required for PostgreSQL connection
- **Port Configuration**: Server runs on port 5000 (configurable)

### Replit Configuration
- **Modules**: Node.js 20, Web, PostgreSQL 16
- **Auto-scaling**: Configured for automatic scaling
- **Public Access**: External port 80 mapped to internal port 5000

## Changelog
```
Changelog:
- June 26, 2025. Initial setup
```

## User Preferences
```
Preferred communication style: Simple, everyday language.
```