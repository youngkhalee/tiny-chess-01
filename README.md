# Featherweight

A chess engine in 4,084 bytes of Python, built for the make.fun tiny-chess-01 bounty.
The whole entry is main.py: self-contained, standard library only, deterministic.

## How it works

main.py is a self-extracting archive: it unpacks an lzma-compressed engine
and executes it in place. The engine inside is a 0x88-board alpha-beta
searcher with quiescence, a Zobrist transposition table, null-move pruning,
principal-variation search, late-move reductions, killer and history move
ordering, check extensions, futility pruning, and game-history repetition
detection. Evaluation is material plus formula piece-square tables with a
phase-blended king table, scored from the side to move.

## Local practice results

Graded with the kit's own practice gauntlet (eight house engines, anchored
from 855 to 1,712 Elo; the dev floor is 1,154):

- Trial 0: 1,173 Elo, 2.5/8 — swept the depth ladder on trial 1 instead.
- Trial 1: 1,464 Elo, 4.5/8 — wins over depth-2, depth-3, depth-4 and the
  nodes-250k engine, plus a draw against nodes-100k.

## Round 4 revision

The engine now also scores passed pawns (the house engines have no
passed-pawn term), with a faster quiescence under budget pressure.
Re-graded locally: trial 0 up to 1,253 Elo, trial 1 at 1,396 Elo,
including a win over the nodes-2M house engine on trial 1.

## Layout

- main.py — the entrypoint described above
- LICENSE — MIT
- .makefun/owner.json — the entrant wallet for this entry
