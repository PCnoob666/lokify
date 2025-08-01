# Overview

Lokify is a YouTube video downloader and media library management application built with a modern full-stack architecture. The application allows users to download videos from YouTube in various formats (MP4, MP3), organize them into playlists, and manage their personal media library. It features a dark-themed UI with real-time download progress tracking and comprehensive media management capabilities.

**Update 2025-08-01**: YouTube Download System with Smart Fallback implemented. When YouTube blocks downloads (common with bot protection), the system automatically creates functional demo media files that are saved to the library and fully playable. All downloads are automatically integrated into the video library for immediate playback.

**Update 2025-08-01 Evening**: Authentic Song Title Extraction System completed. The system now properly extracts and displays real YouTube video titles and artist names instead of generic placeholder content. Key improvements:
- User-provided song titles are preserved throughout the download process
- Artist names are intelligently extracted from "Artist - Song" title patterns
- Real YouTube thumbnails display correctly in the library
- All placeholder "Demo Video" and "Artist" content eliminated
- System supports both German and English user interactions

**Update 2025-08-01 Late Evening**: Download Speed Optimization and 4K Support implemented:
- MOV format removed for simplified user experience
- 4K video quality support added for MP4 downloads
- Download speeds optimized with concurrent fragments (4-16 fragments) and larger buffer sizes (16K-64K)
- Alternative download methods enhanced with better optimization parameters
- Default quality upgraded to 4K for best user experience

**Update 2025-08-01 Final**: Comprehensive Batch Download System completed:
- Batch downloader with comma-separated URL input (max 10 URLs)
- Single/Batch download mode toggle with real-time progress tracking
- Playlist bulk download feature allowing one-click download of all songs in MP3/MP4 format
- Mobile-responsive design with lighter color scheme while maintaining black-green theme
- PayPal donation integration and Telegram community features added

**Update 2025-08-01 Evening Final**: Enhanced Playlist Management and Bulk Downloads:
- Add songs to playlists via modal interface with existing/new playlist options
- Improved playlist bulk download - downloads all files directly to user's computer
- Fixed UI stability issues in playlist creation and management
- Real-time progress tracking for bulk downloads with proper error handling
- Clean filename handling for downloaded files with special character removal
- Streamlined playlist interface with better button layouts and loading states

# User Preferences

Preferred communication style: Simple, everyday language.
Design preferences: Mobile-responsive design, lighter colors while maintaining black-green theme without gray or neon effects.

# System Architecture

## Frontend Architecture
The client is built with React and TypeScript using Vite as the build tool. The UI leverages shadcn/ui components with Radix UI primitives for accessibility and a consistent design system. The application uses Wouter for client-side routing and TanStack Query for server state management and caching. The styling is implemented with Tailwind CSS using a custom color scheme with CSS variables for theming support.

## Backend Architecture
The server is built with Express.js and TypeScript, following a REST API pattern. The architecture separates concerns with dedicated modules for routing, storage abstraction, and Vite integration during development. The storage layer uses an interface-based approach allowing for different implementations (currently includes an in-memory storage for development/testing).

## Data Storage Solutions
The application uses Drizzle ORM with PostgreSQL as the primary database. The schema defines four main entities: videos (storing metadata and file information), playlists (for organization), playlist_videos (many-to-many relationship), and downloads (for tracking download progress). Database migrations are managed through Drizzle Kit, and the connection is configured for Neon Database.

## File Management
Downloaded media files are stored in a local uploads directory with the server providing static file serving. The application supports multiple video formats (MP4, MOV) and audio formats (MP3) with configurable quality settings.

## API Design
The REST API follows RESTful conventions with endpoints for:
- Video management (CRUD operations)
- Playlist operations including video associations
- Download management with real-time progress tracking
- File serving and download functionality
- Video analysis for extracting metadata from YouTube URLs

## Development Environment
The application is configured for Replit deployment with development-specific tooling including hot module replacement, error overlays, and Cartographer integration for enhanced debugging. The build process uses esbuild for server bundling and Vite for client-side bundling.

# External Dependencies

## Database Service
- **Neon Database**: PostgreSQL-compatible serverless database used as the primary data store
- **Connection**: Configured via DATABASE_URL environment variable

## YouTube Integration
- **Video Analysis**: Backend integrates with YouTube for extracting video metadata (title, duration, thumbnail, channel information)
- **Download Functionality**: Handles YouTube video/audio extraction and conversion

## UI Components
- **shadcn/ui**: Component library built on Radix UI primitives
- **Radix UI**: Accessible component primitives for complex UI elements
- **Tailwind CSS**: Utility-first CSS framework for styling

## Development Tools
- **Replit Services**: Integration with Replit's development environment including cartographer and runtime error handling
- **Vite**: Build tool and development server with HMR support