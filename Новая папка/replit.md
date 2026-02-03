# DVesti - AI Fashion Stylist Platform

## Overview

DVesti is an AI-powered fashion stylist web application that helps users who are unfamiliar with style and fashion to discover personalized outfits for any occasion. The platform analyzes user queries (like "what to wear to the conservatory"), suggests appropriate fashion styles, and generates complete outfit recommendations with proper color coordination, layering, and silhouette composition.

The application follows a wizard-based flow where users provide their preferences (gender, sizes, material restrictions), describe their occasion or needs in natural language, and receive AI-curated style suggestions and complete outfit compositions.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Routing**: Wouter (lightweight React router)
- **State Management**: TanStack React Query for server state
- **Styling**: Tailwind CSS with CSS variables for theming
- **UI Components**: shadcn/ui (Radix UI primitives + custom styling)
- **Animations**: Framer Motion for page transitions and interactions
- **Build Tool**: Vite with path aliases (@/, @shared/, @assets/)

Design follows a minimalist, elegant aesthetic with light tones and soft purple accents. Typography uses Playfair Display for headings and Lato for body text.

### Backend Architecture
- **Runtime**: Node.js with Express 5
- **Language**: TypeScript (ESM modules)
- **API Pattern**: RESTful JSON API under `/api/*` routes
- **AI Integration**: OpenAI API via Replit AI Integrations for text analysis and outfit generation
- **Development**: Vite dev server with HMR, production serves static files

### Data Storage
- **Database**: PostgreSQL
- **ORM**: Drizzle ORM with Zod schema validation (drizzle-zod)
- **Schema Location**: `shared/schema.ts` (shared between client and server)
- **Migrations**: Drizzle Kit with `db:push` command

### Key Data Models
- **styles**: Pre-defined fashion styles (Classic, Casual, Bohemian, Streetwear, etc.) with gender associations
- **outfitRequests**: User session history storing queries, preferences, and AI-generated outfits
- **conversations/messages**: Chat history for AI interactions (from Replit integrations)

### API Structure
Routes defined in `shared/routes.ts` as a typed contract:
- `GET /api/styles` - List all fashion styles
- `GET /api/styles/:id` - Get single style details
- `POST /api/stylist/analyze` - Analyze user query to extract occasion and suggest styles
- `POST /api/stylist/generate` - Generate complete outfit based on query, preferences, and selected style

### AI Integration Pattern
The stylist uses OpenAI to:
1. Parse natural language queries to understand occasion context
2. Match user needs to appropriate fashion styles
3. Generate coordinated outfit compositions following fashion rules (color theory, layering, silhouette)

## External Dependencies

### AI Services
- **OpenAI API**: Accessed via Replit AI Integrations (`AI_INTEGRATIONS_OPENAI_API_KEY`, `AI_INTEGRATIONS_OPENAI_BASE_URL`)
- Used for text completion (outfit analysis/generation) and image generation capabilities

### Database
- **PostgreSQL**: Connection via `DATABASE_URL` environment variable
- **connect-pg-simple**: Session storage (if sessions are implemented)

### Key NPM Packages
- **drizzle-orm/drizzle-kit**: Database ORM and migrations
- **@tanstack/react-query**: Async state management
- **framer-motion**: Animation library
- **zod**: Runtime type validation
- **Radix UI**: Accessible component primitives (accordion, dialog, select, tabs, etc.)

### Development Tools
- **Vite**: Build tool with React plugin
- **tsx**: TypeScript execution for development
- **esbuild**: Production bundling for server

### Environment Variables Required
- `DATABASE_URL`: PostgreSQL connection string
- `AI_INTEGRATIONS_OPENAI_API_KEY`: OpenAI API key
- `AI_INTEGRATIONS_OPENAI_BASE_URL`: OpenAI base URL (Replit proxy)