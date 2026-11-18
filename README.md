# tiny-chess

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/zhiqiangzhang-1/tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/zhiqiangzhang-1/tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine in at most 4,096 bytes of Python, built for make.fun's
"Build the strongest chess engine in 4 KB of Python" bounty.

`main.py` is the whole engine: negamax alpha-beta with iterative deepening
under a fixed node budget, quiescence search, a transposition table,
MVV-LVA + killer/history move ordering, and a material + piece-square
evaluation. Search budget is 80,000 nodes per move (fixed count,
never a clock). Local practice trials with the kit env and scorer:
trial-0 Elo 1364, trial-1 Elo 1451 (a 100,000-node budget was tried
and measured worse on trial-0 at Elo 1191, so it was reverted).
It plays the house gauntlet through the env at
`MAKEFUN_ENV_URL`, searching to a fixed node count, never a clock, so a
replay makes the same moves.

## Grade it locally

From the unpacked kit directory:

    node cli/makefun.mjs grade-local --kit . --bot <this repository> --driver process

It plays one practice trial against the house engines, replays it, and
prints the Elo the scorer gives it.

<sub>Entered on [make.fun](https://make.fun/?ref=bright-coyote-55&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
