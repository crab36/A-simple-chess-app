# Chess – Play Against the Engine ♟️

A fully offline chess app with its **own JavaScript chess engine** – not a wrapper
around someone else's website, but a standalone open-source project.

## What Makes This App Different

Most Android chess apps are either wrappers around Stockfish or use a very
simple random-move AI. This app takes a different approach:

- **Own engine, no Stockfish wrapper**: The engine is implemented from scratch
  in pure JavaScript (~2000 lines) and runs in a Web Worker.
- **Modern search techniques**: Principal Variation Search (PVS), transposition
  table (2^20 entries), Late Move Reduction, null-move pruning, SEE, countermove
  heuristic, and iterative deepening with aspiration windows.
- **Texel-tuned evaluation**: PeSTO piece-square tables, mobility, outposts,
  protected/connected passed pawns, bad bishop, king safety.
- **Opening book**: 34 main variations with 329 positions.
- **5 difficulty levels** – from beginner to master.
- **Fully offline**: All dependencies (including `chess.js` for PGN handling)
  are embedded locally. No external downloads, no network requests.

## Features

- Player vs. Engine (5 levels) or Player vs. Player (hotseat)
- Full standard chess rules: checkmate, stalemate, castling, en passant, promotion
- 50-move rule, threefold repetition, insufficient material
- Undo/redo, board flip, resign
- PGN import and export
- Captured pieces and material balance
- Info panel with search depth, nodes, time and evaluation
- No ads, no in-app purchases, no tracking, no network permission

## Technical Details

- **Platform**: Android WebView (no native engine, by design)
- **Engine**: 0x88 board, Zobrist hashing (2×32 bit), incremental evaluation
## Why WebView?

The app is intentionally built as a WebView app because the engine is written
in JavaScript, which keeps it usable across platforms (including in a browser).
The WebView only hosts the locally embedded, fully offline HTML file. There are
no network requests, no tracking, and no external resources.
