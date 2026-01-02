# Tetris Math Game (一元一次俄羅斯)

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
