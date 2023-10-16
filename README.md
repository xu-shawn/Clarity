# Clarity

The C++ rewrite is complete! Clarity is now faster and better, using new techniques, and I have learned a new language!

For those who didn't see the engine in its depressing, confusing, error-filled C# state, this engine was originally written in C# before I decided to switch to C++. That decision was one of the greatest I think I've ever had, as the engine is now faster, easier to read, less error-filled(hopefully), and better overall.

My current Estimate of elo (calculated by playing large sums of games against engines with known CCRL ratings) is 2200.

#### Warning: Clarity currently uses pext for move generation, which means that CPUs without BMI2 or CPUs with a slow implementation (Zen 2 or earlier) will not be able to use it, A replacement (magic bitboards) is underway.

### Special Thanks (in no particular order):

  [Toanth](https://github.com/toanth): General help and explaining things I didn't understand before
  
  [Ciekce](https://github.com/Ciekce): Preventing the cardinal sins of C++ since day 1
  
  [RedBedHed](https://github.com/RedBedHed): Lookup tables for move generation
  
  [JW](https://github.com/jw1912): More random C++ things
  
  [A_randomnoob](https://github.com/mcthouacbb): Helping with a lot of random engine bits

  [zzzzz](https://github.com/zzzzz151/): Ideas, planning, and a lot that I probably forgot

### Todo lists:

General Things:
  1. Web version of the engine
  2. or unleash it on lichess

Board Representation:
  1. General performancey things
  2. Magic bitboards as a backup for non-bmi2 CPUs

Search:
  1. I am working on the list of ideas

Evaluation:
  1. Passed pawns
  2. Pawn structure
  3. Texel Tuning
  4. NNUE eventually


## Feature List:

CLI:
  1. UCI Implementation
  2. printstate: shows the state of the board.
  3. perftsuite <suite>: performs a suite of perft tests, currently only supports the suite ethereal.
  4. perft <depth>: performs a perft test from the current position and outputs the result.
  5. splitperft <depth>: performs a perft test from the current position and outputs the result seperated by which move is the first one done.
  6: getfen: outputs a string of Forsyth-Edwards Notation (FEN) that encodes the current position.
  7: incheck: outputs if the current position is in check or not.
  8: evaluate: outputs the evaluation of the current position.
  9: bench <depth>: performs the bench test, a fixed depth search on a series of 50 positions.

Board Representation:
  1. Copymake moves
  2. Board represented using 8 bitboards
  3. Pext bitboards, lookups, and setwise move generation
  4. Repetition detection
  5. Incremental Zobrist hashing
  6. Incremental PSQT updates

Search: 
  1. PVS search
  2. Aspiration windows
  3. Transposition Table(TT) cutoffs
  4. Reverse Futility Pruning
  5. Null Move Pruning
  6. Late Move Reductions (log function, generated on startup)
  7. Fail-soft
  8. Currently nonfunctional LMP

Evaluation:
  1. PeSTO PSQTs and piece weights (soon to be tuned)
  2. Non-functional passed pawn detection

Move ordering:
  1. TT best move
  2. MVV-LVA
  3. History Heuristic
