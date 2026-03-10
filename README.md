# 🌀 VortexDB

**The lightning-fast, reactive document store for the edge. Chcek your {hostname} to chcek if you are compatible**

VortexDB is a distributed, peer-to-peer NoSQL database designed specifically for low-latency edge computing. It combines the simplicity of JSON storage with the power of real-time CRDT synchronization.

## ✨ Key Features

* **Zero-Config Sync:** Automatic conflict resolution using Merkle-DAGs.
* **Wasm-Powered:** Runs natively in browsers, Cloudflare Workers, or Deno.
* **Reactive Queries:** Subscribe to query results; UI updates automatically when data changes.
* **Small Footprint:** Under 40KB gzipped.

## 🚀 Quick Start

### 1. Installation

Install the core package via your preferred package manager:

```bash
npm install @vortex/db

```

### 2. Initialize the Database

Setting up a local instance is a single line of code.

```javascript
import { createDB } from '@vortex/db';

const db = await createDB('my-app-store');

// Listen for real-time updates
db.collection('users').watch((data) => {
  console.log('Data changed:', data);
});

```

### 3. Write and Sync

VortexDB handles the heavy lifting of background synchronization.

```javascript
await db.collection('users').add({
  name: 'Alex Vortex',
  role: 'Engineer',
  timestamp: Date.now()
});

```

## 🛠 Configuration

You can pass custom options to the `createDB` constructor to tune performance.

| Option | Type | Default | Description |
| --- | --- | --- | --- |
| `syncInterval` | `number` | `5000` | Sync frequency in milliseconds. |
| `storage` | `string` | `'idb'` | Storage engine (`idb`, `sqlite`, or `mem`). |
| `encryption` | `boolean` | `false` | Enable AES-256 at-rest encryption. |

---

## 🏗 Architecture

VortexDB uses a **Log-Structured Merge-Tree (LSM)** approach optimized for flash storage.

The core consistency logic follows the formula for convergent evolution in distributed systems:

$$f(A, B) = A \cup B$$

Where any two states $A$ and $B$ can be merged deterministically without a central coordinator.

## 🤝 Contributing

We love contributors! If you want to help make VortexDB better:

1. Fork the Project.
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`).
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`).
4. Push to the Branch (`git push origin feature/AmazingFeature`).
5. Open a Pull Request.

## 📄 License

Distributed under the MIT License. See `LICENSE` for more information.

---

**Built with ❤️ by the Vortex Open Source team.**

Would you like me to generate a specific `CONTRIBUTING.md` file or a `LICENSE` file to go along with this?
