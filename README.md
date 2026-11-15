# tiny-chess-01 entry: 4 KB Python chess engine

A single-file (`main.py`, 3,309 bytes) chess engine: PVS search with
null-move pruning, LMR, a transposition table, killer/history move
ordering, check extensions, quiescence search and tapered piece-square
evaluation, on a fixed 60,000-node budget per move — fully deterministic,
no clock, no randomness (seeded from `MAKEFUN_TRIAL_SEED` if ever needed).

Practice grade (local harness, kit env server + official scorer):
mean Elo 1,550 over trials 0–2 (1,545 / 1,654 / 1,451), above the
sunfish-4k baseline mean of 1,365. Determinism proven (repeated trials
byte-identical); timing ~2.0 s/move, max 2.8 s.

`main.py` is the kit-packed entrypoint (`makefun compress` of `eng3.py`,
the readable source, kept beside it in the working tree).

It plays the house gauntlet through the env at `MAKEFUN_ENV_URL`
(`POST /game`, `/move`, `/resign`), Python 3.13 standard library only.

Grade locally (no Docker on this machine):

    node cli/makefun.mjs grade-local --kit <kitdir> --bot <repo> --driver process --instances 3
