# Tetris Math Game (一元一次俄罗斯)

## Overview
A two-player Tetris-style game with math equation challenges built in pure HTML/CSS/JavaScript. Players compete against each other, and clearing lines triggers math problems for the opponent.

## Project Structure
- `index.html` - Main game file containing all HTML, CSS, and JavaScript
- `bgmusic(1-7).mp3` - Background music tracks
- `stonefall.mp3` - Sound effect for block placement

## Tech Stack
- Pure HTML5/CSS3/JavaScript (no build system or frameworks)
- Static file serving via Python's http.server

## Running the Project
The project runs as a static website served by Python's built-in HTTP server:
```
python -m http.server 5000 --bind 0.0.0.0
```

## Game Controls
- Player A: WASD keys
- Player B: Arrow keys
- Touch controls available for mobile/tablet

## Features
- Two-player competitive mode
- Math equation challenges when lines are cleared
- Multiple background music tracks with volume control
- Fullscreen mode support
- Touch controls for mobile devices
- Answer review system (答题复盘) - review wrong answers after game ends
- Practice mode for wrong questions with answer reveal

## Recent Changes (2026-01-02)
- Converted all traditional Chinese to simplified Chinese
- Added Credits attribution line below the rules table (inside help-content, below red border)
- Implemented answer review system with:
  - Semi-transparent game over popup showing loser's board state
  - Wrong answer tracking during gameplay
  - Review screen displaying all incorrect answers
  - Practice mode: select answers, submit to reveal correct ones
  - Retry practice or restart game options
- Game over display: dual overlays on each player's board (winner/loser messages)
- Responsive math overlay: shrinks on small screens (<600px) to avoid blocking opponent's board
- Button visual feedback: touch buttons now light up red for touch and keyboard controls (not just mouse)
