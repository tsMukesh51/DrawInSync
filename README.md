# DrawInSync

**Real-time collaborative whiteboard built with WebSockets and TypeScript**

A backend-driven system for synchronizing canvas state across multiple users in real time, with a focus on **low-latency updates, consistency, and scalable architecture**.
---

## Live Demo

Check out the live application here: [DrawInSync Live](https://drawinsync.vercel.app/)

---

## **Table of Contents**

1. [Project Overview](#project-overview)
2. [Key Features](#key-features)
3. [Tech Stack](#tech-stack)
4. [Setup Instructions](#setup-instructions)
5. [Available Scripts](#available-scripts)
6. [Acknowledgements](#acknowledgements)

---

## **Project Overview**

DrawInSync allows multiple users to draw simultaneously on a shared canvas while maintaining consistent state across all clients.

This project focuses on solving core challenges of **real-time systems**, including:

* Event synchronization
* Conflict handling
* Efficient state updates
* Network optimization

---

## **Key Features**

* Real-time drawing sync using **WebSockets**
* Multi-user collaboration on shared canvas
* Event-based architecture for state updates
* Modular monorepo structure (apps + shared packages)
* Optimized for low-latency communication

---

## **Project Architecture**

```mermaid
graph TD
    A[Client Request] --> B[Next.js API Routes]
    B --> C["Middleware<br>(Authentication & Validation)"]
    C --> D["Controllers<br>(API & WebSocket Handlers)"]
    D --> E["Services<br>(Business Logic)"]
    E --> F["PostgreSQL<br>(via Prisma)"]
    F --> G["Models<br>(User, Board, BoardCollaborator, Element)"]
    G --> E
    E --> D
    D --> H[Response/WebSocket Updates to Client]
    C --> H
    %% Styling for better readability
    classDef client fill:#f9f,stroke:#333,stroke-width:2px,color:#100c08;
    classDef server fill:#bbf,stroke:#333,stroke-width:2px,color:#100c08;
    classDef database fill:#bfb,stroke:#333,stroke-width:2px,color:#100c08;
    class A client;
    class B,C,D,E server;
    class F,G database;
```

The DrawInSync backend is a Next.js-based application integrated with Express for API routes and WebSocket for real-time drawing synchronization. It uses Prisma to manage PostgreSQL, with models for User, Board, BoardCollaborator, and Element. Middleware handles authentication and validation (via Zod), while services manage business logic. Data flows from client requests to PostgreSQL via Prisma, with WebSocket updates ensuring simultaneous drawing across users—all custom-built for this collaborative proof-of-concept.

---

## **Tech Stack**

- **Framework**: Next.js with Express
- **Language**: TypeScript
- **Database**: PostgreSQL with Prisma ORM
- **Real-Time**: WebSocket for synchronization
- **Validation**: Zod for schema validation
- **Utilities**: dotenv for environment variables
- **Monorepo**: TurboRepo for project management
- **Styling**: TailwindCSS (for potential backend UI or frontend integration)

---

## **Setup Instructions**

### Prerequisites
Ensure you have the following installed:
- Node.js (version 16 or higher)
- pnpm enabled
- PostgreSQL instance (local or cloud)

### Steps

1. Clone the repository:
   ```bash
   git clone https://github.com/tsMukesh51/WebDev.git
   cd ...WebDev/proj-week-23-drawinsync
   ```

2. Install dependencies:
   ```bash
   pnpm install
   ```

3. Create a `.env` file based on the provided `env.example` in `packages/db`, `http-server`, `ws-server`:
   ```bash
   DATABASE_URL=postgresql://user:password@localhost:5432/drawinsync
   ```

4. Build the project:
   ```bash
   pnpm run build
   ```

5. Start the server:
   ```bash
   pnpm start
   ```

6. For development:
   ```bash
   pnpm run dev
   ```

The http-server runs on `http://localhost:3000` by default.
The ws-serrver runs on `http://localhost:8080` by default.
The Next.js runs on `http://localhost:4200` by default.

---

## **Acknowledgements**

Special thanks to my mentor **[Kirat](https://github.com/hkirat)** for guiding me through the initial stages of this project and helping me understand backend development principles.

---
