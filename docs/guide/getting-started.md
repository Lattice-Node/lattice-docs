# Getting Started

## Installation
```bash
npm install @lattice-node/core
```

## Start the server
```typescript
import { LatticeServer } from '@lattice-node/core'

new LatticeServer(8080)
// Lattice server running on port 8080
```

## Connect your first agent
```typescript
import { LatticeClient } from '@lattice-node/core'

const agent = new LatticeClient('AgentA', 'ws://localhost:8080')
await agent.waitForOpen()

// Listen for results
agent.onResult((msg) => {
  console.log('Result from', msg.from, ':', msg.payload)
})

// Send a task to another agent
agent.send('AgentB', 'task', 'Summarize this document')
```

## Message format

Every message in Lattice follows this structure:
```typescript
type LatticeMessage = {
  id: string        // unique message ID
  from: string      // sender agent name
  to: string        // recipient agent name
  type: 'task' | 'result' | 'error'
  payload: unknown  // any data
  timestamp: number
}
```

## Next steps

- [View on GitHub](https://github.com/Lattice-Node/lattice)
- [npm package](https://www.npmjs.com/package/@lattice-node/core)