# Dark Reign Tower Defence - Setup Guide

## Prerequisites

- Node.js 16+ installed
- npm or yarn package manager
- Git

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/lawns2747-ui/dark-reign-tower-defence.git
cd dark-reign-tower-defence
```

### 2. Install All Dependencies

```bash
npm run install-all
```

This will install dependencies for both frontend and backend.

### 3. Setup Environment Variables

Create a `.env` file in the `backend/` directory:

```bash
cd backend
cp .env.example .env
```

Update `.env` if needed (defaults should work for local development).

## Running the Game

### Development Mode (Frontend + Backend)

From the root directory:

```bash
npm run dev
```

This will start both:
- **Frontend**: http://localhost:3000
- **Backend API**: http://localhost:5000

### Running Frontend Only

```bash
cd frontend
npm run dev
```

Access at http://localhost:3000

### Running Backend Only

```bash
cd backend
npm run dev
```

API available at http://localhost:5000

## Testing the API

### Get Leaderboard

```bash
curl http://localhost:5000/api/leaderboard
```

### Submit a Score

```bash
curl -X POST http://localhost:5000/api/scores \
  -H "Content-Type: application/json" \
  -d '{
    "playerName": "Commander Alpha",
    "faction": "freedom_guard",
    "map": "Industrial Wasteland",
    "waveReached": 10,
    "finalScore": 5000
  }'
```

## Building for Production

### Frontend Build

```bash
cd frontend
npm run build
```

Output will be in `frontend/dist/`

### Backend Deployment

```bash
cd backend
npm start
```

## Project Structure

```
dark-reign-tower-defence/
├── frontend/
│   ├── js/
│   │   ├── game.js              # Phaser config
│   │   └── scenes/
│   │       ├── FactionSelectScene.js
│   │       ├── GameScene.js
│   │       └── LeaderboardScene.js
│   ├── css/
│   │   └── styles.css
│   ├── index.html
│   ├── webpack.config.js
│   └── package.json
├── backend/
│   ├── server.js
│   ├── .env.example
│   └── package.json
├── package.json                  # Root workspace
└── README.md
```

## Troubleshooting

### Port 3000 or 5000 already in use

Change the port in:
- Frontend: `frontend/webpack.config.js` (devServer.port)
- Backend: `backend/.env` (PORT variable)

### CORS errors

Ensure both frontend and backend are running on correct ports. Frontend dev server should proxy to backend at http://localhost:5000.

### Module not found errors

Make sure all dependencies are installed:

```bash
npm run install-all
```

## Next Steps

1. Implement enemy spawning system
2. Add tower placement mechanics
3. Create faction-specific towers
4. Integrate database for leaderboard persistence
5. Add sound effects and music
6. Improve graphics and animations

## Support

For issues, check the repository README or create a GitHub issue.
