# Clarity

<img src="assets/Clarity%20Logo.png" width="150" height="150">

> UCI chess engine with NNUE evaluation

A UCI-compatible chess engine. The engine uses an alpha-beta search with many enhancements, and evaluation is handled by a small-size, efficiently updatable neural network (NNUE) trained on data from simulated games against itself.

The last major release (4.0.0 as of the time of typing this) has been rated 3448 Elo in CCRL Blitz and is yet to be fully tested for CCRL 40/15. The blitz elo of 3438 puts it as the 52nd highest-ranked engine based on their testing.

## Feature List:

CLI:
  1. Functional (but not complete) UCI implementation
  2. Custom Commands:
      1. ``printstate``: shows the state of the board.
      2. ``perftsuite <suite>``: performs a suite of perft tests, currently only supports the suite ethereal.
      3. ``perft <depth>``: performs a perft test from the current position and outputs the result.
      4. ``splitperft <depth>``: performs a perft test from the current position and outputs the result seperated by which move is the first one done.
      5. ``getfen``: outputs a string of Forsyth-Edwards Notation (FEN) that encodes the current position.
      6. ``incheck``: outputs if the current position is in check or not.
      7. ``evaluate``: outputs the evaluation of the current position.
      8. ``bench <depth>``: performs the bench test, a fixed depth search on a series of 50 positions.
      9. ``position kiwipete``: loads the position known as kiwipete, with the FEN of ``r3k2r/p1ppqpb1/bn2pnp1/3PN3/1p2P3/2N2Q1p/PPPBBPPP/R3K2R w KQkq - 0 1``.
      10. ``makemove <move>``: takes in one move in long algebraic notation and performs it on the board.
      11. ``undomove``: undoes the most recent move on the board.
      12. ``nullmove``: switches the current color to move, also known as a null move.
      13. ``undonullmove``: undoes a null move.
      14. ``isrepeated``: outputs a boolean of if the current position is a repeat.
      15. ``tunablejson``: outputs the text contents of a JSON file of all of the tunable parameters within Clarity.

Board Representation:
  1. Copymake moves
  2. Board represented using 8 bitboards
  3. Pext bitboards / Magic bitboards, lookups, and setwise move generation
  4. Repetition detection
  5. Incremental Zobrist hashing
  6. Incremental NNUE Updates
  7. Rudimentary (but sufficient) board visualization

Search: 
  1. Fail-Soft PVS search with alpha-beta pruning
  2. Transposition Table (TT) (with adaptable sizing)
  3. Internal Iterative Reductions
  4. Improving Detection + Modifications
  5. Razoring
  6. Reverse Futility Pruning (Static Null Move Pruning)
  7. Null Move Pruning
  8. Check Extensions
  9. Move Ordering (More on this later)
  10. Mate Distance Pruning
  11. Incremental Move Sorting
  12. Futility Pruning
  13. Late Move Pruning
  14. Late Move Reductions
  15. Static Exchange Evaluation (SEE) Pruning
  16. History Pruning
  17. Quiescence Search
      1. TT cutoffs
      2. Stand Pat Shenanigans
      3. Move Ordering
      4. Incremental Move Sorting
      5. SEE Pruning
      6. Dedicated capthist for Q search

Evaluation:
  1. (768->256)x2->1 NNUE trained from over 400 million positions of self play data

Move Ordering:
  1. Transposition Table Best Move
  2. Good Captures (As described by SEE) are sorted with MVV and Capthist
  3. Killer Move 
  4. Quiets are scored with main history and ply - 1 and ply - 2 conthist
  5. Bad Captures are also sorted with MVV and capthist but are not boosted above quiets.
  6. Dedicated and simplified move ordering function for Q search


### Special Thanks (in no particular order):

  [Toanth](https://github.com/toanth): General help and explaining things I didn't understand before
  
  [Ciekce](https://github.com/Ciekce): Preventing the cardinal sins of C++ since day 1
  
  [RedBedHed](https://github.com/RedBedHed): Lookup tables for move generation
  
  [JW](https://github.com/jw1912): More random C++ things
  
  [A_randomnoob](https://github.com/mcthouacbb): Helping with a lot of random engine bits

  [zzzzz](https://github.com/zzzzz151/): Ideas, planning, and a lot that I probably forgot

  **Logo generated by AI**
