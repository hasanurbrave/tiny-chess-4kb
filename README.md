# tiny-chess-01

Deterministic Python chess engine compressed into under 4 KB for the make.fun `tiny-chess-01` competition.

## Overview
- **HTTP Protocol**: Fully compliant with `MAKEFUN_ENV_URL` (`POST /game` and `POST /move`).
- **Search**: MTD(f) zero-window search with Transposition Table move ordering, killer-move heuristics, check extensions in quiescence, and null-move pruning.
- **Evaluation**: Piece-square tables, bishop pair bonus, passed-pawn progression, and endgame king centralization.
- **Draw Rules**: Integrated 3-fold repetition and 50-move rule scoring (0) inside search.
- **Determinism**: 100% deterministic (no clock queries or unseeded randomness), using only the Python 3.13 standard library.
