# CLAUDE.md - AI Assistant Guidelines

This document provides guidance for AI assistants working with this repository.

## Project Overview

This is **inming's blog** repository, currently containing a polished single-page Snake game (贪食蛇). The project uses vanilla web technologies without any build systems, frameworks, or external dependencies.

## Repository Structure

```
/
├── CLAUDE.md          # AI assistant guidelines (this file)
├── README.md          # Project description
└── snake.html         # Complete Snake game (single-file)
```

## Technology Stack

- **HTML5** - Document structure with Canvas element
- **CSS3** - Modern styling (gradients, shadows, animations, responsive design)
- **Vanilla JavaScript (ES6+)** - Game logic and interactivity
- **Canvas 2D API** - Game graphics rendering
- **localStorage API** - Persistent high score storage

**No build tools, bundlers, or package managers are used.**

## Running the Project

Simply open any HTML file directly in a modern web browser:
```bash
# Using a browser directly
open snake.html          # macOS
xdg-open snake.html      # Linux
start snake.html         # Windows

# Or serve locally (optional)
python3 -m http.server 8000
```

## Code Conventions

### File Organization
- Each game/feature is self-contained in a single HTML file
- All CSS is embedded in `<style>` tags within the HTML `<head>`
- All JavaScript is embedded in `<script>` tags at the end of `<body>`

### JavaScript Style
- Use `const` for constants and values that don't change
- Use `let` for mutable variables
- Use camelCase for variable and function names
- DOM elements are cached in variables at script initialization
- Game state is managed through module-level variables

### CSS Style
- Use CSS custom properties (variables) for theme colors
- Primary accent color: `#00ff88` (neon green)
- Dark background theme: `#1a1a2e`, `#0a0a1a`
- Use flexbox for layouts
- Include responsive breakpoints for mobile (max-width: 600px)

### HTML Style
- Use semantic HTML5 elements where appropriate
- Include proper meta tags for viewport and charset
- UI text is in **Simplified Chinese**

## Game Architecture (snake.html)

### Configuration Constants
```javascript
const gridSize = 20;        // Pixels per grid cell
const tileCount = 20;       // 400px canvas / 20 = 20 tiles
```

### Game State Variables
- `snake[]` - Array of {x, y} coordinate objects
- `food{}` - Single {x, y} coordinate object
- `direction` / `nextDirection` - Movement vectors
- `score`, `highScore` - Score tracking
- `gameSpeed` - Interval delay in ms (starts at 100, minimum 50)
- `isGameRunning`, `isPaused` - Game state flags

### Main Functions
- `initGame()` - Reset game state
- `gameStep()` - Main loop (calls update + draw)
- `update()` - Game logic (movement, collision, food)
- `draw()` - Canvas rendering
- `generateFood()` - Random food placement
- `gameOver()` - End game and show results

## Development Workflow

### Adding New Features
1. For new games/pages: Create a new self-contained HTML file
2. For modifications: Edit the existing HTML file directly
3. Test by opening the file in a browser
4. No build step required

### Testing
- Manual testing in browser (no automated tests)
- Test on both desktop (keyboard controls) and mobile (touch buttons)
- Verify localStorage persistence works (high scores)

### Git Workflow
- Main branch: `master`
- Feature branches: `claude/<feature-name>-<id>`
- Use descriptive commit messages
- Create PRs for new features

## Common Tasks

### Modifying Game Speed
Edit the `gameSpeed` variable and the speed adjustment in the update function:
```javascript
gameSpeed = 100;           // Initial speed (ms)
gameSpeed -= 2;            // Speed increase per food
if (gameSpeed > 50) ...    // Minimum speed cap
```

### Changing Colors
Update the color values in CSS:
```css
#00ff88  /* Primary accent (snake, UI highlights) */
#ff4444  /* Secondary accent (food, game over) */
#ffd700  /* Tertiary accent (pause) */
```

### Adding Mobile Controls
Mobile controls are already implemented using button elements with touch events. They appear automatically on screens narrower than 600px.

## Important Notes for AI Assistants

1. **No Build System**: This project intentionally avoids npm, webpack, etc. Keep it simple.

2. **Single-File Architecture**: Each game/feature should be self-contained in one HTML file with embedded CSS and JS.

3. **Chinese UI**: All user-facing text is in Simplified Chinese. Maintain this convention.

4. **Browser Compatibility**: Code should work in modern browsers without polyfills.

5. **No External Dependencies**: Don't add CDN links or external libraries unless explicitly requested.

6. **localStorage Keys**: The snake game uses `snakeHighScore` for persistence. Use unique keys for new features.

7. **Responsive Design**: Always include mobile-friendly styles and controls.

## Quick Reference

| Item | Value |
|------|-------|
| Language | Chinese (Simplified) |
| Canvas Size | 400x400 pixels |
| Grid Size | 20x20 tiles |
| Initial Speed | 100ms per frame |
| Min Speed | 50ms per frame |
| Points per Food | 10 |
| localStorage Key | `snakeHighScore` |
