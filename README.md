# StreamSync

Real-time collaboration platform with conflict-free replicated data types (CRDTs).

## Overview

StreamSync is a distributed collaboration engine designed for seamless multi-user editing. It enables real-time synchronization across multiple clients without central coordination, ensuring eventual consistency even in the presence of network partitions.

## Features

- **CRDT-based Data Structures**: Implements conflict-free replicated data types for automatic merge resolution
- **WebSocket Synchronization**: Real-time bi-directional communication between clients
- **Operational Transforms**: Efficient handling of concurrent document edits
- **Automatic Conflict Resolution**: Deterministic merging without manual intervention
- **Distributed Architecture**: No single point of failure

## Technical Stack

- **TypeScript** - Type-safe implementation
- **WebSockets** - Real-time communication layer
- **Redis** - State persistence and pub/sub messaging
- **React** - Client-side interface
- **CRDT Algorithms** - Convergent data structures

## Architecture

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   Client A  │────▶│  WebSocket  │◀────│   Client B  │
└─────────────┘     │   Server    │     └─────────────┘
                    └──────┬──────┘
                           │
                    ┌──────▼──────┐
                    │    Redis    │
                    │  (State +   │
                    │   Pub/Sub)  │
                    └─────────────┘
```

## How It Works

1. **State Initialization**: Clients connect and receive the current document state
2. **Local Operations**: User actions are applied locally and broadcast
3. **Merge Resolution**: Incoming operations are merged using CRDT semantics
4. **Consistency**: All clients converge to the same final state

## Demo

View the live demo at: https://danielminton.github.io/StreamSync/

## Local Development

```bash
# Install dependencies
npm install

# Start development server
npm run dev

# Build for production
npm run build
```

## Project Structure

```
├── index.html      # Main application entry
├── src/
│   ├── crdt/       # CRDT implementations
│   ├── sync/       # Synchronization logic
│   └── ui/         # React components
└── public/
```

## Author

Daniel Minton