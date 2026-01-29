# AGENTS.md - Game Development Repository Guide

This repository contains HTML5 canvas-based games with vanilla JavaScript. All games are self-contained HTML files with embedded CSS and JavaScript.

## Project Structure
- `index.html` - Main game hub/landing page 
- `game1.html` - Snake RPG game with player customization
- `game2.html` - Bird shooting game with level progression
- `game3.html` - Block Blast puzzle game with drag-and-drop

## Technology Stack
- **Frontend**: Vanilla HTML5, CSS3, JavaScript (ES6+)
- **Graphics**: HTML5 Canvas API
- **Audio**: Web Audio API for synthesized sounds
- **Storage**: localStorage for game state persistence
- **No build tools**: Direct file serving required

## Development Commands
Since this is a static HTML project, there are no build commands. Development workflow:

### Testing Games
```bash
# Serve the directory (any static server)
python -m http.server 8000
# or
npx serve .
# or use VS Code Live Server extension

# Then visit:
http://localhost:8000/index.html
```

### Individual Game Testing
Open directly in browser:
- `file:///path/to/game1.html`
- `file:///path/to/game2.html` 
- `file:///path/to/game3.html`

## Code Style Guidelines

### HTML Structure
- Use semantic HTML5 elements (`header`, `main`, `section`)
- Chinese language support: `<html lang="zh-HK">` or `<html lang="zh-TW">`
- Mobile-first responsive design with viewport meta tag
- Single-file architecture (HTML, CSS, JS embedded)

### CSS Conventions
- CSS custom properties (variables) for theming
- Mobile-first responsive design with `@media` queries
- Flexbox and Grid for layouts
- Touch-friendly: `touch-action: manipulation`, large tap targets
- Use `rgba()` and `hsl()` for colors
- CSS animations over JavaScript animations when possible
- Component-based class naming (`.piece-slot`, `.block-base`)

### JavaScript Standards
- Use `const` and `let` exclusively (no `var`)
- ES6+ features: arrow functions, template literals, destructuring
- Event delegation for dynamic content
- RequestAnimationFrame for smooth animations
- Classes for game objects (Entity, Particle, SoundManager)
- Modular code organization with clear separation of concerns

### Naming Conventions
- **Variables**: camelCase (`currentLevel`, `isGameOver`)
- **Functions**: camelCase with descriptive verbs (`spawnPieces()`, `updateHUD()`)
- **Constants**: UPPER_SNAKE_CASE (`GRID_SIZE`, `COLORS`)
- **CSS Classes**: kebab-case (`.game-container`, `.high-score-container`)
- **DOM Elements**: descriptive with element type suffix (`gridEl`, `scoreEl`)

### Game Development Patterns
- **Game Loop**: Use `requestAnimationFrame()` with timestamp tracking
- **State Management**: Single source of truth for game state
- **Input Handling**: Support both mouse and touch events
- **Performance**: Object pooling for particles, efficient DOM updates
- **Audio**: Web Audio API for synthesized sounds with fallback handling

### File Organization
- Keep HTML, CSS, JS in single files for portability
- Group related functionality with comments
- Use data attributes for element identification (`data-theme`, `data-acc`)
- Separate game logic from rendering logic

### Mobile Optimization
- Viewport configuration: `width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no`
- Touch event handling with `preventDefault()` for game controls
- Responsive layout calculation based on viewport dimensions
- Safe area insets for modern mobile devices

### Performance Guidelines
- Minimize DOM manipulations during animations
- Use CSS transforms and opacity for smooth animations
- Batch DOM updates together
- Clear event listeners on cleanup
- Use `dataset` for simple data storage on elements

### Storage Patterns
- Use `localStorage` for persistent game data
- Implement proper JSON serialization/deserialization
- Provide fallback defaults when stored data is missing
- Store minimal data structures, not full objects

### Error Handling
- Graceful degradation for unsupported features
- Browser compatibility checks for newer APIs
- Safe property access with optional chaining
- Audio context state management (handle suspended state)

## Game-Specific Notes

### Snake Game (game1.html)
- Grid-based movement system
- Player customization with avatar rendering
- Multiple food types with different effects
- Sound synthesis for game events

### Bird Shooter (game2.html)  
- Entity system for moving targets
- Level progression with difficulty scaling
- Particle effects and screen shake
- Touch/click input with position tracking

### Block Blast (game3.html)
- Drag-and-drop system with visual feedback
- Grid placement validation
- Line clearing mechanics
- Theme switching capability

## Browser Compatibility
- Target modern browsers (Chrome, Firefox, Safari, Edge)
- Use feature detection for newer APIs
- Provide fallbacks where necessary
- Test on both desktop and mobile devices

## Accessibility
- Keyboard navigation support where applicable
- High contrast mode support
- Screen reader friendly semantic HTML
- Focus management for interactive elements

## Localization
- Games currently support Traditional Chinese (zh-HK, zh-TW)
- Use Unicode characters for game graphics (emoji)
- Consider RTL language support for future expansions