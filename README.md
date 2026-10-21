# Chess

1v1 online chess with 66+ mutator rules that change the game every 3 moves. Built with Node.js, Express, Socket.IO, and chess.js.

Based on a concept by [DougDoug](https://twitch.tv/dougdoug)

Play at [playanarchychess.com](https://playanarchychess.com).

## Features

- **Mutator system** - every 3 moves, the current player picks from 3 random rule changes (e.g. pieces swap, squares become blocked, pawns gain new abilities)
- **66+ rules** with varying durations, categories, and interactions
- **Room codes** - create/join games with human-readable codes
- **Spectator mode** - watch live games
- **Bot opponent** - practice mode with minimax AI
- **Scoreboard** - persistent leaderboard tracking wins/losses/draws per player (IP-hashed, no PII stored)

## Setup
### Get Git and Node.js
Git: https://git-scm.com/

The game needs Node.js 18+, if you don't have NodeJS download it at: https://nodejs.org/en/download/

### Install

You can download the game files you can either click code (the green button on the top right) -> download zip or run:
```bash
git clone https://github.com/Ryukaki/ThressGame
cd chess
```

### Environment Variables

Create a `.env` file:

```
PORT=3000
BASE_PATH=/chess
```

### Run

```bash
npm start        # production
npm run dev      # development (auto-reload)
```
You can now play offline by accessing [http://localhost:3000/](http://localhost:3000/).

## Project Structure

- `handlers/` - Socket.IO event handlers (join, move, mutator, spectator)
- `mutators/` - Rule definitions, lifecycle engine, hooks, board utilities
- `public/js/` - Modular client (state, board, UI, socket handlers)
- `utils/` - Validation, config, room codes, RPS logic
- `bots/` - Minimax chess AI

## How Mutators Work

Every 3 moves, the active player is shown 3 randomly-weighted rule cards. They pick one, it activates, then they play their move. Rules can:

- Modify piece movement (knights move like bishops, pawns get extra range)
- Add board hazards (minefields, blocked squares, tornadoes)
- Trigger instant effects (swap pieces, destroy squares, shuffle the board)
- Persist for N moves or until expiry conditions are met

Multiple rules stack simultaneously. The system handles conflicts, field restrictions, and deadlock detection automatically.

## Responsible AI Disclosure

Claude Code used to handle deployments/git pushes and generate changelog summaries because I am lazy. 

## License

[ISC](LICENSE)
