# tiny-chess-01

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/arthosiu-cmd/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard)
[![reward](https://make.fun/badge/tiny-chess-01/arthosiu-cmd/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01)

A 4 KB chess engine in Python (stdlib only). `main.py` unpacks an
lzma payload and plays the gauntlet through the env at
`MAKEFUN_ENV_URL`: POST `/game`, POST `/move`.

Engine: 0x88 board, negamax alpha-beta with quiescence (captures,
promotions, check evasions), transposition table, killer moves,
MVV-LVA ordering, iterative deepening to a fixed 50,000 nodes per
move — never a clock, so replays are deterministic. Evaluation is
material (P100 N320 B330 R500 Q900) plus piece-square tables.
Legal move generation is internal (castling, en passant, promotion,
check, stalemate and checkmate); the env's `legal_moves` only
selects the move actually sent.

## Size

- `main.py`: at most 4,096 bytes as committed (packed payload).
- Whole repo: at most 8,192 bytes, no file over 4,096. MIT.
