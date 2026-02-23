# Nine by Nine

A minimalistic, retro-terminal styled Sudoku solver built with vanilla HTML, CSS, and JavaScript. Runs entirely in the browser — no dependencies, no build step.

![nine-by-nine-preview](https://img.shields.io/badge/status-live-00ff88?style=flat-square&labelColor=0a0a0a) ![license](https://img.shields.io/badge/license-MIT-5599ff?style=flat-square&labelColor=0a0a0a)

## How It Works

The solver uses a **backtracking algorithm** — the same approach as a human trying every possibility: place a number, check if it's valid, move on. If you hit a dead end, undo and try the next number.

Three checks run on every placement:
- No duplicate in the same **row**
- No duplicate in the same **column**  
- No duplicate in the same **3×3 box**

If no number works in a cell, the algorithm backtracks to the previous cell and tries the next candidate. This continues recursively until the board is complete — or all possibilities are exhausted (no solution).

## Features

- Backtracking solver ported from Python to JavaScript
- Runs entirely client-side, no server needed
- Keyboard navigation between cells (arrow keys)
- Highlights given numbers vs. solved numbers
- Input validation with visual error feedback
- Built-in example puzzle to get started
- CRT scanline aesthetic with Press Start 2P font

## Usage

Just open `sudoku.html` in any browser. No installation required.

```bash
git clone https://github.com/yaarrjanhavi/nine-by-nine.git
cd nine-by-nine
open sudoku.html
```

Enter your puzzle (leave unknowns blank), then hit **▶ SOLVE**. Use **EXAMPLE** to load a sample puzzle, or **CLEAR** to reset the board.

## Algorithm

```
function sudoku(board, row, col):
    if row == 8 and col == 9 → solved, return true
    if col == 9 → move to next row
    if cell already filled → skip to next cell
    
    for num in 1..9:
        if isSafe(board, row, col, num):
            place num
            if sudoku(board, row, col + 1): return true
            remove num  ← backtrack
    
    return false  ← trigger backtrack
```

Time complexity is O(9^m) where m is the number of empty cells, though in practice the constraint checks prune the search space dramatically.

## Stack

- HTML / CSS / JavaScript (zero dependencies)
- [Press Start 2P](https://fonts.google.com/specimen/Press+Start+2P) via Google Fonts

## License

MIT
