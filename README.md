# Privacy-Focused Communications Platform

A secure, privacy-first communications platform with end-to-end encrypted messaging and server-routed voice chat.

## Core Features

- 🔒 **End-to-End Encrypted Direct Messages** using Signal Protocol
- 🌐 **Server-Routed Voice Chat** with LiveKit SFU (no P2P IP exposure)
- 🛡️ **Privacy by Design** - minimal data collection
- 🔐 **Two-Factor Authentication** for enhanced security
- 🖥️ **Cross-Platform Desktop App** built with Electron

## Tech Stack

- **Frontend**: React + TypeScript + Electron
- **Backend**: Node.js + TypeScript + Express/Fastify
- **Database**: PostgreSQL
- **Real-time**: WebSockets + LiveKit SFU
- **Encryption**: Signal Protocol (libsignal-protocol-javascript)
- **Deployment**: Google Cloud (Cloud Run + GKE)

## Project Structure

```
privacy-comms-platform/
├── apps/
│   ├── backend/          # Node.js API server
│   └── frontend/         # React web app + Electron wrapper
├── packages/
│   └── shared-types/     # Shared TypeScript interfaces
├── package.json          # Root workspace configuration
└── tsconfig.json         # Root TypeScript configuration
```

## Development Setup

### Prerequisites

- Node.js 18+ and npm 9+
- PostgreSQL 14+
- Docker (optional, for containerized development)

### Quick Start

1. **Clone and install dependencies**:
   ```bash
   git clone <repository-url>
   cd privacy-comms-platform
   npm install
   ```

2. **Set up environment variables**:
   ```bash
   cp apps/backend/.env.example apps/backend/.env
   cp apps/frontend/.env.example apps/frontend/.env
   # Edit the .env files with your configuration
   ```

3. **Start development servers**:
   ```bash
   npm run dev
   ```

This will start both backend (port 3001) and frontend (port 3000) in development mode.

### Individual Package Development

- **Backend only**: `npm run dev:backend`
- **Frontend only**: `npm run dev:frontend`
- **Build all**: `npm run build`
- **Run tests**: `npm run test`
- **Lint code**: `npm run lint`

## Security Considerations

This platform is built with security and privacy as core principles:

- All passwords are hashed with Argon2
- Direct messages use Signal Protocol for E2EE
- Voice traffic is server-routed to prevent IP exposure
- Minimal data collection and retention
- Regular security audits planned

## Deployment

The platform is designed for deployment on Google Cloud:

- **Backend**: Cloud Run (auto-scaling containers)
- **Database**: Cloud SQL (managed PostgreSQL)
- **Voice Server**: GKE (LiveKit SFU)
- **Static Assets**: Cloud Storage + CDN

See `docs/deployment.md` for detailed deployment instructions.

## Contributing

1. Check the development checklist in `development-checklist.md`
2. Follow the coding standards (ESLint + Prettier configured)
3. Write tests for new features
4. Consider security implications of all changes

## License

[License TBD]

---

**⚠️ Security Notice**: This project handles sensitive user communications. Please review all code changes carefully and follow security best practices. 