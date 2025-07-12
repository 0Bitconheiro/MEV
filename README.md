# MEV Sandwich Bot Monitoring Dashboard

A comprehensive MEV (Maximal Extractable Value) monitoring system for WETH/DAI trading pairs on Uniswap V3. This dashboard provides real-time mempool analysis, profit calculations, and opportunity tracking with live blockchain data.

## Features

- **Real-time Mempool Monitoring**: Live transaction analysis with authentic blockchain data
- **MEV Opportunity Detection**: Automated sandwich attack opportunity identification
- **Profit Calculations**: Advanced profitability analysis including gas costs and slippage
- **Live Dashboard**: Real-time metrics with WebSocket updates
- **Historical Analysis**: Performance tracking and execution history
- **Database Persistence**: PostgreSQL storage for all opportunities and alerts
- **Bot Configuration**: Adjustable parameters for risk management and thresholds

## Tech Stack

- **Frontend**: React 18, TypeScript, Tailwind CSS, shadcn/ui components
- **Backend**: Express.js, TypeScript, WebSocket server
- **Database**: PostgreSQL with Drizzle ORM
- **Blockchain**: Ethereum integration with ethers.js
- **Real-time**: WebSocket broadcasting for live updates

## Prerequisites

- Node.js 18+ and npm
- PostgreSQL database
- Ethereum API keys (Alchemy or Infura)

## Setup Instructions

### 1. Install Dependencies

```bash
npm install
```

### 2. Environment Configuration

Create a `.env` file in the root directory:

```env
# Database Configuration (Required)
DATABASE_URL=postgresql://username:password@localhost:5432/mev_monitoring

# Ethereum API Keys (At least one required for live data)
ALCHEMY_API_KEY=your_alchemy_api_key_here
INFURA_PROJECT_ID=your_infura_project_id_here

# Development (Optional)
NODE_ENV=development
```

### 3. Database Setup

Set up your PostgreSQL database and update the connection string in the `.env` file.

Push the database schema:

```bash
npm run db:push
```

### 4. Get API Keys

**Alchemy (Recommended):**
1. Sign up at [alchemy.com](https://alchemy.com)
2. Create a new app for Ethereum Mainnet
3. Copy your API key to `ALCHEMY_API_KEY`

**Infura (Alternative):**
1. Sign up at [infura.io](https://infura.io)
2. Create a new project
3. Copy your Project ID to `INFURA_PROJECT_ID`

### 5. Start the Application

```bash
npm run dev
```

The application will start:
- Frontend: http://localhost:5000
- WebSocket server: ws://localhost:8080

## Project Structure

```
├── client/                 # React frontend
│   ├── src/
│   │   ├── components/     # UI components
│   │   ├── hooks/          # Custom React hooks
│   │   ├── lib/            # Utilities and API client
│   │   └── pages/          # Application pages
├── server/                 # Express backend
│   ├── services/           # Business logic services
│   │   ├── mevService.ts   # MEV opportunity analysis
│   │   ├── web3Service.ts  # Blockchain interactions
│   │   └── uniswapService.ts # Uniswap V3 integration
│   ├── db.ts              # Database connection
│   ├── storage.ts         # Data access layer
│   └── routes.ts          # API routes
├── shared/                # Shared types and schemas
└── package.json
```

## API Endpoints

- `GET /api/dashboard/metrics` - Real-time dashboard metrics
- `GET /api/opportunities` - Recent MEV opportunities
- `GET /api/opportunities/historical` - Historical execution data
- `POST /api/calculate-profit` - Profit calculation for amounts
- `GET/PUT /api/bot/configuration` - Bot settings management
- `GET /api/alerts` - System notifications

## WebSocket Events

The WebSocket server broadcasts real-time updates:
- `opportunities` - New MEV opportunities detected
- `metrics` - Updated dashboard metrics
- `alerts` - System notifications and warnings

## Database Schema

The application uses PostgreSQL with the following main tables:
- `transactions` - Blockchain transaction records
- `mev_opportunities` - Detected MEV opportunities with profitability
- `bot_configuration` - Bot settings and parameters
- `market_data` - Price and volume data for trading pairs
- `alerts` - System notifications and warnings

## Development

The project uses:
- **Vite** for fast development and building
- **TypeScript** throughout for type safety
- **Drizzle ORM** for database operations
- **TanStack Query** for API state management
- **Tailwind CSS** for styling

## Security Considerations

This is a monitoring dashboard for educational and analysis purposes. For production MEV execution:

1. **Smart Contract Integration**: Implement proper MEV execution contracts
2. **Private Mempool Access**: Use services like Flashbots or private pools
3. **Advanced Risk Management**: Implement sophisticated position sizing
4. **Slippage Protection**: Add robust slippage and MEV protection
5. **Gas Optimization**: Implement dynamic gas pricing strategies

## License

MIT License - see LICENSE file for details.

## Disclaimer

This software is for educational and monitoring purposes only. MEV extraction involves significant financial risks. Always conduct thorough testing and consider regulatory compliance before any production use.