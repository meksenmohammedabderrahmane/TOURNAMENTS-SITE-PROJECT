# N1 Arena

**Competitive Fortnite Tournament Platform**

N1 Arena is a full-stack esports tournament platform built for competitive Fortnite players. It provides automated bracket generation, real-time match tracking, an in-platform economy, and a complete admin system, all within a modern and responsive interface.

**Live site:** [numberonearena.xyz](https://numberonearena.xyz)

---

## Project Vision

N1 Arena was built to create a community-driven tournament ecosystem where players compete in fair, skill-based competitions. The platform serves **700+ active users** and has distributed **20,000+ DZD in prizes**.

The platform emphasizes:

- Competitive integrity and fair play
- Clean, responsive user experience
- Transparent match reporting and dispute resolution
- Strong admin oversight and moderation tools
- No gambling, betting, or chance-based mechanics

---

## Architecture Overview

The platform is split into three independent services:

| Service | Stack | Deployment |
|---------|-------|------------|
| **Frontend** | Next.js 14 (App Router), React 18, TypeScript, CSS Modules, Framer Motion | Vercel |
| **Backend** | Express.js, TypeScript, Prisma ORM, Socket.IO, Zod | Render |
| **Discord Bot** | discord.js, Node.js | Self-hosted |
| **Database** | PostgreSQL | Supabase |

**Authentication** is handled through Discord OAuth with JWT-based session management.

---

## Core Features

### Authentication
- Discord OAuth login with automatic account creation
- JWT-based session management
- Player profile management (Fortnite IGN, country, linked Epic account)
- IP tracking and security logging

### Tournament System
- Scheduled tournaments with configurable registration windows
- Support for multiple games (Fortnite, Valorant, Rocket League)
- Two tournament formats:
  - **Bracket** (double-elimination with upper/lower brackets, grand final, and grand final reset)
  - **Leaderboard** (points-based with matchmaking queue)
- Automatic bracket generation with proper seeding and bye handling
- Configurable match format (first-to with overtime), regions, entry fees, and prize distribution (1st through 7th place)
- Live bracket visualization and real-time updates via WebSockets

### Match System
- Real-time readiness checks before matches begin
- In-match chat powered by Socket.IO
- Result claiming system: both players submit their claim (won/lost)
- Automatic confirmation when claims agree
- Dispute flagging when claims conflict, with admin resolution tools
- 7-minute auto-resolve timer for unresponsive players
- Full match history with timestamps

### Team System
- Team creation (2v2 support)
- Invitation system with accept/decline flow
- Two payment modes for team entry fees:
  - **Split**: each teammate pays their share
  - **Cover**: one player covers the full entry
- Teammate consent required before registration is finalized
- Timeout expiry for pending teammate acceptance

### Economy and Wallet
- In-platform balance system (DZD currency)
- Virtual currency support (V-Bucks)
- Entry fee deduction on tournament registration
- Automatic prize distribution to winners
- Peer-to-peer tipping between players
- Full transaction history with audit trail
- Deposits and withdrawals coordinated through Discord (no automated payments)

### Shop System
- Cosmetic item shop with titles and avatar borders
- Purchasable titles with custom colors and style effects
- Avatar border overlays with visual customization
- Promotional items with configurable discounts
- Inventory management (equip/unequip items)

### LFG (Looking for Group) Board
- Players can post LFG or LFP listings
- Filterable by game, region, rank, and role
- Support for party codes (Valorant), Epic IDs (Fortnite), and platform info (Rocket League)

### Leaderboard
- Global player rankings
- Stats tracking: wins, losses, matches played, points
- Tournament-specific leaderboard entries

### Admin Panel
- Full tournament lifecycle management (create, edit, start, freeze, finish, delete)
- Match monitoring and manual result forcing
- Dispute resolution interface
- User management: bans (with reason and expiry), balance operations, role assignments
- VIP system management
- Activity log viewer
- IP history and multi-account detection
- Transaction oversight

### SEO and Performance
- Dynamic sitemap generation
- robots.txt configuration
- Optimized metadata per page

---

## Tech Stack

**Languages:** TypeScript, JavaScript, SQL, HTML, CSS

**Frontend:**
- Next.js 14 (App Router)
- React 18
- Framer Motion (animations)
- Socket.IO Client (real-time)
- CSS Modules

**Backend:**
- Node.js with Express.js
- Prisma ORM
- Socket.IO (WebSockets)
- Zod (input validation)
- JSON Web Tokens (auth)

**Database:**
- PostgreSQL (via Supabase)
- Prisma Migrations

**Integrations:**
- Discord OAuth2
- discord.js (bot framework)

**Deployment:**
- Vercel (frontend)
- Render (backend)
- Supabase (database)

---

## Technical Highlights

- **20+ database models** covering users, tournaments, brackets, matches, teams, transactions, shop items, leaderboards, and moderation
- **Double-elimination bracket engine** with deterministic state transitions, proper seeding, bye handling, upper/lower bracket progression, and grand final resets
- **Real-time architecture** using Socket.IO for live match updates, readiness checks, and in-match chat
- **Role-based access control** with admin, owner, VIP, and N1 Member tiers
- **Comprehensive dispute resolution** with claim verification, auto-resolve timers, and admin override capabilities
- **Transaction audit trail** for all balance movements across the platform
- **Edge case handling** for partial registrations, teammate timeouts, conflicting match claims, and bracket anomalies

---

## Development Philosophy

This project was built with the mindset of a real production platform, not a prototype. Significant effort went into:

- Designing reliable tournament flows with deterministic state machines
- Handling edge cases and failure scenarios at every step
- Building smooth, real-time user experiences
- Ensuring logical consistency across all features
- Creating robust admin tooling for platform operations

---

## Future Improvements

- Real-time push notifications
- Match proof uploads (screenshot/video verification)
- Advanced tournament formats (round robin, Swiss)
- Player performance analytics and stat tracking
- Automated moderation tools
- Improved horizontal scaling

---

## Author

Built and maintained as part of the N1 competitive ecosystem.

This project reflects extensive work in full-stack development, system design, real-time architecture, and esports platform engineering.

---

## Disclaimer

N1 Arena is a skill-based tournament platform. It does not include gambling, betting, or chance-based mechanics. All competitions are performance-driven.
