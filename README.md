

# Literate Chess Puzzle Solving with Org


<style>
.figure-number { display: none; }
</style>

Every Wednesday in my town, there's a pub quiz at the Queens Head.
Richard, the landlord, runs a very quirky quiz where the prize hardly ever
goes to the best team.  A typical announcement would be, "Totally chosen at
random by a passing Nun, tonight's Star Prize is a Luxury Deluxe bottle of
Prosecco, going to the team that comes third!".

He also takes out adverts for the pub in a local monthly magazine called
The Fuddler.  Every month, along with the advert, there's a mate-in-2 chess
puzzle.  Richard is a chess fan; I don't know where he gets the puzzles
from, but they're always quite fiendish.

![img](./fuddler.png "Advert in The Fuddler, November 2022")

In the puzzle above, the Black King is hemmed in and can't move.  All White
needs to do is give check, which looks easy: **RxN**, which also removes the
troublesome Knight, and the King still has nowhere to go.  But there's an
escape: **Qf5**, blocking the Rook check.  The Rook can simply take the
Queen, giving check again, but now Black has another escape move: **Ke4**,
since the Bishop is now blocked by the Rook.

And that's as far as I got with this one.

This happens a lot.  Even if I think I've worked out the answer, I'm never
completely sure about it.  And, slightly annoyingly, there's never any
answer to the puzzle in the next issue.  But I'd like to know what I've
missed, mainly to get that "Aha!" moment.  So&#x2026; I decided to find some
tools to help.

I looked at [Lichess](https://lichess.org), which is a great free online chess tool, and accepts
board positions in FEN format.  For the puzzle above, the FEN format is:

    5K2/3PRnQB/2p5/3p4/5k2/7q/2N5/4N3 w - - 0 1

You can get it to set up the position like [this](https://lichess.org/analysis/standard/5K2/3PRnQB/2p5/3p4/5k2/7q/2N5/4N3#0).  Its Stockfish analysis
mode will come up with a mate in 2:

    1. Ne3
    2. Qf5  N3g2#

Hmm.  OK, that's mate, but what if Black had done something different?

[Popeye](https://www.chessprogramming.org/Popeye) link.

Here's the **popeye** input needed to solve the Fuddler puzzle above:

    Begin
    Origin       Fuddler, November 2022
    Pieces       White Se1 Sc2 Pd7 Re7 Qg7 Bh7 Kf8
                 Black Qh3 Kf4 Pd5 Pc6 Sf7
    Option       Variation
    Stipulation  #2
    End

    Popeye Linux-3.16.0-38-generic-x86_64-64Bit v4.79 (1024 MB)
    
           Fuddler, November 2022
    
    +---a---b---c---d---e---f---g---h---+
    |                                   |
    8   .   .   .   .   .   K   .   .   8
    |                                   |
    7   .   .   .   P   R  -S   Q   B   7
    |                                   |
    6   .   .  -P   .   .   .   .   .   6
    |                                   |
    5   .   .   .  -P   .   .   .   .   5
    |                                   |
    4   .   .   .   .   .  -K   .   .   4
    |                                   |
    3   .   .   .   .   .   .   .  -Q   3
    |                                   |
    2   .   .   S   .   .   .   .   .   2
    |                                   |
    1   .   .   .   .   S   .   .   .   1
    |                                   |
    +---a---b---c---d---e---f---g---h---+
      #2                          7 + 5
    
       1.Sc2-e3 ! zugzwang.
          1...Qh3-f1
              2.Qg7-g4 #
          1...Qh3-g2
              2.Se3*g2 #
          1...Qh3*d7
              2.Se3-g2 #
          1...Qh3-e6
              2.Se3-g2 #
          1...Qh3-f5
              2.Se3-g2 #
          1...Qh3-g4
              2.Qg7*g4 #
          1...Qh3-h1
              2.Qg7-g4 #
          1...Qh3-h2
              2.Qg7-g4 #
          1...Qh3*e3
              2.Re7*f7 #
          1...Qh3-f3
              2.Se1-d3 #
          1...Qh3-g3
              2.Qg7-f6 #
          1...Qh3*h7
              2.Qg7-g4 #
          1...Qh3-h6
              2.Se3-g2 #
          1...Qh3-h5
              2.Se3-g2 #
          1...Qh3-h4
              2.Se3-g2 #
          1...d5-d4
              2.Re7-e4 #
          1...c6-c5
              2.Se3*d5 #
          1...Sf7-d6
              2.Qg7-e5 #
          1...Sf7-e5
              2.Qg7*e5 #
          1...Sf7-g5
              2.Qg7-e5 #
          1...Sf7-h6
              2.Qg7-e5 #
          1...Sf7-h8
              2.Qg7-e5 #
          1...Sf7-d8
              2.Qg7-e5 #
    
    
    solution finished. Time = 0.026 s


# License

    Copyright (c) 2022, Glenn Hutchings <zondo42@gmail.com>
    All rights reserved.
    
    This work is licensed under the Creative Commons Attribution-ShareAlike 4.0
    International License.  To view a copy of this license, visit
    http://creativecommons.org/licenses/by-sa/4.0/ or send a letter to Creative
    Commons, PO Box 1866, Mountain View, CA 94042, USA.

