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
- Game over display: dual overlays on each player's board (winner/loser messages)
- Button visual feedback: touch buttons now light up red for touch and keyboard controls (not just mouse)

### Answer Overlay Positioning
- Math overlay positioned completely outside the game board (right:100%/left:100%)
- Player A's overlay appears to the left of their board
- Player B's overlay appears to the right of their board
- Responsive sizing for smaller screens (700px, 500px breakpoints)

### Answer Feedback Animation
- Correct answer: shows cyan checkmark (✓) with pop animation
- Wrong answer: shows red X (✗) with pop animation
- 600ms delay before continuing to next question

### Review System (答题复盘)
- Split into left/right columns (Player A on left, Player B on right)
- Each player has independent submit button
- 50% pass threshold:
  - If correct >= 50%: answers revealed, shows "通过！答案已公布"
  - If correct < 50%: answers hidden, must retry, shows "错误超过50%，请重新作答"
- "重新对决" button appears only when both players have passed OR both have failed

### Audio Controls
- Music button: toggles background music on/off (initial state: on)
- Sound effects button: toggles game sound effects on/off (initial state: on)
- Volume slider: adjusts volume for both music and sound effects

### Game Over Effects
- Music switches to a new random track when game ends
- Music auto-stops after 5 seconds OR when "答题复盘" is clicked
- Winner's board displays celebration confetti animation
- Winner overlay has pulsing green glow effect

### Music Playlist
- Playlist is shuffled at game start (random first song)
- Songs continue in sequence, looping through the playlist

### Smart Distractor System (Updated 2026-01-02)
Math problem options are designed to capture common student misconceptions, with randomized selection from expanded pools to avoid predictable patterns.

**Type 1: x ± a = b** (Pool of 8, randomly select 3)
- b + a (wrong direction)
- a - b (reversed order)
- b (forgot to subtract)
- -b (sign confusion)
- -(b - a) (double sign error)
- -x, x+1, x-1 (fallbacks)

**Type 2: ax ± b = c** (Pool of 9, randomly select 3)
- (c + b) / a (forgot sign change)
- c - b (forgot to divide)
- c / a (forgot constant)
- c (just copied right side)
- (c - b) / (-a) (division sign error)
- b - c (reversed subtraction)
- -x, x+1, x-1 (fallbacks)

**Type 3: a(x ± b) = c** (Pool of 8, randomly select 3)
- c / a (forgot inner constant)
- c / a + b (wrong direction)
- c - b (wrong operation order)
- (c - b) / a (distributed incorrectly)
- c / a + 2b (double constant error)
- -x, x+1, x-1 (fallbacks)

**Type 4: Complex equations**
- Pool of 5 fallback distractors: -x, x±1, x±2

This randomized approach prevents the predictable "answer or its negative" pattern while still capturing meaningful misconceptions.

### Practice Mode (Updated 2026-01-02)
A two-player practice mode for learning equation solving, similar to the review system layout.

**Features:**
- "练习" button next to "开始战斗" on the main screen
- Split into left/right columns (Player A on left, Player B on right)
- Each player gets 3 independent questions (one each from Type 1, 2, 3)
- Players' questions can be different
- Each player has their own submit button
- After submission:
  - Correct answers show cyan checkmark (✓)
  - Wrong answers show red X (✗)
  - Wrong answers reveal detailed step-by-step solution
- Buttons per player: "再次练习" (practice again) or "返回主页" (return to home)
- Return to home requires BOTH players to click "返回主页"
- Shows "等待对方..." when one player has confirmed

**Solution Step Format:**
Solutions show the algebraic principle of "performing the same operation on both sides":

- Type 1 (x ± a = b):
  1. 原式：x + a = b
  2. 等号左右各减去 a
  3. x + a - a = b - a
  4. x = [answer]

- Type 2 (ax ± b = c):
  1. 原式：ax + b = c
  2. 等号左右各减去 b
  3. ax + b - b = c - b
  4. ax = [result]
  5. 等号左右各除以 a
  6. ax ÷ a = [result] ÷ a
  7. x = [answer]

- Type 3 (a(x ± b) = c):
  1. 原式：a(x + b) = c
  2. 等号左右各除以 a
  3. a(x + b) ÷ a = c ÷ a
  4. x + b = [result]
  5. 等号左右各减去 b
  6. x + b - b = [result] - b
  7. x = [answer]
