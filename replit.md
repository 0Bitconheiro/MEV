# MEV Sandwich Bot Monitor

## Overview

This is a sophisticated MEV (Maximal Extractable Value) sandwich bot monitoring application built for WETH/DAI trading pairs on Ethereum. The application provides real-time monitoring of mempool transactions, profit calculations, and historical analysis of MEV opportunities. It features a full-stack architecture with a React frontend and Express.js backend, utilizing PostgreSQL for data persistence and WebSocket connections for real-time updates.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Routing**: Wouter for lightweight client-side routing
- **State Management**: TanStack Query (React Query) for server state management
- **UI Components**: Radix UI primitives with shadcn/ui component library
- **Styling**: Tailwind CSS with custom dark theme variables
- **Build Tool**: Vite with custom configuration for development and production builds

### Backend Architecture
- **Framework**: Express.js with TypeScript
- **Database ORM**: Drizzle ORM for type-safe database operations
- **Real-time Communication**: WebSocket server for live updates
- **API Design**: RESTful API with structured endpoints for dashboard metrics, opportunities, and bot configuration

### Database Schema
- **Database**: PostgreSQL with Neon serverless connection
- **Tables**: 
  - `transactions` - blockchain transaction records
  - `mev_opportunities` - detected MEV opportunities with profitability analysis
  - `bot_configuration` - bot settings and parameters
  - `market_data` - price and volume data for trading pairs
  - `alerts` - system notifications and warnings

## Key Components

### Core Services
1. **MEV Service** - Analyzes transactions for sandwich opportunities and calculates profitability
2. **Web3 Service** - Interfaces with Ethereum blockchain for real-time data
3. **Uniswap Service** - Handles Uniswap V3 pool interactions and price calculations

### Frontend Components
1. **Dashboard** - Main monitoring interface with real-time metrics
2. **Mempool Monitor** - Live transaction feed with opportunity detection
3. **Profit Calculator** - Tool for calculating potential MEV profits
4. **Historical Data** - Analysis of past opportunities and performance
5. **Bot Configuration** - Settings panel for trading parameters
6. **Alerts Panel** - System notifications and warnings display

### Real-time Features
- WebSocket connection for live updates
- Automatic refresh intervals for critical data
- Real-time price feeds and gas price monitoring

## Data Flow

1. **Transaction Monitoring**: Web3 service monitors mempool for large transactions
2. **Opportunity Detection**: MEV service analyzes transactions for sandwich potential
3. **Profitability Calculation**: Estimates profits considering gas costs and slippage
4. **Data Persistence**: Opportunities and results stored in PostgreSQL
5. **Real-time Updates**: WebSocket broadcasts updates to connected clients
6. **Historical Analysis**: Past opportunities analyzed for performance metrics

## External Dependencies

### Blockchain Infrastructure
- Ethereum RPC providers (Infura/Alchemy/custom)
- Uniswap V3 protocol integration
- Gas price oracles for cost estimation

### Database
- PostgreSQL (Neon serverless)
- Drizzle ORM for migrations and queries

### UI/UX Libraries
- Radix UI for accessible component primitives
- Tailwind CSS for styling
- Lucide React for icons
- React Hook Form for form management

## Deployment Strategy

### Development
- Vite dev server with HMR for frontend
- Express server with tsx for TypeScript execution
- Replit integration with custom banners and error overlays

### Production
- Frontend built with Vite and served as static files
- Backend bundled with esbuild for Node.js deployment
- Database migrations managed through Drizzle Kit
- Environment variables for API keys and database connections

### Configuration
- TypeScript strict mode enabled
- ESM modules throughout the application
- Path aliases configured for clean imports
- Tailwind CSS with custom design system variables

The application follows a modular architecture pattern with clear separation of concerns, making it maintainable and scalable for monitoring MEV opportunities in the DeFi ecosystem.