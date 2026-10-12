# Andrew's Game

A terminal adventure I wrote in 2018 as a gift for my best friend Andrew. You play as Andrew (Connor is on the menu too, but there's only one real choice). To cross the map you answer questions about your hero, then beat mini-games. Inside jokes included.

## Build and play

Needs a C++ compiler, `make` and curses: built in on macOS; on Debian or Ubuntu, `sudo apt install libncurses-dev`.

```sh
make            # builds game.x: the quest, with hangman and the worm game
./game.x
```

The quest runs in the terminal: answer the prompts, then play the levels. Hangman reads its words from `hangman.txt`. The worm (snake) game uses curses and the arrow keys.

## What's in here

| Path | What |
|---|---|
| `gameMain.cpp`, `game.cpp` | the quest: hero choice, questions, the map of levels |
| `hangman.cpp`, `worm.cpp`, `board.cpp`, `getChar.cpp` | the mini-games the quest uses |
| `connect4/` | Connect 4, standalone: `cd connect4 && make && ./connect4.x` |
| `worm/` | the worm game on its own: `cd worm && make`, then `./screen.x <rows 10–25> <columns>` |
| `15_puzzle/` | sliding 15-puzzle, standalone: `c++ -o p15 15Puzzle.cpp` |
| `spher/` | a small C program from the same time |
| `hangman/` | an earlier copy of the hangman level |
| `Battle/` | a battle mini-game, unfinished (no `main` yet) |
| `Rules flow chart.pdf` | how the quest flows |

## History

Cleaned up in 2026: committed build output (`.o`, `.x`, `a.out`) and run-time logs were removed and are now ignored, and this README was added. Two standalone builds didn't compile with a current compiler, and both are fixed. Connect 4 had a `main()` with no return type and declared its win counters twice, and the worm screen sent `std::cout` to itself instead of `std::endl`. Four functions also fell off the end without returning a value (`RunWorm`, `connect_Game`, `storeGrowth` and an unused stub). Otherwise the code is as written in 2018.
