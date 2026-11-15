# tiny-chess-01 entry: 4 KB Python chess engine

A single-file (`main.py`, ≤ 4,096 bytes) chess engine: alpha-beta search
with a transposition table, MVV-LVA + killer/history move ordering,
quiescence search and piece-square evaluation, on a fixed node budget per
move — fully deterministic, no clock, no randomness (seeded from
`MAKEFUN_TRIAL_SEED` if ever needed).

It plays the house gauntlet through the env at `MAKEFUN_ENV_URL`
(`POST /game`, `/move`, `/resign`), Python 3.13 standard library only.

Grade locally (no Docker on this machine):

    node cli/makefun.mjs grade-local --kit <kitdir> --bot <repo> --driver process --instances 3
