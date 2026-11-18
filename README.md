# 4 KB Python UCI Chess Engine (`tiny-chess-01`)

A **4,072-byte** (`<= 4,096` bytes) standalone Python 3 UCI chess engine built for the [make.fun 4 KB Python Chess Engine Bounty](https://make.fun/bounty/tiny-chess-01).

## Architecture

- **Search:** Iterative deepening with **MTD(f)** zero-window aspiration search, **Null-Move Pruning** (`R=2`), **Transposition Table** caching `(board, depth, is_root)` bounds, and **Quiescence Search** over captures/promotions (`>= 150` cp).
- **Evaluation:** Piece-Square Tables (PST) across all 6 piece types (`P, N, B, R, Q, K`) packed as 384 signed bytes using `zlib` + Base85.
- **Move Generation & Rules:** 10×12 mailbox board with castling, en passant, queen promotion, and incremental evaluation.
- **Protocol:** Standard UCI (`uci`, `isready`, `position [startpos] moves ...`, `go`, `quit`) plus `--selftest`.

## Quick Start & Verification

Copy `chess_engine_4kb.py` to `main.py` at your repository root before pushing:

```bash
cp chess_engine_4kb.py main.py
wc -c main.py          # Verify <= 4096 bytes (4072 bytes)
python3 main.py --selftest
```

## Pushing & Submitting to `make.fun`

```bash
git init && git add main.py LICENSE README.md makefun-run.json
git commit -m "Initial 4KB Python UCI chess engine"
gh repo create elenavance92/tiny-chess-4kb --public --source=. --push
```

Then download the starter kit from [`https://make.fun/c/tiny-chess-01/kit`](https://make.fun/c/tiny-chess-01/kit), run `node cli/makefun.mjs bundle`, and upload the generated `.tar.gz` bundle with your commit SHA on [make.fun/bounty/tiny-chess-01](https://make.fun/bounty/tiny-chess-01).
